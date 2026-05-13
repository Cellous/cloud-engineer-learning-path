# IAM Notes

- IAM controls who can do what on which resource
- Roles contain collections of permissions
- Policies bind members to roles
- Use groups instead of assigning roles directly to users
- Resource hierarchy:
  Organization → Folder → Project → Resource
 - Policies inherit downward
- Least privilege is recommended
- Predefined roles preferred before custom roles

---

## Key IAM Concepts

### Principle of Least Privilege
Grant only the minimum permissions required.

### Role Types
- Basic
- Predefined
- Custom

### Best Practice
Assign roles to Google Groups instead of individual users.

### Resource Hierarchy
Organization → Folder → Project → Resource

### Common Viewer Permissions
- compute.images.get
- compute.images.list
