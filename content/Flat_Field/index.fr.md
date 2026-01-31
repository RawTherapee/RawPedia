---
title: Flat Field
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Champ Uniforme

</div>

[thumb](image:flatfield_landscape.jpg) La [correction Champ
Uniforme](https://en.wikipedia.org/wiki/Flat-field_correction) est
utilisée pour compenser les non-uniformités caractéristiques de
l'ensemble appareil photo plus objectif. Un exemple bien connu de ce
genre de non uniformité est le vignettage, un assombrissement
périphérique de l'image, plus prononcé dans les coins. Un autre exemple,
plus familier aux utilisateurs d'appareil photo numérique moyen format,
est la dominante de couleur due à l'objectif, à la fois la couleur et la
luminance présentent des non uniformités dans l'image. Ces deux exemples
de non uniformité de l'image peuvent ensuite être compliqués par un
mauvais alignement possible de l'objectif ou par l'usage d'objectif à
décentrement. D'autres exemples de non-uniformités dans la prise de vues
peuvent être dus à des infiltrations de lumière dans l'appareil photo, à
des écarts de température dans le capteur ou à des défauts/irrégularités
dans l'électronique de lecture du capteur. Un autre nom utilisé pour
cette fonction par d'autres logiciels de traitement raw est "Correction
LCC", pour Lens Color Cast (Dominante de couleur de l'objectif), mais la
correction Champ Uniforme est la meilleure dénomination car, comme
décrit, il peut corriger bien des sortes de non-uniformités, pas
seulement la dominante de l'objectif.

La correction manuelle de ces effets en post-traitement est assez
difficile ; surtout lorsqu'elle doit être reproduite pour une série
d'images réalisées sous des conditions changeantes ; et donne rarement
de bons résultats.

L'outil de correction du "Champ Uniforme" dans RawTherapee permet le
mode automatique et le mode manuel assisté. La correction du Champ
uniforme n'est réalisée que sur les données raw linéaires au début du
processus de traitement de l'image et n'introduit pas de modifications
dues au gamma. Ainsi, dans RawTherapee, la correction Champ uniforme ne
peut s'appliquer qu'aux fichiers raw seulement.

Pour raison de prise en considération des performances, les images en
vignettes ne prennent pas en compte les corrections du Champ Uniforme.
Aujourd'hui, seul [l'aperçu
principal](The_Image_Editor_Tab/fr#Le_panneau_Aperçu.md) dans
l'onglet [Editeur](the_image_editor_tab/fr#le_panneau_aperçu)
et l'image de sortie peuvent être corrigées par Champ Uniforme.

La précision de la correction du Champ Uniforme dépend largement de
l'utilisation de l'image Champ Uniforme appropriée, qui doit satisfaire
les exigences du type de correction désiré, soit la non-uniformité
objectif/appareil photo, ou la même chose avec en plus le retrait des
points de poussière. La création des images Champ Uniforme pour les deux
usages est décrite dans la prochaine section.

[thumb](image:flatfield_remove_itself.jpg) Pour illustrer la
correction Champ Uniforme, une image champ uniforme a été appliquée à
elle-même. On constate une asymétrie importante dans l'image "avant",
celle du haut, autant pour la luminosité que pour la dominante verte. La
correction par Champ uniforme enlève à la fois les non uniformités de
luminosité et de couleur et donne une image parfaitement uniforme.
L'histogramme de l'image du bas, "après", indique que l'image corrigée
n'a plus aucune variation de tonalité, exactement ce que l'on est en
droit d'attendre d'un champ uniforme. Le même niveau de correction est
appliqué à l'image "réelle" lorsqu'elle est corrigée par le Champ
uniforme.

Tous les paramètres du panneau "Champ Uniforme" sont sauvegardés dans le
profil de traitement. Ces paramètres peuvent être copiés et collés pour
d'autres images exactement comme tout autre paramètre y compris l'option
"Sélection automatique". La coller à différentes images provoquera une
sélection, automatique et indépendante, du champ uniforme approprié pour
chacune d'entre elles.

## Création et utilisation des images Champ Uniforme pour la correction des aberrations des appareils photo et objectifs

Il est suffisant de ne faire qu'une seule prise d'image champ uniforme
en utilisant les mêmes réglages du boitier et de l'objectif que ceux
retenus pour l'image à corriger. Il est inutile de réaliser plusieurs
prises avec les mêmes réglages, contrairement au cas de la trame noire
où dans le but d'obtenir une meilleure qualité vous devez prendre
plusieurs prises avec les mêmes réglages et les fusionner dans le but
d'accroître le rapport signal/bruit. Cela est inutile avec les images
champ uniforme qui sont floutées et prises avec un faible ISO : 100 si
possible. La balance des blancs ne sert à rien. Le niveau de mise au
point de l'objectif pendant la prise du champ uniforme pour la
correction de l'aberration appareil/objectif n'a pas à correspondre à
celle de l'image à corriger (cela n'est pas vrai si vous prenez des
images champ uniforme en vue de supprimer les taches de poussière, comme
expliqué dans cette section). Maintenir l'objectif non focalisé pendant
la prise de l'image champ uniforme, elle doit être une photo
dé-focalisée d'une lumière uniforme, uniformément colorée et d'une seule
tonalité.

La meilleure méthode pour réaliser une telle image champ uniforme est
d'utiliser un morceau uniforme de [Polyméthacrylate de
méthyle](https://fr.wikipedia.org/wiki/Polym%C3%A9thacrylate_de_m%C3%A9thyle),
laiteux et semi-opaque (PMMA, vendu sous les noms commerciaux de
Acrylite, Lucite, Perspex, Altuglas et Plexiglas). Il doit être uni,
sans couleur, sans symboles ni inscriptions gravées ou
[embossées](https://fr.wikipedia.org/wiki/Embossage). Des feuilles sont
disponibles dans les quincailleries et magasins d'art, ou bien vous
pouvez avoir la chance de trouver un récipient vide fabriqué avec ce
matériau, les bidons de [Nordsjö
Vävlim](http://www.nordsjoidedesign.se/se/PRODUKTER/Ovrigt/Tapettillbehor-1261.html)
conviennent bien. Découper un morceau de la taille du corps de
l'objectif, en cas d'objectif très grand angle, tel qu'un fisheye, alors
la taille doit être de plusieurs fois celle du corps de l'objectif, au
moins 20x20cm. L'épaisseur du PMMA doit être d'au moins 1 mm, de
préférence 3 mm ou plus, pour suffisamment flouter et répartir la
lumière le traversant. Si il est brillant, utiliser du sable pour rendre
la surface mate. Cela est maintenant votre filtre champ uniforme.

Tenir le filtre champ uniforme devant l'objectif (en contact avec
l'objectif), régler sur exposition automatique, et le photographier en
présence d'un éclairage uniforme (par ex : orienter l'appareil vers un
ciel clair). L'idée est de faire pénétrer un éclairage uniforme dans
l'objectif. En conséquence, toute non-uniformité du couple appareil
photo/objectif sera détectée dans l'image raw comme écart par rapport à
une réponse uniforme (champ uniforme) spatialement idéale. Faire une
prise de vue pour chaque ouverture principale (f/1.4, f/2, f/2.8, f/4,
f/5.6, f/8, f/11, etc.). Penser à régler l’exposition automatique à
chaque fois pour avoir un histogramme centré, sans dépassement de
domaine.

Si vous utilisez un objectif zoom plutôt qu'une focale fixe, il peut
être nécessaire de multiplier les prises à plusieurs intervalles de
zoom. Par exemple, pour un objectif 18-55mm, vous pouvez réaliser une
série de prises à 18mm, 36mm et 55mm. Faites vos propres tests avec
votre matériel, peut-être que la prise à 36mm sera la même qu'à 55mm et
vous pourrez alors éviter la série de prises à 55mm.

Si vous utilisez un objectif électronique, alors le nom de fichier est
sans intérêt car RawTherapee peut trouver automatiquement l'image champ
uniforme correcte, cependant en cas d'utilisation d'un vieil objectif
manuel qui n'enregistre pas l'ouverture ni la distance focale, alors
nommez vos fichiers comme suit :

` ff_`*<objectif>*`_`*<aaaammjj>*`_`*<distance_focale>*`_`*<ouverture>*`.`*<raw>*

exemple :

` ff_20141009_pentax18-55mm_36mm_f11.dng`

Cela permettra de les retrouver facilement à la main.

Appliquez les images champ uniforme à vos photos, en faisant
correspondre l'ouverture de l'image champ uniforme avec celle de la
photo, et régler le curseur "Rayon de floutage" à 32 ou plus.

Si vous n'avez pas pu trouver de feuille en PMMA et que vous en avez
besoin en urgence, vous pouvez prendre une photo très floue d'un mur
blanc uni ou d'une grande feuille de papier blanc mat. La difficulté ici
sera d'obtenir un éclairage uniforme, rappelez vous que la [loi en carré
inverse](https://fr.wikipedia.org/wiki/Loi_en_carr%C3%A9_inverse)
travaille contre vous. La source de lumière doit être éloignée et
diffuse, vous n'obtiendrez pas une bonne image de champ uniforme en
utilisant l'éclairage d'une pièce ou une lumière stroboscopique. Ne pas
remplacer la feuille en PMMA par une feuille de papier, celui-ci est
trop irrégulier, toutes les variations d'épaisseur ou de densité
créeront des zones plus claires/sombres qui seront soustraites de la
photo traitée. Si vous tenez à utiliser une feuille de papier, alors
prenez une grande feuille blanche, placez la à un endroit uniformément
éclairé, tel qu'un mur opposé à une grande fenêtre ou dehors sur le sol
et au soleil. Zoomer dessus, flouter, et prendre les photos de la façon
décrite ci-dessus.

## Création et utilisation des images Champ Uniforme pour effacer les tâches de poussière

Suivre soigneusement les instructions données ci-dessus, en appliquant
les changements et suppléments décrits ici.

Si vous désirez utiliser des images Champ Uniforme pour effacer les
tâches de poussière, il est conseillé de réaliser l'image champ uniforme
pas trop longtemps avant ou après la photo à laquelle elle est destinée,
car avec le temps de nouvelles tâches de poussière peuvent apparaître
sur le capteur et les anciennes peuvent bouger ou disparaître, et si
cela se produit, l'effacement parfait des tâches de poussière devient
impossible.

La principale différence entre l'utilisation d'un champ uniforme pour la
correction des aberrations appareil photo/objectif et pour l'effacement
des tâches de poussière est que dans ce cas, l'image ne doit pas être
floutée et cela entraîne quelques modifications. L'utilisation du filtre
champ uniforme décrit ci-dessus rendra ces prises de vues bien plus
faciles, plus rapides et plus précises. En plus de prendre une image
champ uniforme pour chaque ouverture, vous devez aussi prendre en compte
la distance de mise au point. Essayer d'appliquer une image champ
uniforme, pour effacement des tâches de poussière, prise à la distance
de mise au point de 0,5m à une photo ayant une distance de mise au point
à l'infini, aura toutes les chances d'échouer car la mise au point zoome
légèrement l'image, même avec les objectifs à focale fixe. Heureusement,
ce zoom est très faible, ainsi, si pour chaque ouverture, vous prenez
une photo à une faible distance de mise au point (par ex : 0,5m), une
autre à environ 2m et une à l'infini, cela suffira surement.

Les mêmes exigences, telles que décrites ci-dessus, s'appliquent pour
les objectifs zoom, ainsi que la procédure de nommage des fichiers. De
plus, il est conseillé d'inclure la distance de mise au point dans le
nom de fichier :

` ff_`*<objectif>*`_`*<aaaammjj>*`_`*<distance focale>*`_`*<ouverture>*`_`*<distance mise au point>*`.`*<raw>*

par exemple :

` ff_20141009_pentax18-55mm_36mm_f11_2m.dng`

Vous comprenez maintenant pourquoi avoir un petit filtre champ uniforme
en PMMA est si utile, au lieu de faire toute une série de prises champ
uniforme à la maison, vous pouvez simplement faire la prise nécessaire,
juste après la photo elle-même sans changer aucun réglage de l'appareil,
que vous soyez debout sur le haut de la montagne au lever du soleil ou
bien allongé dans les bois à photographier les champignons.

Lors de la prise de certains types de photos, par exemple les
macro-photos, j'ai tendance à rester sur f/11, car pour mon objectif
c'est le compromis optimal entre profondeur de champ et piqué. Si je
diminue l'ouverture, la
[diffraction](https://en.wikipedia.org/wiki/F-number#Effects_on_image_sharpness)
aura un effet négatif sur le piqué perçu. Toujours être à f/11 pour les
macros signifie aussi que je n'ai besoin que d'une ouverture par série
de prises champ uniforme. Les séries seront composées de trois prises :
une à f/11 avec la distance de mise au point au minimum, une à
mi-distance et une à l'infini. Avoir un filtre champ uniforme sous la
main rend cela très facile.

## Quand réaliser les prises Champ Uniforme

Comme décrit ci-dessus, se créer une bibliothèque contenant toutes les
séries de prises de vues nécessaires pour vos objectifs. Il faut la
mettre à jour à chaque achat de nouvel objectif ou boitier d’appareil
photo. De plus, si vous utilisez les prises Champ Uniforme pour
l'effacement des taches de poussière, il faut en faire de nouvelles
après un nettoyage du capteur et lorsque change la disposition des
poussières, c'est à dire de nouvelles taches apparaissent et des
anciennes disparaissent.

## Spécificité des algorithmes et résumé concis

[thumb](image:rt_ff_dust1.jpg) L'image raw Champ uniforme
sélectionnée par l'utilisateur ou automatiquement ne nécessite pas
d'avoir la même balance des blancs que l'image à laquelle elle est
appliquée. Le Champ uniforme est rendu flou selon n'importe lequel des
Types de floutage et Rayon de floutage sélectionnables par
l'utilisateur. Le Champ uniforme rendu flou sert de gabarit pour le
vignettage, les dominantes de l'objectif, etc. et est utilisé pour
rectifier les fichiers images de sortie correspondants. "Zone" utilise
un [flou encadré](https://en.wikipedia.org/wiki/Box_blur) du fichier
champ uniforme et est la méthode classique de correction. Utilisez un
grand Rayon de floutage pour adoucir l'image du Champ uniforme dans le
but d'atténuer les imperfections telles que le bruit, les taches de
poussières, etc. Utilisez un petit Rayon de floutage pour laisser ces
effets dans l'image du Champ uniforme et donc leur action dans l'image
corrigée. Ceci peut être mis à profit, par exemple si le Champ uniforme
présente les mêmes taches de poussière que l'image, l'utilisation d'un
Rayon de floutage de 0 à 1 pixel supprimera l'assombrissement causé par
la poussière éliminant ainsi les taches de poussières de l'image.
Utilisez les options de floutage "Vertical", "Horizonta"l ou "Vert. +
Horiz." si l'appareil photo génère du bruit en forme de lignes répétées,
tel qu'une répétition de lignes verticales.

## Organisation des Champs uniformes

[thumb](image:flatfield_flatfields.jpg) de RawTherapee..\]\]
La non uniformité des champs capturés dépend des paramètres suivants :

- Appareil photo (ensemble appareil et capteur si utilisation d'un [dos
  numérique](https://en.wikipedia.org/wiki/Digital_back) )
- Objectif
- Distance focale
- Ouverture
- Objectif à décentrement

Il est recommandé de constituer une bibliothèque de Champs Uniformes
pour les associations appareil photo / objectif, pris à différentes
ouvertures (susceptibles d'être utilisées pour de réelles prises de
vues). Il est conseillé de donner un nom descriptif à ces fichiers de
Champ uniforme pour qu'ils puissent être facilement identifiés par
l'utilisateur, de préférence incluant les paramètres cités ci-dessus.
Pendant le traitement de la correction du Champ uniforme ces paramètres
sont lus dans les données Exif et le contenu du nom de fichier est de ce
point de vue sans importance. Les fichiers de Champ uniforme sont
enregistrés avec profit dans un répertoire dédié. RawTherapee permet de
le déclarer dans "Préférences \> Traitement de l'image \> Champ uniforme
\> Dossier des images de Champ Uniforme". Déclarer le dossier Champ
uniforme dans la fenêtre des préférences initialise l'analyse de son
contenu. Le nombre de fichiers Champ uniforme et de modèles sont
rapportés dans l'interface utilisateur une fois le comptage terminé
(cela peut prendre un peu de temps selon le nombre d'images champ
uniforme).

## Options du menu contextuel Champ Uniforme du Navigateur de fichiers

[thumb](image:flatfield_moveto_fr.png).\]\] Vous pouvez
appliquer et gérer les images Champ Uniforme depuis l'onglet [Navigateur
de fichiers](The_File_Browser_Tab/fr.md), en cliquant droit sur
une vignette et en sélectionnant l'option "Champ Uniforme". Trois
sous-options vous seront présentées :

- "Sélectionner un Champ Uniforme ..." fait apparaître la boite de
  dialogue de sélection de fichiers pour sélectionner le champ uniforme
  devant être appliqué aux images sélectionnées.
- "Champ Uniforme auto" permet de lancer l'option "Sélection
  automatique" sur les images sélectionnées.
- "Déplacer vers le dossier de Champ Uniforme" déplace l'image
  sélectionnée dans le dossier spécifié dans
  [Préférences](preferences/fr).

  

## Sélection automatique

[left](image:flatfield_autoselection_fr.png)

Les possibilités de la Sélection automatique du Champ uniforme peuvent
être exploitées simplement en cochant la case "Sélection automatique".
RawTherapee recherchera alors parmi les fichiers du "Dossier des images
de Champ Uniforme" spécifié dans Préférences celui qui convient
exactement, ou s'il n'est pas présent celui qui s'en rapproche le plus,
à l'image devant être corrigée sur la base du fabricant de l'appareil
photo, de son modèle, de l'objectif, de la distance focale, de
l'ouverture et de la date du fichier Champ Uniforme. Si un fichier Champ
Uniforme convenable est trouvé, son nom sera affiché à coté avec la
valeur de l'ouverture. Si aucun fichier convenable n'est trouvé, la
correction du Champ Uniforme ne sera pas appliquée et un message sera
adressé à l'utilisateur. Si plus d'un fichier est trouvé, les données
seront moyennées et utilisées pour la correction.

Sélection automatique ne prend pas en compte les objectifs à
bascule/décentrement, les images champ uniforme pour ces objectifs ne
doivent donc pas être enregistrées dans le dossier champ uniforme
principal, mais plutôt dans un sous répertoire correctement nommé. Ces
images champ uniforme inhabituelles doivent être appliquées
manuellement.

  

## Logique de recherche de correspondance :

Clé de champ uniforme (ffInfo::key) :

- fabricant de l'appareil photo,
- modèle de l'appareil photo,
- objectif
- longueur focale,
- ouverture

La recherche pour la meilleure correspondance se fait en 2 temps :

- si une correspondance parfaite par la clé est trouvée, alors la liste
  est scannée pour identifier le plus récent fichier
- sinon, le fichier le plus proche en objectif et ouverture est
  recherché dans la liste.

## Types de floutage

Zone  
Un choix par défaut et généralement le plus utilisé pour appliquer un
flou de façon égale dans toutes les directions. Fonctionne bien pour
corriger le vignettage et les dominantes colorées de l'objectif

Vertical  
Rend flou le champ uniforme selon la direction verticale pour compenser
les non uniformités verticales. Utile si la lecture verticale du capteur
présente des variations entre les colonnes.

Horizontal  
Rend flou le champ uniforme selon la direction horizontale pour
compenser les non uniformités horizontales. Utile si la lecture
horizontale du capteur présente des variations entre les lignes.

Vertical + Horizontal  
Rend flou le champ uniforme dans la direction horizontale puis verticale
de façon séquentielle pour compenser à la fois les non uniformités
verticales et horizontales.

Noter que le concept d'horizontalité et de verticalité est relatif à la
façon dont le capteur est orienté dans le fichier raw, qui reste
toujours le même indépendamment de l'orientation de l’appareil photo au
moment de la prise de vue. Il varie suivant les modèles d'appareils qui
peuvent enregistrer les données du capteur en mode paysage ou portrait.
Donc, pour appliquer les modes Horizontal ou Vertical vous devez tester
quelle direction convient à votre modèle.

## Rayon de floutage

Le curseur "Rayon de floutage" contrôle l'intensité du flou sur les
données du Champ uniforme. La valeur par défaut de 32 est habituellement
suffisante pour se débarrasser des variations locales des données raw
causées par le bruit. Un Rayon de floutage de 0 supprime tout effet de
flou et autorise la correction des grains de poussière et autres débris
sur le capteur (pour autant que leur position n'ait pas changé) au prix
d'une transposition du bruit du Champ uniforme vers l'image corrigée. Si
une telle correction est souhaitée, il est conseillé de créer un fichier
Champ uniforme avec un bruit minimal en choisissant une valeur ISO la
plus basse possible et un exposition à la lumière optimale.

## Contrôle de l'écrêtage

Appliquer une image champ uniforme peut provoquer le passage de zones
proches de la sur-exposition en zones sur-exposées en raison de la
correction. Activer l'option *Contrôle de l'écrêtage* empêchera l'image
champ uniforme de sur-exposer la photo traitée. Les zones de cette photo
qui étaient déjà sur-exposées avant l'application du champ uniforme
risquent d'acquérir une dominante de couleur, suivre donc cette règle :
si votre photo comporte des zones sur-exposées, il est préférable de ne
pas utiliser l'option *Contrôle de l'écrêtage*.

Pour bien comprendre le fonctionnement de l'option *Contrôle de
l'écrêtage*, nous devons faire un peu de technique. L'outil Champ
Uniforme fonctionne en ajustant l'exposition des zones de l'image à
traiter dont les zones correspondantes de l'image champ uniforme
diffèrent de l'exposition mesurée au centre de l'image champ uniforme.
Le facteur par lequel l'exposition d'une zone de l'image à traiter est
multipliée est proportionnel au facteur existant entre l'exposition de
la zone correspondante de l'image champ uniforme et celle de son centre.
Quand l'option *Contrôle de l'écrêtage* est désactivée ou à 0, les
pixels de l'image à traiter peuvent voir leur exposition augmenter
au-delà du niveau blanc raw. *Contrôle de l'écrêtage* fonctionne en
modifiant le facteur de correction d'exposition en fonction du niveau du
blanc, de façon à ce qu'aucun pixel ajusté ne dépasse la valeur du
niveau du blanc.

Par exemple, si l'augmentation nécessaire de l'exposition d'un pixel de
l'image à traiter est de 1.25, a compter du niveau du blanc raw (=1),
alors le facteur de limitation serait de 1 / 1.25 = 0.8. Ce facteur sera
alors utilisé dans le calcul final pour empêcher toute valeur de
dépasser le niveau du blanc.

La formule pour le curseur est :
`clipControlGui = (1 - limitFactor) * 100`

Donc, avec un facteur de limitation de 0,8, la valeur du curseur est de
20.
