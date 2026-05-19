# MySQL Migration Considerations
## Managed vs Self-Managed Databases

| Scenario	| Recommended Service |
| --------- | --------------------------------------------------------- |
| Standard MySQL workloads	| Cloud SQL |
| User-defined functions required	| Compute Engine + self-managed MySQL |
| Full OS/database control required |	Compute Engine |
| Minimal administration	| Cloud SQL |

---
## ACE Exam Insight
- Cloud SQL does not support: user-defined functions (UDFs)
- If UDFs are required: deploy MySQL on Compute Engine.

--- 

## Recommended Machine Types

| Machine Family | Use Case                      |
| -------------- | ----------------------------- |
| E2             | Cost-optimized workloads      |
| N2             | Balanced production workloads |
| C2             | Compute-intensive             |
| M series       | Memory-intensive databases    |

## Associate Cloud Engineer responsibilities include:
- VM deployment
- managed instance groups
- autoscaling
- SSH access
- OS Login
- VM Manager
- quotas
- monitoring agents
- infrastructure automation
