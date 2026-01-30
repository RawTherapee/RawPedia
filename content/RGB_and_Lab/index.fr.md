---
title: RGB and Lab
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

RVB et L\*a\*b\*

</div>

![](RGB_Cube_Show_lowgamma_cutout_b.png "RGB_Cube_Show_lowgamma_cutout_b.png")
![](Lab_color_space.png "Lab_color_space.png")
*[RVB](https://en.wikipedia.org/wiki/RGB_color_space)* (RGB en anglais)
et *[CIE L\*a\*b\*](https://fr.wikipedia.org/wiki/CIE_Lab)* (ou plus
simplement "*Lab*") sont deux [espaces
colorimétriques](https://fr.wikipedia.org/wiki/Espace_de_couleur)
distincts, ou façons de décrire les couleurs (on parle aussi d'espace de
couleur).

Beaucoup de gens se demandent quelles sont les différences entre le
réglage de la luminosité, du contraste et de la saturation dans l'espace
RVB ou de la luminosité, du contraste et de la chromaticité dans
l'espace Lab. RVB travaille dans les trois canaux rouge, vert et bleu.
Lab est une conversion des mêmes informations en une composante de
luminosité L\* et deux composantes de couleur a\* et b\*. La luminosité
est maintenue séparée des couleurs, ainsi il est possible d'en régler un
sans perturber l'autre. La *Luminosité* est conçue pour s'approcher de
la vision humaine qui est très prononcée pour le vert et moins pour le
bleu. Si vous éclaircissez l'image dans l'espace Lab, elle aura souvent
un aspect plus agréable à l’œil, au sens de la couleur. En général, on
peut dire qu'en utilisant des valeurs positives avec le curseur
Saturation dans l'espace Lab, les couleurs sont plus “fraîches”, alors
qu'en utilisant les mêmes valeurs de Saturation dans l'espace RVB, elles
sont plus “chaudes”.

<div align="center">

<File:colorspace_flowers_900_1_neutral.jpg> \| Neutre
<File:colorspace_flowers_900_2_rgb_lightness.jpg> \| Luminosité RVB +30
<File:colorspace_flowers_900_3_lab_lightness.jpg> \| Luminosité Lab +30
<File:colorspace_flowers_900_4_rgb_contrast.jpg> \| Contraste RVB +45
<File:colorspace_flowers_900_5_lab_contrast.jpg> \| Contraste Lab +45
<File:colorspace_flowers_900_6_rgb_saturation.jpg> \| Saturation RVB +25
<File:colorspace_flowers_900_7_lab_chromaticity.jpg> \|Chromaticité Lab
+25 <File:colorspace_flowers_900_8_vibrance.jpg> \| Vibrance +25

</div>

La différence entre le curseur *Luminosité* de la section
*[Exposition](exposure/fr)* (dans l'espace RVB) et le curseur
*Luminosité* de la section *[Lab](lab_adjustments/fr)* est
subtile. Une *Luminosité* de +30 dans dans l'espace RVB donne une image
globalement un peu plus éclatante qu'avec une *Luminosité* de +30 dans
l'espace Lab. Les couleurs de la *Luminosité* Lab sont plutôt plus
saturées. Le contraire est vrai pour les curseurs de contraste; si on
choisit un *Contraste* de +45 dans l'espace RVB, les couleurs sont
nettement plus chaudes qu'avec un *Contraste* de +45 dans l'espace Lab.
Le contraste lui-même est à peu près le même dans les deux cas.
N'hésitez pas à utiliser les deux curseurs pour ajuster la saturation
et/ou le contraste. Comme pour les curseurs *Saturation*/*Chromaticité*,
mettre à -100 le curseur *Saturation* de l'espace RVB donne une image
noir et blanc qui semble avoir un filtre rouge, alors que le curseur
*Chromaticité* de l'espace Lab donne une image noir et blanc plus
neutre. Les valeurs positives de *Saturation* dans l'espace RVB conduira
à des décalages de teinte (plus la valeur est importante, plus le
décalage est visible), alors que les valeurs positives de *Chromaticité*
dans l'espace Lab tonifie les couleurs tout en conservant des teintes
correctes, donnant un résultat soutenu et propre. La chromaticité de
l'espace Lab (utilisant le curseur *Chromaticité* ou la courbe *CC*) est
la méthode recommandée pour rehausser les couleurs.
