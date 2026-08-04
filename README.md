# Exercice d'attention et de temps de réaction

**▶ [Lancer l'exercice](https://pouf.github.io/ortho/)**

Parcours d'obstacles en vue de dessus : un mobile progresse dans un couloir,
des carrés apparaissent sur sa trajectoire, il faut s'en écarter. L'exercice
mesure le temps de réaction et rend un récapitulatif chiffré en fin de partie.

## Utilisation

En ligne via le lien ci-dessus, ou hors ligne en ouvrant `index.html` dans un
navigateur — un simple double-clic suffit. Rien à installer : le fichier est
autonome, sans dépendance ni requête réseau, et fonctionne aussi bien depuis le
disque que depuis un serveur.

Navigateurs : Chrome, Edge ou Firefox à jour.

## Commandes

Manette et clavier fonctionnent **en parallèle** — la commande la plus ample
l'emporte, il n'y a rien à sélectionner.

| | Manette | Clavier |
|---|---|---|
| Se déplacer | stick gauche ou croix directionnelle | flèches, ZQSD ou WASD |
| Démarrer | A ou Start | Entrée |
| Arrêter en cours | — | Échap |

Le déplacement est **proportionnel à l'amplitude** du stick : une inclinaison
partielle donne un déplacement lent. Le clavier étant en tout-ou-rien, il
commande toujours l'amplitude maximale.

L'écran d'accueil affiche un diagnostic de manette (nom, position des axes en
direct) et la fluidité mesurée en images par seconde.

> Sur Chrome et Edge, une manette reste invisible tant qu'aucun de ses boutons
> n'a été pressé : appuyer sur un bouton pour l'activer.

## Réglages

- **Mode** — défilement automatique (commandes gauche/droite seulement) ou
  avance commandée (haut, gauche, droite et diagonales)
- **Vitesse** — en mode automatique, vitesse de début et de fin, avec une rampe
  progressive entre les deux ; en mode manuel, vitesse maximale d'avance
- **Fréquence des obstacles**, **durée**, **vitesse de déplacement latéral**
- **Zone morte** du joystick, en pourcentage

Le couloir ne peut jamais se boucher : une apparition qui ne laisserait pas un
passage assez large est rejetée. Le parcours reste franchissable à toutes les
fréquences.

## Récapitulatif de fin

Affiché à la fin de la durée prévue ou dès l'arrêt anticipé :

- obstacles rencontrés, évités et touchés (nombre et pourcentage)
- contacts avec les murs
- **temps de réaction** — délai entre l'apparition d'un obstacle situé sur la
  trajectoire et la première variation de commande dans le sens de l'esquive.
  La mesure est relative à la commande tenue au moment de l'apparition : elle
  reste donc valable si le joystick n'a pas été ramené au neutre entre-temps.
- **retour au neutre** — temps mis pour relâcher la commande une fois
  l'obstacle franchi
- l'ensemble des réglages employés, pour pouvoir comparer deux parties

## Notes techniques

Canvas 2D en résolution logique fixe (1200 × 900), mise à l'échelle à
l'affichage : la difficulté ne dépend pas de la taille de l'écran. Entrées via
la Gamepad API, avec zone morte radiale réétalée sur [0, 1] pour conserver
toute la course utile du stick. Les éléments visuels sont dessinés par le code,
sans image externe.

État : prototype.
