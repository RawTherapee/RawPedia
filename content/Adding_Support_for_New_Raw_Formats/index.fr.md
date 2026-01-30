---
title: Adding Support for New Raw Formats
contributors:
  - Lebarhon
  - DrSlony
tags:
  - 'General Information'
---

<div class="pagetitle">

Ajouter la prise en charge de nouveaux formats raw

</div>

## Introduction

La prise en charge d'un format raw nécessite ce qui suit :

- Être capable de décoder le fichier raw pour que le programme ait accès
  aux données et métadonnées de l'image enregistrée à l'intérieur de
  chaque fichier raw. Cela est géré soit par un programme intégré dans
  RawTherapee appelé "dcraw", ou par du code personnalisé.
- Etre capable d'interpréter les données de l'image. Cela est détaillé
  ci-dessous :
  - Mesure des "niveaux du blanc" (et quelquefois des "niveaux du noir")
    dans les données de l'image décodée, car chaque appareil photo a une
    idée différente de ce qu'est le blanc le plus blanc (et quelquefois
    le noir le plus noir). Les niveaux du blanc sont mesurés à l'aide de
    photos appelées "trames blanches".
  - Détermination de l'endroit du canevas raw où se trouve l'image
    actuelle, le "cadrage raw".
  - Création du "profil d'entrée" pour reproduire les couleurs avec
    précision.

Vous aurez à prendre les photos, mais ne vous forcez pas à comprendre ou
à effectuer les mesures, nous pouvons le faire à votre place.

### Enregistrement et lecture de l'information

RawTherapee recherche l’information concernant l'interprétation des
données l'image (les niveaux du point noir et du point blanc, la matrice
de couleur et d'autres détails mais pas le profil d'entrée) à trois
places :

- Dans le code dcraw qui est intégré dans RawTherapee,
- Dans le fichier raw,
- Dans un fichier texte sur votre système qui est installé avec
  RawTherapee et qui s'appelle `camconst.json`

Les informations sont collectées depuis ces trois places et les données
de `camconst.json` sont prioritaires sur les autres sources. Il y a une
exception concernant la [matrice de couleur
d'entrée](Color_Management/fr#Input_Profile.md) en ce sens que
si le fichier raw est en format DNG et que la métadonnée Exif `Software`
(`0x0131`) ne commence pas par la chaîne de caractères "Adobe DNG
Converter" et que le fichier contient bien une balise `ColorMatrix2`,
alors la valeur de cette balise est priorisée.

En cas de modifications sur `camconst.json` pendant que RawTherapee est
en exécution, le redémarrer pour que les modifications soient prises en
compte.

## Niveaux de blanc

Que sont les niveaux du noir et du blanc ? Un capteur est constitué de
millions de minuscules éléments photo-sensibles appelés photosites.
Chacun d'eux mesure l'intensité de la lumière que tombe sur lui et
enregistre cette intensité sous forme d'un chiffre, plus la lumière est
intense et plus le chiffre est élevé. La majeure partie du fichier raw
est constituée de ces mesures. Chaque photosite présente un niveau
en-dessous duquel il ne peut mesurer la lumière, c'est comme si le peu
de lumière qui arrive sur lui était trop faible pour provoquer un
signal. Cela s'appelle le niveau du noir, ce n'est pas toujours 0. Il
existe aussi un niveau au-dessus duquel le photosite n'enregistre plus
de changement d'intensité même si la lumière continue de s'entensifier,
Cela s'appelle le niveau du blanc. Un photosite qui ne peut pas
enregistrer une augmentation de luminosité est dit saturé, et dans le
post-traitement cet état est appelé hors domaine.

Les niveaux de blanc sont mesurés sur la base de photos complétement
sur-exposées appelées "trames blanches".

Certains modèles d'appareils photo sont dotés d'une réduction de bruit,
souvent appelée LENR - Long Exposure Noise Reduction (Réduction du bruit
dans les longues expositions). Il peut affecter les niveaux du noir et
du blanc. Si vous l'activez, il rentrera en action lorsque le temps
d'exposition est typiquement supérieur à 1 s. Les étapes expliquées plus
loin indiquent quand l'activer et le désactiver.

Le niveau du blanc sur certains modèles d'appareils photo varie selon
l'ouverture, mais en général cela se produit seulement pour les grandes
ouvertures. Pour éviter que cela soit un problème, régler l'ouverture à
f/5.6 ou supérieur sauf en cas d'instruction contraire.

Pour une meilleure information, précisant les photos requises et les
instructions pour prendre les mesures, lire les commentaires inclus dans
le fichier `camconst.json` :
<https://github.com/Beep6581/RawTherapee/blob/dev/rtengine/camconst.json>

### Comment photographier les Trames Blanches

Prendre les photos en mode manuel (M). Si votre appareil dispose de
plusieurs mode raw, utilisez le mode total, non recadré, compression
sans pertes si possible.

Chaque photo doit être complètement sur-exposée sur toute sa surface. De
ce fait, ce que vous photographiez n'a pas d'importance, tout sera
blanc, mais il est plus facile d'y arriver en pointant l'appareil vers
le ciel ou vers une ampoule de lumière blanche. Peu importe que le ciel
sous ensoleillé ou couvert, mais ne pointez pas vers le soleil, cela
pourrait endommager votre capteur.

Le choix de l'objectif est sans importance, mais il sera plus facile de
réaliser une image entièrement sur-exposée en utilisant pas de grand
angle.

### Jeux de photos requis

Nous avons besoin de trois jeux de photos, chaque jeu supplémentaire
améliorant la qualité de la prise en charge, mais exige aussi un plus
grand effort de votre part et du notre aussi. La plupart du temps, vous
n'avez à réaliser que les deux premiers jeux.

Les jeux :

1.  Si votre appareil dispose d'un dispositif intégré de réduction du
    bruit (LENR), le désactiver. Régler l'ouverture sur f/5.6 ou plus.
    Prendre une série de photos telles que décrites ci-dessus, une photo
    pour chaque valeur ISO dont votre appareil dispose, en vous assurant
    de ne pas dépasser un temps d'exposition de 1 s. Par exemple, vous
    arrivez à environ 8 photos : ISO 100, 200, 400, 800, 1600, 3200,
    6400, 12800. La plupart des appareils disposent souvent de valeurs
    ISO intermédiaires, par exemple ISO160 ou ISO320, ainsi, si vous
    souhaitez améliorer la précision du niveau du blanc vous devez faire
    aussi des prises à ces valeurs intermédiaires.
2.  Si votre appareil dispose du LENR, l'activer. Prendre une seconde
    série de photos telles que décrites ci-dessus, mais cette fois en
    vous assurant que le temps d'exposition est d'au moins 2 secondes
    dans tous les cas, pas moins. Ce qui fait à nouveau 8 photos ou
    plus. Le plus souvent ces deux jeux devraient suffire.
3.  Certains appareils changent les valeurs raw d'échelle pour les plus
    grandes ouvertures, particulièrement les modèles Canon et Nikon. La
    seule façon de savoir avec certitude si votre appareil procède ainsi
    est de prendre une photo et de la mesurer. Prendre une photo en
    utilisant la plus grande ouverture possible de l'objectif, par ex.
    f/1.7, avec un ISO de 100, et le LENR désactivé, et nous l'envoyer
    avec les autres photos. Si nous détectons un changement d'échelle
    des valeurs raw (ou si vous le détectez vous-même en réalisant vos
    propres mesures), alors nous vous demanderons de faire une nouvelle
    série de photos, avec un temps d'exposition inférieur à 1 s, depuis
    l'ouverture la plus grande supportée par votre objectif, en
    diminuant à chaque fois de 1/3 de pas jusqu'à atteindre une
    ouverture pour laquelle le changement d'échelle des valeurs raw
    n'est plus appliqué. Cela peut entraîner beaucoup de photos. Gérer
    le changement d'échelle des valeurs raw causé par les grandes
    ouvertures n'est pas très important, aussi ne vous sentez pas
    découragé par cela, il n'est pas indispensable de le faire même si
    votre appareil y a recours, mais si vous avez le temps et la bande
    passante, alors c'est mieux de le vérifier.

Au final, vous vous retrouvez avec une série d'environ 8 photos du point
1, ou mieux une série du point 1 et du point 2, soit 16 photos ou plus,
plus celle concernant le changement d'échelle des valeurs raw du point
3. Si votre appareil pratique le changement d'échelle des valeurs raw,
vous devriez ajouter les séries décrites au point 3 (soit plus de 50
photos), mais comme cela est beaucoup, on ne les exigent pas.

Compresser toutes ces photos et les téléverser à
[filebin.net](http://filebin.net/), nous envoyer le lien soit sur notre
page [GitHub](https://github.com/Beep6581/RawTherapee/issues/new) soit
sur le [Forum](http://rawtherapee.com/forum).

Des photos totalement hors domaine d'exposition peuvent avoir des taux
de compression étonnants, ne pas oublier de les compresser (7-Zip, ZIP,
bzip2, peu importe) avant de les téléverser ! Pour exemple, 10 fichiers
raw Sony 7M2 complètement hors domaine, avec la LENR désactivée, pèsent
234 Mo, mais une fois compressées avec ZIP, vous obtenez un fichier de 1
Mo.

### Renommage

Pour simplifier le travail avec ces images de trame blanche, les noms de
fichier devraient distinguer les photos utilisant le LNR, l'ouverture et
l'ISO. ExifTool peut les renommer automatiquement :

`exiftool '-FileName<${make}_${model}_${LongExposureNoiseReduction}_${aperture}_${iso}%-c.%le' dir`

## Cadrage Raw

Le cadrage raw peut être déterminé à partir de n'importe qu'elle photo,
aucune photo supplémentaire n'est nécessaire.

## Profil d'Entrée

Un profil d'entrée est nécessaire pour reproduire les couleurs avec
précision. Une photo est exigée par modèle d'appareil photo. Lire
l'article "[Comment créer des profils de couleur
DCP](How_to_create_DCP_color_profiles/fr.md)" pour connaître les
différents types de profils d'entrée et comment photographier une cible
de couleur afin que nous puissions créer un profil d'entrée pour votre
modèle d'appareil photo.
