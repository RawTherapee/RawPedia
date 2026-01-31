---
title: Defringe
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Aberration chromatique

</div>
[thumb](image:defringe.jpg)
[thumb](image:defringe_curve.png) Les franges violettes sont
une forme d'aberration chromatique axiale (ou longitudinale), elles
apparaissent le long des arrêtes sombres adjacentes à des zones
brillantes et sont dues à une focalisation incorrecte, des imperfections
dans l'objectif, ou simplement (mais d'un point de vue plus technique) à
un problème de lentilles qui ne focalisent pas toutes les couleurs dans
le même plan. Vu que les lentilles sont optimisées pour focaliser les
plus grandes longueurs d'onde de la lumière visible sur le même plan,
les longueurs d'onde les plus courtes, loin des longueurs d'ondes pour
lesquelles les lentilles sont optimisées, (c'est à dire le violet, de
longueur d'onde au minimum du spectre visible) peuvent teinter de façon
visible les régions foncées lorsque les régions claires sont
suffisamment intenses. Cet outil devrait être capable d'en enlever la
plupart.

Le traitement est appliqué soit dans l'espace Lab ou CIECAM02 (si
CIECAM02 est validé). En conséquence, valider CIECAM02 peut conduire à
des résultats légèrement différents, surtout en cas d'utilisation de la
courbe *Teinte*.

## Description de l'interface

### Rayon

Les arrêtes colorées trop prononcées sont atténuées en réalisant une
moyenne sur le voisinage de rayon spécifié.

### Seuil

Etablit un seuil pour l'application de l'outil Aberration chromatique.

### Teinte

Vous pouvez utiliser la [courbe
plate](General_Comments_About_Some_Toolbox_Widgets/fr#La_Courbe_Plate.md)
*Teinte* pour indiquer quelles couleurs l'outil *Aberration chromatique*
doit traiter. L'axe horizontal représente les couleurs et le vertical la
force de l'action de retrait des franges. Cela permet de limiter
l'action à certaines couleurs sans affecter les autres.

Si vous placez un point violet en haut et conservez le reste des
couleurs en bas, les franges violettes seront retirées avec une force
maximale tandis que les autres couleurs ne seront pas affectées.
