---
title: File Paths
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Où sont les fichiers

</div>

RawTherapee utilise un dossier "cache" pour stocker des fichiers
temporaires qui peuvent être effacés sans problème, et dossier "config"
qui contient vos paramétrages de RawTherapee, vos profils de traitement
personnalisés et autres fichiers utilisateur éditables. Ces dossiers
résident en un endroit spécial (décrit ci-après), et ont un nom qui
commence par "RawTherapee" suivi éventuellement d'un suffixe. Ce dernier
est fixé par la personne qui a réalisé la compilation du RawTherapee qui
vous utilisez. Voici quelques exemples de désignation :

- RawTherapee
- RawTherapee**4.2**
- RawTherapee**5**
- RawTherapee**5-dev**
- RawTherapee**_test**
- Et autres possibilités, toujours commençant par "RawTherapee"

La première partie, "RawTherapee", est codée en dur. La seconde partie,
le suffixe, est à la discrétion de la personne qui compile. Il peut être
spécifique, comme "5.0-gtk2-123-g87654321", ou général comme "5", il
peut être tout autre chose, comme "_test", ou il peut n'être pas
défini. Nous recommandons que les éditions stables de RawTherapee
n'utilisent aucun suffixe, alors que toutes les versions en
développement utilisent "5-dev", heureusement la personne qui a réalisé
la compilation que vous utilisez a pris ceci en compte.

## Config

Le dossier config de RawTherapee contient :

- le fichier "options" qui contient tous vos paramètres établis dans
  [Préférences](preferences),
- le dossier "batch" qui regroupe les [profils de
  traitement](Sidecar_Files_-_Processing_Profiles)
  temporaires des photos envoyées dans la [File
  d'attente](The_Batch_Queue),
- le fichier éditable par l'utilisateur
  [camconst.json](adding_support_for_new_raw_formats), où
  vous pouvez définir les détails sur la façon dont un format raw
  spécifique doit être traité (ceux-ci prévalent sur les valeurs du
  fichier système camconst.json),
- les règles du [Profil
  dynamique](dynamic_processing_profiles)
- et le dossier "profiles" où vous pouvez copier ou enregistrer vos
  [profils de
  traitement](Sidecar_Files_-_Processing_Profiles)
  personnalisés si vous désirez qu'ils apparaissent dans la liste
  déroulante de RawTherapee.

Vous devriez inclure ce dossier à vos sauvegardes générales afin qu'en
cas d'installation de Rawtherapee sur un nouveau système, vous puissiez
récupérer tous vos paramétrages simplement en recopiant ce fichier
depuis la sauvegarde.

Emplacements par défaut du dossier config de RawTherapee (rechercher le
préfixe de "RawTherapee\*" décrit ci-dessus):

|            |                                                                                         |
|------------|-----------------------------------------------------------------------------------------|
| Windows XP | `%USERPROFILE%\Local Settings\Application Data\`                                        |
| Windows 7+ | `%LOCALAPPDATA%`                                                                        |
| Linux      | `~/.config/`                                                                            |
| macOS      | `~/Library/Containers/RawTherapee/Data/Library/Application Support/RawTherapee/config/` |
{.table .table-striped .table-sm}

Dans le Finder, menu "Aller", cliquer sur "Aller au dossier" (raccourci
Commande+Shift+g) vous pouvez alors taper/coller tout chemin où vous
souhaitez naviguer, même s'il est caché.

## Cache

Le dossier cache de RawTherapee contient des ensembles d’éléments
cachés, où chaque ensemble comprend :

- une vignette,
- les métadonnées
- un fichier accolé
- et optionnellement un profil intégré

Par défaut, RawTherapee conserve jusqu'à 20000 ensembles cachés. Gardez
un œil sur le répertoire "cache" car il peut grossir considérablement à
tout moment ! Cela est principalement du aux vignettes en cache qui sont
sauvegardées dans le sous dossier "images". Effacer ce sous dossier est
possible, vous ne perdrez aucun paramétrage d'image, RawTherapee aura
seulement à régénérer les vignettes.

Emplacements par défaut du dossier cache de RawTherapee (rechercher le
préfixe de "RawTherapee\*" décrit ci-dessus):

|            |                                                                                         |
|------------|-----------------------------------------------------------------------------------------|
| Windows XP | `%USERPROFILE%\Local Settings\Application Data\`                                        |
| Windows 7+ | `%LOCALAPPDATA%`                                                                        |
| Linux      | `~/.cache/`                                                                             |
| macOS      | `~/Library/Containers/RawTherapee/Data/Library/Application Support/RawTherapee/cache/` |
{.table .table-striped .table-sm}

Dans le Finder, menu "Aller", cliquer sur "Aller au dossier" (raccourci
Commande+Shift+g) vous pouvez alors taper/coller tout chemin où vous
souhaitez naviguer, même s'il est caché.

Un ensemble caché utilisé pour contenir un fichier histogramme de 32 ko,
mais à partir de RawTherapee 5.5, le besoin de sauvegarder l'histogramme
a disparu.

## Personnaliser les dossiers config et cache

Vous pouvez imposer à RawTherapee l'utilisation d'un répertoire de
configuration personnalisé en paramétrant la variable d'environnement
`RT_SETTINGS` la faisant pointer par un chemin **absolu** vers ce
répertoire pour lequel vous avez les droits de lecture et d'écriture. De
même, vous pouvez utiliser un répertoire cache personnalisé en
paramétrant la variable d'environnement `RT_CACHE`. Comment faire cela
dépend de votre système d'exploitation, aussi recherchez sur internet
"Comment paramétrer les variables d'environnement dans \<votre système
d'exploitation\>"

Quelque exemples :

Windows  
Nom de la variable: `RT_SETTINGS`, valeur:
`%LOCALAPPDATA%\rawtherapee\5.7`

Nom de la variable: `RT_CACHE`, valeur: `Z:\rawtherapee\cache`

Linux et macOS  
`RT_SETTINGS=/home/bob/.config/rawtherapee/5.7`

`RT_CACHE=/home/bob/junk/rtcache`

## Profils de traitement

Si vous créez vos propres [profils de
traitement](Sidecar_Files_-_Processing_Profiles), pour les
faire apparaître dans la liste des "Profils de traitement" de
RawTherapee, vous devez les enregistrer dans le dossier "*profiles*" que
vous trouverez à l'intérieur du fichier "*config*" come indiqué
ci-dessus.

## Dossier temporaire

L'outil "[Editer l'image courante dans un éditeur
externe](Edit_Current_Image_in_External_Editor)"
enregistre les fichiers image temporaires dans un dossier temporaire :

Windows  
L'emplacement par défaut est celui donné par la variable d'environnement
`$TEMP`, qui généralement est `%LOCALAPPDATA%/Temp`

Si la variable d'environnement `$TEMP` n'est pas définie, `C:\` est
utilisé.

Linux et macOS  
L'emplacement par défaut est celui donné par la variable d'environnement
`$TMPDIR`, qui généralement est `/tmp`

Si la variable d'environnement `$TMPDIR` n'est pas définie, `/tmp` est
utilisé.
