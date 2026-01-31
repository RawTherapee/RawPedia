---
title: Tone Mapping
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Compression tonale

</div>

Les effets de cet outil sont visibles à tout niveau de zoom. Cependant,
en raison de la nature de l’algorithme, seul un l'aperçu à l'échelle de
1:1 (ou plus) correspondra exactement à l'image sauvegardée. Si le zoom
est inférieur à 1:1, vous devez rester conscient que l'aperçu peut
correspondre plus ou moins bien à l'image sauvegardée, en fonction des
curseurs "*Arrêt des bords*" et "*Echelle*". Voir la section "[Faire
correspondre l'aperçu avec l'image
sauvegardée](Tone_Mapping/fr#Faire_correspondre_l'aperçu_avec_l'image_sauvegardée.md)"
ci-dessous. Utiliser une fenêtre de détail (cliquer sur l'icône
![<File:Window-add.png>](Window-add.png "File:Window-add.png") sous le
[panneau de l'aperçu
principal](The_Image_Editor_Tab/fr#Le_panneau_Aperçu.md)) pour
inspecter une partie de l'image, ou bien zoomer l'aperçu principal à
100% (aussi appelé 1:1)
![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png").

------------------------------------------------------------------------

<figure>
<img src="/images/Rt407-ba-tonemapping-hdr-cropped.jpg"
title="Rt407-ba-tonemapping-hdr-cropped.jpg" />
<figcaption>Rt407-ba-tonemapping-hdr-cropped.jpg</figcaption>
</figure>

L'outil Compression tonale peut être utilisé pour relever les zones
sombres de la photo tout en évitant l'apparition de halos, et il peut
être utilisé pour faire ressortir ou supprimer les détails, pour rendre
la photo plus vive ou plus douce. La Compression tonale ajuste le
contraste global d'une image de façon différente que le Contraste local.
Typiquement, c'est très utile pour diminuer les contrastes à grand
échelle tout en préservant (ou intensifiant) les contrastes à petite
échelle. La méthode utilisée est reprise de "Edge-Preserving
Decompositions for Multi-Scale Tone and Detail Manipulation" avec
quelques modifications.

Note : La compression tonale requiert beaucoup de mémoire (RAM) et
sollicite le CPU.

## Faire correspondre l'aperçu avec l'image sauvegardée

Image:Rt tm preview.jpg\|Arrêt des bords=1.40 et Echelle=0.10 pendant
l'édition, mais Echelle est réglée sur 1.00 juste avant la sauvegarde.
Image:Rt tm saved.jpg\|Grâce à cette astuce, l'aperçu correspond très
bien à l'image sauvegardée.

Les effets de cet outil dépendent grandement de la taille de l'image
d'entrée dans le moteur de traitement. Pour conserver un aperçu rapide,
RawTherapee fournit à chaque outil l'image que vous voyez dans l'aperçu
avec la même résolution, pas l'énorme original (cependant, lors de la
sauvegarde, il utilise l'original, énorme, c'est la raison pour laquelle
l'enregistrement prend autant de temps). Traiter une image de 900x600
est beaucoup plus rapide qu'une de 7360x4912. Les effets indésirables de
cela sont qu'un aperçu en zoom arrière (rétréci) peut ne pas
correspondre à l'image sauvegardée, en fonction des curseurs "*Arrêt des
bords*" et "*Echelle*".

Les valeurs par défaut de cet outil sont Arrêt des bords=0.5 et
Echelle=0.10. Ces valeurs donnent généralement de bons résultats et un
aperçu très représentatif de l'image sauvegardée. Si vous désirez
ajuster ces valeurs, vous devrez traiter l'image complète à chaque fois
que vous les changez afin de vous assurer que leurs effets sur l'image
de sortie enregistrée correspond à ce que vous avez en tête. Une façon
commode de simplifier cette tâche consiste à paramétrer un visualiseur
d'image avec "[Editeur
externe](Preferences/fr#Editeur_externe.md)", ainsi, il suffit
de taper le raccourci Ctrl+e pour que RawTherapee traite complétement
l'image et l'affiche automatiquement dans le visualiseur.

Rappelez vous que si vous zoomez l'aperçu à 100%, il correspondra
exactement à l'image sauvegardée indépendamment des valeurs de curseur
utilisées.

  

## Description de l'Interface

### Force

Contrôle la force globale de l'effet. A partir de la version 4.2.156,
lorsque vous augmentez la force, les ombres sont relevées et les hautes
lumières sont légèrement abaissées de façon à conserver la luminosité
moyenne de l'image et donc d'éviter l'aspect délavé.

### Gamma

Gamma déplace l'action de la compression tonale vers les ombres ou les
hautes lumières.

### Arrêt des bords

Ce paramètre détermine la sensibilité des bords, plus il est élevé, plus
un changement d'éclairage sera assimilé à un "bord". S'il est mis à
zéro, la compression tonale aura un effet similaire a celui du [masque
flou](https://fr.wikipedia.org/wiki/Masque_flou).

### Echelle

Ce contrôle définit la différence entre contraste "local" et "global",
plus il est élevé, plus un détail doit être grand pour être intensifié.
Voir la note ci-dessus sur l'influence de ce paramètre sur les
différences entre aperçu et image sauvegardée.

### Itérations de la pondération

Certaines fois, la compression tonale peut provoquer un aspect 'dessin
animé', et dans certains cas rares, des halos doux mais grands, peuvent
apparaître. Augmenter le nombre d'Itérations de la pondération peut
aider à combattre ces problèmes. Quand plus de zéro Itérations de la
pondération sont utilisées, les meilleurs résultats sont obtenus si le
paramètre *Arrêt des bords* est réglé sur un (détail technique : Cela
provient d'une approximation de calcul de l'adoucissement en utilisant
itérativement la pondération des moindres carrés). Les artéfacts dans
les bords de contraste élevé peuvent commencer à apparaitre quand cette
valeur est établie à 1.8 ou plus.
