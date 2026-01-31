---
title: General Comments About Some Toolbox Widgets
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
---

<div class="pagetitle">

Commentaires généraux à propos de certains éléments d'interface
graphique (Widgets) de la boite à outils

</div>

Cet article est destiné à vous permettre une utilisation plus efficace
de RawTherapee et à pleinement exploiter des possibilités que même un
utilisateur expérimenté peut ne pas connaître. Prenez quelques instants
pour le lire.

## Panneaux

L'onglet Éditeur possède trois panneaux principaux dont l'affichage peut
être demandé ou pas à l'aide des boutons Montrer/Cacher dans le panneau
![<File:Panel-to-bottom.png>](Panel-to-bottom.png "File:Panel-to-bottom.png")
![<File:Panel-to-left.png>](Panel-to-left.png "File:Panel-to-left.png")
![<File:Panel-to-top.png>](Panel-to-top.png "File:Panel-to-top.png")
![<File:Panel-to-right.png>](Panel-to-right.png "File:Panel-to-right.png"),
permettant de gérer la place pour l'image d'aperçu.

Vous pouvez utiliser la molette de la souris pour faire défiler les
panneaux vers le haut ou le bas sans modifier accidentellement la valeur
des curseurs, car RawTherapee exige le maintien enfoncé de la touche
Majuscule (Shift) pendant l’utilisation de la molette si votre intention
est de modifier un curseur ou de vous déplacer au travers des options
d'un menu déroulant (appelé "combobox").

## Outils

Il y a beaucoup d'outils, l'espace vertical est limité et faire défiler
prend du temps. Par un clic droit sur le titre d'un outil, vous pouvez
étendre cet outil et réduire tous les autres présents dans le même
panneau. Cela permet de profiter au mieux de l'espace vertical et de
limiter le besoin de faire défiler.

La plupart des outils présentent un bouton d'activation à gauche de leur
titre qui vous permet d'activer/désactiver cet outil. Ce bouton peut
aussi prendre un état "intermédiaire" si vous sélectionnez deux photos
ou plus dans le [Navigateur de fichiers](file_browser/fr).
Dans cet état, l'outil est activé pour certaines des photos
sélectionnées et désactivé pour les autres. Certains outils, à la place
du bouton activer/désactiver, ont un "extenseur" qui permet d'étendre ou
de réduire le contenu de cet outil.

![<File:Power-off-small.png>](Power-off-small.png "File:Power-off-small.png")
Désactivé.

![<File:Power-on-small.png>](Power-on-small.png "File:Power-on-small.png")
Activé.

![<File:Power-inconsistent-small.png>](Power-inconsistent-small.png "File:Power-inconsistent-small.png")
Intermédiaire.

![<File:Expander-closed-small.png>](Expander-closed-small.png "File:Expander-closed-small.png")
Réduit.

![<File:Expander-open-small.png>](Expander-open-small.png "File:Expander-open-small.png")
Étendu.

## Curseurs

Pour régler un curseur, le survoler avec la souris puis actionner la
molette de la souris tout en maintenant la touche appuyée. Actionner la
molette sans appuyer sur la touche fait défiler tout le panneau
verticalement.

Chaque curseur possède aussi un mode de réglage fin qui ralenti l'effet
de la souris, permettant des ajustements très fins, délicats à obtenir
sans ce mode. Pour entrer dans le mode de réglage fin, cliquer sur le
bouton d'ajustement du curseur et maintenir appuyé pendant une seconde
sans bouger. Vous pouvez aussi entrer ou sortir de ce mode en appuyant
sur la touche tout en maintenant le clic sur le bouton du curseur. Ceci
est une caractéristique standard pour tous les programmes qui utilisent
[GTK+ 3](https://fr.wikipedia.org/wiki/GTK%2B).

Chaque curseur possède un bouton "reset"
![<File:Undo-small.png>](Undo-small.png "File:Undo-small.png") qui se
comporte comme suit :

- remet le curseur à sa valeur par défaut, qui est codée en dur à 0 dans
  la plupart des cas, ou à une autre valeur si 0 n'est pas approprié.

- \+ remet le curseur à la valeur qu'il avait initialement, à
  l'ouverture de la photo.

## Courbes

RawTherapee possède trois sortes de widgets pour les courbes :

- Courbes tonales
- Courbes équalizer
- Courbes de seuil

<div align="center">

<File:Rt55> curve type tone.png\|La courbe tonale. <File:Rt55> curve
type equalizer.png\|La courbe équalizer. <File:Rt55> curve type
threshold.png\|La courbe de seuil

</div>

\[\[<File:Rt55> curves.png\|frame\|1- Type de courbe.

2- Mode de courbe.\]\]

La forme d'une courbe tonale ou d'une courbe équalizer est définie sur
la base de points de contrôle que vous créez et positionnez avec la
souris. Pour une courbe linéaire, cela signifie que l'entrée correspond
à la sortie et que la courbe n'a donc aucun effet. Lorsqu'une courbe
n'est pas linéaire, elle a un effet sur l'image.

Le tracé de la courbe se base sur les points de contrôle que vous avez
créés et positionnés. Les mêmes points de contrôle peuvent amener des
courbes différentes selon les lois mathématiques sous-jacentes, vous
pouvez contrôler ces lois en choisissant le type de courbe tonale dans
la liste déroulante :

- ![<File:curve-linear-small.png>](curve-linear-small.png "File:curve-linear-small.png")
  Linéaire,
- ![<File:curve-spline-small.png>](curve-spline-small.png "File:curve-spline-small.png")
  Personnalisé,
- ![<File:curve-catmullrom-small.png>](curve-catmullrom-small.png "File:curve-catmullrom-small.png")
  Flexible,
- ![<File:curve-parametric-small.png>](curve-parametric-small.png "File:curve-parametric-small.png")
  Paramétrique,
- ![<File:curve-nurbs-small.png>](curve-nurbs-small.png "File:curve-nurbs-small.png")
  Cage de contrôle.

Vous pouvez aussi cliquer sur le bouton de type de courbe pour basculer
entre Montrer/Cacher la courbe. cela permet d'exploiter au mieux la
place verticale qui est limitée. Si une courbe n'est pas linéaire et que
l'outil exploité au travers elle est activé, alors cette courbe agit sur
l'image indifféremment du fait qu'elle soit visible ou non.

Chaque courbe peut être resettée,
![<File:Undo-small.png>](Undo-small.png "File:Undo-small.png") à sa
valeur par défaut. Certaines courbes fonctionnent en groupe, par exemple
les courbes d'[Ajustements L\*a\*b\*](lab_adjustments/fr), il
n'y a qu'un bouton reset pour tout le groupe et il s'applique à la
courbe sélectionnée. Cliquer sur le bouton de la liste déroulante des
types de courbe pour effectuer cette sélection.

Certaines courbes ont une pipette
![<File:Crosshair-node-curve.png>](Crosshair-node-curve.png "File:Crosshair-node-curve.png")
et un éditeur des valeurs d'entrée/sortie des points de contrôle
![<File:Edit-point.png>](Edit-point.png "File:Edit-point.png").

### La pipette

<figure>
<img src="/images/Rt55_lab_hh_color_picker.png"
title="Rt55_lab_hh_color_picker.png" />
<figcaption>Rt55_lab_hh_color_picker.png</figcaption>
</figure>

La plupart des courbes de RawTherapee possèdent une pipette
![<File:Crosshair-node-curve.png>](Crosshair-node-curve.png "File:Crosshair-node-curve.png").
Elle permet de placer un point de contrôle sur la courbe à l'endroit
exact qui correspond à la zone survolée dans l'aperçu.

Supposons que vous vouliez changer la teinte violette d'une fleur, pour
la rendre plus bleue. Sans la pipette, vous auriez à deviner le point
exacte sur la courbe qui correspond à la teinte de la fleur, sinon la
gamme des nuances affectées serait trop étendue avec la conséquence de
modifier des teintes qu'on ne désirait pas modifier. Avec la pipette,
vous cliquez simplement sur la fleur, et un point qui correspond
exactement à la teinte apparaît dans la courbe concernée . Vous pouvez
ajuster ce point de contrôle selon votre désir.

Lorsque le bouton pipette est cliqué, la pipette est activée pour la
courbe en question. Maintenant lorsque vous survolez l'aperçu avec la
souris, vous remarquez qu'une ligne horizontale ou verticale apparaît
dans la courbe. Cette ligne représente la valeur du pixel survolé. Pour
placer dans la courbe un point de contrôle correspondant à ce pixel, +
dans l'aperçu, un point de contrôle apparait dans la courbe. Il est
possible de l'ajuster sans quitter l'aperçu, simplement garder appuyé le
bouton gauche de la souris après le placement du point de contrôle,
déplacer la souris de haut en bas et le point de contrôle se déplacera
de haut en bas dans la courbe. Maintenir {k\|Ctrl}} appuyé pendant
l'édition d'un point de contrôle diminue la vitesse de la souris et
permet un ajustement très fin. Vous n'aurez en général pas besoin d'une
telle précision, donc après l'ajout d'un nouveau point de contrôle via
+, lâcher la touche mais maintenir l'appui sur le bouton gauche de la
souris.

Pour désactiver la pipette, soit faire un n'importe où sur l'aperçu ou
refaire un sur le bouton de la pipette.

Il n'est pas nécessaire de désactiver la pipette d'une courbe précédente
pour l'utiliser sur une nouvelle courbe, simplement activer la pipette
comme d'habitude et l'ancienne sera automatiquement désactivée.

#### Valeur d'entrée/sortie de la courbe

Chaque courbe dispose d'un bouton qui permet d'éditer les valeurs
d'entrée/sortie du point de contrôle sélectionné. Vous pouvez utiliser
cet outil, par exemple, pour faire correspondre la valeur de sortie d'un
point de contrôle sur la photo de couleurs cibles avec une valeur de
référence.

L'outil fonctionne avec des points de contrôle, et la méthode la plus
probable avec laquelle vous allez créer ces points de contrôle est en
utilisant la pipette. Pour cet exemple, nous allons commencer avec une
courbe sans aucun point de contrôle et en créer quelques uns avec la
pipette. Cliquez sur le bouton édition des valeurs d'entrée/sortie du
point de contrôle
![<File:Edit-point.png>](Edit-point.png "File:Edit-point.png") auprès de
la courbe, et cliquez aussi sur le bouton Pipette
![<File:Crosshair-node-curve.png>](Crosshair-node-curve.png "File:Crosshair-node-curve.png").
Vous voyez maintenant des valeurs "E" (entrée) and "S" (sortie)
affichées sous la courbe, ils correspondent au point situé sous le
curseur de la souris si vous la déplacez au-dessus de la courbe ou de
l'aperçu. Maintenant, déplacez le curseur au-dessus de l'aperçu. Puisque
vous avez activé la pipette, vous pouvez maintenir + sur un endroit
particulier de l'aperçu pour placer un point de contrôle sur la courbe
qui correspond à la valeur de cet endroit (quelque puisse être cette
valeur, par exemple pour la courbe L\*, la valeur est la luminosité du
pixel sous le curseur, pour la courbe rouge en RVB, c'est la valeur du
rouge dans l'espace RVB du profil de travail). Faites cela, + en un
endroit de l'aperçu. Un point de contrôle apparait sur la courbe. Pour
éditer les valeurs d'entrée/sortie du point de contrôle, cliquer droit
dessus. Il devient rouge avec un anneau rouge. Maintenant vous pouvez
modifier les valeurs d'entrée/sortie et voir le point de contrôle bouger
en temps réel. Pour sortir du mode édition du point de contrôle une fois
la modification terminée, soit cliquer droit n'importe où dans le cadre
de la courbe (en dehors du point de contrôle), ou simplement cliquer à
nouveau sur le bouton d'édition des valeurs du point de contrôle.

### Courbes tonales

![](Rt55_curve_linear.png "Rt55_curve_linear.png")
![](Rt55_curve_standard.png "Rt55_curve_standard.png")
![](Rt55_curve_flexible.png "Rt55_curve_flexible.png")
![](Rt55_curve_parametric.png "Rt55_curve_parametric.png")
![](Rt55_curve_control_cage.png "Rt55_curve_control_cage.png")

Les courbes tonales servent à convertir des valeurs d'entrée (sur l'axe
X, horizontal) en valeurs de sortie (sur l'axe Y, vertical). Bien
qu'elles puissent effrayer au premier abord, après un peu de pratique,
chacun parvient très vite à les prendre en main de façon intuitive. Les
courbes peuvent faire tout ce qui est faisable avec des systèmes de
"niveaux" et bien plus encore, aussi plus vite vous les aurez prises en
main et mieux ce sera.

En guise d'exemple, observons la "Courbe personnalisée" (copie d'écran
sur la droite), dans l'outil [Exposition](exposure/fr). Il y
a une grille en arrière plan avec des lignes espacées de 10%.
L'extrémité gauche de l'axe horizontal (entrées) représente le noir pur,
puis les ombres, puis les tons moyens, puis les hautes lumières et
finalement le blanc pur à l'extrémité droite. De même l'axe vertical
(sorties) représente le noir pur en bas et le blanc pur en haut et la
même graduation entre les deux. Si la courbe est linéaire, par exemple
une droite diagonale de l'angle en bas à gauche vers l'angle en haut à
droite, alors cette courbe n'a aucun effet, tout point de cette courbe
possède une valeur de sortie égale à la valeur d'entrée. Pour que la
courbe agisse, elle doit être non-linéaire quelque part pour que la
valeur de sortie de certains points diffère de la valeur d'entrée. Les
"points de contrôle" que vous placez sur la courbe ne sont là que pour
vous aider à contrôler la courbe, ils n'interviennent pas dans les
calculs, ce qui importe est la "forme" de la courbe. Dans notre exemple
en copie d'écran un point de contrôle placé dans la partie inférieure
gauche décale la courbe vers le bas : le point de contrôle est à 10% sur
l'axe des "entrées", mais à seulement 5% sur l'axe des "sorties", cela
rend les tons sombres encore plus sombres. Un deuxième point de contrôle
est à 40% sur l'axe des "entrées", mais à 60% sur l'axe des "sorties",
les tons moyens sont rendus plus clairs. Puisque seul compte la forme de
la courbe, même en l'absence d'autres points de contrôle dans cet
exemple, la courbe pour une entrés de 60% donne une sortie de 95%, ce
qui signifie que les zones claires seront rendues encore plus claires,
presque blanches. A l'entrée 20% correspond la sortie 20%, ainsi ces
tons sombres restent inchangés.

Il y a plusieurs types de courbes à votre disposition :

- **Linéaire**

  
Le type par défaut, une ligne droite qui n'applique aucune modification
aux valeurs d'entrées. Les initiés aux mathématiques remarqueront qu'il
s'agit de la courbe y=x. Les autres se contenteront de régler la courbe
sur Linéaire pour la désactiver.

- **Personnalisé**

  
Le type le plus répandu dans les autres logiciels. Cliquer n'importe où
pour déposer un point de contrôle puis le glisser pour modifier la forme
de la courbe. Le point en haut à droite représente les zones les plus
claires de la photo. Glisser ce point verticalement vers le bas pour
rendre les hautes lumières moins claires; le glisser horizontalement
vers la gauche pour rendre les zones claires encore plus claires, peut
être au prix d'une surexposition. Le point en bas à gauche représente
les zones les plus sombres de la photo. Glisser ce point horizontalement
vers la droite pour assombrir la photo, peut être au prix d'une
sous-exposition. Le glisser verticalement pour éclaircir les ombres.

- **Flexible**

  
Une caractéristique de la courbe Spline cubique "Personnalisé" est que
l'édition d'un point peut avoir, en fonction des autres points, un
impact énorme sur la courbe. La courbe Spline cubique d'Hermite
"Flexible" vous permet de réaliser des ajustements sur n'importe quelle
partie de la courbe avec peu d’impacts sur les autres parties

- **Paramétrique**

  
Permet l'utilisation de curseurs plutôt que directement glisser des
points de la courbe. Cliquer droit sur la zone de sélection
(![Image:Parametric_curve_bar.png](Parametric_curve_bar.png "Image:Parametric_curve_bar.png"))
remet les index à leur position par défaut. (Le bouton reset le fait
aussi).

- **Cage de contrôle**

  
A première vue ce type de courbe ressemble beaucoup à la courbe
Personnalisé, mais il y a quelques différences. avec la courbe
Personnalisé, ceele ci passe par tous les points de contrôle. Ce qui
n'est pas le cas avec la courbe Cage de contrôle, ici les points de
contrôle attirent la courbe mais elle ne les rejoint pas. Une autre
différence est la possibilité avec la Cage de contrôle d'avoir une
section rectiligne de la courbe, impossible avec la courbe Personnalisé.
La Cage de contrôle nécessite au moins trois points pour cela (soit cinq
au total). Tenir enfoncée la touche Maj pendant le déplacement du point
de contrôle vous aidera à l'aligner entre le point précédent et le point
suivant (alors affichés en rouge par l'outil 'accrocher'), créant ainsi
une droite. Beaucoup d'utilisateurs préfèrent la courbe de type Cage de
contrôle aux autres.

### La Courbe Plate

[frame](image:flat_curve_justcurve.png) Nombre d'outils de
RawTherapee utilisent la *Courbe Plate* :

- [Ajustements Lab](lab_adjustments/fr)
  - [LT](lab_adjustments/fr#courbe_lt)
  - [CT](lab_adjustments/fr#courbe_ct)
  - [TT](lab_adjustments/fr#courbe_tt)
- [Aberration chromatique](defringe/fr)
  - [Teinte](defringe/fr#teinte)
- [Egaliseur TSV](hsv_equalizer/fr)
  - [T](hsv_equalizer/fr#h)
  - [S](hsv_equalizer/fr#s)
  - [V](hsv_equalizer/fr#v)

C'est d'utilisation très simple une fois le principe compris, aussi
utilisons l'[égaliseur TSV](hsv_equalizer/fr) dans l'onglet
![<File:Color-circles.png>](Color-circles.png "File:Color-circles.png")
Couleur en guise d'exemple. Cliquez sur l'icône de la liste déroulante
[image:Drop-down.png](image:drop-down.png) près du bouton
T(einte) et choisissez
![<File:Curve-controlpoints-small.png>](Curve-controlpoints-small.png "File:Curve-controlpoints-small.png")
*"Points de contrôle minima/maxima"*. Vous voyez maintenant six points
sur la ligne horizontale du milieu et six lignes verticales qui passent
par ces points. Notez que ces lignes sont colorées; de la gauche vers la
droite : rouge, jaune vert, turquoise, bleu et magenta. Maintenant
cliquez sur le point le plus à gauche (le curseur se transforme en
petite main) et glissez le légèrement vers le haut puis vers le bas.
Résultat : les rouges deviennent verts puis bleus et magenta si le
curseur est déplacé vers le haut, et roses puis bleus et verts si le
curseur est déplacé vers le bas.

Remarquez qu'une nouvelle ligne horizontale apparaît lorsque vous
commencez à déplacer le point, et notez comment sa couleur change. L'axe
vertical représente les couleurs d'entrée, et l'axe horizontal les
couleurs de sortie.

Lorsque vous cliquez et glissez une ligne verticale (une ligne, pas le
point !), le tout début du déplacement détermine le type de mouvement :
vertical ou horizontal (aussi faite attention à ce début du déplacement
si vous voulez maitriser la suite). Si vous désirez bouger le point dans
les deux directions en même temps, alors cliquer/glisser le point
lui-même. Pour ne déplacer le point que dans une seule direction
(horizontale ou verticale) vous pouvez utiliser la fonction 'accrocher'
en tenant enfoncée la touche Maj pendant le déplacement du point.

[frame](image:flat_curve_zoom.png) Il est facile de voir si
un point est dans sa position neutre (c'est à dire sur la ligne du
milieu) car dans ce cas, sa couleur est verte. Dès que vous bougez un
point de sa valeur neutre, il devient noir.

L'[Egaliseur TSV](hsv_equalizer/fr) s'enroule autour de l'axe
horizontal, si bien que la ligne verticale complètement à gauche est la
même que celle complètement à droite. Vous pouvez le constater en
glissant la ligne rouge à gauche un peu plus vers la gauche. Maintenant
le point de gauche sur le graphe est à la même position que le point
complètement à droite. En maintenant la touche **Maj** appuyée pendant
le déplacement d'un point, on l'empêche de s'enrouler autour de l'axe
horizontal, cela est utile pour éviter des marches accidentelles de la
courbe vers des endroits difficiles à voir le long des bords.

Vous pouvez effacer des points en les glissant en dehors du cadre de
l'éditeur. Vous pouvez en ajouter en cliquant quelque part sur la
courbe. Quand vous placez la souris sur un des points, un indicateur
jaune et bleu apparaît. Placez la souris sur le jaune et le curseur se
transforme en flèche vers la gauche. Maintenant, glissez ce point vers
la gauche pour modifier la tangente de la courbe. Même démarche avec
l'indicateur bleu.

Pour se faire une idée sur le fonctionnement de cet éditeur, effacez
tout sauf deux couleurs (par exemple le rouge et le jaune) et déplacez
les tangentes autour du point, changez la courbe et regardez ce qui
arrive à votre photo.

Ré-initialiser la courbe *Teinte* sur "*Linéaire*" (supprimer tout
changement) en cliquant sur l'icône de ré-initialisation
[image:Gtk-undo-ltr.png](image:gtk-undo-ltr.png) à droite du
bouton *Valeur*. Pour comparer entre les effets de la courbe *Teinte*
avec linéaire : commuter entre "*Linéaire*" et "*Points de contrôle
minima/maxima*" dans le menu déroulant placé auprès de ce bouton. Ou
bien utilisez la liste de l'Historique sur le coté gauche de l'écran.

Il est possible d'enregistrer une courbe pour un usage ultérieur en
cliquant sur le bouton symbolisant un disque. Noter que seule la courbe
en cours (présentée) T, S ou V est enregistrée, non pas les trois. Donc,
ne donnez pas à la courbe un nom tel que ma_tsv car il ne décrit pas si
la courbe concernée est T, S ou V, mais plutôt donnez un nom comme
ma_teinte, ma_sat et ma_val. L'extension "*.rtc*" est ajoutée
automatiquement.

### Courbes de seuil

Les Courbes de Seuil sont les plus simples. Elles sont utilisées pour
indiquer à un outil de RawTherapee la valeur de la tonalité (ou de la
teinte ou de la saturation) que vous désirez voir traitée (ou traitée
différemment).

Comme exemple, considérons l'éditeur de la courbe de seuil de l'outil
Détail -\> [Netteté](sharpening/fr).
![](_Sharpening_Threshold_fr.png "_Sharpening_Threshold_fr.png") Dans
l'exemple présenté, la courbe indique à l'outil netteté d'introduire
rapidement la netteté dans les zones sombres (la ligne en pente raide
sur la gauche), de la maintenir au maximum pour les zones intermédiaires
(la zone en plateau) puis de diminuer lentement la netteté dans les
hautes lumières (la longue pente douce). Cliquer/glisser l'un des points
de contrôle déplacera la pente montante ou descendante depuis ce point.
Pour déplacer le point seulement, et non pas la courbe, maintenir
enfoncée la touche majuscule pendant le glissement.

En haut à droite, se trouve le bouton reset, qui retourne aux réglages
par défaut.

**Attention** retourner aux réglages par défaut de la courbe est
considéré comme une modification de la courbe, aussi, si vous venez de
modifier la courbe et malencontreusement cliqué sur le bouton *Reset*,
il n'est pas possible de récupérer la courbe. (Ctrl-z reviendra d'un pas
dans la liste de l*'Historique*, pas dans l'édition de la courbe). Ce
commentaire s'applique aussi aux Courbes Tonales et aux Courbes Plates.

Vous trouverez également des Courbes de seuil dans les outils [Contraste
par niveaux de détail](Contrast_by_Detail_Levels/fr.md) et
[Vibrance](vibrance/fr).

Vous avez sans doute remarqué que les Courbes de Seuil sont en fait
constituées de quelques segments de droite plutôt que de courbes. Si
cela vous chagrine, faites donc une pause avant de passer aux Courbes
Plates

## La zone d'aperçu

L'aperçu est conçu pour vous montrer le résultat le plus réaliste
possible, Cependant, garder en tête que plus l'image est grande et plus
le temps de traitement est long. Pour des raisons de rapidité, l'aperçu
des effets de la plupart des outils est calculé non pas sur l'image
pleine et entière (ce qui demanderait exactement le même temps que pour
l'enregistrement, rendant impossible l'usage des curseurs et des courbes
pendant ce temps), mais sur l'image de l'aperçu qui fait la taille de la
fenêtre de l'aperçu. Par ailleurs, beaucoup d'outils, tels que l'outil
[Exposition](exposure/fr), peuvent s'appliquer sur une image
de n'importe quelle taille, et leurs effets seront identiques
indépendamment de la taille de l'image en question. Cependant, certains
outils dépendent de la taille, par exemple, tous les outils de l'onglet
Détail, ce qui signifie que si vous appliquez l'un de ces outils sur une
grande image (nombreux pixels) et sur une version réduite de cette image
(nombre de pixels moindre) et qu'ensuite vous réduisiez le nombre de
pixels de la grande image pour obtenir le même nombre que sur la petite,
alors vous aurez deux images différentes. Pour des raisons de rapidité,
RawTherapee doit utiliser une petite image en aperçu afin que votre
travail soit rapide et fluide, mais cela signifie que les effets des
outils sensibles à la taille ne seront pas représentatifs
puisqu'appliqués sur un aperçu fortement zoomé arrière. Nous avons donc
pris la décision de soit désactiver complétement les effets de ces
outils dans l'aperçu si le zoom n'est pas d'au moins 100%, soit de
garder les effets dans l'aperçu mais de vous prévenir que la
visualisation de l'aperçu zoomé à moins de 100% peut s'avérer imprécis
en fonction des paramétrages de l'outil (par exemple [Compression
tonale](Tone_Mapping/fr.md) et [Niveaux
d'ondelettes](Wavelet_levels/fr.md) peuvent être précis ou pas à
des niveaux de zoom inférieurs à 100%, en fonction de leurs réglages).
Vous reconnaîtrez les outils concernés car ils sont repérés par une
icône "1:1"
![<File:One-to-one-small.png>](One-to-one-small.png "File:One-to-one-small.png")
tout près de leur nom. RawPedia détaille dans leur page le niveau de
précision de l'aperçu pour tous les outils concernés.
