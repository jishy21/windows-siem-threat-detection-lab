# Windows SIEM + Threat Detection Lab

## Overview

This project simulates a basic enterprise security monitoring environment using Windows, Splunk Enterprise, Splunk Universal Forwarder, and Sysmon. The goal of this lab was to collect Windows endpoint logs, forward them into a SIEM, and create basic detections for suspicious activity.

This lab demonstrates hands-on experience with log analysis, endpoint monitoring, incident investigation, and security documentation.

## Lab Objectives

- Build a Windows-based SIEM lab environment
- Install and configure Splunk Enterprise
- Forward Windows logs from a client machine into Splunk
- Install Sysmon for enhanced endpoint visibility
- Detect failed logins, successful logins, user creation, administrator group changes, and PowerShell activity
- Document findings using incident-style reports

## Tools Used

- Windows Server 2022
- Windows 10/11 Pro
- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon
- Windows Event Viewer
- PowerShell
- VirtualBox or VMware

## Lab Environment

| System | Role | IP Address |
|---|---|---|
| SIEM-SERVER | Splunk Enterprise Server | 192.168.56.10 |
| WIN-CLIENT01 | Windows endpoint generating logs | 192.168.56.20 |

## Network Setup

Both virtual machines were configured on the same virtual network so the Windows client could forward logs to the Splunk server.

![Client Ping SIEM Server](screenshots/05-client-ping-siem-server.png)

## Splunk Setup

Splunk Enterprise was installed on the Windows Server VM and configured to receive forwarded logs on port `9997`.

![Splunk Home Dashboard](screenshots/08-splunk-home-dashboard.png)

![Splunk Receiving Port](screenshots/09-splunk-receiving-port-9997.png)

## Log Forwarding

Splunk Universal Forwarder was installed on the Windows client VM and configured to forward Windows event logs to the Splunk server.

Forwarded log sources included:

- Security logs
- System logs
- Application logs
- Sysmon Operational logs

![Forwarder Config](screenshots/12-forwarder-windows-logs-added.png)

## Detection Scenarios

### 1. Failed Login Detection

Windows failed login attempts were generated and detected in Splunk using Event ID `4625`.

Search used:

```spl
EventCode=4625

2. Successful Login Detection

Successful login events were identified using Event ID 4624.

Search used:

EventCode=4624

3. PowerShell Activity Detection

PowerShell activity was generated on the Windows client and reviewed in Splunk.

Search used:

powershell OR EventCode=1

4. User Creation Detection

A local test user was created on the Windows client and detected in Splunk.

Search used:

EventCode=4720

5. Administrator Group Change Detection

A test user was added to the local Administrators group and detected using Windows security logs.

Search used:

EventCode=4732
