gcloud Command Recognition

    gcloud functions deploy → deploying event-driven serverless code.
    gcloud run deploy → deploying containers.
    gcloud sql instances create → creating managed databases

```bash
gcloud run deploy inventory-service \
  --source . \
  --region us-central1 \
  --allow-unauthenticated
```
  ---

# ☁️ Cloud Run

## Think:

- Serverless Containers

## Use when:

- deploying Docker containers
- custom packages/libs needed
- scale-to-zero desired
- HTTP services/APIs
- no infrastructure management

## ACE keywords:

- “Serverless container management”
- “Scales based on incoming requests”
- “Scale to zero”
- “Replicated across zones”

---

## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads
