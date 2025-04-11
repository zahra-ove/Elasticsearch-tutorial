
1. `sharding` is a way to divide indices into smaller pieces; each piece is referred to as shard.
2. sharding is done at index level
3. the main purpose of sharding: to harizontally scale the data volume
4. each shard is needed to place on a single node
5. a shard has no predefined size; it grows as documents are added to it. a shard may store up to about two billion documents.

6. The purpose of sharding:
    - mainly to be able to store more documents
    - to easier fit large indices onto nodes
    - improve performance: parallelization of queries increases the throughput of an index 

7. indices in Elasticsearch version < 7.0.0 were created with five shards/ this often led to over sharding, and it was not possible to change the number of shards once an index had been created.
8. since Elasticsearch version 7.0.0, an index contains a single shard by default
9. since Elasticsearch version 7.0.0 for increasing number of shards, there is a `Split API` and it is possile to decrease number of shards with `Shrink API`.