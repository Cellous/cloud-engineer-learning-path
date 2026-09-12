# Cloud SQL Labs

This section documents hands-on Google Cloud SQL exercises, deployment patterns,
connectivity methods, and troubleshooting notes.

## Core Concepts

Cloud SQL is a fully managed relational database service supporting:

- MySQL
- PostgreSQL
- Microsoft SQL Server

Key operational concepts include:

- Managed database provisioning
- High availability and regional failover
- Automated backups and point-in-time recovery
- Read replicas
- Private IP connectivity
- Cloud SQL Auth Proxy
- IAM and VPC integration

## Deployment Recognition

Common `gcloud` commands:

```text
gcloud functions deploy        → deploy event-driven serverless functions
gcloud run deploy              → deploy containerized applications
gcloud sql instances create    → create managed Cloud SQL instances
```

---

## Labs
### Configure Cloud SQL

Hands-on lab covering:

- Creating a Cloud SQL database
- Configuring a VM to run a proxy
- Connecting an application to Cloud SQL
- Connecting through Private IP
- Comparing external proxy and private-network connectivity

See:

- ![ Configure Cloud SQL](README.md)

## ACE Recognition Notes
- Cloud SQL is a managed relational database service.
- Private IP keeps database traffic on private Google Cloud networking.
- Cloud SQL Auth Proxy simplifies authentication and encrypted connectivity.
- Regional HA uses a primary and standby instance.
- Read replicas support read scaling.
- Spanner is generally considered when global scale or horizontal scalability is required
