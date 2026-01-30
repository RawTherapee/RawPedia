---
title: RGB and Lab
contributors:
  - Yz2house
tags:
  - 'General Information'
---

<div class="pagetitle">

RGB対Lab

</div>

![](RGB_Cube_Show_lowgamma_cutout_b.png "RGB_Cube_Show_lowgamma_cutout_b.png")
![](Lab_color_space.png "Lab_color_space.png")
　*\[<https://ja.wikipedia.org/wiki/RGB>　RGB\]* と
*\[<https://ja.wikipedia.org/wiki/Lab%E8%89%B2%E7%A9%BA%E9%96%93>　CIE
L\*a\*b\*\]* (或いは単に "*Lab*")
は、2つの異なる\[<https://ja.wikipedia.org/wiki/%E8%89%B2%E7%A9%BA%E9%96%93>　色空間\]のことで、色の表現方法が違います。

　多くの人が、[露光補正セクション](exposure/jp)（RGB色空間）で明度、コントラスト、彩度を調整することと、[Lab調整セクション](lab_adjustments/jp)（Lab色空間)で明度、コントラスト、色度を調整するのは、何が違うのか不思議に思うでしょう。RGBの色表現は画像データをレッド、グリーン、ブルーの3つの色チャンネルに分けて行います、Lab調整は画像データを、明るさ（明度）を構成するLと、色を構成する2つの補色次元aとbに分けて行います。明るさという要素を色と切り離しているので、1つの要素を動かしても、他が変化することがありません。Labの“明度”は人間の視覚感度に近い、つまりグリーンに非常に敏感で、ブルーに対してはそうでもない、設計になっています。従って、Lab調整で明度を高めると、それによる色合いの変化は概ね人間の目で見たものと同じになります。一般に、Lab調整で色度のスライダーを+方向に動かすと、色は‘新鮮さ’を増し、RGBの彩度スライダーを同じように動かすと色に“暖かみ”が加わると言います。

<div align="center">

<File:colorspace_flowers_900_1_neutral.jpg> \| ニュートラル
<File:colorspace_flowers_900_2_rgb_lightness.jpg> \| RGB明度＋30
<File:colorspace_flowers_900_3_lab_lightness.jpg> \| Lab調整明度＋30
<File:colorspace_flowers_900_4_rgb_contrast.jpg> \| RGBコントラスト＋45
<File:colorspace_flowers_900_5_lab_contrast.jpg> \|
Lab調整コントラスト＋45
<File:colorspace_flowers_900_6_rgb_saturation.jpg> \| RGB彩度＋25
<File:colorspace_flowers_900_7_lab_chromaticity.jpg> \| Lab調整色度＋25
<File:colorspace_flowers_900_8_vibrance.jpg> \| 自然な彩度＋25

</div>

　しかし、露光補正セクション（RGB色空間）の*明度*
のスライダーと、Lab調整セクション（Lab色空間）の*明度*のスライダーの違いは、見た目には小さいものです。RGBの*明度*のスライダーを+30に調整した画像は、Lab調整で*明度*のスライダーを+30に調整した場合に比べ、若干明るく感じる程度で、その時の色の映りは、Lab調整の方が、RGBより鮮やかさが少し強く感じられるくらいです。コントラストスライダーに関しては逆の結果になります。RGBの*コントラスト*を+45に設定した場合と、Lab調整で同じ設定をした場合とでは、前者の画像の方が色の暖かみは強くなります。コントラスト自体の強弱感は、ほぼ同じです。まずは、両方のスライダーを使って彩度やコントラストを変えてみて違いを実感して下さい。*彩度*と*色度*のスライダーに関して言えば、RGBの*彩度*スライダーを‐100に設定すると、赤フィルターを使って撮影したような白黒画像となります。Lab調整の色度のスライダーの場合、よりニュートラルな白黒画像に変わります。RGBの彩度がプラスの値に設定されると、色相も変化します（値が大きくなると、その変化も大きくなります）。Lab調整の*色度*調整では、色相はそのままで、色だけが強くなり、パリッとした透明感のある結果となります。よって、画像の色を強くしたい時は、Lab調整の色度
（“*色度*”のスライダー、或いは“*CC*”カーブで）を使うことをお奨めします。
