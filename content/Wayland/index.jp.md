---
title: Wayland
contributors:
  - Yz2house
tags:
  - 'Troubleshooting'
---

<div class="pagetitle">

Wayland

</div>

## Wayland

　ディスプレイサーバー（Waylandコンポジターと呼ばれる）とクライアントとのコミュニケーションに特化したコンピュータープロトコル、Waylandを利用しているユーザーの場合、RawTherapeeのユーザーインターフェイスに不具合が生じることがあります。例えば、全てのコンボボックス（処理プロファイルセレクターやフィルムシミュレーションのドロップダウンリストなど）で、初回の操作は正確に実行されるものの、その後RawTherapeeを再起動しない限り応答しなくなることがあります。しかし、これはRawTherapeeにバグがあるからではありません。

　バグ報告から判断すると、原因はGTK+とWaylandコンポジターの互換性にあるようです。

　以下に挙げるディストリビューションのユーザーの多くが影響を受けているようです：

- Fedoraのバージョン25以上
- Ubuntuのバージョン17.10 (Ubuntuの18.04 はWaylandの問題でX11
  に戻りました)

　影響を受けているユーザーへのアドバイスは：

- コンポジターをWestonに変更してみる
- 問題が継続する場合はX11 に戻す

　以下のリンクから更なる情報を得られます:
<https://fedoraproject.org/wiki/How_to_debug_Wayland_problems>

　但し、上記の説明文の一部はアップデートされていないので注意して下さい。
