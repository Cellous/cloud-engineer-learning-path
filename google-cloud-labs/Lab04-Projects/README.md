# Lab04 – Managing Google Cloud Projects

## Objective

Learn how Google Cloud projects organize resources, isolate workloads, and connect resources to billing accounts.

---

## Key Concepts

- Projects are the primary organizational unit in Google Cloud.
- Resources exist within a project.
- Projects provide isolation between environments.
- Projects can be created, selected, switched, and scheduled for deletion.
- Cloud Shell can be configured to operate against different projects.

---

## Architecture Overview

Projects act as containers for Google Cloud resources.

```text
Organization
     │
 Billing Account
     │
   Project
     │
 ┌──────────────┐
 │ Resources    │
 │ VM Instances │
 │ Storage      │
 │ Databases    │
 │ Networking   │
 └──────────────┘
