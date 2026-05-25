# Major Operational Pattern

| Kubernetes Resource       | Load Balancer Type        |
| ------------------------- | ------------------------- |
| Ingress                   | Application Load Balancer |
| Service type LoadBalancer | Network Load Balancer     |
| Internal ALB              | requires NEG              |
| gce                       | external                  |
| gce-internal              | internal                  |
