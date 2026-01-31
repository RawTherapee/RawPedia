---
title: Noise Reduction
contributors:
  - Lebarhon
  - Gaaned92
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Réduction du bruit

</div>
## Introduction

<figure>
<img src="/images/Noise-cactus-0-ba.png" title="Noise-cactus-0-ba.png" />
<figcaption>Noise-cactus-0-ba.png</figcaption>
</figure>

La photographie est basée sur l'enregistrement de la lumière qui frappe
un récepteur pendant une exposition. Le récepteur est typiquement un
film ou un capteur numérique. Le signal lumineux "enregistré" par le
récepteur n'est pas une représentation idéale du signal qui vient
frapper ce récepteur, cette différence constitue le bruit. Les photos
sur film ou numériques sont de la même façon sensibles au bruit (appelé
"grain" sur le film), cependant il existe différentes sortes de bruit
provenant des différentes sources spécifiques à chaque type de
récepteur.

Dans le but de traiter efficacement l'atténuation du bruit il est
nécessaire de comprendre les différentes sortes de bruit qui existent et
d'où elles proviennent. Le sujet du bruit est bien expliqué dans ce
papier écrit par l'un des développeurs de RawTherapee et professeur de
physique à l'Institut Fermi, Emil J. Martinec :

[Noise, Dynamic Range and Bit Depth in Digital
SLRs](http://theory.uchicago.edu/%7Eejm/pix/20d/tests/noise/index.html)

La lumière est constituée de paquets d'énergie appelés photons. Un
[capteur
photographique](https://fr.wikipedia.org/wiki/Capteur_photographique)
est comprend des millions d'éléments sensibles à la lumière appelés
*photosites*. Chaque photosite est capable d'enregistrer un signal d'une
certaine quantité de photons, pas assez, et le photosite ne va rien
enregistrer, de trop, et le photosite va saturer dans le blanc
(complètement surexposé). Pensez à un seau qui collecte de l'eau, bien
qu'il y ait de l'humidité dans l'air, s'il ne pleut pas, le seau reste
vide, mais s'il pleut de trop, le seau va déborder. Notez que le concept
de "pixel" n'existe pas encore à ce niveau, l'information en provenance
de plusieurs photosites est plus tard combinée en un pixel pendant le
processus appelé [dématriçage](demosaicing/fr). Notez aussi
que certaines sources écrivent à tort "pixel" pour désigner les
"photosites"

La sensibilité physique du capteur est constante, cependant le
photographe peut amplifier le signal reçu en agissant sur un paramètre
que vous connaissez sous le nom d'ISO (voir l'article [Sensibilité
ISO](https://fr.wikipedia.org/wiki/Sensibilit%C3%A9_ISO) dans
Wikipedia). Puisque le signal enregistré par le capteur n'est pas
parfait, augmenter les ISO n'amplifie pas seulement le signal désiré,
mais aussi le bruit. Les capteurs sont susceptibles de générer du bruit
à tout niveau ISO, cependant, plus le niveau ISO est élevé et plus le
bruit est apparent.

Il existe différents outils pour traiter les différents types de bruit :

- l'outil Réduction du bruit est le plus efficace pour traiter le bruit
  de grenaille (bruit
  [Gaussien](https://en.wikipedia.org/wiki/Gaussian_noise) et de
  [Poisson](https://fr.wikipedia.org/wiki/Bruit_de_grenaille)) et le
  grain du film, ainsi que certains bruits de lecture.
- Le bruit de lecture et le bruit thermique sont le mieux gérés par
  l'outil [Trame Noire](dark_frame/fr).
- Le bruit poivre et sel (pixels soudainement blancs ou noirs) est le
  mieux géré avec l'outil [Réduction du bruit
  d'impulsion](Impulse_Noise_Reduction/fr.md).
- Les pixels chauds ou morts sont le mieux traités avec [Filtrer les
  pixels
  chauds/morts](Preprocessing/fr#Filtrer_les_pixels_chauds/morts.md).
- Bruit en motifs (périodique, anisotropique) est le mieux géré avec
  [Filtre de bruit de
  ligne](Preprocessing/fr#Filtre_de_bruit_de_ligne.md). Vous
  pouvez aussi corriger le bruit en motifs derrière RawTherapee dans
  GIMP, en utilisant la transformée de Fourier dans G'MIC.

Indépendamment de la source, le bruit se manifeste par des taches de
couleurs différentes, "bruit de chrominance", ou de luminosités
différentes, "bruit de luminance".

1.  Le bruit de chrominance est spécifique aux images numériques, il est
    généralement inesthétique et constitue toujours quelque chose que
    vous souhaiterez enlever.
2.  Le bruit de luminance, d'un autre côté, ressemble au grain du film
    et peut être apprécié, il n'est donc pas rare de désirer retirer le
    bruit de chrominance mais de conserver le bruit de luminance.

<div align="center">

<File:noise-wall.png%7CUne> photo de test bruitée prise à 6400 ISO.
<File:Noise-wall-demosaic-amaze.png%7Cle> dématriçage AMaZE apporte des
petits motifs en forme de labyrinthe.
<File:Noise-wall-demosaic-lmmse.png%7Cle> dématriçage LMMSE évite les
petits motifs en forme de labyrinthe tout en préservant le détail.
<File:Noise-wall-luminance100-chrominance-off.png%7CLe> bruit de
chrominance ressemble à cela. Le détail de luminance est masqué pour
faire mieux ressortir le bruit de chrominance. Notez les tâches de
couleur dans le mur qui devrait être uni.
<File:Noise-wall-luminance100-chrominance-on.png%7CActiver> la réduction
du bruit de chrominance élimine les tâches colorées.
<File:Noise-wall-chrominance.png%7CLe> bruit de luminance ressemble à
cela. Le bruit de chrominance est masqué pour faire mieux ressortir le
bruit de luminance.
<File:Noise-wall-luminance-tweaked-chrominance-on-median-off.png%7CA> la
fois le bruit de chrominance et le bruit de luminance sont retirés.
<File:Noise-wall-luminance-tweaked-chrominance-on-zoom-median-off.png>\|
De minuscules artefacts de la taille d'un pixel sont laissés par la
réduction du bruit.
<File:Noise-wall-luminance-tweaked-chrominance-on-zoom-median-on.png%7CCes>
artefacts peuvent être retirés en utilisant le filtre médian.

</div>

Tout le monde n'attend pas la même chose d'une bonne réduction de bruit.
Certains préfèrent un résultat très propre et doux, alors que d'autres
préfèrent qu'il reste du grain pour donner à la photo une qualité
ressemblant au film. Le puissant outil *Réduction du bruit* de
RawTherapee pourvoit à tous vos besoins, il vous permet d'éliminer le
bruit tout en préservant les détails. Il utilise les
[ondelettes](http://fr.wikipedia.org/wiki/Ondelette), une [transformée
de Fourier](https://fr.wikipedia.org/wiki/Transformation_de_Fourier),
ainsi que des filtres médians, pour exercer sa magie. Il vous revient de
les peaufiner comme bon vous semble, et d'apprendre comment le faire
efficacement, bonne lecture !

## Usage

Ce chapitre détaille l'ordre des opérations pour retirer le bruit.

1.  Commencez par vous assurer que vous employez l'algorithme de
    dématriçage optimal. AMaZE est recommandé pour l'utilisation
    générale de RawTherapee, cependant, en cas d'images très bruitées,
    aux ISO élevés, il et recommandé d'utiliser les méthodes de
    dématriçage LMMSE ou IGV. AMaZE peut apporter des petits artefacts
    en forme de labyrinthe qui apparaissent dans les images très
    bruitées alors que LMMSE et IGV sont conçus pour empêcher que cela
    arrive
2.  Vérifier dans les outils de netteté que vous n'êtes pas en train de
    les appliquer sur de fins détails, car votre photo bruitée n'a pas
    de fins détails ! Si vous utilisez [Contraste par niveaux de
    détail](Contrast_by_Detail_Levels/fr.md) or
    [Ondelettes](wavelets/fr), assurez vous que les un ou
    deux premiers curseurs de contraste par niveaux de détail sont à 0
    pour éviter que ces outils n'amplifient le bruit
3.  Zoomer la photo à 100 % ou plus et trouver une région qui possède à
    la fois des parties nettes dans le plan de mise au point et à la
    fois de larges parties unies hors plan de mise au point, de telle
    façon à obtenir une bonne vision générale des effets de l'outil
4.  Activer [Filtrer les pixels
    chauds/morts](Preprocessing/fr#Filtrer_les_pixels_chauds/morts.md)
    si vous remarquez un bruit poivre et sel (pixels noirs et/ou
    blancs).
5.  Activer l'outil de réduction du bruit. Le bruit de chrominance est
    automatiquement retiré et se passe habituellement de tout réglage
    fin. A ce moment, le bruit restant ressemble au grain d'un film. Si
    vous désirez le garder, alors vous avez terminé, sinon continuez la
    lecture.
6.  Pour retirer le bruit de luminance, mettre le curseur "Niveaux de
    détail de luminance" à 0 et augmenter le curseur "Luminance" jusqu'à
    ce que le bruit soit évaporé.
7.  Accroitre le curseur "Niveaux de détail de luminance" jusqu'à
    retrouver un niveau satisfaisant de détail.
8.  Vous pouvez remarquer quelques petits artefacts résiduels après le
    processus de réduction du bruit. Les enlever avec l'outil Filtre
    Médian
9.  Bien qu'il ne soit généralement pas conseillé de combiner la netteté
    avec la réduction du bruit, RawTherapee 5.5 présente un réglage de
    "seuil de contraste" dans l'outil
    [Netteté](sharpening/fr), grâce auquel vous pouvez agir
    sur la netteté des détails tout en préservant la douceur des zones
    plates et uniformes.

<div align="center">

<File:Noise-cactus-1-amaze.png%7CL'image> bruitée.
<File:Noise-cactus-2-lmmse.png%7CChangement> de la méthode de
dématriçage pour LMMSE qui élimine les petits artefacts en forme de
labyrinthe et rend le bruit poivre et sel plus clair.
<File:Noise-cactus-3-pixelfilter.png%7CActiver> [Filtrer les pixels
chauds/morts](Preprocessing/fr#Filtrer_les_pixels_chauds/morts.md)
élimine le bruit poivre et sel.
<File:Noise-cactus-4-nr-chroma.png%7CActiver> la réduction de bruit
chromatique automatique procure une plaisante image grainée.
<File:Noise-cactus-5-nr-luminance.png%7CLe> bruit de luminance est
écarté en douceur avec le curseur *Luminance*.
<File:Noise-cactus-6-nr-detailrecovery.png%7CRestauration> des détails
avec le curseur "niveau de détails de Luminance".
<File:Noise-cactus-7-nr-median.png%7CLe> filtre médian est utilisé pour
éliminer les artefacts résiduels. <File:Noise-cactus-8-sharpen.png%7CLa>
netteté est restaurée grâce à un masque flou avec un seuil de contraste
pour éviter de rendre trop nettes des zones qui doivent rester douces.

</div>

## Interface

### Généralités

Examen rapproché de grandes zones fortement saturées avec de fins
détails, telles que le motif d'une chemise colorée ou une pétale de
fleur, basculement entre les espaces colorimétriques RVB et L\*a\*b\*.

Les images suivantes montrent les effets des différents types de
réduction de bruit, exagérés pour plus de clarté. Alors que l'image
source ne contient pas de "bruit" à très basse fréquence, elle a été
choisie car elle expose très bien les effets (et les effets collatéraux)
que l'on souhaite présenter.

<div align="center">

\<gallery caption="Comparaison des méthodes de réduction du bruit" -
Espaces colorimétriques" mode=nolines widths=600px heights=450px\>

<File:Noise-handkerchief-1-off.png%7CL'image> bruitée. "Niveau de
détails de Luminance" est intentionnellement laissé sur 0, et le niveau
de chromaticité est intentionnellement laissé sur un niveau très haut,
pour amplifier les effets.

<File:Noise-handkerchief-2-luminance-lab-conservative.png%7CRéduction>
du bruit de luminance dans l'espace L\*a\*b\*, mode "Conservatif".

<File:Noise-handkerchief-3-luminance-lab-aggressive.png%7CRéduction> du
bruit de luminance dans l'espace L\*a\*b\*, mode "Agressif".

<File:Noise-handkerchief-4-luminance-rgb-conservative.png%7CRéduction>
du bruit de luminance dans l'espace RVB, mode "Conservatif".

<File:Noise-handkerchief-5-luminance-rgb-aggressive.png%7CRéduction> du
bruit de luminance dans l'espace RVB, mode "Agressif".

<File:Noise-handkerchief-6-chrominance-lab-conservative.png%7CRéduction>
du bruit de chrominance dans l'espace L\*a\*b\*, mode "Conservatif".

<File:Noise-handkerchief-7-chrominance-lab-aggressive.png%7CRéduction>
du bruit de chrominance dans l'espace L\*a\*b\*, mode "Agressif".
Remarquez comme les couleurs déteignent les unes sur les autres dans les
endroits où les teintes se touchent, le bleu marine déteint sur le cyan,
le vert sur le rouge et le rouge sur le pourpre, etc.

<File:Noise-handkerchief-8-chrominance-rgb-conservative.png%7CRéduction>
du bruit de chrominance dans l'espace RVB, mode "Conservatif".

<File:Noise-handkerchief-9-chrominance-rgb-aggressive.png%7CRéduction>
du bruit de chrominance dans l'espace RVB, mode "Agressif". Les détails
basse fréquence sont perdus.

</gallery>
</div>

#### Espace colorimétrique

La réduction de bruit peut être réalisée dans les espaces
colorimétriques L\*a\*b\* ou RGB.

Dans l'espace L\*a\*b\*, le canal L\* est utilisé pour la luminance et
les canaux a\* et b\* pour la chromaticité.

Dans l'espace RVB, le Y de l'espace colorimétrique XYZ du CIE est
utilisé pour la luminance et (X-Y) et (Y-Z) pour la chromaticité.

#### Mode

Il existe deux modes généraux de réduction du bruit qui contrôlent si le
bruit de haute fréquence seul est retiré ou bien si le bruit de basse
fréquence l'est aussi. Le bruit de "basse fréquence" est le bruit dont
les tâches couvrent une large étendue, inversement le bruit de "haute
fréquence" a de plus petites taches qui ne couvrent que quelques pixels.

1.  Conservatif, enlève tout excepté le bruit de très basse fréquence,
    ainsi le détail des couleurs est mieux préservé au dépend du
    maintien des grandes taches. Utilisé la plupart du temps.
2.  Agressif, enlève aussi le bruit de très basse fréquence, au prix
    d'une plus grande agressivité avec le bruit de plus haute fréquence.
    A n'utiliser que sur les photos très bruitées.

#### Gamma

Le gamma varie la force de la réduction de bruit au travers de l'étendue
des tons. Les petites valeurs de gamma laissent agir la réduction du
bruit sur tous les tons, mettant en évidence l'action sur les ombres,
alors que les hautes valeurs limitent l'action aux seuls tons les plus
clairs.

### Luminance

<figure>
<img src="/images/Rt_nr_luminancecurve_books.jpg"
title="Rt_nr_luminancecurve_books.jpg" />
<figcaption>Rt_nr_luminancecurve_books.jpg</figcaption>
</figure>

"Contrôle de luminance" vous permet de choisir entre un curseur ou une
courbe pour manipuler la réduction du bruit de luminance.

Ajuster le curseur "Luminance" revient à manipuler l'amplitude de la
courbe, les deux agissent sur la force de la réduction du bruit. La
courbe présente en plus l'avantage de vous permettre de contrôler la
force de la réduction du bruit en fonction de la luminance des pixels,
par exemple, elle permet une forte réduction du bruit de luminance dans
les ombres et aucune dans les hautes lumières.

Le curseur "Niveau de détails de Luminance" permet de récupérer la
structure sans ré-introduire le bruit, a moins que vous ne lui
attribuiez une valeur trop haute.

### Chrominance

Méthodes  

La réduction du bruit de chrominance peut se réaliser selon une des
trois méthodes,

- Manuel
- Global Automatique
- Aperçu

Bruit de l'aperçu  

L'indicateur "Bruit de l'aperçu", donne les valeurs estimées du bruit
chromatique, après le traitement "Chrominance"

- Moyenne : estime la valeur moyenne du bruit tous canaux considérés.
- Élevée : estime la valeur maximale du bruit tous canaux considérés.

#### Manuel

- Les 3 curseurs et la courbe - agissent sur l'ensemble de l'image. Vous
  contrôlez manuellement les réglages de l'image

Maître  

Contrôle la force de la réduction de bruit de chrominance. Agit en
décalage (offset) et indépendamment des valeurs rouge-vert et
bleu-jaune. Par exemple, si maître = 50, rouge-vert = -50 et bleu-jaune
= -50, le résultat final est nul, aucun effet.

Rouge-Vert  

Réduit / amplifie les effets de la réduction du bruit dans le canal
rouge-vert (a\* dans L\*a\*b\*).

Bleu-Jaune  

Réduit / amplifie les effets de la réduction du bruit dans le canal
bleu-jaune (b\* dans L\*a\*b\*).

Courbe de chrominance  

La courbe de chrominance permet le contrôle du bruit de chrominance en
fonction de la chrominance des pixels, elle permet par exemple d'avoir
une forte réduction du bruit de chrominance dans les zones de basse
saturation et une faible réduction du bruit dans les zones de haute
saturation. Cette courbe module l'action des curseurs "Maître",
"Rouge-Vert" et "Bleu-Jaune" en multipliant leur valeur par l'ordonnée
de la courbe. Par exemple si le curseur Maître est réglé sur 30 et que
la courbe est à mi-hauteur, cela équivaut à environ 45. Il peut s'avérer
utile de renforcer la réduction du bruit dans les zones grises ou ternes
car nous distinguons mieux le bruit dans les zones de faible saturation
que nous ne le faisons dans les zones de haute saturation. Lors de
l'utilisation de la méthode de réduction du bruit "Global Automatique",
les paramètres calculés automatiquement sont une moyenne pour toute
l'image et peuvent être insuffisants pour enlever le bruit dans ces
zones de basse saturation, la courbe de chrominance peut aider.

#### Global Automatique

L'algorithme découpe l'image en de nombreuses cellules. Pour chaque
cellule, sont calculés :

- Un niveau de bruit moyen pour les canaux rouge-vert et bleu-jaune.
- Un niveau de bruit maximum pour les mêmes canaux.

#### Aperçu

Cette méthode n'est opérationnel qu'en zoom 100% et plus. Il analyse les
zones actuellement affichées dans l'aperçu (si le zoom est à 100% ou
plus) et calcule :

- Un niveau de bruit moyen pour les canaux rouge-vert et bleu-jaune.
- Un niveau de bruit maximum pour les mêmes canaux.

La valeur des trois curseurs Maître, Rouge-Vert et Bleu-Jaune ainsi que
celle du "Bruit de l'aperçu" est mise à jour en conséquence.

Si vous voulez garder les valeurs actuellement calculées, alors vous
devez retourner dans la méthode "manuel", sinon les valeurs seront
re-calculées lors d'un panoramique ou si vous copiez le profile pour
d'autres images.

### Médian

<figure>
<img src="/images/Rt_nr_median_books.jpg" title="Rt_nr_median_books.jpg"
width="600" />
<figcaption>Rt_nr_median_books.jpg</figcaption>
</figure>

![](Rt_nr_median_zoom_books.jpg "Rt_nr_median_zoom_books.jpg").

Utiliser ce filtre pour enlever les artéfacts minuscules, au piqué vif,
restés après la réduction du bruit.

Type de médiane  

Le [filtre médian](https://en.wikipedia.org/wiki/Median_filter) remplace
chaque pixel par la valeur médiane des pixels voisins. La matrice des
pixels voisins est appelée "fenêtre", laquelle glisse pixel par pixel
sur toute l'image. Vous pouvez choisir la taille de cette fenêtre en
utilisant la liste déroulante "Type de médiane". Plus elle est grande,
plus long sera le traitement.

Tailles de fenêtres disponibles :

- 3x3 doux: traite 5 pixels dans une fenêtre de 3x3 pixels.

  
○●○

●●●

○●○

- 3x3 : traite 9 pixels dans une fenêtre de 3x3 pixels.

  
●●●

●●●

●●●

- 5x5 doux: traite 13 pixels dans une fenêtre de 5x5 pixels.

  
○○●○○

○●●●○

●●●●●

○●●●○

○○●○○

- 5x5 : traite 25 pixels dans une fenêtre de 5x5 pixels.

  
●●●●●

●●●●●

●●●●●

●●●●●

●●●●●

- 7x7 : traite 49 pixels dans une fenêtre de 7x7 pixels.

  
●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

- 9x9 : traite 81 pixels dans une fenêtre de 9x9 pixels.

  
●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

Il est quelquefois possible d'atteindre de meilleurs résultats en
exécutant plusieurs itérations avec une petite fenêtre plutôt qu'une
seule itération avec une grande fenêtre.

  
Méthode médiane

Vous disposez de cinq méthodes:

- Luminance seulement : travaille dans l'espace L\*a\*b\*, mais
  n'affecte que le canal L\*.
- Chroma uniquement : travaille dans l'espace L\*a\*b\*, mais n'affecte
  que les canaux a\* et b\*.
- L\* Pondéré (faiblement) + a\*b\* (normal) : affecte tous les canaux
  dans l'espace L\*a\*b\*, mais agit plus faiblement sur le canal L\*.
- L\*a\*b\* : affecte tous les canaux avec égalité d'action.
- RVB : travaille dans l'espace RVB et vous ne pouvez choisir que les
  valeurs 3x3 doux, 3x3 et 5x5

Lorsqu'on utilise les méthodes "Luminance seulement" et "L\*a\*b\*", le
filtre Médian sera exécuté après l’étape des ondelettes dans le
processus de réduction du bruit. Si on utilise dans l'espace RVB, il
sera exécuté à la toute fin du processus de réduction du bruit.

Vous pouvez vous demander quelle utilisation Filtre Médian a d'autre que
pour des raisons esthétiques l'élimination de pixels qui diffèrent
fortement de leurs voisins. L'un des bénéfices est la réduction de la
taille de l'image lors de l'enregistrement dans un format compressé tel
que JPEG ou PNG. Filtre Médian enlève des variations qui seront de
toutes façons perdues si vous réduisez la taille de l’image. Vous ne
verrez pas non plus ces variations si vous imprimez l'image. Les enlever
grâce au Filtre Médian peut réduire la taille du fichier jusqu'à 40%
(testé en utilisant la compression JPEG, force 92 avec "qualité
équilibrée" [échantillonnage de la
chrominance](https://fr.wikipedia.org/wiki/Sous-%C3%A9chantillonnage_de_la_chrominance)),
aussi, testez le si la taille du fichier de sortie est critique.

Enfin, la méthode de filtre médian "Chroma uniquement" peut s'utiliser
en complément du calcul automatique de réduction du bruit de
chrominance, en réduisant les valeurs atypiques vives, elle peut adoucir
les valeurs calculées, et éviter ainsi de trop faire pâlir les détails
de couleur.
