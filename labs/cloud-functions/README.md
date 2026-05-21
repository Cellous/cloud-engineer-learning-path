# ☁️ Cloud Run Functions

## Think:

- Serverless Event Functions

## Use when:

- reacting to events
- Pub/Sub triggers
- Cloud Storage events
- lightweight ETL
- small functions/snippets

## ACE keywords:

- “Functions trigger when an event occurs”
- “Event based”
- “Scales by number of events”
---

## gcloud trigger question:
```
gcloud functions deploy ...
--trigger-event google.storage.object.finalize
```
That is:

- event-driven
- stateless
- function execution

NOT container orchestration.

---
## gcloud Command Recognition

- gcloud functions deploy → deploying event-driven serverless code.
- gcloud run deploy → deploying containers.
- gcloud sql instances create → creating managed databases

```bash
gcloud functions deploy trans_mg_function \
  --runtime python39 \
  --trigger-topic truck_data
```
---

- event-driven architecture
- Pub/Sub triggers
- serverless functions  

---

## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads
