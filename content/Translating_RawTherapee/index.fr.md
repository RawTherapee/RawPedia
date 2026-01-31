---
title: Translating RawTherapee
contributors:
  - Lebarhon
tags:
  - 'Localization'
---

<div class="pagetitle">

Traduire RawTherapee

</div>

Cet article explique comment vous pouvez aider à traduire l'interface de
RawTherapee.

## Introduction

L'interface graphique utilisateur de RawTherapee contient du texte en de
nombreux endroits. Dans le but d'autoriser l'affichage de ce texte en
langues variées, le code ne contient que des clés et chaque fois qu'un
texte doit être affiché, le code recherche le texte correspondant à
cette clé dans un fichier texte de traduction [paire
clé-valeur](https://en.wikipedia.org/wiki/Attribute–value_pair)
correspondant à la langue sélectionnée par l'utilisateur (ou
auto-détectée par RawTherapee d'après le paramétrage). Lorsqu'une clé
est trouvée dans le fichier de traduction, elle est remplacée par la
valeur correspondante. Si elle n'est pas trouvée, la valeur
correspondant à l'anglais est utilisée en saufconduit.

Le fichier qui contient les paires clé-valeur de référence est appelé
[`default`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/default).
Il utilise l'anglais américain. Toutes les traductions sont basées sur
ce fichier. Chaque fois qu'une clé n'est pas trouvée dans une
traduction, c'est la clé de ce fichier qui est utilisée.

Les fichiers de traduction sont placés dans
[`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/).

De temps à autres nous exécutons le script
`/tools/generateTranslationDiffs` qui met à jour chaque fichier de
traduction avec les nouvelles clés du fichier `default`. Si une nouvelle
paire clé-valeur est ajoutée à `default`, le script copie cette paire
dans le fichier de traduction si elle n'existe pas, et puisque la valeur
a ce niveau est en anglais, il préfixe cette ligne avec un point
d’exclamation. Lorsque RawTherapee recherche une chaîne de caractères
traduite, il ignore les lignes préfixées avec un point d'interrogation.
Lorsque quelqu'un traduit cette valeur, il doit enlever ce point
d'interrogation afin qu'elle ne soit plus ignorée.

Un inconvénient du système est que si la valeur d'une clé dans le
fichier `default` est modifiée et cette entrée à déjà été traduite,
alors la traduction devient obsolète et cette situation n'est pas
repérée. Pour cette raison, les personnes assurant la maintenance d'une
traduction doit garder un œil sur les modifications apportées aux
valeurs existantes dans `default` et mettre à jour leurs traductions.
Une façon de garder un oeil sur ces modifications est de vérifier [les
commits dans git qui affectent ce
fichier](https://github.com/Beep6581/RawTherapee/commits/dev/rtdata/languages/default).

Utilisons en exemple l'étiquette "Compensation d'exposition" :

- La clé utilisée par le code est `TP_EXPOSURE_EXPCOMP`.
- Le fichier `default` contient la paire clé-valeur :
    
  `TP_EXPOSURE_EXPCOMP;Exposure compensation`
- Le fichier `English (US)` contient la même paire, mais préfixée par un
  point d'exclamation :
    
  `!TP_EXPOSURE_EXPCOMP;Exposure compensation`
- Les traductions devraient contenir la clé avec la valeur traduite et
  le point d'exclamation enlevé, par ex :
    
  `TP_EXPOSURE_EXPCOMP;Compensation d'exposition`

## Mode opératoire

1.  Vérifier s'il existe un fichier de traduction pour la langue dans
    laquelle vous souhaitez traduire en regardant dans
    [`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/tree/dev/rtdata/languages)
    - S'il n'en existe pas, télécharger le fichier
      [`English (US)`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/English%20(US))
      (cliquer droit sur le bouton "Raw" puis sur "Enregistrer la cible
      du lien sous..."), puis le renommer dans votre langue, appelons le
      `Inuktitut` pour la suite de l'article.
    - S'il en existe un, le télécharger (cliquer droit sur le bouton
      "Raw" puis sur "Enregistrer la cible du lien sous...").
2.  Traduire de nouvelles chaînes
      
    Ouvrir `Inuktitut` dans un éditeur de texte moderne (utilisateurs de
    Windows : ne pas utiliser "Notepad", prenez plutôt
    [Notepad++](https://notepad-plus-plus.org/)). Toutes les chaînes à
    traduire sont celles qui sont sur une ligne commençant par un point
    d'exclamation, vous les trouverez à la fin du fichier si vous mettez
    une traduction existante à jour. Les traduire, et pour chaque chaîne
    traduite retirer le point d'exclamation en préfixe.

    Par exemple, vous devez traduire

    `!TP_EXPOSURE_EXPCOMP;Exposure compensation`

    en

    `TP_EXPOSURE_EXPCOMP;Lorem ipsum`
3.  Mise à jour des chaînes existantes
      
    Si votre fichier `Inuktitut` a déjà été traduit il y a longtemps, il
    est probable que certaines parties traduites soient obsolètes. Pour
    les mettre à jour, ouvrir le dernier fichier
    [`default`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/default)
    dans une fenêtre couvrant une moitié de l'écran, ouvrir `Inuktitut`
    dans une fenêtre couvrant l'autre moitié de l'écran, puis comparer
    chaque chaîne déjà traduite dans `Inuktitut` avec la chaîne en
    anglais dans `default`, et rafraîchir la traduction si elle ne
    convient plus à la chaîne anglaise.
4.  Une fois la traduction terminée, ouvrir une [nouvelle publication
    dans GitHub](https://github.com/Beep6581/RawTherapee/issues/new) et
    y lier votre traduction. Veuillez ne pas créer de fichier patch des
    traductions, simplement envoyer la totalité du fichier traduit. Nous
    l'exécuterons alors via le script `/tools/generateTranslationDiffs`
    qui triera les entrées, ajoutera les nouvelles clés et effacera
    celles qui ne sont plus utiles. Nous la commiterons enfin dans la
    base.
5.  Quand vous désirerez mettre à jour votre traduction dans le futur,
    vous devrez télécharger la dernière version de ce fichier depuis le
    dépôt via
    [`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/tree/dev/rtdata/languages)

## Balisage

Certaines lignes ont des éléments qui doivent apparaître en gras ou en
italiques, ou ont des caractères qui doivent être écrits de façon
particulière. Ceci est assuré grâce au
[balisage](https://en.wikipedia.org/wiki/Markup_language). Cependant le
balisage analytique est plus lent que le balisage en plein texte, aussi
RawTherapee ne supporte le balisage que sur les clés dont on sait
qu'elles l'exige. Cela signifie que si vous utilisez le balisage sur des
clés qui ne le supportent pas, alors ces clés ne seront pas affichées
correctement. Toujours respecter le style utilisé dans `default`. Si une
clé dans `default` n'utilise pas le balisage, alors votre traduction ne
la supportera jamais.

Lorsque qu'une clé utilise le balisage, certains caractères doivent
s'écrire en utilisant leur nom de [référence de caractère
HTML](https://fr.wikipedia.org/wiki/Liste_des_entit%C3%A9s_caract%C3%A8re_de_XML_et_HTML)
:

- Ecrire `<` avec `<;`
- Ecrire `>` avec `>;`
- Ecrire `&` avec `&;`

Comment savoir que le balisage est nécessaire ? Regardez `default`. Par
exemple :

- `HISTORY_MSG_251;B&;W - Algorithm` utilise une balise pour afficher le
  caractère `&`, et votre traduction doit le faire aussi.
- `PARTIALPASTE_RAWCACORR_CAREDBLUE;CA red & blue` n'utilise pas de
  balise pour afficher le caractère `&`, et votre traduction ne doit pas
  non plus.
- `FILEBROWSER_EMPTYTRASHHINT;`<b>`Permanently`</b>` delete all files in trash.`
  utilise une balise pour mettre le mot "Permanently" en gras lorsqu'il
  est affiché par RawTherapee, et votre traduction doit le faire aussi.
