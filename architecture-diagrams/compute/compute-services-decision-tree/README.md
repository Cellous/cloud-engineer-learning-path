# Compute Services Decision Tree

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![Compute](https://img.shields.io/badge/Category-Compute-blue)
![Architecture](https://img.shields.io/badge/Type-Decision_Tree-success)
![ACE](https://img.shields.io/badge/Certification-Associate_Cloud_Engineer-orange)

## Overview

This decision tree provides a simplified framework for selecting the appropriate Google Cloud compute service based on workload requirements.

The diagram highlights common architectural decision points encountered during cloud solution design and Associate Cloud Engineer certification scenarios.

---

## Decision Flow

```
Need Compute?
        │
        ▼
Manage Operating System?
        │
 ┌──────┴──────┐
 │             │
Yes            No
 │             │
 ▼             ▼
Compute    Containers?
Engine          │
          ┌─────┴─────┐
          │           │
         Yes      Event-driven?
          │           │
          ▼           ▼
         GKE    Cloud Run Functions
          │
          ▼
      Cloud Run
```

---

## Service Selection Guide

### Compute Engine

Best for:

- Custom operating systems
- Legacy applications
- Lift-and-shift migrations
- Maximum infrastructure control

---

### Google Kubernetes Engine (GKE)

Best for:

- Container orchestration
- Microservices
- Kubernetes workloads
- Enterprise container platforms

---

### Cloud Run

Best for:

- Stateless web applications
- REST APIs
- Managed containers
- Automatic scaling

---

### Cloud Run Functions

Best for:

- Event-driven automation
- Scheduled tasks
- Pub/Sub triggers
- Lightweight serverless functions

---

## ACE Recognition Patterns

Typical certification clues include:

- Manage operating system → **Compute Engine**
- Kubernetes workloads → **GKE**
- Containerized applications → **Cloud Run**
- Event-driven execution → **Cloud Run Functions**

---

## Architecture Principles

Google Cloud encourages selecting the **highest level of abstraction** that satisfies application requirements.

Higher abstraction generally provides:

- Reduced infrastructure management
- Lower operational complexity
- Automatic scaling
- Improved developer productivity
- Faster deployment cycles

---

## Learning Objectives

This diagram reinforces:

- Compute service selection
- Infrastructure vs serverless computing
- Kubernetes architecture
- Event-driven design
- Cloud-native application deployment
- Google Cloud compute services

---

## Files

```
compute-services-decision-tree.drawio
compute-services-decision-tree.png
compute-services-decision-tree.svg
README.md
```

---

## Portfolio Note

This architecture diagram was created as part of the **Google Cloud Associate Cloud Engineer Learning Path** to demonstrate cloud solution analysis, service selection strategies, and practical architectural decision-making based on workload characteristics.
