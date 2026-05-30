# GKE Internal Application Load Balancer Flow

![Google Cloud](https://img.shields.io/badge/Google_Cloud-GKE-blue?logo=googlecloud)
![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.29-326CE5?logo=kubernetes&logoColor=white)
![Ingress](https://img.shields.io/badge/Ingress-L7_Load_Balancing-informational)
![Network Endpoint Groups](https://img.shields.io/badge/NEG-Enabled-success)
![Architecture Diagram](https://img.shields.io/badge/Diagram-draw.io-orange)
![License](https://img.shields.io/badge/License-MIT-green)

## Overview

This diagram documents the architecture and traffic behavior of a Google Kubernetes Engine (GKE) Internal Application Load Balancer (ALB).

The flow demonstrates how Kubernetes Ingress resources interact with the GKE Ingress Controller to automatically provision and configure internal Layer 7 HTTPS load balancing using Network Endpoint Groups (NEGs).

---

## Diagram Files

| File | Purpose |
|---|---|
| `gke-internal-alb-flow.drawio` | Editable source diagram |
| `gke-internal-alb-flow.png` | Preview image |
| `gke-internal-alb-flow.svg` | Scalable vector version |

---

## Key Concepts

### Internal Application Load Balancer
- Layer 7 HTTPS load balancing
- Internal-only traffic within the VPC
- Managed through Kubernetes Ingress resources

### GKE Ingress Controller
- Processes Kubernetes Ingress resources
- Creates and configures:
  - Internal Application Load Balancer
  - Backend services
  - URL maps
  - NEGs

### Network Endpoint Groups (NEGs)
- Represent backend pod endpoints
- Required for GKE Internal Application Load Balancers
- Connect load balancer traffic directly to Pods

### Kubernetes Service
- Provides stable networking access to Pods
- Routes traffic internally within the cluster

### Pods
- Backend application workloads
- Receive traffic from the Service layer

---

## Kubernetes Object Management Models

This diagram compares imperative and declarative Kubernetes management workflows using kubectl commands. It illustrates how declarative orchestration uses YAML manifests, desired state reconciliation, and Infrastructure-as-Code principles compared to imperative command execution.

---
## Ingress Annotation Example

```yaml
kubernetes.io/ingress.class: "gce-internal"
```

This annotation tells the GKE Ingress Controller to create an Internal Application Load Balancer instead of an external load balancer.

---

## Architecture Flow

### Control Plane

```text
Ingress Resource (YAML)
        ↓
GKE Ingress Controller
        ↓
Creates/configures:
- Internal Application Load Balancer
- NEG
- Backend Services
```

---

### Data Plane (Traffic Flow)

```text
VPC Client
        ↓
Internal Application Load Balancer
        ↓
NEG
        ↓
Service
        ↓
Pods
```

---

## ACE Recognition Patterns

| Pattern | Meaning |
|---|---|
| `gce` | External Application Load Balancer |
| `gce-internal` | Internal Application Load Balancer |
| Ingress | Layer 7 Load Balancer |
| Service type `LoadBalancer` | Layer 4 Network Load Balancer |
| NEG required | Internal ALB backend requirement |

---

## Operational Notes

- Internal ALBs are VPC-scoped.
- GKE automatically manages NEGs for Ingress-based internal load balancing.
- Internal ALBs provide HTTP(S)-aware traffic routing.
- Traffic routing can be based on:
  - paths
  - hostnames
  - URL maps
  - backend services

---

## Related Concepts

- Kubernetes Ingress
- GKE Networking
- Layer 4 vs Layer 7 Load Balancing
- Network Endpoint Groups
- Kubernetes Services
- Internal HTTPS Load Balancing

---

## Skills Demonstrated

- Google Kubernetes Engine (GKE)
- Internal Application Load Balancing
- Kubernetes Ingress
- Network Endpoint Groups (NEGs)
- Kubernetes Networking
- Layer 7 Load Balancing
- Cloud Architecture Documentation

---

## References

- Kubernetes Ingress Documentation  
  https://kubernetes.io/docs/concepts/services-networking/ingress/

- GKE Internal Load Balancing  
  https://cloud.google.com/kubernetes-engine/docs/how-to/internal-load-balance-ingress

- About Load Balancing in GKE  
  https://cloud.google.com/kubernetes-engine/docs/concepts/ingress

- Network Endpoint Groups (NEGs)  
  https://cloud.google.com/load-balancing/docs/negs

---

## Repository Context

This diagram is part of the `cloud-engineer-learning-path` repository and supports:
- Associate Cloud Engineer (ACE) preparation
- Kubernetes networking recognition patterns
- GKE operational architecture documentation
- Cloud infrastructure learning
