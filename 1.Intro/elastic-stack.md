### Elastic stack:
    - Kibana: analytics and visualization platform. some kine of `web api` which sends queries (rest api) to Elasticsearch
    - Logstash: process logs from applications and sends them to elasticsearch. it's a `data processing pipeline`
    - X-Pack: pack of functionality that adds additional features to Elasticsearch and Kibana
    - Beats: some kind of data shipper which collects data and sends them to elasticsearch

**ELK** : Elasticsearch + Logstash + Kibana

- Kibana stores its configs in Elasticsearch