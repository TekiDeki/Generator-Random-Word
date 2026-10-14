# LexiGen · Random Word Generator

A small, **single-file, zero-dependency** word generator for writing prompts, language practice and creative ideas. No account, no analytics, no tracking, no backend.

**[Open LexiGen](https://tekideki.github.io/Generator-Random-Word/)** · [Apache-2.0](LICENSE) · [Support with a coffee](https://paypal.me/TekiDeki)

## Features

- **10 languages:** English, Română, Srpski Latin, Српски Cyrillic, Deutsch, Français, Italiano, Español, Português and Nederlands.
- Built-in lists totaling **2,763 distinct word/type/rarity entries** after removing seven exact duplicate entries in memory. These are curated lists, not comprehensive dictionaries or externally validated frequency rankings.
- Filter by maximum length, short words (≤5 characters), long words (≥9), or the list's editorial “rare” flag. Filters are combined with the length limit and are never silently bypassed.
- Copy a word; if clipboard access is denied, the app selects the word and asks you to copy manually instead of falsely reporting success.
- Last 12 generated words per language, native keyboard-accessible history buttons, and a confirmed clear-history action.
- Language, filter, maximum length and light/dark theme preferences are saved locally when browser storage is available.
- Responsive layout, visible focus, reduced-motion support, translated donation/credits and accessible language names.
- Installable PWA, local icon set and offline app shell after a successful online visit.
- **No CDN, external fonts, icon library, npm, framework or build step required.** All app logic, CSS and word lists are in `index.html`; accompanying files provide PWA, metadata and documentation.

## Languages and links

| Language | Open |
|---|---|
| English | [EN](https://tekideki.github.io/Generator-Random-Word/) |
| Română | [RO](https://tekideki.github.io/Generator-Random-Word/?lang=ro) |
| Srpski Latin | [SR](https://tekideki.github.io/Generator-Random-Word/?lang=sr-Latn) |
| Српски Cyrillic | [СР](https://tekideki.github.io/Generator-Random-Word/?lang=sr-Cyrl) |
| Deutsch | [DE](https://tekideki.github.io/Generator-Random-Word/?lang=de) |
| Français | [FR](https://tekideki.github.io/Generator-Random-Word/?lang=fr) |
| Italiano | [IT](https://tekideki.github.io/Generator-Random-Word/?lang=it) |
| Español | [ES](https://tekideki.github.io/Generator-Random-Word/?lang=es) |
| Português | [PT](https://tekideki.github.io/Generator-Random-Word/?lang=pt) |
| Nederlands | [NL](https://tekideki.github.io/Generator-Random-Word/?lang=nl) |

A supported URL language overrides the saved preference, which overrides the browser language. English is the fallback. Language switching updates the URL, HTML language, visible labels, document title, description, canonical URL and social metadata. The app does not put your history or chosen word in the URL.

## Install / offline / local use

Use the live HTTPS app. Supporting Android/desktop browsers may show an install option; an in-app **Install app** button appears only when the browser supplies `beforeinstallprompt`. On iPhone/iPad, open in Safari and use **Share → Add to Home Screen**. Availability depends on browser support and policy.

Visit online once and let the service worker finish caching. The app and its LICENSE text are then available offline, including new language-query URLs. PayPal and GitHub links need an Internet connection. The service worker is scoped to this app and only removes its own old caches, not another TekiDeki project's caches.

For local use, download and open `index.html`. All required UI, lists and logic are embedded. Service workers are unavailable on `file:` URLs and storage/clipboard behavior varies by browser.

For local PWA testing:

```sh
python3 -m http.server 8000
```

Open `http://localhost:8000`. Deploy to HTTPS for production PWA support. Increment the service-worker cache version when changing the offline app shell.

## Generation behavior

Maximum length is an integer between **3 and 22**, counting Unicode code points after NFC normalization. Length includes any non-letter characters present in a list entry. If no entry matches the combination of length and filter, the app shows a translated message and disables copying; it does not pick an out-of-filter fallback word.

Selection uses `Math.random()` over matching list entries. Repeats are possible; homographs with different metadata remain separate entries. The “rare” flag comes from the existing curated lists and is **not** a corpus-derived frequency measurement. Word spellings and labels have not been independently reviewed by native speakers for all ten languages.

**Do not use this generator for passwords, security tokens or codes.** It is a creative tool, not a cryptographic random generator.

Opening the app or switching language generates a word. Consecutive identical history entries are suppressed, but the history is not a unique-word set. Clearing a history removes saved entries for that language; new generation repopulates it.

## Privacy and persistence

`lexigen_preferences_v1` and `lexigen_history_v1` are stored in `localStorage`. Nothing is uploaded. History is limited to 12 items per language and validated against the local lists before rendering. User-facing history labels are created with DOM text nodes, not injected HTML.

Storage is best-effort. If blocked, full or unavailable, the generator still works with in-memory state, but preferences/history may not survive a reload. Clearing site data, changing browser/device/origin or using private browsing can reset it. Data opened from a local file does not automatically move to the live website. Storage is not encrypted and is accessible to someone with access to the browser profile.

The host still receives ordinary page/asset requests. Clicking GitHub or PayPal links involves those external services. There are no embedded third-party requests or tracking scripts.

## SEO and verification

Includes technical metadata: localized titles/descriptions, visible introductory text, canonical/hreflang links, Open Graph/Twitter Card image, WebApplication JSON-LD, `robots.txt` and `sitemap.xml`. Translated content is client-rendered; indexing, social-preview refresh and rankings are not guaranteed.

The 2026-10-14 update was tested in Chromium with Playwright:

- 240 combinations of language/filter/maximum length, three generations per combination;
- history bounds, reload/language persistence, keyboard recall and clearing;
- clipboard success/denial, bad preferences/history, denied storage and direct-file use;
- ten languages × two themes; automated axe-core A/AA checks reported no tested violations;
- 320/390/768/1280 px layout; no third-party network requests;
- manifest parsing, service worker, new-query offline navigation, offline LICENSE and cache isolation.

Automated checks are not a full accessibility certification or comprehensive cross-browser/device testing.

## License and support

Copyright © 2026 Kristian Mario Mišković (**TekiDeki**).

**Apache License, Version 2.0** — see [LICENSE](LICENSE) and [NOTICE](NOTICE).

[Support on PayPal](https://paypal.me/TekiDeki) · [Source code](https://github.com/TekiDeki/Generator-Random-Word)
