# DESIGN.md — Hoa An Hotel · Cao Bang

Design DNA: **"Clay & Stone"** — SEN structure, Hoa An palette. Adopted from the sibling
project `SEN WEB OTA - main` (2026-07-12): its type system, nav, section rhythm and motion,
re-skinned onto the owner's Adobe Color palette.
Register: **product** (see PRODUCT.md). Mobile-first, guest-facing utility pages, foreign
travelers on patchy data. Personality: phiêu lưu · bản địa · thực dụng.

The lead pair is the owner's explicit choice: **clay `#8A5A4E` + gray-white `#D6DADD`**.
Clay-family carries the dark areas (nav, heroes, drenched sections, CTA bands); gray-white
carries the light areas. The full Adobe palette returns as **accents in meaningful places**
(owner: "website nhiều màu sắc chút chẳng sao"). Committed color, "đậm đà & khỏe khoắn":
heavy type, clay surfaces, no timid tints.

---

## Typography

- **Display / headings:** Bricolage Grotesque, weight **800**, `letter-spacing:-0.02em`, `text-wrap:balance`.
  Used for h1–h4, nav logo, big stat numbers, review quotes.
- **Body / UI:** Hanken Grotesk (400–700).
- Accent italics in headings: a clay-family span (e.g. `--clay-l` on dark, `--clay`/`--clay-deep` on light).
- **Font link (every page):**
  `Bricolage+Grotesque:...500;600;700;800 & Hanken+Grotesk:400;500;600;700`.
- **No serif anywhere** — Playfair / Cormorant / Fraunces / DM Sans / Plus Jakarta are fully retired.

---

## Color tokens

Canonical SEN-DNA names (index.html) — new pages should use these. Sub-pages keep their legacy
names (`--green-dark`, `--orange`, `--cream`, `--or`, `--gm`, `--tm`…) whose **values already equal**
the tokens below; the SEN overlay adds the canonical names on top. Converge names opportunistically.

| Token | Hex | Role |
|---|---|---|
| `--paper` | `#F2F3F4` | body — cool stone near-white |
| `--paper-2` | `#E6E9EA` | alt-section tint |
| `--stone` | `#D6DADD` | palette gray — chips, panels, image placeholders |
| `--surface` | `#FFFFFF` | cards |
| `--ink` | `#26201E` | primary text (13.8:1 on paper) |
| `--ink-soft` | `#625A57` | muted body |
| `--clay` | `#8A5A4E` | THE brand color — CTA bands, on-image, big accents |
| `--clay-deep` | `#70493F` | **text-safe** accent + dark hover (6.7:1) |
| `--clay-soft` | `#A46B5D` | lighter hover |
| `--clay-l` | `#CDABA2` | accent on dark surfaces only (logo peak, active link, hero italics) |
| `--clay-x` | `#F2E2DE` | light clay tint |
| `--anchor` | `#4A3531` | nav bar, trust bar, contact, drenched darks |
| `--anchor-deep` | `#33261F` | footer, darkest bands |
| `--on-dark` / `--on-dark-soft` | `#F2EDEA` / `#D8CCC7` | text on anchor |
| `--moss` | `#557047` | nature accents (balcony/mountain/tours tags) |
| `--gold` / `--gold-deep` | `#DFAE4F` / `#9A7420` | stars on dark / on light |
| `--wa` | `#25D366` | WhatsApp — protected |

`--ease: cubic-bezier(0.16,1,0.3,1)` (ease-out-expo) · `--r-pill:999px` · `--maxw:1140px`.

---

## Signature moves (site-wide)

- **Nav = inverted deep-clay bar, 72px** (`#navbar`, `rgba(74,53,49,0.92)` + `blur(14px)`,
  hairline `rgba(255,255,255,0.12)`). Logo = **mountain-peak SVG** (`.peak`, `--clay-l`) +
  "Hoa An Hotel" in Bricolage 800 white. Links white-85% → white, **active = `--clay-l`**.
  Book CTA = **gray-white pill with clay-deep text** (`#F2F3F4` → `#fff`) — the pair statement.
  Scroll adds a shadow via `.scrolled`.
- **Heads use `.lead`, NOT eyebrows.** A bold Bricolage line + one sentence. A small de-tracked
  kicker (`--clay-deep`, `text-transform:none`) is allowed above a head; **no uppercase-tracked
  eyebrow scaffolding on every section** (that cadence is banned — see Bans).
- **Photo hero** with the scrim recipe: directional gradients + bottom melt into `--paper` +
  white text with `-webkit-text-stroke` + text-shadow (index). Sub-page heroes: clay-gradient
  or photo, Bricolage 800 headline, clay-family italic accent span.
- **`.svc-card` / content cards:** white on light, radius 16px, soft double shadow, photo (4/3)
  with a floating dark-solid chip; hover lifts −5px. Never side-stripe borders.
- **Clay-drenched band** (`--clay`) for review/CTA before the footer; WhatsApp green pops on it.
- **`.reveal`** via IntersectionObserver (+unobserve, no-IO fallback), ease-out-expo, 0.8s.
- Focus ring: `3px solid var(--clay-deep)` offset 3px (or `rgba(138,90,78,0.32)` glow on legacy pages).

---

## Nav architectures (two valid patterns — do not homogenize)

The site runs **two** intentional nav systems. Both share the same color/type language; keep both.

1. **Standard `#navbar` bar** — index, rooms, food, services, bus-ticket, how-to-ride,
   bus/ban-gioc-bus-guide. 72px, collapses to a hamburger drawer at the page's own breakpoint
   (900px on index/rooms/food; **700px** on services/bus-ticket/how-to-ride).
   ⚠️ The element **must** carry `id="navbar"` — a bare `<nav>` gets no styling (latent bug fixed
   2026-07-12 on services/bus-ticket/how-to-ride/bus-guide).
   ⚠️ Never style bare `nav {}` (type selector) for the bar — it also matches `<nav class="foot-nav">`
   in the footer and pins it to the top. **Always scope to `#navbar`.**
2. **Compact `#nav` scrim-drawer** — tours, motorbike. 54px bar, slide-down `.nav-links` drawer
   (`translateY(-110%)`) + `.nav-scrim`, animated `.ham`. CTA is `.nav-cta-sm` (already the
   gray-white pill). Peak icon sized down via `#nav .nav-logo .peak { width:20px }`.
3. **Island nav** — welcome.html only (`.nav-wrap`, floating pill). Deliberately its own thing;
   leave it, it just inherits the fonts/tokens.

## The SEN DNA overlay

Each sub-page carries a `/* ═══ SEN DNA OVERLAY ═══ */` block appended before the first `</style>`:
canonical tokens, `body`/`h1–h4` fonts, `#navbar` spec, `.nav-cta` gray-white pill, `.section-label`
de-track, `.reveal`. Later-rule specificity lets it override the legacy nav without touching content
rules. **Keep the overlay in sync across pages** when the shell changes. The overlay must NOT set
`display`/layout on `.nav-links` in a media query — each page owns its own mobile drawer breakpoint,
and a mismatched breakpoint double-styles the bar (fixed 2026-07-12).

---

## Accent colors (allowed, tie each use to meaning)

- **Moss `#557047`** — nature: balcony/mountain badges, tours & services tile accents, welcome sage
  tokens (`#557047`/`#74906A`/`#DCE3CF`/`#E9EBD9`).
- **Gold** — `#FEDF9E` badge bg + ink text ("Bestseller"); text-safe `#7A5C19` on white;
  star gold `#DFAE4F` (dark) / `#9A7420` (light).
- **Clay-light `#CDABA2`** — logo peak, active nav link, hero italics, footer links on dark. **Never as
  text on light backgrounds.**
- Interactive states: filter chips / tabs **active = clay**, hover = sage tint `#E9EBD9` + moss border.
- Room price badges: gold `#FEDF9E` bg + ink text. Bus badges: Limousine = moss tint, Sleeper = clay tint.
- how-to-ride `.ctrl` cards: moss-tinted (guidance) / clay-tinted (danger) — full border+bg, never side-stripes.

## Protected colors (never retheme)

- WhatsApp green **`#1B9E77`** (teal-green đất; refined 2026-07-12 from the neon `#25D366`, which failed
  white-text contrast at 1.98:1 and clashed with the warm palette). Hover `#168060`, welcome-dark `#116149`,
  glow rgba `27,158,119`. WhatsApp CTAs + float only. Recognisable as WhatsApp, tuned to the clay/gray system.
- motorbike.html semantic boxes: blue `#E3F2FD`/`#1565C0`, amber `#FFF8E1`/`#F57F17`, red `#FCE4EC`/`#C62828`.
- Categorical `DAY_COLORS` in itinerary-builder & itinerary-v2 JS.
- Rating-star gold `#DFAE4F` (dark) / `#9A7420` (light).
- **editor.html** — internal admin tool, keeps its functional palette. Never retheme.

---

## Bans (impeccable · product register)

- Side-stripe accent borders. · Uppercase-tracked eyebrow above every section (AI-slop cadence).
- Em-dash overuse (>2 per view reads as AI cadence — use "·", commas, colons).
- Gradient text. · border + big-shadow pairing. · bounce/elastic easing. · gray text on colored bg.
- Fabricated content (reviews, dates). Only the real Brian · England · Mar 2026 review is used;
  rooms reopening month is unknown → truthful "reopening soon · reserve ahead", no fake date.

## Contrast checkpoints (verified)

- White on clay `#8A5A4E` ≈5.5:1 ✓ · white on anchor `#4A3531` ≈11:1 ✓
- `#CDABA2` on `#4A3531` ≈5.2:1 ✓ (never `#CDABA2` as text on light) · ink/muted on `--paper` ✓
- Every page keeps the `prefers-reduced-motion: reduce` kill-switch.

## Pages still on legacy shell (not yet SEN-DNA)

- `itinerary.html`, `itinerary-v2/itinerary-v2.html`, `itinerary-builder.html`, `pick-coords.html`
  — map/planner tools with `.topnav`; palette already clay+gray, fonts not yet swapped. Do when touched.
