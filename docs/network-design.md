# Network Design

## Overview

SECURE VAULT uses an isolated VirtualBox Host-Only network to simulate an enterprise security environment while keeping lab traffic separated from the normal host network.

## Lab Network

```text
Network:        10.10.10.0/24
Host Adapter:   10.10.10.1
Windows VM:     10.10.10.10
Future SIEM:    10.10.10.20
DHCP Server:    10.10.10.100
DHCP Pool:      10.10.10.101 - 10.10.10.200
```

Static infrastructure addresses are kept outside the DHCP pool.

## Architecture

```text
                    Windows 11 Host
                       10.10.10.1
                            |
                            |
                 SEC-LAB Host-Only Network
                       10.10.10.0/24
                            |
              +-------------+-------------+
              |                           |
              |                           |
       SEC-WIN11-01                 SEC-SIEM-01
        10.10.10.10                  10.10.10.20
       Windows Endpoint             Linux / SIEM
                                         [Planned]
```

## Windows Endpoint

```text
IP Address:      10.10.10.10
Subnet Mask:     255.255.255.0
Default Gateway: None
```

The Host-Only adapter is used for isolated lab communication.

## Temporary Internet Access

A second VirtualBox adapter is enabled when the VM needs Internet access.

```text
Adapter 1
Type: Host-Only
Purpose: SEC-LAB communication

Adapter 2
Type: NAT
Purpose: Temporary Internet access
```

Internet connectivity was verified using:

```powershell
Test-NetConnection learn.microsoft.com -Port 443
```

Result:

```text
TcpTestSucceeded : True
```

## Connectivity Validation

Host-to-endpoint communication was tested with:

```powershell
ping 10.10.10.10
```

Result:

```text
Packets Sent: 4
Packets Received: 4
Packet Loss: 0%
```

ARP resolution between the host and Windows endpoint was also verified.

## Firewall

Windows Defender Firewall remains enabled.

A dedicated ICMP rule was created to allow controlled ping testing from the host instead of disabling the firewall.

## Design Goals

- Isolate security lab traffic
- Use predictable static IP addressing
- Keep infrastructure outside the DHCP range
- Maintain host-to-VM connectivity
- Provide temporary Internet access when required
- Prepare the environment for centralized SIEM monitoring
- Support future threat detection and attack simulation

## Planned Systems

```text
10.10.10.10 - Windows Security Endpoint
10.10.10.20 - Linux / SIEM Server
```

