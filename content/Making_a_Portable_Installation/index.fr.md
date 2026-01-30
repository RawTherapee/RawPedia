---
title: Making a Portable Installation
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Réaliser une installation portable

</div>

RawTherapee et le répertoire cache peuvent être installés de façon
autonome sur une clé USB ou tout autre périphérique de stockage de
masse.

## Pour Windows

Se procurer le dernier build de RawTherapee. Puisqu'on le désire
portable, nous n'avons pas besoin de l'installateur, seulement du
programme zippé. Si la dernière version sur notre site web est sous la
forme zippée, sans l'installateur, vous pouvez sauter cette étape.
Cependant, si l'installateur est présent, vous devez d'abord extraire
les fichiers de RawTherapee.

- Si c'est un installateur Inno Setup (extension .exe, tous les
  installateurs récents pour Windows, au jour de la rédaction, été 2014,
  sont des Inno Setup), procurez vous
  [innounp](http://innounp.sourceforge.net/) ou
  [innoextract](http://constexpr.org/innoextract/) pour le décompresser.
- Si c'est un installateur MSI (aucun build récent de Windows ne
  l'utilise au jour de la rédaction), ouvrir un terminal et écrire :
    
      msiexec /a RawTherapee.msi TARGETDIR="C:\TargetDir" /qb
- Remplacer le nom de l'installateur MSI et le répertoire cible de façon
  appropriée. Les espaces sont autorisés dans le chemin de TargetDir,
  puisqu'il est placé entre guillemets.

Supposons que vous ayez dézippé l'archive dans `E:\RawTherapee`, où
`E:\` est la lettre qui correspond à l'unité du lecteur USB flash.
Ouvrir le fichier `E:\RawTherapee\options` et mettre l'option
`MultiUser` sur `false`. Maintenant lorsque vous lancez RawTherapee, il
sauvegardera le cache et vos paramètres dans les sous-répertoires
définis par l'exécutable, appelés respectivement `mycache` et
`mysettings`, donc dans `E:\RawTherapee\mycache` et
`E:\RawTherapee\mysettings`.

Voir aussi la page [Où sont les fichiers ?](file_paths/fr)
pour savoir comment choisir un endroit différent pour ces deux
répertoires.

Lors des mises à jour de RawTherapee, il est recommandé de décompresser
la nouvelle version dans un nouveau répertoire et simplement déplacer
dans ce dernier `mycache` et `mysettings`.

## Pour Linux

Obtenir de Linux qu'il fonctionne depuis un medium portable tel qu'une
clé USB sur différents systèmes Linux n'est pas franchement dans la
nature des systèmes Linux. Alors que la version Windows de RawTherapee
est fournie avec toutes les bibliothèques nécessaires pour fonctionner
sur n'importe quelle version, les distributions Linux diffèrent
significativement les unes des autres avec pour conséquence qu'une
version de Rawtherapee construite pour une distribution a peu de chances
de fonctionner pour une autre. Une façon de contourner cela est
d'utiliser AppImage.

Un AppImage de RawTherapee est un simple fichier qui contient un
exécutable RawTherapee ainsi que tous les fichiers requis pour lui
permettre de fonctionner sur toute distribution Linux. Téléchargez le,
rendez le exécutable, et lancez le. Nous sommes actuellement en phase
test concernant les AppImages. Ils ne sont pas encore disponibles depuis
notre page de téléchargement mais vous pouvez les trouver sur [la page
"development builds" du
forum](https://discuss.pixls.us/t/download-rawtherapee-development-builds/2924?u=morgan_hardwood).

Indépendamment si vous utilisez les AppImages ou une compilation
"propre" de RawTherapee depuis le gestionnaire de paquetage de la
distribution, vous allez souhaiter pouvoir conserver votre configuration
de RawTherapee et des profils de traitement.

Dans le but de sauvegarder la configuration, vous pouvez copier le
répertoire *config* de RawTherapee sur la clé USB. Vous avez
spécifiquement besoin du fichier "*options*", du fichier personnalisé
"*camconst.json*" si vous en avez créé un et de tout profil personnalisé
PP3, ICC, DCP et LCP. La page [Où sont les
fichiers](File_Paths/fr.md) décrit où les trouver
