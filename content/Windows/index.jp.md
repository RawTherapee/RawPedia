---
title: Windows
contributors:
  - Yz2house
tags:
  - 'Compiling'
---

<div class="pagetitle">

Windows

</div>

　以下は、[MSYS2](https://www.msys2.org)のビルド環境を使ってWindows版のRawTherapeeをコンパイルする解説です。カスタマイズとビルド行程の理解には\[\[Linux/jp\]の項を参照して下さい。

　注意1：以下の説明は、**Windows7以降の新しいWindows**の**64ビット**バージョンでRawTherapeeをコンパイルするためのものです。32ビットバージョンのコンパイル、及びWindows7より前のWindows版のビルドサポートは終わりました。最後に作られた32ビットWindows
XPビルドは5.0-rc1です。[here](http://www.rawtherapee.com/downloads/5.0-r1/)からダウンロード出来ます。

　注意2：RawTherapeeのコンパイルには、[Windowsのサポート](https://gitlab.gnome.org/GNOME/gtk/issues/760#note_110809)をしているバージョン3.22.24以上のGTK+も必要です。これが無いと、RawTherapeeのインターフェイスで、Windows10のタスクバーが最大化されて表示されるような、[問題](https://github.com/Beep6581/RawTherapee/issues/4125)が生じます。ビルド環境を更新すれば、こうした問題は起こりません。

## MSYS2のインストール

### MSYS2の基本システムをインストール

　以下の説明に従って、MSYS2のビルド環境を[MSYS2ウェブサイト](https://www.msys2.org)からインストールします。それが最新バージョンであることを確認して下さい。以下のコマンドを使います。

    $ pacman -Syu

　MSYS2は異なる目的を持つ、**MSYS**, **MinGW 32-bit**、**MinGW 64-bit**
という[3つのシェル](https://www.msys2.org/wiki/MSYS2-introduction/)
(コマンドラインインターフェイス)を提供しています。それぞれスタートメニューのショートカットを使って起動できます。PCのOSが64ビットであれば、それに最も適したアプリケーションをビルドすべきなので、**MSYS2
MinGW 64-bit**のシェルを使います。

<figure>
<img src="/images/MSYS2_Shell.jpg" title="File:MSYS2 Shell.jpg" />
<figcaption><a href="File:MSYS2">File:MSYS2</a> Shell.jpg</figcaption>
</figure>

　注意：テキストの中の<MSYS2>はMSYS2のインストールフォルダのことを指します。通常は`C:\msys64`です。

### ツールとライブラリーをインストール

　MSYS2はソフトウェアや構成要素をインストールするためにパッケージマネジャー`pacman`を使います。詳しくは、[pacmanマニュアル](https://wiki.archlinux.org/index.php/pacman)を参照して下さい。

　初めに、幾つか細かいツールをインストールします:

    $ pacman -S tar gzip nano make diffutils intltool git

　次に必要な開発ツールとライブラリーをインストールします:

    $ pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb mingw-w64-x86_64-make mingw-w64-x86_64-pkg-config mingw-w64-x86_64-cmake mingw-w64-x86_64-ninja mingw-w64-x86_64-gtkmm3 mingw-w64-x86_64-lcms2 mingw-w64-x86_64-fftw mingw-w64-x86_64-lensfun

### Lensfunデータベースの更新

　RawTherapeeはレンズに起因する問題の補正に、[Lensfun](https://lensfun.github.io)のライブラリーを使います。以下のコマンドでデータベースを更新します：

    $ lensfun-update-data

　アップデータが更新されたデータベースのある場所にパスを返します。**このパスは後で使うので何処かにコピーしておいて下さい。**

### ダウンロードとlibiptcdataの構築

必要な`libiptcdata`のライブラリーはMSYS2から提供されていないので、手動で構築します。

    $ cd ~
    $ curl -LO http://downloads.sourceforge.net/project/libiptcdata/libiptcdata/1.0.4/libiptcdata-1.0.4.tar.gz
    $ tar xzf libiptcdata-1.0.4.tar.gz
    $ cd libiptcdata-1.0.4
    $ ./configure --prefix=/mingw64

　結果として得られる`Makefile`には幾つか変更が必要です。ファイルの編集はどのエディターを使っても出来ますが（例、貴方のOSにあるエディター、またはシェルに付属しているエディター）、ここでは、シェルに付属している`nano`エディターを使った編集を解説します：

    $ nano Makefile

    # search (command Ctrl+W)
    DIST_SUBDIRS = m4 libiptcdata po iptc docs win python
    # and replace with
    DIST_SUBDIRS = m4 libiptcdata po win python

    # search
    SUBDIRS = m4 libiptcdata po iptc docs win $(MAYBE_PYTHONLIB)
    # and replace with
    SUBDIRS = m4 libiptcdata po win $(MAYBE_PYTHONLIB)

    # save and quit
    Ctrl+X, Y

　最後にライブラリーをビルドしてインストールします：

    $ make install

## クローンとRawTherapeeのビルド

### RawTherapeeのGitレポジトリのクローン

[公式GitHubレポジトリ](https://github.com/Beep6581/RawTherapee)からRawTherapeeのソースコードのクローンを作ります。

    $ cd ~
    $ git clone git://github.com/Beep6581/RawTherapee.git
    $ cd RawTherapee

### ブランチを替える

　クローンが作成されると、自動的に`dev`ブランチが作られます。これが貴方の使うメインのRawTherapeeの開発用ブランチになりますが、これを\[<https://github.com/Beep6581/RawTherapee/branches異なるブランチ%5Dに変える場合は以下のコマンドを使います>：

    $ git checkout branchname # replace with another available branch name

### ビルドのために独立したディレクトリを作成

　アプリケーションを構築するために、新しいディレクトリを作る必要があります。ディレクトリの名前は何でも構いません、例えば：

    $ mkdir build
    $ cd build

　注意：ブランチを替えた場合は、問題発生を防ぐため、常に空のディレクトリを作っておいて下さい。そのためにビルドディレクトリの中のファイルを全て削除するには、`rm -rf *`を使います。

### 構成とコンパイル

　貴方のPCの構造に最も適したビルドを作成するために、以下のコマンドを使います：

    $ cmake -G "Ninja" -DLENSFUNDBDIR=put/your/lensfun/directory/here -DCMAKE_BUILD_TYPE="release" -DPROC_TARGET_NUMBER="2" -DCACHE_NAME_SUFFIX="5-dev" ..
    $ cmake --build . --target install

　必ず、Lensfunのデータベースへのパスを、ソースププログラムの数ステップ前に取得したパスに差し替えます。様々なオプションの詳細を知りたい場合は、[Linuxの](linux/jp#cmake)項を参照して下さい。貴方のPCのシステムにもよりますが、ビルドにはおよそ5分～25分の時間がかかります。

　ビルドの作成中に警告が出ることがあるかもしれませんが、それらは無視して構いません。本解説に従ってビルドの作成を行って、誤入力以外の要因でエラーが発生した場合は、[ここ](https://github.com/Beep6581/RawTherapee/issues/new?assignees=&labels=&template=bug_report.md&title=)に報告して下さい。

### RawTherapeeを起動する

　以上でRawTherapeeを起動することが出来ます：

    $ ./release/rawtherapee.exe # replace release with debug or relwithdebinfo if you built another target

### オプション：予めCMakeのcacheを読み込む

[CMakeのマニュアル](https://cmake.org/cmake/help/latest/manual/cmake.1.html)で以下の様に解説されています。

    -C <initial-cache>

        Pre-load a script to populate the cache.

        When cmake is first run in an empty build tree, it creates a CMakeCache.txt file and populates it with customizable settings for the project. This option may be used to specify a file from which to load cache entries before the first pass through the project’s cmake listfiles. The loaded entries take priority over the project’s default values. The given file should be a CMake script containing SET commands that use the CACHE option, not a cache-format file.

　CMakeの起動を簡素化し、Windows特有のオプションを簡単に定義できるようにするために、ソースの中に`win.cmake`テンプレートスクリプトがあります。`mywin.cmake`の更新などにより、上書きされてしまうことを避けるためRawTherapeeのソースからコピーします。

    $ cmake -G "Ninja" -DLENSFUNDBDIR=share/lensfun -DCMAKE_BUILD_TYPE="release" -DPROC_TARGET_NUMBER="2" -DCACHE_NAME_SUFFIX="5-dev" -C <path/to/mywin.cmake> ..

## バンドルビルドを作成する

　以下は、RawTherapeeをMinGWシェル以外で起動する、もしくはそのビルドを配布する場合の解説です。

　注意：Windowsのファイルマネジャーでもコピー出来ますが、`mingw64`シェルスクリプトの中の[robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)
を使い、オプションで`/`の代わりに`-`を使って行う方法を奨めます。

### フォルダの定義

- <prefix> は <MSYS2>`\mingw64`です
- <MSYS2>はMSYS2のインストレーションフォルダです
- `.`はRawTherapeeのインストレーションフォルダです

### RawTherapeeの実行ファイルと生成されたファイルをコピーする

`c:\code\repo-rt\build\<debug|release|relwithdebinfo> into ..`の中身をコピーします。

### ディペンデンシーのコピー

　必要なDLLsと実行ファイルを<prefix>`\bin`から `.`へコピーします。

　現在のDLLsと実行ファイルの一覧は以下の通りです：

    gspawn-win64-helper.exe
    gspawn-win64-helper-console.exe
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
    libfreetype-6.dll
    libfribidi-0.dll
    libgcc_s_seh-1.dll 
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

　次に示すAdwaitaテーマファイルとディレクトリーを<prefix>`\share\icons\Adwaita\`からコピーし`.\share\icons\Adwaita\`に貼り付けます：

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

　次のファイルをコピーします:

    <prefix>\lib\gdk-pixbuf-2.0 -> .\lib\gdk-pixbuf-2.0
    <prefix>\share\glib-2.0\schemas\gschemas.compiled -> .\share\glib-2.0\schemas
    <prefix>\share\lensfun\version_1\* -> .\share\lensfun

.\share\GTK3に以下を含む`settings.ini`ファイルを作ります：

    [Settings] gtk-button-images=1

## 配布可能なパッケージを作成する

　Windowsのプラットフォームに配布可能なRawTherapeeのパッケージを作る場合は、最初のステップとして、“generic”プロセッサをターゲットとしたRawTherapeeをビルドする必要があります。そのためには、CMakeコマンドで`-DPROC_TARGET_NUMBER="1"`を使います。

　コンパイル中に、RawTherapeeのインストールフォルダに`WindowsInnoSetup.iss`という名前のスクリプトが作成されます。このスクリプトは、Windowsプログラムのためにインストーラーを作るプログラム、[Inno
Setup](http://www.jrsoftware.org/isinfo.php)で使われます。　幾つかの言語による問題を避けるために\[<http://www.jrsoftware.org/download.php/is-unicode.exe>　ユニコードで書かれたバージョン\]のダウンロードを奨めます。

　ユーザーに[バグの報告をしてもらうことがあるので](how_to_write_useful_bug_reports/jp#有効なバグレポートの書き方)、パッケージの管理者には“release”と”debug”の両実行ファイルをビルドし、それらをGDBのデバッガ実行ファイルと共に一まとめにするようお願いします。

　言い換えると、rawtherapee.exe（release）ファイルとrawtherapee.exe(debug)ファイル、及びgdb.exeファイルを同じインストーラー或いは同じアーカイブに一緒に入れます。別な方法として、“release”より最適化はされていませんが、”debug”より動作速度が数段早い“relwithdebinfo”ビルドの作成があります。”debug”ビルドほどの詳細情報は得られませんが、このビルドでもかなりの情報が得られます。

</pre>

　“relwithdebinfo”,
“debug”ビルドの何れの作成するにしても、GDBデバッガの実行ファイルは一緒に入れて下さい。デバッガ実行ファイル`gdb.exe`の32ビット及び64ビットバージョンのWindowsバイナリーは[ここから](http://www.equation.com/servlet/equation.cmd?fa=gdb)ダウンロード出来ます。これで全ての準備が整いました。WindowsInnoSetup.issを右クリックし、コンテックスメニューの中からコンパイルを選択するとパッケージが作成されます。インストーラーが自動的に作成され、親フォルダーの中に置かれます。

　貴方が作成した新しいパッケージとRawTherapeeウェブサイトのアップロードパネルに互換性を持たせるため、新しく作成されたインストーラーとそれに対応するAboutThisBuild.txtファイルの両方を同じ場所に置くためのzipアーカイブを作って下さい。以下のテンプレーで作成したzipアーカイブに名前を付けます：
`RawTherapee_`<branch>`_`<version>`_WinVista_<64>_`<buildtype>`.zip`　

- "WinVista"はWindows10を含むVista以降のどのWindowsバージョンでも動作可能であることを意味します。
- "version"
  は貴方が`5.8`タグと一致させた場合は`5.8`のように表示され、`5.8`タグの後に`dev`ブランチと一致させた場合は、`5.8-g35abd92`と表示されます。

　5.8のタグ付けの後に`dev`をチェックアウトする場合

- 一つのインストーラーに複数のビルドを入れる場合は、名前に<buildtype>を入れないで下さい。
