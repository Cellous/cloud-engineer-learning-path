# Identity and Access Management (IAM) Architecture Diagrams

![Google Cloud](https://img.shields.io/badge/Platform-Google_Cloud-4285F4?logo=googlecloud&logoColor=white)
![IAM](https://img.shields.io/badge/Security-IAM-orange)
![ACE](https://img.shields.io/badge/Certification-Associate_Cloud_Engineer-blue)
![Architecture](https://img.shields.io/badge/Documentation-Architecture-success)

---

# Overview

This collection of architecture diagrams documents the core Identity and Access Management (IAM) concepts used throughout Google Cloud Platform.

These diagrams illustrate how identities, roles, permissions, policies, service accounts, authentication methods, and resource hierarchy interact to provide secure access to Google Cloud resources.

The collection emphasizes **least privilege**, **machine-to-machine authentication**, and **recommended security patterns** frequently tested on the Google Cloud Associate Cloud Engineer (ACE) certification.

---

# Diagram Categories

## IAM Policy Management

Topics include:

- Custom IAM Roles
- IAM Role Updates
- Policy Bindings
- Least Privilege
- Resource Access
- Permission Inheritance

Folder:

```
iam-policy-management/
```

---

## Security Architecture

Topics include:

- Authentication Methods
- OAuth 2.0
- Service Accounts
- Workload Identity
- API Keys
- Application Default Credentials (ADC)
- Authentication Decision Matrix

Folder:

```
security-architecture/
```

---

## Resource Hierarchy

The resource hierarchy demonstrates how permissions are inherited across Google Cloud.

```
Organization
      ↓
Folder
      ↓
Project
      ↓
Resources
```

Resource hierarchy enables centralized administration and policy inheritance.

Diagram:

- `resource-hierarchy-architecture.png`

---

## IAM Resource Model

Illustrates the relationship between:

- Principals
- IAM Roles
- Permissions
- Resources
- IAM Policies

Diagram:

- `iam-resource-model.png`

---

# Key Concepts

## Authentication

Verifies identity.

Examples:

- OAuth 2.0
- Service Accounts
- Workload Identity
- API Keys

---

## Authorization

Determines what an authenticated identity can access.

Implemented through:

- IAM Roles
- IAM Policies
- Permission Bindings

---

## Principal

An identity requesting access.

Examples:

- Google User
- Service Account
- Group
- Domain

---

## Resource

Objects protected by IAM.

Examples:

- Compute Engine
- Cloud Storage
- Cloud SQL
- Cloud Run
- GKE
- Pub/Sub
- BigQuery

---

## IAM Policy

An IAM Policy binds:

```
Principal
      ↓
Role
      ↓
Permissions
      ↓
Resource
```

---

# ACE Recognition Patterns

| Pattern | Recognition |
|-------------------------|--------------------------------|
| OAuth 2.0 | User authentication |
| Service Account | Machine-to-machine identity |
| Workload Identity | GKE authentication |
| API Key | Public API access |
| IAM Role | Collection of permissions |
| IAM Policy | Role binding document |
| Organization → Folder → Project | Resource hierarchy |
| Least Privilege | Security best practice |

---

# Security Best Practices

- Follow the Principle of Least Privilege
- Prefer Workload Identity over service account keys
- Avoid embedding credentials in applications
- Use managed identities whenever possible
- Rotate credentials regularly
- Audit IAM policies periodically
- Grant only required permissions

---

# Directory Structure

```
iam/
│
├── iam-policy-management/
├── security-architecture/
├── iam-resource-model.png
├── resource-hierarchy-architecture.png
└── README.md
```

---

# Skills Demonstrated

- Google Cloud IAM
- Authentication
- Authorization
- IAM Policies
- Service Accounts
- OAuth 2.0
- Workload Identity
- Resource Hierarchy
- Principle of Least Privilege
- Cloud Security Architecture

---

# Related Architecture Sections

- `../gke`
- `../networking`
- `../operations`
- `../monitoring`
- `../storage`
- `../data-solutions`

---

# Repository

This section is part of the **cloud-engineer-learning-path** repository and serves as a visual reference for Google Cloud security architecture, Identity and Access Management, and Associate Cloud Engineer certification preparation.
