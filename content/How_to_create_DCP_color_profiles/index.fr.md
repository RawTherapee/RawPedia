---
title: How to create DCP color profiles
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<div class="pagetitle">

Comment créer des profils de couleur DCP

</div>

## Que sont les profils DCP et pourquoi en ai-je besoin ?

Techniquement, chaque photosite du [capteur
d'image](http://fr.wikipedia.org/wiki/Capteur_photographique) d'un
appareil photo numérique délivre une certain courant en fonction du
nombre de [photons](http://fr.wikipedia.org/wiki/Photon) de lumière qui
ont atteint le photosite. Le courant est converti en un nombre. Ces
nombres, complétés par quelques
[metadonnées](http://fr.wikipedia.org/wiki/M%C3%A9tadonn%C3%A9e), sont
enregistrés dans ce qui est connu sous le nom de "[fichier
raw](http://fr.wikipedia.org/wiki/RAW_%28format_d%27image%29)". A ce
niveau il n'existe aucun concept de couleur et les données raw ne
ressemblent en rien à une image. Comme en photographie traditionnelle,
l'image doit être "développée" vers une forme exploitable. L'une des
étapes de ce développement implique la conversion des nombres en
couleurs, et pour cela il faut profiler l'appareil photo, pour
transformer les nombres en couleurs spécifiques connues.

Pratiquement, vous devez utiliser un profil de couleur d'entrée dans le
but d'obtenir des couleurs fidèles, et actuellement le meilleur moyen de
le faire est d'utiliser un profil "DNG camera profile" (Profil DNG
d'appareil photo, en court DCP - à ne pas confondre avec [Digital Cinema
Package (Paquetage de Cinema
Numérique)](http://en.wikipedia.org/wiki/Digital_Cinema_Package) qui n'a
strictement rien à voir). Le profil de couleur d'entrée est ce qui donne
aux couleurs de l'appareil photo l'aspect qu'elles ont quand ont ouvre
une photo, avant toute retouche.

RawTherapee est fourni avec les types de profils suivant :

- ICC - Ce sont des profils matriciels, conçus pour la lumière du jour
  uniquement, pas très bons pour l'éclairage incandescent. C'est
  l'ancien type de profil.
- DCP - Ce sont les nouveaux types de profils.
  - DCP simple-illuminant - Conçus pour la lumière du jour uniquement.
  - DCP dual-illuminant - Conçus à la fois pour la lumière du jour et la
    lumière incandescente, ils conviennent donc très bien à la plupart
    des situations.

Par ailleurs, vous pouvez créer votre propre profil DCP sur mesure pour
obtenir une grande précision de couleur dans des situations d'éclairage
spécifiques. Supposons que vous photographiez un mariage, ou des
panoramas pour une visite virtuelle, il vous faut des couleurs précises
et constantes. Le [spectre de
couleur](http://en.wikipedia.org/wiki/Color_spectrum) de la lumière
extérieure d'un bâtiment est complètement différente de celle de
l'intérieur, et même à l'intérieur la lumière est différente dans chaque
pièce car les différents types de lampes d'usage général produisent des
lumières de température et de spectre différents, et il y a souvent
plusieurs lampes, de différents types pour éclairer une même pièce. Si
vous disposez d'un nuancier d'étalonnage des couleurs (aussi appelé
charte des couleurs), tel que le X-Rite ColorChecker Passport, tout ce
que vous avez à faire est de prendre une photo de ce nuancier dans les
mêmes lieux que les photos normales, une photo par situation d'éclairage
(qui généralement se traduit par une photo par pièce et une dehors),
puis générez les profils DCP depuis ces photos et utilisez les dans
RawTherapee pour obtenir des couleurs correctes et fidèles et la
[balance des blancs](http://en.wikipedia.org/wiki/White_balance) entre
toutes vos prises de vues.

## Cibles couleur

La meilleure cible pour la plupart des situations de prises de vues est
une cible non brillante, avec de bonnes valeurs de référence, portable
et solide. Pour ces raisons nous recommandons le X-Rite ColorChecker
Passport Photo.

Ne soyez pas trompé en pensant que plus une cible comporte de pièces,
meilleure elle est, ce n'est pas vrai, et avoir plus de pièces rend plus
difficile la production et le réglage de DCP de grande qualité.

Cibles couleur supportées :

- Matte :
  - X-Rite ColorChecker Passport
  - X-Rite ColorChecker 24, connu aussi sous le nom de X-Rite
    ColorChecker Classic
  - Datacolor SpyderCHECKR
  - X-Rite ColorChecker SG
  - QP-Card 203
  - QP-Card 202
- Glossy (difficiles à utiliser, donc non recommandées) :
  - IT 8.7 Reflective DIN A4 (Wolf Faust Coloraid C1)
  - CMP Digital Target 8
  - HutchColor HCT (Fuji RVP)

Pour plus d'informations, se reporter au chapitre "Choix d'une cible
test" de la documentation DCamProf :
httphttps://rawtherapee.com/mirror/dcamprof/dcamprof.html#test_target

## Plus d'informations

Savoir plus :

- Manuel de DCamProf
  <https://rawtherapee.com/mirror/dcamprof/dcamprof.html>
- Page du X-Rite ColorChecker Passport :
  <http://xritephoto.com/ph_product_overview.aspx?id=1257>
- Manuel PDF du X-Rite ColorChecker Passport :
  <https://www.xrite.com/-/media/xrite/files/manuals_and_userguides/c/o/colorcheckerpassport_user_manual_en.pdf>
- Article de QPcard sur les profils de couleur ICC et DCP :
  <http://www.qpcard.com/dcp_icc_profile>

## Photographie de la cible couleur

![](PENTAX_K10D_daylight_london_summer.jpg "PENTAX_K10D_daylight_london_summer.jpg")
![](Colortarget_glare.png "Colortarget_glare.png")
![](Gluehlampe_01_KMJ.png "Gluehlampe_01_KMJ.png")

Ce guide suppose que vous utilisez la cible couleur ColorChecker
Passport de X-Rite, vous pouvez cependant utiliser n'importe quelle
cible couleur supportée. Si vous utilisez la cible couleur ColorChecker
Passport de X-Rite, bien qu'il soit suffisant de photographier la partie
limitée à 24 couleurs, nous préférons utiliser la cible en entier.

La lumière éclairant la cible couleur (l'"illuminant") doit satisfaire
certaines exigences ("[illuminants
standards](https://fr.wikipedia.org/wiki/Illuminant)"), et vous devrez
photographier sous deux types de lumières :

- Lumière émise par une ampoule à incandescence au tungstène, non
  teintée, connue sous le nom de Illuminant Standard A, ou **StdA** pour
  faire plus court.
- Lumière du jour, connue sous le nom de Illuminant Standard D, et vous
  devrez vous efforcer d'atteindre une lumière comprise entre D50 (c'est
  la lumière de « l'horizon ») et D65 (lumière à midi).

Photographier une cible couleur peut répondre à deux scénarios possibles
:

1.  Doter RawTherapee d'un profil double illuminant (StdA et D50/D65)
    DCP précis d'utilisation générale, pour être utilisé par tout le
    monde avec votre modèle d'appareil photo,
2.  Pourvoir à des situations d'éclairage spécifiques non-D65 seulement
    pour vous-même.

Dans le premier cas, vous prendrez grand soin à ce que le profil réponde
aux exigences car beaucoup de personnes l'utiliseront. Dans le deuxième
cas, vous n'utiliserez probablement ce profil que pour cette occasion
spécifique, et il ne sera d'aucune utilité pour d'autres personnes.

Photographie de la cible couleur pour intégration dans Rawtherpee :  

- Nous avons besoin de photos prises dans deux conditions d'éclairage :
  lumière du jour et incandescence.
- Idéalement, attendre une journée claire, ensoleillée quand le soleil
  est haut au-dessus de l'horizon, près du zénith à midi. Vous pouvez
  aussi photographier la cible un jour légèrement nuageux autour de
  midi, mais pas un jour de tempête, en hiver, ou même en été tôt le
  matin ou tard le soir. ceci afin d'éviter les couleurs parasites qui
  apparaissent dans le spectre lorsque le soleil est proche de l'horizon
  ou derrière d'épais nuages ou du brouillard.
- En ce qui concerne la prise de vue en lumière du jour, trouver un
  endroit loin de tout ce qui pourrait réfléchir la lumière. Votre
  balcon n'est pas un bon endroit, les murs renvoient la lumière et
  influencent négativement le spectre de lumière, même si cela ne se
  voit pas à l’œil nu. Un parc n'est pas un bon endroit. Se placer sous
  un toit transparent ou une ombrelle n'est pas un bon endroit. Un grand
  parking, vide loin des murs, des arbres et des voitures garées
  convient très bien. Toute chose autre qu'un ensoleillement clair et
  direct est mauvais. Oubliez le flash, rien ne remplace la lumière
  solaire vraie.
- En ce qui concerne la prise de vue en lumière incandescente, vous
  devez utiliser une ampoule à incandescence au tungstène, claire, du
  genre de celles qui étaient utilisées partout jusqu'à ce que le monde
  passe aux ampoules fluorescentes compactes ces dix dernières années.
  Ne pas utiliser d'éclairage fluorescent, même s'il est de teinte
  chaude, son spectre de lumière est totalement différent de celui du
  tungstène. Ne pas utiliser non plus de lumière halogène ni d'ampoules
  teintées.
- Positionner la cible couleur et vous-même par rapport à la source de
  lumière (le soleil ou l'ampoule) de telle façon qu'il n'y ait pas de
  réverbération de lumière par la cible directement vers l'appareil
  photo risquant de provoquer un éblouissement, mais aussi que la
  lumière ne provienne pas sous un angle extrême. Lors de l'utilisation
  de l'ampoule, pour éviter un éclairage inégal, ne pas placer la cible
  à moins d'un mètre de cette dernière, deux mètres est une bonne
  distance.
- Assurez que la surface de la cible est uniformément éclairée et que la
  lumière réfléchissant du sol, des murs et des objets à proximité ne
  tombe pas dessus.
- Tandis que le soleil est très éloigné et que lors des prises de vue
  D65 vous pourriez vous permettre d'incliner la cible de couleur non
  perpendiculaire au soleil, une ampoule sera toujours près de vous et
  en raison de la loi des carrés inverses la lumière, une cible inclinée
  pourrait être éclairée d'intensité irrégulière. La pointer vers la
  source de lumière pour garantir un éclairage régulier mais de telle
  façon à éviter l'éblouissement.
- Assurez vous que l'arrière plan n'est pas réfléchissant pour éviter
  tous reflets éblouissants. Le goudron noir d'une route ou un vêtement
  noir conviennent, pas le papier blanc.
- Assurez vous que les photos sont nettes. Le logiciel de génération du
  DCP a besoin de reconnaître la poussière et les rayures pour les
  isoler, donc ne prenez pas de vues hors focus ou avec du flou de
  bougé. Utilisez un pied pour les prises en lumière incandescente.
- Positionner la cible couleur de façon à ce qu'elle remplisse le tiers
  central du cadre, pas plus, pas moins. Le centre du cadre possède la
  meilleure optique et le moindre vignetage.
- Enlever tous les filtres de l'objectif.
- Régler l'ouverture entre f5/6 et f/8. Cela minimise le vignetage.
- Prendre les photos à la valeur ISO la plus basse de votre appareil,
  typiquement 100 ISO. Pour la prise StdA, ne pas monter au_delà de 800
  ISO, utiliser un pied. Avec 100 ISO et f/8, les temps typiques
  d'exposition sont d'environ 1/500 s pour de la lumière du jour et
  d'environ 1 à 5 s pour StdA.
- Photographier en raw (plein raw, pas de "s-Raw" ou toute autre
  variante).
- Arrêter tous les paramétrages de l'appareil photo qui pourraient
  influencer le fichier raw, tels que la réduction du bruit dans les
  longues expositions.
- Le bracketing est acceptable et même recommandé, il vous/nous aidera à
  trouver la prise de vue avec la meilleure exposition, sans écrêtage,
  par ex : -1EV/0EV/+1EV. N'hésitez pas à envoyer les 3 images
  bracketées (ou les 6, 3 pour lumière du jour et 3 pour StdA).
- Renommez et/ou décrivez vos photos, nous ne savons pas ce que signifie
  "_DSC1234.DNG". Renommez les en " FABRICANT MODELE lumière.extension"
  par exemple "NIKON D810 daylight+2EV.nef". Si vous téléversez plus
  d'une photo, décrivez en quoi elles diffèrent. Faites nous savoir dans
  quel endroit du monde vous avez réalisé ces prises, par exemple
  "Bikini Atoll, Marshall Islands". Indiquez nous quand fut
  commercialisée votre cible, ou à défaut l'année de son achat. Voici
  une suggestion pour renommer automatiquement des photos avec
  [ExifTool](https://exiftool.org/) :
    
  `exiftool '-FileName<${make}_${model}_iso${iso}_f${aperture}_%c.%le' dir`
- Relisez chacun de ces points et assurez vous que vos photos s'y
  conforment avant de téléverser.
- Ouvrez un nouveau cas sur [RawTherapee la page
  GitHub](https://github.com/Beep6581/RawTherapee/issues/new),
  téléversez vos photos raw D65 et StdA en utilisant
  [Filebin](https://filebin.net/) et collez un lien vers elles dans
  votre nouveau cas GitHub. Seules les photos raw nous intéressent, pas
  les DCP tous faits, nous les ferons nous-mêmes. Si vos photos sont
  bracketées, vous pouvez téléverser les séries, nous choisirons les
  meilleures.

Photographie de la cible de couleur dans des situations d'éclairage spécifiques, pour vous-même :  

- Comme ci-dessus, la cible de couleur doit remplir environ un tiers du
  cadrage, f/8, 100 ISO, nette, bien que l'aspect de l'éclairage ne
  s'applique pas ici. Si vous êtes dans une manifestation au cours de
  laquelle beaucoup de photos seront prises avec les mêmes conditions
  d'éclairage, par exemple des portraits d'affaires, immobilier, une
  série d'images pour un panorama à 360° dans la forêt ou un mariage,
  prendre une photo de la cible de couleur juste avant (ou après) les
  photos elles-mêmes.

## Créer le DCP

Il y a plusieurs façons de créer un DCP. La plus simple est d'utiliser
le logiciel livré avec la cible test. L'alternative Open source de la
plus haute qualité est d'utiliser DCamProf.

### Création de DCP en utilisant le logiciel X-Rite

Tout simplement installer le logiciel X-Rite ColorChecker Passport
fourni avec votre charte (il fonctionne aussi sous Linux avec
[wine](http://www.winehq.org/), suivre les étapes indiquées pour
l'installation d'Adobe DNG Converter dans l'article [Comment convertir
les formats raw en
DNG](How_to_convert_raw_formats_to_DNG/fr#Linux.md)) et ouvrez y
votre photo. Cela suppose que la photo est au format DNG, vous devez
donc auparavant la [convertir en
DNG](How_to_convert_raw_formats_to_DNG/fr#Linux.md).
L'utilisation est simple et évidente, c'est intuitif.

### Création de DCP en utilisant DCamProf

DCamProf, écrit par Anders Torger, est un outil libre et open source en
ligne de commande pour générer des profils d'appareil photo et réaliser
des tâches en rapport aux profils d'appareils photo et au profilage.
Notamment, il peut générer des profils aussi bien dans les formats ICC
et DNG, et il est capable de générer des profils LUT réguliers et de
haute qualité à partir de prises de vues CC24 ou autres cibles.

Le programme contient une documentation claire et complète. Utilisez là
comme source première d'information. Cet article de Rawpedia ne sert
qu'à expliciter la façon de l'utiliser pour créer un profil DCP pour un
double illuminant.

- GitHub hébergeant le projet et la documentation de DCamProf :
    
  <https://github.com/Beep6581/dcamprof>
- Page d'accueil de DCamProf : (actuellement hors ligne) :
    
  <https://www.ludd.ltu.se/~torger/dcamprof.html>

Vous aurez besoin d'installer [ArgyllCMS](http://www.argyllcms.com/),
car vous utililserez certains de ses outils. Dans le code donné en
exemple ci-dessous, les outils ArgyllCMS sont préfixés avec `argyll-`.
Cela est requis par certaines distributions telles que Gentoo et Sabayon
où l'exécutable "scanin" est appelé `argyll-scanin`, mais pas par les
autres telles que Ubuntu où il est appelé simplement `scanin`. Adapter
le code en conséquence.

<figure>
<img src="/images/Daylight_crop.jpg" title="Daylight_crop.jpg" />
<figcaption>Daylight_crop.jpg</figcaption>
</figure>

Pour générer un DCP double illuminant à partir de deux prises de vue du
ColorChecker Passport :

1.  Prendre deux photos de la cible couleur comme expliqué plus haut
    dans le chapitre [Photographie de la charte de
    couleur](How_to_create_DCP_color_profiles/fr#Photographie_de_la_charte_de_couleur.md).
2.  Pour chacune des deux photos, faire ce qui suit :
    1.  Ouvrir le photo dans la dernière version de RawTherapee,
    2.  Appliquer le profil neutre,
    3.  Regardez la cible 24 couleurs (si votre cible comprend une
        seconde cible, ignorez là) la faire pivoter de façon à ce que le
        pavé marron soit dans l'angle supérieur gauche et le noir dans
        l'angle en bas à droite,
    4.  Activer l'outil recadrage, décocher "Ratio fixe", et recadrer au
        niveau des repères dans les angles,
    5.  Dans l'outil Gestion de la couleur (ICM) cliquer sur le bouton
        "Sauver Image de Référence", et dans la fenêtre qui apparait
        s'assurer que "Appliquer la balance des blancs" n'est pas coché.
        Enregistrer l'un sous le nom `daylight.tif` et l'autre sous le
        nom `tungsten.tif` dans le même dossier qui contient
        l’exécutable `dcamprof` compilé.
3.  Ouvrir le dossier contenant l'exécutable `dcamprof` compilé et
    exécuter :

<!-- -->

    argyll-scanin -v -dipn tungsten.tif /usr/share/argyllcms/ref/ColorChecker.cht data-examples/cc24_ref.cie tungsten-diag.tif
    argyll-scanin -v -dipn daylight.tif /usr/share/argyllcms/ref/ColorChecker.cht data-examples/cc24_ref.cie daylight-diag.tif
    ./dcamprof make-profile -i StdA tungsten.ti3 tungsten.json
    ./dcamprof make-profile -i D50 -C daylight.ti3 daylight.json
    ./dcamprof make-dcp -n "Pentax K10D" -n "Pentax K10D" -t acr -o neutral tungsten.json daylight.json "PENTAX K10D.dcp"

Il est très important qu'à l'étape `make-dcp` vous spécifiiez d'abord
`tungsten.json` et `daylight.json` ensuite !

Dans cet exemple,le fichier de sortie s’appelle `PENTAX K10D.dcp`. Vous
devez reprendre exactement le même nom que RawTherapee a désigné. Ouvrir
simplement la photo StdA ou D50/D65 dans RawTherapee et basculer dans le
panneau "Information rapide" (raccourci clavier "i") pour voir sous quel
nom RawTherapee identifie votre appareil photo.

Votre DCP double illuminant est prêt.

Pour que RawTherapee utilise automatiquement votre nouveau DCP, placer
le fichier DCP dans le répertoire `dcpprofiles`. Typiquement, ce
répertoire se trouve à l'intérieur du répertoire d'installation de
RawTherapee dans Windows, ou dans `/usr/share/rawtherapee/dcpprofiles/`
avec Linux et macOS. En parallèle, créez un nouveau PP3 par défaut pour
les fichiers raw qui utilise ce nouveau DCP, voir [Création de profils
de traitement d'usage
général](Creating_processing_profiles_for_general_use/fr.md).

Par défaut DCamProf adoucira la LUT pour prioriser la douceur par
rapport à la précision, ceci donne un profil plus robuste pour une
utilisation générale. Si vous le désirez, il est possible de contrôler
manuellement tous les paramètres d'adoucissement mais généralement ce
n'est pas nécessaire. Voir la documentation de DCamProf pour plus
d'informations.
