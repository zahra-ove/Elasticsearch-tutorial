1. nodes could have roles. all available roles in Elasticsearch are:
    - master  ==> act as master node
    - data    ==> act as a node to store data and responce to search queries
    - ingest  ==> enables a node to run ingest pipelines
    - ml      ==> identifies a node as machine learning node
    - coordination  ==> refers to distribution of queries and the aggregation of results
    - voting only ==> rarely used -> will participate in the voting for a new master node


*note: `ingesting` refers to adding a document to an index