---
title: How to fix crashes on startup
contributors:
  - Lebarhon
tags:
  - 'Troubleshooting'
---

<div class="pagetitle">

Comment résoudre les plantages au démarrage

</div>

RawTherapee peut planter immédiatement après démarrage pour plusieurs
raisons, la plus répandue étant qu'il essaie d'ouvrir un fichier qui
ressemble à une image mais qui n'en est pas une, il essaie d'ouvrir une
image corrompue ou non supportée, ou bien il essaie de charger un profil
de traitement (PP3, ils enregistrent tous les réglages apportés à
l'image dans RawTherapee, il y a un PP3 par photo) qui cause problème.
Même une photo normale peut se révéler être un problème si elle est
corrompue ou si elle déclenche un bogue dans RawTherapee, ou que l'un de
ses aspects ne soit pas supporté, comme par exemple un caractère
d'encodage inhabituel dans les métadonnées, plusieurs calques dans une
image, la présence de quatre canaux, etc.

RawTherapee ne supporte que les images ayant soit un canal (échelle de
gris) ou trois canaux de couleur (RVB ou CMJ). Si vous essayez d'ouvrir
un répertoire contenant des images ayant quatre canaux de couleur (par
ex : CMJN) RawTherapee produira une fenêtre indiquant un message
d'erreur. Déplacer ces images à problèmes en dehors du dossier de
démarrage, comme décrit ci-dessous. Bien sûr, il est aussi possible
qu'une image RVB valable ou un profil de traitement fasse planter
RawTherapee, mais vérifier d'abord l'absence d'images avec un nombre de
canaux non supporté. Les étapes ci-dessous vont vous guider.

Pour chasser les bogues toujours utiliser la dernière version de
RawTherapee que vous pouvez trouver, de préférence une version de
développement, car il est probable que le bug soit déjà résolu. Vous
trouverez la dernière version stable et celle de développement sur notre
[site web](http://rawtherapee.com/downloads/) et dans notre
[forum](https://discuss.pixls.us/t/download-rawtherapee-builds-windows-macos-linux-appimage-other/2924),
ou encore dans votre gestionnaire de paquetages si vous utilisez Linux.

Pour trouver la cause du problème nous allons commencer par l'étape la
plus simple, et monter en complexité si elle ne suffit pas.

1.  Premièrement, faites en sorte que RawTherapee utilise un répertoire
    de démarrage vide :
    1.  Créer un nouveau répertoire vide, quelque part sur votre disque,
          
        Windows: `C:\\test`

        Linux: `/home/vous/test`
    2.  Trouver le fichier "options" en suivant les indications de la
        page [Où sont les fichiers](file_paths/fr).
    3.  Ouvrir le fichier "options" dans un éditeur de texte
          
        trouver la ligne `StartupDirectory` et la paramétrer avec
        `StartupDirectory=last`

        trouver la ligne `StartupPath` et la paramétrer pour qu'elle
        pointe vers le répertoire vide que vous venez de créer (cela
        doit être un répertoire **vide**, **existant** et vous devez
        taper le chemin absolu en entier, sans raccourci, avec des
        doubles anti-slashes si vous utilisez Windows) par ex :

        Windows: `StartupPath=C:\\test`

        Linux: `StartupPath=/home/you/test`
    4.  Maintenant, essayez à nouveau de démarrer RawTherapee. Si cela
        fonctionne, alors vous savez que l'une de vos photos ou fichier
        PP3 ou autre fichier dans le répertoire original de démarrage
        (`StartupPath`) est en cause, passez l'étape 2 et allez
        directement à l'étape 3. Cependant, si RawTherapee plante encore
        aussitôt après le démarrage, suivez l'étape suivante.
2.  Effacez le répertoire `batch` :
    1.  Trouver le répertoire "batch" en suivant les indications de la
        page [Où sont les fichiers](file_paths/fr),
        sauvegarder et compresser tous les fichiers qu'il contient, s'il
        y en a, puis l'effacer.
    2.  Essayez à nouveau de démarrer RawTherapee. Si cela fonctionne,
        alors vous savez que l'un des profils de traitement des photos
        envoyées dans la file d'attente est en cause. Inclure la
        sauvegarde réalisée ci-dessus dans votre [rapport de
        bug](How_to_write_useful_bug_reports/fr.md). Si les
        plantages continuent, procéder à l'étape suivante.
3.  Effacez le répertoire `cache` :
    1.  Trouver le répertoire "cache" en suivant les indications de la
        page [Où sont les fichiers](file_paths/fr).
    2.  Effacer le répertoire cache ou le renommer si vous ne désirez
        pas perdre son contenu (il suffit de renommer "cache" en
        "cache2", RawTherapee ne cherche que "cache" et ne trouvera pas
        "cache2"). Notez que par défaut RawTherapee enregistre les
        profils de traitement à coté des images auxquelles ils se
        rapportent, il est donc sûr d'effacer le cache, mais si
        RawTherapee est paramétré pour n'enregistrer les profils de
        traitement que dans le cache et nul part ailleurs, alors effacer
        le cache vous fera perdre tous vos travaux, dans ce cas il vaut
        mieux le renommer plutôt que l'effacer. Ainsi vous ne perdrez
        rien indépendamment du paramétrage des fichiers PP3.
    3.  Essayez à nouveau de démarrer RawTherapee. Si cela fonctionne,
        alors vous savez que l'un des profils de traitement dans le
        cache est en cause. Trouver lequel demande un effort
        considérable. Mais si vous le voulez vraiment et que vous n'avez
        pas effacé le répertoire cache, alors suivez l'étape "Régler le
        problème". Si RawTherapee plante encore au démarrage au même
        endroit qu'avant alors le problème n'est pas du à une photo ni à
        fichier PP3 corrompus, il est ailleurs, en dehors du périmètre
        de ce guide.
4.  Régler le problème
    1.  Les traces d'appel (stack backtraces) aurait toutes les chances
        de nous dire tout ce dont nous avons besoin, y compris le nom du
        fichier fautif et/ou l'endroit où trouver le problème dans le
        code. Voir le [guide des traces
        d'appel](How_to_write_useful_bug_reports/fr#Quand_RawTherapee_se_plante_-_Introduction_aux_traces_d'appel_(stack_backtraces) "wikilink").
        Les instructions peuvent sembler complexes mais elles sont
        simples à suivre et peuvent apporter une aide importante si vous
        parvenez à les utiliser. Nous envoyer les traces d'appel est
        suffisant la plupart du temps. Cependant dans quelques cas
        rares, nous avons besoin que vous trouviez et nous envoyiez le
        fichier spécifique à la source du problème, si c'est le cas,
        continuez de lire.
    2.  Vous avez établi qu'un profil de traitement, une photo ou tout
        autre fichier est la cause du plantage. Les étapes précédentes
        devraient révéler où se trouve ce fichier. Vous pourriez
        simplement ziper le répertoire en entier et nous envoyer
        l'archive zip, cela serait pratique pour vous. Nous envoyer le
        fichier fautif est important afin que nous puissions l'analyser
        et développer les techniques permettant dans le futur de traiter
        ce genre de fichier. Mais si vous nous envoyez une archive avec
        un millier de fichiers alors que le problème vient d'un seul, il
        nous sera très difficile de trouver le coupable, dans ce cas il
        vous sera plus simple de le découvrir. Pour rendre la procédure
        limpide, supposons trois choses :

    - Le répertoire qui contient le fichier qui plante RawTherapee est
      `C:\photos\paris` et le fichier "Options" contient
      `StartupPath=C:\\photos\\paris`
    - Dans le fichier "Options", vous avez changé
      `StartupPath=C:\\photos\\paris` par le répertoire vide et qui
      existe `StartupPath=C:\\test`,
    - Il y a 100 photos dans le répertoire fautif, nommées de `001.raw`
      à `100.raw`

      
    Trouvons le fichier fautif :

    1.  C'est un travail ingrat. ce guide utilise des fichiers raw pour
        l'exemple, mais dans votre cas cela peut aussi bien être les
        profils de traitement, des images téléchargées, des profils ICC
        d'imprimante ou tout autre fichier. Ce que nous allons faire est
        de récursivement considérer la moitié de la liste des fichiers
        possibles jusqu'à trouver le fautif. C'est la méthode la plus
        rapide.
    2.  Si RawTherapee est ouvert, fermez le.
    3.  Déplacer la moitié des fichiers (`001.raw` - `050.raw`) du
        répertoire problématique (`C:\photos\paris`) vers le répertoire
        lu par RawThrapee au démarrage (`C:\test`)
    4.  Démarrer RawTherapee.
    5.  S'il plante, passer à l'étape suivante. Sinon, retourner à
        l'étape 4.3, mais déplacer l'autre moitié (`051.raw` -
        `100.raw`).
    6.  Déplacer la moitié des fichiers qui viennent de l'être
        (`001.raw` - `025.raw` ou `051.raw` - `075.raw`) en dehors de
        `C:\test` et vers un répertoire que RawTherapee ne lit pas
        (`C:\photos\paris`).
    7.  Retourner à l'étape 4.4. Répéter jusqu'à ce qu'il ne reste qu'un
        fichier, le responsable du plantage.
    8.  Ziper le fichier défectueux. même si c'est un fichier PP3 en pur
        texte, vous devez le ziper car les sites web changent souvent
        les fichiers téléversés de façon invisible, et nous ne voulons
        pas qu'un site altère ce fichier défectueux en aucune façon, car
        cela pourrait obscurcir voire supprimer le problème. Les
        fichiers zip sont des conteneurs sûrs. Télécharger le fichier
        zip avec [FileBin](http://filebin.net/) et envoyez nous le lien
        dans votre [rapport de
        bug](How_to_write_useful_bug_reports/fr.md) ou dans le
        [forum](https://discuss.pixls.us/c/software/rawtherapee) (le
        rapport de bug de préférence), accompagné avec les traces
        d'appel et toute autre information requise décrite dans le guide
        "[Comment écrire de bons rapports de
        bug](How_to_write_useful_bug_reports/fr.md)".
