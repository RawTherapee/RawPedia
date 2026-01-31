---
title: Dark Frame
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Trame Noire

</div>

[Soustraction de trame
noire](https://en.wikipedia.org/wiki/Dark-frame_subtraction) est une
méthode pour traiter le bruit d'origine thermique, le courant
d'obscurité et le motif de bruit fixe. Elle est sans effet contre le
bruit des hauts ISO en raison de sa nature différente, aléatoire. Dans
les prises de vues de longue exposition (plus de 1 sec) le bruit
thermique non homogène devient évident, principalement du aux
irrégularités du capteur et de l'électronique environnante. Une méthode
pour réduire cet effet consiste à soustraire une (ou plusieurs) prises
de vues réalisées dans les mêmes conditions, mais avec le bouchon sur
l'objectif. Seules les images raw du même appareil photo peuvent être
utilisées comme Trame Noire, de préférences prises avec
approximativement le même temps de pose que la photo à traiter. Vu que
réaliser une photo Trame Noire consiste simplement à mettre le bouchon
d'objectif et à déclencher à nouveau sans rien changer aux réglages, ce
n'est pas un problème.

Dans le panneau "Trame noire", vous pouvez spécifier une prise de vue
unique à soustraire de l'image, ou bien cocher "Sélection automatique"
et laisser RT choisir la prise de vue la plus adaptée dans un dossier
spécifié dans "[Préférences](preferences/fr) \> Traitement de
l'image \> Trame Noire". Sous le widget, RT montre combien de prises de
vues sont trouvées et combien de groupes de prises de vue sont trouvés
et moyennés en un modèle. A partir de maintenant, si ce n'est déjà fait,
mettez ici vos images de Trame Noire. Vous pouvez aussi déplacer une
prise de vue depuis l'onglet "Navigateur de fichiers" vers le dossier
Trame Noire par un clic droit sur l'image puis en sélectionnant "Trame
Noire \> Déplacer dans le dossier d'images de Trame Noire". RT choisit
la Trame Noire la plus adaptée en cherchant les images prises avec le
même modèle d'appareil photo et ayant les moindres différences en nombre
d'ISO, temps d'exposition et date. Si plus d'une image est trouvée avec
exactement les mêmes propriétés, alors une moyenne de celles-ci est
utilisée ; cela produit beaucoup moins de bruit ; il est donc préférable
d'avoir 4 à 6 prises de vue prises dans les mêmes conditions que la
photo en cours.

Lors de la sélection d'une Trame Noire (ou avec "Sélection
automatique"), RT en extrait toutes les positions de pixels chauds et
les corrige alors dans l'image finale. Cette correction est meilleure
que la seule application de "Filtre des pixels Chauds/Froids", mais ne
fonctionne que pour les pixels chauds (= blancs), pas pour les pixels
morts (=noirs).

## Logique de recherche auto de la Trame Noire

Clés des Trames Noires (dfInfo::key):

- fabricant de l'appareil photo
- modèle de l'appareil photo
- ISO
- vitesse de l'obturateur

La recherche pour la meilleure correspondance se fait en 2 temps :

- si une correspondance parfaite par la clé est trouvée, alors la liste
  est scannée pour identifier le plus récent fichier,
- sinon, le fichier le plus proche en ISO et vitesse d'obturation est
  recherché dans la liste.

## Mauvais pixels

RawTherapee peut corriger une liste de [mauvais
pixels](https://en.wikipedia.org/wiki/Defective_pixel) (pixels toujours
noirs ou blancs ou toujours de la même couleur) pour votre modèle
particulier d'appareil photo. Pour cela, vous devez écrire un fichier
texte avec les coordonnées raw absolues de ces pixels. Chaque ligne
spécifie un pixel avec les positions `x `<espace>` y `<entrée>.

**Important**: RawTherapee enlève des pixels des bords haut et gauche de
l'image raw (car ils ne peuvent pas être interpolés correctement). Si
vous regardez les coordonnées de pixels dans RawTherapee, ayez
conscience du décalage introduit par cette coupure des bords. A chaque
coordonnée, vous devez ajouter 4 pour un capteur Bayer et 7 pour un
capteur X-Trans. Vous pouvez aussi préciser le décalage (4 pour Bayer et
7 pour X-Trans) dans la première ligne du fichier .badpixels.

Le fichier doit être placé dans le dossier trame noire. Définissez le en
allant dans "*Préférences
[image:preferences.png](image:preferences.png) \> Traitement
de l'image \> Soustraction de Trame Noire*". Les fichiers doivent être
nommés exactement selon le fabricant et modèle de l'appareil photo :
"*fabricant modèle.badpixels*". Obtenez les désignations du fabricant et
du modèle tels que RawTherapee les attend en ouvrant une image raw que
vous désirez corriger dans l'onglet
[Editeur](the_image_editor_tab/fr) et en regardant les nom et
modèle affichés par l'icône "Informations rapides"
![Image:info.png](info.png "Image:info.png"), raccourci "**i**", ex :
"`Pentax K200D.badpixels`"

Souvenez vous que ces fichiers.badpixels doivent être placés dans le
dossier Trame Noire spécifié dans Préférences !

Si vous avez suivi correctement les différentes étapes et si cela ne
fonctionne pas, vérifiez que le fichier badpixels est bien lu, fermez
RawTherapee et éditez le fichier "[options](file_paths/fr)"
dans un éditeur de texte et changez la ligne "*Verbose=false*" par
"*Verbose=true*", puis démarrez RawTherapee depuis une console, ouvrir
la photo que vous souhaitez corriger, et observez le texte affiché dans
la console. Si vous voyez un message comme "*Pentax K10D.badpixels not
found*" *(Pentax K10D.badpixels non trouvé)* alors vous savez comment
renommer le fichier badpixels. Une fois que cela fonctionne, n'oubliez
pas de remettre "*false*" à la place de "*Verbose*".

Les pixels repérés dans la liste des mauvais pixels seront toujours
corrigés dans les photos traitées dès que le fabricant et le modèle
d'appareil photo correspondent au nom du fichier badpixels.

## Logiciels de détection des mauvais pixels

Il existe des programmes pour aider dans la détection des mauvais pixels
:

Dead Pixel Test  
<http://www.starzen.com/imaging/deadpixeltest.htm> (mort)

Miroir:
<https://web.archive.org/web/20140725130003/http://www.starzen.com/imaging/deadpixeltest.htm>

Miroir: <http://rawtherapee.com/mirror/deadpixeltest.zip>

  
Ce fichier est [garanti sans
virus](https://www.virustotal.com/en/file/11e7a0db897fd3ad9f3e24c97c73b178cfe9f9d246e3dadfe57113318e2def06/analysis/1421736881/).

Pixel Fixer  
<http://www.pixelfixer.org/>

Pensez à tenir compte de la suppression des bandes de 4 ou 7 pixels si
vous les utilisez une version de RawTherapee qui le nécessite.
