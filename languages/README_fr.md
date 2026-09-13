# LinkHarvest — Extracteur et analyseur de liens

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère qui extrait tous les liens hypertexte de n'importe quelle page web, avec filtrage intelligent, recherche et export CSV.

> Chromium · Manifest V3 · Aucun suivi · Données 100 % locales

---

## Pourquoi LinkHarvest ?

La plupart des outils d'extraction de liens sont des services en ligne qui nécessitent d'envoyer le contenu de la page. LinkHarvest fonctionne entièrement dans votre navigateur — aucune donnée ne quitte votre appareil.

| Avantage | Détail |
|-----------|--------|
| 🔍 **Scan en un clic** | Extrait tous les liens `<a>` de la page courante |
| 📡 **Surveillance DOM en temps réel** | Le MutationObserver capture les liens ajoutés dynamiquement (SPA, défilement infini) |
| 🔎 **Filtrage intelligent** | Filtres par inclusion/exclusion de mots-clés, tri par colonne ; filtre les ancres et pseudo-liens JS ; distingue interne/externe |
| 📋 **Copie par lot** | Copiez tous les liens valides dans le presse-papiers en un clic |
| 🖱️ **Menu contextuel** | Clic droit sur n'importe quelle page → « Extraire les liens de la page », pas besoin de popup |
| 🔢 **Compteur d'occurrences** | Suit combien de fois chaque URL apparaît sur la page |
| 📥 **Export CSV** | Encodage UTF-8 BOM — compatible avec Excel/WPS (Premium) |
| 🔒 **Données locales uniquement** | Toutes les données stockées en mémoire du navigateur ; effacées à la fermeture de la page |
| 🌍 **Multilingue** | Prend en charge l'anglais, le chinois, le japonais, l'allemand, l'espagnol et le français |
| ⚡ **Léger** | JavaScript vanilla pur, zéro dépendance, package de moins de 100 Ko |
| 🏗️ **Manifest V3** | Utilise `activeTab` + `scripting` + `storage` + `contextMenus` — permissions minimales |

---

## Gratuit vs Premium

| Plan | Fonctionnalités |
|------|----------|
| **Gratuit** | Scan des liens, surveillance DOM en temps réel, recherche et filtrage, copie dans le presse-papiers, export TXT |
| **⭐ Premium** | Export CSV par lot — téléchargez tous les liens filtrés en fichier CSV |

Toutes les fonctionnalités de base (scan, filtrage, copie) sont gratuites à vie. L'**Export CSV** nécessite une licence VKT Premium — un achat unique qui soutient le développement.

- 🛒 Obtenir une licence : `https://www.annmax1983.com/checkout.html?plugin=linkharvest`
- ⚙ L'activer : ouvrez le popup LinkHarvest → cliquez sur le bouton **⚙** → saisissez votre clé de licence.

> L'activation de la licence est **optionnelle**. Le niveau gratuit fonctionne entièrement sans elle — pas de compte, pas d'inscription, pas de clé de licence requise.

---

## Aperçu

<p align="center">
  <img src="screenshot/promo.png" alt="Aperçu LinkHarvest" width="640">
</p>

---

## Navigateurs compatibles

| Navigateur | Statut |
|---------|--------|
| Google Chrome | ✅ Entièrement pris en charge |
| Microsoft Edge | ✅ Entièrement pris en charge |
| Autres navigateurs basés sur Chromium | ✅ Devrait fonctionner |

---

## Installation

1. Ouvrez la page des extensions de votre navigateur :
   - **Chrome** : `chrome://extensions/`
   - **Edge** : `edge://extensions/`
2. Activez le **mode Développeur** (bouton en haut à droite)
3. Cliquez sur **Charger le package décompressé** et sélectionnez le dossier du projet
4. Cliquez sur l'icône 🔗 LinkHarvest dans votre barre d'outils pour commencer

---

## Utilisation

1. **Ouvrez la page cible** et attendez le chargement du contenu dynamique
2. **Cliquez sur l'icône LinkHarvest** dans la barre d'outils
3. **Activez la surveillance DOM** (optionnel) — pour les pages avec défilement infini ou liens en chargement différé
4. **Cliquez sur « Scanner les liens de la page »** — tous les liens sont extraits instantanément
5. **Consultez la liste complète** — ouvre une page de résultats dédiée en vue tableau
6. **Recherchez et filtrez** — utilisez la barre de recherche, les filtres d'inclusion/exclusion de mots-clés et le tri par colonne pour affiner les résultats
7. **Copiez les liens** — copiez les liens filtrés dans le presse-papiers (gratuit)
8. **Exportez en TXT** — enregistrez les URLs filtrées en fichier texte (gratuit)
9. **Exportez en CSV** — téléchargez les liens filtrés en fichier CSV avec le compteur d'occurrences (Premium)

---

## Champs collectés

| Champ | Description |
|-------|-------------|
| `linkText` | Texte d'affichage du lien (nettoyé) |
| `href` | URL absolue complète |
| `target` | `_blank` / `_self` |
| `category` | anchor / javascript / protocol / normal |
| `isInternal` | Si le lien est de même origine |
| `count` | Nombre de fois où l'URL apparaît sur la page |

---

## Confidentialité

- **activeTab** — Accorde l'accès uniquement quand vous cliquez activement sur l'icône de l'extension
- **scripting** — Utilisé pour injecter le script de collecte de liens dans la page courante
- **storage** — Stocke temporairement les résultats du scan pour la page de résultats ; effacé à la fermeture de l'onglet scanné
- **contextMenus** — Ajoute un élément de menu contextuel « Extraire les liens de la page » ; ne lit aucune donnée en soi
- **Licence (optionnelle)** — Uniquement si vous activez une licence payante : une empreinte de l'appareil + des métadonnées du navigateur sont envoyées à `api.annmax1983.com` pour activer/valider la licence. Cela n'inclut jamais vos données de scan, votre historique de navigation ni vos données personnelles.
- Pas de permission `<all_urls>` — n'accède pas aux pages sans votre action
- Pas de requêtes réseau externes pour les fonctionnalités gratuites — tout le traitement se fait en local
- Pas d'accès à l'historique de navigation, pas de suivi utilisateur, pas d'envoi de données
- [Politique de confidentialité](privacy-policy.html)

---

## Structure du projet

```
link-harvest/
├── manifest.json          # Manifest MV3
├── background/sw.js       # Service worker (routage des messages)
├── license.js             # Gestionnaire de licences (activation et validation)
├── content/collector.js   # Script de contenu (extraction des liens)
├── popup/
│   ├── popup.html         # Interface popup (contrôles de scan + modale de licence)
│   ├── popup.css          # Styles
│   └── popup.js           # Logique du popup
├── results/
│   ├── results.html       # Page de résultats complète en tableau
│   ├── results.css        # Styles
│   └── results.js         # Logique tableau, recherche, filtrage, export
├── index.html             # Page de support (6 langues)
├── privacy-policy.html    # Politique de confidentialité
├── promo.html             # Modèle de tuile promotionnelle
├── screenshot/            # Captures d'écran pour la boutique
├── assets/                # Icônes
└── _locales/              # i18n (en/zh/ja/de/es/fr)
```

---

## Avertissement relatif au droit d'auteur

Cette extension lit uniquement les éléments de liens hypertexte rendus publiquement (balises `<a>`) depuis les pages web pour la commodité de l'utilisateur. Tous les droits d'auteur des textes, images et contenus des sites appartiennent à leurs éditeurs originaux. L'extraction de liens ne confère aux utilisateurs aucun droit d'auteur sur le contenu des sites.

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de version et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source destiné aux utilisateurs finaux n'est fourni.

---

## Licence

Copyright © 2026 LinkHarvest. Tous droits réservés.
