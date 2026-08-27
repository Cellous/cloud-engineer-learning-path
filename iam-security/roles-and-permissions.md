# Google Cloud IAM Roles and Permissions

Google Cloud Identity and Access Management (IAM) controls **what actions a principal can perform on a resource**.

A role is a collection of permissions. Google Cloud IAM uses three major role types:

1. **Basic roles**
2. **Predefined roles**
3. **Custom roles**

The choice of role determines how broadly or precisely access is granted.

---

## Three Types of IAM Roles

| Role Type | Scope / Purpose | Access Granularity |
|---|---|---|
| Basic | Broad project-level access | Coarse-grained |
| Predefined | Google-managed roles for particular services or job functions | Fine-grained |
| Custom | User-defined collection of selected permissions | Precise |

---

## Basic IAM Roles

Basic roles provide broad, fixed levels of access across resources in a Google Cloud project.

The principal basic roles are:

- **Owner** — administrative access
- **Editor** — modify and manage resources
- **Viewer** — read-only access

These roles are hierarchical:

- Owner includes Editor permissions.
- Editor includes Viewer permissions.

![Basic IAM Roles](diagrams/basic-iam-roles.png)

### Basic Role Relationship

```text
Owner
  ↓ includes
Editor
  ↓ includes
Viewer
```

