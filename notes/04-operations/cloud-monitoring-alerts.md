# Cloud Monitoring Alert Policies

## Alert Components
- Resource
- Metric
- Threshold
- Duration
- Notification Channel

## Trigger Types
- Any time series violates
- All time series violate
- Percent of time series violate

## Common ACE Examples
- CPU Utilization > 60%
- Disk Usage > 80%
- Memory Usage > 90%

## Recognition Patterns

## Simple ACE Recognition Pattern
- Resource = VM Instance
- Metric = CPU Utilization
- Trigger = Any time series violates
- Threshold = Above X%
- Duration = Y minutes

## CPU Load
CPU Load = number of runnable processes
- Example: Load = 4.2
- Not a percentage.
