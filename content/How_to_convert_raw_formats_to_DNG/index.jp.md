---
title: How to convert raw formats to DNG
contributors:
  - Yz2house
tags:
  - 'General Photography'
---

<div class="pagetitle">

Rawファイルの形式をDNGに変換する

</div>

__FORCETOC__

![](Adobe_dng_converter_83.png "Adobe_dng_converter_83.png")
![](Adobe_dng_converter_raw.png "Adobe_dng_converter_raw.png")

　デジタル（一眼レフ）カメラであれば、殆どの場合画像を[メタデータ](https://ja.wikipedia.org/wiki/%E3%83%A1%E3%82%BF%E3%83%87%E3%83%BC%E3%82%BF)と共に、[JPEG](https://ja.wikipedia.org/wiki/JPEG)形式でも、何百万ものフォトサイトで構成された撮像センサーで捉えた膨大なrawデータをメーカー固有のraw形式でも保存できます。中にはraw形式として、Adobe©が開発した可逆圧縮の[オープンファイル](https://ja.wikipedia.org/wiki/%E3%82%AA%E3%83%BC%E3%83%97%E3%83%B3%E3%83%95%E3%82%A9%E3%83%BC%E3%83%9E%E3%83%83%E3%83%88)である[DNG](https://ja.wikipedia.org/wiki/Digital_Negative)（デジタルネガティブ）を選択できるカメラもあります。既に"現像済み"であるJPEG画像とは異なり、rawファイル（メーカー固有の形式及びDNG形式）は未加工のデータ（故に、"raw"は大文字で書きません、頭字語ではないからです）を含んでおり、画像として見るためにはその処理が必要です。

そのrawファイルを最新のDNG形式に変換して現像に使うことには様々なメリットがあります：

1.  世界共通でサポートされている形式です。貴方のraw画像がDNG形式ではなく、ソフトウェアによってはサポートされていない場合でも、DNG形式に変換することで、利用できる可能性があります。
2.  古臭い形式などではなく、常に維持管理され、バージョンも更新されています。
3.  Adobe DNG
    Converterは、ファイルの変換時に、メーカー形式のrawファイルには欠けていることがあるマトリクスを差し込みます。これにより、RawTherapeeの様なraw現像プログラムを使った処理過程で発生の可能性がある曖昧さを軽減することが出来、引いては色の忠実性が向上します。
4.  より優れた損失のない圧縮方法で、DNG形式のファイルは多くの場合、メーカー形式のファイルよりサイズが小さくなります。
5.  貴方のカメラがDNG形式のraw撮影が出来る機種でも、そのDNG形式が古いバージョンである可能性が高いと思われます。最新のAdobe
    DNG
    Converterで古いDNGファイルを新しいDNG形式に再変換すれば、質が向上することもあります。新しいバージョンのカラーマトリクスの方がより正確である、非損失圧縮が向上している、欠陥ピクセルに対する対処が良くなっている、新しいオペコードが含まれている、便利なメタデータタグが挿入されている、などの可能性があるからです。

　但し、新しいDNG形式に変換する場合は、常に古いrawファイルを消去する前に、一度その新しいrawファイルが正しくプログラムによって処理されるかどうかテストするべきです。ただ、そうは言ったものの、新しいDNG形式に変換することで問題が発生することはまずありません。むしろそうした懸念は誤謬に近いかもしれません。

　RawファイルをDNG形式に変換するプログラムは、Adobe DNG
Converterだけではありません。例えば、Kipi-PluginsにLibrawとLibkdcrawを使ったDNG
Image
Converterがあります。しかし、このコンバーターが使用しているマトリクスは不明で、どこのマトリクスかも分かりません。従って安全を期するならAdobe公式のDNGコンバーターを使うべきでしょう。

　最新のAdobe DNG Converterは以下のリンクから入手できます：

- [Download Adobe DNG
  Converter](https://www.filehorse.com/download-adobe-dng-converter/old-versions/)
  （Linuxにインストールする場合も、以下で説明している様にWindows用を入手します）

　後は解凍して作動させるだけです。

## サポートされていないカメラセンサー

　DNG形式は純粋なrawデータで変換することが出来ますが、デモザイク済みの形式に変換することも出来ます。しかし、それらデモザイク済みの画像は純粋にはraw画像ではありません、何故なら既に処理されているからです。このことは一般的に言えば好ましくありませんが、場合によってはそれを上手く利用することも可能です。![](Adobe_dng_converter_830.png "Adobe_dng_converter_830.png")
　
　撮像センサーの中には、RawTherapeeがサポートしていない\[<https://en.wikipedia.org/wiki/Color_filter_array>　カラーフィルター配列\]を使っているものがあります。従って、これらのrawファイルを直接処理することは出来ませんが、Adobe
DNG
Converterを使って、RawTherapeeでも処理可能な“デモザイク処理済み”のDNGファイルに変換することが出来ます。しかし、これらデモザイク済みのDNGファイルは純粋にはrawファイルではないので、くれぐれも元のrawファイルを消去しないよう（将来、サポートされるようになった時のことを考慮して）注意して下さい。以下の様な設定が必要です：

- “DNG 1.4”を使った“カスタム”コンバーチブルモードで形式を変換
- 必ず“リニア（デモザイク処理）にチェックを入れる

この設定を行うと、DNGファイルが元の入力ファイルより大きくなる－例えば、DNGファイルが入力RAFファイルより142％大きくなるとか－ということがあるかもしれません。

　デモザイク処理が施されたこのDNGファイルはRawTherapee（或いは、他のDNGをサポートしているプログラム）で編集・現像することが可能となります。但し、既にデモザイク処理されているので、RawTherapeeのRawタブにある機能は使えません。

  

## Adobe DNG ConverterをLinuxにインストールする

　Wine prefixとして`$HOME/wine-dng`を使って手順を説明します。
