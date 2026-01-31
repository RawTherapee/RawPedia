---
title: Favorites Tab
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
---

<div class="pagetitle">

L'onglet Favoris

</div>

## Introduction

Un nouvel onglet "Favoris" est apparu avec RawTherapee 5.6. Il permet à
l'utilisateur de lister ses outils favoris et d'y accéder plus
rapidement. Les outils listés dans cet onglet sont retirés de leur
onglet d'origine.

L'onglet Favoris est caché par défaut et n'apparaît que si des outils y
sont ajoutés.

Une interface utilisateur graphique pour placer facilement des outils en
"favoris" est en développement, mais en raison de contraintes de temps
avant la date d'édition, cette interface ne pu être prête pour la sortie
de RawTherapee 5.6 et sera proposée dans une édition future. En
attendant, les utilisateurs qui désirent placer des outils en "favoris"
peuvent le faire manuellement, comme décrit ci-dessous.

## Mode opératoire

Pour ajouter un outil dans l'onglet Favoris :

1.  Si RawTherapee est en cours d'exécution, l'arrêter. Ceci pour
    garantir l'intégrité de vos éditions manuelles dans le fichier
    `options`.
2.  Éditer le fichier [`options`](file_paths/fr) dans un
    éditeur de texte.
3.  Repérer la clé `Favorites=` dans la section `GUI`.
4.  Ajouter les outils par leur nom de code (listés ci-dessous), séparés
    par un point-virgule et en terminant la liste par un point-virgule.
    Ils apparaîtront dans l'ordre où ils sont inscrits dans la clé. Par
    exemple, pour ajouter Exposition, Ombres/Hautes lumières et
    Redimensionnement dans l'onglet Favoris, écrivez la ligne comme suit
    :

`Favorites=tonecurve;shadowshighlights;resize;`

Nom de code des outils :

- Exposition
  - Exposition - `tonecurve`
  - Ombres/Hautes lumières - `shadowshighlights`
  - Compression tonale - `epd`
  - Compression de Plage Dynamique - `fattal`
  - Filtre Vignettage - `pcvignette`
  - Filtre Dégradé - `gradient`
  - Ajustements L\*a\*b\* - `labcurves`

<!-- -->

- Détail
  - Netteté - `sharpening`
  - Contraste Local - `localcontrast`
  - Bords - `sharpenedge`
  - Microcontraste - `sharpenmicro`
  - Réduction du bruit d'impulsion- `impulsedenoise`
  - Réduction du bruit - `dirpyrdenoise`
  - Aberration chromatique - `defringe`
  - Contraste par niveaux de détail - `dirpyrequalizer`
  - Élimination de la Brume - `dehaze`

<!-- -->

- Coleur
  - Balance des blancs- `whitebalance`
  - Vibrance - `vibrance`
  - Mixage des canaux - `chmixer`
  - Noir et Blanc - `blackwhite`
  - Equaliseur HSV - `hsvequalizer`
  - Simulation de Film - `filmsimulation`
  - Lumière douce - `softlight`
  - Courbes RVB - `rgbcurves`
  - Virage Partiel - `colortoning`
  - ICM - `icm`

<!-- -->

- Avancé
  - Retinex - `retinex`
  - Apparence de la Couleur (CIECAM02) - `colorappearance`
  - Niveaux d'Ondelettes - `wavelet`

<!-- -->

- Transformation
  - Recadrage - `crop`
  - Redimensionnement - `resize`
  - Objectif / Géométrie - `lensgeom`
    - Rotation - `rotate`
    - Perspective - `perspective`
    - Profil de correction d'objectif - `lensprof`
    - Distortion - `distortion`
    - Aberration Chromatique - `cacorrection`
    - Correction vignettage - `vignetting`

<!-- -->

- Raw
  - Capteur à matrice de Bayer - `sensorbayer`
    - Dématriçage - `bayerprocess`
    - Points Noirs Raw - `bayerrawexposure`
    - Traitement pré-dématriçage - `bayerpreprocess`
    - Aberration Chromatique - `rawcacorrection`
  - Capteur à matrice X-Trans - `sensorxtrans`
    - Dématriçage - `xtransprocess`
    - Points Noir Raw - `xtransrawexposure`
  - Trame Noire - `darkframe`
  - Champ Uniforme - `flatfield`
  - Points Blancs Raw - `rawexposure`
  - Traitement pré-dématriçage - `preprocess`
  - Film Négatif - `filmnegative`
  - Capture Netteté - `capturesharpening`
