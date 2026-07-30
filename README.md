# ⚡ Nymbus - Username Forge

> A single-file, 100% offline generator for usernames, passphrases, and identities — no backend, no build step, no accounts, no tracking.

![No Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Offline](https://img.shields.io/badge/offline-100%25-blue)
![Stack](https://img.shields.io/badge/stack-HTML%2FCSS%2FJS-yellow)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange)

Nymbus is a single HTML file that runs entirely in your browser and turns a curated 4,600-word dictionary into usernames, secure passphrases, gamer tags, throwaway handles, D&D rosters, and more. Every generator, every setting, and every scrap of history it keeps lives on your machine — there's no server to talk to, so there's nothing to leak.

> 💡 **Add a screenshot or GIF here** — it's the single highest-impact thing missing from this README. Drop one in a `docs/` folder and reference it above, e.g. `![Nymbus screenshot](docs/screenshot.png)`.

## Table of Contents
- [Getting Started](#getting-started)
- [Features](#features)
  - [Generation modes](#generation-modes)
  - [Specialty tools](#specialty-tools)
  - [Formatting and customization](#formatting-and-customization)
  - [Word database](#word-database)
  - [Platform and vibe presets](#platform-and-vibe-presets)
  - [Personalization and quality of life](#personalization-and-quality-of-life)
  - [Data management](#data-management)
  - [Email pairing](#email-pairing)
  - [Privacy, storage and security](#privacy-storage-and-security)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Browser Support](#browser-support)
- [Contributing](#contributing)
- [License](#license)

## Getting Started

Nymbus has no dependencies and no build step — it's one HTML file.

**Just open it**
1. Download or clone this repository
2. Open the `.html` file directly in any modern browser (double-click it, or drag it into a browser window)

```bash
git clone https://github.com/<your-username>/Nymbus-Username-Forge.git
cd Nymbus-Username-Forge
```

**Serve it locally** *(optional — not required)*
```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

**Host it**

Because Nymbus is fully static, it deploys as-is to GitHub Pages, Netlify, Vercel, or any static host. For GitHub Pages specifically: rename the main file to `index.html`, then enable it under **Settings → Pages → Deploy from a branch**.

## Features

### Generation modes
Four distinct ways to build a result, switchable from **Settings → Format**:

| Mode | What it does |
|---|---|
| **Usernames** | `Word` `Word` `Word` + digits, fully configurable — the default mode |
| **Passphrases** | 3–6 dictionary words strung together for a memorable, high-entropy secret |
| **Random** | Fully random characters (not dictionary words) from a configurable charset, 4–40 characters long — good for throwaway signups you'll never need to remember |
| **Constructed** | An entirely invented, pronounceable word built from an onset + vowel + coda syllable grammar (2–5 syllables, soft/balanced/harsh) — no dictionary lookup, so near-zero collision risk |

### Specialty tools
Beyond standard batch generation, the **Generate** tab includes seven more focused tools:

- **Gmail dot-trick** — Gmail ignores dots in the local part of an address, so this generates look-different variants of your own address that all land in the same inbox
- **Seeded / deterministic** — type a seed phrase and a site name and get the exact same username back every time for that pair, computed live from a tiny deterministic PRNG. Nothing here is ever saved, not even locally
- **Style match** — paste a username you like; Nymbus detects its casing, separator, and digit pattern, applies it to your Format settings, and generates a fresh batch in the same style
- **Compare & score** — drop in up to 3 usernames to see length, character mix, an estimated strength in bits, pronounceability, and how each fits every platform preset
- **Fallback variants** — that username's taken? Paste it in for a batch of close alternatives: leetspeak swaps, case variants, reordered word segments, and digit tweaks
- **Aesthetic text styles** — turn any text into 12 Unicode display styles (Bold, Italic, Bold Italic, Script, Double-Struck, Fraktur, Monospace, Fullwidth, Circled, Small Caps, Upside Down, Strikethrough) for bios and display names — most platforms won't accept these as the actual handle, so check first
- **Group / party generator** — generate a themed, guaranteed-unique roster of 2–30 names in one click: a clan, a D&D party, a team

### Formatting and customization
Every mode shares a deep settings surface:

- **Word count** — 1–4 words for usernames, 3–6 for passphrases
- **Case style** — Title Case, camelCase, UPPERCASE, lowercase
- **Separator** — none, underscore, hyphen, dot (plus space, for passphrases)
- **Digits** — 0/1/2/3/4 presets or a custom count up to 10, placed at the start or end (0 digits requires at least 2 words, to keep results distinct enough)
- **Symbols** — 0–3 random symbols from `!@#$%^&*-_=+?`, for passphrases
- **Word linking** — *Alliterate* keeps every word starting with the same letter; *Rhyme* keeps their endings close, for memorable combos like "Silent Shadow"
- **Portmanteau blend mode** — fuses words at their longest shared letters instead of concatenating them (Wolf + Forest → Wolforest)
- **Pronounceable-only filter** — skips words with awkward consonant clusters
- **Custom word slots** — lock any individual word position and leave the rest random
- **Gamer-tag affixes** — `xX` / "The Real" / "Official" prefixes; `Xx` / `_TTV` / `_YT` suffixes (combine `xX` and `Xx` for the full wrap: `xXShadowWolf42Xx`)
- **Live preview** plus an entropy-based strength meter that updates as you tune settings

### Word database
16 hand-curated categories, 4,600 words total (4,487 unique), selectable individually or combined, with optional weighted picking so some categories show up more often than others:

| Category | Words | Category | Words |
|---|---:|---|---:|
| Nature | 415 | Mythology | 270 |
| Animals | 402 | Sports | 257 |
| Food | 373 | Music | 256 |
| Places | 356 | Space | 245 |
| Emotions | 336 | Colors | 222 |
| Technology | 320 | Professions | 208 |
| Fantasy | 305 | Weather | 190 |
| Elements | 271 | Vehicles | 174 |

Category selection only applies to **Usernames** and **Passphrases** — Random and Constructed modes build words a different way and ignore it. You can also **import your own word list** as an additional category (paste comma- or newline-separated words in Settings) and maintain a **blocklist** of words that should never appear.

### Platform and vibe presets

**Platform presets** apply the right length and character constraints for wherever you're signing up:

| Platform | Limit |
|---|---|
| Twitter / X | 15 characters |
| Discord | 2–32 characters |
| Instagram | 30 characters |
| Twitch | 4–25 characters, letters/numbers/underscore |
| Reddit | 3–20 characters |
| Steam | 32 characters |
| Minecraft | 16 characters, letters/numbers/underscore only (forces an underscore separator) |
| Custom | Set your own max-length override |

**Vibe presets** are one-tap mood bundles — category mix + case + separator + digit style together: 🌾 Cottagecore, 🌆 Cyberpunk, 🕯️ Dark Academia, 🏴‍☠️ Pirate, 💿 Y2K.

### Personalization and quality of life
- **Identicons** — a small, deterministic SVG avatar (GitHub-identicon-style 5×5 mirrored grid) generated per username from a string hash — no network request, no Gravatar
- **Near-miss collision warning** — flags a new result that's only a 1–2 character edit away from something already sitting in your history or favorites
- **Pronunciation playback** — hear any result read aloud via the browser's native Web Speech API
- **Global search** — press `/` anywhere to jump straight to the search bar
- **Theme toggle** — AMOLED black (default) or light

### Data management
- **History** — every username generated this session, newest first, with bulk select / favorite / copy / remove and export
- **Favorites** — star anything to save it, filter by tag, bulk actions, export
- **Statistics** — totals generated, possible combinations for your current settings, duplicates avoided, session timer, and a category-usage breakdown
- **Export formats** — TXT, CSV, or JSON, shared by the Download button and by History/Favorites export
- **Session save/load** — export your entire session (history, favorites, blocklist, settings) to a JSON file and reload it later, fully offline
- **Batch import** — paste an existing list of usernames (one per line, comma-separated, or a JSON array) straight into Favorites

### Email pairing
Pair each generated username with an email variant:
- **Plus-addressing** — `you+GeneratedName@example.com`, which lands in your normal inbox on Gmail, Outlook, Yahoo, iCloud, ProtonMail, FastMail, and most providers that support the `+` convention (some signup forms reject `+` in emails)
- **Custom domain** — swap in any domain you own with catch-all mail configured; a handful of major-provider domains are offered as look-only previews

### Privacy, storage and security
- **Zero network calls** — there is no `fetch`, `XMLHttpRequest`, external script, or CDN import anywhere in the file. Nothing you generate ever leaves the browser
- **Auto-save is opt-in and off by default** — off means nothing is stored anywhere and everything is lost on refresh; turning it on saves history, favorites, blocklist, and settings locally, on-device only
- **Optional encrypted backups** — session exports can be password-protected with AES-256-GCM, keyed by PBKDF2-SHA-256 at 250,000 iterations, using the browser's native Web Crypto API with a fresh random salt and IV every time. Unencrypted backups never include your paired email address — only encrypted ones do

  > Nymbus uses standard, well-vetted browser cryptography rather than a custom cipher, but the project hasn't undergone a formal security audit — keep that in mind for highly sensitive use cases.

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `/` | Focus the global search bar |
| `Esc` | Close the mobile sidebar |

## Tech Stack
- Vanilla HTML, CSS, and JavaScript — no framework, no bundler, no transpiler
- Zero external dependencies, zero CDNs, zero web fonts
- Native Web APIs only: **Web Crypto** (`SubtleCrypto`) for encryption, the **Web Speech API** (`speechSynthesis`) for pronunciation, and the **File API** for import/export
- ~5,200 lines in a single self-contained file (~290 KB)

## Project Structure
Currently a single self-contained file:
```
Nymbus-Username-Forge/
└── nymbus-username-forge.html   # markup, styles, and logic — everything
```
For GitHub Pages, rename it to `index.html` at the repo root.

## Browser Support
Any modern evergreen browser (Chrome, Edge, Firefox, Safari) runs Nymbus fully. Two features rely on optional Web APIs and degrade gracefully if they're unavailable:
- **Pronunciation playback** needs `window.speechSynthesis` — Nymbus shows a toast instead of failing silently if it's missing
- **Encrypted session backups** need `window.crypto.subtle`, standard in modern browsers served over `https://` or from `localhost`

## Contributing
Contributions, bug reports, and word-list suggestions are welcome.

1. Fork the repo
2. Create a branch: `git checkout -b feature/my-idea`
3. Make your change in the HTML file — it's organized with clear banner comments (`WORD DATABASE`, `RANDOM MODE`, `SETTINGS CONTROLS`, etc.) to make sections easy to find
4. Open a pull request describing what changed and why

A few ideas if you're looking for a starting point: more platform presets, more vibe presets, additional word categories, or an export option beyond TXT/CSV/JSON. These are suggestions, not a committed roadmap.

## License
Choose and add a license file if you haven't already — [MIT](https://choosealicense.com/licenses/mit/) is a common, permissive choice for a small standalone tool like this. Until a license is added, all rights are reserved by default, which means others can't legally reuse or modify the code even though the repo is public.

---

Built entirely with vanilla web technologies — no trackers, no telemetry, no accounts required.
