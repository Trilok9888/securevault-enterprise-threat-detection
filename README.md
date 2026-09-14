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
