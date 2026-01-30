---
title: Toolchain Pipeline
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'General Information'
---

<div class="pagetitle">

Succession des outils dans le Pipeline - Colorimétrie générale

</div>

## Succession des outils dans le Pipeline

### Ordre des traitements

Tous les traitements apportés à une image, depuis le moment où vous
ouvrez le fichier jusqu'au moment où il est affiché sur l'écran ou
enregistré interviennent dans un ordre imposé. Les données migrent d'un
module dans l'autre, c'est ce qu'on appelle la succession des outils
dans le pipeline. RawTherapee contient 4 pipelines (un pour l'aperçu
principal, un pour l'image enregistrée, un pour la vignette et un
dernier qui m'échappe). La liste suivante présente un ordre simplifié
des opérations :

1.  Prétraitement
    1.  Trame Noire
    2.  Champ Uniforme
    3.  Mauvais pixels
    4.  Pixels chauds
    5.  Étalonnage des couleurs (interne, pas d'outil dans l'interface)
    6.  Points Noir Raw
    7.  Correction de distorsion d'objectif
    8.  Équilibrage du vert
    9.  Filtre du bruit de ligne
    10. Correction de l'aberration chromatique
    11. Points Blanc Raw
    12. Histogramme raw
    13. Préparation de l'exposition auto
2.  Dématriçage
3.  Retinex
4.  Reconstruction des hautes lumières
5.  Balance des blancs
6.  Suppression des spots
7.  Recadrage
8.  Conversion d'espace colorimétrique
9.  Noise reduction
10. Elimination de la brume
11. Compression de Plage Dynamique
12. (branche local ajustements) évitement du décalage de couleurs, Log
    encoding, flou et bruit, réduction de bruit, netteté, dehaze et
    Retinex, cbdl, vibrance, lumière douce, contraste local, wavelet,
    exposition, couleur et lumière, Color apperance (Cam16 & Jzczhz),
    évitement du décalage de couleurs
13. Courbe tonale auto-adaptée
14. Courbe de réponse tonale
15. Procédé RVB
    1.  Mixage des canaux
    2.  Courbe tonale
    3.  Hautes lumières
    4.  Ombres
    5.  Courbes RVB
    6.  Courbes TSV
    7.  Virage partiel
    8.  Simulation de film
    9.  Noir-et-blanc
    10. Grille de correction de la couleur L\*a\*b\* (Lab)
16. Procédé Lab
    1.  Ombres/hautes lumières (Lab)
    2.  Contraste local (Lab)
    3.  Ajustements Lab
    4.  Vibrance
    5.  Grille de correction couleur L\*a\*b\* (Lab)
    6.  Filtre vignettage
    7.  Filtre dégradé
    8.  Compression tonale
    9.  Réduction du bruit d'impulsion
    10. Aberration chromatique
    11. Bordures
    12. Microcontraste
    13. Netteté
    14. Contraste par niveaux de détail
    15. Ondelettes
    16. Lumière douce
    17. Abstract Profile
    18. CIECAM02
    19. Redimensionnement
    20. Netteté après redimensionnement
17. Conversion Lab -\> RVB finale

### Liste de tous les outils de RawTherapee

- Générique/Aperçu principal
  - Profil d'entrée
  - Profil du moniteur couleur
  - Profil de travail
  - Profil de sortie
  - Indications hors domaine
  - Aperçus Rouge/Vert/Bleu/Luminosité/Masque du focus
  - Intention colorimétrique
- Onglet Exposition
  - Exposition
  - Ombres/Hautes lumières
  - Compression tonale
  - Compression de Plage Dynamique
  - Filtre Vignettage
  - Filtre dégradé
  - Ajustements Lab
- Onglet Détail
  - Netteté
  - Contraste local
  - Bords
  - Microcontraste
  - Réduction du bruit d'implusion
  - Réduction de bruit
  - Aberration chromatique
  - Contraste par niveaux de détail
  - Elimination de la brume
- Onglet Couleur
  - Balance des blancs
  - Vibrance
  - Mixage des canaux
  - Noir-&-blanc
  - Égaliseur TSV
  - Simulation de film
  - Lumière douce
  - Courbes RGB
  - Virage partiel
  - Gestion de la couleur
- Onglet Avancé
  - Retinex
  - Apparance de la couleur (CIECAM02)
- Onglet Transformation
  - Recadrage
  - Redimensionnement
  - Objectif/Géometrie
    - Rotation
    - Perspective
    - Profilcde correction d'objectif
    - Distortion
    - Aberration Chromatique
    - Correction vignettage
- Onglet Raw
  - Capteur à matrice de Bayer
    - Dématriçage
    - Points noirs Raw
    - Traitement pré-dématriçage
    - Aberration chromatique
  - Capteur à matrice X-Trans
    - Dématriçage
    - Points noirs Raw
  - Points blancs Raw
  - Traitement pré-dématriçage
  - Trame noire
  - Champ uniforme
  - Film Négatif
  - Netteté de la capture

## Colorimétrie générale

### Colorimétrie - Importance de Ciecam - Lab ?

De nombreux débats ont lieu à propos de la colorimétrie. Pour rappel ce
n'est pas une science exacte...Il ne suffit pas de faire des équations
(mêmes complexes..) pour que l’œil humain soit satisfait d'une image.

Actuellement, RawTherapee utilise l'espace colorimétrique L\*a\*b\* et
CIECAM02/16 pour l'adaptation chromatique et des travaux ont commencé
pour explorer d'autres espaces colorimétriques (Jzazbz) et modèles CAM,
pour les applications HDR (ZCAM ne fonctionne pas).

L'utilisation de l'espace couleur L\*a\*b\* (ou CIELAB) a ses limites,
mais nombre de ses défauts peuvent être atténués avec succès, du moins
pour les applications SDR.

Quelques exemples :

- On dit souvent que L\*a\*b\* est non linéaire et qu'il « déforme » les
  couleurs notamment pour les bleus-violets et les rouges-oranges...si
  on agit par exemple sur une courbe ou un curseur chromaticité... C'est
  vrai ! Mais dans Rawtherapee, si vous cliquez sur « Avoid Color
  Shift », près de 200 LUT vont corriger cette dérive et rendre l'image
  parfaitement linéaire.
- On dit aussi que L\*a\*b\* adresse des couleurs imaginaires...lorsque
  bien sûr le profil de travail le permet...C'est vrai. Mais dans
  Rawtherapee, si vous cliquez sur « Avoid Color shift » , le gamut du
  profil de travail est utilisé, un choix est proposé pour rentrer dans
  le gamut.
  - Il analyse les données de l'image.
  - Si elle est dans le gamut, aucune action n'est entreprise.
  - Si elle est en dehors du gamut, la chroma est réduite et si cela est
    insuffisant, ou si elle est proche de L=0 ou L=100, alors L est
    ajusté.
  - Gamutmap - mis au point par Emil Martinec - permet de contrôler le
    gamut XYZ
  - Cependant, cela devrait rarement se produire si Prophoto est utilisé
    dans le profil de travail et n'est probablement pas important.
  - Si la saturation a été ajustée (chroma, vibrance,...), une
    correction Munsell utilisant près de 200 LUTs est appliquée. Cela
    permet de corriger tout décalage de couleur avec un haut degré de
    précision, par exemple un rouge qui est devenu orange à cause de
    L\*a\*b\*, redeviendra rouge. Il y aura encore quelques erreurs mais
    elles sont très faibles.
  - Vous pouvez utiliser uniquement la correction Munsell en cochant
    "Correction Munsell uniquement"

### L\*a\*b\*

- est une transformation réversible de XYZ (en simplifiant Y est
  transformé en L\* par un gamma de 3.0 et une pente de 9.03), donc
  L\*a\*b\* a sensiblement les mêmes caractéristiques en termes de
  limites - ce sont celles des primaires - que XYZ qui sert de référence
  au "Profil de travail" et fixe les bases du gamut. Donc 'sensiblement'
  les mêmes caractéristiques (latitude d'exposition, gamut, etc.). Un
  point toutefois, dans de rares processus les valeurs de L\* peuvent
  être bornées (Clip), pour limiter des artefacts (contrastes élevés,
  les hautes lumières...).
- mais dans la plupart des cas, L\* n’est pas limité. Si jamais un jour
  on arrive au traitement HDR, il faudra probablement passer au «
  HDR-Lab » ou autre système. Les données ne sont pas perdues, même pour
  les images à plage dynamique élevée (\> 14Ev), mais la progression des
  hautes lumières n'est pas assez progressive lorsqu'elle est utilisée
  avec des moniteurs capables d'afficher des valeurs de luminance dans
  la plage de 120 cd/m² et au-delà.

#### L\*a\*b\* ne pénalise pas le gamut et les images à haute dynamique -exemple image avec une Dynamic Range de 25Ev

A noter que la majorité des appareils numériques en 2024, ont une
Dynamique Range maximum de 15Ev. Cette image est donc exceptionnelle
mais va montrer ici le comportement de L\*a\*b\* pour les images à DR
élévée.

Fichier TIF (Creative Common Attribution-share Alike 4.0):
[1](https://drive.google.com/file/d/1vAzFY7Qh8MdJ882J_4JeO_cnpGELzD8D/view?usp=sharing)

##### Image d'origine - sans traitement

Remarquez :

- les ombres sont bouchées
- 40% environ de l'image est avec des blancs à 100%
- La DR originale est de 25Ev
- la DR restituée est de l'ordre de 12Ev

<figure>
<img src="/images/sweep-rgb-neutral.jpg" title="sweep-rgb-neutral.jpg"
width="600" />
<figcaption>sweep-rgb-neutral.jpg</figcaption>
</figure>

##### Image avec Local Adjustments - Log encoding

Remarquez :

- les ombres et les lumières occupent toute la plage visible de L=1 à
  L=99.8 (échelle 0 - 100)
- les couleurs semblent uniformément réparties selon la luminance.
  L\*a\*b\* ne pénalise pas la Dynamic Range (DR)
- la DR restituée est de 25Ev environ.

<figure>
<img src="/images/sweep-rgb-log.jpg" title="sweep-rgb-log.jpg" width="600" />
<figcaption>sweep-rgb-log.jpg</figcaption>
</figure>

### Ciecam

- On dit souvent que « Ciecam02 » n'est pas capable de traiter les
  images à hautes dynamique, c'est partiellement vrai. De nombreuses
  améliorations ont été apportées par l'équipe de développement il y a
  quelques années pour réduire ce phénomène. Néanmoins il faut
  relativiser, une très forte proportion d'images utilisateur sont dans
  le gamut sRGB...et ne posent aucun problème. Cependant, en utilisant
  le Log Encoding en conjonction avec la Cam16, ou Color Appearance
  (Cam16 & JzCzHz), la grande majorité des problèmes peuvent être
  résolus. Bien sûr, certaines images présenteront encore des problèmes,
  en particulier avec la reconstruction des hautes lumières, mais ce
  n'est pas spécifique à Ciecam. L'ajout de Ciecam16 (Cam16) permet de
  résoudre certains de ces problèmes.
- Par contre Ciecam02/16 est une des seules manières de réaliser une
  véritable colorimétrie prenant en compte la perception de l'homme et
  de son environnement. Par exemple lors d'un souhait pour accroître la
  luminosité et/ou la saturation, Ciecam tiendra compte de l'image et de
  son environnement.

[Ciecam - english](ciecam02)

### Balance des blancs

- La balance des blancs est aussi sujet à débat...Le module « Itcwb »
  (Temperature correlation) récemment introduit dans Rawtherapee est du
  point de vue mathématique (cognitif) presque parfait. Il fait
  coïncider les couleurs xyY de l'image à des données spectrales connues
  ...Mais, sur les images où la température trouvée est loin de D50...la
  colorimétrie ne sera pas correcte...Il va manquer une adaptation
  chromatique, celle nécessaire à nos yeux, à notre cerveau. Ciecam va
  la réaliser. Je n’ai pas prévu une adaptation chromatique
  systématique. Vous pouvez la réaliser, par exemple, en mode symétrique
  avec Color Appearance & Lighting.

### Importance du mode linéaire RGB et colorimétrie

On vante souvent le modèle RGB, en particulier le modèle « linéaire ».
Nous croyons que ce mode linéaire est la meilleure manière d'assurer les
traitements « amont » (demosaicing, balance des blancs, defringe,
aberration chromatique, etc.). tout ce qui peut être réalisé dans ce
mode doit l'être.

Par contre que penser – sauf pour des valeurs modérées – des « tone
curves » :

- Qui non seulement rompent la linéarité, mais sont peu compensées en
  termes de colorimétrie (à l'exception du mode Perceptual qui fait
  appel à Ciecam02) – contrairement aux TRC utilisées dans les sorties
  (moniteur, TIF...).
- "Auto matched Tone Curve" - qui est en fait une copie de la TRC de
  l'APN est appliquée en milieu de processus, rompt la linéarité..

Comment rendre le mode RGB linéaire lorsqu'on change la saturation. Ce
n'est probablement pas impossible, mais difficile, pas implanté dans
Rawtherapee. En opposition à Ciecam « saturation » qui tiendra compte
des variations de luminance (ou de brillance) pour adapter cette
variation de couleur.

Donc, en synthèse, il n'y a pas une bonne manière, et une
mauvaise...Mais des méthodes RGB, L\*a\*b\*, Ciecam qui ont leurs
avantages et inconvénients...à utiliser à bon escient.

### Quels sont les principes acceptables pour traiter les images (SDR ou HDR)?

L’argumentaire ci-dessous prend en partie ses fondements dans le fait
que Rawtherapee dispose de deux modules Ciecam, l’un situé en fin du
processus principal (Color Appearance & Lighting), l’autre dans
Selective Editing, Color Appearance (Cam16) situé juste après la balance
des blancs. Ces 2 modules sont des CAM (Color Appearance Model) et
contiennent les méthodes et outils suffisants pour assurer une bonne
colorimétrie. Néanmoins ces 2 modules ne sont pas toujours capables,
seuls : a) de traiter les images avec une trop forte dynamique, b) ou
les images avec des ombres très prononcées, c) ou des images où les
hautes lumières sont fortement présentes (à ne pas confondre avec la
reconstruction des hautes lumières).

La science de la colorimétrie est souvent inexacte et imprécise.
Néanmoins comme vu précédemment, le traitement le plus linéaire possible
semble recommandé si on peut le faire. Ceci semble toutefois impossible
si les différences liées à, a) b) c) ci-dessus sont importantes. Dans
ces cas je propose en première étape un principe proche de celui du
rendu de la vision humaine : une partie linéaire (slope) pour
"déboucher" les ombres et une partie parabolique (gamma) pour rendre la
perception des moyennes et hautes lumières assez semblable à celle de
notre couple œil/cerveau. Ceci n’est pas une élucubration, on retrouve
cette différenciation linéaire/parabolique dans de différents logiciels
tels, la notion de "gamma sRGB" : slope=12.92 et gamma=2.4, ou de
"BT709" : slope=4.5 gamma=2.22 ou de "Lab" : slope=9.03 gamma=3.0. Les
deux modules TRC "Tone Response Curve" présents soit dans "Abstract
profile", soit dans le module "Selective Editing, Source Data
Adjustments" permettent d’apporter une réponse partielle au traitement
des images au moins de type a) et b), en permettant l'ajustement avec
des valeurs plus élevées de slope et gamma.

Reste ensuite à aborder le problème de l’atténuation des hautes
lumières, l’amélioration du contraste global et l’utilisation d’un
contraste local.

N'oubliez pas que Cam16 est un module de traitement à part entière. Vous
pouvez utiliser pour le traitement des images:

- Surround (Scene conditions) - average, dim, dark, ... - qui permet de
  prendre en compte des fonds sombres ou très sombres. Cet algorithme
  peut à lui seul assurer dans certains images un traitement de relevage
  des ombres.
- Les divers réglages: Lightness, Brightness - et leurs contrastes
  associés, chroma, saturation, colorfullness, ...;

[Selective Editing - Cam16 and HDR
functions](Local_Adjustments#Using_the_Cam16_and_HDR_functions.md)

Mais, l'essentiel est que le résultat vous convienne.

### Utilité des profils d’entrée ICC et DCP ?

Les fichiers Raw sont en général décodés en utilisant une matrice
(origine Adobe) nommée "Color Matrix1" basée sur l’illuminant D65. Cette
matrice est suffisante dans une très grande majorité de cas. On peut y
substituer soit un profil ICC, soit un profil DCP qui a été élaboré soit
par soi-même par exemple à l’aide d’une Colorchecker24, soit fourni par
Rawtherapee ou Adobe. Les problèmes généraux de ces profils sont de 2
types :

- la Colorchecker24 se limite (à une exception près dans les bleus) au
  gamut sRGB. Que penser d’un profil qui sera utilisé par exemple sur
  des fleurs ou des minéraux où le gamut est nettement plus grand ?
- le profil n’a vraiment de pertinence que pour un illuminant donné. Que
  penser d’un profil élaboré en D50 (lumière du jour au soleil) et
  utilisé à l’ombre. Certes les profils DCP ont une table
  d’interpolation entre D65 et Tungstène 2850K, mais cela reste
  approximatif.

Mon propos n’est pas de s’opposer à l’utilisation de ces profils qui
sont très utiles par exemple pour les reproductions (tableaux,
monnaies,…) avec un éclairage maîtrisé, mais de montrer leurs limites.

### Faut-il se servir de "Auto-Matched Tone Curve"?

La réponse est : peut-être ? Cette courbe générée à partir du JPEG joint
au Raw reproduit la colorimétrie du fabriquant de la caméra (Canon,
Nikon, Sony, etc.). C’est un critère de choix, mais qui présente
quelques contraintes:

- la courbe générée peut amener un accroissement du contraste qui, selon
  les images, amènera un débordement de l’histogramme dans les basses et
  hautes lumières. Dans de nombreux cas, cet accroissement du contraste
  n’est pas souhaitable.
- le choix par défaut "Film-like" modifie la colorimétrie. Cette
  modification est en contradiction avec la philosophie de Ciecam. Il
  vaut mieux, si vous souhaitez conserver "Auto-Matched Tone Curve",
  adopter le mode Standard.

### Faut-il se servir du module "Exposure" et en particulier de "Exposure compensation"?

La réponse est : avec réserves. Dans le cas des images de type a), b) ou
c) le slider "Exposure" va amener un changement de l’exposition de façon
linéaire (en Ev), accroissant (ou réduisant) de la même manière les
ombres et les lumières. Certes on peut agir sur "Highlight compression",
"black", etc., mais cette modification n’est pas très intuitive et va à
contresens de l’effet effectué par gamma/slope de la TRC (Tone Response
Curve). Une alternative est d’utiliser "Tone Equalizer" (main ou
Selective Editing) qui permet une différenciation progressive des ombres
et lumières.

### Les modules Tone-mapping description et utilité

Je m’attarderais uniquement sur les modules se servant de "Black Ev",
"White Ev" et "Mean Luminance (Yb%) Scene". En effet pour les autres
modules "Tone mapping" de Rawtherapee :

- "Tone mapping" est plus un module pour agir en profondeur sur le
  contraste local (texture) qu’un réel Tone-mapper,
- "Dynamic Range Compression" utilise un Laplacien et une transformée de
  Fourier. Ses performances sont correctes, mais il est lent et consomme
  beaucoup de ressources.
- A noter que la majorité des images - y compris avec les camera
  modernes - sont limitées à 14 ou 15 Ev. Les logiciels HDR qui
  fabriquent une image DNG à partir de plusieurs images à partir de
  "bracketing" doivent pouvoir atteindre environ 20 Ev.

[Évaluer la Dynamic Range des outils en termes de Dynamic
Range](Local_Adjustments/fr#Évaluer_la_Dynamic_Range_des_outils_en_termes_de_Dynamic_Range_(DR) "wikilink")
In english [An evaluation of the dynamic-range capabilities of tools in
Selective_Editing](Local_Adjustments#An_evaluation_of_the_dynamic-range_capabilities_of_tools_in_Selective_Editing.md)

#### Le principe de calcul de la Dynamique Range - DR

Trois algorithmes utilisent les concepts liés à la Dynamique Range -
Black Ev, White Ev, Mean Luminance (Yb) scene (concept proche de celui
de "Middle grey").

- Log encoding ;
- Sigmoid;
- Gamma based et Slope based (mon préféré).

Comment sont évaluées ces valeurs ? L’exercice est difficile, car il
consiste à trouver sur une image non traitée, le point le plus noir
(Black point), le point le plus blanc (White point) et la valeur du gris
moyen (Yb%). Une formule assez empirique et approximative évalue ces 3
données qui seront ensuite utilisées par les 3 algorithmes cités.

- la première question est : "De quelles données se sert-on, et à quel
  niveau du processus ?". Rawtherapee se sert des données juste après la
  balance des blancs et après conversion vers le Working profile (sauf
  pour Sigmoid Q et Slope based Q qui sont incorporés au process Cam16).
- la seconde question est : "Est-ce que ces valeurs sont représentatives
  de la réalité ?". Pas sûr… Notamment:
  - on ne connaît pas la cartographie des noirs près du "Black point",
    et des blancs près du "White point",
  - la valeur du "Middle grey" est d’une part, entachée d’approximations
    et d’autre part, Ciecam prend en compte la luminance de l’arrière
    plan Yb%, et non la luminance de l’image entière.
  - ceci m’a amené – plutôt que de jouer empiriquement sur les 3
    paramètres Black Ev, White Ev, Mean luminance (Yb%) Scene - de
    prévoir l’action sur la distribution des noirs et des blancs, cette
    action ayant une incidence sur la valeur de Mean Luminance (Yb%)
    Scene. Par défaut "White distribution" est à 20 pour tenir compte de
    Ciecam (Yb%).

#### Comment sont utilisées ces 3 valeurs: Black Ev, White Ev, Mean Luminance (Yb) Scene ?

- Log encoding, calcule une base logarithmique à partir des valeurs de
  Black Ev Scene, Dynamic Range et de Mean Luminance (Yb%) Viewing.
  Cette conversion logarithmique est appliquée à l’ensemble des données
  à traiter. Il semble évident que ici le traitement est "tout sauf
  linéaire". Selon les images on aboutira quelquefois à un excès de
  relevage des ombres et d’atténuation des lumières, par rapport aux
  lumières moyennes. De plus cette conversion peut modifier la
  colorimétrie en profondeur. Pour Log encoding, l’algorithme présent
  dans Rawtherapee ne prévoit que de simples corrections de colorimétrie
  (saturation, brightness compression). L’avantage de cet algorithme est
  qu’il peut traiter de très fortes dynamiques.
- Sigmoid, comme son nom l’indique se sert d’une sigmoid mathématique
  basée sur 3 concepts principaux : a) une atténuation asymptotique
  (surtout des blancs) rendant aux hautes lumières un aspect plus
  naturel ; b) une pente variable de la sigmoid agissant sur le
  contraste global ; c) un déplacement (skew) de la sigmoid pour que
  l’action soit prioritairement sur les lumières ou les ombres (on ne
  peut avoir les deux). L’avantage de cet algorithme c’est sa simplicité
  apparente, il fonctionner très bien sur des images pas trop
  difficiles.
  - Simulation : je joins une démonstration d'une Sigmoid avec 2
    paramètres où "L" correspond au "contraste" et "t" correspond à
    "Skew". A noter que le calcul réalisé dans le code est un peu
    différent. Cette simulation est uniquement à caractère pédagogique.
  - <https://www.desmos.com/calculator/g382ci99gu?lang=fr>
- Gamma based et Slope based, utilisent tous les deux l’algorithme
  Tone-mapping de Freeman. Gamma based n’utilise que la fonction
  asymptotique pour rendre aux hautes lumières un aspect plus naturel.
  Slope based y ajoute la partie des basses lumières et tons moyens. Son
  principe est quelque peu différent de celui de Sigmoid, assez proche
  de celui d’une TRC (le traitement des basses lumières n’étant pas
  strictement linéaire). L’avantage de cet algorithme est sa simplicité,
  il permet un traitement performant de l'atténuation des hautes
  lumières et permet aussi d’agir sur le contraste global.
  - Vous disposez également du choix "RGB channel Slope" qui s'apparente
    en partie à "RGB curves" permettant une action différenciée sur les
    3 canaux R, G et B. Par rapport à Slope based, des réglages ont été
    ajoutés pour exploiter pleinement l'algorithme de Freeman :
    - Prise en compte de la DR (dynamic range) pour Yb Viewing, en plus
      de Yb Scene,
    - Lumosity mode pour essayer de préserver la luminance (similaire à
      RGB curves) - ce mode peut amener de forts artefacts,
    - Prise en compte d'un seuil (Attenuation threshold) associé au
      choix "Highlight attenuation only" pour moduler le début de
      l'action sur les highlights (normalement à partir de Yb scene).

Dans les 3 cas (Log encoding, Sigmoid, algorithme de Freeman) on utilise
les données de "Scene" (Source) pour les faire rentrer dans une plage
utile pour notre vue ou nos périphériques (écrans,…). Cette plage utile
est elle aussi source de débats : a) doit-on se servir de luminance
relative pour les périphériques de sortie ou de la luminance absolue
avec les notions pour la luminance de "Peak" et de "Diffuse white" ; b)
notre couple œil cerveau dispose de performances nettement supérieures à
tous les systèmes et prend en compte d’autres paramètres physiologiques
(Ciecam). Le module Cam16 (Selective Editing) essaye de prendre en
compte (au mieux) l’ensemble de ces paramètres.

- Le cas de Sigmoid Q et Slope based Q : j’ai tenu à intégrer dans la
  boucle Q (Absolute luminance) de Cam16 (qui dispose de 6 variables),
  les 2 algorithmes Sigmoid et Slope based. Il est évident que nous ne
  sommes plus en amont du processus, mais dans le processus. En
  particulier la valeur de "Middle grey - ici Yb% Scene" est
  profondément modifiée par Ciecam. J’ai appliqué un coefficient
  correctif empirique moyen. Ces 2 algorithmes doivent plus être vus
  comme des défis personnels, que comme de réelles alternatives.

#### Comment utiliser ces algorithmes Tone-mapping ?

- Ces algorithmes Tone-mapping peuvent être qualifiés de
  semi-automatiques, car les paramètres utilisés Black-point,
  White-point, Mean Luminance (Yb%) Scene, sont pré-calculés
  automatiquement. Les valeurs à ajuster de Sigmoid ou Slope based sont
  proches des valeurs par défaut.
- Log encoding, peut être utilisé en première étape, et en complément on
  peut utiliser la TRC (gamma, slope, midtones), voire Sigmoid.
- Pour les autres cas (majoritaires), je recommande de commencer le
  processus par la TRC (gamma, slope, midtones) et d’atténuer les hautes
  lumières soit par "Ev based", "Gamma based". Si un accroissement du
  contraste global est souhaité vous pouvez activer "Slope based" ou
  "Sigmoid".

[Rawtherapee Processing Challenge April
2024](Rawtherapee_Processing_Challenge_feedback.md)

### Le contraste local

Comme je l’ai évoqué précédemment, je pense qu’il vaut mieux pour mettre
en valeur le sujet principal (fleur, immeuble, animal…) agir modérément
sur le contraste global et compléter par un contraste local. Celui-ci se
présente sous 2 formes :

- soit par un algorithme de type Guided-filter (incorporé à Cam16), pour
  de petits ajustements,
- soit en utilisant le contraste local (variable) utilisant les
  wavelets.
  - Dans "Abstract profile" vous disposez de "Contrast enhancement"
    s’appuyant sur la notion de "Contrast profiles".

<img src="/images/APwav.jpg" title="APwav.jpg" width="600" alt="APwav.jpg" />

- Dans Selective Editing, vous avez en mode Basic "Local contrast &
  Wavelets" qui vous permet, en choisissant l’étendue des niveaux de
  décomposition concernés, d’agir sur le "Local contrast", mais aussi
  sur la "Clarity".

<figure>
<img src="/images/locwav.jpg" title="locwav.jpg" width="600" />
<figcaption>locwav.jpg</figcaption>
</figure>
