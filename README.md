# LinkHarvest — Link Extractor & Scanner

[English](README.md) | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

A lightweight browser extension that extracts all hyperlinks from any webpage, with smart filtering, search, and CSV export.

> Chromium-based · Manifest V3 · No tracking · Local-only data

---

## Why LinkHarvest?

Most link extraction tools are online services that require uploading page content. LinkHarvest runs entirely in your browser — no data leaves your device.

| Advantage | Detail |
|-----------|--------|
| 🔍 **One-Click Scan** | Extract all `<a>` tag links from the current page |
| 📡 **Real-Time DOM Monitor** | MutationObserver captures dynamically added links (SPA, infinite scroll) |
| 🔎 **Smart Filter** | Filter anchor links, JavaScript pseudo-links; distinguish internal/external |
| 📋 **Batch Copy** | Copy all valid links to clipboard in one click |
| 📥 **CSV Export** | UTF-8 BOM encoding — compatible with Excel/WPS (Premium) |
| 🔒 **Local-Only Data** | All data stored in browser memory only; cleared when page closes |
| 🌍 **Multi-Language** | Supports English, Chinese, Japanese, German, Spanish, French |
| ⚡ **Lightweight** | Pure vanilla JavaScript, zero dependencies, < 40KB package |
| 🏗️ **Manifest V3** | Uses `activeTab` + `scripting` + `storage` — minimal permissions |

---

## Free vs Premium

| Plan | Features |
|------|----------|
| **Free** | Scan links, real-time DOM monitor, search & filter, copy to clipboard |
| **⭐ Premium** | CSV batch export — download all filtered links as CSV file |

All core features (scan, filter, copy) are free forever. **CSV Export** requires a VKT Premium license — a one-time purchase that supports development.

- 🛒 Get a license: `https://www.annmax1983.com/checkout.html?plugin=linkharvest`
- ⚙ Activate it: open the LinkHarvest popup → click the **⚙** button → enter your license key.

> License activation is **optional**. The free tier works fully without it — no account, no sign-up, no license key required.

---

## Preview

<p align="center">
  <img src="screenshot/promo.png" alt="LinkHarvest Preview" width="640">
</p>

---

## Supported Browsers

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Fully supported |
| Microsoft Edge | ✅ Fully supported |
| Other Chromium-based browsers | ✅ Should work |

---

## Installation

1. Open your browser's extension page:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Enable **Developer mode** (top-right toggle)
3. Click **Load unpacked** and select the project folder
4. Click the 🔗 LinkHarvest icon in your toolbar to start

---

## Usage

1. **Open the target webpage** and wait for dynamic content to load
2. **Click the LinkHarvest icon** in your browser toolbar
3. **Enable DOM Monitor** (optional) — for pages with infinite scroll or lazy-loaded links
4. **Click "Scan Page Links"** — all links are extracted instantly
5. **View full list** — opens a dedicated results page with table view
6. **Search & Filter** — use the search box and filter toggles to narrow results
7. **Copy links** — copy filtered links to clipboard (free)
8. **Export CSV** — download filtered links as CSV file (Premium)

---

## Collected Fields

| Field | Description |
|-------|-------------|
| `linkText` | Link display text (cleaned) |
| `href` | Full absolute URL |
| `target` | `_blank` / `_self` |
| `category` | anchor / javascript / protocol / normal |
| `isInternal` | Whether the link is same-origin |

---

## Privacy

- **activeTab** — Grants access only when you actively click the extension icon
- **scripting** — Used to inject the link collection script into the current page
- **storage** — Stores scan results temporarily for the results page; cleared when the scanned tab is closed
- **License (optional)** — Only if you activate a paid license: a device fingerprint + browser metadata is sent to `api.annmax1983.com` to activate/validate the license. This never includes your scan data, browsing history, or personal data.
- No `<all_urls>` permission — does not access pages without your action
- No external network requests for free features — all processing happens locally
- No browsing history access, no user tracking, no data upload
- [Privacy Policy](privacy-policy.html)

---

## Project Structure

```
link-harvest/
├── manifest.json          # MV3 manifest
├── background/sw.js       # Service worker (message routing)
├── license.js             # License manager (activation & validation)
├── content/collector.js   # Content script (link extraction)
├── popup/
│   ├── popup.html         # Popup UI (scan controls + license modal)
│   ├── popup.css          # Styles
│   └── popup.js           # Popup logic
├── results/
│   ├── results.html       # Full results table page
│   ├── results.css        # Styles
│   └── results.js         # Table, search, filter, export logic
├── index.html             # Support page (6-language)
├── privacy-policy.html    # Privacy policy
├── promo.html             # Promotional tile template
├── screenshot/            # Screenshots for store listing
├── assets/                # Icons
└── _locales/              # i18n (en/zh/ja/de/es/fr)
```

---

## Copyright Disclaimer

This extension only reads publicly rendered hyperlink elements (`<a>` tags) from web pages for the user's convenience. All text, images and content copyright of the website belong to the original publisher. Extracting links does not grant users any copyright authorization for the website content.

---

## License

Copyright © 2026 LinkHarvest. All rights reserved.
