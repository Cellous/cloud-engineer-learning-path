# Compute Engine + GKE Notes

## Topics Covered
- Compute Engine machine families
- Disk types
- Managed Instance Groups (MIGs)
- GKE deployment models
- Terraform basics
- Serverless vs VM architectures

## Key ACE Recognition Patterns
- High availability → Regional
- Less operational overhead → Autopilot
- Internal-only access → Private cluster

## Compute Engine Machine Families
| Machine Type | Use Case |
| ------------ | -------- |
| Standard	| General workloads |
| High Memory |	Databases |
| High CPU | CPU-intensive applications |
| Compute Optimized	| High-performance computing |
| Shared Core |	Small/low-cost workloads |
| Custom	| Specific CPU/memory requirements |

## Disk Options
| Disk | Type	Characteristics |
| ---- | -------------------- |
| Persistent HDD |	Low cost, bulk storage |
| Persistent SSD |	Balanced production storage |
| Local SSD |	High IOPS, temporary |
| RAM Disk	| Extremely low latency, volatile |

## ACE Recognition Notes
- Local SSD = high performance but temporary
- Regional persistent disks = zone redundancy
- GPUs require compatible VM families
- Persistent SSD = production workloads
- HDD = cheaper bulk storage
