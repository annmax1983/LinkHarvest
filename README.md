# LinkHarvest

[English](README.md) | [中文](languages/README_zh.md) | [Español](languages/README_es.md) | [Deutsch](languages/README_de.md) | [日本語](languages/README_ja.md) | [Français](languages/README_fr.md)

A lightweight browser extension that extracts all hyperlinks from any webpage, with smart filtering and CSV export.

> Chromium-based · Manifest V3 · No tracking · Local-only data

---

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **One-Click Scan** | Extract all `<a>` tag links from the current page |
| 📡 **Real-Time DOM Monitor** | MutationObserver captures dynamically added links (SPA, infinite scroll) |
| 🔎 **Smart Filter** | Filter anchor links, JavaScript pseudo-links; distinguish internal/external |
| 📋 **Batch Copy** | Copy all valid links to clipboard in one click |
| 📥 **CSV Export** | UTF-8 BOM encoding — compatible with Excel/WPS |
| 🔒 **Local-Only Data** | All data stored in browser memory only; cleared when page closes |
| 🌍 **Multi-Language** | Supports English, Chinese, Japanese, German, Spanish, French |
| ⚡ **Lightweight** | Pure vanilla JavaScript, zero dependencies, < 40KB package |
| 🏗️ **Manifest V3** | Uses `activeTab` + `scripting` — minimal permissions |

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
4. Click the LinkHarvest icon in your toolbar to start

---

## Usage

1. **Open the target webpage** and wait for dynamic content to load
2. **Click the LinkHarvest icon** in your browser toolbar
3. **Enable DOM Monitor** (optional) — for pages with infinite scroll or lazy-loaded links
4. **Click "Scan Page Links"** — all links are extracted instantly
5. **View full list** — opens a dedicated results page with table view
6. **Search & Filter** — use the search box and filter toggles to narrow results
7. **Copy or Export** — copy links to clipboard or export as CSV file

> **⚠️ CSV Export Notice:** Exported CSV files are saved to your local device disk. These files are managed by you; the extension does not control their lifecycle. Please manually delete exported files when no longer needed.

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

- Only `activeTab` + `scripting` permissions — nothing more
- `activeTab`: Grants access only when you actively click the extension icon
- `scripting`: Used to inject the link collection script into the current page
- No `<all_urls>` permission — does not access pages without your action
- No external network requests — all processing happens locally
- No browsing history access, no user tracking, no data upload
- All scan data is stored in browser memory only and cleared when the page closes
- [Privacy Policy](privacy-policy.html)

### Permissions NOT Requested

| Permission | Reason for not requesting |
|------------|---------------------------|
| `<all_urls>` | Will not access pages without user action |
| `storage` (persistent) | Does not save data to local persistent storage |
| `notifications` | Does not send system notifications |
| `cookies` | Does not read or modify cookies |
| `webRequest` | Does not intercept or monitor network requests |

### Data NOT Collected

- ❌ Passwords, form input content
- ❌ Cookies, LocalStorage, IndexedDB, SessionStorage data
- ❌ Browser cache, browsing history
- ❌ User credentials, login information
- ❌ Page body text, images, videos, or other media content
- ❌ Third-party script data, advertising tracking information
- ❌ Device identifiers, IP addresses, user behavior data

### User Rights (GDPR/CCPA)

- **Right to Stop:** You can close the extension or stop scanning at any time
- **Right to Delete:** All memory data is automatically cleared when you close the page or browser; you can also manually delete locally exported CSV files
- **Right to Access:** This extension does not store any personally identifiable user data
- **Right to Data Portability:** CSV export functionality supports data export
- **Right to Opt-Out:** This extension does not involve any data tracking or profiling

---

## Copyright Disclaimer

This extension only reads publicly rendered hyperlink elements (`<a>` tags) from web pages for the user's convenience. All text, images and content copyright of the website belong to the original publisher. Extracting links does not grant users any copyright authorization for the website content.

### Usage Restrictions

Users shall NOT use this extension to:

- Conduct high-frequency bulk crawling or scraping that violates target website terms of service
- Perform mass downloading of resources in violation of intellectual property laws
- Engage in large-scale unauthorized reproduction or distribution of copyrighted content
- Violate target website `robots.txt` protocols or user agreements

Users are advised to review the target website's `robots.txt` and terms of service before bulk extracting links. All responsibility for misuse rests with the user.

Users shall abide by local intellectual property laws when using extracted links.

---

## License

Copyright © 2026 LinkHarvest. All rights reserved.

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this software in accordance with the license terms.

---

## Audit Notes

For application store reviewers, this extension declares the following:

| Item | Details |
|------|---------|
| Permissions requested | `activeTab`, `scripting` only |
| `activeTab` usage | Temporary access to current tab when user clicks the extension icon |
| `scripting` usage | Inject link collection script on user-triggered scan |
| Network requests | None — all processing is local |
| Data storage | Browser session memory only (`chrome.storage.session`) |
| Third-party services | None |
| User tracking | None |
