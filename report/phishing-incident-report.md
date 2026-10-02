# Phishing Email Investigation Report

## 1. Incident Summary

**Incident Type:** Suspected Phishing Email  
**Severity:** High  
**Investigation Type:** Simulated SOC Investigation  
**Status:** Investigated  
**Analyst:** Apeksha R. Rai

A simulated phishing email was investigated to identify indicators of compromise (IOCs), analyse email authentication results, assess severity, map observed behaviour to MITRE ATT&CK, and develop an appropriate SOC response.

The email impersonates Microsoft 365 security personnel and attempts to create urgency by claiming that the recipient's account will be suspended unless they complete a security verification process.

---

## 2. Email Details

**From:**
security@micros0ft-security.example

**To:**
employee@company.example

**Subject:**
URGENT: Your Microsoft 365 account will be suspended

**Date:**
Thu, 24 Sep 2026 09:17:22 +0000

**Reply-To:**
security-help@micros0ft-security.example

**Return-Path:**
bounce@micros0ft-security.example

---

## 3. Investigation Objectives

The investigation aimed to:

1. Analyse the email headers.
2. Identify suspicious indicators.
3. Extract IOCs.
4. Analyse the embedded URL without visiting it.
5. Review SPF, DKIM, and DMARC results.
6. Assess the incident severity.
7. Map observed behaviour to MITRE ATT&CK.
8. Develop a SOC response and containment plan.
9. Document limitations of the simulation.

---

## 4. Header Analysis

### Sender

The sender claims to represent Microsoft 365 Security but uses:

`micros0ft-security.example`

The domain uses the number `0` in place of the letter `o`, creating a lookalike domain.

### Reply-To

The Reply-To address also uses the suspicious domain:

`security-help@micros0ft-security.example`

This increases suspicion because replies would be directed to the same lookalike domain.

### Return-Path

The Return-Path is:

`bounce@micros0ft-security.example`

This is another indicator connecting the message to the suspicious domain.

### Received Header

The simulated message contains:

`mail.micros0ft-security.example [198.51.100.24]`

The IP address `198.51.100.24` is a documentation/example IP used for this simulation.

---

## 5. Email Authentication Results

| Authentication Method | Result |
|---|---|
| SPF | FAIL |
| DKIM | FAIL |
| DMARC | FAIL |

All three authentication checks fail in the simulated email.

These results provide additional evidence that the message should not be trusted as an authenticated Microsoft 365 security message.

---

## 6. URL Analysis

The email contains the following URL:

`https://login-microsoft-security.example/verify`

The URL was analysed as text only.

### URL Components

**Protocol:**

`https://`

HTTPS provides encrypted communication but does not prove that a website is legitimate.

**Domain:**

`login-microsoft-security.example`

The domain contains terms designed to appear associated with Microsoft security services.

**Path:**

`/verify`

The path suggests that the user is being directed to an account verification page.

### Assessment

The URL is considered suspicious because it is presented as an account verification link and is associated with a lookalike phishing domain.

The URL was not opened or visited during this investigation.

---

## 7. Phishing Indicators

The following indicators were identified:

- Lookalike sender domain.
- Number substitution in the domain (`0` instead of `o`).
- Urgent account-suspension language.
- Threat of losing account access.
- Suspicious account-verification URL.
- SPF failure.
- DKIM failure.
- DMARC failure.
- Sender, Reply-To, and Return-Path use the same suspicious domain.

The combination of these indicators increases confidence that the message is a phishing attempt within the simulated environment.

---

## 8. Indicators of Compromise

| Type | Indicator | Description |
|---|---|---|
| Email | security@micros0ft-security.example | Suspicious sender |
| Domain | micros0ft-security.example | Lookalike domain |
| URL | https://login-microsoft-security.example/verify | Suspicious verification URL |
| IP | 198.51.100.24 | Documentation/example IP |

The IP address is included because it appears in the simulated email header. It is not classified as a real malicious IP.

---

## 9. Threat Intelligence Assessment

The indicators in this investigation use `.example` domains and a documentation/example IP.

Therefore, this project does not claim that these indicators have real-world malicious reputation.

In a real SOC investigation, analysts could investigate indicators using:

- Domain reputation services.
- IP reputation services.
- WHOIS and domain registration information.
- Passive DNS.
- Internal security logs.
- Email security platforms.
- Phishing and malware intelligence sources.

Any external intelligence result should be recorded with its source, timestamp, result, and confidence level.

---

## 10. MITRE ATT&CK Mapping

### T1566 — Phishing

The simulated attacker behaviour involves sending a deceptive email designed to influence the recipient.

### T1566.002 — Phishing: Spearphishing Link

The email contains a suspicious link intended to direct the recipient to an account verification page.

The mapping represents the simulated behaviour and does not establish that a real attacker or campaign exists.

---

## 11. Severity Assessment

**Severity: HIGH**

The simulated incident was assessed as high severity because multiple phishing indicators are present:

- Lookalike sender domain.
- Urgent account-suspension language.
- Suspicious verification URL.
- SPF failure.
- DKIM failure.
- DMARC failure.

### Limitations

There is no evidence in this simulation that:

- The recipient clicked the URL.
- Credentials were entered.
- Malware was downloaded.
- An account was compromised.
- Data was accessed or exfiltrated.

Therefore, the severity assessment is based on the characteristics of the phishing message rather than confirmed compromise.

---

## 12. SOC Response

Recommended immediate actions include:

1. Do not click the suspicious URL.
2. Preserve the original email and headers.
3. Quarantine or remove the message.
4. Identify other recipients.
5. Search email logs for related messages.
6. Search for the identified indicators.
7. Determine whether any recipient interacted with the message.
8. If credentials were submitted, begin the organisation's credential-compromise response process.
9. Review authentication activity for affected users.
10. Escalate if evidence of compromise is identified.

---

## 13. Containment and Remediation

Potential containment actions include:

- Quarantining matching emails.
- Blocking or monitoring suspicious indicators through approved controls.
- Identifying additional recipients.
- Reviewing authentication and endpoint logs.
- Removing remaining copies of the phishing message.
- Updating detection rules where appropriate.

If credentials were compromised, additional actions could include password reset, session revocation, authentication review, and investigation of suspicious account activity.

---

## 14. Recovery

Recovery activities could include:

- Confirming affected accounts are secure.
- Monitoring authentication activity.
- Confirming phishing messages have been removed.
- Continuing monitoring for related indicators.
- Closing the incident after required investigation and remediation are complete.

---

## 15. Lessons Learned

The investigation demonstrates several useful phishing detection indicators:

- Lookalike domains.
- Urgent or threatening language.
- Suspicious verification URLs.
- SPF/DKIM/DMARC failures.
- Mismatched or suspicious sender information.

Potential detection improvements include:

- Lookalike-domain detection.
- URL reputation monitoring.
- Email authentication monitoring.
- Phishing-reporting procedures.
- User security awareness training.
- SIEM correlation between email and authentication events.

---

## 16. Simulation Limitations

This project is a controlled cybersecurity simulation.

No real phishing email was sent.

No suspicious URL was opened.

No credentials were entered.

No real user account was accessed.

No real domain or IP address was blocked.

The indicators were intentionally created for educational purposes.

---

## 17. Analyst Conclusion

The simulated email contains multiple characteristics consistent with a phishing attempt.

The primary indicators are the lookalike sender domain, urgent account-suspension language, suspicious verification URL, and failed SPF, DKIM, and DMARC authentication checks.

The appropriate SOC workflow would be to preserve evidence, contain the message, identify potentially affected users, determine whether anyone interacted with the message, and investigate for credential compromise or account takeover if user interaction occurred.

This investigation demonstrates a basic SOC phishing-triage workflow from initial alert analysis through IOC extraction, severity assessment, MITRE mapping, and response planning.
