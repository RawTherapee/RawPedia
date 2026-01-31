---
title: Raw White Points
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Points Blancs raw

</div>

Il y a peu de chance que vous deviez un jour utiliser l'outil Points
Blancs raw autrement qu'à des fins de diagnostic.

Le curseur Correction du Point Blanc ajuste le niveau du blanc en cours
pour tous les canaux. Il ajuste linéairement les échantillons raw après
soustraction du niveau de noir et peut être utilisé pour simuler un
nouveau niveau de blanc. Cela peut être nécessaire si le décodeur raw de
RawTherapee possède un niveau de blanc incorrect, ce qui peut arriver
pour des appareils photo rares ou récents. La correction [Champ
Uniforme](Flat_Field/fr.md) peut aussi dans certains cas, par
effet de bord, réduire les échantillons raw si bien que les hautes
lumières brulées sont altérées (généralement rosies). Dans ce cas, ce
paramètre peut être utilisé pour dilater les données raw de manière à ce
qu'elles atteignent à nouveau le niveau de blanc.
