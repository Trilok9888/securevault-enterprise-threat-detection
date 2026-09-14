# SECURE VAULT Architecture

## Overview

SECURE VAULT is designed as a segmented enterprise security lab for endpoint monitoring, centralized logging, threat detection, investigation, and incident response.

The architecture is being built in phases so each component can be tested independently before being integrated into the complete security monitoring environment.

## Current Architecture

```text
                         Windows 11 Host
                            10.10.10.1
                                 |
                                 |
                   SEC-LAB Host-Only Network
                         10.10.10.0/24
                                 |
                 +---------------+---------------+
                 |                               |
                 |                               |
          SEC-WIN11-01                    SEC-SIEM-01
           10.10.10.10                     10.10.10.20
          Windows 11                        Linux
                 |                           [Planned]
                 |
              Sysmon
                 |
        Windows Event Logs
                 |
                 +--------------------------+
                                            |
                                            v
                                    Centralized SIEM
                                       [Planned]
                                            |
                           +----------------+----------------+
                           |                |                |
                        Alerts         Dashboards       Investigation
                           |                                 |
                           +---------------+-----------------+
                                           |
                                    Incident Response
```

## Network Segmentation

The lab uses a dedicated VirtualBox Host-Only network:

```text
SEC-LAB Network: 10.10.10.0/24
Host:            10.10.10.1
Windows:         10.10.10.10
SIEM:            10.10.10.20
```

This keeps security lab traffic separated from the host's normal network.

## Windows Endpoint Layer

The Windows endpoint currently provides:

- Windows 11 operating system
- Static SEC-LAB IP addressing
- Windows Defender Firewall
- Microsoft Sysmon
- Windows Event Logs
- PowerShell administration
- Endpoint telemetry generation

The endpoint acts as the primary monitored system in the lab.

## Telemetry Layer

Microsoft Sysmon provides enhanced endpoint telemetry including:

```text
Process Creation
Network Connections
File Creation
Registry Activity
DNS Queries
Process Tampering
```

This telemetry will later be forwarded to the centralized SIEM.

## SIEM Layer

The planned SIEM server will use:

```text
Hostname: SEC-SIEM-01
IP:       10.10.10.20
Platform: Linux
```

Its responsibilities will include:

- Centralized log collection
- Sysmon event ingestion
- Windows security log ingestion
- Security dashboards
- Detection rules
- Alert generation
- Threat hunting
- Event correlation

## Detection Engineering Layer

Future detection engineering exercises will include:

- Suspicious PowerShell activity
- Unusual process execution
- Network connection anomalies
- Credential-related activity
- Persistence techniques
- Registry modifications
- Suspicious DNS activity
- Process tampering

## Attack Simulation Layer

Controlled security simulations will be performed only against systems inside SECURE VAULT.

The purpose of these simulations is to generate realistic telemetry and validate detection coverage.

The workflow will follow:

```text
Attack Simulation
       |
       v
Endpoint Activity
       |
       v
Sysmon / Windows Logs
       |
       v
SIEM
       |
       v
Detection Rule
       |
       v
Security Alert
       |
       v
Investigation
       |
       v
Incident Response
```

## Automation Layer

Future automation will use PowerShell and Python for tasks such as:

- Log analysis
- IOC extraction
- Alert enrichment
- Incident triage
- Automated response
- Security reporting

## Planned Expansion

Later phases will extend SECURE VAULT with:

```text
Linux Security Monitoring
Additional Windows Endpoints
Detection Engineering
Threat Hunting
Attack Simulation
Incident Response
Python Automation
Cloud Security
DevSecOps Security
```

## Architecture Goal

The final goal is to demonstrate an end-to-end defensive security workflow:

```text
Endpoint
   ↓
Telemetry
   ↓
Centralized Logging
   ↓
Detection
   ↓
Alert
   ↓
Investigation
   ↓
Response
   ↓
Automation
```
