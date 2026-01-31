---
title: Unclipped
contributors:
  - Lebarhon
tags:
  - 'Bundled Processing Profiles'
---

<div class="pagetitle">

Sans suppression hors domaine

</div>

## Introduction

Les [Profils de
traitement](Sidecar_Files_-_Processing_Profiles/fr.md) "Sans
suppression hors domaine" (introduit par RawTherapee 5.6) permet la
sauvegarde d'une image de manière à conserver toutes les données
couvrant la gamme tonale en totalité, y compris les ombres et hautes
lumières hors domaine, autorisant ainsi sur l'image enregistrée, des
ajustements sur de fortes expositions et des compressions de la gamme
dynamique tout en conservant les détails dans les ombres et les hautes
lumières. Cela peut être souhaité pour des utilisations scientifiques
mais aussi quand l'image est destinée à une manipulation ultérieure et
que l'exposition finale est encore inconnue, comme par exemple dans le
cas d'assemblage de panoramas qui exige des ajustements d'exposition
afin que les images se soudent entre-elles sans joint apparent.

<div align="center">

<File:Batcat.jpg%7CCeci> est le fichier raw d'une scène ayant une gamme
dynamique très élevée. Remarquez que l'histogramme indique des ombres et
des hautes lumières hors domaine. <File:Batcat.jpg%7CLe> fichier raw
doit cependant contenir des données concernant toute la gamme dynamique,
y compris ces ombres et hautes lumières qui s'avèrent être hors domaine
(non visibles). Nous savons que c'est bien le cas car en ajustant la
compensation d'exposition dans RawTherapee ces détails sont révélés.
Cependant, il y a des situations où à ce stade nous devons manipuler le
moins possible les images, ce qui interdit la manipulation de la
compensation d'exposition ou d'utiliser la compression de la gamme
dynamique. <File:Batcat.jpg%7CUne> fois enregistré au format de fichier
ordinaire 16-bit TIFF, ce qui avant apparaissait hors domaine est
maintenant vraiment coupé, les données sont perdues, il est impossible
de récupérer les ombres ou les hautes lumières de ce fichier TIFF. Ici
une compensation d'exposition de -2EV a été réalisée dans GIMP, et les
résultats sont inutilisables. <File:Batcat.jpg%7CLa> solution est
d'utiliser le profil "Sans suppression hors domaine", comme décrit
ci-dessous dans la section "Usage", et sauvegarder dans un fichier TIFF
16 ou 32 bits en virgule flottante. Le fichier TIFF produit contient les
données de la gamme dynamique en entier, et même des ajustements poussés
de l'exposition montrent des détails parfaitement intacts.

</div>

Tous les outils ne sont pas utilisables en cas de sauvegarde d'une image
sans suppression hors domaine. Les outils ou paramètres suivants sont
incompatibles avec la sauvegarde d'une image sans suppression hors
domaine dans RawTherapee 5.6, et sont donc désactivés par ce profil de
traitement :

- [Courbes tonales
  d'exposition](Exposure/fr#Courbes_tonales.md),
- [Vibrance](vibrance/fr),
- Les courbes Avant/Après dans l'outil
  [Noir-et-Blanc](black-and-white/fr),
- [Simulation de Film](film_simulation/fr),
- [Courbes RVB](rgb_curves/fr) en mode luminosité,
- [Utiliser Look table de
  DCP](Color_Management/fr#Utiliser_Look_table.md),
- [Modèle d'apparence des couleurs CIE 2002 et Cat02 White
  Balance](CIECAM02/fr.md)

## Usage

1.  Appliquer le profil "Sans suppression hors domaine". Ce profil
    désactive les outils et paramètres qui sont incompatibles avec la
    sauvegarde d'images sans suppression hors domaine. Assurez vous que
    le profil ICC de sortie est soit v4, ou une courbe de réponse tonale
    linéaire v2.
    - Si vous désirez appliquer ce profil et ré-initialiser tous les
      outils à des valeurs par défaut sûres, alors régler le [mode de
      complètement du profil de
      traitement](Sidecar_Files_-_Processing_Profiles/fr#Profils_de_traitement_partiels_et_modes_de_complètement.md)
      sur "bouton pressé"
      ![<File:Profile-filled.png>](Profile-filled.png "File:Profile-filled.png")
      avant d'appliquer le profil.
    - Si vous désirez appliquer ce profil tout en préservant les
      ajustements existants, alors régler le mode de complètement du
      profil de traitement sur "bouton relevé"
      ![<File:Profile-partial.png>](Profile-partial.png "File:Profile-partial.png")
      avant d'appliquer le profil.
2.  Enregistrer l'image sous forme d'un fichier TIFF en virgule
    flottante soit en 16 bits soit en 32 bits.
