# Home SOC Installation Guide

This document provides the installation and deployment process for building the Home Security Operations Center (Home SOC). It is intended to serve as a reproducible guide for rebuilding the environment from scratch.

---

# Project Overview

The objective of this project is to build a Home Security Operations Center capable of:

- Collecting endpoint logs
- Monitoring system activity
- Detecting malicious behavior
- Performing network intrusion detection
- Simulating cyber attacks
- Documenting the entire deployment process

---

# Hardware

## Home SOC Server

| Component | Specification |
|-----------|---------------|
| Model | HP EliteDesk 705 G2 Desktop Mini |
| CPU | AMD PRO A8-8600B |
| RAM | 8 GB DDR3 |
| Storage | SSD |
| Network | Ethernet |
| Operating System | Linux Mint 22.3 Cinnamon |

---

# Phase 1 – Base Operating System

## Install Linux Mint

Linux Mint 22.3 Cinnamon was selected as the operating system because it provides:

- Long Term Support (LTS)
- Ubuntu package compatibility
- Low hardware requirements
- Stable desktop environment
- Excellent documentation

After installation, the system was updated to the latest packages.

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Phase 2 – Network Configuration

## Assign Static IP Address

A static IP address was reserved through the home router to ensure the Home SOC server always receives the same IP address.

This prevents monitoring agents from losing connectivity due to DHCP address changes.

Current IP Address:

```
10.0.0.44
```

---

# Phase 3 – Git Version Control

Git was installed and configured to maintain version control for the project documentation.

Repository structure includes:

```
README.md
docs/
configs/
scripts/
diagrams/
```

The project is synchronized with GitHub to maintain version history throughout development.

---

# Phase 4 – Firmware Update

During deployment, the server reported only approximately 3 GB of usable RAM despite having 8 GB installed.

The following actions were performed:

- Updated the HP BIOS to the latest available release
- Verified memory detection under Linux
- Verified memory detection under Windows
- Reseated both DDR3 memory modules

After reseating the RAM, the system correctly detected approximately 7 GB of usable memory.

Detailed investigation can be found in:

```
docs/Troubleshooting.md
```

---

# Current Status

Completed

- Linux Mint installation
- System updates
- Static IP configuration
- Git configuration
- GitHub repository setup
- BIOS update
- RAM troubleshooting

In Progress

- Home SOC documentation

Upcoming

- Wazuh Installation
- Wazuh Dashboard
- Wazuh Manager
- Wazuh Indexer
- Windows Agent
- Sysmon
- Suricata IDS
- Attack Simulation
- Detection Engineering

---

# Project Roadmap

| Phase | Status |
|---------|--------|
| Base System Installation | ✅ Complete |
| Infrastructure Configuration | ✅ Complete |
| Documentation | 🔄 In Progress |
| Wazuh Deployment | ⏳ Pending |
| Endpoint Monitoring | ⏳ Pending |
| Network IDS | ⏳ Pending |
| Attack Simulation | ⏳ Pending |
| Detection Engineering | ⏳ Pending |
| Portfolio Completion | ⏳ Pending |

---

# References

- Linux Mint Documentation
- Wazuh Documentation
- Suricata Documentation
- Git Documentation
- HP EliteDesk 705 G2 Documentation

---

This document will continue to evolve as additional components are installed throughout the project.
