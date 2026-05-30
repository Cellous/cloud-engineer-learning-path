

---

# `load-balancing.md`

```markdown
# Google Cloud Load Balancing
```
## Overview

Google Cloud Load Balancers distribute traffic across backend services and instances.

Benefits:
- High availability
- Scalability
- Traffic distribution
- Fault tolerance

---

## Load Balancer Types

| Type | Layer | Scope |
|---|---|---|
| HTTP(S) Load Balancer | Layer 7 | Global |
| Internal Application LB | Layer 7 | Regional |
| TCP/UDP Network LB | Layer 4 | Regional |

---

## GKE Integration

Kubernetes Ingress resources can automatically provision:
- Backend services
- URL maps
- Health checks
- Load balancers

---

## Internal vs External

### External
Public internet access.

### Internal
Private VPC-only traffic.

---

## Important Components

- Ingress
- NEG (Network Endpoint Groups)
- Backend services
- URL maps
- Health checks

---

## ACE Recognition Patterns

| Requirement | Likely Solution |
|---|---|
| HTTP routing | Layer 7 |
| Internal-only traffic | Internal ALB |
| Pod-level traffic | NEG |
| TCP traffic | Layer 4 |

---

## Related Topics

- GKE
- Ingress
- Networking
- Cloud Armor
