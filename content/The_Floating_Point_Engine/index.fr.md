---
title: The Floating Point Engine
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Le calcul en virgule flottante

</div>

RawTherapee réalise tous les traitements de l'image en précision 32 bits
en [virgule flottante](https://fr.wikipedia.org/wiki/Virgule_flottante)
(par opposition avec le 16 bits en nombre entiers utilisé par beaucoup
des développeurs photo comme
[dcraw](https://en.wikipedia.org/wiki/Dcraw) et aussi RawTherapee
jusqu'à la version 3.0).

Les développeurs classiques de photos fonctionnent en 16 bits nombres
entiers. Un canal de pixels contient des valeurs allant de 0 à 65535 en
précision 16 bits (pour améliorer la précision, les développeurs
complètent habituellement les valeurs en 12 ou 14 bits de l'appareil
photo pour arriver à 16 bits). Les nombres ne sont pas fractionnés,
ainsi par exemple il n'y a pas de nombres entre 102 et 103. Au
contraire, les nombres en virgule flottante contiennent des valeurs sur
une étendue beaucoup plus importante, avec une précision de 6 ou 7
chiffres significatifs. Cela est utile surtout dans les hautes lumières,
où il est possible de récupérer de plus grandes étendues de valeurs. Il
permet aussi des résultats intermédiaires dans la chaîne de traitement
pour temporairement sur-exposer ou sous-exposer sans perdre
d'informations. La possibilité d'avoir des valeurs fractionnées améliore
aussi le dégradé de couleurs en douceur et permet d'éviter les effets de
bandes.

L'inconvénient de cela est l'espace mémoire RAM exigé par les nombres en
virgule flottante, lequel est exactement le double de celui demandé par
le 16 bits en nombres entiers. Ajouté avec le nombre toujours croissant
de mégapixels utilisés par les appareils photo, un système
d'exploitation 32 bits peu très vite se retrouver en manque de mémoire
et causer le crash de Rawtherapee. Par conséquent, un système
d'exploitation en 64 bits est hautement recommandé pour garantir la
stabilité.

Nous avons officiellement arrêté le support des versions 32 bits de
RawTherapee depuis l'édition 5.0-r1 en février 2017. Ne pas faire de
rapports de bug concernant les systèmes 32 bits.

Si néanmoins vous avez besoin d'utiliser RawTherapee sur des systèmes 32
bits, ce qui suit vous aidera à en tirer le meilleur profit :

- Utilisez les fonctions 4-Gigabyte Tuning de Windows. Voir cette page
  de la bibliothèque de Microsoft pour obtenir une explication de ce
  qu'est 4-Gigabyte Tuning : "[4-Gigabyte Tuning: BCDEdit and
  Boot.ini](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)",
  et découvrez comment l'utiliser dans Windows XP, Vista et 7 en lisant
  ce quide : "[How to set the /3GB Startup Switch in Windows XP and
  Vista](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)".
- Fermez les autres programmes pour travailler avec RawTherapee
- Utilisez le [mode simple
  éditeur](Preferences/fr#Habitudes_de_travail.md).
- Arrêter l'"auto-start" dans la [file
  d'attente](The_Batch_Queue/fr.md). Ajouter les photos dans la
  file d'attente comme d'habitude. Une fois prêt à les traiter,
  redémarrer RawTherapee pour libérer de la RAM (sans image d'ouverte
  dans l’Éditeur), et démarrer la file d'attente.
- Assurez vous que RawTherapee [ne charge
  pas](Preferences/fr#Dossiers.md) les images de trame noire ni
  de champ uniforme si vous ne les utilisez pas.
- Evitez d'avoir plus d'une centaines de photos par dossier, car les
  photos exigent un peu de RAM (vignette, profil ICC intégré, etc.)

## Besoins en mémoire

Pour ouvrir une image dans l’Éditeur, RawTherapee 5.6 a besoin très
approximativement de ces quantités de mémoire, en octets :

- Non-raw
  - 8-bit:
    `(largeur * hauteur * 3) + (largeur * hauteur * 4) + (largeur aperçu * hauteur aperçu * 28)`
  - 16-bit:
    `(largeur * hauteur * 3 * 2) + (largeur * hauteur * 4) + (largeur aperçu * hauteur aperçu * 28)`
  - 32-bit:
    `(largeur * hauteur * 3 * 4) + (largeur * hauteur * 4) + (largeur aperçu * hauteur aperçu * 28)`
- Raw
  - `(largeur * hauteur * 4) + (largeur * hauteur * 4) + (largeur * hauteur * 12) + (largeur aperçu * hauteur aperçu * 28)`

Un peu de mémoire supplémentaire est nécessaire, par exemple pour
générer les vignettes ou d'autres images qui résident dans le dossier
ouvert des images.

Le besoin de mémoire pour le traitement et la sauvegarde d'une image
dépend des outils utilisés et peut s'écarter significativement des
indications ci-dessus, qui ne s'appliquent qu'à l'ouverture d'une image.
