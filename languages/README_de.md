# LinkHarvest — Link-Extraktor & Scanner

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung, die alle Hyperlinks von jeder Webseite extrahiert — mit intelligentem Filter, Suche und CSV-/JSON-Export.

> Chromium-basiert · Manifest V3 · Kein Tracking · Nur lokale Daten

---

## Warum LinkHarvest?

Die meisten Link-Extraktions-Tools sind Online-Dienste, die den Seiteninhalt hochladen müssen. LinkHarvest läuft komplett in deinem Browser — keine Daten verlassen dein Gerät.

| Vorteil | Details |
|---------|---------|
| 🔍 **Ein-Klick-Scan** | Alle `<a>`-Tag-Links von der aktuellen Seite extrahieren |
| 📡 **Echtzeit-DOM-Überwachung** | MutationObserver erfasst dynamisch hinzugefügte Links (SPA, Infinite Scroll) |
| 🔎 **Intelligenter Filter** | Keyword Ein-/Ausschluss-Filter, Spaltensortierung; Anchor & JS-Pseudo-Links filtern; intern/extern unterscheiden |
| 💾 **Gespeicherte Filter** | Aktuelle Filterkombination benennen und später per Klick erneut anwenden (lokal gespeichert) |
| 📋 **Kopieren in mehreren Formaten** | Gefilterte Links als URL-Liste, Markdown, HTML-`<a>`-Liste oder JSON Lines kopieren (kostenlos) |
| 🌐 **In Tabs öffnen** | Gefilterte Links nacheinander in Hintergrund-Tabs öffnen, Verzögerung einstellbar (kostenlos) |
| 🖱️ **Kontextmenü** | Rechtsklick auf beliebige Seite → „Seitenlinks extrahieren", kein Popup nötig |
| 🔢 **Häufigkeitszähler** | Zählt, wie oft jede URL auf der Seite erscheint |
| 📥 **JSON-/TXT-Export** | Strukturierte JSON-Datei & URL-Liste (kostenlos) |
| 📥 **CSV-Export** | UTF-8 BOM-Kodierung — kompatibel mit Excel/WPS (⭐ Premium) |
| 🔒 **Nur lokale Daten** | Scan-Ergebnisse nur im Browser-Speicher (beim Schließen der Seite gelöscht); gespeicherte Filter und Oberflächen-Einstellungen liegen im localStorage dieses Browsers und werden nie hochgeladen |
| 🌍 **Mehrsprachig** | Unterstützt Englisch, Chinesisch, Japanisch, Deutsch, Spanisch, Französisch |
| 🌙 **Dunkler Modus** | Folgt automatisch dem Systemfarbschema |
| ⚡ **Leichtgewichtig** | Reines Vanilla JavaScript, null Abhängigkeiten, < 100KB Paket |
| 🏗️ **Manifest V3** | Verwendet `activeTab` + `scripting` + `storage` + `contextMenus` — minimale Berechtigungen |

---

## Kostenlos vs. Premium

| Plan | Funktionen |
|------|-----------|
| **Kostenlos** | Links scannen, Echtzeit-DOM-Überwachung, Suche & Filter, gespeicherte Filter, Kopieren in mehreren Formaten, in Tabs öffnen, TXT-/JSON-Export, dunkler Modus |
| **⭐ Premium** | CSV-Batch-Export — alle gefilterten Links als CSV-Datei herunterladen |

Alle Kernfunktionen (Scan, Filter, Kopieren) und der **JSON-/TXT-Export** sind für immer kostenlos. Der **CSV-Export** erfordert eine VKT Premium-Lizenz — ein einmaliger Kauf, der die Entwicklung unterstützt.

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
   - 💾 Filterkombination als benannten Preset speichern und später per Klick erneut anwenden
   - 🌐 Gefilterte Links nacheinander in Hintergrund-Tabs öffnen (Verzögerung einstellbar)
7. **Links kopieren** — als URL-Liste, Markdown, HTML oder JSON Lines kopieren (kostenlos)
8. **TXT exportieren** — gefilterte URLs als reine Textdatei speichern (kostenlos)
9. **CSV exportieren** — gefilterte Links mit Häufigkeitszähler als CSV-Datei herunterladen (Premium) · JSON-Export kostenlos

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
- **Lizenz (optional)** — Nur bei Aktivierung einer kostenpflichtigen Lizenz: Lizenzschlüssel und eine zufällige Installationskennung + Browser-Metadaten werden an `api.annmax1983.com` gesendet, um die Lizenz zu aktivieren/validieren. Dies enthält nie deine Scandaten, deinen Browserverlauf oder persönliche Daten.
- Keine `<all_urls>`-Berechtigung — greift nicht auf Seiten ohne deine Aktion zu
- Keine externen Netzwerk-Anfragen für kostenlose Funktionen — alles passiert lokal
- Kein Zugriff auf den Browserverlauf, kein Nutzertracking, kein Datenupload
- [Datenschutzerklärung](privacy-policy.html)

---

## Urheberrechtshinweis

Diese Erweiterung liest nur öffentlich gerenderte Hyperlink-Elemente (`<a>`-Tags) von Webseiten für die Bequemlichkeit des Nutzers. Alle Text-, Bild- und Inhaltsrechte der Website gehören dem jeweiligen Herausgeber. Das Extrahieren von Links gewährt Nutzern keine Urheberrechtslizenz an Website-Inhalten.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store vertrieben. Es werden keine Offline-Installationspakete oder Endbenutzer-Quellcodes bereitgestellt.

---

## Lizenz

Copyright © 2026 LinkHarvest. Alle Rechte vorbehalten.
