

## 🎯Objective
Create a Google Cloud Storage bucket using both the Google Cloud Console and Cloud Shell.

## 💻Commands Executed
```bash
gcloud storage buckets create gs://marcellous-searcy-lab01-6142026
```

---

### creates a temporary student account
It assigns:
✅ A temporary email
✅ A temporary password
✅ A temporary Google Cloud project ID
✅ Temporary permissions needed for the lab

This lets you experiment in a sandbox without affecting your personal Google account or billing.

Why use a temporary account?
- It keeps your personal Google Cloud resources separate.
- You can't accidentally incur charges on your own account.
- Every student starts with the same clean environment.
- When the lab ends, the account and its resources are automatically deleted.
---

## 🛠Technologies Used
## 📝Steps Performed
## Architecture
---

## 📚Lessons Learned
- Cloud Storage bucket names must be globally unique.
- Bucket names cannot contain @ symbols or brackets.
- Cloud Shell provides authenticated command-line access to Google Cloud resources.
- HTTP 409 indicates the resource already exists and is owned by the current project.

## 📸Screenshots
