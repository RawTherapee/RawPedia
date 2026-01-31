---
title: Demosaicing
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Dématriçage

</div>
![](Chipincamera.jpg "Chipincamera.jpg")
![](Bayer_pattern_on_sensor.svg "Bayer_pattern_on_sensor.svg")
![](Bayer_pattern_on_sensor_profile.svg "Bayer_pattern_on_sensor_profile.svg")

## Introduction

La plupart des appareils photo numériques utilisent un capteur qui
contient des millions d'éléments sensibles à la lumière, tous
identiques, appelés photosites. Dans le but de capter une couleur, un
[filtre couleur](https://en.wikipedia.org/wiki/Color_filter_array) est
placé devant le capteur, ainsi chaque photosite n'enregistre qu'une
longueur d'onde spécifique de la lumière. Le "[Filtre
Bayer](https://en.wikipedia.org/wiki/Bayer_filter)" est le plus répandu,
il utilise une matrice 2x2 répétitive de pastilles bleues, rouges ou
vertes. Il existe aussi une autre disposition de filtre appelé
"[X-Trans](https://en.wikipedia.org/wiki/Fujifilm_X-Trans_sensor)"
utilisé par certains appareils photo Fujifilm, avec une matrice 6x6
répétitive de pastilles. Etant donné que chaque photosite capture une
bande passante spécifique de lumière, il y a trois principaux problèmes
qui doivent être traités :

1.  Il n'existe encore aucun concept de couleur car chaque photosite
    n'enregistre qu'un simple signal électrique produit par les photons
    qui traversent le filtre et viennent le frapper,
2.  Il y a deux fois plus de photosites verts que de rouges ou de bleus,
3.  et la moitié (vert) ou les trois-quarts (rouge, bleu) de chaque
    canal de couleur sont en fait dépourvus d'information (photosites
    noirs, non exposés, puisqu'il n'y a par exemple qu'un photosite
    fltré en rouge sur quatre).

Afficher une image à partir d'un appareil photo équipé d'un capteur
Bayer ou X-Trans n'est donc pas immédiat, la mosaïque de points discrets
d'information nécessite d'être convertie en une image couleur cohérente.
Ce processus est appelé **dématriçage**.

RawTherapee offre plusieurs algorithmes de dématriçage, chacun avec ses
propres caractéristiques. Les différences entre eux peuvent être
subtiles, certaines ont besoin de zoomer à 100% ou plus pour découvrir
les nuances. Cependant puisque le dématriçage est la base sur laquelle
tous les autres outils travaillent, le choix de l'algorithme de
dématriçage peut avoir des effets visuellement significatifs sur le
résultat final, particulièrement en cas d'observation de près. Le choix
de l'algorithme de dématriçage influence principalement la qualité des
détails très fins de l'image et la visibilité d'artéfacts sous forme de
motifs en labyrinthes.

Concernant les appareils photo Bayer, AMaZE est généralement la meilleur
méthode pour les images prises à faible ISO, alors que LMMSE ou IGV sont
préférables pour les ISO plus élévés. Concernant les appareils X-Trans,
3-pass (Markesteijn) est généralement la meilleure méthode.

A noter que [le capteur Foveon
X3](https://en.wikipedia.org/wiki/Foveon_X3_sensor) n'utilise pas de
filtre couleur et en conséquence, les images produites par un appareil
équipé d'un tel capteur n'ont pas besoin de dématriçage. Elles ne sont
d'ailleurs pas supportées par RawTherapee.

<div align="center">

Image:Demosaicing city1 amaze.png\|AMaZE Image:Demosaicing city1
igv.png\|IGV Image:Demosaicing city1 lmmse.png\|LMMS Image:Demosaicing
city1 eahd.png\|EAHD Image:Demosaicing city1 hphd.png\|HPHD
Image:Demosaicing city1 vng4.png\|VNG4 Image:Demosaicing city1
dcb.png\|DCB Image:Demosaicing city1 ahd.png\|AHD Image:Demosaicing
city1 fast.png\|Fast Image:Demosaicing city1 none.png\|None

</div>

## Méthodes de dématriçage

- Méthodes courantes :
  Fast  
  Méthode de dématriçage très rapide mais simple et de basse qualité,
  non recommandée.

  Mono  
  N'est utile que pour les utilisateurs soit d'appareils photo
  monochromes ou dont le filtre mosaïque de couleur est retiré.

  None  
  signifie qu'il n'y a pas de dématriçage. Cela peut être utile pour des
  diagnostics, mais vous ne devez pas l'utiliser en photographie.
- Méthodes Bayer :
  AMaZE  
  (Aliasing Minimization and Zipper Elimination) est la méthode par
  défaut de dématriçage de Rawtherapee car elle donne les meilleurs
  résultats dans la plupart des cas. Dans RawTherapee de versions 2.4 et
  antérieures, VNG4 était habituellement l'algorithme préféré pour les
  appareils Olympus vu que AMaZE n'existait pas encore et que VNG4
  éliminait certains artefacts gênants qui pouvaient avoir été provoqués
  par les autres méthodes, mais depuis l'introduction de la méthode
  AMaZE dans la version 3.0 de RawTherapee, les utilisateurs d'Olympus
  peuvent la préférer.

  RCD  
  ([Ratio Corrected
  Demosaicing](https://github.com/LuisSR/RCD-Demosaicing)) donne
  d'excellents résultats pour les bords courbes, par exemple les étoiles
  en astro-photographie, tout en préservant presque un niveau de détail
  équivalent à AMaZE.

  DCB  
  [DCB](https://discuss.pixls.us/t/diagonal-interpolation-correction-artifacts-with-amaze-demosaicing/3338/45?u=morgan_hardwood)
  produit des résultats similaires à AMaZE. AMaZE peut souvent se
  montrer légèrement supérieur dans la récupération des détails, alors
  que DCB peut être plus efficace pour éviter les fausses couleurs,
  surtout dans les images en provenance d'appareils photo dépourvus de
  filtres anti-aliasing.

  LMMSE et IGV  
  Sont recommandés pour travailler sur des images à hauts ISO, très
  bruitées, en conjonction avec l'outil [Réduction du
  bruit](Noise_Reduction/fr.md). Il empêcheront l'apparition
  d'artefacts en labyrinthe, et que l'image apparaisse délavée en raison
  d'un traitement intense de la réduction du bruit. IGV est aussi assez
  efficace pour atténuer les effets de moiré.

  AHD, EAHD et HPHD  
  AHD (Adaptive Homogeneity-Directed), EAHD (Horvath's AHD) et HPHD
  (Heterogeneity-Projection Hard-Decision) sont d'anciennes méthodes qui
  sont généralement lentes et inférieures aux autres méthodes.

  VNG4  
  Si vous utilisez un appareil photo moyen format avec un objectif grand
  angle quasi symétrique, tels que les Schneider Digitar 28mm ou 35mm,
  il est probable que le fichier souffre de diaphonie, surtout si
  l'objectif est décalé (en raison de l'arrivée de la lumière sous un
  angle très fermé avec ces objectifs, une partie de la lumière déborde
  sur le pixel voisin du capteur), et dans ce cas, vous pouvez obtenir
  des artefacts en labyrinthe avec AMaZE et DCB à cause de la séparation
  du canal vert provoqué par la diaphonie. Si, a l'aide d'adaptateurs,
  vous combinez un appareil photo sans miroir et un objectif grand angle
  conçu pour le film, vous pouvez aussi obtenir de la diaphonie. Il peut
  alors être préférable d'utiliser l'algorithme **VNG4** (Variable
  Number of Gradients), plus robuste, qui gère bien cette situation, au
  prix de quelques fins détails. Une autre alternative consiste à
  valider [l'équilibrage du
  vert](Preprocessing/fr#Equilibrage_du_vert.md) pour atténuer
  la différence entre les canaux verts.

  Pixel Shift  
  Certains appareils Pentax ou Sony supportent la prise de photos en
  mode Pixel Shift (décalage de pixel) qui consiste à prendre quatre
  photos avec à chaque fois un décalage de un pixel de façon circulaire,
  puis de sauvegarder les quatre prises dans un seul grand fichier raw.
  RawTherapee sait combiner les quatre prises en une seule image tout en
  masquant les objets ayant bougé, réduisant ainsi le niveau de bruit et
  accroissant la netteté de l'image.
- Méthodes Fujifilm X-Trans :
  3-Pass  
  est une méthode de dématriçage pour appareils photo munis de capteurs
  X-Trans (Fuji). Elle exécute trois passes sur l'image ce qui donne des
  résultats plus nets bien que cela ne soit visible que sur des photos
  de bas ISO. Elle est plus lente que 1-Pass.

  1-Pass  
  est une méthode de dématriçage pour appareils photo munis de capteurs
  X-Trans (Fuji). Elle est plus rapide que la méthode 3-Pass bien que
  légèrement inférieure en qualité, mais cette différence n'est visible
  que dans les prises de vues à bas ISO. Si la vitesse vous pose
  problème, vous pouvez utiliser cette méthode dans les hauts ISO sans
  différence visible de qualité.

## Comment trouver la meilleure méthode de dématriçage

[thumb](image:demosaicing_city1_example_bad.jpg)

Zoomer à au moins 100% (1:1) et essayer tous les algorithmes de
dématriçage, voir celui qui fonctionne le mieux. Les tester sur des
photos bien piquées avec des petits détails et des motifs répétitifs
minuscules, tels que ceux ondulants d'un tissu (rechercher des artefacts
en forme de labyrinthe), ceux d'un mur en brique lointain, ceux d'un
panneau routier rond lointain (rechercher le moiré le long des bords
ronds), et tester avec des prises de vues à faible ISO et à haut ISO.
Utilisez des photos réalisées avec votre propre appareil, le meilleur
pour les raw d'un Nikon n'est peut-être pas le meilleur pour ceux d'un
Olympus.

## Appareils photo monochromes

Un appareil monochrome a le même filtre de lumière devant chaque pixel,
ce qui produit une image en noir et blanc et aucun dématriçage n'est
nécessaire. Certains de ces appareils n'ont pas de filtre infra-rouge et
sont de ce fait sensibles à cette lumière, ce qui peut être exploité
pour la réalisation de photos noir et blanc créatives.

RawTherapee supporte les appareils monochromes, mais l'interface
utilisateur n'est pas adaptée, ainsi lorsqu'un fichier monochrome est
chargé, tous les outils pour la couleur restent actifs .

Il y a quelques facteurs additionnels à prendre en compte pour
travailler avec des fichiers monochromes : certains appareils
monochromes prétendent ne posséder qu'un seul canal monochrome et une
matrice de couleur neutre, comme le Leica M Monochrom, tandis que
d'autres prétendent avoir des canaux RVB dans une configuration type
Bayer (comme les Phase One IQ260 Achromatic, ou les appareils modifiés
pour l'infra rouge). S'il n'y a qu'un seul canal, RawTherapee le détecte
et n'effectuera aucun dématriçage (la choix du dématriçage reste
accessible mais est sans effet), et tout fonctionne normalement.
Cependant, en présence d'une configuration type Bayer, le dématriçage
sera réalisé et une matrice de couleur sera appliquée. Pour empêcher
cela, vous devez sélectionner l'option de dématriçage "Mono", et
sélectionner "Sans profil" comme [profil
d'entrée](Color_Management/fr#Profil_d'entrée.md) dans l'onglet
Couleur, panneau ICM.

## Interface

Les méthodes de dématriçage et leurs paramètres associés sont répartis
dans deux outils principaux séparés, "Capteurs avec matrice Bayer" et
"Capteurs avec matrice X-Trans". Chacun d'entre eux est visible lors de
l'édition d'un fichier raw produit par un appareil utilisant l'un des
capteurs. Le paramétrage dans l'un de ces deux outils est sans effet
dans l'autre. Si vous ouvrez une image raw issue d'un capteur de type
Bayer, seuls les paramètres de l'outil "Capteur à matrice de Bayer"
seront utilisés, les paramètres de l'outil "Capteur à matrice X-Trans"
seront ignorés et réciproquement.

### Méthode

Les algorithmes de dématriçage suivants sont disponibles pour les
fichiers raw issus de capteurs Bayer :

- AMaZE
- AMaZE+VNG4
- RCD
- RCD+VNG4
- DCB
- DCB+VNG4
- LMMSE
- IGV
- AHD
- EAHD
- HPHD
- VNG4
- Fast
- Mono
- Pixel Shift
- None

Les algorithmes suivants de dématriçage sont disponibles pour les
fichiers raw issus de capteurs X-Trans :

- 3-pass+fast
- 3-pass (Markesteijn)
- 1-Pass+fast
- 1-Pass (Markesteijn)
- Fast
- Mono
- None

#### Dématriçage Duo

Les méthodes de dématriçage duo, telles que AMaZE+VNG4, vous permet le
dématriçage de zones de haut contraste (par ex des détails) en utilisant
une méthode, et le dématriçage de zones de faible contraste (par ex des
surfaces unies, sans détails comme le ciel) en utilisant l'autre
méthode. Etant donné que certains algorithmes sont préférables pour le
rendu de fins détails alors que d'autres sont meilleurs pour le rendu de
surfaces unies et douces, cette option de dématriçage duo combine le
meilleur des deux mondes, offrant ainsi un meilleur point de départ pour
les autres outils, atténuant le besoin de netteté ou de réduction du
bruit. L'inconvénient est que l'image doit être dématricée deux fois,
prenant plus de temps qu'une méthode simple de dématriçage.

Le seuil de réglage du niveau de détail à partir duquel un algorithme de
dématriçage doit être utilisé à la place de l'autre est contrôlé avec le
curseur "Seuil de contraste". Le curseur comprend une case à cocher qui
calcule automatiquement le niveau optimal.

### Bord

Le dématriçage peut s'appuyer sur l'échantillonnage des pixels qui
entourent le pixel considéré. Lors du dématriçage d'un pixel situé sur
le bord supérieur de l'image raw, il n'y a aucun pixel au-dessus, il ne
peut donc être dématricé selon la même méthode, avec la même qualité,
que les autres pixels qui sont entourés d'un nombre de pixels
suffisamment important. La plupart des convertisseurs raw retranchent
ainsi quelques rangs et colonnes de la périphérie de l'image, comme le
fait RawTherapee par défaut. Cependant, vous pouvez forcer le non
rognage de ces pixels périphériques en modifiant la valeur de "Bord". La
fixer à "0" signifie qu'aucun rognage n'est réalisé, et RawTherapee fera
ce qu'il peut pour dématricer les pixels en bordure, mais des artéfacts
peuvent apparaître !

Vous devriez généralement laisser ce paramètre à sa valeur par défaut,
et le changer poue 0 seulement si absolument nécessaire, par exemple
pour le traitement de fichiers raw DNG en
[1080p](https://fr.wikipedia.org/wiki/1080p) où vous devez préserver le
nombre de pixels de 1920x1080.

### Sub-Image

Certains fichiers raw contiennent plus d'une image. Lors de l'édition
d'un tel fichier, l'option sub-image apparaît, et permet l'édition d'une
image contenue particulière, ou de combiner toutes les images contenues
d'une façon ou d'une autre.

Certains appareils photo Fujifilm EXR supportent le "mode SN" au moment
de la capture, ce qui signifie "Signal to Noise priority" (priorité du
signal sur le bruit). Lors de l'édition d'une telle image, la boite de
commande combinée sub-image permet de sélectionner le "mode SN", lequel
fusionne les pixels des deux images contenues et utilise la moyenne, ce
qui réduit le bruit.

### Itérations pour la suppression des fausses couleurs

Etablit le nombre de passes du filtre médian réalisées pour supprimer
les artefacts de dématriçage lors de l'application de l'algorithme de
dématriçage. De fausses couleurs (mouchetage) pourraient être
introduites pendant la phase de dématriçage où de très fins détails sont
résolus. La suppression des fausses couleurs est similaire à
l'adoucissement de la couleur. Le canal de luminance n'est pas affecté
par cette suppression.

Les fausses couleurs sont le plus souvent apparentes dans les images en
provenance d'appareils photo dépourvus de filtres anti-aliasing.
Remarquez que c'est le plus souvent l'algorithme de dématriçage qui est
la facteur déterminent dans l'importance que prendra le problème des
fausses couleurs que vous aurez à gérer. Dans certaines situations, il
peut être préférable de changer l'algorithme de dématriçage plutôt que
de valider la suppression des fausses couleurs, car ce dernier réduit la
résolution des couleurs.
