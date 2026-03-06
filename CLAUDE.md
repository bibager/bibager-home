# Bibager Home

## Overview
Static homepage for **bibager.com** — a hub linking to various side projects and experiments.

## Tech Stack
- Plain HTML/CSS (no framework, no build step)
- Google Fonts: Inter (400, 500, 600, 700)
- Hosted at bibager.com

## File Structure
```
/
├── index.html                    # Main homepage (5 project cards)
├── style.css                     # Homepage styles (Notion-inspired)
├── mascot.png                    # Bibager mascot avatar
├── README.md                     # Repo description
├── CLAUDE.md                     # This file — project context for Claude
├── twilio-a2p-registration.txt   # Pre-filled A2P 10DLC campaign info for Twilio form
├── sms/
│   ├── index.html                # SMS landing page
│   ├── privacy-policy.html       # Privacy Policy (URL for Twilio)
│   ├── terms-and-conditions.html # Terms & Conditions (URL for Twilio)
│   └── sms-style.css             # Shared styles for SMS pages
├── docs/
│   └── plans/                    # Design docs and implementation plans
└── .claude/
    └── settings.json             # Claude Code project settings
```

## Design Conventions
- **Notion-inspired aesthetic**: clean white background (#ffffff), muted gray text (#787774), subtle borders (#e8e8e5)
- **Accent color**: #2eaadc (links)
- **Card layout**: vertical stack of project cards with emoji icons, description, and subdomain link
- **Responsive**: mobile breakpoint at 480px
- **Typography**: Inter font, h1 at 40px/700, body at 14-16px
- **Max width**: 720px container, centered
- **SMS pages**: separate `sms-style.css` — same branding but simpler text-focused layout

## Current Projects Listed
1. **N8N** — n8n.bibager.com (workflow automation)
2. **Fillory** — fillory.bibager.com (browser RPG)
3. **RZE** — rze.bibager.com (AI stock trading)
4. **Personal CRM** — crm.bibager.com (AI contact manager)
5. **Twilio SMS** — bibager.com/sms (SMS compliance pages, local link — no `target="_blank"`)

## Architecture Decisions
- No JavaScript needed — pure static HTML/CSS
- Each project card is an `<a>` tag wrapping the card for full-card clickability
- External subdomain cards open in new tabs (`target="_blank"`), local cards do not
- CSS has a `.coming-soon` class (dashed border, reduced opacity) for future projects not yet live
- SMS pages have their own `sms-style.css` to keep concerns separated from homepage styles
- SMS pages use `../mascot.png` relative path for the mascot image

## Current Task
None — SMS landing page redesigned for Twilio toll-free resubmission. Awaiting next task.

## Next Steps
- Deploy updated SMS pages to bibager.com
- Resubmit toll-free verification in Twilio console (within 7 days for prioritized review)
- Commit changes to git

## Workflow Conventions
- **CLAUDE.md is updated immediately** when we make an important decision, complete a meaningful step, or establish a convention — not deferred to end of session
- **Current Task** section always reflects what we're actively working on
- **Next Steps** section always reflects what comes after the current task
- This ensures the file is always current enough to resume from if the session ends unexpectedly

## Session Log

### 2026-02-26 — Session Setup
- Created CLAUDE.md and .claude/settings.json for session continuity
- Established convention: update CLAUDE.md immediately on significant changes, not just at session end

### 2026-02-26 — Twilio SMS A2P 10DLC Compliance
- Designed and built SMS compliance pages: landing page, privacy policy, terms & conditions
- Created shared `sms/sms-style.css` with branded text-focused layout
- Added "Twilio SMS" card to homepage (5th card, links to sms/ locally)
- Created `twilio-a2p-registration.txt` with all pre-filled campaign info (description, 5 sample messages, consent, URLs, opt-in keywords/message, checkbox guidance)
- Design docs saved to `docs/plans/`

### 2026-03-05 — Toll-Free Verification Resubmission (Error 30513)
- Rejection reason: "Opt-in language is unclear and not sufficient" (Error 30513)
- Root cause: No visible opt-in form on SMS page; consent was descriptive text, not an actionable mechanism
- Redesigned `sms/index.html` with a prominent opt-in form featuring:
  - Phone number input field
  - Unchecked checkbox with explicit TCPA consent language ("I agree to receive automated SMS text messages from Bibager...")
  - Consent standalone and visually separated (not buried in ToS/Privacy)
  - All CTIA required disclosures (frequency, rates, STOP, HELP, not condition of purchase)
  - Branded with company name in consent text
  - Links to Privacy Policy and Terms & Conditions in disclosure box
- Added form styles to `sms/sms-style.css`
- Updated `twilio-a2p-registration.txt` with resubmission #2 notes
