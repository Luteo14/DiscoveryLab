# LUTEO14 — DISCOVER // LAB

Application de Product Discovery hybride : collecte avant, pendant et après atelier, modération, consultation collective et export CSV.

- `index.html` : interface et parcours participant.
- `css/style.css` : thème visuel sombre inspiré de la structure éditoriale LUTEO14 SPORT (à ajuster si les styles sources sont fournis).
- `js/config.js` : URL publique de l'API.
- `js/app.js` : navigation, validation, soumission, modération et export.
- `worker/index.js` : API Cloudflare Worker.
- `worker/migrations/0001_init.sql` : tables D1.
- `worker/wrangler.toml` : configuration Worker à compléter.
- `docs/DEPLOIEMENT.md` : guide en français.

Aucune donnée fictive n'est affichée et aucune contribution n'est sauvegardée localement. Le déploiement effectif et les tests de bout en bout nécessitent vos comptes GitHub et Cloudflare.

## Refonte - Ateliers Product Discovery / Client Xperience

Le site contient désormais :
- **Accueil** : proposition de valeur DISCOVER // LAB.
- **La méthode** : 4 phases / exploration du problème et des solutions.
- **Les ateliers** : 8 fiches détaillées, déroulés, questions d'ouverture, livrables et filtres.
- **Client Xperience** : accès distinct à « Déposer une contribution » et « Explorer les remontées ».
- **Animateur** : gestion des statuts et export via l'API Cloudflare préexistante.

Les 8 ateliers sont présentés à titre de proposition modulable. Les durées et outils sont indicatifs.

**La refonte conserve la logique existante de stockage** : l'interface publique GitHub Pages est statique ; aucune contribution n'est enregistrée sans Worker Cloudflare opérationnel et base D1 configurée. Renseigner `js/config.js` après le déploiement de l'API. Ne jamais y insérer de secret.

**Documentation méthodologique** : inspirée des étapes générales décrites dans l'article WeFiiT « Qu'est-ce que la Product Discovery ? » https://www.wefiit.com/blog/product-discovery (vision, connaissance produit, marché, données, recherche utilisateur, priorisation et tests). Les textes et les huit déroulés sont des créations spécifiques pour DISCOVER // LAB.

**Publication GitHub Pages** : déposer le contenu du dossier `discover-lab/` à la racine du dépôt, puis `Settings > Pages > Deploy from a branch > main > /(root)`.
