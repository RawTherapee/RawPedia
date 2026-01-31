---
title: Forum
contributors:
  - Yz2house
tags:
  - 'Interact'
---

<div class="pagetitle">

フォーラム

</div>

　私達のフォーラムにお越し下さい：http://rawtherapee.com/forum/

## スクリーンショットの作り方

　PCの**Print
Screen**ボタンを使って、画像エディターに貼り付け、PNG形式で保存するか、或いは、より多くの機能を持つ画像エディター、例：Gimp（下に、WindowsとMacのリンクがあります）、をインストールして、スクリーンショットを作ることが出来ます。Gimpにスクリーンショットを取り込み、“ファイル→新規作成→スクリーンショット”で作成します。

　Wikipediaにラスタデータを使うグラフィックエディターの便利な\[<http://en.wikipedia.org/wiki/Comparison_of_raster_graphics_editors>　比較表\]（英語）があります。

　どの様な画像編集プログラムを使おうとも、スクリーンショットは、最大圧縮を使ったPNG形式がベストです。また、必要、或いは、明らかな意図がなければ、画像のリサイズは行わない方がいいでしょう。私達に送られてくるスクリーンショットの中にも、小さすぎて何だか分らないものがあります。JPEG形式のファイルを使う場合は、サブサンプリング（1:1:1）を無効にした方が、見栄えがいいでしょう。

## ファイルのアップロード

　Zip、7z、TIFF、CR2やDNG、PEFのようなrawフォーマット、問題の多いJPEGの様な**ファイル**（下記を参照して下さい）、PNG、などのファイルをアップロードする際は、以下のサイトをご利用ください（英語）：

- [FileBin](http://filebin.net/)
- [SendSpace](http://www.sendspace.com/)
- [WikiUpload](http://www.wikiupload.com/)
- [Zippyshare](http://www.zippyshare.com/sites/index_old.jsp)
- [Dropbox](https://www.dropbox.com/)

　注意：貴方の使っているRawTherapeeの動作に問題を起こしたJPEGやPNG画像を、バグを報告するために送る場合、私達もそれと**全く同一の画像**を受け取る必要があります。その際に“イメージシェアリング”が使われているウェブサイトからは送らないで下さい。それらのサイトは貴方が送る画像を再圧縮してしまい、同じ画像ではなくなってしまいます。

　Wikipediaにファイル送信のウェブサイトの\[<https://en.wikipedia.org/wiki/File_hosting_service>　比較と説明\]があります。

## スクリーンショットのアップロード

　RawTherapeeに問題を起こしたJPEG／PNG画像は、**以下のサイトからは送らないで下さい**。これらのサイトは貴方がアップロードしたファイルを自動的に再処理してしまいます。見た目は同じでも、同一ではありません。スクリーンショットを送るには十分に使えますが、それ以上には使えません。通常、これらのサイトは1～2MBのスクリーンショットを送ることが出来ます：

- [imgur](http://imgur.com/)
- [TinyPic](http://www.tinypic.com/)

## コードの貼り付け

　当フォーラムにコードを貼り付ける必要がある場合（例：エラーメッセージやコンソールアウトプット）、モノスペース（固定幅フォント）を使って頂けると、私達としては読みやすくなります。そのために、`[code] [/code]`タグを使って下さい。以下に例を示します：

`[code]`  
`Your code here.`  
` ______________________`  
`/ You see me because I \`  
`\ use monospace font.  /`  
` ----------------------`  
`       \   ,__,`  
`        \  (oo)____`  
`           (__)    )\`  
`              ||--|| *`  
`[/code]`

　または、以下のサイトでコードを貼り付けることも出来ます：

- [Paste2](http://paste2.org/)
- [Pastie](http://pastie.org/)
- [PasteBin.com](http://pastebin.com/)
- [PasteBin.ca](http://pastebin.ca/)

　Wikipediaに便利なpastebinの\[<http://en.wikipedia.org/wiki/Comparison_of_pastebins>　比較表\]があります。

## スクリーンキャストの作成

　スクリーンキャストとは、デスクトップ上の操作をレコーディングするものです。これを使って指導書を作ったり、他の人のそれを手に入れて自分の操作に役立てたりします。バグレポートでも時折、このスクリーンキャストのソフトを使って、他の人が問題点をより正しく分析するのに使います。

　インストールなしにオンラインで使えるスクリーンキャストのソフトが手に入れば幸運でしょう（英語）：

- [Screenr](http://www.screenr.com/)

　以下は、Windowsで使えるオープンソフトです（英語）：

- [CamStudio](http://camstudio.org/)

　Linuxユーザーが使えるフリーソフトは幾つかありますので、自由に選んで下さい（英語）：

- [recordMyDesktop](http://recordmydesktop.sourceforge.net/about.php)
  （QT-recordMyDesktopか、GTK-recordMyDesktopを選びます）
- [VLC](https://www.videolan.org/vlc/)
- [Eidete](https://launchpad.net/eidete)
- [Kdenlive](http://www.kdenlive.org/)
- [Byzanz](https://download.gnome.org/sources/byzanz/0.2/)
- [Kazam](https://launchpad.net/kazam)
- [Tibesti](https://launchpad.net/tibesti)
- [Vokoscreen](http://www.kohaupt-online.de/hp/)
- [Istanbul](https://wiki.gnome.org/Projects/Istanbul)
- [FFmpeg](http://www.ffmpeg.org/)
  このソフトはコマンドラインを使います。また、貴方のRawTherapeeウィンドウのサイズが1920x1080であれば、このソフトは画面全体を記録し720pにスケールダウンしてくれます：

`vid="screencast"; \`  
`crf="23"; \`  
`preset="slower"; \`  
`pushd /tmp/ && \`  
`ffmpeg -y -f x11grab -show_region 1 -s 1920x1080 -i :0.0+0,0 -an -c:v libx264 -preset ultrafast -qp 0 -threads 0 /dev/shm/${vid}.mp4 && \`  
`` ffmpeg -y -ss 00:00:02 -i /dev/shm/${vid}.mp4 -an -c:v libx264 -preset ${preset} -crf ${crf} -s 1920x1080 -s hd720 -sws_flags lanczos -threads 0 ~/${vid}_${crf}crf_${preset}_`date +%F_%H%M%S`.mp4 && \ ``  
`popd && ls -l /dev/shm/${vid}*.mp4 && ls -l ~/${vid}*.mp4 && rm --interactive /dev/shm/${vid}*.mp4`

　Wikipediaに便利なスクリーンキャストの\[<http://en.wikipedia.org/wiki/List_of_screencasting_software>　一覧\]と\[<http://en.wikipedia.org/wiki/Comparison_of_screencasting_software>　比較表\]があります。

　スクリーンキャストを作成したら、上記のホストサイトのどれかにアップロードし、そのリンク先を当フォーラムに貼り付けて下さい。
