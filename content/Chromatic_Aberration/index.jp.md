---
title: Chromatic Aberration
contributors:
  - Yz2house
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

色収差

</div>

　この“色収差”補正機能は、デモザイク処理の**前**に働くので“*Raw*”タブの中に入れてあります。一方、“変形タブ”の中にある[色収差補正はデモザイク](lens/geometry/jp#chromatic_aberration_correction)処理の**後**の画像に働きます。

　Rawレベルの色収差補正は、今のところ\[<https://ja.wikipedia.org/wiki/ベイヤーフィルター>　ベイヤーフィルター\]を使ったカメラで撮影したrawファイルだけに適用出来ます。X-Transセンサーを使ったカメラ（フジ）で撮影したrawファイルの色収差を補正する場合は、変形タブの中にある色収差補正を使います。

　色収差は“レッド”と“ブルー”のスライダーを使って行います。通常、色収差の有無は、画面サイズのプレビュー画像では見分けられないと思いますので、詳細ウィンドウ![<File:Window-add.png>](Window-add.png "File:Window-add.png")や![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png")を使って、画像を100％以上に拡大する方がいいでしょう。

　レンズの色収差によって、主に画像の輪郭部分が、青味がかった緑や、マゼンタ色になる歪みを補正します。この補正はデモザイク処理の前に行われるので、デモザイク処理の質を上げることが出来るでしょう。

<img src="/images/chromatic_aberration_auto1.jpg"
title="chromatic_aberration_auto1.jpg" width="900"
alt="chromatic_aberration_auto1.jpg" />
<img src="/images/chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" width="900"
alt="chromatic_aberration_auto2.jpg" />

## 自動補正

　“自動補正”を有効にすると“レッド”と“ブルー”のスライダーは使えなくなり、プログラムが色収差の発見と補正を自動的に行います。手動による補正は一定の調整値を画像全体に適用しますが、自動補正の場合は、プログラムが画像を幾つものブロックに分けて、それぞれに適した調整値で色収差の補正を行います。そのため、通常はこの自動補正の方が、補正効果は高いと思います。自動的に設定される調整値はスライダーには反映されません。

## 繰り返し

　“自動補正”のオプションが有効の場合に、この設定が出来ます。但し、自動補正の作用は控えめなので、色収差の全部を補正できないことがままあります。残った色収差を補正するために、バージョン5.5のRawTherapeeからは色収差補正を最大5回繰り返すオプションを加えました。繰り返すごとに処理時間は増えますが、残りの色収差を軽減していきます。

## レッドとブルーのスライダー

　“レッド”と“ブルー”のスライダーに、0以外の数値が入力されると、それが色収差を補正する調整値として適用されます。“自動補正”と並行して使うことは出来ません。
