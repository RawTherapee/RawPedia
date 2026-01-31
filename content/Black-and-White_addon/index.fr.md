---
title: Black-and-White addon
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Noir-et-Blanc Supplément

</div>

## Les différentes méthodes

### Généralités

L'outil "Noir et Blanc" est organisé au travers de trois méthodes, qui
produisent chacune un rendu noir et blanc différent.

1.  Désaturation;
2.  Egaliseur de Luminance;
3.  Mixeur de Canaux

A noter que Rawtherapee permet de produire des images noir et blanc sans
l'usage de cet outil.

1.  en réglant à -100 le curseur
    [Saturation](exposure/fr#saturation) dans l'outil
    [Exposition](exposure/fr) de l'onglet Exposition;
2.  en réglant à -100 le curseur
    [Chromaticité](lab_adjustments/fr#chromaticité) dans
    l'outil [Ajustements Lab](lab_adjustments/fr) de l'onglet
    Exposition;
3.  en activant les [simulations de
    films](Film_Simulation/fr.md) Noir et Blanc (films Ilford,
    Kodak, Fuji...)

Néanmoins seules les méthodes utilisées dans l'outil "Noir et Blanc",
permettent son exploitation maximum.

Afin d'assurer un gris parfait, sauf dans le cas ou [Virage
partiel](Color_Toning/fr.md) est activé, comme le module
"Ajustements Lab" est situé en fin de processus de traitement, les
valeurs "a" et "b" de [Ajustements Lab](lab_adjustments/fr)
de l'onglet "Exposition" sont mises à zéro.

A noter également l'interaction avec l'outil [Virage
partiel](Color_Toning/fr.md), voir le [paragraphe Virage
partiel](#Virage_Partiel.md) ci-dessous.

### Désaturation

Cette méthode est telle que chaque pixel (R=G=B) se voit attribuer la
valeur de la luminance équivalente L=0.299\*r + 0.587\*g + 0.114\*b.
Elle assure un gris neutre sur toute l'image. A noter que les 2 autres
méthodes de type désaturation présentes dans Rawtherapee donnent des
résultats différents du fait d'algorithmes différents. Dans
"Exposition", c'est le canal "s" de TSV qui est mis à zéro. Dans
"Ajustements Lab", c'est la chromaticité C=sqrt(a\*a+b\*b) qui est mise
à zéro.

### Egaliseur de luminance

Cette méthode utilise [une courbe
plate](General_Comments_About_Some_Toolbox_Widgets/fr#La_Courbe_Plate.md),
où la luminance peut varier en fonction de la teinte.

L'algorithme utilise une conversion RVB ==\> LCT \[modification de L en
fonction de H\] ==\> RVB avec contrôle du gamut.

Contrairement à d'autres logiciels du commerce qui agissent par curseurs
sur un nombre limité de couleurs, vous pouvez interagir sur l'ensemble
de la palette colorée.

En final,les valeurs R, V, B sont mises au même niveau afin d'assurer un
gris parfait.

Il y a un contrôle du gamut, mais ceci n'empêche pas d'avoir la
possibilité d'obtenir de très bons effets spéciaux en déplaçant la
courbe vers les valeurs extrêmes.

Ici, la pipette est très utile. Par exemple, choisissez avec la pipette
une zone de teinte que vous souhaitez obscurcir. La couleur est repérée
dans le graphique de la courbe. A cet emplacement déplacer la courbe
vers le bas (obscurcir), ou vers le haut (éclairer).

### Mixeurs de canaux

C'est la méthode qui apparemment présente le plus de complexité !

Elle est pourtant d'une explicitation très simple : cette technique
consiste à utiliser un mélangeur de canaux de manière à apporter un soin
minutieux à l'équilibre entre les différentes composantes
colorimétriques de l'image, afin d'harmoniser la répartition des tons
clairs, moyens et foncés. Ceci revient à prendre un pourcentage de
chaque canal (R,V,B) et de les assembler !

Le lecteur avisé remarquera qu'un esprit mathématique dira que la somme
des 3 canaux doit être à 100%, si l'on veut éviter de brûler les hautes
lumières ! Ce même lecteur envisagera des coefficients positifs, car
logiques, mais point de valeurs négatives !

Mais que nenni ce serait faire fi de la créativité, ouvrons donc la
porte :

a\) aux valeurs supérieures à 100% ;

b\) aux coefficients négatifs.

Avec ces 2 ouvertures qu'il va falloir gérer, vos pourrez accéder aux
effets spéciaux, aux filtres de couleurs - dont l'infrarouge, mais aussi
à des réglages courants comme paysages, portrait, contraste, etc.

#### Les composantes du mixeur

##### Préréglages

Il permet de choisir entre :

- certains réglages prédéfinis du mixeur (Contraste Normal, Contraste
  Elevé, Luminance, Portrait, Paysage, Basse et Haute Sensibilité,
  Panchromatique, Hyper Panchromatique, Orthochromatique, Infrarouge);
- des réglages à disposition de l'utilisateur selon 4 critères:

1.  **RVB Absolu** : dans ce cas, il est offert à l'utilisateur de
    mélanger les 3 canaux principaux R,V,B, mais sans contrôle des
    limites. On peut entrer des valeurs positives où négatives avec une
    somme inférieure, égale ou supérieure à 100%.
2.  **RVB Relatif** :dans ce cas, il est offert à l'utilisateur de
    mélanger les 3 canaux principaux R,V,B,mais avec contrôle des
    limites. On peut entrer des valeurs positives où négatives, mais
    dans tous les cas, le total sera ramené à 100%. Par exemple si vous
    entrez R=10% G=10% B=30%, cela sera équivalent à R=20% G=20% B=60%.
    Ce mode est celui "par défaut" utilisé par tous les préréglages
    fixes comme "Paysage": R=66% G=24% B=10%. Ce réglage est le plus
    intuitif, le plus simple, surtout si on n'entre pas de valeurs
    négatives.
3.  **ROJVCBPM Absolu**²² : (pour Rouge Orange Jaune Vert Cyan Bleu
    Pourpre Magenta). Pour l'anecdote, ce mixeur à 8 couleurs provient
    je pense d'une incompréhension, un utilisateur habitué à Lightroom,
    où est présent un "Égaliseur de Luminance" (alors que celui-ci
    n'était pas encore dans le module Noir et Blanc de Rawtherapee), a
    demandé l'extension du mixeur de 3 à 8 couleurs. Ce mixeur "spécial"
    possède 2 options intéressantes:
    - ajuster les couleurs complémentaires - dans ce cas, lorsqu’on agit
      sur un des curseurs "OJCPM", une correction est automatiquement
      assurée sur les couleurs complémentaires principales (rouge, vert,
      bleu);
    - algorithme OJCPM: lorsqu'il est sur "Linear", la réponse est
      strictement proportionnelle à la force souhaitée et interagit
      directement et proportionnellement sur les 2 couleurs principales,
      par exemple "orange", interagit sur "rouge" et "vert"; à l'inverse
      "Special effects" - comme son nom l'indique introduit des
      bizarreries dans la "conversion" de "orange" vers "rouge" et
      "vert" (réponse non linéaire, avec interaction possible sur le
      bleu selon les valeurs des curseurs).

      
    Ce réglage et de loin le moins intuitif, là où la créativité sera
    maximum.
4.  **ROJVCBPM** Relatif : comme ci-dessus, mais en conservant un total
    de 100% pour les 3 canaux principaux (Rouge Vert Bleu)

##### Filtre de couleur

Le filtre de couleur simule les prises de vues avec un filtre coloré
placé devant l'objectif. Ces filtres réduisent la transmission d'une
plage de couleur spécifique et affectent la luminosité. Par exemple un
filtre rouge assombrit les ciels bleus et éclaircit les rouges. Ce
filtre joue comme un multiplicateur vis-à-vis des réglages obtenus après
"Préréglages".

##### Auto

Ce bouton active un algorithme qui opère un calcul sur l'ensemble de
l'image et équilibre strictement les 3 canaux Rouge - Vert - Bleu pour
donner à chaque couleur le même poids relatif.

#### Avertissements

Vous pouvez constater après actions sur les réglages possibles dans
"Préréglages" (y compris avec "Ajuster les couleurs complémentaires" et
"Algorithm OYCPM"), l'incidence sur le seul véritable réglage final du
mixeur de canaux. La ligne située sous "Préréglages" fait apparaître 4
nombres, par exemple R:37.2% V=-82.3% B=126,6% Total=155%. Dans ce cas,
la luminosité globale de l'image sera 55% plus importante que
l'originale, et chaque pixels verra ses valeurs multipliées - avant
mixage - par les 3 données précédentes.

Pour les valeurs positives et en mode relatif, le résultat est
prédictible... C'est le mode le plus courant de ce mixeur (encore appelé
mélangeur) de canaux. Par exemple on trouve sur le web, des valeurs à
entrer pour simuler des films noir et blanc par exemple "Ilford Delta
100 : 21,42,37", etc.

A l'inverse, le mode absolu, les valeurs négatives, l'utilisation des
curseurs "OJCPM" et de l'algorithme "Special effects", peut aboutir à
des résultats inattendus : écran noir, artefacts,...

## Correction gamma

Vous pouvez changer le rendu des tons de chaque canal (R,V,B), en
modifiant le gamma. Cette commande simule sensiblement le rendu des
papiers sous l'agrandisseur (dur, normal, doux). Plus les curseurs
seront à gauche (valeurs inférieures à zéro) plus l'image sera sombre et
contrastée, plus ils seront à droite (valeurs positives) plus l'image
sera douce. Attention, il n'y a pas de bug pour le canal Bleu : en effet
le choix fait d'utiliser Prophoto, comme profil de travail, rend le
canal bleu peu opérant. Il suffit de choisir sRGB pour voir l'effet.

## Courbes avant après

Ces courbes ont un mode d'emploi et une finalité identique à ce qui est
décrit dans le chapitre [Courbes
tonales](Exposure/fr#Courbes_tonales.md) de l'outil
[Exposition](exposure/fr).

Elles permettent une personnalisation du module "Noir et blanc", le
rendant ainsi "indépendant" des modifications pouvant être réalisées par
ailleurs.

A noter que la courbe "après" ne dispose que d'un seul "mode", car
l'image est maintenant en noir et blanc !

## Virage Partiel

Vous pouvez utiliser [Virage partiel](color_toning/fr) avec
l'outil Noir et Blanc pour produire des effets spéciaux.

Vous pouvez également utiliser [Virage
partiel](Color_Toning/fr.md) avec les simulations de film noir
et blanc à condition d'activer l'outil Noir et Blanc.

L'architecture (l'emplacement des divers outils dans le processus de
traitement), ainsi que les algorithmes "Virage partiel" et "Noir et
Blanc" ont été adaptés afin de profiter au maximum des effets conjugués.

Tous les modules de "Virage partiel" permettent une action conjuguée.
Néanmoins c'est [Balance Couleur Ombres / Tons moyens / Hautes
lumières](Color_Toning/fr#Balance_Couleur_Ombres/_Tons_Moyens_/_Hautes_Lumières.md)
qui donnera le plus de possibilités. Essayez des allers et retours entre
les [Balance Couleur Ombres / Tons moyens / Hautes
lumières](Color_Toning/fr#Balance_Couleur_Ombres/_Tons_Moyens_/_Hautes_Lumières.md)
et par exemple [Mixage
Lab](Color_Toning/fr#Particularités_Mixage_Lab_et_RVB_curseurs.md),
essayez les gammas et les courbes avant après.

Bien sûr l'atteinte des résultats devra faire l'objet d'itérations
essais-erreurs, si vous recherchez des effets spéciaux.
