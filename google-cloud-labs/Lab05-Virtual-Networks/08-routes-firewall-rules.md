# Routes and Firewall Rules
Routing chooses the path. Firewall rules allow or deny the packet.

## Objective

Understand how Google Cloud VPC routes traffic and how firewall rules allow or deny network connections.

---

## Big Idea

Google Cloud networking uses both routes and firewall rules.

A route tells traffic where to go.

A firewall rule decides whether the traffic is allowed.

```text
Route = destination path
Firewall rule = permission control
```
Creating a route does not guarantee that packets will be delivered.

Firewall rules must also allow the traffic.

---

## Routes

A route is a mapping of an IP range to a destination or next hop.

Routes match packets by destination IP address.

The destination is written in CIDR notation.

Example:
```bash
10.128.0.0/20
0.0.0.0/0
```
--- 

## Default Routes in a VPC Network

By default, every VPC network includes routes that allow instances in the same network to communicate.

Routes are also created when subnets are created.

These subnet routes allow VMs in the same VPC network to communicate, even across subnets.

Most VPC networks also have a default route:
```bash
0.0.0.0/0
```
The default route directs traffic to destinations outside the VPC network, such as the internet.

---

## Route Selection

Routes apply to traffic leaving a VM.

This is called egress traffic.

Google Cloud selects the most specific matching route.

Example:
```text
10.128.1.0/24 is more specific than 10.128.0.0/16
```
If two routes match, Google Cloud prefers the more specific destination range.

---

## Instance Routing Tables

Google Cloud creates read-only routing tables for each VM instance.

A route applies to an instance when:

- The route belongs to the same VPC network
- The route target matches the VM
- Or the route has no target tags and applies to all instances in the network

Each VM sends packets to the VPC virtual router.

The VPC virtual router checks the VM's routing table and forwards the packet to the correct next hop.
---

## Important Route Concept

Routes control packet direction.

Firewall rules control packet permission.
```text
VM sends packet
      ↓
Route chooses next hop
      ↓
Firewall rule must allow traffic
      ↓
Packet is delivered
```
---

## Firewall Rules

Google Cloud firewall rules protect VM instances from unapproved connections.

Firewall rules apply to the VPC network, but connections are allowed or denied at the instance level.

A VPC network functions as a distributed firewall.

Firewall rules can control:

- Ingress traffic
- Egress traffic
- Traffic between VMs
- Traffic from external sources
- Traffic to external destinations

---

## Stateful Firewall Rules

Google Cloud firewall rules are stateful.

This means that when a connection is allowed, return traffic for that connection is also allowed.

Example:

If an ingress rule allows a client to connect to a VM on port 80, the return traffic from the VM back to the client is automatically allowed.

---

## Implied Firewall Rules

Every VPC network has implied firewall rules.

### Implied Deny Ingress
Inbound traffic is denied unless an ingress firewall rule allows it.

```bash
Ingress default = deny
```

### Implied Allow Egress
Outbound traffic is allowed unless an egress firewall rule denies it.
```bash
Egress default = allow
```
--- 

## Default Network vs Manually Created Network

The default VPC network includes preconfigured firewall rules.

These rules allow common traffic, including communication between instances in the default network.

Manually created VPC networks do not automatically include the same preconfigured firewall rules.

For custom VPC networks, you usually need to create firewall rules yourself.

---

## Firewall Rule Components

A firewall rule is made of several parts.

### Direction
Determines whether the rule applies to inbound or outbound traffic.
```bash
Ingress = inbound traffic
Egress = outbound traffic
```

### Source or Destination

For ingress rules, define the source.

Example:
```bash
Source CIDR range: 0.0.0.0/0
```

For egress rules, define the destination.

Example:
```bash
Destination CIDR range: 10.10.0.0/16
```

### Protocol and Port

Firewall rules can allow or deny specific protocols and ports.

Examples:
```bash
tcp:22
tcp:80
tcp:443
icmp
```

### Action
The action determines whether matching traffic is allowed or denied.
```text
allow
deny
```

### Priority
Priority controls the order in which rules are evaluated.

Lower numbers have higher priority.

Example:
```text
Priority 1000 is evaluated before priority 2000
```
The first matching rule is applied.

### Rule Assignment
Firewall rules can apply to all instances or only specific instances.

Rules can be assigned using:

- Network tags
- Service accounts
- Target instances

---

## Egress Firewall Rules

Egress firewall rules control outbound connections started from inside the VPC network.

Egress rules can match:

- Destination CIDR ranges
- Protocols
- Ports

Egress allow rules permit matching outbound traffic.

Egress deny rules block matching outbound traffic.

Example use cases:

- Block VMs from reaching unauthorized external IP ranges
- Prevent VMs from connecting to restricted internal ranges
- Limit outbound traffic to approved ports only

--- 

Ingress Firewall Rules

Ingress firewall rules control inbound connections coming into VM instances.

Ingress rules can match:

- Source CIDR ranges
- Protocols
- Ports

Ingress allow rules permit matching inbound traffic.

Ingress deny rules block matching inbound traffic.

Example use cases:

- Allow SSH from a trusted admin IP range
- Allow HTTP or HTTPS to a web server
- Block access from untrusted networks
- Restrict VM-to-VM communication inside the same VPC

---

## Route vs Firewall Rule
| Concept	| Route	| Firewall Rule |
| ------- | ----- | ------------- |
| Main purpose |	Chooses where traffic goes	| Allows or denies traffic |
| Matches by	| Destination IP range	| Source/destination, protocol, port |
| Applies to	| Egress traffic leaving a VM	| Ingress or egress traffic |
| Uses CIDR	| Yes	| Yes |
| Required for traffic?	| Yes	| Yes |
| Example	| Send 0.0.0.0/0 to internet gateway	| Allow tcp:80 from 0.0.0.0/0 |

---

## ACE Exam Notes
- A route maps an IP range to a destination or next hop.
- Routes match packets by destination IP address.
- Routes apply to traffic leaving a VM.
- The most specific matching route is used.
- Subnet routes allow VMs in the same VPC network to communicate.
- The default route 0.0.0.0/0 sends traffic to destinations outside the VPC.
- A route alone does not guarantee packet delivery.
- Firewall rules must also allow the traffic.
- VPC networks function as distributed firewalls.
- Firewall rules are applied to the network, but enforced at the instance level.
- Firewall rules are stateful.
- Implied ingress rule denies inbound traffic.
- Implied egress rule allows outbound traffic.
- Ingress rules control inbound connections.
- Egress rules control outbound connections.
- Ingress rules use source CIDR ranges.
- Egress rules use destination CIDR ranges.
- Firewall rule priority determines which matching rule is applied first.
- Lower priority numbers are evaluated first.
- The default VPC network includes preconfigured firewall rules.
- Manually created VPC networks require you to create needed firewall rules.
---

## Takeaway

>Routes decide where packets should go.
>
>Firewall rules decide whether packets are allowed.
>
>Google Cloud uses subnet routes, default routes, and custom routes to move traffic through a VPC network.
>
>Firewall rules protect VM instances from unauthorized ingress and egress connections.
>
>For traffic to succeed, both routing and firewall rules must permit the flow.
