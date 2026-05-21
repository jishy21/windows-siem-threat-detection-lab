# Windows SIEM + Threat Detection Lab

## Overview

This project simulates a basic enterprise security monitoring environment using Windows, Splunk Enterprise, Splunk Universal Forwarder, and Sysmon. The goal of this lab was to collect Windows endpoint logs, forward them into a SIEM, and create detections for suspicious activity.

This lab demonstrates hands-on experience with:

- Log analysis
- Endpoint monitoring
- Incident investigation
- Security event detection
- SIEM configuration
- Technical documentation

---

## Lab Objectives

- Build a Windows-based SIEM lab environment
- Install and configure Splunk Enterprise
- Forward Windows logs from a client machine into Splunk
- Install Sysmon for enhanced endpoint visibility
- Detect failed logins, successful logins, user creation, administrator group changes, and PowerShell activity
- Document findings using incident-style reports

---

## Tools Used

- Windows Server 2022
- Windows 10/11 Pro
- Splunk Enterprise
- Splunk Universal Forwarder
- Sysmon
- Windows Event Viewer
- PowerShell
- VirtualBox or VMware

---

## Lab Environment

| System | Role | IP Address |
|---|---|---|
| SIEM-SERVER | Splunk Enterprise Server | 192.168.56.10 |
| WIN-CLIENT01 | Windows endpoint generating logs | 192.168.56.20 |

---

## Splunk Setup

Splunk Enterprise was installed on the Windows Server VM and configured to receive forwarded logs on port `9997`.

![Splunk Install Complete](screenshots/02-splunk-install-complete.png)

![Splunk Login Page](screenshots/03-splunk-login-page.png)

![Splunk Home Dashboard](screenshots/04-splunk-home-dashboard.png)

![Splunk Receiving Port](screenshots/05-splunk-receiving-port-9997.png)

---

## Log Forwarding

Splunk Universal Forwarder was installed on the Windows client VM and configured to forward Windows event logs to the Splunk server.

### Forwarded Log Sources

- Security logs
- System logs
- Application logs
- Sysmon Operational logs

![Universal Forwarder Install](screenshots/06-universal-forwarder-install.png)

![Windows Logs Added](screenshots/07-forwarder-windows-logs-added.png)

![Splunk Index Search Results](screenshots/08-splunk-index-search-results.png)

---

## Sysmon Configuration

Sysmon was installed to improve endpoint visibility and generate detailed process creation logs.

![Sysmon Installed Successfully](screenshots/10-sysmon-installed-successfully.png)

![Sysmon Service Running](screenshots/11-sysmon-service-running.png)

![Sysmon Log Forwarding Added](screenshots/12-sysmon-log-forwarding-added.png)

---

## Detection Scenarios

### 1. Failed Login Detection

Windows failed login attempts were generated and detected in Splunk using Event ID `4625`.

#### Search Used

```spl
EventCode=4625
```

![Failed Login Attempts Client](screenshots/13-failed-login-attempts-client.png)

![Failed Login Attempts SIEM](screenshots/14-failed-login-attempts-siem.png)

![Splunk Lockout Logs](screenshots/15-splunk-lockout-logs.png)

---

### 2. Successful Login Detection

Successful login events were identified using Event ID `4624`.

#### Search Used

```spl
EventCode=4624
```

![Successful Login Event](screenshots/16-successful-login-event.png)

---

### 3. PowerShell Activity Detection

PowerShell activity was generated on the Windows client and reviewed in Splunk.

#### Search Used

```spl
powershell OR EventCode=1
```

![PowerShell Activity](screenshots/18-splunk-powershell-activity.png)

---

### 4. User Creation Detection

A local test user was created on the Windows client and detected in Splunk.

#### Search Used

```spl
EventCode=4720
```

![Local Admin User Created](screenshots/19-local-admin-user-created.png)

![User Creation Detection](screenshots/20-splunk-user-creation-detected.png)

---

### 5. Alert Creation

Custom alerts were created in Splunk to monitor suspicious activity and important security events.

#### Failed Login Alert

![Failed Login Alert Created](screenshots/21-failed-login-alert-created.png)

#### New User Alert

![New User Alert Created](screenshots/22-new-user-alert-created.png)

#### Administrator Group Change Alert

![Admin Group Alert Created](screenshots/23-admin-group-alert-created.png)

---

## Incident Reports

Incident-style reports were created to document investigation steps, evidence, and remediation actions.

### Reports Included

- Failed Login Investigation
- Successful Login Investigation
- PowerShell Activity Investigation
- Suspicious User Creation Investigation
- Administrator Group Membership Change Investigation

---

## Skills Demonstrated

- SIEM setup and configuration
- Windows log analysis
- Splunk searching and detection creation
- Sysmon deployment and monitoring
- Endpoint visibility and monitoring
- Security event investigation
- Incident response documentation
- PowerShell administration
- Technical troubleshooting
- GitHub documentation

---

## Lessons Learned

This lab reinforced how enterprise environments use centralized logging solutions to monitor endpoints and investigate suspicious activity. It also improved understanding of Windows Event IDs, Splunk log analysis, Sysmon monitoring, and incident investigation workflows.
