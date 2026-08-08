# Troubleshooting Log

This document records issues encountered during the development of the Home Security Operations Center (Home SOC) and how they were resolved.

---

# Issue 001 – Wazuh Installation Failed Due to Insufficient RAM

**Date:** August 2026

## Problem

The Wazuh installer stopped during the hardware verification stage with an error indicating that the system did not meet the minimum memory requirements.

## Environment

- Hardware: HP EliteDesk 705 G2 Mini
- CPU: AMD PRO A8-8600B
- RAM Installed: 8 GB DDR3 (2 × 4 GB)
- Operating System: Linux Mint 22.3

## Symptoms

- Wazuh installer reported approximately 3 GB of available RAM.
- Linux reported:

```bash
free -h
```

Only around 3.2 GB of usable memory.

Windows Task Manager also reported:

- Installed Memory: 8 GB
- Usable Memory: 3.4 GB
- Hardware Reserved: 4.6 GB

## Investigation

Performed the following diagnostics:

- Verified RAM in BIOS
- Verified memory using `dmidecode`
- Verified memory using `lshw`
- Updated HP BIOS to the latest available version
- Tested memory detection under Windows
- Compared results with another identical HP EliteDesk
- Reseated both DDR3 memory modules

## Root Cause

One or both memory modules were not making proper electrical contact with the motherboard.

Although both modules were detected by the firmware, excessive memory was being hardware reserved, leaving only about 3 GB available to the operating system.

## Resolution

Reseated both RAM modules.

## Result

Before:

- Installed RAM: 8 GB
- Usable RAM: ~3.4 GB
- Hardware Reserved: 4.6 GB

After:

- Installed RAM: 8 GB
- Usable RAM: ~6.9 GB
- Hardware Reserved: ~1.1 GB

## Lessons Learned

- Firmware detection does not always guarantee usable system memory.
- Verify hardware before assuming an operating system or application issue.
- Compare behavior across multiple operating systems when troubleshooting hardware.
