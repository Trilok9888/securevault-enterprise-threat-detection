# SECURE VAULT - Lab Evidence

This directory contains sanitized screenshots that demonstrate the implementation and validation of the SECURE VAULT cybersecurity lab.

Sensitive information such as usernames, host paths, personal IP addresses, credentials, tokens, and unrelated host-network traffic should be removed before screenshots are published.

## Evidence Categories

### 1. Windows Endpoint

Planned evidence:

```text
windows/
├── windows-desktop.png
├── vm-configuration.png
└── guest-additions.png
```

These screenshots demonstrate:

- Windows 11 endpoint deployment
- VirtualBox VM configuration
- Guest Additions installation
- Endpoint readiness

---

### 2. SEC-LAB Networking

Planned evidence:

```text
networking/
├── static-ip.png
├── host-to-vm-ping.png
├── host-only-adapter.png
└── internet-connectivity-test.png
```

These screenshots demonstrate:

- SEC-LAB Host-Only network configuration
- Static endpoint address `10.10.10.10`
- Host-to-endpoint communication
- Controlled NAT Internet access
- Successful connectivity validation

---

### 3. Sysmon Telemetry

Planned evidence:

```text
sysmon/
├── sysmon-installation.png
├── sysmon-service-running.png
└── sysmon-event-log.png
```

These screenshots demonstrate:

- Microsoft Sysmon installation
- Sysmon configuration validation
- Running Sysmon service
- Security event generation
- Windows endpoint telemetry

---

## Current Evidence Status

```text
[✓] Windows endpoint deployed
[✓] Static networking configured
[✓] Host-to-VM connectivity verified
[✓] Temporary NAT connectivity verified
[✓] Sysmon installed
[✓] Sysmon service running
[✓] Sysmon telemetry validated

[ ] Sanitized screenshots uploaded
[ ] SIEM screenshots
[ ] Detection-rule screenshots
[ ] Security-alert screenshots
[ ] Incident-investigation screenshots
```

## Screenshot Safety

Before publishing screenshots, verify that they do not expose:

- Passwords
- API keys
- Authentication tokens
- Personal email addresses
- Sensitive usernames
- Personal filesystem paths
- Real host-network packet captures
- Private account information
- Recovery keys or secrets

Only screenshots relevant to the isolated SECURE VAULT lab should be published.

## Purpose

Screenshots provide supporting evidence that the documented lab components were actually deployed, configured, tested, and validated.

They complement the technical documentation and configuration files stored in this repository.
