# VM Lifecycle
`
Create
   ↓
Provisioning
   ↓
Staging
   ↓
Running
`
Running can transition to:
```
Running
 │
 ├── Stop
 ├── Suspend
 ├── Repair
 ├── Reset
 ├── Delete
 └── Live Migration
```
## Provisioning

Resources are reserved.

- CPU
- Memory
- Disk

VM is not yet running.
---

## Staging

Google Cloud prepares the VM.

- Boot image
- IP Address
- Boot loader
- Networking
---

## Running

The VM is fully operational.

Available actions:

- SSH
- RDP
- Snapshots
- Metadata updates
- Live Migration
---

## Stopping

Shutdown scripts execute.

Approximate shutdown time:
```
90 seconds
```
---

## Terminated

CPU billing stops.

Still charged for:

- Persistent Disks
- Reserved IP Addresses

You can now:

- Resize machine
- Change machine type
- Restart

Cannot:

- Change boot image
---

## Repairing

Occurs when

- Hardware failure
- Maintenance issue

Notes

- No VM billing
- No SLA during repair
---

## Suspending

Memory is preserved.

Later
`
Resume
`
without full reboot.

## Reset

Similar to pressing the reset button on a physical computer.

- Memory cleared
- VM stays in Running state
---

## Live Migration

Moves a VM to another host without downtime.

Default maintenance behavior.
---

Availability Policies

Configure:

- Automatic Restart
- Live Migration
- Terminate on Host Maintenance
