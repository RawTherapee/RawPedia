---
title: IPTC Tab
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Metadata Tab'
---

<div class="pagetitle">

Onglet IPTC

</div>

Les valeurs
[IPTC](https://fr.wikipedia.org/wiki/IPTC_Information_Interchange_Model)
sont des métadonnées, elles sont en effet stockées dans le fichier image
sans affecter l'image proprement dite. Les métadonnées appelées IPTC
contiennent des informations additionnelles au sujet de l'image. Ces
informations étant enregistrées dans le fichier image, on ne peut les
perdre. Cela facilite beaucoup le travail car il n'y a pas à se soucier
de fichiers supplémentaires lors de sauvegardes ou de tri des images.

IPTC est habituellement utilisé pour décrire l'image en détail. Il
existe de nombreux logiciels de banques d'images qui utilisent les
informations IPTC enregistrées dans l'image pour par exemple renseigner
leurs champs descriptifs. Vous pouvez aussi utiliser les champs IPTC
lorsque par exemple vous souhaitez vendre vos images. La plupart des
sociétés de vente en ligne utilisent IPTC lorsque vous téléchargez vos
images dans leur banque, vous avez de ce fait moins de travail. Ajouter
par exemple des mots clé sur votre ordinateur à la maison, lors du
développement des photos, est beaucoup plus confortable et efficace que
de le faire via le navigateur internet à chaque fois que vous partagez
une image. De multiples "Mots clé" et "Catégories suppl." (Catégories
supplémentaires) peuvent être ajoutés ou enlevés grâce aux signes plus
[image:List-add-small.png](image:list-add-small.png) ou moins
[image:List-remove-red-small.png](image:list-remove-red-small.png)
situés à coté.

Il y a trois boutons :

- "[image:Gtk-undo-ltr.png](image:gtk-undo-ltr.png)
  Réinitialisation" réinitialise les données IPTC à leur valeur
  enregistrée dans votre profil de traitement actif.
- "[image:Gtk-copy.png](image:gtk-copy.png)" copie les
  réglages IPTC dans le presse papiers. C'est particulièrement utile
  quand vous désirez appliquer les mêmes données IPTC à de multiples
  images.
- "[image:Gtk-paste.png](image:gtk-paste.png)" colle les
  réglages IPTC préalablement copiés depuis le presse papiers vers
  l'image courante.

## Technical Details

Les chaînes IPTC sont manipulées par `libiptcdata`. Lors de
l'enregistrement, RawTherapee fixe le `IPTC_TAG_CHARACTER_SET` sur
UTF-8.
