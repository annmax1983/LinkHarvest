# LinkHarvest — Link-Extraktor & Scanner

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | Deutsch | [日本語](README_ja.md) | [Français](README_fr.md)

Eine schlanke Browser-Erweiterung, die alle Hyperlinks von jeder Webseite extrahiert — mit intelligentem Filter, Suche, CSV-/JSON-Export und optionaler Link-Prüfung.

> Chrome / Edge / Firefox · Manifest V3 · Kein Tracking · Nur lokale Daten

---

## Warum LinkHarvest?

Die meisten Link-Extraktions-Tools sind Online-Dienste, die den Seiteninhalt hochladen müssen. LinkHarvest läuft komplett in deinem Browser — keine Daten verlassen dein Gerät.

| Vorteil | Details |
|---------|---------|
| 🔍 **Ein-Klick-Scan** | Alle `<a>`-Tag-Links von der aktuellen Seite extrahieren |
| 📡 **Echtzeit-DOM-Überwachung** | Erfasst auch nachträglich hinzugefügte Links (SPA, Infinite Scroll) |
| 🔎 **Intelligenter Filter** | Keyword Ein-/Ausschluss-Filter, Spaltensortierung; Anchor & JS-Pseudo-Links filtern; intern/extern unterscheiden |
| 💾 **Gespeicherte Filter** | Aktuelle Filterkombination benennen und später per Klick erneut anwenden (lokal gespeichert) |
| 📋 **Kopieren in mehreren Formaten** | Gefilterte Links als URL-Liste, Markdown, HTML-`<a>`-Liste oder JSON Lines kopieren (kostenlos) |
| 🌐 **In Tabs öffnen** | Gefilterte Links nacheinander in Hintergrund-Tabs öffnen, Verzögerung einstellbar (kostenlos) |
| 🖱️ **Kontextmenü** | Rechtsklick auf beliebige Seite → „Seitenlinks extrahieren", kein Popup nötig |
| 🔢 **Häufigkeitszähler** | Zählt, wie oft jede URL auf der Seite erscheint |
| 📥 **JSON-/TXT-Export** | Strukturierte JSON-Datei & URL-Liste (kostenlos) |
| 📥 **CSV-Export** | UTF-8 BOM-Kodierung — kompatibel mit Excel/WPS (kostenlos) |
| 🩺 **Link-Prüfung** | Prüft den HTTP-Status gefilterter Links und markiert defekte, blockierte, weitergeleitete und nicht erreichbare Links; kostenlose Vorschau von 100 Links pro Durchlauf (⭐ Premium: bis zu 2.000 Links + CSV-Bericht) |
| 🔒 **Nur lokale Daten** | Scan-Ergebnisse nur im Browser-Speicher (beim Schließen der Seite gelöscht); gespeicherte Filter und Oberflächen-Einstellungen liegen im localStorage dieses Browsers und werden nie hochgeladen |
| 🌍 **Mehrsprachig** | Unterstützt Englisch, Chinesisch, Japanisch, Deutsch, Spanisch, Französisch |
| 🌙 **Dunkler Modus** | Folgt automatisch dem Systemfarbschema |
| ⚡ **Leichtgewichtig** | Reines Vanilla JavaScript, null Abhängigkeiten, < 100KB Paket |
| 🏗️ **Manifest V3** | Verwendet `activeTab` + `scripting` + `storage` + `contextMenus` — minimale Berechtigungen |

---

## Kostenlos vs. Premium

| Plan | Funktionen |
|------|-----------|
| **Kostenlos** | Links scannen, Echtzeit-DOM-Überwachung, Suche & Filter, gespeicherte Filter, Kopieren in mehreren Formaten, in Tabs öffnen, TXT-/JSON-/CSV-Export, dunkler Modus, Vorschau der Link-Prüfung (100 Links pro Durchlauf) |
| **⭐ Premium** | Vollständige Link-Prüfung — bis zu 2.000 Links pro Durchlauf und Export eines CSV-Berichts mit Statuscodes, Weiterleitungszielen und Antwortzeiten |

Alle Kernfunktionen und der **TXT-/JSON-/CSV-Export** sind für immer kostenlos. Die **Prüfungsvorschau** ist kostenlos; die **vollständige Prüfung und der Bericht** erfordern eine VKT Premium-Lizenz.

- 🛒 Lizenz erhalten: `https://www.annmax1983.com/checkout.html?plugin=linkharvest`
- ⚙ Aktivieren: LinkHarvest Popup öffnen → **⚙**-Button klicken → Lizenzschlüssel eingeben.

> Die Lizenzaktivierung ist **optional**. Die kostenlose Stufe funktioniert vollständig ohne sie — kein Konto, keine Anmeldung, kein Lizenzschlüssel erforderlich.

---

## Vorschau

<p align="center">
  <img src="../screenshots/promo.png" alt="LinkHarvest Vorschau" width="640">
</p>

---

## Unterstützte Browser

| Browser | Status |
|---------|--------|
| Google Chrome | ✅ Vollständig unterstützt |
| Microsoft Edge | ✅ Vollständig unterstützt |
| Mozilla Firefox | ✅ Vollständig unterstützt |
| Andere Chromium-basierte Browser | ✅ Sollte funktionieren |

> **Firefox-Hinweis:** Website-Berechtigungen werden über den nativen Firefox-Dialog bestätigt und lassen sich jederzeit im Add-on-Manager widerrufen. Die übrigen Funktionen verhalten sich wie unter Chrome / Edge.

---

## Installation

| Store | Link |
|---|---|
| Chrome Web Store | [In Chrome installieren](https://chromewebstore.google.com/detail/cnkbdmjkfnlgpjehaogliipehjaibojn) |
| Microsoft Edge Add-ons | [In Edge installieren](https://microsoftedge.microsoft.com/addons/detail/abfpbiilibfniidobemeffponimgdaff) |
| Firefox-Add-ons (AMO) | 🔜 In Prüfung – Link folgt nach der Freigabe |

> Installieren Sie nur über die offiziellen Stores oben – meiden Sie Download-Seiten Dritter.

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
7. **Kopieren oder exportieren** — Links als URL-Liste, Markdown, HTML oder JSON Lines kopieren (kostenlos), TXT / JSON / CSV mit Häufigkeitszähler exportieren (kostenlos)
8. **Link-Prüfung starten** — prüft den HTTP-Status der gefilterten Links und findet defekte, blockierte, weitergeleitete und nicht erreichbare Links; die kostenlose Vorschau umfasst 100 Links pro Durchlauf, Premium bis zu 2.000 und exportiert einen CSV-Bericht

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
- **Optionaler Website-Zugriff (Link-Prüfung)** — Der Browser fragt beim Start einer Prüfung nach der Berechtigung. Anfragen gehen direkt von deinem Browser an jede URL (HTTP HEAD/GET, ohne Cookies); nur Statuscode, Weiterleitungsziel und Antwortzeit werden im Speicher gehalten. Seiteninhalte werden weder gelesen noch hochgeladen.
- **Lizenz (optional)** — Nur bei Aktivierung einer kostenpflichtigen Lizenz: Lizenzschlüssel und eine zufällige Installationskennung + Browser-Metadaten werden an `api.annmax1983.com` gesendet, um die Lizenz zu aktivieren/validieren. Dies enthält nie deine Scandaten, deinen Browserverlauf oder persönliche Daten.
- Kein Zugriff auf alle Websites standardmäßig — der Zugriff ist optional und wird nur beim Start der Link-Prüfung angefordert
- Keine externen Netzwerk-Anfragen außer der optionalen Lizenzvalidierung und den von dir gestarteten Prüfungen
- Kein Zugriff auf den Browserverlauf, kein Nutzertracking, kein Datenupload
- [Datenschutzerklärung](privacy-policy.html)

---

## Urheberrechtshinweis

Diese Erweiterung liest nur öffentlich gerenderte Hyperlink-Elemente (`<a>`-Tags) von Webseiten für die Bequemlichkeit des Nutzers. Alle Text-, Bild- und Inhaltsrechte der Website gehören dem jeweiligen Herausgeber. Das Extrahieren von Links gewährt Nutzern keine Urheberrechtslizenz an Website-Inhalten.

---

## Quellcode-Hinweis

> ⚠️ **Dieses Repository veröffentlicht keinen Quellcode.** Es enthält nur Nutzerdokumentation, Versionshinweise und Support-Ressourcen. Die Erweiterung wird ausschließlich über den Chrome Web Store, Microsoft Edge Add-ons und Firefox-Add-ons (AMO) vertrieben. Es werden keine Offline-Installationspakete oder Endbenutzer-Quellcodes bereitgestellt.

---

## Lizenz

Copyright © 2026 LinkHarvest. Alle Rechte vorbehalten.
