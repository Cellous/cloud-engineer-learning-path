# VM Access

Google Cloud supports different methods of connecting to Linux and Windows virtual machines.
---

## Linux (SSH)
| Method               | Description                        |
| -------------------- | ---------------------------------- |
| Google Cloud Console | Browser-based SSH                  |
| Cloud Shell          | SSH using the Google Cloud SDK     |
| Local Computer       | SSH client with generated key pair |


### Requirements

- SSH Firewall Rule
- TCP Port 22
- SSH key pair (if connecting externally)

### Example
```
gcloud compute ssh vm-name
```
---

## Windows (RDP)
| Method                | Description           |
| --------------------- | --------------------- |
| Remote Desktop Client | Standard Windows RDP  |
| PowerShell            | Administrative access |


### Requirements

- Windows password
- Firewall rule
- TCP Port 3389
---

## Security Notes
- SSH uses public/private key authentication.
- RDP uses username/password authentication.
- Default VPC networks already include common SSH and RDP firewall rules.
