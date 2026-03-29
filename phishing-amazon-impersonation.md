# SOC Investigation - Phishing Campaign (True Positive)

**Platform:** TryHackMe - SOC Simulator  
**Date:** 29/03/2026  
**Severity:** High  
**Outcome:** True Positive - Escalated

---

## Summary
A high severity alert was triggered when a user clicked 
a confirmed malicious URL contained within a phishing 
email impersonating Amazon. The firewall successfully 
blocked the outbound connection however the incident 
was escalated due to my belief the user needs dedicated training

---

## Investigation Process
The first port of call was analyse the firewall log that was flagged
and I saw a bitly link,which suggests the sender is trying to hide
the actual URL. I copied the bitly link and pasted it into Splunk,
which revealed the attempt to access the website, by the user, and
the initial email. I noticed that the email came from
"urgents@amazon.biz", which immediately suggested it was a phising
attempt, as any correspondance from Amazon would come from "amazon.com".
After noticing this, I copy and pasted the URL into the resident URL
analysis tool and it came back as a malicious URL.

---

## Evidence

### Initial Firewall Alert
![Firewall Log](images/Firewall%20log.png)

### Splunk Investigation Log
![Splunk Log](images/splunk%20analysis.png)

### URL Threat Intelligence Analysis
![URL Analysis](images/URL%20analysis.png)

---

## Determination
True Positive — escalated for the following reasons:
I believe that the user 'H.Harris' needs dedicated
training in the dangers of phishing, what to look out
for and educated on the high percentage of attacks that
stem from user error.

---

## Key Lessons
- URL shorteners like bit.ly are commonly used in 
  phishing to disguise malicious destinations
- Firewall blocks do not guarantee no compromise 
  occurred - endpoint investigation still required
- Human error accounts for the majority of successful 
  breaches - user awareness training is a critical 
  remediation step
- Patterns across multiple alerts involving the same 
  user should always be flagged even if individual 
  incidents appear contained
