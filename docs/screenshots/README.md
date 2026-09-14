# SECURE VAULT - Lab Evidence

This directory contains sanitized screenshots that demonstrate the implementation and validation of the SECURE VAULT cybersecurity lab.

The screenshots are organized by technical area so each configuration and validation step can be independently reviewed.

## Networking Evidence

### Static IP Configuration

The Windows endpoint is configured with the static SEC-LAB address:

```text
10.10.10.10/24
```

![Static IP Configuration](networking/static-ip.png)

---

### Host-to-VM Connectivity

Connectivity from the Windows host to the security endpoint was validated using ICMP.

```text
Target: 10.10.10.10
Packet Loss: 0%
```

![Host to VM Ping](networking/host-to-vm-ping.png)

---

### Temporary Internet Connectivity

A secondary NAT adapter is used when Internet access is required for downloads and updates.

Connectivity was validated using:

```powershell
Test-NetConnection learn.microsoft.com -Port 443
```

Result:

```text
TcpTestSucceeded : True
```

![Internet Connectivity Test](networking/internet-connectivity-test.png)

---

### Firewall Validation

Windows Defender Firewall remains enabled.

A controlled inbound ICMP rule named:

```text
SEC-LAB Ping
```

was configured to allow host-to-endpoint connectivity testing.

![Firewall Rule](networking/firewall-rule.png)

---

## Sysmon Evidence

### Sysmon Service

Microsoft Sysmon is installed and running on the Windows endpoint.

Validation command:

```powershell
Get-Service Sysmon64
```

Expected status:

```text
Running
```

![Sysmon Service Running](sysmon/sysmon-service-running.png)

---

### Sysmon Event Generation

Sysmon events were successfully generated and validated from the Windows Event Log.

Validation command:

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" -MaxEvents 10 |
Select-Object TimeCreated, Id, ProviderName
```

![Sysmon Events](sysmon/sysmon-events.png)

---

## Evidence Summary

```text
[✓] Static IP configured
[✓] Host-to-VM communication verified
[✓] Internet connectivity verified
[✓] Windows Firewall rule validated
[✓] Sysmon service running
[✓] Sysmon events generated
```

These screenshots provide direct evidence that the Windows endpoint, network configuration, and endpoint telemetry components of SECURE VAULT are functioning as intended.
