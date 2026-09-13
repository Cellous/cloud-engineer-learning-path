# Resource Manager Diagrams

Architecture diagrams documenting Google Cloud Resource Manager concepts.

## Organization and Project Delegation

![Organization Project Delegation](diagrams/organization-project-delegation.png)

Shows:

- Organization as the root resource
- Organization Admin
- Project Creator delegation
- Projects under the organization

---

## Resource Manager Hierarchy

![Resource Manager Hierarchy](diagrams/resource-manager-hierarchy.png)

Shows:

- Organization
- Folders
- Projects
- Resources
- IAM policy inheritance
- Billing and resource consumption flow

Key concept:

**IAM inheritance flows downward, while resource consumption and billing
accumulate upward.**

---

## Resource Scope and Projects

![Resource Scope and Projects](diagrams/resource-scope-and-projects.png)

Shows the relationship between:

- Global resources
- Regional resources
- Zonal resources
- Projects
- Billing and reporting boundaries

Examples:

| Scope | Examples |
|---|---|
| Global | Images, snapshots, networks |
| Regional | External IP addresses |
| Zonal | VM instances, disks |

---

## Editable Sources

Editable versions are included for future modification:

- `.drawio` — diagrams.net
- `.vsdx` — Microsoft Visio
- `.svg` — scalable vector export
- `.png` — GitHub preview image
