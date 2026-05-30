# VPC Subnet Expansion

## Overview
Subnet expansion allows a Google Cloud VPC subnet to support more IP addresses by reducing the CIDR prefix length.

Example:
- /24 = 256 addresses
- /21 = 2048 addresses

Smaller prefix number = larger subnet.

---

## Key Concepts

### CIDR Prefix Length
IPv4 addresses contain 32 total bits.

Formula:

Host bits = 32 - prefix length

Addresses = 2^(host bits)

---

## Example

Current subnet:

10.1.2.0/24

Need approximately 2000 addresses.

Calculation:

32 - 21 = 11

2^11 = 2048 addresses

Expanded subnet:

10.1.0.0/21

---

## ACE Recognition Patterns
| Requirement | Likely Prefix |
| ----------- | ------------- |
| ~256 hosts  | /24           |
| ~512 hosts  | /23           |
| ~1024 hosts | /22           |
| ~2048 hosts | /21           |

---

## Operational Notes
- Subnet expansion is non-disruptive in many scenarios.
- Existing IPs remain valid.
- Cannot shrink subnet ranges directly.
- Proper IP planning prevents exhaustion.

---
## GCP Command

```bash
gcloud compute networks subnets expand-ip-range mysubnet \
--region us-central1 \
--prefix-length 21
```
---

## Related Topics
- VPC Networking
- CIDR
- Static IPs
- Cloud NAT

