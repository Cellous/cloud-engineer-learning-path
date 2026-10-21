# Interconnecting Networks

Different applications and workloads require different network connectivity
solutions.

Google Cloud provides multiple options for connecting external infrastructure
to Google Cloud and for sharing networking resources within Google Cloud.

## Module Topics

1. Cloud VPN
   - Lab: Configure Google Cloud HA VPN

2. Cloud Interconnect and Peering

3. Sharing VPC Networks

## Hybrid Connectivity

The primary hybrid connectivity options covered in this module are:

- Cloud VPN
- Cloud Interconnect
- Peering

Conceptually:

```text
External Infrastructure
        |
        +-- Cloud VPN
        |
        +-- Cloud Interconnect
        |
        +-- Peering
        |
        v
   Google Cloud VPC
```
## Key Idea
Different connectivity requirements call for different solutions.
Examples of factors that can influence the choice include:
- Connectivity method
- Performance requirements
- Reliability requirements
- Network architecture
- Whether the connection is between Google Cloud and external infrastructure
- Whether networking resources need to be shared inside Google Cloud

---

## ACE-style notes, simple recognition block:

```text
Cloud VPN
→ Hybrid connectivity using VPN

Cloud Interconnect
→ Dedicated/private connectivity to Google Cloud

Peering
→ Network-to-network connectivity

Shared VPC
→ Share VPC networking resources across Google Cloud projects
```

