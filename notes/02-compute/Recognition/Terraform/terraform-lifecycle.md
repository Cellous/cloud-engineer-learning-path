# Terraform Lifecycle

## YAML Example (Cloud Build)

```yaml
steps:
  - name: hashicorp/terraform
    args: ["init"]

  - name: hashicorp/terraform
    args: ["plan"]

  - name: hashicorp/terraform
    args: ["apply", "-auto-approve"]
```

## Recognition Pattern

- `terraform init` → downloads providers/modules
- `terraform plan` → previews infrastructure changes
- `terraform apply` → creates infrastructure
- `terraform destroy` → removes infrastructure

## Important Files

| File | Purpose |
|---|---|
| `main.tf` | Terraform resources |
| `backend.tf` | Remote state backend |
| `terraform.tfstate` | Infrastructure state tracking |
| `cloudbuild.yaml` | Cloud Build automation instructions |
