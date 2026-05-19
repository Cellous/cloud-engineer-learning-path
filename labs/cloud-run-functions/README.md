# Cloud Run Functions Deployment Lab

## Objective

Deploy an event-driven Cloud Run function triggered by Pub/Sub.

---
gcloud Command Recognition

    gcloud functions deploy → deploying event-driven serverless code.
    gcloud run deploy → deploying containers.
    gcloud sql instances create → creating managed databases

## Deployment Command

```bash
gcloud functions deploy trans_mg_function \
--runtime python39 \
--trigger-topic truck_data
```

## Key Concepts

- Serverless compute
- Event-driven architecture
- Pub/Sub integration
- Python runtime deployment

---

## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads
