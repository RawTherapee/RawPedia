---
title: The File Browser Tab
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Le Navigateur de fichiers

</div>

__TOC__

L'onglet Navigateur de fichiers est l'endroit pour prendre les photos en
considération, sélectionner celles que l'on souhaite éditer, ou bien
réaliser des opérations de traitement par lots. Il comprend les parties
suivantes : ![](Rt_setm_fb.png "Rt_setm_fb.png") (actuellement ouvert),
File d'attente, Éditeur et Préférences. 2- Panneaux utilisés pour la
navigation dans les dossiers et fichiers. 3- Vignettes du dossier
actuellement ouvert. 4- Filtres pour limiter l'affichage des vignettes
aux seules qui répondent à certaines métadonnées ou états. 5- Zoom des
vignettes et infos. 6- Opérations rapides sur les images. 7-
Sous-onglets du Navigateur de fichiers: Filtre (actuellement ouvert),
Inspecter (pour visualiser l'aperçu JPEG intégré en plein format),
Édition par lot (pour appliquer des réglages à toutes les images
sélectionnées) et Export rapide (basse qualité et escamote certains
outils mais sauvegarde rapide - a ne pas utiliser pour une sauvegarde
principale !). 8- Menu contextuel du clic droit (a utiliser typiquement
pour appliquer un profil de traitement à tous les fichiers
sélectionnés).\]\]

- Le panneau de gauche
  - Le panneau "Emplacements" en haut, offre des liens vers votre
    répertoire personnel, les lecteurs de cartes USB, le répertoire par
    défaut "photos" du système ou d'autres répertoires personnalisés.
  - En dessous il y a un navigateur de fichiers de type arborescence
    standard qu'il est possible d'utiliser pour naviguer dans les
    dossiers contenant vos photos. RawTherapee ne vous complique pas les
    choses en exigeant que vous importiez vos photos dans des bases de
    données comme le font certains autres logiciels.
- le panneau de droite
  - L'onglet "Filtrer" permet de ne visualiser que les photos qui
    répondent aux critères spécifiés.
  - L'onglet "Inspecter" affiche un aperçu de l'image survolée par la
    souris à une échelle déterminée de 100%, ce qui correspond à soit la
    plus grande image JPEG intégrée dans le fichier raw, ou bien à
    l'image elle-même en cas de survol d'images non-raw.
  - L'onglet "Édition par lot" permet d'appliquer l'action des outils à
    (aux) image(s) sélectionnée(s). Ceci permet d'appliquer rapidement
    l'action des outils à plusieurs images à la fois.
  - L'onglet "Export Rapide" permet de traiter rapidement les images
    sélectionnées en by-passant certains outils même s'ils sont activés
    dans le profil de traitement de ces images, ainsi vous pouvez
    obtenir un aperçu rapide du fichier raw, par exemple pour effacer
    les prises de vues qui sont floues ou bien hors mise au point.
- Le panneau central affiche les vignettes du contenu du répertoire
  actuellement sélectionné.

Vous pouvez cacher ces panneaux individuellement grâce aux boutons
"Montrer/cacher le panneau gauche
![<File:Panel-to-left.png>](Panel-to-left.png "File:Panel-to-left.png")"
et "Montrer/cacher le panneau de droite
![<File:Panel-to-right.png>](Panel-to-right.png "File:Panel-to-right.png")".
Voir la page [Raccourcis clavier](keyboard_shortcuts/fr).

Quand vous ouvrez un répertoire, RawTherapee génère dans le panneau
central les vignettes des photos trouvées dans ce répertoire. La
première fois que vous ouvrez un répertoire plein de fichiers de photos
raw, RawTherapee lit chaque fichier et crée la vignette sur la base de
l'image JPEG intégrée (chaque photo raw possède une image JPEG intégrée,
quelquefois même plusieurs de différentes tailles). Cela peut prendre du
temps pour les plus grands répertoires qui contiennent des centaines de
photos, mais ne se produit qu'à la première ouverture dudit répertoire.
Toutes les fois suivantes que vous entrez dans un répertoire qui a déjà
été ouvert, RawTherapee lit les vignettes depuis son cache s'il existe,
et cela est beaucoup plus rapide que lors de la première fois.

L'image JPEG intégrée dans chaque photo raw est identique à l'image JPEG
produite par l'appareil photo que vous obtenez lors de prises de vues en
mode JPEG (ou en mode "RAW+JPEG"). Cette image JPEG n'est pas
représentative des données raw présentes dans cette photo, car votre
appareil photo applique toutes sortes d'adaptations à l'image JPEG,
telles que accroitre un peu l'exposition, accroitre la saturation, le
contraste, la netteté, etc.

Une fois l'édition de la photo commencée, sa vignette dans l'onglet
"Navigateur de fichiers" est remplacée par ce que vous voyez dans
l'aperçu de l'onglet "Editeur", et tout réglage effectué est transposé
dans la vignette. Elles sont enregistrées dans le cache en vue d'un
futur rapide accès. Pour rétablir la vignette identique à l'image JPEG
intégrée, cliquer droit sur la vignette (ou sélection des vignettes)
puis cliquer sur "*Opérations sur les profils \> Remettre le profil à
zéro*".

Utiliser les icônes de zoom dans la barre d'outils du haut du Navigateur
de fichiers pour agrandir ou diminuer les vignettes. Chacune utilise un
peu de mémoire (RAM), il est donc conseillé de ne pas choisir une taille
trop élevée ("*Préférences \> Navigateur de fichiers \> Options du cache
\> Hauteur maximale des vignettes*").

On peut filtrer les photos visibles en utilisant les boutons de la barre
d'outils du haut du *Navigateur de fichiers* ou de *[La bande
film](The_Image_Editor_Tab/fr#La_bande_film.md)*, ainsi qu'en
utilisant la boîte de dialogue "*Chercher*" ou l'onglet "*Filtrer*".
Utilisations possibles :

- Ne montrer que les photos non éditées
- Ne montrer que les photos bracketées à + 2IL
- Ne montrer que les photos cotées 5 étoiles
- Ne montrer que les photos situées dans une gamme ISO spécifique
- Ne montrer que les photos avec l'extension NEF.

__TOC__

## Classement

RawTherapee permet le classement des images entre 0 et 5 étoiles.
RawTherapee 5.7 a vu apparaître la possibilité de lire le classement
enregistré dans les métadonnées de l'image, enregistrement réalisé par
exemple par l'appareil photo ou une autre application, et de l'afficher
sous forme d'un système d'étoiles.

Les enregistrements dans les métadonnées pour traduire le classement ont
évolué au cours des années, et RawTherapee les priorise dans l'ordre
ascendant suivant :

1.  Exif `rating`
2.  XMP `rating`
3.  PP3 `rank`

En conséquence, si une image possède un enregistrement Exif `rating`
avec la valeur 1 et un enregistrement XMP incorporé `rating` avec la
valeur 2, alors RawTherapee indiquera 2 étoiles. Si vous classez ensuite
cette image 3 étoiles dans RawTherapee, le classement 3 étoiles est
alors indiqué dans le navigateur et la bande film de RawTherapee.

Notez que le classement par étoiles de RawTherapee n'est pas exporté
avec les images sauvegardées. En conséquence, si vous sauvegardez
l'image de l'exemple précédent, le fichier enregistré contiendra
`Exif:rating=1` et `XMP:rating=2` si la configuration de "mode de copie
des métadonnées" (onglet META) est "copier à l'identique", le classement
3 étoiles n'apparaîtra nul part. Si la configuration de "mode de copie
des métadonnées" est "Appliquer les modifications", le fichier
enregistré ne contiendra que `Exif:rating=1`, car l'édition de XMP
n'étant pas supporté, il sera effacé.

## Ajustements par lots - Sync

## Effacement de fichiers

Étant donné que RawTherapee est un programme multi-plateforme, il
possède sa propre corbeille, indépendamment de celle de votre système,
si toutefois il en possède une.

### Utilisation de la corbeille

Pour déplacer des fichiers dans la corbeille, soit utiliser le bouton
"Déplacer dans la corbeille"
![<File:Trash.png>](Trash.png "File:Trash.png") situé dans l'angle en
haut à droite de chaque vignette, ou bien cliquer droit sur une
sélection de fichiers et choisir "Opérations sur les fichiers \>
Déplacer dans la corbeille". Ces fichiers sont alors repérés comme étant
dans la corbeille mais ne sont pas supprimés du disque dur.

- Pour cacher tous les fichiers qui sont repérés comme étant dans la
  corbeille, cliquer sur le bouton "Voir uniquement les images non
  supprimées"
  ![<File:Trash-hide-deleted.png>](Trash-hide-deleted.png "File:Trash-hide-deleted.png")
  dans la barre d'outils supérieure.
- Pour voir le contenu de la corbeille, cliquer sur le bouton "Voir le
  contenu de la corbeille"
  ![<File:Trash-show-full.png>](Trash-show-full.png "File:Trash-show-full.png").
- Lorsque le contenu de la corbeille est affiché, un nouveau bouton
  apparaît à gauche des vignettes "Supprimer définitivement les fichiers
  de la corbeille" ![<File:Trash.png>](Trash.png "File:Trash.png"),
  l'utiliser pour supprimer définitivement du disque dur tous les
  fichiers repérés comme étant dans la corbeille.
- Cliquer sur le bouton "Voir toutes les images du dossier"
  ![<File:Filterclear.png>](Filterclear.png "File:Filterclear.png") pour
  retourner dans lavue par défaut.

### Effacer du disque dur

Pour effacer des fichiers sur le disque dur sans passer par la
corbeille, simplement cliquer droit sur un fichier ou sur une sélection
de fichiers et choisir "Opérations sur les fichiers \> Retirer du
système de fichiers" ou "Supprimer (y compris les sorties de la file de
traitement)". Dans les deux cas,les images sélectionnées et leurs
fichiers accolés sont effacés du disque dur, mais "Supprimer (y compris
les sorties de la file de traitement)" efface aussi les images
sauvegardées dont le nom de fichier (chemin inclus) correspond au modèle
actuellement défini dans le champ "Utiliser le modèle" de l'onglet File
d'attente.
