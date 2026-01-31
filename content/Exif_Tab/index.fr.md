---
title: Exif Tab
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Metadata Tab'
---

<div class="pagetitle">

Onglet EXIF

</div>

L'onglet "Métadonnées" permet de contrôler quelles métadonnées
[Exif](https://en.wikipedia.org/wiki/Exif) seront contenues dans le
fichier image (développé) sauvegardé. Les métadonnées Exif sont
habituellement créées par l'appareil photo lui-même et intégrées dans le
fichier image raw. Les informations Exif fondamentales sont directement
visibles, les informations exif complémentaires, aussi appelées [données
makernote](https://en.wikipedia.org/wiki/Exchangeable_image_file_format#MakerNote_data)
(données fabricant) sont organisées en arborescence. Cliquer sur une
flèche à l'extrémité gauche d'une sous-arborescence pour afficher son
contenu.

Vous pouvez "Retirer", "Conserver", ou "Ajouter/Editer" les métadonnées
Exif. La manipulation des métadonnées ne change en rien le fichier
source ! Pour restaurer une valeur modifiée ou effacée, tout simplement
cliquer sur "Réinitialiser". "Réinitialiser tout" fonctionne de façon
similaire mais s'applique à l'arborescence de façon récursive, ce qui
signifie que toutes les valeurs modifiées/effacées dans la
sous-arborescence sont restaurées.

Il est possible d'"Ajouter/Editer" les informations Exif suivantes :

- Artist (Artiste)
- Copyright (Droits d'auteur)
- ImageDescription (Description de l'image)
- Exif.UserComment (Commentaires de l’utilisateur)

Seuls les noms en anglais des champs Exif sont affichés pour un
référencement aisé. Ils ne sont pas traduits lorsque vous choisissez une
autre langue pour l'interface.

## Détails techniques

Lecture du `Exif.UserComment`:

- les valeurs ASCII sont lues sans problèmes.
- Pour les valeurs Unicode, RawTherapee détecte si la chaîne présente
  une longueur anormale.
  - Dans ce cas, c'est supposé être une chaîne UTF-8.
  - Dans le cas contraire, il essaie de détecter s'il existe un
    Indicateur d'ordre des octets UCS-2 (Byte Order Mark ou BOM en
    anglais).
  - Si aucun BOM n'existe et que la chaîne UTF-8 est valide, il essaie
    d'auto-détecter le BOM en se basant sur le comptage des "zéros".
  - Si ce n'est pas une chaîne UTF-8, c'est supposé être une chaîne
    UCS-2 utilisant l'ordre des octets de la plateforme.
- Pour les valeurs indéfinies, RawTherapee essaie de convertir la chaîne
  depuis le jeu de caractères local vers l'UTF-8.

Enregistrement du `Exif.UserComment`:

- Si la chaîne est du pur ASCII, elle est sauvée en ASCII.
- Sinon, la chaîne est convertie en UTF-16et enregistrée sans Indicateur
  d'ordre des octets, en utilisant l'ordre des octets des métadonnées.
