# CIDR & Subnet Sizing

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

## GCP Command Example

gcloud compute networks subnets expand-ip-range mysubnet \
--region us-central1 \
--prefix-length 21
