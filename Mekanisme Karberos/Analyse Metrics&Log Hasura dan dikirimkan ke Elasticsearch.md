### HIT
```
 "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "_hJAm5MBatu-e5CDz5v_",
  "_version": 1,
  "_source": {
    "@timestamp": "2024-12-06T09:10:40.290802493Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_cache_request_count": 0,
    "host": {
      "hostname": "hasura-nino-6f5d5f4768-dv965:8080",
      "name": "hasura-nino-6f5d5f4768-dv965:8080"
    },
    "service": {
      "name": "hasura"
    },
    "status": "hit"
  },
  "fields": {
    "@timestamp": [
      "2024-12-06T09:10:40.290Z"
    ],
    "service.name": [
      "hasura"
    ],
    "data_stream.namespace": [
      "default"
    ],
    "data_stream.dataset": [
      "generic"
    ],
    "host.hostname": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "host.name": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "data_stream.type": [
      "metrics"
    ],
    "hasura_cache_request_count": [
      0
    ],
    "status": [
      "hit"
    ]
  }
}

```

### FAILED

```
{
  "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "TC05qZMBatu-e5CD1agx",
  "_version": 1,
  "_source": {
    "@timestamp": "2024-12-09T02:17:41.986251451Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_cron_events_invocation_total": 0,
    "hasura_cron_events_processed_total": 0,
    "hasura_oneoff_events_invocation_total": 0,
    "hasura_oneoff_events_processed_total": 0,
    "host": {
      "hostname": "hasura-nino-6f5d5f4768-dv965:8080",
      "name": "hasura-nino-6f5d5f4768-dv965:8080"
    },
    "service": {
      "name": "hasura"
    },
    "status": "failed"
  },
  "fields": {
    "hasura_cron_events_processed_total": [
      0
    ],
    "@timestamp": [
      "2024-12-09T02:17:41.986Z"
    ],
    "service.name": [
      "hasura"
    ],
    "data_stream.namespace": [
      "default"
    ],
    "data_stream.dataset": [
      "generic"
    ],
    "hasura_cron_events_invocation_total": [
      0
    ],
    "hasura_oneoff_events_processed_total": [
      0
    ],
    "host.hostname": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "host.name": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "data_stream.type": [
      "metrics"
    ],
    "hasura_oneoff_events_invocation_total": [
      0
    ],
    "status": [
      "failed"
    ]
  }
}
```
### SUCCESS
```
{
  "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "AC05qZMBatu-e5CD1agx",
  "_version": 1,
  "_source": {
    "@timestamp": "2024-12-09T02:17:26.983945757Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_graphql_requests_total": 8,
    "host": {
      "hostname": "hasura-nino-6f5d5f4768-dv965:8080",
      "name": "hasura-nino-6f5d5f4768-dv965:8080"
    },
    "operation_type": "query",
    "parameterized_query_hash": "7116865cef017c3b09e5c9271b0e182a6dcf4c01",
    "response_status": "success",
    "service": {
      "name": "hasura"
    }
  },
  "fields": {
    "parameterized_query_hash": [
      "7116865cef017c3b09e5c9271b0e182a6dcf4c01"
    ],
    "@timestamp": [
      "2024-12-09T02:17:26.983Z"
    ],
    "operation_type": [
      "query"
    ],
    "response_status": [
      "success"
    ],
    "service.name": [
      "hasura"
    ],
    "data_stream.namespace": [
      "default"
    ],
    "data_stream.dataset": [
      "generic"
    ],
    "host.hostname": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "host.name": [
      "hasura-nino-6f5d5f4768-dv965:8080"
    ],
    "data_stream.type": [
      "metrics"
    ],
    "hasura_graphql_requests_total": [
      8
    ]
  }
}
```

