1. Mapping defines the structure of the documents (e.g. fields and their data types). also used to configure how values are indexed. similar to table's schema in RDBMS.

2. In Elasticsearch there are two approaches for mapping:
   - explicit mapping (we define field mapping ourselves)
   - dynamic mapping (Elasticsearch defines field mappings for us)



![img1](./../images/mapping.png)




3. it is possible to retieve an index as mapping to check the mapping of the index. for this we use `Mapping API`

shows mapping of "reviews" index
```json
GET /reviews/_mapping
```

shows the mapping of "reviews" index and field "content"
```json
GET /reviews/_mapping/field/content
```


```json
PUT /reviews
{
  "mappings": {
    "properties": {
      "rating": {"type": "float"},
      "content": {"type": "text"},  
      "product_id": {"type": "integer"},
      "author": {
        "properties": {
          "first_name": {"type": "text"},
          "last_name": {"type": "text"},
          "email": {"type": "keyword"}
        }
      }
    }
  }
}
```


another way for defining mapping for an index is to use dot notation:

```json
PUT /reviews
{
  "mappings": {
    "properties": {
      "rating": {"type": "float"},
      "content": {"type": "text"},  
      "product_id": {"type": "integer"},
      "author.first_name": {"type": "text"},
      "author.last_name": {"type": "text"},
      "author.email": {"type": "keyword"},
    }
  }
}
```


4. it is possible to add another mapping to existing index.\
   for example suppose in "reviews" indexl we want to add "created_at"\
   field to this index with mapping:

```json
PUT /reviews/_mapping
{
   "properties": {
      "created_at": {
         "type": "date"
      }
   }
}
```


and now we can check the mapping for "reviews" index:

```json
GET /reviews/_mapping
```



