# Google Cloud Networking & Load Balancing

## Overview

Google Cloud provides multiple load balancing solutions based on:

- OSI layer
- internal vs external traffic
- regional vs global scope
- application traffic vs network traffic

---

# Application Load Balancers (Layer 7)

Application Load Balancers operate at Layer 7 of the OSI model.

They support:
- HTTP
- HTTPS
- URL routing
- SSL/TLS termination
- content-based routing

Best for:
- web applications
- APIs
- ecommerce platforms
- Cloud Run
- GKE web services

---

# Network Load Balancers (Layer 4)

Network Load Balancers operate at Layer 4.

They manage:
- TCP
- UDP
- IP traffic

Types:
- Proxy
- Passthrough

Best for:
- gaming
- raw TCP services
- high-performance networking
- non-HTTP workloads

---

# Proxy Load Balancers

Proxy load balancers:
- terminate client connections
- create new backend connections
- provide advanced traffic control

Advantages:
- better traffic management
- SSL offloading
- backend flexibility

---

# Passthrough Load Balancers

Passthrough load balancers:
- forward traffic directly
- do not terminate connections
- preserve original packets

Best for:
- ultra-low latency
- direct TCP/UDP forwarding

---

# Layer 4 vs Layer 7

| Feature | Layer 4 | Layer 7 |
|---|---|---|
| Protocol Awareness | TCP/UDP | HTTP/HTTPS |
| Routing | IP/Port | URL/Header |
| SSL Handling | Limited | Advanced |
| Use Case | Network traffic | Web applications |

---

# Key Associate Cloud Engineer Concepts

- Global Application Load Balancer = Layer 7
- Global Proxy Network Load Balancer = Layer 4
- Regional Passthrough Network Load Balancer = Layer 4
- Internal Application Load Balancer = private web traffic

### Official Documentation
- Cloud Load Balancing overview: [https://cloud.google.com/load-balancing/docs/load-balancing-overview]
- Networking Fundamentals
