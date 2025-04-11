### Defining field aliases

1. Field names can be changed when reindexing documents
◦ Probably not worth it for lots of documents

2. An alternative is to use field aliases
◦ Doesn’t require documents to be reindexed
◦ Let’s add one pointing from comment to content
◦ Aliases can be used within queries
◦ Aliases are defined with a field mapping


```json
PUT /reviews/_mapping
{
  "properties": {
    "coment": {
      "type": "alias",
      "path": "content"
    }
  }
}
```



### Updating field aliases

3. Field aliases can actually be updated
    - Only its target field, though

4. Simply perform a mapping update with a new path value
    -Possible because aliases don’t affect indexing

It’s a query-level construct


5. smilar to field aliases, Elasticsearch also support index aliases.
6. 