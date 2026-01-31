---
title: Linux
contributors:
  - Lebarhon
  - Jdc
tags:
  - 'Compiling'
---

<div class="pagetitle">

Linux

</div>

Cette page détaille les instructions pour compiler RawTherapee dans les
systèmes **GNU/Linux**. Vous trouverez aussi des instructions pour la
compilation dans [Windows](windows/fr) et
[MacOS](macos/fr).

En cas de doute, [Joigniez nous sur IRC](irc/fr) ou sur le
[Forum](forum/fr) et demandez à un humain !

## Dépendances

Pour compiler RawTherapee votre système nécessite un jeu d'outils et des
bibliothèques venues d'autres programmes. Ils sont appelés dépendances,
en voici la liste pour la dernière version de RawTherapee.

| Package     | Version             | URL                                                                         |
|-------------|---------------------|-----------------------------------------------------------------------------|
| CMake       | cmake\>=3.5         | <https://cmake.org/>                                                        |
| EXIV2       | exiv2\>=0.19        | <http://www.exiv2.org/>                                                     |
| EXPAT       | expat\>=2.1.0       | <https://libexpat.github.io/>                                               |
| FFTW3       | fftw\>=3.2.2        | <http://fftw.org/>                                                          |
| GCC         | gcc\>=4.9           | <https://gcc.gnu.org/>                                                      |
| GLIB2       | glib-2.0\>=2.24     | <https://www.gtk.org/>                                                      |
| GLIBMM      | glibmm-2.4\>=2.24   | <https://www.gtkmm.org/>                                                    |
| GTK+        | gtk+-3.16 \< 3.24.0 | <https://www.gtk.org/>                                                      |
| GTKMM       | gtkmm-3.16          | <https://www.gtkmm.org/>                                                    |
| JPEG        | libjpeg\>=6b        | <https://libjpeg-turbo.org/> <https://jpegclub.org/> <https://www.ijg.org/> |
| LCMS2       | lcms\>=2.6          | <http://www.littlecms.com/>                                                 |
| LENSFUN     | lensfun\>=0.2       | <http://lensfun.sourceforge.net/>                                           |
| LIBCANBERRA | libcanberra\>=0.29  | <http://0pointer.de/lennart/projects/libcanberra/> (Linux only)             |
| LIBIPTCDATA | libiptcdata\>=1.0.2 | <http://libiptcdata.sourceforge.net>                                        |
| PNG         | libpng\>=1.2.44     | <http://www.libpng.org/>                                                    |
| librsvg     | librsvg\>=2.40      | <https://github.com/GNOME/librsvg>                                          |
| SIGC        | sigc++-2.0          | <https://github.com/libsigcplusplus/libsigcplusplus>                        |
| TIFF        | libtiff\>=4.0.4     | <http://libtiff.org/>                                                       |
| ZLIB        | zlib\>=1.2.3        | <http://www.zlib.net/>                                                      |

Dépendances pour RawTherapee:

Pour installer toutes ces dépendances, vous devez ouvrir une console et
y coller le code de la section appropriée. Les fragments de code
ci-dessous listent les dépendances pour la dernière version de
RawTherapee qui exige GTK3. Nous avons laissé tombé le support de GTK2
depuis l'édition "5.0-r1-gtk2" de février 2017. Si vous utilisez une
distribution moderne, simplement copier et coller les fragments de code
tels qu'ils sont. Si vous êtes sur une vieille distribution sans le
support de GTK3, alors reportez vous sur l'article archivé
[GTK2](linux_gtk2/fr), puis choisissez et compilez la balise
obsolète `5.0-r1-gtk2`.

### Arch/Manjaro

Les versions actuelles de Arch et de Manjaro fonctionnent correctement
"au sortir de la boite". Reportez vous à l'article
[GTK2](linux_gtk2/fr) si vous compilez sur une version
antérieure à 17.1.2.

    sudo pacman -S --needed bzip2 cmake exiv2 expat fftw glib2 glibmm gtk3 gtkmm3 lcms2 lensfun libcanberra libiptcdata libjpeg-turbo libpng librsvg libsigc++ libtiff zlib

Procéder à la [compilation](#compilation).

### CentOS

CentOS 7 possède des paquetages très dépassés et nécessite des étapes
supplémentaires pour installer des versions récentes de GCC, git,
lensfun et libtiff. Les étapes ci-dessous ont été vérifiées et
fonctionnent dans CentOS 7.4.1708, mais vous les utiliserez à votre
propre risque.

GCC \>=4.9.3:

    sudo yum update
    sudo yum install cmake git
    sudo yum install centos-release-scl
    sudo yum install devtoolset-7-gcc*
    scl enable devtoolset-7 bash
    source /opt/rh/devtoolset-7/enable

git \>=2.7:

    sudo yum install http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-2.noarch.rpm

lensfun:

    wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
    sudo rpm -ivh epel-release-latest-7.noarch.rpm

libtiff \>=4.0.4:

    sudo yum install ninja-build
    mkdir ~/programs && cd ~/programs
    wget http://download.osgeo.org/libtiff/tiff-4.0.9.tar.gz
    tar zxvf tiff-4.0.9.tar.gz
    mkdir tiff-4.0.9/libtiff-build && cd tiff-4.0.9/libtiff-build
    cmake -DCMAKE_INSTALL_DOCDIR=/usr/share/doc/libtiff-4.0.9 -DCMAKE_INSTALL_PREFIX=/usr -G Ninja ..
    ninja-build
    sudo ninja-build install

Installation des autres dépendances :

    sudo yum install curl expat-devel fftw-devel gtk3-devel gtkmm30-devel lcms2-devel lensfun-devel libcanberra-devel libiptcdata-devel libjpeg-turbo-devel libpng-devel librsvg2-devel zlib-devel

Lien symbolique vers libatomic :

    sudo ln -s /usr/lib64/libatomic.so.1 /usr/lib64/libatomic.so

Pour procéder à la prochaine étape, la compilation, vous aurez besoin
d'éditer le script `build-rawtherapee` et ajoutez ces trois lignes dans
la section CMake près de la fin du fichier, par exemple après la ligne
"-DWITH_BENCHMARK" et avant la ligne "\$HOME" :

        -DTIFF_INCLUDE_DIR="$HOME/programs/tiff-4.0.9/libtiff" \
        -DTIFF_LIBRARY="$HOME/programs/tiff-4.0.9/libtiff-build/libtiff/libtiff.so" 
        -DCMAKE_CXX_FLAGS="-Wno-deprecated -Wno-parentheses" \

Procéder à la [compilation](#compilation).

### Debian/Ubuntu/Mint/elementary OS

Les versions actuelles de ces distributions fonctionnent correctement
"au sortir de la boite". Reportez vous à l'article
[GTK2](linux_gtk2/fr) si vous compilez sur une version
d'Ubuntu antérieure à 16.04.

==== Ubuntu \>=16.10, Mint \>=18.3, elementary OS \>=0.4.1 ====

    sudo apt update
    sudo apt install build-essential cmake curl git libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg-dev liblcms2-dev libpng-dev librsvg2-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

Procéder à la [compilation](#compilation).

#### Ubuntu 16.04 LTS

    sudo apt-get update
    sudo apt-get install build-essential cmake curl git libbz2-dev libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg8-dev liblcms2-dev liblensfun-dev libpng12-dev librsvg2-dev  libsigc++-2.0-dev libtiff5-dev zlib1g-dev

Procéder à la [compilation](#compilation).

### Fedora

Les versions actuelles de Fedora fonctionnent correctement "au sortir de
la boite". Reportez vous à l'article [GTK2](linux_gtk2/fr) si
vous compilez sur une version antérieure à 22.

    sudo dnf install cmake curl expat-devel fftw-devel gcc-c++ git exiv2-devel gtk3-devel gtkmm30-devel lcms2-devel lensfun-devel libatomic libcanberra-devel libiptcdata-devel libjpeg-turbo-devel libpng-devel librsvg2-devel libtiff-devel zlib-devel

Procéder à la [compilation](#compilation).

### Gentoo/Sabayon

Les utilisateurs de Sabayon doivent pouvoir utiliser les mêmes
dépendances que pour Gentoo, mais à la place de `sudo emerge -uva`,
prendre `sudo equo install sys-devel/gcc dev-vcs/git`.

    sudo emerge -uva dev-cpp/gtkmm:3.0 dev-libs/expat dev-util/cmake media-gfx/exiv2 media-libs/lcms media-libs/lensfun media-libs/libcanberra media-libs/libiptcdata media-libs/libjpeg-turbo media-libs/libpng gnome-base/librsvg media-libs/tiff net-misc/curl sci-libs/fftw sys-libs/zlib x11-libs/gtk+:3

Procéder à la [compilation](#compilation).

### openSUSE

Les versions d'openSUSE supérieures à Leaf 15.0 et Tumbleweed devraient
fonctionner sans aucune réserve. Des problèmes sérieux de compilation
sont probables avec les versions antérieures. Reportez vous à l'article
[GTK2](linux_gtk2/fr) si vous compilez sur une version
antérieure à 42.1.

    sudo zypper cmake gcc gcc-c++ gtk3-devel gtkmm3-devel liblcms2-devel fftw3-devel libitpcdata-devel librsvg-devel libtiff-devel libjpeg-devel libcanberra-gtk3-devel

Ensuite, `lensfun` doit être installé manuellement:

    wget https://sourceforge.net/projects/lensfun/files/0.3.2/lensfun-0.3.2.tar.gz
    tar xvf lensfun-0.3.2.tar.gz
    cd lensfun-0.3.2.tar.gz
    mkdir build
    cd build
    cmake ../
    make
    sudo make install

Procéder à la [compilation](#compilation).

## Compilation

Il existe deux écoles pour compiler RawTherapee : soit utiliser le
script Bash [automatique](#la_méthode_automatique) qui
compile RawTherapee à votre place (recommandé), ou faites le
[manuellement](#la_méthode_manuelle).

### La méthode automatique

Voici la façon recommandée pour compiler RawTherapee car elle est
rapide, simple et sûre. Elle s'appuie sur un script Bash qui télécharge
le dernier code source de RawTherapee et le compile de façon optimisée
pour votre processeur. Les compilations sont prêtes à l'usage. Le script
ne vérifie pas la disponibilité des dépendances, lisez donc bien le
chapitre [Dépendances](linux/fr#dépendances) avant de lancer
le script. Les compilations sont autonomes, c'est à dire que vous pouvez
faire cohabiter plusieurs versions de RawTherapee en même temps,
simplement en renommant les dossiers de compilation afin que la création
d'une nouvelle compilation n'écrase pas la précédente, ce qui est le cas
par défaut.

Lancer le script sous un compte utilisateur, pas sous root !

Ouvrir un terminal, aller chercher le script, le rendre exécutable et le
lancer :

    cd ~
    wget https://raw.githubusercontent.com/Beep6581/RawTherapee/dev/tools/build-rawtherapee -O build-rawtherapee
    chmod +x build-rawtherapee
    ./build-rawtherapee

Si tout va bien, le script se terminera par le message "Pour lancer
RawTherapee entrer : ..."

Pour mettre RawTherapee à jour si vous l'avez précédemment compilé avec
ce script, simplement exécuter à nouveau le script, c'est tout.

Le script `build-rawtherapee` est inclus dans le code source de
RawTherapee. Puisque l'exécution du script met le code source à jour,
après votre première compilation vous pouvez effacer le script
téléchargé manuellement ci-dessus avec wget, et utiliser à la place
`~/programs/code-rawtherapee/tools/build-rawtherapee` qui se maintiendra
toujours à jour.

Le script compile la branche courante, qui est par défaut `dev` où est
réalisé la plupart du développement. Pour compiler une branche
différente, la récupérer en utilisant les commandes git usuelles avant
d'exécuter le script. Pour en savoir plus au sujet des branches de
RawTherapee lire ci-dessous le paragraphe [Choisir une
branche](Linux/fr#Choisir_une_branche.md).

Pour plus d'informations, voir `./build-rawtherapee --help`.

Vous avez terminé, RawTherapee est prêt à l'utilisation. Vous pouvez
passer le chapitre "La méthode manuelle"

### La méthode manuelle

La façon recommandée pour compiler RawTherapee est d'utiliser le script
automatique, voir [la méthode
automatique](#La_méthode_automatique.md). Pour apprendre à
compiler manuellement, continuez la lecture.

Afin de préserver le bon ordre dans votre répertoire "home" pendant la
compilation manuelle de multiples programmes (par ex. en n'utilisant pas
le gestionnaire de paquetages de votre distribution) et pour que ce
tutoriel de compilation manuelle reste compatible avec le script de
compilation automatique, veuillez créer le dossier `~/programs/` qui va
contenir dans le dossier `~/programs/code-rawtherapee`, tous les codes
sources relatifs à RawTherapee, et dans le dossier
`~/programs/rawtherapee`, la compilation. Vous pouvez utiliser la même
disposition pour compiler d'autres programmes.

#### Cloner la source

Premièrement, il faut cloner le dépôt du code source de RawTherapee.
Ouvrir une console et exécuter ces commandes :

    mkdir -p ~/programs
    git clone https://github.com/Beep6581/RawTherapee ~/programs/code-rawtherapee
    cd ~/programs/code-rawtherapee

#### Choisir une branche

- Les fonctionnalités sont développées sur leur propre branche de
  fonctionnalité
- Les développements sont effectués dans la branche `dev`. Les branches
  de fonctionnalité sont fusionnées avec la branche `dev` quand elle
  sont prêtes. La branche `dev` est instable.
- Les publications sont issues de la branche `releases`.

Essayez la dernière publication si vous souhaitez la version la plus
stable. Pour voir toutes les branches disponibles, tapez :

    git tag

Choisir la branche `dev` ou une autre branche de fonctionnalité si
désirez tester le code dernier cri. Pour voir toutes les branches
disponibles tapez :

    git branch -a

Le "choix" se fait via la commande "git checkout". Pour choisir une
publication ou une branche, tapez

    git checkout <publication ou branche>

RawTherapee utilise GTK+ pour l'interface utilisateur et exige la
version 3.16 ou supérieure. Si votre système ne supporte pas cette
version 3.16 ou plus récente, vous devez utiliser la publication
`5.0-r1-gtk2`. Notre support de GTK2 a officiellement cessé le 02
février 2017. Reportez vous à l'article archivé
[GTK2](linux_gtk2/fr) et mettez votre système à jour.

La compilation d'anciennes versions de RawTherapee échouera sur un
système moderne, car les vieilles dépendances seront manquantes.

#### Compiler RawTherapee

Vous allez maintenant réaliser une compilation de RawTherapee, elle sera
construite dans le dossier `~/programs/code-rawtherapee/build/release`,
et ensuite vous déplacerez ce dossier dans `~/programs/rawtherapee`

##### CMake

Vous devez avoir connaissance de quelques paramètres de compilation,
vous passerez ceux-ci à CMake en utilisant l'option `-D`, comme décrit
ci-dessous :

CMAKE_BUILD_TYPE  
Un des suivants : `release` (par defaut), `relwithdebinfo` ou `debug`.

Cela détermine si la compilation doit favoriser la rapidité d’exécution
ou la quantité des commentaires en sortie de déboguage.

Les compilations "relwithdebinfo" et "debug" vous fournira une [trace
d'appels bien utile](How_to_write_useful_bug_reports/fr.md) si
RawTherapee se plante pendant l'exécution de GDB et vous pourrez nous la
soumettre afin que nous puissions résoudre le problème. La compilation
"debug" est la plus lente mais génère les informations les plus
détaillées. La compilation "relwithdebinfo" est presque aussi rapide
qu'une compilation "release" et génère le plus souvent suffisamment
d'informations bien que pas aussi détaillées qu'avec la compilation
"debug". La compilation "release" ne fournira aucune information mais
contient de nombreuses optimisations de la vitesse ce qui en fait un
programme qui fonctionne beaucoup plus vite que la version "debug". Pour
une utilisation usuelle choisissez une compilation "release" ou
"relwithdebinfo". Si vous tombez sur un bug reproductible, alors
refaites la compilation avec "debug" et envoyez nous la trace d'appels
(ou réparez vous même et envoyez nous le patch !). Nous préférons les
traces d'appels des compilations debug plutôt que celles des
compilations relwithdebinfo

  
Pour réaliser une compilation de type "release", écrire
`-DCMAKE_BUILD_TYPE="release"`

<!-- -->

USE_OLD_CXX_ABI  
`ON` or `OFF` (par défaut).

Lors de la compilation d'un programme, on doit utiliser les mêmes
conventions que celles utilisées par les bibliothèques appelées par
ledit programme, sinon, la compilation (création des liens) échouera. En
général, on n'a pas besoin de s'en préoccuper, mais nous sommes
actuellement à une époque de remplacement progressif de GCC4 par GCC5,
chacun utilisant par défaut une convention incompatible avec l'autre, ce
qui est la cause du problème. Si les bibliothèques sur votre système ont
été compilées avec GC5, elles utilisent probablement un standard appelé
C++11. Cela signifie que votre compilation de RawTherapee doit utiliser
le même standard, ce qui est le cas par défaut. Cependant, si malgré
l'utilisation de GCC5 vos bibliothèques étaient compilées avec l'ancien
standard C++03, alors RawTherapee doit être paramétré pour utiliser le
même, et pour cela vous devez configurer "USE_OLD_CXX_ABI" sur "ON":

<!-- -->

  
  
Pour valider USE_OLD_CXX_ABI, écrire : `-DUSE_OLD_CXX_ABI="ON"`

<!-- -->

CACHE_NAME_SUFFIX  
Les options CACHE_NAME_SUFFIX définissent le suffixe des noms du
répertoire de configuration et du cache qui seront utilisés par la
compilation de RawTherapee. : Voir l'article [Où sont les fichiers
?](File_Paths/fr.md) pour une explication de ce que sont ces
répertoires.

<!-- -->

  
Pour les versions stables (si vous choisissez la branche "releases")
mettre `-DCACHE_NAME_SUFFIX=""`

<!-- -->

  
Pour les compilations de développement (si vous choisissez la branche
"dev" ou toute autre branche que "releases") mettre
`-DCACHE_NAME_SUFFIX="5-dev"`

<!-- -->

PROC_TARGET_NUMBER  
Entre `0` (par défaut) et `9`.

L'option PROC_TARGET_NUMBER définit pour quel type de CPU doit se faire
l’optimisation.

Si vous compilez pour vous-même, mettre "2". Cela signifie "natif", donc
l'optimisation sera automatiquement pour le CPU détecte et RawTherapee
sera aussi rapide que possible sur votre CPU. Il se peut qu'il ne
fonctionne pas du tout sur d'autres architectures.

Si vous compilez pour distribuer (à d'autres personnes), mettre "1".
Cela signifie "générique", ainsi seules les optimisations supportées par
le plus grand nombre de CPU seront utilisées, la compilation peut donc
être téléchargée et utilisée par tout le monde, mais n'aura pas les
meilleures optimisations possibles.

Pour plus d'informations, voir le fichier "ProcessorTargets.cmake" dans
le dossier cloné.

  
Pour que la compilation utilise l'optimisation "native", écrire :
`-DPROC_TARGET_NUMBER="2"`

<!-- -->

BUILD_BUNDLE  
`ON` ou `OFF`

Il est forcé sur "ON "pour Windows et macOS. Optionnel pour Linux où
c'est "OFF" par défaut.

Si réglé sur "ON", le programme sera compilé dans un répertoire
(`DATADIR`), sinon il sera installé selon `CMAKE_INSTALL_PREFIX` qui
vaut typiquement pour tout le système.

<!-- -->

BUNDLE_BASE_INSTALL_DIR  
Utiliser un chemin absolu.

Le programme sera compilé dans ce répertoire.

Par exemple, choisir :
`-DBUNDLE_BASE_INSTALL_DIR="$HOME/programs/rawtherapee"`

S'il n'est pas défini, `${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE}` sera
utilisé par défaut

<!-- -->

LENSFUNDBDIR  
Non défini par défaut

L'option `LENSFUNDBDIR` permet de situer la base de données lensfun dans
le répertoire spécifié. Elle peut être non définie, absolue ou relative.

Si non définie, alors Lensfun utilise sa propre logique pour trouver la
base de donnée. C'est l'option recommandée si Lensfun est déjà installée
pour tout le système et que vous souhaitez l'utiliser.

Vous pouvez choisir un chemin relatif ou absolu pour utiliser une base
de données lensfun personnalisée.

Si vous compilez un lot, le chemin est relatif au répertoire racine du
lot, sinon il est relatif au `DATADIR`, c'est-à-dire
`${CMAKE_INSTALL_PREFIX}/share/rawtherapee`

<!-- -->

OPTION_OMP  
`ON` (par défaut) ou `OFF`.

Si validé, compile avec le support de OpenMP, ce qui valide le
multithreading et rend RawTherapee plus rapide.

<!-- -->

WITH_LTO  
`ON` ou `OFF` (par défaut).

Si validé, compile avec les optimisations de link-time, ce qui peut
rendre RawTherapee un peu plus rapide.

<!-- -->

WITH_PROF  
`ON` ou `OFF` (par défaut).

Pour des fins de débogage. Génère du code supplémentaire pour écrire des
informations de profil adaptées au programme d'analyse gprof.

<!-- -->

WITH_SAN  
`OFF` (défaut) ou l'une des diverses autres options.

Pour des fins de débogage. Permet d'activer divers débogueurs.

Voir le chapitre [Program Instrumentation
Options](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html)
du manuel de GCC davantage d'informations.

<!-- -->

WITH_SYSTEM_KLT  
`ON` ou `OFF` (par défaut).

Si sur ON, compiler en utilisant la bibliothèque du systeme KLT, sinon,
utilise le bouquet de fichiers KLT avec RawTherapee.

Le détecteur de traits Kanade–Lucas–Tomasi (KLT) feature tracker est
utilisé par l'outil de [Correction automatique de la
distortion](Lens/Geometry/fr#Distorsion.md).

<!-- -->

WITH_BENCHMARK  
`ON` ou `OFF` (par défaut).

Compilation avec les fonctions de synchronisation en service pour
mesurer les performances.

##### Make

Trouvez combien de threads sont supportés par votre CPU. Cela rendra la
compilation plus rapide mais n'aura aucun effet sur la vitesse
d’exécution de RawTherapee. Pour trouver combien de threads sont
supportés par votre CPU, exécutez dans un terminal :

    nproc --all

Il retournera un nombre. Utilisez le pour le paramètre `--jobs`
ci-dessous.

Compile:

    cd ~/programs/code-rawtherapee
    mkdir build
    cd build

    cmake \
        -DCMAKE_BUILD_TYPE="release"  \
        -DCACHE_NAME_SUFFIX="5-dev" \
        -DPROC_TARGET_NUMBER="2" \
        -DBUILD_BUNDLE="ON" \
        -DBUNDLE_BASE_INSTALL_DIR="$HOME/programs/rawtherapee" \
        -DOPTION_OMP="ON" \
        -DWITH_LTO="OFF" \
        -DWITH_PROF="OFF" \
        -DWITH_SYSTEM_LIBRAW="ON"\
        -DWITH_SAN="OFF" \
        -DWITH_SYSTEM_KLT="OFF" \
        ..


    make --jobs=4
    make install

#### Exécuter RawTherapee

Pour lancer RawTherapee :

    ~/programs/rawtherapee/rawtherapee

Ou pour lancer la version en ligne de commande :

    ~/programs/rawtherapee/rawtherapee-cli

Le dépot du code source est dans `~/programs/code-rawtherapee` et le
programme compilé est dans `~/programs/rawtherapee`

Vous pouvez effacer en toute sécurité `~/programs/code-rawtherapee` si
vous le désirez. Le programme compilé continuera de fonctionner, mais
vous aurez à refaire toutes les étapes ci-dessus pour réaliser une mise
à jour. Il vaut mieux laisser le dépôt intact et vous pourrez ainsi
réaliser l'étape suivante dans une semaine ou un mois, lorsque vous
désirerez mettre à jour.

#### Mettre à jour RawTherapee

Chaque fois que vous désirez mettre RawTherapee à jour vers le dernier
code disponible, simplement faire ce qui suit :

    cd ~/programs/code-rawtherapee
    git pull

Puis répéter l'étape [Make](#make) ci-dessus.

Pour la mise à jour, vous pouvez récupérer le dossier `build` de la fois
précédente pour éviter d'avoir à recompiler des choses qui n'ont pas
changé et rendre le processus plus rapide. CMake devrait détecter
automatiquement les changements. Cependant, il y a des situations où la
compilation échoue si l'on ré-utilise le dossier `build`, typiquement
cela se produit si l'on passe d'une branche vers une autre très
différente. Si cela arrive, simplement effacer le dossier `build` puis
procéder selon les étapes de la section "Make".
