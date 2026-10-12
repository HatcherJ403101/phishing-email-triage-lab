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
## 3. URL Indicator Analysis

### Observed Indicator

The email contains the defanged URL:

`hxxps://m365-secure-login[.]example/verify`

### Analysis

The hostname uses Microsoft 365-related wording, while the `/verify` path is consistent with the type of wording that might be used to encourage a recipient to review an account.

This supports the concern that the message is attempting to appear legitimate and direct the recipient towards an account-verification page. However, the URL's wording alone cannot establish the operator's identity or prove malicious intent.

The `.example` domain is a placeholder used for this synthetic exercise. No live destination was visited, and no reputation, DNS or hosting checks were performed.

### Safe Handling

The URL was kept defanged in the report to reduce the risk of accidental navigation. It was not opened, resolved or submitted to an external scanning service.

### Limitation

Because the destination is a reserved example domain, the actual site's content, ownership, reputation and behaviour cannot be assessed from this sample.
## 4. Risk Assessment and Recommended SOC Response

### Assessment

**Training assessment: High suspicion**

The sample contains several mutually reinforcing phishing indicators:

- A lookalike sender domain intended to resemble a recognised service.
- A Reply-To address using a different domain.
- Urgent language threatening mailbox suspension.
- A request to verify an account through a supplied link.
- Simulated SPF, DKIM and DMARC failures.

The combination warrants a cautious response in a real environment. The sample does not establish that a real account was targeted or compromised.

### Recommended SOC Actions

1. **Contain and preserve:** If received in a real organisation, quarantine the email where appropriate and preserve the original message, headers and relevant email-security logs.
2. **Identify exposure:** Determine whether the email was delivered to other users, opened, replied to or reported. Do not assume that a recipient clicked the link without supporting evidence.
3. **Investigate indicators:** Review the sender and Reply-To domains, authentication results and URL using approved organisational security tools. Do not visit the link directly.
4. **Search for related activity:** Look for matching messages, similar sender patterns and relevant email-security alerts across the organisation.
5. **Respond proportionately:** Remove confirmed malicious messages according to organisational procedures. Block indicators only after appropriate validation and consideration of legitimate business impact.
6. **Escalate if necessary:** If evidence indicates that a recipient submitted credentials, follow the organisation's incident-response process for account protection, credential reset, session revocation and relevant identity-log review.

### Severity Considerations

The synthetic email is assessed as highly suspicious based on its combined indicators. A real incident's severity would depend on additional factors, including the recipients affected, whether the message was delivered or acted upon, evidence of credential submission, and any subsequent account activity.

### Investigation Limitations

This exercise used fabricated email content and simulated authentication results. No real email infrastructure was tested, no live URL was visited, and no recipient impact was established. The assessment demonstrates an investigation method rather than a confirmed real-world incident.

## 5. Conclusion

This investigation demonstrated how sender details, social-engineering techniques, authentication results and URL characteristics can be combined to assess a potentially suspicious email.

The findings show why email triage should consider multiple indicators together rather than relying on any single signal. The investigation also reinforced safe handling practices, evidence-based conclusions and proportionate response recommendations.
