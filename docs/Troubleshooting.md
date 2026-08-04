## BIOS Memory Investigation

### Problem

Wazuh installer reported insufficient RAM.

### Investigation

- BIOS detects 8192 MB RAM.
- dmidecode detects both 4 GB DIMMs.
- lshw detects 8 GB installed.
- Linux kernel only reports ~3.2 GB usable.

### Current BIOS

N26 Version 02.10 (2016-08-08)

### Planned Fix

Update BIOS to the latest HP release (2020) and verify whether Linux recognizes the full 8 GB.
