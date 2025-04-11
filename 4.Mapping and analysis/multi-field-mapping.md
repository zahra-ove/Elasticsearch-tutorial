1. text fields are used for performing full-text searches that do not require exact matches.
2. when doing exact matches on text values, we should query a "keyword" mapping.


3. in some situations it is needed to query a field in a different ways. that's why we define `multiple mapping` for a field.


4. keyword mapping --> for aggregations and sorting
5. text mapping --> for full-text search

6. in the below query, we defined two mapping for "ingredients" field:

```json
PUT /multi_field_test
{
  "mappings": {
    "properties": {
      "description": {
        "type": "text"
      },
      "ingredients": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword"
          }
        }
      }
    }
  }
}
```

