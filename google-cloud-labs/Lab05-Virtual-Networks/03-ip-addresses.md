# IP Addresses

## Objective

Understand how Google Cloud assigns internal and external IP addresses to VM instances.

---

## Internal IP Addresses

Every VM receives an Internal IP address.

Characteristics

- Assigned automatically by DHCP
- Allocated from the subnet IP range
- DHCP lease renews every 24 hours
- Registered automatically in the network DNS
- Used for private communication inside the VPC

---

## External IP Addresses

External IP addresses are optional.

Use an external IP when a VM must communicate with the Internet.

Types

### Ephemeral

- Assigned automatically
- Comes from Google's public IP pool
- May change if released

### Static

- Reserved by your project
- Remains the same until released
- Charged if reserved but unused

---

## Bring Your Own IP (BYOIP)

Organizations may advertise their own public IP ranges through Google Cloud.

Requirements

- Own a public IPv4 block
- Minimum size: /24

---

## DNS

Google Cloud automatically registers

VM Name → Internal IP

DNS works only inside the same VPC network.

It cannot resolve VM names located in another VPC network.

---

## Key Concepts

Internal IP

- Required
- Private communication
- DHCP assigned

External IP

- Optional
- Internet access
- Ephemeral or Static

---

## ACE Exam Notes

✔ Every VM receives an internal IP.

✔ External IPs are optional.

✔ Internal IPs come from the subnet.

✔ DNS is scoped to the VPC network.

✔ Static external IPs cost more if reserved but not attached.

✔ BYOIP requires at least a /24 public block.

---

## Takeaway

> Every Google Cloud VM receives an internal IP address.
>
> External IP addresses are optional and can be ephemeral or static.
>
> Internal communication uses private subnet addresses while Internet access uses external addresses.
