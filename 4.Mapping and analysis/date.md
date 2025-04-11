1. Dates are specified in one of three ways:
    - Specially formatted strings (defaults to ISO 8601 — can use custom formats)
    - Milliseconds since the epoch
    - Seconds since the epoch

2. Dates are stored as long values internally (converted to UTC first)
  - The same conversion happens for search queries

**Don’t provide UNIX timestamps for default date fields**

3. different type of date handling in Elasticsearch:


- for "created_at" field: `T` in the ""2015-04-15T13:07:412"" means `time`
- 
```json
PUT /reviews/_doc/3
{
  "rating": 3.5,
  "content": "Could be better",
  "product_id": 123,
  "created_at": "2015-04-15T13:07:412",
  "author": {
    "first_name": "Spencer",
    "last_name": "Pearson",
    "email": "spenzen@example.com"
  }
}
```


- note "+1:00" in the "2015-01-28T09:21:51+01:00" which means 1hour after UTC
```json
PUT /reviews/_doc/4
{
  "rating": 5.0,
  "content": "Incredible!",
  "product_id": 123,
  "created_at": "2015-01-28T09:21:51+01:00",
  "author": {
    "first_name": "Adam",
    "last_name": "Jones",
    "email": "adam.jones@example.com"
  }
}
```

- if unit timestamp is used please not to multiply it by 1000 beacuase elasticseach consider it based on milisecond.\

(epoch time (unit timestamp) is based on second)

```json
PUT /reviews/_doc/5
{
  "rating": 4.5,
  "content": "Very useful",
  "product_id": 123,
  "created_at": "1456011284000",
  "author": {
    "first_name": "Taylor",
    "last_name": "West",
    "email": "twest@example.com"
  }
}
```