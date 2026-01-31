---
title: Contrast by Detail Levels
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Contraste par niveaux de détail

</div>
*Contraste par niveaux de détail* utilise la décomposition en
vaguelettes pour décomposer l'image en cinq niveaux, chacun réglable par
un curseur. Le curseur 0 (les plus petits) a un rayon de pixel de 1, les
curseurs 1 à 4 ont un rayon de pixel d'approximativement 2, 4, 8 et 16
pixels. Régler un curseur en dessous de 1.0 décroit le contraste local à
ce niveau, alors que le régler sur une valeur supérieure, l'accroit.
Ainsi, vous pouvez accroitre la netteté perçue d'une image, accroitre le
contraste local ou bien atténuer certains niveaux de détail.

Gardez à l'esprit que le redimensionnement d'une image a un impact
direct sur la netteté perçue, tout comme la distance d'observation. En
pratique, cela signifie qu'on devrait utiliser cet outil sur l'image
zoomée à peu près au même niveau que celui de l'observation finale
supposée et à la même distance d'observation. Ainsi, si vous avez
l'intention d'imprimer une image en haute résolution sur un support de
90x60cm et de l'admirer à 30cm de distance, alors cela est raisonnable
de la zoomer à 100% et de peaufiner le curseur "0 (les plus petits)".
Cependant, dans la réalité de tels impressions de grande taille sont
accrochées au mur et sont observées depuis un divan distant de quelques
mètres, d'où le réglage des plus petits détails est sans effet, les yeux
ne pouvant percevoir le détail à cette distance. Il en va de même pour
les images destinées à être redimensionnées (diminution du nombre de
pixels) pour utilisation sur Internet ou en pièces jointes de courriels
pour des amis ou des clients, non seulement la définition est abaissée
mais les images seront vues sur des appareils à faible définition,
probablement même pas en plein écran, sur un portable, une tablette ou
un smartphone. Dans ce cas aussi, l'utilisation du niveau de détail "0
(les plus petits)" n'apportera aucune différence. Le plus souvent seuls
les curseurs "3" et "4" apportent un effet utile.

<img src="/images/Rt_cbdl_100.jpg" title="Rt_cbdl_100.jpg" width="900"
alt="Rt_cbdl_100.jpg" /> Par exemple, sur cette photo de 10 mégapixels,
alors que votre intention est de la regarder en pleine grandeur et
d'assez près (par ex dans une galerie d'art), dans le but d'enlever les
défauts de la peau tout en préservant sa texture, zoomer à 100% et
commencer par régler les curseurs comme suit, enfin régler finement à
son goût :

`0 (les plus petits)  : 1.4`  
`1                    : 1.4`  
`2                    : 0.4`  
`3                    : 0.4`  
`4 (les plus gros)    : 1.2`  
`Protection/Ciblage des Tons Chairs : -75`

<img src="/images/Rt_cbdl_25_1.jpg" title="Rt_cbdl_25_1.jpg" width="900"
alt="Rt_cbdl_25_1.jpg" /> Si vous désirez diminuer l'échelle de la photo
pour l'utiliser sur le Web, vous devriez la zoomer arrière d'environ
25%, ce qui est plus ou moins la taille à laquelle l'image sera
visionnée. Avec les réglages ci-dessus on peut voir que la peau est
toujours adoucie, mais si on remet les trois premiers curseurs à "1.0",
vous constatez que cela ne fait aucune différence ! la raison en est
qu'à cette définition réduite, les changements à ces niveaux sont perdus
par l'abaissement d'échelle. On aurait le même résultat en enregistrant
l'image en pleine taille puis en la réduisant ensuite de 25% dans un
autre programme quelconque, ne pensez donc pas qu'il s'agisse d'une
faiblesse de RawTherapee, c'est ainsi que la netteté fonctionne
(définition et [piqué](https://fr.wikipedia.org/wiki/Piqu%C3%A9)).
Sachant cela, si votre seule intention est de partager la version
réduite de votre photo, vous pouvez économiser du temps en ignorant les
trois premiers curseurs.

<img src="/images/Rt_cbdl_25_2.jpg" title="Rt_cbdl_25_2.jpg" width="900"
alt="Rt_cbdl_25_2.jpg" /> De plus, vous pouvez découvrir en zoomant
arrière que les curseurs apportent des effets qui n'étaient pas visibles
à 100%. Par exemple que le curseur "4 (les plus gros)" peut adoucir de
façon plaisante les grandes ombres dures, donc, le régler à 0,5 et
ajuster selon son goût.

## Traitement effectué Avant/Après *Noir-et-Blanc*

Cette liste déroulante vous permet de décider à quel moment l'outil
"Contraste par niveaux de détail" (CpND) sera exécuté dans le pipeline.
Cet outil a été ajouté il y a longtemps à RawTherapee, mais plus
récemment est arrivé l'outil Noir-et-Blanc, placé avant CpND dans le
pipeline. Avec pour conséquence imprévue que si vous activez l'outil
Noir-et-Blanc alors alors vous ne pouvez pas utiliser la fonction
Protection/Ciblage des tons chairs car une image Noir-et-Blanc ne
possède pas d'information sur la couleur de peau. Cette liste déroulante
a été ajoutée pour remédier au problème. Exécuter l'outil CpND avant
l'outil Noir-et-Blanc vous permet de cibler les tons chairs avant la
conversion en Noir-et-Blanc. Nous vous recommandons de garder l'option
par défaut, "Avant Noir-et-Blanc".

## Contraste +/- et Neutre

Cliquez sur le bouton "*Contraste-*" pour déplacer les cinq curseurs
d'une valeur prédéterminée vers la gauche (réduction du bruit). Cliquez
sur le bouton "*Contraste+*" pour déplacer les cinq curseurs d'une
valeur prédéterminée vers la droite (Netteté). Cliquez sur le bouton
"*Neutre*" pour remettre tous les curseurs à 0.

Vous avez aussi la possibilité de déplacer les curseurs individuellement
et de constater le résultat dans une fenêtre de détail. Vous pouvez
zoomer à 200% et plus pour mieux apprécier l'action du filtre.

Pour les prises de vues avec une sensibilité ISO importante (1600 et
plus), essayez par exemple de cliquer deux fois sur le bouton
"*Contraste-*" et utilisez [Netteté](sharpening/fr) \>
[Masque Flou](sharpening/fr#masque_flou) avec une Quantité de
80.

## Seuil

Le paramètre "*Seuil*" est utilisé pour éviter d'appliquer la netteté
sur le bruit : si la luminance d'un pixel ne diffère que d'un bit par
rapport à ses voisins (la différence est inférieure au seuil), alors le
filtre n'est pas appliqué. Il est possible de mettre le seuil à 0, mais
alors tout sera traité par le filtre (y compris le bruit).
