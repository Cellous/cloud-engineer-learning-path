# Cloud NAT

## Overview

Cloud NAT allows private VM instances to access the internet without requiring external IP addresses.

---

## Purpose

Cloud NAT provides:
- Outbound internet access
- Private infrastructure security
- Reduced external IP usage

---

## Common Use Cases

- Private GKE clusters
- Backend application servers
- Software updates
- Package downloads

---

## Architecture

Private VM
    ↓
Cloud Router
    ↓
Cloud NAT
    ↓
Internet

---

## Key Concepts

### No inbound connections
Cloud NAT only handles outbound traffic.

### Managed service
Google manages scaling and availability.

---

## Security Benefits

- Reduces attack surface
- Prevents direct internet exposure
- Supports zero-trust networking

---

## ACE Recognition Patterns

| Requirement | Solution |
|---|---|
| Private VM internet access | Cloud NAT |
| No external IPs | Cloud NAT |
| Secure outbound traffic | Cloud NAT |

---

## Related Topics

- VPC
- Cloud Router
- Private GKE
