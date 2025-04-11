1. generally, Elasticsearch field mappings cannot be changed
2. a few mapping parameters can be updated for existing mappings. for example it is possible to add "ignore_above" parameter to any existing field and update it:


```json
PUT /reviews/mapping
{
  "properties": {
    "product.id": {
      "type": "keyword"
    },
    "author": {
      "properties": {
        "email": {
          "type": "keyword",
          "ignore_above": 256
        }
      }
    }
  }
}
```


response:

```json
{
  "acknowledged": true
}
```



### Limitations for updating mappings

3. Even for an empty index, we cannot update a mapping

4. Field mappings also cannot be removed

5. Just leave out the field when indexing documents

6. The Update By Query API can be used to reclaim disk space

7. The solution is to reindex documents into a new index (sorry 😊)


*note*: when a field is used for full text search -> the data type should be "text".\
when a field is used for filtering -> the data type should be "keyword"\




8. for getting mapping of an index:

```json
GET /reviews/_mappings
```





