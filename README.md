# Phishing Email Triage Lab

## Project Overview

This project demonstrates foundational Security Operations Centre (SOC) email-triage skills through three synthetic email investigations.

The investigations examine sender identity, social-engineering techniques, email authentication results and suspicious URLs. Each report documents the available evidence, provides a proportionate assessment and recommends appropriate defensive actions.

## Objectives

- Identify suspicious sender and Reply-To addresses.
- Recognise social-engineering techniques such as urgency, impersonation and document-sharing lures.
- Understand SPF, DKIM, DMARC and domain alignment.
- Explain why passing email authentication does not guarantee that a message is trustworthy.
- Record suspicious URLs safely without visiting them.
- Distinguish suspicious indicators from confirmed malicious activity.
- Recommend appropriate SOC investigation and response actions.
- Avoid false positives by assessing multiple indicators in context.

## Investigations

### Investigation 01 — Mailbox Warning Email

**Assessment:** High suspicion in the synthetic training scenario.

Examined a simulated mailbox-suspension email containing a lookalike sender domain, a different Reply-To domain, urgent language, a suspicious URL and simulated SPF, DKIM and DMARC failures.

**Key learning:** Multiple independent indicators can reinforce suspicion, but the findings must be interpreted in context.

**Report:** [Read Investigation 01](investigations/01-mailbox-warning-analysis.md)  
**Sample:** [View the synthetic email](investigations/samples/01-synthetic-mailbox-warning.eml)

### Investigation 02 — Service-Desk Notification

**Assessment:** Low suspicion based on the available evidence; authenticity not verified.

Examined a routine-looking service-desk notification with passing authentication results, a different Reply-To domain, no supplied link and no obvious urgency or demand for credentials.

**Key learning:** A different Reply-To domain does not automatically indicate phishing, and analysts should avoid unsupported conclusions.

**Report:** [Read Investigation 02](investigations/02-service-desk-notification-analysis.md)  
**Sample:** [View the synthetic email](investigations/samples/02-service-desk-notification.eml)

### Investigation 03 — Document-Sharing Email

**Assessment:** Suspicious; further verification warranted.

Examined a document-sharing email with passing SPF, DKIM and DMARC results but a lookalike sender domain and a document-sharing URL designed to appear associated with SharePoint.

**Key learning:** Authentication can validate a message against its sending domain without proving that the domain belongs to the brand it claims to represent.

**Report:** [Read Investigation 03](investigations/03-document-sharing-analysis.md)  
**Sample:** [View the synthetic email](investigations/samples/03-document-sharing-notification.eml)

## Tools and Techniques

- Static email analysis
- Sender and Reply-To inspection
- SPF, DKIM and DMARC interpretation
- Domain-alignment analysis
- Lookalike-domain recognition
- Suspicious URL analysis and safe handling
- Phishing triage and risk assessment
- Incident-response recommendations
- Technical documentation

## Safety and Scope

All three emails are synthetic training samples. The domains and URLs use reserved example names, and authentication results are simulated.

No live phishing links were visited, no attachments were executed, and no real mail systems were tested.

The investigation outcomes demonstrate analysis techniques rather than confirmed real-world incidents.

## Skills Demonstrated

- Analytical thinking and attention to detail
- Evidence-based security assessment
- Recognition of phishing and impersonation techniques
- Understanding of email authentication
- False-positive reduction
- Clear technical reporting
- Proportionate incident-response recommendations
