# Margate Hedges & Tree Services — how-to article template contract

Contract for every future `how-to/*.html` article shipped by the nightly
content-ingestion routine on this repo.

Owner of the routine: Richard (his claude.ai/code account) — see `INGESTION.md`.
Owner of this contract: Jet (website fleet).

Version: 1.0 — 2026-08-12 (scaffolded from scratch for this site; not a copy
of sandwichhedges.co.uk's contract — this site has its own established
markup, JSON-LD shape and voice, and its own assigned structural angle. See
"Ring positioning" below).

## Ring positioning — this site is story-led, not procedural-default

margatehedges.co.uk is one of 9 sister sites in a Kent "hedge ring"
(broadstairs/canterbury/deal/dover/margate/ramsgate/thanet/wingham/sandwich
hedges). Same business model, same underlying HTML/CSS plumbing, different
towns. Google sees all 9 domains. To avoid a templated-content signal across
the ring, each site has been assigned a genuinely distinct macro-structure.

**This site's assigned angle: case-study / story-led.**

Every how-to article MUST open with a short, real-feeling scenario before it
moves into the practical or legal detail — e.g. "A customer in Cliftonville
called us in June about a leylandii hedge that had crept over her
neighbour's fence line..." This is not optional local colour on top of a
generic structure — it is this site's house style, the same way
sandwichhedges.co.uk rotates procedural/comparison/decision-tree/checklist
skeletons. Do not quietly drift back to a plain "hero → intro → steps"
shape; the opening story is the thing that makes this site's articles read
differently from the other 8 domains.

**Do not copy sandwichhedges.co.uk's contract verbatim.** That site uses
`Article`+`BreadcrumbList` in an `@graph`, a `data-howto-cat` filter system,
and `JET-RELATED-GUIDES` HTML comment blocks. **None of that exists on this
site.** This site has its own established conventions (below), and they are
simpler. Follow what is actually on disk in `how-to/*.html`, not what's on a
sister site.

## The story-led opening — the hard requirement (P1)

Every article's lede (or the paragraph immediately after it) must set up a
concrete, specific-feeling job story:

- A named-ish situation: a customer, a location within Margate/Cliftonville/
  Westbrook/Garlinge/Northdown/Palm Bay/Westgate-on-Sea, a hedge problem.
  Never a generic "many homeowners ask us..." opener — make it feel like one
  real call.
- Do not name a real private individual. "A customer in Cliftonville",
  "A holiday-let owner near Dreamland", "A reader emailed after reading our
  conservation-area guide" are all fine. A first name with no surname
  ("Dave, over towards Garlinge") is also fine and matches the site's
  existing confident-contractor voice — just don't fabricate a full name +
  identifiable detail that reads as a real traceable person.
- The story frames the practical problem the rest of the article solves. It
  is not a throwaway anecdote bolted onto a generic guide — the numbered
  sections / calendar / comparison that follows should visibly be answering
  the story's problem.
- Length: 2-4 sentences is enough. This is a frame, not a short story.
- Existing articles on this site (e.g. `high-hedges-neighbour-law-margate.html`,
  `staged-hedge-reduction-margate-coastal.html`) already open with
  "Every [couple of months / year] I get a call from..." — that first-person
  contractor voice is close to story-led but genericised across many calls.
  New articles should go one step further into a single, specific-feeling
  incident, not "every year I get called about X" in the aggregate.

### Reference shape (adapt, don't template mechanically)

1. Story open (2-4 sentences, specific scenario).
2. One-line bridge sentence: what this article is going to answer as a
   result of that job.
3. The practical/legal detail in whatever shape suits the topic (numbered
   steps, month-by-month, comparison, decision points) — see "Structural
   variation within the story frame" below.
4. A callout box back to the story where it helps ("Back on the
   Cliftonville job, once the nest check came back clear, we...") is a nice
   touch but not required on every article — don't force it if it reads
   forced.
5. Closing CTA `.callout` box → `contact.html`.

## Hard requirements (P1 — must be in every article)

### 1. Match the existing page anatomy exactly

Copy the head/body shape from an existing article (e.g.
`how-to/hedge-nesting-season-margate.html` or
`how-to/high-hedges-neighbour-law-margate.html`), not a generic template.
That means, verbatim/unchanged from an existing article:

- `<title>` ending ` | Margate Hedges & Tree Services`
- `meta description`, `canonical`, `og:type=article`, `og:image` (the shared
  `assets/img/og-default.png` unless a better topic-specific image exists),
  `og:image:width`/`height`, `og:title`, `og:description`, `og:url`,
  `meta name="robots" content="index,follow,max-image-preview:large"`
- Google Fonts `<link>` block: Playfair Display 700 + Work Sans
  400/500/600 — do not add other weights or fonts
- `<link rel="stylesheet" href="/assets/css/styles.css"/>`
- The inline SVG data-URI favicon — copy verbatim, do not invent a new one
- GA4 snippet with the real property ID `G-53100B6S34` (not the
  `G-MARGATE-PLACEHOLDER` string mentioned in `README.md` — that placeholder
  was superseded; every live page already carries the real ID) verbatim
- Full topbar (`"Salt-hardened. Seaside-sharp."` strap, pensioner-discount
  badge, phone `07763 100 477`, WhatsApp button with the
  `wa.me/447763100477?text=From%20margatehedges.co.uk...` prefill, email
  `hello@margatehedges.co.uk`) — copy verbatim
- Full site nav (Home / Services / Areas / Guides / Recent jobs / About /
  Contact) with `class="active"` on the Guides link
- Full footer (business blurb + strapline, Services column, Local guides
  column, Contact column, foot-bottom with year script + Privacy/Sitemap
  links) — copy verbatim structure; only the "Local guides" column's 3 links
  are curated by hand and are **not** a growing per-article list (see §7)
- `<script src="../assets/js/main.js">` if present on the reference article,
  plus the inline `document.getElementById('yr')...` year script

### 2. JSON-LD — this site's established pattern is a single `Article` object

Every existing how-to article on this site uses one `<script
type="application/ld+json">` block with a **flat `Article` object**, not an
`@graph`:

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "…",
  "description": "…",
  "author": {"@type": "Person", "name": "Richard Lim"},
  "publisher": {"@type": "Organization", "name": "Margate Hedges & Tree Services"},
  "datePublished": "YYYY-MM-DD",
  "inLanguage": "en-GB",
  "mainEntityOfPage": "https://margatehedges.co.uk/how-to/<slug>.html"
}
```

**Keep using this exact shape.** Do not switch to `HowTo`, do not switch to
an `@graph`, and do not add `BreadcrumbList` inside the article's own
script — that pattern belongs to `how-to/index.html` (the hub page), which
uses a different, separate `@graph` with `CollectionPage` + `BreadcrumbList`.
The hub and the individual articles have never matched each other on this
site; that inconsistency already exists in the 9 hand-authored articles and
is out of scope to "fix" as part of content ingestion. If a future article
genuinely needs `dateModified` (because it's an edit, not a first ship),
add it alongside `datePublished` — none of the 9 existing articles currently
carry `dateModified`, so its absence on first-ship articles is correct; add
it only when an article is later revised.

`author.name` is always `"Richard Lim"` (a real named person, per this
site's existing convention — do not switch to an `Organization`-only author
or invent a different name).

### 3. FAQPage JSON-LD — not yet established here, optional P2 addition only

Unlike some sister sites, **no existing article on this site carries
`FAQPage` schema.** Adding one is a reasonable, low-risk enhancement for a
genuinely procedural/calendar/legal-process article (nesting season, TDC
hedge-height complaints, conservation-area notices), but it is **not** a
hard requirement — do not treat its absence as a bug against this contract.
If added, keep it as a second, separate `<script type="application/ld+json">`
block (do not merge into the `Article` object), 3-5 Q&A pairs, genuinely
distinct questions (not padding).

### 4. The nesting-season safety/legal callout

Any article that touches cutting/trimming *timing* must reference the UK
**Wildlife and Countryside Act 1981**, section 1: it is an offence to
intentionally damage or destroy an active wild bird's nest (fine up to
£5,000 per nest). Nesting season runs **1 March – 31 August**; the
legal-default safe cutting window is **September to late February**; a
summer cut is only acceptable after a competent visual nest check confirms
the hedge is empty. Blackbirds can still be sitting into October, so even a
September cut warrants a check.

The reference implementation is `how-to/hedge-nesting-season-margate.html` —
match its framing (including, where the job is genuinely coastal/seaward,
the Thanet Coast SSSI / Sandwich & Pegwell Bay Ramsar / North Foreland RNR
flags it covers) rather than writing generic nesting-law boilerplate from
scratch.

**This site does not yet have a dedicated `.callout--warn` CSS class.** The
existing `.callout` class (`article.guide .callout`, gold/`--sun` left
border, defined in `assets/css/styles.css`) is currently used for CTA boxes
only — no existing article uses a visually distinct warning box for the
WCA/legal material; it's handled in plain prose with `<h2>`/`<h3>` headings
instead (see the reference article). Two acceptable options for new
articles:

- **Default:** follow the reference article's approach — plain prose under
  a clear `<h2>The rule</h2>` / `<h2>The dates that matter</h2>`-style
  heading. No new CSS needed.
- **If a visually distinct box is wanted** for a particularly
  legal-heavy article, reuse `.callout` with an inline border-color
  override: `<div class="callout" style="border-left-color: var(--accent-alt);">`
  (pier-red, `#c94a3f` — already defined in `:root`) to distinguish it from
  the gold-bordered CTA callout, rather than inventing a new class name.
  Do not add new rules to `assets/css/styles.css` as part of a content
  commit — if a genuine new CSS class is warranted, that's a separate,
  deliberate template-maintenance change, flagged in the run report, not
  silently added.

### 5. High-hedges neighbour law, where relevant

Where a story genuinely touches a neighbour-dispute angle, reference the
Anti-social Behaviour Act 2003 Part 8 high-hedges process (Thanet DC's
£650 complaint fee, 2m evergreen threshold, mediation-first expectation) at
a summary level and link to `high-hedges-neighbour-law-margate.html` for the
full detail rather than duplicating it inline.

### 6. Open Graph image

Every article needs `og:image`. Reuse `https://margatehedges.co.uk/assets/img/og-default.png`
(the shared default already used by every existing article) unless a
genuinely better topic-specific image already exists in `assets/img/` —
don't fetch or invent a new external image URL.

### 7. Growth surface — how this site's how-to section actually grows

This site has **no filter/category JS system** (`how-to/index.html` is a
plain `.grid.grid-2` of cards, not a filterable hub) and **no
`JET-RELATED-GUIDES` comment-block convention** inside article bodies. Do
not invent either as part of routine content work — that would be a
structural change out of scope for nightly ingestion.

The actual growth surface is:

- **`how-to/index.html`** — add a new `.card` inside `.grid.grid-2`, in
  reading order (append at the end is fine; existing cards are not sorted
  by date). Each card needs a `<p class="section-eyebrow">` topic label.
  Reuse one of the existing eyebrow labels where the topic genuinely fits:
  `Rules & paperwork`, `Species & planting`, `Wildlife & the law`,
  `Owners & managers`, `Reductions & renovation`, `Seasonality`. Only
  introduce a new eyebrow label if none of these genuinely fit — note it in
  the run report if you do.
- **`sitemap.xml`** — add the new URL.
- **Footer "Local guides" column** — this is a static, hand-curated
  3-link list on every page (not a growing feed). Leave it alone unless
  explicitly asked to change it; do not treat it as a place new articles
  must be added.
- **In-article cross-links** — where genuinely relevant, add a plain
  `<a href="/how-to/other-article.html">` inline link from the new article
  to 1-2 existing ones (and optionally vice versa) in running prose. There
  is no dedicated "related guides" card section at the bottom of articles on
  this site today; don't add one as a silent structural change — a plain
  in-text link is the existing convention (see how `high-hedges-neighbour-law-margate.html`
  is referenced inline from `hedge-nesting-season-margate.html`'s equivalent
  articles).

## Strong recommendations (P2)

### 8. Structural variation within the story frame

The story-led *opening* is mandatory and constant. What follows it should
still rotate, so 9 story-led articles in a row don't all read identically
after paragraph three:

- **Story → numbered steps (default, ~40%)**
- **Story → month-by-month / calendar** (good fit for timing topics)
- **Story → comparison** (e.g. two species, DIY vs professional, reduction
  vs removal — a plain `<table>` is fine, no existing article uses one yet
  but plain HTML tables are safe within `.prose`)
- **Story → decision points** ("If the hedge is inside the Old Town
  conservation area boundary... If it's outside...")

Never publish three articles in a row with the same post-story shape.

### 9. Video credit (if a video is embedded or cited)

If the article is generated from a YouTube source, credit the creator by
name/channel and link to the original in a short paragraph. Prefer a
UK-based creator/source and techniques that suit Kent's hedge species and
coastal climate.

### 10. Thanet/Margate specificity

Every article should reference something genuinely local: named
neighbourhoods (Old Town, Cliftonville, Westbrook, Garlinge, Northdown, Palm
Bay, Westgate-on-Sea), the Thanet DC conservation-area system, salt-line
coastal exposure, the holiday-let/Airbnb turnover pattern already covered in
`holiday-let-hedge-maintenance-margate-airbnb.html`, or Dreamland/Turner
Contemporary-adjacent seasonality. This is what keeps content local rather
than generic hedge-care copy applicable to any UK town.

## Non-goals

- No cookie banners.
- No `<script>` tags beyond the GA4 gtag snippet and `assets/js/main.js` (if
  the reference article uses it).
- No third-party embeds beyond a single YouTube iframe, if used.
- No author bylines beyond `"Richard Lim"` in JSON-LD and the site's
  existing first-person contractor voice in body copy — no additional named
  authorship, no fake reviewer schema.
- Do not add a `data-howto-cat` filter system, a `JET-RELATED-GUIDES`
  comment block, or an `@graph`/`BreadcrumbList` JSON-LD pattern to
  individual articles as part of routine content work — those are
  sandwichhedges.co.uk conventions, not this site's. If the fleet later
  decides to standardise all 9 ring sites on one JSON-LD/growth-surface
  pattern, that is a deliberate, separate cross-site change, not something
  a nightly content run should introduce unilaterally.
- Do not silently soften or drop the story-led opening requirement. If a
  topic genuinely resists a story frame, use the closest honest
  approximation (a reader-question opener, a recurring-pattern-across-jobs
  opener like the site's existing articles already do) rather than falling
  back to a generic "Learn how to..." hero.

## UK voice and copy rules (fleet-wide, restated here)

- British English (colour, organisation, whilst). Postcode, pavement, tyre.
- **No em-dashes.** Commas, full stops, colons or parentheses instead.
  Hyphens in compound words and en-dashes in ranges are fine.
- No corporate filler: utilise, leverage, seamlessly, best-in-class,
  synergy, robust, cutting-edge, "elevate your outdoor space".
- First-person contractor voice, consistent with existing articles
  ("Every couple of months I get a call from...", "On the fleet, that
  means..."). Confident, current, seaside-modern tone per the site's own
  README ("Turner Contemporary + Dreamland proximity in the language").
- Dates as "22 April 2026" or "late August".

## Adopting this contract

The routine should read this file at the start of every run, plus one
existing article in full (`hedge-nesting-season-margate.html` is the best
single reference: it has the nesting-law detail, the coastal specificity,
and a near-story-led opening already). New articles must satisfy every P1
rule from first ship, and must open story-led — that is this site's one
non-negotiable structural signature within the ring.
