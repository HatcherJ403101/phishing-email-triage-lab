# Investigation 03 — Document-Sharing Email Analysis

## 1. Objective

The objective of this investigation was to assess a document-sharing notification that passes the supplied SPF, DKIM and DMARC checks but contains other potentially suspicious indicators.

The investigation demonstrates why email authentication results must be considered alongside sender identity, message content and destination URLs.

## 2. Data Source

- **Sample:** `03-document-sharing-notification.eml`
- **Sample type:** Synthetic training email
- **Analysis method:** Static review of email fields, authentication results and message content

The domains, URL and authentication results are illustrative. No real email system or website was tested.

## 3. Findings

### Finding 1 — Lookalike sender domain

The displayed sender claims to represent Microsoft SharePoint:

`sharepoint-notice@micros0ft-docs.example`

The domain contains a zero in place of the letter "o" in "Microsoft". This resembles a lookalike-domain technique intended to make an address appear associated with a trusted brand.

The displayed sender name does not prove the identity of the sender, and the `.example` domain is a placeholder.

### Finding 2 — Email authentication passes

The supplied Authentication-Results header reports:

- **SPF:** Pass
- **DKIM:** Pass
- **DMARC:** Pass

In this synthetic sample, the authentication mechanisms pass for the `micros0ft-docs.example` domain.

These results do not establish that the domain belongs to Microsoft. Authentication can indicate that a message was authorised by the domain it represents without proving that the domain itself is legitimate.

Consequently, passing SPF, DKIM and DMARC does not rule out phishing or impersonation using a lookalike domain.

### Finding 3 — Document-sharing lure

The subject is:

"A document has been shared with you"

The email refers to a document titled "Updated Staff Information" and asks the recipient to review it today.

This may exploit a recipient's curiosity about workplace changes. The request to act today creates some pressure, although it is less explicit than the two-hour mailbox-suspension threat observed in Investigation 01.

The combination of a document-sharing pretext and a lookalike sender domain warrants further scrutiny.

### Finding 4 — Suspicious URL

The message contains the defanged URL:

`hxxps://sharepoint-document-review[.]example/open/003`

The hostname uses wording associated with document sharing and SharePoint. However, the hostname is a placeholder and does not establish that the destination is a genuine Microsoft service.

The URL was not visited or resolved. Its ownership, reputation, redirects and actual behaviour therefore remain unknown.

A real destination could attempt to impersonate a login page or collect sensitive information, but this sample does not demonstrate that such activity occurred.

## 4. Security Assessment

**Training assessment: Suspicious — further verification warranted.**

The principal concerns are:

- A lookalike domain used with a trusted brand's displayed name.
- A document-sharing pretext that may encourage the recipient to follow a link.
- A destination hostname that imitates a document-sharing service.
- Passing email authentication results that authenticate the supplied domain but do not establish that the domain belongs to the claimed brand.

The authentication results do not remove the other concerns. Conversely, the available evidence does not establish that the link is operational, that credentials would be collected, or that an account has been compromised.

## 5. Recommended SOC Actions

If a comparable email appeared in a real organisation:

1. Preserve the original email and its full headers.
2. Verify the sender and document-sharing request through a trusted organisational channel.
3. Examine the actual domain using approved security tools, including relevant reputation and redirect information, without browsing to the suspicious destination directly.
4. Search email-security logs for related messages and determine whether other users received them.
5. If evidence indicates that credentials were submitted or an account was accessed, follow incident-response procedures for account protection and identity-log review.
6. Apply blocking or quarantine actions based on the evidence and organisational procedures.

## 6. Limitations

- The email is a synthetic training sample.
- The SPF, DKIM and DMARC results are simulated.
- The `.example` domain does not establish real domain ownership or reputation.
- The destination was not visited, resolved or examined in a sandbox.
- No credential theft, session-token theft or account compromise was observed.
- The assessment is based on the supplied email content rather than live telemetry.

## 7. Conclusion

This investigation demonstrated that successful email authentication does not guarantee that an email is trustworthy.

The sender domain, document-sharing pretext and URL wording provide reasons to investigate further despite the passing authentication results. However, the available evidence does not establish the behaviour of the destination or prove that data was stolen.

The exercise reinforced the importance of examining domain identity and message context, validating suspicious requests through trusted channels, and distinguishing a plausible attack scenario from an observed security incident.
