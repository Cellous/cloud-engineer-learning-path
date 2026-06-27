# Network Pricing
```text
Ingress = coming in
Egress = going out
Most surprise network costs come from egress and external IP addresses
```

## Objective

Understand the main Google Cloud network pricing concepts for ingress, egress, external IP addresses, and cost estimation.

---

## Pricing Warning

Google Cloud network pricing is subject to change.

Use these notes for concepts, not exact prices.

Always check the official Google Cloud pricing documentation or use the Google Cloud Pricing Calculator before estimating real costs.

---

## Big Idea

Google Cloud networking charges usually depend on:

- Traffic direction
- Source and destination
- Region
- Zone
- Whether internal or external IP addresses are used
- Whether another resource processes the traffic
- External IP address usage

---

## Ingress Traffic

Ingress means traffic coming into Google Cloud.

In many cases, ingress traffic has no charge.

However, charges can apply when another Google Cloud resource processes the traffic, such as a load balancer.

Example:

```text
Internet
   ↓
Google Cloud VM
```
This is ingress into Google Cloud.

---

## Egress Traffic

Egress means traffic leaving a Google Cloud resource.

Responses to requests usually count as egress.

Example:
```text
Google Cloud VM
   ↓
Internet
```
This is egress from Google Cloud.

Egress pricing depends on where the traffic is going.

---

## Common Network Pricing Patterns
### Usually No Charge

These are commonly shown as no charge in the training material:

- Ingress traffic
- Egress to the same zone using internal IP addresses
- Egress to some Google products
- Egress to some Google Cloud services within the same region

### Usually Charged

These traffic types are commonly charged:

- Egress between zones in the same region
- Egress between regions
- Egress to the internet
- Egress to the same zone when using an external IP address

## Internal IP vs External IP Pricing Effect

Traffic between VMs in the same zone should use internal IP addresses when possible.

Using the internal IP address can avoid some egress charges.

Using an external IP address can cause traffic to be treated differently because Google Cloud cannot always determine the VM zone from the external IP path.

---

## External IP Address Pricing

External IP addresses can create charges.

Google Cloud can charge for:

- Static external IP addresses
- Ephemeral external IP addresses
- External IP addresses attached to VM instances
- External IP addresses used by Cloud NAT

Unused reserved static external IP addresses can cost more than external IP addresses that are attached and in use.

## Static External IP Cost Warning

A reserved static external IP address can continue to cost money if it is not attached to a resource.

Example:
```text
Reserved static external IP
        ↓
Not attached to VM or forwarding rule
        ↓
Possible higher charge
```
Cost-control habit:
```text
If you reserve it, use it or release it.
```
---

## Pricing Calculator

Use the Google Cloud Pricing Calculator to estimate costs before deploying resources.

The calculator can estimate costs for combinations of services such as:

- Compute Engine
- Cloud Network
- VM machine type
- Region
- Monthly egress traffic
- Time frame
- Currency

Google’s calculator lets you add and configure Google Cloud products to create a shareable cost estimate.

---

## Example Estimate Scenario

A network estimate might include:
```text
Compute Engine:
n1-standard-1
Region:
us-central1
Network:
100 GB monthly egress
Destination:
Americas and EMEA
```
The calculator returns an estimated cost based on the selected resources and usage.

---

## Cost-Control Habits

Use these habits to reduce surprise charges:

- Prefer internal IP addresses for private VM-to-VM communication
- Avoid unnecessary external IP addresses
- Release unused static external IP addresses
- Watch egress between zones and regions
- Use the pricing calculator before building
- Review billing reports after labs
- Set budgets and alerts

---

## Key Concepts
### Ingress
- Traffic entering Google Cloud
- Often no charge
- Can be charged if processed by another resource
### Egress
- Traffic leaving a Google Cloud resource
- Often charged
- Depends on destination, zone, region, and network path
### Internal IP Traffic
- Used for private communication
- Can reduce cost compared with external IP paths
### External IP Address
- Public address
- Can be static or ephemeral
- Can create hourly charges
### Pricing Calculator
- Estimates Google Cloud costs before deployment
- Useful for planning and budgeting

---

## ACE Exam Notes
- Ingress means traffic coming into Google Cloud.
- Egress means traffic leaving a Google Cloud resource.
- Ingress is often no charge, but exceptions exist.
- Responses to requests count as egress.
- Egress is commonly charged.
- Egress pricing depends on source, destination, region, and traffic path.
- Egress to the same zone using internal IP addresses can avoid some charges.
- Egress using external IP addresses can be charged even when resources are in the same zone.
- External IP addresses can create charges.
- Static and ephemeral external IP addresses can be charged.
- Reserved but unused static external IP addresses can cost more than in-use external IP addresses.
- Use the Google Cloud Pricing Calculator to estimate costs.
- Pricing changes, so always check official pricing documentation.
---
## Takeaway

> Ingress is traffic entering Google Cloud.
>
> Egress is traffic leaving a Google Cloud resource.
>
> Egress is where many network charges appear.
>
> Internal IP communication is usually preferred for private VM-to-VM traffic.
>
> External IP addresses can create hourly charges.
>
> Always estimate costs with the Google Cloud Pricing Calculator before deploying real workloads.
