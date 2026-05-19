Deploy a Compute Engine VM

# Terraform Basics

## Terraform Workflow

```bash
terraform init
```
Downloads providers and modules.

```bash
terraform plan
```
Shows a preview of infrastructure changes.

```bash
terraform apply
```
Creates infrastructure resources.

---

# Example Terraform Configuration

## main.tf

```hcl
provider "google" {
  project = "my-gcp-project"
  region  = "us-central1"
  zone    = "us-central1-a"
}

resource "google_compute_instance" "vm_instance" {
  name         = "ace-study-vm"
  machine_type = "e2-medium"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "debian-cloud/debian-11"
    }
  }

  network_interface {
    network = "default"

    access_config {
    }
  }

  tags = ["http-server"]

  metadata = {
    enable-oslogin = "TRUE"
  }
}
```

---

# What This Configuration Does

- Creates a Google Compute Engine VM
- Uses an E2 machine type
- Deploys Debian Linux
- Enables external IP access
- Enables OS Login
- Uses the default VPC network

---

# ACE Recognition Notes

- `terraform init` = initialize providers/modules
- `terraform plan` = preview infrastructure changes
- `terraform apply` = deploy infrastructure
- Infrastructure as Code (IaC) reduces human error
- Terraform uses declarative infrastructure configuration

---

### Next-Level Terraform Examples Later

| Example                 | Skill       |
| ----------------------- | ----------- |
| VPC creation            | networking  |
| Firewall rules          | security    |
| Managed instance groups | autoscaling |
| Cloud SQL               | databases   |
| GKE cluster             | Kubernetes  |
| Load balancer           | networking  |
| Cloud Storage bucket    | storage     |
| IAM roles               | governance  |


