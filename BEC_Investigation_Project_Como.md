###### **SOC SIMULATION PROJECT** 

# **BEC INVESTIGATION REPORT** 

##### Project Como 

WDLabs // Microsoft 365 UAL Investigation 

|Affected account|Natasha Romanenko - natasha.romanenko@wdlabs.com.au|
|---|---|
|Incidentrange|8 June 2026 to 12 June 2026|
|Investigation date|19 June 2026|
|Analyst|Imran Ata|
|Timestandard|GMT(UTC+0)|



#### **Attack Narrative** 

A Business Email Compromise incident affected Natasha Romanenko's Microsoft 365 account. 

At 08:08:00 GMT on 8 June 2026, Natasha received an email from bbenson17891@outlook.com with the subject June Remittance Advice. The message was delivered to her Junk Email folder. Natasha accessed it at 08:10:08 GMT. 

At 08:12:49 GMT, approximately two minutes and forty-one seconds after the message was accessed, the first confirmed unauthorised sign-in occurred from 54.79.179.92 . This sequence supports credential phishing as the initial access method. Browser history was not available to confirm whether Natasha selected a link or entered her credentials into a phishing page. 

After gaining access, the threat actor accessed 30 mailbox items and downloaded 62 files from Microsoft 365 resources. The actor remained active until 12 June 2026. 

On 10 June at 13:02:51 GMT, the actor created an inbox rule named . to move messages associated with ACME Pty Ltd into the Conversation History folder. The rule reduced the likelihood that Natasha would see correspondence relating to the fraudulent payment request. 

The actor then used Natasha's mailbox and an existing invoice conversation to send unauthorised emails concerning invoice WDL-2026-0048 . Examination of the acquired mailbox identified a five-message chain containing three legitimate messages and two malicious messages. 

ACME acted on a change-of-payment-details request that appeared to come from Natasha. The incident was discovered after ACME received a fraudulent payment notification from its bank. Sarah Mitchell contacted Natasha by phone, and Natasha confirmed that she had not requested any change to the payment details. 

WDLabs disabled the compromised account, reset the password, revoked active sessions, reset MFA and revoked MFA sessions. These actions removed the threat actor's access before the detailed impact assessment began. 



#### **Timeline of Events** 

All timestamps are in GMT. 

|**Time**|**Activity**|**Detail**|
|---|---|---|
|2026-06-08 08:08:00|Phishing email received|Email from bbenson17891@outlook.com with the subject June<br>Remittance Advice was delivered to Natasha's Junk Email folder.|
|2026-06-08 08:10:08|Phishing email accessed|The message was accessed by the legitimate mailbox user.|
|2026-06-08 08:12:49|Initial unauthorised access|First confirmed unauthorised sign-in from 54.79.179.92|
|2026-06-08 08:47:40 to<br>2026-06-12 08:55:57|Mailbox access|During this malicious mailbox activity a total of 30 mail items were<br>accessed.|
|2026-06-08 08:48:27|File downloads began|Start of a download sequence involving 62 files.|
|2026-06-08 09:13:33|File downloads ended|The 62-file download sequence ended.|
|2026-06-10 13:02:51|Inbox rule created|Rule  named "." created  to  move messages  from <br> acmebusiness@gmail.com to the Conversation History folder. This<br>corresponds to 23:02:51 AEST.|
|2026-06-10 13:12:34|Malicious email sent|Email sent from Natasha's mailbox to  acmebusiness2026@gmail.com <br>with the subject Re: Invoice WDL-2026-0048.|
|2026-06-10 13:14:04|Inbox rule modified|Rule condition changed from acmebusiness@gmail.com to<br> acmebusiness2026@gmail.com .|
|2026-06-12 08:55:57|Last identified mailbox<br>access|End of the period in which 30 mailbox items were accessed.|
|2026-06-12 08:56:05|Second malicious email<br>sent|Another email was sent to acmebusiness2026@gmail.com with the<br>subject Re: Invoice WDL-2026-0048.|



### **Findings** 

#### **Initial Access** 

The initial access vector was most likely a credential-phishing email. 

The phishing message was sent from bbenson17891@outlook.com with the subject June Remittance Advice. It appeared to use a shared-file or remittance-document lure. Although the message was placed in Junk Email, it remained available to the user and was accessed at 08:10:08 GMT. 

The first confirmed malicious sign-in occurred at 08:12:49 GMT from (54.79.179.92). The short interval between the email access and unauthorised sign-in, together with the matching IP evidence, supports the assessment that the email led to the account compromise. 

Sign-in activity from Switzerland was also identified during the investigation. This activity was inconsistent with Natasha's normal behaviour because she worked in Melbourne, had not travelled recently and did not use a VPN. 

#### **Unauthorised Activity** 

The threat actor performed the following actions after obtaining access: 

- Accessed 30 mailbox items between 8 June and 12 June. 

- Downloaded 62 files shortly after the first unauthorised sign-in. 

- Created an inbox rule named . on 10 June. 

- Configured the rule to move ACME-related messages into the Conversation History folder. 

- Modified the rule's sender condition shortly after sending the first malicious email. 

- Used Natasha's mailbox to send two unauthorised emails concerning invoice WDL-2026-0048. 

- Used an existing business relationship and invoice conversation to make the payment request appear legitimate. 

The mailbox rule was a concealment mechanism. Its name attracted little attention, while its action prevented relevant correspondence from appearing in Natasha's Inbox. 

Autopsy examination identified five relevant messages in the invoice chain: 

|**Message**|**Classification**|**Direction**|
|---|---|---|
|1|Legitimate|Natasha to ACME|
|2|Malicious|Natasha's compromised mailbox to ACME|
|3|Legitimate|ACME to Natasha|
|4|Malicious|Natasha's compromised mailbox to ACME|
|5|Legitimate|Natasha to ACME|



This mixture of legitimate and malicious messages is consistent with email-thread hijacking. The threat actor used a genuine mailbox and existing conversation to support the fraudulent change-of-payment-details request. 

Message-trace evidence also showed that some suspicious emails were quarantined and did not reach the mailbox. The June Remittance Advice message was sent to Junk Email rather than quarantine, which allowed Natasha to access it. 


#### **Data Access** 

###### **Exchange Online** 

Microsoft 365 audit events recorded 30 mail items accessed between: 

- Start: 2026-06-08 08:47:40 GMT 

- End: 2026-06-12 08:55:57 GMT 

These events confirm unauthorised access to mailbox content. The evidence does not establish whether the messages or their attachments were exported outside Microsoft 365. 

###### **SharePoint and OneDrive** 

Audit activity recorded 62 files downloaded between: 

- Start: 2026-06-08 08:48:27 GMT 

- End: 2026-06-08 09:13:33 GMT 

The downloads began approximately 36 minutes after the initial unauthorised sign-in. This activity confirms that files were transferred from WDLabs' Microsoft 365 environment. 

###### **Mailbox Acquisition and Autopsy Analysis** 

Microsoft Purview eDiscovery was used to export Natasha's mailbox as a `.pst` file. The PST file was imported into Autopsy for mailbox examination. 

A search for invoice-related correspondence identified the email chain associated with invoice `WDL-2026-0048` . Analysis of the messages helped distinguish the legitimate correspondence from the messages sent by the threat actor. 

###### **Exfiltration Assessment** 

|**Data Source**|**Finding**|
|---|---|
|Mailbox|Thirty items were accessed. Further export was not confirmed.|
|SharePoint/OneDrive|Sixty-two files were downloaded. Data transfer is confirmed.|
|Data sensitivity|Not determined from the available evidence.|
|Externalsharing|No confirmed sharing-link creation was identified.|



#### **Facilitation of the Payment Fraud** 

The payment fraud was enabled through four connected actions: 

- **1** The threat actor obtained access to Natasha's genuine Microsoft 365 account. 

- **2** The actor reviewed mailbox content and identified the existing relationship with ACME. 

- **3** An inbox rule concealed ACME-related correspondence from Natasha. 

- **4** The actor used the existing invoice thread to send a change-of-payment-details request that appeared to come from Natasha. 

Because the request came from a known mailbox and referred to a genuine invoice, ACME treated it as legitimate and actioned the request. 

 

#### **Impact** 

The confirmed impact includes: 

- Compromise of Natasha Romanenko's Microsoft 365 account. 

- Unauthorised access to 30 mailbox items. 

- Download of 62 files. 

- Creation and modification of a malicious inbox rule. 

- Two unauthorised emails sent from the compromised mailbox. 

- Misuse of a genuine invoice conversation. 

- ACME acting on fraudulent payment instructions. 

- Exposure of WDLabs and ACME to financial, privacy and reputational harm. 

#### **Containment and Remediation** 

Containment was completed before the detailed impact assessment. This prevented the threat actor from continuing to use Natasha's account while logs and mailbox evidence were examined. 

The following actions were completed: 

- **1** Account disabled: Natasha's account was disabled to stop further access during containment. 

- **2** Password reset: The password was reset first to prevent the threat actor from creating a new authenticated session using the compromised credentials. 

- **3** Active sessions revoked: All active account sessions were revoked. Resetting a password does not automatically terminate existing sessions, so this step removed the threat actor's current access and forced any new connection to authenticate again. 

- **4** MFA reset: Existing MFA registration was reset, and Natasha was required to register MFA again. This removed the possibility that an unauthorised authentication method had been registered. 

- **5** MFA sessions revoked: Existing MFA sessions were revoked so that previously satisfied MFA claims could not continue to be used. 

The order of the password reset and session revocation was important. Resetting the password first prevented the threat actor from immediately creating another session. Revoking sessions afterward removed the existing authenticated access. 



#### **Indicators and Investigation Artefacts** 

|**Type**|**Value**|**Context**|
|---|---|---|
|Compromised<br>account|natasha.romanenko@wdlabs.com.au|WDLabs user account|
|Phishingsender|bbenson17891@outlook.com|Sender of June Remittance Advice|
|Phishing subject|June Remittance Advice|Initial phishing message|
|Confirmed initial IP|54.79.179.92|First unauthorised sign-in and associated<br>phishing evidence|
|Malicious session ID|005ccdea-964a-c068-181e-c9402d6df272|Used to correlate Microsoft 365 activity|
|Inbox rule|.|Moved selected messages to Conversation<br>History|
|Fraud-related subject|R e : Invoice WDL-2026-0048|Used in unauthorised sent messages|
|Ruleaddress|acmebusiness@gmail.com|Original rule condition|
|Modified rule and<br>recipient address|acmebusiness2026@gmail.com|Modified rule condition and sent-email recipient|



The following IP addresses were included in the threat-hunting list: 

|**IP Address**|**Country**|**City**|
|---|---|---|
|37.140.254.32|Switzerland|Zurich|
|173.239.216.150|Switzerland|Bern|
|85.204.124.86|Romania|Bucharest|
|85.204.124.84|Romania|Bucharest|
|85.204.124.85|Romania|Bucharest|
|85.204.124.83|Romania|Bucharest|
|200.162.146.87|Netherlands|Lelystad|
|37.140.254.42|Switzerland|Zurich|
|37.140.254.43|Switzerland|Zurich|
|200.162.146.253|Netherlands|Lelystad|
|200.162.146.109|Netherlands|Lelystad|
|200.162.146.203|Netherlands|Lelystad|
|200.162.146.129|Netherlands|Lelystad|
|54.79.179.92|Australia|Sydney (AWS IP ranges)|


#### **Lessons Learned** 

The first priority in an active account compromise is containment. Detailed analysis should begin only after the account has been disabled, the password has been reset and all active and MFA sessions have been revoked. 

A password reset alone is not sufficient because it does not terminate existing sessions. Resetting the password before revoking the sessions prevents the threat actor from creating a replacement session with the compromised password. 

The investigation should start with a correlated search across SigninLogs and OfficeActivity. Matching the user, malicious IP addresses and Microsoft Entra session ID made it possible to follow the threat actor across authentication, mailbox and file activity. 

Time zones should be normalised before building the timeline. Some tools displayed AEST, while the investigation timeline used GMT. Recording one time standard at the start prevented events from appearing out of order. 

Junk Email and quarantine must be treated differently. Quarantined messages are blocked before reaching the mailbox. Messages placed in Junk Email remain accessible and can still lead to compromise. 

Browser history should be requested early in a suspected phishing investigation. It could have confirmed whether Natasha selected the shared-file link and identified the phishing page used to capture her credentials. 

Microsoft Purview eDiscovery was used to obtain a PST copy of Natasha's mailbox. Autopsy was then used to search the acquired mailbox, examine the invoice correspondence and reconstruct the sequence of legitimate and malicious messages. 

It shows the value of alerts for inbox-rule creation, abnormal sign-ins, unusual mailbox access and bulk file downloads. The attacker's rule and file-download activity showed that the incident extended beyond a single suspicious login. 

#### **Appendix**
Invoice Search in Autopsy:
<img width="940" height="496" alt="image" src="https://github.com/user-attachments/assets/43f9a383-4207-43df-b35f-c106ad64beac" />

<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/08828c83-c9b5-4f2c-baa6-eaeaf1ead310" />

<img width="940" height="531" alt="image" src="https://github.com/user-attachments/assets/0071bab9-750e-4acd-932b-b4fdf226e83c" />

<img width="940" height="498" alt="image" src="https://github.com/user-attachments/assets/c6457bea-0c29-4339-b712-67af4ce0e067" /> 

---

Relevant Emails:

No 1- Legitimate: Natasha to ACME

<img width="940" height="281" alt="image" src="https://github.com/user-attachments/assets/22085a9f-1598-4bd9-a530-34d05b53b076" />
<img width="675" height="987" alt="image" src="https://github.com/user-attachments/assets/b26f38ec-ccbd-4c50-a5b9-7c305cab3138" />


No 2 - Malicious: Natasha to ACME

<img width="940" height="471" alt="image" src="https://github.com/user-attachments/assets/6284dacf-83be-49d1-bbba-2d2c625eae49" />
<img width="940" height="856" alt="image" src="https://github.com/user-attachments/assets/29e53528-423f-477b-9a5a-0ae05840f1ca" />


No 3- Legitimate: ACME to Natasha

<img width="940" height="358" alt="image" src="https://github.com/user-attachments/assets/92304401-455b-4b4d-acc9-0cf9411252d0" />


No 4 - Malicious: Natasha to ACME

<img width="940" height="275" alt="image" src="https://github.com/user-attachments/assets/1db7e7fc-08c5-4c37-886b-2450bba05103" />


N0 5- Legitimate: Natasha to ACME

<img width="940" height="350" alt="image" src="https://github.com/user-attachments/assets/50ee89d5-f03d-4454-98db-1e7ce8005274" />


---

KQL Queries:


Malicious logs:

let badIPs = dynamic([
"37.140.254.32","173.239.216.150","85.204.124.86","85.204.124.84","85.204.124.85","85.204.124.83","200.162.146.87","37.140.254.42","37.140.254.43","200.162.146.253","200.162.146.109","200.162.146.203","200.162.146.129", "54.79.179.92"
]);

OfficeActivity

| extend AADSessionId = tostring(parse_json(AppAccessContext).AADSessionId)

| where UserId == "natasha.romanenko@wdlabs.com.au"

| where ClientIP in (badIPs)
    or AADSessionId == "005ccdea-964a-c068-181e-c9402d6df272"

| sort by TimeGenerated asc

<img width="940" height="448" alt="image" src="https://github.com/user-attachments/assets/5be3ff14-fb17-418a-9c79-853776484de6" />


Search by Operation:

let badIPs = dynamic([
"37.140.254.32","173.239.216.150","85.204.124.86","85.204.124.84","85.204.124.85","85.204.124.83","200.162.146.87","37.140.254.42","37.140.254.43","200.162.146.253","200.162.146.109","200.162.146.203","200.162.146.129", "54.79.179.92"    
]);

OfficeActivity

| extend AADSessionId = tostring(parse_json(AppAccessContext).AADSessionId)

| where UserId == "natasha.romanenko@wdlabs.com.au"

| where ClientIP in (badIPs) or AADSessionId == "005ccdea-964a-c068-181e-c9402d6df272"

| summarize count() by Operation

| sort by count_




<img width="1039" height="504" alt="image" src="https://github.com/user-attachments/assets/ec7998c4-53ee-458a-ad2a-74e16d604193" />


---

Bulk IP Check:


<img width="1064" height="546" alt="image" src="https://github.com/user-attachments/assets/fc853058-f676-44df-bd84-3375875fbb9a" /> 

<img width="1064" height="571" alt="image" src="https://github.com/user-attachments/assets/083df202-334f-42f2-a4d4-7c748389a5e2" />



Further IP Check:



<img width="1064" height="616" alt="image" src="https://github.com/user-attachments/assets/e5ef6fd7-c4fa-45da-9c1a-8a67fda084e9" />
























