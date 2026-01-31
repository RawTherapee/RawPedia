---
title: How to get LCP and DCP profiles
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<div class="pagetitle">

Comment obtenir des profils LCP et DCP

</div>

Une importante collection de LCP (Adobe Lens Correction Profiles -
Profils de correction des objectifs pour corriger la distorsion, le
vignetage et l’aberration chromatique) et de DCP (DNG Color Profiles -
profils de couleur DNG, profils de couleur d'entrée de l'appareil photo)
est livrée avec [Adobe DNG
Converter](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows).

Cette section explique comment installer Adobe DNG Converter et où
trouver les profils DCP et LCP.

__FORCETOC__

## Linux

Nous utiliserons `$HOME/wine-dng` comme préfixe Wine.

- Trouver les profils **LCP** correspondants à votre appareil photo :

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/LensProfiles/1.0/"

- Trouver les profils **DCP** standards dans :

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Adobe Standard"

- Trouver les profils des 'modes' de l'appareil photo **DCP** (portrait,
  paysage, gros plan, etc) dans :

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Camera/"

Recopier les profils désirés dans un répertoire différent pour un accès
plus facile, par exemple `~/profiles/`

## Windows

1.  [Télécharger Adobe DNG Converter pour
    Windows](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows).
2.  Installer Adobe DNG Converter

- Trouver les profils **LCP** correspondants à votre appareil photo :

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\LensProfiles\1.0"

- Trouver les profils **DCP** standards dans :

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Adobe Standard

- Trouver les profils des 'modes' de l'appareil photo **DCP** (portrait,
  paysage, gros plan, etc) dans :

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Camera

Recopier les profils désirés dans un répertoire différent pour un accès
plus facile.

## Fait par la Communauté

[TooWaBoo](https://discuss.pixls.us/u/toowaboo) a réalisé à la main deux
LCP pour le de-fishing de l'objectif Samyang 8mm, conçu sur mesure pour
la taille du capteur APS-C utilisé par Nikon, Pentax et Sony. Peut
demander des réglages pour Canon.

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Panini.lcp"
  title="File:Samyang 8mm APS-C Panini.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Panini.lcp</figcaption>
  </figure>

  
Mettre la Correction de Distortion = 0, Remplir = non coché

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Rectilinear.lcp"
  title="File:Samyang 8mm APS-C Rectilinear.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Rectilinear.lcp</figcaption>
  </figure>

  
Mettre la Correction de Distortion = -0.5, Remplir = non coché
