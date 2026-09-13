# Google Cloud Resource Management

## Overview

Resource Management in Google Cloud focuses on controlling:

- Access to resources
- Resource consumption
- Costs
- Quotas
- Labels and naming
- Billing

Google Cloud resources are billable, so resource management is closely
connected to cost control and governance.

This module builds on IAM concepts by adding operational controls around
resource usage and spending.

## Module Topics

1. Resource Manager
2. Quotas
3. Labels
4. Billing
5. Lab: Examine Billing Data with BigQuery

## Why Resource Management Matters

Resource management helps organizations:

- Control who can access resources
- Prevent accidental over-consumption
- Monitor resource usage
- Organize resources
- Track and control costs
- Set budgets and alerts

## Quotas

Quotas limit how much of a resource can be consumed.

They provide a checkpoint before unusually large amounts of resources
are provisioned.

In many cases, default quotas can be increased by request.

---

## Resource Manager

Google Cloud Resource Manager organizes resources hierarchically.

```text
Organization
└── Folders
    └── Projects
        └── Resources
```
---

## IAM Policy Inheritance

IAM policies are inherited from parent resources down the hierarchy.

For allow policies, effective access can come from both:

- Parent policies
- Policies applied directly to the resource

Deny policies can block permissions even when a principal has otherwise
been granted a role containing those permissions.

---

## Billing

Billing tools help organizations:

- Monitor spending
- Set budgets
- Configure alerts
- Analyze billing data

The module includes a lab that uses BigQuery to examine billing data.

### Billing Direction

IAM inheritance generally flows:
```text
Organization
    ↓
Folder
    ↓
Project
    ↓
Resource
```
Billing and resource consumption accumulate in the opposite direction:
```text
Resource
    ↑
Project
    ↑
Billing account / organization reporting
```
A resource belongs to one project, so the project accumulates the
consumption of its resources.

---
## Projects

Projects are important administrative boundaries in Google Cloud.

They are used to:

- Track resource usage
- Track quota usage
- Enable billing
- Manage permissions and credentials
- Enable services and APIs
- Provide billing and reporting boundaries

---

## Project Identifiers

A Google Cloud project has three identifying attributes:

| Identifier     | Purpose                                        |
| -------------- | ---------------------------------------------- |
| Project Name   | Human-readable project name                    |
| Project Number | Server-generated numeric identifier            |
| Project ID     | Unique identifier used to identify the project |

The Project Name is primarily for humans and is not used as the
identifier by Google APIs.

## Resource Scope

Google Cloud resources can be global, regional, or zonal.

| Scope    | Examples from this module   |
| -------- | --------------------------- |
| Global   | Images, snapshots, networks |
| Regional | External IP addresses       |
| Zonal    | VM instances, disks         |

Regardless of scope, resources are organized under projects.

---

## ACE Recognition Notes

Remember these distinctions:

- Organization = root of the Google Cloud resource hierarchy
- Folder = groups projects or other folders
- Project = administrative, quota, API, billing, and reporting boundary
- Resource = actual cloud service object such as a VM or disk

### IAM inheritance:

Organization → Folder → Project → Resource

### Billing accumulation:

Resource → Project → Billing

### Resource location:

Global / Regional / Zonal

### Think:

- IAM → who can access resources

- Quotas → how much can be consumed

- Labels → how resources are organized and tracked

- Billing → how spending is monitored and controlled

- BigQuery → analyze exported billing data

```test
Access control + consumption limits + organization + cost control
= Resource Management
```
