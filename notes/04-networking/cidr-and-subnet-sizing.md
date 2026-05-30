# CIDR & Subnet Sizing

## Important Networking Insight
| Requirement         | Networking Thought       |
| ------------------- | ------------------------ |
| More devices        | Larger subnet            |
| More isolation      | Smaller subnet           |
| Kubernetes clusters | CIDR planning            |
| Hybrid cloud        | Route management         |
| Scaling             | IP exhaustion prevention |

---

## Core Formula

IPv4 = 32 bits total

Host bits:
32 - prefix length

Addresses:
2^(host bits)

---

## Common Prefix Sizes

| Prefix | Hosts |
|---|---|
| /24 | 256 |
| /23 | 512 |
| /22 | 1024 |
| /21 | 2048 |
| /20 | 4096 |

---

## Key Rule

Smaller prefix number = larger subnet

Example:
- /20 bigger than /24

---

## Example

10.1.2.0/24

32 - 24 = 8

2^8 = 256 addresses
---

## ACE Recognition Patterns
Need ~2000 IPs
→ Think /21

Need ~1000 IPs
→ Think /22

Need ~500 IPs
→ Think /23

---

## GCP Command Example

gcloud compute networks subnets expand-ip-range mysubnet \
--region us-central1 \
--prefix-length 21
