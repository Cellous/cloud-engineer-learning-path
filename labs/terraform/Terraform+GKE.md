## Terraform + GKE

Terraform can provision GKE clusters declaratively.

Example resource:

```hcl
resource "google_container_cluster" "primary" {
  name     = "gke-cluster"
  location = "us-central1"

  initial_node_count = 1
}
```

Useful for:
- Infrastructure as Code (IaC)
- Repeatable deployments
- Automation
- Version-controlled infrastructure
