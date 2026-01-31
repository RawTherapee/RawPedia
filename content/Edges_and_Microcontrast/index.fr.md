---
title: Edges and Microcontrast
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Bords et Microcontraste

</div>

__TOC__

## Généralités

Contrairement à *[Masque flou](sharpening/fr#masque_flou)*,
*Bords* est un vrai algorithme de netteté. Il n'introduit pas de halos,
il peut être utilisé sur les images bruitées et il fonctionne dans
l'espace colorimétrique Lab. *Bords* accentue les arêtes uniquement et
peut être complété par *Microcontraste* pour rehausser la texture.

Le concepteur des 2 algorithmes (Bords et Microcontraste) est [Manuel
Llorens](https://github.com/ManuelLlorens).

## Bords

Cet outil effectue un renforcement de la netteté (ou **sharpening**) des
bords présentant un contraste suffisant pour être interprétés comme des
bords *ciblés*. En d'autres termes, il améliore la netteté des bords
déjà nets, ignorant les bords qui ont trop peu de contraste. Il est
important de noter que l'algorithme n'est pas perturbé par le bruit de
l'image et qu'il ne génère pas de halos.

Ce type d'amélioration de la netteté peut donner aux bords un aspect un
peu artificiel, comme s'ils étaient découpés. En outre, si les
paramètres sont trop élevés, les bords résultants pourront présenter un
effet d'escalier[Aliasing](https://en.wikipedia.org/wiki/Aliasing)..
C'est pourquoi vous devez être prudent lorsque vous l'appliquez à des
images aux bords incurvés. Cependant, lorsque les lignes droites
prédominent (surtout si elles ne sont pas diagonales) - c'est le cas
notamment en architecture - l'algorithme "bords" apporte une
accentuation notable de la netteté.

Les meilleurs résultats sont obtenus :

1.  Itérations : nombre d'itérations que l'algorithme effectue. Un
    nombre élevé produit un effet trop accentué aux environs des bords.
    Dans certains cas, avec une valeur de *2* ce problème est déjà
    observable. En général, " 1 ou 2 itérations " donnent les meilleurs
    résultats.
2.  Quantité : nombre de pixels adjacents à analyser pour un bord. Des
    valeurs plus élevées produisent des bords plus nets et un effet
    "dents de scie" plus important.
3.  Luminance uniquement: l'outil fonctionne dans l'espace couleur
    L\*a\*b\* et cette option renforce uniquement "L"

<figure>
<img src="/images/edges.jpg" title="edges.jpg" />
<figcaption>edges.jpg</figcaption>
</figure>

Information supplémentaire ici :
<https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en>

## Microcontraste

"Microcontraste" peut être défini comme le contraste sur un pixel
level[1](https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en#comment-306),
par opposition au "contraste local" qui concerne le contraste entre des
zones plus grandes (de plus basse fréquence).

L'outil Microcontraste augmente le contraste d'un pixel par rapport à
ses voisins, ce qui entraîne une augmentation apparente de la texture.
L'intention est de permettre de récupérer la texture perdue en raison de
la réduction du bruit. Il n'introduit pas de halos.
[2](https://web.archive.org/web/20100324142513/http://www.rawness.es/contraste-local-y-microcontraste/?lang=en)

<figure>
<img src="/images/seagull-microcontrast.jpg"
title="seagull-microcontrast.jpg" />
<figcaption>seagull-microcontrast.jpg</figcaption>
</figure>

Les contrôles de l'outil sont progressifs et vous permettent de choisir
un équilibre entre l'augmentation du contraste au niveau des pixels et
l'apparition d'artefacts :

- Seuil de contraste : définit le contraste minimum à partir duquel
  l'outil agira sur les pixels.
- Quantité : intensité de l'effet. Plus la valeur est élevée, plus la
  différence entre les pixels est importante.
- Uniformité : à gauche, l'algorithme tend à respecter les gradients de
  contraste initiaux. Vers la droite, les contrastes sont plus intenses
  et les gradients de contraste initiaux sont ignorés, ce qui rend
  l'image plus dure.
- Matrice : définit la zone qui sera utilisée pour calculer la variation
  de contraste. Il y a deux possibilités, une matrice de 3x3 pixels
  autour du pixel analysé, ou une matrice de 5x5 pixels. Par défaut, ce
  sera 5x5, donnant un effet plus intense, la matrice 3x3 sera plus
  appropriée pour les images bruyantes.
