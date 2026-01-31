---
title: Color Management
contributors:
  - Lebarhon
  - Hombre
  - Jdc
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Gestion de la couleur

</div>

## Profil d'entrée

Un fichier raw contient une collection de relevés de lumière [capturés
et quantifiés](Demosaicing/fr#Introduction.md) par le capteur et
son électronique associée. Le rôle du profil d'entrée est d'attribuer
avec précision à chacun de ces relevés une couleur de l'espace
colorimétrique pour assurer une fidèle reproduction de toutes les
couleurs de la scène capturée. Le profil d'entrée est appliqué aux
données de l'image au début du
[pipeline](toolchain_pipeline/fr) de traitement de
RawTherapee et la plupart des outils traitent les données en aval dans
le pipeline.

Pour obtenir des informations détaillées voir :

- <https://www.ludd.ltu.se/~torger/dcamprof.html>
- <https://ninedegreesbelow.com/photography/articles.html#profile-digital-camera>
- [How to create DCP color
  profiles/fr](How_to_create_DCP_color_profiles/fr.md)

### Sans profil

Aucun profil de couleur d'entrée ne sera appliqué. La matrice de
couleurs sera composée de "1" le long de la diagonale et de "0" partout
ailleurs.

- Les fichiers raw utiliseront les couleurs RVB natives de l'appareil
  photo. Ne seront effectués que le dématriçage et la balance des
  blancs.

<!-- -->

- Lee fichiers non-raw seront affichés sans aucun profil d'entrée
  intégré d'appliqué, y compris sans correction gamma, ce qui signifie
  qu'ils auront un aspect lumineux.

Cette option n'est généralement utilisée qu'à des fins d'enseignement ou
scientifiques. Par exemple si l'appareil photo a enregistré des couleurs
bien en dehors des gamuts conventionnels, ne pas utiliser de profil
d'entrée garantit qu'aucun écrêtage ne se produit.

### Celui de l'appareil photo

RawTherapee recherche la matrice de couleurs dans trois endroits :

- Dans le code dcraw qui est intégré dans RawTherapee,
- Dans le fichier raw lui-même,
- Sur votre système, dans un fichier texte appelé `camconst.json` qui
  est installé avec RawTherapee.

Les informations sont collectées depuis ces trois places et les données
de `camconst.json` sont prioritaires sur les autres sources. Il y a une
exception concernant la [matrice de couleur
d'entrée](Color_Management/fr#Input_Profile.md) en ce sens que
si le fichier raw est en format DNG et que la métadonnée Exif `Software`
(`0x0131`) ne commence pas par la chaîne de caractères "Adobe DNG
Converter" et que le fichier contient bien une balise `ColorMatrix2`,
alors la valeur de cette balise est priorisée.

Une *matrice de couleur* est une matrice 3x3 de valeurs constantes qui
est multipliée par les couleurs RVB natives de l'appareil photo, pour
les convertir en couleurs aussi fidèles que possible. Une matrice de
couleurs fonctionne mieux (c'est à dire fournit des couleurs plus
précises) lorsque la balance des blancs est proche de ce pourquoi la
matrice a été calibrée. La matrice "standard de l'appareil photo" est
calibrée pour [D65](https://en.wikipedia.org/wiki/Illuminant_D65), c'est
à dire 6500K. Ne pas s'inquiéter si la balance des blancs en est assez
éloignée, les couleurs seront tout de même assez précises.

Pour les applications n'exigeant pas des couleurs les plus précises et
les mieux ajustées, tel qu'une photo de paysage, la matrice de couleur
donnera de bons résultats. Un avantage du traitement par la matrice de
couleur, par opposition aux conversions DCP et ICC basées sur des tables
de correspondance, est qu'il est purement linéaire, c'est à dire qu'une
couleur sombre et une claire de même teinte et saturation sont traduites
de la même façon. Cela le rend robuste et il sera sûrement le meilleur
choix si vous exportez les images pour traitement dans une application
HDR ou autre alors qu'une réponse linéaire et prévisible de la couleur
est requise.

### Sél. auto du profil de l'APN

Utilise un profil d'entrée DCP ou ICC. Les profils DCP sont priorisés.
Ils peuvent fournir des couleurs plus précises que la matrice standard.

Ces profils sont méticuleusement créés par nous, en utilisant des photos
de cibles couleurs soumises par les utilisateurs. si vous avez accès à
une cible couleur et que nous n'avons pas encore de profil DCP double
illuminant pour votre appareil photo (voir
[1](https://github.com/Beep6581/RawTherapee/tree/dev/rtdata/dcpprofiles)),
alors soumettez nous les photos demandées afin que nous puissions
améliorer la précision de couleur pour votre modèle d'appareil photo.
Vous trouverez des instructions dans l'article intitulé "[Comment créer
des profils de couleur
DCP](How_to_create_DCP_color_profiles/fr.md)".

Si aucun profil DCP ou ICC n'est disponible pour votre appareil photo,
RawTherapee reviendra à la matrice de couleur standard de l'appareil
pĥoto.

Les profils de l'appareil photo fonctionnent dans le domaine normal, du
noir jusqu'au dépassement hors domaine. Si vous validez la
reconstruction des hautes lumières, des données nouvelles sont ajoutées
au-delà du niveau hors domaine et si vous les amenez dans l'espace
colorimétrique visible (avec une exposition négative par exemple), ce
domaine ne sera pas naturellement couvert par le profil. Cependant,
RawTherapee étendra linéairement le profil pour couvrir aussi ce
domaine, ces couleurs là obtiendront la même correction que les couleurs
les plus lumineuses de la même teinte et saturation du domaine normal.

### Personnel

Spécifie un profil d'entrée d'appareil photo personnalisé DCP ou ICC.

Si RawTherapee n'a pas de profil DCP pour votre modèle d'appareil photo
et que vous n'avez pas accès à une cible couleur, vous pouvez obtenir un
profil auprès de Adobe DNG Converter. Voir l'article "[Comment obtenir
des profils LCP et DCP](How_to_get_LCP_and_DCP_profiles/fr.md)"
pour apprendre comment procéder.

DCP est un format spécialement conçu pour les profils d'appareil photo
et RawTherapee supporte en principe les plus récents standards DNG (ce
qui englobe les DCP), ainsi, vous pouvez par exemple utiliser tous ceux
fournis par le convertisseur DNG d'Adobe. D'un autre côté, les profils
ICC sont plus délicats. Les profils ICC sont utilisés pour une multitude
d'usages (imprimantes, écrans, etc.) et puisqu'ils ne sont pas conçus
spécifiquement pour le profilage d'appareils photo, les divers
revendeurs ont choisi différentes approches pour leurs profils ICC. En
pratique cela signifie que l'image d'entrée doit être pré-traitée d'une
façon spécifique pour que le profil fonctionne. Le profil lui-même
manque d'informations sur la manière de réaliser ce pré-traitement, ce
qui signifie que si vous utilisez un profil fourni par un tiers,
RawTherapee peut ne pas faire le pré-traitement attendu; les résultats
seront variables.

### DCP

#### DCP Illuminant

Certains profils de Rawtherapee ont un mode d'éclairage unique (Lumière
du jour/D50), alors que d'autres ont un double mode d'éclairage
(Daylight/D50 et Tungsten/StdA). Si un profil à double mode d'éclairage
est chargé, le paramètre "DCP Illuminant" est validé et vous pouvez
choisir lequel doit être pris en compte. Le standard actuel DCP (partie
du standard DNG) ne permet pas ce choix, mais à la place une
interpolation entre les deux illuminants est calculée sur la base de la
balance des blancs choisie (il n'y aura interpolation que si la balance
des blancs se situe entre les deux illuminants, sinon le plus près est
choisi). Ce mode "interpolé" est la configuration par défaut de "DCP
Illuminant" et pour tout usage habituel vous n'avez pas besoin de le
changer.

Vous pouvez cependant choisir de baser le rendu des couleurs sur un des
illuminants spécifiques. dans certains cas cela peut produire des
couleurs plus agréables. Cela peut aussi être intéressant à des fins de
diagnostic pour constater l'importance de la différence du rendu de
couleurs entre les illuminants, mais comme déjà dit, pour un usage
ordinaire, ce paramètre ne devrait pas être modifié.

#### Courbe tonale du profil DCP

Certains DCP fournis par des tiers contiennent une courbe tonale qui
pourrait être utilisée pour ajouter du contraste et de la luminosité
afin de simuler un aspect de film. Ceci est principalement utilisé dans
les profils simulant les réglages du fabricant de l'APN. La case à
cocher Courbe tonale sera désactivée pour les profils qui ne contiennent
pas de courbe tonale.

Le mode de courbe utilisé par la courbe tonale du DCP est le même que le
mode "[Similaire Film](exposure/fr#similaire_film)" de
l'outil Exposition, ce qui fait que vous pouvez reproduire l'effet
obtenu en utilisant les courbes tonales de l'outil Exposition dans le
mode Similaire Film. Lorsque le contraste est appliqué avec une courbe
similaire film l’apparence des couleurs change et la saturation globale
est augmentée, sauf pour les couleurs lumineuses qui sont dé-saturées à
la place. Certains profils qui possèdent des courbes intégrées sont
pré-corrigés pour tenir compte de ce changement de l'apparence des
couleurs et ne produira donc pas l'aspect attendu sans que la courbe
soit appliquée. La plupart cependant donnent de bons résultats sans
appliquer la courbe tonale surtout si vous ajoutez vous-même une courbe
similaire parmi les courbes de l'outil Exposition, mais si vous désirez
voir exactement ce que le concepteur du profil a souhaité obtenir vous
devriez activer la courbe tonale.

Alors que le profil couleur d'entrée est appliqué aux premières étapes
de la [Succession des outils dans le
pipeline](Toolchain_Pipeline/fr.md), la courbe tonale DCP est
appliquée plus tard dans le pipeline quelque part après 'outil
Exposition.

Si le profil DCP comporte un droit d'auteur mentionnant "Adobe Systems",
peu importe qu'il contienne une courbe tonale ou pas, RawTherapee créera
automatiquement une courbe tonale similaire à la courbe Adobe Camera
Raw. La raison de cela est qu'ainsi l'utilisation du DCP dans
RawTherapee peu correspondre aux résultats obtenus en utilisant ce DCP
dans Lightroom. C'est pourquoi la case à cocher "Courbe tonale" n'est
pas grisée lorsqu'on utilise un profil DCP qui ne contient pas de courbe
tonale, tant qu'il comporte la mention du droit d'auteur telle que
décrite.

#### Table de base

Cela active la table de correspondance "HueSatMap" du DCP qui est
utilisée pour ajouter des corrections non linéaires sur la matrice de
base. C'est un paramètre pour utilisateur avancé et à moins que vous ne
désiriez que le pur résultat matriciel, laissez le activé. Il est grisé
si le profil embarqué n'a pas de table HueSatMap.

#### Table de correspondance

Cela active la table de correspondance "LookTable" du DCP qui est
utilisée pour ajouter un aspect subjectif généralement accompagné d'une
courbe tonale intégrée. C'est à dire que si vous désactivez la table de
correspondance et la courbe du DCP, vous risquez d'obtenir un profil
"colorimétrique" neutre, si le DCP a été conçu de cette manière, ce qui
n'est pas toujours le cas (si le DCP possède à la fois une table de
correspondance et une table de base il est probable que ce soit le cas,
mais s'il ne possède qu'une table de correspondance il ne fonctionnera
probablement pas bien si elle est désactivée). La désactivation
d'éléments individuels du DCP est considérée comme paramétrages
d'utilisateur avancé, vous devriez normalement les laisser activés.

#### Exposition de base

Le DCP peut indiquer un décalage d'exposition qui correspond à un
décalage du curseur d'exposition. l'objectif de cela est typiquement de
rendre la luminosité de l'image équivalente à la luminosité des propres
JPEG de l'appareil photo, ce qui peut être utile si vous prenez des vues
en exposition automatique. Actuellement ce décalage est appliqué "sous
la surface" vous ne le voyez donc pas sur le curseur d'exposition.

Notez que si vous utilisez des profils propriétaires d'Adobe, ceux-ci
considèrent que la balise "baseline exposure" (exposition de référence)
du DNG est aussi appliquée (le décalage du profil est ajouté au total).
Actuellement il n'y a pas de support pour la balise du DNG, vous devez
donc la trouver par vous-même (en utilisant exiftool par exemple) et
ensuite entrer ce décalage avec le curseur d'exposition si vous voulez
obtenir exactement la même luminosité qu'avec Camera Raw d'Adobe.

### Notes pratiques

#### Support de DCP tiers

Un profil DNG d'appareil photo, DCP, est le format de profil préféré
pour RawTherapee. Tous les éléments de la spécification DNG 1.4 sont
supportés, à l'exception de la balise du rendu du noir (voir
ci-dessous). Un DCP peut être un profil purement matriciel, il peut
avoir un LUT (Look Up Table = Table de Correspondance) (typiquement
2.5D) pour améliorer la précision colorimétrique, et enfin il peut avoir
une courbe intégrée et finir avec une "table de correspondance" séparée.
Il peut aussi ajouter un décalage d'exposition. Tous ces éléments
peuvent être activés/désactivés en cochant des cases. Cependant, vous
devez être conscient qu'un profil ne peut produire les couleurs les plus
précises que si tous les éléments qui le constituent sont activés. Par
exemple, la courbe tonale elle-même change l'apparence des couleurs,
donc si vous désactivez une courbe tonale intégrée pour obtenir un
profil linéaire, vous ne pouvez espérer obtenir des couleurs absolument
fidèles. Néanmoins, bien des photographes préfèrent une apparance
esthétiquement plaisante à une précision absolue, donc cela ne devrait
pas être un problème à moins d'une nécessité cruciale de fidélité des
couleurs.

Les profils tiers typiques sont fournis par Adobe Camera Raw /
Lightroom, et RawTherapee les supporte. Beaucoup de profils Adobe sont
dépourvus de courbe tonale, mais dans le monde d'Adobe, cela ne signifie
pas qu'aucune courbe tonale ne doit être appliquée mais qu'il faut
appliquer la courbe d'Adobe par défaut. Par conséquent, RawTherapee va
identifier les profils d'Adobe (à partir du texte de copyright) et y
ajouter la courbe par défaut (activable/désactivable depuis la case à
cocher de la courbe tonale).

DNG converter d'Adobe peut ajouter une "exposition de référence" au
fichier DNG. Les DCP d'Adobe sont conçus pour travailler avec cette
exposition de référence et donc de produire une sortie par défaut qui
possède à peu près les mêmes luminosité et contraste que les propres
JPEG de l'appareil photo. RawTherapee peut honorer cette exposition de
référence si le DCP en contient une.

Le format DCP possède aussi une balise du rendu du noir. Cela indique si
le convertisseur raw doit procéder ou pas à une soustraction
"automatique" du noir. RawTherapee ignore cette balise, vous pouvez
réaliser une soustraction manuelle du noir grâce à l'outil [Points noirs
raw](Raw_Black_Points/fr.md) ou avec le curseur
[noir](exposure/fr#noir) de l'outil Exposition. Un grand
nombre de profils d'Adobe indiquent la soustraction automatique de noir
et Adobe Camera Raw / Lightroom le font, dans ces cas RawTherapee aura
un rendu avec un contraste un peu plus faible et des ombres un peu plus
claires.

#### Support de ICC tiers

RawTherapee possède un support spécifique pour les profils ICC fournis
avec Capture One et Nikon NX2, ainsi ceux là devraient fonctionner
correctement. Ce n'est cependant pas le cas pour les profils ICC plus
anciens (typiquement les images deviennent très foncées avec les profils
ICC non supportés).

Certains profils ICC appliquent une courbe tonal et désaturent les
hautes lumières brillantes pour un aspect plus proche du film. Ces
profils peuvent ne pas fonctionner correctement avec une [Reconstruction
des hautes
lumières](Exposure/fr#Reconstruction_des_hautes_lumières.md). Si
vous voyez un changement de contraste important lors de l'application du
profil ICC, celui-ci a appliqué une courbe tonale et vous ne devriez
donc pas l'utiliser en même temps que [Reconstruction des hautes
lumières](Exposure/fr#Reconstruction_des_hautes_lumières.md).

A la différence des profils DCP, le traitement des profils ICC peut
occasionner l'écrêtage des couleurs extrêmement saturées pendant la
conversion. En pratique ceci est rarement, sinon jamais un problème,
mais néanmoins DCP devrait être le choix prioritaire s'il est
disponible.

Note concernant l'utilisation des profils ICC Capture One : RawTherapee
applique le profil ICC avant le réglage de l'exposition dans l'intention
que le profil de l'appareil photo ne soit utilisé que pour rendre
l'appareil plus précis, pas pour appliquer un effet (vous concevez
l'effet en utilisant l'outil approprié). Les profils ICC de Phase One
possèdent néanmoins un aspect subjectif, ce qui signifie qu'ils
contiennent typiquement des "déformations de teintes", par exemple la
saturation est accrue un peu plus dans les ombres. Cela signifie que si
vous avez une photo sous exposée et que vous l'avez poussée de quelques
diaphragmes, ces déformations de teintes ont été appliquées sur l'image
sombre, avant le réglage de l'exposition, et seront ainsi au mauvais
endroits après avoir poussé l'image, vous n'avez pas le même résultat
qu'avec Capture One de Phase One. Cependant, il est recommandé d'avoir
une exposition correcte au sortir de l'appareil photo pour utiliser les
profils ICC de Phase One. Vous devriez aussi appliquer une courbe
[similaire Film](exposure/fr#similaire_film) RVB correcte,
car ces profils ICC sont conçus pour être utilisés avec.

Nous sommes conscients que les ICC des LUT devraient être appliqués
après l’exposition (exactement comme les DCP Looktables), et cela
devrait mieux supporter par exemple les profils Capture One. Cela sera
résolu dans une future version.

### Sauver Image de Référence

En cliquant sur le bouton "Sauver Image de Référence", vous enregistrez
l'image TIFF linéaire avant l'application du profil d'entrée. Ce fichier
peut-être ensuite utilisé pour le profilage, c'est à dire pour créer un
profil d'entrée d'appareil photo. Vous pouvez utiliser le programme
open-source ArgyllCMS pour réaliser des profils ICC, et DCamProf pour
créer des profils ICC ou DCP.

Les recadrages, redimensionnements et transformations (rotation)
s'appliquent, vous permettant de rendre l'image de sortie plus facile à
exploiter par le logiciel qui la reçoit. ArgyllCMS est très exigent par
exemple et exige que la scible du test soit seule visible dans l'image.

Vous avez aussi le choix d'exporter avec ou sans l'application de la
balance des blancs. Pour les profils ICC vous devriez exporter avec la
balance des blancs, mais si vous désirez réaliser un profil DNG ou une
matrice de couleur de type DCRAW, vous devriez exporter sans appliquer
la balance des blancs.

## Profil de travail

Le profil de travail par défaut est ProPhoto et ne doit pas être modifié
pour un usage habituel.

Le profil de travail spécifie l'espace colorimétrique de travail, qui
est l'espace colorimétrique utilisé pour les calculs internes, par
exemple le calcul de la saturation, la brillance/contraste RVB et les
ajustements de la courbe tonale, la chrominance, etc.

Quand RawTherapee était basé sur les nombres entiers il était recommandé
de ne pas utiliser un espace colorimétrique plus étendu que l'absolue
nécessité pour obtenir une meilleure précision des calculs. Cependant,
RawTherapee a opté en 2011 pour le calcul en virgule flottante et depuis
la version 4.0.12 le profil de travail par défaut est ProPhoto qui
présente un gamut très étendu.

Le choix du profil de travail influence les effets de la courbe dans
tous les modes sauf le mode perceptuel, dans ce mode, changer de profil
de travail n'affectera pas les effets de la courbe. Si vous avez des
difficultés pour faire tenir les couleurs à l'intérieur du gamut de
sortie, vous pouvez tenter de changer de profil de travail alors que
vous utilisez les courbes, et ce dans tout mode sauf le mode perceptuel.

Notez que le profil de travail ne spécifiera que les couleurs primaires
rouge, verte et bleue, gamma ne changera pas car le pipeline de
traitement de RawTherapee est en virgule flottante sans encodage du
gamma (c'est à dire gamma = 1.0). Certains outils (comme les courbes et
les histogramme) continueront à s'afficher avec un gamma (généralement
un gamma sRGB) qui est codé en dur pour l'outil et reste le même quelque
soit le profil de travail.

### Ajout de profils de travail personnalisés

RawTherapee 5.5 autorise la spécification de profils de travail
personnalisés grâce à un fichier
[JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation). Le
fichier doit s'appeler `workingspaces.json` et être placé dans :

- Le dossier des profils ICC, comme indiqué dans [Préférences \> Gestion
  des couleurs \> Dossier des profils
  ICC](Preferences/fr#L.27onglet_Gestion_des_couleurs.md),
- Ou dans le dossier des profils ICC propre à RawTherapee :
  - Windows: `<dossier d'installation de rt>\iccprofiles`
  - Linux :
    - Si installé au moyen du gestionnaire de paquets ou bien compilé
      par vous-même avec l'option `BUILD_BUNDLE=OFF` :
      `/usr/share/rawtherapee/iccprofiles`
    - Si compilé par vous-même avec l'option `BUILD_BUNDLE=ON` :
      `<dossier d'installation de rt>/iccprofiles`
  - macOS : `/library/ColorSync/Profiles/Displays`

Le format de `workingspaces.json` est comme suit :

    {"working_spaces": [
        {
            "name" : "ACES",
            "file" : "/path/to/ACES.icc"
        },
        {
            "name" : "ACEScg",
            "matrix" : [0.7184354, 0.16578523, 0.09882643, 0.29728935, 0.66958117, 0.03571544, -0.00647622, 0.01469771, 0.66732561]
        }
    ]}

Si "matrix" est présent, "file" est ignoré. Si "file" est seul présent,
la matrice est extraite du profil ICC. Pour cela, RawTherapee ne regarde
que les colonnes R, V et B de la matrice et le point blanc défini dans
le profil. L'adaptation Bradford est utilisée pour convertir la matrice
en D50. Tout le reste dans le profil (LUT, TRC, etc.) est ignoré.

Il est de la responsabilité de l'utilisateur se s'assurer que le profil
est adapté pour une utilisation dans un espace de travail.

## Profils abstraits

3 mars 2024

### Qu'est-ce c'est un « abstract profile » ?

- Nous pouvons reprendre la définition de « ICC International color
  consortium » : Les profils abstraits vous permettent de réaliser des
  effets d'image personnalisés, comme l'application d'un "look"
  particulier à une série d'images. Un tel profil vous permet de définir
  des valeurs CIELAB (ou CIEXYZ) en entrée et en sortie. Ainsi, vous
  pouvez définir de manière algorithmique les changements de couleur de
  votre choix et produire la LUT qui y parvient. Un petit nombre
  d'applications de gestion des couleurs prennent en charge la création
  et/ou l'utilisation de profils abstraits.
- Dans le cas de Rawtherapee ceci revient à utiliser les « virtual
  profiles » de LCMS, qui permettent d'agir sur les données avec les
  mêmes algorithmes et principes que les « Profils d'entrée » ou les
  « profils de sortie », c'est à dire en agissant sur une ou plusieurs
  des 3 composantes d'un profil ICC : Courbe de réponse tonale – TRC,
  illuminant (point blanc) – Primaires ;
- est-ce que un "abstract profile" est de la gestion des couleurs ?
  Vaste débat.. mais largement plus que le profil de travail (working
  profile) qui n'a rien d'un profil puisque c'est une simple
  transformation de code C++, convertissant des données RGB en XYZ. Pour
  revenir à l'abstract profil, en termes de définition de "ICC
  international color consortium", ainsi que de LCMS (virtual profile)
  la réponse est évidemment oui.

### Le diagramme CIE xy

Le profil virtuel (LCMS) utilisé va modifier les données "x", "y" qui
sont une parmi d'autres des représentations possibles de la
colorimétrie. Cette représentation permet de voir facilement:

- les limites de la vue humaines en termes de fréquences visibles de
  380nm à 770nm

<figure>
<img src="/images/ciexy-color.jpg" title="ciexy-color.jpg" width="600" />
<figcaption>ciexy-color.jpg</figcaption>
</figure>

- une modélisation des espaces colorimétriques par leur représentations
  en "triangle" sur la base des primaires

<figure>
<img src="/images/ciexy-3space.jpg" title="ciexy-3space.jpg" width="600" />
<figcaption>ciexy-3space.jpg</figcaption>
</figure>

- la courbe de l'évolution du point blanc (une des bases de
  l'illuminant - D50 - D65 - Std A, )

<figure>
<img src="/images/ciexy-wp.jpg" title="ciexy-wp.jpg" width="600" />
<figcaption>ciexy-wp.jpg</figcaption>
</figure>

- A noter que cette représentation doit être interprétée avec
  précautions, car c'est une projection verticale du gamut. Une couleur
  qui est en dehors du triangle du gamut est obligatoirement hors-gamut,
  mais une couleur à l'intérieur du triangle peut être hors gamut, car
  cette projection ignore la composante luminance.

#### Quelques valeurs de "primaires"

- sRGB - Red x=0.64 y=0.33 - Green x=0.30 y=0.60 - Blue x=0.15 y=0.06
- Rec2020 - Red x=0.708 y=0.292 - Green x=0.17 y=0.797 - Blue x=0.131
  y=0.046
- ProPhoto - Red x=0.7347 y=0.2653 - Green x=0.1596 y=0.8404 - Blue
  x=0.0366 y=0.0001
- ACESp0 - Red x=0.7347 y=0.2653 - Green x=0 y=1.0 - Blue x=0.0001
  y=-0.077

Lorsque une des primaires se trouve en dehors des limites de la vision
humaine on parle de couleurs imaginaires.

### Utilisation des données du diagramme "CIE xy" par "Abstract profiles"

<img src="/images/cie-abstract_graph3.jpg" title="cie-abstract_graph3.jpg"
width="600" alt="cie-abstract_graph3.jpg" /> Vous pouvez agir comme vous
le souhaitez sur les 3 composantes du profil virtuel. La saisie d'écran
représente la configuration lorsqu'on souhaite améliorer la
"calibration" du profil d'entrée (Input profile).

- Dans cet exemple, le profil de travail (Working profile) est Prophoto
  qui n'a pas été modifié au niveau des primaires. Lorsque vous
  choisissez "Destination primaries: Custom" l'algorithme va choisir par
  défaut ce même profil de travail pour élaborer le profil virtuel
- si vous changez toujours dans "Destination primaries:" pour une valeur
  différente de celle de "Working profile" vous allez générer des effets
  spéciaux de type "Color Toning" ou "Channel Mixer"
- si vous changez "Illuminant:" D50, pour une autre valeur, soit vous
  cherchez à créer / amplifier des effets spéciaux, soit vous souhaitez
  adapter l'illuminant pour une usage spécifique.

Le diagramme CIExy est affiché avec les valeurs par défaut du working
profile - ou du choix que vous avez fait dans "Destination primaries":

- les 3 primaires - Rouge - Vert - Bleu
- le point blanc

Si, dans le menu "Destination primaries", vous changez

- pour "Adobe RGB" (ou un autre profil) les primaires et le point blanc
  de ce profil vont s'afficher sur le diagramme
- Custom (sliders)
  - les curseurs Red X, Y - Green X, Y, Blue X, Y seront actifs
  - la combobox "illuminant" sera active
  - les changements sont répercutés dans le diagramme CIE xy : l'action
    sur le diagramme ne permet pas de modifier les valeurs des primaires
    et de l'illuminant.
- Custom (CIE xy Diagram)
  - vous pouvez modifier les primaires avec la souris, les changement
    seront répercutés sur les curseurs Red, Green, Blue qui sont non
    modifiables avec les curseurs.
  - l'illuminant ne peut être modifié

Ce comportement est “normal”, mais pourquoi ? La raison est qu’on ne
modifie pas le “working profile”, mais les données qui ont déjà été
modifiées. Par soucis pédagogique examinons le fonctionnement de
ciecam02/16 en mode symétrique. Si la balance des blancs est par exemple
réglée sur 7500K et qu’elle correspond à la réalité de l’illuminant,
donc bien réglée, l’image apparaîtra avec des blancs jaunâtres et
globalement l’image tend à être avec une dominante rouge. L’adaptation
chromatique cat02/16 va permettre de refroidir l’image… et pour cela on
règle la température dans “Viewing conditions” à celle de la balance des
blancs - soit 7500K. La balance des blancs agit comme le working
profile, en amont, l’adaptation chromatique agit comme “abstract
profile”, en aval.

Note: le diagramme est donné à titre d'information - les limites sont
peu précises notamment vers les verts.

#### Soft radius & Local contrast

Cet ajustement - mettant en oeuvre un "Guided Filter", n'est à utiliser
que dans des cas rares, lorsque les primaires et/ou les illuminants ont
été profondément changés.

- les primaires et / ou l’illuminant ont été changé fortement pour
  accroître la saturation et changer les teintes, notamment en noir et
  blanc, cela peut conduire à des artefacts. Dans ce cas utiliser
  “Guided filter” comme adoucissant (avec les valeurs négatives du
  curseur), voire si on pousse le curseur au delà de -60, comme floutage
  général de l'image (blur).
- à l’inverse lorsque les primaires ont été “élargies” souvent au delà
  du spectre visible, l’image devient terne, peu colorée… Dans ce cas
  utiliser "Guided filter" (avec les valeurs positives du curseur) pour
  accroître le contraste local.

### Quelles données et profiles sont utilisés-modifiés

Les "Abstract profiles" (profils virtuels) implantés ici

- ne modifient pas le "working profile"
- ne modifient pas les "Input profile"
- ne modifient pas les "Output profiles"
- mais ils modifient des données (datas) comme le font n'importe quel
  algorithme de Rawtherapee. Les particularités:
  - l'abstract profile - qui correspond à un profil ICC virtuel de
    LCMS - agit comme un patch en fin de processus (juste avant Ciecam -
    et juste avant la conversion vers un profil écran ou un profil de
    sortie), agit sur les 3 composantes d'un profil ICC (Tone Response
    Curve, Illuminant (point blanc), Primaires). En fonction des choix
    et des réglages ont peut modifier l'image
    - en profondeur dans son apparence en agissant sur le répartition de
      la luminance et les couleurs - comme un "Channel Mixer" ou "Color
      Toning" auquel on aurait ajouté une dimension supplémentaire.
    - uniquement sur la répartition de la luminance via la TRC - soit
      pour changer l'aspect par défaut qui dans Rawtherapee est une TRC
      sRGB - soit pour agir comme Shadows/Highlights
    - pour modifier / affiner les résultats du profil d'entrée (Input
      profile) à l'aide d'une charte de couleurs (Colorchecher24 ou
      autre), soit avec le même illuminant qui a servi lors de
      l'élaboration du profil d'entrée, soit avec un autre illuminant -
      dans le cas l'utilisation conjointe de Ciecam sera nécessaire.

### Trois usages principaux, associés ou non à Ciecam :

- TRC : ajuster le gamma et la pente à des fins diverses. a) modifier le
  rendu de l'image qui par défaut est g=2.4 s=12.92 ; b) relever les
  ombres et agir sur les tons clairs tout en préservant la colorimétrie
  et le gamut.
- Illuminant (point blanc) : a) ajuster le gamut du " profil de travail
  " pour l'adapter aux conditions de prise de vue. Dans ce cas, on
  cherchera à privilégier la colorimétrie. Si une image est prise à
  4000K, en sRGB (qui est D65), le gamut peut ne pas être adapté.
  L'action conjointe de " l'illuminant " et du Ciecam (symétrique) doit
  permettre de mettre en œuvre une adaptation chromatique de qualité
  ; b) utilisée conjointement avec les modifications primaires
  ci-dessous.
- Primaires : c'est ici que la notion de « Profils abstraits » a tout
  son sens. Plusieurs possibilités sont offertes : a) Se servir de ce
  module comme « Channel mixer » afin d'aboutir si on le souhaite à des
  effets spéciaux proches de ceux de « Color Toning » en association ou
  non avec Ciecam ; b) Plus simplement restituer les couleurs
  (saturation) d'une image, en assurant dans la majorité des cas la
  préservation de l'équilibre (balance) des couleurs; c) S'en servir
  pour modifier / affiner le résultat du profil d'entrée (Input profile)
  afin d'assurer une meilleure colorimétrie (calibration).

### Où est-il situé dans le processus de Rawtherapee ?

Il est situé en fin de processus - juste avant Ciecam - et permet ainsi
soit:

- d'appliquer des effets spéciaux sensiblement au "même niveau" que
  "Color toning - Color corrections regions"
- restituer les couleurs (saturation) d'une image, en assurant dans la
  majorité des cas la préservation de l'équilibre (balance) des
  couleurs;
- d'apporter une correction colorimétrique (calibration) en fin de
  processus - tenant compte des modifications apportées en amont à
  l'image - juste avant les profils de sortie.

Cette position permet également d'éviter d'introduire des
non-linéarités.

### TRC - Courbe de réponse tonale

Cette fonctionnalité permet de faire varier le gamma et la pente sur la
base du "working profile" - elle ne modifie pas ce profil, mais prend en
compte ses caractéristiques. Elle s'applique à la fin du processus,
juste avant Ciecam. On la retrouve dans d'autres logiciels comme UFRaw
©, mais aussi incorporé aux profils de sortie...

Elle vise plusieurs objectifs :

- Pédagogique : vous pouvez ainsi voir directement à l'écran les
  importantes différences induites par les changements de gamma (g) et
  de pente (s) par exemple:
  - un gamma standard = 1.8 - utilisé en Output profile par Prophoto
  - un gamma standard = 2.2 - utilisé en Output profile par AdobeRGB
  - une TRC - "BT709" qui correspond à gamma =2.22 et pente (slope) =
    4.5 - une partie linéaire "jusque 4.5", puis une partie
    logarithmique avec g=2.22. Cet ensemble donne pour les moyennes et
    hautes lumières le même résultat que "gamma standard = 1.8", mais
    apporte un bien meilleur rendu des ombres, en supprimant
    l'impression de grisaille.
  - une TRC - "sRGB" qui correspond à g=2.4 et s=12.92 - une partie
    linéaire "jusque 12.92", puis une partie logarithmique avec g=2.4.
    C'est le rendu habituel choisi par des nombreux logiciels dont par
    exemple Lightroom ©, ainsi que la sortie écran et output par défaut
    de Rawtherapee.
  - etc.

<!-- -->

- Exportation - activités particulières : vous pouvez décider de
  travailler avec un gamma linéaire, par exemple pour exporter vers un
  autre logiciel (pour impression, ou modifier avec Photoshop ou Gimp)
  et / ou voir directement les résultats.

<!-- -->

- Action sur Ombres et Lumières (Shadows - Highlights) : cette
  fonctionnalité ne remplace pas les autres modules de Rawtherapee comme
  par exemple "Shadows/Highlights", ou les courbes dans "Exposure",
  etc., mais elle les complète :
  - vous pouvez déboucher les ombres en agissant sur le curseur "Slope",
    des valeurs jusque 300 permettent une transformation importante de
    l'image dans les ombre.
  - vous pouvez agir sur les hautes et moyennes lumières en agissant sur
    le curseur "gamma", des valeurs jusque 15 sont disponibles
  - regardez l'évolution de l'histogramme

<!-- -->

- En complément de la calibration, pour ajuster la luminance des gris,
  lorsqu'on se sert par exemple d'une ColorChecker24

<!-- -->

- Notez que le curseur Slope n'est actif que pour des valeurs de Gamma
  \>1. En raison de l'algorithme utilisé pour générer la TRC, elle
  présente un comportement erratique lorsqu'elle est réglée sur
  certaines valeurs. Elle se comporte comme prévu lorsque 'Slope' est
  réglé sur zéro et pour des valeurs supérieures à 1, mais peut donner
  des résultats inattendus entre les deux.
  - lorsque "slope" est à "0", on obtient une courbe avec un "gamma
    seul", l'image a le rendu obtenu avec les profils de type "AdobeRGB
    2.2" ou "ProPhoto 1.8"
  - lorsque "Slope" atteint la valeur "1", l'action de Slope est maximum
    pour réduire l'effet de grisaille dans les ombres (en fait le
    système se comporte comme avec un gamma = 1). Celles-ci sont plus
    sombres, l'image plus contrastée, sans presque changer le rendu dans
    les moyennes et hautes lumières.
  - au fur et à mesure qu'on accroît "Slope", les ombres s'éclaircissent
    progressivement, en fonction aussi du gamma. Une valeur de "Slope"
    très élevée (50 ou plus) nécessite un gamma élevé pour "ouvrir" les
    possibilités.
  - il y a "correspondance" entre certaines parties des TRC. Par exemple
    une image ouverte avec "Adobe g=2.2" aura sensiblement les mêmes
    valeurs de luminance pour les tons moyens et les hautes lumières que
    celle ouverte avec "sRGB g=2.4 s=12.92". Par contre notez
    l'importante différences pour les ombres.

#### Différences avec une Tone-Curve classique

- comme évoqué précédemment, elle est située en fin de processus -
  évitant au maximum les non-linéarités, gage d'une meilleur qualité des
  résultats
- lorsqu'elles sont utilisées conjointement avec "Illuminant" ou
  "Primaires" elles garantissent une inscription dans le gamut et une
  meilleure colorimétrie. Cette maîtrise du gamut n'est pas garantie
  autrement - utilisation de la TRC isolée afin d'optimiser les temps de
  traitement, mais néanmoins est pertinente dans une très grande
  majorité de cas.
- la partie linéaire, souvent de faible valeur (s= 2..s=13) raccordée à
  une partie parabolique, est pratiquement impossible à réaliser avec
  une tone-curve
- elle constitue - dès qu'on active "Illuminant" (ne serait-ce que pour
  confirmer l'illuminant, par exemple D50 pour ProPhoto), ou
  "Primaires" - une partie d'un profil ICC virtuel qui peut être
  appliqué en fin de processus à une image ou une série d'images.

### Illuminant - point blanc

Par défaut l'illuminant est réglé sur la valeur correspondant au
"working profile", à titre d'exemple cela correspond à D50 pour
"ProPhoto", D65 pour "sRGB", D60 pour "ACESp1".

<img src="/images/ciexy-wp.jpg" title="ciexy-wp.jpg" width="600"
alt="ciexy-wp.jpg" /> Pourquoi le changer ? Plusieurs raisons peuvent
amener à vouloir changer cette valeur :

- pour volontairement changer les couleurs comme on le ferait avec
  "Channel Mixer" ou "Color Toning". Si on examine le diagramme "CIE
  xy", on voit que lorsqu'on change l'illuminant le point blanc se
  déplace
  - vers la zone des rouges si la température de l'illuminant baisse
  - vers la zone des bleus si la température de l'illuminant augmente
  - donc avec cet usage on modifie son équilibre rouge / bleu pour
    l'essentiel

<!-- -->

- pour "patcher" le "working profile" et adapter la colorimétrie à des
  images spécifiques. Par exemple imaginons qu'on ait pris des photos
  vers la tombée du jour et que le "working profile" soit "Prophoto" -
  illuminant D50.
  - soit vous voulez accentuer les effets d’un coucher de soleil et
    rendre l’image plus chaude encore. dans ce cas choisissez un “white
    point” avec une température plus basse que celle du Working profile,
    par exemple D41 si le Working profile est “Prophoto D50”
  - soit vous souhaitez optimiser le gamut pour obtenir une meilleure
    prise en compte des données dans des conditions de prise de vue du
    coucher de soleil. Dans ce cas choisissez un “white point” avec une
    température plus élevée que celle du “Working profile”, par exemple
    si ce “working profile” est “Prophoto D50”, et que la prise de vue
    est vers 4000K, alors choisissez un Illuminant vers D60 ou D65.
    Attention la fonction “white point” n’est pas linéaire, l’approche
    ne peut être qu’approximative."
  - le profil virtuel va "patcher" les données en changeant les valeurs
    XYZ de la matrice de conversion RGB-XYZ les adaptant mieux aux
    données de l'image, évitant ainsi les valeurs hors-gamut

### Primaires

Par défaut les primaires sont réglées sur les valeurs de celles du
"Working profile". Pourquoi les changer ?

- pour créer des effets spéciaux de type "Channel Mixer" ou "Color
  Toning" - à noter qu'un Channel Mixer de type "primaires" est un peu
  plus intuitif qu'un Channel Mixer RGB dans le sens où l'action sur une
  primaire agit principalement sur cette couleur - , dans ce cas vous
  avez 2 possibilités:
  - choisir dans "Destination primaries", des primaires différentes de
    celles du "Working profile". L'examen du diagramme "CIE xy" montre
    que le triangle est déplacé globalement - bien sûr en fonction du
    couple "Working profile" - "Destination primaires" introduisant un
    écart de chaque primaires constant quelque soit les images
    auxquelles on applique ce "patch". Bien sûr les résultats seront
    différents d'une image à l'autre, car la répartition des couleurs
    est différente, mais le "patch" sera constant. En principe, dans ce
    cas, l'équilibre des couleurs est respecté. Si vous choisissez un
    "Destination primaries", plus grand que le "working profile" vous
    allez désaturer l'image. A l'inverse, si vous choisissez un
    "Destination primaries" plus petit que le "working profiles" vous
    allez accroître la saturation.
  - choisir dans "Destination primaries" des primaires différentes / ou
    identiques à celles du "Working profile", en choisissant ensuite
    "Custom". Dans ce cas vous allez vous même modifier l'emplacement
    des 3 sommets du triangle de "Destination primaries" ouvrant des
    possibilités quasiment illimitées

<!-- -->

- pour modifier/affiner les images afin qu'elles soient le plus en
  conformité avec la prise de vue - réduction des deltaE.
  - l'utilisation avec une charte (ColorChecker24 ...) est quasi
    obligatoire
  - Ciecam devra être utilisé si on souhaite que la profil d'entrée
    puisse être utilisé avec pertinence avec un autre illuminant que
    celui ayant servi à l'élaborer

### Example TRC & Primaires

Cet exemple permet de comprendre 3 changement simples:

1.  TRC : a) action substantielle sur les ombres avec le curseur
    Slope; b) action modérée sur les lumières avec le curseur Gamma.
2.  Destination primaries :accroître la saturation générale de l'image
    en choisissant Adobe RGB comme 'Destination Primaries', avec
    'Working Profile' inchangé Prophoto.
3.  Custom CIExy diagram : modifier l'équilibre de l'image.

Bien sûr, vous pouvez modifier finement saturation, chromaticité,
colorfullness, brightness et lightness avec les modules Ciecam
'Apparence le couleur (menu principal)' ou 'Ajustements locaux -
Apparence couleurs (Cam16 & JzCzHz)'

Fichier raw (Brian Poindexter - Creative Common Attribution-share Alike
4.0):
[2](https://drive.google.com/file/d/16qz6PPfkHyeNEJ_sPPNM8xPqr17EWGzu/view?usp=share_link)

#### Image originale (Rawtherapee - default)

<figure>
<img src="/images/flowerT.jpg" title="flowerT.jpg" width="600" />
<figcaption>flowerT.jpg</figcaption>
</figure>

#### Appliquer une TRC

<img src="/images/flowerT-trc.jpg" title="flowerT-trc.jpg" width="600"
alt="flowerT-trc.jpg" /> Examinez la partie verte de l'image:

- Plus vous agissez sur Slope, plus la partie sombre va s'éclaircir
- Plus vous agissez sur Gamma, plus la partie claire va d'éclaircir.

#### Changer les primaires

Adobe RGB remplace Prophoto (Working profile), réglage par défaut de
Rawtherapee
<img src="/images/flowerT-primaries.jpg" title="flowerT-primaries.jpg"
width="600" alt="flowerT-primaries.jpg" /> Essayez de changer
'Destination primaries - Adobe RGB' par une autre valeur, par exemple
Rec2020 ou ACESp0

#### Changer les primaires Custom CIExy diagram

<img src="/images/flowerT-prim-CIExydiag.jpg" title="flowerT-prim-CIExydiag.jpg"
width="600" alt="flowerT-prim-CIExydiag.jpg" /> Le changement concerne
uniquement le point rouge (origine Adobe RGB): observez l'image et le
changement des valeurs des primaires Rx, Ry

### Noir et Blanc

Un cas particulier d'effets spéciaux est la possibilité d'utiliser
"Abstract profile" pour générer des images noir et blanc. La combinaison
des 3 composantes de "Abstract profile" permet d'obtenir des effets
saisissants en noir et blanc, notamment par l'usage:

- d'un point blanc décalé par rapport aux conditions habituelles, par
  exemple "Tungsten 2000K".
- de primaires elles aussi fortement décalées par rapport au "Working
  profile", notamment en les concentrant loin des 3 primaires de départ.
- d'une TRC changeant la répartition des gris, par exemple une TRC
  g=2.793 s=4.26

Vous pouvez associer le module Ciecam02/16, par exemple les réglages
"Temperature" et "Teinte" dans "Viewing Conditions" pour obtenir des
virages colorés (Sepia, ...)

Les réglages donnés dans l'exemple sont à titre pédagogique. Bien sûr
vous pouvez (devez) utiliser des réglages plus proches des valeurs du
"working profile".

<div>

<img src="/images/ciexy-bw1.jpg" title="ciexy-bw1.jpg" width="600"
alt="ciexy-bw1.jpg" /> Fichier Raw:
[3](https://drive.google.com/file/d/1azCxu1midw6dcuN7SbvbAiJH4pxX5BTA/view?usp=sharing)

</ul>
</div>

### Comment fonctionne l'algorithme "Primaires et Point Blanc"

Quand vous changez les "primaires" et le "point blanc", une nouvelle
matrice "XYZ=WRGB" est appliquée aux données. Cette matrice est fabriqué
selon le processus simplifié ci-après:

- partir avec les valeurs chromatqiues le rouge, vert, bleu de chaque
  primaire (cela correspondaux valeurs xyY avec Y=1),
- convertir les valeurs xyY en XYZ pour obtenir la première matrice XYZ:
  \[M1\],
- inverser cette matrice : \[IM1\].
- uutiliser \[IM1\] et la point blanc source (e.g. D45, D55, D60, StdA
  etc.), en déduire les valeurs Sr, Sg & Sb.
- produire une nouvelle matrice \[Mat_xyz\] en multipliant Sr, Sg, Sb
  avec les données originales XYZ \[M1\].

Bradford transformation

- Preambule: Bradford est une adaptation chromatique, basée sur le
  concept de "cones de réponse". Il va adapter les données XYZ calculée
  avec un illuminant D50, en des valeurs XYZ pour un autre illuminant
  tels D41, D55, etc. Il utilise le concept de "RGB source" (RGB s) et
  "RGB destination" (RGB d), pour calculer les valeurs du "cone de
  réponse. C'et similaire au concept LMS (long, medium, short), qui
  représente un espace colorimétrique qui représent les réponses des 3
  types de cones de la vision humaine.
- calculer RGB s = Source White point \* \[M(Bradford)\]
- calculer RGB d = D50 White point \* \[M(Bradford)\]
- calculer the Cone _response (destination source) = RGB d / RGB s
- développer une nouvelle matrice \[Cone_matrix\] = Cone_response \*
  \[Inverse-M(Bradford)\]
- développer une nouvelle matrice \[Chromatic_adaptation\] =
  \[M(Bradford)\] \* \[Cone_matrix\]
- développer la matrice finale quui prend en compte le nouveau point
  blanc: \[Mat_xyz_bradford\] = \[Mat_xyz\] \* \[Chromatic_adaptation\]

[Bruce Lindbloom Chromatic adaptation for information - (légèrement
différent de l'implémentation
RT))](http://www.brucelindbloom.com/index.html?Eqn_ChromAdapt.html)

#### Afficher la Matrice XYZ-RGB - "Mat_xyz_bradford"

- Si vous lancez Rawtherapee depiis la console, et en options - verbose
  = true, la matrice de conversion XYZ vers RGB "Mat_xyz_bradford" sera
  affichée. Elle prend en compte "Destination primaries" et
  "Illuminant".
- Example avec "Destination primaries - Rec2020" et illuminant réglé à
  D80
  - Illuminant: D80
  - rX=0.661827 gX=0.178737 bX=0.123636
  - rY=0.274860 gY=0.678752 bY=0.046389
  - rZ=-0.00275 gZ=0.031042 bZ=0.796608

Note Importante:

- le point blanc source est seulement utilisé par le ICC profile (les
  données de la matrice XYZ-RGB). La modification en profondeur de
  l'image ne peut résulter de cette modification, elle est assurée par
  le processus de "color-management" (Balance des blancs, Ciecam,...)

### Exemple possible d'utilisation pour modifier / améliorer l'action du profil d'entrée

- basculer sur "Neutral"
- chargez l'image de la charte qui a servi à élaborer le profil d'entrée
  (Input profile), avec les réglages de la balance des blancs
  correspondants.
- choisissez le profile (Bundled profile...) que vous utilisez
  habituellement(defaut - Auto match curve - ISO Low) - sans autres
  réglages additionnels.
- choisissez "abstract profile" - et "Custom" par défaut le profil
  sélectionné sera le même que "Working profile" (ainsi que
  l'illuminant) - ne changez pas ces valeurs
- sélectionnez "Custom" dans "Destination primaries"
- les primaires du "working profiles" s'affichent, vous pouvez
  maintenant les modifier
- utilisez le "lockable color picker"
  - sélectionnez parmi les cellules : 2 ou 3 gris répartis entre les
    plus sombres et les plus clairs, 1 rouge (saturé), 1 vert (saturé),
    1 bleu (saturé)
  - les valeurs L\*a\*b\* de ces cellules (celles de la charte - valeurs
    de référence) vont devenir les objectifs à atteindre.
  - adaptez gamma (g) et slope (s) de telle manière que les 3 gris
    soient le plus proches des valeurs de référence
  - modifiez les valeurs "x" et "y" des primaires "rouge", "vert" et
    "bleu" de telle manière que les valeurs mesurées soient le plus
    proche des valeurs de référence
  - Agir si nécessaire sur "Preserves Pastel tones" : ce curseur permet
    d'éviter l'action sur les teintes très peu saturés (proches des tons
    neutres) et de réduire progressivement l'action sur les tons
    pastels.
  - sauvez le résultat.

Si vous souhaitez que votre profil (par exemple élaboré en D50) puisse
servir dans une autre plage de température. Il est nécessaire de prendre
en compte Cat16 dans Ciecam:

- choisissez dans "White balance" la nouvelle température - par exemple
  6000K
- sélectionnez "Color Appearance & Lightning (Ciecam02/16)
- sélectionnez: CAM Model \> CIECAM16
- sélectionnez CatO2/16 mode \> Automatic symmetric
- Ajustez la température dans "Viewing conditions" à celle de la balance
  des blancs (dans cet exemple 6000K)
- puis utilisez le même processus que précédemment.

Pour utiliser les résultats de ce profil virtuel pour d'autres images,
procédez comme suit:

- sur la vignette dans le "file browser" - cliquer droite - “Processing
  profile operations”, “Copy”…then “Paste partial” “Color management”.

Remarque: Bien sûr, les valeurs peuvent aussi être ajustées
empiriquement comme dans ART et Lightroom. Pour de petits écarts par
rapport aux primaires d'origine, on peut avoir une assez bonne
prévisibilité du résultat. Par contre, si nous faisons de gros
changements, les résultats seront plus variés.

### Plusieurs améliorations ont été apportées - mars 2024

Ces améliorations concernent :

- l'interface GUI;
- le nombre de primaires et illuminants;
- la possibilité d'agir sur la couleur dominante à partir du diagramme
  CIExy

<figure>
<img src="/images/cie-abstract_graph4.jpg" title="cie-abstract_graph4.jpg"
width="600" />
<figcaption>cie-abstract_graph4.jpg</figcaption>
</figure>

Vous pouvez retrouver la description de ces fonctionnalités dans "Local
Adjustments" - "Color Appearance (Cam16 & JzCzHz) [Local Adjustments -
Cam16 avec prétraitement
HDR](Local_Adjustments/fr#Cam16_-_avec_prétraitement_HDR_branch_lacam16n.md)

## Profil de sortie

Spécifie le profil de couleur de sortie, l'image sauvegardée sera
transformée dans cet espace colorimétrique et le profil sera intégré
dans les métadonnées. Les effets du profil de sortie sur l'image ne
peuvent être vus dans l'aperçu.

RawTherapee permet de spécifier des profils de classe périphérique d'
*entrée* (par ex le profil de votre boitier), d' *affichage* ou de
*sortie* (par ex imprimante) avec un espace colorimétrique RVB, car
RawTherapee n'enregistre que des images RVB. Les profils listés dans la
liste déroulante sont ceux qui sont livrés avec RawTherapee et ceux
enregistrés dans le répertoire défini dans Préférences \> [Gestion des
couleurs](Preferences/fr#L'onglet_Gestion_des_couleurs.md).

La fonctionnalité d'épreuvage écran est dédiée à la simulation du rendu
de l'imprimante. Elle vous permet de prévisualiser ce que donnera votre
image une fois imprimée, en supposant que vous utilisez un profil
d'imprimante qui simule correctement le couple imprimante et papier.
Pour une meilleure qualité d'impression, après avoir peaufiné votre
photo en utilisant l'épreuvage d'écran, vous devriez sélectionner le
profil de l'imprimante en tant que profil de sortie et enregistrer la
photo avec ce dernier. Cela garantit que l'image est encodée avec
l'espace colorimétrique de l'imprimante directement depuis la
représentation en virgule flottante interne de haute qualité de
RawTherapee, au lieu d'un enregistrement en image 8 bits en sRVB par
exemple, et puis ensuite convertie dans le profil de l'imprimante, ce
qui provoquerait des pertes.

L'histogramme principal, le navigateur et les indicateurs d'écrêtage
utiliseront soit le profil de travail, soit le profil de sortie. Vous
pouvez choisir le comportement en utilisant le bouton
![<File:gamut-hist.png>](gamut-hist.png "File:gamut-hist.png") dans
l'onglet Editor.

RawTherapee est livré avec de nombreux profils de sortie de haute
qualité de fabrication maison : Ils sont de 2 types selon la
compatibilité ICC v2 ou v4 : RTv2_xxx ou RTv4_xxx. Vous pouvez utiliser
sans soucis les versions v4 qui doivent dans une majorité de cas assurer
une portabilité correcte entre logiciels, les versions v2 sont
maintenues le cas échéant.

Pour chacun de ces types v2 ou v4 vous avez une terminaison "xxx" qui
correspond aux primaires de l'espace de sortie:

- _sRGB : similaire à sRGB
- _Medium : similaire à AdobeRGB1998
- _Large : similaire à ProPhoto
- _ACES-AP0 : similaire à ACES AP0
- _ACES-AP1 : similaire à ACES AP1
- _Wide : similaire à Widegamut
- _Rec2020 : similaire à Rec2020
- _Best : similaire à Best
- _Beta : similaire à Beta
- _Bruce : similaire à Bruce

Par défaut tous ces profils ont une TRC (Courbe de reproduction des
tons) de type sRGB - gamma =2.4 slope =12.92

Vous pouvez personnaliser ces profils à l'aide de "ICC profile creator"
[Générateur de profils ICC](icc_profile_creator/fr) :

- changer la TRC et assigner des valeurs de 1 - gamma linéaire, ou toute
  autre valeur
- changer les primaires et l'illuminant pour l'adapter à vos besoins
- changer les libellés, description,...

Le profil de sortie recommandé pour une sauvegarde sous un format 8 bits
et/ou publication sur le web est RTv4_sRGB. Si aucun profil n'est
sélectionné, aucun ne sera intégré, ce qui signifie l'utilisation de
"sRGB", bien qu'il soit plus sûr d'intégrer RTv4_sRGB en termes
d'obtention d'un affichage correct dans diverses applications.

RTv4_sRGB est une version **de qualité supérieure** du profil standard
sRGB, qui de façon surprenante est de qualité inégale d'une
implémentation à l'autre. RTv4_sRGB a été fabriqué maison pour
RawTherapee et possède 4096 points LUT, a comparer à la plus faible
qualité de 1024 points des profils sRGB. Les applications qui n'ont pas
de gestion de la couleur et qui ne tireront aucun avantage de RTv4_sRGB
se replieront sur sRGB.

Les profils de sortie de gamut étendu tels que RTv4_Large sont
généralement utilisés pour une exportation en format 16 bits ou plus en
vue d'une édition ultérieure dans une autre application. Si vous envoyez
l'image pour impression, un profil de sortie de gamut étendu est aussi
recommandé, car certaines imprimantes peuvent les utiliser (au moins
dans certaines couleurs).

Vous devriez avoir un moniteur de gamut étendu si vous désirez
travailler avec des profils à gamut étendu, sinon vous pilotez dans
l'obscurité.
