---
title: File Paths
contributors:
  - Yz2house
tags:
  - 'General Information'
---

<div class="pagetitle">

ファイルパス

</div>

　RawTherapeeはcacheとconfigフォルダーを利用しています。これらフォルダーは特定の場所（以下で説明）に収められ、その名前は“RawTherapee”で始まり、その後に接尾語が付いています。これら接尾語は、貴方が使っているバージョンのRawTherapeeを作った人によって付けられたものです。幾つか例を挙げますと：

- RawTherapee
- RawTherapee**4.2**
- RawTherapee**5**
- RawTherapee**5-dev**
- RawTherapee**_test**
- そして、他にもRawTherapeeで始まるフォルダー名がファイルパスフォルダーである可能性があります

　
“RawTherapee”という最初の部分はハードコードされています。次の接尾語はその実行プログラムを作った人により付けられたもので、“5.0-gtk2-123-g87654321”のように長いものもあれば、単純に”5“や”_test”、或いは接尾語のないものもあります。私達は“安定”バージョンをリリースする際は、接尾語を付けないようにしていますが、“開発中”バージョンでは常に“5‐dev”のようにどのバージョンで開発中なのか分かるようにしています。

## Config

　RawTherapeeのconfigフォルダーには以下のものが含まれています。

- [環境設定で](preferences/jp)貴方が設定した数値すべてを記録しているoptionsファイル
- 貴方がキューに移動した画像に関する一時的な[処理プロファイルを](sidecar_files_-_processing_profiles)記録している[バッチフォルダー](the_batch_queue)
- 貴方が定義した画像のraw形式の特定的な扱い（システムのcamconst.jsonを上書きしたもの）を記録した編集可能な[camconst.jsonファイル](adding_support_for_new_raw_formats)
- ダイナミックプロファイルの規定
- RawTherapeeのドロップダウンリストに貴方独自の処理プロファイルを表示させるために保存しておくための“profile”フォルダー

　Configフォルダーはバックアップにも保存しておく方がいいでしょう。新しいPCでRawTherapeeを使う際に、前のPCで貴方が行った設定や、作成したプロファイルがそのまま使えるからです。

　RawTherapeeのconfigフォルダーのデフォルトでの格納場所は（前述した“RawTherapee\*”接頭語を探します）:

　**WindowsXPの場合**  
`%USERPROFILE%\Local Settings\Application Data\`

　**Windows 7、8、10の場合**  
`%LOCALAPPDATA%`

　**Linuxの場合**  
`~/.config/`

　**macOSの場合**  
`~/Library/Application Support/RawTherapee/config/`

　 　ファインダーの‘Go’メニューの下にある‘Go to
Folder’をクリックし（ショートカット：コマンド+Shift+g）、ナビゲートしたいパスを入力/貼り付ければ、それが隠しファイルになっていても見つけることが出来ます。

## Cache

　
　RawTherapeeのcacheフォルダーには以下一連のcacheアイテムが含まれています。

- サムネイル
- メタデータ
- サイドカーファイル
- 任意に埋め込まれたファイル

　RawTherapeeはデフォルトで20,000個のcacheを設定できるようにしてありますが、この“cache”フォルダーのサイズが時間経過と共に著しく大きくなるかもしれないので注意して下さい。“画像”のサブフォルダーに保存されるキャッシュ化されたサムネイルの数が著しく増えた場合にそうなります。“画像”サブフォルダーを削除することでこの問題を避けることが出来ます。それによって画像に施された設定がなくなることはありません。RawTherapeeがサムネイルを再生成するだけで済むからです。

　RawTherapeeのcacheフォルダーのデフォルトでの格納場所は（前述した“RawTherapee\*”接頭語を探します）:

　**WindowsXPの場合**  
`%USERPROFILE%\Local Settings\Application Data\`

　**Windows 7、8、10の場合**  
`%LOCALAPPDATA%\`

　**Linuxの場合**  
`~/.cache/`

　**macOSの場合**  
`~/Library/Application Support/RawTherapee/cache/`

　ファインダーの‘Go’メニューの下にある‘Go to
Folder’をクリックし（ショートカット：コマンド+Shift+g）、ナビゲートしたいパスを入力/貼り付ければ、それが隠しファイルになっていても見つけることが出来ます。

　一つのcacheに32kBのヒストグラムを含むように設定されていましたが、RawTherapee5.5以降は、その必要が無くなったので設定を解除しました。

## 独自のconfigとcacheフォルダー

　`RT_SETTINGS`の環境変数を読み込み/書き込みのアクセス権がある絶対パスに設定することでRawTherapeeに独自のconfigフォルダーが使えます。同じようにして`RT_CACHE`の環境変数を設定すれば、独自のcacheフォルダーが使えます。設定方法は貴方のOS次第なので、インターネットで“<貴方のシステム>の環境変数の設定の仕方”を探して下さい。

例を示します：

Windowsの場合  
変数名：`RT_SETTINGS`、変数：`%LOCALAPPDATA%\rawtherapee\5.7`

変数名：`RT_CACHE`、変数：`Z:\rawtherapee\cache`

LinuxとmacOSの場合  
`RT_SETTINGS=/home/bob/.config/rawtherapee/5.7`

`RT_CACHE=/home/bob/junk/rtcache`

## 処理プロファイル

　貴方ご自身の独自の[処理プロファイルを](sidecar_files_-_processing_profiles/jp#サイドカーファイル‐処理プロファイル)作成した場合は、それをRawTherapeeの“処理プロファイル”リストに表示されるよう、“*profiles*”に保存して下さい。上記“*config*”フォルダーの中にあります。

## 一時フォルダー

　“[外部エディターで今の画像を編集](edit_current_image_in_external_editor/jp)”の操作が行われると、中間画像のファイルを一時的なフォルダーに保存します：

Windowsの場合  
デフォルトでは`$TEMP`環境変数の中に保存されます。通常は`%APPDATA%/Local/Temp`です。

`$TEMP`環境変数がない場合は、`C:\`が使われます。

<!-- -->

LinuxとmacOSの場合  
デフォルトでは、`$TMPDIR`環境変数の中に保存されます。通常は`/tmp`です。

`$TMPDIR`環境変数がない場合も、`/tmp`が使われます。
