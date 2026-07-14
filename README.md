# Aura Pulse Website

**Marketing site for Aura Pulse — the Tron-grade system telemetry desktop app.**

A static single-page site (HTML + inline React) built on the Aura design system. Showcases Aura Pulse's features: system telemetry, AI clipboard vault, hardware benchmarks, and the optimization engine.

Built by Dušan Milosavljević (Lean Progress IQ). Companion to the [aura-pulse](https://github.com/DusanCar-sudo/aura-pulse) desktop app.

![Status](https://img.shields.io/badge/status-live-success)
![Aura](https://img.shields.io/badge/Aura-Design%20System-purple)

## Quick Start

This is a static site — open `index.html` directly, or serve with any HTTP server:

```bash
# Python
python3 -m http.server 8000

# Or Node
npx serve .

# Or simply
xdg-open index.html
```

## Files

- `index.html` — single-page marketing site (inline React via CDN + Babel)
- `tweaks-panel.jsx` — React component source for the tweaks panel
- `assets/` — hero image, feature screenshots (diagnostics, optimization, vault)
- `_ds/` — Aura Design System bundle (tokens, fonts, components)

## Features

- **Single-page design** — everything in `index.html`, no build step required
- **React 18 via CDN** — uses `@babel/standalone` for in-browser JSX transform
- **Aura Design System** — consistent tokens (colors, typography, spacing)
- **Hero image + feature shots** — `aura-hero.jpg`, `shot-diagnostics.png`, `shot-optimization.png`, `shot-vault.png`
- **Screenshot showcase** — diagnostics, optimization engine, and AI vault UI

## License

MIT — see [LICENSE](LICENSE).

## Author

Built by **Dušan Milosavljević** — see [OWNERSHIP.md](OWNERSHIP.md).
