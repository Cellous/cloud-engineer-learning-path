# Cloud DNS and Alias IP Ranges

## Objective

Understand the difference between Cloud DNS and Alias IP ranges in Google Cloud networking.

Cloud DNS provides managed DNS name resolution.

Alias IP ranges allow a VM network interface to use additional internal IP ranges for workloads such as containers, applications, and GKE Pods.

---

## Diagram

![Alias IP Range](diagrams/cloud-dns-alias-ip/alias-ip-range.png)

---

## Cloud DNS

Cloud DNS is Google Cloud's managed DNS service.

DNS translates human-readable names into IP addresses.

Example

```
www.example.com

↓

34.120.50.18
```
Cloud DNS can be used for public DNS zones and private DNS zones.
---

## Benefits

- Managed DNS service 
- Uses Google's global Anycast network 
- Low-latency DNS responses 
- High availability 
- Supports large numbers of DNS records 
- Can be managed through the Google Cloud Console 
- Can be managed with the `gcloud` CLI 
- Can be managed through APIs

---

## Cloud DNS vs Internal DNS
Cloud DNS and Compute Engine internal DNS are related, but they are not the same thing.

### Cloud DNS
Cloud DNS is a managed DNS service for creating and managing DNS zones and records.

It can be used for:
- Public DNS zones 
- Private DNS zones 
- Custom domain name resolution

### Compute Engine Internal DNS
It maps VM names to internal IP addresses inside the VPC network.

Example:
```text
vm-name -> internal IP address
```
Internal DNS is useful for VM-to-VM communication inside the same VPC network.

---

## Alias IP Ranges

Alias IP ranges allow one VM network interface to use additional internal IP addresses.

Instead of creating multiple network interfaces, one VM can have a primary internal IP address and one or more alias IP ranges.

Alias IP ranges are commonly used when multiple applications, containers, or Pods need their own internal IP addresses.

Example:
A VM has a primary internal IP address:
```bash
VM Primary IP
10.1.0.2
```
The VM is also assigned an alias IP range:
```bash
Alias IP Range
10.2.1.0/24
```
Applications or containers on the VM can use IP addresses from that alias range:
```bash
App A: 10.2.1.10
App B: 10.2.1.11
App C: 10.2.1.12
```
These alias IP addresses are internal addresses.

They are not public internet addresses.

---
## Where Alias IP Ranges Come From
Alias IP ranges are allocated from a subnet.

They can come from:
- The subnet's primary CIDR range
- A secondary CIDR range on the same subnet

For container-based workloads, secondary CIDR ranges are commonly used.

This is especially important for Google Kubernetes Engine because Pods can receive IP addresses from secondary ranges.

---

## Benefits of Alias IP Ranges
Alias IP ranges are useful for:
- Containers
- Google Kubernetes Engine
- Multiple applications on one VM
- Workloads that need separate internal IP addresses
- Avoiding unnecessary extra network interfaces
- Simplifying VPC routing for container workloads

---
## Key Concepts
### Cloud DNS
- Managed DNS service
- Resolves names to IP addresses
- Supports public and private zones
- Uses Google's global infrastructure
- Can be managed by UI, CLI, or API
### Internal DNS
- Automatically created for Compute Engine VMs
- Maps VM names to internal IP addresses
- Works inside the VPC network
- Useful for VM-to-VM communication
### Alias IP Range
- Additional internal IP range assigned to a VM network interface
- Comes from the same subnet as the VM network interface
- Can come from a primary or secondary subnet range
- Commonly used with containers and GKE
- Avoids creating extra network interfaces


---

# ACE Exam Notes

- Cloud DNS is Google's managed DNS service.
- Cloud DNS resolves domain names to IP addresses.
- Cloud DNS supports public and private DNS zones.
- Cloud DNS uses Google's global Anycast infrastructure.
- Compute Engine internal DNS automatically maps VM names to internal IP addresses.
- Internal DNS is scoped to the VPC network.
- Alias IP ranges allow a VM network interface to use additional internal IP addresses.
- Alias IP ranges are not external public IP addresses.
- Alias IP ranges come from subnet CIDR ranges.
- Alias IP ranges can come from a primary or secondary subnet range.
- Alias IP ranges are frequently used with containers and GKE.
- Alias IP ranges help avoid creating additional network interfaces.

---

## Takeaway

> Cloud DNS provides managed name resolution for Google Cloud DNS zones.
>
> Compute Engine internal DNS automatically maps VM names to internal IP addresses inside a VPC network.
>
> Alias IP ranges allow multiple applications, containers, or Pods on the same VM or node to use separate internal IP addresses.
>
>Alias IP ranges are internal addresses allocated from subnet CIDR ranges, not public external IP addresses.
