---
title: MacOS
contributors:
  - Lebarhon
tags:
  - 'Compiling'
---

<div class="pagetitle">

MacOS

</div>

Cette page détaille les instructions pour compiler RawTherapee sur les
systèmes **macOS**. Il existe aussi une page séparée pour la compilation
sur [Linux](linux/fr) et [Windows](windows/fr).
Cette page détaille le **Quoi** et le **Comment** de la compilation.
Pour le **Pourquoi** et les explications de ces commandes, pour avoir la
liste des dépendances, les options de CMake et d'autres informations,
veuillez vous référer l'article détaillée de
[Linux](linux/fr).

En cas de doute, [joigniez nous sur IRC](irc/fr) et demandez
à un humain !

Pour obtenir des instructions sur le clonage de la source, le choix de
la branche, la configuration de CMake et la réalisation de la
compilation, voir ces chapitres dans le guide [Linux](linux).
Les informations ci-dessous viennent en complément.

## Dépendances

Voir la liste des dépendances dans le chapitre [Compilation avec
Linux](Linux/fr#Dépendances.md).

### Homebrew

La commande suivante installe les dépendances de RawTherapee :
`brew install gtk+3 gtkmm3 gtk-mac-integration adwaita-icon-theme libsigc++ little-cms2 libiptcdata fftw lensfun wget llvm cmake expat pkgconfig libomp`

### MacPorts

Testé sur OS X 10.9 et suivants

- **Prérequis :**
  - Outils du développeur Xcode & Outils en ligne de commande
  - MacPorts
    - Des instructions détaillées concernant la configuration des
      MacPorts et les outils du développeur sot disponibles sur le [Site
      Web MacPorts](https://www.macports.org).
- **Configurer MacPorts :**

  
Ajouter la ligne suivante à /opt/local/etc/macports/variants.conf:

  
`+quartz -x11 -gnome`

- **Dépendances**

  
Pour installer les indépendances, exécuter dans un terminal :

  
`sudo port install git clang++-mp-9.0 libomp gtk3 gtkmm3 gtk-osx-application-gtk3 adwaita-icon-theme libsigcxx2 lcms2 libiptcdata fftw-3-single lensfun`

Si vous compilez avec Xcode 9.2 vous devez aussi faire :

  
`sudo port install ld64 +ld64_xcode`

- **Configuration du système de compilation pour MacPorts**

  
Ajouter le drapeau suivant à la commande `cmake` :

  
`-DLOCAL_PREFIX=PATH:"/opt"`

## Compilation

Voir les instructions dans l'article [Compilation avec
Linux](Linux/fr#Compilation_:_la_méthode_manuelle.md) pour
savoir comment **cloner** le code source, choisir une **branche** et
configurer **CMake**. Ignorer le code "Maintenant, vous êtes prêt pour
la compilation : " de cette page mais suivre le code ci-dessous.

Si vous désirez téléverser une compilation ou éventuellement la partager
avec d'autres, vous devez utiliser :

  
`-DPROC_TARGET_NUMBER="1"`

et paramétrer manuellement le label du processeur en entrant :

  
`-DPROC_LABEL="generic processor"`

Si vous désirez compiler pour vous même uniquement, alors utiliser :

  
`-DPROC_TARGET_NUMBER="2"`

et le label du processeur est alors inutile, vous pouvez l'ignorer.

Si vous désirez [signer le
code](https://developer.apple.com/support/code-signing/) de votre
compilation, ajoutez vos éléments dans la commande CMake :

  
`-DCODESIGNID:STRING="Identification du développeur : Nom prénom (XXXXXXXXXX)"`

L'application et le dmg (Apple Disk Image) générés seront signés.

Pour
[certifier](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution/customizing_the_notarization_workflow?language=objc)
votre compilation signée, incluez vos crédits dans la commande CMake :

  
`-DNOTARY="--username user@mail.com --password abcd-efgh-ijkl-mnop"`

L'application et le dmg seront certifiés (scannés pour détecter les
malwares) et annexés (le ticket de certification sera joint).

### Compiler RawTherapee

Vous êtes maintenant prêt à compiler :

    cd ~/repo-rt
    rm -rf build
    mkdir build && cd build
    cmake -DCMAKE_BUILD_TYPE="release" \
          -DPROC_TARGET_NUMBER="1" \
          -DPROC_LABEL="generic processor" \
          -DCACHE_NAME_SUFFIX="5-dev" \
          -DCMAKE_C_COMPILER="clang-mp-9.0" \
          -DCMAKE_CXX_COMPILER="clang++-mp-9.0" \
          -DWITH_LTO="OFF" \
          -DLENSFUNDBDIR="./share/lensfun" \
          ..
    make -j$(sysctl -n hw.ncpu) install
    sudo make macosx_bundle

<hr>

Si vous compilez avec les dépendances maison w/llvm clang 8, utiliser la
commande cmake suivante :

    export PKG_CONFIG_PATH=/usr/local/opt/libffi/lib/pkgconfig:/usr/local/opt/expat/lib/pkgconfig && \
    cmake  .. -DCMAKE_BUILD_TYPE="release" \
              -DPROC_TARGET_NUMBER="2" \
              -DCACHE_NAME_SUFFIX="5.8-dev" \
              -DCMAKE_C_COMPILER="clang"\
              -DCMAKE_CXX_COMPILER="clang++" \
              -DWITH_LTO="ON" \
              -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
              -DCMAKE_BUILD_TYPE=Release \
              -DOpenMP_C_FLAGS=-fopenmp=libomp \
              -DOpenMP_CXX_FLAGS=-fopenmp=libomp \
              -DOpenMP_C_LIB_NAMES="libomp" \
              -DOpenMP_CXX_LIB_NAMES="libomp" \
              -DOpenMP_libomp_LIBRARY="/usr/local/lib/libomp.dylib" \
              -DOpenMP_CXX_FLAGS="-Wno-pass-failed -Wno-deprecated-register -Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
              -DOpenMP_CXX_LIB_NAMES="libomp" \
              -DOpenMP_C_FLAGS="-Wno-pass-failed -Wno-deprecated-register -Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
              -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
              -DCMAKE_EXE_LINKER_FLAGS="-L/usr/local/opt/libffi/lib -L/usr/local/lib" \
              -DCMAKE_AR="/usr/local/Cellar/llvm/8.0.0/bin/llvm-ar" \
              -DCMAKE_RANLIB="/usr/local/Cellar/llvm/8.0.0/bin/llvm-ranlib"

### Méthode depuis zéro

- Cette
  [1](https://raw.githubusercontent.com/Benitoite/RTdeps/master/macbuildRT.sh)
  liste complète de commandes peut éventuellement être utilisée pour
  réaliser la compilation de RawTherapee et de ses dépendances depuis
  zéro sur macOS 10.15.3 / Xcode 11.
- JDK[2](https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html)
  doit être installé.
- Xcode 11.1+ [3](https://developer.apple.com/xcode) doit être installé.

<hr>

### Exécutez et partagez RawTherapee

Vous trouverez une image disque dans le répertoire de compilation ;
c'est l'édition de distribution qui peut être exécutée sur n'importe
quelle machine qui répond aux exigences de l'architecture spécifiées
auparavant dans le fichier variants.conf.

Le fichier zip généré est nommé selon ce modèle :

  
RawTherapee_OSX_**<minimum supported macOS version>**_64_**<RawTherapee version>**.dmg.zip

RawTherapee_OSX_10.9_64_5.8-94-g4dbbc4053.dmg.zip

Téléverser l'archive zip vers <http://filebin.net/> et [open a new issue
on our GitHub page](https://github.com/Beep6581/RawTherapee/issues/new)
avec le lien afin que nous puissions le téléverser sur le site web.

#### macOS 10.15

- Pour exécuter RawTherapee 5.8 sur macOS 10.15 *Catalina* vous devez :
  - Copier l'application dans le dossier `/Applications``/Applications`
    et l'éxécuter depuis ce dossier.
  - Ajouter `/bin/sh` dans Préférences système \> Sécurité et vie privée
    \> Vie privée \> Accès à tout le disque. Vous serez invité à faire
    cela automatiquement lors du premier démarrage du programme.
