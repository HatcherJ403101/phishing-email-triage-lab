# Investigation 01 — Mailbox Warning Email

## 1. Initial Email Triage

**Sample type:** Synthetic phishing email  
**Purpose:** Practise identifying suspicious sender details, social-engineering indicators and email authentication failures.

### Observations

- The displayed sender claims to represent Microsoft 365 Security.
- The sender domain uses a lookalike character: `micros0ft-support.example`.
- The Reply-To address uses a different domain from the displayed sender.
- The message creates urgency by threatening mailbox suspension within two hours.
- The message encourages the recipient to follow a link to retain account access.
- The supplied authentication results show SPF, DKIM and DMARC failures.

### Initial Assessment

The combination of a lookalike sender domain, a different Reply-To domain, urgent account-suspension language and failed email authentication checks is consistent with common phishing characteristics.

This is a synthetic training sample, and the authentication results are simulated. These observations are used to practise investigation methodology, not to assert that a real email or sending system was tested.
