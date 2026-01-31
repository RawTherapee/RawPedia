---
title: Preprocessing
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Traitement pré-dématriçage

</div>

Il existe plusieurs paramètres de traitement pré-dématriçage et ils sont
séparés en deux parties dans l'interface utilisateur, toutes les deux
dans l'onglet "Raw" : une partie apparaît comme étant le principal outil
de "Traitement pré-dématriçage", et l'autre partie apparaît dans l'outil
"Capteur à matrice de Bayer". Les paramètres de traitement
pré-dématriçage dans le groupe principal "Traitement pré-dématriçage"
agissent sur les fichiers raw de tous types alors que ceux de l'outil
"Capteur à matrice de Bayer" n'agissent que sur les fichiers raw issus
d'appareils photo utilisant un filtre bayer.

## Filtre de lignes PDAF

<figure>
<img src="/images/Pdaf_lines_filter_sony.png" title="Pdaf_lines_filter_sony.png"
width="900" />
<figcaption>Pdaf_lines_filter_sony.png</figcaption>
</figure>

Les appareils photo équipés d'Auto-Focus à Détection de Phase (Phase
Detection Auto Focus ou PDAF) sont susceptibles de produire des
artéfacts sous forme de rayures avec des lumières parasites (flare), sur
des photographies prises en contre-jour. Certains objectifs
interchangeables, dépourvus de miroir, de chez Sony sont connus pour
souffrir de ce problème.

Activer le Filtre de lignes PDAF pour supprimer les artéfacts de rayures
PDAF.

RawTherapee 5.5 peut supprimer ces artéfacts de rayures PDAF pour les
appareils photo suivants :

- Sony DSC-RX1RM2
- Sony ILCE-6000
- Sony ILCE-6300
- Sony ILCE-6500
- Sony ILCE-7M3
- Sony ILCE-7RM2
- Sony ILCE-7RM3
- Sony ILCE-9

## Filtre de bruit de ligne

Un bruit de ligne se présente sous la forme de bandes horizontales ou
verticales principalement dans les images bruitées. Il est causé par du
bruit dans l'électronique du capteur qui lit les valeurs de chaque
photosite ligne par ligne ou bien colonne par colonne.

Vous pouvez voir des exemples de ce à quoi ressemble un bruit de ligne
dans ce message de forum par MagicLantern :
<http://www.magiclantern.fm/forum/index.php?topic=10111.msg105001#msg105001>

Plusieurs objectifs interchangeables, dépourvus de miroir, de chez Nikon
utilisent l'Auto-Focus à Détection de Phase (PDAF), et ils réalisent un
filtrage en interne dans l'appareil photo pour adoucir les rayures
artéfacts dues au PDAF. Cependant, le filtrage réalisé semble excessif
et génère des "Bandes PDAF", des bandes plus foncées dans les zones
sombres.

Utiliser le filtre de bruit de ligne pour corriger les bandes PDAF,
régler la direction sur "Horizontales seulement sur les lignes PDAF".

RawTherapee 5.5 peut supprimer ces artéfacts de bandes PDAF sur les
Nikon pour les appareils suivants :

- Nikon Z 6
- Nikon Z 7

Le "Filtre de lignes PDAF" n'a aucun effet sur les bandes PDAF des
Nikon.

## Equilibrage du vert

<img src="/images/645D_amaze_crosshatch_pattern.jpg"
title="645D_amaze_crosshatch_pattern.jpg" width="900"
alt="645D_amaze_crosshatch_pattern.jpg" /> Certains appareils photo (par
exemple Olympus, Panasonic, Canon 7D et quelques appareils moyen format)
utilisent des filtres verts légèrement différents dans chacun des deux
canaux verts du [filtre de
couleur](https://en.wikipedia.org/wiki/Color_filter_array) dans le
capteur de l'appareil. Cela n'est généralement pas une caractéristique
du capteur, mais plutôt une conséquence des limites du procédé de
fabrication quand le filtre de couleur est appliqué sur la surface du
capteur. Un filtre vert peut attraper une petite pollution du filtre
rouge et un autre vert, du filtre bleu par exemple. Equilibrage du vert
supprime les artefacts d'interpolation qui pourraient résulter de
l'utilisation d'algorithmes de dématriçage qui supposent des filtres
identiques en réponse dans les deux canaux de vert. Le seuil détermine
la différence de pourcentage en dessous de laquelle les valeurs de
pixels verts avoisinants sont équilibrées.

Choisir une valeur suffisante pour faire disparaître les labyrinthes
mais pas plus. L'algorithme de dématriçage DCB est très sensible à la
séparation du vert, il est donc recommandé de l'utiliser pendant la
recherche de la meilleure valeur.

L'équilibrage du vert peut aussi être utilisé pour égaliser la
séparation du vert causée par la diaphonie. Si, par exemple avec un
adaptateur, vous utilisez un objectif grand angle sur votre appareil
photo, la lumière entrante arrive sous un angle si fermé qu'une partie
traverse le filtre de couleur puis est enregistrée au niveau du pixel
voisin appartenant à un autre canal de couleur, cela est la diaphonie.
Comme un canal vert a des voisins bleus et l'autre des voisins rouges,
le premier captera une diaphonie du bleu et l'autre du rouge, d'où une
séparation qui peut provoquer des motifs en labyrinthes. Les canaux
rouges et bleus, dans une telle situation souffriront aussi de la
diaphonie, mais comme ils ne capteront que celle du vert il n'y a pas de
séparation dans ces canaux. La diaphonie modérée n'aura aucun effet
visible si le vert est égalisé, alors qu'une diaphonie importante
apparaîtra sous forme de couleurs dé-saturées non désirées (car les
canaux ont été mélangés). Notez que la diaphonie ne se produit
généralement pas en cas de forte dominante de couleur, mais dans ce cas,
utilisez aussi la correction par champ uniforme.

## Filtrer les pixels chauds/morts

Cet outil supprime les [pixels morts ou
chauds](https://en.wikipedia.org/wiki/Defective_pixel) pixels morts ou
chauds en les remplaçant par la moyenne du voisinage.

<figure>
<img src="/images/Rt-43_hotdead1.jpg" title="Rt-43_hotdead1.jpg" width="900" />
<figcaption>Rt-43_hotdead1.jpg</figcaption>
</figure>

Les "Pixels chauds" apparaissent sous le forme de minuscules points
brillants et saturés. Ils sont chacun d'eux le résultat de la délivrance
d'un courant plus élevé qu'il ne devrait par un photosite du capteur. Le
fait qu'un seul photosite du capteur corresponde à un seul pixel de
l'image traitée dépend de la méthode choisie de dématriçage (et autres
outils) ; la plupart des méthodes, telle que AMaZE celle par défaut,
n'associent pas de rapport direct entre photosite et pixel, et donc les
pixels chauds peuvent apparaitre non seulement comme des points d'un
seul pixel mais aussi comme de minuscules croix de 3x3 pixels ou de
gouttes légèrement plus grosses. La présence de pixels chauds est un
phénomène tout à fait normal dans tous les appareils photo, cependant
vous n'en trouverez pas dans des photos ordinaires prises en lumière du
jour. Plus l'exposition est longue, plus élevée est la probabilité
d'apparition des points chauds et plus important est leur nombre, les
expositions supérieures à deux secondes sont généralement considérées
comme sujettes à ce problème. La chaleur est aussi un facteur aggravant,
les capteurs chauds étant plus sensibles au problème.

Les "Pixels morts" d'un autre coté apparaissent sous la forme de points
(ou croix ou gouttes) noirs. Ils sont le résultat de photosites morts
sur le capteur, et comme tels, le temps d'exposition n'a aucune
influencce sur leur apparition, si un photosite est mort, chaque photo
aura un pixel mort au même point. En raison de leur position statique et
toujours présente tant que l'on utilise le même boitier, il est possible
de les traiter non seulement en utilisant le "Filtre pixel mort"
automatique mais aussi en ajoutant leurs coordonnées dans un fichier
*.badpixels* ; voir [Mauvais
pixels](Dark_Frame/fr#Mauvais_pixels.md).

<figure>
<img src="/images/Rt-43_hotdead2_artifacts.jpg"
title="Rt-43_hotdead2_artifacts.jpg" width="900" />
<figcaption>Rt-43_hotdead2_artifacts.jpg</figcaption>
</figure>

Il est impossible de détecter les pixels chauds ou morts avec certitude
par l'analyse d'une seule photo (par opposition à l'analyse de toute une
série de photos), mais il faut cependant trouver un juste équilibre
entre le retrait justifié et les [faux
positifs](http://en.wikipedia.org/wiki/False_positives_and_false_negatives).
Le curseur de seuil permet de définir la sensibilité de la détection
automatique des points chauds ou morts. Les valeurs les plus basses
rendent la détection des pixels chauds/morts plus agressive, mais les
faux positifs peuvent provoquer des artéfacts. Si vous remarquez
l'apparition d'artéfacts lors de l'activation des Filtres pixels
chauds/morts, augmentez graduellement la valeur du seuil jusqu'à leur
disparition.
