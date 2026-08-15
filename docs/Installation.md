# Phase 1 – Base Operating System

## Install Linux Mint

Linux Mint 22.3 Cinnamon was selected as the operating system because it provides:

- Ubuntu/Debian package compatibility
- Long-term support
- Low hardware requirements
- Stable desktop environment
- Extensive community documentation

After installation, the system was updated:
sudo apt update
sudo apt upgrade -y


### Phase 2 — Hardware Validation & Firmware

# Phase 2 – Hardware Validation and Firmware Update

During initial deployment, the server reported only approximately 3.2 GB of available RAM despite having 8 GB physically installed.

The system was investigated through:

- BIOS hardware information
- Linux hardware and memory information
- Windows Task Manager
- Individual RAM module testing
- RAM reseating
- BIOS firmware update

The HP EliteDesk 705 G2 Desktop Mini BIOS was updated to the available N26 release.

After reseating the DDR3 memory modules, the system correctly detected both RAM modules and approximately 7 GB of usable memory under Windows.

Detailed investigation can be found in:
docs/Troubleshooting.md


### Phase 3 — Network Configuration

# Phase 3 – Network Configuration

## Assign Static IP Address

A static IP address was reserved through the home router to ensure the Home SOC server maintains a consistent network address.

This prevents monitoring agents from losing connectivity due to DHCP address changes.

Current SOC Server IP:
10.0.0.44


### Phase 4 — Git & Documentation


# Phase 4 – Git Version Control and Documentation

Git was configured to maintain version control for the Home SOC project.

The project documentation is maintained in a GitHub repository.

Current project structure includes:
README.md
docs/
configs/
scripts/
diagrams/


### Phase 5 — Wazuh Deployment


# Phase 5 – Wazuh SIEM Deployment

## Wazuh Installation

Wazuh was deployed on the Linux SOC server as the primary Security Information and Event Management (SIEM) platform.

The Wazuh installation deployed the required server components, including:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Wazuh API

Installed Wazuh version:
4.14.7


### Phase 6 — Windows Endpoint Integration

# Phase 6 – Windows Endpoint Integration

A Windows endpoint was enrolled into the Wazuh Manager.

The endpoint was configured with:
Agent Name: Windows-Main
Wazuh Manager: 10.0.0.44
Agent Group: default

### Phase 7 — Sysmon Deployment

# Phase 7 – Sysmon Deployment

## Sysmon Installation

Microsoft Sysmon was installed on the Windows endpoint to provide enhanced Windows security telemetry.

Sysmon was configured using a dedicated XML configuration.

The Sysmon service was verified as running:
Service: Sysmon64
Status: Running

### Phase 8 — Docker Deployment

# Phase 8 – Docker Deployment

Docker was installed on the Linux SOC server to provide a platform for deploying additional security tooling.

Docker installation was verified and configured so that the user can execute Docker commands without requiring `sudo`.

Docker will be used to support additional components of the Home SOC environment without unnecessarily modifying the base operating system.


# Current Lab Architecture

The current environment consists of:

                    ┌─────────────────────────┐
                    │     Windows Endpoint    │
                    │                         │
                    │   Wazuh Agent           │
                    │   Sysmon                │
                    │   Windows Event Logs    │
                    └────────────┬────────────┘
                                 │
                          Security Telemetry
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │     Home SOC Server     │
                    │                         │
                    │     Linux Mint          │
                    │     Wazuh Manager       │
                    │     Wazuh Indexer       │
                    │     Wazuh Dashboard     │
                    │     Wazuh API           │
                    │     Docker              │
                    └─────────────────────────┘

### Current Status

# Current Status

## Completed

- Linux Mint installation
- System updates
- Static IP configuration
- Git configuration
- GitHub repository setup
- BIOS firmware update
- RAM troubleshooting and reseating
- Wazuh Manager installation
- Wazuh Indexer installation
- Wazuh Dashboard installation
- Wazuh API deployment
- Wazuh Dashboard verification
- Windows Wazuh Agent deployment
- Windows endpoint enrollment
- Windows Event Log collection
- Sysmon installation
- Sysmon configuration
- Wazuh Sysmon event-channel configuration
- Docker installation

## In Progress

- Sysmon event visibility in Wazuh
- Validation of the complete endpoint telemetry pipeline
- Home SOC documentation

## Upcoming

- Sysmon event investigation
- Suricata IDS deployment
- Network security monitoring
- Attack simulation
- Detection engineering
- MITRE ATT&CK mapping
- Threat hunting
- Incident investigation
- Incident response documentation
- Portfolio documentation


# Project Roadmap

| Phase | Status |
|-------|--------|
| Base System Installation | ✅ Complete |
| Hardware Validation & Firmware | ✅ Complete |
| Network Configuration | ✅ Complete |
| Git & Documentation | ✅ Complete |
| Wazuh Deployment | ✅ Complete |
| Windows Endpoint Integration | ✅ Complete |
| Sysmon Deployment | ✅ Complete |
| Docker Deployment | ✅ Complete |
| Telemetry Validation | 🔄 In Progress |
| Network IDS | ⏳ Pending |
| Attack Simulation | ⏳ Pending |
| Detection Engineering | ⏳ Pending |
| Threat Hunting & Investigation | ⏳ Pending |
| Incident Response | ⏳ Pending |
| Portfolio Completion | ⏳ Pending |


# Lessons Learned

This project is being documented as an iterative learning environment.

Troubleshooting and lessons learned include:

- Diagnosing abnormal RAM detection
- Updating system firmware
- Testing individual RAM modules and slots
- Configuring a static network environment
- Deploying a SIEM on limited hardware
- Enrolling and troubleshooting Wazuh endpoints
- Configuring Windows Event Log collection
- Deploying Sysmon for enhanced endpoint telemetry
- Managing Linux services
- Using Docker for security tooling
- Troubleshooting communication between SOC components

Additional lessons will be documented as the project progresses.

This document will continue to evolve as additional components are installed throughout the project.
