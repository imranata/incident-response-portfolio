**Executive Summary**

A Business Email Compromise (BEC) incident was investigated involving the Microsoft 365 account of
Natasha Romanenko. Audit logs identified successful logins from Switzerland, despite the user
residing in Melbourne and having no history of overseas travel or VPN usage. Following
authentication, the threat actor accessed SharePoint resources, viewed and downloaded files, and
used the compromised mailbox to facilitate a fraudulent payment request sent to ACME Pty Ltd.

**Scope**

•  User: Natasha Romanenko

•  Environment: Microsoft 365

•  Evidence (Signin Logs, Message Trace, Mailbox PST):

<img width="940" height="494" alt="image" src="https://github.com/user-attachments/assets/348dedc4-e3c5-4f33-8181-d1d7ce9e210e" />




<img width="940" height="464" alt="image" src="https://github.com/user-attachments/assets/0316aaa4-3bc5-4adf-896b-448ca731a0a6" />



 
 
 **Findings:**


<img width="309" height="254" alt="image" src="https://github.com/user-attachments/assets/9679ab2e-363b-4559-bb72-4fb60982227b" />




**Initial Access**

**Normal login:**

49.185.122.38  Australia

**First unauthorized login observed on 8 June 2026 from Swiss IP addresses:**

85.204.124.83

85.204.124.84

85.204.124.85

85.204.124.86



**Threat Activity**

•  Successful authentication.

•  SharePoint browsing.

•  File access.

•  File downloads.

•  Mailbox compromise.

•  Fraudulent payment request.


**Data Exposure**

Audit records containing FileDownloaded indicate that corporate files were downloaded, suggesting
likely data exfiltration.

**Business Impact**

•  Potential financial fraud.

•  Exposure of sensitive business information.

•  Reputational risk.

•  Third-party compromise.




**Root Cause**

The investigation indicates compromise of valid Microsoft 365 credentials. While the exact
acquisition method cannot be proven from the available evidence, phishing or credential theft is a
plausible explanation and should be treated as a hypothesis rather than a confirmed finding.

**Recommendations**

•  Reset credentials and revoke active sessions.

•  Enforce phishing-resistant MFA.

•  Review mailbox rules and delegated access.

•  Notify affected third parties.

•  Perform a wider threat hunt for related indicators.

•  Monitor for further suspicious sign-in activity.



<img width="940" height="485" alt="image" src="https://github.com/user-attachments/assets/4d4c4b46-880c-492a-9004-836769c00812" />


•  Review downloaded files for sensitivity and disclosure obligations.



