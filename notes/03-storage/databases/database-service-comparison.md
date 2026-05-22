# GCP Database Recognition Patterns

| Service | Type | Best For | Recognition Pattern |
|---|---|---|---|
| Cloud SQL | Relational DB | Traditional apps | Managed MySQL/PostgreSQL/SQL Server |
| Bigtable | NoSQL Wide-Column | Massive low-latency workloads | Time-series / IoT / billions of rows |
| BigQuery | Analytics Warehouse | Analytics & reporting | SQL analytics on huge datasets |
| Spanner | Global Relational DB | Horizontal relational scaling | Global consistency + relational semantics |

## Recognition Framework
| Technology                            | Think                           |
| ------------------------------------- | ------------------------------- |
| Compute Engine                        | Virtual machines                |
| Managed Instance Groups               | VM autoscaling                  |
| Cloud Run                             | Serverless containers           |
| GKE                                   | Kubernetes containers           |
| Cloud Functions / Cloud Run functions | Event-driven functions/snippets |
| Spanner                               | Global relational DB            |
| Bigtable                              | NoSQL massive scale             |
| BigQuery                              | Analytics warehouse             |
