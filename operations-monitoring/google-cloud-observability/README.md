# Google Cloud Observability

## Overview

Google Cloud Observability provides integrated monitoring, logging,
diagnostics, tracing, and application-performance tools for cloud systems.

It can dynamically discover cloud resources and application services
across environments such as Google Cloud and AWS.

## Core Services

| Service | Purpose |
|---|---|
| Cloud Monitoring | Metrics, dashboards, uptime, and alerts |
| Cloud Logging | Centralized log collection and analysis |
| Error Reporting | Detect and group application errors |
| Cloud Trace | Analyze request latency and distributed traces |
| Cloud Profiler | Analyze CPU and memory usage in applications |

## Why Observability Matters

Observability helps cloud engineers:

- Detect failures
- Investigate incidents
- Monitor resource health
- Analyze application performance
- Diagnose latency
- Review logs
- Establish operational visibility

## ACE Recognition Note

Think:

Metrics → Monitoring  
Logs → Logging  
Exceptions → Error Reporting  
Request latency → Trace  
CPU / memory hot spots → Profiler

```text
Google Cloud Observability
        │
        ├── Monitoring
        ├── Logging
        ├── Error Reporting
        ├── Trace
        └── Profiler
```

Important operational concept is:

```text
Monitoring → What is happening?
Logging → What happened?
Error Reporting → What is failing?
Trace → Where is the request slowing down?
Profiler → Where is the application consuming resources?
```

