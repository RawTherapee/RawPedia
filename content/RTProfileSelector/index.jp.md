---
title: RTProfileSelector
contributors:
  - Yz2house
tags:
  - 'Processing Profile Scripts'
---

<span style="color: #000000; background: none; overflow: hidden; page-break-after: avoid; font-size: 2.0em; font-family: Georgia,Times,serif; margin-top: 1em; margin-bottom: 0.25em; line-height: 1.3; padding: 0; border-bottom: 1px solid #AAAAAA;">RTプロファイルセレクター
</span>

<div class="pagetitle">

RTプロファイルセレクター

</div>

　　**RTプロファイルセレクター**はRawTherapeeのプラグインで、ユーザーが定義したルールに基づいて、カスタム処理プロファイル（pp3ファイル）を自動的に選択させます。ルールはExif領域のデータとRawTherapeeで初めて開いたrawファイルから抽出した実際の値とマッチする値で設定されます。

　RTプロファイルセレクターを使ってRawTherapeeに自動で幾つかの作業させることが出来ます：

- カメラの撮影セッティング（例えば、“白黒”、“鮮やかさをプラス”、“フィルム調”など）に合わせて、貴方が作成した処理プロファイルを自動で選択させる。
- カメラの機種やISO設定に合わせて、ノイズ低減の調整値を自動で選択させる。
- 撮影に使ったレンズやカメラに合わせて、レンズ補正プロファイルを自動で選択させる。

　RTプロファイルセレクターはC++11言語で書かれており、WindowsとLinuxの両方でコンパイルされています。ソースコードとWindowsの実行ファイルは\[<https://github.com/marcapelini/RTProfileSelector>　
GitHubのリポジトリー\]（英語）からダウンロードできます。画像からメタデータを取り出す際には\[<http://www.sno.phy.queensu.ca/~phil/exiftool/>　ExifTool\]（英語）を使います。

　インストールと使い方は、このプラグイン導入の[Wikiセクション](https://github.com/marcapelini/RTProfileSelector/wiki)（英語）をお読み下さい。
