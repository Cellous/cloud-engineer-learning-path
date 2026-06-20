Lab01-CloudShell.md

1. Objective
2. Skills Learned
3. Screenshots
4. Commands Used
5. Challenges and Troubleshooting
6. Lessons Learned

# Skills Demonstrated

- Created Cloud Storage bucket using Google Cloud Console
- Created Cloud Storage bucket using Cloud Shell
- Uploaded a local file to Cloud Shell
- Copied a file into a Cloud Storage bucket
- Listed Google Cloud compute regions
- Created and verified Linux environment variables
- Used Linux commands (`ls`, `echo`)
- Diagnosed and corrected Cloud Storage command syntax errors

# Commands Used

```bash
ls
gcloud compute regions list
echo $INFRACLASS_REGION
gcloud storage cp hello-cloud-shell.txt gs://bucket-name
```

# Lessons Learned

- Bucket names are not files.
- `gcloud storage cp` requires a source file.
- Environment variables can simplify repeated commands.
- Cloud Shell combines Linux tools with Google Cloud CLI.
