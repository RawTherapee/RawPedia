---
title: Retinex
contributors:
  - Jdc
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Advanced Tab'
---

<div class="pagetitle">

Retinex

</div>

# Généralités

Alors que l'œil est capable de voir correctement les couleurs dans des
conditions de faible éclairage ou d'ambiance colorée ou de voile
atmosphérique, les appareils photo réussissent mal dans ces conditions.
C'est en s'inspirant des mécanismes biologiques de l'œil pour s'adapter
à ces conditions que l'algorithme MSR (MultiScale Retinex) a été
élaboré. Outre la photographie numérique, l'algorithme Retinex (Retinex
est la contraction de Rétine+cortex) est utilisé en astronomie pour
rendre visible l'information contenu dans les photographies
astronomiques, en médecine pour détecter des structures peu visibles
dans les radiographies et les tomodensitométries. De nombreuses théories
et algorithmes ont été mis au point depuis plus de 20 ans. La première
expérimentation a été proposée par Rahman en 1996. L'approche s'inspire
de la perception visuelle humaine et de la fonction rétinienne d'Edwin
Land. D'une certaine manière cette approche est assez « semblable » à
CIECAM. Cette fonction et plus particulièrement sa forme générale est
similaire à une différence de gaussienne \[DOG (Difference of Gaussian)
\]. L'idée consiste à caractériser l'information lumineuse d'un point à
partir de son intensité et celles de ses voisins. Ceci étant cette
approche ne repose sur aucun fondements scientifiques et s'appuie sur
l'expérience et diverses constantes empiriques. Au fil des ans de
nombreuses améliorations ont été apportées, mais de mon point de vue
aucune n'est parfaitement satisfaisante. Je me suis appuyé sur deux
documents:

- "Automatic Image Haze Removal Based on Luminance Component" (Fan Guo,
  Zixing Cai, Bin Xie, Jin
  Tang"[1](http://www.mcs.csueastbay.edu/~grewe/pubs/DistSensorNetworkBook2011/Atmosphere/HazeREmoval_SingleImage_Luminance.pdf)
- "Retinex Algorithm on Changing Scales for Haze Removal with Depth Map"
  (Weixing Wang, Lian Xu)"
  [2](https://scholar.google.com/scholar?cluster=13539545875418694074&hl=en&as_sdt=0,5)
- et de quelques astuces de programmation inspirées de "2003 Fabien
  Pelisson"

L'utilisation de Retinex pourra être bénéfique pour le traitement des
images :

- brumeuse ou avec voile atmosphérique
- où les écarts de luminance sont importants
- où l'utilisateur souhaite arriver à des effets spéciaux (Tone
  mapping,...)

## Retinex en début de processus

C'est l'algorithme décrit dans cette page, avec ses limitations, ses
avantages et inconvénients

## Retinex dans 'wavelet'

J'ai installé deux possibilités d'activer Retinex dans le processus
Wavelet [Wavelet levels/fr](wavelet_levels/fr). Certaines des
limitations évoquées ne sont plus présentes !

Comparaison rapide entre les deux versions "Retinex in wavelet" et
"Retinex en début de processus"
:[Wavelet_levels/fr#Avantages_.28.2B.29_et_inconv.C3.A9nients_.28-.29_de_Retinex.2Ffr_par_rapport_.C3.A0_Retinex_in_wavelet](wavelet_levels/fr#avantages_.28.2b.29_et_inconv.c3.a9nients_.28-.29_de_retinex.2ffr_par_rapport_.c3.a0_retinex_in_wavelet)

# Les limitations imposées par Rawtherapee

L'algorithme de base impose une référence à l'image entière, et non à un
« crop » ou une réduction de l'image comme dans le processus de RT.
Cette limitation imposée par la fonction Gaussienne amène plusieurs
conséquences :

- Le traitement a été décalé de sa place dédiée – qui aurait du être
  proche de « Lab adjustements » - vers le début du processus de RT –
  qui est obligatoirement (sauf si quelqu'un a une idée pour faire
  autrement) un process Raw. Ceci a pour conséquence que les fichiers
  non raw (TIF, JPG, etc.) ne peuvent être traités par cet algorithme.Ce
  problème va probablement être résolu prochainement (novembre 2015 ??).
- La deuxième conséquence de ce positionnement est que les
  caractéristiques des données Raw situées juste après interpolation
  (demosaicing) sont très différentes de celles situées en aval : pas de
  gamma, pas de limitation de gamut, par de balance des blancs, pas de
  conversion RGB....donc il faut s'attendre à des artefacts et des
  rendus luminance et couleurs peu performants.
- La troisième conséquence est le temps de réponse du système qui impose
  à chaque changement de réglages de réactualiser l'ensemble du
  processus.
- La quatrième, dans certains cas, amènera la retouche du point blanc,
  afin d'éviter les distorsions de couleurs (ex : ciel magenta)
- Mais, avantage, ce process étant situé avant "Denoise", le traitement
  du bruit sera ici pleinement efficace.

Néanmoins, malgré ces handicaps, comme nous le verrons plus loin, les
résultats sont plus que satisfaisants aussi bien en temps de traitement
que en rendu des contrastes et couleurs notamment en conjurant l'action
de Retinex avec celle de Ondelettes.

# Le principe de l'algorithme

Pour de plus amples informations, lire les documents « pdf » situés en
généralités.

## Élaborer un fichier « transmission map » obtenu

- en faisant la différence, pour la luminance seulement, entre le
  logarithme de chaque pixel de l'image originale et le logarithme de la
  gaussienne correspondante des pixels voisins. L'écart-type (fonction
  gaussienne) ici utilisé est très élevé – usuellement dans RT des
  valeurs de sigma de 0.5 à 5 sont courantes – ici les valeurs se
  situent entre 10 et 280 (Single Scale Retinex) -au choix de
  l'utilisateur.
- en modifiant la distribution des luminances de l'image source par : a)
  l'application d'un gamma avant la création du fichier 'Transmission
  Map'; b) l'application d'un gamma inverse pour restaurer les
  caractéristiques de l'image source. Cette modification de la
  distribution permet : 1) de changer la tonalité de l'image ; 2)
  modifier le fichier "Transmission map" pour prendre en compte par
  exemple les zones sur ou sous exposées.
- en appliquant plusieurs fois (scale) – 3 fois , non modifiable par
  l'utilisateur - cet algorithme avec une sommation à partir de
  coefficients empiriques (Multi Scale Retinex). (De faibles valeurs de
  scale accroissent le contraste apparent, mais donnent à l'image un
  aspect perspective, de fortes valeurs rendent l'image plus naturelle,
  mais ont tendance à accroître le bruit.)
- en faisant varier au choix de l'utilisateur, MSR en fonction de
  l'effet souhaité (Uniforme, Bas, Haut, Highlight) :
  - Uniforme : tend à traiter les intensités faibles et les intensités
    fortes de manière équilibrée.
  - Bas : améliore les zones de faibles intensités
  - Haut : améliore le rendu des zones les plus claires
  - Highlight : améliore le rendu des zones très claires qui peuvent
    conduire à des teintes magenta, mais peut amener de forts artefacts.

<!-- -->

- en choisissant un espace de travail :
  - L\*a\*b\* logarithmique
  - HSL Logarithmique
  - HSL linéaire - cette version non "conforme" aux algorithmes
    "Retinex" permet dans certains cas un traitement plus approprié des
    images

On obtient ainsi une distribution logarithmique (Transmission Map) -
sauf en mode linéaire ! - qu'on pourra ensuite « retrancher » de l'image
originale, pour obtenir une image en théorie dépourvue de brume ou
d'effet de voile ou obtenir des effets spéciaux. Cette distribution a
approximativement une représentation gaussienne, avec un minimum (minT)
aux alentours, selon les images - plus élevées pour les images avec
voile - de -10 à -40, une moyenne proche de -1 à +2, un écart-type
souvent aux environs de 2 à 6, et un maximum (maxT) aux alentours de 10
à 40. Les valeurs négatives traduisent les faibles intensités et les
positives les fortes intensités. Attention ces valeurs sont des
coefficients logarithmiques qui traduisent de très fortes valeurs (log
1000 = 6.9) (exp 10 \# 22000)...(exp 20) \# 500.000.000 En théorie, il
faudrait utiliser de fortes valeurs de « scale » et de Gaussienne dans
les zones proches de l'objectif (celles où l'incidence du voile est plus
faible) et de faibles valeurs dans les zones distantes (celles où
l'incidence du voile est forte).

## Traiter le masque issu du traitement Gaussien

Le fichier "Transmission map" correspond à un traitement récursif de :

- l'image source - image originale qui a subi diverses modifications par
  l’égaliseur d'histogramme et le gamma
- des fichiers "masque" directement issus du traitement Gaussien (scale,
  radius, méthode low...high...)

## Type d'affichage "masques"

Traiter les fichiers "masques" (l'idée m'est venue en observant le
plugin de Russell Cottrell) va permettre de réduire les halos et
artefacts. J'ai ajouté une "combobox" qui permet de choisir le type
d'affichage. Celui-ci est à la fois un dispositif pédagogique et
également une assistance pour trouver les "bons" réglages.

- Process:
  - Standard : c'est le réglage par défaut.
  - Mask : affiche le masque obtenu par l'algorithme Retinex, issu du
    traitement Gaussien. Ici on verra les incidences:
    - des différents réglages situés en amont : méthode (low, uniform,
      high et highlight), radius, gamma, histogram equalizer. Par contre
      les autres réglages situés en aval n'ont pas d'incidences sur cet
      affichage : contrast, gain, brightness, threshold ainsi que la
      courbe "Transmission map"
    - des différents réglages du "Mask equalizer".
    - vous pouvez exporter ces réglages (TIFF/JPG) pour utiliser ce
      masque dans des logiciels externes (Gimp, Photoshop).
  - Unsharp mask : vous pouvez utiliser cette option afin de retrancher
    le mask à l'image originale. Dans ce cas l'action sur "strength"
    permettra de doser la combinaison entre l'image originale et le
    masque. On obtient ainsi la possibilité d'images avec de très hautes
    valeurs de rayons.
  - Transmission : affiche une "image" du fichier "Transmission map".
    - Cette "image" ne correspond pas à la réalité qui elle correspond à
      une échelle logarithmique dont les valeurs sont généralement
      situées entre -30 et + 30.
    - (fixed) Afin de rendre "visible" ces valeurs j'ai appliqué 2
      coefficients arbitraires - j'ai évité le calcul automatique afin
      de permettre des comparaisons - qui décalent et amplifient les
      valeurs de base;
    - (auto) Ici j'utilise les valeurs affichées dans le Preview (TM Min
      Max Mean Sigma) pour élaborer un fichier dont les valeurs se
      situent entre 0 et 32700. Bien sûr ces données deviennent visibles
      avec le maximum d'amplitude, mais ne correspondent pas à la
      réalité. Cette configuration peut selon les images être préférable
      à "(fixed)".
    - L'image affichée prend en compte l'ensemble des traitements
      Retinex, sauf : a) le "median filter"; b)le "Gain"; c)
      "Brightness" (offset); c) et bien sûr "Strength".
    - Vous pouvez agir sur les différents réglages notamment ceux du
      "Mask equalizer" et aussi la courbe "Transmission map" et voir
      ainsi directement les actions sur le halo, les artefacts et les
      contrastes.

## Méthodes d'action sur les masques

J'ai mis en place 3 méthodes :

- une courbe diagonale qui agit directement sur le contraste des
  fichiers "masque" récursif. Attention cette courbe est très sensible
  et peut amener d'importants artefacts. Par contre elle n'a pas, ou
  peu, d'incidences sur les temps de traitement.Vous pouvez utiliser
  cette courbe de façon isolée ou combinée avec les autres méthodes
- un traitement Gaussien est appliqué aux masques. Vous pouvez agir sur
  les ombres, les hautes lumières et le rayon. L'accroissement des temps
  de traitement est "raisonnable"
- un traitement "wavelet" (Sharp mask) est appliqué aux masques. Vous
  pouvez agir sur les ombres et les hautes lumières. L'accroissement des
  temps de traitement est important ou très important selon la méthode
  choisie (partielle ou totale).

## Traiter le fichier « Transmission map »

<img src="/images/TMap.jpg" title="TMap.jpg" width="200" alt="TMap.jpg" />

Le traitement de base principal consiste à partir de la moyenne et de
l'écart-type de « transmission map » à appliquer une transformation de
type :

- newT = (oldT – mini) / maxi-mini.
- avec mini = moyenne – k \* écart-type
- avec maxi = moyenne + k \* écart-type

Le choix de k – contraste (variance) : accessible à l'utilisateur - est
déterminant dans le rendu de l'image : de faibles valeurs vont accroître
le contraste apparent, de fortes valeurs vont rendre l'image plus
naturelle avec moins d'artefacts et halos.

J'ai ajouté trois composantes à ce traitement de base :

- Un seuil – accessible à l'utilisateur – qui va permettre de réduire
  les valeurs maximum (maxT) et minimum (minT) en intégrant les valeurs
  écrêtées à la nouvelle distribution. Par exemple si le seuil choisi
  est 10, toutes les valeurs inférieures à -10 deviendront -10, toutes
  les valeurs supérieures à +10 deviendront +10. Cette action va
  accroître les contrastes, mais peut amener des artefacts.
- Une courbe (flatcurve) – accessible à l'utilisateur – pour agir
  directement sur la distribution, en remplaçant la théorie par la
  pratique...C'est en agissant sur la distribution que l'utilisateur
  pourra par exemple réduire les valeurs négatives et accroître les
  positives, (ou l'inverse) pour améliorer le rendu en temps réel.
- Un median 3x3 – accessible à l'utilisateur – qui agit sur les
  irrégularités de la distribution, afin de réduire les artefacts

## Élaborer le fichier « Image Haze-free »

<img src="/images/Hazefree.jpg" title="Hazefree.jpg" width="200"
alt="Hazefree.jpg" /> Ce fichier s'obtient par "différence" entre
l'image source et le fichier "Transmission map".

On utilisera ici deux paramètres supplémentaires, Gain et Brightness
(Offset) : Ces 2 paramètres vont permettre d'intégrer le fichier «
Transmission map » à une image exploitable. En effet sans précautions,
l'image restaurée peut se situer complètement en dehors des limites
habituelles de luminance, comprises entre 0 et 32768.

- « Gain » va jouer sur l'amplitude globale en la réduisant ou
  l'accroissant et par exemple réduire le nombre de pixels complètement
  noirs.
- "Brightness" (« Offset ») va permettre de rétablir la luminance après
  l'action de "gain"

Afin d'apporter une aide à l'utilisateur, j'ai intégré au GUI un
affichage des valeurs minimum de l'image « haze-free ». On peut agir sur
« Gain » et « Brightness (Offset) », mais également sur tous les autres
paramètres notamment ; « contraste » (variance) et la courbe «
transmission map ». L'idéal est d'amener les valeurs Min au plus proche
de 0, et Max au plus proche de 32768, par exemple une image "originale"
avec min=-44230 et max=76000 pourra devenir min=32 max=32500. Bien sûr
rien n'interdit des valeurs différentes, mais dans tous les cas ces
valeurs seront "clipées" et ramenées à 0..32768, on aura perdu la
richesse du fichier "Transmission map"!!.

- Légende des sigles et labels utilisés au niveau GUI pour "faciliter"
  l'utilisation :
  - Restored haze-free Min=-5681 Max=34568 : affiche les valeurs
    minimales et maximales de l'image "Sans voile" avant d'être
    clippées.
  - TM Min=-3.8 Max=4.1 Mean=0.1 Sigma=3.3 : Tansmission Map -- Min et
    Max correspondent au calcul suivant Min=Mean - Sigma \* Variance /
    100 ; Max=Mean + Sigma \* Variance / 100
  - TM Tm=-6.5 TM=11.8 : Transmission Map -- Tm valeur minimale de la
    distribution; TM valeur maximale de la distribution.

Il est évident qu'un affichage dans le GUI : a) de la distribution
"Transmission Map" ainsi que, b) des valeurs des données de l'image
"Haze-free", rendrait plus faciles à la fois la compréhension du système
et l'ergonomie d'utilisation...mais cela reste à mettre au point ???

## Retinex versus Tone-mapping

Il existe plusieurs manières (selon les sources spécialisées en ce
domaine) d'adapter l'algorithme Retinex à un rendu "Tone-mapping".
L'examen du code en place, ma compréhension du problème,... m'ont
conduit à la solution suivante:

- Procéder à plusieurs itérations du code spécifique "Retinex".
  J'appelle code spécifique la partie excluant:
  - les conversions RGB==\>L\*a\*b\* ou RGB==\>HSL (et réciproquement).
  - l'égaliseur d'histogramme.
  - le gamma différentiel (low, middle, high, free).
  - de même ne sont pas concernés les choix faits avec la méthode "Low",
    "Uniform", "High", "Highlight"
- Ces itérations accroissent évidemment le temps de traitement, jusque
  2.5 fois pour 5 itérations.

Vous pouvez opter pour plusieurs manières de réaliser les itérations en
jouant sur 3 facteurs que j'ai appelé "Gradient"

- "Gaussian gradient" qui agit sur: a) le sigma du flou gaussien (Radius
  ou Neighboring pixels); b) le facteur "scale" (qui par défaut est fixé
  à 3).
- "Transmission gradient" qui agit sur: a) le contraste (variance); b)le
  seuil (threshold) qui limite le fichier "Transmission Map"
- "Strength gradient" qui agit sur "Strength", c'est-à-dire la
  combinaison de l'image "Haze-free" avec l'image originale.

Si vous réglez les 3 gradients à 0, toutes les itérations seront
identiques au processus de base.

Incidences de chaque gradient :

- "Gaussian gradient" : selon l'itération "it", la valeur de Radius
  ("Neighboring pixels") est divisée par "grad" et la valeur de "scale"
  devient:
  - Gg 1 :
    - it=1 grad=1; it=2 grad=1.25;it=3 grad=1.5;it=4 grad=1.75;it=5
      grad=2
    - it=1 scal=4; it=2 scal=3; it=3 scal=3; it=4 scal=3; it=5 scal=2
  - Gg 2 :
    - it=1 grad=1; it=2 grad=1.50;it=3 grad=2.0;it=4 grad=2.50;it=5
      grad=3
    - it=1 scal=5; it=2 scal=4; it=3 scal=3; it=4 scal=2; it=5 sca=2
  - Gg 3 :
    - it=1 grad=1; it=2 grad=1.66;it=3 grad=2.3;it=4 grad=3.00;it=5
      grad=3.6
    - it=1 scal=5; it=2 scal=4; it=3 scal=3; it=4 scal=2; it=5 scal=2
  - Gg 4 :
    - it=1 grad=1; it=2 grad=1.80;it=3 grad=2.6;it=4 grad=3.40;it=5
      grad=4.2
    - it=1 scal=5; it=2 scal=4; it=3 scal=3; it=4 scal=2; it=5 scal=2
  - Gg 5 :
    - it=1 grad=1; it=2 grad=3.50;it=3 grad=6.0;it=4 grad=8.5;it=5
      grad=11.0
    - it=1 scal=5; it=2 scal=4; it=3 scal=3; it=4 scal=2; it=5 scal=2
  - Gg 6 :
    - it=1 grad=1; it=2 grad=6.00;it=3 grad=11.0;it=4 grad=16.0;it=5
      grad=21.0
    - it=1 scal=5; it=2 scal=4; it=3 scal=3; it=4 scal=2; it=5 scal=2
  - Gg-1 :
    - it=1 grad=1; it=2 grad=0.875;it=3 grad=0.75;it=4 grad=0.50;it=5
      grad=0.37
    - it=1 scal=3; it=2 scal=3; it=3 scal=3; it=4 scal=3; it=5 scal=3

Pour Gg 5 et Gg 6, il est tenu compte de la méthode choisie, si celle-ci
est "highlight", les valeurs de 'grad' sont amplifiées en fonction de
"Highlight Threshold"

- "Transmission gradient" : selon l'itération "it" le contraste
  (variance) et le seuil (threshold) sont multipliés par "var":
  - Tg 1: it=1 var=1; it=2 var=0.875; it=3 var=0.75; it=4 var=0.625;
    it=5 var=0.5
  - Tg 2: it=1 var=1; it=2 var=0.800; it=3 var=0.60; it=4 var=0.400;
    it=5 var=0.2
  - Tg-1: it=1 var=1; it=2 var=1.125; it=3 var=1.25; it=4 var=1.375;
    it=5 var=1.5
  - Tg-2: it=1 var=1; it=2 var=1.400; it=3 var=1.80; it=4 var=2.200;
    it=5 var=2.6

<!-- -->

- "Strength gradient" : selon l'itération "it" la force "strength" est
  multipliée par "s":
  - Sg 1 : it=1 s=1.30; it=2 s=1; it=3 s=0.70; it=4 s=0.5; it=5 s=0.5
  - Sg 2 : it=1 s=1.60; it=2 s=1; it=3 s=0.40; it=4 s=0.3; it=5 s=0.3
  - Sg-1 : it=1 s=0.80; it=2 s=1; it=3 s=1.20; it=4 s=1.2; it=5 s=1.2
  - Sg-2 : it=1 s=0.60; it=2 s=1; it=3 s=1.40; it=4 s=1.5; it=5 s=1.5

Remarque : L'égaliseur de teinte (Hue equalizer) et le "Transmission
median filter" ne sont appliqués qu'une seule fois quelque soit le
nombre d'itérations.

# Les différents réglages

## Réglages accessibles dans tous les cas

Vous disposez de 5 réglages :

- Retinex method : avec "Low" "Uniform" "High" "Highlight"
  - Low :améliore les zones de faibles intensités
  - Uniforme : tend à traiter les intensités faibles et les intensités
    fortes de manière équilibrée.
  - High : améliore le rendu des zones les plus claires
  - Highlight : améliore le rendu des zones très claires qui peuvent
    conduire à des teintes magenta (attention aux artefacts).

Ces 4 méthodes agissent directement sur le fichier "Transmission Map"

- Espace
  - L\*a\*b\*
  - HSL Log
  - HSL Lin

Le choix entre ces 3 espaces dépend de l'image...Les 2 premiers sont
"conformes" aux algorithmes Retinex

- Strength : combine l'image "Haze-free" avec l'image originale.
  Strength=0 n'apporte aucun traitement "Retinex" à l'image.
  Strength=100 amène un traitement total, seule l'image "Haze-free" est
  affichée. Des valeurs inférieures à 50 sont recommandées.

<!-- -->

- Chroma (patch): agit sur la composante couleur en utilisant
  l'algorithme Retinex en pourcentage de la valeur de "strength"
  relative à la Luminance. Le curseur exécute un processus Retinex dédié
  à la composante couleur en "simplifiant" le processus - les
  composantes spécifiques luminance - gamma, Luminance, masque Gaussien,
  ... - ne sont pas exécutées. Attention, les temps de traitement sont
  doublés et les appels en mémoire supplémentaire conséquents.

<!-- -->

- Radius (Neigboring pixels) : prend en compte les pixels voisins par un
  algorithme "Différence de Gaussien", plus les valeurs sont fortes,
  plus l'avant plan sera affecté. Plus les valeurs sont faibles plus les
  zones distantes seront affectées. Agit directement sur le fichier
  "Transmission Map"

<!-- -->

- Highlight threshold : uniquement accessible avec la méthode
  'Highlight'; règle le seuil de la méthode 'Highlight', une valeur de 1
  donnera sensiblement les mêmes effets que la méthode 'High', des
  valeurs élevées devraient permettre de réduire les couleurs magenta
  des zones surexposées. Attention il sera probablement nécessaire de :
  - changer les réglages en particulier 'Radius' ('Neighboring pixels')
  - accroître la valeur de 'Raw white point' dans le cas de teintes
    magentas dans les zones surexposées.
  - utiliser 'Hue equalizer' dans le cas de teintes magentas dans les
    zones surexposées.
  - agir sur "Gamma Retinex"

<!-- -->

- Contraste (Variance) : ce coefficient pondère la moyenne et
  l'écart-type de "Transmission map". C'est un facteur clef de rendu de
  l'image. Il agit sur les seuils haut et bas de contraste du fichier
  "Transmission Map", plus les valeurs sont faibles plus l'image sera
  contrastée, plus les valeurs sont élevées plus l'image sera naturelle
  et les artefacts réduits. Ce contraste (variance) n'agit pas sur le
  fichier "Transmission Map", mais permet le calcul de l'image
  Haze-free.

## Réglages accessibles avec "Setting"

- Gamma retinex : avec 4 choix "Low", "Middle", "High" et "Free" qui
  permet de choisir le gamma et la pente (slope), d'un gamma appliqué
  avant l'algorithme retinex, et d'un gamma inverse appliqué juste après
  reconstruction de l'image. Des valeurs élevées de gamma associées à de
  faibles valeurs de pente (slope) peuvent conduire à des artefacts.
  L'utilisation est fonction des images, de l'espace L\*a\*b\* ou HSL,
  des réglages utilisés...et des effets souhaités.
- Histogram Equalizer:Cette courbe est un pis-aller...car elle vise à
  elle seule à rétablir, le gamma, la conversion RGB, le profil input
  icc, la balance des blancs...dont le manque est du à la position de
  "Retinex" dans le process, qui est placée en Raw afin de travailler
  sur l'image complète. En l'absence de cette courbe, les données de
  "Transmission Map" sont généralement mauvaises et amènent d'important
  artefacts. A noter que l'interface prévoit 2 courbes différentes pour
  L\*a\*b\* et HSL. Par défaut cette courbe est sans action, mais en
  mode L\*a\*b\*, il est quasi indispensable d'affaiblir l'action du
  premier quart (à régler par l'utilisateur) et affaiblir les valeurs
  élevées, afin de réduire artefacts et halos. C'est l'expérience qui
  guidera l'utilisateur.
- Hue equalizer : Cette courbe va permettre :
  - de moduler l'action de Retinex en fonction de la teinte, par exemple
    affaiblir un ciel, renforcer un feuillage,...
  - de réduire l'action dans le cas de zones surexposées de teinte
    magenta.
  - à noter que lorsque la méthode 'highlight' est sélectionnée, cette
    courbe agit également sur la chroma de l'image finale

Ces 3 réglages (Gamma Retinex, Histogram Equalizer,Hue equalizer),
n'agissent pas directement sur le fichier "Transmission map", mais
modifient sa valeur d'origine.

- Gain et Brightness (Offset): Utilisés en conjugaison, ils permettent
  de positionner correctement l'image "haze-free". Vous pouvez vous
  aider des information contenues dans le GUI, et situer Min proche de
  zéro et Max proche de 32768. Gain et Offset agissent sur l'image
  "Haze-free" et sont sans action sur le fichier "Transmission Map"

<!-- -->

- Threshold : ce coefficient agit sur les valeurs maximales et minimales
  de "Transmission map"

<!-- -->

- Transmission Map : cette courbe permet d'interagir avec le fichier
  "Transmission map", l'abscisse de la courbe représente la base de
  distribution de "Transmission map" (MinT, moyenne \[mean\] , MaxT).
  Abaisser la partie gauche va réduire les valeurs minimales (celles
  relatives à l'avant plan) et réciproquement, abaisser la partie droite
  va réduire les valeurs maximales (celles relatives à l'arrière plan)
  et réciproquement. Cette courbe est un point clef de régulation de la
  qualité perçue de l'image.

<!-- -->

- Transmission median filter : réduit les artefacts dus aux trop fortes
  variations locales de "Transmission map"

J'ai ajouté une "combobox" qui permet de choisir le type d'affichage.
Celui-ci est à la fois un dispositif pédagogique et également une
assistance pour trouver les "bons" réglages.

- Process (preview):
  - Standard : c'est le réglage par défaut.
  - Mask : affiche le masque obtenu par l'algorithme Retinex, issu du
    traitement Gaussien. Ici on verra les incidences:
    - des différents réglages situés en amont : méthode (low, uniform,
      high et highlight), radius, gamma, histogram equalizer. Par contre
      les autres réglages situés en aval n'ont pas d'incidences sur cet
      affichage : contrast, gain, brightness, threshold ainsi que la
      courbe "Transmission map"
    - des différents réglages du "Mask equalizer".
    - vous pouvez exporter ces réglages (TIFF/JPG) pour utiliser ce
      masque dans des logiciels externes (Gimp, Photoshop).
  - Unsharp mask : vous pouvez utiliser cette option afin de retrancher
    le mask à l'image originale. Dans ce cas l'action sur "strength"
    permettra de doser la combinaison entre l'image originale et le
    masque. On obtient ainsi la possibilité d'images avec de très hautes
    valeurs de rayons.
  - Transmission : affiche une "image" du fichier "Transmission map".
    - Cette "image" ne correspond pas à la réalité qui elle correspond à
      une échelle logarithmique dont les valeurs sont généralement
      situées entre -30 et + 30.
    - (fixed) Afin de rendre "visible" ces valeurs j'ai appliqué 2
      coefficients arbitraires - j'ai évité le calcul automatique afin
      de permettre des comparaisons - qui décalent et amplifient les
      valeurs de base;
    - (auto) Ici j'utilise les valeurs affichées dans le Preview (TM Min
      Max Mean Sigma) pour élaborer un fichier dont les valeurs se
      situent entre 0 et 32700. Bien sûr ces données deviennent visibles
      avec le maximum d'amplitude, mais ne correspondent pas à la
      réalité. Cette configuration peut selon les images être préférable
      à "(fixed)".
    - L'image affichée prend en compte l'ensemble des traitements
      Retinex, sauf : a) le "median filter"; b)le "Gain"; c)
      "Brightness" (offset); c) et bien sûr "Strength".
    - Vous pouvez agir sur les différents réglages notamment ceux du
      "Mask equalizer" et aussi la courbe "Transmission map" et voir
      ainsi directement les actions sur le halo, les artefacts et les
      contrastes.

## Synthèse pratique des différents réglages

| Réglage                                | Fonctionnalité principale                                                                                                   | Fonctionnalité complémentaire - remarque                                                  |
|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| Strength                               | Combine l'action de l'image Retinex avec l'originale                                                                        | Aucune incidence sur le traitement Retinex                                                |
| Method : Low,Uniforme, High, highlight | Différencie l'action selon l'intensité de la luminance (low = faible intensité, highlight = peut réduire artefacts colorés) | Plus les valeurs sont fortes, plus l'avant plan est concerné (high favorise l'avant plan) |
| Radius                                 | Valeurs fortes pour avant-plan, valeurs faibles arrière-plan                                                                | Valeurs fortes peuvent générer des artefacts                                              |
| Contrast                               | Valeurs faibles, accroît le contraste général, favorise avant-plan, génère artefacts                                        | Valeurs fortes, réduisent les artefacts                                                   |
| Threshold                              | Valeurs faibles, accroît le contraste général, accroît les artefacts de transition                                          | Valeurs faibles, réduit les artefacts arrière plan                                        |
| Courbe Transmission-map                | Partie gauche agit sur l'avant-plan, partie droite sur arrière-plan                                                         | Déplacer le point median agit sur le contraste et les artefacts                           |
| Gain et Brightness                     | Positionne Retinex par rapport à l'image source (voir Seetings - restored haze-free)                                        | Peut donner l'illusion d'agir sur le contraste et la luminosité                           |
|                                        |                                                                                                                             |                                                                                           |

Synthèse des effets des principaux réglages sur le contraste

| Réglage                      | Fonctionnalité principale                                                         | Fonctionnalité complémentaire - remarque                        |
|------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------|
| Gaussian-mask et Sharp-mask  | Réduit les artefacts dues aux trop importants contrastes locaux                   | Les valeurs importantes réduisent l'action de Retinex           |
| Method L\*a\*b\* - HSL -...  | Changent la répartition initiale de la luminance, permet de réduire les artefacts | L\*a\*b\* semble plus adapté aux images avec fortes expositions |
| Gamma et Histogram equalizer | Changent la répartition initiale de la luminance, pour réduire les artefacts      | Gamma est compensé par son inverse en fin de traitement Retinex |
|                              |                                                                                   |                                                                 |

Synthèse des autres réglages

# Utilisation en conjugaison avec Niveaux d'Ondelettes et 'Lab adjustements'

Dans le cas d'images avec voile atmosphérique, le rétablissement du
contraste avec l'algorithme Retinex :

- est quelquefois insuffisant - ou accompagné d'artefacts si "strength"
  est trop élevé ;
- se traduit par une insuffisance de chroma, et d'accentuation.

Plusieurs solutions peuvent être mise en œuvre notamment :

- accroitre la chroma par L\*a\*b\* adjustements (curseur chroma ou
  courbe C/C ou courbe a\* = f(a\*) et b\* = f(b\*);
- ajuster le contraste global par L\*a\*b\* adjustement (courbe L)
- accroitre la chroma par l'image résiduelle de wavelet ;
- bien sûr il est possible d'utiliser d'autres contrôles de Rawtherapee,
  notamment dans le volet "Exposure"

Mais je pense que privilégier l'outil Wavelet est un choix pertinent -
notamment pour les images avec voile atmosphérique : On pourra en plus
des réglages cités ci-dessus:

- accroitre le contraste de l'image résiduelle;
- utiliser la méthode de compression "contrast" en baissant "compression
  strength" et ajustant "gamma"
- accroitre modérément "Edge sharpness" avec "edge detection"
- utiliser "Final touchup", en particulier : "Final local contrast",
  "Fina contrast curve" et éventuellement (effet Tone-Mapping") ,
  "Contrast balance method"

# Un exemple possible - Dehaze - quelques recommandations

Afin de mieux expliciter le processus de traitement utilisant Retinex,
je vais prendre appui sur une image difficile, particulièrement brumeuse
et emprunte de voile atmosphérique.
[Madeira](http://rawtherapee.com/shared/test_images/madeira.dng)

Attention ce traitement vise un but pédagogique et en aucun cas, ne vise
l'obtention d'une image "parfaite" ! (c'est quoi d'ailleurs et emprunt
de subjectivité). L'utilisateur aura tout loisir de procéder à des
changements, modifications pour obtenir le rendu qu'il souhaite.

## Premiers réglages Retinex

- Au démarrage (afin d'obtenir les mêmes informations) : après avoir
  appliqué Profiles "Neutral", choisir "Bundle profiles" =\> "Default".

<!-- -->

- Activer "Retinex" ...et rien d'autre.

Pour avoir une synthèse de l'action des différents opérateurs
[\#Synthèse pratique des différents
réglages](#Synthèse_pratique_des_différents_réglages.md)

Sur une image de ce type, où le voile est présent dans l'avant plan et
l'arrière plan et avec un histogramme assez bien réparti, je prends
l'option de choisir:

- Method : Uniform
- L\*a\*b\* : car celle-ci est la plus performante des 3 (Lab, HSL - Log
  et HSL Lin)

Puis je choisis, pour "Radius", "Contrast" et "Strength", les réglages
par défaut soit respectivement 80, 200 et 20

### Réglages Transmission map - itérations avec Radius, contrast, scale

<img src="/images/TMap.jpg" title="TMap.jpg" width="300" alt="TMap.jpg" />
L'étape suivante consiste à examiner dans la rubrique "settings",
l'indicateur qui traduit partiellement l'optimisation de Retinex le
fichier "Transmission-map", c'est à dire "Restore haze-free". Vous
pouvez si vous le souhaitez visualiser le fichier "Transmission-map"
(Process Transmission fixed")

On voit apparaître les valeurs : Min=-5799 Max=14069., ainsi que
d'autres valeurs TM min =-9.8, Max=7.7 Mean=8.8 Sigma=4.4 Tm=-13.1
TM=20.7

Intéressons nous aux deux valeurs Min=-5799 et Max=14069. Ceci revient à
dire que l'image correspondant à ces valeurs qui sera soustraite de
l'image initiale, ne correspond pas du tout aux valeurs habituelles de
luminance qui sont rappelons le en L\*a\*b\* dans Rawtherapee entre 0 et
32768. Le premier travail va être d'utiliser la courbe "Transmission -
map" pour obtenir des valeurs plus pertinentes. Attention l'objectif
n'est pas d'obtenir Min = 0 et Max = 32768, mais des valeurs plus
raisonnables. Par exemple, il est possible d'abaisser un peu la partie
gauche de la courbe et relever un peu la partie centrale. On aboutit par
exemple aux réglages suivants
:[Media:madeira-first.pp3](media:madeira-first.pp3)

#### L'image Haze-free

<img src="/images/Hazefree.jpg" title="Hazefree.jpg" width="300"
alt="Hazefree.jpg" /> Pour l'instant je ne modifie pas les valeurs qui
peuvent influer sur "Transmission - map", comme "radius", "contrast".

Ensuite, je vais essayer par une démarche itérative, entre "Gain
transmission" + "offset" et "radius", "contrast" et "scale" :

- agir sur la courbe "Gain transmission" et "offset" afin d'obtenir des
  valeurs Min et Max proches de 0 et 32768, mais -400 et +39000 peuvent
  convenir..
- et agir ensuite sur "radius", "contrast", "scale" pour obtenir une
  image plaisante à l’œil, suffisamment contrastée, mais sans trop
  d'effets de relief...ici c'est affaire de goût.
- procéder par itérations

J'ai arbitrairement choisi les valeurs suivantes reprises dans le pp3
[Media:madeira-second.pp3](media:madeira-second.pp3)

### Appliquer un masque Gaussien et un gamma

Ces deux outils permettent de modifier la répartition de l'action entre
hautes et basses lumières

- choisissez "Mask Method" = Gaussian mask et augmentez hihlight = 23
  pour mieux éclaircir le ciel, vous pouvez vous servir de l'option
  "mask" pour visualiser les corrections.
- positionnez "Gamma" dans "settings" sur "Low"

Là encore, tout est affaire de goût.

On aboutit par exemple aux réglages suivants
:[Media:madeira-third.pp3](media:madeira-third.pp3)

## Agir sur la chroma

Trois cas :

- dans la version "Retinex en début de processus" il n'y a pas d'action
  Retinex sur la chroma. Vous pouvez utiliser l'outil "Lab ajustements"
  et agir soit sur le curseur "Chromaticity", soit sur les 2 courbes
  a\*=f(a\*) et b\*=f(b\*), soit sur la courbe C=f(C) plus intuitive.
- dans la version "patch" disponible dans la branche "waveletnew", vous
  avez accès à un curseur "chroma" pour "Retinex en début de processus"
- dans la version "Retinex in Wavelet", agir sur le curseur Chroma dans
  Wavelet

On aboutit aux réglages
suivants:[Media:madeira-four.pp3](media:madeira-four.pp3)

## Accroître les contrastes et réduire encore le voile atmosphérique - Wavelet

- accroître légèrement le contraste avec "contrast levels"
- dans "Residual image", accroissez contraste et chroma (contrast = 25,
  chroma = 22), puis choisissez "Compression method" = "Tone mapping" et
  réduisez compression strength = -0.29
- dans "Final Touchup", choisissez "Contraste balance" sélectionnez
  "slider" et réglez "Contrast balance d/v-h" à 19
- activez "chroma balance"

Vous aboutissez aux réglages suivants
:[Media:madeira-five.pp3](media:madeira-five.pp3)

## Réglage final

Vous pouvez si nécessaire :

- ajuster "strength" dans Retinex
- agir dans wavelet sur "Final contrast" et/ou "after contrast curve"
- ainsi que tous les autres réglages habituels

Vous aboutissez aux réglages suivants :
[Media:madeira-six.pp3](media:madeira-six.pp3)
