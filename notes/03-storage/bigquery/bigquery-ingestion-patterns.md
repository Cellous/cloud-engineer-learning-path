# BigQuery Ingestion Patterns

## Batch Loading
- Best for slowly changing data
- Cheapest ingestion method
- Uses Cloud Storage + Data Transfer Service

## Streaming
- Best for real-time analytics
- Uses Streaming API
- Costs associated with streaming inserts

## Recognition Patterns
- "Hourly uploads" → Batch
- "Real-time events" → Streaming
- "Minimize cost" → Batch
