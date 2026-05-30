# CIDR and Subnet Expansion

## Key Concept
CIDR prefix length defines how many bits belong to the network.

IPv4 addresses contain 32 bits total.

Host bits:
32 - prefix length

## Examples

| Prefix | Hosts |
|---|---|
| /24 | 256 |
| /23 | 512 |
| /22 | 1024 |
| /21 | 2048 |

## GCP Example

gcloud compute networks subnets expand-ip-range mysubnet \
--region us-central1 \
--prefix-length 21

## Key Rule

Smaller prefix number = larger subnet

## ACE Recognition Pattern

Need ~2000 IPs:
2^11 = 2048
32 - 11 = /21
