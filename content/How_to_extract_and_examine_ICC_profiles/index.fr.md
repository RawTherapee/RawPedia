---
title: How to extract and examine ICC profiles
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<div class="pagetitle">

Comment extraire et étudier des profils ICC

</div>

## DisplayCAL

Projet : DisplayCAL  
Site web : <https://displaycal.net/>  

Interface utilisateur pour Linux, macOS et Windows.

DisplayCAL utilise ArgyllCMS, il permet de visualiser les détails d'un
profil ICC y compris les courbes et le gamut de l'espace colorimétrique.
Il autorise aussi de les exporter en tant qu'images ou ou fichiers 3D
HTML/VRML/X3D que vous pouvez partager et visionner dans un navigateur
Web.

## ArgyllCMS

Projet : ArgyllCMS  
Site web : <https://www.argyllcms.com/>  
Documentation (iccdump): <https://www.argyllcms.com/doc/iccdump.html>  
Documentation (extracticc): <https://www.argyllcms.com/doc/extracticc.html>  

Ligne de commande pour Linux, macOS et Windows.

ArgyllCMS permet d'extraire les profils ICC des fichiers image et de
transférer le contenu des profils ICC en texte lisible par un être
humain..

- Extraction : `extracticc photo.jpg profil.icc`
- Examiner directement dans une image: `argyll-iccdump -s photo.jpg`
- Examiner un fichier ICC : `argyll-iccdump profil.icc`

## ICC Examin

Projet : Oyranos  
Site web : <http://www.oyranos.org/icc-examin/>  

Interface utilisateur pour Linux, macOS et Windows.

ICC Examin permet de visualiser les détails d'un profil ICC y compris le
visualiser en 3D.

## colord

Projet : colord  
Site web : <https://www.freedesktop.org/software/colord/>  

Service système, interfaces utilisateur disponibles. Linux.

colord permet de visualiser les détails d'un profil ICC

## ExifTool

Projet : ExifTool  
Site web : <http://www.sno.phy.queensu.ca/~phil/exiftool/>  

Ligne de commande pour Linux, macOS et Windows.

ExifTool permet de visualiser les profils ICC, indépendamment du fait
qu'ils soient intégrés à une image ou bien des fichiers ".icc"
autonomes. Il permet aussi d'extraire des profils ICC d'images et de les
intégrer dans des images.

- Extraction : `exiftool -icc_profile -b -w icc photo.jpg`
- Intégrer: `exiftool "-icc_profile<=profile.icc" photo.jpg`
- Examiner directement dans une image :
  `exiftool -icc_profile:* photo.jpg`
- Examiner un fichier ".icc" : `exiftool profile.icc`

## GIMP

Projet : GIMP  
Site web : <https://www.gimp.org/>  

Interface utilisateur pour Linux, macOS et Windows.

- Extraction : Ouvrir la photo avec GIMP 2.9, puis cliquer sur "Image \>
  Gestion de la couleur \> Enregistrer le profil couleur dans un
  fichier".

## ImageMagick

Projet :: ImageMagick  
Site web : <https://www.imagemagick.org/script/index.php>  

Ligne de commande pour Linux, macOS et Windows.

- Extraction : `convert photo.jpg profil.icc`

## iccToXml

Projet : IccXML  
Site web : <https://sourceforge.net/projects/iccxml/>  

Ligne de commande pour Linux et Windows. Projet abandonné.

iccToXml fait partie du projet IccXML. Vous pouvez l'utiliser pour
convertir un profil ICC en un fichier XML lisible par un être humain.

Conversion : `iccToXml profil.icc profil.xml`

## ICC Profile Inspector

Projet : ICC Profile Inspector  
Site web : <http://www.color.org/profileinspector.xalter>  

Interface utilisateur pour Windows seulement bien que fonctionne avec
wine. Projet abandonné.
