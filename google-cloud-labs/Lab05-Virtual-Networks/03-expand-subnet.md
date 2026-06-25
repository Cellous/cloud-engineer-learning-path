# Demo 03 – Expand a Subnet

## Objective

Learn how to expand a custom VPC subnet without interrupting running workloads.

---

## Why Expand a Subnet?

A subnet can run out of available IP addresses as additional VM instances are created.

Google Cloud allows subnet expansion without shutting down virtual machines.

---

## Demo Summary

### Initial Configuration

- Custom VPC subnet
- CIDR: `10.0.0.0/29`
- Four VM instances running

Attempting to create a fifth VM fails because no IP addresses remain.

Error:

```
IP space exhausted
```

---

## Subnet Expansion

The subnet is edited from:

```
10.0.0.0/29
```

to

```
10.0.0.0/23
```

The change completes while all existing VM instances remain online.

---

## Result

After the subnet expansion:

- Existing VMs continue running
- No downtime occurs
- New VM deployment succeeds
- Additional IP addresses become available

---

# Key Concepts

- Google Cloud supports live subnet expansion.
- Existing workloads continue running.
- Expanding a subnet does not require VM restarts.
- Expanded IP ranges cannot overlap other subnet ranges.
- Subnet expansion cannot be reversed.

---

# ACE Exam Notes

✔ Expand subnet without downtime

✔ Existing VM instances remain online

✔ Custom mode provides full subnet control

✔ New subnet range must not overlap existing ranges

✔ Subnet expansion is one-way

---

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
