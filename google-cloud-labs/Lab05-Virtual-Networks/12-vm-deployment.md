# 12. Virtual Machine Deployment

## Why VM Creation Failed

- No local network available
- Deleting the default VPC removes available networks
- Every Compute Engine VM requires a VPC

![Compute Engine required VPC](screenshots/03-no-network-error.png)

---

## Create managementnet-us-vm

![VM Instances](screenshots/04-vm-instances.png)

Configuration

- Name
- Region
- Zone
- Machine Type
- Debian 12

![Create management VM](screenshots/14-create-management-vm.png)

Networking

- managementnet
- managementsubnet-us

![Management VM networking](screenshots/15-management-vm-networking.png)

---

## Create privatenet-us-vm

Cloud Shell command

```bash
gcloud compute instances create privatenet-us-vm ...
```

![Create privatenet VM](screenshots/16-create-privatenet-vm.png)

![Equivalent gcloud command](screenshots/07-equivalent-gcloud-command.png)
