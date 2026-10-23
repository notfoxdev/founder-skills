# Deliverability and compliance basics

Read this before the first send of any sequence. The founder should verify current mailbox provider requirements and local law; rules change. Nothing here is legal advice.

## Domain and inbox setup

- **Authenticate:** publish SPF and DKIM records for the sending domain, and a DMARC record (start with `p=none` to monitor, tighten later). Google and Yahoo now require authentication from senders; bulk senders face stricter rules.
- **Domain choice:** sending from the main company domain is fine at founder-scale volumes. If planning higher volume, consider a separate, similar-looking domain or subdomain so mistakes do not damage the primary domain's reputation. Set it up weeks before use.
- **Domain age:** brand-new domains and inboxes have no reputation. Use the inbox normally for 2–4 weeks before outreach (real conversations, newsletters you subscribe to, replies).
- **Warm-up:** ramp volume gradually. Automated warm-up services exist; real low-volume, high-reply sending is the safer warm-up.
- **Signature:** real name, title, company, and a postal address for commercial email.

## Volume

Heuristics for founder-led outreach from a single inbox:

| Week | New contacts per day |
|---|---|
| 1 | 10–15 |
| 2 | 15–25 |
| 3+ | up to ~30–50, only if bounce and complaint rates stay low |

- Follow-ups count toward sending volume.
- Spread sends through the working day; do not send in a single burst.
- If you need more volume, the problem is usually targeting, not inbox count.

## Content

- Plain text. No HTML templates, images, or attachments.
- No open-tracking pixels or click-tracking links for early sends; they hurt deliverability and add little at low volume.
- Zero or one link per email. Use the full, real domain, not a link shortener.
- Avoid spam-trigger patterns: ALL CAPS, multiple exclamation marks, "free", "guarantee", "act now", money symbols in subject lines.
- Vary messages genuinely. Identical bodies at volume look automated.

## List hygiene

- Work addresses only, from sources that permit their use: the person's own public listing, company site, a contact who shared it, or a data provider whose terms and data sourcing the founder has checked.
- Verify addresses before sending. Keep hard bounces under ~2%; pause and clean the list if higher.
- Remove role addresses (info@, sales@) unless that is the intended recipient.
- Honour opt-outs immediately and permanently. Keep a suppression list across all tools.

## Monitoring thresholds

| Signal | Healthy | Act if |
|---|---|---|
| Hard bounce rate | under ~2% | above 2%: stop, verify list |
| Spam complaint rate | under ~0.1% | approaching 0.3%: stop; Google lists 0.3% as a limit for senders |
| Positive reply rate | depends on targeting | under ~5% after 50+ sends: fix targeting or ask |
| Inbox placement | replies arriving, no complaints | sudden reply drop: test placement with seed inboxes |

Google Postmaster Tools shows domain reputation and spam rate for mail sent to Gmail once volume is high enough.

## Platform rules

- **LinkedIn:** connection notes have a character limit (300) and free accounts may face monthly caps on personalised invites. Automation tools and scraping can violate LinkedIn's terms and risk account restriction. Send manually.
- **X:** many users restrict DMs. Do not mass-DM; it can trigger spam enforcement.
- **Scraping:** do not scrape personal emails or profile data in violation of a site's terms of service.

## Compliance basics

General orientation only. Rules differ by country and change; the founder should check the regimes that apply to their recipients.

### United States: CAN-SPAM (commercial email)
- Accurate "From", "To", and routing information.
- Subject line must not be deceptive.
- Identify the message as commercial where required.
- Include a valid physical postal address.
- Provide a clear way to opt out, and honour opt-outs within 10 business days.
- You remain responsible if a contractor sends on your behalf.

### EU / UK: GDPR plus ePrivacy rules (PECR in the UK)
- You need a lawful basis to process personal data such as a work email. For B2B outreach this is commonly legitimate interest: the message is relevant to the person's professional role, the data used is minimal, and you have weighed their interests. Document that assessment.
- Tell recipients who you are, where you got their data (if asked or on first contact, per local practice), and how to object.
- Honour objections and deletion requests promptly.
- E-marketing rules differ for individual subscribers versus corporate addresses, and by country. Some countries require prior consent even for B2B. Check the recipient's country.

### Canada: CASL
- Generally requires consent (express or implied) before sending commercial electronic messages. Implied consent may exist when an address is conspicuously published, relevant to the person's role, and not marked "no unsolicited messages". Requires sender identification and an unsubscribe mechanism.

### Everywhere
- Opt-out line in every message.
- No deceptive headers, fake replies ("Re:"), or false claims.
- Keep records of where each contact came from.
- When in doubt about a jurisdiction, flag `[NEED: check with counsel for <country>]`.
