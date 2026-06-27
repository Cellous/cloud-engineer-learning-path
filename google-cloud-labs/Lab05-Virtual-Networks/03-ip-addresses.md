# IP Addresses

## Objective

Understand how Google Cloud assigns internal and external IP addresses to Compute Engine VM instances.

---

## Internal IP Addresses

Every Compute Engine VM network interface receives a primary internal IP address.

Internal IP addresses are used for private communication inside a VPC network.

Characteristics:

- Required for VM network communication
- Allocated from the subnet IP range
- Automatically assigned if no specific address is selected
- Can be ephemeral or static
- Not publicly routable from the internet
- Used for private communication between resources in the VPC network

Google Cloud can automatically assign an internal IP address from the subnet range. If a fixed internal address is required, you can reserve a static internal IP address or promote an existing ephemeral internal IP address to static.

---

## External IP Addresses

External IP addresses are optional.

Use an external IP address when a VM needs direct public internet access or must be reachable from the internet.

External IP addresses are publicly routable. Resources with external IP addresses can communicate with the public internet.

Types:

### Ephemeral External IP

- Assigned automatically when requested
- Comes from Google Cloud's public IP address pool
- Does not persist beyond the life of the resource
- May be released when the resource is stopped or deleted

### Static External IP

- Reserved by your project
- Remains assigned to the project until released
- Useful when a service needs a fixed public address
- Can cost more when reserved but not attached to a resource

---

## Cloud NAT Note

A VM does not always need an external IP address for outbound internet access.

Cloud NAT can allow VMs without external IPv4 addresses to reach IPv4 destinations on the internet. Cloud NAT supports outbound connections and return traffic, but it does not allow unsolicited inbound connections from the internet.

---

## Bring Your Own IP (BYOIP)

Bring Your Own IP allows an organization to bring its own public IP address ranges to Google Cloud.

Requirements:

- Own a public IP address range
- Provision the range into Google Cloud
- Use the imported addresses with supported Google Cloud resources

BYOIP addresses are managed similarly to Google-provided external IP addresses after they are imported.

---

## Internal DNS

Google Cloud automatically creates internal DNS records for Compute Engine instances.

Default internal DNS mapping:

```text
VM name -> Internal IP address
