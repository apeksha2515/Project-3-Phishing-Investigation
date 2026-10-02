# Phishing Email Investigation & SOC Triage

## Project Overview

This project demonstrates a practical Security Operations Centre (SOC) workflow for investigating a simulated phishing email.

The investigation covers email header analysis, IOC extraction, URL analysis, email authentication checks, threat intelligence considerations, MITRE ATT&CK mapping, severity assessment, and incident response planning.

The project was completed as a controlled cybersecurity simulation using non-real phishing indicators.

---

## Objectives

- Investigate a suspicious phishing email.
- Analyse email headers.
- Identify indicators of compromise (IOCs).
- Analyse a suspicious URL safely without visiting it.
- Interpret SPF, DKIM, and DMARC results.
- Assess incident severity.
- Map observed behaviour to MITRE ATT&CK.
- Develop a SOC containment and response plan.
- Produce a professional incident investigation report.

---

## Investigation Scenario

The simulated email impersonates Microsoft 365 security personnel and claims that the recipient's account will be suspended unless they complete a security verification process.

The message contains:

- A lookalike sender domain.
- Urgent account-suspension language.
- A suspicious verification URL.
- SPF failure.
- DKIM failure.
- DMARC failure.

---

## Key Findings

| Finding | Observation |
|---|---|
| Sender | Lookalike micros0ft-security.example domain |
| URL | Suspicious account verification URL |
| SPF | FAIL |
| DKIM | FAIL |
| DMARC | FAIL |
| Source IP | 198.51.100.24 documentation/example IP |
| Severity | High within the simulation |

---

## Indicators of Compromise

| Type | Indicator | Purpose |
|---|---|---|
| Email | security@micros0ft-security.example | Suspicious sender |
| Domain | micros0ft-security.example | Lookalike domain |
| URL | https://login-microsoft-security.example/verify | Suspicious verification URL |
| IP | 198.51.100.24 | Documentation/example IP |

The .example domains and documentation IP are intentionally used for this educational simulation.

---

## MITRE ATT&CK Mapping

- **T1566 — Phishing**
- **T1566.002 — Phishing: Spearphishing Link**

The mapping represents simulated behaviour and does not establish the existence of a real attacker or campaign.

---

## SOC Response

The simulated SOC response includes:

1. Preserve the original email and headers.
2. Do not interact with the suspicious URL.
3. Quarantine or remove the message.
4. Identify other recipients.
5. Search email security logs for related messages.
6. Determine whether any recipient interacted with the message.
7. Investigate possible credential compromise if interaction occurred.
8. Escalate evidence of compromise according to organisational procedures.

---

## Skills Demonstrated

- Phishing email analysis
- Email header analysis
- IOC extraction
- URL analysis
- SPF, DKIM and DMARC interpretation
- Threat intelligence concepts
- MITRE ATT&CK mapping
- Incident severity assessment
- SOC incident response
- Evidence preservation
- Security documentation

---

## Safety and Ethics

This project is a controlled cybersecurity simulation.

No real phishing email was sent.

No suspicious URL was opened.

No credentials were collected.

No real user account was accessed.

No real domain or IP address was blocked.

The indicators were created specifically for educational purposes.

---

## Author

**Apeksha R. Rai**

MSc Cyber Security  
Aspiring SOC Analyst
