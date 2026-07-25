# LinkHarvest

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine leichte Browser-Erweiterung, die alle Hyperlinks einer Webseite extrahiert, mit intelligenten Filtern und CSV-Export.

> Chromium-basiert · Manifest V3 · Kein Tracking · Nur lokale Daten

---

## Funktionen

| Funktion | Beschreibung |
|----------|-------------|
| 🔍 **Ein-Klick-Scan** | Alle `<a>`-Links der aktuellen Seite extrahieren |
| 📡 **Echtzeit-DOM-Überwachung** | MutationObserver erfasst dynamisch hinzugefügte Links (SPA, Endlos-Scrollen) |
| 🔎 **Intelligenter Filter** | Anker-Links, JS-Pseudo-Links filtern; intern/extern unterscheiden |
| 📋 **Stapelkopie** | Alle gültigen Links mit einem Klick in die Zwischenablage kopieren |
| 📥 **CSV-Export** | UTF-8 BOM-Kodierung — kompatibel mit Excel/WPS |
| 🔒 **Nur lokale Daten** | Alle Daten nur im Browserspeicher; werden beim Schließen gelöscht |
| 🌍 **Mehrsprachig** | Englisch, Chinesisch, Japanisch, Deutsch, Spanisch, Französisch |
| ⚡ **Leichtgewichtig** | Reines JavaScript, keine Abhängigkeiten, Paket < 40KB |
| 🏗️ **Manifest V3** | Nur `activeTab` + `scripting` — minimale Berechtigungen |

---

## Vorschau

<p align="center">
  <img src="../screenshot/promo.png" alt="LinkHarvest Vorschau" width="640">
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

1. Öffnen Sie die Erweiterungsseite Ihres Browsers:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Aktivieren Sie den **Entwicklermodus** (Schalter oben rechts)
3. Klicken Sie auf **Entpackte Erweiterung laden** und wählen Sie den Projektordner
4. Klicken Sie auf das LinkHarvest-Symbol in der Symbolleiste

---

## Verwendung

1. **Ziel-Webseite öffnen** und warten, bis dynamische Inhalte geladen sind
2. **LinkHarvest-Symbol klicken** in der Symbolleiste
3. **DOM-Überwachung aktivieren** (optional) — für Seiten mit Endlos-Scrollen oder nachgeladenen Links
4. **Auf "Seitenlinks scannen" klicken** — alle Links werden sofort extrahiert
5. **Vollständige Liste anzeigen** — öffnet eine dedizierte Ergebnisseite mit Tabellenansicht
6. **Suchen & Filtern** — Suchleiste und Filter-Toggles verwenden
7. **Kopieren oder Exportieren** — Links in Zwischenablage kopieren oder als CSV exportieren

> **⚠️ CSV-Export Hinweis:** Exportierte CSV-Dateien werden auf Ihrem lokalen Gerätespeicher gespeichert. Diese Dateien werden von Ihnen verwaltet; die Erweiterung steuert nicht den Lebenszyklus lokaler exportierter Dateien. Bitte löschen Sie exportierte Dateien manuell, wenn sie nicht mehr benötigt werden.

---

## Erfasste Felder

| Feld | Beschreibung |
|------|-------------|
| `linkText` | Link-Text (bereinigt) |
| `href` | Vollständige absolute URL |
| `target` | `_blank` / `_self` |
| `category` | Anker / JS-Pseudo-Link / Protokoll-Link / Normal |
| `isInternal` | Ob der Link gleichursprünglich ist |

---

## Datenschutz

- Nur `activeTab` + `scripting` Berechtigungen — nichts weiter
- `activeTab`: Gewährt Zugriff nur bei aktivem Klick auf das Erweiterungssymbol
- `scripting`: Wird verwendet, um das Link-Erfassungsskript in die aktuelle Seite einzufügen
- Keine `<all_urls>` Berechtigung — greift nicht ohne Ihr Handeln auf Seiten zu
- Keine externen Netzwerkanfragen — alle Verarbeitung erfolgt lokal
- Kein Zugriff auf Browserverlauf, kein Tracking, kein Daten-Upload
- Alle Scan-Daten werden nur im Browserspeicher gehalten und beim Schließen gelöscht
- [Privacy Policy](../privacy-policy.html)

### Nicht angeforderte Berechtigungen

| Berechtigung | Grund für Nichtanforderung |
|--------------|---------------------------|
| `<all_urls>` | Greift nicht ohne Benutzeraktion auf Seiten zu |
| `storage` (persistent) | Speichert keine Daten im lokalen persistenten Speicher |
| `notifications` | Sendet keine Systembenachrichtigungen |
| `cookies` | Liest oder ändert keine Cookies |
| `webRequest` | Fängt keine Netzwerkanfragen ab oder überwacht diese |

### Nicht erfasste Daten

- ❌ Passwörter, Formulareingaben
- ❌ Cookies, LocalStorage, IndexedDB, SessionStorage-Daten
- ❌ Browser-Cache, Browserverlauf
- ❌ Benutzeranmeldeinformationen, Login-Daten
- ❌ Seiteninhaltstext, Bilder, Videos oder andere Medieninhalte
- ❌ Drittanbieter-Skriptdaten, Werbeverfolgungsinformationen
- ❌ Gerätekennungen, IP-Adressen, Nutzerverhaltensdaten

### Nutzerrechte (DSGVO/CCPA)

- **Recht auf Unterbrechung:** Sie können die Erweiterung jederzeit schließen oder den Scanvorgang stoppen
- **Recht auf Löschung:** Alle Speicherdaten werden automatisch gelöscht, wenn Sie die Seite oder den Browser schließen; Sie können auch lokal exportierte CSV-Dateien manuell löschen
- **Recht auf Zugang:** Diese Erweiterung speichert keine personenbezogenen Benutzerdaten
- **Recht auf Datenübertragbarkeit:** Die CSV-Exportfunktion unterstützt den Datenexport
- **Recht auf Widerspruch:** Diese Erweiterung beinhaltet keine Datenverfolgung oder Profilerstellung

---

## Urheberrechtshinweis

Diese Erweiterung liest nur öffentlich gerenderte Hyperlink-Elemente (`<a>`) von Webseiten zum Komfort des Benutzers. Alle Text-, Bild- und Inhaltsrechte der Website gehören dem ursprünglichen Herausgeber. Das Extrahieren von Links gewährt den Benutzern keine Urheberrechte an den Website-Inhalten. Benutzer müssen beim Verwenden extrahierter Links die lokalen Gesetze zum geistigen Eigentum einhalten.

### Nutzungsbeschränkungen

Benutzer dürfen diese Erweiterung NICHT verwenden für:

- Hochfrequentes massenhaftes Crawling oder Scraping, das gegen die Nutzungsbedingungen der Ziel-Website verstößt
- Massenhaftes Herunterladen von Ressourcen unter Verletzung von Gesetzen zum geistigen Eigentum
- Großangelegte unbefugte Vervielfältigung oder Verbreitung urheberrechtlich geschützter Inhalte
- Verstöße gegen die `robots.txt`-Protokolle oder Nutzungsvereinbarungen der Ziel-Website

Benutzer sollten vor dem massenhaften Extrahieren von Links die `robots.txt` und die Nutzungsbedingungen der Ziel-Website prüfen. Jegliche Verantwortung für Missbrauch liegt beim Benutzer.

---

## Lizenz

Copyright © 2026 LinkHarvest. Alle Rechte vorbehalten.

Dieses Projekt steht unter der [MIT-Lizenz](../LICENSE). Sie dürfen diese Software gemäß den Lizenzbedingungen frei verwenden, ändern und verteilen.

---

## Audit-Hinweise

Für Prüfer von Anwendungsstores erklärt diese Erweiterung Folgendes:

| Punkt | Details |
|-------|---------|
| Angeforderte Berechtigungen | Nur `activeTab`, `scripting` |
| Verwendung von `activeTab` | Temporärer Zugriff auf die aktuelle Registerkarte, wenn der Benutzer auf das Erweiterungssymbol klickt |
| Verwendung von `scripting` | Einbetten des Link-Erfassungsskripts bei benutzergesteuertem Scan |
| Netzwerkanfragen | Keine — alle Verarbeitung erfolgt lokal |
| Datenspeicherung | Nur Browser-Sitzungsspeicher (`chrome.storage.session`) |
| Drittanbieterdienste | Keine |
| Nutzerverfolgung | Keine |
