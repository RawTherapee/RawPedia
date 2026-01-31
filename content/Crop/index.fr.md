---
title: Crop
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Transform Tab'
---

<div class="pagetitle">

Recadrage

</div>

L'outil Recadrage de RawTherapee n'efface pas la partie retirée de
l'image, il la cache seulement en créant un cadre et en grossissant
l'image pour adapter ce cadre à la partie utile de l'écran. Vous pouvez
toujours voir la zone retirée par le recadrage dans l'aperçu si vous
zoomez arrière et réglez la [Couleur d'arrière plan de l'aperçu de
l'éditeur](The_Image_Editor_Tab/fr#Couleur_d'arrière_plan_de_l'aperçu_de_l'éditeur.md)
sur "Dépendant du thème". Les parties retirées par recadrage, bien sûr
n’apparaissent pas sur l'image enregistrée.

Si vous réglez la [Couleur d'arrière plan de l'aperçu de
l'éditeur](The_Image_Editor_Tab/fr#Couleur_d'arrière_plan_de_l'aperçu_de_l'éditeur.md)
sur tout autre chose que "Dépendant du thème", alors les parties
retirées par recadrage seront complètement cachées dans l'aperçu, mais
avec "Dépendant du thème", alors par défaut les parties retirées par
recadrage seront recouvertes par un masque sombre semi-transparent. Vous
pouvez choisir la transparence et la couleur de ce masque dans
"[Préférences](preferences/fr) \> Général \> [Masque de
recadrage](Preferences/fr#Thème.md)".

Activez le mode recadrage en cliquant sur le bouton "Sélection du
recadrage" dans le panneau de l'outil, ou sur le bouton
![<File:Crop.png>](Crop.png "File:Crop.png") dans la barre du haut de
l'[Editeur](the_image_editor_tab/fr) ou sur le [raccourci
clavier approprié](Keyboard_Shortcuts/fr.md), puis créer le
cadre de sélection sur l'image d'aperçu par cliquer/glisser de la
souris. Appuyer sur la touche **Majuscule** pour déplacer ce cadre sur
l'image. Redimensionner le cadre en plaçant la souris sur un des bords
ou angles, le curseur devient une double flèche. Pour effacer le cadre,
activer à nouveau le mode recadrage (avec le raccourci ou un des boutons
mentionnés ci-dessus), et cliquer n'importe où à l'intérieur de l'aperçu
sans glisser. Pour ne voir que la zone recadrée, utiliser le [raccourci
clavier](Keyboard_Shortcuts/fr.md) "Adapte la zone recadrée à
l'écran ".

Utilisez *Type de guide* pour sélectionner un des guides qui vous aidera
à composer un bon recadrage avec une orientation horizontale (paysage)
ou verticale (portrait). Pour l'orientation du cadre, par défaut depuis
la version 4.2.214, RawTherapee détecte et utilise automatiquement la
même orientation que celle de l'image, l'option "As Image" (= comme
l'image).

La valeur PPI (PPP ou points par pouce) ne change aucune propriété
physique de l'image, mais ne sert qu'à vous aider à voir quelle taille
physique aurait la version imprimée de ce recadrage en utilisant cette
valeur de PPI.

## Ratio dimensionnel

![](Sensor_sizes_overlaid_inside.svg "Sensor_sizes_overlaid_inside.svg")
![](SensorSizes.svg "SensorSizes.svg")
![](Vector_Video_Standards2.svg "Vector_Video_Standards2.svg")

### Ratio de recadrage personnalisé

Il est possible de créer un ratio de recadrage personnalisé à partie de
RawTherapee 5.1.

1.  Décocher "Ratio fixe",
2.  Faire un cadrage, utiliser les valeurs de "L" (largeur) et "H"
    (hauteur) pour définir le ratio, par exemple, pour un cadrage de
    ratio 5:4, indiquer L=5 et H=4, ou bien, L=1280 et H=1024.
3.  Pour redimensionner le cadrage tout en conservant le ratio
    personnalisé, maintenir la touche Shift enfoncée pendant le
    déplacement du bord ou de l'angle du cadre avec la souris.

### Ratio de recadrage imposé

Cochez "Ratio fixe" pour imposer un cadre de rapport longueur/largeur
prédéfini

3:2  
Les négatifs classiques ont ce format, tout comme les appareils photo
[APS-C](https://fr.wikipedia.org/wiki/APS-C) et
[DSLR](https://fr.wikipedia.org/wiki/Appareil_photographique_reflex_num%C3%A9rique).

4:3  
Le [format quatre
tiers](https://en.wikipedia.org/wiki/Four_Thirds_system).

16:9  
Les format d'affichage [haute
définition](https://en.wikipedia.org/wiki/High-definition_video)
[1080p](https://fr.wikipedia.org/wiki/1080p) et
[720p](https://fr.wikipedia.org/wiki/720p), et de ce fait, le format des
écrans des ordinateurs les plus répandus depuis 2010.

16:10  
Le format des écrans d'ordinateurs les plus populaires entre 2005
et 2009. Encore répandu pour les tablettes.

24:65 XPan  
Appareils photo moyen format de chez Hasselblad.

1.414 DIN EN ISO 216  
[1.414 DIN EN ISO 216](https://fr.wikipedia.org/wiki/ISO_216) est le
format normalisé des feuilles de papier, tel que A4, B5, etc.

8.5:11  
Le format des [lettres
US](https://en.wikipedia.org/wiki/Letter_(paper_size)).

11:17 - Tabloid  
Un format répandu pour les [journaux
tabloïds](https://en.wikipedia.org/wiki/Tabloid_(newspaper_format)).

45:35 - ePassport  
Des guides pour vous aider à cadrer un portrait pour un [passeport
biométrique](https://en.wikipedia.org/wiki/Biometric_passport). Les
dimensions officielles ne définissent pas de format exact, seulement des
dimensions mini/maxi à l'intérieur desquelles les yeux et la distance
menton-crâne doit tenir. Les guides représentent les moyennes de ces
distances. Le premier guide horizontal correspond au crâne, le deuxième
est grosso-modo pour les narines, le troisième pour le menton. "Sur la
photo, le visage doit avoir entre 29mm et 34mm depuis le bas du menton
jusqu'en haut du crâne (le haut de la tête, pas le haut des cheveux)."
[1](http://www.homeoffice.gov.uk/agencies-public-bodies/ips/passports/information-photographers/).
