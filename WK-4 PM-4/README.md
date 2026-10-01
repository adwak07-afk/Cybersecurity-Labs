

NETWORKWALKS
WEEK 4 • AUTHORIZED SECURITY ASSESSMENT

PENETRATION
TESTING REPORT
MEDIROZA GENERAL HOSPITAL
https://medirozahospital.com
Prepared by	Adewuyi Wakeel (Pen Tester)
Course / Engagement	Cybersecurity Int. B083A — Waqas Karim, CCIE
Assessment Type	Authorized Black-Box Penetration Test
Client / Target	Mediroza General Hospital
Authorization	Written permission granted for the controlled training environment
Assessment Date	30th September 2026
Classification	CONFIDENTIAL
 

01 — Engagement Overview
Authorization & Liability
This report covers cybersecurity testing carried out solely within the sanctioned Mediroza General Hospital training environment. The engagement took the form of a controlled black-box assessment targeting the web application. Testing was confined to the approved target; denial-of-service attacks, social engineering, and testing of unrelated systems were excluded.
The project serves an educational purpose: identifying security flaws, assessing their potential impact, and outlining practical remediation. The techniques described should not be used against systems without explicit authorization from the system owner.

Executive Summary
The Week 4 engagement followed a realistic penetration-testing workflow from reconnaissance through impact analysis and reporting. The supplied evidence confirms the public-facing Mediroza website, a dedicated patient login portal, sensitive paths disclosed through robots.txt, and a patient-report area containing three encrypted pathology reports.
The broader workflow included controlled authentication testing, password-strength assessment of protected PDFs, investigation of legacy content, and review of potential exposure of employee or shareholder information. Patient information, recovered passwords, salary figures, and shareholder details are intentionally withheld from this report.
Scope & Methodology
Target	https://medirozahospital.com
Engagement model	Authorized educational black-box web-application assessment
Primary objectives	Identify entry points; evaluate authentication and access control; examine protected patient documents; assess document-password strength; investigate legacy resources; check sensitive organizational-data exposure; provide remediation guidance.
Rules of engagement	Approved domain only. No denial-of-service, social engineering, destructive changes, or out-of-scope systems.
Evidence policy	Only supplied screenshots are treated as visual proof; other stages are described narratively without fabricated evidence.
 

02 — Tools & Assessment Workflow
Tool / Technique	Purpose
Web Browser / Firefox	Manual navigation, authentication review, portal validation, and inspection of web-accessible resources.
robots.txt Review	Passive discovery of paths excluded from search-engine crawling but visible to users.
curl	Direct HTTP request/response inspection and validation of web resources.
SQL Injection Testing	Authorized assessment of whether authentication inputs are handled safely by the back-end application.
Browser Developer Tools	Inspection of page source and login-form behaviour.
Networkwalks Hash Calculator / Password Cracker	Lab tools for PDF hash extraction and dictionary-based password assessment.
Text / Database Analysis Utilities	Review of retrieved legacy backup material for sensitive-data exposure without altering original evidence.
Claude	Conversion of raw SQL data into readable tables during analysis.
Assessment Sequence
The work was arranged chronologically so that each stage answered a specific security question and demonstrated how one weakness could increase the impact of another.
1. Initial reconnaissance and application mapping
2. Patient-portal authentication review
3. Passive discovery through robots.txt
4. Patient-report area review
5. Controlled retrieval of protected PDF reports
6. PDF encryption and hash preparation
7. Authorized password-recovery assessment
8. Verification of decrypted documents
9. Legacy /old/ resource review
10. Database-backup and sensitive-information review

 

03 — Technical Assessment
3.1 Initial Reconnaissance & Application Mapping
The public-facing Mediroza General Hospital website was examined first. Its homepage displayed navigation items including Home, About, Doctors, Contact, Staff Login, and Patient Portal. The dedicated patient authentication section was treated as a high-value target because access to it could expose confidential medical records.
3.2 Patient Portal Authentication Surface
The Patient Portal presented a standard username/password form, a Sign-in button, and an option to reveal the typed password. The authorized scope included controlled SQL-injection testing against the login system to determine whether attacker-supplied values could alter an underlying database query. A secure implementation should treat input as data, use parameterized queries, and reject access without valid credentials.
3.3 Public Discovery of Sensitive Paths through robots.txt
The robots.txt file listed three disallowed paths — /patient/, /staff/, and /old/ — together with a sitemap link. A robots.txt entry is not an access-control mechanism; it is a request to compliant crawlers to avoid indexing a path. Sensitive directories therefore still require real authentication and authorization. The /old/ path was particularly relevant because legacy resources can contain forgotten backups, outdated files, or older application components.
3.4 Patient Report Area
The evidence described a patient-report section containing three downloadable pathology reports, each labelled with a patient's name and marked as an encrypted PDF. A note indicated that report passwords came from the laboratory. This creates two security layers: portal access control and document-level password protection.
3.5 Controlled Retrieval of Protected PDFs
The three reports were downloaded into the controlled test environment for authorized offline assessment. This confirmed that the risk extends beyond webpage visibility to acquisition of protected files. The files were treated as sensitive evidence and retained only within the project's findings area.
3.6 PDF Encryption and Hash Preparation
Each protected PDF was handled independently. The process identified the encryption type and extracted a password-verification hash using the Networkwalks Hash Calculator. The hash does not directly reveal the password; it provides a reference against which candidate passwords can be tested separately. Actual hash values are intentionally omitted.
3.7 Authorized Password-Recovery Assessment
The extracted PDF hashes were subjected to dictionary-based password testing using the Networkwalks Password Cracker. Each file was assessed individually. The purpose was to determine whether weak, reused, predictable, or common passwords could undermine document encryption. Specific recovered passwords are intentionally omitted.
3.8 Verification of Decrypted Documents
A recovered password is treated as confirmed only when it successfully unlocks its corresponding PDF in the controlled environment. Confidential medical content is not reproduced unnecessarily in the final report.
 

04 — Legacy Resources & Data Exposure
4.1 Legacy /old/ Resource Review
The /old/ path identified during reconnaissance was singled out for follow-up because legacy directories can contain obsolete components, archived material, or backup data that remains reachable after active use has ended. The project workflow specifically called for investigating previously gathered material for a further significant exposure on the server.
4.2 Database Backup Exposure
Database backups can contain substantially more information than normal application pages, including user records, internal identifiers, historical entries, credentials or password hashes, employee data, and ownership details. A backup reachable through the web should therefore be treated as a serious configuration issue even when the live application otherwise enforces access controls.
4.3 Employee Salary Information
The review included searching recovered database content for employee records and salary fields. Exposure of salary information represents a confidentiality issue and can increase privacy, fraud, social-engineering, and reputational risks. Actual names and figures are withheld from this report.
4.4 Shareholder and Ownership Information
The recovered material was also reviewed for shareholder-related information such as names, share allocations, contact details, or ownership records. Such information should remain within protected project evidence rather than a public-facing report. The finding is framed as sensitive corporate-data exposure associated with insufficient protection of legacy backup files.
Data-handling note: Detailed patient, employee, financial, ownership, hash, and password evidence should remain restricted to the authorized project evidence set. This report deliberately summarizes the categories of exposure rather than reproducing sensitive records.

 

05 — Risk Analysis
The ratings below reflect the likely security significance of the Week 4 findings. They are based on the supplied report's assessment and distinguish direct observations from later-stage impacts documented through the authorized workflow.

#Finding	Finding	Risk	Impact / Justification
1	Patient authentication weakness / potential SQL injection	High	Unsafe input handling could permit authentication bypass and access to protected medical resources.
2	Protected patient reports reachable after portal access	High	Unauthorized portal access can expose confidential reports and enable offline attacks against document passwords.
3	Sensitive paths disclosed in robots.txt	Low	Reveals /patient/, /staff/, and /old/, aiding reconnaissance but not bypassing access control by itself.
4	Weak PDF password protection	High	Predictable or crackable document passwords can undermine encryption after files are obtained.
5	Legacy /old/ content exposed	High	Forgotten resources may expose backup files or outdated components outside normal application controls.
6	Database backup accessible from web content	Critical	A single exposed backup can disclose large volumes of application, employee, and corporate data.
7	Employee salary information exposure	High	Confidential HR data can create privacy, targeted-social-engineering, and reputational risks.
8	Shareholder information exposure	High	Sensitive ownership information can create commercial, privacy, and targeted-fraud risks.
 

06 — Recommendations & Remediation
1. Use parameterized queries
All authentication and data-access queries should use prepared statements or parameterized APIs. User input should never be concatenated directly into SQL.
2. Strengthen authentication controls
Implement secure credential verification, generic error messages, rate limiting, secure session management, and server-side authorization checks on every protected resource.
3. Do not rely on robots.txt for protection
Sensitive paths require genuine authentication and authorization. Remove unnecessary directory references and avoid exposing legacy locations publicly.
4. Remove or isolate legacy content
Delete obsolete directories from the production web root. If retention is necessary, move backups to non-web-accessible storage with restricted permissions.
5. Protect database backups
Never serve backups through the web application. Encrypt backups at rest, restrict access, apply retention policies, and monitor backup repositories.
6. Use strong document protection
Apply long, unique, randomly generated passwords to protected files and avoid predictable lab, patient, date, or dictionary-based passwords.
7. Prefer secure document delivery
Where possible, use authenticated portal access and protected server-side storage rather than long-lived encrypted documents that can be attacked offline.
8. Minimize sensitive-data exposure
Store only necessary employee and shareholder data, apply least privilege, and redact or tokenize highly sensitive fields where feasible.
9. Centralize logging and alerting
Monitor repeated authentication failures, abnormal file downloads, directory enumeration, and access to legacy or backup locations.
10. Conduct periodic security reviews
Repeat authorized penetration tests after remediation, including regression testing for authentication, access control, backup exposure, and sensitive-file handling.
 
07 — Evidence Register

All screenshots supplied below by the pen tester are treated as embedded visual evidence. No substitute images are created for stages without user-provided visual evidence from basic reconnaissance to analysis of significant confidentiality information.

 <img width="954" height="413" alt="WK-4 Pic18" src="https://github.com/user-attachments/assets/209445ba-56bc-43c7-ad7a-7e2234e658ed" />
<img width="954" height="424" alt="WK-4 Pic17" src="https://github.com/user-attachments/assets/9c79f62c-97d5-4e1e-a8b0-a3c799075f69" />
<img width="953" height="291" alt="WK-4 Pic16" src="https://github.com/user-attachments/assets/3907d53c-7dd9-4c12-91a2-18d73680a1b0" />
<img width="960" height="152" alt="WK-4 Pic15" src="https://github.com/user-attachments/assets/2975fb70-1d72-4a91-8676-fc787c373ce2" />
<img width="470" height="293" alt="WK-4 Pic14" src="https://github.com/user-attachments/assets/d2431d93-f1d0-42fa-ab58-f503f4abe5a1" />
<img width="458" height="323" alt="WK-4 Pic13" src="https://github.com/user-attachments/assets/d0befd01-fa3b-4a74-ba4b-90d6effea398" />
<img width="780" height="406" alt="WK-4 Pic12" src="https://github.com/user-attachments/assets/e597a13d-3e14-45d8-82a4-ce54c04f8bc9" />
<img width="953" height="460" alt="WK-4 Pic11" src="https://github.com/user-attachments/assets/1406a906-c7e2-40af-8f9d-8af9769a2c06" />
<img width="957" height="462" alt="WK-4 Pic10" src="https://github.com/user-attachments/assets/f6d7e8f0-fa30-4713-bcfb-2dd728cc0e5d" />
<img width="959" height="464" alt="WK-4 Pic9" src="https://github.com/user-attachments/assets/b0c893ad-f217-46d2-a7a8-34522de8dc85" />
<img width="960" height="471" alt="WK-4 Pic8" src="https://github.com/user-attachments/assets/3dec3420-adab-4730-8c52-7bf75621e757" />
<img width="956" height="177" alt="WK-4 Pic7" src="https://github.com/user-attachments/assets/6aacbb1e-2b6e-4204-806b-aff314db64cd" />
<img width="955" height="457" alt="WK-4 Pic6" src="https://github.com/user-attachments/assets/03e77eff-83b6-41bf-b31e-02961b0024ad" />
<img width="555" height="468" alt="WK-4 Pic5" src="https://github.com/user-attachments/assets/57db3c49-bc17-4861-85e2-fc5e3843d304" />
<img width="764" height="357" alt="WK-4 Pic4" src="https://github.com/user-attachments/assets/8137d6cd-390d-4408-a981-43530bd41524" />
<img width="788" height="373" alt="WK-4 Pic3" src="https://github.com/user-attachments/assets/80c43f8f-bc91-4610-ad38-e1e6c3579f74" />
<img width="411" height="282" alt="WK-4 pIC2" src="https://github.com/user-attachments/assets/632c6021-1965-4147-b1c8-951b0d94e2ad" />
<img width="812" height="269" alt="WK-4 Pic1" src="https://github.com/user-attachments/assets/9bb72e2e-2737-4302-b7e7-faad571bbf45" />




 
 
 





 


 
 


 


 
 

 

 

 

 

 

 

08 — Conclusion
The Week 4 Mediroza engagement demonstrates how a black-box assessment can progress from basic reconnaissance to analysis of significant confidentiality risks. The public-facing application exposes a patient portal, while robots.txt reveals role-specific and legacy paths that help map the application's structure. The supplied evidence also confirms three encrypted pathology reports in the patient-report area, placing authentication and document security at the centre of the assessment.
The broader workflow examines whether authentication can be bypassed through unsafe input handling, whether protected PDFs can withstand offline password attacks, and whether legacy server resources expose database backups containing confidential employee or shareholder data. These stages illustrate how a seemingly minor weakness can become more significant when combined with weak access control, predictable document passwords, or poorly secured backup data.
The recommended remediation approach is layered: secure database queries, enforce authorization across sensitive resources, remove legacy content from public access, store backups outside the web root, strengthen document-password practices, minimize sensitive-data exposure, and monitor unusual authentication and file-access activity. A focused retest should follow remediation to confirm that identified attack paths have been closed.






Prepared by: Adewuyi Wakeel
CONFIDENTIAL — For authorized training, assessment, and remediation use only.

