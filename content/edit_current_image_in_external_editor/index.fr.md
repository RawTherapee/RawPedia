---
title: Éditer l'image courante dans un éditeur externe
contributors:
  - Lebarhon
tags:
  - 'General Information'
---


La fonction "*Editer l'image courante dans l'éditeur externe*" a pour
effet le traitement complet de l'image courante par RawTherapee et son
ouverture immédiate dans une application externe. Vous pouvez utiliser
cette fonction pour envoyer facilement l'image dans un éditeur d'image
comme GIMP ou Photoshop pour un traitement supplémentaire, ou bien la
configurer pour envoyer l'image dans afficheur, ainsi d'un simple clic
sur un bouton, vous pouvez voir l'image finale avec une qualité élevée.

Le bouton pour envoyer l'image dans un éditeur externe
![<File:Palette-brush.png>](Palette-brush.png "File:Palette-brush.png")
est situé en bas à gauche du panneau d'aperçu. Lors de l'utilisation de
cette fonction, Rawtherapee traite votre image et l’enregistre au format
TIFF 16 bits entiers codé gamma dans le [dossier
temporaire](/file_paths#dossier-temporaire). Ces fichiers
intermédiaires, destinés à quitter le contrôle de Rawtherapee, ne sont
pas automatiquement effacés quand RawTherapee est fermé, ne perdez pas
cela de vue et effacez les manuellement.

Vous devez être conscient que GIMP-2.8 et précédents ne gère pas les
images 16 bits, donc elles sont sous échantillonnées en 8 bits. Vous
devez aussi être conscient que GIMP-2.8 et précédents annule toutes les
données Exif des fichiers TIFF ! C'est un bug de GIMP, pas de
RawTherapee. GIMP 2.9, et au-dessus gère les images ayant une profondeur
d'un grand nombre de bits (jusqu'à 64 bits par canal !), conserve toutes
les métadonnées et est quasi stable, on vous encourage donc à vous
procurer [GIMP 2.9 ou plus](http://www.gimp.org/downloads/).

Spécifiez votre éditeur externe préféré dans "*[Préférences \> Général
\> Editeur externe](/preferences#editeur-externe)*".
Cliquer sur le lien pour obtenir des informations sur la spécification
d'un éditeur externe.
