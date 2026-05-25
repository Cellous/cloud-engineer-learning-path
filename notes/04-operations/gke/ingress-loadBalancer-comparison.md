

| Feature        | Ingress        | Service LoadBalancer |
| -------------- | -------------- | -------------------- |
| Layer          | L7             | L4                   |
| Type           | Application LB | Network LB           |
| Supports NEG   | Yes            | No                   |
| Internal ALB   | Yes            | No                   |
| Protocol-aware | Yes            | Limited              |

Could become: gke-l4-vs-l7-load-balancer-comparison.png
