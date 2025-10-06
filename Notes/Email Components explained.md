## Headers:
Headers are lines of metadata attached to an email and contain many useful string of information for analysis and investigators.

##### Basic headers:
- **From:** Email addresses and name of the sender. Can be spoofed to impersonate someone.
- **To:** Recipients's email address. May expose multiple addresses (in mass mails).
- **Date:** Timestamp of when the email was sent. Mismatched times can reveal forged headers.
- **Subject:** Title of the email. May contain urgency of fear phishing.

##### Technical headers:
- **Return-Path:** Actual return address for bounced emails. Often used to trace spoofing.
- **Received:** Shows the path an email took from sender to recipient. Useful to detect anomalies in sending servers.
- **Reply-To:** Address used when replying. May differ from "From:" in phishing attempts.
- **Message-ID:** Unique identifier for the email. Useful for identifying duplicates or threading.
- **DKIM-Signature:** Validates domain ownership using cryptographic signature. Missing or invalid DKIM suggests forgery.
- **Sender Policy Framework (SPF):** Checks if the sender IP is authorized to sen email for that domain. Failing SPF means possible spoofing.
- **Authentication-Results:** Shows results of SPF, DKIM, and DMARC checks. Failures here are red flags for spoofed emails.
- **X-Originating-IP:** Reveals the sender's IP (if present, sometimes leaks attacker location).
- **MIME-Version:** Specifies the NAME version used.
- **Content-Type:** Type of content (e.g. HTML, text, multipart). HTML and multipart/mixed may contain hidden links or scripts.
- **User-Agent:** Email client or software used to sent the email. Can indicate suspicious tools. Odd or blank entries may signal mass mailers or spoofers.
## Body:
The email body is the main content of an email message that is visible to the recipient.
It typically contains the message that the sender wants to convey, including text, images, links, and any attachments.

#### Body Elements:
- **Body content:** Main message (text, HTML, or both). May include scams, threats, fake, updates, or lies.
- **Hyperlinks:** Clickable text or buttons that redirect to a webpage or resource. Common in newsletters, updates, promotions, etc. Can hide malicious links under clean-looking text.
- **Display Name:** The name shown next to the sender's address. used for clarity and to identify the sender. Can mismatch real email address to trick users.
- **Branding/Logos:** Visual elements like company logos or colors to reflect the sender's brand identity. Copied logos can make fake emails look real.
- **Language/Tone:** Conveys style (formal, casual, informative). Poor grammar or forced urgency are red flags.
- **Attachments:** Files sent with the email (PDFs, images, etc.).
- **HTML Forms:** Embedded forms (surveys, RSVP, etc). Can contain malware, exploits, or malicious macros.
- **Formatting (Tables, Styles):** Helps organize and beautify the content. Used to mislead or hide malicious content.
- **Email Signature:** Sender's title, phone, company info. Faked names and titles can create false trust.
- **Alt Text (Images):** Description for images when not loaded. Can guide content or manipulate spam filters.
- **Tracking Pixels:** 1x1 invisible images to detect/read events. Used to track victims or validate targets.
- **Inline images:** Images displayed inside the message. Can contain visual lures or fake buttons.
- **Multilingual Text:** Used for international readers. Fake language blocks used to seem more official.
- **Social Media Icons:** Links brand's social platforms. Can redirect to phishing pages.

## Addresses:
# ![[Drawing 2025-10-06 04.37.37.excalidraw]]
- **Email Address:** A unique identifier in the format [local-part@domain.com](#). Attackers spoof or create look-alike addresses.
- **Local Part:** The part before @ (Usually the user's mailbox name). Can be random or similar to trusted usernames to trick recipients.
- **Domain name:** The part after @ (Points to the mail server). Attackers use typosqatted or malicious domains.
- **Top-Level  Domain (TLD):** The suffix after the las dot in the domain (e.g., .com, .org, .gov). Categorizes or identifies the domain type or country.
- **Subdomain:** A Prefix added before the main domain. often used for service segregation. Can be abused to make links appear legitimate (e.g., login.bank.example.com.attacker.net).
- **Alias/Display Name:** A friendly name that appears in the email client. Often spoofed to impersonate legitimate contacts.
- **IP Address of Mail Server:** Numeric address used by the mail server to send/receive messages.
- **Return address / Envelope From:** The technical sender address used by the mail transport for bounces. Often different from visible **From:** in phishing to evade detection.
 
## Protocols:
- **SMTP (Simple Mail Transfer Protocol):** Protocol used to send and relay outgoing email between servers. Open or misconfigures SMTP relays can be abused for spam or spoofing.
- **POP3 (Post Office Protocol v3):** Downloads email from server to local client, usually deletes the server copy after retrieval. Unencrypted POP3 can expose credentials to attackers.
- **IMAP (Internet Message Access Protocol):** Syncs email between server and client keeping messages stored on the server. Weak authentication or lack of encryption can be exploited.
- **MIME (Multipurpose Internet Mail Extensions):** Defines how to send different content types (HTML, attachments, images) in email. Malicious payload often hide in MIME attachments.
- **TLS/STARTTLS:** Encrypts the connection between mail clients and servers. If missing or downgraded, attackers can intercept or modify emails (MITM).

## Mail Agents:
 - **MUA (Mail User Agent):** The client used by the end user to read, write, and send email (e.g., Outlook, Thunderbird, Gmail webmail). Users can be tricked to open malicious attachments or click links.
 - **MSA (Mail Submission Agent):** Receives outgoing mail from MUAs and forwards it to the next hop (usually an MTA). Misconfigured MSAs may allow unauthorized relaying.
 - **MTA (Mail Transfer Agent):** Routes and transfers mail between servers (e.g., Postfix, Exim, Sendmail). Open relays or vulnerable MTAs can be abused for spam.
 - **MDA (Mail Delivery Agent):** Delivers messages to the recipient’s mailbox (e.g., Dovecot, Procmail). Weak filters can let malicious emails into inboxes.
 - **Webmail Interface:** Browser-based access to email (e.g., Gmail, Yahoo Mail). Phishing pages often mimic legitimate webmail logins.
 - **Security Gateways / Filters:** Tools that scan, block, or quarantine malicious email before delivery. Misconfiguration can allow attacks to pass through or block legitimate mail.