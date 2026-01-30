---
title: Saving Images
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Enregistrer les images

</div>

Votre fichier raw original ne sera jamais altéré par RawTherapee.

Il existe plusieurs façons d'enregistrer une image depuis l'onglet
[Editeur](the_image_editor_tab/fr) :

- ![<File:Save.png>](Save.png "File:Save.png") Enregistrement immédiat
  depuis l'onglet Editeur,
- ![<File:Gears.png>](Gears.png "File:Gears.png") Enregistrer via [la
  file d'attente](The_Batch_Queue/fr.md),
- ![<File:Palette-brush.png>](Palette-brush.png "File:Palette-brush.png")
  "[Editer l'image courante dans l'éditeur
  externe](Edit_Current_Image_in_External_Editor/fr.md)" (décrit
  dans sa propre page).

## Enregistrement immédiat

Dans l'onglet Editeur, si vous cliquez sur l'icône du petit disque dur
![<File:Save.png>](Save.png "File:Save.png") en bas à gauche de l'image
d'aperçu ou bien tapez le raccourci **Ctrl+s** pour "*Enregistrement
immédiat*". Ceci fonctionne comme une boite de dialogue "Enregistrer
sous ...". Vous pouvez choisir le nom et la destination de
l'enregistrement du fichier (RawTherapee ajoutera automatiquement
l'extension correspondant au format choisi), choisir un format de
fichier de sortie et la profondeur de couleur, définir un niveau de
compression, choisir la possibilité d'enregistrer le profil de
traitement (aussi appelé Paramètres de développement) dans un fichier
accolé créé à coté de celui de l'image de sortie, etc. La dernière
option vous laisse le choix entre "*Enregistrement immédiat*" ou bien de
"*Placer au début/à la fin de la file de traitement*" (aussi appelée
file d'attente). Si vous choisissez "*Enregistrement immédiat*" ,
RawTherapee sera occupé à enregistrer votre photo dès le clic sur
"*OK*", il sera donc moins réactif à traiter les réglages que vous êtes
susceptibles d'essayer pendant ce temps et il prendra aussi plus de
temps pour ouvrir les autres photos. Pour cette raison, il est
généralement recommandé d'utiliser la file de traitement si vous désirez
travailler imméddiatement sur d'autres images.

La fenêtre Enregistrer s'ouvre par défaut sur le dernier endroit où un
enregistrement a eu lieu. Pour votre confort, un raccourci vers le
dossier contenant l'image source est automatiquement ajouté dans le
panneau des favoris sur la partie gauche de la fenêtre Enregistrer. Si
vous désirez enregistrer l'image dans le dossier source, cliquer sur ce
favori vous évitera de devoir naviguer manuellement jusqu'à cet endroit.

Le bouton *OK* a comme raccourci **Ctrl+Enter**.

## Placer au début/à la fin de la file de traitement

Cliquez sur l'icône des engrenages
[<file:gears.png>](file:gears.png) ou dans la fenêtre
"*Enregistrer*" puis "*Placer au début/à la fin de la file de
traitement*", pour conserver l'image dans une file d'attente en vue
d'être traitée, ultérieurement, ainsi Rawtherapee peut exploiter au
mieux le CPU et être réactif lors du travail sur les photos. Une fois ce
travail terminé et après avoir ajouté les photos à la file de
traitement, vous pouvez demander à RawTherapee de commencer le
traitement de la file pendant que vous partez déguster un thé. L'intérêt
de placer une image dans la file d'attente via la fenêtre
"*Enregistrer*" est de pouvoir choisir individuellement le format de
fichier, le nom et l'emplacement de chaque image, alors que placer
l'image directement dans la file d'attente sans utiliser la fenêtre
"*Enregistrer*" fera appel aux paramètres de l'onglet "[File
d'attente](The_Batch_Queue/fr.md)".

## Nommer

Si le fichier raw d'origine s'appelait "photo_1000.raw", le nom par
défaut du fichier traité sera "photo_1000.jpg" (ou tif ou png). Il
existe une option dans la fenêtre "*Enregistrer*" : "*Ajouter
automatiquement un suffixe si le fichier existe déjà*". Lorsqu'elle est
cochée, cette option permet de conserver différentes versions d'un même
fichier raw, elles seront enregistrées sous le nom "photo_1000.jpg",
"photo_1000**-1**.jpg", "photo_1000**-2**.jpg", etc. Cela s'applique de
même quand vous envoyez différentes versions du même fichier raw vers la
[file d'attente](the_batch_queue/fr).
