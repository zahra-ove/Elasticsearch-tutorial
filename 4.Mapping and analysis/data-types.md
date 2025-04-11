# Elasticsearch Mapping Data Types

Elasticsearch provides a rich set of data types for defining how your data should be indexed and stored. Here's a comprehensive list of all data types used for mapping in Elasticsearch:

## Core Data Types

### 1. Text Types
- **`text`**: Full-text searchable content, analyzed by the analyzer
- **`keyword`**: Exact-value strings for filtering, sorting, and aggregations
- **`wildcard`** (since 7.9): Optimized for wildcard queries on non-analyzed strings

### 2. Numeric Types
- **`long`**: Signed 64-bit integer (-2⁶³ to 2⁶³-1)
- **`integer`**: Signed 32-bit integer (-2³¹ to 2³¹-1)
- **`short`**: Signed 16-bit integer (-32,768 to 32,767)
- **`byte`**: Signed 8-bit integer (-128 to 127)
- **`double`**: 64-bit double-precision floating point
- **`float`**: 32-bit single-precision floating point
- **`half_float`**: 16-bit half-precision floating point
- **`scaled_float`**: Floating point backed by a long, scaled by a fixed factor
- **`unsigned_long`** (since 7.10): Unsigned 64-bit integer (0 to 2⁶⁴-1)

### 3. Date Type
- **`date`**: Can store dates as:
  - Formatted strings (e.g., "2023-01-01")
  - Long numbers (milliseconds since epoch)
  - Integer numbers (seconds since epoch)

### 4. Boolean Type
- **`boolean`**: true/false values

### 5. Binary Type
- **`binary`**: Base64-encoded binary data

### 6. Range Types
- **`integer_range`**
- **`float_range`**
- **`long_range`**
- **`double_range`**
- **`date_range`**
- **`ip_range`**

## Complex Data Types

### 1. Object Type
- **`object`**: JSON object (nested documents)

### 2. Nested Type
- **`nested`**: Arrays of objects where each object should be queried independently

### 3. Flattened Type
- **`flattened`**: Entire object mapped as a single field (for unknown structures)

## Geo Data Types

### 1. Geo-Point
- **`geo_point`**: Latitude/longitude points

### 2. Geo-Shape
- **`geo_shape`**: Complex shapes like polygons

## Specialized Types

### 1. IP Type
- **`ip`**: IPv4 and IPv6 addresses

### 2. Completion Suggester
- **`completion`**: For autocomplete suggestions

### 3. Token Count
- **`token_count`**: Count of tokens in a string

### 4. Percolator
- **`percolator`**: Stores query syntax for percolation

### 5. Alias
- **`alias`**: Defines an alternate name for a field

### 6. Join Type
- **`join`**: Creates parent/child relationships between documents

### 7. Rank Feature
- **`rank_feature`**: Numeric feature that boosts relevance scores
- **`rank_features`**: Multiple numeric features for boosting

### 8. Dense Vector
- **`dense_vector`**: Array of float values for vector similarity search
- **`sparse_vector`** (deprecated in 7.0): For sparse vectors

### 9. Search-as-You-Type
- **`search_as_you_type`**: Optimized for incremental search

### 10. Histogram
- **`histogram`**: Pre-aggregated numerical values for percentiles

### 11. Constant Keyword
- **`constant_keyword`**: Keyword that always has the same value

### 12. Version
- **`version`**: Software version numbers (e.g., "1.2.3")

## Multi-Field Mappings

You can define multiple data types for a single field:
```json
{
  "mappings": {
    "properties": {
      "city": {
        "type": "text",
        "fields": {
          "raw": {
            "type": "keyword"
          }
        }
      }
    }
  }
}
```




