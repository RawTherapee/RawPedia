---
title: Making a Portable Installation
contributors:
  - Yz2house
tags:
  - 'General Information'
---

<div class="pagetitle">

ポータブルメディアにインストール

</div>

　RawTherapee
とそのcacheフォルダーは、USBやその他の大容量記録デバイスに、自立型で保持出来ます。

## Windowsの場合

　RawTherapeeの最新バージョンをダウンロードして下さい。ポータブルにしたいのですから、インストーラーは必要ないでしょう。単に簡潔なZip形式のプログラムだけいいはずです。当ウェブサイトでダウンロードしたバージョンが、インストーラーのない単純なZip形式であれば、以下に説明されている操作は不要です。しかし、インストーラーが付いている場合は、RawTherapeeのファイルを抜き出す必要があります。

- それがInno
  Setupインストーラーの場合は（これを書いている2014年夏時点で言えば、最近のWindowsインストーラーは全てInno
  Setupです。拡張子は.exe）、[innounp](http://innounp.sourceforge.net/)（英語）、或いは[innoextract](http://constexpr.org/innoextract/)（英語）を手に入れ解凍して下さい。
- それがMSIインストーラーの場合は（最近では使われていません）、以下のコマンドプロンプトで起動します：
    
      msiexec /a RawTherapee.msi TARGETDIR="C:\TargetDir" /qb

　MSIインストーラーの名前を置き換えて、適当なディレクトリーに入れます。TargetDirパスで
は、パスが引用符で括られているのでスペースの入力も出来ます。

　仮に解凍されたZipファイルが`E:\RawTherapee`にあるとしましょう。この場合の`E:\`はUSBフラッシュメモリーのドライブのことを指しています。ここで、`E:\RawTherapee\options`のファイルを開き、`MultiUser`オプションを無効にします。これでRawTherapeeを使えば、cacheと貴方の設定は、実行プログラムに関連するサブフォルダーに保存されます。名前はcache、設定の順に、`mychache`、`mysettings`、つまり`E：￥RawTherapee\mycache`、`E:\RawTherapee\mysettings`です。

　これら2つのフォルダーを別々な場所に保存する場合は、[ファイルパスの](file_paths/jp)項を参照して下さい。
　RawTherapeeを更新する際は、新しいバージョンを別なフォルダーに入れて、`mychache`と`mysettings`をそこに移動することを奨めます。

## Linuxの場合

　OSがLinux
の場合、USBフラッシュメモリーなどをポータブルメディアとして使いRawTherapeeを走らせるのは少し複雑になります。これはLinux
の性質に起因しています。Windows対応の　RawTherapee
には必要な全てのプログラムやデータが予め備わっているので、どのWindowsバージョンでもRawTherapee
は動作します。しかし、Linuxの配給バージョンは各々著しく異なるため、ある配給版で動作するRawTherapeeが、他の配給版では動作しないことの方が多いのです。一つの手段として、AppImageを使う方法があります。

　RawTherapee
AppImageはどのLinuxバージョンでもRawTherapeeが動作するために必要なファイルを実行ファイルと共に一つにまとめたファイルです。これをダウンロードし、実行ファイルを開き、プログラムを走らせます。

　AppImageバージョン、安定バージョンのどちらを使用するにしても、RawTherapeeのコンフィギュレーションと処理プロファイルは保持したいところです。

　コンフィギュレーションのバックアップを取っておくため、RawTherapeeの“config”フォルダーから　USBにコピーして下さい。具体的に言えば、“options”ファイルと、貴方が作成した“camconst.json”、PP3、ICC、DCP、LCPなどのカスタムプロファイルです。[ファイルパスの](file_paths/jp)項目に、これらファイルの探し方が説明されています。
