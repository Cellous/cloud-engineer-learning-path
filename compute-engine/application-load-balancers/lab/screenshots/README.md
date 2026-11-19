# Configure an Application Load Balancer with Autoscaling

## Lab Overview

This lab demonstrates how to configure and test a Google Cloud Application Load Balancer with autoscaling.

Two managed instance groups are deployed as backend resources in different regions.

The load balancer distributes incoming traffic across healthy backend instances and the managed instance groups can automatically scale as workload demand changes.

## Lab Objectives

In this lab, I will:

1. Create HTTP and health-check firewall rules.
2. Create a custom image for a web server.
3. Create an instance template from the custom image.
4. Create two managed instance groups in different regions.
5. Configure an Application Load Balancer with IPv4 and IPv6.
6. Stress-test the load balancer to observe global load balancing and autoscaling.

## Architecture

The lab architecture includes:

```text
                    Internet
                       |
                  Anycast IP
                       |
              Global Forwarding Rule
                       |
                  Target Proxy
                       |
                    URL Map
                       |
                Backend Service
                  /           \
          Region 1             Region 2
             |                    |
     Managed Instance      Managed Instance
          Group                 Group
             |                    |
       Compute Engine       Compute Engine
          Instances             Instances
```

A health check determines which backend instances are healthy and eligible to receive traffic.

Firewall rules permit the required HTTP traffic and health-check traffic.

## Key Concepts Demonstrated

```text
Application Load Balancer
→ Global traffic distribution

Managed Instance Groups
→ Regional backend compute resources

Health Check
→ Determines which instances can receive traffic

Autoscaling
→ Adds or removes VM instances based on demand

Stress Test
→ Generates enough traffic to observe scaling behavior
```
