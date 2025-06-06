---
title: Toolchain Pipeline jp
contributors:
  - Yz2house
---

<div class="pagetitle">

ツールチェーンパイプラインと測色

</div>

## ツールチェーンパイプライン

### 処理の順番

　以下全てが画像に影響します、画像ファイルを開いた時からスクリーンに表示する、或いは保存するまで、固定された順に影響します。一つのモジュールから次のモジュールまでのデータの流れ、これがツールチェーンパイプラインです。RawTherapeeには4つのパイプライン（メインプレビューに関するもの、保存画像に関するもの、サムネイルに関するもの、もう一つ準備中です）があります。以下は機能が実行される順を単純に示したものです:

1.  プロセス
    1.  ダークフレーム
    2.  フラットフィールド
    3.  バッドピクセル
    4.  ホットピクセル
    5.  比色分析 (内部処理、ユーザーインタフェースの機能にはない)
    6.  Raw ブラックポイント
    7.  レンズの歪曲補正
    8.  グリーン平衡化
    9.  ラインノイズフィルタ
    10. 色収差補正
    11. Raw ホワイトポイント
    12. Raw ヒストグラム
    13. 自動露光補正
2.  デモザイク
3.  レティネックス
4.  ハイライト復元
5.  ホワイトバランス
6.  切り抜き
7.  色空間の変換
8.  ノイズ低減
9.  霞除去
10. ダイナミックレンジ圧縮
11. トーンカーブの自動適用
12. （ローカル編集の）色ずれの回避、対数符号化、ぼかしとノイズ、ノイズ低減、自然な彩度、詳細レベルによるコントラスト調整、ソフトライト、ローカルコントラスト、ウェーブレット、シャープネス、レティネックス、露光補正、色と明るさ
13. TRC（トーンレスポンスカーブ）
14. RGBでの処理
    1.  チャンネルミキサ
    2.  トーンカーブ
    3.  ハイライト
    4.  シャドウ
    5.  RGB カーブ
    6.  HSV カーブ
    7.  カラートーン調整
    8.  フィルムシミュレーション
    9.  白黒
    10. L\*a\*b\* カラー補正グリッド (Lab)
15. Labでの処理
    1.  シャドウ/ハイライト (Lab)
    2.  ローカルコントラスト (Lab)
    3.  Lab調整
    4.  自然な彩度
    5.  L\*a\*b\* カラー補正グリッド(Lab)
    6.  ビネットフィルタ
    7.  グラデーションフィルタ
    8.  トーンマッピング
    9.  インパルスノイズ低減
    10. フリンジ低減
    11. エッジ
    12. マイクロコントラスト
    13. シャープニング
    14. 詳細レベルによるコントラスト調整
    15. ウェーブレット
    16. ソフトライト
    17. アブストラクトプロファイル
    18. CIE色の見えモデル2002
    19. リサイズ
    20. リサイズ後のシャープニング
16. 最終Lab -\> RGB変換

### RawTherapeeの機能一覧

- 一般/メインプレビュー
  - 入力プロファイル
  - モニターのカラープロファイル
  - 作業プロファイル
  - 出力プロファイル
  - クリッピングインジケーター
  - レッド/グリーン/ブルー/輝度/フォーカスマスクのプレビュー
  - 測色の意図
- 露光補正タブ
  - 露光量補正
  - シャドウ/ハイライト
  - トーンマッピング
  - ダイナミックレンジ圧縮
  - ビネットフィルタ
  - グラデーションフィルタ
  - Lab 調整
- ディテールタブ
  - シャープニング
  - ローカルコントラスト
  - エッジ
  - マイクロコントラスト
  - インパルスノイズ低減
  - ノイズ低減
  - フリンジ低減
  - 詳細レベルによるコントラスト調整
  - 霞除去
- カラータブ
  - ホワイトバランス
  - 自然な彩度
  - チャンネルミキサ
  - 白黒
  - HSVイコライザ
  - フィルムシミュレーション
  - ソフトライト
  - RGBカーブ
  - カラートーン調整
  - カラーマネジメント
- 高度な機能タブ
  - レティネックス
  - CIE色の見えモデル2002
  - ウェーブレット
- 変形タブ
  - 切り抜き
  - リサイズ
  - レンズ/ジオメトリ
    - 回転
    - パースペクティブ
    - レンズ補正プロファイル
    - 歪曲収差補正
    - 色収差補正
    - 周辺光量補正
- Raw タブ
  - ベイヤー配列を使ったセンサー
    - デモザイク
    - Raw ブラックポイント
    - 前処理
    - 色収差補正
  - X-Trans を使ったセンサー
    - デモザイク
    - Raw ブラックポイント
  - Raw ホワイトポイント
  - 前処理
  - ダークフレーム
  - フラットフィールド
  - ネガフィルム
  - キャプチャーシャープニング

## 測色

### 測色-色の見えモデルとL\*a\*b\*の重要性

　測色に関する論議は枚挙にいとまがありませんが、正確には科学と呼べないところがあります。如何に複雑な方程式を駆使しても、人間の目が知覚するように画像を表現するには十分ではありません。

　現在、RawTherapeeはL\*a\*b\*色空間と、色順応のために色の見えモデル02/16を使っていますが、HDRアプリケーションとして別の色空間（Jzazbz）と新しい色の見えモデル（ZCAMはまだ使い物になりません）の開発を模索しています。

　L\*a\*b\*色空間の利用は独自の限界を持ちますが、その欠点の多くは少なくともSDR用のアプリケーションとしては軽減に成功しています。

例えば：

- 　L\*a\*b\*は線形ではないので色が“歪む”、特にブルーとバイオレット、レッドとオレンジの間で、と言われます、確かに、色度のカーブやスライダーを単純に調整するだけであれば、色は歪みます。しかし、RawTherapeeでは、"色ずれの回避"（マンセル補正）のオプションを有効にすれば、その歪みを200近いルックアップテーブル（LUT）を使ってほぼ完璧な線形的変化に補正します。
- 　また、L\*a\*b\*はその作業色空間の範囲で、偽色を生むとも言われます。これもまた然りですが、やはり“色ずれの回避”を有効にすれば補間されます。この場合、次の様に作業色空間に相対的な測色の補正を行います：
  - 　画像データの解析を行います
  - 　データが色域の領域に収まっていれば、補正は行われません
  - 　収まっていない場合は、色度が減ぜられます。それでも十分でなければ（或いは、L\*が0や100に近い場合）、L\*が減ぜられます。
  - 　但し、作業色空間にProphotoが使われている限り、上記の様なケースが起こることは非常に稀なので、気にする程の事ではないでしょう。
  - 　彩度（或いは、色度や自然な彩度）が調整された場合は、200近いLUTを使ったマンセル補正が行われます。これでどの様な色ずれも高い確度で補正することが出来ます。例えば、Lab色空間での作業でレッドがオレンジになってもレッドに戻すことが可能です。若干の差は残りますが非常に小さいものです。
  - 　"マンセル補正だけ"のオプションを有効にすれば、マンセルだけで補正を行うことが出来ます。

#### L\*a\*b\*

　L\*a\*b\*色空間はXYZ色空間の可逆変換です（単純に言えば、ガンマ3.0、勾配9.03を適用すれば、YはL\*に変換出来ます）。つまりL\*a\*b\*は、その境界範囲（原色に関する）という点においては、作業プロファイルの基準と色域の基本になるXYZとほぼ同じ様な特性（ダイナミックレンジや色域に関して）を持ちます。但し、多くの場合、L\*a\*b\*はアーティファクト（ハイコントラストやハイライトにおいて）の発生を抑制するためにL\*値を制限できます。私たちがHDR（ハイダイナミックレンジ）の処理を出来るようになれば、恐らく使用する色空間をL\*a\*b\*から"HDR–L\*a\*b\*"に変える必要があるでしょう。データ自体はHDR画像（Evが25以上）でも失われることはありませんが、最大表示輝度が120カンデラ⁄平方メートル程度の普通のモニターでは、十分なハイライトの連続性が得られないからです。

　RGBからL\*a\*b\*への変換自体がHDRの完全な処理を妨げるとは思いません。一般的にこれらの計算には‘浮動小数点’や‘倍精度’のデータ値（32或いは64ビット）、或いはストリーミングSIMD拡張命令（128ビット：4x32または2x64ビット）が使われるからです。L\*a\*b\*変換の線形部分では0.005カンデラ/平方メートル以下の輝度を処理することが出来ます。放物線部分（ガンマ＝3）では、ハイライトのデータ値の配分を制限し、120カンデラ/平方メートル以上の輝度値をより正確に再現（適切なモニターを使用している場合）することが出来ます。XYZ⇔L\*a\*b\*変換では殆どデータ損失はありません（二重変換による損失は微々たるものです）ので、ある種の可逆圧縮とも言えるでしょう。もちろん、完全なHDR処理を目指すのであれば、モニターにデータが転送される前のデータの処理の方法を確実なものにして、ハイライト部分の処理の向上を図る必要があります。この点において、RawTherapeeにとって望ましいアプローチは、L\*a\*b\*の代わりにHDR‐L\*a\*b\*を使うことでしょう。しかし、それまでは、幾つかの機能（ウェーブレット、トーンマッピング、など）で、線形にするためにL\*a\*b\*のガンマ（3.0）を変更出来るようにしました。留意点として、RawTherapeは、彩度（特にオレンジとパープルの彩度）が変化した際に色相が保持されないというL\*a\*b\*の欠点の一つを、“均一的な知覚のLab”（UP
Lab）を使って克服していることが挙げられます。これには、偽色を抑えるための色域調整と同様、一連のマンセル補正のためのLUT（ルックアップテーブル）使用も関係します。

#### Ev25のHDR画像を例にして、L\*a\*b\*が色域やダイナミックレンジに影響を与えないことを示す

　2024年現在、主なデジタルカメラのダイナミックレンジは最大約15Evです。従って、この画像は特別なものですが、ハイダイナミックレンジ画像に関するL\*a\*b\*の動作を示しています。

TIF ファイルのリンク (Creative Common Attribution-share Alike 4.0):
[1](https://drive.google.com/file/d/1vAzFY7Qh8MdJ882J_4JeO_cnpGELzD8D/view?usp=sharing)

##### 元画像 - 25Ev – 未処理

注目点：

- 　シャドウ部分の詳細が不足しています。
- 　画像の約40％は100％ホワイトです。
- 　復元されたダイナミックレンジは概ね12Evから13Evです。

<figure>
<img src="/images/sweep-rgb-neutral.jpg" title="sweep-rgb-neutral.jpg"
width="600" />
<figcaption>sweep-rgb-neutral.jpg</figcaption>
</figure>

##### ローカル編集の対数符号化を使って補整した画像

注目点：

- 　シャドウ部分とハイライト部分がL＝1からL＝99.8までの可視領域全体を占めています（尺度0～100）。
- 　輝度に応じて色が均等に配分されています。つまり、このL\*a\*b\*機能はダイナミックレンジに影響しないことが分かります。
- 　復元されたブラック、ホワイト、及び色のダイナミックレンジは25Evです。

注意："ホワイトの配分"は90を使っています。

<figure>
<img src="/images/sweep-rgb-log.jpg" title="sweep-rgb-log.jpg" width="600" />
<figcaption>sweep-rgb-log.jpg</figcaption>
</figure>

#### 色の見えモデル02/16

　色の見えモデル02はハイダイナミックレンジと色域の広い画像が処理できない、とよく言われます。このことは部分的には正しい評価です。RawTherapeeの開発チームは数年前からこの問題に取り組み、問題の軽減を図ってきました（但し、多くのユーザーの画像はsRGBの色域に収まるので問題にはならないことをお忘れなく）。最近更に、〈対数符号化〉にCAM16、或いは色の見え（CAM16＆JzCzHz）を組み合わせたことで、この問題は殆ど解決したと言えます。もちろん、ハイライト復元機能の問題を含め、幾つか問題は残っています。しかし、これは何も色の見えモデルだけに限られた問題ではありません。

　その一方、色の見えモデル02は人間の視覚と周囲環境を考慮して正確に測色を行うモデルの一つです。例えば、画像の明るさや彩度を変える際に、色の見えモデルは画像とそれを見る周囲の環境も考慮します。

#### ホワイトバランス

　画像のホワイトバランスもよく論議される話題ですが、RawTherapeeは“Itcwb”（色温度との相関関係）を導入することで、数学的にほぼ完璧なホワイトバランスを作れるようになりました。このアルゴリズムは既知のスペクトルデータと適合する画像のXYZ表色系の色を作ります。但し、色温度がD50のそれとは大きく外れている画像に関しては、人間の視覚特性ほど色順応が出来ないため、測色が不正確になります。色の見えモデルはそれを考慮することが出来ます。

### 線形RGBモデルと測色の重要性

　RGBモデル（特に線形RGB）が評価される理由はその線形性です。線形であることは、画像のアップストリーム処理（デモザイク、ホワイトバランス、デフリンジ、色収差補正など）において非常に有利です。処理が可能な種類のものであれば、このモードを使うべきでしょう。

　しかし、L\*a\*b\*も色の見えモデル02/16も欠点はあるものの必要です。これまで理解してきたように、両方の色空間は、CIEのXYZ3刺激値から導き出されたもので、色の見えモデルは測色の補正が出来る唯一の方法だからです。

　しかし、トーンカーブの調整はどうでしょう？：

- 　調整が非線形であると言うだけでなく、測色の補間にも限界があります（色の見えモデルを使う知覚モードを除く）。このことは、出力（モニター、TIF。。。）で使われるトーンリプロダクションカーブ（TRC）とは対照的です。
- 　処理プロファイルの中にある〈Auto Matched Tone
  Curve〉はカメラに備わっているトーンリプロダクションカーブをコピーしたもので、中間処理で使用されますが、やはり線形ではありません。

　では、彩度に関してはどうでしょう？

　画像の彩度を変える場合に、RGBの線形性を保つのは不可能ではないかもしれませんが、非常に困難で、RawTherapeeではそう言った処置は行われません。しかし、色の見えモデルは、この色の変化に順応するために、明度（或いは明るさ）の変化も考慮します。

　結論として、RGB、L\*a\*b\*、及び色の見えモデルは、どれも長所と欠点を持っています。これらが適切に使われるよう、それぞれに対する理解が必要です。
