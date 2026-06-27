# Cloud DNS and Alias IP Ranges

## Cloud DNS

Cloud DNS is Google's managed authoritative DNS service.

It translates domain names into IP addresses.

Example

```
www.example.com

↓

34.120.50.18
```

---

## Benefits

- Managed service
- Global Anycast network
- Low latency
- 100% uptime SLA
- Millions of DNS records
- UI
- CLI
- API

---

## Alias IP Ranges

Alias IPs allow one VM to use multiple internal IP addresses.

Instead of creating multiple network interfaces, multiple applications or containers can each receive their own IP.

Example

```
VM

Primary IP
10.1.0.2

↓

Alias Range

10.2.1.0/24
```

Applications

```
Container A

10.2.1.10

Container B

10.2.1.11

Container C

10.2.1.12
```

---

## Benefits

- Kubernetes
- Containers
- Multiple applications
- Simpler networking
- No additional NICs required

---

# ACE Exam Notes

✔ Cloud DNS is managed by Google

✔ Uses Google's global Anycast network

✔ Alias IPs come from subnet CIDR ranges

✔ Alias IPs avoid creating additional NICs

✔ Frequently used with GKE

---

## Takeaway

Cloud DNS provides scalable global name resolution, while Alias IP Ranges allow multiple services running on the same VM to communicate using separate internal IP addresses.
