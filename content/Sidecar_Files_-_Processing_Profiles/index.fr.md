---
title: Sidecar Files - Processing Profiles
contributors:
  - Lebarhon
tags:
  - 'Processing Profiles'
---

<div class="pagetitle">

Fichiers accolés - Profils de traitement

</div>

## Introduction

Les profils de traitement (avec une extension PP3 pour la version 3, ou
PP2 pour l'ancienne version 2) sont des fichiers texte qui contiennent
tous les paramètres des outils que RawTherapee applique à l'image
associée. Si vous êtes familier avec d'autres logiciels de traitement
raw, vous connaissez peut-être leur équivalent sous le nom de
"Paramètres prédéfinis"(ou "Presets" en anglais). Ils sont enregistrés à
côté de leur photo associée, c'est pourquoi on les appels ([fichiés
accolés](https://en.wikipedia.org/wiki/Sidecar_file).

Quand vous ouvrez un répertoire contenant des photos dans le navigateur
de fichiers de RawTherapee pour la première fois, aucune des images n'a
encore de fichier accolé PP3. Les vignettes affichées qui représentent
des images n'ayant pas de de profil de traitement associé (ces images
n'ont jamais été ouvertes ni éditées) sont créées à partir des images
JPEG intégrées dans tout fichier raw. Un profil de traitement est
assigné à l'image dès qu'une de ces actions est engagée :

- Vous ouvrez l'image pour
  [édition](the_image_editor_tab/fr).
- Vous appliquez manuellement un profil de traitement en utilisant le
  menu contextuel du clic droit dans le [Navigateur de
  Fichiers](The_File_Browser_Tab/fr.md) ou [La bande
  film](The_Image_Editor_Tab/fr#_La_bande_film.md).
- Vous appliquez un [Profil de traitement
  dynamique](Dynamic_processing_profiles/fr.md).

Lorsque vous ouvrez une image pour édition, ou lorsqu'un profil de
traitement est assigné, RawTherapee va convertir les données raw réelles
en un image affichable. Dans ce but, il y a beaucoup de paramètres qui
doivent être réglés sur "quelque chose", et ces valeurs spécifiques
dépendent de :

- Vos [Paramètres de traitement d'image par
  défaut](Preferences/fr#Paramètres_de_traitement_d'image_par_défaut.md).
- Vos [Règles de profils
  dynamiques](Dynamic_processing_profiles/fr.md), si elles
  existent.
- Ou du profil de traitement sélectionné par le menu contextuel du clic
  droit si vous avez cliqué droit sur une vignette.

## Sources

Les profils de traitement proviennent de trois sources légèrement
différentes bien qu'il fonctionnent exactement de la même façon :

- "Les profils fournis"
    
  RawTherapee est livré avec une proposition de profils. Leur mission
  est de vous donner un bon point de départ, pour démontrer comment les
  outils s'articulent entre eux. Ce sont ceux que vous voyez dans la
  liste déroulante de la section profils de traitement [Sélecteur de
  profil de
  traitement](The_Image_Editor_Tab/fr#Sélecteur_de_profil_de_traitement.md)
  dans [L'onglet Editeur](the_image_editor_tab/fr).

<!-- -->

- "Mes profils".
    
  Quand vous réalisez un profil de traitement que vous prévoyez de
  ré-utiliser, par exemple un profil qui fonctionne bien avec votre
  appareil photo et votre style, vous pouvez le sauvegarder de telle
  sorte qu'il soit visible dans la liste déroulante du sélecteur du
  profil de traitement, dans la section "Mes profils". Pour cela,
  enregistrer le profil dans le sous dossier "profils" du dossier
  "config". Voir la page [Où sont les fichiers](file_paths)
  pour le trouver.

<!-- -->

- Profils générés automatiquement.
    
  Chaque fois que vous éditez une image, le paramétrage des outils que
  vous souhaitez voir appliquer à cette image est enregistré dans un
  profil de traitement qui est spécifique à cette image (la cotation
  (étoiles), l'historique et les captures ne sont pas enregistrés dans
  ces fichiers jusqu'à présent, voir [issue
  473](https://code.google.com/p/rawtherapee/issues/detail?id=473)).

## Enregistrement

Etant donné que le simple visionnage d'une image nécessite du
traitement, RawTherapee enregistre les paramètres qu'il utilise pour
vous présenter l'image dans un fichier profil de traitement accolé au
fichier image. Ce profil de traitement enregistre aussi tous les
réglages des outils effectués dans l'onglet Editeur.

Le profil de traitement est écrit sur le disque :

- Quand vous appliquez manuellement un profil de traitement ou utilisez
  un profil dynamique.
- Quand vous fermez l'image courante (l'onglet Editeur) si vous utilisez
  le [Mode Multiple de l'onglet
  Éditeur](The_Image_Editor_Tab/fr#Modes_de_l'onglet_Editeur.md)
  (METM).
- Quand vous fermez l'image courante en ouvrant une autre image si vous
  utilisez le [Mode Unique de l'onglet
  Éditeur](The_Image_Editor_Tab/fr#Modes_de_l'onglet_Editeur.md)
  (SETM).
- Quand vous fermez l'image courante en fermant RawTherapee.
- Quand vous enregistrez manuellement le profil de traitement si vous
  utilisez le panneau [Sélecteur de profil de
  traitement](The_Image_Editor_Tab/fr#Sélecteur_de_profil_de_traitement.md).
- Quand vous utilisez le [raccourci
  clavier](Keyboard_Shortcuts/fr.md) qui "force l'enregistrement
  des paramètres actuels dans le profil de traitement" depuis l'onglet
  Editeur.

Si une photo possède un profil de traitement associé, un coche vert
apparait sur sa vignette.

Si une photo est ouverte dans l'onglet Editeur alors que vous réalisez
des modifications dessus depuis le Navigateur de fichiers, les
modifications sont immédiatement reportées dans l'onglet Editeur.

## Enregistrement

L'endroit où s'effectue l'enregistrement peut être configuré dans
[Préférences \> Gestionnaire des profils de
traitement](Preferences/fr#Gestionnaire_des_profils_de_traitement.md).

Par défaut, le profil de traitement d'une image est enregistré à coté de
l'image d'entrée (si vous ouvrez `kitty.raw`, un nouveau fichier
`kitty.raw.pp3` sera créé a côté de lui), mais il peut aussi être
enregistré dans un [cache central](file_paths/fr). Il est
possible de choisir si RawTherapee doit utiliser le cache, écrire le
profil de traitement à côté de l'image ou les deux, dans "*Préférences
\> Traitement de l'image*". Nous recommandons d'enregistrer ces fichiers
à côté de l'image d'entrée afin que si vous décidez de déplacer les
images, il soit facile de déplacer les profils de traitement en même
temps.

Lors de l'enregistrement d'une image vous avez la possibilité de cocher
la case "Enregistrer les paramètres de développement avec l'image". Si
elle est cochée et si vous travaillez sur `kitty.raw`, l'enregistrant
dans un fichier JPG, alors le profil de traitement utilisé pour
développer cette image sera enregistré dans un fichier appelé
`kitty.jpg.out.pp3`. L'ajout "out" est là pour éviter les conflits en
cas de travail sur des fichiers non-raw.

## Profils par défaut

Le profil de traitement par défaut utilisé à l'ouverture d'images
**non-raw** est appelé "[Neutre](neutral/fr)". Pour ce
profil, tous les paramètres des outils sont à la valeur neutre, ils
n'ont donc aucun effet. Puisque les images non-raw ont habituellement
déjà été traitées et sont prêtes au visionnage, le comportement attendu
par défaut de RawTherapee est de n'ajouter aucun réglage supplémentaire.

Les profil de traitement par défaut utilisé pour les images **raw** est
appelé "[Auto-Matched Curve/fr](auto-matched_curve/fr)" (à
partir de RawTherapee 5.4). Ce profil donne à votre image un aspect JPEG
sorti tout droit du boitier, ce qui est habituellement un bon point de
départ.

Par ailleurs, la plupart des outils de l'onglet Editeur ont un bouton de
retour aux réglages par défaut.

- Cliquer sur ce bouton remet l'outil à sa valeur neutre codée en dur,
  généralement zéro.
- Ctrl+cliquer sur ce bouton remet l'outil à la valeur qu'il avait quand
  l'image a été ouverte, c'est-à-dire comme si on remontait la pile de
  l'historique jusqu'au début.

## Profils de traitement partiels et modes de complètement

Les profils de traitement peuvent être copiés, collés, chargés,
enregistrés et appliqués au complet ou partiellement. Cliquer sur les
boutons dans le [Sélecteur de profil de
traitement](The_Image_Editor_Tab/fr#Sélecteur_de_profil_de_traitement.md)
les manipule au complet, alors que cliquer+Ctrl ces boutons les manipule
partiellement, une fenêtre surgit vous permettant de choisir les
paramètres à inclure. Cette fonctionnalité vous permet, par exemple, de
ne copier que les paramètres de la réduction du bruit d'une image à
l'autre, ou seulement la balance des blancs, ou les deux.

le mode de complètement du profil de traitement vous permet de décider
ce qui se produit lorsque vous appliquez un profil de traitement sur une
image alors que dans ce profil certains paramètres d'outils ne sont pas
renseignés

- Mode "bouton pressé"
  [image:Profile-filled.png](image:profile-filled.png)
    
  En mode "bouton pressé", les valeurs manquantes seront considérées
  valoir les valeurs par défaut codées en dur de RawTherapee
  (typiquement neutre). Par exemple, si vous appliquez un profil partiel
  qui ne contient que les paramètres de netteté, tous les autres outils
  (tels que Exposition, Compression tonale, Réduction du bruit,
  Redimensionnement, etc.) seront réglés à leur valeur par défaut.

<!-- -->

- Mode "bouton relevé"
  [image:Profile-partial.png](image:profile-partial.png)
    
  En mode "bouton relevé", seules ces valeurs du profile seront
  appliquées, et les autres restent inchangées.

## Créer vos propres profils de traitement

Utiliser certains outils de certaines façons peut rendre votre profil de
traitement utilisable uniquement avec cette image spécifique. Par
exemple, si vous paramétrez une balance des blancs, un recadrage et une
rotation, vous n'obtiendrez pas de bons résultats en appliquant ce
profil sur une image prise sous un éclairage différent et avec un
appareil photo tourné d'une autre façon. Consultez l'article [Création
de profils de traitement d'usage
général](Creating_processing_profiles_for_general_use/fr.md)
pour connaître la façon de créer des profils de traitement utilisables
sur de nombreuses images. Lors de l'enregistrement d'une image, vous
avez la possiblité de cocher la case "Enregistrer les paramètres de
développement avec l'image". Si elle est cochée et si vous travaillez
sur le fichier `kitty.raw`, l'enregistrant au format JPG, alors le
profil de traitement utilisé pour développer cette image sera enregistré
dans un fichier appelé `kitty.jpg.out.pp3`. L'ajout "out" est là pour
éviter les conflits en cas de travail sur des fichiers non-raw.

## Compatibilité

Les profils de traitement évoluent d'une version à l'autre de
RawTherapee. Nous nous efforçons d'assurer la compatibilité avec les
anciennes versions (par exemple, un profil créé avec la version 5.3 et
utilisé dans la version 5.4 devrait donner le même résultat), mais ce
n'est pas toujours possible.

Les profils de traitement peuvent recevoir de nouveaux paramètres ou
bien perdre ceux qui deviennent obsolètes. Le comportement de l'outil
peut aussi évoluer, changer de valeur par défaut ou en cas extrême,
interpréter différemment le sens d'une valeur. L'outil de réduction du
bruit nous donne un exemple de cela, où une valeur de réduction du bruit
de luminance de 10 dans RawTherapee-3.0 donnerait un résultat différent
dans RawTherapee-4.0.10, car l'outil de réduction du bruit a été
profondément amélioré dans son ensemble.

La consolidation des profils de traitement dans un cache permet de
conserver une copie des profils séparément pour chaque version de
RawTherapee. De ce fait, le cache peut être utilisé pour traiter à
nouveau les photos afin de retrouver le même résultat qu'à l'origine
(mais par ex. en changeant la dimension ou l'espace colorimétrique) en
utilisant la même version de RawTherapee que celle utilisée pour éditer
l'image à l'origine. Savoir si cela est souhaitable est discutable.
Considérons que vous souhaitez compacter autant de vos fichiers raw que
possible. Si deux ans plus tard, vous souhaitez revenir à un vieux
fichier raw, il se peut que renouveler le résultat obtenu deux ans
auparavant ne soit pas la meilleure idée, car les capacités de
RawTherapee auront été améliorées durant ce temps, vous aurez peut-être
acquis un meilleur écran et vos goûts et compétences auront aussi
évolué. Néanmoins, en conservant une sauvegarde complète du répertoire
cache à chaque nouvelle installation de RawTherapee, vous vous préservez
la possibilité de revenir à une ancienne version de RawTherapee pour
obtenir exactement le même résultat.

La page [Où sont les fichiers ?](file_paths/fr) explique où
vous pouvez trouver les répertoires "*cache*" et "*config*" sur votre
système.

Lors de la sortie d'une nouvelle version majeure de RawTherapee, les
répertoires "*cache*" et "*config*" peuvent avoir un nouveau suffixe. Ce
qui fait que la nouvelle version de RawTherapee ne verra pas l'ancienne
configuration ni les profils de traitement. Bien que cela semble
préjudiciable, il y a de bonnes raisons pour agir (rarement) ainsi :

- Rétro-compatibilité. Il peut y avoir des changements de comportement
  entre les nouvelle et ancienne versions d'un outil particulier. Par
  exemple, les effets de l'outil Niveaux auto ont évolué (pour le
  meilleur) entre les versions 4.0.11 et 4.0.12, ainsi, s'il était
  activé avec les anciens profils de traitement, les résultats avec
  4.0.12 sont légèrement différents et peuvent nécessiter une correction
  des vieux profils.
- Certains utilisateurs n'ont pas vérifié
  "[Préférences](preferences/fr)" depuis longtemps, et les
  réglages sont restés ceux qui fonctionnaient le mieux il y a
  longtemps, pas ce qui fonctionne le mieux maintenant. Ceux par défauts
  sont bons, nous les maintenons à jour pour assurer un bon
  fonctionnement de RawTherapee dès la mise en route, donc quelquefois
  faire démarrer RawTherapee avec des valeurs par défaut toutes fraîches
  est une bonne chose, et motivera les utilisateurs pour a nouveau
  consulter "[Préférences](preferences/fr)".
- Certains utilisateurs n'ont jamais regardé dans
  "[Préférences](preferences/fr)" et n'ont pas conscience des
  fonctionnalités qui peuvent être enclenchées ici. Comme ci-dessus, des
  valeurs par défaut toutes fraîches vont activer ces choses.
- Les anciens répertoires "*cache*" et "*config*" peuvent éventuellement
  planter RawTherapee. Pendant que l'on remédie aux cas spécifiques
  portés à notre connaissance, il est prudent de considérer qu'il y aura
  toujours des cas qui nous sont inconnus et toujours cause
  d'instabilité. Démarrer avec de nouveaux répertoires "*cache*" et
  "*config*" atténue ce problème.
