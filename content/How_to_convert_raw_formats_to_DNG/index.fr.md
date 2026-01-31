---
title: How to convert raw formats to DNG
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<div class="pagetitle">

Comment convertir les formats raw en DNG

</div>

__FORCETOC__

<figure>
<img src="/images/Adobe_dng_converter_83.png"
title="Adobe_dng_converter_83.png" />
<figcaption>Adobe_dng_converter_83.png</figcaption>
</figure>

<figure>
<img src="/images/Adobe_dng_converter_raw.png"
title="Adobe_dng_converter_raw.png" />
<figcaption>Adobe_dng_converter_raw.png</figcaption>
</figure>

Les appareil photo numériques peuvent le plus souvent enregistrer vos
photos au format [JPEG](http://fr.wikipedia.org/wiki/JPEG), aussi bien
que de collecter les valeurs raw de chacun des millions de photo-sites
qui composent le capteur, et de les enregistrer, en y ajoutant quelques
[metadonnées](http://fr.wikipedia.org/wiki/M%C3%A9tadonn%C3%A9e), dans
un format raw propriétaire. Certains appareils photo vous permettent
aussi de choisir le format raw
[DNG](http://en.wikipedia.org/wiki/Digital_Negative) (Digital Negative),
qui est un format [ouvert](https://fr.wikipedia.org/wiki/Format_ouvert),
et sans pertes développé par Adobe. A la différence des images JPEG, qui
sont déjà "développées", ces fichiers raw (propriétaires et DNG)
contiennent des données raw (d'où le nom "fichier raw" - ne pas mettre
en majuscules, ce n'est pas un acronyme !) qui doivent d'abord être
traitées avant d'obtenir une image.

Il existe de nombreux avantages à convertir vos fichiers raw dans le
format DNG :

1.  Il bénéficie d'un support universel. Vous serez en mesure d'utiliser
    vos images DNG dans des programmes qui ne supportent pas votre
    format raw non-DNG.
2.  Ce n'est pas un format mort, il est constamment maintenu.
3.  Le DNG Converter d'Adobe intègre des matrices de couleur et des
    niveaux de blancs dans les fichiers DNG convertis, ceux ci ne sont
    généralement pas présents dans les fichiers non DNG, et ceux d'Adobe
    sont souvent plus précis que ceux de dcraw. Ceci amène des couleurs
    plus précises et diminue le risque de dominante de couleur dans les
    zone en dépassement de domaine.
4.  Les fichiers DNG sont souvent plus petits que le fichier raw
    original en raison d'une meilleure compression sans pertes. Le
    logiciel de l'appareil photo est limité par le matériel, il doit
    écrire le fichier raw le plus vite possible et ne pas consommer trop
    de courant, la compression est donc optimisée pour la vitesse, pas
    pour la taille du fichier. Le logiciel sur l'ordinateur, ne connaît
    pas cette limitation.
5.  Même si votre appareil photo supporte la prise de vue directement au
    format DNG, la version du DNG implantée dans votre appareil est très
    certainement
    [obsolète](https://en.wikipedia.org/wiki/Digital_Negative#Versions_of_the_specification).
    Dans certains cas, il peut être justifié de re-convertir vos vieux
    DNG dans un format DNG plus récent, utilisant la dernière version du
    DNG Converter d'Adobe. Les raisons possibles peuvent être une
    nouvelle matrice de couleurs plus précise, la compression sans
    pertes améliorée, amélioré aussi le repérage des pixels défectueux,
    l'intégration de nouveaux opcodes, l'adjonction de nouvelles balises
    utiles de métadonnées, etc.

Si vous procédez à la conversion de vos fichiers raw en DNG, vous
devriez toujours commencer par tester vos fichiers DNG afin de s'assurer
que tout va bien dans vos habitudes et procédés de travail avant
d'effacer les fichiers sources. Cela étant dit, les problèmes sont très
rares avec DNG, contrairement à ce qu'affirme le
[FUD](http://fr.wikipedia.org/wiki/Fear,_uncertainty_and_doubt) fait
autour de lui, il est loin d'être mourant.

Le DNG Converter d'Adobe n'est pas le seul programme qui convertit les
fichiers raw en DNG. Il y a par exemple les plugins kipi DNG Image
Converter qui utilise [LibRaw](http://www.libraw.org/) et libkdcraw,
cependant les matrices utilisées par ce convertisseur ne sont pas bien
connues, pas plus que leur origine, il est donc plus sûr d'utiliser le
DNG Converter officiel d'Adobe.

Obtenez ici la dernière version du DNG Converter d'Adobe :

1.  [Adobe DNG Converter pour
    Windows](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows)
    (prenez ceci si vous utilisez Linux - l'installation est expliquée
    ci-dessous).
2.  [Adobe DNG Converter pour
    macOS](http://supportdownloads.adobe.com/product.jsp?product=106&platform=mac).

Lancez le et c'est terminé.

## Capteurs non supportés

<figure>
<img src="/images/Adobe_dng_converter_830.png"
title="Adobe_dng_converter_830.png" />
<figcaption>Adobe_dng_converter_830.png</figcaption>
</figure>

Le format DNG peut contenir de pures données raw, mais il peut aussi
contenir des images dématricées. Celles-ci ne sont plus vraiment des
raw, elles ont été pré-arangées. Bien que cela soit généralement non
désirable, il existe des situations dans lesquelles on peut en tirer
profit. Certains appareils photo utilisent des capteurs avec une
disposition du [filtre de
couleur](https://en.wikipedia.org/wiki/Color_filter_array) et des pixels
dans le capteur non supportés par RawTherapee. Bien que vous ne puissiez
pas directement traiter ces fichiers raw dans RawTherapee, vous pouvez
les convertir vers un fichier DNG dématricé en utilisant DNG Converter
d'Adobe. Comme ces fichiers DNG dématricés ne sont plus vraiment des
raw, n’effacez donc pas vos fichiers raw originaux ! Cette procédure
n'est qu'un artifice.

Pour convertir en fichiers DNG dématricés les fichiers raw non
actuellement supportés par RawTherapeeaw, utilisez les paramètres
suivants :

- Choisir "Custom" dans "compatibility" puis entrer "DNG 1.4"
- Cocher la case "Linear (demosaiced)".

Les fichiers DNG résultants peuvent au final être plus lourds que les
fichiers entrants, par exemple un fichier entrant RAF a donné un fichier
DNG plus gros de 142%.

Ces fichiers DNG dématricés peuvent maintenant être utilisés dans
RawTherapee (ou tout autre programme supportant le DNG), bien qu'étant
déjà dématricés les outils de l'onglet "Raw" seront désactivés.

  

## Installation d'Adobe DNG Converter dans Linux

Nous utiliserons `$HOME/wine-dng` comme préfixe pour Wine.
