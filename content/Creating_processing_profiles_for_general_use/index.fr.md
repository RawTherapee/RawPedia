---
title: Creating processing profiles for general use
contributors:
  - Lebarhon
tags:
  - 'Processing Profiles'
---

<div class="pagetitle">

Création de profils de traitement d'usage général

</div>

Dans RawTherapee, nous appelons les fichiers accolés "Profils de
traitement". Tout un lot de ces profils sont livrés avec RT, vous pouvez
donc commencer avec un aspect tout prêt de la photo puis le modifier
selon votre goût, économisant ainsi votre temps. "Pop 1" est un exemple
d'un tel profil, il rend la photo éclatante et charmante, il relève les
ombres et fait ressortir les détails.

La liste complète des Profils de traitement est visible dans l'onglet
*[Editeur](the_image_editor_tab/fr)*, si vous déroulez la
liste des "Profils de traitement". Vous pouvez aussi la voir dans
l'onglet *Navigateur de fichiers* en cliquant droit sur une vignette et
en choisissant "*Opérations sur les profils \> Appliquer le profil*".

Lisez le court article "[Sélecteur de profil de
traitement](The_Image_Editor_Tab/fr#Sélecteur_de_profil_de_traitement.md)"
pour vous assurer de bien comprendre comment faire bon usage du
sélecteur, des profils partiels et du bouton bascule du mode de de
complètement des profils de traitement.

## Création de profils de traitement

![](Rt_file_browser_custom_profile_fr.jpg "Rt_file_browser_custom_profile_fr.jpg")).\]\]
![](Rt_imageeditor_customprofile_cropped_fr.jpg "Rt_imageeditor_customprofile_cropped_fr.jpg")
de l'[Editeur](the_image_editor_tab/fr).\]\]

Il est possible de créer ses propres profils de traitement et de les
voir apparaître dans la liste déroulante [Sélecteur de profil de
traitement](The_Image_Editor_Tab/fr#Sélecteur_de_profil_de_traitement.md).

- Ouvrez une photo pour laquelle vous souhaitez créer un bon début de
  profil.
- Vous pouvez démarrer avec le profil 'Neutral', ou bien en changer pour
  n'importe quel autre profil fourni avec RawTherapee.Appliquez
  simplement le profil désiré à votre photo.
- Réalisez les modifications désirées, sans perdre de vue que plus vos
  réglages sont spécifiques, moins il y aura de photos à s'y adapter car
  chaque photo est différente et ce qui va bien pour l'une peut ne pas
  convenir à l'autre si elles diffèrent significativement. Par exemple,
  si votre appareil photo a un capteur à très faible bruit et que votre
  objectif n'a pas un bon piqué, vous pourriez probablement activer la
  [netteté](sharpening/fr), ou à l'inverse si votre appareil
  photo a un capteur générant du bruit vous pourriez appliquer un
  certain niveau de [réduction du bruit](noise_reduction/fr)
  par défaut. Il est d'usage courant d'entrer son nom dans le champ
  "Auteur" de [l'onglet IPTC](iptc_tab/fr) et faire en sorte
  que RawTherapee [copie vos modifications de métadonnées dans les
  fichiers sauvegardés](Metadata_Copy_Mode/fr.md). Généralement,
  il vaut mieux laisser la [balance des
  blancs](White_Balance/fr.md) réglée sur "Appareil photo" car
  vos photos seront prises sous différents éclairages.
- Quand vous avez terminé vos ajustements, cliquer sur l’icône
  *Enregistrer le profil courant*
  ![<File:save.png>](save.png "File:save.png") dans le panneau ''Profils
  de traitement". Entrer un nom, pas la peine de préciser l'extension,
  RawTherapee l'ajoutera pour vous. Pour voir le profil apparaître dans
  la liste déroulante, vous devez l'enregistrer dans le sous-répertoire
  "profiles" du répertoire "config". Reportez vous à la page [Où sont
  les fichiers ?](File_Paths/fr.md) pour connaître où sont ces
  répertoires sur votre système.
- Redémarrer RawTherapee, et maintenant votre nouveau profil de
  traitement va apparaître dans la liste déroulante sous "Mes profils".

  

## Profils de traitement partiels

[thumb](image:pp3_partial_window_fr.png)

Quelquefois, on ne désire sauver qu'une partie des paramètres
disponibles, par exemple pour éviter de stocker des paramètres
géométriques comme Rotation, Recadrage et Redimensionner. Dans ce cas,
maintenir appuyée la touche *Contrôle* pendant le clic sur le bouton
*Enregistrer le profil actuel*. Quand le nom du fichier de sortie est
choisi et que vous cliquez sur *Save* (Enregistrer), une fenêtre
apparaît et permet de choisir les paramètres à sauvegarder. Vous pouvez
maintenant partager ces profils avec vos amis ou bien sûr notre forum.

Rappelez vous que pour rendre un profil applicable de façon universelle
à toutes les photos d'une même scène et même situation (profil pour un
bébé dans cet exemple), vous devez penser à toutes les variantes de tous
les portraits de bébé auxquelles vous pourriez appliquer ce profil.
Rappelez vous que les expositions peuvent changer d'une photo à l'autre,
même si bébé est photographié en studio, le petit bougre ne va
probablement pas tenir en place, et pire si vous envoyez votre profil
sur internet pour d'autres photographes de bébés avec différents
appareils photo et différents accessoires d'éclairage. Aussi, ne pas
paramétrer une exposition spécifique, telle que +0,60, mais plutôt
valider *Niveaux auto*. Ceci s'applique aussi à tous les autres
réglages, rappelez vous de ne paramétrer que le minimum d'options pour
atteindre l'effet désiré, laisser le reste non touché, car il est très
probable que les réglages apportés à ces autres options ne
s'appliqueraient pas correctement aux autres photos. Si votre Profil de
traitement est censé rendre le visage de bébé doux et câlin par un
savant mélange de Compression des hautes lumières, Niveaux d'exposition
auto, Courbes tonales Lab et RVB, alors n'ajoutez pas de Réduction de
bruit (car les photos peuvent être prises à différentes valeur ISO), ne
définissez pas de Balance des blancs personnalisée car la lumière peut
avoir changé entre les prises), ne tournez pas la photo, etc.. Tous ces
paramètres superflus sont susceptibles de changer d'une photo à l'autre
sans influencer d'aucune façon le regard doux du bébé, donc les activer
ne fera que polluer le profil. Vérifiez bien ces choses avant de
partager vos profils.

## Profil de traitement par défaut Raw/Non-raw

Pour utiliser votre propre profil de traitement par défaut pour les
photos raw et non raw, le paramétrer dans "*Préférences \> Traitement de
l'image \> Paramètres de traitement de l'image par défaut*".

Si vous désirez utiliser un profil dynamique, alors régler "Paramètres
de traitement de l'image par défaut pour (non/)raw" sur "(Dynamic)".
