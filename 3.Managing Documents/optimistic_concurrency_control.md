1. Sending write requests to Elasticsearch concurrently may overwrite changes made by other concurrent processes

2. Traditionally, the _version field was used to prevent this

3. Today, we use the _primary_term and _seq_no fields

4. Elasticsearch will reject a write operation if it contains the wrong primary term or sequence number. This should be handled at the application level