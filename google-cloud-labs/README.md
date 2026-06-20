

## Objective
Create a Google Cloud Storage bucket using both the Google Cloud Console and Cloud Shell.

## Commands Executed
```bash
gcloud storage buckets create gs://marcellous-searcy-lab01-6142026
```

## Lessons Learned
- Cloud Storage bucket names must be globally unique.
- Bucket names cannot contain @ symbols or brackets.
- Cloud Shell provides authenticated command-line access to Google Cloud resources.
- HTTP 409 indicates the resource already exists and is owned by the current project.
