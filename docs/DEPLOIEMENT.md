# Guide de déploiement — DISCOVER // LAB

## Prérequis
Un compte GitHub et un compte Cloudflare. Cette livraison est un projet **prêt à configurer**, pas un service déjà déployé. Aucun accès aux comptes n'a été fourni.

## 1. Cloudflare D1
Dans Cloudflare > Workers & Pages > D1, créer la base `luteo14-discover-lab`. Copier son identifiant dans `worker/wrangler.toml` à la place de `REMPLACER_PAR_ID_D1`.

## 2. Cloudflare Worker
Créer un Worker nommé `luteo14-discover-lab-api` et publier le contenu de `worker/index.js`. Configurer la liaison D1 `DB` avec la base créée, et la variable `ALLOWED_ORIGINS` avec `https://luteo14.github.io` (sans barre finale). Ajouter le secret `ADMIN_TOKEN` (valeur longue et aléatoire) dans les secrets du Worker, jamais dans GitHub ou le JavaScript du site. Appliquer le SQL de `worker/migrations/0001_init.sql` dans la console D1. L'usage de Wrangler (outil officiel) permet aussi de déployer ce dossier et d'appliquer les migrations ; il nécessite une authentification Cloudflare.

## 3. GitHub Pages
Créer un dépôt GitHub public, par exemple `discover-lab`, et y ajouter les fichiers du dossier racine (`index.html`, `css`, `js`, etc.). Dans Settings > Pages, sélectionner Deploy from a branch, branche main, dossier `/ (root)`. L'URL attendue dépendra du nom réel du dépôt : ne pas la présumer définitive.

## 4. Connecter le site à l'API
Après publication du Worker, copier son URL HTTPS dans `js/config.js` comme valeur de `apiBase`, par exemple `https://NOM-REEL.workers.dev` (sans `/api`). Publier cette modification dans GitHub.

## 5. Vérifier
Ouvrir le site, déposer une contribution test avec un code atelier de 3 caractères minimum, puis ouvrir Animation avec ce code et le secret `ADMIN_TOKEN`. Vérifier qu'elle apparaît en `pending`. Cliquer sur Valider, puis ouvrir Remontées : elle doit être visible. Masquer la contribution et vérifier qu'elle disparaît de la vue collective. Tester l'export CSV.

## 6. Fonctionnement hybride
Avant : communiquer le code atelier et collecter les contributions. Pendant : valider les contributions et projeter Remontées. Après : exporter le CSV et conserver l'historique D1.

## 7. Confidentialité et sécurité
Les contributions sont privées par défaut (statut `pending`). La vue collective ne contient pas les noms. Le secret animateur n'est pas stocké dans le dépôt, mais il est saisi dans le navigateur lors de l'animation. Ne pas utiliser cette version pour des données confidentielles ou sensibles sans ajouter une authentification forte (Cloudflare Access), des règles de conservation et des protections anti-abus/rate limiting. Le code atelier n'est pas un mécanisme d'autorisation. Les contributions approuvées sont accessibles à quiconque connaît le code atelier. Prévoir une information RGPD, une durée de conservation et un mécanisme de suppression avant un usage réel en entreprise.

## 8. Limites de cette V1
Pas de vote, de création d'ateliers sécurisée, de gestion multi-animateurs, de statistiques avancées ni de temps réel par WebSocket : la vue collective est rafraîchie manuellement. Le secret administrateur est commun à tous les ateliers. L'API ne dispose pas encore de limitation de débit. Les données sont stockées dans D1 et ne sont pas sauvegardées automatiquement dans GitHub. Prévoir une stratégie de sauvegarde D1 et de suppression des données.
