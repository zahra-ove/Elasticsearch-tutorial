### Routing
1. default routing formula of Elasticsearch:

```
shared_num = hash(_routing) % num_primary_shards
```

2. Routing is the process of resolving a shard for a document.
3. A formula is used when indexing, retrieving, and updating documents.
4. Routing may be customized (advanced).
5. The default routing strategy distributes documents evenly.
6. One of the reasons why an index’s shards cannot be changed is that the routing formula would then yield different results.



### Reading Flow
 - A read request is received and handled by a coordinating node
 - Routing is used to resolve the document’s replication group
 - ARS is used to send the query to the best available shard
 - ARS is short for Adaptive Replica Selection
 - ARS helps reduce query response times
 - ARS is essentially an intelligent load balancer
 - The coordinating node collects the response and sends it to the client


### Writing Flow
1. Write operations are sent to primary shards
2. The primary shard forwards the operation to its replica shards
3. Primary terms and sequence numbers are used to recover from failures
4. Global and local checkpoints help speed up the recovery process
5. Primary terms and sequence numbers are available within responses