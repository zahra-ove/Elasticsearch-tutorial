### How missing fields are handled in Elasticsearch

1. Elasticsearch will validate field values against any mapping that might exists, but it won't reject documents that leave fields out.

2. you can leave out fields even if a mapping exists for it, so adding a field mapping does not make the field required.