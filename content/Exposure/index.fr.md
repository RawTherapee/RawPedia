---
title: Exposure
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Exposition

</div>

## Niveaux Auto

L'outil Niveaux Auto analyse l'histogramme puis ajuste les curseurs de
la section Exposition pour obtenir une image correctement exposée.

Il n'utilise que les curseurs "Compensation d'exposition", "Compression
hautes lumières", "Reconstruction des hautes lumières", "Noir",
"Luminosité" et "Contraste".

Envisager les réglages de Niveaux Auto comme un bon départ. Ils ont été
réglés pour donner de bons résultats avec les prises de vues classiques,
donc bien souvent le résultat est esthétiquement plaisant, mais comme le
programme ne connaît pas vos goûts ni attentes, ce ne sera pas toujours
le cas. Par exemple, si vous souhaitez obtenir un aspect sur-exposé
(c'est à dire pas classique), vous devrez régler vous même les valeurs.

Il est possible de réinitialiser tous les curseurs de la section
Exposition en cliquant sur le bouton Neutre. Les Courbes Tonales ne sont
pas concernées.

## Rognage %

Niveaux auto utilise la valeur de Rognage % pour ajuster l'exposition.
Ce nombre définit le pourcentage de pixels pouvant être classés hors
domaine au-delà du point blanc et du point noir de l'histogramme raw. La
valeur minimum est 0,00 et la valeur maximum est 0,99. Les valeurs les
plus élevées accroissent le contraste, les plus basses le diminuent.

A partir de Rawtherapee 5.5, alors que l'outil Niveaux Auto de l’Éditeur
utilises encore la valeur Rognage %, les vignettes utilisent une valeur
fixe de 0.2%, ceci pour réduire le nombre de fichiers à sauvegarder dans
le [cache](file_paths/fr#cache).

## Reconstruction des hautes lumières

Cocher *Reconstruction des hautes lumières* pour essayer de restaurer
les hautes lumières surexposées dans le fichier raw. Il tente de
restaurer les zones hors domaine (brûlées) de l'image raw en comptant
sur le fait que les trois canaux du fichier raw ne sortent pas du
domaine en même temps et ainsi une zone manquante (rognée) dans un canal
peut être devinée à partir des données présentent dans l'un des autres
canaux de couleur. Avec la méthode de *Propagation de la couleur*, les
données rognées peuvent aussi être devinées à partir des données
environnantes des canaux non rognés, si elles existent. Rappelez vous,
cet outil est utilisé pour la *reconstruction* des hautes lumières
rognées, alors que si vous désirez seulement *compresser* les hautes
lumières qui n'étaient pas rognées au départ mais le devinrent en raison
de l'utilisation, par exemple, de *Compensation d'exposition*, alors
utiliser le curseur [Compression hautes
lumières](Exposure/fr#Compression_hautes_lumières.md). Le bouton
*Niveaux Auto* activera automatiquement *Reconstruction des hautes
lumières* si nécessaire.

Quatre méthodes différentes de reconstruction des hautes lumières sont
disponibles :

1.  Récupération de la luminance
      
    Les détails récupérés seront gris neutre.

    Les valeurs de "*Compression hautes lumières*" en dessous de 100
    sont recommandées dans la plupart des cas.
2.  Propagation de la couleur
      
    C'est la méthode de récupération la plus efficace. En plus que de
    récupérer la luminosité, la *Propagation de la couleur* essaie de
    restaurer également les informations de couleur en 'faisant
    déborder' les couleurs environnantes connues vers la zone rognée
    manquante. Cette méthode fonctionne mieux sur de petites zones
    surexposées, et peut faire des merveilles sur de la peau surexposée.
    Sa faiblesse réside dans le risque de 'faire déborder' des couleurs
    incorrectes, en fonction des éléments d'image environnant la zone de
    hautes lumières brûlées, ou la couleur peut donner des effets
    indésirables. Elle est aussi consommatrice de calculs intensifs et
    est donc plus lente que les autres méthodes.

    Fonctionne bien, même avec de très grandes valeurs de "*Compression
    hautes lumières*" (en-dessous de 500).
3.  Mélange CIELab
      
    Réduit le canal de la luminance et essaie ensuite de restaurer les
    couleurs.

    Des valeurs de "*Compression hautes lumières*" en-dessous de 100
    sont le plus souvent recommandées.
4.  Blend (mélange)
      
    Tente de deviner les canaux des couleurs rognées en renseignant
    leurs valeurs depuis la plus proche correspondance en provenance des
    régions environnantes ayant des hautes lumières non rognées.

    Des valeurs de "*Compression hautes lumières*" en-dessous de 100
    sont le plus souvent recommandées.

## Compensation d'exposition

Les valeurs du curseur Compensation d'exposition sont des valeurs ISO.
Cela signifie qu'une valeur de +1 équivaut à un pas de sur-exposition
(+1 IL, indice de lumination, appelé aussi +1 EV, Exposure Value). Si
vous faites deux photos, une sans correction (IL=0) et une sous-exposée
de un pas (IL=-1), vous pouvez obtenir des photos exactement identiques
en réglant Compensation d'exposition pour la photo surexposée à -1, ou
pour la photo sous exposée à +1. Surveillez l'histogramme pendant le
déplacement de ce curseur. Le bouger vers la droite, décale tout
l'histogramme vers la droite. Cela signifie que ce curseur modifie le
point noir (complètement à gauche de l'histogramme) et le point blanc
(complètement à droite).

Si vous tentez de diminuer l'exposition d'une photo qui contient des
zones hors domaine, vous remarquerez que ces zones virent au gris
uniforme. Activer la "*Reconstruction des hautes lumières*" empêchera
cela jusqu'à un certain point en retrouvant des informations sur ces
hautes lumières dans les canaux non hors domaine.

Si vous utilisez RawTherapee depuis un moment, vous remarquez peut-être
que vous avez presque toujours besoin d'une Compensation d'exposition
positive, comme si toutes vos photos étaient sous-exposées. Ne vous
inquiétez pas, c'est normal. Une majorité d'appareils photo
sous-exposent délibérément pour préserver les hautes lumières (bien que
certains autres logiciels de traitement raw le dissimulent).

Pour les utilisateurs intéressés par les entrailles du système, voici
une description technique sur la façon dont IL=0 est relié aux données
raw : tandis que IL=0 vaut 1.0 en gain (c'est à dire, pas de
changement), il existe une balance des blancs dépendante du gain de base
appliquée avant l'exposition. Ce gain de base est calculé de telle façon
que le canal de couleur ayant la plus petite étendue peut tout juste
atteindre la valeur maximum. Bien que tous les canaux raw aient la même
étendue dans le fichier raw, la balance des blancs modifie cet équilibre
(une température plus faible signifie plus de gain sur le rouge, une
plus élevée, plus de gain sur le bleu) si bien que les canaux ne
saturent pas tous au même niveau. Le gain de base élève le plus petit
canal juste assez pour être sûr qu'à IL=0, aucune haute lumière ne sera
basée sur des données raw hors domaine (écrêtage). Comme la balance des
blancs change les gains des canaux raw, le gain de base sera donc changé
tel un effet indésirable lorsque la balance des blancs est changée. Pour
les modifications importantes de la balance des blancs, vous pouvez
apercevoir une légère variation de la luminosité de l'image. Notez que
le gain de base se rapporte à la valeur maximum que les canaux peuvent
représenter, c'est à dire que s'il n'y a pas de hautes lumières hors
domaine dans le fichier raw, aucune haute lumière n'atteindra le niveau
maximum pour IL=0.

## Compression hautes lumières

Le curseur Compression hautes lumières peut être utilisé pour récupérer
par compression les hautes lumières dans une photo, utile pour
'assombrir' (ou éclaircir) légèrement les zones surexposées. Alors que
l'outil *Reconstruction des hautes lumières* vous laisse essayer de
*régénérer* les données manquantes du fichier raw en comptant sur le
fait que les trois canaux du fichier raw ne sont pas rognés en même
temps, et ainsi une zone manquante (rognée) dans un canal peut être
devinée à partir des données présentes dans l'un des autres canaux de
couleur, cet outil *Compression hautes lumières* ne fonctionne qu'avec
les données qui sont déjà présentes, donc qui n'ont pas été perdues
irréversiblement au moment de la prise de vue. Si l'image originale n'a
aucune zone rognée, mais qu'en raison de l'action par exemple de la
Compensation d'exposition, vous avez créé un dépassement hors domaine,
alors vous pouvez utiliser la *Compression hautes lumières* pour
compresser ces zones rognées dans la partie visible. Cet outil ne
fonctionne pas que sur les fichiers raw, mais aussi sur les images
normales.

Pour savoir si votre photo comporte des zones surexposées, cliquez sur
l'icône Indication hautes lumières hors domaine
![<File:Warning-highlights.png>](Warning-highlights.png "File:Warning-highlights.png")en
haut à droite de l'image d'aperçu. Les zones surexposées apparaîtront en
noir.

<figure>
<img src="/images/Hra_0_fr.png" title="Hra_0_fr.png" />
<figcaption>Hra_0_fr.png</figcaption>
</figure>

<figure>
<img src="/images/Hra_0_chi_fr.png" title="Hra_0_chi_fr.png" />
<figcaption>Hra_0_chi_fr.png</figcaption>
</figure>

En poussant le curseur de la *Compression hautes lumières* vers la
droite, l'intensité des hautes lumières va décroître. Pour que la
Compression hautes lumières fonctionne le mieux, il faut aussi activer
la *Reconstruction des hautes lumières*. Chaque méthode de
reconstruction a ses points forts et points faibles, comme expliqué
ci-dessus. Propagation de la couleur est la méthode la plus apte à
produire des résultats probants quand le curseur Compression hautes
lumières est significativement au-dessus de 100. Pour les autres
méthodes, s'efforcer de conserver le curseur de *Compression hautes
lumières* autour ou en-dessous de 100, surveiller l'histogramme et
l'aperçu pour trouver la valeur optimale.

<figure>
<img src="/images/Hra_125_ba.jpg" title="Hra_125_ba.jpg" />
<figcaption>Hra_125_ba.jpg</figcaption>
</figure>

Pour trouver la valeur optimale de *Compression hautes lumières*
utilisez l'histogramme. Dans les captures d'écran ci-dessus, on peut y
voir des nuages surexposés au-dessus du volcan Teide à Ténérife. En
survolant avec la souris les zones surexposées, l'indicateur de valeur
des pixels (dans le panneau *Navigateur*, sous le petit aperçu) indique
que la luminosité (L) est à 100, et l'histogramme montre que tous les
canaux sont rognés (Voyez les petits carrés rouges, vert et bleu dans
l'angle supérieur droit de l'histogramme, ils indiquent qu'ils y a
tellement de pixels à la valeur maximum qu'ils sont hors échelle).
Déplacez le curseur de Compression hautes lumières jusqu'à ce que les
canaux rouge, vert et bleu de l'histogramme ne viennent plus se tasser
en butée contre le bord droit de l'histogramme, il doivent venir toucher
le bord sans s'écraser contre. Il est recommandé d'activer l*'Indication
hautes lumières hors domaine*
![<File:Warning-highlights.png>](Warning-highlights.png "File:Warning-highlights.png")
avant de déplacer le curseur Compression hautes lumières. Une fois que
les zones noires de l'indicateur ont quitté les parties blanches à
récupérer, ce qui correspond aussi à une luminosité de ces pixels
descendue de L=100 à L=99, vous arrêtez. Ne pas augmenter davantage la
Compression hautes lumières, car maintenant les zones définitivement
blanches sans espoir de récupération vont devenir grises, ce n'est pas
l'effet recherché. Cela rendrait l'image triste, sans goût. Dans cet
exemple, les zones noires de l'indicateur ont disparu avec une
Compression hautes lumières de 125.

<figure>
<img src="/images/Hra_toomuch_histogram.png"
title="Hra_toomuch_histogram.png" />
<figcaption>Hra_toomuch_histogram.png</figcaption>
</figure>

En règle générale, l'histogramme d'une image correctement développée
doit toucher les deux extrémités, la noire et la blanche. Sinon, cela
signifie que l'image n'est pas correctement développée. Ceci est vrai
pour une grande majorité de photos, les seules exceptions étant les
photos qui manquent d'étendue dynamique, par exemple les scènes
brumeuses. Si le curseur Compression hautes lumières est trop poussé,
alors les blancs deviennent gris car l'histogramme n’atteint plus la
valeur maximum. Des exemples de photos qui ont été "sur-compressées"
peuvent facilement être trouvés sur internet. Elles sont horribles, ne
faites pas cela ! Ne récupérez que ce qui est possible, ce qui est
au-delà de la réparation doit rester blanc.

RawTherapee offre d'autres moyens pour traiter les hautes lumières
brûlées. Les effets indésirables de toutes ces méthodes sont qu'ils
enlèvent aussi une partie de l'éclat des photos, qui deviennent en
conséquence « plates » ou « ternes ». La récupération des hautes
lumières est très utile si utilisée avec modération, mais rappelez vous
que vous ne pouvez pas récupérer ce qui n'est plus là, ainsi dès que
vous remarquez que les zones blanches hors domaine deviennent grises,
vous devez réduire le taux de récupération jusqu'à ce quelles
redeviennent blanches. Pour créer les plus belles images finales,
apportez à RawTherapee les meilleures images possibles, donc commencez
par les exposer correctement !

## Seuil de compression des hautes lumières

Le curseur Seuil de compression des hautes lumières définit le point où
le curseur de la Compression hautes lumières démarre la compression. Une
valeur de 0 signifie que le seuil de compression est à zéro : la
compression des données affecte toute la gamme des tonalités. 100
établit le seuil à un pas en-dessous du blanc, ainsi toutes les hautes
lumières compressées s'entassent dans le dernier pas d'en haut. En
pratique, le plus grand nombre de hautes lumières sont compressées quand
ce curseur est réglé à 0.

## Noir

Utilisez le pour fixer le point noir. Regardez bouger le coté gauche de
l'histogramme quand vous déplacez le curseur. Les valeurs supérieures à
0 assombrissent l'image, les valeurs négatives éclaircissent les parties
sombres de la photo.

## Compression des ombres

Le curseur *Compression des ombres* 'tempère' l'effet du curseur *Noir*,
la valeur maximum de 100 donne une image moins sombre. Ce curseur n'agit
que lorsque le curseur *Noir* est réglé sur autre chose que 0. En
utilisation pratique, le curseur *Compression des ombres* permet un
réglage fin de l'intensité des ombres de la photo.

## Luminosité

Ce curseur applique une courbe des tons codée en dur pour élever ou
baisser les tonalités de la photo, il en résulte une image plus ou moins
lumineuse. La même courbe des tons est appliquée séparément à chaque
canal R, V et B. Le point noir et le point blanc gardent leur position.

## Contraste

Ce curseur accroît ou diminue le contraste de la photo. Il applique une
courbe de contraste centrée sur le niveau moyen de luminance. Les
tonalités au-dessus de la moyenne sont élevées (ou baissées), alors que
les tonalités en-dessous de la moyenne sont baissées (ou élevées). La
même courbe de contraste est appliquée séparément à chaque canal R, V et
B.

## Saturation

Ce curseur rend une photo plus ou moins saturée. En termes plus
techniques, il ajuste la saturation de l'image en appliquant un
multiplicateur au niveau de saturation des pixels dans l'espace
colorimétrique TSV.

## Courbes tonales

Vous pouvez ici construire votre propre Courbe tonale. Elle agit sur les
trois canaux R, V et B en même temps (vous ne pouvez donc pas agir sur
le seul canal R).

Il y a deux courbes tonales disponibles, lesquelles peuvent être conçues
selon différents types de courbes et appliquées dans plusieurs modes
différents, toutes expliquées ci-dessous. Cliquer sur un bouton de la
courbe la fait disparaître de l'interface, cela ne la désactive pas.

L'histogramme affiché en arrière plan de la courbe vous montre le niveau
des données qui sont traitées par la courbe en ce point dans le pipeline
de traitement. Vous remarquerez qu'il diffère de l'histogramme principal
qui vous montre le niveau des données de l'image finale, à la toute fin
du pipeline.

Bien qu'il soit possible de n'utiliser qu'une seule courbe pour
effectuer les réglages, un contrôle tonal plus fin peut être atteint en
utilisant les deux courbes à la fois. L’utilisation typique des deux
courbes consiste à en utiliser une pour diminuer les valeurs et à
utiliser l'autre pour les augmenter. Cela est similaire à la création
d'une courbe en S dans l'une d'entre elles, mais vous serez capable de
réaliser des réglages plus fins en utilisant les deux sans pénétrer trop
rapidement dans la "zone dangereuse" où les couleurs deviennent
irréelles.

Il est possible de sauvegarder une courbe. Cliquer sur le bouton
*Enregistrer la courbe actuelle*
![Image:Gtk-save-large-dark.png](Gtk-save-large-dark.png "Image:Gtk-save-large-dark.png")
à côté du graphe et lui donner un nom. Utiliser le bouton *Charger une
courbe depuis un fichier*
![Image:Gtk-open.png](Gtk-open.png "Image:Gtk-open.png") pour pouvoir
appliquer cette courbe plus tard sur une autre image. Utiliser le bouton
*Réinitialise la courbe en linéaire*
![Image:Gtk-undo-ltr.png](Gtk-undo-ltr.png "Image:Gtk-undo-ltr.png")
pour effacer tous les points créés et réinitialiser la courbe au type
neutre/linéaire. Vous pouvez aussi *Copier*
![Image:Gtk-copy.png](Gtk-copy.png "Image:Gtk-copy.png") et *Coller*
![Image:Gtk-paste.png](Gtk-paste.png "Image:Gtk-paste.png") les courbes
depuis/vers le propre presse-papiers de RawTherapee, ce qui est très
pratique pour rapidement appliquer une courbe identique sur un autre
outil. Les courbes sauvegardées possèdent l'extension de fichier `.rtc`.

Autant de points de contrôle que désirés peuvent être utilisés dans une
courbe.

Des courbes peuvent être définies pour chaque type de courbe, mais
seulement celle qui est sélectionnée dans le menu déroulant est
appliquée à la photo.

La courbe et l'histogramme sont toujours affichés avec le gamma sRGB,
indépendamment des profils de travail et de sortie. Cela signifie que
l'étendue des ombres est majorée et celle des hautes lumières réduite
pour mieux correspondre à la vision humaine.

### Linéaire

![](Rt55_curve_linear.png "Rt55_curve_linear.png") Représente l'image
non modifiée (ou linéaire), donc sans application d'aucune courbe. Elle
désactive les autres courbes

  

### Personnalisé

<figure>
<img src="/images/Rt55_curve_standard.png" title="Rt55_curve_standard.png" />
<figcaption>Rt55_curve_standard.png</figcaption>
</figure>

C'est une type classique courbe Spline cubique, rencontré aussi dans
beaucoup d'autres programmes. La partie gauche du graphique représente
les tons les plus sombres de la photo et la partie droite les tons les
plus clairs. Cliquez sur la courbe pour marquer un point et déplacez le
avec la souris pour changer les tonalités. Glisser le point vers le bas
rend l'image plus sombre, alors que le pousser vers le haut la rend plus
claire. La ligne diagonale en pointillés indique l'état linéaire et non
modifié de la photo. Appuyez sur la touche **Contrôle** et maintenez la
enfoncée pour ralentir le mouvement. Appuyez sur la touche **Majuscule**
pour accrocher le point à des éléments clé : valeur maximum, valeur
minimum, valeur milieu (par exemple, accrocher la diagonale en
pointillés), même valeur que le point précédent, même valeur que le
point suivant, et pour le type *Cage de Contrôle* la ligne allant du
point précédent au point suivant. Pour effacer un point de la courbe, le
glisser en dehors du cadre de l'éditeur.

Le point supérieur droit représente la zone la plus claire de la photo.
Glissez ce point verticalement vers la bas pour rendre les hautes
lumières un peu moins claires; déplacez le horizontalement vers la
gauche pour les rendre encore plus claires, peut-être au prix d'une
surexposition.

Le point en bas à gauche, représente la zone la plus sombre de la photo.
Déplacez le horizontalement vers la droite pour rendre la photo plus
sombre, peut-être au prix d'une sous-exposition. Glissez ce point
verticalement vers le haut pour éclaircir les parties sombres.

Changer l'orientation de la courbe en déplaçant le coin bas à gauche
vers le haut à gauche et le point haut à droite vers le bas à droite
produit le négatif de l'image.  
Une utilisation typique de la courbe personnalisée est de construire une
courbe appelée *courbe en S*. Marquez trois points aux 'coordonnées'
(2,2); (5,5) et (8,8). Glissez le point situé en (2,2) un peu plus bas
et le point situé à (8,8) un peu plus haut. Votre image aura de cette
façon plus de "punch". Si la courbe en S est symétrique, par exemple si
le premier point (2,2) est déplacé de la même valeur que le (8,8) mais
dans la direction opposée, alors l'effet obtenu sera le même qu'en
utilisant le curseur *Contraste*.  

### Flexible

<figure>
<img src="/images/Rt55_curve_flexible.png" title="Rt55_curve_flexible.png" />
<figcaption>Rt55_curve_flexible.png</figcaption>
</figure>

Une caractéristique de la courbe Spline cubique "Personnalisé" est que
l'édition d'un point peut avoir, en fonction des autres points, un
impact énorme sur la courbe. La courbe Spline cubique d'Hermite
"Flexible" vous permet de réaliser des ajustements sur n'importe quelle
partie de la courbe avec peu d’impacts sur les autres parties

### Paramétrique

<figure>
<img src="/images/Rt55_curve_parametric.png"
title="Rt55_curve_parametric.png" />
<figcaption>Rt55_curve_parametric.png</figcaption>
</figure>

Cette courbe présente quatre curseurs et trois points de contrôle. Les
curseurs sont utilisés pour contrôler respectivement les hautes
lumières, les zones claires, les zones sombres et les ombres bouchées
(ici ombres bouchées signifie très foncées). Déplacez la souris
au-dessus des quatre curseurs et une zone sombre placée sur la courbe
vous indique quel curseur agit sur quelle partie de la courbe. Déplacez
le curseur *Hautes lumières* vers la gauche pour les rendre moins
claires, vers la droite pour les rendre encore plus claires. Le curseur
*Zones claires* agit sur les tons clairs mais pas sur les hautes
lumières de la même façon que ci-dessus. De même pour le curseur *Zones
sombres* : le déplacer vers la droite éclaircit les zones sombres, le
déplacer vers la gauche les assombrit. Le curseur *Ombres bouchées*
fonctionne comme le curseur *Zones sombres* mais seulement sur les
parties les plus sombres de la photo. De nouveau, vous pouvez construire
la courbe stylisée Courbe en S mentionnée ci-dessus, bien que la courbe
paramétrique vous laisse moins le contrôle 'total' sur la forme de la
courbe. Ce mode cependant, possède son intérêt, car les courbes sont
formées de façon maîtrisée. Notez que l'utilisation de ces curseurs peut
avoir une profonde influence sur le contraste général de l'image.

Si nécessaire, utilisez les trois points de contrôle situés sous la
courbe. Ils déterminent quel point de la courbe sera affecté par le
déplacement des curseurs. Déplacer le point de contrôle central vers la
droite assombrit l'image (la forme de la courbe change à nouveau, tout
comme la zone sombre autour de la courbe), le déplacer vers la gauche
l'éclaircit. Déplacer le point de contrôle gauche vers la gauche
assombrit légèrement les zones sombres, le déplacer vers la droite les
éclaircit, toujours légèrement. Déplacer le point de contrôle droit vers
la droite éclaircit les hautes lumières, vers la gauche, les assombrit.

Utiliser le bouton *Réglages par défaut*
![Image:Gtk-undo-ltr.png](Gtk-undo-ltr.png "Image:Gtk-undo-ltr.png")
auprès des curseurs pour réinitialiser les curseurs individuellement,
utilisez le même bouton en haut de la section Courbe tonale pour
réinitialiser tous les quatre curseurs et les points de contrôle à
Linéaire (zéro).  

### Cage de contrôle

<figure>
<img src="/images/Rt55_curve_control_cage.png"
title="Rt55_curve_control_cage.png" />
<figcaption>Rt55_curve_control_cage.png</figcaption>
</figure>

A première vue, cette courbe ressemble beaucoup à la courbe
*Personnalisé*, mais il y a quelques différences.

Avec la courbe *Personnalisé*, la courbe passe par tous les points de
contrôle, ce n'est pas le cas avec la courbe *Cage de contrôle*. Pour
voir cela, cliquez quelque part sur la courbe et déplacez le point noir
d'un centimètre vers la droite ou vers la gauche. Maintenant, la courbe
passe au voisinage du point noir, mais n'y passe pas. Une autre
différence est que la *Cage de contrôle* permet la création d'une
section droite sur la courbe, alors que vous ne pouvez pas faire cela
avec une courbe *Personnalisé*. Pour cela, la courbe nécessite au moins
trois points (donc cinq au total). Maintenir enfoncée la touche
**Majuscule** pendant le déplacement d'un point vous aidera à créer une
ligne droite en accrochant le point à la ligne rejoignant les points
précédent et suivant (affichés en rouge avec l'outil *accrocher*).
Maintenant créez un nouveau point entre les deux points les plus à
gauche et bougez le. Comme vous pouvez le voir, seule la partie du coté
gauche bouge, pas le reste de la courbe.  

## Mode de courbe

A côté de chaque type de courbe, se trouve une liste déroulante de *Mode
de courbe*. Cela permet de choisir l'algorithme qui sera utilisé pour la
courbe correspondante. Le mode de courbe a un effet puissant sur
l’apparence des couleurs, surtout si vous utilisez une courbe qui
rehausse le contraste (S-curve). On peut exploiter cela pour des effets
créatifs, mais cela peut aussi dans certains usages ou styles causer des
changements de couleurs indésirables selon le mode. Choisissez un mode
qui convient à vos goûts et besoins concernant une photo. En combinant
deux courbes tonales différentes, courbes 1 et 2 vous pouvez aller plus
loin dans les réglages évolués de l'aspect.

Le choix du profil de travail influence les effets de la courbe dans
tous les modes sauf le mode perceptuel, dans ce mode, changer de profil
de travail n'affectera pas les effets de la courbe.

### Standard

C'est le mode le plus simple (et le seul disponible dans les anciennes
versions de RawTherapee et on le trouve sous une forme ou une autre dans
la plupart des logiciels dédiés à l'image). Les valeurs de chaque canal
RVB sont modifiées par la courbe selon une méthode de simple
"correspondance", la même courbe est donc appliquée à tous les canaux.

L'inconvénient de ce mode est que par exemple en considérant la courbe
en S pour augmenter le contraste, une couleur orange avec une valeur
importante de rouge et de vert et une valeur faible de bleu va tendre à
se décaler vers le jaune, car les composantes rouge et verte seront
augmentées alors que la bleue sera diminuée.

En général, une courbe en S accroît la séparation des canaux et donc
accroît la saturation, ce qui est un comportement similaire à la façon
dont les films couleur réagissent au contraste. Ceci ajouté à la
simplicité de l'implantation a rendu ce type de courbe populaire dans
les convertisseurs raw en général et est souvent la seule alternative
disponible dans les logiciels moins évolués.

### Standard pondéré

Utiliser cette méthode pour limiter le décalage de la couleur de la
courbe standard, même si elle ne la supprime pas totalement. En
conservant l'exemple précédent, cette méthode va augmenter la première
composante (rouge), et modifiera aussi linéairement les composantes
verte et bleue en les augmentant aussi. Nous finissons avec trois valeur
(R, v et b) alors que nous n'avons traité que la composante rouge.

Le traitement est poursuivi pour les composantes verte et bleue, si bien
qu'à la fin nous avons neuf valeurs (R,v,b / r,V,b / r,v,B). Toutes les
valeurs de la même composante sont alors mixées ensemble, ce qui produit
une couleur résultante avec un plus faible décalage.

### Similaire Film

La courbe similaire-film fournit un résultat très similaire au type
standard (c'est à dire une forte augmentation de la saturation avec un
contrate poussé), mais la teinte RVB-TSV est gardée constante, c'est à
dire qu'il y a moins de problèmes de décalage de la couleur. Ce type de
courbe fut conçu par Adobe en tant que partie de DNG et est ainsi celui
utilisé par Adobe Camera Raw et Lightroom.

### Mixage Saturation et Valeur

Ce mode est typiquement plus adapté aux photos avec un effet high key,
mais on peut aussi bien l'utiliser pour des effets créatifs dans
d'autres photos. La valeur moyenne des trois composantes est calculée,
puis la courbe est appliquée à ces valeurs, donnant un gain positif ou
négatif. La couleur est convertie dans sa représentation en Teinte,
Saturation et Valeur, puis si le gain est positif, le pixel est
linéairement transformé en Valeur=1 et Saturation=0, la Teinte est
préservée. Si le gain est négatif, le pixel est linéairement transformé
en Valeur=0, Saturation et Teinte sont préservées.

Le résultat est très similaire à une courbe de luminance dans l'espace
colorimétrique Lab (changement du contraste sans modifier la teinte ni
la saturation). Pour les courbes d'augmentation du contraste, l'aspect
sera légèrement dé-saturé. Ce n'est pas vraiment parce que la courbe
dé-sature les couleurs mais parce que dans la vision humaine le
contraste et la saturation sont très liés, ainsi une même image avec un
contraste plus important demande une saturation plus importante pour
sembler avoir la même.

### Luminance

Chaque composant du pixel is amplifié du même facteur, ainsi la couleur
et la saturation sont stables, c'est à dire, le résultat est très fidèle
à la couleur originale. Cependant, les courbes d'accroissement du
contraste sont susceptibles de produire un aspect légèrement dé-saturé
pour la même raison que celle décrite dans le chapitre "Mode de courbe"
"Mixage Saturation et Valeur". Si vous désirez contrer la désaturation
manuellement, utiliser le curseur Chromaticité de Ajustements Lab est
plus neutre que d'utiliser le curseur saturation basé sur le RVB.

Bien que l'histogramme montré dans l'arrière plan de la courbe soit R, V
et B (réunis), la courbe travaille sur des valeurs de luminance, où la
[Luminance](https://fr.wikipedia.org/wiki/Luminance_lumineuse) Y =
R\*0.2126729 + V\*0.7151521 + B\*0.0721750

La valeur de la luminance d'un pixel est d'abord obtenue, puis la courbe
est appliquée à cette valeur, le facteur de multiplication entre avant
et après la luminance est calculé, et enfin, ce facteur est appliqué à
chaque composante R, V et B. Cela est en opposition avec les autres
méthodes où la courbe est appliquée séparément à chaque composante R, V
et B.

### Perceptual

Ce mode conserve l'apparence originale de la couleur concernant la
teinte et la saturation, c'est à dire que si par exemple vous appliquez
une courbe en S, l'image aura bien sur un contraste amplifié mais les
teintes resteront les mêmes et l'image ne semblera pas plus ou moins
saturée que l'original. C'est spécifiquement utile pour établir un
contraste de base agréable sans altérer les couleurs fournies par le
profil de l'appareil photo, lequel n'applique pas de courbe (si vous
utilisez un profil tiers qui applique vraiment une courbe, c'est déjà
typiquement du mode perceptual avec des techniques similaires à celles
décrites ici).

Le choix du profil de travail influence les effets de la courbe dans
tous les modes sauf le mode perceptuel, dans ce mode, changer de profil
de travail n'affectera pas les effets de la courbe.

L'algorithme fonctionne de la façon suivante : Il analyse la courbe pour
obtenir une valeur de contraste, qui est utilisée comme base pour régler
la chromaticité (saturation) de telle sorte que plus de contraste donne
plus de saturation et réciproquement. Comme le contraste et la
saturation sont très liés dans la vision humaine ce réglage est
nécessaire pour que la saturation "apparaisse" constante. Il y a ensuite
des réglages fins tels qu'un accroissement supplémentaire de la
saturation dans les ombres, et moindre pour les couleurs qui sont déjà
très saturées, cela correspond aussi à la vision humaine, ainsi l'effet
total est que les couleurs sembles constantes. Dans les hautes lumières
extrêmes, proches du point blanc, l'algorithme produit un mélange
au-delà du blanc (comme les courbes standards) ce qui est moins fidèle à
la couleur mais plus réaliste pour les sorties réelles vu que la couleur
la plus lumineuse du media de sortie (écran ou papier) est blanche.

Cependant, bien garder à l'esprit que le mode perceptual n'est pas
parfait et ne peut pas l'être. Ce n'est qu'une courbe, le contenu de
l'image n'est pas analysé et aucune modification locale n'est réalisée.
Cela signifie par exemple que pour une courbe en S, un vaste ciel bleu
plat (au contraste local faible) peut apparaitre légèrement plus saturé
que l'original. Si vous voulez faire des comparaisons après/avant, ne
pas comparer cote à cote, car l’œil sera alors perturbé par les deux
niveaux de contraste observés simultanément et alors la saturation
n'apparaitra pas identique, mais plutôt comparer l'un après l'autre en
laissant l’œil s'adapter pendant quelques secondes.

Si vous désirez régler plus en détail la saturation manuellement, il est
généralement préférable d'utiliser les outils chroma L\*a\*b\*.

En raison des nombreux composants dans l'algorithme, il est
considérablement plus lent que les autres modes de courbe, aussi le taux
de rafraichissement peut en souffrir.
