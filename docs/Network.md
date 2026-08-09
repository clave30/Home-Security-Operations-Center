# Network Configuration

This document describes the network architecture of the Home Security Operations Center (Home SOC), including device roles, IP addressing, and future network expansion.

---

# Network Overview

The Home SOC is deployed on a home network and is designed to monitor endpoint activity while collecting security events from connected devices.

Current topology:

```
                Internet
                    │
                    │
             Home Router
                    │
        ┌───────────┴───────────┐
        │                       │
        │                       │
 Main Windows PC         Home SOC Server
                        (Linux Mint 22.3)
```

---

# Device Inventory

| Device | Purpose | Operating System |
|---------|---------|------------------|
| Home Router | Network Gateway | Vendor Firmware |
| Home SOC Server | Security Monitoring | Linux Mint 22.3 |
| Main Windows PC | Endpoint / Wazuh Agent (Planned) | Windows 10 |

---

# IP Addressing

| Device | IP Address | Assignment |
|---------|------------|------------|
| Home Router | (Gateway IP) | DHCP Gateway |
| Home SOC Server | 10.0.0.44 | Static Reservation |
| Main Windows PC | DHCP | Dynamic |

---

# Network Objectives

The network is designed to support:

- Security event collection
- Endpoint monitoring
- Intrusion detection
- Centralized logging
- Attack simulation
- Future expansion

---

# Planned Services

| Service | Status |
|----------|--------|
| Wazuh Manager | Planned |
| Wazuh Dashboard | Planned |
| Wazuh Indexer | Planned |
| Windows Agent | Planned |
| Sysmon | Planned |
| Suricata IDS | Planned |

---

# Planned Network Expansion

Future additions include:

- Additional Windows endpoint
- Linux endpoint
- Virtual machines for attack simulation
- Dedicated attacker machine
- Network intrusion detection using Suricata

Planned topology:

```
                    Internet
                        │
                    Home Router
                        │
        ┌───────────────┼───────────────┐
        │               │               │
        │               │               │
 Windows PC       Linux Home SOC     Test Machine
 (Agent)            (Wazuh)          (Attacker)
                        │
                 Suricata IDS
                        │
                 Security Dashboard
```

---

# Security Considerations

- Static IP reservation for the Home SOC server.
- Home SOC server dedicated to security monitoring.
- Documentation maintained through GitHub.
- Network will be expanded as additional security tools are deployed.

---

# Revision History

| Date | Change |
|------|--------|
| August 2026 | Initial network documentation created. |
