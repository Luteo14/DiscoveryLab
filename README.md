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
