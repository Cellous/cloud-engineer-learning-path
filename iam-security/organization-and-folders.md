# Google Cloud Organizations and Folders

Google Cloud resources are organized in a hierarchy that supports centralized administration, policy inheritance, and delegated access control.

An **organization** is the root of the Google Cloud resource hierarchy. Folders can be used beneath the organization to group projects by departments, teams, legal entities, applications, or other administrative boundaries.

IAM policies applied higher in the hierarchy can be inherited by resources below them.

Organization
↓
Folder
↓
Project
↓
Resource

---

## Organization Roles

![Organization Admin and Project Creator](diagrams/organization-admin-and-project-creator.png)

## Folder Hierarchy

![Folder Resource Hierarchy](diagrams/folder-resource-hierarchy.png)

## Resource Manager Roles

![Resource Manager Roles](diagrams/resource-manager-roles.png)


| Scope        | Role    | Purpose                                           |
| ------------ | ------- | ------------------------------------------------- |
| Organization | Admin   | Administer organization-level IAM policies and resource hierarchy |
| Organization | Viewer  | View resources across the organization            |
| Folder       | Admin   | Full control over folders                         |
| Folder       | Creator | Browse hierarchy and create folders               |
| Folder       | Viewer  | View folders and projects below the resource      |
| Project      | Creator | Create new projects                               |
| Project      | Deleter | Delete projects                                   |

---

## Key Concepts

- The organization is the root of the Google Cloud resource hierarchy.
- Folders provide grouping and administrative boundaries between projects.
- Folders can contain projects as well as other folders.
- IAM policies can be inherited from parent resources by child resources.
- Administration can be delegated at different levels of the hierarchy.
- Roles should follow the principle of least privilege.
