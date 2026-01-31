---
title: Forum
contributors:
  - Lebarhon
tags:
  - 'Interact'
---

<div class="pagetitle">

Forum

</div>

Visitez notre Forum à <https://discuss.pixls.us/c/software/rawtherapee>

## Création de captures d'écran

La création de copies d'écran peut se faire soit en utilisant la touche
**impr écran** du clavier puis en collant l'image dans n'importe quel
éditeur d'image et en l’enregistrant au format PNG, ou mieux, installer
un véritable éditeur d'image comme [1](http://www.gimp.org/GIMP), Libre
et Open Source. (liens pour Windows et Mac en bas de la page). Pour
prendre une copie d'écran avec Gimp, cliquer sur "Fichier \> créer \>
Copie d'écran".

Wikipedia propose un bon [comparatif d'éditeurs
graphiques](http://en.wikipedia.org/wiki/Comparison_of_raster_graphics_editors).

Suggestions d'applications pour faire des copies d'écran :

- [Shutter (Linux)](http://shutter-project.org/)
- [ShareX (Windows)](https://getsharex.com/)

Indépendamment du programme utilisé, il est préférable de sauvegarder
les copies d'écran au format PNG (utiliser la compression maximum), et
ne jamais les redimensionner, car on rencontre quelquefois des problèmes
lorsque les copies d'écran sont si petites qu'on ne peut plus rien en
faire. Si vous préférez utiliser des images JPG, elles seront plus
belles si vous désactivez le sous-échantillonnage chroma (le mettre à
"sans", "aucun", "4:4:4" ou "1/1", ils sont équivalents, si le programme
vous le permet comme le fait GIMP).

## Téléverser des fichiers

Pour téléverser des **FICHIERS** tels que ZIP, 7z, TIFF, ou des formats
raw tels que CR2, DNG, PEF, des fichiers problématiques tels que JPG
(voir la note ci-dessous), PNG, etc. essayez ces sites :

- [FileBin](http://filebin.net/)
- [SendSpace](https://www.sendspace.com/)
- [Zippyshare](http://www.zippyshare.com/)
- [Dropbox](https://www.dropbox.com/)

Note: Si vous avez des images JPG/PNG qui vous causent des problèmes
dans RawTherapee, alors nous devons les recevoir **exactement** telles
que vous les avez. N'utilisez pas de sites Web de "partage d'images",
car ces sites recompressent les images, et l'image reçue n’est pas
identique à celle envoyée !

Wikipedia possède [une explication et une comparaison des sites Web
d'hébergement de
fichiers](http://fr.wikipedia.org/wiki/Site_d%27h%C3%A9bergement_de_fichiers).

## Téléverser des captures d'écran

**Ne pas** téléverser d'images JPG/PNG avec lesquelles vous rencontrez
des problèmes dans RawTherapee dans ces sites Web ! Ils modifient
automatiquement vos images et bien qu'elles aient la même apparence, ce
que vous téléversez n'est pas identique à ce que nous recevons. Ils
conviennent assez bien pour les captures d'écran, rien de plus. Ils
acceptent des fichiers jusqu'à 1 ou 2 Mo.

- [imgur](http://imgur.com/)
- [TinyPic](http://www.tinypic.com/)

## Coller du Code

Si vous devez copier/coller du code dans le forum (par exemple des
messages d'erreur, sorties de console), il est plus facile à lire si
vous utilisez une police monospace (largeur fixe). Vous pouvez faire
cela par quatre méthodes :

- Si c'est une courte ligne de code, la mettre entre de simples coches
  inversées, comme ceci : `` `un peu de code` ``
- Si vous avez plusieurs lignes de code, mettre trois coches inversées
  sur une ligne, puis démarrer une nouvelle ligne et mettre ici le code,
  terminer avec trois coches inversées supplémentaires sur une nouvelle
  ligne, comme ceci :

<!-- -->

    ```
    plusieurs
    lignes 
    de
    code
    ```

- Une autre méthode pour une seule ou bien plusieurs lignes de code est
  d'insérer une ligne blanche pour séparer le code du texte le précédant
  puis d'indenter chaque ligne de code avec quatre caractères espace,
  comme ceci :

<!-- -->

    Bla bla, un paragraphe de texte ordinaire. La ligne suivante doit être vide.

        du code
        remarquez les quatre espaces à gauche
    vous pouvez continuer ici avec du texte normal.

- Une dernière méthode pour plusieurs lignes de code consiste à les
  mettre entre balises `[code] [/code]`, comme ceci :

<!-- -->

    [code]
      _____________________________
     / Vous me voyez car j'utilise \
     \ une police monospace, moo   /
      -----------------------------
            \   ,__,
             \  (oo)____
                (__)    )\
                   ||--|| *
     [/code]

Sinon, vous pouvez coller du code dans l'un de ces sites :

- [Paste2](http://paste2.org/)
- [dpaste](https://dpaste.de/)
- [Pastie](http://pastie.org/)
- [PasteBin.com](http://pastebin.com/)
- [PasteBin.ca](http://pastebin.ca/)

Wikipedia possède un bon [comparatif de
pastebins](http://en.wikipedia.org/wiki/Comparison_of_pastebins).

## Création de vidéographies

Une vidéographie est un enregistrement de l'activité de l'écran. Cela
peut s'employer pour des tutoriels, et pour permettre aux autres de
mieux vous aider si vous enregistrez tout ce qui vous donne des
problèmes. Quelquefois, en rapportant un bug, vous pouvez être sollicité
pour réaliser une vidéographie pour faciliter l'assistance.

Voici une liste de logiciels Libres pour création de vidéographies sous
Windows :

- [ShareX](https://getsharex.com/)
- [Open Broadcaster Software](https://obsproject.com/)
- [SimpleScreenRecorder](http://www.maartenbaert.be/simplescreenrecorder/)

Les utilisateurs de Linux ont plusieurs logiciels Libres de vidéographie
à leur disposition (sans ordre particulier) :

- [Open Broadcaster Software](https://obsproject.com/)
- [SimpleScreenRecorder](http://www.maartenbaert.be/simplescreenrecorder/)
- [recordMyDesktop](http://recordmydesktop.sourceforge.net/about.php)
  avec utilisation de l'une des interface, soit QT-recordMyDesktop ou
  GTK-recordMyDesktop
- [VLC](https://www.videolan.org/vlc/)
- [Eidete](https://launchpad.net/eidete)
- [Kdenlive](http://www.kdenlive.org/)
- [FFmpeg](http://www.ffmpeg.org/) avec utilisation de la ligne de
  commande, voir [guide wiki officiel de
  FFmpeg's](https://trac.ffmpeg.org/wiki/Capture/Desktop), ou utilisez
  ceci si la taille de votre fenêtre de RawTherapee est de 1920x1080
  pixels (il enregistre tout l'écran puis réduit à 720p) :

`vid="screencast"; \`  
`crf="23"; \`  
`preset="slower"; \`  
`pushd /tmp/ && \`  
`ffmpeg -y -f x11grab -show_region 1 -s 1920x1080 -i :0.0+0,0 -an -c:v libx264 -preset ultrafast -qp 0 -threads 0 /dev/shm/${vid}.mp4 && \`  
`` ffmpeg -y -ss 00:00:02 -i /dev/shm/${vid}.mp4 -an -c:v libx264 -preset ${preset} -crf ${crf} -s 1920x1080 -s hd720 -sws_flags lanczos -threads 0 ~/${vid}_${crf}crf_${preset}_`date +%F_%H%M%S`.mp4 && \ ``  
`popd && ls -l /dev/shm/${vid}*.mp4 && ls -l ~/${vid}*.mp4 && rm --interactive /dev/shm/${vid}*.mp4`

Wikipedia possède un bon [comparatif de logiciels de
vidéographie](http://fr.wikipedia.org/wiki/Liste_de_logiciels_de_screencasting).

Une fois la vidéographie réalisée, utilisez l'un des sites d'hébergement
listés ci-dessus pour le téléverser puis coller le lien dans le fil
approprié du forum.
