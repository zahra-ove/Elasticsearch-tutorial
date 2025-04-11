### The Bulk API 
allows you to perform multiple index, create, delete, and update operations in a single request, which is much more efficient than sending individual requests for each operation.



### Basic Structure
A bulk request consists of newline-delimited JSON (NDJSON) with alternating action/metadata lines and (optional) source lines:


```
action_and_metadata\n
optional_source\n
action_and_metadata\n
optional_source\n
...
```


### Supported Operations

1. Index
Adds a document, replacing if it already exists

```
{ "index" : { "_index" : "test", "_id" : "1" } }
{ "field1" : "value1" }
```


2. Create
Adds a document only if it doesn't exist

```
{ "create" : { "_index" : "test", "_id" : "1" } }
{ "field1" : "value1" }
```


3. Delete
Removes a document

```
{ "delete" : { "_index" : "test", "_id" : "2" } }
```

4. Update
Updates a document (partial update)

```
{ "update" : { "_index" : "test", "_id" : "1" } }
{ "doc" : { "field2" : "value2" } }
```


