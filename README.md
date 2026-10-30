# Site web de Score Cartes

Site statique de l'application iOS **Score Cartes** (accueil, assistance, politique de confidentialité), en trois langues.
Il est publié avec GitHub Pages ; l'URL de la politique de confidentialité et celle de l'assistance
sont celles à saisir dans App Store Connect.

```
website/
  index.html            accueil (français)          en/index.html   de/index.html
  assistance.html       assistance (FAQ + contact)  en/support.html  de/support.html
  confidentialite.html  confidentialité             en/privacy.html  de/datenschutz.html
  css/style.css  assets/
.github/workflows/pages.yml   déploie website/ à chaque push sur main
```

Le site existe en **français** (à la racine), **anglais** (`en/`) et **allemand** (`de/`). Chaque page porte un sélecteur
FR / EN / DE dans l'en-tête et des liens `hreflang` ; le choix est mémorisé (`localStorage`). À la première visite, une
page française redirige vers l'anglais ou l'allemand si la langue du navigateur est l'une des deux. Les trois versions sont
des fichiers HTML écrits à la main : toute modification de contenu se fait dans **les trois**.

Adresses à saisir dans App Store Connect, par langue de la fiche :

| Langue | URL marketing | Assistance | Confidentialité |
|---|---|---|---|
| Français | `/` | `/assistance.html` | `/confidentialite.html` |
| English | `/en/` | `/en/support.html` | `/en/privacy.html` |
| Deutsch | `/de/` | `/de/support.html` | `/de/datenschutz.html` |

(toutes précédées de `https://scorecartes.jepico.fr`)

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

- Les pages doivent suivre l'app : jeux pris en charge (accueil, assistance), fonctions (scan, compte rendu PDF, iCloud, langues) et, surtout, ce que dit la politique de confidentialité des données (iCloud, partage). Les textes de la fiche App Store sont dans le dépôt de l'app (`appstore/textes-fiche.md`).
- La date « dernière mise à jour » de la politique de confidentialité, dans les trois langues, si elle change (dernière : 30 octobre 2026).
- Le bouton « Bientôt sur l'App Store » des trois pages d'accueil (`index.html`, `en/index.html`, `de/index.html`) : remplacer par le lien de la fiche une fois publiée.
