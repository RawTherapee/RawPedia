---
title: Color Toning
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Virage partiel

</div>

## Introduction

![](Rt55_color_toning_grids_1_mask_on.png "Rt55_color_toning_grids_1_mask_on.png")
![](Rt55_color_toning_grids_1_mask_off.png "Rt55_color_toning_grids_1_mask_off.png")

La première question qui se pose est : quelle est la définition ou
qu'entends-t-on par "Virage partiel" ou "Color Toning" ou "Split Toning"
? En effet lorsqu'on consulte le web, le plus souvent on tombe sur
quelque chose comme : "Virage partiel consiste à colorer une image noir
et blanc de manière différenciée dans les hautes et dans les basses
lumières", par exemple colorer les hautes lumières en jaune et les
basses en bleu.

En étendant le concept, il est possible de mettre sous la même
définition:

- le virage d'une image couleur qui permet d'ajouter une dominante de
  couleurs dans l'image. Cette dominante pourra être réglée dans les
  zones claires et/ou foncées de l'image.
- étendre le virage à l'ensemble du spectre de la luminance, et non de
  façon limitative aux basses et hautes lumières

Dans Rawtherapee, deux types d'algorithmes essaient de répondre aux
principes définis ci-dessus :

- Mélange à partir de couleurs cibles (blending) : dans ce cas une
  valeur chromatique est pondérée selon une formule de type : "teinte
  résultante"= "teinte source" + ("teinte cible" - "teinte source")\*
  balance où balance est un coefficient compris entre zéro et 1. On
  trouve facilement sur le web des références à ce type d'algorithme
- Addition et réduction des canaux RVB" (addition) : dans ce cas, selon
  la luminance (ombres/tons moyens/hautes lumières), chaque canal est
  amplifié en même temps que les deux autres canaux sont réduits. Par
  exemple une action sur le canal rouge, pour une certaine tranche de
  luminance, se traduira par "R" accru de X% en même temps que "V" et
  "B" seront réduits de X%. Attention ce n'est pas un "mixeur"
  (mélangeur) de canaux. Je n'ai pas trouvé de références à ce type
  d'algorithmes, mais en observant le comportement du module "Color
  Balance" de Photoshop, je pense avoir imaginé un algorithme qui donne
  des résultats semblables.

Par expérience, le premier type d’algorithme donnera de bons résultats
en virage d'une image couleur mais en étant peu facilement prédictible,
et je serais plus nuancé pour son utilisation en noir et blanc, même si
bien sûr il donne des résultats satisfaisants. Cet algorithme est
implanté de deux manières différentes - il n'y en a pas une meilleure
que l'autre - qui donnent des résultats variés:

- Mode RVB : chaque canal R, V, B, se voit attribué l'algorithme repris
  en (i).
- Mode Lab : chaque composante couleur "a" (canal rouge vert") et "b"
  (canal "bleu jaune") se voit attribué l'algorithme repris en (i). Ce
  mode permet selon les choix proposés (menus) une prédictibilité
  normale ou une créativité importante.

Le second type d'algorithme peut avoir 3 usages selon le curseur
"Force":

- En utilisant de faibles valeurs, l'utilisateur peut simuler une
  "balance des couleurs" et ajuster finement la colorimétrie
- En utilisant de fortes valeurs, l'utilisateur pourra, en mode
  "couleur", obtenir des résultats semblables à ceux de l'algorithme
  "blend", mais avec moins de créativité
- En utilisant de fortes valeurs, l'utilisateur pourra, en mode "noir et
  blanc", obtenir des effets spéciaux très marqués.

## Méthodes

### Méthodes "mixage"

Les méthodes "mixage" se décomposent en **Mixage Lab** qui utilise les 2
composantes chroma lab "a" et "b", et **RVB curseurs** et **RVB
courbes** qui utilisent le même algorithme RVB, mais différent par
l'interface utilisateur.

La méthode Lab, isole la composante couleur de la luminance, alors que
les 2 méthodes RVB agissent indirectement sur la luminance. Cette
différence explique en partie les écarts de comportement de ces
méthodes.

Même si la forme est différente (curseurs ou courbes), les 2 méthodes
RVB, n'utilisent qu'un seul type d'opacité (le contrôle du mélange des
couleurs), alors que le mode Lab en propose quatre. La première "Chroma
standard" est semblable à celle utilisée dans "RGB courbes". Les 3
autres autorisent des effets spéciaux.

Les courbes utilisées sont des courbes plates spéciales.

1.  la courbe couleur reprend en abscisse la luminance et en ordonnée
    les teintes cibles. Les deux barres verticales délimitent les
    principales zones résultantes. En faisant varier :
    - les positions des barres verticales;
    - la forme de la courbe;
    - les choix des teintes cibles;

      
    On obtiendra des résultats différents
2.  la courbe opacité (Chroma Standard et RVB courbes) reprend en
    abscisse la luminance et en ordonnée l'opacité (encore appelée
    Balance) qui traduit la manière dont sont assemblées la teinte
    origine (image) et la teinte cible, dans ce cas l'opacité est
    comprise entre 0 et 1. Plus la courbe sera haute, plus le mélange
    s'approchera de la teinte cible. La courbe opacité mise à zéro, ne
    modifie pas l'image.

Le réglage de la saturation (l'intensité maximale des effets) peut être
ajusté :

1.  Manuellement, dans ce cas "Automatic" n'est pas activé. Vous pouvez
    agir sur les 2 curseurs "seuil" et "Protection"
2.  Automatique, dans ce cas "Automatic" est activé. Un algorithme tient
    compte de l'espace de travail (sRGB, Adobe, Prophoto...) et de la
    saturation des pixels de l'image, pour déterminer des valeurs
    optimales de "seuil" et "Protection"
      
    Ces réglages sont évidemment sans effet pour les images converties
    en Noir et Blanc

#### Particularités Mixage Lab et RVB curseurs

##### Chroma spécial

Ici, la courbe plate est remplacée par une courbe diagonale. Les 2
composantes chroma "a" et "b" (Lab) sont modifiées avec la même
amplitude. Si vous déplacez la courbe sous la diagonale, vous
introduisez des valeurs d'opacité négatives, qui vont amener des effets
spéciaux souvent imprédictibles.

##### Chroma spécial a\* et b\*

Ici, la courbe plate est remplacée par deux courbes diagonales. Les 2
composantes chroma "a" et "b" (Lab) sont modifiées séparément par 2
courbes différentes. La première n'agit que sur la composante "a" (Lab)
, c'est à dire la dimension rouge-vert. La seconde n'agit que sur la
composante "b" (Lab) , c'est à dire la dimension bleu-jaune. Si vous
déplacez la(es) courbe(s) sous la diagonale, vous introduisez des
valeurs d'opacité négatives, qui vont amener des effets spéciaux souvent
imprédictibles

##### Chroma spécial 2 couleurs

Ici, comme dans "Chroma special" la courbe plate est remplacée par une
courbe diagonale. Les 2 composantes chroma "a" et "b" (Lab) sont
modifiées avec la même amplitude. Si vous déplacez la courbe sous la
diagonale, vous introduisez des valeurs d'opacité négatives, qui vont
amener des effets spéciaux souvent imprédictibles.

La différence avec "Chroma Special" tient dans l'utilisation de la
courbe couleur. Dans "chroma special", l'ensemble de la courbe
teinte=f(Luminance) est utilisée, dans le cas "Chroma special 2
couleurs", seules les 2 teintes repérées par les barres verticales sont
utilisées.

##### RVB Curseurs

L'ergonomie recherchée vise à se rapprocher de celle de Lightroom (comme
par ailleurs "Saturation 2 couleurs").

Vous disposez de 2 curseurs à deux niveaux, le premier pour les hautes
lumières, le second pour les ombres. Pour chacun des deux curseurs vous
pouvez régler la teinte et la force souhaitée : les 2 curseurs forces
mis à zéro, n'amènent aucun changement à l'image.

Le curseur Balance permet d'équilibrer l'action entre les hautes et
basses lumières. En le déplaçant à gauche (valeurs négatives) l'action
sur les hautes lumières est accrue, à droite (valeurs positives), c'est
celle sur les basses lumières qui est accrue.

### Méthodes "Addition"

#### Balance Couleur Ombres/ Tons Moyens / Hautes Lumières

Cette méthode est très proche à la fois dans son mode d'emploi, et son
rendu du module de PhotoShop "Balance Couleur".

Vous pouvez agir différemment sur les ombres, les tons moyens et les
hautes lumières.

Chaque curseur agit sur une couleur et sa couleur complémentaire : Rouge
et Cyan, Vert et Magenta, Bleu et Jaune

Le curseur "Force" permet de régler la sensibilité du système :

1.  pour de faibles valeurs - inférieures à 50 - vous pouvez utiliser
    cet outil pour corriger la balance des couleurs de l'image modifiant
    ainsi le mélange d’ensemble pour aboutir à une correction
    chromatique généralisée.
2.  pour des valeurs moyennes , vous pouvez utiliser cet outil comme
    Virage partiel couleur
3.  pour des valeurs élevées , vous pouvez utiliser cet outil comme
    Virage partiel Noir et Blanc en interaction avec le module "Noir et
    Blanc" (les réglages internes de l'algorithme sont différents pour
    une action en couleur et en noir et blanc).

Sélectionnez "Préserver la luminance" pour empêcher la modification des
valeurs de luminosité dans l’image lors de la modification de couleur.
Cette option permet de conserver la balance des tons dans l’image.

#### Saturation 2 Couleurs

Cette méthode est proche dans son emploi et son rendu de ACR et
Lightroom.

Elle est essentiellement destinée au virage partiel couleur, même si son
usage peut être envisagé en conjugaison au module Noir et Blanc.

Vous disposez de 2 curseurs à deux niveaux, le premier pour les hautes
lumières, le second pour les ombres. Pour chacun des deux curseurs vous
pouvez régler la teinte et la force souhaitée : les 2 curseurs Force mis
à zéro, n'amènent aucun changement à l'image.

Le curseur Balance permet d'équilibrer l'action entre les hautes et
basses lumières. En le déplaçant à gauche (valeurs négatives) l'action
sur les hautes lumières est accrue, à droite (valeurs positives), c'est
celle sur les basses lumières qui est accrue.

Le curseur "Force" permet de régler la sensibilité globale du système.

Sélectionnez "Préserver la luminance" pour empêcher la modification des
valeurs de luminosité dans l’image lors de la modification de couleur.
Cette option permet de conserver la balance des tons dans l’image.

### Grille de Correction des Couleurs L\*a\*b\*

Harmonise les ombres et les hautes lumières en ajustant les nœuds noir
et blanc correspondants sur une grille de couleur.

Double cliquer sur un nœud pour le ramener à la position neutre

### Régions de correction L\*a\*b\*

Un outil puissant qui vous permet non seulement le virage partiel basé
sur un nombre quelconque de masques, mais permet aussi des effets de
l'[American Society of Cinematographers Color Decision List (ASC
CDL)](https://blender.stackexchange.com/a/55239).

## Interaction avec d'autres outils

### Noir et Blanc

C'est par des allers et retours entre l'outil [Noir-et-Blanc
Supplément](Black-and-White_addon/fr.md) - en particulier
l'outil [Egaliseur de
luminance](Black-and-White_addon/fr#Egaliseur_de_luminance.md)
et le module "Virage partiel" - en particulier [Balance Couleur Ombres/
Tons Moyens / Hautes
Lumières](Color_Toning/fr#Balance_Couleur_Ombres/_Tons_Moyens_/_Hautes_Lumières.md)
que vous obtiendrez les effets spéciaux (noir et blanc) les plus
marqués.

### Simulation de films

- Dans le cas de [simulation de
  filmscouleurs](Film_Simulation/fr.md), l'ensemble des modules
  "Virage partiel" est directement accessible
- Dans le cas de [simulation de films](film_simulation/fr)
  noir et blanc, il est indispensable d'activer le module "Noir et
  Blanc". La méthode
  [désaturation](black-and-white_addon/fr#désaturation) est
  quasiment neutre et permet un usage direct des simulations Noir et
  Blanc dans l'ensemble des modules "Virage partiel", mais sans pouvoir
  utiliser les effets spéciaux du module "Noir et Blanc"
