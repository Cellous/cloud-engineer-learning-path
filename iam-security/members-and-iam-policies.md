# Google Cloud IAM Members and Policies

Google Cloud IAM identifies **who** can access resources and associates those identities with roles through IAM policies.

The course also refers to an IAM member as a **principal** or **identity**.

---

## IAM Member Types

The course identifies five types of IAM members:

1. Google Accounts
2. Service Accounts
3. Google Groups
4. Google Workspace Domains
5. Cloud Identity Domains

### Google Account

A Google Account represents an individual such as a developer or administrator.

An email address associated with a Google Account can be used as an identity.

### Service Account

A service account represents an application or workload rather than an individual user.

See [Service Accounts](service-accounts.md) for additional details.

### Google Group

A Google Group is a named collection of Google Accounts and service accounts.

Groups allow administrators to assign or modify access for multiple identities together instead of managing each identity individually.

### Google Workspace Domain

A Google Workspace domain represents the Google Accounts associated with an organization's Workspace domain.

### Cloud Identity Domain

Cloud Identity provides identity and group management capabilities for organizations that do not require the Google Workspace collaboration applications.

---

## Identity Administration

IAM is used to control access to Google Cloud resources.

IAM itself is not used to create or manage users or groups.

The course identifies:

- Google Workspace
- Cloud Identity

as services used to create and administer those identities.

---

## IAM Policies

An IAM policy consists of a list of **bindings**.

A binding associates:

```text
One or more principals
        +
       Role
        ↓
   Policy Binding
