# Cloud Run Functions Deployment Lab

## Objective

Deploy an event-driven Cloud Run function triggered by Pub/Sub.

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
