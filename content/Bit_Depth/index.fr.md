---
title: Profondeur de couleur
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Profondeur de couleur

</div>

## Introduction

Il vous arrive d'entendre des termes tels que "8-bits", "16-bits",
"24-bits", "32-bits", "64-bits" et "96-bits" en rapport avec les images
numériques. Cet article va clarifier la signification de ces termes

Les images numériques sont constituées de millions de pixels, et chaque
pixel décrit un ou plusieurs canaux de couleur. Les images en niveaux de
gris n'ont besoin que d'un canal (la valeur de 0 peut représenter le
noir pur, 255 le blanc pur et les valeurs intermédiaires représentent
alors les gris entre noir et blanc), alors que les images couleur en
mode RVB ont besoin de trois canaux, un décrit le rouge, un le vert et
un le bleu. Chaque canal ne décrit que l'intensité, aussi il n'y a rien
de fondamentalement vert à propos du nombre qui décrit a pixel du canal
vert; les couleurs sont la conséquence de l'interaction entre les trois
canaux dans le [modèle colorimétrique Rouge Vert Bleu](https://fr.wikipedia.org/wiki/Rouge_vert_bleu).

Un seul pixel peut représenter plus de trois canaux, par exemple il peut
contenir l'information du canal alpha (lequel décrit la transparence) ou
un canal infra-rouge (supporté par certains scanners).

Plus la profondeur de couleur est importante, le plus précisément la
couleur est décrite, au prix d'un calcul plus long, de plus de RAM et de
plus d'espace de stockage.

## Bits par quoi ?

La profondeur de couleur s'exprime sous forme d'une valeur qui décrit
soit le nombre de **bits par pixel** (BPP), ou de **bits par canal**
(BPC). Typiquement, le format très populaire
[JPEG](https://fr.wikipedia.org/wiki/JPEG) enregistre ses images avec
une précision de 8 bits par canal, utilisant trois canaux, pour un total
de 24 bits par pixel. Le format
[TIFF](https://fr.wikipedia.org/wiki/Tagged_Image_File_Format) supporte
différentes profondeurs de couleur, par exemple, 32 bits par canal pour
un total de 96 bits par pixel.

Lors de propos au sujet de la profondeur de couleur, précisez bien ce
dont vous parlez pour ne laisser aucune ambiguïté. Par exemple, si
quelqu'un dit posséder une image de "32-bits", cela signifie t-il 32
bits par canal, ou est-ce 4 canaux de 8 bits ?

## Précision

Quelle différence apporte la profondeur de couleur (soit le nombre de
bits par couleur) ? Plus les bits sont nombreux pour décrire une couleur
et plus cette couleur est décrite précisément.

- Une précision de 1 bit par canal signifie qu'il n'y a qu'un bit pour
  décrire la valeur. Un bit ne peut valoir que 0 ou 1, vous ne pouvez
  donc représenter que deux valeurs, soit probablement noir et blanc.
- Une précision de 2 bits par canal signifie qu'il n'y a deux bits pour
  décrire la valeur. Comme chaque bit peut valoir 0 ou 1, deux bits
  peuvent valoir 4 valeurs :
      [00] = 0
      [01] = 1
      [10] = 2
      [11] = 3

  Si nous utilisons le 0 pour représenter le noir et le 3 pour le blanc,
  il y a deux teintes de gris qui peuvent être décrites.
- Une précision de 8 bits par canal signifie qu'il y a 8 bits qui
  peuvent représenter 256 valeurs :
      [0000 0000] = 0
      [0000 0001] = 1
      (...)
      [1111 1110] = 254
      [1111 1111] = 255

  Si nous utilisons le 0 pour représenter le noir et le 255 pour le
  blanc, on peut aussi décrire 254 nuances de gris. C'est ce qui est
  utilisé par les fichiers JPEG, 8 bits par canal, avec 3 canaux. C'est
  suffisant pour la plupart des utilisations pour les photographies
  prêtes à la présentation dans l'espace colorimétrique
  [sRGB](https://fr.wikipedia.org/wiki/SRGB) sans
  [postérisation](https://fr.wikipedia.org/wiki/Posterisation) visible.
  Vous pouvez donc l'utiliser pour enregistrer des photos destinées à
  une présentation sur internet. Ce n'est pas convenable pour un format
  intermédiaire ou final s'il est possible qu'une retouche ultérieure
  soit réalisée car vous courrez le risque d'introduire des artefacts de
  postérisation, en fonction de l'intensité des ajustements. Une
  précision de 8 bits n'est pas suffisante pour représenter une scène à
  haute gamme dynamique de façon linéaire sans postérisation, en fait,
  vous pouvez théoriquement utiliser une précision de 8 bits pour
  décrire une scène à haute gamme dynamique de façon linéaire, mais les
  nombres seraient si distants entre eux qu'une postérisation importante
  se produirait. Par exemple, si on veut prendre une photo qui
  représente un jour ensoleillé dans un parc, et si nous supposons que
  le noir est 0 et le blanc 1 000 000, on pourrait faire correspondre le
  0 au 0 et le 255 à 1 000 000, mais il n'y aurait plus que 254 valeurs
  pour décrire les 999 999 nuances de gris restantes sur la scène
  originale.
- Une précision de 16 bits par canal (16 bits entiers) signifie qu'il y
  a 16 bits qui peuvent représenter 65536 valeurs :
      [0000 0000 0000 0000] = 0
      [0000 0000 0000 0001] = 1
      (...)
      [1111 1111 1111 1110] = 65534
      [1111 1111 1111 1111] = 65535

  Les appareils photo numériques typiquement capturent la lumière avec
  un précision de 12 bits ou de 14 bits (et en raison du bruit et de
  l'imprécision de l'électronique, les bits les plus bas sont de qualité
  douteuse). 16 bits par canal sont suffisants pour la plupart des
  besoins photographiques, y compris pour les fichiers intermédiaires
  (quand vous désirez transférer une image d'une application à une autre
  sans perte de données).
- Les valeurs d'une image 16 bits en [virgule flottante](https://fr.wikipedia.org/wiki/Virgule_flottante), aussi
  connus comme [virgule flottante demi précision](https://en.wikipedia.org/wiki/Half-precision_floating-point_format),
  sont réparties de façon à échantillonner la lumière plus
  judicieusement qu'en 16 bit entiers. Cela pour plusieurs raisons : la
  vision humaine est plus sensible aux petits changements dans les
  ombres qu'en pleine lumière; nos yeux ont une réponse logarithmique à
  la lumière (elle doit être 10 fois plus intense pour qu'on la perçoive
  comme deux fois plus); et les les hautes lumières spectaculaires, qui
  peuvent être les éléments les plus lumineux de la scène (le soleil se
  réfléchissant sur une poignée de porte), n'ont pas besoin d'être
  décris aussi précisément que tous les autres tons. En notation 16 bits
  virgule flottante, les valeurs sont réparties de façon plus rapprochée
  dans les tons sombres (en bas) que dans les tons lumineux (en haut),
  permettant ainsi une description plus précise dans les tons les plus
  significatifs pour nous.
- Une image 32 bits [virgule flottante](https://fr.wikipedia.org/wiki/Virgule_flottante) peut
  représenter 4,3 milliards de valeurs par canal, et nécessite à peu
  près deux fois plus de place disque qu'une image 16 bits. Peu
  d'applications supportent les images 32 bits.

Une des raisons pour lesquelles la profondeur de couleur affecte
principalement les ombres est due à la façon dont les couleurs sont
enregistrées. Chaque couleur est définie par un mélange de rouge, de
vert et de bleu. En prenant une image 8 bits et la couleur orange en
exemple, beaucoup de valeurs sont possibles pour décrire un orange
clair, mais le nombre de valeurs pour décrire un orange foncé tombe à
très peu, en fait seuls les 3 ou 4 bits les plus bas de chaque canal
peuvent être utilisés pour décrire un orange foncé, ce qui ne fait que
16 possibilités. Plus la profondeur de couleur est importante et plus le
nombre de couleur augmente et plus la postérisation est évitée.

## Correction Gamma

La [correction gamma](https://fr.wikipedia.org/wiki/Correction_gamma)
peut s'utiliser lors de l'enregistrement des fichiers, elle modifie les
valeurs de telle sorte qu'un plus grand nombre d'entre elles peuvent
être attribuées dans les ombres plutôt que dans les hautes lumières, ce
qui correspond mieux à la sensibilité de l’œil humain. Cela signifie
qu'une image JPEG 8 bits peut afficher jusqu'à log2((1/2^8)^2.2) = 17.6
pas de gamme dynamique, ce qui effectivement dépasse les 14 pas des
meilleurs appareils photo actuels. Cela explique pourquoi vous pouvez
quelque fois voir le bruit de l'ombre de l'appareil photo même dans une
photo JPEG 8 bits. Cependant, en raison de la distribution non linéaire,
nous perdons de la précision en comparaison avec les fichiers raw
enregistrés de façon linéaire par un appareil numérique. En pratique,
cela n'est pas un problème quand le fichier de sortie est le fichier
définitif et ne sera pas retouché, mais une photo peut-être largement
améliorée si elle est enregistrée au format raw et retouchée à l'aide
d'une application de traitement raw au gout du jour, telle que votre
serviteur - RawTherapee.

## Après RawTherapee

Après la retouche d'une photo avec Rawtherapee, que vous êtes prêt à
l'[enregistrer](saving_images/fr), vous faites face au choix
des [profil de sortie, profondeur de couleur](color_management/fr#profil_de_sortie),
[espace colorimétrique et correction gamma](color_management_addon/fr#espace_de_sortie_"output_profile").
Si vous envisagez de post-traiter vos photos après Rawtherapee dans un
programme d'édition d'images 16 bits, il est préférable de les
enregistrer dans un format 16 bits sans pertes. RawTherapee peut
enregistrer les images avec une précision 16 bits entiers (nommé "TIFF
(16-bit)" dans la boite de dialogue d'enregistrement) mais aussi en
précision 16 bits en virgule flottante (nommé "TIFF (16-bit float)"). Le
format TIFF non compressé de précision 16 bits entiers est recommandé
comme format intermédiaire car il est le plus rapide à l'enregistrement
et est largement compatible avec les autres logiciels. Les fichiers 32
bits sont grossièrement deux fois plus gros et mal supportés par les
autres logiciels.
