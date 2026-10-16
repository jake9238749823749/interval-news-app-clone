# Interval News — Product Research (for clone)

Researched 2026-10-16. Sources: App Store listing + iTunes lookup API, Google Play listing,
interval.news (landing + legal pages), Notion job post, App Store / Play / third-party reviews,
founder social posts. Reference screenshots are in `docs/reference/` (their copyrighted assets —
for internal reference only, don't ship them).

---

## 1. What it is

**Interval News** — "The headlines you're missing." A curated, human-edited daily news app focused
on *underreported / "suppressed"* stories. Each story is a short card → article with a
**summary**, **evidence** (primary sources: court docs, UN docs, footage, tweets, Truth Social posts),
**sources** (original reporting), and a **coverage meter** showing how many major outlets covered it,
with call-outs of "controversial outlets" and how they framed (or ignored) the story.

Positioning: anti-algorithm, anti-billionaire-owned-media, "no ads", "receipts". Audience came largely
from TikTok/Instagram (founder has ~400K followers; @interval_news IG ~236K). Many reviews mention it
"replacing TikTok / doomscrolling" — the UI is deliberately Instagram-like.

| | |
|---|---|
| Company | Interval Collective Inc. (team@interval.news) |
| Founder | Syed Hemu Rahman — product designer / creator, independent journalist, Substack + TikTok |
| iOS | id6756529560, bundle `com.interval.IntervalBeta`, first release 2025-12-20, public launch ~Jan 1 2026; v1.17 (2026-08-28); 12.9 MB; iOS 17+; iPhone only; English only |
| Android | `com.intervalcollective.news`, released 2026-03-05, 10K+ installs (~12.8K), 3.8★; updated 2026-09-10 |
| Ratings | iOS 4.8★ (~150 ratings); claimed #2–#5 in News on launch week, 17.5K users first week |
| Price | Premium Monthly **$11.99**, Premium Annual **$79.99** (earlier: $9/mo, $90/yr). 2-week free trial (per review). No ads. |
| Category | Magazines & Newspapers / News; age 12+/13+ |

---

## 2. Feature inventory

### Free vs. Premium (current listing)
- **Free:** all headlines + subheaders, **5 free full articles** (lifetime-ish meter), daily video/audio episode.
  (Has changed several times: "1 featured headline/day", "3 articles/week" in older copy.)
- **Premium:** all articles in full, summaries/key takeaways, evidence & original sources, coverage &
  visibility indicators ("controversial reporting details"), misinformation section.

### Screens (from screenshots — see `docs/reference/`)

**Tab bar** (light mockup on site, `site_home_light_tabbar.png`): `Headlines` · `Fake news`
(misinformation) · `Stories` (video) · `More` + a floating circular **Search** button to the right.
Translucent/blurred pill-style tab bar.

**1. Home / Headlines feed** (`appstore_1/2.jpg`)
- Centered lowercase wordmark **"interval"** at top.
- Horizontal scroll of **topic chips** with emoji/flag icon: e.g. `🏛 Trump Admin`, `🇵🇸 Gaza Genocide`,
  `II News Feed`, `👁 Surveillance`, `🇮🇱 Israel`, … Selected chip = filled dark-gray pill.
  Older design: Instagram-**Stories-style circular avatars** per topic (Israel-Palestine, Epstein Files,
  Trump Economy, ICE Arrests…).
- **Hero card** (first story): large centered serif headline, 2-line gray subheader, meta row
  `1d ago · Moderate coverage ▬▬ · ⋯`, then full-bleed image below.
- **List cards**: serif headline left (3–4 lines), square thumbnail right (rounded), meta row
  `4d ago   Suppressed ▬  ⋯`. Coverage label + tiny progress bar.
- "Staff picks" row on home feed (v1.15).

**2. Article detail** (`appstore_4.jpg`, `appstore_8.jpg`, `site_article_light.png`)
- Full-bleed hero image fading to black; floating glass buttons: back `‹` (left), **bookmark**,
  **share**, **report/feedback** (speech-bubble-with-!) (right, grouped in one pill).
- Big centered serif headline, date (`July 8, 2026`), lead paragraph (sans).
- **Segmented tabs:** `Summary` · `Evidence` · `Sources` (underline indicator). (Earlier: Summary · Deep Dive · Evidence.)
- **Summary** = numbered key-takeaway cards, each with an emoji + bold title + paragraph
  (e.g. "🔍 1. UN Special Committee Investigation", "🍽 2. Starvation as a Weapon of War", "⚖️ 3. …", "🛑 4. …").
- **Evidence** = cards: emoji + bold title (the claim/fact), gray paragraph, blue `View source →` link.
- **Sources** = list of original reporting outlets/links.
- Older light design had a bottom bar: back, coverage meter, bookmark, share.

**3. Coverage sheet** (`appstore_7.jpg`, `site_coverage_*.png`) — bottom sheet with grabber, opened
from the coverage indicator.
- Title "Coverage is *SUPPRESSED* / *MODERATE* / *UNIVERSAL*" (italic caps serif).
- Progress bar + big serif fraction `0/35`, `8/40`, `13/20`, `17/20` + "Major outlets have covered this headline."
- **Controversial outlets** list: outlet logo + name + 1–3 sentence critique of how that outlet framed/underplayed it
  (NYT, CNN, BBC, MSNBC, Fox News…).
- Coverage levels inferred: **Suppressed** (~0–25%), **Moderate** (~40–70%), **Universal** (~85%+). Possibly a
  "Low"/"High" tier in between — unconfirmed. Ratio denominators vary per story (20/35/40) → the outlet
  panel is story-specific, not a fixed list.

**4. Misinformation ("Fake news") tab** (`appstore_5.jpg`)
- "Trending misinformation" header, horizontal carousel of large image cards with serif claim headline + time.
- "All" section below: list cards like the home feed. Each item = a false/misleading claim + debunk with visuals.
- Reviews describe using it to check social media claims.

**5. Interval Daily (video/audio)** (`appstore_6.jpg`)
- Full-screen vertical video (TikTok-style), header "Interval Daily · 20h ago · New episodes M–F, 3pm ET",
  burned-in captions, segmented progress bar at bottom (chapters), embedded story card overlay linking to the
  article being discussed.
- v1.16 switched to **audio-only podcast with playback speeds**. Reviews mention both ("audio or video").

**6. Other** (inferred from listing/reviews/release notes): Sign in with Apple, paywall + trial, push
notifications (breaking headlines; Android notifications reported broken), bookmarks/saved, share sheet
(v1.15 "new sharing options", likely share-as-image cards), report-an-issue/corrections feedback, search.
Reviews ask for: more international (non-Israel) coverage, copy text, a cheaper/free tier, easy
subscription cancellation, full-article links.

---

## 3. Design language

- **Dark-first** app (black `#000` bg, cards ~`#1C1C1E`/`#2C2C2E`, secondary text ~`#8E8E93`,
  link blue ~`#0A84FF`). Early version + marketing used a light theme (white cards on `#F2F2F7`).
- **Typography:** headlines in **PP Editorial New** (Pangram Pangram; condensed-feeling editorial serif,
  *Italic* for emphasis words — "you're *missing*", "*suppressed*"). UI/body in **SF Pro** (iOS) / Inter (web).
  PP Editorial New needs a commercial license — free alternatives: *Instrument Serif*, *Playfair Display*,
  *Fraunces*, *Newsreader*.
- Logo: **"II"** serif mark (pause-symbol / roman numeral two = "interval"); wordmark lowercase "interval".
- Rounded cards (~16–20 px radius), generous padding, glassmorphism buttons over images, gradient fades from hero image to black.
- Landing site: Framer; colors `#111`, `#444`, `#999`, `#EEE`, `#FBFBFB`, accent `#0099FF`; GA4.

---

## 4. Content operation (from the Notion "Editorial Operator" job post)

Interval is **human-curated, not algorithmic**. Small remote rotation, 7 days/week:
- Monitor wires/majors (AP, Reuters, NYT, BBC, Al Jazeera) + independent journalists, Substack, X, Telegram, TikTok.
- Pick stories that are suppressed / misleadingly framed / missing context.
- Per story: tight headline, neutral summary, **primary sources + evidence**, a visual (templated), entered
  into the **Interval CMS**. ~20–40 min/story; **5–8 headlines/day**, ready by early morning ET; breaking
  headlines via notifications.
- Coordination on Slack/Signal. Corrections policy: fix promptly, note significant corrections in-article,
  no silent fixes; corrections via team@interval.news.

→ **Implication for the clone:** the product is ~50% an editorial CMS. We need an admin tool, and likely
LLM-assisted drafting (summary, takeaways, evidence extraction, coverage counting) to make a small team viable.

---

## 5. Tech observations

- iOS binary is only 12.9 MB and bundle id `com.interval.IntervalBeta` → likely **native SwiftUI**
  (RN/Flutter apps are usually larger). Android shipped 2.5 months later with lower rating + notification bugs,
  suggesting a separate/second-class build. *Inference, not confirmed.*
- Privacy label: collects purchase history + user ID (linked), product interaction (not linked). Auth = Sign in
  with Apple. Payments = App Store IAP (probably RevenueCat or StoreKit 2 — unknown). No ad SDKs.
- Web: Framer landing, Tally forms (contact), Notion (jobs), GA4. No web reader.

---

## 6. Proposed clone architecture (recommendation)

**App:** Expo / React Native (one codebase for iOS + Android, and fixes Interval's weak Android story)
— or SwiftUI if iOS-only fidelity matters most.

**Backend:** Supabase (Postgres + Auth w/ Apple/Google + Storage + edge functions) or equivalent.
**Payments:** RevenueCat (entitlement `premium`, monthly + annual, 14-day trial).
**Push:** Expo Notifications / FCM+APNs. **Media:** Mux or plain HLS/MP3 on a CDN for the daily episode.
**Admin CMS:** small Next.js app on the same DB; optional Claude-assisted drafting.

### Data model (draft)
```
topics(id, name, emoji, slug, sort, is_active)
stories(id, topic_id, headline, subheadline, lead, hero_image_url, image_credit,
        published_at, status[draft|published], is_staff_pick, is_free, coverage_count,
        coverage_total, coverage_level[suppressed|moderate|universal], updated_at)
story_takeaways(id, story_id, position, emoji, title, body)          -- Summary tab
story_evidence(id, story_id, position, emoji, title, body, source_url, source_type)  -- Evidence tab
story_sources(id, story_id, outlet, title, url, author)              -- Sources tab
outlets(id, name, logo_url, is_major)
story_outlet_notes(story_id, outlet_id, covered bool, critique text) -- Coverage sheet
misinfo_items(id, claim, image_url, verdict, explanation, evidence[], published_at, is_trending)
episodes(id, title, media_url, kind[video|audio], duration, published_at, chapters jsonb, linked_story_ids[])
corrections(id, story_id, note, created_at)
users(id, ...) ; bookmarks(user_id, story_id) ; article_reads(user_id, story_id)  -- free-article meter
reports(id, user_id, story_id, message)
```

### MVP scope (suggested order)
1. Feed with topic chips + hero/list cards + coverage label
2. Article detail with Summary / Evidence / Sources tabs + coverage bottom sheet
3. Admin CMS to create stories
4. Auth + paywall + 5-free-articles meter
5. Misinformation tab
6. Daily episode player (audio first)
7. Bookmarks, share-as-image, search, push

---

## 7. Legal / product cautions for a clone
- Don't reuse the **Interval** name, "II" mark, tagline copy, screenshots, or their story content.
- PP Editorial New is a paid font; license it or use a free serif.
- Summaries of third-party reporting are fine; don't republish full articles or outlet logos beyond fair use.
- "Suppressed" framing + outlet critiques carry defamation/accuracy risk — keep a visible corrections policy.
- Make cancellation easy (a recurring review complaint) — link to the platform's subscription management screen.

## Sources
- App Store: https://apps.apple.com/us/app/interval-news/id6756529560 (and `?see-all=reviews`)
- iTunes lookup: https://itunes.apple.com/lookup?id=6756529560
- Google Play: https://play.google.com/store/apps/details?id=com.intervalcollective.news
- Site / legal: https://www.interval.news , https://www.interval.news/privacy-policy
- Job post: https://www.notion.so/Founding-Researcher-Writer-Interval-Early-Hire-2a37832a292580c187d5db9264f6d842
- Reviews aggregator: https://justuseapp.com/en/app/6756529560/interval-news/reviews
- Market data: https://mwm.ai/apps/interval-news/6756529560
- Founder: https://www.linkedin.com/in/syed-hemu-rahman-a115a294/ , https://hemurahman.substack.com/p/big-life-updates-and-the-evolution ,
  https://www.tiktok.com/@hemu_rahman/video/7590898165885275406
