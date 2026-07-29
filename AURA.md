# Aura Standing Rules

## Surfaces
This repo is the marketing site for Aura Pulse. `index.html` is the
website. `README.md` is the repo page. They are different surfaces
and a change to one does not change the other.

When the request says website, site, page or landing page, edit
`index.html`. When it says repo, readme or github, edit `README.md`.
Putting an image "in the repo" means commit it to `assets/` and
reference it from `README.md` — it never means adding it to
`index.html`. Removing an image "from the website" means deleting
the `<img>` from `index.html`; it does not mean deleting the file
from `assets/`, which the README may use.

Committing an asset and displaying it are two separate steps. Do
only the one asked. Never mirror an edit onto the other surface to
be helpful. If you cannot tell which is meant, stop and ask.

## This repo is not the app
`DusanCar-sudo/aura-pulse` is the actual desktop application. This
repo holds only its marketing page. A request about Aura Pulse the
app belongs in that repo. Do not add app code here, and do not edit
marketing copy there.

## Design system is vendored
`_ds/aura-design-system-*/` is a vendored bundle. Restyle through
the token files in `tokens/` rather than editing `_ds_bundle.js`.
`tweaks-panel.jsx` is standalone and not wired into `index.html`.

## Build and branch
No build step. Serve with `python3 -m http.server 8000` or
`npx serve .`. The default branch is `master`, not `main`.

## Secrets
Never inline a token into a shell command. Use `gh` or an env file.
