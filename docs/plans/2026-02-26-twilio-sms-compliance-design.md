# Twilio SMS A2P 10DLC Compliance — Design

**Date**: 2026-02-26
**Status**: Approved

## Context

Bibager needs a Twilio phone number to send automated SMS alerts from its projects (RZE, Personal CRM, N8N, Fillory). Twilio requires A2P 10DLC registration, which needs publicly accessible Privacy Policy and Terms & Conditions pages, plus campaign registration details.

## Requirements

- **Recipients**: Sole proprietor only (one phone number)
- **Message type**: One-way automated alerts (no replies expected)
- **Sources**: RZE trade alerts, CRM reminders, N8N workflow notifications
- **Hosting**: Subpages at bibager.com/sms/
- **Page style**: Basic but branded (Bibager branding, clean readable layout)

## Deliverables

### 1. New Files

```
sms/
├── index.html                 # Landing page describing the SMS service
├── privacy-policy.html        # Privacy Policy (URL for Twilio form)
├── terms-and-conditions.html  # Terms & Conditions (URL for Twilio form)
└── sms-style.css              # Shared styles — branded, text-focused

twilio-a2p-registration.txt    # Pre-filled A2P campaign info for Twilio form
```

### 2. Homepage Card

Added to `index.html` after existing four cards:
- **Title**: Twilio SMS
- **Icon**: Message/phone emoji
- **Description**: SMS notification service for Bibager projects. Privacy policy and terms for A2P 10DLC compliance.
- **Link**: bibager.com/sms/ -> sms/index.html

### 3. SMS Landing Page (sms/index.html)

- Bibager header with mascot
- Brief description of the SMS service (automated alerts, sole recipient)
- Links to Privacy Policy and Terms & Conditions
- Branded footer

### 4. Privacy Policy (sms/privacy-policy.html)

Covers:
- What data is collected (phone number, message logs)
- How data is used (one-way automated alerts)
- No third-party data sharing
- Data retention and deletion policy
- Twilio as messaging provider
- Contact information

### 5. Terms & Conditions (sms/terms-and-conditions.html)

Covers:
- Service description (automated SMS alerts from Bibager projects)
- Message frequency (varies by project)
- Opt-out instructions (reply STOP)
- Message and data rates disclaimer
- No warranties / liability limits
- CTIA-compliant language
- Contact information

### 6. Registration File (twilio-a2p-registration.txt)

Pre-filled answers for Twilio A2P 10DLC form:
- Campaign Description
- 5 Sample Messages (one per project/scenario)
- End-user consent description
- Privacy Policy URL
- Terms & Conditions URL
- Opt-in Keywords
- Opt-in Message
- Message Contents checkbox guidance

## Design Decisions

- **Separate CSS file** for SMS pages rather than reusing main style.css — keeps concerns separated and avoids bloating the homepage styles
- **Landing page** gives the homepage card a meaningful destination and provides context for Twilio reviewers who may visit the URL
- **Text file for registration** rather than .doc — simpler, no dependencies, easy to copy-paste into the Twilio form
- **Sole proprietor framing** throughout all legal text — accurate and simplifies compliance language
