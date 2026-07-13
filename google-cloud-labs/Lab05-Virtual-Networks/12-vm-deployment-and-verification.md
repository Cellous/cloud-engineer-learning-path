# 12. Virtual Machine Deployment

## Why VM Creation Failed

- No local network available
- Deleting the default VPC removes available networks
- Every Compute Engine VM requires a VPC

![Compute Engine required VPC](screenshots/03-no-network-error.png)

---

## Create managementnet-us-vm

![Instruction allow](screenshots/12-managementnet-firewall-rule.png)

![Settings](screenshots/13-firewall-rule-properties.png)

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

## Equivalent gcloud Command

![Equivalent gcloud command](screenshots/07-equivalent-gcloud-command.png)
The Console automatically generates the CLI command.
---

## Verify VM Deployment
![VM Instances](screenshots/04-vm-instances.png)

> **ACE Exam Tip**
>
> The Google Cloud Console can generate the equivalent `gcloud` command for many actions. This is a useful way to learn the CLI while working in the graphical interface.
