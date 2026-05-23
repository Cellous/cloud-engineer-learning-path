# GKE Recognition Pattern
Containers + Kubernetes
→ GKE

Need external connectivity
→ Ingress object

Need global HTTP(S) access
→ External HTTP(S) Load Balancer
---
## Major ACE clue:
```
kind: Ingress
```
### usually means:
- GKE
- load balancing
- external routing
- Kubernetes networking
