---
title: Color Management addon
contributors:
  - Jdc
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Gestion de la couleur-Supplément

</div>

## Concepts de la colorimétrie

Ce document vise plusieurs objectifs relatifs à la colorimétrie :

1. Résumer le processus de traitement d'un fichier Raw du point de vue
de la colorimétrie et mettre en évidence les points clefs, les lacunes

2. Expliquer les principes des étapes essentielles afin que
l'utilisateur puisse évaluer les enjeux

3. Expliciter l'emploi de certaines fonctions qui peuvent paraître
obscures aux non-initiés.

A noter que ce document concerne exclusivement RT4 avec le travail avec
des nombres réels, et non RT3. De plus, il ne prend pas en compte les
dysfonctionnements possibles (bugs) qu'il peut rester à solutionner !

### Avertissement

- Il n'est pas dans les objectifs de ce document de traiter l'ensemble
  des aspects de la colorimétrie qui ne sont pas spécifiques à RT, comme
  par exemple : a) l'impression ; b) le calibrage des écrans.
- Cependant, il est recommandé de calibrer son écran avec un des
  nombreux produits du marché : sonde colorimétrique, plus logiciel. Le
  profil élaboré ne concerne que le moniteur et ne doit en aucun cas
  être utilisé soit comme profil d'entrée, soit comme profil de sortie.
- Sous Windows , MacOS ou sous Linux, un logiciel comme DispalGUI de
  Argyll, associé à une sonde de qualité même ancienne (par exemple, la
  sonde DTP94 que je possède et pour laquelle il n'existe plus \[??\] de
  pilotes sous Windows) donne de très bon résultats ; le temps
  d'élaboration est assez élevé (de l'ordre de 1 heure).
- RT reconnaît automatiquement le profil système ; néanmoins vous pouvez
  entrer le nom du fichier icc écran, dans « Preference/ Color
  Management / Monitor Profile »
- Il est souhaitable que le lecteur ait une connaissance *a minima* de
  la gestion des couleurs: triplet matriciel, notions RGB XYZ Lab,
  espace, primaires et profil colorimétrique,...Le lecteur avisé pourra
  consulter le site de B.Lindbloom [1](http://www.brucelindbloom.com)
- L'affichage de l'histogramme ainsi que le naviguateur sont
  paramétrables : par défaut les valeurs affichées prennent en compte le
  "Output profile". Vous pouvez chnager ce comportement en allant dans
  "Préférences" et cocher "Use working profile fr main histogram and
  navigator"
- Bien sûr, le contenu de ce document n'est pas - et de loin -
  exhaustif. Le sujet est complexe

### Processus Raw initial avant conversion RGB

#### Lire le fichier Raw et utiliser ses données

- La première étape, assurée pour l'essentiel par la base Dcraw (merci
  D.Coffin) consiste à lire les fichiers Raw de tous types, avec leurs
  codages propriétaires : profondeur des données 12 ou 14 bits,
  saturation du capteur, balance des blancs,... et bien sûr les données
  rggb ou rgbg;
- la balance des blancs par défaut est celle choisie par l'utilisateur
  sur son boîtier au moment de la prise de vue;
- l'interpolation (AMaZE, AHD, DCB...) intervient ensuite en faisant
  évoluer les données en rgb (image pouvant être évaluée visuellement
  sur un écran) : l'interpolation ne doit pas modifier (ou peu) la
  colorimétrie et c'est le cas pour l'ensemble des interpolations
  présentes dans RT (le deltaE94 du à l'interpolation est
  approximativement de 1 donc négligeable), par contre aux limites (très
  hautes lumières,...) des artefacts peuvent apparaître pour certaines
  d'entre elles.
- ces données rgb sont modifiées pour leur donner un aspect plus proche
  de la réalité, par : soit une matrice de couleur (origine Adobe), soit
  un profil DCP (origine Adobe – ou RT) , soit un profil ICC "input",
  nous reviendrons ci-après sur ces profils ICC, leur élaboration et
  leur utilisation;
- les valeurs rgb sont sans espace colorimétrique - ce point est
  fondamental (le choix par exemple sRGB ou AdobeRGB proposé sur le
  boîtier ne concerne que les fichiers JPG)
- la gestion des couleurs est opérée : a) en partie avec LCMS2, qui a
  fait de gros progrès, et maintenant à la possibilité de travailler en
  virgule flottante en évitant de "cliper" les couleurs; b) directement
  par calcul (conversion XYZ, Lab, RGB, gamma, etc.)

#### Les profils ICC "input" : élaboration, utilisation, lacunes

- ces profils s'appliquent (au sens colorimétrie "apply" et non
  "convert") : soit comme profils externes après conversion RGB (comme
  le fait Capture NX2) aux données rgb, donc théoriquement sans
  intention (relative, absolue, perceptuelle, saturation). Ils modifient
  les valeurs Lab, mais pas les valeurs rgb - les histogrammes restent
  identiques, soit comme profils internes comme le fait RT
  (théoriquement sans intention...) ;
- ils essaient de réduire l'écart entre leurs valeurs initiales (celles
  du capteur) et une valeur cible en théorie parfaite;
- ils sont théoriquement valables pour : un illuminant donné (D50, C,
  ombre,...), les conditions de la prise de vue de la mire, l'objectif
  de prise de vue...
- néanmoins on peut sans problème les utiliser à condition de rester
  sensiblement dans le même environnement, par exemple flash au lieu de
  lumière du jour, D55 au lieu de D50...

<!-- -->

- élaboration :

<figure>
<img src="/images/Mire468.jpg" title="Mire468.jpg" />
<figcaption>Mire468.jpg</figcaption>
</figure>

1.  photographier une mire dans des conditions idéales de prise de vue
    qui correspondent à votre utilisation souhaitée (extérieur,
    studio,...) ;
2.  plus le gamut de la mire sera grand, meilleur sera le résultat, par
    exemple la ColorChecker24 est proche de sRGB, même si elle donne de
    bons résultats dans les cas courants, comment peut-elle évaluer
    efficacement les couleurs réelles qui sont au-delà de sRGB (fleurs,
    couleurs artificielles...)?
3.  plus la mire aura un nombre de cellules important, meilleur sera le
    résultat (meilleur guidage du profil)
4.  La mire 468 couleurs, dévelopéée avec un collègue"Rouli", dépasse
    WideGamut pour certaines couleurs, et présente des valeurs de
    luminance basse.
5.  par exemple à titre d'information pour mon D200, les résultats des
    deltaE94 obtenus à partir du cliché (NEF) de ma mire 468 couleurs
    sur lequel j'applique le profil d'entrée ou la matrice : a) matrice
    de couleurs d'origine (Dcraw) – (ou résulats obtenus avec Camera Raw
    6.6 et profil DCP) : moyenne=4.37, écart-type=1.82, maximum=13.75
    ; b) profil ICC, présent dans le répertoire "Iccprofile" élaboré à
    partir de la ColorChecker24 proche de sRGB : moyenne=3.66,
    écart-type=2.08, maximum=11.28; c)profil ICC, élaboré par mes soins
    à partir de la mire 468 couleurs à gamut très large proche de
    WideGamutRGB : moyenne=2.05, écart-type=1.44, maximum=8.8; d)Bien
    sûr dans une majorité de cas, le profil réalisé avec une
    ColorChecker24 (ICC ou DCP) sera suffisant !
6.  prendre les photos de la mire vers 12h en plein soleil (a), ou par
    temps couvert (b), ou à l'ombre (c) ou avec un éclairage tungstène
    (d), ou avec une lampe de studio Solux (e) qui a un spectre très
    proche de la lumière du jour, ou f) un autre éclairage qui
    correspond à vos besoins: a) mettre le boîtier en mode manuel
    (exposition...) ; b)régler la balance des blancs sur a) 5000K (ou
    équivalent « soleil »); b) 6000K; c) 8000K; d) tungstène 2850K; e)
    Sun 4700K; f)... ;c) s'assurer qu'il n'y a aucun reflet ; d) prendre
    plusieurs clichés par 1/3 IL ; e) s'assurer de la plus parfaite
    égalité d'exposition entre le centre et les 4 bords de la mire
7.  mettre le(s) fichier(s) Raw dans un dossier RT
8.  ouvrir le Raw avec un profil pp3 "neutral" et choisir "Prophoto"
    comme "working profile", dans "Input Profile" choisissez "No
    profile"
9.  évaluer l'exposition à partir d'une des cellules grises de la mire
    dont la luminance est comprise entre L=40 et L=60 et examiner la
    différence d'exposition entre les bords sombres de la mire; choisir
    le cliché avec le meilleur compromis; recommencer éventuellement la
    prise de vue
10. régler éventuellement l'exposition avec "raw white-black point", de
    telle manière que la valeur de L de la cellule de référence grise
    "K14" soit la plus proche possible de la référence (L=43.85)
11. ajuster la balance des blancs avec SpotWB, en choisissant une
    cellule grise (L\>20 - L\<80) dont les valeurs "a" et "b" soient le
    plus proche de zéro (pour cette opération les valeurs « a » et « b »
    doivent être inférieures à 0.5 - les 2 meilleures cellules sont
    "K14" avec a=-0.07 b=-0.3 ou "H15" avec a=0.06 b=0.24 ; sinon si la
    cellule possède des valeurs « a » et « b » proches de 1, ajuster
    avec les curseurs "température" et "teinte" (voire plus loin les
    remarques sur la balance des blancs) de telle manière à aboutir aux
    valeurs Lab de la cellule de référence.
12. puis cliquer sur "Save reference image for profiling"
13. utiliser votre "profiler" qui se servira selon le fabricant soit des
    valeurs spectrales, soit des valeurs Lab ou XYZ : générer un profil
    de type reproduction pour l'illuminant correspondant à la prise de
    vue (D50, D65, Solux, etc.).
14. bien sûr certains « profilers » (Profilemaker5, etc.) permettent
    d'élaborer des profils qui ne sont pas des profils « reproduction »
    qui minimisent les deltaE94, mais des profils qui vont donner un
    rendu spécifique (portrait, paysage, etc.) en jouant sur la courbe
    de contraste et sur la chromaticité différenciée des tons pastels et
    saturés. Ces profils fonctionnent mais de mon point de vue sortent
    de l'esprit de « Rawtherapee » en introduisant dès le départ des
    processus des écarts de teintes et de contrastes qui ne seront plus
    rattrapables par les divers algorithmes. Néanmoins ce choix est
    possible.

#### Balance des blancs

##### Lacunes de la balance des blancs

- la balance des blancs n'est vraiment opérationnelle que si on utilise
  "SpotWB" sur un gris parfait ("a" et "b" de Lab à zéro), mais comme il
  est quasi impossible de mettre une charte de gris sur chaque photo
  prise (sinon de le faire à la Alfred Hitchcock) , il faut passer en
  général si on souhaite ajuster la balance des blancs du boîtier, par
  les curseurs "Temperature" et "Tint";
- Or les curseurs donnent une amplitude 1500K à 25000K, et la base de
  calcul utilisée correspondant à l'illuminant D (Daylight) n'est pas
  valable en dessous de 4000K (les calculs ne sont qu'une extrapolation)
- De plus les informations deviennent erronées si l'illuminant est
  différent de la lumière du jour (D) par exemple l'illuminant
  "Blackbody" ou "Fluorescent"
- Donc prudence, grande prudence lorsqu'on est en dehors de l'illuminant
  D (lumière du jour) et pour des températures inférieures à 4000K

<figure>
<img src="/images/illum1.jpg" title="illum1.jpg" />
<figcaption>illum1.jpg</figcaption>
</figure>

##### Principes

Prise de vue : Lors de la prise de vue, 2 options de base s'offrent à
l'utilisateur : a) travailler en mode RAW , dans ce cas les erreurs sont
permises et une retouche est possible avec un logiciel de traitement
Raw, par exemple RT ; b) travailler en JPEG, dans ce cas si le choix de
la balance des blancs sur le boîtier est différent des conditions
d'éclairage la retouche est plus difficile. Nous privilégierons l'étude
du mode Raw.

Cependant un boîtier dispose, (indispensable en JPEG, souhaitable en Raw
) de plusieurs réglages balance des blancs. Bien sûr ces fonctionnalités
dépendent de la marque et du modèle, mais on retrouve souvent :

- Un mode « auto » : c'est l'électronique du boîtier qui décide quelle
  est la bonne valeur, à partir d'algorithmes « maison ». Ce mode
  fonctionne généralement assez bien, sauf lorsqu'il y a de fortes
  dominantes de couleurs.
- Un mode « manuel » , où l'utilisateur, pour certaines marques, entre
  une valeur de température, par exemple 7000K. Ce choix est fait par un
  utilisateur averti en fonction de son expérience.
- Un mode « préselection » où l'utilisateur peut choisir parmi un
  certain nombre de situations prédéterminés en « usine » : « soleil »,
  « ombre », « couvert », « flash », « incandescent », « fluorescent
  »,...
- à noter que chaque marque et chaque boîtier à ses spécificités, par
  exemple pour le mode fluorescent : a) Canon dote ses boîtiers d'un
  seul mode ;b)Fuji en donne 3; c) Pentax en donne 3 ;d) Nikon en donne
  jusque 7 (D3S, D300,...); e) etc.

<!-- -->

- à noter également que la valeur « flash » est différente d'une marque
  à l'autre, par exemple pour : a) un Nikon D300, l'illuminant flash
  correspond sensiblement à 6400K; b) un Leica R9, l'illuminant flash
  correspond sensiblement à 5500K; c) un Sony A900, l'illuminant flash
  correspond sensiblement à « shade » soit, vers 7000K...
- bien sûr dans une majorité de cas le choix de la présélection est
  assez évident, mais dans d'autres cas l'utilisateur ne saura que
  choisir...En effet lors d'une exposition, visite d'un musée, etc. quel
  est l'éclairage utilisé ?
- Tous ces réglages agissent sur les multiplicateurs de canaux ;
- En final lors d'un traitement « raw » ce choix apparaîtra dans RT
  comme « Camera »

##### Traitement raw

RT offre 5 possibilités:

- « Camera » : le logiciel utilise - lorsque elles existent les données
  EXIF à la prise de vue
- « Auto » : le logiciel évalue, la balance des blancs par une « moyenne
  » des données vis-à-vis d'un gris neutre théorique ;
- « Réglages prédéfinis » : comme ombre, soleil, fluorescent, etc.
- « Custom » : l'utilisateur peut choisir, la température et la teinte
  (voir le chapitre « lacunes de la balance des blancs »)
- « Spot WB » : l'utilisateur choisi une zone gris neutre comme
  référence. Ceci suppose quasi obligatoirement la présence au moment du
  cliché d'une charte gris neutre.

##### Objet coloré – illuminant – observateur

En simplifiant la colorimétrie peut se synthétiser en 3 types de données
:

- Objet coloré : il se caractérise par ses pigments (rouge, bleu,...)
  quelque soit la source lumineuse éclairante. On peut l’évaluer avec un
  specto, qui va en donner une représentation unique
- Illuminant ou source lumineuse : cette donnée caractérise, la nature
  de la source éclairante (soleil à midi, ombre, flash, lampe tungstène,
  tube fluorescent...). Elle s'évalue par 2 données : sa répartition
  spectrale et sa température corrélée ; attention 2 sources lumineuses
  qui ont la même température ne sont pas identiques car leurs données
  spectrales sont différentes.
- Observateur : faites l'expérience suivante, observez la couleur d'un
  mur peint, puis celui de l'échantillon qui vous a permis le choix,
  vous constaterez que la sensation colorée est différente. La CIE
  (Commission Internationale de l’Éclairage) a défini 2 « observateur
  s», 2° et 10°, caractérisés par l'angle d'examen de la couleur.

Pour calculer les valeurs observées d'un objet coloré, sous l'illuminant
X, il est nécessaire de faire intervenir dans le calcul les données
spectrales de l'objet, de l'illuminant et de l'observateur Ces valeurs
XYZ seront spécifiques à la température de l'illuminant (par exemple
6500K) ; au niveau des logiciels (Photoshop, RT...) la norme est
d'utiliser D50. Il est donc impératif de réaliser une adaptation
chromatique des valeurs XYZ(illuminant) vers XYZ(D50). Pour cela
plusieurs méthodes existent de la moins performante à la plus
performante : Von Kries, Bradford, CIECAM02.

##### L'illuminant lumière du jour (Daylight)

Cet illuminant a fait l'objet de nombreuses études de Judd, MacAdam et
Wyszecki, à partir de plusieurs centaines d'exemples. Sommairement
l'illuminant « D » est la somme de 3 parties : S(lamda)=S0(lamda) +
M1\*S1(lamda)+M2\*S2(lamda)

- une partie « fixe » So qui est la moyenne de tous les exemples testés
  ;
- une première partie « variable » S1 qui correspond aux variations «
  bleu/jaune » dues à la présence ou non de nuages ou à la position et à
  l'intensité du soleil direct ;
- une deuxième partie « variable » S2 qui correspond aux variations «
  rose/vert » dues à la présence d'humidité sous forme de vapeur ou de
  brume... ;
- Concrètement cela se traduit par une formule « simple » qui détermine
  2 valeurs x_D et y_D en fonction de la température de l'illuminant
- x_D=0.244063 + 0.0991\*103/T+2.9678\*106/T2 -4.6070\*109/T3 pour 4000K
  \< T \< 7000K
- x_D=0.237040 + 0.24748\*103/T + 1.9018\*106/T2 -2.0064\*109/T3 pour
  7000K \< T \< 25000K
- y_D = -3.0\*x_D2 + 2.87\*x_D-0.275
- ces formules sont utilisées pour calculer les paramètres M1(x_D,y_D)
  et M2(x_D,y_D) de S(lamda)=S0(lamda) + M1\*S1(lamda)+M2\*S2(lamda) –
  ce n'était pas le cas jusqu'ici dans RT. Précédemment dans RT les
  valeurs xD et yD servaient directement au calcul des multiplicateurs
  de canaux, maintenant ces valeurs servent à déterminer les valeurs
  spectrales de l'illuminant à la température T. C'est seulement ensuite
  qu'on calcule de secondes valeurs qui permettent de déterminer les
  multiplicateurs

On constate immédiatement 2 choses :

- il n'existe aucune référence « Daylight » en dessous de 4000K, la
  précédente formule utilisée dans RT (de 1200K à 4000K) a été «
  inventée » dans le cadre de Ufraw ;
- rien ne s'oppose à modifier RT pour faire passer la valeur maximum de
  12000K à 25000K (réalisé depuis 2013)

##### L'illuminant « corps noir » (blackbody) et «A : tungstène »

« L'illuminant A de la CIE est utilisé pour représenter la lumière
typique d'un filament de tungstène d'une ampoule domestique. Sa
distribution spectrale relative est celle d'un radiateur de Planck à une
température approximative de 2856 K. L'illuminant A de la CIE peut être
employé dans toutes les applications de colorimétrie impliquant
l'utilisation d'une lumière incandescente, à moins qu'il y ait des
raisons spécifiques d'employer un autre illuminant. »

L'illuminant « corps-noir » (blacbody ) peut être calculé par la formule
de Planck qui est la généralisation de l'illuminant en fonction de T :

- S(lamda)= c1 \* pow(wavelength, -5.0)) / (exp(c2 / (wavelength \*
  blackbody_Temp)) – 1.0);
- où les 2 valeurs c1 et c2 correspondent à : a) c1=2\*Pi\*h\*c2
  h=constante de Planck c=célérité de la lumière ; b) c2=h\*c/k
  k=constante de Boltzmann

Cet illuminant se raccorde bien vers 4000K avec l'illuminant « Daylight
» avec des écarts minimes j'ai donc choisi pour RT d'utiliser en dessous
de 4000K et jusque 1500K, l'illuminant « corps-noir » (il semble que «
ACR » ait fait le même choix)

##### Les illuminants Fluorescent

La normalisation a prévu 12 illuminants de ce type, correspondants aux
tubes vendus dans le commerce :

- F1 : lumière du jour fluorescente – 6430K
- F2 : Blanc fluorescent froid – 4230K
- F3 : Blanc fluorescent – 3450K
- F4 : Blanc fluorescent chaud – 2940K
- F5 : lumière du jour fluorescente – 6350K
- F6 : Blanc lumineux fluorescent – 4150K
- F7 : simulateur D65 – 6500K
- F8 : Simulateur D50 – 5000K
- F9 : Blanc froid deluxe – 4150K
- F10 : Philips T85 – 5000K
- F11 : Philips T84 – 4000K
- F12 : Philips T83 – 3000K

Ces illuminants (voir « lacunes de la balance des blancs ») ont une
répartition spectrale très différente entre eux et entre les illuminants
« daylight » et « blackbody ». Il est donc très peu conseillé de
remplacer – lors d'un éclairage fluorescent – l'illuminant en question
(par exemple F11 4000K), par un équivalent « Daylight 4000K »

<figure>
<img src="/images/Comp4000.jpg" title="Comp4000.jpg" />
<figcaption>Comp4000.jpg</figcaption>
</figure>

En fait la balance des blancs, calcule à partir des données spectrales,
2 coefficients xD, yD qui modifient les multiplicateurs de canaux : ce
calcul de xD et yD agit à la façon d'un calcul intégral moyenné. Certes
la balance des blancs « moyenne » sera bonne, mais les pics ou les
écarts des données spectrales par rapport à un idéal théorique
(corps-noir ou lumière du jour) amèneront localement pour certaines
couleurs des écarts de teinte plus ou moins importants.

Il existe un concept « CRI = Color Rendering Index » qui traduit la
qualité de la source lumineuse. Ce « CRI » est un chiffre qui vaut 100
pour une source parfaite. On estime que des valeurs supérieures à 90
donnent des résultats acceptables. A titre d'exemple :

- Fluo F4 « warm white » : CRI=51
- Clear Mercury Vapor : CRI=17
- plusieurs LED avec « CRI » compris entre 50 et 96
- Solux 4700 : CRI=92
- etc.

Ce concept est implanté (non encore utilisé) dans RT avec les choix
suivants :

- 20 couleurs de référence dont 8 « standard » de la Colorchecker24 plus
  , 4 teintes peau, 4 gris (blanc – noir), 3 bleus
- utilisation de CIECAM02 pour l'adaptation chromatique
- utilisation de CIE Lab pour calculer les deltaE

Pour y remédier (partiellement), il suffit de réaliser un profil ICC
d'entrée (voir le paragraphe concerné) avec la source lumineuse voulue
assortie des données spectrale correspondantes.

##### Autres illuminants

Il existe d'autres illuminants dérivés de l'illuminant A et proche de «
daylight » :

- B et C que je n'ai pas implanté dans RT, mais il est possible de le
  faire
- un illuminant à énergie égale : « E »
- l'illuminant des lampes de studio (cinéma, éclairage de scènes ,
  musées, studio photo, etc.) qu'on retrouve sous les appellations :
  HMI, GTI, Solux 4700K , JudgeIII, Solix4100K, Solux3500K, etc., qui
  sont implantés dans RT.
- Illuminants LED : ces lampes présentent souvent de grosses lacunes
  dans les bleus. Quelques unes possèdent des caractéristiques très
  satisfaisantes
- L'illuminant des flash « propriétaires » (Canon , Nikon, Pentax...) et
  des flashs de studio : généralement ils sont très proches de la
  lumière du jour, mais chacun à des températures différentes : j'ai
  réalisé plusieurs regroupements à 5500K, 6000K et 6500K, pour les
  flash de studio il serait nécessaire d'avoir leurs caractéristiques
  : a) en théorie il serait nécessaire d'avoir les données spectrales de
  chaque flash (je ne les possède pas) ; de plus ces données varient
  selon la puissance de l'éclair...; b) donc j'ai préféré utiliser
  l'équivalent « daylight »

Comme on peut le constater la situation n'est pas simple et pose de
nombreux problèmes aux logiciels de traitement Raw, dont RT.

##### Diagrammes des illuminants et Color Rendering Index (CRI)

<File:I_llumD50.jpg%7CIlluminant> D50 (CRI=100 Sigma=0)
<File:I_llumA.jpg%7CIlluminant> A 2856K (CRI=100 Sigma=0)
<File:I_llumD150.jpg%7CIlluminant> D150 -15000K (CRI=100 Sigma=0)
<File:I_llumF1.jpg%7CIlluminant> Fluo F1 "daylight" 6430K (CRI=77
Sigma=10) <File:I_llumF2.jpg%7CIlluminant> Fluo F2 "coolwite"4230K
(CRI=64 Sigma=12) <File:I_llumF3.jpg%7CIlluminant> Fluo F3 "white" 3450K
(CRI=60 Sigma=12) <File:I_llumF4.jpg%7CIlluminant> Fluo F4 "warm white"
2940K (CRI=54 Sigma=11) <File:I_llumF5.jpg%7CIlluminant> Fluo F5
"daylight" 6350K (CRI=74 Sigma=12)

<File:I_llumF6.jpg%7CIlluminant> Fluo F6 "Lite white" 4150K (CRI=61
Sigma=13) <File:I_llumF7.jpg%7CIlluminant> Fluo F7 "D65 simulator" 6500K
(CRI=90 Sigma=2) <File:I_llumF8.jpg%7CIlluminant> Fluo F8 "D50 sylvania
F40" 5000K (CRI=94 Sigma=1.4) <File:I_llumF9.jpg%7CIlluminant> Fluo F9
"Cool white delux" 4150K - 4330K (CRI=89 Sigma=2)
<File:I_llumF10.jpg%7CIlluminant> Fluo F10 "Philips TL85" 5000K (CRI=72
Sigma=11) <File:I_llumF11.jpg%7CIlluminant> Fluo F11 "Philips TL84"
4150K - 4000K (CRI=77 Sigma=9) <File:I_llumF12.jpg%7CIlluminant> Fluo
F12 "Philips TL853" 3000K (CRI=72 Sigma=8)
<File:I_llumHMI.jpg%7CIlluminant> Lamp HMI 4800K (CRI=97 Sigma=1)

<File:I_llumCTI.jpg%7CIlluminant> Lamp GTI 5000K (CRI=90 Sigma=2)
<File:I_llumJudge.jpg%7CIlluminant> Lamp Judge III 5000K (CRI=92
Sigma=2) <File:I_llumSolux3500.jpg%7CIlluminant> Lamp Solux 3500K
(CRI=95 Sigma=2) <File:I_llumSolux4100.jpg%7CIlluminant> Lamp Solux
4100K (CRI=92 Sigma=2) <File:I_llumSolux4700.jpg%7CIlluminant> Lamp
SoluxNG 4700K - 4480K (CRI=97 Sigma=1)
<File:I_llumLED-LSI-lum2040.jpg%7CIlluminant> Lamp LED LSI Lumelex
2040 - 3000K(CRI=90 Sigma=2) <File:I_llumLED_CRSSP12.jpg%7CIlluminant>
Lamp LED CRS SP12 WWMR16 - 3050K(CRI=94 Sigma=3)

##### Algorithme

Je me sers de l'algorithme de base « Daylight » : a) calcul des valeurs
x_D et y_D qui sont passés comme paramètres à M1 et M2 (S(lamda) =
S0(lamda) + M1\*S1(lamda) +M2\*S2(lamda) dont on dérive Xi,Yi,Zi par
calcul matriciel \[XiYiZi\]=\[observ2°xyz\]\[S(lambda)\] puis on calcule
les modifications des multiplicateurs de canaux par un simple calcul
matriciel \[mulrgb\]=\[sRGBd65_xyz\]\*\[XiYiZi\]

- je me suis servi des travaux de John Walker (domaine public) , de
  B.Lindbloom -en accroissant la précision et l'étendue spectrale -
  notamment de la fonction « Spectrum_to_xyz » encore appelée «
  CIE_colour_match » qui convertit les données spectrales (350 – 830nm)
  d'une couleur ou d'un illuminant en valeurs xBar, yBar, zBar (via les
  données Observer 2°). En sortie on obtient les valeurs x et y.

Pour le corps-noir (blackbody) j'utilise la formule de Planck : le
raccord entre les 2 formules se fait très bien avec un très léger
décalage des valeurs xD et yD à 4000K (qu'on peut apercevoir avec
l'histogramme entre 3995K et 4005K) :a) daylight 4000K : xD=0.382
yD=0.383 (à titre d'information pour 4500K : xD=0.362 yD=0.370 , pour
7000K xD=0.30 yD=0.32 , pour 25000K xD=0.25 yD=0.25); b) blackbody 4000K
: xD=0.381 yD=0.377 ;

Pour les autres illuminants, les travaux que j'ai fait précédemment sur
l'étalonnage (mire 468 couleurs) m'ont conduit à rechercher (et trouver)
les données spectrales des illuminants que j'ai sélectionnés (tungstène,
Fluorescents, HMI, GTI, Solux, etc.)

===Conversion rgb ==\> RGB - espace de travail "Working Profile" - ===
Cette "conversion", convertit les données rgb (sans espace
colorimétrique) dans l'espace de travail choisi par l'utilisateur.

Ces "working space" sont au nombre de 8 (ce qui me semble largement
suffisant voir excédentaire...): sRGB, AdobeRGB, Prophoto, Widegamut,
BruceRGB, BetaRGB, BestRGB, Rec2020. parmi ces 8 profils 5 sont à large
gamut : BetaRGB (origine B.Lindbllom), BestRGB, Rec2020, WideGamut et
Prophoto.

Lors de cette conversion, Rawtherapee travaille toujours en mode
linéaire, sans gamma. A la fin du processus soit :

- un gamma interne est attribué par RT qui est toujours « gamma sRGB »,
  c'est à dire « gamma=2.4 et pente=12.92 » (comme Lightroom – voir plus
  loin)
- soit un Profil d'écran a été élaboré par l'utilisateur et c'est celui
  ci qui amène les conditions de perception de l'image (généralement le
  gamma attribué par ce profil sera proche d'un gamma sRGB)

A noter que d'autres logiciels ont faits d'autres choix :

- Adobe avec ACR propose 4 choix (AdobeRGB, ColorMatch, Prophoto et
  SRGB)
- Adobe avec Lightroom : pas de choix mais un espace Prophoto modifié
  avec un gamma sRGB (Melissa)
- DxO : pas de choix, mais un espace Adobe
- NX2 : choix dans les espaces de sortie disponibles

Lequel choisir ? Vaste débat où les partisans des petits espaces
s'opposent aux partisans des grands...: entre pertes de données et
données fausses ou imaginaires. En effet le plus large des espaces
(Prophoto) contient par construction des couleurs invisibles, voire
imaginaires. De plus dans la zone des bleus, il peut amener dans
certaines circonstances à générer des artefacts.

Un bon espace de travail aurait une forme prenant en compte le gamut qui
minimise l'espace perdu...ce qui revient à dire qu'il faudrait choisir
l'espace en fonction de chaque image, un trop grand espace pouvant
amener dans les cas extrêmes des couleurs peu saturées (dans le «
working profile », mais qui seront restituées lors de la conversion en
output...). Néanmoins, en théorie, la gestion des couleurs doit rendre
ce choix totalement transparent.

Ma réponse est pragmatique : choisir l'espace qui convient le mieux !
Mais sur quoi se fonder ?

- faites-vous pour l'essentiel des travaux d'impression avec une
  imprimante à pilote CMJN ?: dans ce cas il n'est guère utile de
  choisir un profil à large gamut

<figure>
<img src="/images/GAMUTS.jpg"
title="représentation du gamut de 4 profils ou espaces" />
<figcaption>représentation du gamut de 4 profils ou espaces</figcaption>
</figure>

- faites-vous des travaux d'impression avec une imprimante à jet d'encre
  de haute qualité ? : dans ce cas il est souhaitable de choisir
  Prophoto (les imprimantes de ce type ont un gamut, qui pour certaines
  couleurs, est supérieur à WidegamutRGB), comme "Working Profile", mais
  aussi comme "Output Profile" et bien sûr de choisir le bon profil
  d'imprimante... sur ce graphique on voit le gamut de : a) 3 espaces
  colorimétriques habituels (sRGB en bleu, AdobeRGB en rose, WideGamut
  en jaune), b) le profil ICC pour mon D200 en gris, c) le profil de le
  l'imprimante Epson et son papier à large gamut «
  3800MOABKOKOPELI_2431_V4 »
- avez-vous un moniteur de très haute qualité dont le gamut est proche
  de AdobeRGB ou WideGamutRGB, dans ce cas prendre un profil à large
  gamut.

Un moyen "assez simple" d'évaluer le profil minimum est d'utiliser les
statistiques fournies par "vibrance" en mode Debug (avec verbose=true).
Dans la fenêtre de Rawtherapee.exe, vous verrez un message:

- Gamut : G1negat=x iter - G165535= y iter - G2negat= z iter - G265535=
  w iter
- si une valeur (x ou y) supérieure à 0 apparaît pour l'un ou les 2 G1,
  c'est que l'image initiale (avec les contrôles faits en amont :
  contraste, exposition,...) dépasse le gamut de l'espace choisi dans
  "working profile"
- si une valeur (z ou w) supérieure à 0 apparaît pour l'un ou l'autre
  des 2 G2, c'est que la saturation mise en place par "vibrance" a
  dépassé le gamut..
- A vous de choisir si vous voulez conserver ces valeurs (voir
  ci-dessus) ou les faire rentrer dans le gamut ("vibrance" s'en charge,
  ainsi que "avoid color clipping" + "enable saturation limiter"), mais
  vous "perdez" des couleurs!
- la conversion rgb==\>RGB permet avec le travail en "float" de
  conserver les indispensables valeurs négatives et supérieures à 65535

### Travail dans l'espace colorimétrique choisi par l'utilisateur (espace de travail "Working Profile")

RT a fait le (bon) choix de travailler en mode Lab (ou ses variantes Luv
ou Lch) ou en mode CIECAM02 et avec des réels. Ceci permet de préserver
au mieux les couleurs et le gamut.

Les fonctions présentes dans "Exposure", ne modifient pas la teinte,
sauf "Saturation" qui le fait par défaillance du mode Lab (voir à ce
sujet le paragraphe "Munsell")

Il en est de même pour "Lab adjustements", pour le curseur "saturation"
ainsi que pour les curves "a" et "b" et l'ensemble des courbes qui
contrôlent la chromaticité.

"Channel Mixer" et "HSV equalizer" modifient profondément la
colorimétrie : à utiliser en toute connaissance des conséquences sur la
colorimétrie Les fonctions : contraste, brigthness, tone curve,..
peuvent assez profondément modifier le gamut (voir plus haut le contrôle
à l'aide des statistiques "vibrance")

### Que se passe-t-il lorsqu'on est dans un « Working Profile » ou que l'on change de « Working Profile » ou les réglages ?

Lorsqu'on est dans un profil « étroit » comme sRGB, il peut sembler
évident que les couleurs seront limitées aux limites de ce profil ! Donc
si une couleur d'origine (celle du capteur, légèrement modifiée par
l'interpolation), est à l'intérieur de sRGB que se passe-t-il lorsqu'on
touche aux curseurs et aux courbes :

- en mode RGB (Exposure), lorsqu'on modifie la saturation, la «
  lightness » ou le contraste, on travaille en mode « rgb » ou son
  dérivé linéaire « hsv ». Ceci revient à dire que l'effet obtenu va
  dépendre de l'espace de travail (sRGB, AdobeRGB, Prophoto), les
  résultats seront différents lorsqu'on passera de « sRGB » à « Prophoto
  », même si on reste dans les limites du gamut.
- en mode Lab, lorsqu'on modifie, la « lightness », la chromaticité, le
  contraste, ou les courbes, on modifie directement les valeurs «L»,
  «a», «b» (ou «C», «h»). Ceci revient à dire que si on reste dans les
  limites du gamut, l'image sera identique (aux limites près de la
  gestion des couleurs).

Lorsqu'on dépasse le gamut – soit l'image d'origine– soit par action sur
les curseurs, ou par action sur les courbes que se passe-t-il ?

- prenons un exemple :une couleur d'origine est L=27 a=2 b=-75; cette
  couleur est dans l'espace Prophoto et vaut R=42 G=52 B=158, et en sRGB
  R=-85 G=69 B=184 (R negatif traduit le hors gamut). Si on change de «
  working profile », il est évident que cette couleur ne pourra pas être
  restituée ; la conversion XYZ aboutira à L=32 a=21 b=-67 et R=0 G=69
  B=184. La couleur sera différente en aspect car elle est totalement
  impossible à reproduire dans l'espace plus petit
- deuxième exemple : une couleur est à l'intérieur de sRGB : L=40 a=42
  b=-44 soit en RGB (sRGB) R=133 G=66 B=166, et en RGB(Prophoto) R=102
  G=64 B=140: a)Si on applique dans « exposure » de la saturation (+30),
  les valeurs vont devenir – Prophoto – L=36 a=49 b=-49 et sRGB L=38
  a=47 b=-47, car on agit sur les valeurs RGB; b) Si on applique dans «
  Lab adjustements » de la « chromaticity », les valeurs Lab deviennent
  L=40 a=55 b=-58 aussi bien dans sRGB que Prophoto, car on reste dans
  le gamut sRGB.; c) Si on choisit une couleur, assez proche des limites
  du gamut sRGB, mais dans le gamut : L=40 a=63 b=37 et on applique de
  la chomaticity +30, les valeurs Lab deviennent – Prophoto L=40 a=81
  b=49 – on remarquera que le teinte est conservée (arctg(b,a)), et en
  sRGB L=44 a=69 b=50 – la teinte n'est pas conservée

### Que fait « avoid color shift »?

Si on applique à c) ci-dessus , « Avoid color shift », le système va
essayer de préserver la teinte, en appliquant une colorimétrie relative
les valeurs Lab deviennent L=40 a=65 b=38 (ce qui aboutit au canal(RGB)
G=0). « Avoid color shift » réalise 2 choses :

- essayer de mettre dans le gamut de « working profile » des données en
  dehors de ce gamut, en privilégiant une colorimétrie relative. Les
  valeurs négatives RGB sont détectées et la chromaticité (ainsi que la
  luminance) sont modifiées pour atteindre la valeur 0.
- appliquer une correction « Munsell »

### La correction "Munsell"

Objectif : donner la possibilité à l'utilisateur de corriger
automatiquement les couleurs qui sont quelquefois fausses en mode Lab
lorsqu’on modifie la saturation, notamment dans les bleus-pourpres, les
rouges-jaunes et les verts (correction de type Munsell)

Cet objectif exige la création de 160 tables look-up avec la précision
en virgule flottante (LUTf) :

- ces LUTf donnent pour chaque couleur (au sens Munsell), chaque
  luminance, les valeurs de la teinte en fonction de la chromaticité :
  2, 3 ou 4 points sont fixés pour les chromaticités \[0..180\] de 5,
  45, 85, 125 voire 139 quand c'est possible. Les valeurs intermédiaires
  sont interpolées linéairement. Ces LUT amènent une occupation mémoire
  minime : chacune a entre 45 et 140 entrées, soit au total environ
  16000 entrées...
- Les LUTf sont réalisées pour 4 zones critiques, où la dérive par
  rapport au mode Lab est importante (bleu-pourpre, rouge-jaune, vert,
  rouge-pourpre), pour les autres zones les écarts sont faibles, en tous
  cas nettement inférieurs aux possibilités des matrices et profiles ICC
- Ces LUTf ont pour base l’illuminant C (un peu différent de D50 ou
  D65), mais du fait qu'on travaille sur des écarts et non les valeurs
  absolues, l'erreur de calcul est minime (moins de 10% de la
  correction, en tous cas nettement inférieure aux possibilités des
  matrices et profils ICC).
- Ces corrections sont rapides : néanmoins elles accroissent le temps de
  traitement « vibrance ou Lab adjustements » de l'ordre de 10%.
- Si l'option « verbose » est activée on voit apparaître, pour chaque
  type de correction, le nombre de pixels concernés et un ordre de
  grandeur de la correction (en radians). Pour les valeurs de
  corrections en radians, l’écart de couleur en deltaE94 est le suivant
  :

1.  correction=0.4 rad deltaE94=12 pour bleu-pourpre
2.  correction=0.2 rad deltaE94=8 pour rouge-jaune
3.  correction=0,1 rad deltaE94=3,7 pour vert
4.  correction=0.05 rad deltaE94=2 pour rouge-pourpre
5.  les valeurs habituelles maximales de dérives peuvent atteindre pour
    des modifications moyennes de saturation, de l'ordre de 0.05 radians
    à 0.15 radians, les valeurs de 0.2 à 0.25 radians ne sont pas
    exceptionnelles.
6.  Pour information, un deltaE94 inférieur à 1 est négligeable, il est
    notable vers 2 ou 3 et très important à 8 ou 11.

<File:Munsell-Lab-L20.jpg%7CReprésentation> des dérives de couleurs pour
L=20 <File:Munsell-Lab-L40.jpg%7CReprésentation> des dérives de couleurs
pour L=40 <File:Munsell-Lab-L70.jpg%7CReprésentation> des dérives de
couleurs pour L=70

### Espace de sortie "Output Profile"

#### Choix de l'espace

La première chose à examiner est : quels sont les profils de sortie qui
sont installés sur votre machine ? Ceci dépend : a) du système
d'exploitation (a priori Linux n'installe aucun profil); b) des autres
logiciels graphiques qui sont installés (Capture NX2, PhotoShop CS, DxO,
etc.), chacun installe des profils propriétaires, par exemple NX2
installe des NKsRGB.icm NkAdobe.icm, etc. qui sont protégés par
copyright...; c) de profils que vous pouvez avoir téléchargés sur le
web, par exemple sur le site de Adobe ou sur celui de B.Lindbloom.

Par principe je recommanderais de vérifier l'installation ou d'installer
les profils de sortie correspondants aux profils de travail (working
profile) - qui sont des fichiers \*.icm ou \*.icc présents physiquement
sur votre machine et qui n'ont rien à voir avec les matrices de calcul
de "iccmatrices.h". Si ces fichiers sont absents la sortie en TIFF ou
JPG ne pourra pas s'effectuer vers ces profils, mais sera par défaut (si
le fichier « RT_sRGB.icm » est présent) vers l'espace de sortie SRGB.

Ces profils ont les noms suivants (on peut en trouver d'autres qui ont
les mêmes caractéristiques ou des caractéristiques proches), en général
ils sont protégés par des copyright et ne peuvent donc être distribués
par un logiciel Open-Source sans autorisation. Ils sont disponibles sur
le Web : ProPhoto.icm; SRB Color Space profile.icm ; AdobeRGB1998.icc;
BestRGB.icm ; BetaRGB.icc; Bruce.icm; WideGamutRGB.icc ; Bien sûr vous
pouvez en installer d'autres comme : CIE.icc ; Colormatch.icc; etc.

Ces profils sont à installer dans le dossier "Iccprofiles/output" de RT
ou dans \windows\system32\spool\drivers\color pour Windows et
/usr/share/color/icc pour les autres systèmes.

Lorsque vous choisissez un profil de sortie, par exemple AdobeRGB1998 et
que vous avez choisi un profil de travail Prophoto, LCMS2 va convertir
avec une intention (choisie par défaut dans les options de RT :
relative, perceptuelle,...) les données RGB de l'espace de travail vers
l'espace de sortie.

<figure>
<img src="/images/GamutL50.jpg" title="Gamut pour une luminance L=50" />
<figcaption>Gamut pour une luminance L=50</figcaption>
</figure>

<File:GamutL05.jpg%7CGamut> pour une luminance L=5
<File:GamutL25.jpg%7CGamut> pour une luminance L=25
<File:GamutL75.jpg%7CGamut> pour une luminance L=75
<File:GamutL95.jpg%7CGamut> pour une luminance L=95

Bien sûr les remarques sur le choix de l'espace de sortie sont
similaires à celles de l'espace de travail (impression, écran,..).

Si vous souhaitez imprimer sur une imprimante à jet d'encre de haute
qualité (rappel RT n'a pas à ce jour de module d'impression), il faudra
passer par un logiciel tiers (Photoshop...), dans ce cas je ne saurais
que recommander un « Ouput Profile » de type Prophoto ou WideGamut.
Attention toutefois les sorties JPG donc 8 bits sont quasiment
incompatibles - risque important de postérisation - avec les espaces à
gamut important (Prophoto, WideGamut...)

#### Fichiers fournis

Du fait des copyrights, j'ai fourni des fichiers spécifiques avec des
LUT plus détaillées qui devraient apporter moins de postérisation dans
les ombres. Ces fichiers sont un sous-produit de "outout gamma" (voir
plus loin)

- RT_sRGB.icm : similaire (primaires) à sRGB.icm standard avec gamma
  interne proche de sRGB: g=2.40 pente=12.92
- RT_sRGB_gBT709.icm : semblable (primaires) à sRGB.icm standard avec
  gamma interne BT709 : g=2.22 pente=4.5
- RT_sRGB_g10.icm : semblable (primaires) à sRGB.icm standard avec gamma
  interne liénaire : g=1.0 pente=0
- RT_Middle_gsRGB.icc : semblable (primaires) à AdobeRGB1998.icc
  standard avec gamma interne proche de sRGB: g=2.40 pente=12.92
- RT_Large_gsRGB.icc :semblable (primaires) à ProPhoto.icm standard avec
  gamma interne proche de sRGB : g=2.40 pente=12.92 (proche de « Melissa
  » utilisé par Lightroom)
- RT_Large_gBT709.icc :semblable (primaires) à Prophoto.icm standard
  avec gamma interne BT709 : g=2.22 pente=4.5 :
- Rec2020.icm : nouvelles primaires - profil à gamut élevé (inférieur à
  Widegamut) avec gamma interne BT709 : g=2.22 pente=4.5

#### Lacunes de RT

L'utilisateur peut facilement constater que la sortie « output » est
légèrement différente de « preview ». Cela ne tient pas à un défaut de «
output » mais à l'élaboration des « curves » qui prennent mal en compte
la notion de TRC (incorporation de profil ICC, pour modifier de
l'intérieur le rendu des tons)

C'est une des raisons qui m'a amené à donner la possibilité de sorties
"variables" :

- soit en choisissant un profil de sortie avec un autre gamma ;
- soit avec un gamma variable (gamma et pente)
- soit éventuellement de réaliser une sortie linéaire et l'ajuster dans
  Photoshop...
- (voir plus loin les schéma des histogrammes)

#### Output Gamma

De mon point de vue, Output Gamma, est un des points clefs d'une sortie
réussie en TIFF ou JPEG, pour plusieurs raisons : depuis l'ajout des
profils icc/icm ci-dessus- qui sont directement dérivés et élaboés par
Output gamma- cette option présente un intérêt moins important car
l'utilisation de ces pseudos profils Prophoto et SRGB « nouveaux »
apporte des avantages similaires à Output Gamma lorsqu'on sélectionne
les pseudo sRGB et Prophoto ! (voir ci-dessus). Cette option permet de
palier partiellement la lacune de RT (différence « output » / « preview
») ;

L'idéal aurait été de mettre "Output gamma" en premier traitement avant
les onglets "Exposure", "Highlights reconstructions" ,
"Shadows/highlights", etc.; mais et c'est je pense une lacune de RT,
cette modification s'est avérée impossible sans amener d'importants
artefacts : les différents "pipelines" de RT s'imbriquent et la
colorimétrie dans la partie initiale du traitement ressort plus à du «
bricolage » qu'à un traitement professionnel...

J'ai donc choisi d'implanter ce processus en phase terminale, ce qui
n'est pas totalement incongru (même si je pense cela aurait été mieux en
phase initiale). Ouput Gamma, va permettre :

- une évaluation de l'image pour les logiciels sans gestion des couleurs
- une modification de l'image si vous imprimez en CMJN (bien sûr à
  l'aide d'un logiciel tiers).

#### Quelques réflexions

Le gamma agit de manière un peu similaire à une combinaison entre
"Exposure curves" + "black point" + "tonecurves" présentes dans
Rawtherapee, mais modifient de manière plus radicale les contrastes, la
répartition de l'histogramme notamment entre les basses lumières et les
hautes lumières, en modifiant simultanément (ce que ne peut faire les
fonctions précédentes), les courbes TRC de l'entête du fichier
similaires à un profil ICC d'entrée. Un ami photographe me disait
récemment: "au début je pensais qu'on pouvait simuler le gamma par des
contrastes, et courbes tonales..mais le résultat est différent"

Pourquoi en effet Adobe avec Lightroom a-t-il fabriqué "Melissa" qui est
un espace colorimétrique Prophoto avec un gamma sRGB, c'est-à-dire une
partie linéaire jusque r=12.92 puis un gamma de 2.4 ?

Pourquoi D.Coffin a implanté dans Dcraw depuis longtemps un gamma
linéaire, ainsi qu'un gamma variable ?

En théorie, si la gestion des couleurs est parfaite, quelque soit le
gamma de sortie (standard, variable...) l'image devrait être identique,
car la gestion des couleurs se sert des données Lab (ou XYZ) et de ce
qu'on appelle le PCS (Profil Connexion Space en D50) ; en pratique
l'image à l'air semblable, mais si on examine les basses lumières on
peut se rendre compte qu'il y a des écarts, certes assez faibles mais
suffisants pour que des utilisateurs de RT aient pu dire : l'image de
sortie est différente de « preview ».

D'autre part, pour les logiciels qui ne gèrent pas les couleurs comme
beaucoup de navigateurs Web (Chrome,...) l'image de sortie va dépendre
du gamma; il est donc important que RT permette de visualiser ce que
sera le fichier de sortie (softproofing). Plusieurs facteurs doivent
être pris en compte à ce jour :

- conversion de l'espace de travail (« working profile ») vers l'espace
  de sortie (Output profile) : il peut sembler évident que si l'image à
  des couleurs hors gamut pour un des deux espaces ou pour les deux, si
  l'étendue des espaces est différente, le rendu des images sera
  différent ;
- présence ou non de la gestion des couleurs : dans le cas de RT, ou
  d'un éditeur qui gère les couleurs, les écarts (à espace de sortie et
  de travail identiques) seront faibles mais néanmoins significatifs ;
  dans le cas de logiciels qui ne gèrent pas les couleurs l'incidence du
  gamma sera très importante
- possibilité de paramétrer dans le softproofing, l'intention et le
  point noir.
- À terme il doit être assez facilement possible de simuler une
  impression en convertissant la sortie vers le profil de l'imprimante;
  à noter que dans ce cas, une visualisation des couleurs imprimables
  serait un plus important.

Lorsque Rawtherapee disposera d'une fonction similaire à celle de
Photoshop CS « Format d'épreuve - Couleurs d'épreuve », le problème de
visualisation de « Ouput gamma » sera résolu!Cette fonction permet le «
soft proofing », par exemple pour simuler l'aspect qu'aura un fichier
dans le Web ou encore sur une imprimante CMJN.

#### Les divers Output Gamma

Dans le menu déroulant vous disposez de 7 gamma prédéfinis :

- BT709 : pente=4.5 gamma=2.2
- sRGB : pente=12.92 gamma=2.4
- linear : gamma=1.0
- standard : pente=0 gamma=1.8
- standard : pente=0 gamma=2.2
- High : pente=3.35 gamma=1.3
- Low : pente=6.9 gamma=2.6

BT709 " va mieux traiter les ombres (elles seront moins grises) que sRGB
et a fortiori standard 2.2 ou 1.8

"Low" va augmenter le contraste des images un peu pauvres, et permettre
un meilleur post-traitement des images surexposées

"High" à l'inverse va réduire le contraste...

Linear : permet un traitement dans Photoshop des images à très haute
dynamique en ajustant dans Photoshop les courbes RGB (exercice
difficile...)

De plus vous avez la possibilité de "free gamma" qui permet d'associer à
un profil de sortie n'importe quelle valeur de pente et de gamma, ainsi
vous pouvez si vous le souhaitez sortir en dehors des nouvelles sorties
liées aux nouveaux profils icc/icm ajoutés :

- sRGB avec gamma standard 1.8
- WideGamut avec gamma BT709
- sRGB avec gamma : 2.2 et pente 6.5

A titre d'exemple voici avec le même fichier NEF divers histogrammes
avec divers gamma et en référence l'histogramme RT (preview) avec les
mêmes réglages (espace de travail Prophoto, profile « neutral », output
profile = Prophoto et ses variantes en gamma).

![Preview Prophoto](RT_prev_Prophoto.jpg "Preview Prophoto")
![<File:GammaS.jpg>](GammaS.jpg "File:GammaS.jpg") Plus l'histogramme
sera décalé vers la gauche, plus l'image paraîtra sombre... De plus, ce
n'est pas parce que les histogrammes sont strictement semblables que le
rendu des images sera semblable. En effet intervient la notion de « TRC
» aussi bien pour le « preview » que pour le fichier de sortie. Cette «
TRC » agit sur l'entête du fichier (profil ICC) et modifie les données
tonales. Si la valeur « TRC » du fichier de sortie est à coup sûr bonne,
car elle est déterminée par les caractéristiques du fichier de sortie
(Prophoto.icm, RT_srgb.icc,...), je pense qu'il n'en est pas de même
pour le « preview »...(voir plus loin les remarques sur la sortie sRGB)

Certains pourraient avoir des inquiétudes est-ce que "RT_SRGB" est
identique à "sRGB_Color_Space_Profile" et de différences avec le
preview. De plus quelle est l'incidence d'un autre gamma

<File:RT_prev_sRGB.jpg%7CPreview> en SRGB <File:RT_sRGB.jpg%7COutput>
RT_sRGB <File:SRGB_color_space.jpg%7COutput> sRGB_Color_space_Profile
<File:RT_sRGB_gBT709.jpg%7COutput> sRGB gamma BT709
<File:RT_sRGBg23p8.jpg%7COutput> sRGB gamma=2.3 pente=8

#### Comment s'en servir ?

Par souci de simplicité, le profil de sortie sera "dérivé" du profil de
travail "working profile", la case "Output Profile" apparaît en grisé.
Ce qui revient à dire que Profil de sortie = Profil de travail.

Par exemple vous sélectionnez "working Profile"=Prophoto et Free gamma =
2.1 et pente=4.0.

Puis vous validez une sortie TIF ou vers l'éditeur et vous générez un
fichier TIF en sortie, avec profil Prophoto et gamma 2.1 / 4.0. Lorsque
vous voudrez ouvrir le fichier dans un éditeur externe (par exemple
Photoshop CS), il apparaîtra «Préférer le profil incorporé : Large_B709
», qui correspond au profil RT_Large_gBT709, mais avec une modification
que nous examinerons plus loin.

Autre exemple, vous sélectionnez « Working profile »=sRGB et Free
gamma=2.3 et pente=10.0, vous allez générer un TIFF avec sortie sRGB et
gamma 2.3 et pente=10. Lorsque vous voudrez ouvrir le fichier dans un
éditeur externe (par exemple Photoshop CS), il apparaîtra « Préférer le
profil incorporé : sRGB IEC61966-2.1 (RTH gamma BT709 similar to HP
sRGB)» qui correspond au profil RT_sRGB_gBT709 mais avec une
modification que nous examinerons plus loin.

Si vous validez l'option (Photoshop CS) : « Supprimer le profil
incorporé », le fichier TIFF apparaîtra avec les nouvelles valeurs RGB
dues aux nouvelles valeurs de gamma et pente, mais l'apparence de
l'image sera différente (absence d'entête de fichier)

L'algorithme utilise la fonction "CMSToneCurve" de LCMS :

- les espaces de sortie sont calculés à partir de leurs primaires
  (rouges, vert, bleu) par exemple pour Prophoto : p1=0.7347; p2=0.2653;
  p3=0.1596; p4=0.8404; p5=0.0366; p6=0.0001;
- les paramètres du gamma sont calculés avec la fonction "calcgamma" qui
  va en fonction du gamma et de la pente déterminer 5 paramètres à
  passer à la fonction adhoc de LCMS2.

On crée ainsi un pseudo profile, de type RGB "Prophoto" et avec un gamma
correspondant à celui sélectionné

Mais on retrouve ici une lacune de LCMS2 qui en créant ce profil
n'indique pas dans l'entête du fichier le profil correspondant, car il
travaille en valeur RGB et non en LUT / Lab. En théorie il faudrait
autant de profil avec un gamma adapté et non un seul. En pratique j'ai
apporté une profonde modification à « Output Gamma » et contourné la
lacune de LCMS2, en appliquant – après la conversion RGB, un profil
\*.icc qui a les mêmes caractéristiques que les profils \*.icc ou \*.icm
qu'utilise « Output Gamma », mais où les Tag rTRC, gTRC, bTRC sont
calculées avec « calcgamma ».

Pour améliorer la compréhension du traitement d'un TIF en mode linéaire,
vous pouvez consulter le tutoriel(Dcraw) de Guillermo Luijk
<http://www.guillermoluijk.com/tutorial/dcraw/index_en.htm>

D'où la nécessité d'avoir dans le dossier "Iccdirectory" les fichiers
"\*.icc" et"\*.icm" : BestRGB.icm ; BetaRGB.icc; Bruce.icm;
WideGamutRGB.icc, (ainsi que les fichiers icc/icm ajoutés pour les
pseudo Prophoto , Adobe, SRGB dans « Iccprofile/output »).

#### Qualité des profils RT

L'utilisateur peut à juste titre se poser la question de la validité des
profils « RT » (RT_sRGB, RT_Large,...).

Ces profils ont les mêmes caractéristiques que les « originaux »
(AdobeRGB1998, Prophoto, SrGB Color Space Profile), seules apparaissent
de petites différences au niveau des primaires et/ou des points blancs
qui n'ont aucune incidence sur la qualité et le niveau des sorties.

Par contre les TRC ont des LUT plus détaillées passant de 1024 points à
4096 points. Ceci a pour conséquence – dans le cas de sRGB qui est la
sortie la plus fréquente – un histogramme avec beaucoup moins d'arêtes
de poissons qui peuvent amener dans les ombres des postérisations. Voici
à titre de comparaison avec la même image, l'agrandissemnt de
l'histogramme 16 bits dans les basses lumières, entre « sRGB Color Space
profile » et « RT_sRGB »

<File:SRGB16bits.jpg%7Chistogramme> partiel 16 bits
sRGB_color_space_profile <File:RT_sRGB16bits.jpg>\| histogramme partiel
16 bits RT_sRGB
