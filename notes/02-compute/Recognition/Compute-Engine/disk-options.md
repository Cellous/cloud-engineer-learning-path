
# Compute Engine Disk Options

## Persistent HDD
- cheap
- bulk storage
- slower I/O

## Persistent SSD
- balanced performance
- higher random IOPS (Input/Output Operations Per Second).
- Production workloads

## Local SSD
- Does NOT persist if VM is terminated.
- extremely fast
- attached physically to host
- temporary
- high IOPS/low latency

## RAM Disk
- fastest
- volatile
- high risk of data loss

## Regional Persistent Disks
- Regional persistent disks replicate across zones.
  - HA (High Availability)
  - failover resilience 

## Performance Tradeoffs

## ACE Recognition Notes
- Local SSD = high performance but temporary
- Regional persistent disks = zone redundancy
- GPUs require compatible VM families
- Persistent SSD = production workloads
- HDD = cheaper bulk storage

## Diagnostic Question Lessons

- Local SSD provides high IOPS but is temporary.
- Persistent SSD is recommended for production workloads.
- Regional persistent disks provide zone redundancy.
- GPU support depends on machine family and zone availability.
