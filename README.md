# margatehedges.co.uk

Local hedge-trimming site for Margate and the Thanet coast.

## Stack
Plain static HTML. No framework. No build step.

- `index.html` — homepage
- `services/` — 4 service pages (cutting, reduction, removal, planting)
- `areas/` — coverage landing (Old Town, Cliftonville, Westbrook, Garlinge, Northdown, Palm Bay, Westgate-on-Sea)
- `how-to/` — hand-authored locally-grounded guide articles (organic-draw layer): Margate CA rules, salt-tolerant species, nesting-season on Thanet coast. More to come.
- `jobs/` — JSON-driven recent-jobs feed (`jobs.json` is the source of truth; append new entries to the top)
- `contact-submit.php` — form handler, posts to Resend (config in `config/secrets.php`, template in `config/secrets.example.php`)
- `assets/css/styles.css` — sun-bleached-sand / sun-teal / pier-red palette + Playfair Display + Work Sans typography
- `assets/partials.html` — reusable HTML fragments (header / footer / topbar) for hand-copying into new pages

## Identity
- **Palette:** sand `#f0e6d2`, cream `#faf5ea`, deep ink `#1a2a35`, sun-teal `#4a8b8f`, pier-red `#c94a3f`, sun `#e6b64c`.
- **Typography:** Playfair Display 700 (headlines, brand), Work Sans 400/500/600 (body, UI).
- **Tone:** confident, current, seaside-modern. Turner Contemporary + Dreamland proximity in the language.

## Analytics
No Google Analytics. Visit counting is NordAnalytics (first-party, cookieless): `/assets/js/analytics.js`, included at the end of every page.

## Deploy
TBC — Krystal cPanel FTPS via a dedicated `margatedeploy` FTP user (to be provisioned per the 3dbee UAPI pattern).

## Fleet consistency
Shares HTML skeleton, service categories (cutting / reduction / removal / planting), JSON-LD schema pattern, jobs feed pattern and header/footer structure with the other Kent-ring sites. Content, palette, typography and tone are distinct per town — the ring is 5 different businesses on shared plumbing, not one brand five times.

## Content sources
Research brief for Margate is in the launch project spec (Thanet DC CAs, salt-line species matrix, Manston Road HWRC / Richborough waste routes, Thanet Coast SSSI &amp; Pegwell Bay Ramsar flags, Cliftonville / Westbrook / Garlinge neighbourhood notes, seasonality curve for holiday-let turnover).
