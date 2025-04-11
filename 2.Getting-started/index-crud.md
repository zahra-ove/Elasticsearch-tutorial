1. create new index: `PUT /pages`
2. delete an index: `Delete /pages`

3. create a new index with index configs in the request body

```
PUT /products
{
    "settings": {
        "number_of_shards": 2,
        "number_of_replicas": 2
    }
}
```


4. add a document to index\
   note: `_id` value if given by elasticsearch if not specified in the query

```
POST /products/_doc
{
    "name": "Coffee Maker",
    "price": 64,
    "in_stock": 4
}
```

[result](./../images/creating-doc-result.png)


5. add new document to the index and specify the `_id` value\
   note: notice the http verb which is used.

```
PUT /products/_doc/100

{
    "name": "Coffee Maker",
    "price": 64,
    "in_stock": 4
}
```

[result](./../images/creating-doc-by-id-result.png)


6. there is a config in the Elasticsearch which is:\

`action.auto_create_index` which is by default `True` \
which means if we try to add a document to a non-exiting index,
the index will be created automatically.


7. retrieve the specific document by id:

```
GET /products/_doc/100
```

the result is:

```
{
  "_index": "products",
  "_type": "_doc",
  "_id": "100",
  "_version": 1,
  "_seq_no": 1,
  "_primary_term": 1,
  "found": true,
  "_source": {
    "name": "Toaster",
    "price": 49,
    "in_stock": 4
  }
}
```

if the resource is found then the `found` key is equal to `True`.

8. update a document

```
POST /products/_update/100
{
  "doc": {
    "in_stock":9
  }
}
```

if update operation is done successfully, then the `result` will be `updated` but the update operation fail, then `result: noop`

we could also add a key to the document which that key does not exists before like:

```
POST /products/_update/100
{
  "doc": {
    "tags":["electronics"]
  }
}
```



**note: Elasticsearch documents are immutable. in the previous example we actually replaced the document and not updated it/



9. updating a document in other way

method 1:
```
POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}
```


method 2:
```
POST /products/_update/100
{
  "script": {
        "source": "ctx._source.in_stock = 10"
  }
}
```

method 3:
```
POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock -= params.quantity",
    "params": {
      "quantity": 4
    }
  }
}
```


10. three other way to update a document conditionally

```
POST /products/_update/100
{
    "script": {
        "source": """
            if (ctx._source.in_stock == 0) {
                ctx.op = 'noop';
            }
            ctx._source.in_stock--;
        """
    }
}
```
if the quanity of the document is zero then no opeation is done and else the result will be "updated"


```
POST /products/_update/100
{
    "script": {
        "source": """
            if (ctx._source.in_stock > 0) {
                ctx._source.in_stock--;
            }
        """
    }
}
```
if the quantity of the document is bigger than 0 then the result is "updated" otherwise the result will also be "updated".

```
POST /products/_update/100
{
    "script": {
        "source": """
            if (ctx._source.in_stock <= 1) {
                ctx.op = 'delete';
            }
            ctx._source.in_stock--;
        """
    }
}
```
if the quantity is less than 0 then the result will be "deleted" and the record will be deleted; otherwise the update operation will be done.




11. `upsert` operation. if the document already exists then the document will be updated but the document does not exists the document will be created.

```
POST /products/_update/101
{
  "script": {
    "source": "ctx._source.in_stock++"
  },
  "upsert": {
    "name": "Blender",
    "price": 399,
    "in_stock": 5
  }
}
```


12. replacing a document with new value
```
PUT /products/_doc/100
{
  "name": "Toaster",
  "price": 79,
  "in_stock": 4
}
```



