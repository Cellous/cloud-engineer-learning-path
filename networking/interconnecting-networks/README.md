# Interconnecting Networks

Different applications and workloads require different network connectivity
solutions.

Google Cloud provides multiple options for connecting external infrastructure
to Google Cloud and for sharing networking resources within Google Cloud.

![Interconnecting Networks Overview](diagrams/interconnecting-networks.png)

## Module Topics

1. Cloud VPN
   - Lab: Configure Google Cloud HA VPN

2. Cloud Interconnect and Peering

3. Sharing VPC Networks

## Hybrid Connectivity

The primary hybrid connectivity options covered in this module are:

- Cloud VPN
- Cloud Interconnect
- Peering

Conceptually:

```text
External Infrastructure
        |
        +-- Cloud VPN
        |
        +-- Cloud Interconnect
        |
        +-- Peering
        |
        v
   Google Cloud VPC
```
## Key Idea
Different connectivity requirements call for different solutions.
Examples of factors that can influence the choice include:
- Connectivity method
- Performance requirements
- Reliability requirements
- Network architecture
- Whether the connection is between Google Cloud and external infrastructure
- Whether networking resources need to be shared inside Google Cloud

---

## Cloud VPN

Cloud VPN securely connects an external or on-premises network to a
Google Cloud VPC network through encrypted IPsec VPN tunnels.

Google Cloud provides two Cloud VPN gateway types:

- Classic VPN
- HA VPN

---

## Classic VPN

Classic VPN securely connects an on-premises network to a Google Cloud
VPC network over the public internet using IPsec encryption.

Traffic is encrypted by one VPN gateway and decrypted by the gateway at
the other end of the connection.

Classic VPN is useful for relatively low-volume data connections.

### Classic VPN Characteristics

- 99.9% service availability SLA
- Site-to-site VPN
- Static routing
- Dynamic routing
- IKEv1 and IKEv2
- Regional Cloud VPN gateway
- Regional external IP address

Classic VPN does not provide client "dial-in" VPN connectivity.

Dynamic routes use Cloud Router.

### Classic VPN Concept

```text
Google Cloud VPC
      |
Cloud VPN Gateway
      |
Encrypted IPsec Tunnel
      |
Public Internet
      |
On-Premises VPN Gateway
      |
On-Premises Network
```
### MTU Consideration
The course notes that the on-premises VPN gateway MTU must not exceed:
```text
1460 bytes
```
This accounts for VPN encryption and packet encapsulation overhead.
---
## HA VPN
HA VPN is Google's high-availability Cloud VPN solution.
It securely connects a peer network to a Google Cloud VPC using IPsec
VPN connections.
### HA VPN Characteristics
- Up to 99.99% service availability SLA
- Two fixed gateway interfaces
- One automatically assigned external IP per interface
- Multiple VPN tunnels supported per interface
- Dynamic routing using BGP
- Cloud Router required
For the 99.99% SLA, the VPN topology must be configured with the required
redundant tunnels.
---
## HA VPN Gateway
```text
             HA VPN Gateway
              /          \
      Interface 0      Interface 1
          |                |
       Tunnel 0         Tunnel 1
          |                |
       Peer VPN Gateway(s)
```
---
### Routing Modes
HA VPN can be configured as:

```text
Active / Active
```
or:
```text
Active / Passive
```
depending on routing priorities.
---
## HA VPN Peer Configurations
The course describes three common peer gateway configurations:
1. Two peer VPN devices, each with its own IP address.
2. One peer VPN device with two separate IP addresses.
3. One peer VPN device with one IP address.
Using two physical peer gateways provides additional redundancy and allows
maintenance or failure of one gateway without losing the entire VPN
connection.
---
## HA VPN with AWS
HA VPN can connect to AWS using:
- AWS Transit Gateway
- AWS Virtual Private Gateway
The course notes that only the AWS Transit Gateway supports:

```text
ECMP
Equal-Cost Multipath Routing
```
ECMP distributes traffic across active VPN tunnels.
A supported AWS HA configuration can use four tunnels.

---
## HA VPN Between Google Cloud VPC Networks
Two Google Cloud VPC networks can also be connected by placing an HA VPN
gateway in each VPC.

Conceptually:
```text
VPC Network A
     |
HA VPN Gateway A
   /        \
Tunnel 0   Tunnel 1
   \        /
HA VPN Gateway B
     |
VPC Network B
```
The course topology provides 99.99% availability when configured with both
interfaces and redundant tunnels.
---
## Dynamic Routing with Cloud Router
Cloud Router provides dynamic route exchange for Cloud VPN.
It uses:
```text
BGP
Border Gateway Protocol
```
Cloud Router allows routes to change and propagate without changing the VPN
tunnel itself.

Conceptually:

```text
Google Cloud VPC
      |
 Cloud Router
      |
 BGP Session
      |
 VPN Tunnel
      |
Peer VPN Gateway
      |
Peer Network
```
![Cloud Router BGP Routing Flow](diagrams/cloud-router-bgp-routing-flow.png)

### Why Dynamic Routing Matters
Suppose new subnets are added:
```text
Google Cloud:
10.22.0.0/16

On-premises:
10.0.30.0/24
```

With BGP, Cloud Router and the peer gateway advertise the new routes
automatically.

You do not need to manually rebuild the VPN tunnel.

### BGP Link-Local Addresses
The BGP endpoints use addresses from: 

```text
169.254.0.0/16
```
These addresses are used only for the BGP session and are not part of the
normal address space of either connected network.

---

## ACE-style notes, simple recognition block:

```text
Cloud VPN
→ Hybrid connectivity using VPN

Cloud Interconnect
→ Dedicated/private connectivity to Google Cloud

Peering
→ Network-to-network connectivity

Shared VPC
→ Share VPC networking resources across Google Cloud projects
```
```text
Need encrypted site-to-site connectivity over the public internet
→ Cloud VPN

Need high availability
→ HA VPN

Need 99.99% VPN SLA
→ Properly configured HA VPN

Need static routes
→ Classic VPN

Need dynamic route propagation
→ Cloud Router + BGP

HA VPN routing
→ Dynamic BGP only

Need automatic propagation of newly added subnets
→ Cloud Router

Need AWS multipath traffic distribution
→ AWS Transit Gateway + ECMP
```

## Classic VPN vs HA VPN
| Feature | Classic VPN | HA VPN |
|---|---|---|
| SLA | 99.9% | 99.99% when properly configured |
| Routing | Static or dynamic | Dynamic BGP |
| Cloud Router | Optional for dynamic routing | Required |
| High availability design | Limited | Yes |
| Gateway interfaces | Legacy model | Two |
| Multiple redundant tunnels | Possible | Core design |

---

## Cloud Interconnect and Peering

Google Cloud provides several services for connecting external infrastructure to Google's network.

These services can be compared by:

- Dedicated vs. shared connectivity
- Layer 2 vs. Layer 3 connectivity

### Connectivity Services

| Service | Connection Type | Network Layer |
|---|---|---|
| Direct Peering | Dedicated | Layer 3 |
| Carrier Peering | Shared | Layer 3 |
| Dedicated Interconnect | Dedicated | Layer 2 |
| Partner Interconnect | Shared | Layer 2 or Layer 3 |

### Dedicated vs. Shared

**Dedicated connections** provide a direct connection to Google's network.

**Shared connections** provide connectivity to Google's network through a service provider or partner.

### Layer 2 Connectivity

Layer 2 connectivity uses VLAN-based connectivity into the Google Cloud environment.

It can provide access to internal IP addresses within RFC 1918 private address space.

### Layer 3 Connectivity

Layer 3 connectivity provides access to services such as:

- Google Workspace
- YouTube
- Google Cloud APIs

These services are reached using public IP addresses.

### Cloud VPN Comparison

Cloud VPN differs from Interconnect and Peering because it uses the public internet while encrypting traffic.

Cloud VPN can still provide access to internal IP addresses.

```text
Cloud VPN
Public Internet
      +
Encrypted traffic
      +
Internal IP connectivity
```

This makes Cloud VPN useful alongside Direct Peering and Carrier Peering when encrypted private connectivity is required.

---

## Cloud Interconnect Options

Google Cloud provides several connectivity options for connecting VPC networks to on-premises networks or other cloud providers.

The primary options covered in this lesson are:

- Cloud VPN
- Dedicated Interconnect
- Partner Interconnect
- Cross-Cloud Interconnect

## Dedicated Interconnect

Dedicated Interconnect provides a direct physical connection between an on-premises network and Google's network.

It is designed for organizations that need to transfer large amounts of data without relying on the public internet.

### Requirements

Dedicated Interconnect requires:

- A supported colocation facility
- A physical cross-connect between the customer router and Google's network
- Cloud Router
- BGP routing between the Cloud Router and on-premises router

Conceptually:

```text
Google Cloud VPC
      |
Cloud Router
      |
BGP
      |
Google Peering Edge
      |
Physical Cross-Connect
      |
On-Premises Router
      |
On-Premises Network
```

Dedicated Interconnect can support high-throughput connectivity using:

```text
10 Gbps
or
100 Gbps
per link
```

The course notes that configurations can support either 99.9% or 99.99% availability depending on the redundancy design.

## ACE-style notes, simple recognition block:

Dedicated Interconnect
→ Dedicated Layer 2 connectivity

Partner Interconnect
→ Shared connectivity through a partner

Direct Peering
→ Dedicated Layer 3 connection to Google

Carrier Peering
→ Shared Layer 3 connection through a carrier

Layer 2
→ Private/internal RFC 1918 connectivity

Layer 3
→ Public Google services and APIs
---

## Partner Interconnect

Partner Interconnect provides connectivity between an on-premises network and Google Cloud through a supported service provider.

This option is useful when:

- A customer cannot physically reach a Google-supported colocation facility.
- Bandwidth requirements do not justify Dedicated Interconnect.
- A service provider already has connectivity to Google's network.

Conceptually:

```text
Google Cloud VPC
      |
Cloud Router
      |
Google Peering Edge
      |
Service Provider Network
      |
Service Provider Peering Edge
      |
On-Premises Router
      |
On-Premises Network
```

BGP is used between Cloud Router and the on-premises network to exchange routes.

Partner Interconnect supports connection capacities ranging from:

```text
50 Mbps
to
50 Gbps
per connection
```

## Cross-Cloud Interconnect

Cross-Cloud Interconnect provides high-bandwidth dedicated connectivity between Google Cloud and a network hosted by another cloud service provider.

It supports integrated multi-cloud architectures.

The course lists support for:

- Amazon Web Services
- Microsoft Azure
- Oracle Cloud Infrastructure
- Alibaba Cloud

Cross-Cloud Interconnect connection sizes are:

```text
10 Gbps
or
100 Gbps
```

A redundant design requires primary and redundant ports on both Google Cloud and the remote cloud provider.

Conceptually:

```text
Google Cloud VPC
      |
Cross-Cloud Interconnect
      |
Remote Cloud Provider
      |
Remote Cloud Network
```

---

## Interconnect Comparison

| Connectivity Option | Provides | Capacity | Requirement |
|---|---|---:|---|
| Cloud VPN | Encrypted connectivity over public internet | 1.5–3 Gbps per tunnel | Remote VPN gateway |
| Dedicated Interconnect | Direct physical connection to VPC networks | 10 or 100 Gbps per link | Colocation facility |
| Partner Interconnect | Connectivity through a service provider | 50 Mbps–50 Gbps | Supported service provider |
| Cross-Cloud Interconnect | Dedicated connection to another cloud provider | 10 or 100 Gbps | Primary and redundant ports |

All of these options can provide access to internal IP addresses.

## ACE Recognition Notes

```text
Lower cost / lower bandwidth / migration testing
→ Cloud VPN

High throughput + direct physical connection
→ Dedicated Interconnect

Cannot reach a Google colocation facility
→ Partner Interconnect

Need connectivity through a service provider
→ Partner Interconnect

Google Cloud ↔ AWS / Azure / OCI / Alibaba Cloud
→ Cross-Cloud Interconnect

Need 10 or 100 Gbps dedicated cloud-to-cloud connectivity
→ Cross-Cloud Interconnect

Need private connectivity using BGP
→ Cloud Router
```
---

## Resource Cleanup and Cost Control

Cloud resources should be removed in dependency-aware order when they are no longer needed.

Manual cleanup is useful in a real Google Cloud environment because unused resources can continue consuming resources or generating charges.

The HA VPN lab demonstrated a practical cleanup sequence:

![Manual Cloud Resource Cleanup Order](diagrams/manual-cloud-resource-cleanup-order.png)

### Cleanup Order

```text
VPN tunnels
    ↓
BGP peers
    ↓
Cloud Routers
    ↓
VPN gateways
    ↓
VM instances
    ↓
Firewall rules
    ↓
Subnets
    ↓
VPC networks
```

### Why the Order Matters

Cloud resources can depend on other resources.

For example:

- VPN tunnels depend on VPN gateways and Cloud Routers.
- BGP peers are configured on Cloud Routers.
- VM instances depend on VPC subnets.
- Subnets belong to VPC networks.

Removing dependent resources first makes it easier to delete the parent resources later.

### Cost-Control Recognition

```text
Unused cloud resource
        ↓
Continued resource consumption
        ↓
Potential ongoing cost

Proper cleanup
        ↓
Delete dependent resources first
        ↓
Remove parent infrastructure
        ↓
Reduce unnecessary resource usage
```

### Lab Observation

During manual cleanup, VM instances and Cloud Routers took longer to delete than simpler resources such as firewall rules.

The lab also used temporary Google Cloud resources that are automatically removed when the lab ends, but manual cleanup was practiced to demonstrate how resources should be removed in a real environment.

