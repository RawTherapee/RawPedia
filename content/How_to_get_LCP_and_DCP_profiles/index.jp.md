---
title: How to get LCP and DCP profiles
contributors:
  - Yz2house
tags:
  - 'General Photography'
---

<div class="pagetitle">

LCPとDCPプロファイルを取得する方法

</div>

　Adobe DNG Converterには、LCP（Adobe Lens Correction
Profiles－レンズの歪曲収差、周辺光量不足、色収差を補正するプロファイル）とDCP（DNG
Color
Profiles－カメラの入力カラープロファイル）の豊富なコレクションが含まれています。

__FORCETOC__

　この項では、Adobe DNG
Converterのインストール手順、DCPとLCPプロファイルを捜す手順を説明します。

## Adobe DNG ConverterをLinuxにインストールする

　では、`$HOME/wine-dng`を Wine prefixとして使った手順を示します。

- 貴方のカメラの**LCP**プロファイルを以下で探します:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/LensProfiles/1.0/"

- 標準的な**DCP**プロファイルを以下で探します:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Adobe Standard"

- カメラ‘スタイル’の**DCP**プロファイル (人物、風景、鮮やか、など)
  は以下で探します:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Camera/"

簡単にアクセスが出来るよう、必要なプロファイルを別なフォルダー、例えば`~/profiles/`にコピーします。

## Windowsの場合

1.  [Adobe DNG
    ConverterのWindows版](http://suportdownloads.adobe.com/product.jsp?product=106&platform/=Windows)をダウンロードします。
2.  Adobe DNG Converterをインストールします：

- 貴方のカメラの**LCP**プロファイルを以下で探します:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\LensProfiles\1.0"

- 標準的な**DCP**プロファイルを以下で探します:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Adobe Standard

- カメラ‘スタイル’の**DCP**プロファイル (人物、風景、鮮やか、など)
  は以下で探します:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Camera

　簡単にアクセスが出来るよう、必要なプロファイルを別なフォルダーにコピーします。

## コミュニティメイド

　ミュニティの一人、[TooWaBoo](http://discuss.pixls.us/u/toowaboo)がSamyang
8mmレンズの歪みを補正するLCPを2つ手作りしました。ニコン、ペンタックス、ソニーのセンサーサイズがAPS-Cのカメラに利用出来ます。キャノン製のカメラでは調整がかもしれません。

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Panini.lcp"
  title="File:Samyang 8mm APS-C Panini.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Panini.lcp</figcaption>
  </figure>

  
このLCPの場合は、歪曲収差を0に、オートフィルは無効にします。

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Rectilinear.lcp"
  title="File:Samyang 8mm APS-C Rectilinear.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Rectilinear.lcp</figcaption>
  </figure>

  
このLCPの場合は、歪曲収差を0.5に、オートフィルは無効にします。
