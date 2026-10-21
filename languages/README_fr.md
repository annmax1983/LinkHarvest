# LinkHarvest — Extracteur et analyseur de liens

[English](../README.md) | [中文](README_zh.md) | [Español](README_es.md) | [Deutsch](README_de.md) | [日本語](README_ja.md) | Français

Une extension légère qui extrait tous les liens hypertexte de n'importe quelle page web, avec filtrage intelligent, recherche, export CSV/JSON et audit de liens optionnel.

> Chromium · Manifest V3 · Aucun suivi · Données 100 % locales

---

## Pourquoi LinkHarvest ?

La plupart des outils d'extraction de liens sont des services en ligne qui nécessitent d'envoyer le contenu de la page. LinkHarvest fonctionne entièrement dans votre navigateur — aucune donnée ne quitte votre appareil.

| Avantage | Détail |
|-----------|--------|
| 🔍 **Scan en un clic** | Extrait tous les liens `<a>` de la page courante |
| 📡 **Surveillance DOM en temps réel** | Le MutationObserver capture les liens ajoutés dynamiquement (SPA, défilement infini) |
| 🔎 **Filtrage intelligent** | Filtres par inclusion/exclusion de mots-clés, tri par colonne ; filtre les ancres et pseudo-liens JS ; distingue interne/externe |
| 💾 **Filtres enregistrés** | Nommez la combinaison de filtres actuelle et réutilisez-la en un clic (stocké localement) |
| 📋 **Copie multi-formats** | Copiez les liens filtrés en liste d'URL, Markdown, liste HTML `<a>` ou JSON Lines (gratuit) |
| 🌐 **Ouvrir dans des onglets** | Ouvrez les liens filtrés dans des onglets en arrière-plan, avec un délai réglable (gratuit) |
| 🖱️ **Menu contextuel** | Clic droit sur n'importe quelle page → « Extraire les liens de la page », pas besoin de popup |
| 🔢 **Compteur d'occurrences** | Suit combien de fois chaque URL apparaît sur la page |
| 📥 **Export JSON / TXT** | Fichier JSON structuré et liste d'URL (gratuit) |
| 📥 **Export CSV** | Encodage UTF-8 BOM — compatible avec Excel/WPS (gratuit) |
| 🩺 **Audit de liens** | Vérifie le statut HTTP des liens filtrés et signale les liens cassés, bloqués, redirigés et inaccessibles ; aperçu gratuit de 100 liens par exécution (⭐ Premium : jusqu'à 2 000 liens + rapport CSV) |
| 🔒 **Données locales uniquement** | Les résultats de scan restent en mémoire du navigateur (effacés à la fermeture de la page) ; les filtres enregistrés et les préférences d'interface sont stockés dans le localStorage de ce navigateur et ne sont jamais envoyés |
| 🌍 **Multilingue** | Prend en charge l'anglais, le chinois, le japonais, l'allemand, l'espagnol et le français |
| 🌙 **Mode sombre** | Suit automatiquement le thème du système |
| ⚡ **Léger** | JavaScript vanilla pur, zéro dépendance, package de moins de 100 Ko |
| 🏗️ **Manifest V3** | Utilise `activeTab` + `scripting` + `storage` + `contextMenus` — permissions minimales |

---

## Gratuit vs Premium

| Plan | Fonctionnalités |
|------|----------|
| **Gratuit** | Scan des liens, surveillance DOM en temps réel, recherche et filtrage, filtres enregistrés, copie multi-formats, ouverture dans des onglets, export TXT / JSON / CSV, mode sombre, aperçu de l'audit de liens (100 liens par exécution) |
| **⭐ Premium** | Audit de liens complet — jusqu'à 2 000 liens par exécution et export d'un rapport CSV avec codes de statut, destinations de redirection et temps de réponse |

Toutes les fonctionnalités de base et l'**export TXT / JSON / CSV** sont gratuits à vie. L'**aperçu de l'audit** est gratuit ; l'**audit complet et le rapport** nécessitent une licence VKT Premium.

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
   - 💾 Enregistrez cette combinaison de filtres comme préréglage nommé et réutilisez-la en un clic
   - 🌐 Ouvrez les liens filtrés dans des onglets en arrière-plan, avec un délai réglable
7. **Copiez ou exportez** — copiez les liens en URLs, Markdown, HTML ou JSON Lines (gratuit), exportez en TXT / JSON / CSV avec le compteur d'occurrences (gratuit)
8. **Lancez un audit de liens** — vérifie le statut HTTP des liens filtrés et détecte les liens cassés, bloqués, redirigés et inaccessibles ; l'aperçu gratuit couvre 100 liens par exécution, Premium jusqu'à 2 000 et exporte un rapport CSV

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
- **Accès optionnel aux sites (audit de liens)** — Le navigateur demande l'autorisation au lancement d'un audit. Les requêtes partent directement de votre navigateur vers chaque URL (HTTP HEAD/GET, sans cookies) ; seuls le code de statut, la destination de redirection et le temps de réponse sont conservés en mémoire. Le contenu des pages n'est ni lu ni envoyé.
- **Licence (optionnelle)** — Uniquement si vous activez une licence payante : la clé de licence et un identifiant d'installation aléatoire + des métadonnées du navigateur sont envoyées à `api.annmax1983.com` pour activer/valider la licence. Cela n'inclut jamais vos données de scan, votre historique de navigation ni vos données personnelles.
- Pas d'accès à tous les sites par défaut — l'accès est optionnel et demandé uniquement au lancement de l'audit de liens
- Pas de requêtes réseau externes en dehors de la validation optionnelle de la licence et des audits que vous lancez
- Pas d'accès à l'historique de navigation, pas de suivi utilisateur, pas d'envoi de données
- [Politique de confidentialité](privacy-policy.html)

---

## Avertissement relatif au droit d'auteur

Cette extension lit uniquement les éléments de liens hypertexte rendus publiquement (balises `<a>`) depuis les pages web pour la commodité de l'utilisateur. Tous les droits d'auteur des textes, images et contenus des sites appartiennent à leurs éditeurs originaux. L'extraction de liens ne confère aux utilisateurs aucun droit d'auteur sur le contenu des sites.

---

## Avis sur le code source

> ⚠️ **Ce dépôt ne publie pas le code source.** Il contient uniquement la documentation d'utilisation, les notes de version et les ressources d'assistance. L'extension est distribuée exclusivement via le Chrome Web Store. Aucun package d'installation hors ligne ni code source destiné aux utilisateurs finaux n'est fourni.

---

## Licence

Copyright © 2026 LinkHarvest. Tous droits réservés.
