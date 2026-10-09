# Lode

Un jeu de plateforme et de réflexion inspiré de *Lode Runner* (1983), fait pour se jouer au doigt dans le navigateur d'un téléphone.

Ramassez tout l'or du niveau, creusez des trous dans la brique pour piéger les gardes, puis montez par l'échelle cachée qui apparaît en haut de l'écran.

## Jouer

Le jeu tient dans un seul fichier, `index.html`, sans dépendance ni build.

- **En local** : `python3 -m http.server` dans ce dossier, puis ouvrir `http://<ip-de-votre-ordi>:8000` sur le téléphone (même Wi-Fi).
- **En ligne** : activer GitHub Pages sur la branche principale (Settings → Pages). L'URL `https://<utilisateur>.github.io/<dépôt>/` s'ouvre sur mobile, et « Ajouter à l'écran d'accueil » installe le jeu en plein écran, jouable hors ligne.

## Commandes

| Mobile | Clavier | Action |
| --- | --- | --- |
| Croix directionnelle (glisser le pouce, diagonales acceptées) | Flèches, ZQSD ou WASD | Courir, grimper, se suspendre, lâcher une corde |
| Bouton CREUSE gauche / droit | J / K | Creuser la brique en bas à gauche / à droite |
| Bouton pause | Échap ou P | Pause, recommencer le niveau |

En portrait, la loupe dans la barre du haut bascule entre vue zoomée (la caméra suit le joueur) et vue entière.

## Règles

- Les briques rouges se creusent, le béton gris non. Certaines briques sont fausses et on passe à travers.
- Un trou se rebouche après environ 6 secondes. Un garde qui tombe dedans reste coincé un moment et lâche l'or qu'il porte. S'il y est encore quand le trou se referme, il est écrasé et réapparaît en haut. Le joueur aussi peut se faire enfermer.
- On peut marcher sur la tête d'un garde coincé.
- Or : 250 points, garde piégé ou écrasé : 75, niveau terminé : 1500 et une vie en plus.

## Ajouter des niveaux

Les niveaux sont dans `index.html`, entre `/*LEVELS*/` et `/*END LEVELS*/` : 14 lignes de 22 caractères.

```
' ' vide      # brique     @ béton      H échelle     - corde
X fausse brique             S échelle cachée (apparaît une fois l'or ramassé)
$ or          P joueur (un seul)        E garde
```

La rangée du haut ne doit être atteignable que par une échelle `S` : c'est la sortie.

## Fichiers

- `index.html` : le jeu (moteur, rendu canvas, commandes tactiles, niveaux)
- `manifest.webmanifest`, `sw.js`, `icon*.png`, `icon.svg` : installation sur l'écran d'accueil et mode hors ligne
