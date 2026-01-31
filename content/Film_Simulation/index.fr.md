---
title: Film Simulation
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Simulation de Film

</div>

<img src="/images/Rt_haldclut_london.jpg" title="Rt_haldclut_london.jpg"
width="900" alt="Rt_haldclut_london.jpg" /> L'outil *Simulation de Film*
permet en un seul clic de donner à une photo les couleurs d'une image de
référence choisie. Cet outil nécessite l'utilisation d'images de
références sur le modèle HaldCLUT, au format PNG ou TIFF. CLUT pour
"Color Look-Up Table" = Table couleur de correspondance. Chaque image
HaldCLUT correspond à un "aspect". Bien que l'aspect peut être basé sur
n'importe quoi, la plupart des images de référence que nous fournissons
sont basées sur des pellicules standard, d'où le nom de l'outil.

RawtTherapee a besoin d'accéder à ces images HaldCLUT, pour vous
permettre d'utiliser l'outil. Vous pouvez soit télécharger note
collection appelée [Collection de Simulation de Film de
RawTherapee](Film_Simulation/fr#Collection_de_Simulation_de_Film_de_RawTherapee.md),
ou bien la réaliser vous-même. Vous en saurez plus à ce sujet plus loin.
A la première utilisation de l'outil, vous verrez un message vous
informant de la nécessité d'indiquer à RawTherapee le dossier qui
contient les images de références. Une fois qu'elles sont prêtes dans un
répertoire, allez dans "Préférences \> Traitement de l'image \>
Simulation de Film" et indiquez le dossier qui les contient dans
"Dossier HaldCLUT".

## Mise en route

A chaque démarrage du programme, RawTherapee va balayer le dossier
HaldCLUT désigné, c'est pourquoi il est important de créer un dossier
qui ne servira qu'au stockage de ces images Hald CLUT et rien d'autre
afin que RawTherapee ne perde pas son temps a balayer des fichiers non
concernés. Par mesure de sécurité, vous serez prévenu si le scan au
démarrage prend plus de 10 secondes. Si cela se produisait, simplement
cliquer sur le bouton dans la fenêtre qui apparaît pour arrêter le scan,
puis allez dans "Préférences \> Traitement de l'image \> Simulation de
Film" pour voir quel est le dossier utilisé, et indiquer à RawTherapee
soit un dossier qui ne contient que des images HaldCLUT et rien d'autre,
soit un dossier vide si vous ne désirez pas utiliser l'outil Simulation
de Film.

Pour vous donner un idée de l'impact important sur le temps de
démarrage, la différence entre avoir 500 images dans le dossier HaldClut
(ce qui est plus que dans notre collection), et n'en avoir aucune est
d'environ 100ms, ce qui n'est rien. Si cependant, vous aviez par
accident informé RawTherapee que le dossier HaldCLUT est
`C:\Program Files (x86)`, alors le démarrage pourrait même prendre
plusieurs minutes, car ce répertoire contient des centaines de milliers
de fichiers. Comme vous pouvez le constater, il n'y a aucune raison de
s'inquiéter lors de l'utilisation des HaldCLUT à la condition d'utiliser
un dossier dédié, ne contenant que des images HaldCLUT.

## Fonctionnement

<figure>
<img src="/images/Hald_CLUT_Identity_12.png"
title="Hald_CLUT_Identity_12.png" />
<figcaption>Hald_CLUT_Identity_12.png</figcaption>
</figure>

L'outil Simulation de Film utilise des images spécialement préparées en
ce qui s'appelle le modèle HaldCLUT. "CLUT" signifie "Color Look-Up
Table" pour "Table couleur de correspondance", alors que la
signification de "Hald" est laissée aux suppositions de chacun. Une
image HaldCLUT contient un jeu de gradients des différentes teintes
disposés en matrice. L'état neutre, inchangé est appelé une "image
HaldCLUT identité". Appliquer un HaldCLUT identité à une photo ne
produira aucun changement. Pour créer un "look", l'image identité est
ouverte par un programme d'édition d'image, n'importe quel programme
d'édition d'image, et les couleurs sont modifiées de façon globale, par
exemple en utilisant les niveaux, les courbes, en modifiant les teintes
et la saturation, etc. Seuls les réglages globaux comme ceux listés
doivent être utilisés, les réglages locaux ne sont pas compatibles avec
le mode de fonctionnement du principe; par exemple, il est impossible
qu'une image HaldCLUT donne un rendu de compression tonale, elle ne peut
non plus réduire le bruit, augmenter la netteté, mais elle peut donner
un aspect plus bronzé à la peau et les feuillages plus éclatants.

Bien que l'image HaldCLUT ressemble à un jeu de gradients, ce qu'elle
est réellement, c'est une représentation graphique d'une matrice de
nombres. Ces nombres sont les valeurs de "sortie" ou "résultat". Les
valeurs "entrée" ou "source" sont connues de tous les programmes qui
supportent les images HaldCLUT. Ces programmes savent par exemple qu'un
pixel à la position x=143 y=0 doit être pur rouge RVB=(100%, 0%, 0%). Si
vous éditez l'image identité et changez ce pixel pour le rendre moins
rouge, disons plus orange, puis sauvez cette image identité modifiée
dans un nouveau fichier HaldCLUT, alors chaque fois que vous utiliserez
ce fichier, RawTherapee appliquera le même changement à tous les pixels
de rouge pur. Cela signifie que si vous désirez rendre une certaine
nuance de rouge plus orange, vous n'avez pas besoin pour cela d'éditer
des nombres ennuyeux, vous ouvrez simplement l'image HaldCLUT identité
dans un éditeur d'image tel que RawTherapee ou GIMP, ajustez cette
nuance de rouge (ou plus concrètement, vous réalisez des ajustements
globaux qui affectent toutes les couleurs ou toutes les nuances de
rouge, en manipulant par exemple les courbes RVB), et enregistrez
l'image HaldCLUT. Utilisez là maintenant avec RawTherapee sur toute
photo pour renouveler les mêmes ajustements.

Le choix du profil colorimétrique assigné à l'image HaldCLUT ne devrait
pas faire de différence. L'important, ce sont les valeurs des piixels,
car souvenez vous, une image HalCLUT est simplement une matrice de
valeurs de "sortie". Assigner un profil colorimétrique ne modifie pas
les valeurs enregistrées de pixels, mais "appliquer" ou "convertir"
modifie bien les valeurs des pixels, ne faites donc pas cela. Ceci dit,
le profil colorimétrique assigné pourrait avoir une influence, car un
programme d'édition d'image peut changer l’espace de travail en fonction
du profil colorimétrique assigné.

La précision de la transformation des couleurs dépend du nombre de
niveaux (colonnes) dans l'image HaldCLUT, et du nombre de bits de
profondeur utilisés pour enregistrer l'image HaldCLUT. Si vous
travaillez sur une image 32 bits (ou dans n'importe quelle profondeur
d'image dans un espace 32 bits) avec un HaldCLUT 12-niveaux enregistré
dans un fichier 8 bits, par exemple, le HaldCLUT enregistre les valeurs
des couleurs avec moins de précision que votre image (ou espace de
travail) peut en stocker. Ceci ne devrait pas être un problème, car les
couleurs inconnues sont interpolées depuis les valeurs connues, donc il
ne devrait pas y avoir de pixellisation. La profondeur de l'image
utilisée pour enregistrer le HaldCLUT dépend de vos besoins et n'est pas
strictement liée au nombre de niveaux contenus par le HaldCLUT. Les
photographes peuvent utiliser avec raison des HaldCLUT 8-niveaux
enregistrés dans des image 8 bits même en cas de traitement de photos
d'un plus grand nombre de bits de profondeur.

Pour plus d'informations, se reporter sur la page d'Eskil Steenberg
consacrée au HaldCLUT :

<http://www.quelsolaar.com/technology/clut.html>

Pour générer une image HaldCLUT 16 bits de niveau 12 de référence (qui
ne modifie pas la photo) en utilisant ImageMagick, lancez cette commande
dans une console :

`convert hald:12 -depth 16 -colorspace sRGB hald12_16bit.tif`

## Mise en garde

Nous vous recommandons d'utiliser ImageMagick pour générer l'image de
référence si vous avez besoin d'en générer une, car le programme pour le
faire sur www.quelsolaar.com souffre d'un bug qui peut causer des
problèmes avec les hautes lumières. Vous pouvez bien sur utiliser le
fichier de référence que nous fournissons ici - garanti sans bug. Plus
loin, nous vous recommandons d'utiliser Hald CLUTs en format TIFF si
vous utilisez RawTherapee-4.2.140 ou plus ancien, vu qu'il y avait un
petit bug sur le gamma qui rendait l'image globalement légèrement plus
sombre. Ce bug a été résolu dans la version 4.2.141. Vous pourriez bien
sûr totalement ignorer le problème si vous utilisez Hald CLUTs à des
fins esthétiques, car l'assombrissement est subtile et peut facilement
être compensé avec les les curseurs ou courbes d'exposition de
RawTherapee, ou bien en prétextant que cela fait partie de l'effet
désiré du CLUT.

## Créer votre collection

Ce chapitre explique comment exploiter le fichier de référence HaldCLUT
afin qu'il produise un effet spécifique sur la couleur et la luminosité.

1.  Ouvrir une photo dans RawTherapee ou tout autre éditeur d'image et
    arrangez la à votre goût. Souvenez vous que l'outil Simulation de
    Film ne peut reproduire des changements de tonalité que sur l'image
    entière, ne donc jamais faire de modifications locales, pas de
    contraste local, pas de virage partiel, etc. ; ne pas faire de
    modifications qui déplacent des pixels, pas de correction de
    distorsion ; pas de netteté ni de réduction du bruit ; ne faire que
    des ajustements sur toute l'image de la tonalité, de la saturation,
    de courbes, de niveaux et des ajustements L\*a\*b\*. Enregistrer le
    fichier accolé ou recopier les arrangements que vous avez réalisés
    de façon à pouvoir reproduire ces arrangements dans l'étape
    suivante.
2.  Ouvrir l'image de référence HaldCLUT dans le même programme et y
    appliquer le même fichier accolé ou refaire les mêmes arrangements
    qu'à l'étape précédente.
3.  Enregistrer cette image au format TIFF ou PNG 8-bit sRGB dans le
    dossier HaldCLUT indiqué à RawTherapee. C'est maintenant prêt pour
    utilisation. Redémarrer RawTherapee pour que votre nouveau Hald CLUT
    apparaisse dans la liste.

Même si votre image HaldCLUT contient des couleurs avec une précision de
seulement 8 bits, les valeurs manquantes seront interpolées de façon à
éviter l'apparition de postérisation dans la photo. En conséquence,
puisqu'il n'y a pas de perte visuelles de qualité, nous recommandons
d'utiliser le niveau 12 de l'image HaldCLUT de référence, ou même un
niveau 8, et de sauvegarder vos propres réalisations d'images HaldCLUT
dans un fichier PNG ou TIFF à 8 bits par canal.

Le profil de couleur assigné à l'image HaldCLUT sauvegardée n'a pas
d'importance. Ce qui importe sont les valeurs des pixels de cette image.
Vous êtes peut-être familier des termes "profil couleur assigné" versus
"conversion dans le profil de couleur" dans GIMP ou Photoshop, le profil
de couleur assigné est sans importance car il ne modifie pas les valeurs
des pixels, mais la conversion importe car cette fois les valeurs des
pixels changent. Lors de l'édition de l'image HaldCLUT dans RawTherapee,
le choix du [profil de couleur de
sortie](Color_Management/fr#Profil_de_sortie.md) importe car il
modifie les valeurs des pixels de l'image enregistrée. Comme l'image
identité que nous fournissons ou générée selon notre recette utilise les
chromaticités primaires sRGB, ainsi vous devez utiliser RTv2_sRGB ou
RTv4_sRGB pour sa sauvegarde afin de préserver les couleurs

Si vous appliquez ce HaldCLUT à une photo dans RawTherapee et que cette
photo devient considérablement et de façon inattendue plus claire ou
plus foncée que ce qui était espéré, c'est probablement du au programme
avec lequel vous avez traité la photo qui est intervenu sur le gamma.
Pour y remédier, vous devez retirer ce que ce programme a fait. essayez
de générer votre propre HaldCLUT de niveau 12, mais au lieu d'utiliser
l'espace colorimétrique "sRGB", prenez simplement "RVB".

### Avancé - DNG de référence

Cela est expérimental, le fonctionnement n'est pas garanti.

Certains programmes peuvent ne pas vous laisser ouvrir une image TIFF.
Si le programme supporte les fichiers DNG, et les dématricés à ce format
(ce que DNG Converter d'Adobe appelle "(Dématricé) linéaire"), alors
essayez ce truc. Il utilise ImageMagick, ExifTool et les commandes
ci-dessous, exploitant le fait que DNG est simplement une forme de TIFF,
vous pouvez générer un HaldCLUT de référence au format DNG :

    convert hald:12 -depth 16 -colorspace RGB -gravity NorthWest -splice 4x4 -gravity SouthEast -splice 4x4 foo.tif
    exiftool -DNGVersion=1.4.0.0 -PhotometricInterpretation='Linear Raw' foo.tif
    mv -v foo.tif Hald_CLUT_Identity_12.dng

Les programmes d'édition Raw annulent un certain nombre de lignes et de
colonnes de pixels sur les bords de l'image pour des raisons techniques
en rapport avec le dématriçage. Combien de lignes et de colonnes seront
supprimées dépend entièrement du programme. Vous devez comprendre cela.
Un HaldCLUT de référence de niveau 12 aura précisément 1728x1728 pixels.
Quand vous traitez ce CLUT dans un programme à qui sont ces effets de
couleurs que vous essayez d'émuler, l'image enregistrée doit avoir
précisément 728x1728 pixels. Puisque vous trompez le programme en lui
faisant croire qu'il travaille sur un fichier raw, et puisqu'il annulera
sans doute quelques pixels auprès des bords, vous devez savoir
exactement combien combien de lignes et de colonnes blanches
supplémentaires sont nécessaires et les ajouter autour de l'image.
RawTherapee enlève 4 pixels tout autour lors de la lecture des fichiers
DNG dématricés, ainsi, la commande ci-dessus ajoute d'abord une ligne et
un colonne de 4 pixels sur les cotés du bas et de droite, puis a nouveau
une ligne et un colonne de 4 pixels sur les cotés du haut et de gauche.
Quand vous ouvrez cette image dans le programme cible, zoomez sur le
bord de chaque coté et observez s'il est nécessaire d'en ajouter (ou
d'en retirer) un peu, modifier alors la commande en conséquence.

Une fois que les bordures sont réussies, simplement ouvrir ce DNG dans
le programme cible et suivre les étapes données ci-dessus dans le
chapitre "Créer votre collection".

## Naviguer dans RawTherapee

Il y a beaucoup de HaldCLUT dans notre collection et vous allez surement
vouloir tous les essayer. Vous n'avez pas besoin de cliquer sur chaque
avec la souris ! Il existe une façon facile de tous les tester, un par
un, sans besoin de la souris. En supposant que vous avez déjà configuré
RawTherapee pour qu'il pointe sur le dossier HaldCLUT, que vous avez une
photo d'ouverte et que l'outil Simulation de Film est prêt à
l'utilisation, simplement choisir n'importe quelle image HaldCLUT dans
la boîte combo et utiliser les touches "haut" et "bas" du clavier pour
appliquer la précédente ou la suivante. Grâce à cette astuce, vous
pouvez même sauter par dessus les sous dossiers, par exemple depuis Noir
et Blanc à Couleur si vous utilisez notre collection.

Si vous vous vouliez comparer les effets de plusieurs HaldCLUT
spécifiques, alors qu'ils ne sont pas consécutifs dans la boite combo,
un moyen facile de passer de l'un à l'autre est de [faire des
captures](The_Image_Editor_Tab/fr#Captures.md) après les avoir
tous appliqués tour à tour, puis de cliquer sur les captures.

## Collection de Simulation de Film de RawTherapee

Cette archive contient une collection de HaldCLUT de films de simulation
que vous pouvez appliquer à vos photos pour instantanément leur donner
les couleurs sur lesquelles sont basés les HaldCLUT des films standards.
Sauf indication contraire dans le nom de fichier, ils sont tous dans
l'espace colorimétrique sRVB, 8-bit par canal, dans le format image PNG.
La plupart d'entre eux sont conçus pour imiter divers films référencés,
poussés ou tirés de différentes façons ou bien ternis par le temps.

Appliquez ces images à vos photos avec un logiciel adapté au Hald CLUT
tel que RawTherapee-4.2 pour instantanément obtenir une photo aux
couleurs correspondantes à la référence choisie.

Les suffixes +, ++, +++, -, --, --- se réfèrent à la force avec laquelle
le film fut [poussé](https://en.wikipedia.org/wiki/Push_processing) lors
du développement (non-linéaire), et "generic" se réfère au type de film
habituellement vendu aux revendeurs.

[Téléchargement](http://rawtherapee.com/shared/HaldCLUT.zip) (402 Mo!)

Changelog  
20-09-2015  
Ajouté la collection de couleur "CreativePack-1"

Tous les TIFF convertis en PNG (sauf pour l'image de référence)

25-03-2015  
Le CLUT de référence avait un bug donnant des couleurs cyan dans les
hautes lumières, il a été remplacé par un autre corrigé.

Numérotage des fichiers, ainsi ils peuvent être triés dans le bon ordre
lorsqu'il sont "pushed" ou "pulled" (--, -, normal, +, ++).

25-08-2014  
Première édition pour le publique.

Ré-organisation en sous-répertoires *Couleur* et *Noir-et-blanc*, triés
par marques.

15-08-2014  
fichier README.txt complet et ajout d'un avis légal.

05-07-2014  
Première édition interne.

Toutes les images sont re-compressées avec une compression sans pertes
maximale.

En savoir plus à propos du HaldCLUTs :

  
<http://www.quelsolaar.com/technology/clut.html>

<http://blog.patdavid.net/2013/08/film-emulation-presets-in-gmic-gimp.html>

<http://blog.patdavid.net/2013/09/film-emulation-presets-in-gmic-gimp.html>

Crédits:

  
Pat David - <https://discuss.pixls.us/u/patdavid>

Pavlov Dmitry -

Michael Ezra - <https://discuss.pixls.us/u/michaelezra>

Déclaration légale:

  
Les noms de marques qui peuvent apparaître dans le nom de fichier des
images HaldCLUT sont là dans un but informatif uniquement. Ils servent à
renseigner l'utilisateur de quel film une image HaldCLUT donnée est
conçue pour s'approcher. Comme il n'existe pas d'autre moyen de donner
cette information qu'en citant le nom de la marque, nous pensons que
cela en constitue une utilisation régulière. Ni l'éditeur ni les auteurs
ne sont affiliés aux ou avalisés par les compagnies qui possèdent ces
noms de marques.
