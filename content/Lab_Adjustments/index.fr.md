---
title: Lab Adjustments
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Ajustements L\*a\*b\*

</div>

<figure>
<img src="/images/Lab_color_space.png" title="Lab_color_space.png" />
<figcaption>Lab_color_space.png</figcaption>
</figure>

[Lab](https://en.wikipedia.org/wiki/Lab_color_space) (aussi appelé
CIELAB ou L\*a\*b) est un espace colorimétrique tri-dimensionnel conçu
pour se rapprocher de la vision humaine, alors que RVB est utilisé pour
modéliser les couleurs fabriquées par des périphériques physiques plutôt
que la perception visuelle de l'homme. Il définit la tonalité (aussi
appelée luminosité ou valeur) séparément de la couleur, ainsi il est
possible d'en régler une sans changer l'autre.

- La composante L est très proche de la perception humaine de la
  luminosité.
- La composante a positionne la couleur entre vert et magenta.
- La composante b positionne la couleur entre jaune et bleu.

## Luminosité

Quand vous utilisez le curseur Luminosité de la section Lab, une courbe
tonale est appliquée au canal L de l'espace colorimétrique Lab. Comme
pour le curseur Luminosité de la section Exposition ci-dessus, ni le
point noir, ni le point blanc ne bougent.

## Contraste

Le curseur Contraste de la section Lab accroît ou diminue le contraste
de la photo, également appliqué au canal L. En termes de développement :
ce curseur applique une courbe de contraste centrée sur le niveau moyen
de luminosité. Les tonalités au-dessus du niveau moyen sont augmentées
(abaissées) alors que les tonalités au-dessous du niveau moyen sont
abaissées (augmentées).

## Chromaticité

Le curseur Chromaticité de la section Lab accroît ou diminue la
chromaticité de la photo en appliquant une courbe de contraste aux
canaux a et b de l'espace colorimétrique Lab. Positionner ce curseur à
-100 retire toutes les couleurs, donnant une image noir et blanc. La
meilleure façon de convertir une image en noir et blanc est d'utiliser
l'outil *Noir et blanc*, dédié et puissant, qui se trouve dans l'onglet
*Couleur*.

## Mode N&B colorisable

Cette case à cocher, "*Mode N&B colorisable*" est obsolète depuis la
version 4.0.12 et est remplacée par l'outil *[Noir et
Blanc](Black-and-White/fr.md)* qui se trouve dans l'onglet
*Couleur*. Pour des raisons de compatibilité descendante, lors de
l'ouverture de profils de traitement où *Mode N&B colorisable* était
utilisé, le curseur *Chromaticité* ira automatiquement sur -100,
fournissant le même effet.

## Eviter les dérives de teinte

Fait correspondre les couleurs de l'image avec le gamut de l'espace
colorimétrique de travail et applique la [correction de
Munsell](https://fr.wikipedia.org/wiki/Nuancier_de_Munsell) pour
conserver la pureté de la couleur.

## Restreindre LC aux tons rouge et peau

Si activé, il restreint les effets de la courbe *Luminosité en fonction
de la chromaticité' (*LC''), ainsi on peut rendre une peau plus belle
(en augmentant la luminosité de la peau) sans changer l'aspect des
vêtements du modèle ni l'arrière plan.

## Protection des tons rouges et chair

Si activé, les effets du curseur Chromaticité et de la courbe CC ne
seront pas appliqués aux couleurs de peau, ainsi il est possible
d'accroître la chromaticité de la photo sans provoquer un apparence
sur-saturée de la peau.

## Courbes

Ajustements Lab fournit une richesse de courbes pour agir sur l'aspect
de l'image. Des explications pour chaque courbe sont illustrées
ci-dessous.

### Courbe L

![](Lab_L_BA_fr.png "Lab_L_BA_fr.png") La courbe L permet le contrôle de
la luminosité de sortie basée sur la luminosité d'entrée, L = f(L).
L'histogramme sur la courbe L reflète la luminosité après les
ajustements Lab. Cette courbe vous permet de contrôler la luminosité
sans affecter les couleurs.

Une courbe en forme d'S appliquée au canal L accroît le contraste de
l'image. Cela conduit en même temps à un perceptible aspect désaturé.
Des ajustements de chromaticité peuvent être utilisés pour compenser
cela.  

### Courbes "a" et "b"

Les courbes "a" et "b" permettent le contrôle des canaux de sortie "a"
et "b" en fonction des canaux d'entrée respectivement "a" et "b", a =
f(a) et b = f(b).

Comme indiqué par les barres de couleur, la courbe "a" permet de décaler
les couleurs entre le vert et le magenta, et la courbe "b" entre le bleu
et le jaune. Cela peut être utilisé pour créer des effets colorés.  

#### Mode N&B colorisable

Coloriser une image noir et blanc peut se faire selon l'une de ces deux
méthodes : Celle qui est recommandée et la plus intuitive utilise
l'outil [Virage Partiel](color_toning/fr#noir_et_blanc) en
combinaison avec l'outil Noir et Blanc. L'autre moins puissante, utilise
les courbes a\* et b\* de l'outil Ajustements L\*a\*b\* une fois l'image
dé-saturée. La raison pour laquelle nous continuons à décrire comment
opérer sans utiliser les outils Noir et Blanc et Virage Partiel est que
ces outils sont relativement nouveaux dans RawTherapee, et peut-être que
vous préférez encore utiliser votre vieille version dépourvue de ces
outils.

Lisez comment coloriser une image Noir et Blanc selon la méthode
recommandée sur la page de l'outil [Virage
Partiel](Color_Toning/fr#Noir_et_Blanc.md). Ce chapitre ci
décrit le mode opératoire de la méthode utilisant les courbes a\* et
b\*.

Vous devez d'abord rendre l'image noir et blanc. C'est réalisable par
n'importe quelle méthode disponible : soit avec l'outil Noir et Blanc,
ou en diminuant la saturation dans l'outil Exposition, ou en diminuant
la chromaticité dans l'outil Ajustements L\*a\*b\*. chaque outil donnera
un effet différent car ils travaillent selon différentes méthodes et
dans différents espaces colorimétriques. Ce n'est qu'une question de
goût. Une fois l'image réduite en niveaux de gris, vous pouvez donner
une tonalité à l'image en utilisant les courbes a\* et b\*.

Pour seulement copier la tonalité d'une image à l'autre, copier le
profil de traitement en cours dans le presse-papiers
![Image:Gtk-copy.png](Gtk-copy.png "Image:Gtk-copy.png"), puis le coller
partiellement soit par un clic droit sur une photo dans le "Navigateur
de fichiers" puis sélectionner "*Opérations sur les profils \> Coller
partiellement*", ou bien, depuis l'onglet *Editeur* par un contrôle+clic
sur "*Colle le profil dans le presse papiers*"
[image:Gtk-paste.png](image:gtk-paste.png) pour ne coller que
la partie *Ajustements L\*a\*b\** du profil. Notez que les autres
ajustements de la section *Ajustements L\*a\*b\** seront copiés aussi.
De même, les courbes a\* et b\* peuvent être copiées/collées
individuellement. Ceci est une autre raison pour utiliser la méthode
recommandée, car il est plus facile, pus précis, de copier et coller les
outils Virage Partiel et Noir et Blanc.  

### Courbe LT

![](Lab_LH_BA_fr.png "Lab_LH_BA_fr.png") La courbe LT (luminosité en
fonction de la teinte) permet de modifier la luminosité en fonction de
la teinte. Pour éclairer certaines couleurs, bouger le point désiré sur
la courbe LT vers le haut, et pour assombrir, vers le bas.  

### Courbe CT

![](Lab_CH_BA1_fr.png "Lab_CH_BA1_fr.png") La courbe CT (chromaticité en
fonction de la teinte) permet de contrôler la chromaticité de sortie en
fonction de la teinte d'entrée, C=f(T). Grâce à elle, vous pouvez très
facilement dynamiser ou éteindre certaines gammes de couleurs de votre
choix.  

### Courbe TT

![](Lab_HH_BA_fr.png "Lab_HH_BA_fr.png") La courbe TT (teinte en
fonction de la teinte) permet de modifier la teinte d'une teinte
spécifiée. Par exemple, il est possible de relever les rouges vers plus
d'orange en bougeant le point rouge jusqu'à la ligne horizontale épaisse
qui apparaît alors que le point en déplacement devient de la couleur
désirée. RawTherapee possède deux courbes TT, une parmi les outils Lab,
dans l'onglet Exposition, et l'autre dans l'outil TSV de l'onglet
Couleur. La courbe TT des outils Lab offre une gamme de couleurs
d'étendue réduite, comparée à la courbe TT de l'égaliseur TSV, afin
d'autoriser des ajustements plus fins. La gamme s'étend entre les
couleurs précédente et suivante, par exemple, le vert peut être changé
par une couleur entre jaune et bleu (comme vous pouvez le voir sur la
copie d'écran ci-dessus). C'est pratique, par exemple, pour un réglage
fin de l'apparance tonale de la peau, retirant un aspect vertdâtre pâle
en décalant les rouges et les jaunes un peu vers le magenta.  

### Courbe CC

La courbe CC (chromaticité en fonction de la chromaticité) permet de
contrôler la chromaticité de sortie en fonction de la chromaticité
d’entrée, C=f(C). L'histogramme sur la courbe CC représente la
chromaticité avant l'ajustement. Ceci permet de régler séparément la
chromaticitè de pixels de basse et haute saturation, ainsi, il est
possible d'amplifier la saturation où c'est nécessaire sans créer de
dépassement dans les zones déjà saturées.

Image:Lab_CC_BA1.jpg\|Amplification de basse chromaticité, réduction de
haute chromaticité. Image:Lab_CC_BA2.jpg\|Réduction de basse
chromaticité. Image:Lab_CC_BA3.jpg\|Réduction de basse chromaticité.

Vous pouvez utiliser le bouton Montrer/Cacher l'histogramme de
Chromaticité
![<File:Histogram-gold-on-small.svg>](Histogram-gold-on-small.svg "File:Histogram-gold-on-small.svg")
à côté de l'histogramme pour vous aider à voir sur l'histogramme les
effets des actions avec la courbe CC, et ainsi trouver la valeur
maximale avant de commencer l'écrêtage des couleurs.

Image:Lab_CC_hist_neutral.png\|Histogramme de chromaticité doux avec une
courbe CC neutre. Image:Lab_CC_hist_clipped.png\|Histogramme de
chromaticité pointu avec une courbe CC trop accentuée.

La copie d'écran montre à quoi ressemble l'histogramme de chromaticité
de l'image non modifiée, puis ce qui arrive si l'on augmente la
chromaticité de trop (vous pouvez faire cela en utilisant le curseur
Chromaticité, ou comme dans la copie d'écran, en glissant vers la gauche
le point en haut à droite de la courbe CC. Maintenir la touche Majuscule
enfoncée pendant le déplacement aide à maintenir le point tout en haut).

Pour trouver l'augmentation maximum de chromaticité admissible, sans
causer d'effets mauvais, qui apparaîtront soudainement sous forme de
zones plates de couleur dans l'image, comme de la postérisation, tout ce
que vous avez à faire est de cliquer sur le bouton Montrer/Cacher
l'histogramme de Chromaticité, si ce n'est déjà fait, puis d'augmenter
lentement la chromaticité jusqu'au début de la formation de piques dans
l'histogramme. Bien sûr, la courbe n'a pas à être linéaire.

### Courbe LC

La courbe LC (luminosité en fonction de la chromaticité) permet de
contrôler la luminosité de sortie basée sur la chromaticité d'entrée, L
= f(C). Vous pouvez l'utiliser sur les portraits pour éclaircir la peau.

Image:Lab LC BA1.jpg\|Eclaircissement de zones de faible chromaticité.
Image:Lab LC BA2.jpg\|Eclaircissement de la peau.

L'action de la courbe LC est modulée par la case à cocher *Restreindre
LC aux tons rouge et peau*. Ainsi la courbe LC fournit un contrôle
complexe de l'image, modification de la luminosité basée sur la
chromaticité de l'image et aussi ciblée sur une gamme définie de
teintes. Avec cette option activée, la luminosité des seuls tons rouges
et chairs est affectée, permettant par exemple de rendre une peau plus
belle et dissimuler des rides et des imperfections tout en préservant la
couleur des vêtements du modèle et de l'arrière plan. Si elle est
désactivée, la courbe LC agit aussi sur les autres couleurs.

La couleur de la barre sur l'axe horizontal de la courbe LC change pour
refléter les couleurs sur lesquelles s'applique la courbe, tel que
choisi par la case à cocher Restreindre LC aux tons rouge et peau.

### Courbe CL

La courbe CL (chromaticité en fonction de la luminosité) permet le
contrôle de la chromaticité de sortie en fonction de la luminosité
d'entrée, C=f(L). Elle permet de contrôler séparément la chromaticité de
certaines zones de l'image en fonction de leur luminosité, ainsi vous
pouvez par exemple diminuer la chromaticité des ombres si elles sont
bruitées où dans un but artistique, ou bien accroitre la chromaticité
des ombres et demi-tons sans impacter le ciel lumineux.

Image:Lab CL BA1.jpg\|Accroissement de la chromaticité de zones claires
sans saturer les ombres. Image:Lab CL BA2.jpg\|Accroissement de la
chromaticité des ombres et demi-tons sans saturer le ciel.
