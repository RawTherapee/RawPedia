---
title: Download
contributors:
  - Yz2house
tags:
  - 'General Information'
weight: 3
---

<div class="pagetitle">

ダウンロード

</div>

## 安定リリース

　RawTherapeeの安定ビルドは[**当ウェブサイト**](https://rawtherapee.com/downloads)、或いは貴方の**パッケージマネジャー**を通してダウンロード出来ます。安定ビルドは改良/修正を繰り返して得られた安定したビルドなので業務や仕事での使用にも適しています。

## 開発用ビルド

　開発用ビルドは当公式[**Githubレポジトリー**](https://github.com/Beep6581/RawTherapee/releases/tag/nightly-github-actions)からダウンロードできます。

　開発用ビルドのファイル名は以下の様に構成されています：

`RawTherapee_`<branch>`_[operating-system]_`<build-type>`.`<extension>

Branch  
　ここには各コミットメント名が入っています。メインのbranchは`dev`になっています。新しい機能は独自のbranchで開発され、完成すると`dev`に統合されます。どの開発用ビルドをダウンロードするか判らない場合は、`dev`を選んで下さい。

Operating system  
　ここにはそのビルドが使える特定のオペレーティングシステム名が入っています。最近のWindows64ビット版のビルドであれば`win64`、特定のmacOS版、或いはそれ以降ビルであれば`macOS_10.15`が入っています。Linuxの場合、最近のディストリビューションはOperating
systemのセグメントが省かれ、代わりに拡張子として`AppImage`が入っています。

Build type  
　ここには、`release`、また又は`debug`が入っています。`release`タイプは、動作が優先された安定したビルドですが、クラッシュが発生した場合その原因を突き止めるための情報は殆ど手に入りません。一方、`debug`はクラッシュが発生した場合に[バク報告](http://rawpedia.rawtherapee.com/How_to_write_useful_bug_reports/jp)で役に立つ情報を提供してくれるビルドです。しかし、その分動作速度が著しく下がります。どちらが良いか不明な場合は、`release`タイプを選んで下さい。

　ソースコードが変更される度に、開発用ビルドが自動的に作成されます。これらビルドはユーザーに最新の機能を備え、且つ、最も直近までのバグが修正されたビルドを試してもらい、そして何か問題を発見したら[GitHub](https://github.com/Beep6581/RawTherapee/)、或いは[当フォーラム](https://discuss.pixls.us/c/software/rawtherapee/)当フォーラムを通じてそれを報告してもらうために提供されているビルドです。

　開発用ビルドは**仕事や業務の使用に適していません**（新しい機能の追加や改良により動作が不安定になっている、新しいバグが発生している、などの可能性が小さくないからです）。また、開発用ビルドで編集を行った際に生成される[サイドカーファイル](sidecar_files_-_processing_profiles/jp)（pp3）は**後方互換性も前方互換性も保証されていません。**つまり、ある開発用ビルドで作成されたサイドカーファイルを、安定ビルドや他の開発用ビルドで使うと、異なる編集結果になり易いと言うことです。貴方にとって安定性と互換性が重要であれば、常に最新の安定ビルドを使用することを勧めます。"安定"という条件の下で、開発用ビルドの新しい機能や直近のバグ修正が行われたビルドを使いたいのであれば、次の安定ビルドがリリースされるのを待つ必要があります。
