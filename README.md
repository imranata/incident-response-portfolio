# Microsoft 365 BEC Investigation – SOC Simulation Project

This repository presents a simulated Microsoft 365 Business Email Compromise investigation completed through the WDLabs SOC Simulation Project.

I conducted the analysis and prepared the investigation report using evidence supplied through an authorised training environment. The identities, accounts, business correspondence and incident activity in the case are simulated. No employer, client or real-user information is included.

## Case Study

[Microsoft 365 BEC Investigation – Project Como](BEC_Investigation_Project_Como.md)

## Investigation Overview

The investigation examined a compromised Microsoft 365 account used to access mailbox content, download cloud files, create a malicious inbox rule and manipulate an existing invoice conversation.

The analysis covered:

* Credential-phishing activity and unauthorised sign-ins
* Correlation of user activity, source IP addresses and Microsoft Entra session IDs
* Exchange Online mailbox access and message activity
* Malicious inbox-rule creation and modification
* Email-thread hijacking and fraudulent payment instructions
* SharePoint and OneDrive file-download activity
* Mailbox acquisition and PST examination
* Incident timeline reconstruction
* Account containment and session revocation
* Impact assessment and remediation recommendations

## Tools and Data Sources

| Area                   | Tools and evidence                                    |
| ---------------------- | ----------------------------------------------------- |
| Identity               | Microsoft Entra ID sign-in logs                       |
| Microsoft 365 auditing | Unified Audit Log                                     |
| Email investigation    | Exchange Online message trace and inbox-rule activity |
| Cloud activity         | SharePoint and OneDrive audit events                  |
| Query and correlation  | Microsoft Sentinel and KQL                            |
| Evidence acquisition   | Microsoft Purview eDiscovery                          |
| Mailbox examination    | Autopsy and PST analysis                              |

## Skills Demonstrated

* Microsoft 365 account-compromise investigation
* Authentication, IP address and session correlation
* KQL event analysis
* Mailbox and email-thread analysis
* Inbox-rule abuse investigation
* SharePoint and OneDrive activity analysis
* Incident scoping and impact assessment
* Timeline reconstruction
* Containment and remediation planning
* Technical incident documentation

## Key Findings

The investigation identified:

* A phishing email followed by unauthorised account access
* Thirty mailbox items accessed during the compromise
* Sixty-two files downloaded from Microsoft 365 resources
* A malicious inbox rule used to conceal relevant correspondence
* Two unauthorised emails sent from the compromised mailbox
* An existing invoice conversation used to support fraudulent payment instructions
* Activity requiring password reset, session revocation and MFA re-registration

## Professional Profile

[LinkedIn – Imran Ata](https://www.linkedin.com/in/imran-ata-91278542a/)
