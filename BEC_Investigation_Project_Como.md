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

At 08:08:00 GMT on 8 June 2026, Natasha received an email from b b e n s o n 1 7 8 9 1 @ o u t l o o k . c o m with the subject June Remittance Advice. The message was delivered to her Junk Email folder. Natasha accessed it at 08:10:08 GMT. 

At 08:12:49 GMT, approximately two minutes and forty-one seconds after the message was accessed, the first confirmed unauthorised sign-in occurred from 5 4 . 7 9 . 1 7 9 . 9 2 . This sequence supports credential phishing as the initial access method. Browser history was not available to confirm whether Natasha selected a link or entered her credentials into a phishing page. 

After gaining access, the threat actor accessed 30 mailbox items and downloaded 62 files from Microsoft 365 resources. The actor remained active until 12 June 2026. 

On 10 June at 13:02:51 GMT, the actor created an inbox rule named . to move messages associated with ACME Pty Ltd into the Conversation History folder. The rule reduced the likelihood that Natasha would see correspondence relating to the fraudulent payment request. 

The actor then used Natasha's mailbox and an existing invoice conversation to send unauthorised emails concerning invoice W D L - 2 0 2 6 - 0 0 4 8 . Examination of the acquired mailbox identified a five-message chain containing three legitimate messages and two malicious messages. 

ACME acted on a change-of-payment-details request that appeared to come from Natasha. The incident was discovered after ACME received a fraudulent payment notification from its bank. Sarah Mitchell contacted Natasha by phone, and Natasha confirmed that she had not requested any change to the payment details. 

WDLabs disabled the compromised account, reset the password, revoked active sessions, reset MFA and revoked MFA sessions. These actions removed the threat actor's access before the detailed impact assessment began. 

SOC Simulation Project 

Page 1 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

#### **Timeline of Events** 

All timestamps are in GMT. 

|**Time**|**Activity**|**Detail**|
|---|---|---|
|2026-06-08 08:08:00|Phishing email received|Email fromb b e n s o n 1 7 8 9 1 @ o u t l o o k . c o m with the subject June<br>Remittance Advice was delivered to Natasha's Junk Email folder.|
|2026-06-08 08:10:08|Phishing email accessed|The message was accessed by the legitimate mailbox user.|
|2026-06-08 08:12:49|Initial unauthorised access|First confirmed unauthorised sign-in from5 4 . 7 9 . 1 7 9 . 9 2. The<br>application used was not identified in the supplied evidence.|
|2026-06-08 08:47:40 to<br>2026-06-12 08:55:57|Mailbox access|During malicious mailbox activity a total of 30 mail items were<br>accessed.|
|2026-06-08 08:48:27|File downloads began|Start of a download sequence involving 62 files.|
|2026-06-08 09:13:33|File downloads ended|The 62-file download sequence ended.|
|2026-06-10 13:02:51|Inbox rule created|Rule  named. created  to  move messages  from<br>a c m e b u s i n e s s @ g m a i l . c o mto the Conversation History folder. This<br>corresponds to 23:02:51 AEST.|
|2026-06-10 13:12:34|Malicious email sent|Email sent from Natasha's mailbox toa c m e b u s i n e s s 2 0 2 6 @ g m a i l . c o m <br>with the subject Re: Invoice WDL-2026-0048.|
|2026-06-10 13:14:04|Inbox rule modified|Rule condition changed froma c m e b u s i n e s s @ g m a i l . c o m to<br>a c m e b u s i n e s s 2 0 2 6 @ g m a i l . c o m .|
|2026-06-12 08:55:57|Last identified mailbox<br>access|End of the period in which 30 mailbox items were accessed.|
|2026-06-12 08:56:05|Second malicious email<br>sent|Another email was sent toa c m e b u s i n e s s 2 0 2 6 @ g m a i l . c o m with the<br>subject Re: Invoice WDL-2026-0048.|



SOC Simulation Project 

Page 2 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

### **Findings** 

#### **3.1 Initial Access** 

The initial access vector was most likely a credential-phishing email. 

The phishing message was sent from b b e n s o n 1 7 8 9 1 @ o u t l o o k . c o m with the subject June Remittance Advice. It appeared to use a shared-file or remittance-document lure. Although the message was placed in Junk Email, it remained available to the user and was accessed at 08:10:08 GMT. 

The first confirmed malicious sign-in occurred at 08:12:49 GMT from 5 4 . 7 9 . 1 7 9 . 9 2 . The short interval between the email access and unauthorised sign-in, together with the matching IP evidence, supports the assessment that the email led to the account compromise. 

Sign-in activity from Switzerland was also identified during the investigation. This activity was inconsistent with Natasha's normal behaviour because she worked in Melbourne, had not travelled recently and did not use a VPN. 

#### **3.2 Unauthorised Activity** 

The threat actor performed the following actions after obtaining access: 

- Accessed 30 mailbox items between 8 June and 12 June. 

- Downloaded 62 files shortly after the first unauthorised sign-in. 

- Created an inbox rule named . on 10 June. 

- Configured the rule to move ACME-related messages into the Conversation History folder. 

- Modified the rule's sender condition shortly after sending the first malicious email. 

- Used Natasha's mailbox to send two unauthorised emails concerning invoice W D L - 2 0 2 6 - 0 0 4 8 . 

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

SOC Simulation Project 

Page 3 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

#### **3.3 Data Access** 

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



#### **3.4 Facilitation of the Payment Fraud** 

The payment fraud was enabled through four connected actions: 

- **1** The threat actor obtained access to Natasha's genuine Microsoft 365 account. 

- **2** The actor reviewed mailbox content and identified the existing relationship with ACME. 

- **3** An inbox rule concealed ACME-related correspondence from Natasha. 

- **4** The actor used the existing invoice thread to send a change-of-payment-details request that appeared to come from Natasha. 

Because the request came from a known mailbox and referred to a genuine invoice, ACME treated it as legitimate and actioned the request. 

SOC Simulation Project 

Page 4 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

#### **3.5 Impact** 

The confirmed impact includes: 

- Compromise of Natasha Romanenko's Microsoft 365 account. 

- Unauthorised access to 30 mailbox items. 

- Download of 62 files. 

- Creation and modification of a malicious inbox rule. 

- Two unauthorised emails sent from the compromised mailbox. 

- Misuse of a genuine invoice conversation. 

- ACME acting on fraudulent payment instructions. 

- Exposure of WDLabs and ACME to financial, privacy and reputational harm. 

#### **3.6 Containment and Remediation** 

Containment was completed before the detailed impact assessment. This prevented the threat actor from continuing to use Natasha's account while logs and mailbox evidence were examined. 

The following actions were completed: 

- **1** Account disabled: Natasha's account was disabled to stop further access during containment. 

- **2** Password reset: The password was reset first to prevent the threat actor from creating a new authenticated session using the compromised credentials. 

- **3** Active sessions revoked: All active account sessions were revoked. Resetting a password does not automatically terminate existing sessions, so this step removed the threat actor's current access and forced any new connection to authenticate again. 

- **4** MFA reset: Existing MFA registration was reset, and Natasha was required to register MFA again. This removed the possibility that an unauthorised authentication method had been registered. 

- **5** MFA sessions revoked: Existing MFA sessions were revoked so that previously satisfied MFA claims could not continue to be used. 

The order of the password reset and session revocation was important. Resetting the password first prevented the threat actor from immediately creating another session. Revoking sessions afterward removed the existing authenticated access. 

SOC Simulation Project 

Page 5 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

#### **Indicators and Investigation Artefacts** 

|**Type**|**Value**|**Context**|
|---|---|---|
|Compromised<br>account|n a t a s h a . r o m a n e n k o @ w d l a b s . c o m . a u|WDLabs user account|
|Phishingsender|b b e n s o n 1 7 8 9 1 @ o u t l o o k . c o m|Sender of June Remittance Advice|
|Phishing subject|J u n e R e m i t t a n c e A d v i c e|Initial phishing message|
|Confirmed initial IP|5 4 . 7 9 . 1 7 9 . 9 2|First unauthorised sign-in and associated<br>phishing evidence|
|Malicious session ID|0 0 5 c c d e a - 9 6 4 a - c 0 6 8 - 1 8 1 e - c 9 4 0 2 d 6 d f 2 7 2|Used to correlate Microsoft 365 activity|
|Inbox rule|.|Moved selected messages to Conversation<br>History|
|Fraud-related subject|R e : I n v o i c e W D L - 2 0 2 6 - 0 0 4 8|Used in unauthorised sent messages|
|Ruleaddress|a c m e b u s i n e s s @ g m a i l . c o m|Original rule condition|
|Modified rule and<br>recipient address|a c m e b u s i n e s s 2 0 2 6 @ g m a i l . c o m|Modified rule condition and sent-email recipient|



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



SOC Simulation Project 

Page 6 

**WDLABS | PROJECT COMO** 

BEC INVESTIGATION REPORT 

#### **Lessons Learned** 

The first priority in an active account compromise is containment. Detailed analysis should begin only after the account has been disabled, the password has been reset and all active and MFA sessions have been revoked. 

A password reset alone is not sufficient because it does not terminate existing sessions. Resetting the password before revoking the sessions prevents the threat actor from creating a replacement session with the compromised password. 

The investigation should start with a correlated search across SigninLogs and OfficeActivity. Matching the user, malicious IP addresses and Microsoft Entra session ID made it possible to follow the threat actor across authentication, mailbox and file activity. 

Time zones should be normalised before building the timeline. Some tools displayed AEST, while the investigation timeline used GMT. Recording one time standard at the start prevented events from appearing out of order. 

Junk Email and quarantine must be treated differently. Quarantined messages are blocked before reaching the mailbox. Messages placed in Junk Email remain accessible and can still lead to compromise. 

Browser history should be requested early in a suspected phishing investigation. It could have confirmed whether Natasha selected the shared-file link and identified the phishing page used to capture her credentials. 

Microsoft Purview eDiscovery was used to obtain a PST copy of Natasha's mailbox. Autopsy was then used to search the acquired mailbox, examine the invoice correspondence and reconstruct the sequence of legitimate and malicious messages. 

It shows the value of alerts for inbox-rule creation, abnormal sign-ins, unusual mailbox access and bulk file downloads. The attacker's rule and file-download activity showed that the incident extended beyond a single suspicious login. 

SOC Simulation Project 

Page 7 



<!-- Start of picture text -->
At NatashaMailbox - Autopsy 4.23.1 - o x<br>pa<br>eo 2 Keyword search 1 - Invoice WOL-20... seve<br>+ Data Sources search €<br>||B & &File File Views:Types Table Thumbnail “om ‘Save Tableas CSV<br>| RMB_ Deleted Files at<br>2| BBBABDotsFileCommunication ArtifactsSe Accounts (20) NameDBBB nstashasomonenkoQudlabs.comsu.0D\E-Mail Messages Artifact KeywordSubject : Preview Re «invoice WOL-2026-O0«DatReceiv e d Location—/LogicalfileSet'/nateshazomanenkogwdlabs:com.au....Modified0000-00-00000000 Time 9000-00-09Change Time 020000 Aecess 9000-00-00.000:00 Time Created0000-00-0000-00.09 Time 64521]See<br>| cp rere Dl E-Mail Messages Artifact pst Subject:NatashasinvoiceRe: elnwoiceWOL-2026-004Bmeginvoice WOL-2026-0088«TecNatashaWORe... /LogicalFileSet/natasha.romanenko@wilabs.com.su,,._—_/LogicalFileSet}/natasharomanenkof@wdlabs.com.2u...0000-00-000000000000-00-00 000-00 0000-00-00 0900-00-00000G00 0000:00  0000-00-0000-0000 0000-00-00:0000:00 0000-00-00. 0000-00-00.00000000.0000 64521]64521<br>| 1 m Default 26) (3 E-Mail Messages Artifact Subject: Re «invoice WOL-2026-0048+To:Natasha Ro... /LogicalFileSet!/natashs.zomanenko@wdlabs.com.su.... 0000-00-00 00:00:00 0000-00-00 00:00:00  0000-00-00.00:02.00 0000-00-000000000 64521]<br>| - > Metadata(3) (Dy E-Mail Messages Artifact ACMESubject: sirvosce WOL:2026-0048«Date Recewed /LogicalfileSet!/natasha somanenko@wdlabs.com.su.... 0000-00-00 00:00:00 0000-00-00 00:00:00 0000-00-00 000000 0000-00-00:00:00.09 64521)<br>|© BS KeywordHits (2446)<br>© BiGH Tage05 Accounts<br>© O sor<br>— & Reports<br>Hex Tet Appiceton SourceFile Metadata 05 Account Data Artifacts Sowiyos Sesults: Contes Annotations Other Occurrences:<br>Heedere Tet HTML TF Attachments(1) Accounts<br>Hi Sarah, fj<br>Apologies - quick update before you process this, we've recently changed banking providers and our account details have been updated. It is important that the payment goes to this account because the old |<br>‘accountis closing soon.<br>Find attached.<br>Thanks,<br>Natasha<br><!-- End of picture text -->



<!-- Start of picture text -->
Ab NatashaMailbox - Autopsy 4.23.1 - Oo x<br>C a en ee aa<br>i¢ > Oo Keyword search 1 - Invoice WOL-20... ayo<br>te ‘Data Sources search 6<br>@ Fle Views ‘Table Thumbnail 09<br>® & File Types Save Table as CSV<br>& %_ Deleted Files [Se<br>2 GB©22|S MBMWDots FileSceCommunicationLieiMeape Artifactsme Deteuk a28) caeAccounts (30) NameDB(DBB8 CininatashaE-MadsomanenboQwdlabs.comaul0Lipst.E-Mea MapatadMessagesMessages Artifact Artifact NatashasinvoiceSubject:Subject:KeywordSkReeRePreview slevoice«invoice WOL-2026-004BmsginvoiceMAO. WOL-2028-0048<DateWOL-2026-D04deTo:NatasheReceived WO Ro...—_/LogicalfileSet1/natashaLocationon/LogicalFileSet1/nateshe.romenenko@wlbs.com.eu.../LogicalfileSet!/natasha.ramanenko@welabs.com.su...romanenko@yeftabs.comaus... Mosfied TimeTd0000-00-000000-00-000000:000000-00-00 000000020000 Change OOD0-KI-WORDROO 9000-00-09020000 9000-00-000200:00eons Tiene ‘Access 9On0-00-N0.0NR0D9000-00-00.0000-00OON-DO-OCORROOencom Time 00NT-KI-0Created9000-00-0000000:00—9000-00-00000R09cme Time00.0200 64521]64521}TostG42]Siee<br>BOoSMetadataAnalysis Resultsenue3) (5BeDEE-Mad Mat MessagesMessagesasArtifactArtitoct ‘SubjectACMESubject ReWOL-2034-ObkzaDute: sinvoicesirvoice  WOL-2026-O048-DatRecewedReceivedReceiv e d— /LogycalfleSet!/nstasha,romanenko®wdabs.coma../LogicalFileSet!Ms /natacha.romanenko@vdliabs.com.au... 900-00-00000000000-00-00: 000200 0000-00-00 0000-X1-00.020000 9D00:00 900 0000-00-00.008R0000-004 0 0 0009-0006 -00-00 0000-00-00000200 0 -0a  0.0 0 00 64521]4521<br>© (GB OS Accounts<br>© Gl Togs<br>© O Som<br>-& Reports<br>Her Tet Soplivion Source<br>[RestEma348 of 356 esteFie Metadata 05 count Data Atfacts yuiyin Yells Contest Annotations Other Occurrences essen |<br>Hesdes Tet HTML fT) Attachments(1) Accounts<br>‘iesNew Yitone<br>7<br>[Table] Thumbnail rman<br>‘Save Table as CSV<br>Location Se Mimetype Known<br>MogicalileSetVinatashasomenenko@wdlabs.com 12517 application/pdt unknown<br><!-- End of picture text -->



<!-- Start of picture text -->
1 NatashaMaitbax - Autopsy 423.1 - o x<br>ase View Tools Window Help<br>off Add Data Source MB images/Videos [Gj Communications Q Geclocetion FE timeine fj Discovery Generate Report gp Close Case = BB -Keywordtists | Qe Keyword Search<br>\¢ > > _Usting | Keyword search 1-Invonce WOL-20,.. teva<br>® search 6 Res<br>2 WH ©  Data File  SourcesVie Table Thumbnail Soy<br>| DeletedMB© FaeType: Files 7Save Tableas CSVa<br>2© DataD FiteCommunicaton ArifactsSine Accounts (30) NameByD natashasomanenko@wdlabs.com.au.00lEMail Messages Artifact pst KeywordSubjectNatachaeinvoice : Preview:Re slawoiceWDL:2026-00t2<.msginvoiceWOL-2026-0088<DateReceivedWD Location:/LogicslFdeSet!/nstasha.romanenko@wdiabs.com.au/LagicalFileSet1/natasha.tomanenko@wdiabs,com.au—0000-00-00Modified0000-00-00 00:0000 Time00-0020 0000-00-00 0000-00-000n0000Change TimeOG:O00 ‘Access9000-00-000000000000-00-00 Time 02000 0000-00-00Created0000-00-00000000 Time ORO 61521]4521]See<br>| ° . Benaebred Bi E-Mait Messoges Artifect Subject:Re: «invoice WDL-2026-004B<To:Natasha Ro... /LogicalFileSet !/netashe.romanenko@wdishs.com.au— 0000-IN-0000500:00  0000-00-00.00:0000 0000-00-00 00-0000 0000-00-00 00-0000 6521<br>® me Default G26) (Ch E-Mail Messages Artifect Subject:Re: sinvoice WDL-2026-0048To:Natasha Ro... /LogicaiFieSet /natasha.romanenko@walabs.com.au 0000-00-00 00:00:00  C000-00-00 00:00:00 9000-00-00 0000 0000-00-00 00:00:00 64521]<br>| Metadata(3) Di E-Mail Messages Artifact ACMESubject : clnvoice WDL-2026-(048<DatReceiv e d /LogicalfileSet/natasha.romanenko@wolabs-com.au—0000-00-00 00:00:00  0000-C0-00.00:00:00  O006-00-00.00:0200 0000-00-00 00.0009 e521<br>» BS KeywordHs (1486)<br>© BB OSAccounts<br>*O Toys score<br>/& Reports<br>He Tet Appocstion SourceFile Metadata Account Date Attfects Avsiyic Revit Conte! Anmetations Other Occurrences<br>Hesden Tet HTML 1) Attachments(1) Accounts View in New Window<br>7<br>Table Thumbnad So") ‘View Fleie Directory<br>Location View‘View inFile Newin Timeline.Window Save Table2s CSV<br>Eatract File(s)<br>Export‘Add FleSelected Tog Rows to CSV ><br>Remove File Toy ><br>= Bo: son= ‘AdeaFile to Hash Set > eafhaeasex= ~ 8S5 oe oemaE<br>16 NatasnaMailbox - Autopsy 4.23.1 - oo x<br>Care View Tools Window Help err<br>off Act Data Source MB images/Videos §E5j Communications @ Geolocaton FE, Timeine pf) Discovery i GenerateRepot q@ Clove Case © BS Keywordticts | Qe Keyword Search<br>id > 2 Kepword search} - Invoice WDL-20... th58<br>| cynord search 6 Res<br>2 WD ©  Oats FileViews Sources Toble Thumbnail 4(08h)<br>|G© FileType: Save Tableas CV<br>| MB%_ Deleted Files =e<br>oaBAB DataCommunicationFieArtifactsSe Accounts (30) Marve:Dy natathasomanenko@wdlabs.com.au00! E-Mail Messages Artifact pst Keyword‘SubjectNatathasinvoice :  PreviewRe «invoiceWDL-2026-0048«.meginvoice WDL-2026-0048-DateReceivedWD —_/LogicalfileSet!/nateshaLocation_/LogicalFileSet!/natasha.romanenko@wdlabs.com.au... romanenko@wdlabs.com.au.... Modified0000-00-0000.00:000000-00-00Time00:00 0000-00-000000-00-00Change Time 00.000002:00:00 0000-00-00‘ecess 0000-00-00.00:00:00Time00200 0000-00-000000-00-00Created Time 001000000000 68521]64521]see<br>| BI E-Mail Messages (326) 5<br>|| SABFlt DataDefaultDeron) 26) (5 E-Mail; Mezcages Artifact ‘Subject: Re slnveice WDL-2026-0045+To:Natashs Ro... /LogicalFileSet!/natesha romanenko@wadlabs.com.au.... 0000-00-00000000 0000-00-00 00000  0000-00-0000:0200 0000-00-00 000009 64521]<br>2Q6D© BS EgeMetadataKepwordyr(3) (DyDi E-MailE-Mail Messages Messages Atifact Artifact SubjectACMESubject: Re «lrwcice : slevoice WOL-2026-O048.Date WOL-Ni26-0048xDateReceivedReceived— /LogicalFileSet!/nateshasomanenko@wdlabs.com.au..../LogicalfileSet!/natasha somanenko@wdlabs.com.su.... 0000-00-00000000 0000-00-00 00:00:00 0000-00-000000-00-00 02:00:00 020000  0000-00-00.0000:00 0000-00-00.02.0200 0000-00-000000-00-00 000000 000000 64521]64521]<br>| 05 Accounts Hits (2446)<br>@ i Togs<br>2 @O sor<br>© Reports<br>Hex Tet Appicsen SourceFile Metadata O° A count Data Artifacts ost Feu Contet Annotations Other Occurrences:<br>‘Headers fo) HTML f 1) Sie hmern ) Accounts<br>HEADERS |<br>Received:by1343447 SY3PPFA341207D0.AUSP300.PROD.OUTLOOK.COM  trom«0000 SY8P300MBRI211.AUSP300,PROD.OUTLOOK.COMwith HTTPS; (2603:10610262:10) Thu, 11 Jun 2026<br>ARC-Seat te2, aerea-shal56, arcselector!0001;s» demicrosoft.comcvs pass,<br>20Z0Pkat8fIvhN/LIH+searcselector10001;TevSLACz+--Meszage-Signature: 2/P2BheMTbbctjRiP Kid V0gKRMpISOgaggprcRilqfin2; axrsa-sha256; TUFPBTELtIWVMz0goce relaxed/relaced: NCU | kp p/pS25q¥QQo6iq00z/hikOXRxYdamicrosoft.com;oye 24 16I7/HODPSX GM+ /AVBIEIFISqgOw/Sq691 GIZIIUMc TBBIKQoC4OVmiFC3HaksPHyuXoVA« SullegOnRolbIBcyhGplSuker7LDSNGaVird@OHCQhTATUXGW2Q== 1ww Wm SwOundtgnaltSccwebebDhvwzImHnexCtkw6VEP o/ gLFAY)ArredEMstG6lrbl xhUeudQSePFKT)<br>hs FrormDate: Subject Message-ID:Content-Type-MIME-Version:X-MS-Exchange-AntiSpam-MezsageData-ChunkC ount:X-MS-Exchange-AntiSpam-MessageDate-0:X-MS-Exchange-AntiSpam-MessageData- |;<br>‘bh=TXCSDex¥mZiWakglv2sSO33BI20fCOcO9p+ KEnVyaw=;<br>=I AUD CMIBVrHXSiAKH2mspbAlaXut QrE ESL IDVREXCmhikMonazéP 6D vKaUzeOr6AnivrGaBE2 1 pOcUHsuCitr.xO2H it «BEL GldmpuAf WBbEF1 HA6remXAbKs6dMoguPnZaUDay 1AdfObKL ukq7GKmi0SeHaxRUt/PRIRQVWScDwij+VtoebZIMWEQIKLRe<br>‘SSTTymkKEN2~ MGHIVVIAGV- 7)t5BePuiFeNsv8sQ2mbWESOFVUR)b IqF qaBF2DQVGczncF9yEQWIC SkayCehqO+ H3t/IRqQAlpe/ Weet7dLWtWre/JTASCsENXNMBrnGndUPA==<br>‘Authentication Results: i=2: mucmacrosott.com 1; spf=pass (sender wp is<br><!-- End of picture text -->

From: Natasha Romanenko </O=EXCHANGELABS/OU=EXCHANGE ADMINISTRATIVE GROUP (FYDIBOHF23SPDLT)/CN=RECIPIENTS/CN=B5F7E4B37023475E9ED2077375B79B55-D669C084-28> 2026-06-10 22:56:37 AEST To: ACME ae Subject: Invoice WDL-2026-0048 HTML Attachments (1) Accounts Download Images Hi Sarah, Attached is invoice WDL-2026-0048 for May services. $9,350.00 inc. GST, due 24 Jun. Thanks, Natasha 



<!-- Start of picture text -->
©<br><!-- End of picture text -->

## WDLabs Pty Ltd 

|BILL TO|In|voice Number:|WDL-2026-0048|
|---|---|---|---|
|Acme Financial Services Pty Ltd<br>||Invoice Date:<br>|70 Jun 2026<br>|
|Attn: Sarah Mitchell, Accounts Payable<br>||Due Date:<br>|24 Jun 2026<br>|
|45 Harbour Boulevard, Sydney NSW 2000<br>|P|ayment Terms:<br>|Net 14 Days<br>|
|acmebusiness2026@gmail.com||Reference:|PO-ACK 8834|
|DESCRIPTION|PERIOD|UNIT PRICE|ary<br>AMOUNT|
|Cybersecurity Consulting Services<br>Mal<br>1<br>chesten<br>B<br>respons<br>sory,<br>Uhreal<br>inbelliger|May 2026|$4,500.00|i<br>$4,500.00|
|Incident Response Retainer<br>Monthly IR.<br>retainer<br>is<br>Of1-Gall<br>8<br>ft<br>i|May 2026|$2,200.00|i<br>$2,200.00|
|Security Awareness Training Delivery<br>L<br>fig<br>Sirmiuilal<br>Meaiqn and 2x staf<br>taining|May 2026|$7,800.00|i<br>$1,800.00|
|||Subtotal<br>GST (10%):|34,500.00<br>$850.00|
|||TOTALDU|E:<br>$9,350.00|





<!-- Start of picture text -->
PAYMENT DETAILS<br><!-- End of picture text -->



<!-- Start of picture text -->
Bank: Commonwealth Bank of Australia Please include the inveica number and purchase order<br>Account Name: WDLabe Pty Lid reference in the payment description to ensure correct<br>BSB:<br>Account No: Remittance advice to:<br>“aun natasha.romanenkoiwdlabs.com.au<br>Reference: WIDL-2026-0048 / PO-ACM-Baa4 .<br>+613 9000 1234<br><!-- End of picture text -->

FOR DEMONSTRATION PURPOSES ONLY — ALL COMPANYNOTNAMES,REPRESENTACCOUNTANYNUMBERS,ABAL ENTITYGSB NUMBERSOF ACCOUNTAND FINANCIAL DETAILS ARE ENTIRELY FICTITIOUS AND Dd 



<!-- Start of picture text -->
From: Natasha Romanenko <natasha.romanenko@wdlabs.com.au> 2026-06-10 23:12:35 AEST<br>To: ACME<br>cc<br>Subject: Re: Invoice WDL-2026-0048<br>HTML Attachments (1) Accounts<br>Download Images<br>Hi Sarah,<br>Apologies - quick update before you process this, we've recently changed banking providers and our account details have been updated. It is important that the payment goes to this account because the old<br>account is closing soon.<br>Find attached.<br>Thanks,<br>Natasha<br>From: Natasha Romanenko<br>Sent: Wednesday, June 10, 2026 10:56 PM<br>To: ACME <acmebusiness2026@gmail.com><br>Subject: Invoice WDL-2026-0048<br>Hi Sarah,<br>Attached is invoice WDL-2026-0048 for May services.<br>$9,350.00 inc. GST, due 24 Jun.<br>Thanks,<br>Natasha<br><!-- End of picture text -->

From: Natasha Romanenko Sent: Wednesday, June 10, 2026 10:56 PM To: ACME <acmebusiness2026@gmail.com> Subject: Invoice WDL-2026-0048 Hi Sarah, Attached is invoice WDL-2026-0048 for May services. $9,350.00 inc. GST, due 24 Jun. Thanks, Natasha (82) he SOC Simulation Project ee 



<!-- Start of picture text -->
PAYMENT DETAILS<br><!-- End of picture text -->



<!-- Start of picture text -->
Bank: NAB Please include the invoice number and purchase order<br>Account Name: Infoservices Pty Ltd reference in the payment description to ensure correct<br>allocation.<br>BSB:<br>Account No:- Remittance advice to:=,<br>natasha.romanenko@wdlabs.com.au<br>Reference: WDL-2026-0048 / PO-ACM-8834<br>Quenes:<br>+613 9000 1234<br><!-- End of picture text -->

FOR DEMONSTRATION PURPOSES ONLY — ALL COMPANY MAMES, ACCOUNT NUMBERS, 858 NUMBERS AND FINANCIAL DETAILS ARE ENTIRELY FICTITIOUS 4ND OO NOT REPRESENT ANY REAL ENTITY OR ACCOUNT 



<!-- Start of picture text -->
Headers Text HTML RIF Attachments (0) Accounts<br>Download Images<br>Hi Natasha, no worries. A<br>Just to confirm the account name changed to ‘Infoservices’ - is that right?<br>Regards,<br>Sarah<br>On Wed, Jun 10, 2026 at 11:12 PM Natasha Romanenko <natasha.romanenko@wdlabs.com.au> wrote:<br>Hi Sarah,<br>Apologies - quick update before you process this, we've recently changed banking providers and our account details have been updated. It is important that the payment goes to this account because the old<br>account is closing soon.<br>Find attached.<br><!-- End of picture text -->

Thanks, 

Natasha 



<!-- Start of picture text -->
Headers Tet HTML RTF Attachments (0) Accounts<br>Download Images<br>Yes that is correct al<br>From: ACME <acmebusiness2026@gmail.com><br>Sent: Thursday, June 11, 2026 11:43 PM<br>To: Natasha Romanenko <natasha.romanenko@wdlabs.com.au><br>Subject: Re: Invoice WDL-2026-0048<br>Hi Natasha, no worries.<br>Justto confirm the account name changed to Infoservices' - is that right?<br>Regards,<br>Sarah _|<br><!-- End of picture text -->

|Headers<br>Tet<br>HTML<br>RTF<br>Attachments (0)<br>Accounts|
|---|
|Download Images<br>   <br>|
|Yesthatiscorrect<br>al|
|From:ACME<acmebusiness2026@gmail.com><br>|
|Sent:Thursday,June11,2026 11:43PM<br>To: NatashaRomanenko<natasha.romanenko@wdlabs.com.au><br>Subject: Re: InvoiceWDL-2026-0048|
|HiNatasha,noworries.|
|Justto confirm the account name changed to Infoservices' - is thatright?|
|Regards,<br>Sarah<br>_||



|Headers Tet<br>HTML<br>RTF<br>Attachments (0)<br>Accounts|
|---|
|Download Images|
|Great-Ihaveprocessedthepayment.<br>a|
|Kindregards,<br>Sarah|
|OnFri,Jun 12.2026 at6:56PMNatashaRomanenko<natasha.romanenko@wdlabs.com.au> wrote:<br>Yesthat is correct|
|From:ACME<acmebusiness2026@gmail.com><br>Sent:Thursday,June 11,202611:43PM|
|To: Natasha Romanenko<natasha.romanenko@wdlabs.com.au><br>Subject: Re: InvoiceWDL-2026-0048|
|HiNatasha,noworries.|
|Just to confirm the account name changed to'Infoservices' -is that right?|
|Regards,<br>Sarah|





<!-- Start of picture text -->
Time range: Custom Show:1000 results<br>t6 1)3<br>17 ~OfficeActivity<br>1918 || whereextendUserIdAADSessionId== “natasha.romanenko@wdlabs.com.au”= tostring(parse json(AppAccessContext). AADSessionId)<br>2@ | where ClientIP in (badIPs)<br>2422 | sortor AADSessionIdby TimeGenerated== "@05ccdea-964a-c068-181e-c9402d6dF272"asc [|<br>=A<br>Results Chart P<br>CO) TimeGenerated [UTC] AADSessionld UserAgent RecordType Operation Organizationld Organizationld_ UserType @<br>COC >> 6/8/2026,6/8/2026, 8:47:40.000AM 8:47:40.000AM ——005ccdea-964a-c068-181e-c94...—_005ccdea-964a-c068-181e-c94... ExchangeltemAggregatedExchangeltemAggregated MailltemsAccessedMailltemsAccessed 567ea528-4e82-40fa-914e-38c...567ea528-4e82-40fa-914e-38c...  567ea528-4e82-40fa-914e-38c...567ea528-4e82-40fa-914e-38c.. RegularRegular j z8<br>CO > 6/8/2026, 8:47:40.000AM —00Sccdea-964a-c068-181e-c94... ExchangeitemAggregated MailltemsAccessed 567ea528-4e82-40fa-914e-38c...  567ea528-4e82-40fa-914e-38c... Regular<br>CO > 6/8/2026, 8:48:18.000 AM ——005ccdea-964a-c068-181e-c94..._  Mozilla/5.0 (Windows NT 10.0;... _ SharePointListOperation ListCreated 567ea528-4e82-40fa-914e-38c.. 567ea528-4e82-40fa-914e-38c.. Regular<br>(> 6/8/2026, 8:48:19.000AM —005ccdea-964a-c068-181e-c94...  Mozilla/5.0 (Windows NT 10.0;..._  SharePointSharingOperation SharinginheritanceBroken 567ea528-4e82-40fa-914e-38c... 567ea528-4e82-40fa-914e-38c.. Regular<br>CO > 6/8/2026, 8:48:19.000AM ——005ccdea-964a-c068-181e-c94..._  Mozilla/5.0 (Windows NT 10.0; .._ SharePointListOperation ListViewed 567ea528-4e82-40fa-914e-38c...  567ea528-4e82-40fa-914e-38c.. Regular<br>(> 6/8/2026, 8:48:20.000AM —005ccdea-964a-c068-181e-c94... Mozilla/5.0 (Windows NT 10.0;....  SharePointfileOperation FileAccessed 567ea528-4e82-40fa-Q14e-38c.. 567ea528-4e82-40fa-914e-38c.. Regular<br>005ccdea-964a-c068-181e-c94...  Mozilla/5.0 (Windows NT 10.0;... _ SharePointFileOperation FileDownloaded 567ea528-4e82-40fa-914e-38c..  567ea528-4e82-40fa-914e-38c... Regular<br>CO > 6/8/2026, 8:48:27.000AM ——00Sccdea-964a-c068-181e-c94..._  Mozilla/5.0 (Windows NT 10.0;... SharePointFileOperation FileDownloaded 567ea528-4e82-40fa-Q14e-38c.. 567ea528-4e82-40fa-914e-38c.. Regular<br>CO > 6/8/2026, 8:51:52.000AM —005ccdea-964a-c068-181e-cO4... ExchangeitemAggregated MailltemsAccessed 567e2528-4e82-40fa-914e-38c...  567ea528-4e82-40fa-914e-38c... Regular<br>(> 6/8/2026, 9:12:31.000AM ——005ccdea-964a-c068-181e-<94...  Mozilla/5.0 (Windows NT 10.0;.... SharePoint SigninEvent 567ea528-4e82-40fa-914e-38c.. 567ea528-4e82-40fa-914e-38c... Regular<br>(CD > 6/8/2026, 9:12:32.000AM ——005ccdea-964a-c068-181e-c94... Mozilla/5.0 (Windows NT 10.0;... SharePoint PageViewed 567ea528-4e82-40fa-914e-38c..  567ea528-4e82-40fe-914e-38c... Regular<br>(> 6/8/2026, 9:12:37.000AM ——005ccdea-964a-c068-181e-c94..._ Mozilla/5.0 (Windows NT 10.0;... SharePoint PageViewed 567ea528-4e82-40fa-914e-38c.. 567ea528-4e82-40fa-914e-38c... Regular<br>CD > 6/8/2026, 9:12:39.000AM ——00Sccdea-964a-c068-181e-c94....  Mozilla/5.0 (Windows NT 10.0;... SharePointFileOperation FileAccessed 567ea528-4e82-40fa-914e-38c..  567ea528-4e82-40fa-914e-38c... Regular<br>a nities een oe . wet enn tnt ane nee a cet can nn ene nes ne ~<br><!-- End of picture text -->



<!-- Start of picture text -->
Logs a<br>e New Query 7* sf New Query 8 2 New Query 1* y® New Query2* «x + Observability agent (New Save vf] Sharevi ++ 8= Queries hub<br>= Time range: Custom Show: 1000 results KaLmode Vv<br>@ ou 200.162.146.129",<br>15 "54.79.179.92"<br>(Al) 16 9);<br>© 171819 OfficeActivity|| extendwhere UserIdAADSessionId== "natasha.romanenko@wdlabs.com.au”= tostring(parse json(AppAccessContext). AADSessionId)<br>2@ | where ClientIP in (badIPs) L<br>21 or AADSessionId == “@e5ccdea-964a-c068-181e-c9402d6df272"<br>22 [summarize count() by Operation<br>23 |sort by count_ =a<br>Results Chart Al K vo)<br>©.OD >Operation FileDownloaded count_62 ig:g<br>DO > MailtemsAccessed 30 a<br>OD > FileAccessed 7<br>O > PageViewed 4<br>OD > ListViewed 3<br>CD >  ListitemCreated 3<br>(C0 >  SharinginheritanceBroken 2<br>O > Create 2<br>OD > Send 2<br>© > FilePreviewed 1<br>C0 > PagePrefetched 1<br>(> SearchQueryPerformed 1<br>OD > SigninEvent 1<br>© > GlientViewSignaled 1<br><!-- End of picture text -->



<!-- Start of picture text -->
< G |G https:/www.abuseipdb.com/bulk-check Aaxt © + om ~-<br>@Abuseipps ReportIP Bulk Checker Bulk Reporter Pricing Integrations + Docs IP Utilities» | Contact More~ & imranatasi~ ®<br>Need to check many IPs at once? Upload your list as a TXT file and get results in seconds. It's faster, more efficient, and designed for high-volume checks.<br>Note: This tool runs on our API. Your daily usage limits depend on your subscription plan.<br>Bulk Check Upload Settings J ussoeoveriew<br>API Key @ Checks used today: 24/1000 @<br>Practice v Bulk checks used today: 1/5 =<br>Max IPs per bulk check: 1000<br>Max Age (days) @<br>x83reg Options:30a<br>C Remove duplicates @<br>C Allow partial @<br>Upload TXT @<br>Choose File | No file chosen<br>Max file size: 8 MB<br>Bulk Check History<br>ID Status Progress Created # of IPs Download Action<br>01a02e27-950c-7efb-9868-da5c9b 1c066f Completed 100%9 5 seconds ago 24<br><!-- End of picture text -->



<!-- Start of picture text -->
File Home insert Page Layout Formulas + Data._««sReview += View‘ Help_—Nitro Pro. Acrobat. @ Share<br>Pastea~  éClipboardFormatEicopy en ~ Painter 5 Calibri idFont “in kw)a 5 ===Ses= SB) eeczSeAlignment| 8BwepterSwear 5 General$+ Number% 9 8S.5 Formatting»Conditionalfa FormatTableER~as = BadStyles Goodplanati Neutral . BBInsert>DeleteCells Formats @2 Autosum Clear~Fill» Editing~ Filter»Sort47& LpSelectFind&~ AdobeCreatea PDF>Acrobat A<br>L29 ~|@ fe v<br>4 A 8 c D E F 6 H Il J kK L M N cs)<br>1 |ipAddress isPublic _ipVersion isWhitelisted abuseConfidence! countryCode usageType isp domain hostnames isTor _totalReports numDistinctUsers lastReportedAt<br>2 |202.128.121.70 1 4 t) oau Fixed Line ISP LEAP leaptel.com.au _202.128.121.70.vic.leaptel.network t) 0 o<br>3 is ° 6 t) o Reserved t) 29 1 2026-08-23T01:23:18<br>4 |2603:1046:a00:8::4 1 6 oO OAU Data Center/Web Hosting/Transit Microsoft Corporation microsoft.com 0 tC) tC)<br>5 |49.185.122.38 1 4 t) oau Fixed Line ISP Optus Internet Pty Ltd optus.net.au pa49-185-122-38.pa.vic.optusnet.com.au t) 0 0<br>6 |2603:1016:401:2822::5, 1 6 t) oau Data Center/Web Hosting/Transit Microsoft Corporation microsoft.com t) ° °<br>7 /103.51.113.20 1 4 t) oaU Fixed Line ISP Leaptel leaptel.com.au _ 103.51.113.20.vic.leaptel.network t) 0 )<br>8 |37.140,254.32 1 4 t) 17 CH Data Center/Web Hosting/Transit VPN Consumer Network Services vpnconsumer.com t) 2 2 2026-07-31T01:00:11<br>9 |173.239.216.150 1 4 t) 42.CH Data Center/Web Hosting/Transit LogicWeb Inc. logicweb.com t) 5 5 2026-08-13T09:43:11<br>10 |85.204.124.86 1 4 ° 22 RO Data Center/Web Hosting/Transit M247 Europe SRL m247global.com t) 2 2 2026-08-05T16:23:2¢<br>11 |85.204.124.84 1 4 t) 20 RO Data Center/Web Hosting/Transit M247 Europe SRL m247global.com t) 3 3 2026-08-05T23:05:25<br>12|52.106.216.136 1 4 t) oau Data Center/Web Hosting/Transit Microsoft Corporation microsoft.com t) 0 0<br>13 |85.204.124.85 1 4 t) 34 RO Data Center/Web Hosting/Transit M247 Europe SRL m247global.com t) 7 6 2026-08-05T21:05:14:<br>14|20.190.142.169 1 4 0 2AU Data Center/Web Hosting/Transit Microsoft Corporation microsoft.com t) 1 1 2026-07-29723:52:18<br>15 |4.147.25.124 1 4 t) oau Data Center/Web Hosting/Transit Microsoft Corporation microsoft.com t) o )<br>16 |54.79.179.92 1 4 t) oau Data Center/Web Hosting/Transit Amazon.com, Inc. amazon.com ec2-54-79-179-92.ap-southeast-2.compute.amazonaws.com t) 0 0<br>17 |85.204.124.83 1 4 t) 18 RO Data Center/Web Hosting/Transit M247 Europe SRL m247global.com t) 4 3 2026-08-05T21:05:14:<br>18 |202.179.131.77 1 4 t) oaU Fixed Line ISP Leaptel leaptel.com.au _202.179.131.77.vic.leaptel.network t) o °<br>19 |200.162.146.87 1 4 t) ONL Data Center/Web Hosting/Transit ExpressVPN expressvpn.com t) 0 0 2026-06-18T16:50:14:<br>20 |37.140.254.42 1 4 t) 17 CH Data Center/Web Hosting/Transit VPN Consumer Network Services vpnconsumer.com t) Ey 2 2026-07-31701:49:35<br>21 |37.140.254.43 1 4 t) 19 CH Data Center/Web Hosting/Transit VPN Consumer Network Services vpnconsumer.com t) Ey 3 2026-07-31T08:25:01<br>22 |200.162.146.253 1 4 t) 2NL Data Center/Web Hosting/Transit ExpressVPN expressvpn.com t) CY) 0 2026-07-14T12:06:<br>23 |200.162.146.109 1 4 t) ONL Data Center/Web Hosting/Transit ExpressVPN expressvpn.com t) 0 0 2026-06-10T13:40:1<br>24 |200.162.146.203 1 4 t) 1NL Data Center/Web Hosting/Transit ExpressVPN expressvpn.com t) 0 0 2026-07-14T11:57:18<br>25 |200.162.146.129 1 4 t) 8 NL Data Center/Web Hosting/Transit ExpressVPN expressvpn.com t) 0 0 2026-07-14T11:26:14:<br>26<br>27<br>28<br>2930 |<br>31<br>32<br>33<br>34<br>35<br>36<br>37 i<br>01a02e27-950c-7efb-9868-da5c9b1 ® 5 jr)<br>Ready E23 =] -——#——-+ 100%<br><!-- End of picture text -->



<!-- Start of picture text -->
< GB https://ip-api.com/#54,79.179.92<br>@ip-api DOCUMENTATION SIGN UP CONTACT<br>AP| Demo<br>Search any IP address/domain<br>ee. ELANUKA<br>£ EN Hornsby HEIGHTS3<br>“query”: "54.79.179.92", WAHROONGA Fe<br>Astatus":ae "success",. LE<br>“continent”: “Oceania”, PYMBLE<br>="continentCode":‘a ies: "OC",” IRTH 9 ALLAMBIE ~<br>“countryCode":country": “Australia”,"AU", IAT. eppinG ;A eget, Ne<br>"region": "NSW", DENISTONE pais “Chatswood<br>“regionName": "New South Wales”, Be WEST a<br>“city":“district”:"Sydney","", mySie Morns 9, h Sydney<br>“rip": "2000", Lay<br>"Lat": -33.8591, JBURN e ney<br>"lon": 151.2002, FINE BEN ~<br>"timezone": “Australia/Sydney”, LEICHHARDT Hes<br>"offset": 36000, of PETERSHAM gg<br>*ENEAUD CAMPSIE,aN bef RANDWIC<br>“isp”:“org”: "Amazon"AWS EC2Corporate(ap-southeast-2)",Services Pty Ltd, Amazon.com, Inc.”, atn4 2"MASCOTee aah Le<br>"“ as ":name":"AS16509"AMAZON-02",Amazon.com, Inc.”, } BRIGHLe SAM-WOM Xi .—<br>"mobile": false, Y ;<br>“proxy”: false, raf fie<br>E “hosting”: true ~ SYLVA!ib,Ei sougl bercait aes<br><!-- End of picture text -->

