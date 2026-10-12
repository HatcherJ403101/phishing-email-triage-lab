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
## 2. Email Authentication and Domain Alignment

### Observed Results

The synthetic sample's Authentication-Results header reports:

- **SPF:** Fail
- **DKIM:** Fail
- **DMARC:** Fail

The domain shown in the SPF `smtp.mailfrom`, DKIM `header.d` and DMARC `header.from` fields is `micros0ft-support.example`.

### Analysis

The recorded domain values match, but domain alignment alone does not make an email authenticated.

DMARC requires at least one of SPF or DKIM to pass and align with the visible From domain. In this sample, both SPF and DKIM fail, so there is no passing aligned mechanism to satisfy DMARC.

These results strengthen the suspicious indicators already identified during triage. However, they are deliberately simulated values in a synthetic email and do not represent a live authentication test.

### Investigative Limitation

The sample contains no verified server-side authentication logs or real DNS records. The authentication results can therefore be used to practise interpreting SPF, DKIM and DMARC, but not to establish the behaviour of a real sender or mail system.
