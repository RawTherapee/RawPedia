---
title: Local Adjustments
contributors:
  - Jdc
  - Sguyader
  - DrSlony
tags:
  - 'Tool Description'
  - 'Selective Editing'
---

<div class="pagetitle">

Contrôles Locaux Lab

</div>

Texte original rédigé par Jacques Desmis (mise à jour 3 décembre 2022).

Les lecteurs de la version en langue française, peuvent s'étonner de
voir les titres des rubriques, champs, bouton à cocher, etc. utiliser la
langue anglaise, plutôt que le français, par exemple "Color & Light", au
lieu de "Couleur & Lumière". C'est le résultat d'un compromis, pour
plusieurs raisons:

- la totalité des échanges sur la mise au point de "Ajustements locaux"
  se fait en anglais (forum, issues, Pull Request), et donc la version à
  jour est obligatoirement celle en anglais (langue que je maîtrise très
  mal);
- je suis le seul rédacteur pour "Ajustements Locaux", "Local
  adjustments" de Rawpedia. Bien sûr la première version est rédigée en
  francais mais les captures d'écrans où on voit apparaître les réglages
  dans le panneau de droite, doivent être en anglais, car Rawpedia est
  complexe. Le faire en plusieurs langues m'aurait obligé à le faire
  aussi en allemand, espagnol, etc., d'où un travail considérable...que
  je ne sais évidemment pas faire, ce qui est impensable. En conséquence
  ce qui apparaît est en anglais (outils, curseurs, boites de dialogues,
  etc.);

Je souhaite bon courage aux traducteurs dans les autres langues!

J'espère que vous comprendrez ce compromis.

Merci

Jacques

## Introduction

L'édition locale dans RawTherapee est basée sur des Spot RT, qui sont
similaires dans leur principe au concept U-Point utilisé à l'origine
dans Nikon Capture NX2, puis dans la Nik Collection, DxO PhotoLab et
Capture NXD. Les RT-spots utilisent des algorithmes développés
spécifiquement pour RawTherapee par Jacques Desmis.  
Cette approche est complètement différente des méthodes d'édition
locales plus familières utilisées dans des applications telles que GIMP,
Photoshop, etc., qui utilisent principalement des outils de sélection
tels que des lassos, des baguettes magiques, etc., associés à des
pinceaux, des calques et des masques de fusion. Ces méthodes peuvent
prendre du temps et être difficiles à utiliser avec précision lorsque
des formes complexes sont impliquées.  
Un point RT se compose soit d'une ellipse, soit d'un rectangle avec un
cercle de diamètre variable au centre. Les formes ont quatre points de
contrôle, qui peuvent être ajustés indépendamment ou symétriquement. Le
spot rectangulaire peut également être utilisé en mode plein écran qui
définit automatiquement les points de contrôle en dehors de la zone de
prévisualisation de l'image. Les développements futurs fourniront une
manipulation de forme améliorée.

<div align="center">

<File:ellipse.jpg%7CEllipse>. <File:rectangle.jpg%7CRectangle>.

</div>

L'algorithme RT-spot utilise une détection de forme basée sur ΔE (le
changement de la perception visuelle de deux couleurs données) pour
sélectionner les parties de l'image à modifier à l'intérieur de
l'ellipse ou du rectangle. Les valeurs de référence utilisées pour
l'algorithme de détection de forme sont basées sur la moyenne des
valeurs de teinte, de saturation et de luminance à l'intérieur de
l'ellipse ou du rectangle de taille variable. Cela signifie qu'en mode
plein écran (ainsi qu'en mode Normal ou Exluding), ces valeurs et la
détection de forme qui en découle peuvent varier en fonction de la
position du cercle.

La mesure dans laquelle ces modifications sont appliquées peut être
finement contrôlée permettant des sélections très précises. Un ajout
supplémentaire est possible avec des masques paramétriques
supplémentaires, mais les algorithmes de détection de forme devraient
être suffisants pour la grande majorité des exigences d'édition locales.
Les RT-spot peuvent également être utilisés en mode "excluding spot"
pour empêcher l'algorithme d'influencer certaines parties de l'image.
Les modifications pouvant être effectuées sont importantes et intègrent
la plupart des fonctions disponibles dans les outils de réglage global
de RawTherapee ainsi que quelques outils supplémentaires disponibles
uniquement dans l'onglet Réglages locaux.

Remarque : tant que la case à cocher "Avoid Color Shift" dans le module
Paramètres n'a pas été désactivée, les opérations suivantes seront
effectuées sur les données avant et après l'activation de tout RT Spot.

- Une correction colorimétrique relative pour conserver les données dans
  le gamut.
- Une correction Munsell (qui peut être utilisée seule, sans le contrôle
  du gamut) utilisant des LUT pour garantir que les données restent
  linéaires et éviter les changements de teinte.

.

### Les outils

Les outils sont regroupés dans les modules suivants (Nom de l'outil -
position dans le pipeline) :

#### Color & Light - 11

Ajuste la couleur, la luminosité, le contraste et corrige les petits
défauts tels que les yeux rouges, la poussière du capteur, etc. D'autres
fonctions incluent un filtre gradué, des courbes L\*a\*b\* et des modes
de fusion.

#### Shadows/Highlights & Tone Equalizer - 6

Ajuste les ombres et les lumières avec les curseurs d'ombres/lumières,
un égaliseur de tonalité (Tone Equalizer) ou une courbe de réponse de
tonalité "Tone Response Curve (TRC)". Peut être utilisé à la place ou en
conjonction avec le module d'exposition. Peut également être utilisé
comme filtre gradué.

#### Vibrance & Warm/Cool - 5

Ajuste la vibrance (pratiquement identique à l'ajustement global).
Effectue l'équivalent d'un réglage de la balance des blancs à l'aide
d'un algorithme CIECAM.

#### Log Encoding - 0

Ajuste les images sous-exposées ou à plage dynamique élevée à l'aide
d'un algorithme codé logarithme.

#### Dynamic Range & Exposure - 10

Modifie l'exposition dans l'espace L\*a\*b\* à l'aide d'un algorithme à
base de Laplacien PDE pour prendre en compte deltaE et minimiser les
artefacts. Les opérateurs laplaciens sont utilisés car ils sont
particulièrement bons pour détecter les détails fins mais vous n'avez
pas besoin de comprendre leur fonctionnement pour utiliser cet outil !

#### Common Color Mask - 12

Un outil à part entière. Il permet de régler l'aspect de l'image
(chrominance, luminance, contraste) et sa texture en fonction de la
portée (Scope).

#### Soft Light & Original Retinex - 7

Applique un mélange de lumière douce (identique à l'ajustement global).
Effectue un "dodge and burn" en utilisant l'algorithme Retinex original.

#### Blur/Grain & Denoise - 1

Peut être utilisé pour flouter les arrière-plans, adoucir la peau,
ajouter du grain de film et débruiter

#### Tone Mapping - 2

Identique à l'outil de Tone mapping du menu principal. L'outil du menu
principal doit être désactivé si cet outil est utilisé .

#### Dehaze & Retinex - 3

Dehaze et Retinex (mode avancé uniquement). Utile pour retirer la brume,
le contraste local avec des valeurs élevées et la simulation de la
"clarté" (clarity).

#### Sharpening - 8

Utilise RL deconvolution sharpening. Visualiser à 1:1

#### Local Contrast & Wavelets - 8

Contraste local : essentiellement les mêmes fonctions que le Contraste
local de l'onglet Détails. Ondelettes : basé sur Niveaux d'ondelettes
(wavelet) dans l'onglet Avancé, avec essentiellement les mêmes fonctions
(clarté, contraste, flou, etc., voir la documentation). Des fonctions
supplémentaires telles que le filtre gradué (Graduated Filter), Tone
mapping, etc. ont également été incluses. Son utilisation dans les
Réglages locaux offre des possibilités supplémentaires telles que
l'élimination de gros défauts, de taches de graisse, etc.

#### Contrast By Detail Levels - 4

Contrast by detail levels :Peut être utilisé pour éliminer les marques
du capteur (graisse,..) ou de l'objectif.

#### Color appearance(Cam16 & Jzcz) - 12

Ce module est une version simplifiée du module Color Appearance &
Lighting(Ciecam02/16) de l'onglet Avancé du menu principal, qui a été
adapté aux exigences spécifiques des réglages locaux. Il a également été
étendu pour prendre en compte le pic de luminance HDR et inclut une
fonction expérimentale JzCzHz (en mode Avancé) pour améliorer le
traitement HDR.

Chaque module d'outil peut être basculé entre les modes de complexité:
basic, standard et advanced. Le mode par défaut peut être défini dans la
fenêtre Préférences de RawTherapee.

## Comment démarrer - premiers pas

Les exemples qui suivent sont conçus pour donner un aperçu de certaines
des façons dont les différents outils peuvent être utilisés pour les
ajustements locaux. Toutefois, si vous préférez explorer les
possibilités par vous-même, essayez de régler la "complexité par défaut
des ajustements locaux" dans le module Préférences sur Basic et décochez
la case "Afficher les paramètres supplémentaires" en haut du module
Ajustements locaux. Vous obtiendrez ainsi une version simplifiée mais
puissante des ajustements locaux.

De mon point de vue, Basic est le mode qui correspond le mieux (absence
de masques et généralement de courbes) à mon intention initiale en 2015.

Pour commencer, explorez les capacités des outils "Color & Light",
"Shadows/Highlights & Tone Equalizer" et " Vibrance & Warm/Cool " et
n'hésitez pas à essayer les fonctionnalités supplémentaires en réglant
manuellement le mode de complexité sur Standard (dans la boîte combo du
module sur lequel vous travaillez).

L'outil Color & Light est extrêmement puissant et comprend des fonctions
du module "Coor Toning \> Color corrections Région" dans l'onglet
Couleur du menu principal ainsi que les courbes L\*a\*b\* disponibles
dans l'onglet Exposition. Remarque : les captures d'écran des exemples
suivants sont actuellement mises à jour pour tenir compte des derniers
développements. De ce fait, certains noms de curseurs et de modules
seront différents du texte.

### Premiers pas

#### Démarrage

- Dans la barre des onglets, sélectionnez la "main" (Onglet Local)
- Puis activez "expander" "Local Adjustments" (si il n'est pas déjà
  activé)
- Sélectionnez "Add"

<div>

<img src="/images/startspot.jpg" title="startspot.jpg" width="600"
alt="startspot.jpg" /> Fichier raw (Jacques Desmis - Creative Common
Attribution-share Alike 4.0):
[1](https://drive.google.com/file/d/1X2g73FqzQl7-WRfzhF7zHa7XWwnKcwtx/view?usp=sharing)

</ul>
</div>

#### Préparation

Positionnez le RT-spot à l'endroit souhaité. Dans ce cas, je souhaite
accroître la saturation de la fleur rouge et réduire la luminance
(lightness) sans affecter le reste de l'image:

- déplacez le centre du RT-spot de telle manière que son centre soit
  situé sur une zone représentative de ce que vous souhaitez changer.
- positionnez les 4 délimiteurs largement au delà de la fleur.
- sélectionnez le "Lockable color picker" et repérez 3 couleurs : a) une
  sur la fleur rouge, b) une sur le ciel bleu, c) une sur une feuille
  verte
- Dans l'exemple les 3 couleurs sont:
  - fleur rouge L=48.6 a=74.4 b=47.0
  - ciel bleu : L=68.6 a=-3.1 b=-16.6
  - feuille verte : L=48.3 a=-28.3 b=51.4

<figure>
<img src="/images/prepare1.jpg" title="prepare1.jpg" width="600" />
<figcaption>prepare1.jpg</figcaption>
</figure>

#### Ajouter l'outil Color & Light

Voir dans "Quelques particularités du mode local (par rapport à Lab
adjustments)": [Particularités Color &
Light](Local_Lab_controls/fr#Color_&_Light.md)

Dans le menu settings, choisissez "Add tool to current spot..."

- une liste de choix vous est proposée : "Color&light 11",..., "Log
  Encoding 0". Pour chaque RT-spot vous pouvez associer 1 ou plusieurs
  outils de la liste. L'ordre de traitement dans le processus correspond
  au numéro à la fin du choix : "Encoding Log - 0" est le premier
  traitement (si bien sûr il est activé), "Color&light(defects) -11" est
  le dernier. Ceci est également vrai pour les masques associés.
- sélectionnez "Color & Light (Defects) - 11"

<figure>
<img src="/images/addtoolcolorandlight1.jpg" title="addtoolcolorandlight1.jpg"
width="600" />
<figcaption>addtoolcolorandlight1.jpg</figcaption>
</figure>

#### Réglez la luminance (lightness) et la chrominance

- réglez la luminance sur -70
- réglez la chrominance sur 130

<!-- -->

- Examinez les résultats
- la fleur rouge a une nouvelle couleur L=41.3 a=66.0 b=50.4
- le ciel est inchangé
- la feuille verte est inchangée

<figure>
<img src="/images/lightchro1.jpg" title="lightchro1.jpg" width="600" />
<figcaption>lightchro1.jpg</figcaption>
</figure>

#### Essayez Scope Color Tools - Transition

Dans le menu "settings"

- Agissez sur "Scope Color Tools"
  - si vous réduisez la valeur (par défaut 30) seule une partie des
    rouges sera concernée.
  - si vous accroissez la valeur, progressivement le ciel, puis la
    feuille verte, puis toute l'image sera concernée (Scope=100)

Laissez la valeur Scope à 100 et dans le menu "settings"

- Agissez sur transition:
  - essayez de réduire vers 5
  - essayez d’accroître vers 100 et constatez le résultat

#### Prévisualisez la zone modifiable - deltaE - ΔE

Vous pouvez avoir un aperçu des zones de l'image qui seront touchées par
les modifications - cela ne montre pas les modifications, ni les
transitions, mais permet de régler "Scope". Deux possibilités:

- utiliser le bouton "Preview ΔE" situé dans "settings" et un et
  seulement un, outil doit être activé (expander)
- utiliser dans "Mask and modifications" - "Preview deltaE" - dans ce
  cas le GUI prend en compte l'état des outils - cette option fonctionne
  quelque soit le nombre d'outils activés.

Vous pouvez faire varier l'intensité et la couleur de cette
prévisualisation avec "ΔE preview color - Intensity" Vous pouvez aussi
voir l'action des divers réglages possibles relatif à la détection de
forme : essayez les curseurs de "Shape detection" à l'exception de
Threshold structure.

<figure>
<img src="/images/previewdeltae1.jpg" title="previewdeltae1.jpg" width="600" />
<figcaption>previewdeltae1.jpg</figcaption>
</figure>

#### Voir les modifications

Vous pouvez avoir un aperçu des modifications que vous avez réalisées:

- Allez à "Mask and modifications" - "Show modifications without mask"

<!-- -->

- vous pouvez visualiser les incidences de la luminance, du contraste,
  des changements de couleurs et saturation, structures,...
- vous pouvez aussi visualiser l'incidence des réglages de la transition
  (settings) :
  - transition value : pourcentage géographique entre pleine action et
    action décroissante (jusque zéro)
  - transition decay (linear-log) : "vitesse" d'affaiblissement de la
    zone d'action décroissante
  - transition différentiation XY : différence entre abscisse et
    ordonnée

Essayez ici tous les réglages:

- ceux de Scope (deltaE)
- ceux des transitions
- les réglages de l'outil (luminance, chroma, etc.)

<figure>
<img src="/images/showmodif.jpg" title="showmodif.jpg" width="600" />
<figcaption>showmodif.jpg</figcaption>
</figure>

#### Travailler en Image entière et utiliser "excluding" spot

Local adjustments ne se limite pas aux retouches locales. Vous pouvez
profiter des ressources de ce module pour traiter l'image entière.
Actuellement ce mode est "manuel", une automatisation du GUI est
prévue...

Choisissez dans "settings" :

- Shape RT-spot area = rectangle
- positionnez les 4 délimiteurs en dehors de la prévisualisation
  (preview)
- réglez la transition sur 100 (ou une autre valeur si vous le
  souhaitez... pour générer un gradient), mais il y a d'autres outils
  pour réaliser des gradients!

Vous êtes prêts maintenant pour utiliser l'ensemble des outils en mode
pleine image <img src="/images/fullim1.jpg" title="fullim1.jpg" width="600"
alt="fullim1.jpg" />

#### Combinaison d'outils avec un seul RT-spot

La plupart des outils d'ajustement local peuvent être utilisés ensemble
dans le même RT-Spot. Cependant, les combinaisons de Log Encoding, Tone
Mapping et Retinex doivent être évitées. En effet, le fichier de sortie
TIFF ou JPG peut ne pas correspondre à l'aperçu, en particulier lorsque
celui-ci a été agrandi à l'aide de la fonction zoom.

L'association de l'un des outils ci-dessus avec les autres outils
d'ajustement local, tels que Color & Light, ne pose pas de problème.

Si vous souhaitez utiliser des combinaisons des 3 outils mentionnés
ci-dessus, vous pouvez simplement ajouter un autre RT-Spot à proximité
du premier.

Par exemple, le premier RT-Spot pourrait être consacré à Log Encoding,
et le second à la cartographie des tons ou au Retinex. D'autres outils
peuvent être ajoutés à l'un ou l'autre des deux points RT selon les
besoins.

### Exemples concrets

#### Changer la couleur des feuilles vertes - sauf une

##### Changer le couleur des feuilles

- L'utilisation des composantes "a" et "b" de "Lab" dans "Color grid
  correction", en choisissant "direct" et une valeur élevée de
  "Strength", amène un changement de couleur de toutes les feuilles.
- Vous pouvez adapter si nécessaire avec "Scope color tools"
- Les autres couleurs : fleur, ciel ne sont pas modifiées

\[[la couleur des
feuilles](File:colorleav1.jpg%7C600px%7Cthumb%7Ccenter%7CChanger)

##### Une des feuilles redevient verte

- Ajouter un deuxième RT-spot (add)
- choisir Spot Method = Excluding Spot
- déplacer le RT-spot vers la feuille à conserver - encadrer largement
- agir sur "Scope excluding" (settings) jusqu'à obtenir l'effet désiré
- vous pouvez utiliser le "Excluding spot" comme un RT-spot normal et si
  nécessaire utiliser tous les outils disponibles notamment Denoise,
  Blur, etc.

<figure>
<img src="/images/excluding1.jpg" title="excluding1.jpg" width="600" />
<figcaption>excluding1.jpg</figcaption>
</figure>

#### Traiter les yeux rouges - retirer les défauts du capteur

Voir dans "Cas d'usage spécifique : réduction des défauts": [Réduction
des
défauts](Local_Lab_controls/fr#Cas_d'usage_spécifique_:_réduction_des_défauts_(capteur_sale,_yeux_rouges,_...) "wikilink")

Traiter les yeux rouges - 3 étapes : préparation, régler le RT-spot,
supprimer le rouge

##### Préparation

- Choisissez une sélection large autour de l’œil
- mettez le RT-spot sur la zone rouge de l’œil (pupille)
- mettez 4 "Lockable color pickers" pour repérer les changements

<figure>
<img src="/images/Redeye_prepare1.jpg" title="Redeye_prepare1.jpg"
width="600" />
<figcaption>Redeye_prepare1.jpg</figcaption>
</figure>

##### Régler le RT-spot

- Ajoutez l'outil "Color & light"
- Pressez le bouton dans "Settings" "Preview deltaE"
- Réglez le RT-spot pour obtenir l'effet désiré au niveau de la
  sélection
  - Ici j'ai choisi de réduire la taille du centre (Spot size) = 14
  - Scope color tools = 18

<figure>
<img src="/images/Redeye_previewdE1.jpg" title="Redeye_previewdE1.jpg"
width="600" />
<figcaption>Redeye_previewdE1.jpg</figcaption>
</figure>

##### Supprimer le rouge

- dans l'outil "Color & light", réduisez la chrominance à -100
- examinez le résultat :
  - la pupille de l’œil n'a quasiment plus de dominante de couleur
  - l'iris, la cornée et la peau du visage sont inchangés
  - vous pouvez être amenés selon les cas, à changer les valeurs des
    "transitions" (plus faibles) et "transition decay" plus élevée

<figure>
<img src="/images/Redeye1.jpg" title="Redeye1.jpg" width="600" />
<figcaption>Redeye1.jpg</figcaption>
</figure>

##### Même démarche pour retirer les défauts de capteur ou les taches

Vous pouvez utiliser le même principe pour retirer les petits défauts de
capteur, mais avec d'autres outils

- soit avec Contrast By Detail Levels)
- soit avec Wavelet pyramid2 - Contrast by levels
- dans les 2 cas, réduisez le contraste pour les bas niveaux de
  décomposition
- agissez éventuellement sur Blur levels (wavelet pyramid1)
- Utilisez de faibles valeurs de "transition" (moins de 20) et
  d'importantes valeurs de "transition decay" (plus de 15)
- la taille minimale du RT-spot dans ces 2 cas est de 32x32 - ce qui n'a
  que peu d'incidences

###### Un exemple - retirer de nombreuses taches avec wavelet pyramid2

- constat

<img src="/images/Blotches.jpg" title="Blotches.jpg" width="600"
alt="Blotches.jpg" />

- une solution possible
- activez l'outil "local contrast - wavelets"
- choisissez "advanced", puis "wavelet"
- réglez scope vers 20
- allez dans Pyramid2 et activez "Contrast by level"
- réglez avec des valeurs élevées de "Attenuation Response", "Offset",
  "Chroma levels" (si nécessaire)
- activez la courbe "Contrast by level" en réduisant le contraste pour
  les faibles niveaux.

<img src="/images/Blotchesless1.jpg" title="Blotchesless1.jpg" width="600"
alt="Blotchesless1.jpg" />

#### Comment réaliser un Dodge and burn (Éclaircir et brûler)

Voir dans "Quelques particularités du mode local (par rapport à Lab
adjustments)":[Original
Retinex](Local_Lab_controls/fr#Original_Retinex.md)

Dans beaucoup de portraits, ou de photos où la peau est exposée à la
lumière, il se produit un phénomène peu agréable d'accroissement de
contraste, certaines parties de la peau sont légèrement surexposées,
alors que d'autres sont légèrement sous exposées.

- traditionnellement ce problème est traité avec des masques et des
  calques - il est existe de nombreux tutoriels avec Photoshop (C). Vous
  pouvez aussi probablement le traiter avec les masques incorporés dans
  RT "Local adjustments"
- d'autres techniques permettent un traitement localisé avec des
  brosses, faisant ou non appel à des processus automatiques de
  traitement.
- ce que je propose ici est tout autre, il s'agit d'utiliser le concept
  de "Original Retinex" (Provient de la recherche Ipol) - ce pourquoi a
  été élaboré Retinex dans les années 1970 et non l'usage qui en a été
  fait ailleurs - y compris ici dans Rawtherapee:
  - utiliser un ou plusieurs Laplaciens à seuil réglable
  - résoudre l'équation de Poisson (PDE - Équation aux dérivées
    partielles)
  - équilibrer les luminances.

Je ferais la démonstration en 3 étapes : préparation, réglages du
Laplacien et aperçu des modifications, résultat

##### Préparation

- Je ne reprendrais pas les étapes de réglage du deltaE (attention à
  utiliser le Scope de Original Retinex), ni des transitions, les
  principes sont identiques aux exemples précédents
- j'ai choisi un portrait, mais par souci de confidentialité j'ai masqué
  les yeux.
- choisir "Add tool to current spot..." : "Soft Light - Original
  Retinex" - "Advanced" - "Original Retinex"

<img src="/images/Dodgeburn1.jpg" title="Dodgeburn1.jpg" width="600"
alt="Dodgeburn1.jpg" />  

##### Réglages du Laplacien et aperçu des modifications

- Agir sur le curseur : Strength (qui prend en compte le seuil du
  premier Laplacien)
- Agir sur le curseur : Laplacian threshold deltaE (qui prend en compte
  le deltaE de l'image pour agir sur un deuxième Laplacien). Ce
  traitement est en amont des algorithmes Scope - et peut prendre en
  compte les différences dans les arrières plans...
- Visualiser les modifications en choisissant: "Show process Fourier" :
  "show modifications without mask"

<img src="/images/Dodgeburnshow1.jpg" title="Dodgeburnshow1.jpg" width="600"
alt="Dodgeburnshow1.jpg" />

##### Résultats

<img src="/images/Dodgeburnmodif1.jpg" title="Dodgeburnmodif1.jpg" width="600"
alt="Dodgeburnmodif1.jpg" /> Un algorithme similaire est utilisé dans
"Exposure" - Laplacian PDE IPOL Contrast attenuator" - il permet de
traiter des images avec d'importants écarts d'exposition, souvent
globalement sous-exposées.

#### Réaliser un "Graduated Filter" Luminance - Chrominance et Teinte (filtre dégradé)

A voir dans Principes généraux [Graduated Filter Luminance Chrominance
Teinte](Local_Lab_controls/fr#Algorithme_complémentaire_:_Graduated_Filter_-_GF.md)

Toujours à titre de démonstration, je vais utiliser les possibilités de
réaliser un Filtre dégradé à la fois pour la luminance, la chrominance
et le teinte (hue).

##### Préparation

- je choisis l'image qui a servi au démarrage
- Je repère 7 points avec un "Lockable color picker"
- Add tool to current spot..." - "Color & Light" - "Advanced"

<img src="/images/gradprepa1.jpg" title="gradprepa1.jpg" width="600"
alt="gradprepa1.jpg" />` `

Fichier raw (Creative Common Attribution-share Alike 4.0):
[2](https://drive.google.com/file/d/1X2g73FqzQl7-WRfzhF7zHa7XWwnKcwtx/view?usp=sharing)

##### Réaliser un "Graduated Filter"

Arbitrairement je choisis les réglages suivants

- Gradient strength luminance : -0.44
- Gradient strength Chrominance : -1.13
- Gradient strength Hue : 2.69
- Gradient angle : -87.6
- Scope color tools = 30
- Feather gradient(settings) = 25

<img src="/images/gradLCH1.jpg" title="gradLCH1.jpg" width="600"
alt="gradLCH1.jpg" />` `  

##### Changer les réglages par défaut

- Essayez de changer progressivement "Scope color Tools", portez le à
  70, 75, 80, 85, 90, 100
- Changez "Feather" et notez les variations
- Bien sûr vous pouvez aussi changer les valeurs des gradients (L, C, H,
  angle)
- et aussi si vous le souhaitez les valeurs de "Color and light"

<img src="/images/gradLCHScopeFeather1.jpg" title="gradLCHScopeFeather1.jpg"
width="600" alt="gradLCHScopeFeather1.jpg" />

#### Cinq manières de changer l'exposition - relever les ombres - Évaluer la Dynamique Range - DR

Voir dans: Quelques particularités du mode local (par rapport à Lab
adjustements)- Shadows/Hightligt & Tone Equalizer [Shadows/Highlights &
Tone
Equalizer](Local_Lab_controls/fr#Shadows_Highlight&_Tone_Equalizer.md)

Cette démonstration est uniquement à caractère pédagogique, pour montrer
les diverses possibilités (non exhaustives) en matière de traitement de
l'exposition. Mes choix sont arbitraires.

- J'ai choisi de le faire avec une image difficile, ombre accentuées
  avec au centre une zone proche des limites d'exposition.
- Cinq méthodes sont juste "montrées" avec des réglages arbitraires
  - Shadows/Highlight
  - Tone Equalizer
  - TRC (Tone Response Curve)
  - Log Encoding
  - Exposure (Dynamic Range & Exposure)

J'aurais pu aussi utiliser :

- des courbes de contraste,
- ou relever les ombres avec "Lightness" (Color & Light)
- ou utiliser un Graduated Filter Luminance
- ...

##### Préparation

- par défaut j'ai réglé Scope à 50 ("Scope color tools" pour
  Shadows/Highlight", mais aussi Scope pour Log Encodinh, Scope pour
  Exposure)
- Essayez de faire varier cette valeur de 20 à 100

<img src="/images/shadows-prepa.jpg" title="shadows-prepa.jpg" width="600"
alt="shadows-prepa.jpg" />

Fichier raw (Rawtherapee - Creative Common Attribution-share Alike 4.0):
[3](https://drive.google.com/file/d/1ziux382pWgdYa4jySimwKaKnK_KdDhno/view?usp=sharing)

##### Utiliser Shadows/Highlights

`Add tool to current spot..."Shadows/Highlights & Tone Equalizer"`

- Shadows/Highlight
- essayez de changer "Shadows tonal width"...et "Highlight"

<img src="/images/shadows-sh.jpg" title="shadows-sh.jpg" width="600"
alt="shadows-sh.jpg" />

##### Utiliser Tone Equalizer

`Add tool to current spot..."Shadows/Highlight & Tone Equalizer"`

- Tone Equalizer
- essayez les curseurs 2, 3 et 4

<img src="/images/shadows-toneeq.jpg" title="shadows-toneeq.jpg" width="600"
alt="shadows-toneeq.jpg" />

##### Utiliser TRC

`Add tool to current spot..."Shadows/Highlight & Tone Equalizer" au moins en mode "Standard"`

- TRC
- augmentez "slope" jusque 150....revenez à 60
- essayez de diminuer gamma et de l'accroître

<img src="/images/shadows-trc.jpg" title="shadows-trc.jpg" width="600"
alt="shadows-trc.jpg" />

##### Utiliser Log Encoding

`Add tool to current spot..."Log Encoding"`

- Attention le "scope" à utiliser est celui de "Log encoding" : scope =
  50
- cliquez sur le bouton "Automatic"
- agissez sur "Target grey point"

<img src="/images/shadows-elog.jpg" title="shadows-elog.jpg" width="600"
alt="shadows-elog.jpg" />

##### Utiliser Exposure

Add tool to current spot... "Dynamic Range & Exposure"

- Choisissez "standard"
- Réglez "Exposure compensation ƒ" (un Laplacien et une transformée de
  Fouriers sont appliqués en amont de Exposure)
- j'ai réglé des curseurs de "Tools exposure" : black à -1500, shadows à
  50
- par défaut "Highlight compression" est à 20, faites varier
- essayez en neutralisant ces réglages
- essayez d'autres réglages de "Tools exposure"

<img src="/images/shadows-expo.jpg" title="shadows-expo.jpg" width="600"
alt="shadows-expo.jpg" />

##### Recommandations

Pour les portraits et les images à faible gradient de couleurs:

- utiliser "Exposure" avec précautions, dans ce cas des portraits
  (skin), ainsi que ceux avec une faible variation de couleurs,
  l'algorithme proche de celui de "exposure compensation main" est peu
  approprié, il vient d'être amélioré (5 juillet 2020) par l'ajout d'un
  Laplacien pour résoudre les différences de contraste.

Malgré les améliorations et d'une manière générale:

- l'algorithme "Exposure" est peu performant, mais les utilisateurs ont
  l'habitude de l'utiliser. J'ai été amené à mettre en place des
  palliatifs pour le rendre convenable;
- lui préférer (solutions les plus simples):
  - Tone Equalizer - dans Shadows/Highlight & Tone Equalizer
  - Tone Response Curve (TRC) - lui aussi dans dans Shadows/Highlight &
    Tone Equalizer (Equalizer en mode "Standard"). N'hésitez pas à
    accroître "Slope" pour déboucher linéairement les ombres. Vous
    pouvez agir sur le gamma pour éclaircir les zone claires.

Si néanmoins vous souhaitez utiliser "exposure",je recommande - non
obligatoire - de changer dans "settings" les paramètres de "Shape
detection"

- accroître "Threshold ΔE scope"
- réduire "ΔE decay"
- régler "Balance ΔE ab-L" vers L
- adapter Scope si nécessaire

##### Évaluer la Dynamic Range des outils en termes de Dynamic Range (DR)

Fichier TIF (Creative Common Attribution-share Alike 4.0):
[4](https://drive.google.com/file/d/1vAzFY7Qh8MdJ882J_4JeO_cnpGELzD8D/view?usp=sharing)

###### Image d'origine - 25Ev - sans traitement

Remarquez :

- les ombres sont bouchées
- 40% environ de l'image est avec des blancs à 100%
- la DR noir et blanc restituée est d'environ 12 à 13 Ev

<figure>
<img src="/images/sweep-rgb-neutral.jpg" title="sweep-rgb-neutral.jpg"
width="600" />
<figcaption>sweep-rgb-neutral.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Log encoding

Remarquez :

- les ombres et les lumières occupent toute la plage visible de L=1 à
  L=99.8 (échelle 0 - 100)
- les couleurs semblent uniformément réparties selon la luminance.
  L\*a\*b\* ne pénalise pas la Dynamic Range (DR)
- la DR couleur et noir et blanc restituée est de 25Ev
- Noter l'utilisation de "White distribution = 90"

<figure>
<img src="/images/sweep-rgb-log.jpg" title="sweep-rgb-log.jpg" width="600" />
<figcaption>sweep-rgb-log.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Color Appearance - Cam16

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=80.9 (échelle 0 - 100)
- les couleurs semblent uniformément réparties selon la luminance.
  L\*a\*b\* ne pénalise pas la Dynamic Range (DR)
- la DR couleur et noir et blanc restituée est de 25Ev
- Noter l'utilisation de "White distribution = 100" et "Black
  distribution = 60".

A noter la différence avec Log encoding, qui est due à l'action de
Ciecam et change la répartition des lumières.

- Agir sur le gamma de la TRC restitue sensiblement l'image Log Encoding
  ci-dessus.
- Ou agir sur Contrast J et Luminance J restitue sensiblement l'image
  Log Encoding ci-dessus.

<figure>
<img src="/images/sweep-rgb-cie.jpg" title="sweep-rgb-cie.jpg" width="600" />
<figcaption>sweep-rgb-cie.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Tone Equalizer

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=82 (échelle 0 - 100)
- les couleurs ne semblent pas uniformément réparties selon la
  luminance. L\*a\*b\*, la Dynamic Range est un peu pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 15Ev à
  18Ev
- Noter l'utilisation de un cinquième slider pour traiter les très
  hautes lumières : 5(lightest) = -100

<figure>
<img src="/images/sweep-rgb-te.jpg" title="sweep-rgb-te.jpg" width="600" />
<figcaption>sweep-rgb-te.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Dynamic Range & Exposure

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=4 à L=95.8 (échelle 0 - 100)
- les couleurs ne semblent pas uniformément réparties selon la luminance
  et selon les couleurs (dérive de couleurs dans les bleus). L\*a\*b\*,
  la Dynamic Range est un peu pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 17Ev à
  20Ev
- notez la complexité et le peu d'intuitivité des actions et le temps de
  traitement important

<figure>
<img src="/images/sweep-rgb-drexp1.jpg" title="sweep-rgb-drexp1.jpg"
width="600" />
<figcaption>sweep-rgb-drexp1.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Dehaze

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=88 (échelle 0 - 100), les ombres sont peu débouchées
- les couleurs ne semblent pas uniformément réparties selon la
  luminance. L\*a\*b\*, la Dynamic Range est pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 15Ev à
  16Ev

<figure>
<img src="/images/sweep-rgb-deha.jpg" title="sweep-rgb-deha.jpg" width="600" />
<figcaption>sweep-rgb-deha.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Shadows/Highlights

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=70 (échelle 0 - 100)
- les couleurs ne semblent pas uniformément réparties selon la
  luminance. L\*a\*b\*, la Dynamic Range est pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 12Ev à
  14Ev

<figure>
<img src="/images/sweep-rgb-sh.jpg" title="sweep-rgb-sh.jpg" width="600" />
<figcaption>sweep-rgb-sh.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Tone Response Curve - TRC

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=95.6 (échelle 0 - 100)
- les couleurs ne semblent pas uniformément réparties selon la
  luminance. L\*a\*b\*, la Dynamic Range est un peu pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 12Ev à
  16Ev

<figure>
<img src="/images/sweep-rgb-trc.jpg" title="sweep-rgb-trc.jpg" width="600" />
<figcaption>sweep-rgb-trc.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Dynamic Range & Exposure : Exposure only

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=70.9 (échelle 0 - 100)
- les couleurs ne semblent pas fidèles, ni uniformément réparties selon
  la luminance. L\*a\*b\*, la Dynamic Range est très pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 11Ev à
  14Ev

<figure>
<img src="/images/sweep-rgb-exp.jpg" title="sweep-rgb-exp.jpg" width="600" />
<figcaption>sweep-rgb-exp.jpg</figcaption>
</figure>

###### Image avec Local Adjustments - Tone Mapping

Remarquez :

- les ombres et les lumières occupent une partie de la plage visible de
  L=1 à L=72.4 (échelle 0 - 100)
- les couleurs ne semblent pas uniformément réparties selon la
  luminance. L\*a\*b\*, la Dynamic Range est très pénalisée
- la DR noir et blanc et couleur restituée est sensiblement de 10Ev à
  14Ev

<figure>
<img src="/images/sweep-rgb-tm.jpg" title="sweep-rgb-tm.jpg" width="600" />
<figcaption>sweep-rgb-tm.jpg</figcaption>
</figure>

###### Synthèse

- Les outils utilisant l'algorithme "Log encoding" - comme "LA Log
  encoding" ou "LA Color-Appearance Cam16" ont une restitution maximale
  et totale des couleurs et de la dynamic range (DR), mais leur
  utilisation n'est pas intuitive.
- "LA Tone Equalizer" assure une assez bonne restitution pour cette
  image. L'outil doit convenir pour une majorité d'images issues
  d'appareils photos. Il est intuitif mais nécessite au moins 5
  réglages.
- "LA Dynamic Range & Exposure" a une restitution de la DR très bonne,
  certaines couleurs subissent des dérives. Les réglages sont peu
  intuitifs, le système est lent.
- "LA TRC" assure une restitution moyenne pour cette image. L'outil doit
  convenir pour beaucoup d'images issues d'appareils photos.
  L'utilisation est simple et intuitive.
- "LA Dehaze" peut être apporter un traitement significatif de la DR, si
  il est utilisé par ailleurs, par exemple pour ce qu'il est conçu, le
  traitement de la brume.
- Les autres outils, "LA Exposure", "LA Shadows/Highlights" ne sont que
  de peu d'intérêt pour la DR.
- Curieusement 1 outils "dédié" (en théorie) à la DR - "LA Tone Mapping"
  n'a pas de bons résultats.

#### Traitement d'une image brumeuse

Quelques explications dans "Quelques questions" : [Association Retinex -
Dehaze](Local_Lab_controls/fr#A_quoi_sert_l'association_Retinex_-_Dehaze.md)

Je prendrais l'exemple d'une image très brumeuse et appliquerais en
première étape le traitement "Dehaze" du main menu Puis je continuerais
le traitement avec un complément pour le ciel et l'horizon, avec Retinex
local

##### Image originale

<img src="/images/haze.jpg" title="haze.jpg" width="600" alt="haze.jpg" />

Fichier raw (Pixls.us - Common Attribution-share Alike 4.0):
[5](https://drive.google.com/file/d/1tc9TxHGwYnVQ2OwiTZIiszDOEXfDjkh6/view?usp=sharing)

##### Traitement avec Dehaze (main)

J'aurais pu le faire avec "dehaze local" (Dehaze & Retinex) ...et un
RT-spot! Mais examinez l’arrière plan, les collines...il reste beaucoup
de brume

<img src="/images/haze-dehaze.jpg" title="haze-dehaze.jpg" width="600"
alt="haze-dehaze.jpg" />

##### Complément avec Retinex local

- Choisir "add tools to current spot.." : Dehaze - Retinex - "advanced"
- Essayer plusieurs réglages par itérations successives
- agissez si nécessaire avec la courbe "transmission map"...avec un
  affaiblissement de la courbe à droite...
- examinez maintenant les collines et le ciel à l'horizon !

<img src="/images/haze-reti1.jpg" title="haze-reti1.jpg" width="600"
alt="haze-reti1.jpg" />

#### Comment utiliser le module "Denoise"

Voir dans "Quelques particularités du mode local (par rapport à Lab
adjustements) [Denoise](local_lab_controls/fr#denoise)

Plusieurs utilisations sont possibles.

- en complément sur certaines zones du module "denoise main", dans ce
  cas les réglages de "denoise main" seront réalisés a minima
- en traitant toute l'image en mode "local adjustments" - "Denoise" et
  en excluant une zone avec "excluding"
- pris isolément pour réduire le bruit dans des images peu bruitées -
  par exemple pour retirer le bruit d'un ciel, ou d'un visage
- pris isolément pour traiter le bruit dans une zone choisie et en le
  laissant volontairement dans le reste de l'image, à des fins
  artistiques

C'est ce dernier cas que je vais expliciter.

L'image de la jeune fille est particulièrement bruitée avec un fort
bruit chromatique

<img src="/images/denoise-prepa1.jpg" title="denoise-prepa1.jpg" width="600"
alt="denoise-prepa1.jpg" />

Fichier raw (Copyright Ian Burley - Common Attribution-share Alike 4.0):
[6](https://drive.google.com/file/d/1poZporRNILcYfab1Y_f1i-SIEB4acn6L/view?usp=sharing)

##### Zoom 100%

<img src="/images/denoise-zoom1.jpg" title="denoise-zoom1.jpg" width="600"
alt="denoise-zoom1.jpg" />

##### Quels réglages pour denoise ?

- la position du spot, sa taille ont de l'importance : j'ai choisi une
  zone du visage avec un fort bruit chromatique et un assez gros RT-spot
  "spot size"
- le choix de scope est important : dans ce cas - où le bruit occupe
  quasiment tout le spectre coloré (rouge, vert, bleu, jaune) il faut
  choisir une valeur élevée de scope (ici 90). Si, avec une autre image,
  le traitement du bruit concernait uniquement la luminance il faudrait
  choisir la valeur de scope "habituelle", soit aux environs de 30, pour
  permettre à l'algorithme de différencier l'action selon les couleurs.
- par rapport à "denoise main" plusieurs changements:
  - possibilité de régler le débruitage luminance en fonction du niveau
    de détail (de 0 à 6 selon la position sur l'abscisse de la courbe),
    à l'aide d'une courbe
  - une différentiation est faite en fonction du niveau de détail : si
    les niveaux 3 et au-dessus sont supérieurs à 20% de l'ordonnée de la
    courbe, il en résultera une action plus destructive sur la
    luminance.
  - la différenciation "sombre - clair" pour la luminance est traitée
    par un "equalizer", plutôt que par "gamma"
  - possibilité de différencier l'action entre "chroma fine" (bruit
    d'impulsion, bruit faible de chrominance...niveaux de 0 à 4) et
    "chroma coarse" (paquets, bloatches..niveaux 5 et 6)
  - l'algorithme "chroma" utilise une action plus destructive, si le
    curseur "coarse" est supérieur à 20.
  - un "equalizer" "rouge vert" / "bleu jaune" peut être utile pour les
    images faiblement bruitées
  - ajout d'un curseur "chroma detail recovery" - utilisant DCT
    (discrete cosinus transform : Fourier)
  - ajout d'un curseur "Detail threshold luminance Chroma (DCT)" qui
    permet de différencier l'action en fonction des bords ("edge
    detection")

<img src="/images/denoise1.jpg" title="denoise1.jpg" width="600"
alt="denoise1.jpg" />

##### Un cas complexe "Denoise" - comment différentier l'action sur les structures et les aplats

Ce cas, habituel en photographie, consiste à isoler un sujet sur un
fond. Le sujet pouvant être un animal, une plante, une personne,... Le
fond peut être le ciel, une pelouse, une forêt, un mur... Le problème à
traiter par les logiciels de dé-bruitage est complexe, car l'algorithme
le plus souvent "ignore" la différence "sujet", "fond" et aboutit si on
souhaite supprimer le bruit sur le "fond" à perdre toute les reliefs,
contrastes et couleurs du "sujet"

###### Un exemple le "mulot"

J'ai choisi cette image, avec l'accord de son auteur Andy Astbury, car
d'une part elle est excellente, l'animal se détache très bien sur un
fond d'apparence gris, et d'autre part elle est bruitée (légèrement). Si
on souhaite retirer le bruit sur le fond, avec "Noise reduction" (main),
le "mulot" perd contraste et saturation et détails.

Fichier raw :(Copyright Andy Astbury - Creative Common Attribution-share
Alike 4.0)
[7](https://drive.google.com/file/d/1uND8pqgfxxaBhs554RnCvOS5NI3KsWT5/view?usp=sharing)

Fichier pp3
\[<https://drive.google.com/file/d/1qwslSsbXlM4Ns8A_2t_8_QSMWfsIuAR8/view?usp=sharing>
Le fichier pp3 ne donne pas "le bon réglage" mais garde la trace de
réglages de certains outils pour faciliter la découverte des méthodes et
outils.

Traditionnellement dans Rawtherapee, on utilise pour retirer le bruit,
le module "Noise reduction" (onglet détail). Si on a pour objectif de
rendre l'arrière plan sans bruit de luminance et de chrominance - je ne
montre pas l'image ni les réglages - on aboutit a des réglages de
l'ordre de:

- curseur luminance = 65
- curseur chrominance - Master = 20

Certes le fond d'image sera parfait, mais notre gentil "mulot" va
devenir terne, lavé... Alors comment faire ?

Principe de la démarche:

- traiter le bruit en 2 étapes - une première *a minima* utilisant
  "noise reduction" va permettre de traiter le bruit sur le sujet qu'on
  souhaite préserver (ici le "mulot"); dans le cas présent l'œil du
  "mulot" sera discriminant, ainsi également par exemple que la queue. A
  noter que dans d'autres images cette étape pourra permettre aussi de
  réduire les gros paquets de bruit.
- mais le bruit s'apparente aux principes des modèles d'apparence
  colorée; il sera nettement plus visible sur un fond gris que sur un
  fond plus sombre (notamment le bruit de chrominance), il en est de
  même pour les parties lumineuses. On a donc intérêt à coupler dans la
  même démarche un ajustement des tons de l'image - qui peut également
  la rendre plus attractive - et le dé-bruitage.
- ensuite, en deuxième étape, nous traiterons le bruit avec "Local
  adjustments", en utilisant les capacités de cet outil, notamment, les
  5 méthodes ci-dessous:

1.  le masque qui va permettre de différencier l'action entre les
    reliefs ("mulot", "végétation"...) et le "fond".
2.  l'égalisateur Hue qui va permettre de différencier l'action entre la
    couleur du "mulot" et le "fond"
3.  le curseur Scope (deltaE) qui permet de différencier l'action selon
    les différences de couleurs
4.  les curseurs "luminance detail recovery (DCT) - et dans "edge
    detection" - luminance et chroma detail theshold, qui agissent par
    un traitement du bruit (Fourier) basé sur le bruit résultant de
    l'écart entre l'image originale et celle débruitée par les wavelets.
5.  le débruitage par morceaux - encore appelé "Non local Means", un
    autre algorithme de débruitage, fondé sur la similarité de pixels et
    de patch - va lui aussi permettre de différencier l'action entre les
    reliefs ("mulot", "végétation"...) et le "fond".

- puis nous ferons des ajustements terminaux pour obtenir l'image
  souhaitée - saturation, contraste local, etc.
- bien sûr ce document est à titre pédagogique, les réglages sont
  arbitraires plus tournés vers l'exemple que la recherche d'une belle
  image.

###### Premier "denoise" et "égalisateur de tons"

Sur cette image apparaît seulement l'égalisateur de tons. On agira en
même temps sur "Noise reduction" - luminance et chrominance.

On positionnera des "lockable color pickers" sur l'œil, la fourrure, la
végétation, la queue.

- ajouter un nouveau "RT spot" - choisir dans settings "Full image".
  Toujours dans settings aller à "Mask and merge" et régler "background
  color for luminance and color masks" à 0 (ceci va permettre un
  meilleur suivi des valeurs de la luminance)
- Add tool to current spot..: choisir "shadows/highlight and Tone
  equalizer" - Basic
- positionner le centre du "RT-spot" sur le "fond"
- agir sur les curseurs de l'égalisateur pour obtenir le meilleur
  compromis, tout en agissant sur les 2 curseurs de "Noise reduction" -
  ici j'ai utilisé - Luminance = 4 - chrominance = 6.5

<img src="/images/mulot_first.jpg" title="mulot_first.jpg" width="600"
alt="mulot_first.jpg" />

###### Deuxième étape - Local adjustments - Blur/grain & Denoise module

- Add tool to current spot... Sélectionnez "Blur/grain & Denoise", puis
  "Denoise", "Avancé"
- Utiliser la courbe "Luminance detail by level"
- à titre pédagogique et afin de voir l'efficacité des divers outils
  vous pouvez mettre cette courbe au maximum et activer
  "agressive"...bien sûr il faudra ensuite la ramener à des valeurs
  normales.

Puis, je recommande, toujours à titre pédagogique d'essayer une par une,
les 5 méthodes citées plus haut. Par exemple pour voir l'action de
l'égalisateur Hue, mettre Scope à 100, mettre le curseur "Recovery
threshold à 1" dans "Recovery based on luminance mask" pour le
désactiver, laisser les 3 curseurs DCT à leurs valeurs par défaut.

- régler le Equalizer hue en renforçant le débruitage pour le "fond" et
  en l'atténuant pour le "mulot"
- agir légèrement sur "Fine chroma"
- examinez les résultats

<img src="/images/mulot_levelhue.jpg" title="mulot_levelhue.jpg" width="600"
alt="mulot_levelhue.jpg" />

- Réaliser un masque.
  - Ce masque va permettre ensuite avec un des outils de "Local
    adjustments - denoise", de discriminer l'action entre le "fond" et
    le reste de l'image "mulot" et végétation.
  - Dans le cas présent je me suis servi d'une simple courbe L(L), du
    gamma et de la courbe de contraste , mais d'autres images pourraient
    nécessiter d'utiliser la courbe LC(H), structure mask strength,
    Smooth radius, etc.

<img src="/images/mulot_mask.jpg" title="mulot_mask.jpg" width="600"
alt="mulot_mask.jpg" />

Courbe de contraste:

<img src="/images/mulot_mask2.jpg" title="mulot_mask2.jpg" width="600"
alt="mulot_mask2.jpg" />

Ensuite:

- activez le masque (mask and modifications)
- ouvrez l'expander "Recovery based on luminance mask"
- agissez sur "Recover threshold", des détails vont réapparaître...

Pour d'autres images il sera peut être nécessaire d'agir sur :

- "Dark area luminance threshold", valeurs en-dessous de laquelle la
  luminance du masque sera prise en compte pour accroître le
  dé-bruitage - la référence du noir étant celle du masque
- "Light area luminance threshold", valeurs au-dessus de laquelle la
  luminance du masque sera prise en compte pour accroître le dé-bruitage
  de manière régressive - la référence du blanc étant celle du masque si
  elle existe correspondra au dé-bruitage maximum- de cette référence
  jusqu'au blanc maximum qui si il est à 100 n'aura pas de dé-bruitage.
  Cette action va ici permettre par exemple de "dé-bruiter" ou non les
  parties claires de la végétation.
- decay permet de gérer la progressivité des changements
- les 2 curseurs "Gray area" permettent si nécessaire de réintroduire un
  débruitage dans la zone "protégée" - tons moyens du masque

<figure>
<img src="/images/mulot_recovery.jpg" title="mulot_recovery.jpg" width="600" />
<figcaption>mulot_recovery.jpg</figcaption>
</figure>

- Utilisation de Scope : ici nous sommes en terrain connu. Vous pouvez
  utiliser dans "Mask and modifications" les 2 sélections "Show modified
  areas with mask" et "Show modified areas whithout mask" pour voir
  l'incidence de Scope...Ou plus simplement agir sur Scope et voir
  l'effet. Sur cette image, avec "Equalizer hue" désactivé et "Recovery
  based on luminance mask" à 0, l'action de Scope est sensible entre 50
  et 100.
- Utilisation des 2 curseurs "Luminance detail recovery" et "Luminance &
  chroma detail threshold"
  - accroissez progressivement "Luminance detail recovery"
  - agissez en parallèle sur le "Luminance & chroma detail threshold"...
    vous verrez réapparaître des détails.
  - 2 algorihmes sont possibles - le premier utilise un masque interne -
    le second un Laplacien. Chacun a ses particularités, le Laplacien
    est plus sélectif, mais moins progressif

<!-- -->

- Utiliser "Débruitage par morceaux (patch)" (Non-local means)
  - Débruitage par morceaux - c'est quoi ? Contrairement aux filtres
    habituels qui réalisent une moyenne des valeurs du groupe de pixels
    localisés autour d'un pixel cible afin de réduire le bruit, le
    filtre "non-local means" réalise une moyenne de la totalité des
    valeurs des pixels contenus dans l'image, pondérées en fonction de
    leur similarité avec le pixel cible. Le résultat d'un tel filtrage
    permet d’amoindrir la perte de détails au sein de l'image, comparé
    aux filtres réalisant des moyennes localement.

<figure>
<img src="/images/mulot_nlmeans.jpg" title="mulot_nlmeans.jpg" width="600" />
<figcaption>mulot_nlmeans.jpg</figcaption>
</figure>

Afin de bien percevoir les effets de cette méthode, je recommande
toujours à titre pédagogique:

- activer en méthode de débruitage - mode : "Non-local means only"
- désactivez le masque
- mettez Scope à 100

En mode "avancé" vous disposez de 5 curseurs:

- Strength
- Detail recovery - permet une première sélection entre les aplats et
  les textures. Plus les valeurs sont élévées plus les détails
  réapparaissent
- Gamma - seconde sélection entre les aplats et les textures. Plus le
  gamma sera faible plus les détails et les textures seront
  reconstituées
- Maximum patch size : permet d'adapter la taille du "patch" (morceaux)
  à la taille des objets. En théorie, plus l'image est bruitée plus
  cette valeur doit être grande. En pratique c'est par l'observation et
  la minimisation des artefacts dans les transitions - aplats /
  textures - que l'on sera guidé
- Maximum radius size : plus cette valeur sera grande, meilleure sera
  théoriquement le débruitage, mais en conséquence les temps de
  traitement vont considérablement s'accroître.

###### Ajustement final - Saturation et Contraste local

Ajoutez un nouveau RT-spot, centré sur le "mulot".

Puis ajoutez 2 outils:

- add tool to current spot - "Vibrance and warm cool" - basic
  - agissez sur le curseur "vibrance" jusqu'à obtenir l'accroissement
    souhaité de saturation

<!-- -->

- add tool to current spot - "Local contrast & Wavelet" - Wavelet -
  Advanced
  - utilisez "contrast by level" en privilégiant les premiers niveaux

<figure>
<img src="/images/mulot_wav.jpg" title="mulot_wav.jpg" width="600" />
<figcaption>mulot_wav.jpg</figcaption>
</figure>

###### Autres méthodes et outils

D'autres méthodes peuvent être utilisées avec la même finalité:

- méthodes de "Local adjustments"
  - "Denoise based on luminance mask" - se sert du même masque que
    "Recovery based on luminance mask" mais renforce ou affaibli le
    débruitage "wavelet" - il agit à la manière de "l'equalizer hue" -
    "avant", alors que "Recovery based on luminance mask" agit "après"
    en comparant l'image originale bruitée et l'image débruitée.
  - "equalizer white-black" et "equalizer blue-yellow red-green" : ils
    sont l'équivalent de la courbe "luminance curve" dans "Noise
    reduction" et peu efficaces ici
  - "Guided Filter" dans "Blur/grain & denoise" - "Blur & Noise" : vous
    utilisez le même masque et le même processus "Recovery based on
    luminance mask" en utilisant les valeurs négatives du curseur
    "détail"
  - "Excluding spots" - qui permettent de restaurer l'image avant
    l'action du RT-spot "Full image"
  - "Median" dans "Flouter/grain & Dé-bruiter" \> "Flouter & Brui": peu
    efficace ici.
  - "Netteté des bords" dans "Contrast local & Ondelettes" \>
    "Ondelettes" \> "Pyramide 1": si vous voulez flouter une partie de
    l'image en fonction du niveau de détail.

<!-- -->

- autres méthodes de Rawtherapee (non développées ici)
  - "Noise reduction" : les courbes "Luminance control" et chromiannce
    curve permetent une certaine forme de sélection, mais insuffisante
    ici.
  - "Wavelet levels - noise reduction" - avec notamment un "equalizer
    hue" et l'utilisation de "Local contrast"

Comparaison des outils denoise [Comparaison des 3 outils « Denoise » de
Rawtherapee](Denoise/fr.md)

###### Synthèse

Cet exemple, merci encore à Andy Astbury pour cette excellente image,
qui permet de déployer à titre pédagogique 5 méthodes pour différencier
l'action entre structures et aplats.

- "Equalizer hue"
- "Recovery based on luminance mask"
- "Scope" - deltaE
- "DCT - Edge detection"
- "Non-local means"

Dans une image difficile il sera probablement nécessaire d'activer les 5
méthodes avec un équilibre toujours difficile à trouver. Le résultat
étant affaire de goût de chacun et est assez subjectif.

Notamment:

- le "fond" qui ici est uniforme, pourra poser plus de problèmes si il y
  a du relief, des structures.
- les couleurs qui ici sont bien séparées, ne vont pas permettre une
  telle séparation si elles sont plus "mélangées"
- le deltaE qui peut être très perturbé par le bruit chromatique, avec
  en plus la même remarque que ci-dessus
- "Edge detection" qui lui aussi sera perturbé par un bruit de luminance
  important

#### Un moment de folie - utiliser wavelet

A voir dans : Quelques particularités du mode local (par rapport à Lab
adjustements)
[Wavelets](Local_Lab_controls/fr#Wavelets_Pyramid_(détails) "wikilink")

##### A titre de démonstration....(ne fuyez pas... ce n'est pas si complexe que cela)

Image originale, avec "Exposure compensation" +1.5

<img src="/images/Amsterdam15.jpg" title="Amsterdam15.jpg" width="600"
alt="Amsterdam15.jpg" />

##### La même image avec "Levels Dynamic Range (un)Compression (wavelet local) "Local contrast & Wavelets"

- Tous les réglages par défaut (settings)
- Outil "wavelet pyramid2" activé (advanced)
- scope (wavelet) réglé sur 80
- puis les réglages visibles sur la capture d'écran
- bien sûr l'apparence est subjective, chacun peut accentuer ou réduire
  les réglage, en ajouter,....
- cette version de "Tone mapping" est différente des autres algorithmes
  implantés dans Rawtherapee (Fattal "dynamic range compression",
  Mantiuk "Tone mapping", Log Encoding), elle est spécifique à
  Rawtherapee Wavelet.

<img src="/images/Amsterdam15_wavtm1.jpg" title="Amsterdam15_wavtm1.jpg"
width="600" alt="Amsterdam15_wavtm1.jpg" />

#### Trois manières d'accroître la texture

Toujours à titre de démonstration, 3 manières d’accroître la texture.
Ceci est obtenu par des principes de Tone-mapping J'utiliserais :

- tone-mapping (Mantiuk)
- Retinex
- Wavelet

##### Préparation - image originale - Venise

<img src="/images/texture-normal1.jpg" title="texture-normal1.jpg" width="600"
alt="texture-normal1.jpg" />

Fichier raw (Copyright Sebastien Guyader - Common Attribution-share
Alike 4.0):
[8](https://drive.google.com/file/d/1DASGpHfl_9RDRhbq2_JQVgypgKyrdiBk/view?usp=sharing)

##### Traitement "Tone mapping"

Voir dans :Quelques particularités du mode local (par rapport à Lab
adjustements) [Avec Tone
mapping](Local_Lab_controls/fr#Tone_Mapping.md)

- remarquez l'utilisation de "normalize luminance" qui maintient à
  l'image la même moyenne et la même variance que l'image originale
- utilisation du mode "advanced" - "edge stopping" et "scale'

` `<img src="/images/texture-tm1.jpg" title="texture-tm1.jpg" width="600"
alt="texture-tm1.jpg" />

##### Traitement "Retinex"

Voir dans : Quelques particularités du mode local (par rapport à Lab
adjustements) [Avec
Retinex](Local_Lab_controls/fr#Dehaze_&_Retinex.md)

- remarquez l'utilisation de "Normalize luminance" qui maintient à
  l'image la même moyenne et la même variance que l'image originale
- l'usage de "Fast Fourier Transform"

` `<img src="/images/texture-reti1.jpg" title="texture-reti1.jpg" width="600"
alt="texture-reti1.jpg" />

##### Traitement "Wavelet" (Local contrast & wavelets)

Voir dans : Quelques particularités du mode local (par rapport à Lab
adjustements) : [Avec
Wavelets](Local_Lab_controls/fr#Wavelet_level_tone_mapping.md)

- remarquez l'usage de "Levels dynamic range compression", les valeurs
  de "Attenuation Response", "balance threshold" et "compress residual
  image"
- essayez aussi "Contrast by levels"
- essayez aussi "Levels directionnal contrast"
- ou une combinaison de ces traitements

` `<img src="/images/texture-wav1.jpg" title="texture-wav1.jpg" width="600"
alt="texture-wav1.jpg" />

#### Fusion d'images - modes de fusion (merge file)

Voir dans Principes généraux : [Fusion
d'images](Local_Lab_controls/fr#Algorithme_complémentaire_:_fusion_d'images.md)

Vous pouvez utiliser dans "Color & light" - "Merge file" qui va vous
permettre de simuler la fusion de calques. En effet chaque RT-spot
correspond (ce n'est qu'une similitude) à un calque. Le système proposé
permet de gérer jusqu'à une prise en compte de 2 RT-Spot et l'image
d'origine.

- Le premier "calque" est appelé "Original", il correspond (comme
  "Excluding spot") aux données avant toute intervention "Local
  adjustments"
- si vous empilez des RT-spots l'un au dessus de l'autre, par exemple 6:
  - "Merge file" fusionnera le 6ème (calque) si le Spot courant est le
    6, soit avec le 5ème (Previous Spot), soit avec "Original" (les
    données d'origine), soit avec une couleur définie dans "background"
  - "Merge file" fusionnera le spot courant (par exemple le 3 sur les 6
    en cours) avec le 2ème (Previous spot), soit avec "Original" (les
    données d'origine), soit avec une couleur définie dans "background"
  - pour chacune de ces fusions vous disposez de 21 modes de fusions
    inspirés de ceux de Photoshop (C) (Normal, differences, ....soft
    light,..., overlay,...)
  - pour chacun vous pouvez gérer l'opacité, la prise en compte du
    deltaE, et un "contrast threshold" (à l'exception du choix
    "background")
  - les "Graduated Filter" (Luminance, Chrominance, Hue) - situés dans
    "Color and Light" - fonctionnent avec "merge files"

<!-- -->

- A titre d'exemple je vais utiliser ces fonctionnalités pour gérer un
  flou variable (bien sûr vous pouvez faire autre chose)

##### Préparation

Je passe sur les premières étapes qui sont similaires. Dans ce cas, je
choisis "add tool to current spot" = "Smooth - Blur - denoise"

- régler le RT-spot en inverse
- choisir Scope = 90 ou 100 selon l'effet recherché
- régler radius sur une valeur élevée (2000 ou plus - noter l'option
  FFTW), régler le mode de flou sur "Luminance & chrominance"

`  `<img src="/images/mergeblurinv_2.jpg" title="mergeblurinv_2.jpg" width="600"
alt="mergeblurinv_2.jpg" />

Fichier raw (Rawtherapee - Creative Common Attribution-share Alike 4.0):
[9](https://drive.google.com/file/d/1dJ5yiqF-XdLQdKizCDseUxHf34y4AKZ6/view?usp=sharing)

##### Créer un deuxième RT-spot

Avec "Add tool to current spot" - "Color & light" - "advanced"

- réglez "Scope color tools" sur 100

`  `<img src="/images/mergetwo1.jpg" title="mergetwo1.jpg" width="600"
alt="mergetwo1.jpg" />

##### Première fusion - mode de fusion "normal"

- Allez jusque l'expander "merge file"
- choisissez dans la liste "Original" - les autres choix :
  - "Previous spot" permet la fusion avec le RT-spot précédent
    (identique à Original - si il n'y a que 1 RT-spot)
  - "Background" permet la fusion avec un fond coloré;

<!-- -->

- choisissez ensuite dans "Merge with Original or Previous or
  Background" le mode de fusion et choisissez les réglages : Merge
  background, Opacity, contrast threshold
- bien sûr vous pouvez utiliser tous les réglages possibles de "Color &
  Light"

`   `<img src="/images/mergeorignrmal1.jpg" title="mergeorignrmal1.jpg" width="600"
alt="mergeorignrmal1.jpg" />

##### Deuxième mode de fusion - Soft light

Dans la liste des modes de fusion essayez "Soft light (legacy)" (ou un
autre mode...)

- choisissez les réglages, essayez...
- remplacez "Original" par "Previous Spot"...notez les différences

`  `<img src="/images/mergeorigsoftlight1.jpg" title="mergeorigsoftlight1.jpg"
width="600" alt="mergeorigsoftlight1.jpg" />

#### Utilisation d'un masque simple pour accroître la sélection de couleur

Voir dans "Principes généraux": [Utilisation d'un masque
simple](Local_Lab_controls/fr#Algorithme_complémentaire_-_Mask_and_Modifications.md)

##### Préparation

- J'ai choisi l'image de la montagne de sel à Pammukale (Turquie).
- C'est une image difficile à traiter, du fait des faibles différences
  de couleurs entre le ciel et la montagne. De plus cette montagne
  contient de nombreuses irrégularités.
- Je passe sur les étapes préliminaires similaires aux cas précédents.
  Notez le réglage de "Scope color tools = 40" qui est un compromis pour
  permettre de traiter correctement la montagne
- Je propose à titre pédagogique d'accroître de manière très forte la
  luminance (lightness) et la chrominance de la montagne (ce n'est pas
  un objectif artistique) : l'objectif est si possible que cette
  modification ne touche pas le ciel
- j'aurais pu utiliser des "excluding spot", ou si le GUI le prévoit un
  jour, une délimitation par un polygone; mais à titre pédagogique
  j'utilise un masque simple. J'aurais pu utiliser plusieurs courbes
  pour le masque, ou plusieurs masques (dupliquer le RT-spot).
- "Local adjustments" permet la gestion de 2 types de masques:
  - 1\) ceux qui n'ajoutent ou ne retranchent pas le masque à l'image.
    On vise l'amélioration de la qualité de la sélection deltaE
  - 2\) ceux qui utilisent ces différences
  - nous sommes ici dans le premier cas (amélioration de la sélection)

` `<img src="/images/masksimpleprepa1.jpg" title="masksimpleprepa1.jpg" width="600"
alt="masksimpleprepa1.jpg" />

Fichier raw (Jacques Desmis - Creative Common Attribution-share Alike
4.0):
[10](https://drive.google.com/file/d/1azCxu1midw6dcuN7SbvbAiJH4pxX5BTA/view?usp=sharing)

##### Accroître fortement lightness et la chrominance

- Constatez le résultat : les couleurs bavent, le ciel est touché par
  les changements, alors que je souhaite l'éviter

<figure>
<img src="/images/masksimplelum250chro1401.jpg"
title="masksimplelum250chro1401.jpg" width="600" />
<figcaption>masksimplelum250chro1401.jpg</figcaption>
</figure>

##### Élaborer un masque simple

- j'ai pris le parti de ne me servir que de une des 3 courbes LCH (ici
  L)
- examinez le positionnement de la courbe L(L) : le point d'inflexion
  est situé à la transition entre zones grises. Pour toutes les
  courbes - C(C), L(L), LC(H), cette "transition" correspond aux 3
  références du RT-spot (chroma, luma, hue)
- ne pas utiliser "blend" : donc il n'y a que la détection de forme qui
  est améliorée
- vous pouvez utiliser aussi dans "Mask and modifications" - "Show
  modifications with mask"

<figure>
<img src="/images/masksimpleshow1.jpg" title="masksimpleshow1.jpg"
width="600" />
<figcaption>masksimpleshow1.jpg</figcaption>
</figure>

##### Finaliser le résultat

- mettez "mask and modifications" sur "none"
- activez "enable mask"
- agissez si nécessaire sur "Smooth radius mask"
- retouchez éventuellement les courbes "Contrast curve" et L(L)
- passez en mode "advanced" et essayez "Gamma", "Slope", ainsi que
  "Laplacian thresholdk" (à la place de "Smooth radius")
- certes ce n'est pas parfait, mais nettement mieux....l'objectif est la
  découverte du fonctionnement des masques.

Pour améliorer le traitement de type masque, 2 solutions s'offrent à
vous :

- Dupliquer le RT-spot : si vous dupliquez le RT-spot, à côté du
  précédent, en changeant légèrement la position du centre (références),
  vous pouvez utiliser un second masque pour retoucher les "anomalies -
  incomplétudes" du précédent. De plus cette option permet de retoucher
  si nécessaire la valeur des traitements (ici lightness, chrominance)
  et la "partager" entre les 2 RT-spot pour une meilleure homogénéité.
- Utiliser le masque d'un autre outil ouvert (si bien sûr celui-ci est
  doté d'un masque). Dans ce cas vous conservez les mêmes références
  (luma, chroma, hue) aussi bien pour élaborer les masques que pour la
  prise en compte du deltaE (scope)

Prise en compte des deltaE:

- vous pouvez désactiver la fonction cœur de "Local adjustments" - c'est
  à dire la fonction "Scope" qui prend en compte le deltaE - si vous
  souhaitez travailler entièrement avec les masques et ignorer "Scope",
  dans ce cas réglez "Scope=100". A l'évidence la fonctionnalité "Scope"
  étant désactivée, seule l'utilisation de "blend" sera opérationnelle
  pour assurer la combinaison masque / image.
- Lorsque vous utilisez les outils des masques "Tools" (Contrast curve
  mask, chroma mask, gamma mask, etc.), ceux-ci sont sensibles au
  réglage spécifique du deltaE masque : "Mask deltaE image" ("settings")

<figure>
<img src="/images/masksimple1.jpg" title="masksimple1.jpg" width="600" />
<figcaption>masksimple1.jpg</figcaption>
</figure>

##### Amélioration du résultat avec 'Recovery based on luminance mask'

Nous allons élaborer un masque qui sera utilisé d'une manière différente
des autres processus dans RT. Ce masque sera utilisé "en direct" et son
analyse va servir à combiner l'image sans l'action de "Color and Light",
avec l'image traitée avec "Color and light"

- régler l'arrière plan des masques afin que la lecture des valeurs
  L\*a\*b\* des "Lockable Color pickers" correspondent aux valeurs
  réelles : dans "Local adjustments" - "Settings" -"Mask and merge" -
  "Background color for luminance and color masks = 0"

Selon les réglages de "Recovery based on luminance mask":

- les zones sombres et noires du masque donneront la possibilité de
  ramener l'image combinée au plus près de l'image originale.
- les zones très claires ou blanches du masque donneront la possibilité
  de ramener l'image combinée au plus près de l'image originale.
- la zone intermédaire conservera les réglages de "Color and Light".

Image avec réglages "Color & Light" - sans masque

Fichier pp3;
[11](https://drive.google.com/file/d/1BWpBUd5qjpDHv_stdF5ord8qFGhxC0J0/view?usp=sharing)

<figure>
<img src="/images/mask_recov0.jpg" title="mask_recov0.jpg" width="600" />
<figcaption>mask_recov0.jpg</figcaption>
</figure>

###### Création du masque

Notez l'utilisation de "Blur mask" avec 'Contrast threshold' et
'Radius'. Cette action permet de relever la valeur des gris dans la
partie droite de la montagne de sel pour permettre une action 'légère'
de Color and Light' Remarque : l'utilisation 'avancée' de ce masque avec
'Recovery' n'esr pas en opposition avec l'utilisation 'normale' du
masque :

- l'utilisation 'normale' va améliorer la sélection
- l'utilisation 'avancée avec recovery' va à nouveau améliorer la
  sélection.

<figure>
<img src="/images/mask_recov.jpg" title="mask_recov.jpg" width="600" />
<figcaption>mask_recov.jpg</figcaption>
</figure>

###### Récupération des caractéristiques de l'image d'origine

- Assurez vous que le masque est activé dans "Masque et modifications":
  case "Enable mask" cochée.
- dépliez l'expander "Recovery based on luminance mask"
- agissez sur "Recovery threshold" : plus le curseur sera proche de "2",
  plus les zones sombres et très claires du masque seront prises en
  compte, plus ces zones seront ramenées aux valeurs de l'image
  originale
- agissez sur les curseurs "Dark area luminance threshold" et "Light
  area luminance threshold" pour inclure ou exclure certaines parties de
  l'image. Les valeurs correspondantes (ici dark = 32.1 et Light = 85)
  sont les 2 limites en deçà et au delà desquelles les actions du masque
  seront progressivement prises en compte.
- agissez éventuellement sur "decay" pour régler la "vitesse" de la
  décroissance.
- essayez dans "Masque et modifications" de désactiver le masque : case
  "Enable mask" décochée.
- essayez dans "Masque et modifications"avec masque activé - case
  "Enable mask" cochée - de remettre à 1 le curseur 'Recovery threshold'
- essayez d'autres réglages de "mask" et des 4 réglages de "recovery"

<figure>
<img src="/images/mask_recovend.jpg" title="mask_recovend.jpg" width="600" />
<figcaption>mask_recovend.jpg</figcaption>
</figure>

#### Que faire quand un masque présente une apparence poivre et sel ?

Lorsque vous utilisez lors de la création du masque, la courbe LC(h),
l'image du masque peut être perturbée par une multitude de points noirs
et blancs (poivre et sel) qui détournent le masque de son usage. L'image
originale choisie ne convient pas car elle est peu bruitée j'en ai
choisie une autre qui présente la caractéristique d'un bruit chromatique
assez important.

<figure>
<img src="/images/masknoisechroma.jpg" title="masknoisechroma.jpg"
width="600" />
<figcaption>masknoisechroma.jpg</figcaption>
</figure>

##### Comment le traiter?

Vous trouverez dans "Settings" \> "Show additional settings" \> "Mask
and Merge", un curseur "Denoise chroma mask".

- agissez jusqu'à obtenir l'effet désiré

<figure>
<img src="/images/masknoisechromaden.jpg" title="masknoisechromaden.jpg"
width="600" />
<figcaption>masknoisechromaden.jpg</figcaption>
</figure>

##### Le bruit chromatique peut avoir d'autres incidences sur l'utilisation des masques

Si vous souhaitez utiliser pour l'élaboration du masque la courbe C:,
lors de la fusion du masque avec l'image originale des artefacts
(paquets) de tâches grisâtres peuvent apparaître. Dans ce cas c'est
probablement le bruit chromatique qui est en cause. Procédez comme
précédemment.

#### Utilisation d'un masque avec mélange (blend) du masque et de l'image

Je souhaite ici accroître l'impression de perspective (relief) des
Pagodes...

##### Préparation

- j'aurais pu ici utiliser des outils spécifiques pour accroître
  l'impression de relief, comme CBDL ("contrast by detail levels") ou
  Wavelet pyramid (Local contrast & wavelets)
- mais à titre pédagogique je vais utiliser un masque avec "blend"
- je ne retrace pas les démarches de démarrage qui sont identiques
- à retenir : "Scope color" réglée à 40 (arbitraire), et "Color and
  Light" en mode "advanced"

<img src="/images/maskblendprepa1.jpg" title="maskblendprepa1.jpg" width="600"
alt="maskblendprepa1.jpg" /> Fichier raw (Creative Common
Attribution-share Alike 4.0):
[12](https://drive.google.com/file/d/1GdqejdnbW1kJFNY6y9sdQDlF2rCEGMCu/view?usp=sharing)

##### Réglages du mask - ce qu'il ne faut pas faire

- A titre pédagogique j'utilise 2 fonctionnalités:
  - Courbe LC(H) pour sélectionner les couleurs
  - "Mask Blur" qui associe un "contrast threshold" et une fonction de
    floue (blur)
- A noter la case à cocher "FFTW", qui certes consomme des ressources,
  mais accroît les possibilités ainsi que la qualité des résultats :
  dans le cas sans FFTW le rayon (radius) est limité à 100, avec FFTW
  celui-ci est porté à 1000.

<figure>
<img src="/images/maskblendshow2.jpg" title="maskblendshow2.jpg" width="600" />
<figcaption>maskblendshow2.jpg</figcaption>
</figure>

###### Résultats

- Là encore, activez le masque "Enable mask"
- réglez "blend" à votre souhait
- éventuellement ajustez "Smooth radius mask"
- si vous avez activé les réglages "non mask" de "Color and light"
  (lightness, contrast, etc.), le curseur "Structure spot" va avoir une
  incidence.
- vous pouvez constater que l'image a maintenant une dominante de
  couleur... La cause, la courbe LC(H) qui utilise "blend", donc amène
  un changement de couleur
  - essayez de passer la courbe en mode "linear", vous verrez la
    disparition de la dominante
  - conséquence : évitez de mettre plusieurs réglages masques impliquant
    ou non "blend"
  - si vous avez besoin de ces 2 réglages, il est souhaitable comme dans
    le cas vu plus haut "masque simple" soit de créer un deuxième (ou
    plus) RT-Spot avec "dupliquer", l'un avec "blend", l'autre sans (ou
    avec des valeurs de "blend" différentes), soit d'utiliser un autre
    masque associé à un autre outils.

##### La bonne démarche

Comme vu plus haut, elle consiste à procéder en 2 étapes, par exemple en
créant 2 spots

- le premier pour prendre en compte la courbe LCH..
- le second qui va agir sur la structure

###### Action sur la structure

Plusieurs outils de type "mask" (en mode "advanced") permettent de
modifier la structure

- "Mask Blur" qui associe un "contrast threshold" et une fonction de
  floue (blur)
- "Mask structure" qui agit directement sur la structure du "mask"
- Pour ces deux outils, les courbes LCH peuvent être inactives (pas de
  courbes); si vous le souhaitez vous pouvez associer la courbe L(L) de
  LCH;
- Ces 2 outils "Mask blur" et "Mask Structure" peuvent être associés

<!-- -->

- "Mask levels local contrast" et "Mask wavelet levels", peut être
  associé à la courbe de création de masque L(L) et générer un "local
  contrast"

Rappel:

- Là encore, activez le masque "Enable mask"
- réglez "blend" à votre souhait
- éventuellement ajustez "Smooth radius"

<figure>
<img src="/images/maskblend2.jpg" title="maskblend2.jpg" width="600" />
<figcaption>maskblend2.jpg</figcaption>
</figure>

#### Comment se servir de Common Color Mask - puis Exemple de combinaison avec une fusion de 2 RT-Spot

Voir dans Principes généraux [Masque commun
couleur](Local_Lab_controls/fr#Masque_commun_couleur.md)

Ce masque ne fonctionne pas exactement comme les autres masques de
"Local adjustments". Il ne vient pas en complément d'un outil, comme par
exemple le masque dans "Color and light", mais est un outil en lui même.
Vous pouvez vous en servir pour changer l'apparence d'une image -
contraste, luminance, couleur....mais aussi texture.

- cet outil fonctionne en prenant en compte le masque qui vient modifier
  l'image (en plus ou en moins). L'écart des couleurs entre l'image +-
  masque et l'image originale est régulée par la prise en compte du
  deltaE - ΔE - et bien sûr des transitions.
- bien sûr vous pouvez l'utiliser aussi en association avec d'autres
  outils dans le même RT-spot ou non
- l'exemple donné - simple - permet de comprendre le fonctionnement; Il
  rentre dans la "philosophie" de "Local adjustments"...utiliser le ΔE

##### Préparation

Je ne reprends pas toutes les étapes, seulement celle de l'ouverture de
l'outil

- "Add tool to current spot...", "Common color mask" - "Normal", et à
  titre pédagogique pas d'autres outils ouverts.
- pour l'élaboration du masque, je vais simplifier au maximum en ne
  prenant que 2 courbes C(C) et L(L) et en prenant en compte les
  références du RT-spot
- notez que les 2 curseurs "Add / substract mask luminance" et "Add /
  substract mask chrominance" ne sont pas à zéro, afin que l'utilisateur
  ne soit pas dérouté par une absence de réponse du système; les 2
  valeurs -10 sont arbitraires et de faible amplitude.

<img src="/images/common-maskprepa1.jpg" title="common-maskprepa1.jpg"
width="600" alt="common-maskprepa1.jpg" /> Fichier raw (Creative Common
Attribution-share Alike
4.0):[13](https://drive.google.com/file/d/1aWvYbW-rDPQaLWoRzbK5HAcz9dU0GHFU/view?usp=sharing)

##### Masque luminance

J'ai choisi une action simple sur la luminance et de relativement faible
amplitude.

- remarquez la position du sommet de la courbe sur la transition
  grise....Le masque "Luminance" s'accorde avec la référence du RT-spot

<figure>
<img src="/images/common-mask-showL1.jpg" title="common-mask-showL1.jpg"
width="600" />
<figcaption>common-mask-showL1.jpg</figcaption>
</figure>

##### Masque chrominance

- remarquez la position du sommet de la courbe sur la transition
  grise....Le masque "Chrominance" s'accorde avec la référence du
  RT-spot

<figure>
<img src="/images/common-mask-showC1.jpg" title="common-mask-showC1.jpg"
width="600" />
<figcaption>common-mask-showC1.jpg</figcaption>
</figure>

##### Preview ΔE

C'est à partir d'ici que vous pourrez jouer sur le deltaE (ΔE), entre
"Image +- Masque" et "Image originale"

- essayez d’accroître ou réduire "Scope" (attention c'est le curseur de
  "common color mask" qui a une action).
- essayez les réglages de "settings" - "Shape detection" : "Threshold ΔE
  scope", "ΔE decay", "Balance ΔE ab-L", "Balance ΔE C-H"

<figure>
<img src="/images/common-mask-previewdE1.jpg" title="common-mask-previewdE1.jpg"
width="600" />
<figcaption>common-mask-previewdE1.jpg</figcaption>
</figure>

##### Show modifications

Allez dans "Show modifications with mask"

- agissez sur "Add / substract mask luminance" et "Add / substract mask
  chrominance" (j'aurais pu appeler ces curseurs "Opacité")

<figure>
<img src="/images/common-mask-modif1.jpg" title="common-mask-modif1.jpg"
width="600" />
<figcaption>common-mask-modif1.jpg</figcaption>
</figure>

##### Résultat

Vous pouvez changer:

- "Scope" (toujours celui de "Common color mask" qui agit sur le ΔE)
- activer "Smooth Radius"... qui va tenter de réduire les artefacts dus
  à l'élaboration du masque par les 3 courbes - C(C), L(L), LC(H).
- chroma
- agir sur la courbe "Contrast curve"
- essayez dans "settings" - "Scope Mask ΔE image" : ce curseur agit sur
  la masque et prend en compte le deltaE du masque par rapport au centre
  du RT-spot, c'est différent du "Scope" (le premier curseur de "Color
  color mask") qui agit par différence entre l'image originale et le
  masque que vous avez créé

Passez en mode "advanced"

- agissez sur "Soft Radius", celui-ci va réduire les artefacts entre
  l'image originale et celle obtenue après "addition" du masque. Par
  défaut même en mode "normal" (il est à 1) ce qui induit un petit
  changement - même sans masque - dans "show modifications".
- essayez "Laplacian threshold", et notez les différences avec "Smooth
  radius"
- essayez "Gamma mask" et "Slope mask"
- essayez de changer la structure par un des outils fournis : "Mask
  Structure", "Mask Blur", "Mask levels local contrast"
- essayez "Graduated Filter"

<figure>
<img src="/images/common-mask1.jpg" title="common-mask1.jpg" width="600" />
<figcaption>common-mask1.jpg</figcaption>
</figure>

Maintenant nous allons améliorer cette image "common color mask" avec
l'outil "Merge file" de "Color and Light"

##### Ajouter un nouveau RT-spot "Color & light - Advanced"

Toujours à titre pédagogique, sans recherche artistique, je vais
expliquer comment réaliser 3 modes de fusion parmi les 21 possibles

- ajoutons un nouveau RT-spot
- créons un outil "Color & Light" - "Advanced"
- réglons correctement "Scope" (avec Preview ΔE)
- choisissons 3 réglages pour accroître la luminance, le contraste et la
  chrominance

<figure>
<img src="/images/common-color1.jpg" title="common-color1.jpg" width="600" />
<figcaption>common-color1.jpg</figcaption>
</figure>

##### Préparer le "merge" (fusion en français)

- choisir "Previous spot", on va donc fusionner le nouveau RT-spot
  (Color and Light) et le précédent (Common color mask)

<figure>
<img src="/images/common-color-prepa1.jpg" title="common-color-prepa1.jpg"
width="600" />
<figcaption>common-color-prepa1.jpg</figcaption>
</figure>

##### Première fusion en mode "normal"

- choisir le mode de fusion "normal"
- arbitrairement j'ai choisi 3 réglages : Merge background = 54.2 prend
  en compte le deltaE entre les 2 couches; Opacity = 54.2 - environ 50%
  pour chacun; Contrast threshold = 12.5 - prend en compte les
  différences aplats / structure
- les deux valeurs 54.2 identiques sont le fait du hasard, il est
  évident que vous pouvez choisir d'autres valeurs 43, 68, etc.

<figure>
<img src="/images/common-color-normal1.jpg" title="common-color-normal1.jpg"
width="600" />
<figcaption>common-color-normal1.jpg</figcaption>
</figure>

##### Deuxième fusion en mode "SoftLight (legacy)"

- changer de mode de fusion et choisir "Softlight (legacy)"

<figure>
<img src="/images/common-color-softphot1.jpg" title="common-color-softphot1.jpg"
width="600" />
<figcaption>common-color-softphot1.jpg</figcaption>
</figure>

###### Troisième fusion en mode "Color Burn"

- changer de mode de fusion et choisir "Color Burn"
- bien sûr ces 3 choix de modes de fusion sont arbitraires
- notez les différences de rendus en luminance et chrominance

<figure>
<img src="/images/common-color-colburn1.jpg" title="common-color-colburn1.jpg"
width="600" />
<figcaption>common-color-colburn1.jpg</figcaption>
</figure>

##### Plus

Bien sûr, vous pouvez créer autant de "Common color mask" que vous
souhaitez, dupliquer ce "masque" près de l'autre avec des réglages
proches...

Rappel sur les courbes des masques : C(C), L(L), LC(H)

- Ces courbes permettent de créer le masque
- Pour chacune des courbes la ligne de séparation verticale gris foncé /
  gris clair représente les 3 références du RT-spot respectivement :
  Luminance, Chroma et Teinte (hue)
- lorsque la courbe est de premier type ci-dessous, le sommet de la
  courbe sur la sélection (ici L), la sélection deltaE est améliorée
- lorsque la courbe est de deuxième type ci-dessous - la sélection de
  teinte pour le masque correspond à la références teinte du RT-spot (le
  sommet de la courbe sur la sélection - ici H -), comme la courbe
  inversée, cette couleur (ou L, ou C) sera réduite et l'incidence sur
  la luminance et la chrominance du masque maximum.
- lorsque la courbe est de troisième type ci-dessous, la sélection de
  teinte pour le masque ne correspond pas à la références teinte du
  RT-spot, et la courbe inversée, cette couleur (ou L, ou C) sera
  réduite et l'incidence sur la luminance et la chrominance du masque
  maximum.

<figure>
<img src="/images/mask-curve.jpg" title="mask-curve.jpg" width="600" />
<figcaption>mask-curve.jpg</figcaption>
</figure>

- J'ai fait le choix pour cette démonstration d'une image à 2
  dominantes, magenta (fleur) et vert (feuilllage). Une image plus
  variée (ciel, mer, montagne, maisons, champs, fleurs, portraits...) va
  autoriser un usage plus riche des masque, car plus de couleurs /
  luminance / chrominance à prendre en compte.
- j'ai aussi fait le choix de rester dans la "philosophie" de "Local
  adjustments", s'appuyer sur les références du RT-spot. J'aurais pu
  faire l'inverse, comme évoqué dans les courbes ci-dessus. Les
  résultats auraient été totalement différents.
- De même, j'ai fait le choix dans la fusion (merge) de choisir la même
  gamme de couleur que pour le masque, j'aurais pu faire un autre choix
  pour le deuxième RT-spot, en le positionnant sur le feuillage...La
  fusion aurait été différente, avec moins de variation dans les
  fleurs...c'est un choix pédagogique

#### Une approche de traitement complet - Portrait sombre - peau granuleuse - Mairi

Le portrait de Mairi, va être l'occasion d’utiliser plusieurs outils:

- accroître "l'exposition" de l'image pour qu'elle soit moins sombre
- utiliser "CBDL" pour adoucir la peau et "Clarity" pour éclaircir le
  visage
- réaliser un "graduated filter" pour dégager les ombres du visage à
  droite
- utiliser 3 "excluding spot" pour "exclure" les yeux et les lèvres du
  traitement
- utiliser un "masque LC(H)" pour "exclure" les cheveux de
  l'adoucissement (et donc perte de définition)
- comparer avant après
- remarque : les réglages ont donnés à titre indicatif, tout est
  fonction de son goût....

<img src="/images/mairi.jpg" title="mairi.jpg" width="600" alt="mairi.jpg" />
Fichie raw (Copyright Pat David - Common Attribution-share Alike 4.0):
[14](https://drive.google.com/file/d/1m4UBhES2AVe_sJNqMVSz5jA-Qg-s7LHt/view?usp=sharing)

##### Accroître exposition

Exposure + 0.5 J'aurais pu utiliser un RT-spot pour limiter la zone qui
sera accrue en exposition au lieu d'un accroissement global de
l'exposition.
<img src="/images/mairiexp05.jpg" title="mairiexp05.jpg" width="600"
alt="mairiexp05.jpg" />

##### Utiliser Contrast By Detail Level

- Créer un RT-spot avec un "gros" Spot Size = 47
- Réduction progressive du contraste pour les niveaux 0 à 4
- Clarity à 60
- Scope à 40

<figure>
<img src="/images/mairi-cbdl_1.jpg" title="mairi-cbdl_1.jpg" width="600" />
<figcaption>mairi-cbdl_1.jpg</figcaption>
</figure>

##### Graduated Filter

- Créer un autre spot "Color & Light"
- Graduated filter : luminance -0.6 ; Gradient angle = 5
- vous pouvez aussi (advanced) jouer sur la chrominance

<figure>
<img src="/images/mairi-grad1.jpg" title="mairi-grad1.jpg" width="600" />
<figcaption>mairi-grad1.jpg</figcaption>
</figure>

##### Exclure les yeux et les lèvres

- Créer 3 RT-spot "exluding" sur les yeux et les lèvres
- agir sur Scope (excluding) pour obtenir le résultat recherché

<figure>
<img src="/images/mairi-excluding1.jpg" title="mairi-excluding1.jpg"
width="600" />
<figcaption>mairi-excluding1.jpg</figcaption>
</figure>

##### Masque pour exclure les cheveux

- revenir au premier RT-spot
- aller sur masque
- show mask
- utiliser la courbe LC(H)
- repérer la couleur de la peau (séparation des zones grises)
- abaisser la courbe comme sur le graphique (ou similaire)
- agir sur Smooth radius mask
- agir éventuellement sur "gamma", "slope" et "contrast curve" mask

\[\[<File:mairi-mask_1.jpg%7C600px%7Cthumb%7Ccenter%7CMasque>

##### Résultat

- mettre mask sur none
- cocher "enable mask"

<figure>
<img src="/images/mairi-fin1.jpg" title="mairi-fin1.jpg" width="600" />
<figcaption>mairi-fin1.jpg</figcaption>
</figure>

##### Comparaison avant après

<figure>
<img src="/images/mairi-befaft1.jpg" title="mairi-befaft1.jpg" width="600" />
<figcaption>mairi-befaft1.jpg</figcaption>
</figure>

##### Une alternative - remplacer Contrast by detail levels par "wavelet contrast by level"

- Le module "wavelet" est plus performant que Contrast By Detail
  Levels....il peut sembler plus complexe...vu le nombre d'options.
- Il permet à contrario de CBDL de différencier l'action avec notamment
  les curseurs "Attenuation Response" et "offset" : au lieu d'avoir une
  réponse linéaire sur le signal de la décomposition - même amplitude
  pour les petites valeurs (bruit) et les grosses valeurs -
  l'amplification (ou la réduction) prend en compte la valeur du signal.
- bien sûr vous disposez aussi d'une fonction "Clarity"

<img src="/images/mairi-wav_1.jpg" title="mairi-wav_1.jpg" width="600"
alt="mairi-wav_1.jpg" />

##### Et bien sûr, vous pouvez utiliser un masque avec "wavelet"

<figure>
<img src="/images/mairi-wavmask1.jpg" title="mairi-wavmask1.jpg" width="600" />
<figcaption>mairi-wavmask1.jpg</figcaption>
</figure>

#### Ajouter une bordure à une image

##### Généralités

Vous pouvez utiliser les ajustements locaux pour ajouter une bordure à
une image. Cette bordure peut être: blanche, noire, grise ou colorée.

Vous pouvez télécharger les fichiers pp3 suivants. Bordure Blanche
[15](https://drive.google.com/file/d/1fDIQl7Vp82SA4iY4TwwDazFpu97en0Fz/view?usp=sharing)
Bordure Grise
[16](https://drive.google.com/file/d/1mXM1zRaA8w8yai7UGgkae_lg7VggjmCK/view?usp=sharing)
Bordure Colorée
[17](https://drive.google.com/file/d/1Ztj8y1XFwlJ7fH0WXco8WRRKa6G4BzQm/view?usp=sharing)
Bordure Noire
[18](https://drive.google.com/file/d/1KND7KTPfHybarkcUiSibtJ3FqISRUl9q/view?usp=sharing)

Contrairement à d'autres logiciels qui ajoutent une bordure à
l'extérieur de l'image (en accroissant sa taille), cette procédure rogne
l'image de la partie concernée par le bord.

Vous pouvez bien sûr personnaliser ces bordures : changer les dimensions
(bords verticaux ou horizontaux), changer la couleur. Vous pouvez
utiliser "partial paste" pour mettre en place cette modification sur les
images de votre choix.

Je tiens à remercier Arturo Isilvia pour sa contribution à ces presets.

##### Les deux RT-spots

Ce module est constitué de deux RT-spots:

- le premier, utilise le mode "full image". Il rend le fond de l'image
  noir, blanc, gris ou coloré.
  - il met en œuvre l'outil "Color and Light"
    - pour les bordures noires, blanches ou grises, l'outil "RGB Tones
      Curve" est utilisé.
    - pour les bordures colorées, c'est l'outil "Color correction grid"
      qui est utilisé.
- le second, est en mode "excluding", utilise un rectangle qui assure
  les limites de la bordure

##### Le premier RT-Spot

###### Détails des réglages du premier RT-Spot - Bords noirs, Gris, Blancs

<figure>
<img src="/images/Borderrgb.jpg" title="Borderrgb.jpg" width="600" />
<figcaption>Borderrgb.jpg</figcaption>
</figure>

- Color and Light est utilisé en mode "Avancé"
- Seul l'outil RGB Tone Curve est utilisé. Le réglage correspond à
  l'exemple ci-dessus (bord gris).
- Dans "Settings" - transition est réglé sur 100.

###### Détails des réglages du premier RT-Spot - Bords colorés

<figure>
<img src="/images/Bordergrid.jpg" title="Bordergrid.jpg" width="600" />
<figcaption>Bordergrid.jpg</figcaption>
</figure>

- Lightness, Contrast, Chrominance sont réglés à -100; Gamma à 0.5
- Choisissez la couleur de votre choix dans "Color correction grid"- ici
  le réglage de base est vert.
- Dans "Settings" - les réglages suivants sont nécessaires : transition
  = 100, Scope = 100, DeltaE scope threshold = 10.

##### Le deuxième RT-Spot

<img src="/images/Borderexcluding.jpg" title="Borderexcluding.jpg" width="600"
alt="Borderexcluding.jpg" /> Notez les réglages suivants:

- Scope = 100, Transition = 100, DeltaE scope threshold = 10
- La "shape method" utilisée est "Symmetrical (mouse + sliders)" (dans
  “Show additional settings” \> “Specific cases” \> “Shape method”).
  Vous pouvez facilement changer les valeurs de "Right" et "Bottom" qui
  permettent ainsi de régler les dimensions de la bordure:
  - "Right" change la largeur (partie verticale).
  - "Bottom" change la hauteur (partie horizontale).

## HDR-SDR Première approche : Log encoding – Cam16 – JzCzHz – Sigmoid

Les images à dynamique élevée sont l'un des problèmes récurrents du
traitement d'images. Il existe déjà plusieurs algorithmes:

- dans les onglets Exposition et Couleur de RawTherapee qui peuvent être
  utilisés pour réduire la plage dynamique, avec plus ou moins de succès
  :Dynamic Range Compression, Shadows/Highlights,
- dans l'onglet Local, Dynamic Range & Exposure, Tone Equalizer, Tone
  Response Curve, Wavelets, etc.

Ils ont été complétés par un module supplémentaire de codage
logarithmique **Log Encoding** dans l'onglet Ajustements locaux pour
faciliter le traitement des images à gamme dynamique élevée. Une version
simplifiée, **Using the Cam16 and HDR functions** du module Color
Appearance & Lighting (Ciecam02/16) de l'onglet Advanced du menu
principal a également été adaptée aux exigences spécifiques des réglages
locaux et étendue pour prendre en compte le pic de luminance HDR. Il
inclut également une fonction **experimental JzCzHz** (en mode Avancé)
pour améliorer le traitement HDR.

Attention, les explications ci-après peuvent être sujet à controverse du
fait, notamment pour JzCzHz et une partie de Cam16:

- absence de documentation pour JzCzHz;
- mauvais fonctionnement de l'algorithme de base des chercheurs (défaut
  de saturation, mauvais comportement avec les ombres profondes, ...)
  pour JzCzHz;
- mon interprétation personnelle, pour résoudre les dysfonctionnements.

### **Log encoding**

Cette partie de Rawtherapee est :

- très proche dans son code et son utilisation du module « Log Tone
  mapping » de ART – merci à Alberto Griggio de l'avoir conçu,
- proche du module « Filmic » de Darktable (travaillant en mode RGB)
- tous s'inspirent des travaux sur le codage logarithmique élaboré par
  « The Academy Color Encoding System (ACES) ».

Dans une première étape, pour une image donnée, qu'elle soit ou non HDR,
l'algorithme calcule l'écart par rapport au gris moyen théorique – gris
à 18% - du noir le plus prononcé et du blanc le plus vif, exprimés en
unité photographique (indice de lumination Ev- en relation avec la
luminosité de la scène). Ces deux valeurs, ainsi que la luminance
moyenne de la scène (Mean luminance Yb%) sont utilisés par l’algorithme
– automatiquement (ou avec reprise manuelle) - pour modifier l'équilibre
des valeurs RGB, réduisant de fait les contrastes, en rehaussant les
ombres et réduisant les hautes lumières, sans trop dénaturer le rendu de
l'image.

Dans une seconde et troisième étape, les données sont corrigées
manuellement par l'utilisateur – accroissement du contraste local
(affaibli par la conversion 'Log') et ajustement des conditions de
visualisations au moment de l'affichage de l'image sur les périphériques
de sortie.

#### Exemple Adaptation chromatique

La première étape : réaliser une balance des blancs - presque
mathématiquement parfaite - en utilisant "White Balance" - "Auto" -
"Temperature correlation" - (même exemple et mêmes réglages que dans le
tutoriel "Ciecam advanced tab")

Fichier raw (Rawtherapee - Creative Common Attribution-share Alike
4.0)[19](https://drive.google.com/file/d/1CiQ2t4KyD3tdCiNNhskqUG2cH9LT2ly7/view?usp=sharing)

<figure>
<img src="/images/catATwb.jpg" title="catATwb.jpg" width="600" />
<figcaption>catATwb.jpg</figcaption>
</figure>

##### Choisir un réglage "Local adjustements" adapté - Préparation

- Sélectionner "Local adjustments"
- Spot "rectangle", très largement au delà des limites du preview (pour
  permettre de déplacer le centre du RT-spot)
- transition = 100
- mettez en place quelques "lockable color picker"

<figure>
<img src="/images/catLAset.jpg" title="catLAset.jpg" width="600" />
<figcaption>catLAset.jpg</figcaption>
</figure>

##### Sélectionnez Log encoding

Choisissez : Add tool to current spot : Log encoding
<img src="/images/catLAlog.jpg" title="catLAlog.jpg" width="600"
alt="catLAlog.jpg" />

- Essayez de changer la place du centre du RT-spot
- Essayez de change "Scope" : 40 - 60 - 80 - 100
- Observez les résultats
- Mais l'image est toujours jaunâtre

Nouvelle Interface - branch lacam16
<img src="/images/catLAlog2.jpg" title="catLAlog2.jpg" width="600"
alt="catLAlog2.jpg" />

##### Modifier Chromatic adaptation - cat02

<figure>
<img src="/images/catLAlogadap.jpg" title="catLAlogadap.jpg" width="600" />
<figcaption>catLAlogadap.jpg</figcaption>
</figure>

- Refroidir l'image en déplaçant le curseur "Chromatic adaptation cat02"
  vers la gauche
- pour refroidir 10 unités correspond à une baisse de Température de
  l'illuminant de 300K
- Essayez -23

#### Image à forte dynamique + Ciecam

L'image choisie est difficile (la même que celle pour Ciecam advanced
tab) : ombres très marquées et arrière plan éclairé en plein soleil.
Utilisez les traitements par défaut de Rawtherapee. Positionnez des
"Lockable color picker" afin de visualiser le traitement.

Fichier raw (Pixls.us Creative Common Attribution-share Alike 4.0)
[20](https://drive.google.com/file/d/1ctjOWX2lVmgcAzJtBwt69FGpxZOq-LyP/view?usp=sharing)
<img src="/images/ciecam_light_prepa.jpg" title="ciecam_light_prepa.jpg"
width="600" alt="ciecam_light_prepa.jpg" />

##### Utiliser Log encoding + Ciecam

Choisissez "add tool to current spot" : Log encoding Pour l'exemple, et
la comparaison avec "Ciecam & Light", le choix (arbitraire) est fait de:

- spot rectangle - au delà du preview
- transition = 100
- scope = 79
- niveau de complexité : advanced
- Pressez le bouton "Automatic"...

<figure>
<img src="/images/ciecamlog1.jpg" title="ciecamlog1.jpg" width="600" />
<figcaption>ciecamlog1.jpg</figcaption>
</figure>

- Déplacez le RT-spot, observez les effets
- Changez "Scope" , observez les effets

##### Utiliser Log encoding et les réglages Ciecam

- Scene conditions , choisissez "Surround = Dim"; l'image va s'éclaircir
- Image Adjustments, Saturation (s) = 30, Contrast (J) = -10
- Observez l'image dans les ombres..

<figure>
<img src="/images/ciecamlog_cie.jpg" title="ciecamlog_cie.jpg" width="600" />
<figcaption>ciecamlog_cie.jpg</figcaption>
</figure>

Maintenant, ouvrez l'expander "All tools"

- essayez Colorfulness (M) à la place de saturation (s)
- essayez Contrast (Q) à la place de Contrast (J)
- agissez sur Lightness

#### Log encoding - Dodge and Burn - Ciecam

##### Préparation

Encore une autre manière de réaliser un Dodge and Burn avec l'appoint de
Ciecam Positionnez le RT-spot sur le visage, et mettez 2 "Lockable color
pickers"

Fichier raw (Copyright - Jean Christophe Frisch - Common
Attribution-share Alike
4.0)[21](https://drive.google.com/file/d/1oyPu-U6CD1DjWuO8LuqJdIdDau1-2yY1/view?usp=sharing)
<img src="/images/Dblogciecamprepa.jpg" title="Dblogciecamprepa.jpg" width="600"
alt="Dblogciecamprepa.jpg" />

##### Utiliser Log encoding - manuel et Ciecam

- Add tool to current spot : Log encoding
- complexité : advanced
- Cliquez sur automatic
- puis accroissez légèrement White Ev, jusqu'à obtenir l'effet souhaité
  (dans l'exemple de 3.0 à 5.0)
- accroissez légèrement la Saturation (s)
- déployez expander "all tools", et réduisez légèrement Brightness (Q)
- essayez les autres réglages : Dim, lightness, etc.
- vous pouvez agir sur Scope et déplacer le RT-spot

<figure>
<img src="/images/Dblogciecam.jpg" title="Dblogciecam.jpg" width="600" />
<figcaption>Dblogciecam.jpg</figcaption>
</figure>

### **Log Encoding et récupération des hautes lumières**

Voir dans : Quelques particularités du mode local (par rapport à Lab
adjustements) [Log
Encoding](Local_Lab_controls/fr#Log_Encoding.md)

L'utilisation de "Log Encoding" peut quelque fois aboutir à des
résultats inattendus. Si l'image contient des hautes lumières qui ont
été surexposées à la prise de vue, la récupération est obligatoire. Mais
dans ce cas, "Encoding log" va "écraser" ces hautes lumières
reconstruites, aboutissant à des effets peu agréables. Nous utiliserons
2 manières de préserver ces hautes lumières:

- avec un masque et un processus de récupération
- avec des "excluding spots"

#### Préparation

Fichier raw (Pixls.us - Common Attribution-share Alike
4.0):[22](https://drive.google.com/file/d/1I-Y6xqFoYMaxj9v3uEcvXfZomuJxyX6R/view?usp=sharing)
Fichier pp3
[23](https://drive.google.com/file/d/1JQG52i76FxFWUWqi4Mz_5seWpLD-rvT6/view?usp=sharing)

Plusieurs étapes à la préparation (non reprises dans ce descriptif)

- régler la balance des blancs : à part la personne qui a pris cette
  image, on ne sait rien des conditions de prises de vue. A l'arrière
  plan sont-ce des LED ? ou des lampes à incandescence ? Et pour le
  premier plan ?
  - vous pouvez laisser l'image telle quelle
  - ou utiliser la balance des blancs automatique : "temperature
    correlation"
- "highlight reconstruction" : j'ai utilisé ici l'excellent algorithme
  de Emil Martinec "Color Propagation"
- régler l'arrière plan des masques afin que la lecture des valeurs
  L\*a\*b\* des "Lockable Color pickers" correspondent aux valeurs
  réelles
  - dans "Local adjustments" - "Settings" -"Mask and merge" -
    "Background color for luminance and color masks = 0"

Préparation du RT-Spot

- choisissez "Rectangle"
- positionnez les délimiteurs en dehors du "preview"
- réglez la transition à une valeur assez élevée
- positionnez sur l'image une série de "Lockable Color pickers"

<figure>
<img src="/images/loghigh-prepa.jpg" title="loghigh-prepa.jpg" width="600" />
<figcaption>loghigh-prepa.jpg</figcaption>
</figure>

#### Appliquer Encoding Log

- ajouter l'outil "Encoding Log" : Add tool to current spot...
- sélectionnez "advanced" (ou standard)
- cliquez sur le bouton "Automatic"
- réglez "Scope" à une valeur élevée : 80 ou plus

"Log Encoding" va faire son travail notamment sur l'avant plan, mais
l'arrière plan avec les hautes lumières "reconstruites" précédemment
voit les couleurs se délaver, la luminance maximum baisser.

D'autre part, l'image après cette opération semble trop saturée et
l'exposition mal répartie.

<figure>
<img src="/images/loghigh-log.jpg" title="loghigh-log.jpg" width="600" />
<figcaption>loghigh-log.jpg</figcaption>
</figure>

#### Elaboration du masque

Nous allons élaborer un masque qui sera utilisé d'une manière différente
des autres processus dans RT. Ce masque sera utilisé "en direct" et son
analyse va servir à combiner l'image sans l'action de "Encoding log",
avec l'image traitée avec "Log Encoding"

Selon les réglages de "Recovery based on luminance mask":

- les zones sombres et noires du masque donneront la possibilité de
  ramener l'image combinée au plus près de l'image originale.
- les zones très claires ou blanches du masque donneront la possibilité
  de ramener l'image combinée au plus près de l'image originale.
- la zone intermédiaire conservera les réglages de "Encoding log".

Dans le cas présent je me suis servi de la courbe LC(H), d'autres images
nécessiteront la courbe L(L). A noter que la courbe C(C) n'a aucune
incidence sur le "mélange" mais peut être utilisée pour améliorer la
sélection.
<img src="/images/loghigh-mask.jpg" title="loghigh-mask.jpg" width="600"
alt="loghigh-mask.jpg" />

#### Récupération partielle des hautes lumières avec masque

- Assurez vous que le masque est activé : case "Enable mask" cochée
- dépliez l'expander "Recovery based on luminance mask"
- agissez sur "Recovery threshold" : plus le curseur sera proche de "2",
  plus les zones sombres et très claires du masque seront prises en
  compte, plus ces zones seront ramenées aux valeurs de l'image
  originale
- agissez sur les curseurs "Dark area luminance threshold" et "Light
  area luminance threshold" pour inclure ou exclure certaines parties de
  l'image. Les valeurs correspondantes (ici dark = 25.5 et Light = 98.3)
  sont les 2 limites en deçà et au delà desquelles les actions du masque
  seront progressivement prises en compte.
- agissez éventuellement sur "decay" pour régler la "vitesse" de la
  décroissance.

<figure>
<img src="/images/loghigh-recov.jpg" title="loghigh-recov.jpg" width="600" />
<figcaption>loghigh-recov.jpg</figcaption>
</figure>

#### Récupération des hautes lumières avec 'Excluding spot'

Bien sûr la "force" de "Local adjustments" est toujours présente. Vous
pouvez rétablir l'image originale en utilisant les "excludings
spots".... Les réglages sont arbitraires...
<img src="/images/loghigh-exclu.jpg" title="loghigh-exclu.jpg" width="600"
alt="loghigh-exclu.jpg" />

#### Ajustement final avec Ciecam16

Maintenant, une fois les divers traitement "Color propagation", "Local
adjustments" réalisés, on peut affiner le résulat. Dans ce cas j'ai
choisi divers réglages Ciecam (ici Ciecam 2016).

- accroissement du contraste
- réduction de la saturation, notamment pour la peau
- changement de l'adaptation chromatique, pour rendre l'image un peu
  plus "froide"...
- mais tout est assez arbitraire....selon la perception de chacun

Dernière remarque:

- l'image est particulièrement bruitée
- je n'ai pas souhaité "ajouter" ce traitement, mais il est évident
  qu'il faut le faire.

<figure>
<img src="/images/loghigh-ciecam.jpg" title="loghigh-ciecam.jpg" width="600" />
<figcaption>loghigh-ciecam.jpg</figcaption>
</figure>

### **Autre exemple avec Log Encoding**

Les images à forte dynamique sont un des problèmes récurrents du
traitement d'image. Plusieurs algorithmes dans Rawtherapee permettent un
traitement plus ou moins complet de ces problèmes : Dynamic range
compression, Shadows / highlight, Tone Equalizer, Tone Response Curve,
etc.

- dans le cas présent je tiens à montrer l'outil "Encoding Log" (Origin
  Filmic - Darktable - adapté à ART par A.Griggio). J'ai adapté
  légèrement cet outil à Rawtherapee - "Local adjustments"
- je l'ai associé à un autre objectif pédagogique : réaliser un gradient
  de luminance, sans faire appel au Graduated filter pourtant présent
  dans le menu "Encoding Log"
- Trois étapes : préparation, réglages automatiques, ajustements

#### Préparation

- Régler le RT-spot de telle manière que :
  - le centre se trouve en bas à gauche de l'image
  - le coin supérieur droit soit aux limites de l'image
- Aller à "Add tool to current spot..." : "Encoding log" (j'ai
  volontairement désactivé l'outil)

<img src="/images/encodlogprepa.jpg" title="encodlogprepa.jpg" width="600"
alt="encodlogprepa.jpg" /> Fichier raw (Copyright - Roberto Posadas -
Common Attribution-share Alike 4.0):
[24](https://drive.google.com/open?id=1RXoXp-AHWzo6mzbd-VyRTRvmRlFtyZDq)

#### Réglages automatiques

- Appuyez sur le bouton "Automatic"
- l'image va s'éclaircir
- re-cliquez sur le bouton "Automatic" pour mieux percevoir les réglages
- Black Ev = -6.7, White Ev = 6.9 : traduisent une dynamique de 13.6 EV
  très importante
- Source gray point : value (réglée en automatique) = 1.2
- ces 2 réglages (que vous pouvez changer) traduisent les calculs
  réalisés en amont du processus après la conversion vers un espace de
  travail

<figure>
<img src="/images/encodlogaut.jpg" title="encodlogaut.jpg" width="600" />
<figcaption>encodlogaut.jpg</figcaption>
</figure>

#### Ajustements

Vous pouvez maintenant adapter l'image à vos souhaits:

- jouer sur le gradient diagonal en agissant sur "settings" -
  "Transitions" : "Transition value" = 45. vous pouvez aussi agir sur
  "Transition decay" et "Transition differentiation XY" (essayez)
- agir sur la répartition de l'action à l'intérieur de l'image en
  agissant sur Scope (Encoding log) = 50
- Changer la luminance globale de l'image en agissant sur "Target Gray
  point" = 22.0

<figure>
<img src="/images/encodloggrad.jpg" title="encodloggrad.jpg" width="600" />
<figcaption>encodloggrad.jpg</figcaption>
</figure>

### **Utilisation de Cam16 et des fonctionnalités HDR**

Voir dans Quelques particularités du mode local (par rapport à Lab
adjustements):[Cam16 et possibilités
HDR](Local_Lab_controls/fr#Color_appearance_(Cam16_&_JzCzHz) "wikilink")

#### Préambule

Le module Cam16 (Color appearance(Cam16 & JzCzHz) permet également de
prendre en compte certaines des caractéristiques d'une image qui
autoriseront un traitement HDR. Pour rappel, que ce soit « Log
encoding », « JzCzHz » ou Cam16 ne sont qu'une étape vers HDR car
l'ensemble du processus doit être pris en compte, ce qui n'est pas le
cas actuellement notamment pour la prise en compte complète du moniteur
HDR (y compris le code utilisant LCMS), la plupart de ceux en service
étant SDR.

#### Différences avec le module (main) « Color appearance & Lighting (Ciecam02/16)»

- prise en compte des caractéristiques de « Local adjustments » (deltaE,
  transitions, masques...) ;
- simplification du processus d'adaptation chromatique ;
- moins de courbes ;
- prise en compte simplifiée de la fonction PQ (Perceptual Quantizer) :
  cette fonction positionnée au début du traitement Cam16, change le
  processus interne de calcul des valeurs Brightness (Q), Lightness (J),
  Colorfullness (M), Saturation (s) et Chroma (C).
- possibilité d'utiliser « Log encoding Q » ou « Sigmoid Q » en prenant
  ou non en compte « Black Ev » et « White Ev », c'est à dire la
  dynamique d'exposition (Dynamic Range).
- possibilité d'utiliser 'Whites distribution' et 'Blacks distribution'
  [Whites & Blacks
  distribution](Local_Adjustments/fr#Whites_distribution_&_Blacks_distribution.md)

#### Quelques rappels

- les valeurs de « Scene conditions » sont calculées, d'une part par les
  algorithmes de Cam16 et, d'autre part par un processus situé en amont
  de « Local adjustments », juste après les profils « input », le
  dématricage, et le choix du profil de travail (working profile) qui
  rappelons le, est entièrement en mode linéaire.
- Les conversions RGB=\>Lab en début du processus « Local adjustments »
  (LA) et « Lab=\>RGB » en fin de processus LA ne changent pas la DR
  (Dynamic Range). Si une image présente une DR de 15Ev avant le module
  « LA », elle présente sensiblement la même après le module « LA » (les
  différences tiennent bien sûr au traitement que l'utilisateur aura
  réalisé). Par contre, comme il est évoqué ici [JzCzHz et
  Lab](CIECAM02/fr#Jzazbz_-_Un_nouveau_CAM_.3F.md), Lab si il
  permet la prise en compte des très basses lumières (moins de 0.005
  cd/m2), il ne permet pas l'étalement des hautes lumières au delà de
  120 cd/m2 du fait de l'utilisation du gamma. Mais il préserve ces
  hautes lumières, jouant en quelques sortes un rôle de compression des
  données. Cette nécessaire évolution devra être réalisée dans des
  évolutions ultérieures (HDR-Lab, processus de sortie, etc.).
- Si dans « Settings » vous cochez les 2 cases – « Avoid color shift »
  et « Munsell correction only », l'ensemble du processus « LA »
  maintiendra une constance de la teinte (hue) quelque soient les
  actions sur la saturation.

#### Cam16 - avec prétraitement HDR branch lacam16n

Une nouvelle approche de traitement intégré (avec le Tag 6.0, car des
incompatibiltés sont possibles) permet de :

- mieux exploiter le potentiel de Cam16 reconnu pour ses capacités à
  prendre en compte les aspects physiologiques du traitement d'image;
- intégrer si les images le nécessitent, un traitement HDR en amont de
  Ciecam - Cam16.

Si c'est votre premier contact avec Cam16, ou si un discours trop
technique vous rebute, vous pouvez omettre de lire le paragraphe
suivant.

##### Deux difficultés importantes: Cam16 nécessite des variables à 6 dimensions et particularités de Q (brightness)

###### Cam et les 6 dimensions

Un point de programmation est nécessaire pour comprendre certaines
difficultés et contraintes du travail avec Cam16 (c'est identique avec
Cam02). Lors de la mise au point de Ciecam, vers 2011 2012, il est
rapidement apparu que contrairement au travail en mode RGB, XYZ, ou Lab
qui nécessite des déclarations de variables à 3 dimensions, Ciecam
nécessite 6 dimensions : J luminance, Q brightness, C chromaticité, S
saturation, M colorfullness, h hue. Ceci implique une occupation mémoire
considérable et des temps de traitements importants. Le choix a été fait
d'utiliser ces variables une par une et de manière séquentielle dans une
boucle globale, ce qui limite l'occupation mémoire, mais présente un
inconvénient majeur : l'optimisation d'une procédure appelée au milieu
de la boucle est quasi impossible. En conséquence, les optimisations de
fonctions telles que contraste, sigmoid, etc. sont limitées et globales.

De plus Cam16 introduit à la fois:

- un éclaircissement des ombres (Lighting);
- un traitement perceptuel des hautes lumières;

qui rendent plus difficiles les traitements HDR de type "Log encoding".

###### Particularités de Q - Brightness

- Par conception Q (brightness) contrairement à J (lightness), L
  (L\*a\*b\*), et aux calculs de luminance en mode RGB, HSV,...est
  calculée à partir de la luminance absolue et n'a pas de limites fixes
  (0..1, 0..65535).
- Q, alors que J est dans l'intervalle \[0, 1\], peut atteindre des
  valeurs de 5 ou 10, selon les conditions de la scène. Cette réalité
  est une très forte contrainte sur les calculs des références des
  algorithmes (moyenne, seuils, etc.) et rend difficile l'automatisation
  des algorithmes.
- mais Q aboutit dans une majorité de cas, à un rendu plus naturel, plus
  proche de la perception humaine.

###### Déplacement des modules HDR - "Log encoding Q" et "Sigmoid Q" - précédemment intégrés à Cam16 Image Adjustments

![](sourcedata1.jpg "sourcedata1.jpg")Devant les difficultés induites et
décrites dans les deux précédents paragraphes, j'ai choisi:

- de mettre les outils HDR, ou de colorimétrie, dans un module "Source
  Data Adjustments", situé dans le processus en amont de Ciecam - Cam16,
  mais intégré logiquement pour l'utilisateur dans le GUI de Color
  Appearance. Ce module contient plusieurs outils plus ou moins utiles
  selon la nature de l'image:
  - Log encoding : assure un codage logarithmique des données qui permet
    de traiter les images avec une importante dynamique (Dynamic Range).
    Bien sûr vous pouvez utiliser cet outil de manière systématique,
    mais il n'est vraiment utile que si la DR est élevée, souvent
    supérieure à 10 ou plus. Son utilisation injustifiée peut amener une
    modification de la colorimétrie globale pas toujours facilement
    récupérable. Le curseur "Brightness compression" permet de limiter
    l'action pour les hautes valeurs de luminance.
  - Tone Response Curve & Midtones : vous permet dans une majorité de
    cas, de modifier les images sous exposées (avec des ombres
    profondes), ou des images ou l'équilibre de la luminance est
    perturbé. Cette approche est identique aux autres modules utilisant
    cette "TRC" dans Rawtherapee
    - Gamma: permet de modifier l'action sur les lumières;
    - Slope: permet de déboucher les ombres;
    - Midtones: permet d'ajuster les tons moyens.
    - Smooth highlights: complète le traitement effectué par le gamma,
      la pente (slope) et les tons moyens (mid tones) en provoquant une
      légère baisse des hautes lumières. Veuillez noter que cela ne
      remplace pas la reconstruction des hautes lumières.
  - Primaires & Illuminant, vous permet:
    - de retoucher la colorimétrie des images ou par exemple un mélange
      des illuminants amène des dérives visibles (LED), où lorsque les
      conditions de prise de vue (illuminant stdA, fleurs à dominante
      rouge, etc.) amènent le système à de réponses insatisfaisantes
      (saturation exagérée des bleus ou des rouges...)
    - Attention si vous changez le "Working profile" (Tab Color) qui par
      défaut est Prophoto, il vous revient d'adapter "Destination
      Primaries" (ce n'est pas automatique)
    - de modifier localement ou globalement les couleurs ou la
      saturation d'une image:
      - Le système calcule les valeurs xy de la couleur dominante de
        l'image et l'affiche (point gris) sur le diagramme CIExy;
      - Déplacer le curseur de "Refine colors (white-point)" va
        permettre de modifier la saturation de l'image
      - Modifier la position de cette couleur dominante avec les
        curseurs "Shift x" et "Shift y" va permettre d'ajouter ou
        retirer une dominante de couleurs (teinte et saturation) sans
        changer les primaires
    - Gamut control : assure un contrôle de gamut, notamment si les
      primaires ont été modifiées
    - Matrix adaptation : avec 4 choix - Bradford, Cat16, Cat02, Von
      Kries, XYZ scale - assure une adaptation chromatique lorsque les
      primaires sont changées.

Certains de ces outils sont proches du concept de "Abstract Profile".

##### Source Data Adjustments et Scene conditions

Je ne reviendrais pas sur ce qu'est "Scene conditions" (voir les
tutoriels sur Ciecam), même si cette notion est plus complexe et
incomprise que beaucoup d'utilisateurs ne le pensent. A titre de rappel
sommaire "Scene conditions" (ou Scene-referred, ou Source, selon les
usages) prend en compte les caractéristiques de l'image lors de la prise
de vue. Ceci est à différencier de "Viewing Conditions" (ou
Display-referred, selon les usages) qui prend en compte l'environnement
de visualisation. Par exemple le système de diffusion de l'image, sa
luminance, son contraste (moniteur HDR ou non, téléviseur, projecteur,
imprimante,...), où encore la luminance de l'arrière plan (en plein
soleil, dans une pièce sombre, etc.). Attention à ne pas dévoyer les
réglages de "Viewing conditions" de leur vocation, afin de palier à des
réglages imparfaits de "Scene conditions" ou de "Source Data
Adjustments".

###### Quels principes utilisent "Log encoding" et "Scene conditions" pour restituer une image et alimenter Cam16?

<img src="/images/whiteblackdisr.jpg" title="whiteblackdisr.jpg" width="400"
alt="whiteblackdisr.jpg" />Il est nécessaire de fournir à Cam16 les
notions de:

- Absolute luminance : ce calcul est réalisé à partir des données Exif à
  la prise de vue : vitesse, diaphragme, correction d'exposition,...
- Mean luminance, encore appelé "grey point". Ce calcul est réalisé
  comme décrit au paragraphe ci-après.

Il est nécessaire pour traiter les images HDR, celles à fortes dynamique
de calculer les valeurs nécessaires à la conversion logarithmique :

- BlackEv et WhiteEv, ainsi que du "grey point" évoqué ci-dessus.

Où prendre ces valeurs, comment les calculer ? La logique de "Scene
conditions" amène à se placer le plus en amont du processus de
traitement avec des données utilisables. Le choix a été (à l'origine par
ART) de prendre une copie des données de l'image juste après
demoisaicing. L'inconvénient de ce choix est que par définition l'image
n'est pas traitée et que la distribution des couleurs et lumières est
mal connu et peu fiable. La difficulté introduite par la conversion
logarithmique pour compresser les données (Log 2) est qu'elle n'est pas
linéaire.

Il faut donc, à la fois, prendre en compte le bruit numérique, estimer
les valeurs minimales et maximales RGB et estimer un point gris. Ces
réglages devraient également tenir compte des modifications possibles
ultérieures de la luminance. Des formules plus ou moins empiriques du
calcul de la luminance moyenne et du point gris résultant, ont été
élaborées par les concepteurs d'origine. Il n'empêche que le résultat
peut être décevant.

En pratique cela revient une fois les calculs réalisés à retoucher
manuellement a minima BlackEv, WhiteEv, Mean luminance (Yb% - Grey
point) source, et ou Mean luminance (Yb% - Grey point - Viewing
conditions" (ce qu'il ne faut pas faire pour ce dernier point, à
réserver à l'usage de Viewing conditions), et autres ajustements
ultérieurs de la luminance. D'où la difficulté d'obtenir un résultat de
manière intuitive.

Pour essayer de résoudre cette problématique, j'ai choisi d'ajouter 2
réglages d'ajustements des blancs et noirs extrêmes. Je les ai appelés
"White distribution" et "Black distribution". Il n'y a évidemment pas de
règles générale pour le traitement d'une image, on affaiblit ou on
renforce la partie la plus exposée ou la plus sombre de la copie de
l'image. L'algorithme interne recalcule les valeurs de BlackEv, WhiteEv
et de Mean luminance (Grey point) qui seront obligatoirement cohérentes.
L'avantage c'est (je l'espère) un système plus intuitif. Il y a peut
être d'autres moyens (?) d'y arriver; celui-ci à la mérite de
fonctionner.

Ces contrôles ne sont disponibles que si "Scene conditions" - Automatic
est cochée.

##### Le GUI de l'application a été simplifié et plus intuitif, notamment par l'utilisation d'Expanders

<figure>
<img src="/images/Cam16exp.jpg" title="Cam16exp.jpg" width="600" />
<figcaption>Cam16exp.jpg</figcaption>
</figure>

##### Tutoriel Cam16 avec une image HDR

J'ai choisi une image du pont Alexandre III à Paris, prise fin octobre
2021.

- Nikon Z6 II
- Fichier Raw (Jacques Desmis - Creative Common Attribution-share Alike
  4.0):
  [25](https://drive.google.com/file/d/17G1H-7S2uCyDa92CiJf9g35jhegvCZu_/view?usp=sharing)
- Fichier pp3 ![Alexandre3.pp3](Alexandre3-1.pp3 "Alexandre3.pp3")

Cette image présente une dynamique élevée un peu plus de 13Ev, avec
quelques zones où l'exposition (luminance) est importante (L \>= 100)

Le but de ce tutoriel n'est pas de réaliser le «meilleur» traitement de
cette image, mais de montrer l'intégration d'un module situé en amont de
Ciecam pour produire des images à très haute dynamique, afin d'être
facilement traitées ensuite par Ciecam (Cam16).

J'ai ajouté un deuxième exemple, sans rapport avec le pont Alexandre
III, pour montrer l'usage possible de "Tone Response Curve - TRC".

###### Préparation : s'assurer de bonnes conditions de démarrage - repérer les problèmes à résoudre

Je fais le premier choix suivant:

- appliquer un profil "neutral"
- appliquer la balance des blancs: Auto - Temperature correlation
- activer Highlight reconstruction: Inpaint Opposed - Gain threshold
  0.82

Avec ces réglages de base:

- les ombres de la partie supérieure droite de la charpente métallique
  sont entièrement bouchées
- les hautes lumières sont acceptables (L = 97)- sans dérives apparentes
  de couleurs
- l'histogramme montre que le canal rouge est hors limites
- l'image manque réellement d'un rendu plaisant.

<figure>
<img src="/images/Alex3-neutr.jpg" title="Alex3-neutr.jpg" width="600" />
<figcaption>Alex3-neutr.jpg</figcaption>
</figure>

###### Appliquer le rendu "Nikon" Auto-Matched Tone Curve

Par défaut Rawtherapee charge le profil de rendu Nikon Z6 II

Constat:

- l'image semble plus plaisante, plus équilibrée;
- les zones sombres sont encore plus bouchées;
- les hautes lumières sont hors limites (L \>= 100).

<figure>
<img src="/images/Alex3-automatch.jpg" title="Alex3-automatch.jpg"
width="600" />
<figcaption>Alex3-automatch.jpg</figcaption>
</figure>

###### Traiter la Dynamique élevée

- Activez l'expander Source Data Adjustments
- Activez Log encoding

Examinez le résultat:

- Dynamic Range élevée : 13.6Ev (d'après les calculs)
- les ombres sont débouchées - probablement trop !
- les lumières sont aux limites acceptables L=98
- l'histogramme montre un dépassement dans les rouges
- globalement l'image est trop lumineuse

<figure>
<img src="/images/Alex3-logencode.jpg" title="Alex3-logencode.jpg"
width="600" />
<figcaption>Alex3-logencode.jpg</figcaption>
</figure>

Pour relever les ombres, réduire les lumières:

- régler (Scene Conditions) White distribution à -74 et Black
  distribution à -59 : ces choix sont assez arbitraires dépendent de la
  perception de chaque utilisateur.
- régler Midtones (Source Data Adjustments) à -70, afin de rétablir une
  luminance moyenne plus acceptable
- relever Brightness compression (Source Data Adjustments - Log
  encoding) à 0.90 pour abaisser un peu les lumières élevées.

<figure>
<img src="/images/Alex3-dynamic1.jpg" title="Alex3-dynamic1.jpg" width="600" />
<figcaption>Alex3-dynamic1.jpg</figcaption>
</figure>

###### Rendre l'apparence de la Seine plus estivale

Le temps d'automne (et la propreté de la Seine ?) rendent l'aspect de
l'eau peu flatteur.

Nous allons la rendre (un peu) plus plaisante. Créons un deuxième
RT-Spot (Scope = 60).

Dans Source Data Adjustments, Tone Response Curves : Midtones = -70.

Dans Primaries & illuminant - allez à Dominant Color:

- Déplacez le point gris représentatif de couleur dominante avec les 2
  curseurs Shift x et Shift y
- Shift x = 0.2, Shift y = -0.0454
- De telle façon que le point blanc (white point), le point gris
  (dominant color) et le point noir représentatif de la primaire rouge
  soient sensiblement alignés.
- En déplaçant Refine color (white-point), nous allons à la fois
  modifier la teinte vers plus de bleu/vert et la saturation. Bien sûr
  j'aurais pu faire d'autres choix.

<figure>
<img src="/images/Alex3-seine1.jpg" title="Alex3-seine1.jpg" width="600" />
<figcaption>Alex3-seine1.jpg</figcaption>
</figure>

##### Un deuxième exemple - Utiliser la TRC ou Surround - Camionnette sous un tunnel

- Fichier raw (Copyright - Roberto Posadas - Common Attribution-share
  Alike 4.0):
  [26](https://drive.google.com/open?id=1RXoXp-AHWzo6mzbd-VyRTRvmRlFtyZDq)
- pp3 ![Truck-tunnel.pp3](Truck-tunnel-1.pp3 "Truck-tunnel.pp3")

###### Image d'origine

<figure>
<img src="/images/Van-tunnel-0.jpg" title="Van-tunnel-0.jpg" width="600" />
<figcaption>Van-tunnel-0.jpg</figcaption>
</figure>

###### Image avec Source Data Adjustments - Tone Response Curve & Midtones

- Scope = 60;
- Remarquez que les réglages sont simplifiés et intuitifs:
  - Gamma = 2.90 : éclaircit les lumières;
  - Slope = 80 : éclaircit les ombres.

<figure>
<img src="/images/Van-tunnel.jpg" title="Van-tunnel.jpg" width="600" />
<figcaption>Van-tunnel.jpg</figcaption>
</figure>

###### Image avec Scene Conditions - Surround

Ici, c'est encore plus simple.

- Scope = 60;

Scene conditions:

- Surround = Dark.

Source Data Adjustments:

- Smooth Highlights = enabled

Cam16 Image Adjustments:

- Contrast J = 24.

<figure>
<img src="/images/Van-tunnel-surround.jpg" title="Van-tunnel-surround.jpg"
width="600" />
<figcaption>Van-tunnel-surround.jpg</figcaption>
</figure>

##### Comparaison entre les 2 TRC modules « Abstract Profiles  - AP» et « Source Data Adjustments - SDA » - incidences de Ciecam

Il existe deux outils TRC dans RawTherapee, l'un dans le module
"Abstract Profile" dans la gestion des couleurs et l'autre dans le
module Ajustements des données sources (SDA) de l'outil Ajustements
locaux, apparence des couleurs.

Les modules Profil abstrait et Ajustements des données sources sont
presque identiques à l'exception d'une fonction supplémentaire Log
encoding, intégrée dans ce dernier, cet outil doit être réservé aux cas
extrêmes qui ne peuvent être résolus autrement. En effet, la manière
dont ils sont rendus peut être imprévisible et perturbe souvent
l'équilibre de la lumière et des couleurs. En effet, ils sont basés sur
le même concept de base, l’utilisation d’un profil virtuel pour modifier
les données. Ils comprennent :

- Tone Response Curve : Gamma (lumières), Slope (ombres).
- Dans ce même intitulé sont également présents deux outils
  complémentaires :
  - Midtones qui permet d’ajuster les tons moyens,
  - Smooth highlights qui permet d’atténuer les lumières élevées,
    pratiquement celles où Ev \> 0 jusque Ev= +12.
- Primaries & Illuminant qui permet d’ajuster la colorimétrie des
  images : choix de l’illuminant, des primaires, et action sur la
  couleur dominante.

###### Situation dans le processus (pipe-line)

AP et à la fin du processus, juste avant Color Appearance &Lighting. SDA
(intégré à Local Adjustments – Cam16) est situé juste après la balance
des blancs, vers le début du processus. Cette différence de situation va
amener une différence de comportement vis à vis des ombres et lumières :

- SDA est situé avant Exposure, avant Auto-matched Tone Curve, avant
  tous les curseurs et courbes de « Exposure »
- SDA utilise pour les calculs internes, ceux de Scene conditions, les
  données RGB après demoisaicing.
- AP utilise les données RGB, avec les valeurs calculées à son niveau du
  processus (en fin).

Il semble évident, selon les réglages ci-dessus réalisés par
l’utilisateur et l’action de « Auto-matched Tone curve » dépendante de
chaque image et de chaque boîtier, que la répartition des ombres et
lumières seront très probablement différentes.

Gamma (lumières) et Slope (ombres) auront un comportement différent : il
faudra généralement des réglages plus faibles dans SDA que AP. Primaries
& illuminants, auront une sensibilité différente, notamment la couleur
dominante.

###### Influence de Ciecam

AP est indépendant du module Ciecam situé derrière lui (Color Appearance
& Lighting). Si vous rendez actif « Ciecam » les paramètres du module
« AP » seront pris en compte. SDA est intégré au module Ciecam de Local
Adjustments. Les réglages de SDA sont obligatoirement pris en compte par
le modèle d’apparence coloré (CAM).

###### Que fait Ciecam ?

Nous n’allons pas ici (re)décrire le tutoriel sur Ciecam, mais de
manière simplifiée Ciecam, que ce soit dans « Color Apperance &
Lighting » ou dans « Local adjustments – Color Appearance Cam16 » :
“Trying to take into account by software, the physiological aspects due
to the perception of the eye and the brain”.

Vous pouvez avoir une information partielle sur les effets que prend en
compte les 2 versions de Ciecam implantées dans RT. [Historique - effets
pris en compte](CIECAM02/fr#Introduction_-_historique.md)

La prise en compte de la majorité des effets est automatiquement
réalisée par le logiciel. C’est particulièrement vrai pour SDA.

L’effet de Stevens est un cas particulier. Il est réalisé par les 2
combobox « surround », avec par exemple dans « Scene conditions » les
réglages possibles : Average, Dim, Dark, Extremely Dark.

La prise en compte de ces effets modifie en profondeur l’image pour la
rendre plus proche des conditions de prise de vue et de visionnage. Bien
sûr seul celui qui a pris le cliché peut complètement restituer le
contexte.

Quelques remarques sur l’incidence de certains effets pris en compte :

- Surround (effet de Stevens) va éclaircir les ombres. Il semble évident
  que plus Surround aura un effet élevé (exemple Dark), plus il faudra
  réduire l’action de la Tone Response Curve – notamment Slope.

<!-- -->

- Le contraste simultané, d’autant plus important que les écarts de
  luminance dans l’image seront grands, sera pris en compte
  automatiquement et va augmenter la saturation des couleurs. Ceci
  revient à dire que les images où il y a un déséquilibre entre les
  ombres et les lumières - naturel, ou artificiellement obtenu par une
  inadéquation entre gamma (lumières) et Slope (ombres) - aboutira à une
  augmentation exagérée de la saturation.

<!-- -->

- L’effet de Hunt, sera effectué (si les données Exif sont prises en
  compte) à partir des valeurs de Absolute Luminance.

Les réglages dans Cam16 Images Adjustments, prennent eux aussi en compte
ces effets. Par exemple :

- Brightness Q (et contrast Q) s’appuient sur la valeur de Absolute
  Luminance pour se différencier de Lightness (J) (et Contrast J).
- Saturation (s), va augmenter la sensation de couleur de manière
  différentiée : moins d’action dans les ombres, par rapport à Chroma
  (C).

Donc, en résumé pour SDA :

- plus vous agissez sur Surround (Scene) plus il faudra réduire les
  paramètres « Slope » et « Gamma » - par rapport à ceux de AP.
- la saturation des couleurs sera directement impactée par des choix
  exagérés. Vous pouvez l’ajuster si nécessaire avec le curseur
  Saturation (Cma16 Images Adjustments). Le système est sous votre
  contrôle, il n’y a pas de IA (Intelligence Artificielle).
- la prise en compte des « effets » a une incidence sur la répartition
  ombres lumières et sur les couleurs. Il est impossible de transposer
  les réglages de AP (au moins ceux concernant la luminance : gamma,
  slope, midtones…) vers SDA et réciproquement, sinon globalement de
  réduire leurs valeurs.

###### Synthèse

Ciecam, notamment sous sa dernière évolution Cam16 (2020, 2022) est un
outil de très grande qualité (même s’il n’est pas parfait) . Il est le
seul à ma connaissance à réunir la quasi totalité des concepts de
Modèles d’Apparence Colorés (CAM), ce qui n’est pas le cas d’autres
systèmes comme CieLab OKLab, Jzazbz , etc.:

- Séparation en 3 processus : Scene conditions, Image Adjustments,
  Viewing conditions ;
- Présence d’outils et processus pour prendre en compte les aspects
  physiologiques du couple oeil-cerveau chez l’homme : contraste
  simultané, surround, adaptation chromatique, etc. ;
- Utilisation des 6 variables nécessaires à un CAM : lightness (J),
  brightness (Q), chroma (C), saturation (s), colorfullness (M), hue
  (h).

Il présente toutefois une lacune qui peut être un handicap dans le cas
d’images difficiles (à haute dynamique par exemple), l’absence de prise
en compte d’une cartographie globale de l’image, car Cam16 travaille
pixel par pixel.

Le module SDA, permet partiellement de contourner cette lacune. Il
réalise une analyse globale des tonalités et couleurs avec des outils
associés (Log encoding, Tone Response Cuve & Midtones…). Il est associé
partiellement à Cam16. C’est à dire que les changements induits par SDA
seront pris en compte par Cam16, mais sans apporter de jugement sur leur
pertinence. Il est possible, selon les images, réglages de SDA, ou des
processus en aval (exposure, etc.) que l’image obtenue soit trop
contrastée dans certaines zones, ou trop saturées notamment dans les
ombres.

Il revient à l’utilisateur d’utiliser les outils présents notamment dans
Image Adjustments (saturation, brightness,…) soit sur la totalité de
l’image, soit avec l’aide d’un RT-spot supplémentaire sur les zones
concernées. De la même façon, le traitement important des ombres amène
souvent une montée du bruit, qu’il convient de maîtriser : l’outil
Denoise de Blur/Grain & Denoise doit permettre d’y remédier.

#### Le module Sigmoid Q & Log encoding Q (obsolète)

- ce module ressemble à celui implanté dans « JzCzHz » :
  - choix entre « Log encoding » ou « Sigmoid »
  - prise en compte ou non de « Black Ev » et « White Ev »
- mais il apporte un ajout important, celui lié à l'utilisation d'un
  vrai CAM (ce qui n'est pas le cas de JzCzHz) qui va automatiquement
  corriger la chromaticité en prenant en compte l'ensemble des
  paramètres de la « scène » et des « viewings conditions ».
- l'utilisation est similaire à celle du module JzCzHz, vous pouvez agir
  sur les paramètres qui auront une incidence évidente sur le rendu
  - Mean luminance (Yb%), Absolute luminance, HDR PQ (Peak Luminance)
  - « Black Ev » et « White Ev », si cette option est choisie
  - Si vous avez choisi « Sigmoid » : « Contrast » agit sur la forme de
    la sigmoid et en conséquence sur la force, « Threshold » (point
    gris) distribue l'action en fonction de la luminance, « Blend » agit
    sur l'aspect final de l'image contraste et luminance.

<!-- -->

- Tous les modules qui contrôlent le « Dynamic Range » : Log encoding,
  Dynamic Range & exposure, Tone mapping, Color Appearance (Cam16 &
  JzCzHz), du fait qu'ils sont situés après le processus « Highlight
  reconstruction » (Color Propagation) vont modifier les données
  « reconstruites ». Lorsque l'utilisation de « Highlight
  reconstruction » (Color Propagation) est nécessaire, ce qui n'est pas
  synonyme d'images à forte dynamique, vous devez utiliser soit des
  « Excluding Spots », soit un masque.

<figure>
<img src="/images/Cam16-sigmoid.jpg" title="Cam16-sigmoid.jpg" width="600" />
<figcaption>Cam16-sigmoid.jpg</figcaption>
</figure>

### **Tutoriel Ciecam - JzCzHz**

[Tutoriel - Ciecam -
JzCzHz](CIECAM02/fr#Tutoriel_Color_Appearance_.26_Lighting_.28CIECAM02.2F16.29_et_Color_Appearance_.28Cam16_.26_JzCzHz.29.md)

### **Le module expérimental JzCzHz**

Pour une présentation de ce module dans Ciecam, suivre ce lien:
[Jzazbz - un nouveau CAM ? (Cam16 &
JzCzHz)](CIECAM02/fr#Jzazbz_-_Un_nouveau_CAM_(Cam16_&_JzCzHz) "wikilink")

#### Comprendre les réglages CAM - SDR - HDR - Généralités

Voir à ce sujet dans Ciecam:[Comprendre les réglages CAM - SDR - HDR -
Généralités](CIECAM02/fr#Comprendre_les_réglages_CAM_-_SDR_-_HDR_-_Généralités.md)

#### Comprendre les réglages CAM - SDR - HDR - En pratique - Introduction

Voir à ce sujet dans Ciecam:[Comprendre les réglages CAM - SDR - HDR -
Introduction](CIECAM02/fr#Comprendre_les_réglages_CAM_-_SDR_-_HDR_-_Introduction.md)

##### Comprendre - En pratique avec une saisie d'écran

<img src="/images/Jzsettings.jpg" title="Jzsettings.jpg" width="600"
alt="Jzsettings.jpg" /> Vous disposez de 6 réglages qui interagissent
sur Jz:

- "Mean luminance (Yb%)" correspond à la valeur moyenne (exprimée en %
  de gris) de l'image juste après dématricage (demosaicing). Plus le
  curseur sera à droite, plus le résultat final sera sombre. Ce curseur
  agit aussi sur la valeur de référence prise en compte par "Log
  encoding Jz", cette valeur va changer le contraste apparent de l'image
  avant la conversion logarithmique.
- "Absolute luminance" - "La" (décrite plus haut), permet, en corrigeant
  si nécessaire cette valeur:
  - d'une part d'agir sur la partie commune CAM (Color Appearance
    Model), pour prendre en compte la vraie valeur utilisée par Jz et Q.
  - d'autre part (mon interprétation) de modifier l'amplitude utile des
    valeurs de Jz dans le code (qui nous l'avons vu étaient très
    faibles), par interaction non linéaire avec le curseur "PU
    adaptation" (Perceptual uniform adaptation). Des valeurs élevées de
    "La" vont accroitre en internes les valeurs de Jz, dont le rendu
    n'est pas linéaire du fait de la fonction PQ.
- "PU adaptation", permet d'agir sur les valeurs internes de Jz
  indépendamment des valeurs de "La".
- "Jz reference 100 cd/m2". Ce curseur pour lequel je recommande de ne
  pas y toucher correspond au rapport 8 bits / 10 bits des valeurs de Jz
  entre les valeurs SDR (100 cd/m2) et HDR (10000 cd/m2 choisis par
  Dolby). Néanmoins une action est autorisée qui sera (ou non) validée
  lors de l'usage réel de moniteurs HDR.
- "PQ - Peak luminance", traduit la valeur du "Peak luminance", utilisée
  en interne par la fonction PQ. Cette valeur utilisée en interne pour
  l’ensemble des calculs HDR en amont du moniteur est à différencier de
  celle qui pourra être allouée au moniteur (lorsque ces fonctionnalités
  seront disponibles...avec le moniteur assorti...). Essayez d'agir sur
  PQ, vous verrez une variation des ombres et des lumières, ainsi que de
  la saturation.
- ces 3 derniers réglages - "Jz remapping" - permettent une meilleure
  adaptation des valeurs internes de Jz. Pour que les courbes, sliders,
  outils réagissent correctement, une deuxième correction est appliquée
  uniquement au niveau de ces outils pour mettre Jz dans l'intervalle
  \[0..1\].
- "Surround" (Average, Dim, Dark), prend en compte les conditions de
  l'environnement lors de la prise de vue. Est-ce que le fond, autour de
  la scène, était normal, un peu sombre, ou très sombre. Agir sur ce
  réglage va changer l'apparence de l’image en l’éclaircissant
  progressivement.
- Essayez d'agir sur ces 6 réglages. Attention, certains ont un effet
  que si un réglage Jz est en cours (Log encoding, Sigmoid Jz, JzczHz
  adjustments)
- Vous pouvez visualiser l'incidence de ces réglages dans la console,
  par exemple;

La=250.0 PU_adap=1.6 maxi=0.018249 mini=0.000016 mean=0.002767,
avgm=0.249170 to_screen=42.941518 Max_real=0.783651 to_one=1.276078 Où :

- "to_screen" est le multiplicateur appliqué à Jz, pour le traitement à
  proprement parler,
- "to_one" est le deuxième multiplicateur permettant aux courbes,
  fonctions de travailler dans un intervalle habituel \[0..1\]

#### Un outil HDR - Sigmoid Jz (et Log encoding Jz)

La version de "Log encoding Jz" est proche dans son concept de celle du
module "Log encoding". La principale différence tient à l’évaluation de
la luminance qui dans le module "Log encoding" est calculée en mode RGB,
avec les éventuelles conséquence sur des dérives de teinte (hue) si
cette évaluation n'est pas parfaite.

Dans le cas de "Log encoding Jz" la luminance utilisée est Jz qui se
comporte comme un CAM et dans ce sens les seules variations de teintes
sont celles voulues par les chercheurs au niveau des matrices de
conversion. Les évaluations menées sur Jz amènent des résultats proches
de Cam16, c'est à dire très bons, donc sans dérive de couleurs.

D'autres différences qui résultent du choix de Jz comme guide de la
luminance (au lieu de RGB) sont au niveau de la prise en compte des
valeurs de "Mean luminance (Yb%)" et "Viewing luminance (Yb%)" qui
tiennent compte des particularités de Jz dans le calcul des 2 points
gris.

Pour "Log encoding Jz" et de "Sigmoid Jz" un calcul - à partir des
données de l’image juste après dématricage (demosaicing) - évalue les
valeurs de: a) "Black Ev" (point le plus sombre de l'image), b) White Ev
(point le plus clair de l'image), c) "Mean luminance (Yb%)".

- Ces valeurs sont utilisées en mode logarithmique, la luminance "Jz"
  devient "(log2(Jz) - black Ev)/Dynamic Range)"
- Pour "Log encoding Jz" une solution unique à l'équation
  logarithmique - afin de (re)mettre les valeurs en linéaire - est
  calculée à partir des valeurs de a), b) et "Viewing mean luminance
  (Yb%)" - la valeur de c) influant la répartition du contraste, sans
  interférer sur le calcul. Nous verrons qu'il en va différemment avec
  "Sigmoid Jz".

**Sigmoid Jz**
<img src="/images/Sigmoidjz1.jpg" title="Sigmoidjz1.jpg" width="600"
alt="Sigmoidjz1.jpg" />

- Rappel des principes de Sigmoid Jz [Sigmoid Jz -
  principes](CIECAM02#Sigmoid_Jz.md)
- Fichier raw (Rawtherapee - Creative Common Attribution-share Alike
  4.0):
  [27](https://drive.google.com/file/d/1ziux382pWgdYa4jySimwKaKnK_KdDhno/view?usp=sharing)

Comme il a été évoqué précédemment, faire rentrer une image HDR - ici
14.8 Ev et une luminance absolue de 2000 cd/m2 - dans les
caractéristiques d'un moniteur SDR (7 Ev, 120 cd/m2) relève de mission
impossible, sans compromis. Que ce soit "Log encoding Jz" ou "Sigmoid
Jz" la teinte est préservée, mais les réglages de répartition de la
luminance entre les ombres les plus profondes, les hautes lumières et
les tons moyens vont dépendre de l'utilisateur et des choix qu'il
réalise. Pour "Log encoding Jz" - "Mean luminance (Yb%)" a une très
forte incidence sur le résultat, en modifiant le contraste. "Viewing
mean luminance (Yb%)" va lui agir sur la luminance globale de l’image.
Les 2 autres réglages "Black Ev" et "White Ev" - qui dépendent d'une
échelle logarithmique vont comme "Mean luminance (Yb%)" agir sur la
répartition entre les ombres et les lumières. Il est évident que les
réponses et donc les réglages sont dépendants de l'image, du moniteur,
et des 6 réglages vus précédemment - pour ces 3 réglages il y a une
solution unique pour "rendre linéaire" la conversion logarithmique.

Pour "Sigmoid Jz":

- "Mean luminance (Yb%)" aura une incidence plus faible que pour "Log
  encoding Jz", car il n'agit pas dans les calculs de "Sigmoid"
- "Black Ev" et "White Ev" auront le même comportement de principe que
  pour "Log encoding Jz". Selon les images les ajustements de "Black Ev"
  et "White Ev" pourront être différents entre "Log encoding Jz" et
  "Sigmoid Jz". Par exemple "White Ev" pourra être augmenté afin
  d'assurer un meilleur rendu des hautes lumières, améliorer le
  contraste et la saturation.

La différence est principalement dans l'utilisation des 2 curseurs
"Contrast" et "Threshold (gray point)".

- "Contrast" agit sur la pente de la Sigmoid, plus "Contrast" est élevé
  (supérieur à 0.5) plus la fonction exponentielle sera plate, plus les
  écarts entre "ombres" et "lumières" seront faibles. Il est préférable
  d'utiliser les valeurs inférieures à 0.5 et d'ajuster ensuite
  "Threshold".
- "Threshold" va déplacer le point d'équilibre (un peu à la manière de
  "Mean luminance (Yb%) pour Log encoding Jz), en privilégiant soit les
  ombres - déplacer le curseur à gauche va éclaircir les ombres avec un
  impact faible sur les lumières et réciproquement.
- C'est la fonction exponentielle qui "résout l'équation" qui convertit
  les données logarithmiques en données linéaaires (Black Ev, White Ev,
  et Jz mis en logarithme base 2). C'est donc l'utilisateur qui "résout"
  l'équation.
- A noter de ce fait, qu'il n'y a pas "une" solution mais plusieurs.
- La fonction "blend" agit - un peu comme "Viewing mean luminance
  (Yb%)" - sur la luminance globale de l'image et n'a pas d'incidences
  sur les calculs de la Sigmoid.

Les réglages par défaut (Contrast = 0.5, Threshold = 1, Blend = 1)
doivent convenir, avec de faibles variations autour de ces valeurs,
notamment pour "Contrast", en première approche pour une majorité
d'images. Probablement les réglages satisfaisants sont un peu plus longs
à trouver avec "Sigmoid Jz" par rapport à "Log encoding Jz", mais ils
sont pluriels.

Mais (rappel) le réglage fin de l'image (répartition du contraste et de
la luminance) va dépendre (comme dans le cas de log encoding Jz) des
caractéristiques de l'image, de celle du moniteur et de celles des 6
réglages de "Scene conditions Jz".

**Ajustements des réglages "Log encoding Jz" et "Sigmoid Jz"**

- Comme évoqué précédemment les calculs automatiques de "Log encoding
  Jz" ou les réglages (plus souples) de "Sigmoid Jz" doivent être
  complétés pour arriver à un bon résultat, par les réglages disponibles
  dans "Jz Cz Hz Images adjustments":
  - action sur Brightness et Contrast pour affiner la répartition de la
    luminance, notamment le contraste.
  - saturation (ou chroma) et les courbes Cz(C), Cz(J) pour amener la
    chromaticité aux valeurs souhaitées (celles ci auront généralement
    été réduites du fait des changements importants de luminance).

### **Generalized Hyperbolic Stretch**

## Principes généraux

### L'Objet RT-spot

Comme je l'ai évoqué, le système utilisé est proche de celui mis au
point par Nik Software, avec de grandes différences:

- chaque RT-spot, peut être considéré comme un objet qui comporte
  plusieurs champs : Il y a environ 640 "events" gérés, dont environ 160
  seulement pour le mode "basic". Ils sont constitués de curseurs,
  courbes, combobox, checkbox, expanders, mask, etc.;
- chaque champ, organisé en groupes, peut être ou non activé, et peut
  avoir des valeurs variables selon sa nature ;
- les groupes sont des ensembles cohérents pour l'utilisateur : Color &
  Light, Shadows Highlight & Tone equalizer, Vibrance & Warm/Cool, Log
  Encoding, Color appearance (Cam16 & JzCzHz), Dynamic Range & Exposure,
  Common Color Mask, Soft Light & Original Retinex, Blur/Grain &
  Denoise, Tone Mapping, Dehaze & Retinex, Sharpening, Local Contrast &
  Wavelets, Contrast by Detail Levels; Voir tutoriel Ciecam pour le
  module Color apperance (Cam16 & JzCzHz) [Tutoriel Color Appearance &
  Lighting (CIECAM02/16) et Color Appearance (Cam16 &
  JzCzHz)](CIECAM02/fr#Tutoriel_Color_Appearance_.26_Lighting_.28CIECAM02.2F16.29_et_Color_Appearance_.28Cam16_.26_JzCzHz.29.md)

<!-- -->

- chaque RT-spot, crée une "couche" supplémentaire qui peut être
  assimilée à un calque. Chaque Rt-spot ajouté travaille par
  transparence et laisse voir les modifications précédentes - "Excluding
  Spot" permet d'accéder à l'image originale (zone à exclure, ou simuler
  un mode inverse).
- l'ensemble des RT-spots fonctionne en mode L\*a\*b\* - contrairement
  au mode pleine image qui est soit en mode "RGB" avant demosaicing,
  soit en mode "rgb", soit en mode L\*a\*b\*
  - évidemment vous allez me dire "mais le mode L\*a\*b\* pose de
    nombreux problèmes, il est limité à 7Ev" (c'est vrai pour les
    profils ICC de sortie vers le moniteur codés en 8 bits), "il ne
    respecte pas les couleurs" (c'est vrai, si il n'y a pas de
    corrections - dérive dans les bleus-pourpres, et les
    rouges-orangés), etc.
  - dans une majorité de cas, lorsqu'on utilise L\*a\*b\* avec des réels
    (32 bits) et la correction Munsell de Rawtherapee (qui corrige les
    dérives de couleurs), seule la partie très hautes lumières (en HDR)
    va poser problème. L\*a\*b\* passe largement plus de 15Ev (mes
    essais, sur des images à forte dynamique...). Mais qui possède un
    équipement HDR ? Le module JzCzHz est une première approche HDR.
  - pour plus d'informations allez dans "Succession des outils dans le
    pipeline - Colorimétrie" [Succession des outils dans le pipeline -
    Colorimétrie générale](Toolchain_Pipeline/fr.md)
- les "RT-spots objets" sont gérés - création, modification, suivi -
  dans une boucle "for";
- il n'y a pas de duplication de code. Par exemple le module "Denoise"
  de "Blur/Grain & Denoise", utilise les fonctions du module "main",
  qu'il a bien sûr fallu adapter pour élever le niveaux de décomposition
  en ondelettes. Il en est de même de "Retinex", etc. Par contre
  certains modules ont un code différents de "main" par exemple "Color &
  Light", etc.
- Beaucoup d'outils de "Local adjustments" sont semblables à ceux de
  "main", mais il y a des fonctions supplémentaires, comme par exemple :
  "Tone Equalizer" ou "Tone Response Curve (TRC)" (avec
  Shadows/Highlights) qui permet un ajustement fin et différencié de
  l'exposition, "Original Retinex" qui permet un "dodge and burn", "Log
  encoding" qui est une sorte de "Tone mapping" utilisant un codage
  logarithmique simple, "Warm/cool" (Vibrance & Warm/Cool) qui permet
  une simulation de changement de température, comme dans "White
  Balance", "Blur/grain" (Blur/Grain & Denoise) permet des flous locaux
  ou des ajouts de simulation de grain ou de bruit, JzCzHz et CAM16 avec
  Sigmoid et autres avancées (Color Appearance(Cam16 & JzCzHz)) qui
  autorisent une ouverture vers des fonctions HDR, Wavelets avec de
  nombreux nouveaux outils (tone mapping ou décompression, clarity,
  etc.).

### La délimitation des zones - l’aperçu de la zone RT-spot

Lorsque l’utilisateur sélectionne un RT-spot (spot de contrôle),l’image
à l’écran montre:

- un centre "C", constitué d'un cercle dont on peut faire varier : a) le
  diamètre, b) la position avec la souris ou les curseurs;
- quatre "points délimiteurs" horizontaux ou verticaux ("T" top, "B"
  bottom, "L" left, "R" right) dont on peut faire varier les positions
  avec la souris ou les curseurs.

On aboutit à :

- une zone globale (ellipse, rectangle) délimitée par les 4 "points
  délimiteurs" ("T", "B", "L", "R"): cette zone est celle où sont opérés
  les calculs des différents algorithmes (Color & Light, Dynamic Range &
  Exposure, Retinex, Shadow/Highlight & Tone Equalizer, etc.). C'est à
  l'intérieur de celle-ci (sauf bien sûr en mode inverse) que sont
  calculés et appliqués les algorithmes de détection de couleur et de
  structure.
- 4 zones (à l'intérieur de la zone globale - les 4 parties de l'ellipse
  ou du rectangle), dont on ne peut pas faire varier l'orientation; ces
  4 zones ont chacun de leurs sommets reliés par une ellipse imaginaire
  ou un rectangle (settings).

Il est possible de pointer les limites des zones en dehors de la zone
"preview". Ce qui est toujours le cas en mode "full image".

A noter que l'utilisation de un ou plusieurs masques (avec 1 ou 2
Spots), peut suppléer à certaines fonctionnalités manquantes ou être un
"plus" dans le traitement (surtout selon les habitudes de chacun).

De même vous ne pouvez pas faire pivoter le Rt-spot, car cela pose 2
problèmes : le premier de GUI qui ne semble pas insurmontable (si
quelqu'un de compétent souhaite le faire); le second, plus complexe est
la modification de l'algorithme de calcul...

### Les 3 types de gradient

L'objet RT-spot est conçu sur le principe de 3 gradients:

- gradient du à la dissymétrie possible. En plaçant le centre du spot
  dans un angle du Spot et en faisant varier hauteur et largeur on crée
  naturellement un gradient différentiel avec les 3 gradients suivants :
- gradient du à la transition - réglable - du centre vers la périphérie
  du Spot : 3 sliders permettent une variation différentielle.
  - "Transition value" : jusque la valeur choisie "x" - l'algorithme est
    appliqué à 100% du centre jusque "x%" de la zone sélectionnée, puis
    une décroissance est assurée jusque 0, pour atteindre la périphérie
    du Spot. Avec cette transition on aboutit à 3 zones (à noter que en
    mode inverse, ces 3 zones sont inversées !):
    - zone 0 : celle située à l'extérieur du rectangle/ellipse de
      sélection et donc à l'extérieur des 4 courbes aucune action.
    - zone 1 : celle située à l'intérieur des 4 courbes où est prise en
      compte l'action des curseurs "transition" : action progressive.
    - zone 2 : celle située à l'intérieur des 4 courbes, proche du
      centre "C", où n'est pas prise en compte l'action des curseurs
      "transition" : action complète.
  - "Transition decay (linear - log)" : fait varier l'intensité
    géographique de la transition décroissante: 1 loi linéaire - à
    partir de 2 loi parabolique - à partir de 3 jusque 10, loi cubique
    transition à très forte décroissance (jusque puissance 25).
  - "Transition differentiation XY" : Si le slider est différent de
    zéro, crée un gradient différentiel entre l'abscisse et l'ordonnée.
    Les valeurs négatives réduisent la zone de transition en ordonnée,
    et l'inverse pour les valeurs positives.
  - "Feather gradient (Grad. Filters) : utilisé uniquement par les
    "Graduated filters, lorsqu'ils sont présents dans certains outils.
    Agit par pourcentage de la diagonale du RT-spot
- gradient de couleur (en fait de deltaE) grâce à la fonction "Scope"
  (étendue) - cette fonction prend en compte le deltaE. Plus les valeurs
  sont faibles, moins les écarts de couleur (L, C, H) sont pris en
  compte, à partir de Scope=80, l'étendue augmente pour à 100 atteindre
  une action égale quelque soient les couleurs. 3 sliders permettent de
  faire varier le gradient.
  - "deltaE decay" : intensité de l'action en fonction du deltaE - 1
    linéaire - jusque 10 à très forte décroissance (puissance 10). Les
    hautes valeurs sont plutôt réservées aux images à très large gamut.
  - "DeltaE-scope threshold" : interagit sur les valeurs de deltaE
    prises en compte et "scope" - réduit ou accroît la sensibilité - à
    utiliser selon l'image. Les images à fort gamut (fleurs, couleurs
    artificielles..) supportent des valeurs élevées de ce slider.
  - "ab-L balance deltaE" : Pour une valeur de 1, le calcul du deltaE
    prend en compte de manière égale les 3 composantes L\* , a\* , b\*.
    Les valeurs supérieures vont accroître l'action de L\* et
    réciproquement
  - "C-H balance deltaE": pour une valeur de 1, le calcul du deltaE
    prend compte à part égales, la chromaticité et la teinte, les
    valeurs supérieures vont accroître l'action de H (hue) et
    réciproquement.
  - "DeltaE preview color - intensity": par défaut la couleur est verte.
    Si vous utilisez des valeurs négatives, la couleur sera bleue. Plus
    la valeur sera élevée plus la couleur aura une forte intensité

Ainsi, tous les modules (y compris Contrast By Detail Levels, Retinex,
Tone Mapping, etc.), ainsi que les modules agissant principalement sur
la luminance (Color & Light, Dynamic Range & Exposure, Shadows Highlight
& Tone Equalizer, ...) réalisent de fait des gradients, croissants ou
décroissants. Le centre du Spot étant toujours le point de référence.

### Les 3 types de RT-spot

Trois types de RT-spot sont proposés:

- Normal spot: chaque nouveau spot prend en compte les réglages des
  précédents - si bien sûr ils sont dans la zone d'action commune - on
  peut parler d'action récursive (d'une certaine manière cela
  s'apparente un peu à des calques superposés).
- Excluding spot: chaque nouveau spot réinitialise, l'image à partir des
  données originales, mais garde pour les calculs, les références de
  l'image modifiée par les autres RT-spots. Il permet d'annuler dans la
  zone sélectionné par Excluding Spot, l'action du Normal Spot. Peut
  également servir à réaliser le mode "inverse" de certains outils.
- Full image :
  - vous permet de travailler sur l'image entière, de la même manière
    que les outils de "main", mais en prenant en compte le deltaE. Ce
    qui est un net avantage (si vous ne souhaitez pas en bénéficier
    régler le Scope des outils à 100...
  - Les délimiteurs du RT-spot (rectangle) sont placés nettement au delà
    des limites de l'image, vous pouvez les changer, si vous le
    souhaitez par exemple si vous changez la transition par défaut (100)
    pour obtenir l'effet souhaité.
  - La transition est réglée sur 100. Vous pouvez la changer, notamment
    pour créer des gradients.
  - Du fait de l'utilisation du deltaE, le rendu de l'image dépendra de
    la position du centre du Rt-spot (comme les 2 autres types). C'est
    la position du centre du Rt-spot, et sa taille qui détermine les
    paramètres de base de calcul du deltaE.
  - Attention avec certains modules, par exemple dans "denoise"
    (Blur/Grain & Denoise", "wavelet" (Local contrast & Wavelets ou
    "Retinex" (Dehaze & Retinex), la quantité de mémoire requise peut
    être nettement supérieure à 8M°, voire 16M°, selon la taille des
    images. De plus FFTW (lorsqu'on l'utilise) risque d'accroître les
    temps de traitement..

Dans les trois cas, vous avez accès à la quasi totalité des réglages
pour tous les outils.

#### Commentaires sur le "Excluding spot":

- il est dans le principe assez similaire au "Contre point" de Capture
  NX2(c) et permet de défaire des actions trop invasives par exemple une
  "bavure" non désirée, ou d'empêcher l'action sur une partie
  déterminée, par exemple si l'utilisateur souhaite accroître la
  saturation d'un portrait et qu'il veut exclure l’œil ou une partie
  avec une exposition différente.
- l'algorithme que j'ai utilisé est très proche de ceux présents
  jusqu'ici dans "local adjustements", il est fondé sur les différences
  de deltaE et aussi sur la structure de l'image (via une transformée de
  Sobel Canny). Il n'est pas "parfait" mais devrait satisfaire 70% des
  cas.
- il permet de simuler un module "inverse", pour cela: créez un Rt-spot
  qui dépasse les limites de l'image, appliquez le, à l'outil souhaité
  en mode "Normal spot" ou "Full image" , puis positionnez un second
  Rt-psot où vous souhaitez revenir sans modifications, choisissez
  "Excluding Spot", agissez sur Scope si nécessaire. Bien sûr vous
  pouvez avec ce RT-spot "excluding" apporter les modifications à tous
  les outils (Color & Light, etc.).

#### Comment se servir de "Excluding spot"

1.  il suffit de placer le nouveau spot sur la zone à exclure.
2.  choisir dans le menu "Settings", Spot method = "Excluding spot".
3.  Puis régler "Scope", "Transition", "Spot size" ainsi bien sûr que 4
    limiteurs de zone, pour obtenir les effets désirés. Vous pouvez
    utiliser si nécessaire, des réglages complémentaires (comme pour le
    spot normal) par exemple "Color & Light", etc.)
4.  dans certains cas (faible différence de deltaE...) il peut être
    nécessaire d'ajuster le curseur "Threshold deltaE-scope" - notamment
    en réduisant la valeur par défaut.
5.  dans le cas de zones avec aplat, vous pouvez utiliser "Spot
    structure" (lorsque ce slider est présent dans un outil) qui pourra
    aider dans certains cas à une meilleure délimitation de l'action.

### Les trois niveaux de complexité

Chaque outils (Color & Light, Tone mapping, etc.), est doté d'un
sélecteur de niveau de complexité avec 3 cas possibles : Basic,
Standard, Advanced

- "Basic" est le mode par défaut, il permet dans une majorité de cas les
  problèmes courants, il n'est pas doté de masques et rarement de
  courbes.
- "Standard", est enrichi de fonctions supplémentaires quelques réglages
  complémentaires, par exemple des "Graduated filters", ou des courbes,
  ainsi que de masques simplifiés.
- "Advanced" est le mode le plus complet, il comprend des fonctions
  avancées nécessitant des utilisateurs expérimentés, par exemple:
  - Color & Light, dispose d'un module "Merge file" qui permet comme
    Photoshop des mélanges de "calques" (en fait ce sont des Rt-spots)
    comme les modes : Difference, Multiply, Soft Light, Overlay, etc.
  - Masques : des fonctions complètes plus avancées, comme "Structure
    Mask", "Blur Mask", etc.

Une exception toutefois : Dehaze & Retinex - les options disponibles en
"Basic" et "Standard" sont identiques, il faudrait réduire le choix à
"Basic" et "Advanced", mais la modification du GUI semble très
complexe...

### Les références teinte, chroma, luminance et le principe de l'algorithme

Afin de mettre en œuvre un algorithme performant de détection de forme :

- la zone du cercle central, sert de référence. En fonction du diamètre
  choisi par l'utilisateur, le système calcule, la moyenne de la teinte
  (hue), de la chroma, et de la luminance (lors de l'utilisation de
  Denoise, ces différentes valeurs sont calculées après un léger flou
  pour réduire l'impact du bruit);
- le choix du diamètre de la zone centrale dépend de l'usage. Par
  exemple pour un feuillage, l'utilisateur aura intérêt à choisir une
  valeur faible afin de ne sélectionner que le vert du feuillage; à
  l'inverse pour la peau l'utilisateur aura intérêt à accroître le
  diamètre afin d'éviter les prises en compte de données parasites
  (bruit, cils, etc.);
- pour chaque quart (de l'ellipse ou du rectangle), et en fonction du
  curseur "scope", le système prend en compte :

1.  en premier lieu de l'écart de deltaE (différence perçue entre 2
    couleurs prenant en compte, la teinte, la chroma et la luminance)
    entre la zone centrale et le pixel courant;
2.  puis, un algorithme s'appuyant sur ce deltaE , atténue l'action en
    fonction de l'écart de deltaE entre la zone centrale et le pixel
    courant;
3.  la modification d'action utilise soit une loi linéaire, soit une loi
    de type puissance (parabolique, cubique,....) en fonction du réglage
    de "DeltaE decay" dans Settings (1 conduit à une loi linéaire, 2
    parabolique, etc.).

Ceci va permettre de différencier l'action selon les critères énoncés
ci-dessus, comme par exemple, si le cercle central se trouve dans un
feuillage, de limiter l'action à l'ensemble du feuillage sans toucher à
l'arrière plan, par exemple le ciel (ce qui est impossible avec un
lasso). De plus si un autre feuillage se situe dans la zone couverte,
celui-ci sera également concernés par la modification.

- l'action sur le curseur transition va permettre de faire varier
  l'action : si le curseur est réglé sur 50, la moitié (linéaire) de la
  zone concernée verra une application à 100% de l'effet, puis une
  transition agira régressivement jusqu'aux limites de la zone. Cette
  régression est par défaut "linéaire"; vous pouvez changer pour une
  régression parabolique ou une autre puissance, en agissant sur
  "transition decay";
- si on accroît la valeur de "scope", progressivement l’ensemble de la
  zone sélectionnée est prise en compte quelque soit la couleur, la
  chroma et la luminance;
- si on réduit la valeur de "scope", l'action se limitera aux pixels
  très proches (en termes de deltaE) de la zone de référence;
- si scope est supérieur à 80, progressivement l'ensemble de la zone est
  concernée de manière identique (pas du tout de prise en compte du
  deltaE). Ce mode de travail doit rester exceptionnel et n'est en
  général pas recommandé sauf par exemple pour créer des gradients de
  luminance.

L'algorithme de détection de forme est opérationnel en mode "normal" -
son implantation en mode inverse s'accompagne de restrictions.

Au dessus de la valeur de "scope" choisie, l'algorithme "deltaE" n'est
pas pris en compte (voir ci-après).

#### Mise à jour récursive des références

Si vous activez la case à cocher "Recursives references"

- les références hue (teinte) chroma, luma (luminance) et Sobel seront
  dynamiquement mises à jour, d'une part entre chaque module utilisé
  pour un même RT-spot, et d'autre part pour chaque RT-spot;
- les références qui apparaissent dans les masques C(C), L(L) et LC(H)
  et h(H) seront elles aussi mise à jour.

#### Prévisualisation des zones sélectionnées Preview ΔE (deltaE)

Dans "Settings", si vous sélectionnez le bouton "Preview ΔE", vous aurez
un aperçu des zones de l'image affectée par la sélection - les
transitions ne sont pas prises en compte.

Egalement dans "settings" "Color preview ΔE and intensity" permet:

- la sélection de la couleur de prévisualisation - bleu ou vert - et son
  intensité

Les curseurs et courbes agissant sur la couleur sont sans effet avec
cette sélection. Les curseurs et courbes agissant sur la luminance ont
un effet avec cette sélection.

"Scope" est le réglage le plus sensible puisque il agit directement sur
le deltaE. Attention, le réglage de Scope situé dans "Settings" n'est
actif que sur sur les outils "Color & Light", "Shadows/Highlights & Tone
Equalizer", "Vibrance & Warm/Cool". Tous les autres outils ont un
réglage Scope spécifique.

Les 4 curseurs situés en "Settings": a) Threshold ΔE-scope, b) ΔE decay,
c) Balance ΔE ab-L, d) Balance ΔE C-H, ont également un effet avec cette
sélection.

### Algorithme complémentaire - détection de structure

L'algorithme de Sobel-Canny permet en association avec le filtre "Guide
Filter" qui lisse les irrégularités, d'utiliser la différence entre la
référence (cercle central) et la valeur de la structure en chaque point
de l'image.

Cet "écart" est ajouté au calcul de deltaE pour mieux déterminer les
contours et les zones à réduire l'effet. Ce système est efficace, si:

- la référence est dans une zone avec une assez importante structure
- la zone à affaiblir est un aplat ou avec une structure faible.

Structure est implanté dans "Color & Light" et "Dynamic Range &
Exposure" ainsi que dans "Excluding spot". Dans le sens Aplats vers
structure vous pouvez agir si nécessaire, sur "Threshold structure"
(Settings), la valeur est fonction du niveau de bruit.

Il est possible d'utiliser "structure" lorsque :

1.  les différences de deltaE sont très faibles et qu'on souhaite une
    différenciation
2.  et lorsque que se trouve accolée une zone avec structure et une
    autre avec aplats

### Synthèse des différentes options de settings

Settings reprend tout ce qui est commun à la gestion des RT-spot, par
exemple :

- les transitions seront identiques quelque soit l'outil choisi (Color
  and Light, Dynamic Range & Exposure, Bur/Grain & Denoise...)
- mais ce qui n'est pas commun sera traité spécifiquement dans chaque
  outil, comme par exemple la gestion du deltaE (Scope) pour les outils
  autres que "Color & Light","Shadows Highlight & Tone Equalizer",
  "Vibrance & Warm/cool".
- remarque : des outils comme:
  - le choix de travailler avec la souris ou avec des sliders (présents
    dans les versions de développement) a été caché pour simplifier
    l'interface (il est facile de le réactiver si nécessaire)

#### Gestion des RT-spots

Les premières lignes de l'interface permettent la gestion des RT-spot

- création (add)
- Suppression (delete)
- Duplicate - créer un nouveau spot avec les caractéristiques de
  l'ancien en termes de forme
- Rename (renomme le nom du Spot pour personnaliser le suivi)
- Show - Hide : permet de cacher le Rt-spot pour assurer une meilleure
  lisibilité.

#### Forme du RT-spot

Permet de choisir entre ellipse et rectangle comme forme du Rt-spot. A
noter que dans une majorité de cas, ce choix est avec très peu
d'incidences sur les résultats. Peut être, dans les semaines à venir y
aura-t-il d'autres mode (courbes de Beziers, polygone...) avec toutes
les difficultés évoquées précédemment (GUI, modification de
l'algorithme)

- Ellipse est le mode par défaut
- Rectangle peut également servir à travailler en mode pleine image
  (Full image)

#### Spot méthode

Par défaut en mode "normal spot". Chaque RT-spot peut contenir tout ou
partie des outils disponibles. L'action est récursive

En mode "excluding spot" Chaque Rt-spot peut contenir tout ou partie des
outils disponibles. Excluding réinitialise les données d'origine.
Excluding va par exemple permettre de supprimer des actions trop
invasives ou de créer un mode inverse

En mode "full image", l'image entière est utilisée, par défaut seul le
deltaE (position et taille du centre du Rt-spot) a une incidence. vous
pouvez jouer sur les limites (situées au delà de l'image) et sur les
transition pour ajouter des effets possibles (gradients, etc.)

#### Taille du Spot - Spot size

La taille par défaut doit convenir dans une majorité de cas. De petites
valeurs, permettent de ne traiter par exemple que les feuilles d'un
arbre (bien sûr en association avec Scope deltaE) Des valeurs plus
importantes vont permettre de gommer les petits écarts dans le calcul
des références (hue, chroma, luma). Ceci peut être utile pour traiter la
peau.

#### Transition Gradient

- Transition value : permet de choisir l'incidence du réglage de tous
  les RT-spot. Géographiquement selon le réglage de Transition "X",
  en-dessous de cette valeur 100% des réglages sont appliqués, au dessus
  il y a décroissance progressive (sauf si vous choisissez 100%)
  - de très faibles valeurs permettent par exemple la réduction des
    défauts

<!-- -->

- Transition decay : traduit la vitesse d'affaiblissement au del de "X%"
  ci-dessus. Avec 1 la décroissance est linéaire,...avec 25 une loi
  exponentielle réduit considérablement l'incidence de l'action, la
  rendant quasiment nulle. Ceci permet de choisir des Rt-spot
  relativement importants pour traiter certaines actions (défauts,...)
  sans incidences (ou presque au delà de %)

<!-- -->

- Transition differentiation XY: permet de différentier l'action selon
  l'abscisse ou l'ordonnée créant de fait une variation du gradient

<!-- -->

- Feather gradient : n'a aucune action si un des "Graduated filter"
  utilisable dans de nombreux outils n'est pas activé. Agit en
  pourcentage de la taille de diagonal du Rt-spot, lorsque un ou
  plusieurs des "Graduated filter" (luminance, chrominance, hue, local
  contrast) est utilisé.

#### Détection de forme

- DeltaE -scope threshold: permet d'adapter les réglages par défaut du
  deltaE au type d'image. Si l'image est avec un fort gamut (fleurs,
  couleurs artificielles,...) il peut être nécessaire d'accroître les
  valeurs.

<!-- -->

- DeltaE decay : accroît (ou réduit) l'efficacité du deltaE, de fortes
  valeurs vont rendre la sélection plus pertinente pour les images à
  fort gamut. L'intensité de l'action est ajustée en fonction du deltaE
  et de DeltaE decay - 1 linéaire - jusque 10 à très forte décroissance
  (puissance 10), en dessous de 1 il y a réduction..(par défaut 2).

<!-- -->

- ab-L balance (deltaE) : équilibre l'action de deltaE par rapport aux
  lois habituelles, plus axées vers la luminance, ou vers la couleur.

<!-- -->

- C-H balance deltaE : équilibre l'action de deltaE par rapport aux lois
  habituelles, plus axées vers le teinte, ou vers la chromaticité.

<!-- -->

- deltaE preview color - intensity et bouton associé "Peview DeltaE": le
  slider permet de choisir la couleur visible "bleue" ou "verte" ainsi
  que son intensité. Le choix "vert" permet aussi de visualiser en
  couleur dans "mask and modifications" - show modifications with or
  whithout mask. Presser le bouton donne un aperçu de ce qui est
  concerné par le deltaE (sans tenir compte pleinement ni des
  modifications, ni des transitions), mais cette possibilité est limitée
  à un outil actif (alternative : Mask and modifications : Preview
  deltaE)

#### Evite les dérives de couleur - Avoid Color shift

Tente de remettre les couleurs dans le gamut du working profile, une
correction Munsell est ensuite appliquée. Je recommande dans une
majorité de cas, de cocher "avoid color shift", associé à "Munsell
correction only". Ce choix permet une neutralité de L\*a\*b\* en termes
de teinte (hue), lorsqu'on change la saturation, et évite le contrôle de
gamut qui peut amener des artefact dans les images surexposées.

#### Tous les changements forcés en noir et blanc

Lorsque l'utilisateur a utilisé en amont de "Local adjustments" un
module noir et blanc ou une simulation de films noir et blanc, cette
case à cocher permet d'éviter l’apparition de couleurs dues aux réglages
de "Local adjustments"

#### Références récursives

Force l'algorithme à recalculer les références après chaque outil.

#### Forme Méthode

Vous pouvez choisir plusieurs mode (désactivé par défaut):

- Indépendant (souris) - réglage par défaut
- Symétrique (souris)
- Indépendant (souris + curseurs)
- Symétrique (souris + curseurs)

#### Wavelet Edge performance

Une image qui a été décomposée en ses composantes par la méthode de
Daubechies peut avoir jusqu'à 10 échelles de coefficients allant de D2
(qui correspond à la décomposition de Haar) à D20. Dans RawTherapee les
coefficients *D2 (faible), D4 (standard), D6 (standard plus), D10
(moyen)* et *D14 (élevé)* sont utilisés. Plus il y a de coefficients,
plus l'ondelette distinguera de détails, mais avec une légère
augmentation du temps de traitement (souvent négligeable).

Bien qu'il n'y ait pas de relation directe entre la qualité résultante
et le nombre de coefficients (selon l'image d'origine), choisir le bon
nombre de coefficients permettra d'affiner la qualité des niveaux
inférieurs, ou celle de l'image résiduelle :

- dans certains cas, les meilleurs résultats pour la détection des
  contours sont obtenus avec D2
- dans les autres cas avec D6 ou D14

#### Masque et Fusion

Uniquement utilisé par les masques (lorsqu'ils sont activés : courbes
LCH, etc.)

- case à cocher DeltaE image mask : Pour tous les masques :
  - prend en compte le deltaE de l'image, pour éviter de modifier la
    zone de sélection lorsque les outils de masque suivants sont
    utilisés: Gamma, Pente, Chroma, Courbe de contraste, Contraste local
    (par niveau d'ondelette), Masque de flou et Masque de structure (si
    activé).
  - désactivé lorsque le mode Inverse est utilisé.
- Scope (deltaE image mask) : permet de prendre en compte le deltaE pour
  l’élaboration des masques - ce réglage est sans action sur les
  différents "Scope" présent dans chaque outils - il permet une
  meilleure sélection du masque - suppose que un des outils masque est
  activé (chroma mask, contrast cuve mask, gamma mask, slope mask....)
- Denoise chroma mask : permet le contrôle du bruit chromatique du
  masque. utile pour un meilleur contrôle du bruit de chrominance et
  éviter les artefacts, notamment lorsque on utilise la courbe LC(h)
- Background color/luma mask : ajuste le niveau de gris ou de couleur de
  l'arrière plan des masques (Show mask and modifications).

### Algorithme complémentaire - Soft process (Soft radius)

Certains algorithmes peuvent être agressifs et sont dotés de cette
fonction (sauf en mode Basic):

- Color & light
- Dynamic Range & Exposure
- Contrast By Detail Level

L'utilisation de "GuideFilter" sur la variation de luminance entre
l'image originale et l'image modifiée, va permettre d'adoucir le
résultat.

Nota : "Shadows/Highlight & Tone Equalizer" possède par conception cet
algorithme.

Actuellement seule la luminance est traitée... rien ne s'oppose à
traiter la dimension "couleur" soit sous la forme de "Chroma" (C\*) soit
sous la forme des 2 composantes a\* et b\*

### Algorithme complémentaire : Graduated Filter - GF

En m'inspirant du "Graduated Filter" (gradient de luminance) présent
dans le menu principal, j'ai élaboré 2 autres gradients:

- chrominance : il est ainsi possible de faire varier la chrominance et
  réaliser des dégradés de chroma (ciel, portrait)
- hue : il est possible de faire varier la teinte et réaliser des
  dégradés de teinte (paysages, réglages fins, effets spéciaux..)

Exemple d'utilisation d'un Graduated Filter avec Luminance Chrominance
et Teinte : [Exemple dans Premiers pas d'un Graduated Filter avec
Luminance Chrominance et
Teinte](Local_Lab_controls/fr#Réaliser_un_"Graduated_Filter"_Luminance_-_Chrominance_et_Teinte_(filtre_dégradé) "wikilink")

Les modules suivants sont dotés d'un module "Graduated Filter"

- Color & Light : luminance, chrominance, hue (teinte).
- Dynamic Range & Exposure : luminance
- Shadows/Highlight & Tone Equalizer: luminance
- Vibrance & Warm/Cool: luminance, chrominance, teinte
- Local contrast & Wavelet: uniquement Wavelet local contrast (au sens
  Wavelet)

Le réglage de "feather" - répartition sur le RT-Spot du gradient - se
trouve dans Settings

Il n'y a pas "d'aide" avec la souris pour accompagner la rotation du
gradient, c'est un curseur (-180 +180) qui permet cette fonctionnalité.

Bien sûr les fonctions de "transition" et de "scope" sont conservées.

### Algorithme complémentaire : fusion d'images

Exemple d'utilisation de fusion d'images (Color & Light) :[Exemple dans
Premiers pas de fusion
d'images](Local_Lab_controls/fr#Fusion_d'images_-_modes_de_fusion_(merge_file) "wikilink")

Dans "Color & light" vous pouvez choisir dans : "Merge image and Mask",
5 possibilités:

- "None" : Rawtherapee utilise toutes ses fonctions habituelles y
  compris les masques
- "Original image" : permet la fusion de l'image courante avec
  l'originale sans aucune modification
- "Previous Spot" : permet la fusion de l'image courante avec l'image du
  spot précédent
- "Background" : permet de choisir un fond avec choix de couleur (hue,
  chroma) et luminance.

#### Background permet de simuler une brosse (brush)

`En association avec: `

- une faible taille du Rt-spot,
- une valeur très faible de transition,
- une valeur élevée de transition decay
- dupliquer le spot

#### Plusieurs types de fusion sont possibles avec ou sans utilisation du mask

Bien sûr les fonctions de Scope et Transition sont conservées.

Modes de fusion - similaires à ceux de Photoshop (c):

- normal, substract, difference, multiply, addition, divide, soft Light
  (legacy), SoftLight Illusion, Soft Light W3C, hard light, overlay,
  screen, darken only, lighten only, exclusion, Hue, stauration, Color,
  Luminosity
- vous pouvez régler le "mélange" à l'aide du curseur "Opacity"
- Merge background (deltaE): prend en compte le deltaE lors de la fusion
  (un peu comme un équivalent de "Scope")

#### Exemple d'effet spécial obtenu avec "merge file"

Bien sûr cet exemple n'est pas exhaustif, mais uniquement démonstratif.
L'exemple va permettre de créer un double dégradé sur fond flou.

- créer un premier RT-spot, "Normal spot", "Elipse"
  - Inverse
  - sélectionner avec les 4 délimiteurs, la zone à conserver exempte de
    flou gaussien
  - Blur/grain & Denoise" / "Blur & Noise" / "Gaussian Blur - Noise
    Grain" :
  - "Radius" 1000 à 10000 (utilise une transformé de Fourier FFTW)
  - "Noise" : éventuellement si vous souhaitez ajouter du bruit de
    luminance

<!-- -->

- créer un deuxième RT-spot, "Normal spot", "Elipse", "Transition" 60,
  mais vous pourrez changer ensuite selon souhaits:
  - mettre le centre de ce RT-spot à l'intérieur de l'aire du premier
    (zone exempte de flou)
  - sélectionner avec les 4 délimiteurs, la zone qui sera avec un flou
    variable, évidemment au delà de la première. Si vous sélectionnez au
    delà de l'image, il n'y aura qu'une simple dégradé de flou.
  - activer "Color & Light"
  - "Scope" élévé proche de 100 ou 100
  - "Merge File" : "Original Image"
  - "Merge with Original or Previous or Background" : "Normal" ou autre
    par exemple "Soft Light Photoshop" - selon souhaits
    - Merge Background (deltaE) : 50 plus ou moins selon souhaits
    - Opacity : 50 plus ou moins selon souhaits
    - Contrast Threshold : selon souhaits

<figure>
<img src="/images/doubleblur.jpg" title="doubleblur.jpg" width="300" />
<figcaption>doubleblur.jpg</figcaption>
</figure>

### RT-spot et calques

Lorsque vous créez un nouveau Spot, un "calque" est créé, c'est en
réalité une copie de l'image précédente entière, même si le Spot est
petit.

Imaginons que l'utilisateur à créé 2 spots, on aboutit à :

- calque N°1 : image originale non modifiée (celle qui est en "réserve")
  et qui peut servir pour "excluding spot"
- calque N°2 : image copie de N°1 avec le Spot créé, par exemple la
  retouche d'une fleur à gauche de l'image
- calque N°3 : image copie de n°2 avec un deuxième Spot créé, par
  exemple un portrait à droite de l'image

1.  Lorsqu'on fusionne N°2 et N°1 (Fusion du premier Spot avec
    "Original"), les modes de fusion répondent comme on s'y attend, par
    exemple si on active "mode difference", l'image dans la zone
    concernée de la fleur sera noire (si Scope est à 100)
2.  Si on fusionne N°3 et N°1 (Fusion du 2ème Spot avec "Original"), les
    modes de fusion laisseront apparaître l'image entière créée à
    l'occasion de la création du Spot N°1, donc le mode de fusion
    "difference" ne fera pas apparaître une image noire.
3.  Si on fusionne N°3 et N°2 (Fusion du 2ème Spot avec "Previous"),les
    modes de fusion laisseront apparaître l'image entière "originale",
    donc le mode de fusion "difference" ne fera pas apparaître une image
    noire.

Les mode de fusion sont sensibles aux paramètres de chaque RT-Spot, par
exemple dans le cas de l'exemple N°1 ci-dessus, l'image noire ne sera
possible que si Scope = 100

### Algorithme complémentaire - Recovery based on luminance mask

Est utile pour moduler les effets d'un outil (lorsque il est doté de
cette fonction). Le système est fondé sur les informations de luminance,
lorsqu'on utilise les courbes L(L) ou LC(H) dans "Mask and
modifications"

Il est évident que le masque doit être activé, ainsi que au moins une
des courbes ci-dessus.

Les zones "Dark" et "Light" situées en dessous du seuil "dark" et
au-dessus du seuil "Light" seront progressivement restaurées à leurs
valeurs d'origine avant d'être modifiées par les paramètres de l'outil
en cours (Color & Light, Shadows/Highlight & Tone Equalizer, etc.)

Entre ces deux zones, la valeur des paramètres de l'outil en cours sera
appliquée.

### Algorithme complémentaire - Mask and Modifications

Exemple d'utilisation d'un masque: [Exemple dans Premiers pas pour
accroître la sélection de
couleurs](Local_Lab_controls/fr#Utilisation_d'un_masque_simple_pour_accroître_la_sélection_de_couleur.md)

#### Préambule

Les masques dans "Local adjustments" sont d'une conception personnelle.
Le point de départ qui m'a inspiré est situé dans "Color Toning",
"Mask", est l'utilisation de 3 courbes H, C, L. Le reste a des
particularités spécifiques:

- qui peuvent surprendre l'utilisateur habitués aux masques des autres
  logiciels en service;
- possède des limitations, souvent les mêmes que celles liées de manière
  générale dans "Local adjustments", pas de possibilités de basculer le
  masque, ni de faire des courbes de Bezier ou des polygones;
- par contre il est doté de possibilités que je pense rares comme par
  exemple (en mode avancé) et pour certains outils:
  - "Structure mask", la structure de l'image sera utilisée seule, ou en
    combinaison avec les autres outils du masque, pour renforcer la
    différentiation des zones claires et sombres.
  - "Blur Mask" qui va faire varier le contraste du masque, là encore
    pour renforcer la différentiation des zones claires et sombres.
  - "Wavelet selection" qui selon les niveaux minima et maxima de
    décomposition en ondelettes va modifier le masque.

Certains diront, il manque ceci, il manque cela,.. c'est sûr. Tout
développeur qui souhaite modifier le code pour atteindre d'autres
objectifs est libre de le faire.

Les masques ne sont accessible que si le sélecteur de complexité est sur
"Standard", ou "Advanced".

#### Introduction

Les 11 modules "Color & Light" , "Dynamic Range & Exposure",
"Shadows/Highlight & Tone Equalizer","Vibrance & Warm/cool", "Log
encoding", "Color appearance(Cam16 & JzCzHz)", "Contrast by details
levels","Local contrast & Wavelets", "Tone mapping", "Retinex" ,
"Blur/grain & Denoise" (ces 2 deux modules ont un masque commun) - ont
la possibilité d'utiliser un masque:

- Pour 3 modules : "Color & light", "Dynamic Range & Exposure",
  "Shadows/highlight & Tone Equalizer", ces masques peuvent être
  utilisés en mode inverse (avec des limitations)
- Pour 2 modules : "Blur/Grain" et "Denoise", le masque est commun
- Pour 2 modules : "Tone mapping" et "Retinex", le masque peut être
  utilisé "avant" le traitement ou "après le traitement"

Vous pouvez agir sur la luminance de l'arrière plan des masques (menu
settings), par défaut il est réglé à 10. A zéro, le masque traduit les
réelles modifications, mais on peut moins percevoir les détails de
structure.

#### Mask and modifications

Ce menu déroulant dispose de plusieurs choix, variables selon les outils

- Show modified image : montre les modifications de l'image en prenant
  en compte les effets de l'outil et du masque.
- Show modifed areas without mask : montre l'aperçu des modifications -
  prend en compte les transitions – avant toute action sur les masques
- Show modified areas with mask : montre l'aperçu des modifications si
  le masque est activé - prend en compte les transitions
- Show mask : permet de visualiser l'aspect du masque avec l'action sur
  les courbes, filtres divers - ne prend pas en compte les transition et
  le deltaE principal, prend en compte le "Mask deltaE image" (Scope
  Mask deltaE image)
- Show Spot structure (Advanced) : permet de visualiser l'effet sur la
  structure du curseur "Structure Spot" lorsqu'il est implanté
- Preview DeltaE : permet visualiser l'image avec le deltaE quelque soit
  l'outil

#### Ces masques visent 2 objectifs principaux:

1.  augmenter la sensibilité de détection et donc permettre une
    meilleure sélection des objets (objectif principal), sans modifier
    l'image, lorsque l'algorithme deltaE n'est pas suffisamment
    pertinent (rare).
2.  aboutir à des effets spéciaux en combinant l'image du masque et
    celle originale.

#### Fonctionnalités

##### Courbes LCH

L'image est modifiée avant le traitement (exception pour "Tone mapping"
et "Retinex" où l'image servant au masque peut tenir compte du
traitement) par les algorithmes de "Color & Light", "Dynamic Range &
Exposure", "Shadows Highlight & Tone Equalizer", "Vibrance & Warm/Cool",
"Log Encoding", "Color Appearance" "Contrast by details levels",
"Blur/Grain & Denoise", "Local contrast & Wavelets" mais ces
modifications sont prises en compte par les algorithmes de "Local
adjustments" que ce soit la détection de forme, les transitions, ...
L'utilisateur dispose de 3 courbes qui sont au démarrage toutes
positionnées à 1 (maximum) :

- C=f(C) la chrominance varie en fonction de la chrominance,
  l'utilisateur peut ainsi diminuer la chroma pour améliorer la
  sélection.
- L=f(L) la luminance varie en fonction de la luminance, l'utilisateur
  peut ainsi diminuer la luminosité pour améliorer la sélection
- L et C = f(H) la luminance et la chrominance varient en fonction de la
  teinte, l'utilisateur peut ainsi diminuer la luminosité et la chroma
  pour améliorer la sélection.

Si l'utilisateur positionne les courbes près de l'ordonnée zéro, l'effet
des masques sera inversé.

##### Structure Mask

Un masque utilisant la structure de l'image (différenciation des zones
sans contraste - ciels, aplats.. - et des zones avec contraste
"habitations", "reliefs", ... -) peut être utilisé de 2 façons:

- "Structure mask" (slider Threshold) avec la case à cocher "Structure
  mask as tool" non cochée : Dans ce cas, un masque faisant apparaître
  la structure sera généré même si aucune des 3 courbes n'est activée.
  Une action modérée sur le slider est recommandée !
- "Structure mask" (slider Threshold) avec la case à cocher "Structure
  mask as tool" cochée : Dans ce cas, un masque faisant apparaître la
  structure sera généré après la mise en œuvre des courbes "Mask Curves
  : L(L) ou LC(H). Ici, "Structure mask" se comporte comme les autres
  outils : gamma, slope, etc. Il permet de différencier l'action sur le
  masque selon la structure de l'image.
- "Structure mask" est disponible pour les masques "Blur/Grain &
  denoise" et "Color & Light"

##### Blur Mask

Un maque utilisant la création d'un flou à grand rayon (Mask Blur),
permet de faire varier le contraste de l'image et/ou assombrir /
éclaircir des parties d'images (Color & Light)

- Contrast threshold: permet de déterminer en fonction de la texture de
  l'image, les zones impactées ou non
- Radius: permet de faire varier le "rayon" du flou gaussien (0 à 500)
- case à cocher FFTW : utilise la transformée de Fourier pour une
  meilleure qualité (augmentation du temps de traitement et des besoins
  en mémoire)

A noter que selon le "mode" (advanced, standard, basic), cette fonction
est ou non présente. De plus en mode "absence de FFTW" le rayon limité à
100.

##### Radius et Laplacian Theshold

L'utilisation simultanée des 2 filtres est peu conseillée (cas sans
résolution de l'équation PDE)

###### Radius

Un curseur "radius" - utilisant "GuideFilter" permet de diminuer les
artefacts et adoucir les transitions.

###### Laplacian Threshold

Permet une modification de la luminance du masque en accroissant la
luminance des zones claires.

##### Gamma, Slope, Chroma, Blend

Vous pouvez modifier le masque - avec bien sûr l'incidence inverse sur
l'image - à l'aide de 3 curseurs qui jouent:

- sur la chroma en adaptant sa force à la valeur réelle rencontrée qui
  dépend de plusieurs facteurs dont la grandeur de l'espace de travail
  (sRGB, Prophoto, ...).
- sur le gamma et la pente "Slope" (même principe par exemple que le
  gamma sRGB). La fonction agit sur le canal Luminance L\*. Cette
  fonction, sans discontinuité, associe une partie linéaire pour les
  basses lumières et une courbe parabolique au delà.

##### Blend

- Blend permet de mélanger en plus ou en moins le masque avec l'image en
  cours

##### Contrast curve, Wavelet local contrast, Hue curve

- tous les masques sont dotés de la fonction "contrast curve"
- 2 masques "Blur/Grain & Denoise" et "Color & Light" sont dotés d'un
  contraste local fondé sur les "wavelets" avec choix du niveau
- "Color and Light" est doté de la fonction H=f(H) qui permet des
  retouches fine de la teinte, par exemple pour la peau

##### Quel usage, quelle action, sur la luminance des masques et la couleur

- Gamma et Slope : permet une transformation douce et sans artefacts du
  masque avec une action sur "L" très progressive sans aucune
  discontinuité
- Contrast curve : peut être utilisée comme "Gamma et slope", mais son
  usage est une action ciblée sur certaines parties (en général les plus
  claires du masque) en utilisant une courbe excluant les parties
  sombres
- Wavelet local contrast : permet de diminuer ou accroître l'action sur
  le niveau de détail souhaité du masque, en privilégiant l'action sur
  certaines zones de luminance (en général les plus claires)
- Hue curve : permet la retouche fine de la couleur du masque,
  évidemment les seules couleurs qui peuvent être impactées sont celles
  qui apparaissent dans le masque

##### Case à cocher "Mask deltaE Image" et curseur "Scope Mask DeltaE image (menu Settings)

Ces 2 fonctionnalités permettent

- pour chaque masque.
- pour les curseurs et courbes qui modifient l'action sur les masques
  après leur élaboration :
  - curseurs :"gamma" "Chroma" "slope"
  - courbes : "contrast curve" , "Levels contrast" (lorsque cette courbe
    est présente), "Hue curve" (lorsqu'elle est présente)
- d'éviter une action sur la zone de sélection - celle où est présente
  le RT- spot
- le plus "Scope" sera faible, plus l'action sera différenciée
- cette fonctionnalité est désactivée en mode "Inverse"

#### Utilisation

Comment procéder, pour l'essentiel pour l'objectif n°1 ?

- pour satisfaire l'objectif n°1 il est impératif de ne pas (ou peu)
  modifier la zone où se trouve le "spot". Le GUI permet de visualiser
  sur la courbe elle même la valeur de L, C ou H à éviter de modifier,
  c'est à l'utilisateur de positionner correctement le point des courbes
  qui ne sera pas modifié. Il suffit de positionner le sommet de la
  courbe à chacun de ces points (limite de la transition gris foncé,
  gris clair) selon le cas.
- attention, la case à cocher "Recursive reference" peut interagir sur
  cette limite (gris foncé, gris clair) : si le masque concerne le
  module sur lequel on souhaite agir (par exemple "Exposure
  compensation" pour le module "Dynamic Range & Exposure"),il est
  souhaitable, pour trouver la bonne valeur pour le masque de désactiver
  l'expander.

<!-- -->

- ensuite en examinant le masque, vous pouvez réduire très
  raisonnablement les valeurs de chroma, ou luma, selon le cas. Des
  réductions de 10 à 20% sur l'échelle des ordonnées doivent être
  suffisante dans la majorité des cas, comme dans l'exemple ci-dessous.

<figure>
<img src="/images/mask_sensi_obj1.jpg" title="mask_sensi_obj1.jpg"
width="600" />
<figcaption>mask_sensi_obj1.jpg</figcaption>
</figure>

- pour satisfaire l'objectif n°1, il est souhaitable que le curseur
  "blend" soit à zéro.

Pour l'objectif n°2, tout est fonction de ce que l'on veut faire, mais
je recommande quand même d'appliquer le même processus que ci-dessus,
sinon que les valeurs d'affaiblissement peuvent être plus importantes
que 10 à 20% et atteindre si nécessaire 100%. A noter que le masque
utilisé dans le cas de l'objectif n°2, sera aussi utilisé pour accroître
la sélection comme dans l'objectif n°1, mais les effets seront
augmentés.

- pour satisfaire l'objectif n°2, il est souhaitable que les curseur
  "blend" ne soient pas à zéro: si vous réglez blend:
  - avec des valeurs négatives, l'image complémentaire au masque sera
    soustraite de l'image originale, dans le cas d'un masque L, l'image
    résultante va s'assombrir,
  - avec des valeurs positives et ajoutée l'image complémentaire au
    masque sera ajoutée à l'image originale, dans le cas d'un masque L,
    l'image résultante va s'éclaircir.

Plusieurs assistances sont proposées pour aider aux processus :

- a\) visualisation du masque dans tous les cas
- b\) visualisation des modifications sans le masque (pas en inverse)
- c\) visualisation des modifications avec le masque (pas en inverse)

et également pour l'action sur la structure, l’aperçu d'un masque de
structure (pas en inverse). Il n'est - ceci peut paraître évident - pas
possible d'utiliser plusieurs masques en même temps...mais une fois
généré ils peuvent être utilisés ensemble

Vous pouvez changer l'aspect de la visualisation des modifications avec
et sans le masque dans "Settings"

- "DeltaE preview clor - intensity"
  - les valeurs positives du curseur ne modifient l’apparence des
    couleurs
  - les valeurs négatives du curseur ajoutent la composante "b" (de L\*
    a\* b\*) et ainsi permettent une meilleure visualisation des
    changements de luminance.

A noter la consommation importante de mémoire liée à ces masques lors de
la sélection de zones étendues. A noter également le côté peu intuitif
des masques, les actions sur les masques se traduiront par un effet
inversé sur l'image.

#### Utilisation isolée des masques

Chaque module équipé de "mask" peut être utilisé sans activer les
commandes internes à chaque module. Par exemple:

- "Log encoding" qui est le premier outil situé avant "Denoise" dans
  "Succession des outils dans le pipeline;
- tout module situé en amont du module courant (par exemple utiliser le
  masque de "Contrast by detail levels", si le module courant est "Color
  & Light")
- cette utilisation des masques, sans utiliser les sliders, courbes, des
  outils, va permettre de modifier l'image au début du process; par
  exemple modifier le gamma de l'image!
- "Color Appearance(Cam16 & JzCzHz)" est le dernier module dans
  "Succession des outils dans le pipeline". Il peut être utilisé
  uniquement pour les masques, sans utiliser les sliders ou les courbes
  de l'outil. Ceci va permettre de modifier l'image à la fin du process.

Bien sûr, autres modules avec "mask" peuvent aussi être utilisés seuls,
à l'exception de Retinex.

#### Utilisation de plusieurs masques

Pour chaque RT-spot et chaque outil (Tone mapping, Dynamic Range &
Exposure, etc.) vous ne pouvez utiliser qu'un seul masque associé à cet
outil, mais il est très facile d'en utiliser plusieurs.

Le masque suivant prendra en compte les résultats du précédent.

##### Comment utiliser plusieurs masques pour un même outil ?

C'est très simple, il suffit d'activer (expander) un autre outil équipé
d'un masque, et de mettre en œuvre le masque. Vous n'êtes pas obligé de
mettre en œuvre l'outil, par exemple vous pouvez vous servir du masque
de Contrast by detail levels, sans aucune action Contrast by detail
levels (tous les curseurs à 1) Les masques agissent dans l'ordre de
celui de la Succession des outils dans la pipeline.

- Les masques suivants : Color & light, Blur/grain & Denoise, permettent
  l'utilisation d'un "contraste local" fondé sur le niveau de wavelet,
  ainsi qu'un ajustement sur des ombres et des tons moyens  : curseur
  Shadows (Color & Light, Blur/gain & Denoise) et les tons clairs
  curseur Highlights (Blur/grain & Denoise).
- Le masque Color & Light permet l'utilisation d'une courbe hue =
  f(hue).
- le masque Vibrance & Warm/Cool est un peu particulier, car il n'y a
  pas d'action sur la luminance dans Vibrance (sinon pour le contrôle du
  gamut), les réponses en luminance seront donc très faibles.

Bien sûr on peut combiner cela avec les actions Merge file et DeltaE
Image mask (Settings).

##### Comment utiliser plusieurs masques pour un même outil en dupliquant le RT-spot ?

Il suffit de dupliquer le RT-spot et d'ajuster sa position et ses
dimensions. Cette action permet:

- de prendre en compte les nouvelles valeurs des valeurs de référence
  (hue, chroma, luminance)
- de changer la zone d'action
- de changer l'ordre des masques.

#### Cas spécifique de Retinex

Le module masque de Retinex ressemble aux autres mais:

- il ne permet l'accès à l'objectif 1) "accroître les capacités de
  sélection" que en mode "normal" (pas d'utilisation de transmission
  map)
- lorsque l'option "Use transmission map" est choisie, le comportement
  n'est plus "traditionnel":
  - mais va permettre une exploitation de "Retinex" exploitant au
    maximum les effets de contraste local. A noter que le système se
    comporte de la même manière pour les valeurs positives ou négatives
    de "blend"
  - avec "Use transmission map" la fonction d'aide indiquant
    graphiquement les valeurs "référence" 'hue", "Luma", "Chroma" sont
    totalement erronées...

### Masque commun couleur

Exemple d'utilisation d'un Masque commun couleur:[Exemple dans Premiers
pas Masque commun
couleur](Local_Lab_controls/fr#Comment_se_servir_de_Common_Color_Mask_-_puis_Exemple_de_combinaison_avec_une_fusion_de_2_RT-Spot.md)

Ce masque a, en termes d'outils, les mêmes spécifications que les autres
masques cités plus haut. Par contre son fonctionnement et son principe
est différent:

- les masques précédents viennent en complément d'un outil, ils
  améliorent la sélection, ou changent l'image après modifications par
  un outil (Color & Light, Vibrance & Warm/Cool, etc.)

Dans le cas présent, le masque se comporte comme un outil:

- ce sont soit les 3 courbes C(C), L(L), LC(H), soit en mode "advanced",
  "Mask structure" ou "Mask blur" qui vont générer des différences de
  couleurs ou de structure de l'image par rapport à l'image originale
- cette "différence" est de même type que celle par exemple générée par
  "Lightness", ou "chrominance" dans "Color & Light"

Pour utiliser cette particularité, "Masque commun" est doté de 3
curseurs supplémentaires:

- "scope" : permet de gérer en fonction de la position du RT-spot et des
  réglages de "Settings", le deltaE (les autres curseurs Scope sont
  totalement inactifs)
- Add / substract mask luminance : permet d'ajouter ou retrancher le
  masque "Luminance" de l'image originale
- Add / substract mask Chrominance : permet d'ajouter ou retrancher le
  masque "Chrominance" de l'image originale
- ces 2 curseurs réglés à zéro, amènent aucune action
- "Scope" agit sur l'écart généré par les 2 curseurs "add / substract"

### Le fonctionnement en mode inverse

Lorsqu'il est proposé, le fonctionnement en mode inverse est simplifié,
certaines fonctions ne sont pas implémentées (mask partiel, certaines
courbes,...).

### Avoid color shift

Situé dans "Settings"

Deux objectifs sont visés:

- mettre les couleurs dans le gamut de l'espace de travail courant
  (working profile) en utilisant une colorimétrie relative ;
- ajuster les couleurs à l'aide d'une correction "Munsell" - notamment
  les rouges-orangés et les bleus-pourpres, lorsque la saturation dans
  le domaine L\*a\*b\* a évolué notablement.

Difficultés :

- le mode L\*a\*b\* a certes des avantages, mais il n'a pas de limites.
  C'est à dire que si une couleur est presque hors gamut en RGB, une
  fois convertie en L\*a\*b\* rien ne s'oppose si l'utilisateur change
  la saturation d'aller vers des couleurs imaginaires (il faut y
  vraiment changer considérablement les valeurs L\* ou a\* ou b\*). Ce
  pourquoi, il est (parfois) bon, de contrôler le gamut;
- mais, l'algorithme utilisé sait très mal gérer les hautes lumières
  brulées. Par exemple là où un traitement a été fait avec "highlight
  reconstruction", il va détruire ce travail.

En conséquence, pour des images où on est proche du gamut (fleurs,
couleurs artificielles,..), et qu'un traitement accroît la saturation,
et lorsqu'il y a une zone avec des très hautes lumières brulées

- soit on n'applique pas "avoid color shift", mais les couleurs
  L\*a\*b\* dans les bleus-pourpres ou les rouges-orangés vont dériver.
- soit on applique "avoid color shift", mais en cochant la case "Munsell
  corrrection only". On risque d'avoir des couleurs imaginaires..c'est à
  dire hors du champ visuel humain (est-ce grave ?)
- soit on applique "avoid color shift", qui par défaut contrôle le
  gamut, et applique la correction Munsell. Et on utilise un "excluding
  spot" pour les zones des hautes lumières à préserver.

### Fast Fourier Transform

La transformé de Fourier - Fast Fourier Transform - sous sa forme "FFTW
real DCT" est utilisée dans Rawtherapee et notamment dans "Local
adjustements" sous 3 formes:

- Créer un flou Gaussien "Blur"
- Résoudre l'équation de Poisson PDE - suite à un Laplacien
- Réduire le bruit

Elle peut se traduire (images de taille importante - Full image) par des
temps de traitement plus importants.

#### Flou Gaussien

Dans 2 modules de "Local Adjustements", une case à cocher "Use Fast
Fourier" (FFT) a été ajoutée, elle permet d'utiliser la transformée
rapide de Fourier, pour générer le flou (blur) nécessaire à Multi Scale
Retinex (pas installé dans Retinex "pleine image") ou "Local contrast
unsharp",

- La formule utilisée pour le flou est la formule de Gauss qui
  s'applique après la transformée et avant la transformée inverse.
- formule de Gauss G(x,y) = (1/2\*PI\*sigma) \* exp(-(x^2 + y^2) / 2\*
  sigma^2).
- celle appliquée est sa version "Fourier" G(x,y) = exp((-sigma^2)\*(PI
  \* x^2 + PI \* y^2))

Cette formule par définition est exacte quelque soit le rayon sigma.

A noter pour le flou, la différence de rendu avec la fonction utilisée
dans Rawtherapee qui utilise une série de formules approximatives, FFT
est quasiment exacte, donc de meilleure qualité. Pour Retinex MultiScale
il est possible (pas recommandé) d'utiliser la variable Fftwsigma=true
dans "options". Si vous basculez sur "false", l'algorithme FFT sera
modifié pour essayer de s'approcher de la formule "ancienne".

#### Résoudre l'équation de Poisson PDE

Sont concernés par cette utilisation :

- Original Retinex pour atténuer les différences de luminance notamment
  sur les portraits
- Exposure avec 2 modules : a) PDE Ipol Contrast atenuator; b) PDE
  Fatal - Dynamic Range Compression (similaire à Dynamic Range
  Compression "pleine Image")

#### Réduire le bruit

Dans "Local Adjustements" la FFT vient en complément des ondelettes pour
réduire le bruit de Luminance et de chrominance. (non installé pour
Chrominance dans Denoise "main")

#### Optimisation FFT

La FFT (Fast Fourier Transform) a un temps de traitement qui ne dépend
que la surface a traiter et bien sûr du nombre d'appels (exemple scale
Retinex), l'application de la fonction de Gauss, est quasi instantanée
et indépendante du rayon. A noter l'optimisation de la FFT lorsque les
dimensions (H, W) de la zone correspondent à la décomposition en
facteurs premiers et uniquement ceux-ci. 2^n, 3^p, 5^q, 7^r, 11^a, 13^b
(avec a + b = 0 ou 1)

- une table utilisée par le code permet de sélectionner les dimensions
  appropriées : elle est actuellement utilisable jusqu'à une dimension
  (L ou H) de 18144 pixels
- Cette optimisation n'est pas effective dans le Preview.
- Le gain de temps peut varier d'un facteur 2 à 10: 10 si les dimensions
  du RT-spot sont de type 2^n, 2 si on a la combinaison maximale des
  facteurs premiers. De ce fait FFTW peut passer plus de temps pour un
  "petit" spot que pour un "grand"
- A noter que si vous souhaitez sélectionner toute l'image (full image),
  la dimension de la zone traitée avec FFTW sera un peu plus grande que
  la taille de l'image (quelques pixels) afin de permettre que toute
  l'image soit traitée.

#### Précision des calculs

La version FFTW est "float", après plusieurs essais cette précision
semble suffisante, les erreurs après une transformée suivie d'une
transformée inverse, concernent sur une image entière quelques pixels
isolés avec des différences inférieures à 1/1000ème, sur la globalité de
l'image pas de différences mesurables.

Il doit être possible - si la nécessité s'impose - d'installer dans
GitHub - la version "double" de FFTW

## Quelques particularités du mode local (par rapport à Lab adjustements)

Voici quelques informations qui peuvent intéresser l'utilisateur. Ces
informations sont souvent des particularités du mode local

### Color & Light

- Les algorithmes utilisés pour la luminance et le contraste sont
  différents de ceux utilisés par Lab adjustements (main), ce qui peut
  amener quelques différences de rendu.

Un exemple avec Color & light:[Exemple dans Premiers pas avec Color &
Light](Local_Lab_controls/fr#Ajouter_l'outil_Color_&_Light.md)

<img src="/images/Colorspace_flowers.jpg" title="Colorspace_flowers.jpg"
width="300" alt="Colorspace_flowers.jpg" />
<img src="/images/Colorspace_flowers-grid2.jpg"
title="Colorspace_flowers-grid2.jpg" width="300"
alt="Colorspace_flowers-grid2.jpg" />

- Vous disposez d'une fonction "Color correction grid" qui peut être
  selon le cas :

Deux méthodes sont possibles: Color Toning et Direct

- Color Toning

1.  Dans ce cas, la luminance est prise en compte dans la variation de
    la chroma
2.  l'équivalent d'une fonction H=f(H) si le "point blanc" de grid reste
    à zéro et si vous ne faites varier que le point noir.
3.  l’équivalent d'un Color toning si vous faites varier les 2 points.

- Direct

1.  Dans ce cas, il y a action directe sur la chroma

Vous pouvez agir sur l'effet souhaité avec Strength, mais aussi avec les
autres fonctions notamment scope qui permet de délimiter l'action, par
exemple en isolant une couleur parmi d'autres.

- Le mode inverse, est maintenant doté de la fonction scope, il peut
  servir pour l'essentiel, à réaliser des dégradés (gradient),
  simulation de vignettage, ou de cadres dégradés, ou générer des effets
  spéciaux. Dans le cas de cadres dégradés, si vous sélectionnez -100
  pour "lightness", et réduisez la chrominance, et sélectionnez une
  valeur de "scope" supérieure à 75, la "bordure" sera noire.

Il dispose de réglages spécifiques:

- Gamma (advanced): Modifie le gamma de Lab qui par défaut est à 3, pour
  le mettre linéaire si on souhaite travailler en mode HDR. Bien sûr un
  gamma inverse est appliqué en fin de ce processus;
- Spot structure : utilise l'algorithme de Sobel-Canny pour améliorer le
  delatE en prenant en compte les différences de structure;
- Blur shape detection : floute légèrement les résultats du delatE pour
  atténuer les éventuels artefacts.

#### Courbes

- Une courbe L=f(L) et une C=f(C) permet de moduler la luminance ou la
  chrominance pour chaque RT-spot (spot de contrôle) en fonction de la
  luminance ou de la chrominance (mode Standard).
- Une courbe L=f(H) (mode Advanced) permet de moduler la luminance pour
  chaque RT-spot en fonction de la teinte.
- Une courbe C=f(H) (mode Advanced) permet de moduler chrominance pour
  chaque RT-spot en fonction de la teinte.
- Une courbe H=f(H) (mode Advanced) permet de moduler la teinte pour
  chaque RT-spot en fonction de la teinte.
- Une courbe L=f(C) (mode Advanced) permet de moduler la luminance pour
  chaque RT-spot en fonction de la chrominance.
- Une courbe C=f(L) (mode Advanced) permet de moduler la chrominance
  pour chaque RT-spot en fonction de la luminance.

Pour les rendre actives, il est nécessaire d'activer la combobox Curves
type.

Color & Light dispose entre autres de plusieurs améliorations (selon le
niveau de complexité), par exemple: mask et structure.

En mode "inverse" les courbes L=f(H) et H=f(H), L=f(C), C=f(L) ne sont
pas implémentées ainsi que l’aperçu des modifications.

- RGB Tone curves (mode Advanced)
  - En mode RGB vous disposez de 4 choix : Standard, Weighted standard,
    Luminance, Film Like
  - vous disposez d'une case à cocher "Special use of RGB curves" : de
    part la conception de "Local adjustements", l'algorithme va comparer
    le résultat de RGB Tone curves avec l'original, ce qui dans certains
    cas peut fausser les attentes de l'utilisateur, notamment si on
    inverse la courbe par exemple pour créer un effet négatif. La case à
    cocher permet d'isoler le travail RGB Tone curves, supprimant toutes
    les autres actions: "Scope", masques, curseurs...à l'exception des
    transitions. Si vous souhaitez utiliser cette image en la
    travaillant il suffit de créer un nouveau RT-spot au même endroit.

#### Fusion d'images (Merge Files)

De manière assez similaire à Photoshop, vous pouvez fusionner 2 Rt-Spots
ou 1 RT-spot avec un background.

- Avec 21 modes : Normal, Substract, Addition, Multiply, etc.
- Et 3 curseurs pour contrôler l'action: Merge background (deltaE),
  Opacity, Contrast threshold.

### Dynamic Range & Exposure

Légèrement différent de celui du menu principal avec 3 curseurs
identiques: Amount, Detail, Anchor, mais un mode d'action légèrement
différent. Il dispose en plus:

- Gamma : Modifie le gamma de Lab qui par défaut est à 3, pour le passer
  en mode linéaire si on souhaite travailler en mode HDR. Bien sûr un
  gamma inverse est appliqué en fin de ce processus;
- Spot structure : utilise l'algorithme de Sobel-Canny pour améliorer le
  delatE en prenant en compte les différences de structure;
- Blur shape detection : floute légèrement les résultats du delatE pour
  atténuer les éventuels artefacts.

Dynamic Range & Exposure: dispose de l'amélioration "mask" (partiel en
inverse)

#### Algorithmes PDE

##### Contrast attenuator (Ipol - modifié par jacques)

- Cet algorithme qui est un Atténuateur de contraste (ce n'est pas un
  Dynamic Range Compression) PDE possède 4 curseurs :
  - Laplacian threshold qui réalise une convolution ignorant les valeurs
    inférieures au seuil
  - Linearity qui permet d’accroître la luminance pour les valeurs
    inférieures à la moyenne
  - Laplacian Balance qui équilibre le résultat en mélangeant le
    résultat PDE (Partial Differential Equation) à standard (1 = 100%
    PDE)
  - Gamma qui modifie la répartition de la Luminance avant et après le
    Laplacien. .
  - le menu permet de choisir de débruiter ou non avant le Laplacien :
    la méthode utilisée (median) est assez destructrice, il est
    préférable d'utiliser le module Denoise (Blur/Gian & Denoise), soit
    Denoise agit avant (par défaut), soit après si on crée un RT-spot
    supplémentaire.

PDE résout l'équation de Poisson (Laplacien + Fourier) après une
transformée de Fourier.

#### Exposure (partie de Dynamic Range & Exposure)

Ce module "ressemble" à celui en mode global RGB, mais :

- il fonctionne entièrement en mode L\*a\*b\*, d'où des différences de
  rendu;
- il n'a pas les curseurs "lightness, chroma et contraste" dont les
  fonctions sont déjà présentes dans "Color & Light";
- un curseur Chroma compensation est une particularité du mode L\*a\*b\*
  : il permet d'éviter une variation de saturation apparente - le
  réglage par défaut devrait convenir dans une majorité de cas.
- un curseur supplémentaire "shadow" (Exposure Tools) qui utilise le
  même algorithme que "Shadows/Highlight & Equalizer", mais limité à
  shadows et avec les paramètres par défaut : il utilise pour pondérer
  l'action en fonction de la luminance, le même curseur que celui des
  "shadows compression" , en effet soit ils sont exclusifs (black ou
  shadows), soit ils vont dans le même sens. Ce curseur supplémentaire
  "simplifie" l’usage pour l'utilisateur!
- il y a une seule courbe Contraste, similaire à celle de L=F(L)
  présente dans Color & Light. Il est évident que le rendu de cette
  courbe est différent de Tonecurve qui agit en mode RGB. Vous pouvez si
  vous le souhaitez activer les 2 courbes L=f(L) dans Color & Light et
  Exposure.
- ne pas hésiter à utiliser modérément "highlight compression" qui
  améliorera la sélection.

Shadows/Highlight & Equalizer est une alternative possible, notamment si
le RT-spot est dans une zone d'ombre importante.

- Remarque : éviter de placer le Spot dans des parties à très faible
  luminance, les résultats peuvent être inattendus

Conseils :

- **cet algorithme est peu performant**, mais les utilisateurs ont
  l'habitude de l'utiliser. j'ai été amené à mettre en place des
  palliatifs pour le rendre convenable;
- lui préférer (il y en a d'autres, voir dans Premiers pas):
  - Tone Equalizer - dans Shadows/Highlight & Tone Equalizer;
  - Tone Response Curve (TRC) - lui aussi dans dans Shadows/Highlight &
    Tone Equalizer (Equalizer en mode "Standard"). N'hésitez pas à
    accroître "Slope" pour déboucher linéairement les ombres. Vous
    pouvez agir sur le gamma pour éclaircir les zones claires.

### Shadows Highlight& Tone Equalizer

Exemple d'utilisation Shadows/Highligt - Tone Equalizer - Tone Response
Curve(TRC): [Exemple dans Premiers pas
d'utilisation](Local_Lab_controls/fr#Cinq_manières_de_changer_l'exposition_-_relever_les_ombres.md)

Pour l'ensemble du module :

- Est doté de Graduated Filter (Standard / Advanced) et de Recovery
  based on Luminance mask
- Dans les cas d'importants débouchage des ombres, l'utilisation de
  Denoise (Blur/Grain & Denoise) peut être nécessaire.

#### Shadows Highlight

- Seul le mode "L\*a\*b\*" est disponible.

#### Tone equalizer

Ce module Tone Equalizer(origine Darktable - transformé pour Rawtherapee
par Alberto Griggio) permet une retouche progressive des Tons en
fonction de l'exposition (en EV)

- 5 curseurs du plus sombre au plus clair, plus un curseur Detail
  permettent un travail fin sur la luminance, par exemple ne déboucher
  que les ombres très prononcée -16 ou -18EV

#### Tone Response Curve (TRC)

Avec ce module vous pouvez retoucher le gamma et la pente (slope) de
l'image:

- j'ai mis une TRC plutôt qu'un simple gamma / slope pour réduire les
  artefacts et avoir une meilleure restitution des couleurs
- par défaut le réglage : Gamma 2.4 et Slope 12.92 (gamma sRGB)
  correspond à celui mis en œuvre en sortie par défaut dans Rawtherapee
  (profil d'écran, ou sRGB). Rappel tout le traitement de Rawtherapee
  est réalisé avec un gamma de 1.
- Essayez d'autres réglages qui donnent un image semblable mais agissent
  différemment sur les ombres et les lumières
  - BT709 : gamma 2.22 slope 4.5
  - Lab : gamma 3.0 slope 9.02
- Ce module permet d'agir sur:
  - lumières avec Gamma: n'hésitez pas à utiliser de grandes valeurs
    pour gamma, si nécessaire
  - basses lumières avec Slope: n'hésitez pas à utiliser de grandes
    valeurs pour slope, si nécessaire

### Vibrance & Warm/cool

Pour l'ensemble:

- Possibilité de masques en mode standard et advanced.
- Graduated Filter
  - Luminance en mode Standard
  - Luminance, Chroma, Hue en mode Advanced
- Recovery based on Luminance mask

#### Vibrance

Module similaire à celui du menu principal.

#### Warm - Cool

Un curseur permet :

- de faire varier la "chaleur" de la zone sélectionnée.
- de réduire ou supprimer certains artefacts de couleurs, par exemple
  dus à de multiples illuminants,...

A noter que l'algorithme ne correspond pas à une balance des blancs -
même si cela en a l'apparence. L'algorithme utilise une partie de
CIECAM02, le processus CAT02 qui est probablement la meilleure
adaptation chromatique disponible. Par rapport à la référence D50,
lorsque vous souhaitez réchauffer l'image, le curseur va au contraire
abaisser la température des "viewings conditions", et bien sûr
l'accroître lorsque vous souhaitez "refroidir" la zone concernée. A
noter que vous pouvez obtenir un résultat similaire pour l'image entière
en utilisant le module CIECAM02, avec :

- Scene conditions : WP model ==\> free temp + green + cat02,
  temperature = 5000K, Surround = average, CAT02 adpatation = 100,
  Yb=18, Scene absolute luminance = 400
- aucun réglage dans "Image adjustements"
- Viewing conditions : CAT02 adaptation = 100, Viewing absolute
  luminance = 400, Surround = average, Yb=18, et bien sûr réglage de la
  température souhaitée.

### Local contrast & Wavelet

Vous disposez de 2 options:

- Unsharp mask : l'algorithme est similaire à celui du menu principal
- Wavelet (mode standard ou advanced) : l'algorithme est proche de celui
  du menu principal, mais sans Denoise (qui est un module séparé dans
  Local Adjustments). Les fonctions sont similaires mais plus
  performantes (notamment en mode advanced) et bénéficient du DeltaE.
  - en mode standard :l'algorithme correspond à une utilisation -
    simplifiée - du module wavelets, Local contrast & wavelets,
    combinant un algorithme proche de Final contrast local et Contraste
    pour l'image résiduelle. Il permet ainsi de réaliser une fonction
    Clarity.
  - en mode advanced: 2 expanders Wavelet pyramid 1 & 2, abritent divers
    outils, permettant:
    - contraste par niveau, Tone mapping, Directional contrast
    - Graduated Filter, Edge Sharpness, Blur

Pour les 2 modules possibilités de masques et Recovery based on
Luminance mask en modes Standard et Advanced

#### Unsharp mask

Rendu différent du fait de la position dans le processus.

Une case à cocher Use Fast Fourier a été ajoutée, elle permet d'utiliser
la transformée rapide de Fourier, pour générer le flou (blur) nécessaire
à Local contrast.

- La formule utilisée est la formule de Gauss qui s'applique après la
  transformée et avant la transformée inverse.
- formule de Gauss G(x,y) = (1/2\*PI\*sigma) \* exp(-(x2 + y2) / 2\*
  sigma2).
- version adaptée à Fourier : G(x,y) = exp((-sigma)\*(PI \* x2 + PI \*
  y2))

Cette formule par définition est exacte quelque soit le rayon sigma.

A noter la différence de rendu avec la fonction utilisée dans
Rawtherapee qui utilise une série de formules approximatives.

La FFT (Fast Fourier Transform) a un temps de traitement qui ne dépend
que la surface a traiter, l'application de la fonction de Gauss, est
quasi instantanée et indépendante du rayon. A noter l'optimisation de la
FFT lorsque les dimensions (H, W) de la zone correspondent à la
décomposition en facteurs premiers et uniquement ceux-ci. 2^n, 3^p, 5^q,
7^r, 11^a, 13^b (avec a + b = 0 ou 1), et malgré l'optimisation les
temps de traitement peuvent être importants.

#### Wavelets

Un exemple simple (pas avec Pyramid) d'utiliser Wavelets: [Exemple dans
Premiers pas d'utilisation de
Wavelet](Local_Lab_controls/fr#Un_moment_de_folie_-_utiliser_wavelet.md)

Vous disposez:

##### Sélecteur de niveaux

- un sélecteur de level (niveau) avec seuil qui permet de sélectionner
  une plage de niveaux et non un simple niveau maximum - l'algorithme
  réduit automatiquement le niveau si l'espace disponible (taille du
  spot - ou dimension du preview) est insuffisante : au niveau 9, il
  faut au minimum 1024 pixels, au niveau 8 - 512, au niveau 7 - 256, au
  niveau 6 -128, au niveau 5 - 64, au niveau 4 - 32, au niveau 3 - 16,
  au niveau 2 - 8, au niveau 1 - 4, au niveau 0 -2

##### Local contrast

- une courbe Local contrast qui agit sur le contraste (luminance),
  attention on n'agit pas directement sur la luminance mais sur les
  décompositions. Cette première courbe prend en compte la luminance de
  l'image non décomposée et les niveaux de décomposition de 0 à 9 (les
  hauts niveaux ne sont possibles que si la taille du RT-Spot le permet
  et que les dimensions du "Preview" sont suffisantes).
- cette courbe, plus le sélecteur de niveaux va permettre de modifier le
  micro-contraste en fonction de la luminance, par exemple renforcer ce
  contraste dans les moyennes lumières, abaisser le contraste dans les
  ombres. Bien sûr, si nécessaire vous pouvez ajouter un autre RT-spot
  avec d'autres réglages...

##### Image résiduelle

- un curseur qui agit sur le contraste de l'image résiduelle
- un curseur qui agit sur la saturation (chroma) de l'image résiduelle
- 4 curseurs qui permettent d'agir sur shadows/highlight de l'image
  résiduelle, avec la possibilité d'entrer des valeurs négatives.
- 2 curseurs Gamma et Slope permettent d'ajuster les ombres et lumières.

##### Clarity & Sharp Mask et Blend & Soft Images (détails)

- c'est le sélecteur de niveaux qui permet de choisir entre Clarity et
  Sharp mask, pour les valeurs inférieures ou égales à 4 Sharp Mask,
  pour 5 et au dessus Clarity
- Merge Luma permet de sélectionner l'intensité de l'effet recherché sur
  la luminance.
- Merge chroma permet de sélectionner l'intensité de l'effet recherché
  sur la chroma.
- Merge only with original image, empêche de mélanger l'ensemble des
  actions Wavelets pyramid et préserve ainsi la possibilité de Clarity
  et Sharp mask, sans interférences
- attention, Merge Luma et Merge chroma, mélangent l'ensemble du
  processus Wavelets, qui peut se limiter à Clarity (voir ci-dessus).
- Soft radius
  - un slider Soft radius (algorithme GuidedFilter) permet de réduire
    les halos et les irrégularités aussi bien pour Clarity et Sharp Mask
    que pour l'ensemble des processus de Wavelet pyramid. Pour
    désactiver, mettre à zéro

##### Gamma

Gamma : Modifie le gamma de Lab qui par défaut est à 3, pour le mettre
linéaire si on souhaite travailler en mode HDR. Bien sûr un gamma
inverse est appliqué en fin de ce processus.

##### Wavelets Pyramids - 2 expanders

###### Graduated filter & Local contrast

- permet de faire varier le contraste local en fonction d'un gradient
  souhaité et d'un angle. Ce qui est pris en compte est la variation du
  signal Luminance (et non la luminance)

###### Edge sharpness

Ce module comporte les mêmes réglages et finalités que celui du module
principal dans "main wavelets", c'est à dire qu'il est complexe! Il vise
à cibler l'action du contraste local sur les bords et utilise les mêmes
réglages

- [bords
  netteté](Wavelets/fr#Bords_Nettet.C3.A9_.28luminance.29_et_Clart.C3.A9.md)

Bien sûr il bénéficie en plus des particularités de "Local adjustements"
(scope, transition, sélections multiples,...)

###### Blur Levels

- Blur residual : permet de flouter l'image résiduelle, essayez avec des
  valeurs différentes du sélecteur de niveaux. Les valeurs
  intermédiaires du sélecteur de niveaux (Top right, Bottom right)
  peuvent amener des résultats curieux.
- Blur levels : permet de flouter n'importe quel niveau ou plage de
  niveaux. L'abscisse du graphique représente le level de la
  décomposition en ondelettes. La partie gauche correspond aux faibles
  valeurs 2, 4, 8 pixels. Le curseur supérieur permet de fixer le
  maximum de flou, quelque soit les positions du sélecteur de niveaux.
  Chroma levels agit en pourcentage en plus ou en moins de la luminance.

###### Contrast by levels

- est le pendant de Contrast By Details Levels, mais aussi du module
  Contrast de Wavelet main. Là encore la courbe représente en abscisse
  les niveaux de décomposition, et en ordonnée l'amplification ou la
  réduction du signal.
- Attenuation response, permet de choisir l'étendue de la zone impactée,
  autour de la valeur moyenne du signal.
- Offset : déplace l'action centrale du système vers les basses ou
  hautes luminances
- Chroma levels : agit sur les composantes "a" et "b" de L\*a\*b\* en
  pourcentage d'action de la luminance.

Avec ce module, vous pouvez - combiné ou non avec la courbe Local
contraste luminance, renforcer ou atténuer des détails - contraste
apparent.

###### Directional Contrast

Vous pouvez opérer un Tone mapping avec ce module. Il agit sur la
différence entre les 3 directions de décomposition : horizontale,
verticale et diagonale Le processus joue sur l'écart entre diagonal et
le coupe horizontal / vertical. Ceci permet d'agir sur l'effet de bord
(edge). La courbe agit en fonction de la luminance.

- Attenuation response : permet de contrôler l'action au plus proche des
  contrastes moyens, en réduisant l'action sur les faibles et fort
  contrastes (étendue de la zone impactée). L'accroître va augmenter
  l'action en dehors des contrastes moyens.
- Delta balance: permet d'agir selon la valeur positive ou négative,
  plutôt sur les niveaux élevés (levels) ou les niveaux faibles.

###### Wavelet level tone mapping

Exemple pour accroître la texture : [Exemple dans Premiers pas -
accroître la texture avec Wavelets Tone
mapping](Local_Lab_controls/fr#Trois_manières_d'accroître_la_texture.md)

Ce module ne fait intervenir que l'outil Wavelet avec une compression
(ou décompression) qui peut toucher chaque niveau de décomposition et
l'image résiduelle. L’atténuation des artefacts dus à la recomposition
est assurée par un Guided Filter (voir ci-dessous).

- Attenuation response : permet de contrôler l'action au plus proche des
  contrastes moyens, en réduisant l'action sur les faibles et fort
  contrastes (étendue de la zone impactée). L'accroître va augmenter
  l'action en dehors des contrastes moyens.
- Balance Threshold: (défaut 1.4) permet un équilibrage de l'action,
  autorisant dans certains cas aux ombres d'être débouchées
  - Les valeurs négatives assurent la compression des données et donnent
    un rendu Tone mapping, différent des opérateurs habituels (Mantiuk,
    Fattal...); il sera plus sensible - par conception - aux différents
    niveaux de contraste local, et moins sensible pour traiter les
    aplats.
  - Les valeurs positives servent à réduire le contraste apparent et
    permettent des effets similaires à Original Retinex. Ils sont une
    alternative à Dodge and burn.
  - Compress residual image : accroît ou réduit le contraste de l'image
    résiduelle.
- il est recommandé, pour réduire les artefacts, d'utiliser si
  nécessaire Clarity and Sharp mask - Blend & Soft images, en ajustant
  la valeur de "Soft radius" qui est à 1 par défaut (faible valeur
  convenant dans une majorité de cas)

##### Commentaire

- n'oubliez pas que vous pouvez utiliser Scope pour cibler l'action
  et/ou Excluding spot pour annuler une action sur une zone choisie,
  notamment avec "Levels dynamic Range Compression" pour annuler des
  ombres trop prononcées.

##### Importance de Attenuation response

Agit sur l'écart type (même si la distribution n'est pas du tout
Gaussienne, mais c'est une modélisation). Pour la quasi totalité des
algorithmes Wavelet pyramid, la prise en compte pour chaque niveau de la
moyenne, de l'écart type, du maximum, permet de traiter la décomposition
d'une manière non linéaire afin d'éviter les artefacts. Les valeurs de
micro-contraste proche de la moyenne subissent une amplification plus
importante que les basses et hautes valeurs.

### Tone Mapping

Exemple d'utilisation pour accroître la texture :[Exemple dans Premiers
pas - accroître la texture avec Tone
mapping](Local_Lab_controls/fr#Trois_manières_d'accroître_la_texture.md)

- Possibilité de masque et Recovery based on Luminance mask en modes
  Standard et Advanced.
- Ajout d'un slider saturation (formule de Mantiuk quelquefois
  insuffisante)
- Strength est renommé en Compression strength - sa vraie fonction:les
  réglages possibles sont différents / Lab adjustments -1 à 2 / Local
  adjustments -0.5 à 2
- Gamma: les réglages possibles sont différents / Lab adjustments 0.8 à
  1.5 / Local adjustments 0.4 à 4
- Reweighting Iterates : les réglages possibles sont différents / Lab
  adjustments 0 à 9/ Local adjustments 0 à 3
- ajout d'une Checkbox : Normalize luminance. Dans le cas activé,
  l'image finale a la même moyenne et la même variance que l'image
  initiale.
- Mask

Tone-Mapping associé à "scope" permet de réaliser - entre autres -une
fonction clarté (clarity), limitée à une zone d'action.

### Soft Light & Original Retinex

Soft Light est identique à celui du menu principal

#### Original Retinex

Un exemple d'utilisation:[Exemple dans Premiers pas de Dodge and burn -
éclaircir et
bruler](Local_Lab_controls/fr#Comment_réaliser_un_Dodge_and_burn_(Éclaircir_et_brûler) "wikilink")

Après essais, j'ai tenu à ajouter - exclusivement en mode local,
l'algorithme original de Retinex (origine Ipol). Cet algorithme est
différent de ceux utilisés par ailleurs, y compris dans Rawtherapee. Il
essaie de traduire la perception de l’œil lorsque il y a des ombres et
des variations de luminance; perception de l’œil qu'un capteur
photographique a du mal à rendre. Par exemple pour un portrait au flash
ou en lumière forte le visage verra souvent apparaître des zones ombre
ou lumineuse trop accentuées - qu'on pallie quelquefois avec des
fonctions telles "dodge" and "burn"

Il peut dans certains cas remplacer cette fonction "dodge" and "burn"
qui dans certains logiciels indiquent avec une brosse les endroits à
assombrir ou éclaircir. Dans le cas de ce Retinex original PDE cette
opération est automatique.

Je me suis servi du code trouvé sur "Ipol"
<https://www.ipol.im/pub/art/2011/lmps_rpe/> que j'ai modifié et adapté
à Rawtherapee et au "contrôle local"

Cet algorithme complexe se décompose en plusieurs étapes:

- lecture de l'image
- utilisation d'un Laplacien discret avec seuil qui permet de déterminer
  l'intensité du Laplacien : les valeurs de "strength" aux environs de
  70 amènent un "threshold" interne du Laplacien aux environs de "4"
  (référence habituelle des transformées de Laplace). Ce Laplacien va
  éliminer les petites variations de luminance inférieures au
  "threshold"
- Le curseur "Laplace threshold deltaE" permet une différenciation du
  seuil du Laplacien selon le deltaE. Sous la valeur sélectionnée un
  Laplacien "plein effet" est choisi, au dessus de la valeur un 2ème
  Laplacien 60% plus faible est combiné avec le premier. Cette action
  est différente de celle de "scope" qui réduit l'action mais
  globalement. Ceci permet de mieux séparer l'avant-plan de l'arrière
  plan.
- création d'une transformée de Fourrier - 2 dimensions (DCT: Discrete
  Cosinus Transform)
- résolution de l'équation de Poisson (PDE) pour "équilibrer" le système
- transformée inverse de Fourrier - 2 dimensions
- normalisation de la luminance par rapport à l'image d'origine : même
  moyenne et même écart-type.

Vous pouvez avoir un aperçu du processus avec le menu "Show process
Fourier" qui permet de voir les différentes étapes;

1.  création du Laplacien variable (1ère étape)
2.  transformée de Fourier (DCT : discrete cosinus transform) de ce
    Laplacien
3.  résolution de l'équation de Poisson (PDE : Poisson discrete
    equation) sous la décomposition de Fourier : notez la relative
    proximité de cette image (sous sa forme Fourier) et celle du
    Laplacien
4.  transformée inverse - non visible dans cet aperçu... mais vous avez
    le résultat final!
5.  normalisation de la luminance (ici "absence de")

A tester, notamment dans les portraits...

### Dehaze & Retinex

Dehaze est similaire à celui de main, mais peut être associé à Retinex
pour de meilleurs résultats.

#### Retinex : Avertissement important

Exemple d'utilisation pour accroître la texture : [Exemple dans Premiers
pas - accroître la texture avec
Retinex](Local_Lab_controls/fr#Trois_manières_d'accroître_la_texture.md)

Dans Local adjustments, Retinex est proche de celui de "main", mais avec
des différences.

Retinex exige de sévères conditions pour fonctionner de manière
optimale. Il est indispensable d'avoir l'étendue nécessaire pour mettre
en œuvre les très importants rayons de flou gaussien. L'architecture de
Rawtherapee ne permet pas dans le "preview" d'avoir dans tous les cas
les conditions qui permettent cette mise en œuvre. En conséquence il y
aura des différences entre l’aperçu à l'écran et la sortie "TIF ou JPG".
Ces différences sont d'autant plus importantes que:

- le spot est de petite taille;
- les valeurs de scale sont élevées;
- "radius" est important.

L'algorithme "pleine image" n'est pas soumis à ces restrictions !

De plus la quantité de ressources consommées, mémoire, temps de
traitement augmente avec :

- la taille du spot
- radius, élevé
- scale, élevé
- utilisation de masques
- utilisation de FFTW

On peut facilement atteindre des valeurs de 6 ou 8 GB ou plus de mémoire
consommée ! Par exemple une image de D850 : 8280\*5512 - Retinex : spot
au delà des limites de l'image, Radius = 500, Scale = 10, pas de
masques, aboutit à plus de 9GB nécessaires !!

#### Fast Fourier Transform

Une case à cocher Use Fast Fourier, a été ajoutée, elle permet
d'utiliser la transformée rapide de Fourier, pour générer le flou (blur)
nécessaire à Multi Scale Retinex. Elle s'accompagne d'un accroissement
notable du temps de traitement, mais d'un gain en qualité pour les
grands rayons

#### Fonctionnalités

J'ai apporté des modifications suivantes:

- à l'interface GUI;
- ajouté un curseur à Dehaze (depth), alors que auparavant il était
  calculé à partir des paramètres Retinex
- ajouté une case à cocher pour choisir entre mode 'linéaire' qui me
  semble approprié pour travailler sur le contraste et mode "logarithm"
  plus approprié pour réduire la brume, mais qui permet aussi des effets
  sur le contraste local plus importants, mais "logarithm" peut apporter
  ou accroître un effet de halo.
- ajouté une courbe Transmission Map qui permet d'agir en interne sur la
  Transmission et réduire les artefacts
- ajouté l'affichage des données liées à Transmission map et aux données
  reconstituées
- ajouté un curseur Clip Restored Data, qui permet d'ajuster -
  conjointement avec Threshold et aussi Offset, les valeurs affichées de
  Transmission Map.
- ajouté un curseur Reduce artifact deltaE, qui agit sur les données
  juste après les actions sur "transmission map"
- changé les paramètres par défaut
- séparé (au niveau du GUI et en partie au niveau de l'algorithme) la
  place de Dehaze :
  - dans "main" ce sont 2 algorithmes séparés (séparation liée à
    l'historique de l'élaboration de chacun des algorithmes), alors
    qu'ils visent en partie une même finalité, atténuer la brume.
  - dans "Local adjustments", ils sont réunis dans la même interface,
    pour mieux profiter des points forts de chacun des 2 algorithmes.

Le nombre de réglages est différent, par rapport au mode "main". D'autre
part, Retinex local, agit en fin de processus contrairement au mode
standard qui est au début du processus Raw. Vous disposez en plus du
module "raw" Retinex (main):

- le module dehaze, Dehaze & Retinex (qui utilise l'algorithme dehaze
  pleine image). La combinaison des 2 algorithmes de réduction du voile
  atmosphérique (Retinex et Dehaze) permet une résolution élevée du
  traitement du voile atmosphérique, chacun des algorithmes ayant ses
  points forts - en particulier Retinex permet de différencier avant et
  arrière plan et Dehaze est globalement plus facile et pertinent dans
  l'action.
- Par défaut Dehaze est en mode L\*a\*b\*, sauf si vous cochez
  "Luminance only"

L'algorithme Retinex n'est utilisé que si Strength Retinex est supérieur
à 0.2

- Si vous choisissez scale=1, l'algorithme "Retinex" est partiellement
  court-circuité et le process se comporte comme "local contrast" mais
  avec des valeurs de réglages nettement plus importants - certaines
  fonctionnalités ont disparues ou changées (masques, Tone mapping...),
  d'autres ont des réglages différents (radius, variance, Threshold).
- Darkness et Lightness sont sans effet lorsque la valeur 1 est choisie.
  Dans les autres cas, la dernière étape de Multiple scale Retinex se
  voit appliquée un algorithme proche de "local contrast", ces 2
  curseurs, associés à "Strength" vont permettre de jouer en amont sur
  le contraste local.
- les autres sélections possibles : Méthode : low, uniform, high,
  Strength, Radius, Threshold, Contrast, ont un principe similaire à
  ceux du module principal, même si certains réglages et effets induits
  sont un peu différents.
- ajout d'une checkbox : Normalize luminance. Dans le cas activé,
  l'image finale a la même moyenne et la même variance que l'image
  initiale.

Possibilité de masques (uniquement pour Retinex) dont le fonctionnement
est globalement similaire aux autres masques, mais qui a ses
particularités - notamment d'être incorporé au processus Retinex avec la
possibilité, soit d'être élaborés juste au début du traitement, soit à
la fin prenant en compte "transmission map"

Par exemple pour traiter une image fortement brumeuse:

- en première étape agir dans le menu principal avec la fonction Dehaze,
  dans certains cas l'arrière plan ne sera pas ou peu impacté et restera
  brumeux
- puis sélectionner Retinex, positionner le spot dans la zone brumeuse
  puis
  - agir sur Dehaze
  - puis généralement régler radius, avec une valeur élevée (supérieure
    à 100 ou 150, mais des valeurs inférieures peuvent convenir)
  - régler généralement variance (contraste) avec une valeur faible
    (inférieure à 100, mais des valeurs supérieures peuvent convenir)
  - régler scale sur 3 ou plus. Plus les valeurs seront élevées, plus
    variance pourra être élevée et réduire ainsi les artefacts.
  - agir sur scope, strength et chroma pour obtenir l'effet souhaité.

Les résultats sont la plupart du temps assez imprédictibles, par exemple
certaines images seront peu sensibles au curseur Threshold, d'autres
très sensibles... Mais globalement ce module à deux usages essentiels -
avec des réglages différents :

- traiter les images brumeuses.
- réaliser un contraste local avec des valeurs importantes, avec
  possibilité de simuler "Clarity"...

##### Maîtriser les artefacts et le halo

Retinex est très performant, mais : a) complexe, b) il peut générer des
artefacts notamment aux zones de transition de luminance, c) il peut
généralement produire du halo

Pour réduire artefacts et halos, une fois les réglages de base choisis
(Radius, variance, scale, darkness, transmission gain...et strength)

- Utiliser le tableau de bord des données Transmission map.
- agir sur Clip Restored datas, Offset, ainsi que sur Threshold pour
  obtenir des valeurs de Restored datas, Min et Max proches
  respectivement de 0 et 32768. Attention d'autres valeurs peuvent
  convenir, mais il est important que les ordres de grandeurs soient
  respectées, par exemple éviter des valeurs telles que Min = -25000 et
  Max = 90000
- si les artefacts persistent, agir sur la courbe Transmission map et
  abaisser la partie proche du milieu de l'abscisse (qui correspond à la
  moyenne des données), vous pouvez également essayer de modifier les
  parties Max et min de l'abscisse (peut être en rehaussant min et
  abaissant max)
- vous pouvez aussi agir sur la courbe Transmission gain.
- vous pouvez également agir sur Reduce deltaE artifacts, en accroissant
  la valeur par défaut (vous pouvez également agir sur Scope)
- vous pouvez déplacer le Rt-spot pour changer les valeurs de référence
- bien sûr vous pouvez modifier les réglages de base et recommencer la
  démarche !
- vous pouvez vous aider d'un masque notamment sur la luminance en
  privilégiant le mode Use transmission map, et agir sur les paramètres
  de fusion (Blend, radius, etc.)

Certes c'est complexe, mais les images obtenues notamment pour
travailler sur le contraste local peuvent être très belles.

### Sharpening

Seul le mode RL deconvolution, est proposé, vous devez travailler en
mode 1:1 (zoom 100%) .

### Contrast By Detail Levels

- zone minimum d'action : 64x64 pixels - mais vous pouvez utiliser
  conjointement les propriétés de "Transition" pour réduire la zone
  d'action.
- à utiliser de préférence en mode 1:1 (zoom 100%)
- pas de curseurs pour la gestion de la peau; le système utilisé par les
  RT-spot le remplace.
- ajout d'un curseur pour la chroma
- ajout de Image résiduelle, avec 2 possibilités - Clarity - et
  contraste

Masque et Revovery based on luminance mask, en mode normal et advanced.

Cet algorithme permet plusieurs améliorations locales.

- par exemple réduire les défauts de la peau
- accroître les perspectives et le relief sur des zones de couleurs et
  de structure (comme le wavelet), mais en limitant l'action (par scope)
  à des zones délimitées.
- retirer des défauts (tâches étendues grises ou de couleurs) sur le
  capteur

Rappel - si la zone sélectionnée est grande et comprends plusieurs
objets similaires en "teinte", "chroma", luma" et 'contrast",
l'algorithme ne sélectionnera que celles-ci, laissant le reste de
l'image inchangée.

### Blur/grain & Denoise

#### Blur & Noise

- Pour ces 3 modules vous avez le choix entre travailler en mode
  Luminance only, Chrominance only, ou Luminance + chrominance

Vous avez le choix entre 3 méthodes:

##### Gaussian Blur - Noise - Grain

- Radius :un filtre gaussien est appliqué (vous pouvez choisir
  d'utiliser en sortie TIF/JPG) une transformée de Fourier (FFT), Blur
  n'est actif que si Radius supérieur ou égal à 1.6; En réduisant
  notablement la valeur par défaut de "scope" et en agissant
  éventuellement sur Luminance only il est possible d'obtenir des flous
  différenciés selon la teinte
- Noise : du bruit de luminance est ajouté à l'image;

<!-- -->

- **Film Grain** :
  - Coarseness : avec 2 réglages
    - Distribution : simule le nombre ISO
    - Gamma : change la répartition, les hautes valeurs accroissent les
      effets
  - Strength : règle l'intensité
  - Scale : par défaut à 100...

##### Median

- vous pouvez choisir entre 3x3, 5X5, 7X7, 9X9 et le nombre de passes de
  1 à 4 (ces medians sont directement dérivés de ceux de Denoise)

##### Guided Filter

- vous pouvez sélectionner Soft radius, Strength et detail, l'ensemble
  agit sur l'impression de force. Ce module peut venir en complément de
  denoise.

##### Action en complément de Denoise

Vous pouvez utiliser ce module, notamment Median et Guided filter en
complément de Denoise dans les cas délicats

### Denoise

Exemple d'utilisation de Denoise : [Exemple dans Premiers pas
d'utilisation de
Denoise](Local_Lab_controls/fr#Comment_utiliser_le_module_"Denoise".md)

Ce module est vraiment différent du module "main", pour plusieurs
raisons:

- il est équipé d'un module Non-Local means ou débruitage par morceaux
  qui ne concerne que le bruit de luminance.
- même si il utilise les mêmes fonctions de base Wavelets que "mean"
  celles-ci ont été modifiées afin de pouvoir élever le niveau de
  décomposition :
  - passer de 5 (0 à 4) niveaux à 7 (0 à 6) pour la luminance , ce qui
    permet un débruitage différent, notamment dans les aplats (mais va
    nécessiter plus de ressources).
  - passer de 6 (0 à 5) niveaux à 7 (0 à 6) pour la chrominance,
- il est doté de fonctions supplémentaires:
  - l'algorithme DCT (Discrete Cosinus Transform) est étendu à la
    composante chrominance
  - vous pouvez conjuguer les actions de Wavelets, avec d'autres outils
    par exemple, pour les cas délicats : Guided Filter qui va agir un
    peu à la manière d'un filtre bilatéral notamment pour la dimension
    "chrominance"
- Deux Expanders permettent une action sur le bruit de luminance à
  partir des informations contenues dans le masque:
  - Denoise based on luminance mask
  - Recovery based on luminance mask

Il permet aussi:

1.  Venir en complément de l'algorithme principal. Par exemple faire un
    réglage général avec "main" *a minima*, puis dans certaines zones
    choisies réduire le bruit plus profondément avec Denoise "Local
    contrast & Denoise".
2.  Comme le traitement "local" est plutôt en milieu de processus (le
    module Denoise "main" est au début du processus), il va autoriser
    une réduction du bruit généré par les traitements intermédiaires et
    ceux de "Local adjustments" en ajoutant un dernier RT-spot alloué à
    Denoise.

#### Mode

Avec 4 choix : off, Conservative, Agressive, Non local means only

- Non-local means only : Utilise seulement Débruitage par morceaux
  (patch), (Non-local means), sans utiliser Wavelets
- Conservative et Agressive concerne Wavelets

Sauf dans le cas Non local means only, vous pouvez associer Wavelets
(luminance et/ou chrominance) avec Non-local means.

#### Non-local means (Débruitage par morceaux)

Débruitage par morceaux - c'est quoi ? Contrairement aux filtres
habituels qui réalisent une moyenne des valeurs du groupe de pixels
localisés autour d'un pixel cible afin de réduire le bruit, le filtre
Non-local means, réalise une moyenne de la totalité des valeurs des
pixels contenus dans l'image, pondérées en fonction de leur similarité
avec le pixel cible. Le résultat d'un tel filtrage permet d’amoindrir la
perte de détails au sein de l'image, comparé aux filtres réalisant des
moyennes localement. Il est doté de 5 sliders:

- Strength : règle d'intensité de l'action (à zéro, pas d'action)
- Detail recovery : utilise un Laplacien pour cibler l'action sur les
  aplats, et préserver les structures (détails)
- Gamma : les valeurs faibles préservent détails et structure, les
  valeurs élevées accroissent le débruitage.
- Maximum patch size : adapte le débruitage à la taille des objets à
  débruiter
- Maximum radius size : les valeurs élevées accroissent le débruitage,
  au détriment du temps de traitement.

#### Wavelets

Cette fonction permet 6 usages et doit être utilisé en mode 1:1 (zoom
100%):

1.  Ne sélectionner qu'une zone limitée à débruiter (par couleur...) et
    laisser le reste de l'image bruitée
2.  Débruiter une zone qui aura vu le bruit s'accroître notamment à
    cause d'un accroissement important de l'exposition, ou de débouchage
    des ombres
3.  apporter un flou gaussien par niveau (pour les faibles niveaux 0, 1
    et 2) pour simuler un bokeh

- Zone minimum d'action pour les ondelettes (wavelet) : 128 pixels \*
  128 pixels
- moins de courbes, mais plus de curseurs afin de sélectionner le bon
  niveau de décomposition "wavelet" et affiner le résultat.

##### Luminance

Pour la luminance vous disposez de:

- Une courbe qui permet de répartir l'action (force en ordonnée), en
  fonction du niveau de décomposition en ondelettes (en abscisse :
  détails fins de 0 à 2, gros détails - aplats- à partir de 3).
- Luma detail recovery: utilise la fonction DCT (Discrete Cosinus)
  transform pour récupérer progressivement les détails. Le curseurs à 0,
  l'action de la DCT est maximum, si vous souhaitez restituer des
  détails, accroissez les valeurs.
- Equalizer white-black : équilibre l'action entre les tons sombres et
  clairs
- Gamma : les valeurs faibles préservent détails et structure, les
  valeurs élevées accroissent le débruitage.
- Denoise hue equalizer : courbe qui permet d'ajuster le débruitage en
  fonction de la teinte (Hue)

##### Chrominance

- vous pouvez différencier l'action sur la chrominance en fonction de la
  grosseur du bruit - fine ou coarse: fine (correspond aux 4 premiers
  niveaux) et coarse (correspond aux niveaux supérieurs à 4) .
- de plus vous avez à votre disposition, un curseur DCT : pour la
  chrominance, réglés par défaut à 0%. DCT est désactivé pour une valeur
  de 100.
  - l'algorithme utilise aussi pour la chrominance une transformée de
    Fourier (FFT - fast fourier transformed - DCT discrete Cosinus
    transformed). Le curseur à 0, l'action de la DCT est maximum, si
    vous souhaitez restituer des détails, accroissez les valeurs.
- Qualité améliorée (chroma)
  - Si vous déplacez le curseur "coarse" à 1, pour la chrominance un
    algorithme amélioré est utilisé - en réalité il fait 2 passes.
  - A la position "1" l'algorithme améliore seulement l'algorithme fine
  - A partir de "2" l'algorithme coarse est activé.
- Equalizer Color : Vous disposez d'un equalizer pour la chrominance. Il
  équilibre la force d'action sur le canal rouge -vert ou sur le canal
  bleu - jaune.

##### Deux Expanders

###### Expander: Denoise based on luminance mask

Vous permet d'agir sur le débruitage en fonction des informations de
luminance de l'image contenues dans le masque L(L) ou LC(H) (Masque et
modifications). Le masque L(L) ou le masque LC(H) doit être activé pour
utiliser cette fonction.

- Renforce dark/light areas (Rdla) : agit sur le débruitage des zones
  sombres et claires.

Les deux sliders ci-dessous agissent en fonction de "Renforce dark/Light
areas":

- Dark area luma threshold: si Renforce dark/light areas (Rdla) est
  supérieur à 1, le débruitage est progressivement augmenté de 0 % pour
  le réglage du seuil "noir" (par défaut réglé à 12) à 100 % pour la
  valeur maximale du noir (déterminée par le masque).
- Light area luma threshold : Le débruitage est progressivement réduit
  de 100 % pour le réglage du seuil (par défaut réglé à 85) à 0 % pour
  la valeur maximale du blanc (déterminée par le masque).
- Dans la zone située entre les deux seuils, les réglages du débruitage
  ne sont pas affectés par le masque.

###### Expander: Recovery based on luminance mask

Permet de cibler le débruitage en fonction de l'information de luminance
de l'image contenue dans les masques L(L) ou LC(H) (Masque et
modifications). Le masque L(L) ou le masque LC(H) doit être activé pour
utiliser cette fonction.

- Si le masque est en dessous du seuil Dark area luma threshold (défaut
  12), Denoise sera appliqué progressivement.
- si le masque est au-dessus du seuil Light area luma threshold (défaut
  85), Denoise sera appliqué progressivement.
- Entre les deux, les paramètres de l'image sans Denoise seront
  maintenus, à moins que vous n'ajustiez les curseurs Gray area
  luminance denoise ou Gray area chrominance denoise.

##### Autres

- Le curseur "Scope" permet de faire varier l'action selon le deltaE du
  sujet en tenant compte de la transition, par exemple la zone
  sélectionnée où le deltaE sera pris en compte totalement aura une
  intensité de dé-bruitage maximum, et à l'inverse le débruitage sera
  plus faible lorsque le deltaE ne sera pas (ou peu) pris en compte.
- Un très léger accroissement de la saturation est exécuté, si vous
  actionnez l'un ou l'autre des curseurs "chroma".

#### Action combinée avec Blur & Noise

Vous pouvez conjuguer l'action dans les cas délicats avec le module
précité notamment

- Gaussian Blur Noise grain
- Median
- Guided Filter : qui va agir un peu à la manière d'un filtre bilatéral
  notamment pour la dimension "chrominance"

#### Bilateral filter

Ce dispositif est la réplique du Impulse denoise des rubriques
générales. De mon point de vue son action va au delà du bruit
d'impulsion.

### Log Encoding

#### Quelques liens avec Log Encoding

Exemple d'utilisation :

[Log Encoding](local_adjustments/fr#log_encoding)

[Log Encoding et récupération des hautes
lumières](Local_Adjustments/fr#Log_Encoding_et_r.C3.A9cup.C3.A9ration_des_hautes_lumi.C3.A8res.md)

[Autres exemples avec Log
Encoding](Local_Adjustments/fr#Autre_exemple_avec_Log_Encoding.md)

#### Introduction

Ce module dérivé de celui présent sur ART (Alberto Griggio - merci à lui
pour cet excellent module) permet de traiter les images sous exposées,
ou à très haute dynamique Il encode les données avec une échelle
logarithmique qui va assurer une compression intelligente des données.

J'ai utilisé le vocabulaire et la présentation des modules Ciecam, même
si beaucoup de fonctionnalités sont absentes. Ce module Log Encoding
RGB, est complété par des réglages issus de Cam16.

Dans une première étape, il est important de connaître les valeurs des
zones noires en écart Ev (Black Ev) et celles des zones blanches (White
Ev) pour évaluer le Dynamic range - par défaut à 15 (+ 10 Ev white, -5
Ev black, Mean luminance (Scene conditions) = 10%). Cette estimation est
réalisée en amont du processus, avec une copie d'image réalisée juste
après la conversion colorimétrique (passage à sRGB, Prophoto...), donc
avant les opérations "rgb" du process principal, en particulier "Local
adjustments"

Bien sûr Scope fonctionne et permet de cibler l'action sur certaines
étendues de couleurs.

#### Relative Exposure levels

- Le système va calculer ces 2 valeurs (blackEv, WhiteEv) si vous
  cliquez sur le bouton - Automatic.
- L'algorithme prend en compte la taille du RT-spot et permet de
  différentier si nécessaire des zones à fort contraste ou sombres par
  rapport aux autres. Bien sûr si vous choisissez un RT-spot qui couvre
  toute l'image les résultats seront proches de ceux obtenus avec ART.

Par défaut cette fonctionnalité est désactivée - case à cocher "BlackEv
and WhiteEv for whole image"

- Bien sûr vous pouvez retoucher directement les valeurs de Black Ev,
  White Ev, Value, mais le calcul ne sera ré-effectué automatiquement
  que si vous cliquez sur le gros bouton "Automatic".
- Avec BlackEv and WhiteEv for whole image, désactivée, si vous
  positionnez le RT-spot sur une zone claire, les valeurs Mean
  Luminance - (Scène conditions) seront perturbées et probablement trop
  élevées, donc :
  - privilégiez les zones sombres,
  - ou retouchez si nécessaire "Mean luminance" en le réduisant,
- ou laissez activée la case à cocher.

##### Whites distribution & Blacks distribution

Ces deux curseurs permettent - toujours sur une copie de l'image, et
donc non directement - d'agir sur la distribution de la dynamique de
l'image. Les zones proches de 'White Ev' et de 'Black Ev' voient leurs
distribution changer, respectivement par 'Whites distribution' et 'Black
distribution'.

- les valeurs négatives de 'White distribution' vont agir sur les hautes
  lumières, rendant celles-ci plus perceptibles.
- les valeurs positives de 'Black distribution', vont agir selon les
  images, généralement vers un éclaircissement des zones sombres.

Ces deux réglages ont aussi une incidence sur :

- les valeurs de 'White Ev' et 'Black Ev',
- la dR (Dynamic Range),
- le point gris.

##### Brightness compression

'Brightness compression' vous permet d'agir sur les lumières et hautes
lumières de l'image en assurant une compression progressive des données.
Ce concept, inspiré de ART, a été modifié pour le rendre plus progressif
: les valeurs supérieures à 0.6 se traduisent par une compression
maximale.

#### Scene conditions

Si vous souhaitez que le calcul prenne en compte automatiquement le
Point gris de l'image avant le process, il faut laisser la case à cocher
Auto mean luminance (yb%) activée. Selon le cas, 2 algorithmes assurent
un calcul automatique, celui initialement prévu par les calculs
originaux, il peut dans certains cas échouer. Alternativement un calcul
fait à partir de Yb (luminance moyenne) s'y substitue. 3 réglages sont à
votre disposition

- Mean Luminance (Yb%) :Yb est la luminance relative du background,
  exprimée en % de gris. 18% de gris correspond à une luminance de fond
  de 50% exprimée en CIE L. Les données sont basées sur la luminance
  moyenne de l'image
- Absolute luminance : Correspond à la luminance en candelas par m2 au
  moment de la prise de vue, calculée automatiquement à partir des
  données exif.
- Surround : Modifie les tons et les couleurs pour prendre en compte les
  conditions de la scène.
  - Moyenne (Average) : Environnement lumineux moyen (standard).
  - Légèrement Sombre (Dim) : Environnement sombre. L'image devient
    légèrement lumineuse.
  - Très Sombre (Dark). L'image devient plus lumineuse

#### CAM16 Image Adjustments

- Local contrast : agit principalement sur les hautes fréquences (Basic)
- Contrast J : contraste utilisant la luminance relative (Standard)
- Contrat threshold (J & Q) : ajuste les tons moyens des 2 contrastes J
  & Q (Standard)
- Saturation : agit essentiellement sur les tons moyens et les lumières
  (Standard)

In all tools (advanced)

- Lightness J = Luminosité - luminance relative
- Brightnees Q : Clarté - Luminance absolue
- Contrast Q : contraste utilisant la luminance abslolue
- Chroma : coloration d’un stimulus relativement à la clarté d’un
  stimulus qui apparaît blanc sous des conditions identiques.
- Colorfullnes : La quantité perçue de teinte par rapport au gris.

#### Viewing Conditions

- Mean Luminance (Yb%) : luminance relative du background, exprimée en %
  de gris. 18% de gris correspond à une luminance de fond de 50%
  exprimée en CIE L. Les données sont basées sur la luminance moyenne de
  l'image (en sortie souhaitée)
- Absolute luminance: luminance absolue de l'environnement de sortie
  (par défaut 16cd/m2)
- Chromatic adaptation : L'adaptation chromatique permet d'interpréter
  une couleur en fonction de son environnement spatio-temporel.
  Utilisable lorsque la balance des blancs s'écarte de manière
  significative de la référence D50. Adapte les couleurs à l'éclairage
  du périphérique de sortie.
- Surround : Modifie les tons et les couleurs pour prendre en compte les
  conditions de l'environnement de sortie.
  - Moyenne (Average) : Environnement lumineux moyen (standard).
  - Légèrement Sombre (Dim) : Environnement sombre. L'image devient
    légèrement sombre.
  - Très Sombre (Dark). L'image devient plus sombre
  - Extrêmement sombre (Extremely Dark) : L'image devient très sombre

#### Graduated Filter

A la fin du traitement "log", vous pouvez agir sur la luminance
résultante avec un Graduated Filter doté de 2 sliders : gradient
strength et gradient angle.

### Color appearance (Cam16 & JzCzHz)

Exemple d'utilisation de Color Appearance et des fonctionnalités HDR
:[HDR-SDR Première approche : Log encoding – Cam16 – JzCzHz –
Sigmoid](Local_Adjustments/fr#HDR-SDR_Premi.C3.A8re_approche_:_Log_encoding_.E2.80.93_Cam16_.E2.80.93_JzCzHz_.E2.80.93_Sigmoid.md)

Le module Color appearance(Cam16 & JzCzHz) est à la fois:

- plus simple que Color Appearance & Lighting(Ciecam02/16)
  - il ne dispose pas de CAM02, uniquement Cam16
  - pas de mode Automatic symmetric, ou Mixed. Donc pas de possibilité
    d'adaptation chromatique à la fin d'un processus.
  - pas de choix du White-point model et pas de choix de l'illuminant.
  - pas de possibilités de réglages séparés de CATO2/16 adaptation
    (Scene et Viewing conditions).
  - pas de réglages de température et teinte dans Viewing conditions.

<!-- -->

- plus complet que Color Appearance & Lighting(Ciecam02/16) et selon le
  niveau de complexité (Basic, Standard, Advanced)
  - prise en compte de HDR PQ (Peak Luminance) : première approche HDR
  - fonction Sigmoid Q & Log encoding Q, tenant compte de Black Ev et
    White Ev
  - masques
  - et en mode advanced, le module expérimental JzCzHz (pour un meilleur
    traitement HDR) .

Globalement le module Color Appearance(Cam16 et JzCzHz), au moins pour
la partie Cam16, est plus simple, plus intuitif, et prend en compte les
possibilités de Local Adjustments : deltaE, Scope, transition, excluding
spot, etc.

Pour une présentation de Cam16 : [Utilisation de Cam16 et des
fonctionnalités
HDR](Local_Adjustments/fr#Utilisation_de_Cam16_et_des_fonctionnalit.C3.A9s_HDR.md)

Pour une présentation de JzCzHz :[Le module expérimental
JzCzHz](Local_Adjustments/fr#Le_module_exp.C3.A9rimental_JzCzHz.md)

Pour voir le tutoriel: [Tutoriel Color Appearance & Lighting
(CIECAM02/16) et Color Appearance (Cam16 &
JzCzHz)](CIECAM02/fr#Tutoriel_Color_Appearance_.26_Lighting_.28CIECAM02.2F16.29_et_Color_Appearance_.28Cam16_.26_JzCzHz.29.md)

A titre d'information JzCzHz contient divers outils afin de montrer
qu'il peut se substituer à Lab.

- Courbes: Jz(Jz), Cz(Cz), Cz(Jz), Jz(Hz), Hz(Hz), Cz(Hz)
- Shadows/Highlights Jz
- Wavelet Jz :
  - Local contrast
  - Clarity & Sharp Mask

## Cas d'usage spécifique : réduction des défauts (capteur sale, yeux rouges, ...)

Exemple d'utilisation:[Dans Premiers pas - Traiter les yeux rouges -
retirer les défauts du
capteur](Local_Lab_controls/fr#Traiter_les_yeux_rouges_-_retirer_les_défauts_du_capteur.md)

### Généralités

Par conception "Local Adjustements" n'a pas été conçu pour éliminer ces
défauts. Néanmoins par effet de bord, certains défauts apparents et
gênant en photographie peuvent être réduits voire supprimés. Ceci bien
sûr n'est pas incompatible avec d'autres modules plus spécialisés
incorporés ou non à "Local adjustements"... Au moins 3 fonctions
présentes, en adaptant l'usage, peuvent être utilisées, séparément ou
ensemble :

- "Color & light" pour des défauts ponctuels ou les yeux rouges;
- "Contrast by detail level" pour des défauts répartis (taches de
  graisse,..) ;
- "Wavelet" (Local contrast & wavelets) pour les défauts répartis
  (taches de graisse);
- "Blur/Grain" en complément éventuel : attention cette action est assez
  destructrice - à utiliser avec modération.

Vous pouvez agir soit:

- directement, cas général, sur le fichier "raw", ou "TIF", etc.
- soit sur le fichier flat-field si vous en avez élaboré un.

### Choix de la taille du RT-spot

On peut être tenté d'ajuster la taille du RT-spot à celles des défauts,
en général petits. Cette démarche est en général à éviter car :

- elle masque la visibilité de l'action
- elle risque dans certains cas soit un crash dus à des problèmes
  d'allocation mémoire, soit des dysfonctionnements aux limites des
  processus

Il est préférable de mettre un RT-spot couvrant largement le défaut, et
soit facilement visible par exemple un RT-spot de 50x50 pixels ou
100x100 pixels, puis:

- choisir une taille du Spot (Spot size) petite, adaptée au défaut
- réduire la transition à une valeur faible entre 2 et 10, de telle
  façon que à cette valeur la quasi totalité du défaut est couvert
- accroître "transition decay" jusque 10 ou 15, avec ce réglage la
  décroissance d'action est très rapide
- agir sur "scope" pour centrer l'action sur le défaut

Par exemple si c'est un oeil rouge de 6x6 pixels, choisissez "transition
= 5", "transition decay = 10", à partir du 8ème pixel l’affaiblissement
(sans l'action de "scope") est de plus de 90%.

Exemple d'affaiblissement - sans action avec "scope":

- taille du RT-spot 100x100
- taille du défaut 10x10 (Iris d'un oeil)
- "transition" = 9
- "transition decay" = 15
- à la limite du défaut 10x10 baisse de l'action : 75%
- à 2 pixels après le défaut, baisse de l'action 28%
- à 4 pixels après le défaut baisse de l'action 12%

Si le RT-spot, pour le même défaut est de 50x50

- à 2 pixels après le défaut, baisse de l'action 14%
- à 4 pixels après le défaut, baisse de l'action 4%
- etc.

### Utilisation avec le module "Color & Light"

- Activez "Color Light"
- Vous pouvez utiliser l'équivalent d'une fonction "yeux rouges" en
  choisissant un encadrement assez serré de l’œil - sélecteur circulaire
  centré sur le rouge, délimiteurs de spot proches de l’œil - une valeur
  de scope réduite, puis agir sur réduction "lightness" -100, et
  réduction chrominance -100.
- De la même manière vous pouvez réduire les défaut du capteur de type
  "Spot IR", en choisissant un encadrement assez serré du défaut -
  sélecteur circulaire centré sur le défaut, délimiteurs de spot proches
  du défaut - puis agir sur "chrominance" en réduisant la valeur, agir
  éventuellement sur "scope" pour réduire l'étendue de l'action.
- Vous pouvez dans des cas simples, réduire les défauts de type "capteur
  encrassé" notamment lorsque celui-ci est gras. Ceci se traduit par des
  taches qui apparaissent sur les fonds unis. Pour cela choisissez un
  encadrement assez serré du défaut - sélecteur circulaire centré sur le
  défaut (adaptez la taille du spot) , délimiteurs de spot pas trop
  proches du défaut pour permettre une transition peu visible. Puis: a)
  réduisez "Transition" à des valeurs faibles - transition decay
  élevé; b) agissez sur "luminance" et éventuellement sur "chrominance"
  pour approcher le rendu de la zone polluée à celui de la zone
  saine; c) agir modérément sur "scope" pour moduler l'action
  souhaitée. d) possibilité d'utiliser "Color correction grid - direct",
  ainsi que "Softradius"

### Utilisation avec le module "Contrast by detail levels"

Dans le cas de capteur encrassé (de type "graisse"), et lorsque la zone
est importante ou pour une série de petits défauts, Il peut être utile
d'utiliser "Contrast by details levels" qui va agir comme un outil
"wavelet" sur la luminance et aussi si nécessaire sur la chrominance.
Dans ce cas:

1.  mettez le Spot de sélection sur un défaut prononcé (en adaptant sa
    taille si nécessaire);
2.  choisissez une zone de sélection large pour couvrir la majorité de
    la surface concernée par les défauts;
3.  Sélectionnez une valeur de transition assez importante (selon le
    cas) et "transition decay" élevé;
4.  Activez "Contrast by detail levels" et agissez sur les niveaux 3 , 4
    (rarement 5) ou plus faibles en réduisant le contraste (valeurs
    inférieures à 100) et en agissant si nécessaire sur le curseur
    chroma.

Attention, la zone d'action est limitée à 64x64 pixels, en dessous de
ces valeurs, CBDL est désactivé pour éviter le crash - la décomposition
en ondelettes de Harr, nécessite au mimima 64x64 pixels.

### Utilisation avec le module "Local Contrast & Wavelet"

Vous pouvez utiliser notamment :

- contrast by levels : en agissant sur la courbe, en étant proche de la
  partie gauche de la courbe - les niveaux faibles - et en réduisant le
  micro-contraste
- vous pouvez agir si nécessaire sur "Chroma levels" pour réduire les
  artefacts colorés
- Blur levels : là encore avec les niveaux faibles, vous pouvez flouter
  (blur) les petits défauts, avec ou sans action de "contrast by levels"

## Annexe

### Quel type de contrôle local?

Lorsqu'on observe les différents logiciels du marché on trouve plusieurs
types de contrôles locaux

1.  les contrôles de type "lasso", associés à des calques et masques de
    fusion, comme par exemple dans Photoshop (c). Ce type de contrôle
    est majoritaire dans les logiciels (Photoshop (c), Gimp (c),
    Darktable (c)...) et l'avis des utilisateurs est obligatoirement
    orienté vers ceux-ci au détriment du point 4. ci-dessous moins
    connu!
2.  les dispositifs de suppression de "yeux rouges", ou de "spot"
    (poussières...) liés aux imperfections du capteur
3.  les brosses qui permettent des mini corrections locales
4.  les contrôles de type U-points, utilisés jusque récemment dans Nikon
    Capture NX2 (c), ou comme complément à d'autres logiciels comme Nik
    Software (c), et récemment dans DxO ou Capture NXD. Pour qui a tâté
    de ces dispositifs (encore minoritaires aujourd'hui) il n'est pas
    question de revenir aux calques et masques de fusion! Ce type de
    contrôle **nécessite un apprentissage différent de ceux de type
    lasso-calque et un désapprentissage cognitif** de ceux-ci. De mon
    point de vue, ils sont globalement plus performants.

Dans la version présente de Rawtherapee, l’algorithme développé est
proche dans le principe du point 4. ci-dessus, les U-points avec
quelques possibilités pour 2. Bien sûr, le code de Nik Software m'est
inconnu, mais il y a quelques années j'ai été séduit par la facilité
d'utilisation et les performances des U-points, et j'ai entrepris de
développer un produit qui ne ferait pas appel, ni au lasso, ni aux
calques, ni aux masques de fusion (même si j'en ai récemment ajouté en
complément).

Bien sûr rien n'interdit d'avoir les 3 possibilités (Lasso-calque,
retouches spot, U-points) !

##### Évolution possible?

A terme, il doit être possible, même si l'utilité me semble discutable
du fait de l'algorithme de détection de forme - à noter que DxO et
Capture NXD n'ont qu'une sélection circulaire - , de remplacer l'ellipse
ou le rectangle, par une courbe (courbe de Beziers) ou un polygone
tracée à l'aide de la souris, à condition :

- que la transformée homothétique - de centre le centre du Spot "C" - de
  chacune des 4 courbes n'ait pas d'intersection avec la courbe
  originale.
- chacune des 4 courbes passe par 2 "points délimiteurs" "T" ou "B" et
  "L" ou "R"
- chacune des 4 courbes soit à l'intérieur des 4 rectangles "C", "T",
  "L", "C" ou "C", "T", "R", "C" ou "C", "B", "L", "C" ou "C", "B", "R",
  C" ou à l'intérieur de la zone globale en permettant l'homothétie
  comme évoqué ci-dessus
- permettre l'élaboration de 4 LUT de type y=f(x)

Cette "amélioration" intellectuellement satisfaisante, ne devrait être
que d'un apport négligeable (sauf cas spécifiques) - dans le cas des
RT-spots. Néanmoins il sera toujours possible de faire coexister les
actuels RT-spot avec des contrôles par"lasso" de type Photoshop (c).

### Quels défis à résoudre?

Plusieurs problèmes généraux sont à résoudre afin d'obtenir un
fonctionnement fluide :

- permettre un nombre quasi illimité de RT-spot (spot de contrôles);
- adapter les algorithmes locaux aux problèmes d'échelle, car beaucoup
  d'algorithmes tiennent compte de la taille de l'image - donc de la
  zone traitée. Cet aspect est fondamental, notamment avec les courbes
  qui agissent sur toute l'image;
- adapter - lorsque c'est le cas - les algorithmes RGB du code
  principal, en mode L\*a\*b\* utilisé par le contrôle local
- minimiser l'occupation mémoire et les temps de traitement en sortie
  JPG et TIF;
- permettre des mises à jour logicielles faciles en cas d’évolution des
  algorithmes ou d'évolution du nombre de méthodes ;
- optimiser les écarts entre "preview" et sortie JPG / TIF;
- etc.

Pour chaque RT-spot :

- permettre selon le cas, une action dans la zone sélectionnée ou à
  l'extérieur de la zone sélectionnée;
- permettre selon le cas une détection de forme pour délimiter l'action
  ou une action également répartie sur toute la zone sélectionnée;
- assurer une transition entre le cœur de la zone traitée et le reste de
  l'image;
- etc.

Actuellement, les RT-spot (spot de contrôles) sont opérationnels, pour
le mode L\*a\*b\*, et pour les méthodes suivantes:

1.  Color & light :en mode basic avec possibilité de masques (mode
    standard et et advanced), et inverse ;
2.  Dynamic Range & Exposure: en mode basic avec possibilité de masques
    (mode standard et et advanced) et inverse;
3.  Shadows Highlight & Tone equalizer: en mode basic avec possibilité
    de masques (mode standard et et advanced) et inverse;
4.  Local Contrast & Wavelets :en mode basic avec possibilité de masques
    (mode standard et et advanced);
5.  Vibrance & Warm/Cool : en mode basic avec possibilité de masques
    (mode standard et et advanced);
6.  Soft Light & Original Retinex; Soft Light en mode basic, Original
    Retinex en mode standard et advanced)
7.  Blur/grain & Denoise: en mode basic avec possibilité de masques
    (mode standard et et advanced);
8.  Dehaze - Retinex : Dehaze en mode basic et standard, et Retinex en
    mode advanced avec masques (spéciaux)
9.  Sharpening : en mode normal et inverse;
10. Tone Mapping: en mode basic avec possibilité de masques (mode
    standard et et advanced);
11. Contrast By Detail Levels : en mode basic avec possibilité de
    masques (mode standard et et advanced);
12. Log Encoding : en mode basic avec possibilité de masques (mode
    standard et et advanced);
13. Color Appearance(Cam 16 & JzczHz) :Cam16 en mode basic avec
    possibilité de masques (mode standard et et advanced), JzCzHz en
    mode advanced.

### Développement - Performance - Interface graphique - GUI

L'ensemble de l'équipe de Rawtherapee a contribué au développement, mais
en particulier:

1.  Principe des algorithmes - code de base - Jacques Desmis
2.  Amélioration des performances (vitesse, mémoire...) - Ingo Weyrich
3.  Interface GUI - Pierre Cabrera. Elle me semble simple et intuitive.
4.  Aide à la mise au point (essais, conseils, échanges...) : Sébastien
    Guyader (jusqu'en 2019). A partir de 2020, Wayne Sutton, Jacques
    Dekker, Andy Astbury.
5.  Mise en bon anglais du GUI (outils, sliders, courbes, Tooltips..) et
    mise en anglais de la documentation : Wayne Sutton.

Certaines parties du code, je les ai souvent adaptées, sont issues du
travail de Alberto Griggio:

- Detail threshold recovery (denoise),
- Film grain,
- Tone Equalizer,
- Amélioration de Guide Filter Luminance (log),
- Log Encoding.

#### Nouveauté du GUI (Pierre Cabrera)

Depuis avril 2020, l'interface graphique présente de nombreuses
innovations et depuis mai 2020, vous pouvez pour chaque outil, choisir
le niveau de complexité "Advanced" ou "Standard" ou "Basic":

- pour chaque RT-spot vous pouvez choisir les outils qui vous
  conviennent. Ce qui va éviter de noyer l'interface avec des champs
  inutiles. Par exemple vous pouvez choisir "Color & Light" avec le
  niveau de complexité "Basic" et "Blur/grain & Denoise" avec le niveau
  de complexité "advanced".
- les fichiers pp3 ne contiennent que les modifications, ce qui
  simplifie et accélère le travail courant.
- lorsque vous réalisez un "copy" "paste" des profiles - soit à partir
  du "File Browser", soit à partir de la barre des "Processing
  profiles", un menu vous propose quels RT-spot vous voulez copier.

### Aide - Tooltip

Vous pouvez désactiver l'aide qui apparaît pour certains sliders,
expanders, comboBox,... et qui peut être gênante.

Aller dans "Preferences " - "General" - "Show local adjustments Tooltip"

### Temps de traitement et utilisation de la mémoire

Lorsqu'on utilise la sortie JPG ou TIF, et pour le mode "normal",
l'algorithme n'effectue les calculs que pour la zone délimitée. En ce
sens les temps de traitement et l'occupation mémoire sont réduits. Bien
sûr le temps de traitement va dépendre du nombre de spots de contrôles,
de leur taille, et du type de traitement.

Les plus gros consommateurs de temps sont

- "Retinex" (Dehaze & Retinex) : forte influence de la taille du spot,
  de "radius" et de "scale" et de "chroma" au delà de 40, ainsi que de
  FFTW.
- "Tone Mapping" : "edge stopping" accroît linéairement le temps de
  traitement. "Reweigthting iterate" multiplie par sa valeur les temps
  de traitement. On peut très facilement attiendre des temps de
  plusieurs dizaines de secondes.
- Denoise (Local contrast & Denoise) : en mode full image, et avec des
  niveaux de décomposition élevés, des valeurs de mémoire supérieures à
  8M° voire 16M° sont nécessaires

Activer FFTW, peut se traduire (grandes images) par des temps de
traitement importants.

### DeltaE ΔE utilisé

J'ai choisi la version la plus simple du deltaE.

Si on évalue les valeurs L\*a\*b\* dans l'intervalle : L \[0..100\] a
\[-128..+128\] b \[-128..+128\]

- Si Lc, ac, bc sont les valeurs du pixel courant
- Si Lr, ar, br sont les valeurs de la référence (converties des valeurs
  LCH de base)

<!-- -->

- deltaE = sqrt(SQR(Lc - Lr) + SQR(ac - ar) + SQR (bc - br))
- Bien sûr cette équation de base est modifiée si vous utilisez :
  - ab-L balance deltaE;
  - C-H balance deltaE;
  - DeltaE - decay.

Correspondance avec la valeur de "scope":

- il y a une relation entre scope et deltaE et l'affaiblissement
  (decay), et "threshold deltaE-scope"
- deltaE-scope threshold agit sur l'étendue de prise en compte
  - par défaut deltaE-scope threshold = 2 conduit à des valeurs de
    deltaE prises en compte de 2 à 155
  - si vous réduisez deltaE-scope threshold, la valeur maximale va être
    réduite jusque 130, à l'inverse si vous augmentez au maximum, le
    maximum deltaE sera de 230. De mon point de vue il faut réserver
    cette situation aux images avec de très grosses variations de gamut,
    par exemple des fleurs aux couleurs éclatantes. Par contre accroître
    légèrement deltaE-scope threshold (3 à 5) permet un rendu différent
    du système.
    - un deltaE de 230 ne peut se rencontrer que dans des cas extrêmes,
      par exemple 80 d'écart sur L, 158 sur a, 145 sur b... (uniquement
      accessible pour les très grands espaces de travail, avec des
      couleurs de base telles fleurs éclatantes ou couleurs
      artificielles, et action importante sur les sliders chroma et
      luma)

Cas avec deltaE-scope threshold = 2 (défaut)

- les deltaE pris en compte varient de 2 (scope=0) à 155 (scope=100).
  Bien sûr ce choix est arbitraire on peut changer les 2 seuils mini et
  maxi (voir ci-dessus), mais il semble fonctionner dans une majorité de
  cas.
- 2 n'est pas perceptible par l'œil (mais ici ce n'est pas l'objectif
  recherché)
- 155 correspond à des valeurs très élevées, par exemple 80 d'écart sur
  "a" (composante rouge vert), 80 sur "b" (composante bleu jaune"), 80
  sur "L" ou autre exemple 50 sur "L", 105 sur "a" et 100 sur "b"

Par exemple lorsque "scope" est réglé sur 15, ceci signifie que toutes
les couleurs telles que deltaE \< 3 seront traitées telles quelles sans
atténuation. Celles avec deltaE \> 27.5 seront ignorées, les valeurs
intermédiaires sont affaiblies d'autant plus qu'on se rapproche de
deltaE = 27.5, par exemple:

- un deltaE de 3 correspond par exemple à (il y a d'autres
  combinaisons...):
  - delta L = 2
  - delta a = 1
  - delta b = 2

<!-- -->

- un deltaE de 15 correspond par exemple à (il y a d'autres
  combinaisons...) :
  - delta L = 10
  - delta a = 9
  - delta b = 6.6

<!-- -->

- ou encore un deltaE de 27.5 par exemple à (il y a d'autres
  combinaisons...) :
  - delta L = 15
  - delta a = 14
  - delta b = 18.3

Lorsque on augmente "scope", par exemple à 50, toutes les couleurs
telles que deltaE \< 4.5 seront traitées telles quelles sans
atténuation. Celles avec deltaE \> 80 seront ignorées, les valeurs
intermédiaires sont affaiblies d'autant plus qu'on se rapproche de
deltaE = 80, par exemple:

- un deltaE de 80 correspond par exemple à (il y a d'autres
  combinaisons...):
  - delta L = 20
  - delta a = 62
  - delta b = 44,7

Etc.

### Modules et fonctions disponibles par niveau : Basic, Standard, Advanced (expert)

- ne sont mentionnées que les différences "Advanced" / "Standard"
- "Basic" est similaire à "Standard" sans les masques, les courbes, les
  graduated filters, et évidemment Recovery based on luminance mask,
  ....

#### Color & Light

Différences Advanced / Standard

- Slider Spot structure
- Slider Blur Shape detection
- Merge files (as in Photoshop, with blend modes (difference, multiply,
  etc.)
- Graduated filter: chroma gradient strength, et hue gradient strength
- Curves: C(L), L(C), L(H), C(H), H(H), RGB Tone curves

<!-- -->

- Mask and modifications : Structure Mask, Blur Mask, Laplacian
  threshold, Gamma, Slope, Shadows, Hue curve, Wavelts levels selection.

#### Dynamic Range & Exposure

Différences Advanced / Standard

- Dynamic Range Compression: Gamma, Spot structure
- Recovery based on luminance mask : Decay strength
- Mask and modifications : Laplacian threshold, Gamma, Slope, Graduated
  filter
- Recovery based on luminance mask : Decay strength

#### Shadows Highlight & Tone Equalizer

Différences Advanced / Standard

- Recovery based on luminance mask : Decay strength
- Mask and modifications : Laplacian threshold, Gamma, Slope

#### Vibrance & Warm Cool

Différences Advanced / Standard

- plus d'options dans Vibrance : Pastels tones - Saturated - Curve -
  Skin tones - Avoid color shift
- Recovery based on luminance threshold : Decay strength
- Graduated Filter Chroma gradient strength, Hue gradient strength
- Mask and Modifications : Laplacian threshold, Gamma, Slope

#### Color Appearance(Cam16 & JzCzHz)

Différences Advanced / Standard

- Change tool position : default, Tone mapping, Wavelet, Dynamic Range
- Cam 16 Image adjustments : Brightness (Q), Contrast(Q), Chroma(C),
  Colorfullness(M), Hue, Curves (lightness, Brightness), Curves (Chroma,
  Saturation, Colorfullness)
- Recovery based on luminance mask : Decay strength
- Mask and modifications : Laplacian threshold, Gamma, Slope
- module JzCzHz

#### Soft Light & Original Retinex

Différences Advanced / Standard

- Original Retinex (atténuateur de contraste cf Dodge and Burn): Show
  Fourier(f) process : Show modified image, delta Laplacien (first),
  Fourier(f) DCT, Poisson (pde f), No luminance normalization, show
  modified areas

#### Blur/Grain - Denoise

Différences Advanced / Standard

- Blur/Grain (Gaussian Blur - Noise - Grain) :
  - case à cocher f-always Use Fast Fourrier Tansform
  - Recovery based on luminance mask : Inverse algoritm
- Denoise :
  - Denoise based on luminance mask,
  - Non-local Means luminance : Maximum radius size
  - Recovery based on luminance mask : Decay strength
- Mask and Modifications (Blur/grain & Denoise): Highlight, Wavelet
  level selection

#### Tone mapping

Différences Advanced / Standard

- Gamma, saturation, Reweighting iterates
- Recovery based on luminance mask : Decay strength
- Mask and modifications : Laplacian threshold, Gamma, Slope

#### Dehaze - Retinex

Différences Advanced / Standard

- Retinex: with all Retinex tools, Recovery based on luminance mask,
  Mask and modifications

Attention dans ce module, pas de différences entre les modes "basic" et
"standard" (problème de GUI difficile à résoudre)

#### Sharpening

Différences Advanced / Standard

- Contrast threshold, Blur radius, Gmma, Amount, Damping, Iterations

#### Local contrast & Wavelets

Différences Advanced / Standard

- Wavelets :
  - wavelets levels
  - Residual image (Main): Merge only with original image, Gamma
    (wavelet pyramids)
  - tous les outils "pyramids" (graduated filter, Edge sharpness, Blur,
    Contrast by detail level, Tone mapping, Directional contrast

<!-- -->

- Local contrast & wavelets:
  - Recovery based on luminance mask : Decay strength

#### Contrast by details levels

Différences Advanced / Standard

- Recovery based on luminance mask : Decay strength
- Mask and modifications : Laplacian threshold

#### Log Encoding

Différences Advanced / Standard

- All tools : lightness(J), Brightness(Q), Contrast(Q), Chroma(C),
  Colorfulness(M)

Recovery based on luminance mask : Decay strength

Si on exclue "Denoise" , "Tone mapping" et "Retinex" et certains usages
de "Wavelets", les temps de traitement sont de l'ordre de quelques
dixièmes de seconde par spot de contrôle, et le besoin en mémoire de
l'ordre de quelques centaines de M.

Deux réglages agissent fortement sur les temps de traitement et le
besoin en mémoire :

- "mask" ("Color and Light", "Dynamic Range & Exposure", "Shadows
  Highlight & Tone Equalizer", "Contrast by detail levels", "Tone
  mapping", "Retinex", "Tone mapping, "Blur/grain & Denoise", "Log
  encoding", "Local contrast & wavelets", "Color appearance(Cam16 &
  JzczHz) accroît nettement les besoins en mémoire. Attention si votre
  machine a des capacités limitées et si vous sélectionnez une grande
  zone.
- l'option FFTW (Retinex, Local contrast, Blur/grain...) même optimisée
  peut accroître ou réduire les temps de traitements - dans tous les cas
  elle améliore la qualité:
  - pour des petites tailles et moyennes tailles de Spot (jusque 2000 \*
    2000 pixels) FFTW sera plus rapide
  - pour les grandes tailles (5000 \* 4000 pixels), FFTW sera plus lent

### Aspects logiciels

Comme le traitement est itératif pour chaque Rt-spot, il est important
de connaître l'ordre

- Log Encoding, Blur/grain & Denoise, Contrast By Detail Level, Vibrance
  & Warm/cool, Tone mapping, Shadow Highlight & Tone Equalizer, Soflight
  & Original Retinex, Local contrast & Wavelets, Sharp, Retinex, Dynamic
  Range & Exposure, Color & light, Common Color Mask, Color
  appearance(Cam16 & JzCzHz), Avoid color shift
- Comme évoqué dans le texte, certaines fonctions ont été réécrites,
  soit pour s'adapter à l'échelle, soit par qu'elle fonctionne en mode
  Lab au lieu de RGB.

### Quelques questions ?

#### Et le détourage des objets ?

C'est une question fréquemment posée !

- Dans une majorité de cas, l'algorithme de détection de forme sera
  largement suffisant pour ne sélectionner que ce qui est nécessaire,
  avec à la fois la commande "scope" et les curseurs prévus dans
  "settings" - shape detection et transition
- l'utilisation de "excluding spot" doit permettre de résoudre les cas
  délicats
- les masques prévus dans plusieurs modules - Color & Light, Dynamic
  Range & Exposure, Shadows Highlight & Tone Equalizer", Vibrance &
  Warm/cool, Contrast by detail levels, Local contrast & Wavelets, Tone
  mapping, Blur/Grain & denoise, Log Encoding, Color Appearance(Cam16 &
  JzCzHz) doivent aussi permettre d'améliorer la sélection dans quelques
  cas.
- la sélection peut être encore améliorée en choisissant 2 spot, très
  proches mais chacun sur une "couleur" (au sens deltaE) différente,
  avec 2 masques complémentaires

Si un spécialiste GUI est capable par exemple d'agir sur les 4 ellipses
et les transformer en courbes de Beziers (chacune inscrite dans le
rectangle centre X Y), ou de réaliser un polygone (inscrit dans le
rectangle centre X Y) à main levée alors avec une simple LUT on pourrait
simuler un détourage... pour les irréductibles des détourages,
calques...ET bien sûr (ce n'est pas le moindre problème) - modifier
l'algorithme.

#### A quoi sert l'association Retinex - Dehaze ?

Chacun des 2 algorithmes a ses points forts

- Dehaze est très performant globalement, mais "ignore" les arrières
  plans
- Retinex est performant sur la différenciation avant - arrière plan,
  mais peut produire du halo.

La combinaison des 2 : Dehaze à partir de l'image globale (ou locale) et
Retinex pour la partie locale de l'arrière plan, permet de résoudre la
quasi totalité des cas

Exemple d'utilisation pour une image brumeuse :[Exemple dans Premiers
pas - Traiter une image
brumeuse](Local_Lab_controls/fr#Traitement_d'une_image_brumeuse.md)

#### Pourquoi y a-t-il un "masque" pour chacun des modules concernés et pas un "masque global" ?

Simplement parce que chacun des modules "Dynamic Range & Exposure" ,
"Color & Light", etc. subit les traitements récursif des autres
modules - exactement comme l'ensemble des modules de Rawtherapee,
interagissent l'un sur l'autre. J'ai fait une exception pour "Blur/grain
& Denoise" qui ont en commun un masque, car: a) ils sont en début de
processus "Local adjustements" et n'ont que peu d’interactions.

Avoir un masque global, revient par comparaison à n'avoir qu'une seule
courbe pour gérer l'ensemble des courbes de Rawtherapee.

Bien sûr, par simplification, il n'y a que 11 modules avec "masques",
rien n'interdit de l'étendre aux autres...ce n'est qu'une question de
temps...si la demande s'en fait sentir.

#### Pourquoi n'y a-t-il pas toutes les fonctions de Rawtherapee avec le mode "local" ?

Le mode local est fondé et articulé autour du concept "L\*a\*b\*" et de
la notion de deltaE (Lab nécessaire), une majorité de modules
"principal" ont leur équivalent "local"

Par contre, les modules "rgb" après démosaicing ou "RGB" avant
demosaicing nécessiterait une autre approche que le concept du deltaE.
Donc rien d'impossible, par exemple pour réaliser un module "balance des
blancs locale"...

#### Comment modifier uniquement l'ensemble des feuillages d'une image ?

Fichier raw (Creative Common Attribution-share Alike 4.0):
[28](https://drive.google.com/file/d/1rRcFYYihDjW0ZHadA9S0nNyt3vwxG1Yu/view?usp=sharing)

L'algorithme permet de ne sélectionner qu'une couleur, par exemple les
feuilles d'un arbre.

Pour cela:

- la taille du spot doit être réduite pour ne cerner que la couleur
  concernée.
- Ajuster "scope" sur des valeurs faibles.
- Étendre l'action du RT-spot pour prendre en compte - si vous le
  souhaitez - l’ensemble des feuillages de l'image (par exemple si il y
  a plusieurs arbres)
- Agir sur les champs que vous souhaitez modifier (luminance,
  saturation, etc.)

<figure>
<img src="/images/Horse-foliage_.jpg" title="Horse-foliage_.jpg" width="600" />
<figcaption>Horse-foliage_.jpg</figcaption>
</figure>

Dans l'exemple ci-dessus: Dans Settings:

- Spot size = 4
- Scope (color tools) = 9

Dans Color & Light (mode Basic)

- Chrominance = 143

#### Comment réaliser la fonction "Clarté" (Clarity)

Au moins 3 façons :

1.  en utilisant Contrast by Detail Level et en agissant sur "Residual
    image - Clarity" - effet "moyen"
2.  en utilisant Tone-Mapping - effet "fort" - notamment avec l'usage de
    gamma et amount et des valeurs modérées de "compression" (attention
    aux temps de traitement)
3.  en utilisant Local-contrast & wavelets - en agissant sur "Residual
    image - Clarity" - effet "moyen"

Et pourquoi pas avec Retinex... qui est une autre manière de réaliser un
"local contrast" - plus difficile à manipuler, mais l'algorithme de
principe est proche.

Un masque sur la totalité de l'image (ou partielle) peut permettre de
modifier le gamma de l'image et affaiblir - renforcer la luminance de
certaines zones.

##### Un exemple avec Wavelet

Fichier raw (Copyright Sebastien Guyader - Common Attribution-share
Alike 4.0):
[29](https://drive.google.com/file/d/1DASGpHfl_9RDRhbq2_JQVgypgKyrdiBk/view?usp=sharing)

- Arbitrairement j'ai choisi dans Settings : "Full image"
- Ajouter l'outil : Local Contrast & Wavelet (mode Standard ou Advanced)
  - positionner le Rt-spot sur la couleur que vous souhaitez privilégier

<figure>
<img src="/images/Clarity-wav-before.jpg" title="Clarity-wav-before.jpg"
width="600" />
<figcaption>Clarity-wav-before.jpg</figcaption>
</figure>

<figure>
<img src="/images/Clarity-wav.jpg" title="Clarity-wav.jpg" width="600" />
<figcaption>Clarity-wav.jpg</figcaption>
</figure>

- J'ai choisi aussi arbitrairement de laisser Scope = 60, bien sûr vous
  pouvez le réduire ou l'augmenter.
- vous pouvez aussi bouger la position du RT-Spot.
- Merge Luma = 78.1
- Merge Chroma = 34.2

Là encore, vous faites ce que vous souhaitez, laisser Merge Chroma à 0,
baisser Merge Luma

Essayez de modifier le curseur "Wavelet levels" et observez les
résultats
