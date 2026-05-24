# Privilege Escalation Investigation

## Alert Description

A high-severity security alert was triggered indicating suspicious privilege escalation activity on a Windows endpoint. A standard user account was observed gaining administrative privileges without approved change control.

---

## Severity

High

---

## Detection Source

SIEM (Splunk / Microsoft Sentinel / QRadar correlation)

---

## Investigation Steps

1. Reviewed privilege-related security events from Windows logs.
2. Identified account added to local administrators group.
3. Checked Event ID logs for group membership changes.
4. Analyzed process execution history before privilege escalation.
5. Correlated suspicious PowerShell activity.
6. Verified login source and session history.
7. Checked for malware or credential misuse.
8. Reviewed Active Directory group changes.

---

## Logs Reviewed

- Windows Security Event Logs
- Active Directory Logs
- Sysmon Logs
- SIEM Correlation Events
- PowerShell Operational Logs

---

## Key Events Observed

| Event ID | Description |
|----------|-------------|
| 4624 | Successful login |
| 4672 | Special privileges assigned |
| 4728 | User added to group |
| 4732 | Member added to local admin group |
| 4688 | Process creation (PowerShell execution) |

---

## Suspicious Activity Observed

- PowerShell executed with encoded command
- New local admin account creation detected
- Unexpected group membership change
- Login from unusual workstation

---

## Indicators of Compromise (IOCs)

- User Account: standard.user  
- New Admin Account: temp_admin01  
- Hostname: WIN10-OFFICE03  
- Suspicious Process: powershell.exe -EncodedCommand  
- Source IP: 10.10.20.45  

---

## MITRE ATT&CK Mapping

- T1078 – Valid Accounts  
- T1068 – Exploitation for Privilege Escalation  
- T1059.001 – PowerShell  
- T1547.001 – Registry/Startup Persistence (possible)

---

## Root Cause

The standard user account was compromised, and the attacker executed a PowerShell script that modified local group membership, granting administrative privileges on the endpoint.

---

## Containment Actions

- Removed user from local administrators group
- Reset compromised account password
- Isolated affected endpoint
- Blocked suspicious PowerShell execution
- Reviewed all admin group changes across domain
- Enabled enhanced auditing policies

---

## Final Conclusion

The privilege escalation attempt was successfully detected and remediated before lateral movement or domain-wide compromise occurred.

No evidence of data exfiltration was found.

---

## Recommendations

- Restrict local admin rights
- Monitor group membership changes closely
- Disable unnecessary PowerShell execution
- Enable application whitelisting (AppLocker/WDAC)
- Implement Privileged Access Management (PAM)
