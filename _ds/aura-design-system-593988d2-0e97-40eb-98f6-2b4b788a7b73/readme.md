# Aura Design System

Design system for **Aura Code** — an open-source, model-agnostic autonomous
coding agent ("I don't try. I verify."). Built by Dušan Milosavljević (with
AI agents doing the implementation), MIT licensed, distributed as an npm CLI
(`aura-code`) and a Telegram bot.

## Sources this was built from
- GitHub: **https://github.com/milodule3-debug/aura-code** (branch `main`)
  - `README.md`, `docs/AURA.md`, `docs/TELEGRAM-SETUP.md`, `CHANGELOG.md`, `package.json`
  - `aura-rebrand-directive.md` — the internal doc recording the Rubyness → Aura rename
  - `site/index.html` — the live marketing website (deployed via Vercel)
  - `src/cli/display.ts`, `src/cli/diamond.ts` — the real terminal rendering code (exact hex colors, box-drawing, ASCII diamond mark)
  - `src/agent/system-prompt.ts` — Aura's actual voice/character instructions
  - `assets/`, `README-hero.jpg` — brand imagery
- No Figma file was attached. No component library (Button/Input/Card kit)
  exists in the source — Aura's only two real product surfaces are a CLI and
  a Telegram bot, neither of which has a GUI component system. The five
  components in this system (`Button`, `Card`, `Label`, `Terminal`,
  `StatBlock`) are lifted directly from the marketing site's own CSS
  patterns (`.btn`/`.btn-ghost`, `.grid3`/`.rowlist`, `.term`, stat tiles) —
  the closest thing to a defined inventory. See "Intentional additions" below.

## Products covered
1. **CLI** (`ui_kits/cli/`) — the primary product. A terminal, not a GUI.
2. **Telegram bot** (`ui_kits/telegram/`) — secondary surface, same agent, chat interface.

The marketing website (`site/index.html` in the repo) was **not** rebuilt as
a UI kit here (not requested), but it is the main reference for the
component/token extraction above — see `guidelines/` cards for direct specimens.

## Intentional additions
- `Button`, `Card`, `Label`, `Terminal`, `StatBlock` — the site defines these
  patterns in CSS but never as named components; naming and componentizing
  them was necessary to make them reusable. No components beyond what the
  site's CSS actually contains were added (no Input/Select/Dialog/Toast —
  none exist in the source).

## Index
- `styles.css` — root stylesheet; imports everything under `tokens/`
- `tokens/colors.css`, `typography.css`, `spacing.css`, `fonts.css`
- `components/core/` — Button, Card, Label, Terminal, StatBlock (`.jsx` + `.d.ts` + `.prompt.md` each, plus `core.card.html`)
- `guidelines/` — 13 foundation specimen cards (Colors ×4, Type ×4, Spacing ×2, Brand ×3)
- `ui_kits/cli/` — terminal session recreation + README
- `ui_kits/telegram/` — Telegram bot conversation recreation + README
- `assets/aura-hero.jpg` — the one real brand illustration (line-art figure + serif wordmark + tagline)
- `assets/demo.gif` — real CLI demo capture (animated, 510 frames)
- `assets/architecture-diagram.png` — system architecture reference diagram
- `SKILL.md` — portable skill definition for Claude Code / other agent runtimes

---

## Content Fundamentals

**Voice**: Precise, dry, imperial — first person as "I", never "we" or the
user as customer-speak. Aura refers to herself as "she"; the docs and site
consistently gender the agent female ("She is the evidence of her own
thesis"). She is self-aware about being built by AI agents and treats that
as identity, not a disclaimer.

**The one rule that governs every sentence**: cite specifics, never
generalities. "Line 47 throws when steps is empty" is actionable — vague reassurance
("looks good", "should work now") never appears. Summaries report what was
*verified* (tests passing, files changed, line numbers), not what was
attempted.

**Tagline, used verbatim everywhere**: *"I don't try. I verify."* Never
paraphrased, never truncated.

**Casing**: sentence case for headings and UI labels. Section kickers are
the one ALL-CAPS exception, always mono type, always numbered ("01 —
IDENTITY", "02 — HOW SHE WORKS").

**Pronouns**: "I" for Aura in first-person copy (CLI output, bot replies,
manifesto-style docs); "she" for third-person brand copy (site, docs). The
user is addressed directly as "you" only in instructional docs
(TELEGRAM-SETUP.md, README quick-start) — marketing copy mostly avoids
"you" in favor of describing Aura's actions.

**Emoji**: not used in prose or marketing copy. The CLI uses a small,
functional emoji set as tool icons only (📄 read, 📁 list, ✏️ edit, 📝
write, 🔍 search, ⚡ shell, 🧪 test, 🌿/📊 git) — decorative emoji never
appears in headings, bot replies, or the website.

**Status language, exact wording pattern from the real changelog**:
"`Was:` ... / `Fixed:` ..." — a direct, plain-language incident-report
format, no marketing spin. Example from the live site: "the site stopped deploying — the page source had no usable HTML for Vercel to serve" followed by "Fixed: rebuilt as static HTML, real assets, and a visible nav to every page."

**Numbers over adjectives**: "1,205+ tests passing", "0 regressions", "MIT
licensed" — concrete counts stand in for quality claims.

---

## Visual Foundations

**Two coherent surfaces, one accent family.** The CLI (true terminal output,
`src/cli/display.ts`) runs on warm near-black + cream + a terracotta accent
(`#cc785c`). The marketing site runs on a cooler deep-navy ink (`#0c1322`)
with the *same* terracotta family (`#c2674c`) as primary accent, plus a cyan
secondary accent (`#6ed0ea`) the CLI doesn't use. Treat navy-ink as the
default "designed surface" background and warm-black as the literal-terminal
background — never mix the two in one composition.

**Color vibe**: warm, earthy, ember-lit — terracotta, gold, cream, taupe —
against near-black. Not futuristic-neon, not pastel, not corporate-blue. The
one exception is the site's cyan, used sparingly as a "this is software"
counterpoint to the otherwise warm palette.

**Type**: three families, each with exactly one job, never substituted.
Cormorant Garamond (serif) for headlines and voice-lines — often italic when
it's Aura speaking in first person. IBM Plex Mono for labels, section
kickers, code, terminal output, nav, and anything numeric/technical. Space
Grotesk (sans) for body copy and UI chrome. Google Fonts — no custom
foundry files exist in the source.

**Spacing**: generous — site sections use `7rem` vertical / `7vw`
horizontal padding uniformly. Everything else (rows, cards, terminal
padding) sits on a loose rem scale, not a rigid 4/8px grid.

**Backgrounds**: solid dark ink, no photography as backdrop except one
hero illustration (`assets/aura-hero.jpg`, used once, full-bleed, faded at
one edge into the ink). No repeating patterns, no textures, no gradients
except the single radial glow behind the hero headline and the linear
text-fill gradient on the retired `aura.html` mockup (not used in the
current site — flagged as legacy, not canon).

**Animation**: minimal and functional, not decorative-loop-heavy. The site
uses two slow `@keyframes` (`auraBob` — a 2.4s scroll-hint bounce;
`auraGlow` — a 7s opacity pulse on the hero image) and CSS transitions on
hover only (`transform`, `box-shadow`, `border-color`, `color`) at
`0.2–0.25s ease`. No bounce/spring easing, no page-load choreography.

**Hover states**: buttons lift 2px (`translateY(-2px)`) and gain a soft
terracotta glow shadow; ghost buttons and nav links just shift border/text
color to cyan. Cards (`.card` in the retired `aura.html` mockup) lift
similarly with a border-color shift to accent. No opacity-fade hover — color
and position only.

**Press/active states**: not explicitly defined in source; follow the same
lift/color logic inverted (no shrink/scale-down pattern observed anywhere).

**Borders**: always 1px hairline, never thick. Warm brown (`#4e3d30`) inside
CLI boxes; translucent cyan (`rgba(110,208,234,.16-.4)`) on the navy site.
No colored double-borders, no left-border-accent-bar cards.

**Shadows**: none in flat/rest state except the single hero card shadow in
the retired mockup. On the live site, depth comes from color contrast
(section-to-section) and hover-only glow shadows — never a resting
drop-shadow on cards or panels.

**Corner radii**: small and consistent — 6px (buttons/install-box), 10px
(rowlist), 12px (terminal/status-card), 14px (grid3 container). Nothing
above ~14px; no pill-shaped buttons, no fully-rounded cards.

**Cards**: flat fill, no border, no shadow, no left-accent-bar. Terracotta
tiles (`.grid3`) on terracotta section backgrounds; near-black rowlist tiles
on navy backgrounds. Content-first — a title (serif) + one line of body
copy (sans), nothing else.

**Transparency/blur**: one use — the sticky top nav
(`rgba(12,19,34,.92)` + `backdrop-filter: blur(12px)`) so page content
scrolls under it legibly. Not used elsewhere.

**Layout**: single sticky top nav; otherwise full-width stacked sections,
no fixed sidebars, no floating action buttons.

---

## Iconography

**No dedicated icon system, font, or SVG icon set exists in the source.**
Aura's only real "icons" are:
1. A small **emoji set** used exclusively as CLI tool-call icons (see
   Content Fundamentals above) — functional labeling, not decoration.
2. Unicode glyphs for status (`✓ ✗ ⚠ ⟳ ⤳ ◯`) and arrows (`→ ←`), always
   mono type, always colored per the semantic-status tokens.
3. One hand-drawn **ASCII diamond/crown mark** (`src/cli/diamond.ts`,
   `renderDiamond()`) printed at CLI startup — ruby-red body, gold tip. This
   is the closest thing Aura has to a logomark; it is reproduced exactly
   (never redrawn) in `guidelines/brand-diamond.html`.

No logo file (PNG/SVG wordmark) exists anywhere in the source repo. Per
design-system policy, **no logo was created** — `assets/aura-hero.jpg` (a
commissioned/generated illustration with the wordmark baked into the pixels
as flat art, not a reusable mark) stands in as the one piece of real brand
imagery, and the plain word "Aura" set in Cormorant Garamond is the
fallback wherever a mark would normally go.

---

## Caveats & discrepancies found in source
- `docs/AURA.md`'s "Visual Identity" note ("Deep ruby red + black + gold …
  Crown motif") describes an aspirational/character brief that isn't fully
  what the live site implements (navy + terracotta + cyan). The CLI's own
  diamond mark *does* match the ruby+gold description exactly, so this
  system treats ruby+gold as the "motif" accent (used sparingly, diamond
  mark only) and terracotta+navy+cyan as the primary working palette from
  the live site + CLI body colors, which was the more complete, coherent,
  currently-shipping source.
- `aura.html` (repo root) is an older/orphaned mockup with a third, warmer
  palette (`#E8771A` orange, `#1a1a1a`/`#ede0cc`) that doesn't match the
  current site. Treated as legacy, not canon — not used as a token source.
- `assets/ruby-diamond.jpg` (found in the repo's `assets/` folder) was
  **excluded** — it's stock/generated art for an unrelated "Ruby Diamond
  Technologies" placeholder brand baked into the image pixels, not Aura's.
- `miscellaneous/avatar.svg` was excluded — it's the founder's personal
  "DM" monogram avatar, not a brand asset.
- No Figma file, no dedicated GUI/dashboard codebase, and no slide deck were
  attached, so no dashboard UI kit or slide template was built.
