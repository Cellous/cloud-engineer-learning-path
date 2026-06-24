# Lab04 – Managing Google Cloud Projects

## Objective

Learn how Google Cloud projects organize resources, isolate workloads, and connect resources to billing accounts.

---

## Key Concepts

- Projects are the primary organizational unit in Google Cloud.
- Resources exist within a project.
- Projects provide isolation between environments.
- Projects can be created, selected, switched, and scheduled for deletion.
- Cloud Shell can be configured to operate against different projects.

---

## Architecture Overview

Projects act as containers for Google Cloud resources.

```text
Organization
     │
 Billing Account
     │
   Project
     │
 ┌──────────────┐
 │ Resources    │
 │ VM Instances │
 │ Storage      │
 │ Databases    │
 │ Networking   │
 └──────────────┘
```

## Lab Workflow
Step 1 – Open Google Cloud Console
Figure 1. Google Cloud Console before project creation.
________________________________________
Step 2 – Open Project Selector
Figure 2. Viewing existing projects and accessing the New Project option.
________________________________________
Step 3 – Create a New Project
Figure 3. Creating a new Google Cloud project.
________________________________________
Step 4 – Verify Project Creation
Figure 4. Reviewing notifications generated during project creation.
________________________________________

## Cloud Shell Commands
List current configuration:
```bash
gcloud config list
```
Display active project:
```bash
gcloud config list | grep project
```
Change active project:
```bash
gcloud config set project PROJECT_ID
```
Store a project ID in an environment variable:
```bash
export PROJECT_ID1="my-project-id"
```
________________________________________
## Skills Demonstrated
- Project creation 
- Project isolation concepts 
- Project switching 
- Cloud Shell configuration 
- Resource organization 
- Billing relationship awareness 
________________________________________
## Learning Outcome
This exercise demonstrated how Google Cloud projects serve as the foundation for organizing infrastructure resources, managing access boundaries, and controlling billing relationships across cloud environments.

