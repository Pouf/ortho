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
| Mettre en pause / reprendre | Start | Espace ou P |
| Arrêter en cours | — | Échap |

Pendant la pause, le chronomètre et toutes les mesures sont suspendus : une
interruption au milieu d'un exercice ne fausse pas les temps de réaction.

Le déplacement est **proportionnel à l'amplitude** du stick : une inclinaison
partielle donne un déplacement lent. Le clavier étant en tout-ou-rien, il
commande toujours l'amplitude maximale.

Le **stick employé se choisit dans les réglages**, gauche ou droit, dans tous
les modes. Le stick droit permet de tenir la manette par-dessous d'une seule
main et de commander au pouce, sans qu'un tiers ait à la maintenir. Le choix
apparaît dans le récapitulatif, et le diagnostic signale une manette qui
n'exposerait pas le stick demandé.

L'écran d'accueil affiche un diagnostic de manette (nom, position des axes en
direct) et la fluidité mesurée en images par seconde.

> Sur Chrome et Edge, une manette reste invisible tant qu'aucun de ses boutons
> n'a été pressé : appuyer sur un bouton pour l'activer.

## Réglages

- **Mode** — défilement automatique (commandes gauche/droite seulement), avance
  commandée (haut, gauche, droite et diagonales), ou arrêt contrôlé (voir plus bas)
- **Vitesse** — en mode automatique, vitesse de début et de fin, avec une rampe
  progressive entre les deux ; en mode manuel, vitesse maximale d'avance
- **Durée**, en minutes
- **Largeur de la zone de jeu**, au curseur, de 380 à 1100 px — c'est à la fois
  la zone de déplacement et la zone d'apparition des obstacles. Plus elle est
  large, plus les écarts à faire sont grands.
- **Fréquence des obstacles** et **vitesse de déplacement latéral**
- **Zone morte** du joystick, en pourcentage

Le couloir ne peut jamais se boucher : une apparition qui ne laisserait pas un
passage assez large est rejetée. Le parcours reste franchissable à toutes les
fréquences.

## Mode « arrêt contrôlé »

Ce mode ne travaille pas l'esquive mais le freinage. Le couloir est étroit, la
trajectoire rectiligne, et la commande latérale est ignorée : seule la poussée
vers l'avant agit.

Une barrière barre le couloir, précédée d'une **zone d'arrêt** matérialisée au
sol. Il faut s'immobiliser dans cette zone en ramenant le joystick au neutre et
en l'y maintenant le temps demandé — un relâchement fugace ne valide pas, le
compteur repart de zéro. L'arrêt validé fait disparaître la barrière et la
suivante se présente.

En cas de dépassement, le personnage bute contre la barrière et **reste bloqué
tant que le joystick n'est pas revenu au neutre**. La progression ne reprend
qu'une fois la commande relâchée.

Le rythme d'approche est libre : rien n'oblige à avancer vite, on peut sécuriser
l'arrêt en s'approchant lentement.

Réglages propres à ce mode : **profondeur de la zone d'arrêt** (plus elle est
courte, plus le freinage doit être précis) et **durée d'arrêt à tenir**.

Mesures rendues : arrêts réussis et dépassements, **marge d'arrêt moyenne**
(distance restant à la barrière au moment de la validation), **temps de
relâchement** (entrée en zone → retour au neutre), délai de relâchement après un
blocage, et vitesse moyenne au dépassement.

## Option « ordres STOP »

Cochable en défilement automatique et en déplacement manuel, cette option ajoute
des ordres d'arrêt imprévisibles par-dessus l'exercice en cours. Un grand **STOP**
surgit à intervalle tiré au hasard entre deux bornes réglables ; il faut ramener
le joystick au neutre dans le délai imparti, puis l'y maintenir.

Un ordre n'est donné que si le joystick est effectivement tenu à ce moment-là :
au neutre, la consigne serait déjà satisfaite et la mesure vide de sens.

Passé le délai, l'échec est signalé mais **l'ordre reste affiché jusqu'au
relâchement effectif** — le geste est toujours mené à son terme, et le
dépassement est mesuré.

En défilement automatique, le décor se fige pendant toute la durée de l'ordre :
le défilement n'y est pas commandé au joystick, et sans ce gel un obstacle
pourrait arriver au moment précis où l'ordre demande de lâcher le stick. En
déplacement manuel il n'y a pas de gel : c'est le relâchement lui-même qui
arrête la progression.

Réglages : **délai imparti** en millisecondes, **bornes de l'intervalle** entre
deux ordres, et **durée d'arrêt à tenir** (réglage commun avec l'arrêt contrôlé).

Mesures rendues : ordres donnés, arrêts dans le délai et hors délai, temps de
relâchement moyen et maximal, dépassement moyen du délai sur les échecs.

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
- le nombre de pauses et leur durée cumulée
- l'ensemble des réglages employés, pour pouvoir comparer deux parties

## Notes techniques

Canvas 2D en résolution logique fixe (1200 × 900), mise à l'échelle à
l'affichage : la difficulté ne dépend pas de la taille de l'écran. Entrées via
la Gamepad API, avec zone morte radiale réétalée sur [0, 1] pour conserver
toute la course utile du stick. Les éléments visuels sont dessinés par le code,
sans image externe.

État : prototype.
