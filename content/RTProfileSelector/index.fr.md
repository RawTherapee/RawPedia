---
title: RTProfileSelector
contributors:
  - Lebarhon
tags:
  - 'Processing Profile Scripts'
---

<div class="pagetitle">

RTProfileSelector

</div>

**RTProfileSelector** est un plugin de RawTherapee qui sélectionne
automatiquement les profils de traitement personnalisés (fichiers .pp3)
en fonction de règles définies par l'utilisateur. Les règles sont des
collections de champs et de valeurs Exif qui sont mis en correspondance
avec les valeurs en cours extraites des fichiers raw la première fois
qu'ils sont ouverts dans RawTherapee.

Quelques éléments automatisables dans RawTherapee grâce à
RTProfileSelector :

- Choix de vos propres profils de traitement personnalisés qui
  correspondent approximativement aux paramètres de votre appareil photo
  (tels que "monochrome"/"noir et blanc", "couleurs éclatantes", "types
  de film", eetc.)
- Définir les paramètres de réduction du bruit dans RawTherapee suivant
  le modèle d'appareil et la valeur ISO
- Choix des profils de correction de l'objectif (LCP) en fonction de
  l'objectif et du modèle d'appareil utilisés.

RTProfileSelector est écrit en C++11 et se compile à la fois pour
Windows et Linux. Le code source et l'exécutable Windows sont
téléchargeables depuis son [dépôt
GitHub](https://github.com/marcapelini/RTProfileSelector).
RTProfileSelector utilise
[ExifTool](http://www.sno.phy.queensu.ca/~phil/exiftool/) pour extraire
les métadonnées des images.

Concernant les procédures et la documentation en ligne de
l'installation, veuillez consulter la [section
wiki](https://github.com/marcapelini/RTProfileSelector/wiki) du projet.
