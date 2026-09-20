# Google Cloud Observability

## Overview

Google Cloud Observability provides integrated monitoring, logging,
diagnostics, tracing, and application-performance tools for cloud systems.

It can dynamically discover cloud resources and application services
across environments such as Google Cloud and AWS.

![Google Cloud Observability](diagram/google-cloud-observability.png)

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
The Ops Agent is the primary Google Cloud agent for collecting telemetry from
Compute Engine workloads.

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

If the metric represents the entire managed instance group:

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

---

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
