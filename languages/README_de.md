# LinkHarvest — Link-Extraktor & Scanner

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung, die alle Hyperlinks von jeder Webseite extrahiert — mit intelligentem Filter, Suche und CSV-Export.

> Chromium-basiert · Manifest V3 · Kein Tracking · Nur lokale Daten

---

## Warum LinkHarvest?

Die meisten Link-Extraktions-Tools sind Online-Dienste, die den Seiteninhalt hochladen müssen. LinkHarvest läuft komplett in deinem Browser — keine Daten verlassen dein Gerät.

| Vorteil | Details |
|---------|---------|
| 🔍 **Ein-Klick-Scan** | Alle `<a>`-Tag-Links von der aktuellen Seite extrahieren |
| 📡 **Echtzeit-DOM-Überwachung** | MutationObserver erfasst dynamisch hinzugefügte Links (SPA, Infinite Scroll) |
| 🔎 **Intelligenter Filter** | Keyword Ein-/Ausschluss-Filter, Spaltensortierung; Anchor & JS-Pseudo-Links filtern; intern/extern unterscheiden |
| 📋 **Batch-Kopieren** | Alle gültigen Links mit einem Klick in die Zwischenablage kopieren |
| 🖱️ **Kontextmenü** | Rechtsklick auf beliebige Seite → „Seitenlinks extrahieren", kein Popup nötig |
| 🔢 **Häufigkeitszähler** | Zählt, wie oft jede URL auf der Seite erscheint |
| 📥 **CSV-Export** | UTF-8 BOM-Kodierung — kompatibel mit Excel/WPS (Premium) |
| 🔒 **Nur lokale Daten** | Alle Daten nur im Browser-Speicher; werden beim Seiten-Schließen gelöscht |
| 🌍 **Mehrsprachig** | Unterstützt Englisch, Chinesisch, Japanisch, Deutsch, Spanisch, Französisch |
| ⚡ **Leichtgewichtig** | Reines Vanilla JavaScript, null Abhängigkeiten, < 100KB Paket |
| 🏗️ **Manifest V3** | Verwendet `activeTab` + `scripting` + `storage` + `contextMenus` — minimale Berechtigungen |

---

## Kostenlos vs. Premium

| Plan | Funktionen |
|------|-----------|
| **Kostenlos** | Links scannen, Echtzeit-DOM-Überwachung, Suche & Filter, in Zwischenablage kopieren, TXT-Export |
| **⭐ Premium** | CSV-Batch-Export — alle gefilterten Links als CSV-Datei herunterladen |

Alle Kernfunktionen (Scan, Filter, Kopieren) sind für immer kostenlos. **CSV-Export** erfordert eine VKT Premium-Lizenz — ein einmaliger Kauf, der die Entwicklung unterstützt.

- 🛒 Lizenz erhalten: `https://www.annmax1983.com/checkout.html?plugin=linkharvest`
- ⚙ Aktivieren: LinkHarvest Popup öffnen → **⚙**-Button klicken → Lizenzschlüssel eingeben.

> Die Lizenzaktivierung ist **optional**. Die kostenlose Stufe funktioniert vollständig ohne sie — kein Konto, keine Anmeldung, kein Lizenzschlüssel erforderlich.

---

## Vorschau

<p align="center">
  <img src="screenshot/promo.png" alt="LinkHarvest Vorschau" width="640">
</p>

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Andere Chromium-basierte Browser | ✅ Sollte funktionieren |

---

## Installation

1. Öffne die Erweiterungsseite deines Browsers:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Aktiviere den **Entwicklermodus** (Schalter oben rechts)
3. Klicke auf **Entpackte Erweiterung laden** und wähle den Projektordner
4. Klicke auf das 🔗 LinkHarvest-Symbol in deiner Toolbar zum Starten

---

## Verwendung

1. **Ziel-Webseite öffnen** und warten, bis dynamische Inhalte geladen sind
2. **Auf das LinkHarvest-Symbol klicken** in der Browser-Toolbar
3. **DOM-Überwachung aktivieren** (optional) — für Seiten mit Infinite Scroll oder Lazy-Loaded Links
4. **Auf „Seitenlinks scannen" klicken** — alle Links werden sofort extrahiert
5. **Vollständige Liste anzeigen** — öffnet eine dedizierte Ergebnisseite mit Tabellenansicht
6. **Suchen & Filtern** — Suchbox, Keyword Ein-/Ausschluss-Filter und Spaltensortierung verwenden, um Ergebnisse einzugrenzen
7. **Links kopieren** — gefilterte Links in die Zwischenablage kopieren (kostenlos)
8. **TXT exportieren** — gefilterte URLs als reine Textdatei speichern (kostenlos)
9. **CSV exportieren** — gefilterte Links mit Häufigkeitszähler als CSV-Datei herunterladen (Premium)

---

## Erfasste Felder

| Feld | Beschreibung |
|------|--------------|
| `linkText` | Link-Anzeigetext (bereinigt) |
| `href` | Vollständige absolute URL |
| `target` | `_blank` / `_self` |
| `category` | anchor / javascript / protocol / normal |
| `isInternal` | Ob der Link same-origin ist |
| `count` | Wie oft die URL auf der Seite erscheint |

---

## Datenschutz

- **activeTab** — Gewährt Zugriff nur bei aktivem Klick auf das Erweiterungssymbol
- **scripting** — Wird verwendet, um das Link-Sammelskript in die aktuelle Seite zu injizieren
- **storage** — Speichert Scanergebnisse temporär für die Ergebnisseite; wird beim Schließen des gescannten Tabs gelöscht
- **contextMenus** — Fügt ein Rechtsklick-„Seitenlinks extrahieren"-Menü hinzu; liest selbst keine Daten
- **Lizenz (optional)** — Nur bei Aktivierung einer kostenpflichtigen Lizenz: Ein Geräte-Fingerprint + Browser-Metadaten werden an `api.annmax1983.com` gesendet, um die Lizenz zu aktivieren/validieren. Dies enthält nie deine Scandaten, deinen Browserverlauf oder persönliche Daten.
- Keine `<all_urls>`-Berechtigung — greift nicht auf Seiten ohne deine Aktion zu
- Keine externen Netzwerk-Anfragen für kostenlose Funktionen — alles passiert lokal
- Kein Zugriff auf den Browserverlauf, kein Nutzertracking, kein Datenupload
- [Datenschutzerklärung](privacy-policy.html)

---

## Projektstruktur

```
link-harvest/
├── manifest.json          # MV3 Manifest
├── background/sw.js       # Service Worker (Nachrichtenrouting)
├── license.js             # Lizenzmanager (Aktivierung & Validierung)
├── content/collector.js   # Content Script (Link-Extraktion)
├── popup/
│   ├── popup.html         # Popup-UI (Scan-Steuerung + Lizenzmodal)
│   ├── popup.css          # Styles
│   └── popup.js           # Popup-Logik
├── results/
│   ├── results.html       # Vollständige Ergebnistabelle-Seite
│   ├── results.css        # Styles
│   └── results.js         # Tabelle, Suche, Filter, Export-Logik
├── index.html             # Support-Seite (6-Sprachen)
├── privacy-policy.html    # Datenschutzerklärung
├── promo.html             # Promo-Tile-Vorlage
├── screenshot/            # Screenshots für Store-Listing
├── assets/                # Symbole
└── _locales/              # i18n (en/zh/ja/de/es/fr)
```

---

## Urheberrechtshinweis

Diese Erweiterung liest nur öffentlich gerenderte Hyperlink-Elemente (`<a>`-Tags) von Webseiten für die Bequemlichkeit des Nutzers. Alle Text-, Bild- und Inhaltsrechte der Website gehören dem jeweiligen Herausgeber. Das Extrahieren von Links gewährt Nutzern keine Urheberrechtslizenz an Website-Inhalten.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Endbenutzer-Quellcodes bereitgestellt.

---

## Lizenz

Copyright © 2026 LinkHarvest. Alle Rechte vorbehalten.
