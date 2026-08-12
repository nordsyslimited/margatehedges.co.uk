# Agent / Contributor Notes

Ground rules for any future AI assistant or human contributor working on this site.

## Stack

- Plain HTML, one shared `assets/css/styles.css`, `assets/js/main.js`. **No build step.**
- Deployed via GitHub Actions FTPS to Krystal shared hosting — `.github/workflows/deploy.yml`
  fires on push to `main`, uploads everything except `.git*`, `node_modules`,
  `README.md` and `assets/partials.html`. This repo already has a working
  deploy pipeline; do not assume a manual-FTPS fallback is needed.
  - FTP creds live in the repo's GitHub Actions secrets (`FTP_USER`,
    `FTP_PASS`), not in this repo. A local reference copy for manual/
    emergency FTPS, if ever needed, is expected at
    `~/.claude/secrets/margatehedges-ftp.env` (confirmed present on Jet's
    chassis 2026-08-12) — check `~/.claude/secrets/` for the exact filename
    before assuming its shape; do not commit credentials to this repo.
- Contact form posts to `/contact-submit.php` (server-side PHP, sends via
  Resend). Config template in `config/secrets.example.php`; the real
  `config/secrets.php` is git-ignored / generated on deploy. **Unlike
  sandwichhedges.co.uk (FormSubmit.co), this site's form is PHP+Resend —
  don't port the FormSubmit pattern here.**

## Ring context

This site is one of 9 sister sites in a Kent "hedge ring":
broadstairs/canterbury/deal/dover/margate/ramsgate/thanet/wingham/sandwich
hedges. Same business model and underlying HTML/CSS plumbing, different
towns, deliberately different structural angle per site to avoid a
templated-content signal across sister domains on the same search results.
**This site's assigned angle is case-study / story-led** — every how-to
article opens with a short real-feeling job scenario before the practical
detail. See `TEMPLATES/how-to.md` for the full contract; do not copy another
ring site's template file verbatim, each site's conventions differ
genuinely (JSON-LD shape, growth surface, CSS classes all differ between
this site and sandwichhedges.co.uk, for example).

## Branding

- Palette: sand `#f0e6d2`, cream `#faf5ea`, deep ink `#1a2a35`, sun-teal
  `#4a8b8f` (`--accent`), pier-red `#c94a3f` (`--accent-alt`), sun/gold
  `#e6b64c` (`--sun`). Full variable list in `assets/css/styles.css` `:root`.
- Fonts: Playfair Display 700 (headings/brand/lede) + Work Sans 400/500/600
  (body/UI), Google Fonts.
- Logo/favicon: inline SVG data-URI (dark ink circle, gold sun, cream wave)
  — reuse verbatim, do not regenerate.
- Strapline: "Salt-hardened. Seaside-sharp." — topbar and footer.
- Tone: confident, current, seaside-modern. Turner Contemporary / Dreamland
  proximity in the language (per `README.md`).
- Sister site relationship: same ring-plumbing family as the other 8 hedge
  sites, deliberately distinct palette/voice/structure per town — do not
  clone another ring site's visual style or template.

## Writing style

- British English (colour, organisation, whilst). Postcode, pavement, tyre.
- First-person contractor voice ("Every couple of months I get a call
  from...") — a working contractor, not a national chain.
- **No em-dashes.** Commas, full stops, colons or parentheses instead.
  Hyphens in compound words and en-dashes in ranges are fine.
- No corporate filler: utilise, leverage, seamlessly, best-in-class,
  synergy, robust, cutting-edge.
- Dates as "22 April 2026" or "late August".
- Local detail earns its place: named neighbourhoods (Old Town, Cliftonville,
  Westbrook, Garlinge, Northdown, Palm Bay, Westgate-on-Sea), Thanet DC
  conservation areas, salt-line coastal exposure, holiday-let/Airbnb
  turnover patterns.

## SEO and AI search baked in

Every page must carry:

- Unique `<title>`, `<meta name="description">`, `<link rel="canonical">`.
- Open Graph (`og:type`, `og:image` + dimensions, `og:title`, `og:description`,
  `og:url`) + `meta name="robots"`.
- `<html lang="en-GB">`.
- GA4 tag `G-53100B6S34` (real property ID — the `G-MARGATE-PLACEHOLDER`
  string in `README.md` is stale/superseded, every live page already
  carries the real ID; don't "fix" pages back to the placeholder).
- JSON-LD, per page type:
  - `how-to/*.html` articles: a flat `Article` object (not `@graph`, not
    `HowTo`) — see `TEMPLATES/how-to.md` §2 for the exact established shape.
  - `how-to/index.html` hub: separate, different `@graph` pattern
    (`CollectionPage` + `BreadcrumbList`) — this is intentionally
    inconsistent with the individual articles; that's the existing site
    convention, not a bug to fix as part of content work.
- `robots.txt` / `sitemap.xml` — update `sitemap.xml` whenever a page is
  added or removed; this repo has no build step, nothing does this
  automatically.

## How-to pattern

See `TEMPLATES/how-to.md` for the full nightly-routine contract. This is a
**new** file as of 2026-08-12 — this site had no nightly pipeline before
today. The 9 existing hand-authored articles in `how-to/` are the reference
implementation for markup shape; `hedge-nesting-season-margate.html` is the
single best reference (nesting-law detail, coastal specificity, closest to
story-led already).

Summary for any hand edit:

1. Story-led opening (this site's house style — see TEMPLATES/how-to.md).
2. Page hero with `.meta` line ("← All guides · [Topic] · Updated Month
   YYYY"), `<h1>`, `.lede`.
3. Practical/legal detail (rotates: numbered steps / calendar / comparison /
   decision points — never the same shape 3 articles running).
4. WCA 1981 nesting-season reference wherever cutting timing is discussed.
5. Closing `.callout` CTA box back to `contact.html`.
6. Flat `Article` JSON-LD (not `@graph`, not `HowTo`).
7. New card added to `how-to/index.html`'s `.grid.grid-2` with a
   `.section-eyebrow` topic label reusing an existing category where it
   fits.

## Contact form rules

- Posts to `/contact-submit.php` (PHP, sends via Resend). Redirects to
  `thanks.html` on success.
- Do not switch this to FormSubmit.co or any other provider as part of
  unrelated content work.

## What not to do

- No frameworks (React, Vue, Tailwind, Next, etc.).
- No build step. No npm dependencies.
- No tracking scripts beyond the existing GA4 tag, without asking first.
- No third-party chat widgets.
- Do not clone another ring site's look or template file verbatim.
- Do not add author bylines beyond `"Richard Lim"` (JSON-LD `author`) and
  the existing first-person contractor voice.
- Do not invent a `data-howto-cat` filter system or a `JET-RELATED-GUIDES`
  comment-block convention on this site — those belong to sandwichhedges.co.uk,
  not here. See `TEMPLATES/how-to.md` §7 for this site's actual growth
  surface.
- Do not add new CSS classes (e.g. a `.callout--warn` variant) to
  `assets/css/styles.css` as a silent side effect of a content commit — flag
  it in the run report instead; template-maintenance changes are deliberate
  and separate from nightly content shipping.
