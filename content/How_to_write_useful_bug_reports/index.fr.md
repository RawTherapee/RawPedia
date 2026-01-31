---
title: How to write useful bug reports
contributors:
  - Lebarhon
tags:
  - 'Troubleshooting'
---

<div class="pagetitle">

Comment écrire de bons rapports de bogues

</div>

Les bogues sont à rapporter dans notre [RawTherapee GitHub système de
suivi des bogues](https://github.com/Beep6581/RawTherapee), pas dans le
forum ni dans l'IRC. Nous utilisons l'expression "rapport de bogue" dans
son sens le plus large, tout problème que vous rencontrez doit indiquer
les informations détaillées ci-dessous.

## Exigences pour un bon rapport de bogue

Vous devez fournir les informations suivantes :

- **La version détaillée** de compilation de RawTherapee utilisée. Vous
  trouverez cette information en cliquant sur
  [image:preferences.png](image:preferences.png) Préférences
  \> A propos \> Version et le plus souvent cet onglet est plein de
  renseignements, vous pouvez les copier/coller tous dans votre rapport
  de bogue. Si cet onglet est vide, vous trouverez le numéro de version
  de RawTherapee dans la barre de titre de la fenêtre principale.
- **Le nom et la version de votre système d'exploitation**.
  - Les utilisateurs de Windows peuvent trouver ces informations par la
    raccourci clavier +.
  - Les utilisateurs de Linux peuvent trouver ces informations en tapant
    `uname -a` dans un terminal.
- Expliquer exactement les **étapes pour reproduire** le problème.
  Appliquer le profil de traitement "Neutre" à votre photo puis
  expliquer ce qui doit être fait pour déclencher le problème.
- **Téléverser les fichiers raw + PP3**. Rendre vos fichiers raw et PP3
  accessibles pour nous en les téléversant dans un site de partage de
  fichiers comme [www.filebin.net](http://filebin.net/) si votre bogue
  implique un plantage sur un fichier raw particulier, des paramètres
  particuliers ou une insuffisance de prise en charge de votre fichier
  raw.
- **Présenter une copie d'écran du problème**. Ne pas recadrer la copie
  d'écran, montrer la fenêtre complète de RawTherapee.
- Ouvrir **un problème par bug**, ou un problème par requête de
  fonctionnalité. Ne rapportez pas plusieurs bugs dans le même problème,
  ne faites pas de requête de plusieurs fonctionnalités dans le même
  problème.

De plus, il est souvent bénéfique de faire ce qui suit :

- Présenter un **enregistrement vidéo** sur la façon dont vous
  déclenchez le problème. Un enregistrement vidéo est la meilleure façon
  pour expliquer un problème si les copies d'écran et les **étapes à
  reproduire** sont insuffisants. Vous pouvez en réaliser facilement en
  utilisant du logiciel libre :
  - Windows: [ShareX](https://getsharex.com/)
  - Linux:
    [SimpleScreenRecorder](http://www.maartenbaert.be/simplescreenrecorder/)
- **Veillez à ne pas faire de doublons**. Rechercher dans le forum et
  dans notre système de suivi des bogues avant de renseigner un nouveau
  bogue car il est probable que quelqu'un ait déjà rapporté le même
  problème avant vous, et les duplications font perdre du temps.
- Assurez vous **d'utiliser la dernière version de RawTherapee** car il
  est probable qu'un bogue dans une version antérieure soit résolu dans
  la dernière.
- Si votre problème implique un crash, fournir une **trace d'appel** si
  vous le pouvez. Comment l'obtenir est expliqué ci-dessous. Si vous n'y
  parvenez pas, alors assurez vous de fournir au moins les informations
  ci-dessous, sinon, votre rapport de bug est inutile.

Pour davantage d'informations sur comment rapporter un bogue, lire ceci
: <http://www.chiark.greenend.org.uk/~sgtatham/bugs.html>

## Quand RawTherapee se plante - Introduction aux traces d'appel (stack backtraces)

Une trace d'appel (stack backtrace) est un journal des différentes
étapes par lesquelles est passé un programme à un moment donné. Pour nos
besoins, ce moment sera celui du plantage de RawTherapee, et nous
l'utiliserons pour déboguer RawTherapee, pour résoudre le plantage. Nous
éditons des compilations de RawTherapee qui nous paraissent stables. Si
elles plantent chez vous, vous devez alors nous fournir les informations
nécessaires pour nous permettre de reproduire le problème nous-mêmes, ou
de corriger le bug sans avoir à reproduire le problème. La trace d'appel
est très utile.

Les programmes doivent être compilés pour fonctionner, et d'une façon
générale la compilation peut se faire de deux façons :

- La façon "release", qui optimise le programme pour la vitesse mais
  n'offre aucune information utile en cas de plantage,
- La façon "debug", qui fournit beaucoup d'informations utiles en cas de
  plantage mais s'exécute beaucoup plus lentement.

Bien qu'il soit possible d'obtenir quelques informations d'une
compilation *release*, elle est beaucoup plus précise à partir d'une
*debug*. Vous trouverez les deux compilations de RawTherapee "release"
et "debug" sur la [page officielle des
téléchargements](http://rawtherapee.com/downloads) ainsi que sur [le
forum](https://discuss.pixls.us/c/software/rawtherapee). Pour un usage
quotidien, préférer une compilation de type "release" car elle est plus
rapide. Si vous subissez un plantage, prendre une "debug" pour nous
fournir les informations requises à la résolution du problème.

Disponibilité des compilations debug :

- Les installeurs Windows de RawTherapee doivent contenir
  `rawtherapee.exe` pour "release" et `rawtherapee-debug.exe` pour
  "debug".
- Les paquets Linux sont habituellement "release", à moins que le
  paquetage ne contienne le mot "debug" dans le titre, bien que cela
  dépende de votre distribution, du gestionnaire de paquetage et de la
  source des paqquetages. La meilleure façon d'obtenir une compilation
  debug est de la réaliser vous-même; voir le guide de compilation
  [Linux](linux/fr), c'est facile !
- Les paquets macOS ne contiennent actuellement que les exécutables
  "release". Nous avons espoir d'inclure les exécutables "debug" à
  l'avenir.

### Comment obtenir une version debug ?

Consulter [notre page web](http://rawtherapee.com/downloads) ou votre
gestionnaire de paquetages pour trouver une compilation *debug* de la
dernière version de RawTherapee. S'il n'y en a pas, alors, soit nous en
demander une, ou en réaliser une vous même. Si vous utilisez Linux, cela
est très facile, simplement suivre le guide [Compilation dans
Linux](Linux/fr.md).

Un logiciel peut (et le fait souvent) se comporter différemment suivant
qu'il comporte un débogueur ou non, du au fait que la présence du
débogueur provoque d’inévitables modifications dans le timing interne du
programme. Cela signifie que vous pouvez rencontrer des bogues
(plantages) lors de l'utilisation au jour le jour qui ne se produisent
plus quand RawTherapee est exécuté avec GDB (GDB est le débogueur) !
C'est un fait malheureux, mais rare heureusement, donc, allez y,
continuez, utilisez une compilation "debug" et essayez de reproduire le
plantage, avec cette fois une collecte fructueuse de traces d'appel.

**TOUJOURS** télécharger et tester la dernière version de RawTherapee
avant de rapporter un bogue ! Les rapports de bogues concernant une
ancienne version sont une perte de temps.

## Etape par étape

1.  Se procurer GDB. Comment faire cela dépend de votre système
    d'exploitation/distribution.
    - **Linux** - Utilisez votre gestionnaire de paquetage.
        
      Avec Ubuntu ouvrez un terminal et écrivez :

          sudo apt-get install gdb

      Avec Gentoo écrivez:

          sudo emerge gdb
    - **Windows** - Nos compilations debug pour Windows comprennent
      habituellement `gdb.exe`, vous n'avez donc rien à faire pour
      l'obtenir. Dans le cas contraire, installer
      [TDM-GCC](http://tdm-gcc.tdragon.net/) en vous assurant
      d'installer aussi le paquetage GDB. Copier `gdb.exe` dans votre
      répertoire RawTherapee, afin qu'il soit placé à coté de
      `rawtherapee.exe`
    - **Mac OS X** - si vous savez comment installer GDB sous OS X,
      veuillez écrire cette partie.
2.  Exécuter RawTherapee depuis GDB.
    - Avec **Linux**, supposant que vous utilisez une [compilation
      maison de
      RawTherapee](Linux/fr#Compilation_:_la_méthode_manuelle.md),
      ouvrir un terminal et, en supposant que votre compilation debug a
      été compilée dans `~/rt_debug/` alors taper :
          gdb ~/rt_debug/rawtherapee
    - Avec **Windows**, ouvrir la ligne de commande, naviger jusqu'au
      répertoire RawTherapee et en supposant que le nom de fichier de
      l'exécutable debug est `rawtherapee-DEBUG.exe` alors taper :
          gdb rawtherapee-DEBUG.exe
3.  GDB démarre et est prêt à exécuter RawTherapee. Pour le lancer,
    taper :
      
        r
4.  RawTherapee tourne, et vous pouvez remarquer une abondante
    information dans GDB. Majoritairement, elle ressemble à cela:
      
    `[New Thread 0x7fffa7b2e700 (LWP 11532)]`

    `[New Thread 0x7fffa9b32700 (LWP 11533)]`

    `[Thread 0x7fffaab34700 (LWP 11528) exited]`

    `[Thread 0x7fff97dfd700 (LWP 11507) exited]`

    Refaite ce qui a déclenché le plantage, et lorsqu'il survient, la
    fenêtre de RawTherapee va seulement se figer, elle ne se fermera
    pas. Vous pouvez vous dire qu'il a planté du fait que tout dans la
    fenêtre a arrêté de répondre. Alt+Tab ramène dans le terminal GDB.
5.  Nous voulons une trace d'appel détaillée et pour vous faciliter, au
    cours des trois prochaines étapes, son envoi vers nous, vous allez
    dire à GDB de l'enregistrer dans un fichier texte appelé `log.txt`
    (ou autre, le nom n'a pas d'importance). Taper :
      
        set pagination off

        set logging file log.txt

        set logging on
6.  Maintenant pour que GDB montre l'information sur tous les threads et
    imprime la trace d'appel en question, taper :
      
        info threads

        thread apply all bt full

    Vous devriez voir un écran plein de texte, de nombres, de code et de
    caractères magiques. Tout cela a été automatiquement enregistré dans
    le fichier `log.txt`.
7.  Vous pouvez maintenant quitter GDB. Pour cela, taper :
      
        q

    et confirmer par un

        y
8.  Maintenant il est temps de nous envoyer le rapport de bug. Ouvrir un
    nouveau bug dans notre [Suiveur de bugs
    GitHub](https://github.com/Beep6581/RawTherapee/issues/new),
    expliquer les étapes qui ont conduit au bug, **lier le fichier
    `log.txt`** et fournir toutes les informations demandées ci-dessus.

Du texte bien formaté est plus facile à lire. Si vous collez le code
dans GitHub, utilisez les coches inversés ou indenter le code - lire [le
guide](https://guides.github.com/features/mastering-markdown/). Si vous
voulez coller du code dans le
[forum](https://discuss.pixls.us/c/software/rawtherapee), vous pouvez
aussi utiliser les coches inversés ou indenter le code - lire [Le guide
pour le formatage du code du Forum](Forum/fr.md).

Souvenez vous d'inclure le contenu de
"*[image:preferences.png](image:preferences.png) Préférences
\> A propos \> Version*", un échantillon de fichier raw et PP3, avec une
information complète de la version de votre système d'exploitation, le
type de votre CPU et sa vitesse, de combien de RAM vous disposez, etc.
