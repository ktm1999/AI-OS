# AIS-OS Intake

This is the source-of-truth file for your AIOS. Fill it in by typing, voice-pasting (Wispr Flow / OS dictation), or running `/onboard` for a guided conversation. Whichever mode, this file is what `/onboard` reads to scaffold your Day-1 setup.

**Hard cap: 7 questions.** Each answerable in under 60 seconds. Don't overthink — you can edit and re-run `/onboard` any time.

---

## Q1 — Who are you, what do you sell, who do you sell it to?

Identity, offer, ICP. One paragraph each is fine.

```
Identity: Paris-based solo operator. Full-time Agentic AI & Growth Product Lead at Vestiaire Collective, founder of AVANTIR (growth systems, AI, performance marketing), active real estate investor in French secondary cities, and personal algo trader running automated systems on own capital.

Offer: Three distinct things: (1) end-to-end growth architecture through AVANTIR — paid acquisition, attribution and MarTech systems, SEO/GEO, AI workflows, CRM, cloud infra, conversion-optimized web; (2) strategic consulting on growth and AI systems for companies that need senior operator thinking; (3) real estate — buys, analyzes, and operates multi-unit rental buildings in France as a capital allocation vehicle, not a service.

ICP: For AVANTIR: CMOs, Heads of Growth, or founders at scale-ups and mid-market companies with fragmented stacks and no one internal who can own the full picture — paid, data, and systems together. For real estate: no external ICP, self is the investor.
```

---

## Q2 — Paste 1-2 things you've written recently. Don't edit them.

An email, a LinkedIn post, a DM, a doc — anything that sounds like you when you're not trying. **Paste verbatim.** Do not type these mid-conversation with Claude — chat-shaped samples are worse than no samples (voice contamination).

```
Sample 1 — Email to Google team re: SKAN / ODM (raw paste)

Hello Google team,

Hope you are all doing well.

Thank you for the presentation made to the team regarding iOS measurement best practices for Google Ads in New York.
I would love to deep dive more into this specific topic. Especially Aggregated Signals via SKAN & On-Device Measurement + IDFA.
image.png
We are currently on a 6 bits setup in both SKAN 3 & 4.
As we would like to move to a more granular SKAN setup leveraging conversion schemas, here is a proposal of 63 Conversion values that I would like to propose. Would it be possible for you to review them and give us your feedback based on best practices in the industry?

I also have some specific questions regarding SKAN signals & ODM:
Are SKAN 4 63 CVs & ODM used for campaign optimization? If so, how?
How are SKAN Conversions values different from our regular conversion value based on tracking ? By that, I mean, Is there a risk that if we activate those conversion values, they will be added to our additional event-based conversion value + NCA conversion value, thus unexpectedly driving up the spend as we are not limited by budget and steering on tROAS.
Does Google support triggering ads with SKAN version 4.0 Ad signature for Vestiaire Collective? (Our MMP explained that it can be enabled for us on your side or that you could already have it automatically enabled).
Might be a stupid question because the main goal of SKAN as I understood it is to gain visibility but have you been able to measure incrementality in some way on other clients of having the SKAN 6 bits setup vs SKAN 63 CV setup. Have you also been able to measure incrementality between a setup with ODM and a setup without it?
Thank you!
Louis
```

```
Sample 2 — Email to Adjust & Google re: iOS purchase event drop (raw paste)

Hello Adjust & Google team,

I am reaching out because we are observing a significant decrease in purchase events tracked on Google Ads iOS.

Please find below the volume trend of iOS purchase events (Days to convert = 1 to delete conversion window bias).

As you can see, we are observing a gradual decrease of purchase events on iOS reaching -75% vs 2th of Dec on the 14th.
YELLOW = IOS
BLUE = WEB
RED = ANDROID

image (134).png

Despite this decrease, Adjust unattributed raw purchase volumes on iOS haven't experienced the same scale of decrease and seem seasonality driven. Moreover, META trend of purchase events is also quite flat.
image (137).png
image.png

Also for context, IDFA opt-in rates didn't vary that much throughout Dec.
image (135).png

At last, and I think it's related, we have observed a loss in SEO Google referred internally on version 5.200.0 of our setup. (below is SEO Google referred date_session by app versions)
image (136).png

In addition to this, we do see in terms of conv.value attributed on the following event a drop since the 24th of nov. Note that this is observed from both firebase & adjust on the events (session_start) (conv value per event occurance = 1€)
event event_product_view (adjust)
session_start (adjust)
session_start (1) (Firebase)

image.png

image.png

This investigation leads me to believe that, because raw volumes of purchase on IOS didn't vary a lot on META & Adjust, there is an issue with the way Google Ads claims their purchases. Could you check our volumes of gclid, wbraid & gbraid received on our tracking setup please?
Are you experiencing sent by adjust and received by google in gclid, wbraid & gbraid on the same order of magnitude?

Thanks a lot for support,
Louis
```

---

## Q3 — What are your 2-3 biggest priorities for the next 90 days?

Quarterly priorities. Not yearly aspirations. Things that, if not done by July, would make you say "I wasted Q2."

```
1. Real estate — sign the compromis (preliminary purchase agreement) on a building before summer 2026 (end of June). City TBD, depends on what surfaces. Hard requirement: the operation must generate at least €2,500/month gross rental income.

2. Algo trading — system live before summer 2026 (end of June). Definition of "live": connected to broker, strategy finalized and validated, technical application built and ready to run.

Explicitly deprioritized for Q2: AVANTIR (freelance company). Not a priority this quarter.
```

---

## Q4 — Where does revenue actually land, and where is it tracked?

Multiple answers OK. Stripe? Skool? GoHighLevel? QuickBooks? A spreadsheet?

```
Banking & income aggregation: Powens + Plaid + n8n + custom API connections pull from all bank accounts (Vestiaire salary, AVANTIR freelance revenue, real estate rental income) into a Google Sheet that updates automatically.

Algo trading P&L: Alpaca (automated systems) + Interactive Brokers (manual, non-automated investing). Both broker P&Ls also flow into the Google Sheet.

Single source of truth: the Google Sheet. Everything aggregates there.
```

---

## Q5 — Where do you talk to customers, your team, and the outside world day-to-day?

Email (which one — Gmail / Outlook)? Slack? Teams? DMs (Skool / Discord / iMessage)? Phone?

```
Email: louis.giuliani@vestiairecollective.com (Google Workspace, work) + louisgiuliani@hotmail.com (Outlook, personal).

Internal chat: Slack at Vestiaire only. Nothing else.

DMs (external): WhatsApp, iMessage, LinkedIn DMs, Messenger.

Phone: voice notes can matter, but only for real estate / building calls.

Calendar (auto-inferred): Google Calendar (Vestiaire workspace) + Outlook Calendar (Hotmail). To confirm at scaffold time.
```

---

## Q6 — Where do meeting recordings, notes, and important docs live?

Granola? Otter? Fireflies? Google Drive? Notion? Dropbox? A folder on your desktop you keep meaning to organize?

```
Meeting recordings: Google Meet (native recordings).

Notes: Microsoft To Do.

Docs (work / Vestiaire): Google Drive (Vestiaire Workspace).

Docs (personal — AVANTIR, real estate, algo trading): Google Drive (personal) + Notion.
```

---

## Q7 — What's the one task that eats your week, and where do you currently track work?

The single biggest time-suck or recurring drudgery. Plus where tasks/projects live (ClickUp / Asana / Linear / Notion / a notebook).

```
Top pain (top_pain): Vestiaire Slack triage — responding intelligently to colleagues' Slacks across product teams. The cognitive cost is in pulling the right context to answer well, not the typing itself.

Secondary pain: Daily stand-up meeting eats time.

Tertiary pain: Calling building sellers manually for real estate prospecting. Flagged as a future automation candidate — voice clone (ElevenLabs) + outbound French agent (Vapi / Bland / Synthflow / Retell) can plausibly handle this. To revisit on Day 14 via /level-up.

Everything else is "fairly automated" already.

Task tracking:
- Vestiaire / work: Jira (real tickets, internal).
- Personal tasks (AVANTIR, real estate, algo, life): Microsoft To Do.
```

---

When this file is filled, run `/onboard` (or re-run it) and the wizard will scaffold your Day-1 file set: `context/`, `references/voice.md`, populated `connections.md`, and a filled `CLAUDE.md`.
