---
title: Film Negative
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Film Négatif

</div>

## Introduction

Les négatifs sont des images dont les luminosité et teintes sont
inversées, comme celles produites par les appareils photo à pellicules.
L'outil Film Négatif a été introduit dans RawTherapee 5.7 pour
simplifier le développement de photos raw de négatifs.

L'outil prend en charge les photos raw produites par un capteur de type
Bayer ou X-Trans. Les autres types de raw et les formats non-raw ne sont
pas supportés.

Dans l'image négative, la valeur de chaque canal est proportionnelle à
une puissance de l'inverse du canal correspondant dans l'exposition
originale (pour plus d'informations, voir [Photographic Film -
Basics](https://en.wikipedia.org/wiki/Photographic_film#Film_basics)).
La valeur de chaque canal est élevée à une puissance différente, selon
le type de pellicule, son age et éventuellement d'autres facteurs tels
que les conditions de prise de vue. Ces exposants peuvent être spécifiés
dans le but d'obtenir une meilleure adaptation du procédé de correction
aux caractéristiques de chaque pellicule. Pour simplifier les réglages
manuels, les trois exposants R, V, B sont spécifiés comme étant un
exposant de "référence" (qui est appliqué au Vert), et deux ratios par
rapport à la référence pour les exposants du Rouge et du Bleu. Les
valeurs par défaut produisent en principe de bons résultats sans
modification avec les pellicules usuelles de Kodak comme celles de type
ColorPlus 200 ou Gold 200.

## Utilisation

1.  Ouvrir la photo raw d'un négatif.
2.  Dans l'onglet Raw, activer l'outil Film Négatif.
3.  Optionnellement, vous pouvez essayer d'établir automatiquement des
    valeurs plus précises des proportions de rouge et de bleu. Pour
    cela, cliquer sur le bouton "Sélectionner des points neutres", puis
    cliquer sur un point neutre clair puis foncé dans la photographie.
    :\* Ces points doivent avoir été des points dépourvus de teinte dans
    la scène originale, ils doivent être neutres. Gardez à l'esprit
    qu'ils peuvent ne pas apparaître neutres dans votre négatif de la
    photo jusqu'à l'utilisation de l'outil [Balance des
    blancs](White_Balance/fr.md).

    :\* Les points doivent avoir des luminosités différentes sans être
    hors domaine.

      
    La sélection des points ne doit se faire qu'une fois par rouleau de
    pellicule, ensuite le profil de traitement peut être copié/collé
    dans les autres photos de la même pellicule. Cela vous permet de
    choisir n'importe qu'elle image de toute la pellicule pour
    sélectionner les points neutres.
4.  Régler la Balance des blancs de la photo. Prélever la balance des
    blancs depuis un point qui doit être de teinte neutre, s'il en
    existe un, est le plus simple.
      
    La sélection des points neutres change la valeur des données raw
    dans le [pipeline](toolchain_pipeline/fr) avant l'action
    de l'outil balance des blancs, cependant il est recommandé
    d'utiliser la balance des blancs sur la photo après la sélection des
    points neutres. Si vous procédez à l'inverse, c'est correct aussi
    mais vous serez peut-être amené à utiliser à nouveau la balance des
    blancs par la suite.

Voilà comment opérer en ce qui concerne la correction des images
négatives. Continuer les réglages de la photo exactement comme si
c'était une photo raw "positive" normale.

## Interface

### Exposant de référence (contraste)

Exposant appliqué au canal Vert et proportionnel aux autres exposants
appliqués aux canaux Rouge et Bleu. La modification de cette valeur
change le contraste général de l'image sans impacter les couleurs. La
valeur par défaut convient à une image négative de contraste moyen. Dans
le cas d'une image négative très peu contrastée ou incorrectement
exposée, il est possible que cette valeur doive être augmentée. Dans le
cas d'une image négative très contrastée, l'image positive, après
conversion, peut atteindre des valeurs hors domaine, aussi, aussi cette
valeur devra être diminuée.

### Ratio Rouge

Ratio entre l'exposant du canal Rouge et l'exposant de référence. Ce
coefficient indique avec quelle intensité "fléchit" la courbe de
transfert du canal Rouge, en respectant la courbe de transfert du canal
Vert. La modification de cette valeur change les caratéristiques de
couleur de la correction, tout en préservant le contraste général de
l'image.

### Ratio Bleu

Ratio entre l'exposant du canal Bleu et l'exposant de référence. Ce
coefficient indique avec quelle intensité "fléchit" la courbe de
transfert du canal Bleu, en respectant la courbe de transfert du canal
Vert. La modification de cette valeur change les caratéristiques de
couleur de la correction, tout en préservant le contraste général de
l'image.
