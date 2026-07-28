**Alert:** Suspicious service launched

**Endpoint:** ec2amaz-9oh9aqq

**User:** NT SERVICE\himds

**OS:** WindowsServer2022

**Verdict:** True positive

<img width="940" height="691" alt="image" src="https://github.com/user-attachments/assets/80dccca2-735c-4dbc-95ff-d48976498e38" />


<img width="531" height="1047" alt="image" src="https://github.com/user-attachments/assets/d16397b6-e52d-4e38-acf0-f6feb761dddd" />


The alert tuning rule to hide a specific alert usually means an Exclusion (allowlist override). 

**Why was the alert triggered?**

System's behavioural analysis or threat intelligence matched a running process against SandCat— which is the default agent name for Caldera, an open-source adversary emulation platform created by MITRE.

This behaviour aligns with MITRE ATT&CK technique T1003.001 (LSASS Credential Dumping), which is why Defender generating a Credential Access alert.

**Investigation Findings**

 
<img width="710" height="727" alt="image" src="https://github.com/user-attachments/assets/d5e9372c-3a03-411d-acf7-d9b95d3da74f" />


**Conclusion:**

•  The process tree is mostly composed of legitimate Windows, AWS, Azure, and Microsoft

Defender processes.

•  The significant finding is the CalderaAgent service being launched by services.exe through

nssm.exe, which Microsoft Defender flagged as "Suspicious service launched."

•  There is no direct evidence that malware or ransomware executed.
•  There is evidence of persistence through a Windows service (T1569.002 – Service Execution).
•  CalderaAgent detected due to an authorized red-team emulation exercise using MITRE CALDERA.

•  Tuning the alert is not recommended as an attacker may use CALDERA or a similarly named

service to maintain persistence.

•  Alert closed off

