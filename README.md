# Site web de Score Cartes

Site statique de l'application iOS **Score Cartes** (accueil, assistance, politique de confidentialité).
Il est publié avec GitHub Pages ; l'URL de la politique de confidentialité et celle de l'assistance
sont celles à saisir dans App Store Connect.

```
website/
  index.html            accueil
  assistance.html       questions fréquentes + contact
  confidentialite.html  politique de confidentialité
  css/style.css  assets/
.github/workflows/pages.yml   déploie website/ à chaque push sur main
```

## Prévisualiser en local

```bash
cd website && python3 -m http.server 8000     # puis http://localhost:8000
```

## Publier

Un push sur `main` déclenche le déploiement (Settings → Pages → Source : **GitHub Actions**).

Domaine : **https://scorecartes.jepico.fr** (fichier `website/CNAME`). Côté OVH, zone DNS de `jepico.fr` :
un enregistrement **CNAME** `scorecartes` → `jet4git.github.io.` (comme `caveavin`). Le domaine
`jepico.fr` est déjà vérifié sur le compte GitHub (TXT `_github-pages-challenge-jet4GIt`).
Une fois le DNS propagé, GitHub délivre le certificat (jusqu'à ~1 h) puis on active « Enforce HTTPS ».
URL de secours sans domaine : `https://jet4git.github.io/site-web-scorecartes/`.

## À tenir à jour

- La date « dernière mise à jour » de la politique de confidentialité, si elle change.
- Le bouton « Bientôt sur l'App Store » de `index.html` : remplacer par le lien de la fiche une fois publiée.
