---
title: Dynamic Range Compression
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Compression de Plage Dynamique

</div>

## Introduction

La plage dynamique en termes généraux est le ratio entre la valeur la
plus grande et la plus petite d'un signal mesuré. En tant que
photographe, il y a plusieurs choses que vous devez prendre en compte et
qui ont leur propre plage dynamique, la [perception
visuelle](https://en.wikipedia.org/wiki/Dynamic_range#Human_perception)
humaine possède une plage dynamique (vous pouvez voir de très faibles
étoiles la nuit et aussi le ciel lumineux de jour, bien que pas
simultanément), votre écran possède une plage dynamique (bien plus
faible que la vision humaine), et aussi la capteur de votre appareil
photo et l'électronique qui traite le signal enregistré par le capteur.
L'outil Compression de Plage Dynamique est utilisé pour compresser et
redistribuer la plage dynamique de la scène capturée dans la photo.

La plage dynamique de la scène est le ratio entre l'élément le plus
lumineux de la scène et le plus sombre. Imaginez une scène extérieure un
jour de brouillard épais, l'élément le plus lumineux n'apparaitra pas
plus lumineux que l'élément le plus sombre, cette scène sera dite avoir
une faible plage dynamique. A l'opposé, si vous vous tenez à l'intérieur
par un jour très ensoleillé, les nuages éclairés par le soleil vous
apparaitrons bien plus lumineux que la pièce éclairée par une lampe,
laissant les coins dans l'ombre, cette scène sera dite avoir une plage
dynamique importante.

Généralement, la plage dynamique de la scène capturée est bien plus
importante que la plage dynamique du matériel de visualisation
(moniteur, ordinateur, smartphone). Pour reproduire la scène sur le
matériel de visualisation, généralement deux choses peuvent arriver :
soit la partie de la plage dynamique qui tombe en dehors de ce que le
matériel peut reproduire est purement annulée (le ciel à l'extérieur est
blanc saturé hors domaine et vous pouvez voir l'intérieur de la pièce,
ou bien le ciel est correctement reproduit au prix de l'intérieur de la
pièce saturé noir hors domaine), soit la plage dynamique de la scène est
compressée et ainsi les zones claires et sombres peuvent être visibles
simultanément, c'est ici que cet outil entre en jeu.

L'outil Compression de Plage Dynamique est utilisé pour compresser la
plage dynamique d'une image, réduisant les hautes lumières et les
ombres. Il est basé sur le document [Gradient Domain High Dynamic Range
Compression](http://www.cs.huji.ac.il/~danix/hdr/) (Compression de plage
dynamique importante dans le domaine gradient), cité dans un autre
logiciel comme Luminance HDR sous le nom de "Fattal".

L'outil opère dans l'espace colorimétrique RVB est est appliqué juste
après [Réduction du bruit](noise_reduction/fr) et
[Elimination de la brume](haze_removal/fr), mais avant les
autres ajustements de courbe tonale tels que les contrôles
d'[Exposition](exposure/fr).

Le curseur "Détail" correspond au paramètre α (alpha) du document, et le
curseur "Quantité" correspond à β (beta).

Les existe d'autres moyens de compresser la plage dynamique en utilisant
d'autres outils. Le plus simple serait d'appliquer un contraste de
valeur négative dans l'outil [Exposition](exposure/fr) pour
réduire (ou plutôt pour redistribuer) la plage dynamique, cependant, les
effets ont la pluq grande chance d'apparaître plats et sans attrait. Une
courbe donne un contrôle supplémentaire sur le processus, cependant cet
outil est spécifiquement conçu pour la tâche.

## Utilisation

Utilisez cet outil quand la plage dynamique de la scène photographiée
est trop importante pour être reproduite de façon plaisante sur un
écran, cela se produit quand vous observez que la différence entre les
tons sombres et les tons clairs (le contraste) est si importante que ces
zones manquent de détail.

Maitrisez l'assemblage en panorama ! Les effets de cet outil dépendent
de la plage dynamique (et de l'histogramme) de l'image en cours
d'édition. Si vous traitez une série d'images en vue de les assembler,
où chaque image contient la partie de la scène adjacente à celle
contenue par l'image précédente, même si vous avez appliqué des
paramètres identiques à toutes ces images en utilisant cet outil, le
résultat final sera décevant. Il y aura de soudains changements de
luminosité entre les images adjacentes. N'utilisez pas l'outil de
compression de la plage dynamique sur les images sources. Si vous avez
besoin de compresser la plage dynamique sur une série d'images de façon
cohérente, utilisez plutot une courbe. Vous pouvez, cependant, utiliser
cet outil sur le panorama assemblé.

## Interface

### Quantité

Définit la quantité de compression où les valeurs les plus hautes
produisent le plus de compression.

### Détail

La quantité de détails à préserver peut être définie avec ce paramètre.
Les valeurs négatives adoucissent l'image en réduisant le contraste
local, alors que les valeurs positives l'augmente.

### Ancre

Ce paramètre influe la compression vers les ombres ou les hautes
lumières. Il fonctionne comme une compensation d'exposition.
