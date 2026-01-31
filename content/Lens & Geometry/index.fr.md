---
title: Lens Geometry
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Transform Tab'
---

<div class="pagetitle">

Objectif / Géométrie

</div>

Pour conserver un affichage rapide de l'aperçu lors de l'application de
ces transformations, RawTherapee utilise l'image d'aperçu au niveau de
zoom en cours. A cause de cela, l'image d'aperçu peut perdre son piqué.
Supposons que vous modifiiez une image Nikon D700 4256×2832px (soit 12,1
mégapixels), et que la taille de l'image d'aperçu soit de 600x400px.
Pivoter cette dernière de 5° ne sera pas la même chose que de pivoter
l'image complète de 12,1 Mpx puis de la réduire à 600x400px. La première
solution sera moins piquée que la deuxième, bien que son pivotement
prenne moins de temps que pour la deuxième solution, ce qui est la
raison pour laquelle RawTherapee procède ainsi. Mais ne pas s'inquiéter,
lors de la sauvegarde de l'image, RawTherapee utilise la pleine
résolution, elle sera donc bien piquée. Si vous zoomez l'aperçu, alors
RawTherapee utilisera l'aperçu en haute définition lors du calcul de la
transformation, ainsi pour voir ce à quoi l'image sauvegardée
ressemblera, simplement la zoomer à 100%
![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png").

## Pare-soleil

Ne pas confondre le vignetage avec l'ombre du pare-soleil floutant les
coins de l'image. Certains appareils photo, typiquement les plus petits,
les compactes, les bridges et même ceux dépourvus de miroir, captent en
partie le pare-soleil ou bien le mécanisme de l'objectif dans les angles
de la photo. En général, ces mêmes appareils possèdent des objectifs qui
souffrent d'une importante distorsion. La façon dont ces appareils
traitent ces deux problèmes consiste à corriger la distorsion, en
conséquence de quoi les coins de l'image sont repoussés en dehors du
cadre, cachant de ce fait les coins assombris par le pare-soleil. Si
vous observez une image JPEG produite par ces appareils, la distorsion a
déjà été corrigée intérieurement par l'appareil, ainsi les utilisateurs
en sont-ils généralement inconscients et sont surpris de constater les
angles assombris des images raw.

Il n'est pas possible de corriger le problème des coins assombris avec
l'outil correction du vignetage, il n'existe aucune information sur ce
qui se passe dans ces angles, la scène est occultée par le mécanisme de
l'objectif ou le pare-soleil. Agissez comme l'appareil, corrigez la
distorsion et les angles assombris vont disparaître.

## Remplir

<img src="/images/Lensgeometry_bluehorse_barrel_distortion_correction.jpg"
title="Lensgeometry_bluehorse_barrel_distortion_correction.jpg"
width="900"
alt="Lensgeometry_bluehorse_barrel_distortion_correction.jpg" /> <img
src="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg"
title="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg"
width="900"
alt="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg" />
Cette option agrandit ou diminue la photo afin que l'image entière
tienne à l'intérieur des limites de la photo sans bordures noires
visibles.

Lors de la correction d'images subissant une [déformation en
barillet](https://fr.wikipedia.org/wiki/Distorsion_%28optique%29),
"Remplir" va réaliser une modification d'échelle afin de faire tenir le
maximum possible de l'image modifiée dans les limites de l'image, ainsi
vous ne subissez pas de pertes inutiles. Si l'image subit une
déformation en coussin, "Remplir" va réaliser une augmentation d'échelle
de l'image corrigée afin qu'elle remplisse le cadre sans bordures noires
en périphérie.

  

## Recadrage auto

<img
src="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg"
title="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg"
width="900"
alt="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg" />
<img src="/images/Lensgeometry_bluehorse_autocrop_after_rotation.jpg"
title="Lensgeometry_bluehorse_autocrop_after_rotation.jpg" width="900"
alt="Lensgeometry_bluehorse_autocrop_after_rotation.jpg" />
"[image:Crop-auto.png](image:crop-auto.png) Recadrage auto"
est disponible quand "Remplir" est désactivé. Si activé, il ne provoque
pas d'interpolation de l'image, mais à la place il rogne l'espace libre
délaissé par la correction de la distorsion ou la rotation de l'image.

  

## Rotation

[900px](image:rotate.jpg) Tourne l'image de - 45 à + 45
degrés. Cliquez sur le bouton
"![<File:Rotate-straighten.png>](Rotate-straighten.png "File:Rotate-straighten.png")
Choisir la ligne d'horizon" pour établir un alignement de l'image soit
sur une horizontale soit sur une verticale. Utiliser la souris pour
tracer cette ligne, cliquer et tenir enfoncé pour tracer ce qui sera la
nouvelle direction horizontale ou verticale, et relâcher pour démarrer
la rotation de l'image.

  

## Perspective

<img src="/images/perspective_horizontal.jpg" title="perspective_horizontal.jpg"
width="900" alt="perspective_horizontal.jpg" />
<img src="/images/perspective_vertical.jpg" title="perspective_vertical.jpg"
width="900" alt="perspective_vertical.jpg" />

Horizontale  
Si vous avez pris votre photo alors que vous étiez légèrement décentré
par rapport à l'objet, il est possible de corriger cela (dans une
certaine limite) avec le curseur *Horizontale*.

Verticale  
Très utile pour corriger la perspective des verticales, par exemple dans
les photos d'architecture. Les valeurs les plus élevées des deux
curseurs provoquent une importante distorsion, a utiliser avec
précaution. Ou bien oubliez toute précaution et amusez vous !

  

## Correction des objectifs par profils

A partir de RawTherapee 5.3, la distorsion des objectifs, le vignetage
et l'aberration chromatique peuvent être corrigés à l'aide d'un ou deux
systèmes : Lensfun ou Adobe LCP. Les deux s'appuient sur un profil qui
contient les paramètres destinés à la correction de la distorsion des
objectifs, du vignetage et de l'aberration chromatique.

### Lensfun

Lensfun est un projet open-source. Une base de données de paramètres
d'objectifs est maintenue par les développeurs. Davantage d'informations
sont disponibles dans la [FAQ de
Lensfun](https://lensfun.github.io/faq/).

Les options " Auto-matched correction parameters" (Paramètres de
correction auto-adaptés) et "Manual correction parameters" (Paramètres
de correction manuels) utilisent toutes les deux le système Lensfun. Les
deux listes déroulantes "Appareil photo" et "Objectifs" contiennent de
longues listes d'appareils photo et d'objectifs (dans le cas contraire,
votre installation de RawTherapee est défectueuse, veuillez [le
rapporter](How_to_write_useful_bug_reports/fr.md)). Un profil
correspondant à vos appareil photo et objectif est automatiquement
détecté si vos photos contiennent des métadonnées qui correspondent à
une entrée de la base de données de Lensfun.

Les causes habituelles d'échec de la détection du profile comprennent :

- Il n'existe pas dans votre version de la base de donnée de Lensfun de
  profil correspondant à votre ensemble boitier/objectif
- Un tel profil existe bien mais il utilise des désignations et
  paramètres suffisamment différents pour perturber l'algorithme
  établissant la correspondance, par exemple "Pentax" versus "Ricoh
  Pentax", ou bien "F4.0" versus "f/4".

Dans les deux cas, vous pouvez essayer de trouver et lancer le fichier
exécutable
[`lensfun-update-data`](https://lensfun.github.io/manual/v0.3.2/lensfun-update-data.html)
(données de mise à jour de lensfun) pour télécharger la dernière version
de la base de données Lensfun. Si cela ne convient pas, vous pouvez
copier/coller la partie concernée de la base de données Lensfun (qui
peut être trouvée parmi un des fichiers de `/usr/share/lensfun/`) dans
un nouveau fichier `$HOME/.local/share/lensfun/myLensfun` et modifier le
paramètre concerné pour correspondre aux métadonnées de vos photos. Les
noms et paramètres des appareil photo et objectif contenus dans les
métadonnées des photos peuvent se trouver en explorant dans RawTherapee
le panneau d'information rapide Exif, [raccourcis
clavier](Keyboard_Shortcuts/fr.md) "i" dans l'onglet Editeur. Si
les paramètres de vos appareil photo et objectif n'existent simplement
pas, lisez la [documentation
Lensfun](https://lensfun.github.io/calibration/) pour découvrir comment
les mesurer et les fournir dans l'intérêt de tous.

Notez que bien qu'il soit possible d'éditer directement la base de
données de Lensfun dans `/usr/share/lensfun/`, cela n'est pas recomandé
car vous pourriez perdre vos modifications lors d'une mise à jour.

Au cas où vous désireriez utiliser la base de données de Lensfun d'un
endroit particulier, vous pouvez l'indiquer à RawTherapee en éditant le
fichier [`options`](file_paths/fr#config) pour modifier la
valeur de la clé `DBDirectory` et entrer le chemin absolu vers la base
de données de Lensfun choisie.

### LCP

Adobe fournit et offre des outils pour créer et partager ce qu'on
appelle des Profils de correction d'objectif (LCP). Ce sont des fichiers
texte qui décrivent la distorsion, le vignettage et les aberrations
chromatiques d'un objectif, ainsi un simple chargement de ce fichier
dans un logiciel compatible LCP tel que RawTherapee, corrigera ces
défauts. Sélectionner un fichier [Adobe
LCP](http://www.adobe.com/products/photoshop/extend.displayTab2.html#resources)
(lire le guide sur [Comment obtenir des profils
LCP](How_to_get_LCP_and_DCP_profiles/fr.md)) pour corriger
automatiquement la distorsion géométrique, le vignettage et les
aberrations chromatiques latérales.

La fonctionnalité de correction de la distorsion de l'outil Profil de
correction d'objectif peut s'utiliser en même temps que l'outil
correction manuelle de la
[Distorsion](lens/geometry/fr#distorsion), et la
fonctionnalité correction du vignettage peut s'utiliser en même temps
que l'outil manuel [correction du
vignettage](Lens/Geometry/fr#Correction_vignettage.md) Cela vous
laisse la possibilité d'utiliser les contrôles manuels en plus du profil
LCP pour des raisons artistiques ou si LCP ne réussit pas à corriger
suffisamment un paramètre. (Ce qui arrive quelque fois en cas de
distorsion extrême, par exemple avec des appareils photo compacts
fortement déformants). Soyez donc prudent de ne pas sur-corriger la
distorsion ou le vignettage en oubliant de désactiver les outils manuels
si vous utilisez les équivalents LCP.

La fonctionnalité correction du vignettage est cependant liée à l'outil
[Champ plat](flat_field/fr), donc lorsque vous sélectionnez
une image champ plat, il n'y aura alors pas de correction du vignettage
par LCP.

Les restrictions suivantes s'appliquent :

- Les corrections de la distorsion, du vignettage et de l'aberration
  chromatique sont toutes supportées dans les fichiers raw, mais seule
  la correction de la distorsion est supportée dans les fichiers
  non-raw.
- Bien que la distorsion soit visible dans l'aperçu image complète,
  l'aberration chromatique et la distorsion ne sont pas apparents dans
  la vue détaillée, seulement dans l'image de sortie après la fin du
  traitement. L'outil Remplir n'est pas supporté non plus.
- La correction de l'aberration chromatique n'est supportée que si la
  distance focale est incluse dans les informations Exif (par exemple
  dans les DNG des fichiers Nikon).
- La fonction Remplir est désactivée lorsqu'un LCP avec correction de la
  distorsion est activé, sinon l'aperçu principal peut présenter des
  distorsions, [bug
  1791](https://github.com/Beep6581/RawTherapee/issues/1791).
- Pour conserver un aperçu rapide et réactif, l'image d'aperçu
  principale est utilisée pour afficher les effets du LCP. Comme cette
  image est petite (exactement de la taille que vous voyez), la
  réparation des distorsions peut la faire apparaître légèrement floue.
  Cela n'a aucun effet sur l'image sauvegardée, dont le piqué sera
  correct, de même que pour un aperçu zoomé à 100%, c'est seulement un
  aperçu en zoom arrière qui semblera flou. Voir [feature request
  2186](https://code.google.com/p/rawtherapee/issues/detail?id=2186).

Comme pour n'importe quel autre outil, vous pouvez appliquer LCP à de
multiples images soit en l'incluant dans le profil de traitement (voir
[Création de profils de traitement à usage
général](Creating_processing_profiles_for_general_use/fr.md)),
soit en sélectionnant de multiples images réalisées avec le même
objectif (facilité par l'utilisation des filtres sur les Métadonnées
dans l'onglet Filtrer du Navigateur de Fichiers) et en appliquant le LCP
depuis l'onglet Navigateur de Fichiers.

  

## Distorsion

[framed](image:rt_distortion_correction-fr.png) Corrige les
distorsions dues à l'objectif. Un nombre négatif corrige la distorsion
en barillet, un positif corrige la distorsion en coussin. Vous pouvez
placer une grille sur l'image en activant le
[recadrage](crop/fr) (sans recadrer) puis en choisissant
"*Type de guide \> Grille*". Cela peut servir de guide pour corriger la
distorsion de l'objectif.

Le bouton "**Automatique**" ne fonctionne que si votre appareil photo a
corrigé la distorsion de l'image JPEG intégrée au fichier raw (la
plupart des appareils intègrent une image JPEG dans chaque fichier raw,
et certains corrigent aussi la distorsion de ces dernières). Cet outil
considère l'image JPEG et, s'il elle est corrigée, essaie de corriger la
distorsion de l'image raw en la faisant correspondre à l'image JPEG. Il
y a deux limitations :

- Si l'image JPEG n'a pas été corrigée en distorsion par l'appareil
  photo, ce bouton n'aura aucun effet.
- Si l'image JPEG a été insuffisamment corrigée ou sur-corrigée en
  distorsion par l'appareil photo, il en sera de même de l'image raw,
  mais comme la correction par l'ordinateur est disponible avec le
  curseur *Quantité*, vous pouvez ajuster manuellement.

  

## Aberration chromatique

<img src="/images/chromatic_aberration_auto1.jpg"
title="chromatic_aberration_auto1.jpg" width="900"
alt="chromatic_aberration_auto1.jpg" />
<img src="/images/chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" width="900"
alt="chromatic_aberration_auto2.jpg" />

Ce présent outil "Aberration chromatique" de l'onglet *Transformation*
traite l'image **après** le dématriçage. L'outil [Aberration
Chromatique](Chromatic_Aberration/fr.md) de l'onglet *Raw*
traite l'image **avant** le dématriçage.

L'aberration chromatique peut être corrigée grâce aux deux curseurs
"Rouge" et "Bleu". Normalement, vous ne verrez aucune aberration
chromatique dans l'aperçu réglé sur "Ajuster à l'écran", en conséquence,
il est hautement recommandé d'utiliser la fenêtre de vue détaillée
![<File:Window-add.png>](Window-add.png "File:Window-add.png") ou de
zoomer à 100% ou plus l'aperçu principal
![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png")
pour appliquer cette correction. Comme dans d'autres outils logiciels,
cet algorithme élimine avec satisfaction les aberrations chromatiques
modérées. N'attendez pas de miracles avec les images souffrant d'une
aberration chromatique très importante. Entrées défectueuses, sorties
défectueuses.

  

## Correction du vignettage

Le vignettage consiste en une baisse de la luminosité en périphérie de
la photo par rapport au centre. Une des différences entre un
téléobjectif bon marché et un cher est que le premier a toute les
chances de souffrir d'un vignettage plus important que le plus cher.
L'outil "Correction vignettage" est conçu pour corriger le vignettage du
à l'objectif. Cet outil n'est pas adapté au vignettage artistique, pour
cela utiliser l'outil [Filtre Dégradé](vignetting_filter/fr).

Quantité  
Glisser le curseur Quantité vers une valeur positive éclaircit les
quatre angles de l'image pour corriger le vignettage classique. Vers une
valeur négative, cela les assombrit.

Rayon  
Détermine la part de l'image en partant des bords qui sera éclaircie ou
assombrie. Vers les basses valeurs, la zone d'assombrissement est plus
grande, et vers les hautes valeurs, la zone est plus petite.

Force  
Amplifie les réglages des curseurs "Quantité" et "Rayon". Mettez la
"Quantité" à -100, le "Rayon" à 50 et déplacez le curseur "Force" de 1 à
100, observez l'effet.
