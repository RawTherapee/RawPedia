---
title: Negative fr
contributors:
  - Lebarhon
---

# Négatif

Les négatifs sont des images avec les couleurs et la luminosité
inversées, telles que celles produites par les appareils photo à film.
RawTherapee n'a pas encore de solution idéale en un seul clic pour les
créer, donc cette page a pour but de vous informer des solutions
possibles de contournement :

1.  Inverser la diagonale d'une [courbe
    tonale](Exposure/fr#Courbes_tonales.md) soit dans l'outil
    Exposition, ou bien toutes les courbes dans l'outil [Courbes
    RVB](RGB_Curves/fr.md). Dans l'outil Gestion de la couleur
    (ICM) choisir "[Sans
    profil](Color_Management/fr#Sans_profil.md)" comme profil
    d'entrée. L'inconvénient de cette méthode est d'introduire des
    décalages de tons.
2.  Utiliser un Hald CLUT négatif via l'outil [Simulation de
    film](Film_Simulation/fr.md). La "Collection de simulations
    de Film de RawTherapee" en contient un, procurez vous le depuis la
    page [Simulation de film](film_simulation/fr).
    L'inconvénient de cette méthode est que certains contrôles peuvent
    agir à l'envers, tel que le curseur Exposition, et vous risquez
    d'obtenir des écrêtages dans les ombres et/ou dans les hautes
    lumières car ces outils ne sont pas conçus pour travailler avec le
    négatif.
3.  En complément de l'utilisation d'un Hald CLUT négatif neutre comme
    décrit ci-dessus, si vous avez quantité de négatifs réussis, pas
    seulement par une simple inversion mais aussi pour les avoir
    travaillés à votre goût avec RawTherapee ou une autre application,
    vous pourriez [créer vos propres Hald CLUT
    négatifs](Film_Simulation/fr#Créer_votre_collection.md) pour
    reproduire tout le travail, y compris l'inversion. Pour cela,
    appliquer les mêmes étapes sur l'image "Hald CLUT identity" fourni
    avec la collection Simulation de Film de RawTherapee que celles
    appliquées sur un négatif, enregistrez le sous un nouveau nom, puis
    ouvrir un négatif photo dans RawTherapee et y appliquer ce nouveau
    Hald CLUT. Cela vous permet d'atteindre instantanément, non
    seulement l'inversion en négatif mais aussi vos propres ajustements
    par un clic sur un bouton, ne vous laissant que le soin d'élargir
    l'histogramme en ajustant le curseur Exposition ou en utilisant les
    courbes.
4.  Actuellement, la meilleure méthode est d'utiliser le DCP (DNG Camera
    Profile = Profil d'appareil photo DNG) pour votre appareil photo,
    mais édité dans "DNG Profile Editor" (Editeur de Profil DNG) afin
    que la courbe tonale diagonale y soit inversée, puis manuellement
    charger ce DCP dans RawTherapee pour toutes les prises de vue en
    négatif. La méthode est détaillée ci-dessous. Si vous ne désirez pas
    réaliser votre propre DCP inversé, un échantillon peut être
    téléchargé ici : [Linear
    inverted.dcp](Linear_inverted.dcp.md)

## Création d'un DCP pour négatifs

![](DNG_Profile_Editor_inverted_tone_curve.png "DNG_Profile_Editor_inverted_tone_curve.png")
![](Rt_negative_dcp_l_curve.png "Rt_negative_dcp_l_curve.png")

- Télécharger [DNG Profile
  Editor](http://www.adobe.com/support/downloads/detail.jsp?ftpID=5494).
  Il fonctionne correctement sous Linux avec
  [wine](https://www.winehq.org/).
- Convertir l'une de vos photos raw, obtenue avec l'appareil photo ou le
  scanner, (cela peut être la photo du négatif) en DNG en suivant ce
  guide "[How to convert raw formats to
  DNG/fr](How_to_convert_raw_formats_to_DNG/fr.md)".
- Ouvrir l'image DNG dans DNG Profile Editor.
- Dans l'onglet Color Tables, vérifier si le profil de base appelé
  "Adobe Standard (*\<votre modèle d'appareil\>*) est disponible. Si
  c'est le cas, le sélectionner. Sinon, choisir "Choose external
  profile..." (= choisir un profil externe) et trouver le fichier
  intitulé "*\<votre modèle d'appareil\>* Adobe Standard.dcp". Le guide
  [How to get LCP and DCP
  profiles/fr](How_to_get_LCP_and_DCP_profiles/fr.md) explique
  comment et où les trouver.
- Dans l'onglet Tone Curve, inverser la diagonale afin qu'elle aille
  depuis le coin en haut à gauche dans le coin en bas à droite (le point
  du haut passe en bas).
- Toujours dans l'onglet Tone Curve, choisissez l'une des trois "Base
  Tone Curves". "Base Profile" et "Camera Raw Default" sont
  habituellement identiques et sont davantage contrastées, alors que
  "Linear" rend l'image plus plate. Nous vous recommandons d'enregistrer
  une DCP en utilisant "Base Profile" et une autre avec "Linear", et
  voyez par vous-même laquelle convient le mieux dans RawTherapee. Les
  deux DCP nécessiteront un peaufinage ultérieur de l'image dans
  RawTherapee, mais la "Linear" demandera plus de travail que la "Base
  Curve", bien que cette dernière peut sur-saturer les couleurs, ne pas
  perdre cela de vue.
- Pour créer le DCP, cliquer sur "File \> Export *\<votre modèle
  d'appareil\>* profile...". Comme recommandé dans l'étape précédente,
  enregistrez deux versions.

Pour utiliser ce nouveau DCP pour les négatifs, ouvrez votre négatif raw
dans RawTherapee, aller dans l'onglet Couleur \> ICM \> Profil d'entrée
et choisir Personnel, puis trouver le nouveau fichier DCP. Cocher
"Utiliser la courbe tonale du profil DCP".

Lors du peaufinage des images dans RawTherapee en utilisant ces DCP,
souvenez vous qu'en utilisant des courbes tonale qui travaillent dans
les canaux RVB (Courbes tonales 1 et 2 dans l'outil Exposition de
l'onglet Exposition) vous ne changerez pas seulement la luminosité mais
aussi la saturation des couleurs. Vous pouvez contrôler cette saturation
en utilisant les modes "Standard Pondéré" et "Mixage Saturation et
Valeur" des courbes tonales 1 et 2 ; ou vous pouvez éviter le problème
en travaillant dans l'espace L\*a\*b\*. L'avantage de cet espace est
qu'avec la courbe L\*, les couleurs ne sont pas modifiées lorsqu'on
modifie la luminosité, vous pouvez donc régler d'abord la luminosité
avec toute la puissance de L\*, puis régler la saturation des couleurs
en utilisant par exemple la courbe CC.
