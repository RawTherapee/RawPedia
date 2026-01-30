---
title: The Batch Queue
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

La file d'attente

</div>

## Introduction

[Enregistrer les images](saving_images/fr) à partir de
RawTherapee peut se faire de plusieurs façons, les deux méthodes les
plus utilisées sont Enregistrer l'image courante
![<File:Save.png>](Save.png "File:Save.png") depuis l'onglet Editeur et
l'ajout dans la file de traitement
![<File:Gears.png>](Gears.png "File:Gears.png") gérée dans l'onglet File
d'attente.

La fonctionnalité "Enregistrer l'image courante" mettra votre CPU
immédiatement au travail avec pour conséquence que l'ouverture et le
travail sur d'autres images dans l'onglet Editeur sera un peu plus lent
pendant l’enregistrement de l'image. Le système de la file d'attente
vous permet de placer les images modifiées, en attente d'enregistrement,
dans une file d'attente virtuelle que vous pouvez traiter plus tard.
L'ajout dans le file d'attente est instantané, il est donc possible de
continuer la modification des autres images en disposant du meilleur du
CPU. Lorsque l'édition des images est terminée et qu'elles sont toutes
dans la file d'attente, vous pouvez cliquer sur le gros bouton et aller
vous servir un café pendant que RawTherapee bosse sur les images de la
file.

La file d'attente est persistante, vous pouvez quitter RawTherapee et le
redémarrer plus tard, la file sera toujours là. Elle peut même survivre
à un crash.

## Ajouter des images à la file

Il y a plusieurs méthodes d'ajout :

1.  Lorsque vous avez terminé l'édition d'une image dans l'Éditeur,
    cliquer sur le bouton "Ajouter l'image courante à la file de
    traitement" ![<File:Gears.png>](Gears.png "File:Gears.png").
2.  Toujours dans l'onglet Éditeur, cliquer sur le bouton "Enregistrer
    l'image courante" ![<File:Save.png>](Save.png "File:Save.png") et
    sélectionner "Placer au début/à la fin de la file de traitement"
3.  Cliquer droit sur la vignette dans [Le Navigateur de
    fichiers](The_File_Browser_Tab/fr.md) ou dans [La bande
    film](The_Image_Editor_Tab/fr#La_bande_film.md) et
    sélectionner "Mettre dans la file de traitement"

Quelque soit la méthode utilisée, quand vous allez dans l'onglet "File
d'attente", vous voyez vos photos alignées, prêtes au traitement (si la
file était paramétrée sur "Démarrage auto", il sera peut-être terminé
avant que vous ayez eu le temps de la voir).

## Paramétrage de la file de traitement

<figure>
<img src="/images/Save_window.png" title="Save_window.png" />
<figcaption>Save_window.png</figcaption>
</figure>

La file d'attente possède plusieurs paramètres, tels que le format de
fichier de sortie et la destination. Ces paramètres pressent effet dans
tous les cas sauf si vous utilisez le bouton "Enregistrer l'image
courante"![<File:Save.png>](Save.png "File:Save.png"), sélectionnez
"Placer au début/à la fin de la file de traitement" et activez la case à
cocher "Forcer les options d'enregistrement". Dans ce cas, les
paramètres visibles dans la fenêtre "Enregistrer l'image courante"
seront utilisés et ceux de l'onglet File d'attente seront ignorés. Dans
tout autre cas, les paramètres de l'onglet File d'attente seront
utilisés.

Les paramètres sont évidents, deux choses sont cependant à noter :

1.  "Enregistrer les paramètres de développement avec l'image"
    enregistre un fichier accolé à côté du fichier de sortie, avec le
    même nom mais avec l'extension ".pp3". C'est utile pour la
    sauvegarde de plusieurs copies de la même photo ayant chacune une
    finition différente.
2.  Le dossier de sortie est sélectionné par le bouton "Dossier de
    sauvegarde", mais si vous voulez personnaliser dynamiquement le
    dossier de sortie et le nom de fichier, alors utilisez plutôt le
    bouton "Utiliser le modèle". Survolez la liste déroulante avec votre
    souris et une fenêtre bondissante apparaitra avec des explications.

spécifier le lieu de sauvegarde sur la base du lieu d'origine de la
photo, le rang, le placement éventuel dans la corbeille, ou la position
dans la file d'attente.

Utilisez le chemin de sauvegarde suivant comme exemple :

<b>/home/tom/photos/2010-10-31/photo1.raw</b> la signification du code
est la suivante :

<b>`%d3`</b>` = `<i>`tom`</i>  
<b>`%d2`</b>` = `<i>`photos`</i>  
<b>`%d1`</b>` = `<i>`31-10-2010`</i>  
<b>`%f`</b>`  = `<i>`photo1`</i>  
<b>`%p1`</b>` = `<i>`/home/tom/photos/31-10-2010/`</i>  
<b>`%p2`</b>` = `<i>`/home/tom/photos/`</i>  
<b>`%p3`</b>` = `<i>`/home/tom/`</i>  
<b>`%p4`</b>` = `<i>`/home/`</i>  
  
<b>`%r`</b>` sera remplacé par le rang (nombre d'étoiles) de la photo. Si le rang de la photo n'est pas attribué, %r sera remplacé par '0'. Si la photo est dans la corbeille, %r sera remplacé par 'x'.`  
<b>`%s1`</b>`, ...,  `<b>`%s9`</b>`, etc. sera remplacé par la position initiale de la photo dans la file d'attente au moment du départ. Le numéro spécifie le nombre de chiffres, par ex: `<b>`%s3`</b>` donne  '`<i>`001`</i>`'.`

`Si vous voulez enregistrer l'image de sortie à coté de l'original, écrivez :`  
<b>`%p1/%f`</b>  
  
`Si vous voulez enregistrer l'image de sortie dans un dossier '`<i>`converties`</i>`'  situé dans le dossier de l'original, écrivez `  
<b>`%p1/converties/%f`</b>  
  
`Si vous voulez enregistrer l'image de sortie dans le dossier '`<i>`/home/tom/photos/converties/31-10-2010'`</i>`, écrivez`  
<b>`%p2/converties/%d1/%f`</b>

## Utiliser la file de traitement

En haut à gauche de l'onglet File de traitement, vous trouver un bouton
"On/Off" et la case à cocher "Démarrage auto".

1.  Si Démarrage auto" est coché, le traitement va démarrer dès qu'une
    image est envoyée à la queue. En général, ce n'est pas ce qui est
    désiré car cela utilisera le CPU pour le traitement des photos
    présentes dans la queue en ne laissant que peu de disponibilité du
    CPU pour permettre à RawTherapee d'être réactif pendant que vous
    peaufinez d'autres photos.
2.  Si Démarrage auto" n'est pas coché, vous aurez à activer la file
    manuellement en cliquant sur le bouton "On/Off"

Le traitement de la file peut être suspendu en cliquant à nouveau sur le
bouton "On/Off". RawTherapee terminera d'abord le traitement de la photo
en cours.

## Vider la file d'attente

Vous pouvez retirer une photo de la file en cliquant sur le petit bouton
"Retirer de la file de traitement"
![<File:Cancel-small.png>](Cancel-small.png "File:Cancel-small.png")
présent dans l'angle de chaque vignette.

Vous pouvez effacer tout le contenu de la file par un clic droit sur une
vignette puis choisir "Sélectionner tout" puis "Retirer de la file de
traitement", ou en utilisant le raccourci clavier  + pour sélectionner
toutes les vignettes puis en appuyant sur la touche du clavier.
