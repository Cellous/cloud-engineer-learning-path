# Managed Instance Groups (MIGs)

## Overview

Managed Instance Groups (MIGs) deploy and manage identical VM instances using an instance template.

MIG features:
- Autoscaling
- Autohealing
- Rolling updates
- Load balancing
- High availability

MIGs can be:
- Zonal
- Regional

---

## Key Concepts

### Instance Templates
Define VM configuration:
- machine type
- boot disk
- startup scripts
- networking
- metadata

### Autoscaling
Automatically adds or removes VM instances based on:
- CPU usage
- load balancing capacity
- monitoring metrics

### Autohealing
Recreates unhealthy VM instances automatically.

### Rolling Updates
Updates VM instances gradually to minimize downtime.

### Canary Updates
Deploy updates to a small subset of instances first for testing.

---

## ACE Recognition Notes

### PROACTIVE Updates
- Rolling automated updates
- Minimal resource usage
- Default surge = 1
- Common ACE exam answer

### Opportunistic Updates
- Non-interactive
- Slower rollout behavior
- Not ideal for immediate automated upgrades

### Max Surge
Controls how many extra VMs are temporarily created during updates.

Higher surge:
- faster updates
- more resource usage

---

## Diagnostic Question Lessons

- Managed instance groups use instance templates.
- MIGs maintain VM availability automatically.
- Regional MIGs improve availability across zones.
- Rolling updates minimize downtime.
- PROACTIVE updates are commonly the correct ACE answer.
- Autoscaling reduces costs during low demand.

---

## Real-World Use Cases

- Web server farms
- Backend APIs
- Ecommerce platforms
- Stateless applications
- Autohealing production systems

