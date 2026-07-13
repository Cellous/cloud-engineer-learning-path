
## Why VM creation failed

Deleting the default VPC removes all associated subnets and routes.

Because Compute Engine instances must be attached to a VPC network, Google Cloud prevents VM creation until another network exists.

The Networking tab reports:

"No local network available."

![No Network Error](screenshots/03-no-network-error.png)

![Create management VM](screenshots/14-create-management-vm.png)

![Management VM networking](screenshots/15-management-vm-networking.png)

![Create privatenet VM](screenshots/16-create-privatenet-vm.png)

![Equivalent gcloud command](screenshots/07-equivalent-gcloud-command.png)

![VM Instances](screenshots/04-vm-instances.png)
