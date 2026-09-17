---
title: Concepts about EMAIL
description: Concepts very importants to investigate email headers
date: 2025-05-21 10:00:00 +0000
categories: [Information]
tags: [Sherlock, HacktheBox, EMAIL]
pin: false
mermaid: true
---


# Blue Team — Email Analysis Concepts

## 1. Email Fundamentals

### SMTP — Simple Mail Transfer Protocol

A protocol used to send and transfer emails between mail clients and mail servers.

### MTA — Mail Transfer Agent

A mail server component responsible for transferring emails between mail servers using SMTP.

### MUA — Mail User Agent

An application used by a user to read, compose, and send emails, such as Gmail or Outlook.

### Mailbox

The location where a user's received emails are stored.

### Email Header

Metadata containing information about an email, such as the sender, recipient, routing information, authentication results, and message ID.

### Email Body

The actual content of an email. It can contain plain text, HTML, images, links, and other content.

### SMTP Envelope

Information used by SMTP during mail delivery. It mainly contains the envelope sender (`MAIL FROM`) and envelope recipient (`RCPT TO`).

### MIME — Multipurpose Internet Mail Extensions

A standard that allows emails to contain different types of content, such as plain text, HTML, images, and attachments.

---

# 2. Email Authentication

## SPF — Sender Policy Framework

An email authentication mechanism that allows a domain to specify which servers or IP addresses are authorized to send email on its behalf.

Example:

```text
example.com
     |
     v
SPF Record
     |
     v
Authorized IP addresses
```

### Important

An `SPF PASS` does **not automatically mean that an email is legitimate**.

SPF primarily validates the domain used by the SMTP envelope sender.

---

## DKIM — DomainKeys Identified Mail

An email authentication mechanism that uses cryptographic signatures to verify that an email was authorized by a domain and that the signed content was not modified after signing.

DKIM uses:

* A private key to create the signature.
* A public key published in DNS to verify the signature.

Example:

```text
Sender
   |
   | Private Key
   v
DKIM Signature
   |
   v
Email
   |
   v
Recipient
   |
   | Public Key from DNS
   v
Signature Verification
```

### Important DKIM fields

```text
d=example.com
s=selector1
```

* `d` = Domain that signed the email.
* `s` = DKIM selector.

The public key can usually be found through:

```text
selector1._domainkey.example.com
```

---

## DMARC — Domain-based Message Authentication, Reporting and Conformance

An email authentication policy that uses SPF and/or DKIM to determine whether the visible `From` domain is properly authenticated and aligned.

DMARC helps protect against domain impersonation and spoofing.

---

## SPF Alignment

The relationship between the domain authenticated by SPF and the domain shown in the visible `From` address.

Example:

```text
From:
user@example.com

SPF domain:
example.com
```

The domains are aligned.

---

## DKIM Alignment

The relationship between the domain used in the DKIM signature and the domain shown in the visible `From` address.

Example:

```text
From:
user@example.com

DKIM:
d=example.com
```

The domains are aligned.

---

## ARC — Authenticated Received Chain

A mechanism that preserves email authentication results when a message passes through intermediaries such as forwarding services or mailing lists.

---

## Authentication-Results

An email header containing the authentication results performed by the receiving mail server.

Example:

```text
Authentication-Results:
    spf=pass
    dkim=pass
    dmarc=pass
```

Common results include:

```text
pass
fail
softfail
neutral
none
```

---

# 3. Important Email Headers

## From

Specifies the sender identity displayed to the recipient.

Example:

```text
From: "PayPal" <user@example.com>
```

The `From` field should not be trusted by itself because attackers can manipulate or spoof the displayed sender information.

---

## To

Specifies the recipient shown in the email header.

Example:

```text
To: victim@example.com
```

---

## Reply-To

Specifies the address where replies should be sent.

It can be different from the `From` address.

Example:

```text
From: support@example.com
Reply-To: attacker@evil.com
```

This is something that should be investigated during phishing analysis.

---

## Return-Path

Specifies the envelope sender address used for handling bounced or undeliverable emails.

Example:

```text
Return-Path: <bounce@example.com>
```

The `Return-Path` can be different from the visible `From` address.

---

## Received

A header added by mail servers to record the path an email took through the mail infrastructure.

Example:

```text
Received: from mail.example.com
    by mx.google.com
```

### Important

When analyzing an email path, `Received` headers are generally read **from bottom to top**.

Example:

```text
Received: Server C -> Gmail
Received: Server B -> Server C
Received: Server A -> Server B
```

The approximate path is:

```text
Server A
   |
   v
Server B
   |
   v
Server C
   |
   v
Gmail
```

---

## Delivered-To

Indicates the mailbox where the receiving mail system ultimately delivered the email.

Example:

```text
Delivered-To: victim@gmail.com
```

---

## Message-ID

A unique identifier assigned to an email message.

Example:

```text
Message-ID: <123456@example.com>
```

It can be useful for identifying and correlating messages during an investigation.

---

## Subject

Contains the subject or title of the email.

Example:

```text
Subject: Your account has been suspended
```

The subject can also be useful for identifying phishing and social engineering techniques.

---

## Date

Indicates the date and time associated with the email.

Example:

```text
Date: Mon, 15 Aug 2022 10:35:01 -0400
```

---

# 4. Email Analysis

## Email Spoofing

The manipulation of email information to make a message appear to come from a different sender or domain.

Example:

```text
From: PayPal <attacker@evil.com>
```

The display name says `PayPal`, but the actual domain is `evil.com`.

---

## Phishing

A social engineering technique that attempts to trick users into:

* Revealing credentials.
* Clicking malicious links.
* Downloading malicious files.
* Sending sensitive information.
* Performing an attacker-controlled action.

---

## Brand Impersonation

The use of a legitimate organization's name, logo, or visual identity to make a malicious message appear trustworthy.

Example:

```text
PayPal
Microsoft
Amazon
Google
Apple
```

An attacker may copy their branding to make a phishing email look legitimate.

---

## Social Engineering

The manipulation of people into performing actions or revealing information that benefits an attacker.

Common techniques include:

* Urgency.
* Fear.
* Authority.
* Curiosity.
* Rewards.
* Account warnings.

---

## Display Name

The human-readable name displayed for an email sender.

Example:

```text
From: "PayPal Security" <random@evil.com>
```

The display name is:

```text
PayPal Security
```

The actual email address is:

```text
random@evil.com
```

### Important

The display name can be manipulated and should not be treated as proof of the sender's identity.

---

# 5. URL Analysis

## URL Analysis

The process of examining URLs in an email to determine:

* The actual destination.
* The domain.
* Subdomains.
* Parameters.
* Redirects.
* URL fragments.
* Suspicious paths.
* Possible malicious behavior.

Example:

```html
<a href="https://evil.com/login">
    PayPal
</a>
```

The visible text says:

```text
PayPal
```

but the actual destination is:

```text
https://evil.com/login
```

---

## URL Fragment

The portion of a URL following the `#` character.

Example:

```text
https://example.com/page.html#section1
```

The fragment is:

```text
#section1
```

Fragments are normally processed by the browser and are not sent to the web server as part of the HTTP request.

JavaScript can access the fragment using:

```javascript
window.location.hash
```

Attackers may use URL fragments to pass information to JavaScript or to make URLs more difficult to analyze.

---

## Redirect

A mechanism that sends a user from one URL to another URL.

Example:

```text
Email Link
    |
    v
tracking.example.com
    |
    v
redirect.example.com
    |
    v
malicious-site.com
```

Attackers can use redirects to hide the final destination.

---

# 6. Encoding and Obfuscation

## Obfuscation

The process of making information difficult to understand or analyze while preserving its functionality.

Common examples include:

```text
Base64
HTML Entities
URL Encoding
Unicode
Hexadecimal
JavaScript Obfuscation
```

---

## HTML Entity Encoding

A method of representing characters in HTML using encoded values.

Example:

```html
&#87;&#97;&#108;&#109;&#97;&#114;&#116;
```

This represents:

```text
Walmart
```

Attackers may use HTML entities to make malicious content harder to detect or analyze.

---

## URL Encoding

A method of representing special characters in URLs using percent-encoded values.

Example:

```text
%20
```

represents:

```text
space
```

Example:

```text
https://example.com/hello%20world
```

---

## Base64

An encoding scheme that represents binary or textual data using a set of 64 characters.

Common characters include:

```text
A-Z
a-z
0-9
+
/
=
```

Example:

```text
SGVsbG8=
```

decodes to:

```text
Hello
```

### Important

Base64 is **encoding, not encryption**.

---

## Quoted-Printable

An email encoding method used primarily to represent text safely using ASCII characters.

Example:

```text
=3D
```

represents:

```text
=
```

It is commonly encountered when analyzing raw email messages.

---

# 7. MIME and Email Content

## `Content-Type`

Specifies the type of content contained in an email part.

Common values include:

```text
text/plain
text/html
multipart/alternative
multipart/mixed
multipart/related
application/pdf
application/octet-stream
image/*
```

---

## `multipart/alternative`

Allows an email to contain multiple representations of the same content.

Commonly:

```text
multipart/alternative
    |
    +-- text/plain
    |
    +-- text/html
```

---

## `multipart/mixed`

Often used when an email contains the message body and attachments.

Example:

```text
multipart/mixed
    |
    +-- text/plain
    |
    +-- attachment.pdf
```

---

## `multipart/related`

Used when different parts of an email are related to each other, commonly HTML content and embedded resources such as images.

---

# 8. Threat Intelligence

## IOC — Indicator of Compromise

An observable artifact that may indicate malicious or suspicious activity.

Examples:

```text
IP address
Domain
URL
Email address
File hash
Filename
```

Example:

```text
134.195.196.43
```

could be an IOC that should be investigated.

---

## IOA — Indicator of Attack

An indicator of attacker behavior or activity that may reveal an attack in progress.

Example:

```text
User opens a malicious document
        |
        v
Word launches PowerShell
        |
        v
PowerShell downloads a payload
```

The behavior is an IOA.

---

## IP Address

A numerical address used to identify a device or network interface on a network.

Example:

```text
134.195.196.43
```

During an email investigation, an IP address may be associated with:

* Sending infrastructure.
* Mail servers.
* Hosting providers.
* Command and control infrastructure.
* Malicious infrastructure.

---

## Domain

A human-readable name used to identify an internet resource.

Example:

```text
example.com
```

During email analysis, investigate:

```text
From domain
Return-Path domain
Reply-To domain
Link domain
Received hostname
DKIM domain
```

---

## DNS — Domain Name System

A system that translates domain names into IP addresses and provides other information about domains.

Example:

```text
example.com
     |
     | DNS
     v
192.0.2.10
```

DNS records commonly investigated include:

```text
A
AAAA
MX
TXT
CNAME
NS
```

---

## WHOIS

A service used to retrieve registration information associated with domains or IP address resources.

It can provide information such as:

* Registration dates.
* Registrar.
* Nameservers.
* Domain status.

---

## ASN — Autonomous System Number

A unique number identifying an autonomous system that manages a collection of IP networks under a common routing policy.

ASNs can help identify the network or organization associated with an IP address.

---

## Passive DNS

Historical DNS data used to investigate relationships between domains, IP addresses, and DNS records over time.

For example:

```text
evil-domain.com
      |
      +---- 1.2.3.4
      |
      +---- 5.6.7.8
```

Passive DNS can help identify historical infrastructure.

---

## Reputation

Information used to assess whether an IP address, domain, URL, or file is associated with malicious or suspicious activity.

Reputation should be treated as **supporting evidence**, not absolute proof.

---

## Hash

A fixed-length value generated from data using a hashing algorithm.

Common algorithms include:

```text
MD5
SHA-1
SHA-256
```

Hashes are commonly used to identify files and compare them against known malware samples.

Example:

```text
SHA256:
a3f5...
```


