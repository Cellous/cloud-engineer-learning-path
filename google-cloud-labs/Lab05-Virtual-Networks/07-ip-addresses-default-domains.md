# IP Addresses for Default Domains

## Objective

Understand how Google publishes IP address ranges for Google services and Google Cloud resources.

---

## Overview

Google publishes official IP range files that describe the IP prefixes it announces to the internet.

These files help administrators identify Google public IP ranges and Google Cloud customer-usable external IP address ranges.

This is different from checking the internal or external IP address assigned to a single VM.

---

## Published IP Range Files

Google provides several files for IP range information.

### cloud.json

`cloud.json` provides a JSON representation of Google Cloud IP address ranges organized by region.

Use this when you need to identify Google Cloud customer-usable global and regional external IP ranges.

### cloud_geofeed

`cloud_geofeed` provides IP geolocation information in a standard geofeed format.

This file is shared with third-party IP geolocation providers.

### goog.json and goog.txt

`goog.json` and `goog.txt` include Google public prefixes in CIDR notation.

These files represent Google public IP prefixes.

---

## CIDR Notation

CIDR notation is used to describe IP address ranges.

Example:

```text
34.0.0.0/8
```
The `/8` portion identifies how much of the address is the network prefix.

CIDR ranges are commonly used in:

- Firewall rules
- Routing
- Access control
- IP allowlists
- Network planning

### Why These Files Matter

These files can be useful when administrators need to:

- Identify Google public IP ranges
- Build firewall allowlists
- Understand Google Cloud external IP ranges
- Review regional Google Cloud IP ranges
- Support Private Google Access configuration
- Work with IP geolocation providers

---

## Important Distinction

Published Google IP range files are not the same as a VM's assigned IP address.

### VM IP Address

A VM has:

- Internal IP address
- Optional external IP address

### Published Google IP Range Files

Google publishes:

- Google public IP prefixes
- Google Cloud customer-usable external IP ranges
- Geofeed data for IP location providers

---

## ACE Exam Notes

- Google publishes IP ranges in JSON and TXT formats.
- cloud.json lists Google Cloud customer-usable external IP address ranges.
- cloud.json organizes Google Cloud IP ranges by region.
- cloud_geofeed provides geolocation data for Google Cloud IP ranges.
- goog.json and goog.txt include Google public prefixes in CIDR notation.
- These files replace the older _spf.google.com TXT record method for listing Google IP addresses.
- CIDR notation is used to represent IP ranges.
- These files are useful for firewall rules, allowlists, routing, and Private Google Access planning.

## Takeaway

>Google publishes official IP range files for Google and Google Cloud addresses.
>
>cloud.json is used for Google Cloud customer-usable external IP ranges.
>
>goog.json and goog.txt list Google public prefixes in CIDR notation.
>
>These files describe Google-wide IP ranges, not the IP address assigned to one VM.
