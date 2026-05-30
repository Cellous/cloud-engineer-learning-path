# Cloud DNS

## Overview

Cloud DNS is Google's managed Domain Name System (DNS) service.

It translates domain names into IP addresses.

---

## Core Functions

- Public DNS zones
- Private DNS zones
- Internal service discovery
- Domain management

---

## DNS Concepts

| Record Type | Purpose |
|---|---|
| A | IPv4 address |
| AAAA | IPv6 address |
| CNAME | Alias |
| MX | Mail routing |
| TXT | Verification |

---

## Public vs Private Zones

### Public Zone
Accessible from the internet.

### Private Zone
Accessible only inside a VPC.

---

## Example Flow

Client
    ↓
DNS Query
    ↓
Cloud DNS
    ↓
Resolved IP

---

## Operational Benefits

- High availability
- Global infrastructure
- Low latency
- Managed scaling

---

## ACE Recognition Patterns

| Requirement | Solution |
|---|---|
| Internal hostname resolution | Private DNS |
| Public website domain | Public DNS |
| Managed DNS service | Cloud DNS |

---

## Related Topics

- VPC
- Load Balancing
- Hybrid networking
