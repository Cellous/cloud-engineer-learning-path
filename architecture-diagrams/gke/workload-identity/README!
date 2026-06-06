# GKE to Cloud Spanner Authentication Flow

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![GKE](https://img.shields.io/badge/GKE-Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![IAM](https://img.shields.io/badge/Security-IAM-4285F4)
![Workload Identity](https://img.shields.io/badge/Auth-Workload_Identity-8E24AA)
![Cloud Spanner](https://img.shields.io/badge/Database-Cloud_Spanner-34A853)

## Overview

This diagram illustrates the recommended authentication flow for a Google Kubernetes Engine (GKE) workload accessing Cloud Spanner using **Workload Identity**.

Instead of storing credentials inside a Pod, Kubernetes identities are mapped to Google Cloud service accounts, allowing applications to securely authenticate using IAM and least-privilege access.

---

## Architecture Diagram

![GKE to Cloud Spanner Authentication Flow](workload-identity-spanner-flow.png)

---

## Authentication Flow

```text
GKE Pod
      ↓
Kubernetes Service Account
      ↓
Workload Identity
      ↓
Google Service Account
      ↓
IAM Role
      ↓
Cloud Spanner
```

---

## Components

### GKE Pod

Runs the application workload that requires database access.

---

### Kubernetes Service Account

Provides the Kubernetes identity associated with the Pod.

---

### Workload Identity

Maps the Kubernetes Service Account to a Google Cloud Service Account, eliminating the need for long-lived credentials.

---

### Google Service Account

Represents the application's Google Cloud identity.

Permissions are granted through IAM roles.

---

### IAM Role

Provides least-privilege authorization.

Example:

```
Cloud Spanner Database User
```

---

### Cloud Spanner

Receives authenticated API requests using the service account identity.

---

## Security Benefits

- No embedded service account keys
- Machine-to-machine authentication
- IAM-managed permissions
- Supports least privilege
- Automatic credential rotation
- Reduced secret management

---

## ACE Recognition Pattern

If an exam question mentions:

- GKE Pods
- Cloud Spanner
- Cloud SQL
- Pub/Sub
- BigQuery
- backend authentication

the recommended solution is often:

> **Workload Identity → Google Service Account → IAM Role → Google Cloud API**

---

## Best Practices

✅ Use Workload Identity

✅ Assign only required IAM roles

✅ Use dedicated service accounts per workload

✅ Avoid storing JSON keys in containers

❌ Do not embed service account keys inside Pods

❌ Do not use user credentials for backend services

---

## Skills Demonstrated

- Google Kubernetes Engine
- Workload Identity
- Google IAM
- Service Accounts
- Cloud Spanner
- Authentication
- Authorization
- Least Privilege
- Zero Secret Architecture

---

## Files Included

- workload-identity-spanner-flow.drawio
- workload-identity-spanner-flow.png
- workload-identity-spanner-flow.svg

---

## Related Topics

- Service Accounts
- IAM Roles
- Cloud Spanner
- Kubernetes Service Accounts
- Workload Identity Federation
- Zero Trust Security
- Machine-to-Machine Authentication

---

## Portfolio Note

This architecture diagram was created as part of the **Google Cloud Associate Cloud Engineer Learning Path** to demonstrate secure workload authentication patterns and modern identity management practices for Kubernetes applications running on Google Cloud.
