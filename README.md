# Privilege Escalation Investigation

This folder contains a SOC investigation focused on detecting and analyzing privilege escalation activity within a Windows environment.

---

## Overview

A standard user account was observed gaining administrative privileges without authorization. The activity was detected through SIEM correlation of Windows security events and endpoint logs.

---

## What was analyzed

- Windows Security Event Logs
- Active Directory group changes
- PowerShell execution logs
- Sysmon process monitoring
- SIEM correlation alerts

---

## Key Findings

- Unauthorized addition to local administrators group
- Suspicious PowerShell execution detected
- Compromised user account suspected
- Privilege escalation confirmed via Event IDs

---

## Skills Demonstrated

- Active Directory security monitoring
- Privilege escalation detection
- SIEM log correlation
- Endpoint investigation
- PowerShell analysis
- Incident response workflow
- MITRE ATT&CK mapping

---

## MITRE ATT&CK

- T1078 – Valid Accounts  
- T1068 – Privilege Escalation  
- T1059.001 – PowerShell  

---

## Outcome

The escalation was detected and contained before lateral movement or domain compromise.

---

## Disclaimer

All data used in this investigation is fictional and created for educational portfolio purposes only.
