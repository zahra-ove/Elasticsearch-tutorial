1. an Elasticsearch node will always be part of a cluster, even if there are no other nodes.

2. an index is a collection of documents
3. a cluster is a collection of nodes
4. data is stored as documents, which are json objects.
5. documents are grouped together with indices.


6. when using the console tool in Kibana, Kibana automatically prepends request paths with the Elasticsearch cluster's network address.

7. check cluster health: 
    `GET /_cluster/health`

**note: 
    - `_cluster`: specifies the API path
    - `health`: specifies the command

**note: in Elasticsearch APIs start with underscore by convention.

**note: the leading forward slash is optional in the console tool, and if not added Kibana will automatically include it before sending http request.


8. i$t is possible to change name of clusters in this path:
   `$ES_HOME > config > elasticsearch.yml` 

9. `CAT` api outputs the result in human readable format. (CAT === Compact and Aligned Text)\

    - `GET /_cat/indices/?v`   => list of all indices
    - `GET /_cat/shards?v`     => list of all shards

**note: `?v`  => make output verbos
