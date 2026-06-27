# IP Address Mapping and DNS Resolution

## External IP Mapping

A Google Cloud VM is only aware of its internal IP address.

The external IP address is transparently mapped by the VPC network.

```
Internet
      │
External IP
      │
Google VPC
      │
Internal IP
      │
VM
```

Inside the VM:

```
ifconfig

10.142.0.2
```

The external public IP never appears inside the operating system.

---

# Internal DNS

Every Compute Engine instance automatically receives:

- Hostname
- Internal DNS record

Example

```
vm-1

↓

10.128.0.5
```

Google Cloud supports:

- Zonal DNS (recommended)
- Global DNS

---

## Internal FQDN

Format

```
hostname.zone.c.project-id.internal
```

Example

```
web-server.us-central1-a.c.demo-project.internal
```

---

## Metadata Server

Every VM has access to

```
169.254.169.254
```

The metadata server:

- Resolves internal DNS
- Supplies instance metadata
- Forwards public DNS queries

---

## External DNS

Public DNS records are NOT automatically created.

Administrators may publish DNS records using:

- Cloud DNS
- Third-party DNS providers

---

# ACE Exam Notes

✔ VM only knows its internal IP

✔ External IP is mapped by the VPC

✔ Hostname always resolves to the VM

✔ Zonal DNS is recommended

✔ Metadata Server

```
169.254.169.254
```

---

## Takeaway

Google Cloud automatically manages internal DNS for Compute Engine. External IP addresses are translated to internal addresses by the VPC, allowing applications inside the VM to operate using only private networking.
