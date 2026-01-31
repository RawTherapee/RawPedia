---
title: MacOS
contributors:
  - Yz2house
tags:
  - 'Compiling'
---

<div class="pagetitle">

macOS

</div>

　本項は**macOS**システムでRawTherapeeをコンパイルする説明をしています。[Linux](linux/jp)
と [Windows](windows/jp)
でコンパイルする説明は別項にあります。
ここにはコンパイルの際に**何を**、**どうするのか**という詳細が書かれています。**何故**及びこれらコマンドの説明、ディペンデンシーのリスト、CMakeオプション、その他の情報に関しては、[Linux](linux/jp)
を参考にして下さい。

　不明な点があれば、[IRCに](irc/jp)参加して、他の参加者に聞いてみて下さい。

　ソースコードのクローン作成、ブランチの選択、CMakeの構成、実際のコンパイルの手順に関しては、[Linuxの](linux/jp)同じセクションを参照して下さい。以下の情報はそれに追加されたものです。

## ディペンデンシー

　ディペンデンシーのリストはLinuxの[ディペンデンシーを](linux/jp#ディペンデンシー)参照して下さい。

### Homebrew

　以下のコマンドでRawTherapeeに関するディペンデンシーをインストールします:

`brew install gtk+3 gtkmm3 gtk-mac-integration adwaita-icon-theme libsigc++ little-cms2 libiptcdata fftw lensfun wget llvm cmake expat pkgconfig libomp`

### MacPorts

　以下の手順はバージョン10.9及びそれ以降のOS Xでテスト済です。

- **前提条件:**
  - Xcode デベロッパーツール
  - コマンドラインツール
  - MacPorts
    - MacPortsとXcode デベロッパーツールの詳細設定は[MacPorts
      website](https://www.macports.org)のウェブサイトで見ることが出来ます。
    - Appleが提供している専用システムコンパイリングは非常に古いものでOpenMPをサポートしていませんので使わないようにします。MacPortsの最新の安定したコンパイラを使います-その方がRawTherapeeの動作が速くなります。
- **MacPortsの構成:**

  
以下のラインを/opt/local/etc/macports/variants.confに追加します。

  
`+quartz -x11 -gnome`

- **ディペンデンシー:**

  
ディペンデンシーをインストールするには, ターミナルから実行します:

  
`sudo port install git clang-9.0 ++-mp libomp gtk3 gtkmm3 gtk-osx-application-gtk3 adwaita-icon-theme libsigcxx2 lcms2 libiptcdata fftw-3-single lensfun`

Xcode 9.2上でコンパイルする場合は、以下を追加する必要があります:

  
`sudo port install　ld64 +ld64_xcode`

- **MacPortsのコンパイルシステムの構成**

  
`cmake` コマンドに以下のフラッグを追加:

  
`-DLOCAL_PREFIX=PATH:"/opt"`

## コンパイル

　ソースコードの“クローン”の作り方、“ブランチ”の選び方、“CMakeの構成の仕方に関しては、[手動コンパイリングを](linux/jp#コンパイル)参照して下さい。但し、その中の”RawTherapeeをコンパイルする“に記述されているコードは無視して、以下の説明にあるコードを使います。

　ビルドをアップロードする、或いは第三者とシェアする場合には、以下を使う必要があります、

  
`-DPROC_TARGET_NUMBER="1"`

　そして、設定によりプロセッサラベルを手動で行います

  
`-DPROC_LABEL="generic processor"`

　自分用にコンパイルする場合は以下を使います、

  
`-DPROC_TARGET_NUMBER="2"`

　プロセッサラベルの設定は重要ではないのでスキップします。

　貴方のビルドに[コードサイニング](https://developer.apple.com/support/code-signing/)を施す場合は、CMakeコマンドに詳細を追加します:

  
`-DCODESIGNID="Developer ID Application: Firstname Lastname (XXXXXXXXXX)"`

Appと生成されたdmg (Apple Disk Image)がコードサインされます。

　貴方のコードサインしたビルドに\[<https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution/customizing_the_notarization_workflow?language=objc>　公証\]を受けるため、Cmakeコマンドに貴方のappの固有の承認情報を入れます:
`-DNOTARY="--username user@mail.com --password abcd-efgh-ijkl-mnop"`
Appとdmgが公証され（悪意のあるアプリかどうかの確認）、綴じられます（公証チケットが貼り付けられます）。

### RawTherapeeをコンパイルする

　これでコンパイルの準備が出来ました:

    cd ~/repo-rt
    rm -rf build
    mkdir build && cd build
    cmake -DCMAKE_BUILD_TYPE="release" \
          -DPROC_TARGET_NUMBER="1" \
          -DPROC_LABEL="generic processor" \
          -DCACHE_NAME_SUFFIX="5-dev" \
          -DCMAKE_C_COMPILER="clang" \
          -DCMAKE_CXX_COMPILER="clang++" \
          -DWITH_LTO="OFF" \
          -DLENSFUNDBDIR="./share/lensfun" \
          ..
    make j$(sysctl -n hw.ncpu) install
    sudp make macosx_bundle

<hr>

Homebrewのディペンデンシーを使ってLiwm clan
8でコンパイルするのであれば、以下のCMakeコマンドを使います:

    export PKG_CONFIG_PATH=/usr/local/opt/libffi/lib/pkgconfig:/usr/local/opt/expat/lib/pkgconfig && \
    cmake  .. -DCMAKE_BUILD_TYPE="release" \
              -DPROC_TARGET_NUMBER="2" \
              -DCACHE_NAME_SUFFIX="5.8-dev" \
              -DCMAKE_C_COMPILER="clang"\
              -DCMAKE_CXX_COMPILER="clang++" \
              -DWITH_LTO="ON" \
              -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
              -DCMAKE_BUILD_TYPE=Release \
              -DOpenMP_C_FLAGS=-fopenmp=libomp \
              -DOpenMP_CXX_FLAGS=-fopenmp=libomp \
              -DOpenMP_C_LIB_NAMES="libomp" \
              -DOpenMP_CXX_LIB_NAMES="libomp" \
              -DOpenMP_libomp_LIBRARY="/usr/local/lib/libomp.dylib" \
              -DOpenMP_CXX_FLAGS="-Wno-pass-failed-Wno-deprecated-register-Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
              -DOpenMP_CXX_LIB_NAMES="libomp" \
              -DOpenMP_C_FLAGS="-Wno-pass-failed-Wno-deprecated-register-Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
              -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
              -DCMAKE_EXE_LINKER_FLAGS="-L/usr/local/opt/libffi/lib -L/usr/local/lib" \
              -DCMAKE_AR="/usr/local/Cellar/llvm/8.0.0/bin/llvm-ar" \
              -DCMAKE_RANLIB="/usr/local/Cellar/llvm/8.0.0/bin/llvm-ranlib"

### From-Scratchでコンパイルする方法

- オプションで、この
  [1](https://raw.githubusercontent.com/Benitoite/RTdeps/master/macbuildRT.sh)
  完全なコマンドリストは、from-scratch方式によるRawTherapeeのコンパイルとmacOS10.15.3/Xcode
  11.1の実行に使うことが出来ます。
- \[<https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html>　JDK\]をインストールする必要があります。
- \[<https://developer.apple.com/xcode>　 Xcode 11.1+\]
  をインストールする必要があります。

<hr>

### RawTherapeeの実行とシェア

　ビルドディレクトリーの中にディスクイメージを見つけることが出来るでしょう；これはビルドがディストリビューション用であり、前述したvariants.confで貴方が特定したアーキテクチャー要件を満たすコンピューターであればどれでもビルドを実行することが出来ます。

　RawTherapeeのプロジェクトに貴方のビルドを提供するために、dmgとAboutThisBuild.txtファイルをzipで圧縮して下さい。そして、以下のテンプレートに従ってそのzipファイルに名前を付けます:

  
RawTherapee_OSX_**<minimum supported macOS version>**_64_**<RawTherapee version>**.zip

　例えば、貴方のビルドがRawTherapee 5.2-dev-g1a2b3c4dのmacOS
10.12用であれば、その名前は:

  
RawTherapee_OSX_10.12_64_5.2-dev-g1a2b3c4d.zipとなります。

　そのzipアーカイブをhttp://filebin.net/にアップロードし、[open a new
issue on our GitHub
page](https://github.com/Beep6581/RawTherapee/issues/new)にそのリンクを貼り付けて下さい、そうすれば私たちがウェブサイトにアップロードできます。

#### macOS 10.15

- macOS 10.15 *Catalina*
  上でRawTherapee5.8を実行する場合は以下が必要です:
  - Appをコピーし`/Applications` フォルダーから実行します。
  - `/bin/sh`をSystem Preferences \> Security & Privacy \> Privacy \>
    Full Disk
    Accessに追加します。プログラムを起動した最初の時だけ、自動的にこれが行われるよう要求されます。
