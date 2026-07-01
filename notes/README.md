## ACE Recognition Patterns

| Requirement | Usually Means |
|---|---|
| Lowest operational overhead | Autopilot |
| Full customization | Standard GKE |
| Event-driven | Cloud Functions |
| Containers | Cloud Run |
| Rolling updates | Managed Instance Groups |

## Naming Convention

Do not confuse the VPC network name with the VM name.

VPC Network
-----------
mynetwork

Virtual Machines
----------------
mynet-us-vm
mynet-notus-vm

The lab validator checks VM names separately from VPC names.
