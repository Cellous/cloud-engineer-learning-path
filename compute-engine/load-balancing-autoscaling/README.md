# Load Balancing and Autoscaling

## Overview

Google Cloud Load Balancing distributes traffic across compute resources in one or multiple regions.

It can help provide:

- High availability
- A single anycast IP address
- Distribution of traffic across compute resources
- Autoscaling of backend resources
- Content delivery close to users

Google Cloud Load Balancing is a fully distributed, software-defined, managed service rather than a physical load-balancing appliance.

## Managed Instance Groups
![Managed Instance Group Architecture](diagrams/managed-instance-group-architecture.png)


## Primary Load Balancer Types

Google Cloud provides two primary load-balancer categories:

### Application Load Balancers

Application Load Balancers operate at:

```text
Layer 7
Application Layer
```

They are designed primarily for HTTP(S) workloads.

Application Load Balancers can make routing decisions based on:

- HTTP headers
- Cookies
- URL paths

They also support features such as:

- SSL/TLS termination
- Session affinity
- Content-based routing

### Network Load Balancers

Network Load Balancers operate at:

```text
Layer 4
Transport Layer
```

They are designed for traffic such as:

- TCP
- UDP

Network Load Balancers make routing decisions primarily using:

- IP addresses
- Ports

They are appropriate when low latency or high throughput is important.

Google Cloud Network Load Balancing includes:

```text
Proxy Network Load Balancers
Passthrough Network Load Balancers
```

## Quick Recognition

```text
HTTP(S), URL paths, cookies, headers
→ Application Load Balancer
→ Layer 7

TCP/UDP, IP addresses, ports
→ Network Load Balancer
→ Layer 4
```

## Module Topics

1. Managed Instance Groups
2. Application Load Balancers
   - Lab: Configure an Application Load Balancer with Autoscaling
3. Cloud CDN
4. Network Load Balancing
5. Internal Load Balancing
   - Lab: Configure an Internal Network Load Balancer
6. Choosing a Load Balancer
