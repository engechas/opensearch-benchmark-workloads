## Geopoint workload

This workload is based on [PlanetOSM](http://wiki.openstreetmap.org/wiki/Planet.osm) data.

### Example Document

```json
{
  "location": [
    -0.1485188,
    51.5250666
  ]
}
```

### Parameters

This workload allows to overwrite the following parameters with Benchmark 0.8.0+ using `--workload-params`:

* `bulk_size` (default: 5000)
* `bulk_indexing_clients` (default: 8): Number of clients that issue bulk indexing requests.
* `ingest_percentage` (default: 100): A number between 0 and 100 that defines how much of the document corpus should be ingested.
* `conflicts` (default: "random"): Type of id conflicts to simulate. Valid values are: 'sequential' (A document id is replaced with a document id with a sequentially increasing id), 'random' (A document id is replaced with a document id with a random other id).
* `conflict_probability` (default: 25): A number between 0 and 100 that defines the probability of id conflicts. This requires to run the respective test_procedure. Combining ``conflicts=sequential`` and ``conflict-probability=0`` makes Benchmark generate index ids by itself, instead of relying on OpenSearch's `automatic id generation`.
* `on_conflict` (default: "index"): Whether to use an "index" or an "update" action when simulating an id conflict.
* `recency` (default: 0): A number between 0 and 1 that defines whether to bias towards more recent ids when simulating conflicts. See the [Benchmark docs](https://github.com/opensearch-project/OpenSearch-Benchmark/blob/main/DEVELOPER_GUIDE.md) for the full definition of this parameter. This requires to run the respective test_procedure.
* `number_of_replicas` (default: 0)
* `number_of_shards` (default: 5)
* `max_num_segments`: The maximum number of segments to force-merge to.
* `source_enabled` (default: true): A boolean defining whether the `_source` field is stored in the index.
* `index_settings`: A list of index settings. Index settings defined elsewhere (e.g. `number_of_replicas`) need to be overridden explicitly.
* `cluster_health` (default: "green"): The minimum required cluster health.
* `error_level` (default: "non-fatal"): Available for bulk operations only to specify ignore-response-error-level.

### License

Same license as the original data from PlanetOSM: [Open Database License](http://wiki.openstreetmap.org/wiki/Open_Database_License).
