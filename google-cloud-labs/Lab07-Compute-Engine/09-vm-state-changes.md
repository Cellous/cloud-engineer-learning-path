# Changing VM States

| Action   | Result               |
| -------- | -------------------- |
| Reset    | Running → Running    |
| Reboot   | Running → Running    |
| Stop     | Running → Terminated |
| Start    | Terminated → Running |
| Shutdown | Running → Terminated |
| Delete   | VM Removed           |
| Suspend  | Running → Suspended  |

---

## Shutdown Scripts

Normal VM
```
≈90 seconds
```
Preemptible VM
```
≈30 seconds
```
After timeout
```
ACPI G3 Mechanical Off
```
is sent to the operating system.
--- 

## Patch Management

Google Cloud provides OS Patch Management.

### Capabilities

- Patch Compliance Reporting
- Patch Deployment
- Patch Approvals
- Scheduled Updates
- Pre/Post Patch Scripts
- Centralized Management
---

## Notes
- Patch management is available for both Linux and Windows.
- Premium Windows images include OS licensing and patch management support.
- Long-running VMs should be patched regularly to reduce security vulnerabilities.
