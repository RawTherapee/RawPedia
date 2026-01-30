---
title: Command-Line Options
contributors:
  - Lebarhon
  - Hombre
tags:
  - 'General Information'
---

<div class="pagetitle">

Options en ligne de commande

</div>

## Explication

  
`<`Chevrons`>` indiquent des paramètres que vous pouvez changer.

`[`Crochets`]` signifie que le paramètre est facultatif.

Le symbole du tube `|` indique un choix de l'un ou l'autre.

Le tiret `-` indique une gamme de valeurs possibles depuis l'une jusqu'à
l'autre.

Depuis RawTherapee 5.1, deux exécutables sont fournis

### RawTherapee GUI

Choisir cette application pour démarrer la version avec une interface
graphique.

Utilisation :

  
`rawtherapee [`<répertoire sélectionné>`]`

  
Lance le [Navigateur de fichiers](the_file_browser_tab/fr) à
l'intérieur du répertoire.

`rawtherapee `<fichier>

  
Lance l'[Editeur](the_image_editor_tab/fr) avec le fichier
chargé.

`-w`

  
Ne pas ouvrir la console Windows. Cette option n'est possible que dans
Windows. Si vous passez des paramètres à l'exécutable RawTherapee, il
affiche une console afin que vous puissiez voir les commentaires de
sortie du traitement. Normalement Windows ferme cette console aussitôt
après que RawTherapee ait terminé. Pour vous permettre de voir ces
commentaires nous avons ajouté une invite qui attend que vous ayez
appuyé sur une touche avant de fermer la console. En spécifiant `-w`
aucune console ne sera ouverte et donc, aucun appui sur une touche n'est
nécessaire. C'est utile si vous désirez appeler `rawtherapee.exe` dans
une séquence, par exemple dans un script PowerShell. Notez que `-w`
n'aura aucun effet pour les versions "Debug" où une console sera ouverte
à moins que vous ne démarriez RawTherapee déjà depuis une console.

<!-- -->

  
`-v`

  
affiche le numéro de version de RawTherapee et quitte.

<!-- -->

  
`-R`

  
mode "Remote", disponible depuis RawTherapee 5.2. Lors de l'ouverture
d'une image en utilisant "Ouvrir avec" ou bien en donnant son nom comme
argument, sans l'option `-R`, RawTherapee l'ouvre en mode
"sans-Navigateur-de-Fichiers", c'est un mode dépourvu du Navigateur de
Fichiers, de l'onglet File d'attente et du bouton Préférences. Avec le
nouveau mode `-R`, RawTherapee s'ouvre au grand complet. Le mode mode
`-R` permet aussi d'ouvrir une image dans une session de RawTherapee
déjà en cours, si cette session a aussi été démarrée dans le mode `-R`.
le mode "sans-Navigateur-de-Fichiers" existes pour des raisons
historiques, quand la consommation de RAM était plus importante et la
stabilité moins bonne. Maintenant que le besoin en RAM de RawTherapee
est optimisé et qu'il peut ouvrir des répertoires contenant des milliers
d'images, on peut préférer utiliser le mode `-R` par défaut.

<!-- -->

  
`-h -?`

  
Affiche ces commandes

### RawTherapee CLI

Choisir cette application pour démarrer la version en ligne de commande.
Vous trouverez toutes les options en ligne de commande pour développer
vos photos sans aucune interface graphique.

Utilisation :

  
`rawtherapee-cli `<options>` -c `<répertoire>`|`<fichiers>

  
Traite les fichiers par lots avec les paramètres par défaut si aucune
<options> n'est spécifiée.

<!-- -->

  
`-w`

  
Ne pas ouvrir la console Windows. Cette option n'est possible que dans
Windows. Si vous passez des paramètres à l'exécutable RawTherapee, il
affiche une console afin que vous puissiez voir les commentaires de
sortie du traitement. Normalement Windows ferme cette console aussitôt
après que RawTherapee ait terminé. Pour vous permettre de voir ces
commentaires nous avons ajouté une invite qui attend que vous ayez
appuyé sur une touche avant de fermer la console. En spécifiant `-w`
aucune console ne sera ouverte et donc, aucun appui sur une touche n'est
nécessaire. C'est utile si vous désirez appeler `rawtherapee-cli.exe`
dans une séquence, par exemple dans un script PowerShell.

Autres options utilisées avec `-c` :

  
`rawtherapee-cli [-o `<sortie>`|-O `<sortie>`] [-q] [-a] [-s|-S] [-p `<fichiers>`] [-d] [-j[1-100] [-js<1-3>]|[-b<8|16>] <[-t[z] | [-n]]] [-Y] [-f] -c `<entrée>

<!-- -->

  
`-c `<fichiers>

  
Spécifie un ou plusieurs fichiers ou répertoires d'entrée.

Lors de la spécification de répertoires, RawTherapee cherchera des
fichiers images qui respectent les extensions considérées sélectionnées
(voir l'option `-a`).

L'option `-c` doit toujours être la dernière.

<!-- -->

  
`-o `<fichier>`|`<rép>

  
Sélectionne le fichier ou le répertoire de sortie.

Enregistre le fichier de sortie à côté du fichier d'entrée si -o n'est
pas spécifié

<!-- -->

  
`-O `<fichier>`|`<rép>

  
Sélectionne le fichier ou le répertoire de sortie et copie le fichier
pp3 à l'intérieur.

Enregistre le fichier de sortie à côté du fichier d'entrée si -O n'est
pas spécifié

<!-- -->

  
`-q`<fichier>`|`<rép>

  
Mode démarrage rapide. Ne charge pas les fichiers cachés pour accélérer
le démarrage

<!-- -->

  
`-a`<fichier>`|`<rép>

  
Traite tous les types de fichiers images supportés dans le répertoire
spécifié, même ceux qui ne sont pas actuellement sélectionnés dans
Préférences \> Navigateur de fichiers \> Extensions considérées

<!-- -->

  
`-s`

  
Utilise le fichier accolé existant pour construire les paramètres de
traitement, par ex pour photo.raw, il devrait y avoir un fichier
photo.raw.pp3 dans le même répertoire. Si le fichier accolé n'existe
pas, les valeurs par défaut (neutral) seront utilisées.

<!-- -->

  
`-S`

  
Comme `-s` mais abandonne si le fichier accolé n'est pas trouvé.

<!-- -->

  
`-p <fichier.pp3>`

  
Spécifie le profil de traitement devant être utilisé pour toutes les
conversions. Il est possible de spécifier autant de jeux d'options `-p`
que désirés, chacun sera construit au-dessus du précédent, comme
expliqué ci-dessous.

<!-- -->

  
`-d`

  
Utilise le fichier pp3 raw ou non-raw comme défini dans
"[Préférences](main_page/fr#préférences) \> [Traitement de
l'image](Preferences/fr#L'onglet_Traitement_de_l'image.md) \>
[Paramètres de traitement d'image par
défaut](Preferences/fr#Paramètres_de_traitement_d'image_par_défaut.md)"

<!-- -->

  
`-j[1-100]`

  
Impose le format JPEG pour l'image de sortie (par défaut, si -t et -n ne
sont pas définis)

Optionnellement, spécifie la compression, de 1 à 100 (92 par défaut)

<!-- -->

  
`-js<1-3>`

  
Spécifie le paramètre JPEG de [sous-échantillonnage de la
chroma](http://fr.wikipedia.org/wiki/Sous-%C3%A9chantillonnage_de_la_chrominance),
avec:

  
1 = Meilleure compression : 2x2, 1x1, 1x1 (4:2:0)

  
Chroma divisée par deux verticalement et horizontalement.

2 = Equilibré : 2x1, 1x1, 1x1 (4:2:2)

  
Chroma divisée par deux horizontalement.

3 = Meilleure qualité: 1x1, 1x1, 1x1 (4:4:4)

  
Pas de sous échantillonnage de la chroma

<!-- -->

  
`-b<8|16>`

  
Spécifie la profondeur en nombre de bits par canal (16 par défaut)

ne s'applique qu'aux sorties TIFF et PNG, c'est toujours 8 pour JPEG.

<!-- -->

  
`-t[z]`

  
Impose une sortie au format TIFF (16 bit si `-b8` n'est pas spécifié).

Non compressé par défaut, ou compression ZIP avec 'z'.

<!-- -->

  
`-n`

  
Impose une sortie au format PNG compressé (16 bit si `-b8` n'est pas
spécifié).

La compression est codée en dur au niveau 6.

<!-- -->

  
`-Y`

  
Écrase le fichier de sortie s'il existe.

<!-- -->

  
`-f`

  
Utilise le pipeline personnalisé du traitement d'export rapide

Les fichiers PP3 peuvent être incomplets, RawTherapee fixera les valeurs
comme suit :

1.  Un nouveau profil de traitement est créé en utilisant les valeurs
    internes par défaut (neutral).
2.  Si l'option `-d` est indiquée, les valeurs sont supplantées par
    celles trouvées dans le profil de traitement raw ou non-raw par
    défaut.
3.  Si une ou plusieurs options `-p` est (sont) indiquée(s), les valeurs
    sont à nouveau supplantées par celles trouvées dans ces fichiers de
    traitement.
4.  Si les options `-s` ou `-S` sont indiquées, les valeurs sont enfin
    supplantées par celles trouvées dans les fichiers accolés.

Les profils de traitement sont exécutés dans l'ordre indiqué sur la
ligne de commande

## Redirection de la sortie

Pour rediriger la sortie de RawTherapee vers un fichier texte, vous
devez le démarrer depuis une console et ajouter le code de redirection
comme suit :

Windows (cmd.exe)  
`rawtherapee.exe > rtlog.txt 2>&1`

Linux  
`rawtherapee &> rtlog.txt`

## Exemples

### Exemple 1

Sous Linux, développer un unique fichier raw qui est placé dans /tmp et
est nommé “photo.raw”, utiliser son fichier accolé (photo.raw.pp3) pour
la conversion, l'enregistrer dans le même répertoire sous le nom
“foo.tif”, et écraser l'ancien fichier foo.tif s'il existe:

`rawtherapee-cli -o /tmp/foo.tif -s -t -Y -c /tmp/photo.raw`

### Exemple 2

Dans l'exemple suivant, nous supposons que vous voulez rapidement
traiter toutes les photos du dossier /tmp/jane01 vers un sous-dossier
web en utilisant à la base le profil par défaut, mais aussi le profil
accolé s'il existe, et en retirant certaines données Exif (par ex le N°
de série de l'appareil photo) et en ajoutant des données IPTC (par ex
vos paramètres habituels de copyright), plus redimensionner et rendre
l'image plus nette pour le web (présenté sur plusieurs lignes pour plus
de clarté)

<code>`rawtherapee-cli -o /tmp/Jane01/web `  
`-p ~/profiles/iptc.pp3 `  
`-s `  
`-p ~/profiles/exif.pp3`  
`-p ~/profiles/web.pp3 `  
`-t `  
`-Y `  
`-d `  
`-c /tmp/Jane01/`</code>

Le profil de traitement sera construit comme suit :

1.  Un nouveau profil est créé, utilisant les valeurs par défaut
    internes, codé en dur dans RawTherapee,
2.  puis elles sont supplantées par celles trouvées dans le profil raw,
    (`-d`),
3.  puis elles sont supplantées par celles trouvées dans le fichier
    iptc.pp3,
4.  puis elles sont supplantées par celles trouvées dans le fichier
    accolé (`-s`) s'il existe, ainsi vous pouvez imposer des données
    IPTC même si déjà données par le fichier iptc.pp3,
5.  puis elles sont supplantées par celles trouvées dans le fichier
    exif.pp3, ainsi vous pouvez imposer au profil d'effacer certaines
    données,
6.  puis elles sont supplantées par celles trouvées dans le fichier
    web.pp3, pour redimensionner et rendre l'image plus nette, et
    s'assurer que l'espace colorimétrique de sortie est sRGB.

Comme vous pouvez le voir, la position du commutateur `-s` indique quand
charger le profil accolé en fonction des autres paramètres `-p`. Ce
n'est pas le cas avec le commutateur `-d`.

### Example 3

Dans le troisième exemple, nous allons voir combien de temps cela
prendrait-il pour développer tous les fichiers raw placés dans un
répertoire, en supposant que chaque photo raw possède un profil
correspondant de traitement et supprimer chaque fichier de sortie :

`time { for f in /home/user/photos/2011-11-11/*.raw; do rawtherapee-cli -o /dev/null -S -t -Y -c "$f"; done }`
