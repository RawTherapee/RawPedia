---
title: Edit Current Image in External Editor
contributors:
  - Yz2house
tags:
  - 'General Information'
---

　この機能は、RawTherapeeで編集した画像を直ぐに外部のアプリケーションで開くためのものです。更なる画像処理や閲覧のために、編集した画像をGIMPやPhotoshop©の様な外部エディター、或いは画像ビューワーに簡単に送ることが出来ます。

　画像を外部アプリケーションに送るための操作ボタン![<File:Rt510> edit in
external editor
gimp.png](Rt510_edit_in_external_editor_gimp.png "File:Rt510 edit in external editor gimp.png")が、プレビューパネルの左下にあります。ボタンをクリックすると画像が処理され、現在選択されている外部アプリケーションに送られます。ボタンのアイコンと、その機能のヒントが外部アプリケーションを反映しています。異なるアプリケーションを使う場合は、操作ボタンのドロップダウン矢印をクリックして、そのリストから使いたいアプリケーションを選択します。リストは環境設定パネルの[外部エディターで今の画像を編集で](preferences/jp#外部エディターで今の画像を編集)作成します。注意：リストの最後にある"その他"を選択すると、プログラムにインストールされているアプリケーションのリストが表示されます。

　この機能が使用されると、RawTherapeeは画像を一時的に16ビット整数でガンマ符号化したTIFFに変換して、[環境設定で指定された出力ディレクトリに](preferences/jp#外部エディターで今の画像を編集)保存します。
