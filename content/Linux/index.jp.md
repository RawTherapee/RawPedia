---
title: Linux
contributors:
  - DrSlony
  - Yz2house
tags:
  - 'Compiling'
---

<div class="pagetitle">

Linux

</div>

　本ページは、**GNU/Linux**システムでRawTherapeeをコンパイルするためのインストラクションが詳述されています。[Windowsと](windows/jp)[MacOSのインストラクションは](macos/jp)別項にあります。

　不明な点があれば、[IRC](irc/jp)或いは或いは[フォーラムに](forum/jp)参加して他の参加者に聞いてみて下さい。

## ディペンデンシー

　RawTherapeeをコンパイルするためには一連のツールと他のプログラムからのコードライブラリーが必要で、それらはディペンデンシーと呼ばれています。以下で最新のRawTherapeeのコンパイルに必要なディペンデンシーを一覧にしてあります：

| パッケージ  | バージョン          | URL                                                                         |
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
| LCMS2       | lcms\>=2.6          | <https://www.littlecms.com/>                                                |
| LENSFUN     | lensfun\>=0.2       | <https://github.com/lensfun/lensfun>                                        |
| LIBCANBERRA | libcanberra\>=0.29  | <http://0pointer.de/lennart/projects/libcanberra/> (Linux only)             |
| LIBIPTCDATA | libiptcdata\>=1.0.2 | <http://libiptcdata.sourceforge.net>                                        |
| PNG         | libpng\>=1.2.44     | <http://www.libpng.org/>                                                    |
| librsvg     | librsvg\>=2.40      | <https://github.com/GNOME/librsvg>                                          |
| SIGC        | sigc++-2.0          | <https://github.com/libsigcplusplus/libsigcplusplus>                        |
| TIFF        | libtiff\>=4.0.4     | <http://libtiff.org/>                                                       |
| ZLIB        | zlib\>=1.2.3        | <http://www.zlib.net/>                                                      |

ビルド時に必要なディペンデンシー:

　これらディペンデンシー全てをインストールするには、コンソールを開いて該当セクションからそれらコードをコンソールにコピーします。

　これらコードはGTK3を必要とする最新のRawTherapeeに関するディペンデンシーです。2017年2月にリリースした"5.0-r1-gtk2"を最後に、私たちはGTK2のサポートを公式に終了しました。最近のディストリビューションを使っていれば、そのままコードをコピーして貼り付けるだけです。もし、GTK3をサポートしていない古いディストリビューションを使っている場合は、GTK2のアーカーブを参考にしながら、古い`5.0-r1-gtk2`タグをコンパイルします。

### Arch/Manjaro

　Arch及びManjaroの現在のバージョンは特別な設定無しにコンパイルできます。17.1.2より古いバージョンをコンパイルする場合はGTK2のアーカイブを参考にします。

    sudo pacman -S --needed cmake exiv2 expat fftw glib2 glibmm gtk3 gtkmm3 lcms2 lensfun libcanberra libiptcdata libjpeg-turbo libpng librsvg libsigc++ libtiff zlib

[コンパイルの](linux/jp)項に進みます。

### CentOS

　CentOSは非常に古いパッケージで、現在のGCC、git、lensfun、libtiffをインストールするためには更なるステップが必要です。以下に記したステップはCentOS7.4.1708では確認されていますが、このパッケージでコンパイルするのは常に失敗のリスクが伴うでしょう。

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

他のディペンデンシーをインストールします。:

    sudo yum install curl expat-devel fftw-devel gtk3-devel gtkmm30-devel lcms2-devel lensfun-devel libcanberra-devel libiptcdata-devel libjpeg-turbo-devel libpng-devel librsvg2-devel zlib-devel

シンボリックリンク:

    sudo ln -s /usr/lib64/libatomic.so.1 /usr/lib64/libatomic.so

次のステップ、コンパイルに進むにあたって、`build-rawtherapee`のスクリプトを編集する必要があり、ファイルの最後の方にあるCMakeセクションに以下の3ステップを追加します。例えば、"\$HOME"ラインの前にある"-DWITH_BENCHMARK"ラインの後に：

        -DTIFF_INCLUDE_DIR="$HOME/programs/tiff-4.0.9/libtiff" \
        -DTIFF_LIBRARY="$HOME/programs/tiff-4.0.9/libtiff-build/libtiff/libtiff.so" \
        -DCMAKE_CXX_FLAGS="-Wno-deprecated -Wno-parentheses" \

[コンパイルの](linux/jp)項に進みます。

### Debian/Ubuntu/Mint/elementary OS

　現在のバージョンであればこれらは特別な設定無しにコンパイルできます。Ubuntuはバージョンが16.04より古い場合、GTK2のアーカイブを参考にします。
==== Ubuntu \>=16.10, Mint \>=18.3, elementary OS \>=0.4.1 ====

    sudo apt update
    sudo apt install build-essential cmake curl git libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg-dev liblcms2-dev liblensfun-dev libpng-dev librsvg2-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

[コンパイルの](linux/jp)項に進みます。

#### Ubuntu 16.04 LTS

    sudo apt-get update
    sudo apt-get install build-essential cmake curl git libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg8-dev liblcms2-dev liblensfun-dev libpng12-dev librsvg2-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

[コンパイルの](linux/jp)項に進みます。

### Fedora

　現在のバージョンであれば特別な設定無しにコンパイルできます。バージョンが22より古い場合はGTK2のアーカイブを参考にします。

    sudo yum install bzip2-devel cmake exiv2-devel expat-devel fftw-devel gcc-c++ glib2-devel glibmm24-devel gtk+-devel gtkmm24-devel lcms2-devel libcanberra-devel libiptcdata-devel libjpeg-turbo-devel libpng-devel librsvg2-devel libsigc++20-devel libtiff-devel zlib-devel

[コンパイルの](linux/jp)項に進みます。

### Gentoo/Sabayon

　SabayonのユーザーはGentooと同じディペンデンシーを使います。但し、`sudo emerge -uva`の代わりに`sudo equo install`を使います。

    sudo emerge -uva dev-cpp/gtkmm:3.0 dev-libs/expat dev-util/cmake media-gfx/exiv2 media-libs/lcms media-libs/lensfun media-libs/libcanberra media-libs/libiptcdata media-libs/libjpeg-turbo media-libs/libpng gnome-base/librsvg media-libs/tiff net-misc/curl sci-libs/fftw sys-libs/zlib x11-libs/gtk+:3

[コンパイルの](linux/jp)項に進みます。

### openSUSE

　openSUSEのLeaf
15とTumbleweedは問題なく使えます。但し、古いバージョンではコンパイルにあたって重大な問題発生の可能性があります。バージョンが42.1より古い場合はGTK2のアーカイブを参考にします。

    sudo zypper install git cmake gcc gcc-c++ gtk3-devel gtkmm3-devel liblcms2-devel fftw3-devel libitpcdata-devel librsvg-devel libtiff-devel libjpeg8-devel libcanberra-gtk3-devel

　openSUSE Leap
15.1以降のバージョンに関しては、`lensfun`のライブラリーを以下の手順でインストールする必要があります：

    sudo zypper install lensfun-data liblensfun1

　openSUSE Tumbleweedに関しては、パッケージが若干異なります：

    sudo zypper install lensfun-devel

　openSUSEの他のバージョンに関しては、`lensfun`を手動でインストールする必要があります。

    wget https://sourceforge.net/projects/lensfun/files/0.3.2/lensfun-0.3.2.tar.gz
    tar xvf lensfun-0.3.2.tar.gz
    cd lensfun-0.3.2.tar.gz
    mkdir build
    cd build
    cmake ../
    make
    sudo make install

[コンパイルの](linux/jp)項に進みます。

## コンパイル

　一般的には2つの方法でRawTherapeeをコンパイルします：Bashスクリプトを使った自動で行うコンパイル（推奨）と手動によるコンパイルです。

### 自動コンパイリング

　RawTherapeeのコンパイルには、速くて単純、しかもフールプルーフな自動コンパイルを奨めます。最新のRawTherapeeのソースコードをダウンロードし、CPUにとって最適なコンパイルを行うため、Bashスクリプトを使います。コンパイルされたビルドは直ぐに利用できます。但し、スクリプトがビルド時点のディペンデンシーを確認することはないので、スクリプトを使用する前にディペンデンシーの項の説明を読んで下さい。コンパイルされたビルドは独立しているので、ビルドフォルダーの名前を変更すれば、RawTherapeeの複数のバージョンを同時に維持出来るので、デフォルトで前のビルドが新しいビルドで上書きされることはありません。

　ルートユーザーではなく、普通のユーザーとしてスクリプトを実行して下さい。

　ターミナルを開いてスクリプトを手に入れ、実行可能ファイルを作り、起動します：

    cd ~
    wget https://raw.githubusercontent.com/Beep6581/RawTherapee/dev/tools/build-rawtherapee -O build-rawtherapee
    chmod +x build-rawtherapee
    ./build-rawtherapee

### 手動コンパイリング

　推奨されるRawTherapeeのコンパイル方法は前述の自動スクリプトを使う方法ですが、手動によるコンパイルを学びたいと思う方は、続けて以下を読んで下さい。

　手動で複数のプログラムをコンパイルする（例、ディストリビューションのパッケージマネジャーを使用しない）、及びここで説明する手動コンパイルと自動コンパイルのスクリプトの互換性を維持するためには“home”フォルダーをきれいに保っておく必要があります。そのため、RawTherapeeに関係するソースコード全てを含んでいる`~/programs/code-rawtherapee`フォルダーとコンパイルしたビルドを入れる`~/programs/rawtherapee`フォルダーを分けて入れる`~/programs/`フォルダーを作成します。他のプログラムをコンパイルする場合でも同じスキームを使うことが出来ます。

#### ソースコードのクローン

　初めに、RawTherapeeのソースコードリポジトリーのクローンを作ります。コンソールから以下を入力します：

    mkdir -p ~/programs
    git clone https://github.com/Beep6581/RawTherapee ~/programs/code-rawtherapee
    cd ~/programs/code-rawtherapee

#### ブランチを選択する

- 機能の開発は各々の機能ブランチで行います。
- 開発ビルドは`dev`ブランチで行われ、機能ブランチの準備が整うとそれらが`dev`ブランチに統合されます。`dev`ブランチは安定していません。
- リリースビルドは`releases`ブランチにタグ付けされます。

　最も安定したコードが必要な場合は、最新のタグを確認して下さい。利用可能なタグを全て見るには、次を入力します：

    git tag

　直近の最新のコードを試したい場合は、`dev`ブランチ、或いは他の機能ブランチを確認して下さい。利用可能なブランチを全て見るには、次を入力します：

    git branch -a

　確認作業を終了する場合は、"git
checkout"コマンドを使います。次を入力します：

    git checkout <tag or branch>

　RawTherapeeはユーザーインターフェースにGTK+を使っているため、バージョン3.16より新しいGTK+が必要です。もし、貴方のシステムが3.16より新しいバージョンをサポートしていない時は、5.0-r1-gtk2のタグを確認して下さい。私たちはGTK2のサポートを2017年2月2日に公式に終了しましたので、貴方のシステムを更新して下さい。注意：最近のシステムでRawTherapeeの古いバージョンをコンパイルすると、古いディペンデンシーがないので失敗するでしょう。

#### RawTherapeeをコンパイルする

`これでソースコードからRawTherapeeをコンパイルする用意が整いました。そのビルドは``~/programs/code-rawtherapee/build/release``フォルダーに入るので、後でこのフォルダーを``~/programs/rawtherapee``に移動します。`

##### CMake

　コンパイルに先立って注意すべき設定が幾つかありますが、それらは以下に示すように、`-D`オプションを使ってCMakeに送ります：

BUILD_TYPE  
`release`(デフォルト)、或いは`relwithdebinfo`、`debug`の何れか：

この設定で、そのビルドが実行速度優先か、詳細を優先するデバッグ出力かを制御します。

“debug”と”relwithdebinfo”ビルドは、GDBを実行することでRawTherapeeがクラッシュする問題を解決するために有益なスタックバックトレースが得られます。そのスタックバックトレースを私たちに提供してもらえば、問題個所を見つけ修復します。”debug”は動作が最も遅いビルドですが、最も多くの情報を提供してくれます。“relwithdebinfo”は“release”と同じくらい動作が速いですが、”debug”に及ばないまでもかなりの情報を提供することが多いビルドです。“release”ビルドはプログラムの問題がクラッシュである場合は、有益な情報を提供してくれませんが、動作速度を優先したビルドなので、”debug”より数倍速い動作が期待できます。普通にプログラムを使用するのであれば、“release”或いは”relwithdebinfo“のビルドを作るべきでしょう。もしも、再現可能なバグを見つけた場合は、”debug”ビルドを作成し、スタックバックトレースを私たちに送って下さい（もちろん、自らバグを修正し、そのパッチを送ってもらっても構いません）。私たちとしては、“relwithdebinfo”ビルドより、“debug”ビルドから得たスタックバックトレースの方が有難いです。

  
"release"タイプのビルドを作るためには次の様にセットします：`-DCMAKE_BUILD_TYPE="release"`。

<!-- -->

USE_OLD_CXX_ABI  
ON或いはOFF (デフォルト)

プログラムをコンパイルする時は、プログラムが依存するライブラリーと同じ規則を使う必要があります、そうでないとコンパイル（関連付け）が失敗するでしょう。普段はあまり気にする必要はないことですが、現在、GCC4がGCC5に移行している時期なので、デフォルトで互換性のない規則が使われているため、このことが重要となります。もしも、貴方のシステムライブラリーがGCC5でコンパイルされているなら、恐らくC++11という標準が使われていると思われます。これは貴方のRawTherapeeもデフォルトで同じ標準を使わなければならないという意味になります。しかし、貴方のシステムがGCC5を使っていても古いC++03でビルドがコンパイルされていれば、そのRawTherapeeも同じ標準を使わなければならないので、"USE_OLD_CXX_ABI"
to "ON"という設定が必要です。

USE_OLD_CXX_ABIを有効にするためには、-DUSE_OLD_CXX_ABI="ON"と設定します。

<!-- -->

CACHE_NAME_SUFFIX  
これはコンパイルされたRawTherapeeのビルドが使うcacheとconfigフォルダー名の接頭語を設定するオプションです。ファイルパスの項に説明があります。

安定した“release”ビルドを（”release”ブランチにチェックを入れている場合）コンパイルする場合は、`-DCACHE_NAME_SUFFIX=""`を使います。

”dev”をビルドする場合は、`-DCACHE_NAME_SUFFIX="5-dev"`を使います。

<!-- -->

PROC_TARGET_NUMBER  
`0`（デフォルト）から`9`

PROC_TARGET_NUMBERオプションはどのCPUを最適化するのかを設定するためのものです。

自分のためのビルドを作っている場合は、“2”を選択して下さい。これは“ネイティブ”を意味し、貴方のCPUの最適化を自動で検出し、RawTherapeeがそのCPUで最も速く動作出来るようにします。但し、このオプションは古い或いは異なる構造を持つCPUでは全く動作しないかもしれません。

ビルドがディストリビューション（第三者向け）タイプの場合は、“ジェネリック”を意味する“1”を使います。多くのCPUに対する最適化をサポートするため、ユーザーのCPUだけに限る最適化という有益性はありませんが、誰もがダウンロードできるビルドになります。

更に詳細が知りたい場合は、コピーしたレポジトリーの中の“ProcessorTarget.cmake”を参照して下さい。

  
“ネイティブ”の最適化を行うビルドを作成するには、次の様に設定します：`-DPROC_TARGET_NUMBER="2"`

<!-- -->

BUILD_BUNDLE  
`ON`と`OFF`

WindowsとmacOSには強制的に“ON”が使われます。Linuxの場合、“ON”はオプションで、デフォルトは“OFF”です。

ONが設定されると、ビルドは`DATADIR`フォルダーに作成されます。設定されていない場合は、通常システム全体に影響する`CMAKE_INSTALL_PREFIX`に関連付けられているフォルダーにインストールされます。

<!-- -->

BUNDLE_BASE_INSTALL_DIR  
絶対パスを使います。

プログラムはそのフォルダーに作成されます。

例えば、`-DBUNDLE_BASE_INSTALL_DIR="$HOME/programs/rawtherapee"`というように設定します。

設定されなければ、デフォルトの`${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE}`が使われます。

<!-- -->

LENSFUNDBDIR  
デフォルトでは未設定

`LENSFUNDBDIR`オプションは、lensfunのデータベースを指定したディレクトリーに入れることを許可するものです。未設定は絶対パスでも相対パスでも構いません。

未設定の場合は、lensfunが自らのロジックを使ってデータベースを探します。システム全体にインストールしてそれを使いたい場合は、未設定にすることを奨めます。

カスタムなlensfunのデータベースを使いたい場合は、相対パス或いは絶対パスで設定します。

バンドルを作成する場合は、ルートフォルダーに対する相対パス、その他の場合は`DATADIR`に対する相対パスを使います。例えば、`${CMAKE_INSTALL_PREFIX}/share/rawtherapee`

<!-- -->

OPTION_OMP  
ON（デフォルト）或いはOFF

OpenMPを有効にしてビルドを行うと、マルチスレッドが有効となりRawTherapeeのコンパイルが速くなります。

<!-- -->

WITH_LTO  
ON（デフォルト）或いはOFF

有効にするとリンク時最適化を使ってビルドを行うことが出来ます。RawTherapeeの動作が多少速くなります。

<!-- -->

WITH_PROF  
ON或いはOFF（デフォルト）

これはデバッグが目的のオプションです。プログラムのgprofを分析するのに適したプロファイル情報を書き出すのに、追加となるコードを作成します。

<!-- -->

WITH_SAN  
OFF（デフォルト）或いは様々なオプションの一つ

これもデバッグが目的のオプションです。プログラムの問題を見つけるために様々なバグ検出ツールを有効にするものです。

更なる情報を得るには、GCCマニュアルのProgram Instrumentation
Optionsチャプターを参照して下さい。

<!-- -->

WITH_SYSTEM_KLT  
ON或いはOFF（デフォルト)

ONにするとsystem KLT
libraryを使ったビルドが行われます。OFFの場合は、RawTherapeeに付属するKLTファイルを使います。KLT（Kanade-Lucas-Tomasi）feature
trakerはAuto Distortion Correctionツールでも使われています。

<!-- -->

WITH_BENCHMARK  
ON或いはOFF（デフォルト）

パフォーマンス評価のためにタイミング機能を有効にしてビルドを行うオプションです。

#### Make

　貴方のPCがサポート出来るスレッドの数を調べる設定です。コンパイルする速度には影響しますが、コンパイルされたRawTherapeeの実行速度には影響しません。サポートしているスレッドの数を調べるにはターミナルから次を実行します：

    nproc --all

　数値が返されるので、この数値を以下に示す`--jobs`パラメータに使います。

　コンパイル:

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
        -DWITH_SAN="OFF" \
        -DWITH_SYSTEM_KLT="OFF" \
        ..

    make --jobs=4
    make install

#### RawTherapeeを起動する

　RawTherapeeを実行するには:

    ~/programs/rawtherapee/rawtherapee

　CLIバージョンを実行するには:

    ~/programs/rawtherapee/rawtherapee-cli

　ソースコードは`~/programs/code-rawtherapee`の中に、コンパイルされたプログラムは、`~/programs/rawtherapee`に入ります。

　`~/programs/code-rawtherapee`は安全に消去することも可能です。コンパイルされたプログラムは引き続き使えますが、プログラムのアップデートを行う場合は、再び上記の作業を全て行う必要があります。むしろ、レポジトリーをそのままにしておき、次に説明するアップデートの作業を1週間、或いは1か月先に行う方が簡単でしょう。

#### RawTherapeeのアップデート

　手に入る最新のコードを使ってRawTherapeeをアップデートするには、以下の作業を行います：

    cd ~/programs/code-rawtherapee
    git pull

　次に、先述したMakeの操作を繰り返します。

　更新時に、前回のビルドフォルダーを再利用すれば、変更のない部分を再度コンパイルする必要がないので、作業を迅速に進められます。変更が行われた部分はCMakeが自動的に検出します。但し、その`build`フォルダーがかなり古い場合には　ー典型的には非常に異なるブランチ間を移動した場合にー　コンパイルが失敗することがあります。その場合は、`build`フォルダーを消去し、“Make”オプションに書かれている操作を踏んで下さい。
