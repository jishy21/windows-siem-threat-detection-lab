# Security Tools Used

## Splunk Enterprise

Purpose:
Used as the centralized SIEM platform for log collection, searching, and detection creation.

Key Features Used:
- Log ingestion
- Event searching
- Detection queries
- Security event monitoring
- Alert creation

## Splunk Universal Forwarder

Purpose:
Used to forward Windows logs from the client machine to the Splunk server.

Logs Forwarded:
- Security logs
- System logs
- Application logs
- Sysmon Operational logs

## Sysmon

Purpose:
Enhanced Windows endpoint logging and process visibility.

Key Monitoring Features:
- Process creation events
- PowerShell execution
- Network connections
- File activity
- Service creation

## Windows Event Viewer

Purpose:
Used to verify Windows events locally before forwarding them into Splunk.

Important Event IDs:
- 4624 → Successful Login
- 4625 → Failed Login
- 4720 → User Created
- 4732 → Added to Administrator Group

## PowerShell

Purpose:
Used to simulate administrative and suspicious activity for detection testing.

Example Commands:
```powershell
whoami
ipconfig /all
Get-LocalUser
Get-Process
