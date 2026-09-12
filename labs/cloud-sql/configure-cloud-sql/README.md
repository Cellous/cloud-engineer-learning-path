# Configure Cloud SQL

## Lab Overview

This lab demonstrates how to deploy and connect an application to a
Google Cloud SQL database using both proxy-based and private-IP connectivity.

## Skills Practiced

- Create a Cloud SQL MySQL instance
- Configure private IP connectivity
- Configure Private Service Access
- Deploy a Compute Engine VM
- Configure the Cloud SQL Auth Proxy
- Connect WordPress to Cloud SQL
- Configure a database and database user
- Test application-to-database connectivity
- Compare external proxy and private-IP connection methods

## Architecture

WordPress Application
        |
        +---- Cloud SQL Proxy ----> Cloud SQL
        |
        +---- Private IP ---------> Cloud SQL

## Connection Methods

### Cloud SQL Proxy

Used when connecting from another region, VPC, project, or from outside
Google Cloud.

Benefits:

- Authentication handled automatically
- Encrypted connection
- Key rotation handled automatically

### Private IP

Used when workloads can communicate privately over Google Cloud networking.

Benefits:

- Traffic stays off the public internet
- Lower network exposure
- Strong option for production workloads

## Key Commands

```bash
export SQL_CONNECTION=<project>:<region>:<instance>

echo $SQL_CONNECTION

./cloud_sql_proxy \
  -instances=$SQL_CONNECTION=tcp:3306 &
```

## Application Configuration

WordPress connects to the local proxy using:
```text
Database Host: 127.0.0.1:3306
Database Name: wordpress
Database User: root
```

## What I Learned

Cloud SQL separates database administration from infrastructure management.
Google manages the database platform while the cloud engineer remains
responsible for connectivity, IAM, network design, database configuration,
security, and application integration.

## Troubleshooting Lessons
- Verify the Cloud SQL instance connection name before configuring the proxy.
- Confirm the proxy is listening on TCP port 3306.
- Verify Private Service Access before enabling private IP.
- Check VPC, firewall, routing, and service networking when private connectivity fails.
- Never commit passwords or temporary lab credentials to GitHub.
