---
title: Le Générateur de Profil ICC
contributors:
  - Jdc
  - Lebarhon
  - DrSlony
tags:
  - 'General Information'
---


## Introduction


![](rt55_icc_profile_creator.png)


Le Générateur de Profil ICC vous permet de créer vos propres profils
ICC. Vous pouvez aussi bien utiliser des pré-réglages standards que des
valeurs personnelles.

Utilisation du générateur de profil ICC RawTherapee peut générer des
profils de sortie, ou des profils d'écran, ou des profils de travail
personnalisés en n'utilisant que la matrice XYZ générée pour le profil
[Profils
personnalisés](color_management#adding-custom-working-profiles)

Bien que vous ne puissiez pas régler absolument tous les aspects d'un
profil ICC - comme par exemple les tags A2B ou B2A - avec cet outil,
vous pouvez ajuster les plus importants pour un photographe : les
couleurs primaires, la courbe de reproduction des tons et le point blanc
(illuminant).

Vous pouvez générer des profils conformes aux normes ICC versions 2 et
4, et dans les deux cas vous pouvez utiliser des primaires
personnalisées, modifier l'illuminant ainsi que la courbe de
reproduction des tons (TRC).

Le code utilisé ainsi que les principes de base sont proches des
"Abstract profiles" [Profils
abstraits](color_management#profils-abstraits)

## Comment utiliser le générateur de profils

Pour accéder à la boîte de dialogue du générateur de profil, cliquez sur
le bouton situé à côté des boutons Préférences et
Aide(![<File:Gamut-plus.png>](Gamut-plus.png "File:Gamut-plus.png")) à
l'extrême gauche ou en haut de la fenêtre RawTherapee.

Pour que les profils créés soient disponibles à l'usage dans
RawTherapee, les enregistrer dans le répertoire standard des profils de
couleurs de votre système d'exploitation tel que défini dans Préférences
\> [L'onglet Gestion des
couleurs](Preferences#longlet-gestion-des-couleurs).

### Les couleurs primaires

Ces 3 couleurs - Rouge, Vert, Bleus - sont dans une synthèse additive -
la base de la composition de toutes les autres couleurs. Dans le
générateur de profil ICC, vous spécifiez l'emplacement de ces couleurs
primaires au moyen de coordonnées correspondant au diagramme de
chromaticité CIExy de 1931.

[Diagramme CIE xy](color_management#le-diagramme-cie-xy)

[Fonctionnement de
l'algorithme](Color_Management#comment-fonctionne-lalgorithme-primaires-et-point-blanc)

### La courbe de reproduction des tons (TRC)

La TRC est essentiellement une courbe qui modifie les valeurs initiales
ou d'entrée de l'image en d'autres valeurs, qui seront enregistrées dans
l'image de sortie. On agit sur 2 paramètres:

- gamma;
- pente (slope);

Vous pouvez choisir des valeurs prédéfinies comme par exemple 'standard
g 2.2', 'sRGB g=2.4 s=12.92' ou construire une TRC personnalisée. Dans
ce cas la TRC sera composée d'une partie linéaire et d'une partie
parabolique avec un raccord sans rupture.

Vous pouvez voir d'autres actions possibles d'une TRC dans "Abstract
profiles" [Abstract profile -
TRC](Color_Management#trc---courbe-de-réponse-tonale)

### Illuminant

L'illuminant est la couleur blanche de référence des couleurs de profil.
Le point blanc qui est traduit par une température et un symbole (D50,
stdA 2856K, Fluorescent F11,...) se traduit soit par des données XYZ,
(soit par des données xyY) calculées par : X, Z (Y=1) = Somme du produit
matriciel étendu de 350nm à 830nm \[Observateur 2° x ou z\]\[Illuminant
I\]/ Somme du produit matriciel étendu de 350nm à 830nm \[Observateur 2°
y\]\[Illuminant I\].

Bien que l'illuminant par rapport auquel les couleurs seront encodées
soit souvent l'illuminant standard D50, D60 ou D65, vous pouvez
spécifier un illuminant différent dans la liste et le générateur de
profil ajoutera l'adaptation chromatique nécessaire pour convertir les
couleurs à l'illuminant sélectionné.

D'autres considérations sur l'illuminant - Abstract profiles :
[Illuminant - Abstract
profile](Color_Management#illuminant---point-blanc)
