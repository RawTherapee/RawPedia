---
title: Vignetting Filter
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Filtre Vignettage

</div>

![](Vignette-filter_4.00_50_50.png "Vignette-filter_4.00_50_50.png") Le
filtre vignettage est destiné à l'ajout d'un vignettage artistique sur
votre image. Si l'image est recadrée, le filtre vignettage sera appliqué
à la zone recadrée uniquement.

Pour corriger le vignettage du à l'assombrissement des angles par
l'objectif (sans rapport avec ce filtre qui n'est pas pour corriger des
défauts mais pour créer un effet artistique) utilisez le filtre
[correction
vignettage](Lens/Geometry/fr#Correction_vignettage.md) présent
dans l'onglet Transformation, outil Objectif/Géométrie. Encore mieux,
utilisez l'outil [Champ Uniforme](flat_field/fr).

## Force

Quantité en nombre de pas d'ouverture, de l'assombrissement devant être
appliqué par l'outil. La force maximum est atteinte dans les angles de
l'image. L'application d'une quantité négative provoque un
éclaircissement des angles au lieu de les assombrir.

## Etendue

Le curseur "*Etendue*" contrôle la largeur de l'effet. Si à 0, les
angles seuls sont affectés et le reste de l'image inchangé, à 50,
l'effet avance jusqu'à mi-chemin vers le centre et le reste de l'image
est inchangé, à 100, l'effet avance jusqu'au centre.

<File:Vignette-filter_4.00_00_50.png%7CEtendue=0>
<File:Vignette-filter_4.00_99_50.png%7CEtendue=100>

## Circularité

Le curseur "*Circularité*" contrôle la géométrie du filtre. A 0, la
forme est rectangulaire (avec des angles arrondis), à 50, la forme est
elliptique, à 100, elle est circulaire. A noter que si votre image est
carrée, l'ellipse correspondante sera évidemment circulaire, si bien que
sa forme ne changera pas entre 50 et 100.

<File:Vignette-filter_4.00_50_00.png%7CCirculairité=0>
<File:Vignette-filter_4.00_50_99.png%7CCirculairité=100>
