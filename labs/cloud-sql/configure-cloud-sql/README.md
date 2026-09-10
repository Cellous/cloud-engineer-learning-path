# Configure Cloud SQL

## Lab Objectives

- Create a Cloud SQL database
- Configure a virtual machine to run a proxy
- Create a connection between an application and Cloud SQL
- Connect an application to Cloud SQL using a Private IP address

## Architecture Overview

This lab demonstrates two ways for an application to connect to Cloud SQL.

### External Connection Through a Proxy

A WordPress instance connects to Cloud SQL through a proxy over an external connection.

The proxy listens locally on:

```text
127.0.0.1
```

## Key Concepts Reinforced
- Cloud SQL is a managed relational database service.
- Applications can connect through a proxy or Private IP.
- A proxy can provide encrypted database connectivity.
- Private IP keeps application-to-database traffic on private networking.
- VPC design and application location affect Cloud SQL connectivity.
- The WordPress application is only the example workload; the same connection concepts apply to other applications using SQL databases.
