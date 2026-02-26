# Twilio SMS A2P 10DLC Compliance — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add SMS compliance pages (Privacy Policy, Terms & Conditions, landing page) to Bibager Home, a homepage card linking to them, and a pre-filled A2P registration text file.

**Architecture:** Static HTML/CSS pages in an `sms/` subdirectory with their own stylesheet. No JavaScript, no build step. Registration info delivered as a plain text file in the project root.

**Tech Stack:** HTML5, CSS3, Google Fonts (Inter)

---

### Task 1: Create SMS shared stylesheet

**Files:**
- Create: `sms/sms-style.css`

**Step 1: Create the sms directory**

Run: `mkdir -p sms`

**Step 2: Write the SMS stylesheet**

Create `sms/sms-style.css` with these exact contents:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    background-color: #ffffff;
    color: #37352f;
    line-height: 1.8;
    -webkit-font-smoothing: antialiased;
}

.container {
    max-width: 720px;
    margin: 0 auto;
    padding: 60px 24px 40px;
}

header {
    margin-bottom: 40px;
    padding-bottom: 24px;
    border-bottom: 1px solid #e8e8e5;
}

.header-title {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 4px;
}

.header-title a {
    display: flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
    color: inherit;
}

.mascot {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    object-fit: cover;
    flex-shrink: 0;
}

header h1 {
    font-size: 24px;
    font-weight: 700;
    letter-spacing: -0.3px;
}

.subtitle {
    font-size: 14px;
    color: #787774;
}

nav {
    margin-bottom: 40px;
}

nav a {
    font-size: 14px;
    color: #2eaadc;
    text-decoration: none;
    margin-right: 20px;
}

nav a:hover {
    text-decoration: underline;
}

h2 {
    font-size: 20px;
    font-weight: 600;
    margin: 32px 0 12px;
    letter-spacing: -0.2px;
}

h2:first-of-type {
    margin-top: 0;
}

p {
    font-size: 15px;
    color: #37352f;
    margin-bottom: 12px;
}

ul {
    margin: 8px 0 16px 24px;
    font-size: 15px;
    color: #37352f;
}

ul li {
    margin-bottom: 6px;
}

a {
    color: #2eaadc;
}

.effective-date {
    font-size: 13px;
    color: #787774;
    margin-bottom: 24px;
}

.contact-email {
    font-weight: 500;
}

.page-links {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin: 24px 0;
}

.page-link {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 20px;
    border: 1px solid #e8e8e5;
    border-radius: 8px;
    text-decoration: none;
    color: inherit;
    transition: background-color 0.15s ease;
}

.page-link:hover {
    background-color: #fafafa;
}

.page-link-icon {
    font-size: 20px;
}

.page-link-text h3 {
    font-size: 15px;
    font-weight: 600;
    margin-bottom: 2px;
    color: #37352f;
}

.page-link-text p {
    font-size: 13px;
    color: #787774;
    margin-bottom: 0;
}

footer {
    margin-top: 60px;
    padding-top: 24px;
    border-top: 1px solid #e8e8e5;
}

footer p {
    font-size: 13px;
    color: #b4b4b0;
}

@media (max-width: 480px) {
    .container {
        padding: 40px 16px 32px;
    }

    header h1 {
        font-size: 20px;
    }

    h2 {
        font-size: 18px;
    }
}
```

**Step 3: Commit**

```bash
git add sms/sms-style.css
git commit -m "feat: add shared stylesheet for SMS compliance pages"
```

---

### Task 2: Create SMS landing page

**Files:**
- Create: `sms/index.html`

**Step 1: Write the landing page**

Create `sms/index.html` with these exact contents:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bibager SMS Notifications</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="sms-style.css">
</head>
<body>
    <div class="container">
        <header>
            <div class="header-title">
                <a href="/">
                    <img src="../mascot.png" alt="Bibager mascot" class="mascot">
                    <h1>Bibager SMS</h1>
                </a>
            </div>
            <p class="subtitle">Automated SMS notifications for Bibager projects.</p>
        </header>

        <h2>About This Service</h2>
        <p>Bibager uses SMS to deliver automated notifications from its projects. These include trade alerts from RZE, contact reminders from Personal CRM, and workflow notifications from N8N.</p>
        <p>Messages are sent only to the account owner and are strictly one-way automated alerts. No marketing messages are sent, and your phone number is never shared with third parties.</p>
        <p>Messages are delivered via <a href="https://www.twilio.com" target="_blank">Twilio</a>. Message and data rates may apply. You can opt out at any time by replying STOP to any message.</p>

        <h2>Legal</h2>
        <div class="page-links">
            <a href="privacy-policy.html" class="page-link">
                <span class="page-link-icon">&#128274;</span>
                <div class="page-link-text">
                    <h3>Privacy Policy</h3>
                    <p>How we collect, use, and protect your information.</p>
                </div>
            </a>
            <a href="terms-and-conditions.html" class="page-link">
                <span class="page-link-icon">&#128220;</span>
                <div class="page-link-text">
                    <h3>Terms &amp; Conditions</h3>
                    <p>Terms of use for the Bibager SMS notification service.</p>
                </div>
            </a>
        </div>

        <footer>
            <p>&copy; 2026 Bibager &middot; <a href="/">Home</a></p>
        </footer>
    </div>
</body>
</html>
```

**Step 2: Commit**

```bash
git add sms/index.html
git commit -m "feat: add SMS landing page"
```

---

### Task 3: Create Privacy Policy page

**Files:**
- Create: `sms/privacy-policy.html`

**Step 1: Write the Privacy Policy page**

Create `sms/privacy-policy.html` with these exact contents:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Privacy Policy - Bibager SMS</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="sms-style.css">
</head>
<body>
    <div class="container">
        <header>
            <div class="header-title">
                <a href="/">
                    <img src="../mascot.png" alt="Bibager mascot" class="mascot">
                    <h1>Bibager SMS</h1>
                </a>
            </div>
            <p class="subtitle">Privacy Policy</p>
        </header>

        <nav>
            <a href="index.html">&larr; Back to SMS Home</a>
        </nav>

        <p class="effective-date">Effective Date: February 26, 2026</p>

        <h2>Overview</h2>
        <p>Bibager ("we", "us", "our") operates an automated SMS notification service that delivers alerts from our projects. This Privacy Policy describes how we collect, use, and protect information related to our SMS messaging service.</p>

        <h2>Information We Collect</h2>
        <p>We collect and store the following information in connection with our SMS service:</p>
        <ul>
            <li><strong>Phone number</strong> — The mobile phone number configured to receive SMS notifications.</li>
            <li><strong>Message logs</strong> — Records of messages sent, including timestamps and delivery status, for troubleshooting and service reliability.</li>
        </ul>

        <h2>How We Use Your Information</h2>
        <p>Your information is used solely for the following purposes:</p>
        <ul>
            <li>Delivering automated SMS alerts from Bibager projects (trade alerts, reminders, workflow notifications).</li>
            <li>Monitoring message delivery to ensure service reliability.</li>
            <li>Troubleshooting delivery issues.</li>
        </ul>

        <h2>Third-Party Sharing</h2>
        <p>We do not sell, rent, or share your phone number or message data with any third parties for marketing or any other purpose. The only third party involved in message delivery is <a href="https://www.twilio.com/legal/privacy" target="_blank">Twilio</a>, our messaging service provider, which processes messages on our behalf.</p>

        <h2>Data Retention</h2>
        <p>Message logs are retained for up to 90 days for troubleshooting purposes and are then automatically deleted. Your phone number is stored as long as the SMS service is active and is removed upon request or service discontinuation.</p>

        <h2>Data Security</h2>
        <p>We take reasonable measures to protect your information, including using Twilio's secure messaging infrastructure and limiting access to stored data.</p>

        <h2>Your Rights</h2>
        <p>You may at any time:</p>
        <ul>
            <li>Request deletion of your phone number and message history.</li>
            <li>Opt out of all messages by replying <strong>STOP</strong> to any SMS.</li>
            <li>Contact us with questions about your data.</li>
        </ul>

        <h2>Changes to This Policy</h2>
        <p>We may update this Privacy Policy from time to time. Changes will be reflected on this page with an updated effective date.</p>

        <h2>Contact</h2>
        <p>If you have questions about this Privacy Policy, contact us at <span class="contact-email">privacy@bibager.com</span>.</p>

        <footer>
            <p>&copy; 2026 Bibager &middot; <a href="index.html">SMS Home</a> &middot; <a href="/">Bibager Home</a></p>
        </footer>
    </div>
</body>
</html>
```

**Step 2: Commit**

```bash
git add sms/privacy-policy.html
git commit -m "feat: add SMS privacy policy page"
```

---

### Task 4: Create Terms & Conditions page

**Files:**
- Create: `sms/terms-and-conditions.html`

**Step 1: Write the Terms & Conditions page**

Create `sms/terms-and-conditions.html` with these exact contents:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terms &amp; Conditions - Bibager SMS</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="sms-style.css">
</head>
<body>
    <div class="container">
        <header>
            <div class="header-title">
                <a href="/">
                    <img src="../mascot.png" alt="Bibager mascot" class="mascot">
                    <h1>Bibager SMS</h1>
                </a>
            </div>
            <p class="subtitle">Terms &amp; Conditions</p>
        </header>

        <nav>
            <a href="index.html">&larr; Back to SMS Home</a>
        </nav>

        <p class="effective-date">Effective Date: February 26, 2026</p>

        <h2>Service Description</h2>
        <p>Bibager ("we", "us", "our") provides an automated SMS notification service that delivers alerts from our projects, including but not limited to trade alerts, contact reminders, and workflow notifications. By receiving messages from this service, you agree to these Terms &amp; Conditions.</p>

        <h2>Message Frequency</h2>
        <p>Message frequency varies depending on which Bibager projects are active and their configurations. Messages are sent only when triggered by automated events (e.g., a trade signal, a scheduled reminder, or a workflow completion). You may receive multiple messages per day or none at all, depending on activity.</p>

        <h2>Opt-Out</h2>
        <p>You can opt out of receiving messages at any time by replying <strong>STOP</strong> to any message from Bibager. After opting out, you will receive a single confirmation message and no further messages will be sent. To resume messages, reply <strong>START</strong>.</p>

        <h2>Help</h2>
        <p>For help, reply <strong>HELP</strong> to any message or contact us at <span class="contact-email">support@bibager.com</span>.</p>

        <h2>Message and Data Rates</h2>
        <p>Message and data rates may apply. Bibager is not responsible for any charges incurred by your mobile carrier for receiving SMS messages.</p>

        <h2>Supported Carriers</h2>
        <p>Messages are sent via Twilio and are compatible with all major US mobile carriers. Carriers are not liable for delayed or undelivered messages.</p>

        <h2>Disclaimer of Warranties</h2>
        <p>The SMS notification service is provided "as is" without warranties of any kind, either express or implied. We do not guarantee that messages will be delivered on time or at all. SMS alerts related to financial data (such as trade alerts) are informational only and do not constitute financial advice.</p>

        <h2>Limitation of Liability</h2>
        <p>Bibager shall not be liable for any damages arising from the use of or inability to use the SMS notification service, including but not limited to missed alerts, delayed messages, or actions taken based on message content.</p>

        <h2>Privacy</h2>
        <p>Your use of this service is also governed by our <a href="privacy-policy.html">Privacy Policy</a>, which describes how we collect and use your information.</p>

        <h2>Changes to These Terms</h2>
        <p>We may update these Terms &amp; Conditions from time to time. Changes will be reflected on this page with an updated effective date. Continued receipt of messages constitutes acceptance of updated terms.</p>

        <h2>Contact</h2>
        <p>If you have questions about these Terms &amp; Conditions, contact us at <span class="contact-email">support@bibager.com</span>.</p>

        <footer>
            <p>&copy; 2026 Bibager &middot; <a href="index.html">SMS Home</a> &middot; <a href="/">Bibager Home</a></p>
        </footer>
    </div>
</body>
</html>
```

**Step 2: Commit**

```bash
git add sms/terms-and-conditions.html
git commit -m "feat: add SMS terms and conditions page"
```

---

### Task 5: Add Twilio SMS card to homepage

**Files:**
- Modify: `index.html:60-62` (insert new card after Personal CRM card, before closing `</div>`)

**Step 1: Add the new card**

In `index.html`, insert the following HTML after the Personal CRM `</a>` tag (after line 60) and before the closing `</div>` of `.project-grid` (line 62):

```html
                <a href="sms/" class="project-card" target="_blank">
                    <div class="card-icon">&#128172;</div>
                    <div class="card-content">
                        <h3>Twilio SMS</h3>
                        <p>SMS notification service for Bibager projects. Privacy policy and terms for A2P 10DLC compliance.</p>
                        <span class="card-link">bibager.com/sms &rarr;</span>
                    </div>
                </a>
```

**Step 2: Verify the page renders correctly**

Open `index.html` in a browser and confirm the new card appears as the 5th item.

**Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add Twilio SMS card to homepage"
```

---

### Task 6: Create A2P registration text file

**Files:**
- Create: `twilio-a2p-registration.txt`

**Step 1: Write the registration file**

Create `twilio-a2p-registration.txt` with these exact contents:

```text
=============================================================
TWILIO A2P 10DLC CAMPAIGN REGISTRATION — BIBAGER
=============================================================
Pre-filled answers for the Twilio US A2P 10DLC Registration form.
Copy and paste each field into the corresponding form field.

-------------------------------------------------------------
A2P Brand: My Starter Profile
-------------------------------------------------------------

-------------------------------------------------------------
Available A2P Campaign use cases: Sole Proprietor
-------------------------------------------------------------

-------------------------------------------------------------
Messaging Service: Create new Messaging Service
-------------------------------------------------------------

-------------------------------------------------------------
Campaign Description (paste this):
-------------------------------------------------------------
Bibager is a personal side-projects platform. This campaign
sends automated, one-way SMS notifications from Bibager
projects to the sole proprietor (account owner) only. Alerts
include stock trade signals from the RZE trading platform,
contact reminders from Personal CRM, and workflow completion
notifications from N8N automation. No marketing messages are
sent. Only one recipient receives messages.

-------------------------------------------------------------
Sample Message #1 (paste this):
-------------------------------------------------------------
[RZE] Trade Alert: AAPL buy signal detected. Current price
$187.42, target $195.00, stop $182.50. Confidence: High.

-------------------------------------------------------------
Sample Message #2 (paste this):
-------------------------------------------------------------
[RZE] SPY Zone Update: SPY has entered the caution zone at
$542.18. Consider tightening stops on open positions.

-------------------------------------------------------------
Sample Message #3 (paste this):
-------------------------------------------------------------
[CRM] Reminder: You haven't contacted Sarah Chen in 30 days.
Last interaction: Jan 27 coffee meeting.

-------------------------------------------------------------
Sample Message #4 (paste this):
-------------------------------------------------------------
[N8N] Workflow complete: "Daily Stock Screener" finished
successfully. 3 new signals found. Check RZE dashboard.

-------------------------------------------------------------
Sample Message #5 (paste this):
-------------------------------------------------------------
[N8N] Workflow alert: "Database Backup" failed at 3:15 AM.
Error: Connection timeout. Please check server status.

-------------------------------------------------------------
Message Contents (checkboxes):
-------------------------------------------------------------
[ ] Messages will include embedded links — DO NOT CHECK
[ ] Messages will include phone numbers — DO NOT CHECK
[ ] Messages include content related to direct lending
    or other loan arrangement — DO NOT CHECK
[ ] Messages include age-gated content as defined by
    Carrier and CTIA guidelines — DO NOT CHECK

-------------------------------------------------------------
How do end-users consent to receive messages? (paste this):
-------------------------------------------------------------
The sole proprietor (account owner) consents to receive
messages by personally configuring their own phone number
in the Bibager platform settings. Only the account owner
can add their phone number, and only one phone number is
supported. The account owner can remove their number at
any time through the platform settings or by replying STOP
to any message. No other individuals receive messages from
this campaign.

-------------------------------------------------------------
Privacy Policy URL (paste this):
-------------------------------------------------------------
https://bibager.com/sms/privacy-policy.html

-------------------------------------------------------------
Terms and Conditions URL (paste this):
-------------------------------------------------------------
https://bibager.com/sms/terms-and-conditions.html

-------------------------------------------------------------
Opt-in Keywords (paste this):
-------------------------------------------------------------
START, SUBSCRIBE

-------------------------------------------------------------
Opt-in Message (paste this):
-------------------------------------------------------------
Bibager: You are now opted in to receive automated
notifications from Bibager projects. Msg frequency varies.
Msg & data rates may apply. Reply HELP for help, STOP to
opt out.

=============================================================
NOTES
=============================================================
- Deploy the Privacy Policy and Terms pages BEFORE submitting
  this registration. Twilio reviewers will check the URLs.
- The campaign type is "Sole Proprietor" since messages go
  only to the account owner.
- Keep messages under 160 characters when possible to avoid
  multi-segment charges.
=============================================================
```

**Step 2: Commit**

```bash
git add twilio-a2p-registration.txt
git commit -m "feat: add pre-filled A2P 10DLC registration info"
```

---

### Task 7: Update CLAUDE.md and final commit

**Files:**
- Modify: `CLAUDE.md`

**Step 1: Update CLAUDE.md**

Update the file structure section to include the new `sms/` directory and `twilio-a2p-registration.txt`. Update the Current Task to reflect completion. Add a session log entry.

**Step 2: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: update CLAUDE.md with SMS compliance pages"
```
