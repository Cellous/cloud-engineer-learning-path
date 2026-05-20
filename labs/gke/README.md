# Google Kubernetes Engine (GKE)

## Overview

- Google Kubernetes Engine (GKE) is a managed Kubernetes platform used to deploy and manage containerized applications.
- You use Kubernetes APIs to deploy containers on a set of nodes called a cluster.
  
Kubernetes clusters consist of:
- control plane
- worker nodes
- pods
- networking

User
  ↓
Kubernetes API
  ↓
Control Plane
  ↓
Nodes (VMs)
  ↓
Containers / Pods

## Nodes are VMs (in GKE they're Compute Engine instances)

### GKE is built ON TOP OF Compute Engine.
- Compute Engine → Infrastructure Layer
- GKE → Kubernetes Management Layer
- Pods/Containers → Application Layer
---

## kubectl Recognition

| Command | Purpose |
|---|---|
| kubectl get pods | View running pods |
| kubectl get nodes | View cluster nodes |
| kubectl apply -f | Deploy configuration |
| kubectl describe pod | Detailed pod information |
| kubectl logs | View container logs |
| kubectl delete pod | Remove pod |

---

| Requirement                    | Usually Means   |
| ------------------------------ | --------------- |
| More flexibility/customization | Standard GKE    |
| Less operational overhead      | Autopilot       |
| High availability              | Regional        |
| Internal-only access           | Private cluster |
| Fast/simple deployment         | Cloud Run       |

---

## Key ACE Concepts

### Standard Mode
- Full cluster control
- Manage node pools
- Custom machine images
- Flexible architecture

### Autopilot Mode
- Google manages infrastructure
- Pod-based billing
- Less operational overhead
- Less customization

### Zonal Cluster
- Single control plane zone
- Lower availability
- Lower cost

### Regional Cluster
- Multi-zone control planes
- Higher availability
- More resilient

### Private Cluster
- Internal IPs
- More secure networking
- Common ACE exam answer

---

## Important CLI Commands

### Create GKE Cluster

```bash
gcloud container clusters create my-cluster \
    --zone=us-central1-a
```

### Get Cluster Credentials

```bash
gcloud container clusters get-credentials my-cluster \
    --zone=us-central1-a
```

### Deploy Application

```bash
kubectl apply -f deployment.yaml
```

### View Pods

```bash
kubectl get pods
```

---

## ACE Recognition Notes

- Standard clusters = more flexibility
- Autopilot = managed infrastructure
- Private clusters = secure/internal access
- Regional clusters = high availability
- Zonal clusters = lower cost/lower HA

---

## Official Documentation

### GKE Configuration Overview
https://docs.cloud.google.com/kubernetes-engine/docs/concepts/configuration-overview

### Terraform GKE Cluster Resource
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/container_cluster#argument-reference
## ACE Recognition Notes

- Cloud Run = serverless containers
- Cloud Run functions = event-driven snippets
- GKE = Kubernetes orchestration
- Cloud SQL does NOT support MySQL UDFs
- N2 = balanced production workloads

---

gcloud Command Recognition

- gcloud functions deploy → deploying event-driven serverless code.
- gcloud run deploy → deploying containers.
- gcloud sql instances create → creating managed databases

```bash
gcloud container clusters create supply-chain-cluster \
  --zone us-central1-a
```
---

- zonal vs regional clusters
- autopilot vs standard
- Kubernetes orchestration
