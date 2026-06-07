# Operations Architecture Diagrams

This directory contains Google Cloud operations, infrastructure management, billing, backup, and deployment workflow diagrams created as part of the `cloud-engineer-learning-path` repository.

The purpose of this section is to document operational patterns commonly used in Google Cloud environments and reinforced through Associate Cloud Engineer (ACE) certification preparation.

---

## Included Architecture Modules

| Folder                                          | Topic                                                                                         |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `billing-architecture/`                         | Cloud Billing accounts, payment profiles, projects, and FinOps organization                   |
| `operations-flow-cymbal-superstore/`            | Operational workflows across Compute Engine, GKE, Cloud Run, Dataflow, Bigtable, and BigQuery |
| `terraform-infrastructure-deployment-workflow/` | Terraform plan, apply, Google Cloud APIs, provisioned infrastructure, and state file tracking |
| `google-cloud-documentation/`                   | Reference screenshots from official Google Cloud documentation                                |

---

## Key Operations Concepts

This section supports learning around:

* Cloud Billing and cost organization
* FinOps and billing account structure
* Managed Instance Group updates
* Terraform Infrastructure as Code workflows
* Snapshot scheduling and backup planning
* Cloud resource dependencies
* Cloud Monitoring and Cloud Logging
* Production operations and incident readiness

---

## ACE Recognition Patterns

| Scenario                                | Recognition Pattern                   |
| --------------------------------------- | ------------------------------------- |
| VM template or OS update                | Managed Instance Group rolling update |
| Infrastructure described in `.tf` files | Terraform Infrastructure as Code      |
| Reviewing changes before deployment     | `terraform plan`                      |
| Applying infrastructure changes         | `terraform apply`                     |
| Tracking deployed infrastructure        | `terraform.tfstate`                   |
| Paying for project usage                | Cloud Billing Account                 |
| Enterprise payment method               | Google Payments Profile               |
| Backup scheduling                       | Persistent Disk snapshot schedule     |

---

## Repository Organization

```text
operations/
│
├── billing-architecture/
├── operations-flow-cymbal-superstore/
├── terraform-infrastructure-deployment-workflow/
├── google-cloud-documentation/
└── README.md
```

---

## Original Architecture Work

The following folders contain original architecture diagrams created for this repository:

* `billing-architecture/`
* `operations-flow-cymbal-superstore/`
* `terraform-infrastructure-deployment-workflow/`

---

## Reference Material

The `google-cloud-documentation/` folder contains screenshots and reference images from official Google Cloud documentation. These are kept separate from original architecture diagrams for clarity.

---

## Skills Demonstrated

* Google Cloud Operations
* Cloud Billing
* FinOps
* Terraform
* Infrastructure as Code
* Managed Instance Groups
* Backup and Recovery
* Observability
* Technical Documentation
* Associate Cloud Engineer exam preparation

---

## Repository Context

This section is part of the **cloud-engineer-learning-path** repository and supports Google Cloud operations learning, architecture documentation, and professional portfolio development.
