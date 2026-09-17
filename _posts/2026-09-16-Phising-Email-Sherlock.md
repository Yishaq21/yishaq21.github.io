---
title: Phishing_Email | HTB-Sherlock
description: Investigate a email if contain phising.
date: 2026-09-15 10:00:0 +0000
categories: [Sherlock]
tags: [Sherlock, HacktheBox, EMAIL]
pin: false
mermaid: true
---

Today I am doing a sherlock of HTB about SOC, This is my first writeup about SOC so, There have some tips and how I resolve this Sherlock

First, we need download the files through `RDP (Remote Desktop Protocol).`
We used xfreerdp within this command `xfreerdp /v:<ipaddress> /u:letsdefend /p:''`

We need answer some question to investigate this email.

## Questions
------------


### 1. What is the return path of the email?

To answers this question, we need to inspect the full email headers 
![Headers](assets\img\Write-up\Phishing-Email\Return-path.png)
`Answer: bounce@rjttznyzjjzydnillquh.designclub.uk.com`

### 2. What is the domain name of the url in this mail?

We need investigate the hyperlink embedded in the email body 

`Answer: storage.googleapis.com`.

### 3. Is the domain mentioned in the previous question suspicious?

To answer this question, we need to review reputacion evidencie for the URL. We can use virustotal.com/gui/

`Answer: yes`

### 4. What is the sender IP address shown in the Received-SPF header?

To answer this question, we need to inspect the email headers again and focus on the SPF validation result.

![SPF](assets\img\Write-up\Phishing-Email\SFT-IP.png)
`Answer: 134.195.196.43`


### 5. Is this email a phishing email?

To answer this question we need combine another things like URL, reputation evidence instead of relying on a single indicator.
As we can see, the return path uses designclub.uk.com , which has no relationship to PayPal.

`Answer: Yes`
