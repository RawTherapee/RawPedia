---
title: CIECAM02
contributors:
  - Jdc
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Advanced Tab'
---

<div class="pagetitle">

Modèle d'apparence des couleurs Cam02/Cam16 & Jzazbz

</div>

Par J.Desmis

## Tutoriel Color Appearance & Lighting (CIECAM02/16) et Color Appearance (Cam16 & JzCzHz)

### Introduction

Ce système d'information est commun à :

- Color Appearance & Lighting (CIECAM02/16) – "Advanced Tab"
- Color Appearance (Cam16 & JzCzHz) - "Local Tab"

En effet, ces deux modules utilisent tout ou partie d'un CAM - modèle
d’apparence de couleur. Lorsque une rubrique concernera spécifiquement
un des deux modules, cela sera explicitement mentionné. Ciecam02 possède
de nombreux atouts, néanmoins il n'excelle pas dans le traitement des
images à haute dynamique (HDR), notamment dans les hautes lumières où
son « gamut » est étroit. Il vient d'être nettement amélioré par
Ciecam16.

Le module Color Appearance (Cam16 & JzCzHz) regroupe un véritable CAM
(Cam16) et JzCzHz qui n'en est pas un au sens propre du terme, mais qui
en a des caractéristiques.

[HDR-SDR Première approche : Log encoding – Cam16 – JzCzHz –
Sigmoid](Local_Adjustments/fr#HDR-SDR_Première_approche_:_Log_encoding_–_Cam16_–_JzCzHz_–_Sigmoid.md)

### Définition d'un modèle d’apparence de couleur - CAM

Un modèle d'apparence de couleur (CAM) est un modèle mathématique qui
cherche à décrire les aspects perceptuels de la vision des couleurs chez
l'homme, c'est-à-dire les conditions de visualisation dans lesquelles
l'apparence d'une couleur ne correspond pas à la mesure physique
correspondante de la source de stimulus (RGB, XYZ ne sont pas des CAM,
Lab est un CAM avec très peu de possibilités).

### Ciecam02

Ce module est basé sur le modèle d'apparence des couleurs CIECAM02, qui
a été conçu pour mieux simuler la façon dont la vision humaine perçoit
les couleurs dans différentes conditions d'éclairage, par exemple, en
tenant compte de la variété des arrière-plans. Il prend en compte
l'environnement de chaque couleur et modifie son apparence pour se
rapprocher le plus possible de la perception humaine. Il adapte
également la sortie aux conditions de visualisation prévues (moniteur,
TV, projecteur, imprimante, etc.) afin que l'apparence chromatique et
les contrastes soient préservés dans toute la scène et les
environnements d'affichage.

### Quelques exemples de situations où un CAM est souhaitable

- une même couleur sera perçue différemment sur un fond clair ou sombre,
  plus le fond sera sombre plus il va être nécessaire de renforcer la
  couleur.
- Un objet apparaît plus vif et contrasté en pleine lumière qu’à
  l’ombre.
- Quand la luminance augmente, les couleurs sombres apparaissent encore
  plus sombres et les couleurs lumineuses apparaissent encore plus
  lumineuses.
- Les objets de couleur apparaissent plus clairs que les objets
  achromatiques ayant la même luminance. \* Les couleurs les plus
  saturées apparaissent les plus brillantes.
- L'adaptation chromatique est la capacité du système visuel humain à
  s'ajuster aux changements de conditions d'éclairage (illuminant).
  Autrement dit, nous nous adaptons à la couleur de la source lumineuse
  pour mieux préserver la couleur des objets. Par exemple, sous une
  lumière incandescente, un livre blanc apparaît jaune. Cependant, nous
  avons la capacité automatiquement de modéliser la lumière jaunâtre et
  nous voyons donc le papier comme blanc. Le monde qui nous entoure
  serait en effet très compliqué si les objets changeaient de couleur
  chaque fois que la source de lumière change même légèrement. Depuis la
  nuit des temps, nous devons être capable de savoir si un fruit est mûr
  que ce soit le matin, le midi, ou le soir. L'adaptation chromatique
  nous rend cela possible.

### Variables - données et vocabulaire utilisées par CIECAM

[Variables - données](ciecam02/fr#donn.c3.a9es)

[Définitions](ciecam02/fr#quelques_d.c3.a9finitions)

### Ciecam02 est articulé autour de 3 processus

1.  « Source » ou « Conditions de scène » : correspond aux conditions de
    prise de vue et à la manière de ramener les conditions et les
    données, vers une zone « normale ». Il faut entendre par
    « normale », des conditions et des données moyennes ou standard,
    c'est à dire sans prise en compte des corrections CIECAM, par
    exemple balance des blancs D50 
2.  « Traitement des données issues de « Source »
3.  « Conditions d'observation» : correspond aux conditions dans
    lesquelles sera visionnée l'image finale (moniteur, TV, projecteur,
    imprimante...), ainsi que leur environnement. Ce processus va
    prendre les données venant du processus 2 et les « amener » au
    support de telle manière que les conditions de visualisation et de
    l'environnement de visualisation soient prises en compte.

### Différences d'utilisation des concepts CAM selon 2 modules (Advanced Tab, Local Tab)

« Color Appearance & Lighting (CIECAM02/16) –  Advanced Tab » : ce
module contient l'ensemble des concepts et outils Ciecam02/16, il est
spécifique à Rawtherapee et a été développé dès 2012. Il dispose d'un
sélecteur de complexité :

- 'Standard' : donne à l'utilisateur les outils et variables nécessaires
  pour découvrir les concepts et pour une utilisation courante ;
- 'Advanced' : donne l'ensemble des outils et variables corrélées pour
  une utilisation avancée.

« Color Appearance(Cam16 & JzCzHz) – Local Tab » : Ce module contient
des outils simplifiés Cam16 et une première approche de JzCzHz Il
dispose d'un sélecteur de complexité :

- 'Basic' – donne des outils et variables de base utilisés par Cam16
- 'Standard' – ajoute les outils 'Cam16' pour compléter la prise en
  compte des aspects perceptuels de la vision des couleurs chez l'homme,
  ainsi qu'un Masque
- 'Advanced' – ajoute les outils et variables Cam16 supplémentaires
  ainsi que le module JzCzHz.

### Quelques exemples d'utilisation de Ciecam02/16

Cinq exemples vont permettre de percevoir la puissance de cet outil,
mais aussi certaines des limites.

#### Exemple 1  (Advanced Tab)

Utiliser presque uniquement le processus 1 “Source” pour traiter une
image à forte dynamique sous-exposée…On se sert de Ciecam comme d’un
“Source lighting”

##### Préparation

L'image choisie est difficile : ombres très marquées et arrière plan
éclairé en plein soleil. Utilisez les traitements par défaut de
Rawtherapee. Positionnez des "Lockable color picker" afin de visualiser
le traitement Fichier raw
[1](https://drive.google.com/file/d/1ctjOWX2lVmgcAzJtBwt69FGpxZOq-LyP/view?usp=sharing)

<figure>
<img src="/images/ciecam_light_prepa.jpg" title="ciecam_light_prepa.jpg"
width="600" />
<figcaption>ciecam_light_prepa.jpg</figcaption>
</figure>

##### Eclaircir l'image

Allez dans "Advanced Tab" - sélectionnez "Color Appearance & Lighting
(CIECAM02)" Dans "Scene conditions", avec la ComboBox "Surround - Scene
Lighting", choisissez "Dark" C'est tout !
<img src="/images/ciecam_ligh.jpg" title="ciecam_ligh.jpg" width="600"
alt="ciecam_ligh.jpg" />

Vous pouvez utiliser les réglages "Image adjustments"

- Essayez Lightness (J) et Contrast (J)
- Essayez Chroma (C)

Passez en mode Complexity : advanced (Settings - Preset)

- Choisissez Algorithm : Lightness + Saturation (JS)
- Essayez Saturation (S), comparez avec Chroma (C), regardez les ombres,
  les tons moyens, les hautes lumières..

#### Exemple 2 - adaptation chromatique

a\) « Advanced tab » Utiliser Ciecam en démarche symétrique pour
réaliser une adaptation chromatique, à partir d’une balance des blancs
quasi parfaite.

##### Ciecam Advanced Tab - préparation

Fichier raw
[2](https://drive.google.com/file/d/1CiQ2t4KyD3tdCiNNhskqUG2cH9LT2ly7/view?usp=sharing)

La première étape : réaliser une balance des blancs - presque
mathématiquement parfaite - en utilisant "White Balance" - "Auto" -
"Temperature correlation"
<img src="/images/catATwb.jpg" title="catATwb.jpg" width="600"
alt="catATwb.jpg" />

Examinez le résultat:

- Température : 7450K
- Tint : 1.050

Si vous choisissez "Camera" vous aurez Température : 7862K, Tint : 1.134

Dans les 2 cas regardez l'image...elle est jaunâtre...Pourquoi ? La
raison est l'heure et la latitude de la prise de vue: 8 heures du matin,
en septembre à Londres... Ce n'est pas la balance des blancs qui n'est
pas bonne, mais nos yeux qui eux, font l'adaptation chromatique, que ne
fait pas l'algorithme mathématique.

Pour y remédier nous allons nous servir de Ciecam02

##### Réaliser automatiquement une adaptation chromatique

- Ouvrez "Color Appearance & Lighting (CIECAM02)
- cochez la case "Preset cat02 automatic"....C'est tout!

<figure>
<img src="/images/catATauto.jpg" title="catATauto.jpg" width="600" />
<figcaption>catATauto.jpg</figcaption>
</figure>

Examinez l'image, le ciel est bleu...la peau des personnages est
naturelle.

- Vous pouvez si vous le souhaitez, moduler cette action. Allez dans
  "Viewing conditions", changez "CAT02 adaptation", par exemple en le
  ramenant à 60....
- notez la température - c'est celle de la balance des blancs, vous
  pouvez agir sur cette température (en général la baisser)

#### Exemple 3 - conditions d'observation

Montrer l’incidence du périphérique de sortie et de son environnement.
Exemple d’une photo de voyage, que l’utilisateur souhaite projeter sur
la TV Oled familiale, en fin d’après midi devant un groupe d'amis.
Fichier raw :
[3](https://drive.google.com/file/d/1GdqejdnbW1kJFNY6y9sdQDlF2rCEGMCu/view?usp=sharing)

Nous prendrons des caractéristiques habituelles (voir la documentation
du téléviseur Oled)

- Illuminant = D65
- Mean Luminance (Yb%) = 18 - Nous admettons que la luminance moyenne du
  téléviseur est bien réglée..

Environnement de visualisation :

- Absolute luminance : en fin d'après-midi on peut estimer cette valeur
  à 10 cd/m2...(l'idéal serait d'avoir un appareil pour la mesurer)
- Surround = Dim : l'arrière plan du téléviseur - peinture des murs est
  relativement sombre

<figure>
<img src="/images/voyagejpg.jpg" title="voyagejpg.jpg" width="600" />
<figcaption>voyagejpg.jpg</figcaption>
</figure>

Remarque importante : La visualisation sur votre PC sera obligatoirement
"mauvaise", car elle ne correspond pas aux conditions de visualisation
(illuminant, surround, absolute luminance)

##### Montrer aux invités : il faisait beau, les couleurs sont magnifiques

Evidemment, chacun trouve que ses vacances sont un rêve, et on souhaite
le faire partager aux invités. On triche un peu, en ajoutant un peu de
contraste, et un peu de chroma.
<img src="/images/voyage_plus.jpg" title="voyage_plus.jpg" width="600"
alt="voyage_plus.jpg" />

## Local Adjustments - Color Appearance (Cam16 & JzCzHz)

Voir aussi [HDR-SDR Première approche : Log encoding – Cam16 – JzCzHz –
Sigmoid](Local_Adjustments/fr#HDR-SDR_Premi.C3.A8re_approche_:_Log_encoding_.E2.80.93_Cam16_.E2.80.93_JzCzHz_.E2.80.93_Sigmoid.md)

### Color Appearance - Cam16

Un nouvel outil est disponible (octobre 2021) pour Local Adjustments.
Cet outil reprend:

- la majorité des algorithmes du module principal Ciecam.
- une fonction "Sigmoid J & Q" qui permet en un seul algorithme de
  traiter la luminance (lightness ou brightness) et le contraste.
- une fonction HDR PQ expérimentale qui applique aux matrices de
  conversions XYZ\<=\>Cam16 les fonctions "gamma HDR" - Inverse PQ et
  PQ.
- le mode "symmetric" n'est pas automatique et les processus
  d'adaptation chromatique sont simplifiés.
- il est situé en amont du processus par rapport au module Ciecam
  principal, ce qui devrait réduire les artefacts.
- une combobox "CAM Model" permet de sélectionner soit "CAM16", soit
  "JzCzHz"
- une combobox "Change tool position" permet de choisir soit :
  - le fonctionnement du module "autonome" (default)
  - l'incorporation des algorithmes dans 4 autres outils au choix :
    Tone-mapping, Wavelet, Dynamic Range, Log encoding

## Jzazbz - Un nouveau CAM ? (Cam16 & JzCzHz)

Voir l'utilisation possible dans Local Ajustements : [Module
expérimental](Local_Lab_controls/fr#Le_module_expérimental_JzCzHz.md)

### Généralités

Jzazbz est un espace couleur conçu pour sa « perception uniforme » dans
les applications à dynamique élevée (HDR) et à large gamme de couleurs
(gamut - WCG). Il est similaire à CIE L\*a\*b\*, mais avance des
améliorations théoriques :

- La différence de couleur perçue est prédite par la distance
  euclidienne (deltaE).
- Perception uniforme : Les ellipses de MacAdam sont plus circulaires,
  plus proches de tailles similaires.
- Linéarité de la teinte : une modification de la saturation ou de la
  luminosité entraîne un moindre décalage de la teinte.

Mais, Jzazbz n'est pas un vrai CAM, il n'a pas par exemple un traitement
pour le contraste simultané, pas plus qu'une adaptation chromatique. A
noter que dans RT ces problèmes sont partiellement résolus par la
correction Munsell (Uniform Perceptual Lab) pour les images SDR.

Les diverses études comparatives réalisées (laboratoires, thèses...)
montrent que : CAM16 obtient les meilleures notes pour les images SDR,
Jzazbz se situe juste derrière ; Jzazbz obtient les meilleures notes
pour les images HDR, CAM16 se situe nettement derrière.

Les auteurs de "Jzazbz" travaillent cependant sur "ZCAM", qui est
destiné à être l'équivalent "Jz" de "CAM16". Plusieurs essais de
transposer "ZCAM" dans Rawtherapee ont été réalisés en septembre et
octobre 2021 - le code est toujours présent, mais totalement neutralisé
car les résultats étaient décevants, sa présence est sans incidences sur
les performances, la mémoire utilisée et les temps de traitement. Une
reconstruction sera relativement aisée si cela s'avère nécessaire.

Par contre, nous avons profité de cette expérience, du code de ZCAM
(celui des chercheurs), ainsi que de celui de Cam16, pour donner à
"Jzazbz" quelques caractéristiques supplémentaires d'un CAM (en plus de
"La" - "Absolute luminance"):

- prise en compte de "Yb% - Mean luminance" de la scène;
- "Surround" de la scène avec 3 réglages - Average, Dim, Dark;
- possibilité d'utiliser la "luminance relative" au lieu de la
  "luminance absolue" avec comme conséquences les choix :
  - utiliser "Lightness" et "Contrast Lightness", plutôt que
    "Brightness" et "Contrast Brightness"
  - "Saturation" en addition à "Chroma"

### Problématique

Jzazbz utilise la luminance absolue (La), et non la luminance relative.
Une luminance relative se rapporte à la luminance maximale qu'un
dispositif d'entrée (tel qu'un scanner ou une caméra) peut enregistrer,
ou à la luminance maximale qu'un dispositif de sortie (tel qu'un écran)
peut afficher. Ainsi, une luminance relative de 100 % est le maximum
qu'une caméra peut enregistrer ou qu'un écran peut afficher. Jzazbz est
conçu pour utiliser les luminances absolues. Par exemple, 100% dans le
canal Jz correspond à une luminance de 10000 cd/m2, candelas par mètre
carré. Ce qui on va le voir pose de nombreux problèmes.

Ces problèmes, au niveau de RT et a priori d'autres tentatives de
développement sont difficiles à aborder et traiter par manque de
documentation (voire de réponses aux questions par l'auteur du concept).
Ces problèmes sont de plusieurs types :

- Soient ils sont un défaut de conception non encore abordé ou résolu ?
- Soient ils sont résolus et non documentés ?
- Soient ils sont dus à une mauvaise compréhension et
  interprétation(notamment de ma part) ?

#### Quels sont ces problèmes

- Lorsqu'on examine les valeurs des données avec les réglages de base de
  l'algorithme de conversion original, celles-ci sont très loin des
  limites théoriques (0.08 pour « Jz » - ou moins - au lieu de 1, même
  constat pour « az » et « bz » très loin des valeurs limites théoriques
  de +- 0.5). Ceci a pour conséquence immédiate qu'une simple action sur
  le canal « Jz » se traduit par un défaut flagrant de saturation. Ces
  valeurs sont dues à la mise en œuvre des fonctions Inverse PQ et PQ
  nécessaire dans Jz pour traiter les données HDR.
- Toujours avec l'algorithme original, lorsqu'on agit sur « Jz »
  (brightness) en le réduisant fortement on voit apparaître de forts
  artefacts dans les ombres.
- Il n'y a aucun contrôle de gamut...
- Le problème majeur vient (au moins au niveau de RT) des profils ICC
  vers l’écran (et peut être aussi vers TIF/Jpeg) qui peuvent être
  limités par le PCS (Profile Connection Space). Celui-ci est soit de
  type « Lab PCS 8 bits» et limite la transmission à des valeurs de
  luminance comprises entre 0.1 et 120 cd/m2 ou soit de type XYZ qui ne
  limite pas (profils fournis de type RT2xxx ou RT4_xxx), alors qu'un
  système HDR devrait pouvoir passer des luminances comprises entre
  0.0001 cd/m2 et 10000 cd/m2.
  - De plus la TRC (Tone Response Curve) est de type sRGB – une partie
    linéaire et une partie parabolique. Cette TRC ne peut être remplacée
    par un concept plus performant en HDR, le Perceptual Quantizer (PQ –
    origine Dolby), qui est un gamma capable de varier en fonction du
    pic de luminance maximum supporté par les écrans HDR (en théorie
    jusque 10000 cd/m2 pour les blancs, même si cette valeur n'est
    atteinte par aucun moniteur - les valeurs « habituelles », - écrans
    Oled étant plus proches de 700 à 1000 cd/m2 et 0.0001 cd/m2 pour les
    noirs).
  - Ceci suppose au niveau normalisation de pouvoir utiliser Jzazbz
    comme PCS (ou à défaut XYZ), d'utiliser PQ comme TRC, et dans la
    pratique que LCMS en tienne compte ainsi que accroître la précision
    des calculs des profils écran!
- Je ne pense pas que la transformation RGB-\>Lab soit directement en
  cause pour effectuer un traitement complet HDR. En effet les calculs
  sont faits généralement en 'float' ou 'double' (32 ou 64 bits) ou en
  SSE (128 bits - 4\*32 ou 2\*64 bits). La partie linéaire de la
  transformée Lab permet d'atteindre dans les ombres 0.005 cd/m2 ou
  moins. La partie parabolique (gamma = 3.0) limite la répartition des
  données dans les hautes lumières qui en permettrait une meilleure
  représentation (sur les moniteurs le supportant) et probablement pour
  des valeurs de luminance supérieures à 120 cd/m2 . Néanmoins la
  conversion XYZ\<=\>Lab n'amène aucune pertes de données (sinon
  insignifiantes par les doubles conversions) et peut être considérée
  comme une sorte de compression sans pertes. Bien sûr si on veut
  réaliser un traitement complet HDR, il faut que l'ensemble des données
  traitées en amont du moniteur puisse être plus progressives dans les
  hautes lumières. La piste à privilégier pour Rawtherapee serait la
  mise en place de HDR-Lab à la place de Lab. Mais en attendant j'ai
  pour plusieurs outils (wavelet, TM, etc.) implanté la possibilité de
  changer le gamma de Lab (3.0) notamment pour le rendre linéaire. De
  plus Rawtherapee permet de palier à un des problèmes de Lab qui est la
  non préservation de la teinte lorsque la saturation change (notamment
  dans les oranges et les pourpres - Perceptual Uniform Lab). Cette
  préservation est réalisée par une série de LUT "Munsell", de même un
  contrôle de gamut permet de prévenir les couleurs virtuelles.
- Bien sûr, je ne dispose par de moniteur HDR (avec des pics de
  luminance pouvant atteindre 6000 cd/m2 ou plus), pas plus que de
  profils ICC adaptés, ni d'une version modifiée de LCMS... Donc mes
  propositions ne sont que des hypothèses fondées sur mon expérience de
  la gestion des couleurs et de la mise au point (difficile) de Ciecam02
  et Ciecam16....et utiliser un système SDR (comme je pense 99% des
  utilisateurs).

### Quelles solutions je propose, pour quels objectifs ?

Je me suis fixé comme objectifs ;

- utiliser Jzazbz en SDR sans artefacts et avec une bonne colorimétrie.
  Potentiellement Jzazbz doit pouvoir remplacer (théoriquement en mieux
  L\*a\*b\* ?)  et mettre en œuvre a minima un panel d'outils
  utilisables en mode Jzazbz;
- ouvrir la possibilité de mettre en œuvre HDR !

Quelles solutions ai-je retenues ?

- Prendre en compte « La » (Luminance absolue) de la source ;
- Calculer les valeurs maximum de « Jz » de l'image \[0..1\], souvent
  aux environ de 0.2 ;
- Prendre en compte une valeur estimée de Jz pour 100cd/m2 (courbe
  habituelle des résultats luminance réelle, luminance perçue) - aux
  environ de 0.25 ;
- En fonction de ces 3 valeurs ("La", "maximum", "Jz100") et aussi celle
  de PQ, la valeur de Jz est réévaluée (remapping) en fonction de "La"
  et se situera généralement entre 0.5 et 1 ("maximum" si La est
  supérieur ou égal à 10000 cd/m2). Les courbes et sliders subissent une
  modification de leur plage d'utilisation afin que ces systèmes soient
  dans leurs limites habituelles d'utilisation.
- Modifier le valeur de PQ qui est uniformément à 10000 cd/m2 dans les
  calculs, pour l'adapter à la valeur maximum du pic de luminance du
  moniteur - 100 à 120 cd/m2 pour les moniteurs SDR ou n'importe quelle
  valeur entre 120 et 10000 cd/m2 pour les moniteurs HDR. Cette prise en
  compte évite les artefacts dans les basses lumières lorsqu'on souhaite
  réduire Brightness.

Interface graphique correspondante (GUI) - incorporé au module Local
adjustments Color Appearance (Cam16 & JzCzHz)

- 3 curseurs, situés dans la fenêtre « Jz remapping » permettent de
  mettre en ouvre la solution que j'ai retenue. Attention, il faut
  décocher la case « Auto » dans « Scene conditions » si vous voulez
  faire varier "La" (Absolute luminance)
- "PU - adaptation" - Perceptual Uniform » : prend en compte
  automatiquement « Absolute Luminance ».
- « Jz reference 100 cd/m2 » : réglé par défaut à 0.25.
- « PQ -Peak luminance » : à régler en fonction des caractéristiques du
  moniteur de sortie. En SDR 100 ou 120 cd/m2...En HDR la valeur
  requise.
- Si « PQ -Peak luminance »  à 10000, l'algorithme se comportera comme
  l'algorithme de conversion original avec un maximum de Jz nettement
  inférieur à 1 (souvent 0.02).

Vous pouvez voir dans la console (si verbose = true dans "options") les
valeurs recalculées de "remapping", "Max_real" à comparer à la valeur
"maxi" de Jz original, ainsi que la valeur du coefficient "To_one"
appliqué aux curseurs et courbes de telle manère qu'ils se comportent
normalement.

### Comprendre les réglages CAM - SDR - HDR - Généralités

La mise au point de cet outil (expérimental) a été semé d'embûches,
liées :

- au peu de documentation à propos du concept "JzCzHz" qui se résume
  pour l'essentiel à la description des matrices de conversion
  XYZ-Jzazbz.
- à la pratique courante en photographie d'utiliser les concepts et
  outils SDR, hérités des technologies des années 1990 et 2000, où la
  visualisation était assurée par des moniteurs cathodiques aux
  performances limitées.
- de plus contrairement à la video, le support photographique habituel
  est le papier (par l'utilisation d'une imprimante). Celle-ci a des
  caractéristiques (gamut, dynamic range, pic de luminance) encore plus
  faible (généralement) que le moniteur cathodique. En ce sens si
  l'usage essentiel du photographe est le support papier, à quoi bon
  aller vers le HDR ? De plus, une bonne partie des échanges "photos" se
  font via le Web, donc en sRGB...? En résumé pourquoi dans une majorité
  de cas aller vers HDR ?
- les outils HDR disponibles en photographie sont rares, voire
  inexistants. Par exemple :
  - la sortie moniteur dans Rawtherapee est programmée en L\*a\*b\* 8
    bits (qui limite la DR - Dynamic Range à environ 7 ou 8 Ev, et qui
    limite le pic de luminance à 100 ou 120 cd/m2).
  - la gestion des profils moniteur est assurée par LCMS qui n'a pas à
    ce jour (à ma connaissance) un accès HDR.
- l'utilisation pratique pour le commun des mortels se heurte aux prix
  des moniteurs :
  - 3000 à 5000€ pour disposer d'un moniteur aux performances HDR
    limitées (pic de luminance aux environs de 300 cd/m2).
  - 30000 à 60000€ pour disposer d'un moniteur capable de passer des DR
    de l'ordre de 21 Ev, un pic de luminance supérieur à 3000 cd/m2, et
    un gamut proche de Rec2020.
  - les téléviseurs récents OLED présentent des caractéristiques HDR
    intéressantes (gamut supérieur à sRGB - proche de DCI-P3, contrastes
    infinis, pic de luminance proche de 500 à 800cd/m2, définition :
    3840x2160), néanmoins je n'ai pas trouvé de pilotes, pas plus que de
    profils ICC adaptés. Leur utilisation semble possible en HDR partiel
    et WCG (Wide Color Gamut - proche de DCI-P3) , notamment lors de
    l'utilisation des appareils photos récents dotés d'une forte
    dynamique (14 ou 15 Ev) pouvant être branché directement au
    téléviseurs via un câble HDMI et la norme 2160p. Dans ce cas, c'est
    le JPG (ou le Raw) qui est utilisé avec un profil ICC doté d'une PCS
    (Profil Connexion Space) en XYZ...donc non limitée à 8 bits. Peut
    être ce téléviseur pourrait servir de moniteur si la carte graphique
    du PC supporte HDR ( 3840x2160, gamut, PQ...) et bien sûr si ce PC
    est doté des profils ICC ad-hoc.
- les concepts (CAM, "Absolute and relative luminance", "Dynamic Range",
  PQ et iPQ à la place de la TRC,...) sont souvent abscons, peu
  documentés, et leur utilisation en programmation laissée à
  l'initiative du programmeur (ses compétences, sa compréhension des
  concepts, etc.).

En conséquence l'usage et la programmation HDR semblent aujourd'hui
académiques et plus proches d'une démarche intellectuelle prospective
que d'une utilisation journalière et étendue à une forte population.
Ceci ne m'a pas empêché d'élaborer ce module, qui débroussaille nombre
de concepts et d'essayer de faire partager mes expériences.

#### Comprendre les réglages CAM - SDR - HDR - Introduction

Jzazbz utilise la luminance absolue (La), et non la luminance relative
(comme L\*a\*b\* par exemple). Une luminance relative se rapporte à la
luminance maximale qu'un dispositif d'entrée (tel qu'un scanner ou une
caméra) peut enregistrer, ou à la luminance maximale qu'un dispositif de
sortie (tel qu'un écran) peut afficher. Ainsi, une luminance relative de
100 % est le maximum qu'une caméra peut enregistrer ou qu'un écran peut
afficher. Jzazbz est conçu pour utiliser les luminances absolues. Par
exemple, 100% dans le canal Jz correspond à une luminance de 10000
cd/m2, candelas par mètre carré, métrique utilisée par PQ (origine
Dolby). Ce qui on va le voir pose de nombreux problèmes. Il en est de
même pour la différence entre Q et J dans Ciecam02/16, sinon que Q n'est
pas référencée à une luminance de 10000cd/m2. Il est indispensable
d'avoir 'compris' cette différence entre luminance absolue et relative.
<https://en.wikipedia.org/wiki/Perceptual_quantizer>

Les deux matrices de conversion – directe :XYZ-Jzazbz – et inverse :
Jzazbz-XYZ sont complexes  notamment car :

- elles donnent (contrairement à Cam16) une place à part au bleu.
- elles introduisent, à la place des fonctions gamma et i-gamma qui sont
  habituellement utilisées dans les équipements SDR (non utilisées dans
  les matrices de conversion Cam16), et souvent dans Rawtherapee sous le
  forme de gamma-sRGB (TRC) , la notion de inverse PQ (iPQ) et PQ,
  nécessaires aux équipements HDR. Ces fonctions PQ, sont incorporées
  aux matrices directe (iPQ) et inverse (PQ) et tiennent compte du pic
  de luminance (en lien direct avec la luminance absolue « La »).

Le lecteur intéressé pourra consulter dans le document en lien :

- le schéma de principe du flux de travail de la capture de la lumière à
  l'affichage d'une image, figure 1.3 page 29,
- les formules 1.2 et 1.32 pages 38 et 39 pour la part donnée au bleu,
- les formules 1.5 page 30 pour le gamma (ici BT709) et 1.21 page 38
  pour la fonction iPQ.

<https://tel.archives-ouvertes.fr/tel-02378332/document>

Cette fonction PQ, ressemble à i-gamma et gamma qui prendrait en compte
le pic de luminance. Ceci va se traduire au moment de l'utilisation des
données "Jz", par un affaiblissement très important des valeurs de Jz
(globalement selon la valeur de PQ - Jz se situe entre 0 et 0.02, avec
une valeur moyenne de l'ordre de 0.003 alors que l'intervalle maximum de
Jz est de \[0..1\]). Bien sûr cette conversion est "tout sauf linéaire"
et rend l'utilisation des valeurs de Jz très délicate, voire impossible,
pour les courbes, sliders, fonctions diverses (wavelet, shadows
highlight...). Si j'avais laissé "tout comme cela", c'est à dire ne rien
changer aux deux matrices, le rendu global manquerait manifestement de
saturation, les outils 'habituels' seraient inutilisables, certaines
actions sur les curseurs conduiraient à de très forts artefacts.

A propos de "Dynamic-range" et "Absolute luminance". Ce sont des
informations complémentaires:

- DR ("Dynamic range") traduit la différence (en Ev) entre les valeurs
  maximales et minimales de la luminance (White Ev - Black Ev). Des
  valeurs courantes 'passées' par les APN modernes sont de l'ordre de 13
  à 15 Ev, ou plus si on utilise des fichiers DNG combinant plusieurs
  fichiers Raw.
- "Absolute luminance", "La", traduit la luminance de la scène au moment
  de la prise de vue. Cette valeur est estimée en fonction des données
  EXIF (et peut être fausse notamment lors de l'utilisation de fichiers
  DNG), à partir de la vitesse, du diaphragme, et des ISO. Elle est
  exprimée en candelas par m2. Des valeurs de l'ordre de 2000 à 7000
  cd/m2 (ou plus) sont courantes en été au soleil, ou en hiver dans les
  scènes de neige.
- Ces valeurs sont à rapprocher de celles passées par le moniteur SDR (7
  à 8 Ev, et 120 cd/m2)
- L'exercice va donc consister (pour une part) à faire rentrer ces
  hautes valeurs de "DR" et "La" dans celles du moniteur SDR. **Cet
  exercice ne peut se faire qu'avec des compromis**

A noter que tout ce qui suit est mon interprétation, très contestable,
mais qui a le mérite de fonctionner...

### Mise en oeuvre

- "Jzazbz" (sous la forme "JzCzHz") est incorporé au nouveau module de
  Local adjustments "Color appearance (Cam16 & JzCzHz)
- il n'est disponible - vue sa complexité apparente - qu'en mode avancé
- il utilise le mode "double" (au lieu de "float") pour accroitre la
  précision des calculs - ceci a une incidence sur les temps de
  traitement.

Plusieurs type d'outils sont disponibles afin de pouvoir juger la
pertinence de "Jzazbz" pour remplacer L\*a\*b\*

#### Outils divers

- Outils traditionnels : Brightness (ou Lightness), Contrast Brightness
  (ou Lightness), Chroma, Saturation, Hue rotation ainsi que 6 courbes
  Jz(Jz), Cz(Cz), Cz(Jz), Hz(hz), Cz(hz), Jz(hz).
  - A noter que pour les 3 courbes Hz(hz), Cz(hz), Jz(hz) la conception
    des matrices de conversion XYZ\<=\>Jzazbz amène une réponse plus
    faible (voire nulle) dans les bleus, notamment lorsque la saturation
    est faible.
- Shadows/highlight (similaire à celui présent dans L\*a\*b\*).
- Wavelets :
  - Local contrast.
  - Clarity & Sharp mask.
- Recovery based on luminance mask.
- Mask and modifications.
- Il est tout à fait possible d'ajouter d'autres outils de type
  L\*a\*b\*

#### Deux outils Tone-mapping : Log encoding Jz et Sigmoid Jz

##### Log encoding Jz

Permet - comme son homologue en mode RGB incorporé au module Local
Adjustments [Log encoding](ciecam02/fr#log_encoding) - de
modifier l'équilibre des valeurs "Jz", réduisant de fait les contrastes,
en rehaussant les ombres et réduisant les hautes lumières, sans trop
dénaturer le rendu de l'image. Au lieu de se servir de la luminance RGB
on utilise "Jz" (Brightness) qui sépare parfaitement ce canal des 2
autres canaux Chroma "Cz" et Hue "Hz". La pondération "Log" est
appliquée au canal "Jz". Le résultat est un peu différent de celui du
modèle RGB, plus respectueux de la colorimétrie.

- Quatre réglages principaux permettent d'ajuster les résultats:
  - "Mean Luminance (Yb %)" - incorporé à "Scene Conditions" : réduire
    la valeur du curseur va accroître l'amplification globale de
    l'image. Cette action est située avant les conversions Log.
  - "Black Ev" et "White Ev", vous autorisent à retoucher les valeurs
    calculées de la "Dynamic Range", permettant ainsi une modification
    différenciée sur les ombres et les lumières.
  - "Viewing Mean luminance (Yb%)", agit conjointement à "Black Ev" et
    "White Ev" pour calculer la conversion "Log" finale. Accroître cette
    valeur va éclaircir l'image.

##### Sigmoid Jz

Cet outil, permet en un seul concept, un traitement global des notions
de contraste et luminance, assez proche dans l'esprit de « Log encoding
Jz » ou d'autres concepts "Tone-mapping", car il assure une compression
dynamique de la brightness « Jz ».

- Qu'est-ce qu'une « sigmoid » ?: la définition de Wikipidedia permet
  d'en avoir un aperçu.
- <https://en.wikipedia.org/wiki/Sigmoid_function>.
- La version utilisée dans Rawtherapee est un peu plus complexe et
  utilise 2 paramètres, supplémentaires. Pour information la formule
  mathématique devient : « Sigmoid RT » : Résultat = 1. / (1. +
  exp(lambda - (lambda / threshold) \* Jz))
  - « lambda » agit sur la pente de la courbe, se traduisant par plus ou
    moins de contraste ;
  - « threshold » déplace la courbe vers les ombres ou les lumières,
    permettant ainsi de répartir plus finement l'action selon l'image.
    On peut même dire que « Threshold » ajuste le « point gris ».
  - Simulation : je joins une démonstration d'une Sigmoid avec 2
    paramètres où "L" correspond au "contraste" et "t" correspond à
    "threshold". A noter que le calcul réalisé dans le code est un peu
    différent. Cette simulation est uniquement à caractère pédagogique.
    - <https://www.desmos.com/calculator/g382ci99gu?lang=fr>
- Cette fonction ressemble au premier abord à une «Tone-curve», mais ici
  pas de pied (toe), pas d'épaule (shoulder), pas de partie linéaire,
  mais une variation exponentielle continue, présentant notamment dans
  le cadre des images HDR des particularités intéressantes:
  - pour les valeurs proches de 0 et de 1, la courbe progresse très
    lentement et est proche d'une loi linéaire, permettant ainsi son
    utilisation dans les ombres profondes avec pour Jz (traduites en
    « luminance absolue ») des valeurs faibles de l'ordre de 0.001 cd/m2
    ou élevées avec des valeurs de plusieurs centaines de cd/m2.
  - pour les valeurs intermédiaires , la partie exponentielle assure une
    compression dynamique des données comme le ferait un outil de type
    « Tone mapping ».
- Une option vous permet de prendre en compte les valeurs (calculées
  également pour « Log encoding Jz ») de « Black Ev » et « White Ev ».
  Dans ce cas dans la formule « Sigmoid RT » ci-dessus, « Jz » est
  remplacée par son équivalent exprimé en Ev : Jz_equivalent_Ev =
  (log2(Jz) – Black Ev) / Dynamique Range. Dans ce dernier cas, l'outil
  se comporte de manière un peu similaire à « Log encoding Jz ». La
  différence importante est dans la résolution de l'équation :
  - dans le cas de « Log encoding » les valeurs de « Black Ev », « White
    Ev » et « Viewing mean luminance » servent à calculer la conversion
    « log ».
  - dans le cas de « Sigmoid », les valeurs de « Black Ev », « White
    Ev » et du « Threshold (point gris) » sont modifiées par la courbe
    exponentielle "Sigmoid" qui amène l'utilisateur à résoudre
    visuellement l'équation. Le curseur contraste apporte une
    possibilité supplémentaire de contrôle de la répartition de la
    luminance par rapport à "Log encoding".
  - Un curseur supplémentaire « blend » permet (un peu à la manière de
    « Viewing mean luminance » (pour Log encoding), d'ajuster le
    résultat final.

##### Ajustement de la saturation

Les deux outils préservent la teinte (hue), c'est le fondement de "Jz".
Néanmoins l'action de ces 2 outils peut être importante sur le contraste
avec les conséquences sur l'accroissement ou la baisse de la luminance
résultante "Jz", et peut amener à retoucher la saturation. Dans ce cas
les outils suivants permettent cette retouche en préservant la teinte:

- curseurs chroma et saturation.
- courbes Cz(Cz) et Cz(Jz).

### Documentation

<https://tel.archives-ouvertes.fr/tel-02378332/document>

<https://www.color.org/groups/hdr/HDRWG-Summer2020.pdf>

<https://www.osapublishing.org/oe/fulltext.cfm?uri=oe-29-4-6036&id=447640>

## A propos de CIECAM02

### Introduction - historique

Depuis de nombreuses années l'homme essaie de modéliser la couleur, sa
perception par les individus.

De nombreux travaux ont été réalisés dès le moyen-âge, mais concrètement
c'est au 19ème siècle, puis au 20ème qu'ont été faites les principales
avancées.

Je ne suis pas un spécialiste de la physiologie du système visuel
humain, pas plus qu'un chercheur dans le domaine complexe de la
colorimétrie. J'ai repris quelques informations minimales qui me
semblent indispensable à la compréhension, au lecteur intéressé
d'approfondir s'il le souhaite ces données par l'utilisation du Web ou
des quelques liens que je joins.

Couramment en photographie, on se sert de modèles qui ont 50 ans ou plus
: RGB et ses dérivés (HSV, HSL, CMJN,...), XYZ, et Lab et ses dérivés
(Luv, Lch).

Je ne reviendrais pas sur le modèle RGB qui est connu de tous, il est
dépendant du périphérique et ne prend en compte aucun CAM (color
appearance model).

La définition du CIE XYZ (1931) a constitué le premier pas de la
commission internationale de l'éclairage(CIE) vers une description des
couleurs conforme à la vision humaine. Sommairement, une couleur peut
être caractérisée par 3 valeurs X,Y,Z obtenues par combinaison de «
tristrimulus values », « CIE standard observer » et la « spectral power
distribution » de la couleur de base. Ce modèle est repris dans RT
notamment au niveau de la balance des blancs...Ce modèle ne prend en
compte aucun CAM, mais c'est une avancée extraordinaire, car on peut
dorénavant modéliser la couleur en termes cognitifs.

Le modèle Lab a été mis au point en 1976 par la CIE en le dérivant du
modèle XYZ, il caractérise une couleur à l'aide d'un paramètre
d'intensité correspondant à la luminance et de deux paramètres de
chrominance qui décrivent la couleur. Il a été spécialement étudié pour
que les distances calculées entre couleurs correspondent aux différences
perçues par l’œil humain. Le modèle Lab est très implanté dans RT, il
sert de base à une majorité de fonctionnalités : renforcement
(sharpening), bruit (denoise), tone mapping, Lab adjustements, etc.. Le
modèle Lab possède quelques caractéristiques d'un CAM, mais les
prestations sont sommaires. Le modèle CIECAM02, dérivé du CIECAM97 et
s'appuyant sur les travaux de G.Hunt, est le premier modèle utilisable
couramment en photographie, car il est inversible...et relativement «
simple », il permet de prendre en compte d'autres aspects que ceux
purement cognitifs et est fondé sur les travaux de nombreux chercheurs
sur la base d'échantillon de personnes qui évaluent différents
paramètres comme :

#### le contraste simultané

Variation de l’apparence colorée d’un objet en fonction des
caractéristiques colorimétriques de son environnement proche. Par
exemple une même couleur sera perçue différemment sur un fond clair ou
sombre, plus le fond sera sombre plus il va être nécessaire de renforcer
la couleur... (Creative Common Attribution-share Alike 4.0)
<img src="/images/Simult-contr1.jpg" title="Simult-contr1.jpg" width="600"
alt="Simult-contr1.jpg" />
<img src="/images/Simult-contr3.jpg" title="Simult-contr3.jpg" width="600"
alt="Simult-contr3.jpg" />

#### l'effet de Hunt

Augmentation de la coloration perçue (colorfulness) avec la luminance.Un
objet apparaît plus vif et contrasté en pleine lumière qu’à l’ombre.
(Creative Common Attribution-share Alike 4.0)
<img src="/images/Huntseffect1.jpg" title="Huntseffect1.jpg" width="600"
alt="Huntseffect1.jpg" />
<img src="/images/Huntseffect-2.jpg" title="Huntseffect-2.jpg" width="600"
alt="Huntseffect-2.jpg" />

#### Effet de Stevens

Augmentation du contraste perçu avec la luminance. Quand la luminance
augmente, les couleurs sombres apparaissent encore plus sombres et les
couleurs lumineuses apparaissent encore plus lumineuses. (Creative
Common Attribution-share Alike 4.0)
<img src="/images/Simult-contr2.jpg" title="Simult-contr2.jpg" width="600"
alt="Simult-contr2.jpg" />

#### Effet de Helmholtz-Kohlrausch

Dépendance de la brillance (brightness) par rapport à la luminance et à
la chromaticité. Les objets de couleur apparaissent plus clairs que les
objets achromatiques ayant la même luminance. Les couleurs les plus
saturées apparaissent les plus brillantes. (Creative Common
Attribution-share Alike 4.0)
<img src="/images/Helmholtz-effect.jpg" title="Helmholtz-effect.jpg" width="600"
alt="Helmholtz-effect.jpg" />

#### Adaptation chromatique

Ajustement par le système de vision de l'homme de certains stimuli
couleur. L’adaptation chromatique nous permet d’interpréter une couleur
selon son environnement spatio-temporel. C’est un effet essentiel à
prendre en compte par un CAM.

- L'adaptation chromatique est la capacité du système visuel humain à
  s'ajuster aux changements de conditions d'illuminant. Autrement dit,
  nous nous adaptons à la couleur de la source lumineuse pour mieux
  préserver la couleur des objets. Par exemple, sous une lumière
  incandescente, un livre blanc apparaît jaune. Cependant, nous avons la
  capacité automatiquement de modéliser la lumière jaunâtre et nous
  voyons donc le papier comme blanc. Le monde qui nous entoure serait en
  effet très compliqué si les objets changeaient de couleur chaque fois
  que la source de lumière change même légèrement. Depuis la nuit des
  temps, nous devons être capable de savoir si un fruit est mûr que ce
  soit le matin, le midi, ou le soir. L'adaptation chromatique nous rend
  cela possible. Mais elle peut être aussi la source de nombreuses
  illusions d’optique. Je pense que la majorité des utilisateurs de RT
  connaissent au moins de nom, le précédent modèle d'adaptation
  chromatique « Bradford »
- etc.

Remarque : il ne sera pas ici question de « Munsell Correction », car
par principe CIECAM02 est construit autour des tables de Munsell...cette
correction est donc prise en compte, même si le modèle présente des
lacunes !

#### Origine dans Rawtherapee

Mes premières réflexions à propos de CIECAM02 remontent à 2007, et à
l'élaboration d'une feuille de calcul, pour obtenir les meilleurs
résultats lors de l'élaboration de profils « ICC input ».

Début 2012, je me suis penché sur une demande des utilisateurs : «
peut-on avoir des références de couleurs – palette de couleur – (peau,
ciel,..) qui permettraient par comparaison/itération une meilleure
balance des blancs ». J'ai également travaillé sur la notion de « CRI
-Color rendering Index » qui traduit l'écart d'un illuminant par rapport
aux illuminants de base...plus le CRI est bas, plus le rendu sera
mauvais à température de couleur
identique[Color_Management/fr](color_management/fr)

Le patch s'appuyant sur CIECAM02, contient les éléments nécessaires de
base pour travailler ces 2 points, mais il manque un élément essentiel,
pas évident à élaborer..une pipette...

J'ai longtemps considéré CIECAM02, non pas comme un gadget, mais comme
quelque chose de difficile à mettre en œuvre...et avec un bonus assez
faible par rapport à Lab. La demande de Michael Ezra qui m'a d'abord
surpris, m'a amené à ré ouvrir le dossier ; le plug-in pour Photoshop a
été pour moi une découverte par l’exemple, de CIECAM02. Je suis
aujourd'hui convaincu que même si le modèle n'est pas parfait (pour
certaines photos l'utilisation est quasi impossible!), c'est à ce jour
un plus indéniable en termes de gestion des couleurs. Le module que je
propose est une « initiation », il est possible de développer à partir
des données CIECAM02, une série de fonctionnalités similaire à celles
développées dans RT (Lab adjustements avec divers courbes, tone-mapping,
etc.) avec probablement des avancées significatives en termes de
qualité.

L'absence de véritable documentation ajoute à la complexité...Certains
point de vue sont personnels (peut être entachés d'erreur ?). Si un
spécialiste lit ces lignes je serai heureux de modifier mon texte et mes
algorithmes !)

#### Evolution

##### Ciecam

Depuis 2016, Ciecam16 a été proposé par les chercheurs. J'ai effectué la
mise à jour en 2020, du module situé dans l'onglet "avancé" (avec un
choix possible entre Ciecam02 et Ciecam16, pour préserver la
compatibilité). Désormais il prend le nom de "Color Appearance &
Lighting (CIECAM02/16).

- Ciecam16 présente plusieurs avantages par rapport à Ciecam02 : code
  plus simple, absence d'artefacts, meilleur gamut (beaucoup plus
  large);
- Cam16 (autre nom de Ciecam16) est maintenant présent dans l'onglet
  "Local" - "Color appearance (Cam16 & JzCzHz)"

##### Jzazbz - JzCzHz

JzCzHz est la transformée simple de Jzazbz - comme Lch pour Lab.

Ce module "expérimental" directement dérivé du travail en cours de
chercheurs, n'est pas un CAM à proprement parler. Mais il se comporte
très bien (une fois les nombreux dysfonctionnements résolus) à la fois
pour des images HDR que SDR. Vous le trouvez dans "Color appearance
(Cam16 & JzCzHz)" avec le choix complexité "avancé"

### Quelques définitions - CIECAM02/16

1.  Brigthness \[brillance\](CIECAM02/16 & JzCzHz) : La quantité de
    lumière perçue émanant d’un stimulus = Indicateur qu’un stimulus
    apparaît comme plus ou moins lumineux, clair.
2.  Ligthness \[luminosité, luminance, clarté\](Lab, CIECAM02/16):
      
    La clarté d’un stimulus relativement à la clarté d’un stimulus qui
    apparaît blanc sous des conditions similaires de visualisation.

    A noter que dans RT, le terme « brightness » s'applique à «
    Lightness » ! Il sera nécessaire de réaliser un patch pour renommer
    « brightness » en « lightness » dans les modules « exposition », «
    Lab adjustements », etc.
3.  Hue (teinte) et angle de teinte (partiellement dans Lab ,
    CIECAM02/16) : Le degré auquel un stimulus peut être décrit comme
    similaire à une couleur décrite comme rouge, vert, bleu et jaune.
4.  Colorfulness (CIECAM02/16): La quantité perçue de teinte par rapport
    au gris,= indicateur qu’un stimulus apparaît comme plus ou moins
    coloré.
5.  Chroma (Lab, CIECAM02/16 & JzCzHz) : La « coloration» d’un stimulus
    relativement à la clarté d’un stimulus qui apparaît blanc sous des
    conditions identiques.
6.  Saturation (CIECAM02/16 & JzCzHz): La coloration d’un stimulus par
    rapport à sa propre bril"lance
7.  PQ (Cam16 & JzCzHz): Appliqué aux matrices de conversion, c'est une
    sorte de gamma variable. Modifie les résultats observés, en tenant
    compte des caractéristiques de l'image (Source) et du type de sortie
    (moniteur) HDR ou SDR. Peut être réglé entre 100cd/m2 et 10000cd/m2

En résumé :

1.  Chroma = (Colorfulness) / (Brightness of White)
2.  Saturation = (Colorfulness) / (Brightness)
3.  Lightness = (Brightness) / (Brightness of White)
4.  Saturation = (Chroma) / (Lightness)
      
    = \[(Colorfulness) / (Brightness of White)\]\* \[(Brightness of
    White) / (Brightness)\]

    = (Colorfulness) / (Brightness)

CIECAM02/16 élabore et utilise plusieurs type de variables corrélées qui
permettent d'utiliser ces concepts :

J: lightness ou clarté, proche de L (Lab)

C: Chroma, proche de C (Lab)

h : angle de teinte, proche de H (Lab)

H: teinte. Une teinte peut être décrite par la composition de 2 couleurs
de base parmi 4 (rouge, jaune, vert, bleu), par exemple 30B70G ou encore
40R60Y.

Q: brightness

M : colorfullness

ac, bc : proches de a et b (Lab)

Alors ! Pourquoi la saturation en plus d'autres variables proches ? Je
cite un texte de Robert Hunt (2001)

  
*Of the three basic color perceptions, hue, brightness, and
colorfulness, hue has no relative version, but brightness has lightness,
and colorfulness has chroma and saturation. Correlates of chroma are
widely used in color difference formulae, but saturation currently plays
little part in color science and technology. This is perhaps because in
many industries flat samples are viewed in uniform lighting for the
evaluation of color differences, and in this case chroma is the
appropriate contributor for samples of small angular subtense. For
samples of large angular subtense, however, a correlate of saturation
may be more appropriate to use. In the real world, it is common for
solid objects to be seen in directional lighting; in these circumstances
saturation is a more useful percept than chroma because saturation
remains constant in shadows. In imaging, artists and computer-graphics
operators make extensive use of series of colors of constant saturation.
In optical imaging, saturation can be an important percept in large dark
areas. Recent experimental work has provided a much improved correlate
of saturation.*

## Les 3 processus

Trois processus permettent l'utilisation de CIECAM, leurs appellations
dépend de chaque concepteur...J'en fait une synthèse (rappel : ce
document n'est pas un cours, ni une thèse sur CIECAM...mais une aide à
la compréhension et à l'utilisation).

### Processus 1

On trouve les appellations de « origin », « forward », « input », «
source »... Finalement j'ai choisi « source » qui correspond aux
conditions de prise de vue et à la manière de ramener les conditions et
les données, vers une zone « normale ». Il faut entendre par « normale
», des conditions et des données moyennes ou standard, c'est à dire sans
prise en compte des corrections CIECAM, par exemple « surround=average
», balance des blancs D50 !

### Processus 2

Il correspond au traitement des variables corrélées (J C h H Q M s a b)
à diverses fins : action sur la clarté (lightness J), la brillance
(brightness Q), la chroma (C), la saturation (s), le niveau de couleur
(colorfullness M), l'angle de teinte h, ainsi que sur ac et bc. Il est
tout à fait possible de construire un logiciel graphique autour de ses
variables...

Dans le cas de ce patch pour RT, j'ai choisi arbitrairement 4
regroupements d'algorithmes :

1.  JC en lui adjoignant une fonction contraste ;
2.  Js, comme ci-dessus
3.  QM
4.  Tout : ensemble des paramètres y compris h.

Ces modules sont simples, plus à caractère pédagogique que de chercher à
résoudre les problèmes de colorimétrie, même si les résultats obtenus
sont de mon point de vue excellents.

J'ai complété ce processus par :

1.  des « curves » (double...) agissant sur les contrastes J (lightness)
    ou Q (brightness) dont le principe est similaire aux courbes doubles
    de « exposition » ;
2.  un choix pour des courbes de couleur entre chroma, saturation et
    colorfullness (niveau de couleurs) .

On pourrait ajouter d'autres algorithmes s'appuyant sur la transformée
de Fourrier, ou remplaçant les fonctions équivalentes de RT...

### Processus 3

On trouve les appellations de « inverse », « reverse », « ouput », ou
encore « viewing conditions ».

J'ai choisi « viewing conditions » qui traduit le support sur lequel
sera visionnée l'image finale (moniteur, TV, projecteur,...), ainsi que
son environnement. Ce processus va prendre les données venant du
processus 2 et les « amener » au support de telle manière que les
conditions de visualisation et de son environnement soient prise en
compte.

Nota : c'est ici qu'on trouve l'explication sur la différence de rendu
entre une photo imprimée et une photo examinée sur un moniteur – même si
l'imprimante est haut de gamme et bien étalonnée : les conditions
d'observation ! Une photo imprimée sera souvent regardée dans un album
(souvent sur un fond noir), dans un environnement peu lumineux...et
souvent en éclairage tungstène. L'originale sera vue sur un moniteur
avec un fond clair...et un illuminant D50...Il n'est pas question de
modifier la sortie « impression », mais d'adapter la sortie « moniteur,
TV... »

Ceci revient à dire, mais là s'arrête la comparaison, qu'on réalise
quelque chose qui ressemble à un épreuvage, mais ce n'en est pas un
puisque c'est la finalité de CIECAM, On prend en compte les réglages
situés dans "Viewing conditions" (point blanc du périphérique de sortie
\[écran TV, projecteur...\] via le température de ce point blanc, ainsi
que sa luminance moyenne \[% gris\]. On prend également en compte la
luminance de la pièce dans laquelle se fait l'observation, ainsi que la
luminance relative de l'entourage du périphérique de visualisation (plus
ou moins noir).

Synthèse simplifiée ce que permet RT avec le patch actuel :

1.  cas général de l'utilisateur qui utilise RT pour visualiser son
    développement...ce doit être 95% des cas. Dans ce cas « viewing
    conditions » correspond à l'environnement de travail de RT, par
    exemple :
    - point blanc du moniteur réglé sur 6000K
    - moniteur étalonné : donc Yb=18
    - mais selon :
      - le « theme » choisi dans « Preferences / General» (presque noir
        ou gris), il faut changer « surround »
      - l'emplacement du moniteur (sur fond neutre ou foncé), il faut
        changer « surround »
      - l'éclairage de la pièce, qui va changer avec l'heure , il va
        falloir changer « adaptation luminosity viewing La »: par
        exemple la nuit sans éclairage d'appoint « La » sera proche de 0
        ou de 1, et à l'inverse le jour dans une pièce très lumineuse, «
        La » sera proche de 1000
2.  Cas moins fréquent, mais possible, car je l'ai déjà fait, je me sers
    de RT et du téléviseur familial pour montrer des photos et aussi les
    possibilités de RT. Les « viewing conditions » seront différentes et
    à adapter à chaque cas ; il faut reprendre chacun des points
    ci-dessus avec probablement des réglages différents : point blanc
    TV, Yb TV (empirique) ?, « surround » différent car en général on
    regarde la TV sur un fond tamisé, et on réduit l'éclairage de la
    pièce
3.  on souhaite préparer une série de photos, pour une exposition : dans
    ce cas en bon professionnel on va « voir » les conditions de
    visionnement sur place et on pose des questions sur le projecteur :
    point blanc, étalonnage (??), luminosité de la salle le jour de
    l'expo, etc. Avec RT l'utilisateur va régler « viewing conditions »
    pour les adapter aux conditions de l'exposition, et sortir X jpeg
    (ou TIFF) correspondants
4.  etc.

## Données

Quelles sont les données prises en compte et quelle simplifications
ai-je (arbitrairement?) opérées ? Comment les ajuster ?:

- **Yb** (aussi dans JzCzHz) : Yb est la luminance relative de l'arrière
  plan ! Avec cela on a beaucoup avancé ! Concrètement elle s'exprime en
  % de gris. Un gris à 18% correspond à une luminance du fond exprimée
  en CIE L de 50%.

:\*pour le processus 3), si votre moniteur est étalonné vous devez sans
problème avoir une valeur de Yb proche de 18 ou 20. Si le téléviseur ou
le projecteur, qu'il semble difficile d'étalonner, vous paraît sombre,
ou clair vous pouvez ajuster empiriquement cette valeur. Elle dépend du
support de visualisation et peut donc être considérée comme constante
pour un ensemble de photos dans une condition d'observation. Si vous
souhaitez changer cette valeur allez dans « Preferences », « Color
Management » : « Yb luminance output device (%) »

:\*pour le processus 1) c'est nettement plus complexe, car :

::\*une image est rarement avec une exposition constante et peu de
variations de luminance ;

::\*j'ai placé le module CIECAM en fin du processus Lab, juste avant la
conversion RGB et l'envoie sur des périphériques de sortie ; on peut
donc penser que l'utilisateur aura utilisé les divers outils (de
qualité) de RT pour rendre l'image avec un histogramme « moyen ».

  
  
Cette donnée est calculée à partir de la luminance moyenne de l'image.
Bien sûr si dans l'avenir RT était capable à l'aide de pipettes de
séparer l'images en zones (sombres, normales, lumineuses...) il serait
possible d'entrer plusieurs valeurs Yb. Par exemple sur une image on
pourrait voir trois zones :

- standard qui correspond à la luminance moyenne de l'image avec un Yb
  réglé à 20% ;
- sous exposée (contours approximatifs délimités à la pipette...) où la
  luminance serait calculée et aboutirait par exemple à un Yb de 5% ;
- surexposée où on arriverait à un Yb de 70%...

- **La** (aussi dans JzCzHz) : La est la luminance absolue du champ
  d'adaptation ! Là encore on a beaucoup avancé !

:\*Dans le processus 1) elle correspond à la luminance lors de la prise
de vue, si par exemple vous faites une photo à l'ombre, « La » sera
proche de 2000cd/m2 ; si vous faites des prises de vues intérieur, « La
» variera en fonction de l'éclairage de 20 à 300cd/m2...En reproduction,
ces valeurs pourront être plus faibles encore

:\***”Luminosité de la Scène” et le bouton“Auto”** (processus \#1):

:\*\* Si activée, La est calculée avec les données Exif (vitesse
d'exposition, ISO, Diaphragme, compensation d'exposition de l'appareil)
et aussi le point blanc Raw et le curseur de compensation d'exposition

:\*pour le processus \#3, cette donnée traduit l'entourage de l'image
lors de la visualisation. Plus l'entourage sera sombre, plus il faudra
accroître le contraste de l'image. La variable « surround » n'agit pas
comme un D-lighting ou une courbe de tons, elle modifie également les
couleurs dans les axes rouge-vert et bleu-jaune. Si la luminance de
l'entourage est supérieure à 20% choisissez « average », sinon adaptez à
vos conditions, par exemple les réglages de RT (Preferences / General /
Select theme) auront une incidence sur le rendu final. Ce réglage est
accessible par « Surround(viewing) ». plus l'entourage sera sombre, plus
l'image verra son contraste simultané accentué.

:\*Ces 2 valeurs de “La" sont paramétrable dans RT, dans le module“CIE
Color Appearance Model 2002”

- **Surround** (aussi dans JzCzHz - Scene conditions- (Entourage)

:\*ici encore j'ai procédé à des simplifications...

:\*pour le processus 1) cette donnée traduit certaines conditions de
prise de vue, par exemple photos dans un musée avec un fond sombre, ou
encore réalisation d'un portrait sur un fond noir. Généralement
l'utilisateur de RT aura corrigé avec les nombreux outils, les écarts
par rapport à sa perception. Néanmoins j'ai ajouté une case à cocher «
Surround (scene) dark » (entourage sombre), qui peut être activée si
nécessaire. Son utilisation aura pour effet d'éclaircir l'image (rappel
le processus « ramène » les données pour les amener « normales »

:\*pour le processus 3), cette donnée traduit l'entourage de l'image
lors de la visualisation. Plus l'entourage sera sombre, plus il faudra
accroître le contraste de l'image. La variable « surround » n'agit pas
comme un D-lighting ou une courbe de tons, elle modifie également les
couleurs dans les axes rouge-vert et bleu-jaune. Si la luminance de
l'entourage est supérieure à 20% choisissez « average » (moyen), sinon
adaptez à vos conditions, par exemple les réglages de RT (Preferences /
General / Select theme) auront une incidence sur le rendu final. Ce
réglage est accessible par « Surround(viewing) ». plus l'entourage sera
sombre, plus l'image verra son contraste simultané accentué.

- **White-points model** (modèle de point blanc)

:\*3 possibilités s'offrent à vous, là encore j'ai tenu à simplifier au
maximum.

:\*« WB RT + output » : ici on fait confiance à la balance des blancs de
RT pour le processus 1) ; CIECAM utilise D50 comme référence : la
balance des blancs de RT ramène les conditions à un équivalent D50 ; par
contre pour le processus 3), il va être nécessaire – selon le besoin –
de régler le point blanc du périphérique de sortie. Allez dans «
Preference / Color Management / Settings white output device (monitor,
TV, projector) et choisissez un illuminant parmi la liste (est-elle
suffisante ? Je n'ai aucune idée sur les caractéristiques des
projecteurs , lampe, température...

:\*« WB RT+CAT02/16 + output » ; pour le processus 3) on se retrouve
comme ci-dessus ; pour le processus 1) un mix est réalisé entre la
balance des blancs de RT et CAT02/16 qui utilise ses réglages, ce qui
fait qu'on a une solution où les 2 effets (RT et CAT02) se combinent).
Vous pouvez moduler l'action de CAT02/16, en agissant sur le curseur «
CAT02 adaptation ». Vous serez probablement amenés à changer le réglage
de la balance des blancs de RT, afin de bénéficier des avantages du «
mix », sinon les effets s'ajoutent.

:\*Free temp+green + CAT02 + \[output\]; ici on entre pour l’essentiel
dans le processus symétrique (voir plus loin), en permettant à
l'utilisateur de modifier le point blanc de départ (par défaut D50)

:\*CAT02 est une adaptation chromatique, elle convertit les valeurs XYZ
d'une image dont le point blanc est Xw0,Yw0, Zw0, en de nouvelles
valeurs XYZ dont le point blanc devient Xw1,Yw1,Zw1 ; l'algorithme
utilisé est proche de celui de Von Kries, donc différent de la
correction de RT qui prend en compte les multiplicateurs de canaux !

- **«CAT02 adaptation et case à cocher « auto »**

:\*voir ci-dessus pour l'utilisation « WB CAT02/16 + output »

:\*cependant même lorsque « white point model » est sur « equal », ce
curseur peut être utile. Normalement la cas « auto » doit être cochée et
CIECAM calcule lui même un coefficient interne « D » qui sert ailleurs
qu'à l'adaptation chromatique. Le résultat se traduit par une valeur
supérieure à 0.65 (65%), ; vous pouvez décocher la case ce qui aura pour
effet de modifier le processus 1), les effets peuvent être inattendus...

## Mode normal ou symétrique et CAT02/16 adaptation White Balance

Il y a deux manières de se servir de Ciecam.

### Normal

- le mode "normal" qui consiste à séparer les paramètres de la "scène"
  de ceux "viewing conditions". Dans ce cas, qui semble le plus
  opportun, Les valeurs de "La", "Yb", "Surround", Cat02 sont optimales
  pour chacun des processus 1 et 3. C'est dans ce cas que l'utilisateur
  agira sur les curseurs et courbes du processus 2. Ce mode est le plus
  développé dans cette aide.

### Symetrique

- le mode "symétrique". Celui ci consiste à :
  - mettre les mêmes valeurs de "La", "Yb", "Surround", "Cat02", pour
    les processus 1 et 2. je recommande sauf cas exceptionnel, de mettre
    "La" à 400 et "Yb" à 18.
  - régler "WP model" à "Free temp + green + CAT02 + \[output\]"
  - Dans "Scene conditions", laisser les valeurs de Temperature et Tint
    à respectivement 5000K et 1., qui correspondent à l'illuminant D50
  - Dans "Viewing condition", ajuster le curseur Temperature à la valeur
    de la temperature de la balance des blancs, et ajuster empiriquement
    la valeur de Tint (qui en réalité est en coordonnées Y (XYZ) et non
    G (RGB).
  - on obtient ainsi un remarquable outil d'adaptation chromatique, que
    je pense très performant:
    - nettement plus que les méthodes de Von Kries ou Bradford
    - plus que par l'application séparée des procédures "Cat02" et
      "inverse Cat02", car l'algorithme prend en compte la quasi
      totalité des paramètres Ciecam (contraste simultané, Hunt, etc.)

<!-- -->

- dans certains cas, cette adaptation chromatique, peut être prise en
  défaut, lorsque l'image d'origine à des valeurs de "La" très faibles,
  associée à une température de balance des blancs très basse (souvent
  en dessous de 2500K). On atteint une des limites du modèle Ciecam,
  dans ce cas la solution est de réduire les valeurs de Cat02.

### Adaptation chromatique automatique - cat02/16 preset

Afin de faciliter l'accès à une adaptation chromatique performante, j'ai
ajouté à Ciecam02, une case à cocher "cat02 preset" Cette case à cocher
réalise pour vous une série de réglages de Ciecam pour lui donner les
préréglages requis pour réaliser une adaptation chromatique automatique.

#### Que fait l'adaptation chromatique

La balance des blancs (automatique ou non) va réaliser une analyse
mathématique de l'image et une correspondance plus ou moins exacte
(selon la balance des blancs) entre l'illuminant, les couleurs réelles
(fleurs, ciel, peau, etc.) et l'observateur standard 2°. Par exemple
dans la balance des blancs automatique (Itcwb) une comparaison et une
optimisation est réalisée entre les couleurs majoritaires de l'image et
un panel de couleurs de références en données spectrales. Mais ceci ne
veut pas dire que le résultat vous conviendra. Bien sûr l'algorithme
peut échouer (rare), mais dans une majorité de cas, nos yeux et notre
cerveau "adaptent" les conditions de vision pour les ramener à
l'illuminant lumière du jour D50. C'est un processus physiologique.
L’adaptation chromatique Cat02/16, tente de réaliser ce que fait vos
yeux et votre cerveau. Elle correspond d'une certaine manière aux
adaptations chromatiques présentes dans les profils d'entrée ou dans
certains profils de travail ou de sortie (par exemple sRGB est en D65
avec une adaptation Bradford) Donc, cette adaptation va "réchauffer" ou
"refroidir" l'image après les calculs mathématiques

#### Valeurs des préréglages

Celle-ci devrait convenir dans une majorité de cas. Que fait ce preset ?

- il tient compte des réglages de la balance des blancs (température et
  teinte = 1) et les reporte dans "Viewing conditions"
- il met Ciecam en mode symétrique
- il ajuste les valeurs de "Scene conditions" et "Viewing conditions"
  avec les mêmes valeurs moyennes
  - absolute luminance : 400
  - Mean luminance % : 18
  - Surround : average
- Cat02 adaptation scene est réglée à 90
- Cat02 adaptation viewing conditions est réglée à 90
- WP model est réglé sur "Free" avec "Temperature" = 5000K et "Tint"= 1
  ce qui correspond à la référence de blanc D50. Si vos conditions de
  prise de vue sont différentes et que vous êtes sûr de ces conditions,
  alors changez par exemple pour l'illuminant D65

#### Que faire ?

Dans une majorité de cas, le seul réglage à toucher est Cat02/16
adaptation viewing conditions.

Si vous jugez la correction trop forte, vous pouvez changer "Temperature
viewing conditions". Par exemple si le résultat de la balance des blancs
est 7600K vous pouvez ajuster la température autour de cette valeur,
notamment en fonction du choix de l'illuminant. Vous pouvez également
changer "teinte" qui est à 1. par défaut.

Malheureusement (ou heureusement !) la correspondance entre Ciecam02/16
et la réponse de notre cerveau et de notre œil n'est pas parfaite,
suivant les images et les conditions de prises de vue. Donc une démarche
pragmatique s'impose, avec 2 curseurs prioritaires : "Cat02 adaptation
viewing conditions" et "Temperature viewing conditions".

Dans une démarche avancée vous pouvez si vous le souhaitez, ajuster les
valeurs de "Scene conditions" et "Viewing conditions" aux conditions
réelles, par exemple changer "Surround" (viewing conditions)

Il faut être très prudent avec "Temperature" et "Tint" de "Scene
conditions" qui sont réglées pour l'illuminant D50, vous pouvez si vous
le souhaitez régler le point blanc sur une autre illuminant qui doit
correspond aux condition de prise de vue, par exemple en choisissant
l'illuminant D65 qui va régler la "température" à 6504K, attention à ne
pas toucher à "tint" qui doit rester à 1.

## Algorithmes

Choisissez JC, JS, QM (bien sûr il y a d'autres combinaisons
possibles!), ou « Tout » qui reprend l'ensemble des paramètres possibles
(j'ai arbitrairement exclu « h » ainsi que « ac » et « bc » des 3
algorithmes JC, JS, QM).L'utilisation la plus courante (si on peut
utiliser ce terme pour CIECAM) est JC. Agissez ensuite sur les curseurs
pour obtenir le rendu souhaité...qui je le rappelle dépend du
périphérique de visualisation, de son environnement, de ses réglages et
de la luminance de la pièce.

- **Algorithme JC**

:\*J simule la luminosité (lightness) – proche de L (Lab) et C simule la
chroma, proche de la chromaticité c (Lch). Mais, différence importante,
J et C prennent en compte les « effets » (contraste simultané, Hunt,
Stevens, etc.) ce que ne fait pas Lab et encore moins RGB.

:\*J varie dans l'intervalle \[0..100\] et correspond à une valeur
relative de la luminosité (comme L, ou Value...) et en théorie C dans
l'intervalle \[0..180\] (il peut être plus élevé)

:\*Les 2 curseurs qui utilisent J et C peuvent varier de -100, à +100
avec des actions semblables aux curseurs « Brightness » (qu'il faut
rebaptiser Lightness) et « Chromaticity » de « Lab adjstements »

:\*avec l'algorithme « JC », un contrôle des tons chairs est possible,
l'action est semblable au curseur similaire de « Lab adjustements »

:\*Le curseur « contrast » module l'action de « J » avec une courbe en «
S », qui prend en compte la luminosité moyenne « J » de l'histogramme.

- **Algorithme « Js »**

:\*il est similaire à JC sinon :

:\*la chroma est remplacée par la saturation (CIECAM). Mais pour quel
usage ? Je cite à nouveau un extrait du texte de G.Hunt : *For samples
of large angular subtense, however, a correlate of saturation may be
more appropriate to use. In the real world, it is common for solid
objects to be seen in directional lighting; in these circumstances
saturation is a more useful percept than chroma because saturation
remains constant in shadows. In imaging, artists and computer-graphics
operators make extensive use of series of colors of constant saturation.
In optical imaging, saturation can be an important percept in large dark
areas. Recent experimental work has provided a much improved correlate
of saturation.*

:\*Le contrôle des tons chairs est moins « fin » que avec « JC » plus
étendu globalement aux rouges

- **Algorithme QM**

:\*ici on utilise 2 variables Q (« brightness ») et M (« Colorfullness
») qui ne sont pas des données relatives, mais absolues. On prend en
compte la luminosité du blanc. Il est facile de se rendre compte qu'un
même blanc « J=100 » paraîtra plus lumineux au soleil que dans une pièce
sombre...

:\*la luminosité du blanc prend en compte les paramètres suivant (scène)
: « adaptation luminosity La », « CAT02 adaptation »,ainsi que « Yb »
(non réglable actuellement)

:\*le contrôle en usage courant est plus délicat que avec « JC »,
néanmoins il donne des possibilités pour les images à haut contraste et
ouvre la porte au traitement HDR

:\*Le contrôle des tons chairs est moins « fin » que avec « JC » plus
étendu globalement aux rouges

:\*Le « contraste » agit évidemment différemment...puisqu'il prend en
compte Q différent de J.

- **Algorithme « Tout »**

:\*vous pouvez agir sur l'ensemble des variables CIECAM : J, Q, chroma
C, saturation s, niveau de couleur M, contraste J, contraste Q, angle de
teinte h, protection des tons chair et rouges .

## Courbes tonales et couleur

### Courbes

- vous disposez – comme dans le module «exposition » de deux jeux de
  courbes tonales, qui agissent sur la luminosité J (lightness) et la
  brillance Q (brightness). Vous pouvez n'utiliser qu'une courbe, ou
  deux en mariant ou non « lightness » et « brightness ». Attention, les
  courbes « brightness » peuvent facilement aboutir à des résultats hors
  limites ! « Brightness » est une échelle absolue, alors que «
  Lightness » est une échelle relative, un même blanc « J » paraîtra
  plus blanc au soleil qu'à l'ombre, ce que prend en compte « brightness
  » (Q). De ce fait les courbes, « lightness » et « brightness » auront
  un rendu différent dans les ombres et les lumières élevées.
- vous disposez également d'un jeu de courbe « chroma » avec 3 choix :
  chroma (le plus courant), saturation, colorfullness. Ces 3 courbes
  permettent d'ajuster le paramètre choisi en fonction de lui même, par
  exemple moduler la saturation afin d'éviter que les couleurs déjà
  saturées soient hors gamut. Pour ces 3 courbes, le curseur «
  protection des tons chairs et rouge » est opérationnel, il est plus
  approprié aux tons chairs dans le mode « chroma ». Je recommande
  d'utiliser le mode « parametric » qui permet de différencier selon le
  niveau de sautration des couleurs. Nota : toutes les combinaisons «
  curves chroma» (chroma, saturation, colorfullness) et curseurs
  (chroma, saturation, colorfullness) ne sont pas possible sans
  complexifier par trop le code, d'où quelques cas, où certains curseurs
  peuvent être grisés.

### Histogramme et courbes tonales

L'histogramme des courbes tonales, dans le 'Color Appearance & Lighting
(Ciecam02/16)*, peut montrer les valeurs avant ou après que CIECAM02 est
appliqué. Pour voir les valeurs après l'action de CIECAM02, activer
l'option "*Show CIECAM02/16 output histograms in curves''". Si désactivé
l'histogramme affiche les valeurs avant CIECAM02

### Histogramme et courbe couleur

L'histogramme de la courbe couleur montre la distribution de la chroma
(saturation/colorfullness) en fonction de l'intensité de la chroma
(saturation / colorfullness) ou de la chromaticité en mode Lab. Plus
l'histogramme est décalé à droite, plus les couleurs saturées sont
proches des limites du gamut. Plus l'histogramme est décalé vers la
gauche plus les couleurs seront ternes.

L'absciise représente la valeur de la chroma (saturation/colorfullnees)
ou de la chromaticité en mode Lab. Cette échelle est "ouverte"

Comme d'habitude, l'ordonnée représente le nombre de pixels concernés.

## Gamut control (Lab + CIECAM)

Cette case à cocher va faire rentrer les données dans l'espace de
travail, j'aurais pu réaliser cette action en mode CIECAM (processus 3)
mais cela aurait considérablement ralenti le système.

L'algorithme utilisé est le même que dans « Lab adjustements », il
travaille en colorimétrie relative. Les écarts avec ce qui pourrait se
faire en mode CIECAM sont je pense minimes.

Quelques ajustements du code de CIECAM sont réalisés lorsqu'on coche la
case « Gamut control »...

## Code, précision des calculs et temps de traitement

Le code pour les processus 1 et 3 est strictement celui de CIECAM02
(M.Fairchild, Billy Biggs,...) que j'ai adapté à RT et optimisé, ainsi
que des améliorations apportées à la correction du gamut par Changjun
Li, Esther Perales, M Ronnier Luo and Francisco Martínez-Verdú

Les 2 processus de traitement 1) et 3) sont symétriques et empilent de
nombreux calculs en virgule flottante. D'où des temps de traitement
assez importants de l'ordre de 1 seconde par Mpix. Après des tests
intensifs nous avons montré que l'utilisation de la précision "float" au
lieu de "double" n'avait pas de grosses conséquences en termes de rendu
d'image.

En termes de précision j'ai tenu à vérifier « à blanc », en comparant
une série de données avant et après CIECAM ; les écarts sont très
faibles , par exemple une valeur XYZ au démarrage de 6432,456 se
retrouve en sortie à 6432,388, ce qui est correct.

## Limitations de CIECAM02 et CIECAM16

Ce modèle (CIECAM02) n'est pas parfait et les limitations ci-après sont
identifiées, elles peuvent aboutir pour certaines images à
l'impossibilité d'un traitement correct :

- on a déjà pu le voir pour les réglages de Yb.
- CIECAM02 n'est pas un espace de travail comme sRGB ou Prophoto ou même
  Lab ; en ce sens il est difficile de contrôler le gamut, CIECAM est
  même connu pour ses problèmes de gamut étroit, ainsi des effets
  inattendus peuvent survenir aux limites si vous agissez trop sur les
  curseurs (J, C, s...) ; ceci peut amener dans les cas critiques
  (hautes lumières,...) des points noirs dans ces zones, ou des points
  blancs,...n'hésitez pas à utiliser les outils de RT (highlight
  recovery, highlight reconstruction, impulse noise reduction,...), ou
  des zones brûlées ou noires (raw white and black point, avoid color
  shift,...)
- les grands espaces de travail (widegamut, Prophoto...) pourront amener
  dans certains cas, des zones noires alors qu'elles n'apparaîtront pas
  en sRGB (étroitesse du gamut de CIECAM).
- Les images bruitées vont influer CIECAM, celui-ci pensant que les
  points colorés sont des réalités ; c'est pourquoi j'ai placé CIECAM
  après « denoise »
- le modèle CIECAM privilégie les « cônes » et prend peu en compte les «
  bâtonnets » ..ce qui revient à dire que la vision périphérique est peu
  prise en compte.
- Donc n'espérez pas avec CIECAM02 trouver un remède aux images «
  difficiles » (surexposition, saturation du capteur, etc.) ; par contre
  pour des images « normales » (ce qui est la majorité), les avancées me
  semblent plus que significatives.
- Etc.

CIECAM16 est apparu en 2016, mis à jour dans Rawtherapee en 2020. Il
corrige la quasi totalité des défauts.

## Les 12 principes d'un CAM par R.Hunt

1.  The model should be as comprehensive as possible, so that it can be
    used in a variety of applications; but at this stage, only static
    states of adaptation should be included, because of the great
    complexity of dynamic effects.
2.  The model should cover a wide range of stimulus intensities, from
    very dark object colors to very bright self-luminous color. This
    means that the dynamic response function must have a maximum, and
    cannot be a simple logarithmic or power function.
3.  The model should cover a wide range of adapting intensities, from
    very low scotopic levels, such as occur in starlight, to very high
    photopic levels, such as occur in sunlight. This means that rod
    vision should be included in the model; but because many
    applications will be such that rod vision is negligible, the model
    should be usable in a mode that does not include rod vision.
4.  The model should cover a wide range of viewing conditions, including
    backgrounds of different luminance factors, and dark, dim, and
    average surrounds. It is necessary to cover the different surrounds
    because of their widespread use in projected and self-luminous
    displays.
5.  For ease of use, the spectral sensitivities of the cones should be a
    linear transformation of the CIE x , y , z or x 10 , y 10 , z 10
    functions, and the V’() function should be used for the spectral
    sensitivity of the rods. Because scotopic photometric data is often
    unknown, methods of providing approximate scotopic values should be
    provided.
6.  The model should be able to provide for any degree of adaptation
    between complete and none, for cognitive factors, and for the
    Helson- Judd effect, as options.
7.  The model should give predictions of hue (both as hue-angle, and as
    hue-quadrature), brightness, lightness, saturation, chroma, and
    colorfulness.
8.  The model should be capable of being operated in a reverse mode.
9.  The model should be no more complicated than is necessary to meet
    the above requirements.
10. Any simplified version of the model, intended for particular
    applications, should give the same predictions as the complete model
    for some specified set of conditions.
11. The model should give predictions of color appearance that are not
    appreciably worse than those given by the model that is best in each
    application.
12. A version of the model should be available for application to
    unrelated colors (those seen in dark surrounds in isolation from
    other colors).

## Quelques liens

CIECAM02 Wikipedia [4](http://en.wikipedia.org/wiki/CIECAM02)

Color Appearance Model - Fairchild
[5](http://www.cis.rit.edu/fairchild/PDFs/AppearanceLec.pdf)

Mémoire Laborie ENS Louis Lumière
[6](http://www.ens-louis-lumiere.fr/fileadmin/recherche/Laborie-photo-2007-mem.pdf)
