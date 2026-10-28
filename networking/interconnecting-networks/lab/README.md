# Configure Google Cloud HA VPN

## Lab Overview

This hands-on lab demonstrates how to configure a highly available VPN connection between two Google Cloud VPC networks.

One VPC represents the Google Cloud environment, while the second VPC simulates an on-premises network.

The lab uses:

- Google Cloud VPC
- Compute Engine
- HA VPN
- Cloud Router
- Border Gateway Protocol (BGP)
- Firewall rules
- Dynamic routing
- Global routing
- Redundant VPN tunnels

## Architecture

Two networks were configured:

### `vpc-demo`

- `vpc-demo-subnet1` — `10.1.1.0/24`
- `vpc-demo-subnet2` — `10.2.1.0/24`
- `vpc-demo-instance1`
- `vpc-demo-instance2`

### `on-prem`

The `on-prem` VPC simulated an external customer data center.

- `on-prem-subnet1` — `192.168.1.0/24`
- `on-prem-instance1`

## HA VPN Configuration

An HA VPN gateway and Cloud Router were created for each VPC.

Cloud Router autonomous system numbers:

```text
vpc-demo-router1  → ASN 65001
on-prem-router1   → ASN 65002
```

Two redundant VPN tunnels were configured between the gateways.

```text
vpc-demo                    on-prem
   │                           │
HA VPN                       HA VPN
   │                           │
Tunnel 0 ←────────────────→ Tunnel 0
Tunnel 1 ←────────────────→ Tunnel 1
   │                           │
Cloud Router               Cloud Router
   │                           │
 BGP                         BGP
```

## Dynamic Routing with BGP

BGP peers were configured for both VPN tunnels.

Link-local addresses from the `169.254.0.0/16` range were used for the BGP sessions.

Example:

```text
Tunnel 0
169.254.0.1 ↔ 169.254.0.2

Tunnel 1
169.254.1.1 ↔ 169.254.1.2
```

Dynamic routing allows network routes to be exchanged automatically through Cloud Router.

## Private Connectivity Test

From `on-prem-instance1`, private connectivity to `vpc-demo-instance1` was verified:

```text
Destination: 10.1.1.2

4 packets transmitted
4 packets received
0% packet loss
```

This confirmed that private traffic could travel between the two VPC networks through the HA VPN.

## Global Routing

The `vpc-demo` VPC routing mode was changed from regional to:

```text
GLOBAL
```

This allowed Cloud Router to advertise routes for subnets located in another region.

Connectivity from `on-prem-instance1` to `vpc-demo-instance2` was then verified:

```text
Destination: 10.2.1.2

2 packets transmitted
2 packets received
0% packet loss
```

## HA VPN Failover Test

One VPN tunnel was removed to simulate a tunnel failure.

Connectivity was then tested again from `on-prem-instance1` to `vpc-demo-instance1`.

```text
3 packets transmitted
3 packets received
0% packet loss
```

Traffic continued through the remaining VPN tunnel.

This demonstrated HA VPN redundancy and failover.

## Resource Cleanup

The lab also included manual deletion of cloud resources.

A dependency-aware cleanup sequence was used:

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

Manual cleanup is important in production cloud environments because unused resources can continue consuming resources or generating costs.

## Skills Demonstrated

- Creating custom VPC networks
- Creating regional subnets
- Deploying Compute Engine instances
- Configuring firewall rules
- Creating HA VPN gateways
- Creating redundant VPN tunnels
- Configuring Cloud Router
- Configuring BGP peers
- Working with BGP ASNs
- Using link-local BGP addresses
- Verifying private VPN connectivity
- Configuring global dynamic routing
- Testing HA VPN failover
- Cleaning up dependent Google Cloud resources

## Result

Successfully configured and tested a highly available Google Cloud VPN architecture using redundant VPN tunnels, Cloud Router, and BGP.

The final failover test confirmed continued connectivity with:

```text
3/3 packets received
0% packet loss
```
