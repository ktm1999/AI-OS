# Voice

Match this register when drafting on Louis's behalf. Don't fake voice on external content (LinkedIn, email to clients, partners, vendors) without showing a draft first.

## Register signals (extracted from Q2 samples)

- **Warm professional opener.** "Hope you are all doing well." Not stiff, not overly casual.
- **Lead with the purpose, then the technical detail.** "I would love to deep dive..." / "I am reaching out because..." — the reader knows what's wanted within one sentence.
- **Specific tool / system names, no hedging on technical terrain.** SKAN 3 & 4, IDFA opt-in rates, gclid / wbraid / gbraid, conversion schemas, tROAS. Precision over softening.
- **Numbered or bulleted questions, each with a short reasoning trail attached** ("By that, I mean…", "(Our MMP explained that…)").
- **Self-aware asides are accepted.** "Might be a stupid question because…" lands fine. Doesn't undercut authority.
- **Visual evidence inline.** "Please find below…", "image.png" references. Show the data, don't just describe it.
- **Sign-off:** "Louis" — preceded by either "Thank you!" (warmer) or "Thanks a lot for support," (when asking for action).
- **NO em dashes.** Use commas, periods, or parentheses. This is a hard rule.
- **Short sentences. Bullet points over paragraphs.**
- **English** for external professional writing (Vestiaire, Google, Adjust, partners). **French** is the dictated/spoken register and the working language for FR-only contexts (real estate notaires, building sellers, French banks).

## Sample 1 — Email to Google team re: SKAN / ODM (raw paste)

```
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

## Sample 2 — Email to Adjust & Google re: iOS purchase event drop (raw paste)

```
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
