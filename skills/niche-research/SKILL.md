---
name: niche-research
description: >
  Downloads an entire industry into your brain — pain points, language, where they hang out,
  what they pay for, and the perfect software solution to sell them. Use this skill any time the
  user names a niche or industry and wants to become an instant expert before outreach, discovery
  calls, or building software. Consolidates the prior industry-download and niche-research skills
  into one — always prefer this over either of those. Trigger phrases include "industry download",
  "niche research", "get me up to speed on [industry]", "download the [niche] industry",
  "make me an expert on [industry]", "research this market", or any request to research a specific
  niche before outreach, discovery calls, pricing a project, or deciding what to build.
---

# Niche Research v2

Become an instant insider. Download an entire industry into your brain so you sound credible on
the first call, ask the right questions, and know exactly what to build and how to price it.

This skill replaces the earlier `industry-download` and `niche-research` skills, which produced
near-duplicate output. Use this one going forward.

## What This Skill Does

**Input:** Any niche or industry (auto shops, dental offices, HVAC contractors, music venues, etc.)

**Output:** Complete operator-level intelligence — what they do all day, what they hate, what
they pay for, what they say, what keeps them up at night, and the exact gap in the market —
ending in a concrete software recommendation with two pricing models (one-time project vs.
recurring retainer) so it plugs directly into `niche-opportunity-finder` downstream.

**Persistence:** Assign the niche a slug (`niche_id` — lowercase, hyphenated, e.g.
`auto-shops-3-15-bays`) as your first step, and **save the full report to
`research/{niche_id}/niche-research.md`** before ending your turn. This is not optional — if
this report only exists inline in the current conversation, `niche-opportunity-finder` (which
may run in a different session entirely) has nothing to read from, and every downstream
`icp.fontes`, pain point, and pricing figure has to be re-derived or guessed. Announce the
`niche_id` you picked clearly, since `ride-along` and `niche-opportunity-finder` both need
to reuse the exact same one to find this file later.

## How to Use This Skill

### Step 1 — Validate the niche is specific enough, and confirm the target market
"Small businesses" or "contractors" is too broad — push back and ask for a narrower slice.
"Auto shops with 3-15 bays," "commercial HVAC contractors," "pediatric dentists in suburban
areas" are good. Narrow beats broad — a vague niche produces a vague, useless report.

**Also confirm the target country/market and currency explicitly — don't infer it from the
language the request was written in.** A request in Portuguese could target Brazil, Portugal, or
any other Portuguese-speaking market; guessing wrong means researching the wrong forums, the
wrong price benchmarks, and the wrong competitors without anyone noticing until much later. Ask
if it isn't already stated, and record the answer as `mercado: {pais, moeda}` — this feeds
`niche-opportunity-finder`'s pricing section directly (see Section 9 below).

### Step 2 — Run real web research
Do not invent generic answers. Search:
- Reddit (subreddits, complaint threads — "why does X suck", "what do you hate about your job")
- Facebook Groups, LinkedIn Groups, Slack/Discord communities
- Industry forums and trade publications
- YouTube ("day in the life" videos, tutorials, tool reviews)
- Podcasts
- Conference/trade show listings

Pull real terminology and real quotes. If you can't name the actual software tools this industry
uses and can't quote a real complaint, you haven't researched enough — keep searching before
you write the report.

### Step 3 — Output the full report in the exact structure below
Do not skip sections. Use markdown headers. Be specific — vague answers are useless. Quantify
everything: "loses money" is worthless, "loses $8K-$15K/month" is gold.

## Output Structure

### 1. Industry Overview
- Number of businesses in the target market (approximate)
- Average annual revenue per business
- Average employee count
- Recession-proof? (yes/no/sort-of)
- Current reality check: what's actually happening in this industry right now

### 2. Where They Hang Out Online
Specific names, links where possible, member/subscriber counts. This section isn't just
narrative — it's the raw material for the `fontes` field `niche-opportunity-finder` will
write into `niche-config.yaml`, which `lead-finder` reads to actually go find leads. For every
place listed, tag it explicitly:

- **Automatable** — a platform with a known scraping path (Apify actor or equivalent). Name the
  actor if you know one (e.g. `apify/instagram-hashtag-scraper` for Instagram hashtags,
  `apify/google-maps-scraper` for Maps listings). Include the specific hashtags, search terms,
  or listing categories to use — not just the platform name.
- **Manual** — no reliable scraper exists (most Facebook Groups, invite-gated forums, LinkedIn
  Groups). Name the specific group/forum/community and its member count — "try Facebook" is
  useless, "Auto Shop Owners Hangout (47K members)" is usable.

Cover: Subreddits · Facebook Groups · Industry forums · LinkedIn Groups · YouTube channels ·
Podcasts · Annual conferences (dates/locations) · Trade publications · Directories/Maps
listings, tagging each with its mode as above.

### 3. Pain Points Ranked by Money Lost
Top 10, each with: the pain in their words, what it costs per month/year, why existing
solutions don't fix it.

### 4. Language Dictionary
The most important section — pull directly from forums and Reddit, verbatim where possible:
- **Industry terms** (with definitions) · **Acronyms**
- **Pain phrases** — verbatim things they say when frustrated
- **Success phrases** — verbatim things they say when winning
- **Outsider red flags** — terms that mark you as not one of them, with the correct alternative

### 5. What They Already Pay For
Specific company names, approximate monthly cost, what problem each one solves or fails to
solve. This kills the "but would they pay for this?" objection in one glance.

### 6. What Keeps Them Up at Night
Top 5 fears, ranked, in their language — not corporate language.

### 7. Dream Outcome
What does a perfect day look like for them? What would they pay a premium to make true?

### 8. Market Gaps
Specific software, features, integrations, or services that don't exist yet — or exist but suck.
This is where the opportunity lives.

### 9. The Perfect Software Solution
- **Core problem to solve first** (the painful, expensive one)
- **MVP feature list** (3-5 features max) · **Phase 2 features**
- **Pricing recommendation — both models, with ROI math, anchored to the confirmed `mercado`:**
  - The $10K-$40K one-time / $1,500+/month recurring figures are US-market reference points, not
    universal constants — **do not quote them directly for a non-US market.** Re-anchor using a
    real local benchmark from the research itself (typical revenue or income in the niche,
    what comparable local tools already charge) and convert to the local currency confirmed in
    Step 1.
  - One-time project price, in local currency, with the local benchmark that justifies it
  - Recurring retainer price, in local currency, with the same
  - Both numbers feed directly into `niche-opportunity-finder`, which decides which shape
    fits the specific problem it ends up picking — don't pre-commit to one here, just price both
- **Positioning angle** (one sentence: "The only X built specifically for Y")

### 10. Go-to-Market Cheat Sheet
- Where to find them (specific platforms, links)
- Opening message template (using their actual language)
- 3-5 expected objections and responses
- Proof they need to see before they'll pay

## Worked Example (for calibration)

**Input:** "Research the independent music venue market (under 1,000 capacity)"

**Sample of expected depth:**
- Overview: ~10,000 venues in the US, $500K-$2M average revenue, independents squeezed by
  consolidation (Live Nation/AEG)
- Top pain: double-bookings — artist confirms, venue accidentally books someone else same night
- Language: "load-in time," "door time," "rider," "backline" — say "show" not "concert"
- Market gap: no all-in-one booking + ticketing + contracts + marketing platform under
  $500/month; incumbents (Prism, Artifax) run $800-1,500/month
- Solution: booking calendar with conflict detection + digital contracts + low-fee ticketing,
  priced at $15K one-time build OR $200/month SaaS
- Objection handling: "We already use Prism" → "How much are you paying? We're $200/month vs.
  $1,200 — what features would you actually miss?"

Use this as a bar for specificity, not a template to copy for other niches.

## Pro Tips for Better Output

- **Go narrow, not wide.** "Dentists" → "pediatric dentists in suburban areas." "Contractors" →
  "residential HVAC contractors with 5-15 employees."
- **Hunt complaint threads specifically.** Reddit posts titled "Why does X suck?" or "What do you
  hate about your job?" are pain-point gold mines.
- **Steal their language verbatim.** If a forum post says "I'm drowning in paperwork," your cold
  email says "tired of drowning in paperwork?" — not "optimize your workflow."
- **Quantify aggressively.** Every pain point needs a dollar range or hour count attached.
- **Skip generic SaaS advice.** This is for niche, boring, profitable B2B opportunities — not
  the next consumer app.
- **Validate before building.** After the research, this skill's job is done — but before
  committing to a build, reach out to 5-10 people in the niche and ask: "Is [pain point]
  actually a problem for you? Would you pay $X to solve it? What have you tried so far?"
  Research gets you 80% there; real conversations get the last 20%.

## When to Use This Skill

✅ Before any cold outreach to a new industry
✅ Before any discovery call
✅ Before deciding what to build or how to price it
✅ Before running `ride-along` or `niche-opportunity-finder` — this skill primes the
  vocabulary and pain data those downstream skills consume

❌ Don't use for industries you already know cold
❌ Don't use for markets too broad to be a real niche ("small businesses" isn't one)

## Stacking With Other Skills

```
niche-research  →  ride-along  →  niche-opportunity-finder
  (macro facts,        (embodied         (pick the specific problem, the monetization
   both pricing          empathy)         shape, and validate before building)
   models in §9)
```

## Remember

You're not trying to become a 20-year veteran of this industry — you're trying to sound like
someone who's been around it long enough to ask the right questions and propose the right
solution. This skill gets you 80% of the way there. Real conversations get you the last 20%.

**Outsider to insider. Then you make the call.**
