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

## GCP Command

```bash
gcloud compute networks subnets expand-ip-range mysubnet \
--region us-central1 \
--prefix-length 21
