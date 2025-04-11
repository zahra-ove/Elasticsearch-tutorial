1. Values for a text field are analyzed, and the results are stored in an inverted index.

2. Each field has its own dedicated inverted index.

3. An inverted index is a mapping between terms and the documents that contain them.

4. Terms are sorted alphabetically for optimized search performance.

5. Inverted indices are created and maintained by Apache Lucene (the underlying library), not Elasticsearch itself.


**note**: Lucene Dependency: Elasticsearch relies on Lucene for low-level indexing/search operations.


6. Fast Searches: Inverted indices enable lightning-fast full-text searches.

7. Additional Data: Inverted indices store more than just term mappings:

Includes data for relevance scoring (e.g., TF-IDF, BM25 - covered later).

8. Beyond Inverted Indices: Elasticsearch (via Apache Lucene) uses other specialized data structures:

**note**: BKD Trees: For efficient indexing of:
 - Numeric values
 - Dates
 - Geospatial data (geo points/shapes)




