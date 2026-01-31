---
title: Vibrance
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Vibrance

</div>

*Vibrance* est un outil intelligent d'ajustement de la saturation,
optimisé pour prendre en compte la sensibilité aux couleurs de la vision
humaine. L'effet de Vibrance agit avec une plus grande précision sur une
image ayant une balance des blancs correcte quand les curseurs de la
*Saturation* RVB et de la *Chromaticité* Lab sont positionnés sur 0.
Vous pouvez séparément contrôler la vibrance des tons *pastels* (tons de
faible saturation) et *saturés* (tons de saturation élevée, comme le nom
l'indique).

## Description de l'interface

### Tons pastels/saturés

Ces curseurs *Tons pastels* et *Tons saturés* permettent de contrôler
individuellement la saturation des tons pastels et des tons saturés.

### Seuil entre tons pastels/saturés

Le réglage du seuil permet de différencier les tons pastels et les tons
saturés. C'est le seuil entre ce qui est considéré être un ton pastel et
être un ton saturé.

### Protéger les tons chairs

Si activé, les couleurs proches des tons naturels de la peau ne sont pas
affectés par les ajustements de Vibrance.

### Eviter les dérives de teinte

Si activé, procure un contrôle supplémentaire pour éviter les dérives de
teinte.

### Lier Pastels et Saturés

Si activé, le niveau de Vibrance est ajusté avec un seul curseur
contrôlant de la même façon les tons pastels et les tons saturés.

### Tons chairs – Teinte en fonction de la teinte

[thumb](image:vibrance_hh.jpg) Cette courbe H = f(H) permet
de modifier la teinte des tons chairs. Elle se comporte exactement comme
les courbes tonales que vous connaissez dans tout programme d'édition
d'images, mais au lieu de travailler sur la totalité d'un canal de
couleur, elle se limite à la gamme des tons chairs usuels. L'axe x
représente la teinte d'entrée, et l'axe y la teinte de sortie. L'étendue
du réglage possible concerne pour l'essentiel les teintes rouges et
orangées; exprimée en radians (degrés) celle-ci débute à -0.05 radians
(357.13 degrés) et finit à 1.6 radians (91.7 degrés).

Décidez d'un ton chair spécifique que vous souhaitez ajuster (celui de
votre sujet sur la photo), trouvez le sur l'axe des x puis modifiez la
courbe pour lui faire correspondre un ton plus agréable sur l'axe des y.
En termes pratiques, vous pouvez utiliser cet outil pour transformer un
bronzage rose anglais en un bronzage brun des Maldives.
