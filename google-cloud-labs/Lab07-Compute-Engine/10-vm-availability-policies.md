# VM Availability Policies

Availability Policies determine how a Compute Engine VM behaves during host maintenance,
hardware failures, or unexpected crashes.

---

## Automatic Restart

Automatically restarts the VM when:

- Host crash
- Hardware failure
- Maintenance event

Does NOT restart after:

- User-initiated stop
- User-initiated terminate
- Preemptible VM preemption

---

## On Host Maintenance

Determines what happens during host maintenance.

Options

- Live Migrate (Default)
- Terminate

---

## Live Migration

Default behavior for most Compute Engine VMs.

Benefits

- No reboot
- No downtime
- Workloads continue running
- VM moves to another physical host

Google automatically migrates the VM before maintenance begins.

---

## Metadata

Instance metadata records live migration events.

Useful for:

- Monitoring
- Troubleshooting
- Automation

---

## Exam Tips

✔ Automatic Restart
→ Crash recovery

✔ Live Migration
→ Hardware maintenance

✔ Terminate
→ Used when Live Migration isn't supported (GPU/TPU or certain machine types)
