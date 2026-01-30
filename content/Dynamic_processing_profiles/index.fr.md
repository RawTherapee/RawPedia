---
title: Dynamic processing profiles
contributors:
  - Lebarhon
tags:
  - 'Processing Profiles'
---

<span style="color: #000000; background: none; overflow: hidden; page-break-after: avoid; font-size: 2.0em; font-family: Georgia,Times,serif; margin-top: 1em; margin-bottom: 0.25em; line-height: 1.3; padding: 0; border-bottom: 1px solid #AAAAAA;">Profils
de traitement dynamiques</span>

Quelquefois un simple profil "statique" de traitement par défaut n'est
pas suffisant pour couvrir tous les cas. Par exemple, l'intensité de
réduction du bruit qui doit s'appliquer varie selon l'appareil photo et
les paramètres ISO utilisés. Un autre exemple est le type et l'intensité
des corrections de l'objectif nécessaires.

Pour répondre à de tels cas, RawTherapee dispose d'une fonctionnalité
qui permet la création d'un profil "dynamique" de traitement par défaut,
basé sur les métadonnées de l'image en cours de traitement (telles que
le nom de l'appareil et de l'objectif, la vitesse d'obturation, la
valeur ISO, etc.)

Cela est réalisé en définissant un ensemble de "règles du profil
dynamique". Chaque règle possède un [Profil de traitement
(partiel)](Creating_processing_profiles_for_general_use/fr.md)
qui lui est attaché, plus quelques conditions sur les métadonnées de
l'image qui régissent si la règle est applicable. Quand une image est
éditée pour la première fois, la liste des règles est parcourue et tous
les profils qui correspondent sont combinés (dans l'ordre donné, ainsi
les règles suivantes peuvent écraser les précédentes) pour former le
profil de traitement initial.

Pour activer la fonction, [Paramètres de traitement d'image par
défaut](Preferences/fr#Paramètres_de_traitement_d'image_par_défaut.md)
doit être positionné sur "Dynamique". Les règles sont définies dans
l'onglet [Règles du profil
dynamique](Preferences/fr#L'onglet_Règles_du_profil_dynamique.md)
de la fenêtre Préférences.

Les règles du profil dynamique fonctionnent sur les métadonnées
suivantes de l'image :

Appareil photo  
le nom de l'appareil (y compris la marque) comme indiqué en
surimpression en haut de l'aperçu de
[l'éditeur](the_image_editor_tab/fr) (non présent sur l'image
visible dans ce lien). Si activée, par défaut cette entrée appliquera la
règle à toutes les images réalisées uniquement avec l'appareil spécifié
(excepté que les lettres majuscules sont ignorées). Cependant, si
l'entrée commence par le préfixe `re:`, alors la suite de la chaîne de
caractères sera interprétée comme étant une [expression
rationnelle](https://fr.wikipedia.org/wiki/Expression_rationnelle) à
utiliser pour la recherche de correspondance. Par exemple, une règle
avec une entrée d'appareil photo notée `re:SONY ILCE-[56].00`
s'appliquera à tous les appareils Sony Alpha a5xxx and a6xxx.

<!-- -->

Objectifs  
le nom complet de l'objectif. Come ci-dessus, une expression rationnelle
peut être utilisée en commençant par le préfixe `re:`.

<!-- -->

ISO  
la gamme des valeurs ISO

<!-- -->

Ouverture  
la gamme des ouvertures de l'objectif (mesurés in f/pas)

<!-- -->

Distance focale  
la gamme des longueurs focales utilisées (en mm)

<!-- -->

Obturateur  
la gamme des vitesses d'obturation en secondes (par exemple, entrer 0.03
pour une vitesse de 1/30")

<!-- -->

Compensation d'exposition  
la gamme des compensations d'exposition.

Une copie d'écran est présentée ci-dessous.

<figure>
<img src="/images/dynamic-profile-rules-screenshot.png"
title="File:dynamic-profile-rules-screenshot.png" />
<figcaption><a
href="File:dynamic-profile-rules-screenshot.png">File:dynamic-profile-rules-screenshot.png</a></figcaption>
</figure>
