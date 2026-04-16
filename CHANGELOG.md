# Pastel Whimsy — Changelog

This changelog documents significant changes only — new features, architectural decisions, complete refactors, and new companion skins. Individual CSS tweaks, rule refinements, and minor mobile adjustments are not logged.

---

## V2.1.0 — Mobile Add-on (current)
**Released:** April 16, 2026

### Mobile Add-on

First release of the companion mobile stylesheet (`style_mobile.css`). See the Mobile Add-on section below for full details.

### Stylus Font Loader

Added `stylus_fonts.css` — a one-file Stylus browser extension stylesheet that loads Lora, Playfair Display, and JetBrains Mono on AO3. AO3's skin system strips `@font-face` and external font imports for security reasons; Stylus bypasses this by injecting CSS at the browser level. Without this file the skin falls back to Palatino/Georgia.

First release of the companion mobile stylesheet.

### Mobile Add-on — detail

Matches AO3's own media CSS breakpoints:
- `≤ 62em` — tablet / landscape phone (same as AO3's `25-media-midsize.css`)
- `≤ 42em` — portrait phone (same as AO3's `26-media-narrow.css`)
- `≤ 30em` — very small phones

### ≤62em rules

- Overflow containment: `html`, `body`, `#outer` — `overflow-x: hidden`, `max-width: 100%`
- `#main` — explicit `padding-left/right: 3.5%` with `!important` to survive our desktop overrides
- Header search hidden — too cramped on mobile
- User avatar icons — scaled down to 40px, decoration stripped, simple 1px accent border on image only
- Required-tags icon block — `transform: scale(0.7)` to reduce visual size without breaking the absolute-positioned 2×2 grid
- Blurb header: `padding-top: 44px` to clear scaled icon block; `.blurb .header .heading` and `.blurb .header ul` — both margins zeroed to give full card width
- Datetime — changed from `position: absolute; right: 0` to `position: static; float: right` to stop it overflowing the card edge
- Stats — `float: none` to stop overflowing right
- Tags — `white-space: normal` on `a.tag` + `display: inline-block` so pills wrap to next line as units; extremely long tags break within the pill rather than overflowing
- Index group containers — `overflow: hidden; box-sizing: border-box` to prevent overflow on series/bookmark/collection pages
- `div.preface` side margins zeroed — AO3's `margin: 1.5em 3em` was making summary/notes very narrow
- Dashboard: card borders stripped from `ul:not(.hidden)` (`:not(.hidden)` required so the pseuds dropdown stays closed); `display: inline-block` on `li` and `a`
- Footer modules stacked vertically — overrides AO3's `#footer .module { max-width: 20% }`
- Reduced padding on blurbs, work meta, fieldsets, kudos, splash modules
- Heading sizes reduced slightly (h1 1.35em, h2 1.15em, h3 1.05em)
- Filtered layout (`.filtered .index` / `.filtered#dashboard`) reset to `float: none; width: 100%` — our desktop 74%/24% widths override AO3's own narrow reset without `!important`

### ≤42em rules

- Filtered layout and inbox stacked to single column
- Heading sizes reduced further (h1 1.2em, h2 1.1em, h3 1em)
- Workskin heading sizes: h1 1.5em, h2 1.3em, both with `line-height: 1.4`
- Workskin h3 `line-height: 1.4` for multi-line chapter titles
- Card, comment, inbox item padding tightened (0.6em)
- Buttons/action links — `font-size: 0.85em`, tighter padding
- Tags — `font-size: 0.85em`, tighter padding
- `dl.meta` padding reduced
- Custom scrollbar hidden (irrelevant on touch)

### ≤30em rules

- Minimum heading sizes (h1 1.1em, h2 1em, h3 0.95em)
- Workskin fic title minimum (1.15em)
- Maximum tightening on card padding (0.5em)
- Box-shadows removed on blurbs, comments, work meta, kudos, notices

---

## V2.0.0
**Released:** April 16, 2026

### Architecture

- Ported from a single flat stylesheet to a structured 15-section base-theme architecture with a full table of contents and sub-section headers throughout
- Introduced a `:root` CSS variable system — 44 variables across 3 groups (backgrounds/borders, accent colours, extended palette) with 341 `var()` usages. Change the palette by editing one block only
- Rule count grew from 161 (V1) to 293
- Added companion mobile add-on skin (`style_mobile.css`) with three breakpoints: ≤62em, ≤42em, ≤30em
- V1 had 1 variable usage; V2 has 341, giving consistent colour inheritance across all rules

### Typography

- Body font changed from Verdana stack → **Lora** (serif) with Palatino/Georgia fallbacks
- Heading font changed to **Playfair Display** with serif fallbacks; font applied explicitly to buttons, inputs, and other elements AO3 resets to system fonts
- Per-level heading colours: h1 soft purple, h2 medium purple, h3 hot pink, h4 teal, h5 periwinkle, h6 dark purple-grey
- Button/link text colour changed from grey-dark to deep purple `#5e3f8c`
- Header nav and greeting links given `font-weight: 500`
- Heading decorative accent bars removed — were firing too broadly across the site including header and footer

### Work Page

- Fic title (`h2.title`) — gradient text `purple→pink→blue`, italic, centred
- Full heading hierarchy for user-written fic content (h1–h6), each with a distinct gradient
- Work meta block — three-stop diagonal pastel gradient background
- Author byline — `by` prefix injected via `::before`, bold author name, normal-weight "by"
- Summary and notes blockquotes — left-border accent with pale pink gradient background (work page only, not blurbs)
- Kudos section — pink→mint gradient background
- Work navigation — background cleared
- `#workskin hr` — transparent→pink→purple→mint→transparent gradient, 80% width, centred

### Blurb Cards

- Work titles — gradient text `purple→pink→blue`; visited state uses muted version; hover resets to mint→pink background
- News and blurb title hovers — pink→mint (news) and mint→pink (blurbs) gradients with word-length bottom borders
- Blurb layout: AO3's `.blurb .header .heading` and `.blurb .header ul` both receive `margin: 0.375em 5.25em 0 65px` — we preserve this rather than overriding it, to avoid breaking the required-tags icon offset

### Tag System

- Per-category tag colours with matching hover states: fandom=mint, relationship=sky blue, character=pink, rating=yellow, freeform=blue, warning=purple-pink
- `white-space: nowrap` on all `a.tag` so pills never break mid-word
- "Show additional tags" / "Show warnings" links — `white-space: nowrap !important` so they never break mid-phrase
- Fandom tags — `display: inline-block; margin-bottom: 0.2em` for consistent row spacing

### Header

- Search box — gradient and inset shadow removed; plain white input
- Search button — retains gradient pill styling explicitly

### Dashboard & Sidebar

- Sidebar covers both `div#dashboard` and `nav#dashboard` element types
- News page sidebar — alternating pale purple tint on odd items + bottom border separators
- News admin dashboard — hover gradient and current-item styles matching profile dashboard
- Dashboard current item — mint background, no border
- Dashboard `ul` groups — card styling (border, border-radius, gradient) applied on desktop

### Inbox

- Comment items styled as blurb cards — card gradient, rounded corners, shadow
- Unread items — pink-tinted card
- Byline — purple→mint gradient header strip
- Unread badge — pink→purple pill; replied indicator — teal
- Inbox layout fixed — the inbox page lacks AO3's `.filtered` class; additionally `07-interactions.css` sets `.dashboard > form { width: 100% }`. Fix: explicitly float `form#inbox-form` and `ol.pagination` left at 75%, and `form#inbox-filters` right at 24%

### Footer

- Gradient changed from card→warn to pale purple→soft pink
- Menu card backgrounds — pale lavender→pink
- Footer links and buttons — pill styling removed, plain text

### New Pages Styled (not in V1)

- **News page** — article cards, heading link hovers
- **Reading history** — last visited text italic, smaller, muted purple-grey
- **Statistics page** — alternating row gradients
- **Inbox** — full card treatment, correct two-column layout
- **System pages** (login, skins) — card background on `#main`
- **State indicators** — `.own`, `.draft`, `.unread`, `.child`, `.unwrangled`, `.unreviewed` each get a distinct subtle tint
- **Front page** — Find Your Favorites module (card, gradient tag pills, glow heading), Unread Messages module (pink-tinted comment cards), Is It Later Already? module (mint card); site title styled with Playfair Display italic, hot pink, purple glow
- **Work/Bookmark/Tag/People search pages** — fieldsets card-styled, input widths 100%, legend in Playfair Display; outer form border stripped

### Notices & Alerts

- `.notice`, `.caution`, `.error` — gradient cards with colour-coded borders and text

### Misc Fixes

- `body { overflow-x: hidden }` — prevents page-wide horizontal shift caused by `background-attachment: fixed` triggering a layout shift when the scrollbar appears/disappears
- `body { text-align: left }` — removed `!important` to allow child centering (fic title, preface)
- `.wrapper { box-shadow: none }` — overrides AO3 default grey shadow
- `div.preface` selector in preface centering rule — tightened to `#workskin` only, was centring text in blurb summaries globally
- Stray bare `color: var(--clr-primary-visited)` property outside any rule block — removed
- CSS variable audit — 18 new variables added covering repeated accent colours and shadows; `--icon-border1` (unused) removed

---

## V1.0 (original)
**Released:** February 6, 2026

- Single-file stylesheet, 161 rules, 1 CSS variable usage
- Fonts: Verdana stack (body), system serif (headings)
- Basic colour overrides — purple and pink palette
- Limited page coverage — primarily work page and blurb cards
- Zerafina icon replacements included