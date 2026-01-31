---
title: Windows
contributors:
  - Lebarhon
  - Gaaned92
  - Jdc
tags:
  - 'Compiling'
---

<div class="pagetitle">

Windows

</div>

Cette page détaille les instructions pour la compilation de RawTherapee
sur les systèmes "Windows". Il y a aussi des pages séparées avec des
instructions pour la compilation sur [Linux](linux) et
[macOS](macos). Ce guide détaille le "quoi" et le "comment"
de la compilation. Concernant le "pourquoi" et les explications des
commandes, pour obtenir la liste des dépendances, pour les options de
CMake et d'autres informations, veuillez vous référer à l'article
détaillé pour [Linux](linux).

Concernant les instructions sur le clonage de la source, le choix de la
branche, la configuration de CMake et la réalisation de la compilation à
proprement parler, voir ces instructions dans le guide
[Linux](linux). Les informations ci-dessous sont un
complément à cela.

RawTherapee exige GTK+ 3.22.24 ou plus récent car c'est la [première
version à supporter les fenêtres
natives](https://gitlab.gnome.org/GNOME/gtk/issues/760#note_110809),
sans quoi la fenêtre de RawTherapee pourrait présenter [un étrange
comportement](https://github.com/Beep6581/RawTherapee/issues/4125) comme
de s'agrandir sous la barre des tâches dans Windows 10.

La dernière version de RawTherapee à supporter GTK2 et compatible avec
Windows XP est 5.0-r1-gtk2 éditée le 02-02.2017.

## Installation de MSYS2

### Installation du système MSYS2 de base

Commencez par installer et mettre à jour MSYS2 en suivant soigneusement
les instructions du [MSYS2 site web](https://msys2.github.io/).

Mettre à jour le système MSYS2 de base jusqu'à ce que plus aucune mise à
jour ne soit disponible en utilisant :

    $ pacman -Syu

A la fin de l'installation, vous obtenez trois shells :

- MSYS2 shell : utilisé pour développer le cœur du système et gérer
  l'application MSYS2 (principalement la mise à jour des paquetages
  MSYS2)

<!-- -->

- MINGW64 shell : Il fournit l'environnement pour compiler les
  applications 64 bits.

<!-- -->

- MINGW32 shell : Il fournit l'environnement pour compiler les
  applications 32 bits.

<figure>
<img src="/images/MSYS2_Shell.jpg" title="File:MSYS2 Shell.jpg" />
<figcaption><a href="File:MSYS2">File:MSYS2</a> Shell.jpg</figcaption>
</figure>

Note : dans le texte qui suit, <MSYS2> désigne le répertoire
d'installation de MSYS2.

### Installation des outils et des bibliothèques

Le gestionnaire de paquetages de MSYS2 est pacman. Vous pouvez vous
référer au [manuel de
pacman](https://wiki.archlinux.org/index.php/pacman) pour plus de
détails.

Dans le shell MSYS2 :

Premièrement, installer quelques outils divers :

    $ pacman -S tar gzip nano make diffutils intltool git

Puis installer les outils de développement nécessaires :

    # win32
    $ pacman -S mingw-w64-i686-gcc mingw-w64-i686-gdb mingw-w64-i686-make mingw-w64-i686-pkg-config mingw-w64-i686-cmake
    # win64
    $ pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb mingw-w64-x86_64-make mingw-w64-x86_64-pkg-config mingw-w64-x86_64-cmake 

et les bibliothèques requises :

    # win32
    $ pacman -S  mingw-w64-i686-gtkmm3 mingw-w64-i686-lcms2 mingw-w64-i686-fftw mingw-w64-i686-lensfun 
    # win64
    $ pacman -S  mingw-w64-x86_64-gtkmm3 mingw-w64-x86_64-lcms2 mingw-w64-x86_64-fftw mingw-w64-x86_64-lensfun

### Obtenir les versions applicables des paquetages

Ce paragraphe doit être ignoré pour l'instant. Comme MSYS2 fournit des
rolling releases de ses paquetages, il peut arriver que de nouvelles
versions de certains paquetages soient incompatibles avec la version
présente de RawTherapee.

Voici une liste de tous les paquetages qui doivent rétrograder de
version :


    Liste vide

S'ils ne sont pas présents dans <MSYS2>\var\cache\pacman\pkg, ces
fichiers peuvent être téléchargés à
<http://repo.msys2.org/mingw/x86_64/>

Puis, dans le shell MSYS2, pour chaque fichier :

    Pacman -U <path-to-files>/mingw-w64-x86_64-...

Ajouter ce qui suit au fichier <MSYS2>\etc\pacman.conf pour empêcher
pacman de mettre les paquetages à jour.


    # Pacman ne mettra pas à jour les paquetages listés dans IgnorePkg et membres du IgnoreGroup

    IgnorePkg = mingw-w64-x86_64-<paquetageAIgnorer>
    ...

Si des paquetages sont interdépendants vous devez les installer avec la
même commande:

    Pacman -U <path-to>/<mingw-w64-x86_64-package1> <path-to>/<mingw-w64-x86_64-package2> ...

Pour compiler des applications 32 bits, faites ce qui suit en remplaçant
**x86_64** par **i386**.

### Mise à jour du système de base MSYS2 et des paquetages applicatifs

Dans le shell MSYS2 :

    $ pacman -Syuu

### Mise à jour de la base de données Lensfun

Dans le shell Mingw32 ou Mingw64 :

    $ lensfun-update-data

## Télécharger et compiler libiptcdata

Utiliser soit "*MinGW32 Shell*" pour compiler une version 32 bits, ou
"*MinGW64 Shell*" pour compiler une version 64 bits.

La bibliothèque libiptcdata n'est pas fournie par MSYS2, cependant, elle
est téléchargeable et configurable en utilisant :

    $ curl -LO http://downloads.sourceforge.net/project/libiptcdata/libiptcdata/1.0.4/libiptcdata-1.0.4.tar.gz
    $ tar xzf libiptcdata-1.0.4.tar.gz
    $ cd libiptcdata-1.0.4

    # win32
    $ ./configure --prefix=/mingw32
    # win64
    $ ./configure --prefix=/mingw64

Rester dans le même répertoire Le `Makefile` situé dans ce répertoire
doit être ouvert avec un éditeur de texte pour retirer `iptc` et `docs`
des listes nommées `SUBDIRS` et `DIST_SUBDIRS`, sinon, la compilation ou
l'installation échouera. Vous pouvez utiliser n'importe quel éditeur de
texte, par exemple Notepad++.

    #edition avec nano
    $ nano -m Makefile

    # Rechercher (commande ctrl/W)
    DIST_SUBDIRS = m4 libiptcdata po iptc docs win python
    # et remplacer par
    DIST_SUBDIRS = m4 libiptcdata po win python

    # Rechercher
    SUBDIRS = m4 libiptcdata po iptc docs win $(MAYBE_PYTHONLIB)
    # et remplacer par
    SUBDIRS = m4 libiptcdata po win $(MAYBE_PYTHONLIB)

    # Enregistrer
    ctrl/O

    # Quitter
    ctrl/X

Enfin, compiler et installer la bibliothèque :

    $ make
    $ make install
    $ cd

## Cloner et compiler RawTherapee

Utiliser soit "**MinGW32 Shell**" pour compiler une version 32 bits, ou
"**MinGW64 Shell**" pour compiler une version 64 bits.

### Cloner le dépôt Git de RawTherapee

Le processus de compilation va échouer s'il existe un espace dans le
chemin de votre répertoire `build`. Par exemple si votre nom
d'utilisateur sous Windows est "Zank Frappa" alors le nom du chemin sera
`C:\Users\Zank Frappa\` et si vous clonez RawTherapee dedans alors la
compilation échouera. Clonez dans un répertoire dont ni lui-même ni ses
répertoires parents n'ont d'espace dans leur nom, par exemple
`C:\code\repo-rt`

    $ git clone http://github.com/Beep6581/RawTherapee.git /c/code/repo-rt
    $ cd /c/code/repo-rt

Lors du clonage du dépôt, vous allez automatiquement vous retrouver dans
la branche `dev`. Pour basculer manuellement dans la branche `dev`,
faites ceci :

    $ git checkout dev

### Créer une répertoire séparé pour la compilation

    $ mkdir build
    $ cd build

Notez que si vous changez de branche, alors vous devez effacer et
re-créer le répertoire `build` afin que la compilation parte depuis le
début dans un répertoire vide, sinon la compilation risque d'échouer.
Cependant si vous faites une simple mise à jour sans changer de branche,
alors vous n'avez pas besoin de démarrer dans un répertoire build vide,
vous pouvez utiliser celui qui existe et la compilation sera plus rapide
car tout n'a pas besoin d'être re-compilé.

### Exécuter CMake et Make

    $ cmake -G "Ninja" -DLENSFUNDBDIR=put/your/lensfun/directory/here -DCMAKE_BUILD_TYPE="release" -DWITH_SYSTEM_LIBRAW="ON" -DPROC_TARGET_NUMBER="2" -DCACHE_NAME_SUFFIX="5-dev" ..
    $ cmake --build . --target install

L' option -DPROC_TARGET_NUMBER="2" va générer une compilation optimisée
pour votre l'architecture de votre PC (c'est à dire -march=native)

Vous pouvez trouver des explications au sujet de différentes options de
CMake dans la [page Linux](linux/fr#cmake), y compris une
explication des diverses options de "BUILD_TYPE".

Si vous réalisez une compilation pour Windows 32 bits et utilisez le
"BUILD_TYPE" `release` ou `relwithdebinfo`, vous aurez besoin d'ajouter
le drapeau de compilation `-mstackrealign` avant les deux derniers
points `..` de la commande CMake ci-dessus :

    -DCMAKE_C_FLAGS="-mstackrealign" -DCMAKE_CXX_FLAGS="-mstackrealign"

### Démarrer RawTherapee

RawTherapee peut maintenant être démarré depuis la ligne de commande de
MINGW64 :

    # pour les compilations debug
    $ cd debug
    # pour les compilations release
    $ cd release
    # pour les compilations relwithdebinfo
    $ cd relwithdebinfo
    $ ./rawtherapee.exe

## Copier RawTherapee et les DLL requises

Vous pouvez réaliser les copies soit avec le gestionnaire de fichiers de
Windows ou, plus recommandé, avec
[robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)
à l'intérieur du script shell `<mingw32|mingw64>` en utilisant pour les
options `-` à la place de `/`.

Définition des répertoires :

- <prefix> est <MSYS2>`\<mingw32|mingw64>`,
- <MSYS2> est le dossier d'installation de MSYS2,
- et `.` est le dossier d'installation de RawTherapee.

Copier le contenu de
`c:\code\repo-rt\build\<debug|release|relwithdebinfo>` dans `.`.

Copier les DLL et exe nécessaires de <prefix>`\bin` dans `.`.

Voici une liste des DLL et exe requis :

    gspawn-<win32|win64>-helper.exe
    gspawn-<win32|win64>-helper-console.exe
    gdbus.exe
    libatk-1.0-0.dll
    libatkmm-1.6-1.dll
    libbz2-1.dll
    libcairo-2.dll
    libcairo-gobject-2.dll
    libcairomm-1.0-1.dll
    libcroco-0.6-3.dll
    libdatrie-1.dll
    libepoxy-0.dll
    libexpat-1.dll
    libfﬁ-6.dll
    libfftw3f-3.dll
    libfontconﬁg-1.dll
    lilibfribidi-0.dll
    libfribidi-0.dll
    libgcc_s_seh-1.dll (ou libgcc_s_dw2-1.dll pour W32) 
    libgdk_pixbuf-2.0-0.dll
    libgdk-3-0.dll
    libgdkmm-3.0-1.dll
    libgio-2.0-0.dll
    libgiomm-2.4-1.dll
    libglib-2.0-0.dll
    libglibmm-2.4-1.dll
    libgmodule-2.0-0.dll
    libgobject-2.0-0.dll
    libgomp-1.dll
    libgraphite2.dll
    libgtk-3-0.dll
    libgtkmm-3.0-1.dll
    libharfbuzz-0.dll
    libiconv-2.dll
    libintl-8.dll
    libjpeg-8.dll
    liblcms2-2.dll
    liblensfun.dll
    liblzma-5.dll
    libpango-1.0-0.dll
    libpangocairo-1.0-0.dll
    libpangoft2-1.0-0.dll
    libpangomm-1.4-1.dll
    libpangowin32-1.0-0.dll
    libpcre-1.dll
    libpixman-1-0.dll
    libpng16-16.dll
    librsvg-2-2.dll
    libsigc-2.0-0.dll
    libstdc++-6.dll
    libsystre-0.dll
    libthai-0.dll
    libtiff-5.dll
    libtre-5.dll
    libwinpthread-1.dll
    libxml2-2.dll
    libzstd.dll
    zlib1.dll

Copier la liste suivante des fichiers et rèpertoires du thème Adwaita
doivent être copiés de <prefix>`\share\icons\Adwaita\` vers
`.\share\icons\Adwaita\`:

    scalable\actions
    scalable\devices
    scalable\mimetypes
    scalable\places
    scalable\status
    scalable\ui
    index.theme

    cursors\plus.cur
    cursors\sb_h_double_arrow.cur
    cursors\sb_left_arrow.cur
    cursors\sb_right_arrow.cur
    cursors\sb_v_double_arrow.cur

Copier les fichiers suivants :


    <prefix>\lib\gdk-pixbuf-2.0 -> .\lib\gdk-pixbuf-2.0

    <prefix>\share\glib-2.0\schemas\gschemas.compiled -> .\share\glib-2.0\schemas
    <prefix>\share\lensfun\version_1\* -> .\share\lensfun

Dans .\share\gtk-3.0 créer un fichier `settings.ini` contenant :

    [Settings] gtk-button-images=1

## Création d'un paquetage distribuable

Si vous avez l'intention de distribuer des paquetages de RawTherapee
pour la plateforme Windows, vous devez tout d'abord vous assurer que
RawTherapee sera compilé avec pour cible le processeur "générique". Pour
cela, indiquer `-DPROC_TARGET_NUMBER="1"` dans la commande CMake.

Pendant la compilation, un script nommé `WindowsInnoSetup.iss` est créé
dans le répertoire d'installation de RawTherapee. Ce script est utilisé
par Inno Setup [1](http://www.jrsoftware.org/isinfo.php), un programme
qui est utilisé pour générer des installateurs pour les programmes
Windows. Il est conseillé de télécharger la version Unicode
[2](http://www.jrsoftware.org/download.php/is-unicode.exe) pour éviter
les problèmes avec certaines langues.

Pour aider les utilisateurs [à écrire de bons rapports de
bogues](How_to_write_useful_bug_reports/fr.md), les mainteneurs
de paquetages sont encouragés à produire des compilations qui
contiennent à la fois un exécutable "release" et un "debug", et de les
rassembler avec l'exécutable GDB debugger.

En d'autres termes, mettre ensemble le fichier `rawtherapee.exe`
(release), le fichier `rawtherapee-debug.exe` (debug) et le fichier
`gdb.exe` dans le même installeur ou la même archive. Une autre méthode
est de réaliser des compilations "relwithdebinfo", elles sont beaucoup
plus rapides que "debug", mais pas autant optimisées que "release", et
fournissent a peu près autant d'informations utiles que "debug".

Lors de la réalisation de compilations "relwithdebinfo" ou "debug", vous
devez fournir l'exécutable du debugger GDB. Les binaires Windows du
debugger `gdb.exe` peuvent être téléchargés depuis
[ici](http://www.equation.com/servlet/equation.cmd?fa=gdb) dans les
versions 32 et 64 bits et seront copiés dans le répertoire
d'installation de RawTherapee.

Maintenant que tout est en place, pour créer le paquetage cliquer droit
sur le script `WindowsInnoSetup.iss` et choisir *Compile* dans le menu
contextuel. Il va générer l'installeur automatiquement et le placer dans
le répertoireparent.

Pour rendre votre paquetage compatible avec le panneau de télévezrsement
du site web de RawTherapee, créer une archive zip dans laquelle vous
placerez ensemble l'installeur nouvellement créé et les fichiers
*AboutThisBuild.txt* correspondants qui se trouvent à le même place.
Nommer l'archive zip résultante selon ce modèle :

`RawTherapee_`<version>`_WinVista_<32|64>_`<buildtype>`.zip`

Si vous compilez et distribuez des "nightly builds" (compilations de
dernière minute), suivez ce modéle :

`RawTherapee_`<branch>`_`<version>`_WinVista_<32|64>_`<buildtype>`.zip`

- "WinVista" signifie qu'il peut s'exécuter sur toute version de Windows
  depuis Vista et après, y compris 10.

<!-- -->

- la "version" ressemblera soit à `5.2` si vous utilisez la balise
  `5.2`, ou à `5.2-dev-g1a2b3c4d` si vous utilisez la branche `dev`
  après avoir balisé 5.2.

<!-- -->

- Si vous fournissez plus d'un type de compilation dans l'installeur, ne
  pas inclure <buildtype> dans le nom.
