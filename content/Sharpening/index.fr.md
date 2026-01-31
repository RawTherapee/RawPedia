---
title: Sharpening
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Netteté

</div>
Cet article décrit l'outil appelé "Netteté", cependant, RawTherapee
contient d'autres outils utilisables pour travailler sur différents
types de netteté. Voir les outils [Bords et
Microcontraste](Edges_and_Microcontrast/fr.md) et
[Ondelettes](wavelets/fr).

L'outil Netteté est appliqué à l'image entière **avant** l'outil
[Redimensionnement](resize/fr). Si vous préfériez appliquer
l'outil netteté **après** le redimensionnement, utilisez l'outil
[Post-Resize Sharpening](resize/fr#post-resize_sharpening)
que vous trouverez à l'intérieur de l'outil redimensionnement.

## Masque Flou

[Masque flou](https://fr.wikipedia.org/wiki/Masque_flou) (USM) est une
technique utilisée pour accroitre le
[piqué](https://fr.wikipedia.org/wiki/Piqu%C3%A9) apparent (contraste
des arrêtes) d'une image, la faisant apparaître plus claire, même si
techniquement cela n'augmente pas vraiment la netteté. Plusieurs
phénomènes du système visuel humain sont exploités pour accomplir cet
effet, tels que l'[illusion de
Cornsweet](https://fr.wikipedia.org/wiki/Illusion_de_Cornsweet) et les
[Bandes de Mach](https://fr.wikipedia.org/wiki/Bandes_de_Mach). Bien que
le masque flou dans d'autres logiciels soit facilement sujet aux
[halos](https://en.wikipedia.org/wiki/Haloing), RawTherapee dispose d'un
curseur de seuil, unique, qui permet d'obtenir de superbes effets de
netteté avec un risque minimum de halos.

### Rayon

Le *Rayon* détermine la taille des détails devant être amplifiés et, en
conséquence, est lié à la largeur du halo de netteté. En général, la
qualité de la netteté est meilleure si le rayon de netteté est petit.
Pour les images de faible ISO qui sont correctement focalisées et sans
flou de bougé, une valeur de 0,5 à 0,7 est satisfaisante.

### Quantité

Le paramètre *Quantité* contrôle la force avec laquelle agit l'outil
Netteté.

### Seuil

[image:Usm_threshold.png](image:usm_threshold.png) L'outil
*Seuil* aide à la suppression de l'amplification du bruit et des halos
et à limiter l'action de l'outil Netteté à l'intérieur de la gamme
tonale désirée. L'outil Seuil permet de créer une courbe via laquelle
l'outil Netteté est appliqué. L'axe vertical correspond à l'opacité :
0 % en bas (transparent, netteté non visible), 100 % en haut (opaque,
netteté visible). L'axe horizontal correspond à la luminosité : définir
la gamme tonale à traiter par l'outil Netteté, les tons les plus sombres
sont à gauche, évoluant vers les tons clairs à droite. Comme indiqué
dans la fenêtre pop-up d'aide, pour bouger individuellement les points
de l'outil Seuil, maintenir la touche Shift (Majuscule) appuyée avant de
cliquer sur le point. Maintenir appuyée la touche Ctrl pendant le
déplacement d'un point pour faciliter un positionnement très précis.

Si on déplace la paire droite de curseurs vers la gauche, l'effet
netteté est réduit dans les hautes lumières. Si on déplace la paire
gauche de curseurs vers la droite, l'effet netteté est réduit dans les
ombres et minimise l'amplification du bruit sombre.

Les valeurs par défaut du seuil évitent la "sur-netteté" et les halos
dans la plupart des cas et limitent l'effet netteté aux tons
intermédiaires. Dans l'exemple en copie d'écran, les tons les plus noirs
n'ont pas de masque flou d'appliqué, puis le masque flou est appliqué à
un large éventail de tons du sombre à la lumière, et la force du masque
flou est graduellement diminuée depuis le maximum dans les tons
intermédiaires jusqu'à zéro dans les tons les plus clairs, ceci pour
éviter l'amplification du bruit et les halos.

### Améliorer seulement les bords

Si vous activez "*Améliorer seulement les bords*", alors les zones
uniformes ne seront pas affectées par l'outil Netteté. Ceci est utile
dans le cas photos bruitées.

Deux nouveaux curseurs apparaissent :

#### Rayon

Le *Rayon* est utilisé pour la détection du bruit. Si le bruit est
faible, un Rayon plus petit peut être utilisé et vice versa. Un Rayon
plus grand allonge le temps de traitement.

#### Tolérance des bords

*Tolérance des bords* détermine de combien un pixel doit différer de son
voisin pour être considéré comme un bord et non comme du bruit. C'est
très similaire au paramètre *Seuil* de la méthode USM, et a un fort
impact sur la qualité visuelle. Pour les images prises avec une faible
sensibilité ISO (faible bruit), réglez le curseur à 1000 ou moins, pour
des images prises à de hautes sensibilités ISO, réglez le à 2500-3000
voire plus.

### Contrôle du halo

*Contrôle du halo* est utilisé pour éviter l'effet de halo autour des
objets lumineux induit par un rehaussement de la Netteté très agressif.
Lorsqu'il est activé, un nouveau curseur apparaît.

#### Quantité

A 100, il agit au maximum, réduisant l'impact visuel du filtre USM.

## Déconvolution de Richardson-Lucy

[Déconvolution de
RL](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
du nom des développeurs de l'algorithme, Richardson et Lucy. Il utilise
la [Fonction d'étalement du
point](https://fr.wikipedia.org/wiki/Fonction_d%27%C3%A9talement_du_point)
(Point spread function ou PSF en anglais) pour annuler les effets du
flou de type gaussien. Dans la réalité, le flou produit par l'objectif
ou par le bougé diffère de façon significative du flou gaussien, en
conséquence, certains artefacts tels que des halos, peuvent apparaître
quand le rayon s'écarte de trop du type de flou affectant l'image, et
quand les effets sont trop intenses.

### Rayon

Le rayon définit l'[écart
type](https://fr.wikipedia.org/wiki/%C3%89cart_type) (sigma) du [flou
gaussien](https://en.wikipedia.org/wiki/Gaussian_blur) dans l'image.
Trouvez la valeur correcte au travers d'essais et d'erreurs.

### Quantité

Détermine le taux de mélange entre l'image non traitée pour la netteté
et l'image traitée.

### Amortissement

L'amortissement réduit les effets de la déconvolution à chaque
itération. Il empêche le traitement de netteté sur les détails les plus
fins. A utiliser si l'image traitée a trop de "mordant" au niveau le
plus fin.

### Itérations

RL Deconvolution est un algorithme itératif; il nécessite d'être répété
pour atteindre les résultats escomptés. Chaque répétition du procédé est
appelé une "itération", et chaque résultat d'une itération est utilisé
comme point de départ pour l'itération suivante. Alors que chaque
itération enlève du flou, elle augmente aussi le temps du traitement et
la probabilité de voir un halo apparaître, vous devez donc trouver le
parfait équilibre au travers d'essais et d'erreurs. La valeur par défaut
devrait convenir dans la plupart des cas.
