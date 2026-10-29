# LinkHarvest

English | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

A lightweight browser extension that extracts all hyperlinks from any webpage, with smart filtering, CSV / JSON export and an optional link audit.

> Chrome / Edge / Firefox · Manifest V3 · No tracking · Local-only data

---

## Features

| Feature | Description |
|---------|-------------|
| 🔍 **One-Click Scan** | Extract all `<a>` tag links from the current page |
| 📡 **Real-Time DOM Monitor** | Picks up links added while you scroll (SPA, infinite scroll) |
| 🔎 **Smart Filter** | Keyword include/exclude filters, column sorting; filter anchor & JS pseudo-links; distinguish internal/external |
| 💾 **Saved Filter Presets** | Name the current filter combination and reuse it in one click (stored locally) |
| 📋 **Multi-Format Copy** | Copy filtered links as plain URLs, Markdown, HTML `<a>` list or JSON Lines (free) |
| 🌐 **Open in Tabs** | Open filtered links in background tabs with an adjustable delay (free) |
| 🖱️ **Context Menu** | Right-click any page → "Extract page links", no popup needed |
| 🔢 **Occurrence Count** | Tracks how many times each URL appears on the page |
| 📥 **JSON / TXT Export** | Structured JSON file & plain URL list (free) |
| 📥 **CSV Export** | UTF-8 BOM encoding — compatible with Excel/WPS (free) |
| 🩺 **Link Audit** | Checks HTTP status of filtered links and flags broken, blocked, redirected and unreachable URLs; free preview of 100 links per run (⭐ Premium: up to 2,000 links + CSV report) |
| 🔒 **Local-Only Data** | Scan results live in browser memory only (cleared when the page closes); saved filter presets and UI preferences stay in this browser's localStorage and are never uploaded |
| 🌍 **Multi-Language** | Supports English, Chinese, Japanese, German, Spanish, French |
| 🌙 **Dark Mode** | Follows your system theme automatically |
| ⚡ **Lightweight** | Pure vanilla JavaScript, zero dependencies, < 100KB package |
| 🏗️ **Manifest V3** | Uses `activeTab` + `scripting` + `storage` + `contextMenus` — minimal permissions |

---

---

## Free vs Premium

| Plan | Features |
|------|----------|
| **Free** | Scan links, real-time DOM monitor, search & filter, saved filter presets, multi-format copy, open in tabs, TXT / JSON / CSV export, dark mode, Link Audit preview (100 links per run) |
| **⭐ Premium** | Full Link Audit — up to 2,000 links per run and export a CSV audit report with status codes, redirect targets and response times |

All core features and **TXT / JSON / CSV export** are free forever. The **Link Audit preview** is free; the **full audit and report** require a VKT Premium license.

> License activation is **optional**. The free tier works fully without it.

## Preview

<p align="center">
  <img src="../screenshots/promo.png" alt="LinkHarvest Preview" width="640">
</p>

---

## Supported Browsers

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Fully supported |
| Microsoft Edge | ✅ Fully supported |
| Mozilla Firefox | ✅ Fully supported |
| Other Chromium-based browsers | ✅ Should work |

> **Firefox note:** Site access is confirmed through the native Firefox prompt and can be revoked any time from the Add-ons Manager. Everything else behaves as on Chrome / Edge.

---

## Installation

| Store | Link |
|---|---|
| Chrome Web Store | [Install for Chrome](https://chromewebstore.google.com/detail/cnkbdmjkfnlgpjehaogliipehjaibojn) |
| Microsoft Edge Add-ons | [Install for Edge](https://microsoftedge.microsoft.com/addons/detail/abfpbiilibfniidobemeffponimgdaff) |
| Firefox Add-ons (AMO) | 🔜 Under review — link will be added once the listing is live |

> Install only from the official stores above — avoid third-party download sites.

---

## Usage

1. **Open the target webpage** and wait for dynamic content to load
2. **Click the LinkHarvest icon** in your browser toolbar
3. **Enable DOM Monitor** (optional) — for pages with infinite scroll or lazy-loaded links
4. **Click "Scan Page Links"** — all links are extracted instantly
5. **View full list** — opens a dedicated results page with table view
6. **Search & Filter** — use the search box, keyword include/exclude filters, and column sorting to narrow results
   - 💾 Save this filter combination as a named preset (💾) and reuse it in one click later
   - 🌐 Open the filtered links in background tabs (🌐) with an adjustable delay
7. **Copy or Export** — copy links as plain URLs, Markdown, HTML or JSON Lines (free), export TXT / JSON / CSV with occurrence counts (free)
8. **Run Link Audit** — check HTTP status of the filtered links and spot broken, blocked, redirected and unreachable URLs; the free preview covers 100 links per run, Premium covers up to 2,000 and exports a CSV report

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
| `count` | How many times the URL appears on the page |

---

## Privacy

- Only `activeTab` + `scripting` + `storage` + `contextMenus` permissions, plus optional site access used only by Link Audit
- `activeTab`: Grants access only when you actively click the extension icon
- `scripting`: Used to inject the link collection script into the current page
- `contextMenus`: Adds a right-click "Extract page links" menu item; reads no data itself
- **Optional site access (Link Audit):** The browser asks for permission when you start an audit. Requests go directly from your browser to each target URL (HTTP HEAD/GET, no cookies); only status code, redirect target and response time are kept in memory. No page content is read or uploaded.
- No all-sites access by default — access is optional and requested only when you start Link Audit
- No external network requests except the optional license check and the Link Audit checks you start yourself
- No browsing history access, no user tracking, no data upload
- Scan results are stored in browser memory only and cleared when the page closes; saved filter presets and UI preferences are kept in this browser's `localStorage`
- [Privacy Policy](../privacy-policy.html)

### Permissions NOT Requested

| Permission | Reason for not requesting |
|------------|---------------------------|
| Always-on site access | Site access is optional and requested only when you start Link Audit |
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
- **Right to Delete:** All memory data is automatically cleared when you close the page or browser; you can also manually delete locally exported CSV / JSON files
- **Right to Access:** This extension does not store any personally identifiable user data
- **Right to Data Portability:** CSV / JSON export functionality supports data export
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

This project is licensed under the [MIT License](../LICENSE). You are free to use, modify, and distribute this software in accordance with the license terms.

---

## Audit Notes

For application store reviewers, this extension declares the following:

| Item | Details |
|------|---------|
| Permissions requested | `activeTab`, `scripting`, `storage`, `contextMenus` |
| `activeTab` usage | Temporary access to current tab when user clicks the extension icon (or context menu) |
| `scripting` usage | Inject link collection script on user-triggered scan |
| `contextMenus` usage | Adds the "Extract page links" right-click menu item |
| Network requests | Free features make none; license server is contacted only when activating a paid license |
| Data storage | Scan results stored temporarily in `storage.session` (in-memory, never written to disk), deleted when the scanned tab closes |
| Third-party services | Paid license verification only (`api.annmax1983.com`); free features never connect |
| User tracking | None |
