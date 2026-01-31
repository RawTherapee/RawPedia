---
title: How to create LCP profiles
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<div class="pagetitle">

Comment créer des profils LCP

</div>

You can easily create LCP (Lens Correction Profile) profiles using Adobe
Lens Profile Creator.

Cette section explique comment installer "Lens Profile Creator" d'Adobe
et comment démarrer son utilisation.

__FORCETOC__

## Installation dans Linux

Nous utiliserons `$HOME/wine-dng` comme préfixe Wine.

1.  Installer [Wine](http://www.winehq.org/), de préférence en utilisant
    votre gestionnaire de paquetage.
2.  Etablir le préfixe Wine :
      
        WINEPREFIX="$HOME/wine-dng" wineboot --init
3.  [Télécharger Adobe Lens Profile Creator pour
    Windows](http://supportdownloads.adobe.com/detail.jsp?ftpID=5490).
4.  Au moment de la rédaction, la dernière version est 1.0.4 et c'est un
    plein fichier ZIP. L'extraire quelque part, et déplacer répertoire
    de `Adobe Lens Profile Creator 1.0.4` dans
    `~/wine-dng/drive_c/Program Files (x86)/`
5.  Exécuter Adobe Lens Profile Creator :
      
        WINEPREFIX="$HOME/wine-dng" wine "$HOME/wine-dng/drive_c/Program Files (x86)/Adobe Lens Profile Creator 1.0.4/Adobe Lens Profile Creator.exe"
6.  Ajouter un alias afin de pouvoir facilement lancer Adobe Lens
    Profile Creator depuis une console :
      
        echo "alias lcp='WINEPREFIX=\"\$HOME/wine-dng\" wine \"\$HOME/wine-dng/drive_c/Program Files (x86)/Adobe Lens Profile Creator 1.0.4/Adobe Lens Profile Creator.exe\"'" >> ~/.bashrc && exec bash
7.  Pour lancer Adobe Lens Profile Creator, simplement taper `lcp` dans
    une console.

## Installation dans Windows

1.  [Télécharger Adobe Lens Profile Creator pour
    Windows](http://supportdownloads.adobe.com/detail.jsp?ftpID=5490).
2.  Installer Adobe Lens Profile Creator.

## Utilisation

Fondamentalement, vous devez imprimer un motif à damiers et le
photographier sous différentes ouvertures, et à différents niveaux de
zoom si vous utilisez un objectif avec zoom. Vous ouvrez ensuite ces
photos dans Adobe Lens Profile Creator, entrez quelques métadonnées,
enregistrez, et voilà le LCP.

Le guide utilisateur en pdf d'Adobe Lens Profile Creator explique la
totalité du processus. vous pouvez le trouver sur la page [Digital
Negative
Resources](https://helpx.adobe.com/photoshop/digital-negative.html#resources)
d'Adobe, regardez dans la section de "Adobe Lens Profile Creator" le
lien noté "read the user guide (PDF, 1.64 MB)".
