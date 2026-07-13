# Lessons Learned

## Learning Tip

Whenever possible, click **Equivalent command line**.

This shows the gcloud command that performs the same task as the Cloud Console.

Benefits

- Learn the CLI automatically
- Understand Infrastructure as Code
- Easier automation later
- Better preparation for the ACE exam

## Key Concepts

- Auto Mode VPCs automatically create one subnet in every region.
- Custom Mode VPCs only contain the subnets that you create.
- Firewall rules are attached to VPCs, not directly to VMs.
- VM instances inherit firewall rules from their VPC.
- Internal IP communication depends on routing within the VPC.
- External connectivity depends on firewall rules.
- Google-managed Internet Gateway provides Internet access.
- Cloud Shell provides CLI management using gcloud.

## Commands Used

`gcloud compute networks list`

`gcloud compute networks subnets list`

`gcloud compute firewall-rules list`

`gcloud compute instances list`

`ping -c 3 <ip-address>`

`gcloud compute ssh <vm-name>`

## Skills Demonstrated

- VPC Design
- Subnet Planning
- Firewall Configuration
- Compute Engine
- Cloud Shell
- Linux Networking
- Network Verification
- Microsoft Visio Documentation
