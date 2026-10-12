# Investigation 02 — Service-Desk Notification Analysis

## 1. Objective

The objective of this investigation was to assess a routine-looking service-desk notification and determine whether the available evidence indicated suspicious behaviour.

This investigation also demonstrates the importance of avoiding false positives by considering context and multiple indicators together.

## 2. Data Source

- **Sample:** `02-service-desk-notification.eml`
- **Sample type:** Synthetic training email
- **Analysis method:** Static review of email fields, authentication results and message content

All domains and authentication results in this sample are illustrative. No real email system was tested.

## 3. Observations

### Sender and Reply Address

The displayed sender is `notifications@service-desk.example`, with the display name "Northstar IT Service Desk".

The Reply-To address is `tickets@northstar-support.example`, which uses a different domain.

A separate reply domain could be consistent with an organisation using a dedicated support or ticketing system. However, the relationship between the two domains cannot be verified from this sample.

### Subject and Message Content

The subject is "Update to service request #4821".

The body states that a support request has been updated and directs the recipient to use the organisation's usual service-desk portal. It does not supply a direct login link or attachment.

The message contains no obvious threat, urgent deadline or demand for credentials. These characteristics are less suspicious than the urgency and account-suspension language observed in Investigation 01.

### Authentication Results

The supplied Authentication-Results header reports:

- **SPF:** Pass
- **DKIM:** Pass
- **DMARC:** Pass

The visible From domain, SPF envelope-sender domain and DKIM signing domain all match `service-desk.example` in the sample.

These simulated results demonstrate successful authentication and alignment in the training scenario. They do not independently prove that the message's content or sender is trustworthy.

## 4. Assessment

**Training assessment: Low suspicion based on the available evidence; authenticity not verified.**

The message is consistent with a routine service-desk notification. The absence of a supplied link, attachment, urgent threat or direct request for credentials reduces the obvious signs of phishing.

The passing authentication results also reduce concern about certain forms of sender-domain spoofing. However, successful authentication does not rule out misuse of an account or an authenticated domain.

The different Reply-To domain remains an item that would require context before being accepted as legitimate.

## 5. Recommended SOC Actions

If this email were received in a real organisation:

1. Verify the ticket reference in the organisation's known service-desk portal.
2. Confirm that the sender and reply domain are recognised by the organisation.
3. Review email security logs and authentication results from the actual message if concerns remain.
4. Avoid classifying the email as malicious solely because its Reply-To domain differs from its sender domain.
5. Escalate if additional evidence contradicts the expected service-desk activity.

## 6. Limitations

- The email is synthetic and cannot be confirmed as a genuine communication.
- The `.example` domains are placeholders and do not establish real domain ownership.
- Authentication results are simulated.
- No organisational ticketing system, DNS data or real email headers were examined.
- The assessment is based solely on the supplied sample content.

## 7. Conclusion

This investigation practised assessing a routine-looking notification without automatically classifying it as phishing.

The message contains fewer obvious phishing indicators than the first training sample. However, the appropriate conclusion is that it has low suspicion based on the available evidence, rather than that it has been proven genuine.

The exercise demonstrates the importance of considering authentication, message context and independent verification when making email triage decisions.
