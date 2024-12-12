### Modifications from upstream([langfuse/langfuse-k8s](https://github.com/langfuse/langfuse-k8s))

- set k8s Gateway, GCPGatewayPolicy, HTTPRoute for internal access through [langfuse-v3.getliner.com](https://langfuse-v3.getliner.com/)
- setup connection parameters for Cloud SQL postgres, Memorystore redis, GCS
- deployed ClickHouse on k8s with ClickHouse Keeper(`keeper.enabled=true`) instead of default Zookeeper with custom storageclass `standard-rwo-retain`(pd-balanced(SSD) with `reclaimPolicy: Retain`) along with internal access through http://langfuse-clickhouse.getliner.com:80

### Upgrading helm chart

1. Check k8s context set to `linerva` cluster (`gcloud container clusters get-credentials linerva --region=us-central1-c`)
2. `helm upgrade -n langfuse-v3 langfuse ./charts/langfuse`
