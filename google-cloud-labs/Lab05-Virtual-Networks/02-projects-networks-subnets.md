# Subnet

Default = Auto Mode

Auto Mode
  /20 default
  /16 maximum

Custom Mode
  Full control

Auto → Custom = Yes
Custom → Auto = No
---

# Demo 03 – Expand a Subnet

## Objective

Learn how to expand a custom VPC subnet without interrupting running virtual machines.

---

## Diagram
```text
diagrams/subnet-expansion-no-downtime/
├── subnet-expansion-no-downtime.drawio
├── subnet-expansion-no-downtime.png
└── subnet-expansion-no-downtime.svg
```
Figure 1 – Subnet Expansion Without Downtime

---

## Why Expand a Subnet?

As more VM instances are created, a subnet may eventually exhaust its available IP addresses.

Google Cloud allows administrators to expand a subnet's CIDR range without shutting down running workloads.

---

## Initial Configuration

| Setting       | Value         |
| ------------- | ------------- |
| Network Type  | Custom VPC    |
| Original CIDR | `10.0.0.0/29` |
| Running VMs   | 4             |
| Available IPs | Exhausted     |

A `/29` subnet contains 8 total IP addresses.

Google Cloud reserves 4 addresses, leaving only 4 usable IP addresses for VM instances.
---

## Demonstration

The instructor attempted to create a fifth VM.

Result:
```
VM5
    ↓
IP space exhausted
```
-Attempting to create a fifth VM fails because no IP addresses remain. 
-In other words, the deployment failed because every usable IP address had already been assigned.

Error:

```
IP space exhausted
```

---

## Expanding the Subnet

The subnet is edited from:

```
10.0.0.0/29
```

to

```
10.0.0.0/23
```

The change completes while all existing VM instances remain online.

During the expansion:

- VM1 remained online
- VM2 remained online
- VM3 remained online
- VM4 remained online

No VM restart occurred.

No downtime occurred.

---

## Result

After the subnet expansion:

- Existing workloads continued running.
- The subnet immediately had additional IP addresses.
- VM5 was successfully created using the newly available address space.

---
## Auto Mode VPC Network

When an Auto Mode VPC network is created, Google Cloud automatically provisions one subnet in every supported region.

This eliminates the need to manually create subnets during initial deployment.

### Example

![Auto Mode VPC Subnets](screenshots/auto-mode-subnets-by-region.png)

### Observations

- One subnet is created for each Google Cloud region.
- Each subnet receives a predefined CIDR block (for example, 10.128.0.0/20).
- The network operates in IPv4 single-stack mode by default.
- Auto Mode is convenient for learning and small deployments but is generally not recommended for production environments.
---

# Key Concepts

- Google Cloud supports live subnet expansion.
- Existing VM instances remain online during expansion.
- Expanding a subnet does not require VM restarts.
- Expanded CIDR ranges must not overlap other subnet ranges within the VPC.
- CIDR expansion is one-way. In that, Subnet expansion cannot be reversed.
- The new subnet range must be larger than the original range.

---

# ACE Exam Notes

✔ Custom VPC networks allow subnet expansion.

✔ Existing workloads remain online.

✔ No VM downtime is required.

✔ New subnet ranges cannot overlap existing subnet ranges.

✔ CIDR expansion cannot be reversed.

✔ Larger subnet = More available VM IP addresses.

---
# Diagram Walkthrough
```
Custom Subnet
      │
10.0.0.0/29
      │
 ├── VM1
 ├── VM2
 ├── VM3
 └── VM4

Attempt VM5
      │
      ▼
IP Exhausted
      │
Expand Subnet
      │
10.0.0.0/23
      │
 ├── VM1
 ├── VM2
 ├── VM3
 ├── VM4
 └── VM5 ✓
```

# Example

Before

```
10.0.0.0/29
```

↓

After

```
10.0.0.0/23
```

VM Deployment

```
VM1 ✔
VM2 ✔
VM3 ✔
VM4 ✔
VM5 ✔ (after subnet expansion)
```

## Takeaway

> **Key Point**
>
> Google Cloud supports **live subnet expansion**, allowing administrators to increase available IP addresses **without restarting existing VM instances or causing downtime**. After the expansion completes, new VM deployments can immediately use the additional IP address space.

---

## Diagram Information

Author: Marcellous Searcy

Tool: diagrams.net (draw.io)

Files:
- subnet-expansion-no-downtime.drawio
- subnet-expansion-no-downtime.svg
- subnet-expansion-no-downtime.png

Purpose:
Illustrates live subnet expansion in a Custom VPC without interrupting running VM instances.
