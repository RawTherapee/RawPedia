---
title: Chromatic Aberration
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Aberration Chromatique

</div>

<img src="/images/chromatic_aberration_auto1.jpg"
title="chromatic_aberration_auto1.jpg" width="900"
alt="chromatic_aberration_auto1.jpg" />
<img src="/images/chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" width="900"
alt="chromatic_aberration_auto2.jpg" /> Cet outil "Aberration
Chromatique" traite l'image **avant** le dématriçage, c'est la raison
pour laquelle il est placé dans l'onglet "raw". L'outil [Aberration
chromatique](Lens/Geometry/fr#Aberration_chromatique.md) dans
l'onglet *Transformation* traite l'image **après** le dématriçage.

La correction de l'aberration chromatique au niveau du raw n'est
actuellement supportée que pour les fichiers raw en provenance
d'appareils photo équipés d'un [Filtre
Bayer](https://en.wikipedia.org/wiki/Bayer_filter). Si vous avez besoin
de corriger l'aberration chromatique sur des photos produites par des
appareils équipés de capteurs X-Trans (Fuji), utilisez alors l'outil
[Aberration
chromatique](Lens/Geometry/fr#Aberration_chromatique.md) dans
l'onglet *Transformation*.

L'aberration chromatique peut être corrigée en utilisant les curseurs
"Rouge" et "Bleu". Normalement, vous ne verrez pas d'aberration
chromatique dans l'aperçu réglé sur "Ajuster à la fenêtre", il est donc
recommandé d'ouvrir une vue détaillée
![<File:Window-add.png>](Window-add.png "File:Window-add.png") ou de
zoomer l'aperçu principal à 100%
![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png")
ou plus pour procéder à ce type de correction.

Cet outil corrige les franges vertes-bleuâtres et magenta dues à
l'aberration chromatique latérale de l'objectif qui apparaît
principalement sur les bords de l'image. Cette correction est réalisée
avant le dématriçage et peut quelquefois en améliorer la qualité.

## Correction automatique

Si "Correction automatique" est coché, les curseurs "Rouge" et "Bleu"
sont désactivés et une détection et un correction automatiques de
l'aberration chromatique est réalisée. Alors que la correction manuelle
applique une valeur constante sur toute l'image, la Correction
automatique divise l'image en de nombreux blocs et adapte les valeurs
requises pour éliminer l'aberration chromatique dans chaque bloc. Pour
cette raison, la correction automatique est généralement plus
performante que la correction manuelle, et les valeurs de la correction
automatique ne peuvent pas être affichées par les curseurs.

## Itérations

Ce paramètre est disponible si "Correction automatique" est coché.
Correction automatique est conservatif, c'est à dire que souvent, il ne
corrige pas toutes les aberrations chromatiques. Pour corriger les
aberrations résiduelles, vous pouvez, à partir de RawTherapee 5.5,
utiliser jusqu'à 5 itérations de la correction de l'aberration
chromatique. Chaque itération réduira les aberrations chromatiques
résiduelles de l'itération précédente au prix d'un temps de traitement
additionnel.

## Rouge/Bleu

Si les curseurs "Rouge" et "Bleu" ne sont pas à zéro, les valeurs
affichées sont utilisées pour corriger l'aberration chromatique. Ils ne
peuvent être utilisés pour la Correction automatique.
