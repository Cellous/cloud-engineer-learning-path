# Google Cloud Observability

## Overview

Google Cloud Observability provides integrated monitoring, logging,
diagnostics, tracing, and application-performance tools for cloud systems.

It can dynamically discover cloud resources and application services
across environments such as Google Cloud and AWS.

![Google Cloud Observability](diagrams/google-cloud-observability.png)

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

## Cloud Monitoring

Cloud Monitoring provides visibility into platform, system, and
application performance.

It can dynamically configure monitoring after resources are deployed
and provides intelligent defaults for common monitoring tasks.

Monitoring data can include:

- Metrics
- Events
- Metadata

That data can then be used to build:

- Dashboards
- Charts
- Alerts
- Uptime checks
- Health checks

---

### Metrics Scopes

A metrics scope is the root entity that holds monitoring and
configuration information for monitored projects.

A metrics scope can include:

- Custom dashboards
- Alerting policies
- Uptime checks
- Notification channels
- Group definitions

A single metrics scope can monitor multiple Google Cloud projects.

Conceptually:

```text
                  Metrics Scope
                       |
        +--------------+--------------+
        |              |              |
   Project A        Project B      Project C
                                      |
                               AWS Connector
                                      |
                                AWS Account
```
![Single Pane of Glass](./diagrams/single-pane-of-glass.png)


![Metrics Scope Architecture](diagrams/metrics-scope-architecture.png)

---

### Dashboards

Cloud Monitoring dashboards can visualize metrics such as:

- CPU utilization
- Network traffic
- Packets sent
- Packets received
- Dropped packets

Charts can use:

- Filters
- Groups
- Aggregations

Dashboards provide visual operational awareness, but they require
someone to be looking at them.

---

### Alerting Policies

Alerting policies automatically notify operators when defined
conditions are met.

Conceptually:
```text
Metric
  ↓
Condition
  ↓
Threshold
  ↓
Duration
  ↓
Alert
  ↓
Notification channel
```
Example:

![Alerting Policies](diagrams/alerting-policies.png)

#### Alerting Best Practices
- Alert on symptoms rather than only causes
- Use multiple notification channels
- Make alerts actionable
- Include troubleshooting guidance
- Avoid unnecessary alert noise

![Alert Policy Flow](diagrams/alert-policy-flow.png)
```text
Dashboard = passive visibility

Alert = active notification
```
---

## Uptime Checks

Uptime checks test whether public services are reachable and responding.

They can check services from multiple locations and can be configured for:

- HTTP
- HTTPS
- TCP

Examples of monitored resources include:

- Compute Engine instances
- App Engine applications
- Public host URLs
- AWS instances or load balancers

An uptime check can be associated with an alerting policy.

Conceptually:

```text
Public Service
     ↓
Uptime Check
     ↓
Multiple Global Locations
     ↓
Availability / Latency
     ↓
Alerting Policy
     ↓
Notification
```
The course example checks a service every minute with a 10-second timeout.
A failed response within the timeout is treated as an uptime failure.

---

## Ops Agent
The Ops Agent collects telemetry from inside Compute Engine virtual machines.

This is important because some internal VM metrics cannot be observed directly
from the hypervisor.

The Ops Agent can collect:

- Host metrics
- Process metrics
- Application metrics
- Metrics from supported third-party applications

Conceptually:
```text
Compute Engine VM
      ↓
   Ops Agent
      ↓
Cloud Monitoring API
      ↓
+------------------------------+
| Dashboards                   |
| Uptime checks                |
| Alerting policies            |
| Notifications                |
+------------------------------+
```
> The Ops Agent collects system and application telemetry from
> Compute Engine VM instances and sends it to Cloud Monitoring.

---
![Ops Agent Flow](diagrams/ops-agent-flow.png)

![Monitoring Pipeline](diagrams/monitoring-pipeline.png)


---
## Custom Metrics

If built-in Monitoring metrics do not represent the condition that matters to
an application, custom metrics can be created.

Example:
```text
Game Server
Capacity = 50 users
```
Instead of estimating load using:
```text
CPU utilization
Network traffic
```
the application can publish:
```text
current_users
```
directly as a custom metric.

This provides a more meaningful application-level signal.

Conceptually:
```text
Application
    ↓
Custom Metric
    ↓
Time Series
    ↓
Cloud Monitoring
    ↓
Dashboard / Alert / Autoscaling
```

### Custom Metric to Time Series

This diagram shows how an application-defined metric becomes time-series data in Cloud Monitoring and can then drive dashboards, alerts, or autoscaling.

![Custom Metric to Time Series](diagrams/custom-metric.png)

---

## Autoscaling with Metrics

Managed instance groups can autoscale based on monitoring metrics.

The core idea is:
```text
Metric
  ↓
Utilization Target
  ↓
Compare Current Value
  ↓
Scale Out / Scale In
```
If the metric is produced by each VM in the managed instance group:
```text
VM metrics
   ↓
Average metric value across VMs
   ↓
Compare with utilization target
```
If the metric represents the entire managed instance group:
```text
Group-wide metric
   ↓
Compare directly with utilization target
```
If the metric has multiple values:
```text
Metric
  ↓
Filter
  ↓
Select individual value
  ↓
Autoscaling decision
```
### Metric-Based Autoscaling Flow

![Metric-Based Autoscaling](diagrams/autoscaling-with-metrics.png)


## ACE Recognition
```text
Uptime check
→ Is the service reachable?

Ops Agent
→ What is happening inside the VM?

Custom metric
→ What application-specific value do I want to measure?

Alerting policy
→ When should someone be notified?

Autoscaling metric
→ When should capacity change automatically?
```

## Cloud Logging

Cloud Logging is a fully managed service for storing, searching,
analyzing, monitoring, and alerting on log data from Google Cloud
and AWS environments.

Cloud Logging can collect:

- Platform logs
- System logs
- Application logs

Core capabilities include:

- Reading and writing log entries
- Searching and filtering logs
- Logs Explorer
- Log-based metrics
- Alerting on log events
- Routing logs to other Google Cloud services

### Log Routing

Logs can be routed to different destinations depending on the use case:

![Cloud Logging Routing Flow](diagrams/cloud-logging-routing-flow.png)

Typical destinations include:

- Cloud Storage for long-term retention
- BigQuery for SQL analysis
- Pub/Sub for streaming and automation


```text
Cloud Logging
     |
     +--> Cloud Storage
     |      Long-term storage
     |
     +--> BigQuery
     |      SQL analysis / reporting
     |
     +--> Pub/Sub
            Streaming / automation
```

### BigQuery Log Analysis

Routing logs to BigQuery enables large-scale SQL analysis of
operational and network data.

![BigQuery Log Analysis Flow](diagrams/bigquery-log-analysis-flow.png)

Example use cases include:

- Traffic analysis
- Capacity forecasting
- Network cost optimization
- Incident investigation
- Network forensics
- Identifying high-traffic IP addresses

---

## Error Reporting

Error Reporting is a Google Cloud Observability service that counts,
analyzes, and aggregates errors from running cloud services.

It provides a centralized interface where errors can be:

- Grouped
- Sorted
- Filtered
- Reviewed
- Monitored with notifications

Real-time notifications can be configured when new errors are detected.

### Supported Services

The course lists support for:

- App Engine
- Apps Script
- Compute Engine
- Cloud Run
- Cloud Run functions
- Google Kubernetes Engine (GKE)
- Amazon EC2

### Supported Languages

The exception stack trace parser can process:

- Go
- Java
- .NET
- Node.js
- PHP
- Python
- Ruby

### Conceptual Flow

```text
Application / Cloud Service
          ↓
      Exception
          ↓
    Error Reporting
          ↓
 Count / Analyze / Aggregate
          ↓
 Centralized Error Dashboard
          ↓
 Filter / Investigate / Notify
```
## ACE Recognition

Repeated application exceptions
→ Error Reporting

Need to group similar failures
→ Error Reporting

Need notification when a new application error appears
→ Error Reporting

Need raw log searching
→ Cloud Logging

## Logging vs Error Reporting

| Need                                  | Service         |
| ------------------------------------- | --------------- |
| Search raw log entries                | Cloud Logging   |
| Filter application/system logs        | Cloud Logging   |
| Group repeated application exceptions | Error Reporting |
| Track occurrence of recurring errors  | Error Reporting |
| Notify when new errors appear         | Error Reporting |


---

