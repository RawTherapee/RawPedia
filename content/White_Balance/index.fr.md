---
title: White Balance
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Balance des blancs

</div>

## Introduction

Une image numérique se compose généralement d'un assemblage des trois
couleurs primaires : rouge, vert et bleu. Pour diverses raisons que vous
pouvez approfondir dans d'autres lectures, les valeurs du rouge, vert et
bleu qui servent de point de départ dans n'importe quel programme de
développement de photos raw doivent être corrigées de différentes
manières avant que le rendu ne ressemble à la scène photographiée. Une
de ces corrections est réalisée par l'ajustement de la balance des
blancs, garantissant que les objets de couleur neutre (blanc) de la
scène photographiée apparaissent blancs sur la photo. Le réglage de la
balance des blancs a des conséquences sur toutes les couleurs, bien
qu'il soit plus facile de discerner si une balance des blancs est
correcte en observant un objet connu pour être de couleur neutre (blanc,
gris).

Le réglage de la balance des blancs fonctionne en multipliant chaque
couleur primaire par un montant différent jusqu'à obtenir un résultat
satisfaisant. Dans le but de rendre cette opération aisée pour
l'utilisateur, au lieu d'agir directement sur les trois multiplicateurs,
l'interface présentée à l'utilisateur prend la forme d'un curseur des
températures qui ajuste la couleur sur un axe bleu-jaune, et un curseur
des teintes que les ajuste sur un axe magenta-vert.

Un couleur neutre est celle pour laquelle les valeurs rouge, vert et
bleu sont égales. Par exemple, R=V=B=65% and R=V=B=90% sont neutres
toutes les deux, la première étant plus foncée que la seconde. Vous
pouvez dire si la balance des blancs d'un point qui doit être neutre est
correcte en contrôlant si les valeurs RVB du point correspondent, ou si
les valeurs a\* et b\* dans l'espace colorimétrique La\*b\*
correspondent, ou si les petites barres indicatrices du RVB sous
l'histogramme principal se supperposent exactement. Vous pouvez faire
cela même si votre moniteur est très mal calibré. Votre perception des
couleurs change en fonction des couleur avoisinantes et de l'éclairement
du local, ne faites pas toujours confiance à vos yeux, utilisez plutôt
les méthodes indiquées ci-dessus.

Une balance des blancs incorrecte procure à l'image une dominante de
couleur, typiquement chaude (orange), ou froide (bleue). Certains
utilisent cela à des fins d'effets créatifs. Cependant divers outils et
opérations présument que la balance des blancs de l'image est correcte,
par exemple la reconstruction des hautes lumières dans l'outil
[Exposition](exposure/fr), le réglage des tons chairs dans
l'outil [Contraste par niveaux de
détail](Contrast_by_Detail_Levels/fr.md) ou des tons ciel dans
l'outil [Ondelettes](wavelets/fr), l'outil
[CIECAM02](ciecam02/fr) etc). Ainsi, ne faites pas une
mauvaise utilisation de l'outil balance des blancs pour créer une
dominante de couleur à des fins artistiques, mais utilisez le plutôt
pour vous assurer que les zones neutres restent neutres, puis utilisez
[Virage partiel](color_toning/fr) ou tout autre outil pour
apporter des dominantes créatrices.

L'outil balance des blancs peut être activé/désactivé. Désactivé, les
multiplicateurs sont fixés à R=1 V=1 B=1 pour un travail sur les
fichiers raw. Cela peut s'avérer utile à des fins de diagnostic ou pour
travailler sur des images UniWB.

## Description de l'interface

### Méthode

La balance des blancs peut-être obtenue de différentes façons : Appareil
photo, Auto, Personnalisé ou une multitude de réglages prédéfinis pour
différentes sources de lumière.

- [image:Wb-camera.png](image:wb-camera.png) Appareil photo

  
Reprend la balance des blancs utilisée par l'appareil photo. Si vous
prenez les vues en mode raw uniquement (c'est à dire pas de raw+jpg),
paramétrez la balance des blancs de l'appareil sur Auto. Cela donne en
général de bons résultats.

- [image:Wb-auto.png](image:wb-auto.png) Auto

Deux algorithmes sont à votre disposition

- Auto RGB grey . Corrige automatiquement la balance des blancs, en
  supposant que la couleur moyenne de la scène est gris neutre.
  Fonctionne bien pour une grande variété de scènes, et peut être un bon
  point de départ pour des ajustements manuels.
- Temperature correlation ou (Auto Iterate temperature correlation
  Itcwb) . Assure une équilibre des couleurs généralement meilleur que
  "auto RGB grey"
  - L'algorithme est basé sur la meilleure corrélation (test de Student)
    entre les couleurs de l'image et un panel de couleurs de références
    spectrales parmi 200.
  - Cet algorithme peut donner des résultats erronés:
    - si l'illuminant n'est pas avec un CRI (Color Rendering Index)
      proche de 100, par exemple les conditions "Underwater",
      "Fluoresent", "Led" risquent de donner de mauvais résultats
    - certains fichiers de type DNG obtenus après conversion avec DNG
      converter ou autre converter.
    - si les conditions de prise de vue sont extrêmes (très faibles
      valeurs de luminance...)
    - etc.
  - Le GUI affiche la valeur de la correlation :
    - une valeur de 1000 signifie soit que la calcul n'est pas ré
      effectué, les résultats précédents sont utilisés soit que
      l’algorithme échoue dans ce cas T=5002 est affiché
    - des valeurs inférieures à 0.01 sont bonnes

<!-- -->

- [image:Wb-custom.png](image:wb-custom.png) Personnalisé

  
Réglez votre propre température de couleur et teinte de vert en
déplaçant les deux curseurs et/ou en utilisant l'outil Point de mesure.

- Présélections de sources de lumière
  - [image:Wb-sun.png](image:wb-sun.png) Lumière du jour
    (ensoleillé)
  - [image:Wb-cloudy.png](image:wb-cloudy.png) Nuageux
  - [image:Wb-shade.png](image:wb-shade.png) Ombre
  - [image:Wb-water.png](image:wb-water.png) sous marin
  - [image:Wb-tungsten.png](image:wb-tungsten.png) Tungstène
  - [image:Wb-fluorescent.png](image:wb-fluorescent.png)
    Fluorescent
  - [image:Wb-lamp.png](image:wb-lamp.png) Lampe
  - [image:Wb-led.png](image:wb-led.png) LED
  - [image:Wb-flash.png](image:wb-flash.png) Flash

### Observer (branch whitebalanceopt)

Réglage dans "Preferences / Color Management / White Balance"

La gestion des couleurs dans Rawtherapee (Balance des blancs,
multiplicateurs de canaux, Récupération des hautes lumières,…) utilise
les données spectrales des illuminants et des couleurs. Observer est un
paramètre important de cette gestion qui prend en compte l’angle de
perception de l’œil. En 1931 il a été fixé à 2° (privilégie
l’utilisation des cônes). En 1964 il a été fixé à 10° (privilégie
l’utilisation des cônes, mais prend en compte partiellement les
bâtonnets). Observer 10° est sélectionné par défaut. Pour éviter une
(rare) dérive des couleurs dues au choix Observer 10° - probablement due
à la matrice de conversion – sélectionner Observer 2°. Dans une majorité
de cas Observer 10° sera un choix plus pertinent.

### Principe de l'algorithme Temperature correlation - (Itcwb  Iterate temperature correlation white balance):

Contrairement à la majorité des algorithmes de balance des blancs qui
sont basés sur les gris, celui-ci est basé sur les couleurs. De manière
simplifiée l'algorithme compare un panel majoritaire de couleurs de
l'image et des couleurs de référence à données spectrales.

#### Origine de l'algorithme

C'est une simple lecture d'un résumé de recherche non documenté
précisant 3 phases qui m'a lancé dans la mise au point de l'algorithme :

- a\) comparaison xyY
- b\) données spectrales
- c\) histogramme des couleurs
- c'est sur cette base que j'ai mis au point l'algorithme que je vais
  décrire ci-après, donc à l'origine ni algorithme de principe, ni
  code,...

##### Sa pertinence est fondée sur:

- le choix des couleurs de l'image : échantillonnage, prise en compte
  des couleurs dominantes (peau, ciel, végétaux...)
- la prédétermination de certains paramètres de base pour les calculs
  (température camera, teinte,...)
- le choix des multiplicateurs de canaux RGB et leur calcul en fonction
  de la température de l'illuminant
- le principe mathématique de calcul des valeurs XY des couleurs de
  référence (données spectrale), par une formule « exacte » et un
  échantillonnage des données spectrales à 5nm. Matrice\[Couleur vue\] =
  Matrice\[illuminant\] \* Matrice\[couleur\] / Matrice\[Observer 10°\]
  (ou Observer 2° dans Options ou Preferences)
- L’itération multiple des calculs en prenant en compte à égalité
  l'équilibre vert-magenta et rouge-bleu.
- Des calculs rigoureux si l'illuminant est avec un CRI (Color Rendering
  Index) proche de 100, donc illuminant proche de Daylight dans la
  limite 4000K – 15000K ou Blackbody de 2000K à 4000K.
- La corrélation statistique via un test de Student.

#### Origine et nature des 429 couleurs spectrales de référence :

- soit elles proviennent de données que l'on trouve sur le web pour les
  fleurs, feuillages
- soit elles proviennent de la ColorChecker24 ou d'autres grilles
- soit elles proviennent de la mire d'étalonnage 468 que j'ai élaborée
  pour l'étalonnage il y a quelques années
- soit elles sont élaborées à partir de l'utilitaire Colorlab (Logo
  Gmbh)
- ces couleurs sont réparties à peu près également sur toute la palette
  de couleurs (Rouge, Orange, Jaune, Vert, Cyan, Bleu, Magenta...)
- ces couleurs sont également réparties entre neutres ou proches des
  gris, peu saturées, pastels, saturées
- la luminance n'a que peu d'importance car la comparaison se fait sur
  la composante chroma

#### Principes généraux :

- en amont on calcule à partir de données situées après dématricage 3
  tableaux red, green, blue pour 1 pixel sur 3 de l'image -
  horizontalement et verticalement (il est possible de changer cette
  valeur si nécessaire pour plus ou moins de précision). Les valeurs
  sont ajustées, selon la précision souhaitée, afin qu'elles soient dans
  l'amplitude 0..65535;
- puis on passe à une procédure commune aux 2 algorithmes « autowb » via
  le calcul des multiplicateurs de canaux RGB, qui oriente ensuite soit
  sur « Itcwb », soit sur « wb auto» ("Wbauto")
- « Wbauto » passe les paramètres à "Itcwb" avec les premiers paramètres
  réellement importants (ce sont des choix arbitraires, mais je pense
  pertinents) : température de référence – celle présente dans les
  données Exif (camera) et celle de la teinte également présente dans
  les données Exif, mais dont les valeurs sont bornées à 0.77 et 1.30 –
  (il n'y a pas d’illuminant Daylight ou Blackbody au delà des ces
  limites arbitraires et donc les calculs seront fantaisistes ou
  faux...).

#### Algorithme simplifié « Itcwb » proprement dit :

##### Première étape :

- calcul des multiplicateurs RGB pour chaque température entre 2000K et
  15000K et de la teinte
- calcul des valeurs XY à partir des 429 données spectrales pour chaque
  température
- choix d'une plage de données pour les températures par rapport à la
  référence
- calcul des valeurs xy sous la forme d'un histogramme : positionnement
  de ces couleurs parmi 237 en privilégiant les données les plus
  répandues (peau, ciel,...) pour chaque température
- tri ascendant de ces données en nombre
- pour les données majoritaires, calcul des valeurs chromatiques de
  l'image
- choix des couleurs de référence parmi les 429, par utilisation d'un
  deltaE chroma.
- Calcul des valeurs RGB de référence en fonction de la température de
  référence

##### Deuxième étape :

- calcul pour chaque couleur de référence choisie, des valeurs XY en
  fonction de la température et de la teinte
- calcul des valeurs RGB de l'image à partir des couleurs choisies à
  l'aide des multiplicateurs RGB,
- premier calcul de la corrélation Student
- pour chaque plage de teinte et de température, calcul des
  multiplicateurs de canaux , calcul des XY à partir des bonnes données
  spectrales
- calcul des coefficient de corrélation en fonction de green (teinte)
- tri de ces valeurs
- optimisation afin de déterminer les bonnes valeurs de température et
  teinte.
- Passage de ces paramètres à « wbauto »
- affichage des résultats et prise en compte dans Improccoordinator.cc

##### Dernières Améliorations 05 2023

- Par défaut, car il est nécessaire d'avoir une référence de démarrage
  pour l'algorithme, les paramètres choisis sont ceux de "Camera"
  (température et teinte). Il s'avère que dans quelques cas, ces valeurs
  sont manifestements fausses. Dans le cas où "camera" teinte est
  supérieur à 1.5 ou "Camera" température est inférieure à 3300K ou
  "Camera" température est supérieure à 7700K, la nouvelle référence de
  démarrage est celle calculée avec "Automatic RGB grey" (ou un mix de
  "Camera" et "Automatic RGB grey").
- Lorsque "Camera" température est inférieure à 4000K ou "Camera"
  température est supérieure à 6000K, un processus 2 passes de
  l'algorithme est mis en place, en cherchant si une une autres valeur
  assez distante donne de meilleurs résultats. Lorsque "Camera"
  température est supérieure à 4000K ou "Camera" température est
  inférieure à 6000K, un autre processus 2 passes est mis en oeuvre avec
  de plus faibles écarts par rapport à "Camera".
- Si vous activez "Low sampling & No use Camera settings", en amont de
  l'algorithme et dans l'algorithme, le système utilisera un mix des
  réglages "Camera" et "Auto WB grey"
- le calcul du vert (teinte) a été revu;
- une tentative d'optimisation du patch est réalisée à partir de
  l'analyse chromatique de l'image (écart par rapport au point blanc).
  Plus la valeur est faible, plus en théorie le patch est crédible.
- avant d'élaborer l'histogramme des données de l'image, un léger
  débruitage (median 3x3), est appliqué.
- un contrôle de gamut est également appliqué au moment du calcul des
  données de l'histogramme, éliminant les valeurs aberrantes.

###### Limites de l'algorithme

Le système n'est pas intelligent, il est logique.

Il y aura des images qui ne seront (évidemment) pas bien traitées. Par
exemple les images avec une ou deux fortes dominantes de couleur et
quasi absence de blancs (gris) seront mal optimisées. Par exemple les
fleurs sur un arrière plan de feuillage. De la même façon les
illuminants loin de Daylight (LED) ou les mélanges illuminants amèneront
des résultats incorrects.

##### Données affichées dans le GUI - limites d'interprétation

- Multipliers r, g, b. Ceux-ci sont donnés à titre d'information et ne
  sont pas modifiables;
- Correlation factor: donne une probabilité de corrélation entre les
  données de l'image et les données spectrales. Ce coefficient est
  indicatif, car il suppose que le patch est "bon", or ce patch est
  relativement indéterminé: quelles données prendre ? Sur quelle
  amplitude ? Certes il va traduire, pour un choix température / teinte
  de démarrage le meilleur compromis, mais est-ce que le choix de
  démarrage est optimum ?
- Passes ( 1 ou 2) et Alt_temp: affiche le nombre de passes de
  l'algorithme effectuées ainsi que l'éventuelle température
  alternative. Dans le cas "2 passes" la case à cocher "Remove 2 passes
  algorithm" est active, sinon elle est inactive.
- Read colors : nombre de couleurs lues dans l'image (dépend de
  "Sampling"), le maximum est de 237 qui couvre l'ensemble du diagramme
  CIExy.
- Patch chroma : indicateur qui traduit la tentative d'optimisation du
  patch. Une pondération selon une loi exponentielle,, affecte les
  valeurs pour essayer de prendre en compte "au mieux" les aplats (ciel,
  peau..) et les données plus isolées.
- Size : nombre de couleurs choisies à la fois dans l'image (de la plus
  élevée en nombre de pixels correspondants, à la plus faible).
- patch ΔE : montre le deltaE du patch entre les données images et les
  données spectrales.
- datas x9 : affiche le nombre d'enregistrements trouvés pour chaque
  couleur. Maximum et minimum. Le minimum absolu est(arbitrairement)
  fixé à 400. Pour avoir une évaluation réelle il faut multiplier ces
  valeurs par 9, car seul 1 pixel sur 3 (horizontal et vertical) est
  analysé pour minimiser le temps de traitement.

###### Limites d'interprétation

L'algorithme Itcwb est complexe, mais dépourvu d'intelligence. Il n'y a
pas interprétation de l'image: est-ce un portrait ? un paysage ? quelle
est la nature et la répartition des données ? Donc il faut être très
prudent sur le "pilotage" du système par ces indicateurs. certes ils
semblent robustes dans une majorité de cas mais il y a de nombreuses
exceptions:

- ce n'est pas parce que "patch chroma" est plus bas que le patch est
  obligatoirement meilleur. Cet indicateur montre pour un couple
  "température / teinte" une optimisation possible, mais est-ce la
  meilleure ? Il va permettre de choisir la taille du patch.
- ce n'est pas parce que "deltaE" est le plus bas, que ce choix est le
  plus optimum. Certes il traduit pour une amplitude donnée de
  température / teinte autour d'une valeur de référence, l'optimisation
  des écarts, mais cela ne démontre pas que c'est le meilleur choix.
- ce n'est pas parce que "Correlation factor" est le plus faible que le
  résultat est optimum. Cette correlation traduit l'optimisation d'une
  "teinte" et d'une température autour d'une valeur de référence, mais
  cela ne démontre pas que c'est le meilleur choix.

Le système détermine d'abord (avant d'aborder l'algorithme proprement
dit) quelles références de base utiliser (Camera ou auto WB grey). Puis
il détermine si il va utilser 1 ou 2 passes. En première étape, pour
chaque passes (ou une seule) l'optimisation du patch est faite avec
"patch chroma". Puis l'algorithme teste une plage de température et de
teinte et calcule deltaE du patch et correlation. Un compromis est
trouvé par la prise en compte du minimum de la multiplication du detaE
et de la correlation. D'autre part, lorsqu'on est loin de D65 (valeur
prise en compte par Adobe) pour déterminer la matrice de couleurs, la
probabilité que les données lues et interprétées soient incorrectes
augmente et les résultats affichés probablement entachés d'erreur. Il
n'existe pas à ce jour de possibilité dans Rawtherapee de lire 2
matrices de couleurs. Même si cette possibilité existait le travail de
calcul et saisie des matrices de couleurs stdA serait considérable.

##### Paramètres modifiables par l’utilisateur (branch whitebalanceopt)

Par défaut les réglages doivent convenir dans une majorité de cas.
Néanmoins il est possible d’apporter des modifications personnalisées au
fonctionnement de l’algorithme.

Vous pouvez faire apparaître dans l’onglet  Color / White Balance  une
série de réglages qui permettent d’adapter l’algorithme. A terme
(j’espère) pouvoir supprimer la majorité de ces réglages (peut être
tous). La finalité de cette mise à disposition de ces réglages
(optionnelle) est pour l’essentiel la mise au point de l’algorithme.

Pour faire apparaître ces réglages supplémentaires, aller dans
Preferences / Color Management / White balance – Automatic temperature
correlation, et cocher la case correspondante. Si "Temperature
correlation" n'est pas sélectionné dans "White Balance", les choix
apparaissent en grisé.

###### Quels sont les paramètres qui doivent avoir une influence

Je pense pouvoir émettre un avis pertinent, étant le concepteur de
l'algorithme. Néanmoins, je laisse la 'porte ouverte' à d'autres
hypothèses car la colorimétrie en général et l'adaptation à Rawtherapee
peut réserver des hypothèses.

Paramètres ayant une influence (a priori):

- La matrice de couleur 3x3 :
  - la matrice 3x3 assure la conversion des données brutes Raw, en des
    données utiles. Dans Rawtherapee, ces indispensables matrices qui
    sont utilisées dans plusieurs algorithmes de la partie Raw ont pour
    origine Adobe, soit elles sont issues de Dcraw, soit elles
    proviennent de Adobe DNG converter (Tag matrice). Comment ont été
    obtenues ces matrices par Adobe ? Recherche interne, lien avec le
    constructeur,... ? On peut penser que ces matrices sont construites
    dans un processus commun, et donc que toutes choses égales par
    ailleurs, la même scène, sous le même illuminant, pris dans les
    mêmes conditions (vitesse, diaphragme, objectif,...), avec un
    processus Raw commun, doit amener des données couleurs (et non pas
    la luminance ou la Dynamic Range) Raw utilisables sensiblement
    identiques (avec les réserves possibles dues au paramètres
    développés ci-après). Que ce soit une matrice de Bayer, ou autre, un
    boîtier de marque X ou Y. Évidemment il y a des différences, en
    particulier pour les matrices non-Bayer qui ont un algorithme de
    dématricage spécifique, ainsi que pour les optiques...mais les
    écarts doivent être minimes.
  - Cette matrice est pour l’illuminant D65. Dans les exifs on trouve
    une deuxième matrice pour l’illuminant stdA (tungstène). Un essai
    effectué sur un raw à 2600K, m’amène à penser que ce choix serait
    (un peu) meilleur. Cependant Rawtherapee ne sait gérer que une
    matrice de couleur. D’autre part comment ferait-t-on le choix ? Et
    comment mettre à jour les centaines de camera ?
  - Cette matrice est « le facteur » qui identifie marque, modèle. Il
    permet (sauf si cette matrice est mal calculée, cas rare…) de dire
    que la marque et le modèle sont pris en compte et qu’ils n’ont pas
    d’influence sur l’algorithme. Ceci ne veut pas dire que la marque,
    le modèle n’ont pas d’importance, évidemment que oui au sens gamut.
    Mais c’est pris en compte par l’algorithme si les données spectrales
    sont suffisantes.
- Le nombre de couleurs spectrales : il semble évident que plus on
  augmente le périmètre des données de l’image (lecture des données xyY
  dans le diagramme CIExy), plus les appareils seront récents avec un
  gamut très large, plus il faudra des données spectrales
  correspondantes – sinon l’algorithme fonctionne mal. Le nombre des
  données des couleurs spectrales est passé de 201 jusque début 2023, à
  429 actuellement. Peut être faut-il encore plus de données ?
- L'algorithme de dématricage a lui aussi une (petite) influence, en
  particulier les algorithmes prévus pour traiter les images bruitées
  (LMSSE, IGV), et bien sûr l’algorithme de dématricage pour les
  non-Bayer, par exemple Xtrans-demosaic (Frank Markesteijn's algorithm,
  and Ingo Weirich). De même les traitements Raw exécutés avant Itcwb
  ont eux aussi une incidence certaine, par exemple Capture Sharpening
  et la correction d’aberration chromatique. Mais ce n’est pas un
  dysfonctionnement, au contraire cela montre que l’algorithme
  fonctionne et prend en compte les changements de couleurs induits par
  ces processus.
- Chaque capteur – associé à un boîtier – a :
  - une DR (Dynamic range) spécifique – souvent aux environs de 12Ev
    pour les appareils anciens, proches de 15 ou 16Ev pour les appareils
    récents. Cette DR doit avoir une incidence faible sur l’algorithme,
    la composante luminance est quasi ignorée (sinon pour déterminer le
    gamut).
  - White-levels et Black-levels : si ces 2 composantes ont une forte
    importance pour l’ensemble du traitement Raw, sauf si ils sont très
    mal réglés, ils ne doivent pas avoir d’influence sur l’algorithme.
  - le gamut du capteur : je n’ai pas connaissance de documents
    officiels montrant les limites de transcription des couleurs. Il est
    raisonnable de penser que avant matrice de conversion, ces limites
    sont largement suffisantes et au-delà de Prophoto, et donc n’ont pas
    ou peu d’influence sur l’algorithme.
- La nature et l'intensité des couleurs : la répartition dans le
  diagramme xyY. Est-on avec une image où les couleurs sont proches du
  point blanc (couleurs pastels ou neutres), ou des images avec des
  couleurs aux limites de celles de la perception humaine ?
- La répartition de ces couleurs par rapport à chacune des primaires
  Rouge / Verte / Bleue.
- Comme l'algorithme divise l'espace 'xy' en 236 zones, couvrant
  l'ensemble de l'espace visible, l'algorithme doit prendre en compte
  cette répartition: par exemple une majorité de tons très proches du
  point blanc (neutre) ou une dominante importante (ciel, ou peau).
- Et bien sûr le (les) illuminants. Une image avec des parties à l'ombre
  et au soleil est en réalité avec 2 illuminants Daylights (proches de
  5000K au soleil et de 7000K à l'ombre). Ce qui est quasi insoluble
  avec un seul paramétrage de la balance des blancs (température,
  teinte). Bien sûr c'est encore plus complexe si des illuminants de
  type Fluorescent ou LED sont présents. Mais ces remarques ne sont pas
  spécifiques à Itcwb, mais à tous les algorithmes de balance des
  blancs. Local adjustments (Warm/ cool) permet d'apporter une assez
  bonne correction aux doubles illuminants (soleil, ombre...).
- Toujours concernant les illuminants, ceux-ci ont une définition
  théorique qui lie les données spectrales à une température. Ces
  formules par principe ne peuvent être parfaites et répondre à tous les
  environnements : latitude, altitude, heure, conditions météorologique
  (brumes, gradients,...) qui doivent avoir une incidence sur la teinte
  (green) qui devient différente de 1.
- Observer 2° (1931) ou Observer 10° (1964) : le deuxième assure une
  meilleure perception de la vision humaine. C’est celui utilisé par
  défaut dans Itcwb.
- Pour rappel une couleur perçue avec ses données XYZ est la combinaison
  de 3 matrices :
  - données spectrales de l’illuminant (fonction de la température et de
    la nature de l’illuminant).
  - données spectrale de la couleur de base (mesurée au spectro).
  - données spectrales de l’observer (2° ou 10°).

Par principe cet algorithme n'est pas conçu pour corriger les
dysfonctionnements du processus de traitement (qui est toujours très
complexe). Bien sûr il peut (éventuellement) corriger un problème, mais
ce n'est pas sa finalité.

###### Réglages

- Diagramme CIExy et gamut: On pourra remarquer sur les 2 diagrammes
  ci-dessous, que ce n'est pas parce que une couleur est dans le
  diagramme CIExy qu'elle est dans le gamut.
  - Exemple pour une luminance de 10 et une luminance de 50 \[0..100\].

<figure>
<img src="/images/Gamu-comp10.jpg" title="Gamu-comp10.jpg" />
<figcaption>Gamu-comp10.jpg</figcaption>
</figure>

<figure>
<img src="/images/Gamu-comp50.jpg" title="Gamu-comp50.jpg" />
<figcaption>Gamu-comp50.jpg</figcaption>
</figure>

<figure>
<img src="/images/Rec2020_Pointer.jpg" title="Rec2020_Pointer.jpg" />
<figcaption>Rec2020_Pointer.jpg</figcaption>
</figure>

<figure>
<img src="/images/sRGB2jdcmax.jpg" title="sRGB2jdcmax.jpg" />
<figcaption>sRGB2jdcmax.jpg</figcaption>
</figure>

Après plusieurs semaines de tests par les utilisateurs et l’optimisation
de l’algorithme, 3 paramètres restent accessibles directement à
l’utilisateur :

- Green refinement : Permet de changer la "teinte" (vert) qui servira de
  référence au démarrage de l'algorithme. Il a sensiblement le même rôle
  pour les verts que le "AWB temperature bias" pour la température.
  L'ensemble de l'algorithme est recalculé. Selon les cas, afin de
  guider l'algorithme, l'action sur « Remove 2 pass algorithm » peut
  être nécessaire.
- Remove 2 passes algorithm : cette case à cocher, gère en arrière plan
  un processus complexe, qui amène à ce que dans les cas où il n’y a
  qu’une passe choisie par l’algorithme, l’action sur cette case à
  cocher est sans effet. Dans le cas où 2 passes sont détectées, cette
  case à cocher permet le passage d’un réglage à l’autre. Attention,
  lorsque un des 2 réglages ressort vers des températures proches de
  stdA (Tunsgtène 2855K), il faut prendre les indicateurs (Correlation
  deltaE..) avec précaution, les résultats sont probablement entachés
  d’erreurs liés à la matrice de couleur.
- Choix de l’échantillonnage des données de l’image : 4 choix sont
  proposés :
  - Low sampling – limite les données aux valeurs de sRGB. Dans
    certaines conditions (teinte camera \> 0.8), force l'algorithme à ne
    pas utiliser les réglages "Camera".
  - Medium sampling (defaut) - near Pointers's gamut. Les primaires de
    Beta RGB sont utilisées, on obtient ainsi un domaine de couleur
    proche de la vision humaine en couleur réfléchies (Subtractive color
    mixing). J'aurais aussi pu choisir Rec2020 qui est un peu plus
    "grand" que "Beta RGB".
  - Camera XYZ matrix - utilise la matrice Raw directement dérivée de
    Color Matrice (Adobe)
  - Close to full CIE diagram – la limite est celle de JDCmax, soit
    presque le diagramme CIE en entier.
  - Ces 2 échantillonnages n’ont aucun rapport avec le ‘working profile’
    et n’ont aucune incidence sur la suite du traitement, sinon sur
    l’équilibre de la balance des blancs.
  - Je recommande, dans la mesure où il y a assez de données spectrales
    de choisir ce dernier choix ‘Close to full CIE diagram’, même si
    cela peut produire des couleurs imaginaires (la majorité dans les
    verts extrêmes), car on est dans la continuité du processus avant
    l'application du "working profile". Les exceptions peuvent être de 2
    ordres : a) une image contient des données qui ne sont pas
    référencées en valeurs spectrales (doit être très rare) et dans ce
    cas les deltaE et corrélations seront biaisés ; b) vous souhaitez
    volontairement ne pas prendre en compte des parties de l’image à
    fort gamut, qui pourraient perturber le résultat et ne pas utiliser
    les données "Camera".
  - A noter que lorsque il y a absence de "Input profile" (ou que
    l'utilisateur choisit "Camera standard") les données de référence
    qui servent à l'échantillonnage sont traitées de telle manière à
    être similaires à celles utilisées postérieurement.

Réglages accessibles depuis les pp3:

- Itcwb_findgreen - Find green student : nombre d'itérations pour
  trouver le meilleur compromis entre la corrélation (student) et la
  valeur de green qui pour les illuminants Daylight / Blackbody est
  proche de 1. Par défaut : 3. Étendue des réglages pris en compte
  \[2..5\]. Il semble que la valeur 3 soit un bon compromis, ce qui
  permettrait de supprimer ce réglage.
- No purple color used : par défaut ce réglage n'est pas pris en compte.
  Si l'image a besoin de reconstruction des hautes lumières il peut être
  nécessaire de l'activer.
- itcwb_minsize : fixé par défaut à 20. Fixe la valeur minimum de la
  taille du patch.
- Itcwb_rgreen - Geen range : fixe l'amplitude d'examen de la valeur de
  green dans les itérations, depuis une amplitude faible de 0.82 à 1.25
  jusqu'au maximum d'amplitude 0.4 à 4. Par défaut: 1. Etendue des
  réglages pris en compte \[0..3\]
- Itcwb_delta - Delta temperature in green loop : Fixe pour chaque
  itération "green" essayé, l'écart de température à prendre en compte.
  Par défaut : 4. Etendue des réglages pris en compte \[1..8\]

Réglages accessibles depuis le fichier 'options'

- Itcwb_deltaspec : si Verbose est à "true", affiche les résultats (dans
  la console) des données images et spectrales dont l'écart en deltaE
  est supérieur à cette valeur. Par défaut 0.075.
- Itcwb_maxsize : fixe la taille maximale du patch. Par défaut la valeur
  est de 70.

###### Adaptation chromatique

Les résultats de l'algorithme Itcwb, traduisent la pertinence des
calculs sur des fondements mathématiques objectifs. mais ce résultat -
comme d'ailleurs tous les réglages de la balance des blancs - ne
tiennent pas compte en totalité de la perception humaine : surround,
contraste simultané,... et surtout l'adaptation de notre oeil / cerveau
aux écarts de température par rapport à D50 (qui est la référence en
colorimétrie). Pour palier cet écart, il est possible de mettre en place
une adaptation chromatique "intégrée" à la balance des blancs (c'est ce
que j'avais proposé en 2018...) ou laisser l'utilisateur mettre en place
cette adaptation avec le module "Color Appearance & Lighting".

Pour y parvenir et limiter le rôle de Ciecam, mettez Ciecam en mode
"Automatic symmetric", le système va appliquer 2 adaptations
chromatique, la première de "Scene conditions" à l'illuminant de
référence (en général D50, mais vous pouvez le changer), la seconde de
l'illuminant de référence à "Viewing conditions". Par défaut les 2
pourcentages d'adaptation sont réglés à 90%, vous pouvez accroître ou
réduire ces valeurs. Vous pouvez aussi modifier la température dans
"Viewing conditions" pour obtenir un rendu, plus chaud, plus froid. Vous
pouvez, si vous les souhaitez, changer les réglages de Ciecam comme
"Absolute luminance", "Surround", etc. Voir le tutoriel sur Ciecam.

###### Quelques exemples

J'ai (arbitrairement) choisi ces 6 exemples, pour montrer ce que peut
(et ne peut pas) faire Itcwb associée ou non à Color Appearance &
Lighting.

- Montagne de sel en Turquie (NEF): Cette image qui paraît anodine est
  complexe au niveau de la photo, pour plusieurs points:
  - le blanc de la montagne de sel est difficile à traiter, et est
    affecté d'une structure complexe qui rend difficile le traitement en
    général.
  - Le point qui nous intéresse ici concerne la balance des blancs et la
    répartition des couleurs. La majorité de l'image ciel, arbres,
    montagne est dans sRGB, mais les fleurs en bas de l'image (rouge,
    orangé, jaune) sont bien au-delà: comment traiter, incidences des
    réglages
  - Fichier raw (Jacques Desmis - Creative Common Attribution-share
    Alike 4.0):
    [1](https://drive.google.com/file/d/1azCxu1midw6dcuN7SbvbAiJH4pxX5BTA/view?usp=sharing)
- Lunching Room (CR2): Cette image montre que l'algorithme peut se
  sortir de situations complexes.
  - Par défaut avec White Balance réglé sur "Camera" l'image est verte.
  - Essayez successivement, White Balance auto : 'Rgb grey' et
    "Temperature correlation"
  - Fichier raw (Creative Common Attribution-share Alike 4.0):
    [2](https://drive.google.com/file/d/1MMNzw3tPQuMeD5baqDlBXRvl4lDy2mLX/view?usp=sharing)
- London Bridge (PEF): Cette image montre à la fois la nécessité de
  l'adaptation chromatique et le pertinence de l'algorithme Itcwb.
  - Le réglage par défaut 'Camera' donne une dominante verte/jaunâtre.
  - Itcwb permet de trouver un bon compromis mathématique, mais la
    température est élevée rendant à l'image une coloration chaude, qui
    peut se voir sur les visages, les haubans du pont.
  - Essayez Color Appearance en mode "Automatic symmetric"
  - Fichier raw (Rawtherapee - Creative Common Attribution-share Alike
    4.0)[3](https://drive.google.com/file/d/1CiQ2t4KyD3tdCiNNhskqUG2cH9LT2ly7/view?usp=sharing)
- Mire étalonnage (RAF)
  - j'ai choisi cette mire pour deux raisons: la première c'est un
    fichier RAF donc Non-Bayer; la deuxième c'est qu'il contient des
    blancs et des noirs presque purs (les gris sont dominants dans
    l'image, ce qui pourrait gêner l'algorithme).
  - Néanmoins il ne semble pas à examiner les résultats (neutral) que
    l'appareil ait été étalonné (ou je ne dispose pas du profil), les
    informations sont donc des ordres de grandeurs, mais assez proches
    de la réalité (blancs, noirs , ColorChecker)
  - Itcwb ne sait pas que c'est une mire d'étalonnage, essayez du fait
    du gamut un peu élévé 'Force use of the entire CIE diagram' activé
    ou désactivé, 'Sort in chroma order' désactivé ou activé et "no
    purple used" désactivé - les résultats sont très proches de ceux
    avec Camera (lesquels sont les meilleurs ?), mais il n'y a pas de
    dérives.
  - Fichier raw (Creative Common Attribution-share Alike 4.0):
    [4](https://drive.google.com/file/d/1YFeoPL-RhStftDCCkbDNlmj8New_SgX0/view?usp=share_link)
- Contre-jour Caraïbes (ARW)
  - J'ai choisi cette image, prise avec mon ancien Sony lors d'un voyage
    aux Caraïbes, où j'avais choisi la balance des blancs automatique.
  - Essayez avec 'Camera' puis 'Itcwb'.
  - Fichier raw (Jacques Desmis - Creative Common Attribution-share
    Alike 4.0):
    [5](https://drive.google.com/file/d/1iqpj-vT3dqUmaXKOQE7QB_rynf4cbRPC/view?usp=share_link)
- Utilisation de Inpaint-opposed (NEF)
  - j'ai choisi cette image pour montrer l'incidence de la balance des
    blancs sur "Inpaint opposed" (highlight reconstruction), notamment
    l'influence green (tint)
  - Essayez "Inpaint opposed" avec White Balance réglé sur Camera,
    remarquez les importants artefacts dans le ciel
  - Choisissez "Itcwb" et essayez divers réglages.
  - Fichier raw (Creative Common Attribution-share Alike 4.0):
    [6](https://drive.google.com/file/d/1ZxucMREXAAFlBijiBiBZoH9kG4-O2GYb/view?usp=share_link)

#### Compatibilité 5.9

Les versions de Itcwb postérieures à 5.9 présentent une compatibilité
limitée avec la version 5.9:

- Seul est disponible le réglage "Observer 10° instead of Observer 2°".

Lorsque le système rencontre un fichier pp3 de la version 5.9 utilisant
Itcwb, alors la méthode "Temperature correlation" est affichée. Les
seules informations pertinentes sont:

- les multiplicateurs de la balance des blancs
- la température et la teinte;
- la case à cocher "Observer 10° instead of Observer 2°".

Vous pouvez basculer sur la méthode de Itcwb courante en changeant la
méthode de "Balance des blancs", par exemple en passant par "Custom",
puis "Temperature correlation".

### Pipette

<figure>
<img src="/images/White_balance_1_before.png"
title="White_balance_1_before.png" />
<figcaption>White_balance_1_before.png</figcaption>
</figure>

<figure>
<img src="/images/White_balance_1_after.png"
title="White_balance_1_after.png" />
<figcaption>White_balance_1_after.png</figcaption>
</figure>

Si vous cliquez sur le bouton Pipette
![<File:Color-picker.png>](Color-picker.png "File:Color-picker.png")
(raccourci **W**), le curseur de la souris se change en pipette
lorsqu'il survole l'aperçu. Cliquez sur une zone grise ou neutre pour
déterminer une balance des blancs correcte pour toute l'image basée sur
le point cliqué.

Choisir un point qui doit avoir un ton neutre, gris ou blanc. Ce point
ne doit pas être hors domaine, dans aucun des canaux, car le hors
domaine signifie que l'information du canal hors domaine est manquante.
En ce qui concerne la balance des blancs, "blanc" ne signifie pas R=100%
V=100% B=100% car ce serait un point hors domaine, mais signifie plutôt
une teinte de gris, très clair mais sans dépassement. Le point ne doit
pas non plus être noir, car noir signifie l’insuffisance de données en
ce point, et un calcul correct de la balance des blancs ne peut être
effectué.

Vous pouvez utiliser la pipette plusieurs fois sur différentes parties
de la photo, jusqu'à trouver une lecture idéale. Utilisez la liste
déroulante *Taille* pour modifier la taille de la pipette.

Cet outil peut aussi être utilisé dans une fenêtre de détail. Cliquer
droit pour annuler cet outil et revenir au curseur habituel de la
souris.

### Température et Teinte

Le curseur Température ajuste la couleur le long de l'axe bleu-jaune. Le
déplacer vers la gauche rend l'image plus froide (bleutée), et son
déplacement vers la droite la rend plus chaude (plus jaune).

Le curseur Teinte ajuste la couleur le long de l'axe magenta-vert. Le
déplacer vers la gauche rend l'image violacée, et son déplacement vers
la droite la rend verdâtre.

### Egaliseur Bleu/Rouge

L'égaliseur bleu/rouge permet de s'écarter du comportement normal de la
"Balance des blancs", en augmentant ou diminuant le ratio entre rouge et
bleu. Cela est utile lors de prises de vues éloignées des conditions
d'éclairage standard (par ex sous l'eau), ou bien éloignées des
conditions ayant servi aux calibrages, où les matrices de couleur dans
le profil d'entrée sont inutilisables.

### Ajustement de la température BdB

Le curseur Ajustement de la température Balance des Blancs permet de
spécifier de combien peut dévier la température calculée
automatiquement. Utiliser ce curseur si vous désirez une balance des
blancs calculée automatiquement plus froide ou plus chaude.

## Relation entre balance des blancs et exposition

La balance des blancs est décrite en termes de température et de teinte,
mais sera pour les images raw traduite en poids des canaux rouge, vert
et bleu. Ils seront ajustés de façon à ce que le canal de plus faible
poids atteigne la limite hors domaine dans l'espace colorimétrique de
travail (habituellement ProPhoto RVB) lorsque le canal raw est hors
domaine. En d'autres termes, avec l'exposition réglée à 0.0 et sans
activation de la reconstruction des hautes lumières, toute l'étendue
visible est pleinement définie par le raw. Comme la balance des blancs
change les poids, vous pouvez constater une légère évolution de
l'exposition si vous réalisez d'importantes corrections.
