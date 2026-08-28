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
```
A role is a named collection of IAM permissions.

---

## IAM Policy Inheritance
IAM policy inheritance follows the Google Cloud resource hierarchy:

```text
Organization
     ↓
Folder
     ↓
Project
     ↓
Resource
```

Resources can inherit access granted at higher levels of the hierarchy.

For allow policies, access granted at a parent resource cannot be removed simply by granting a less-privileged role at a child resource.

For example, if a principal has Editor access at a folder level and Viewer access at a project below that folder, the inherited Editor access still applies.

---

## Allow Policies

IAM allow policies grant access to Google Cloud resources.

An allow policy can:

- grant access to a resource
- affect descendant resources through inheritance
- bind one or more principals to a single IAM role
- include context-specific conditions

Example relationship:

```text
Principals
    +
   Role
    ↓
Allow Policy Binding
    ↓
Resource Access
```

---

## Deny Policies

IAM deny policies provide access-control guardrails.

A deny rule defines:

- the principals affected
- the permissions being denied
- optionally, a condition under which the denial applies

When a permission is denied, the principal cannot perform an operation requiring that permission even if an IAM role otherwise grants it.

The course states that IAM evaluates applicable deny policies before applicable allow policies.

---

## IAM Conditions

IAM Conditions provide conditional, attribute-based access control.

A role binding can include a condition that must evaluate to true before access is granted.

Example uses discussed in the course include:

temporary access during a production issue
restricting access based on where a request originates

Conceptually:

```text
Principal
    +
Role Binding
    +
Condition
    ↓
Condition = TRUE
    ↓
Access Granted
```

---

## Organization Policies

Organization policies configure restrictions on Google Cloud resources using constraints.

They can be applied at the organization level and inherited by folders and projects below that organization.

Exceptions require appropriate organization-policy administrative authority.

Organization policies should not be confused with IAM allow policies or IAM deny policies.

---

## Least Privilege

The principle of least privilege applies to:

- identities
- roles
- resources

The course recommends selecting the smallest scope necessary to perform the required task.

Google Cloud Recommender can also identify principals with excess permissions and recommend removing or replacing overly broad roles.

---

## Directory Synchronization

Google Cloud Directory Sync can synchronize users and groups from an existing:

Active Directory environment
LDAP directory

into a Cloud Identity domain.

The course describes this synchronization as one-way, meaning the existing Active Directory or LDAP directory is not modified by the synchronization process.

---

## Single Sign-On

Organizations can continue using an existing identity system through single sign-on.

When Google Cloud requires authentication, the user can be redirected to the organization's identity system.

If authentication succeeds, the user receives access according to the applicable Google Cloud access policies.

---

## Key Takeaways
- Members or principals define the "who" portion of IAM.
- IAM roles define what those principals can do.
- IAM policies bind principals to roles.
- IAM allow policies grant access.
- IAM deny policies can block permissions even when a role grants them.
- IAM Conditions make access dependent on specified conditions.
- IAM policies follow the Google Cloud resource hierarchy.
- IAM does not create or manage users and groups.
- Google Workspace and Cloud Identity provide identity administration.
- Least privilege should be applied to identities, roles, resources, and scope.

---

## Related IAM Documentation
- ![IAM Fundamentals](iam-fundamentals.md)
- ![Organizations and Folders](organization-and-folders.md)
- ![Roles and Permissions](
- ![Service Accounts](service-accounts.md)
- ![IAM Best Practices](iam-best-practices.md)
