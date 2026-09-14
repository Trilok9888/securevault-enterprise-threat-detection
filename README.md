# 🔐 SECURE VAULT
## Enterprise Security & Threat Detection Lab

SECURE VAULT is a hands-on cybersecurity lab designed to simulate an enterprise security environment for practicing endpoint monitoring, network analysis, threat detection, SIEM integration, incident investigation, and security automation.

The goal of this project is to build an end-to-end security monitoring environment rather than only installing individual security tools.

---

## 🎯 Project Objectives

SECURE VAULT is being built to demonstrate practical experience with:

- Enterprise network segmentation
- Windows endpoint security
- Sysmon telemetry
- Windows Event Logs
- Network traffic analysis
- SIEM integration
- Detection engineering
- Attack simulation
- Incident investigation
- Security automation
- Cloud security
- DevSecOps

---
# 📚 Project Documentation

Detailed technical documentation and validation evidence are available below:

| Area | Documentation |
|---|---|
| Architecture | [SECURE VAULT Architecture](docs/architecture.md) |
| Network Design | [SEC-LAB Network Design](docs/network-design.md) |
| Windows Endpoint | [Windows Security Endpoint](docs/windows-endpoint.md) |
| Sysmon Configuration | [Sysmon XML Configuration](configs/sysmon/sysmonconfig.xml) |
| Lab Evidence | [Networking & Sysmon Screenshots](docs/screenshots/README.md) |

## 🔎 Current Evidence

The repository includes validation evidence for:

- Static Windows endpoint IP configuration
- Host-to-VM connectivity
- Temporary NAT Internet connectivity
- Windows Defender Firewall rule
- Running Sysmon service
- Generated Sysmon security events

➡️ [View Lab Evidence](docs/screenshots/README.md)

---

# 🏗️ Lab Architecture

Current environment:

```text
                     Windows 11 Host
                    10.10.10.1
                         |
                         |
                SEC-LAB Host-Only Network
                    10.10.10.0/24
                         |
          +--------------+--------------+
          |                             |
          |                             |
 SEC-WIN11-01                     SEC-SIEM-01
 10.10.10.10                      10.10.10.20
 Windows Endpoint                 Linux / SIEM
      |                             [Planned]
      |
    Sysmon
      |
 Windows Event Logs
