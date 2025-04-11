### Reindexing documents with reindex API

1. changing how documents are mapped, usaully requires reindexing documents.
   - first step is to define new index and define a new mapping 

2. to get mapping of an existing index use:

```json
GET /reviews/_mappings
```

3. there is an API named `Reindex API`. this API does the heavy lifting of moving documents from one index to another so that we don't have to.


4. how to use reindex API

```json
POST /_reindex
{
    "source": {
        "index": "reviews"
    },
    "dest": {
        "index": "reviews_new"
    },
}
```


5. it is possible to change data type while using reindex api:

```json
POST /_reindex
{
  "source": {
    "index": "reviews"
  },
  "dest": {
    "index": "reviews_new"
  },
  "script": {
    "source": """
      if (ctx._source.product_id != null) {
        ctx._source.product_id = ctx._source.product_id.toString();
      }
    """
  }
}
```



this query convert the "product_id" field to "string" if the "product_id" field has value in the source index.


6. it is possible to just reindex documents from source index which match the query. e.g:

```json
POST /_reindex
{
  "source": {
    "index": "reviews",
    "query": {
      "match_all": {}
    }
  },
  "dest": {
    "index": "reviews_new"
  }
}
```

another example:


```json
POST /_reindex
{
  "source": {
    "index": "reviews",
    "query": {
      "range": {
        "rating": {
          "gte": 4.0
        }
      }
    }
  },
  "dest": {
    "index": "reviews_new"
  }
}
```


7. if we want to reindex just specific fields from source index to destination index:

```json
POST /_reindex
{
  "source": {
    "index": "reviews",
    "_source": ["content", "created_at", "rating"]
  },
  "dest": {
    "index": "reviews_new"
  }
}
```


8. another way:

```json
POST /_reindex
{
  "source": {
    "index": "reviews"
  },
  "dest": {
    "index": "reviews_new"
  },
  "script": {
    "source": """
      if (ctx._source.rating < 4.0) {
        ctx.op = "noop";  # Can also be set to "delete"
      }
    """
  }
}
```




