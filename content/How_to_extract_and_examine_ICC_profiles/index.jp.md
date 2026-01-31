---
title: How to extract and examine ICC profiles
contributors:
  - Yz2house
tags:
  - 'General Photography'
---

<div class="pagetitle">

ICCプロファイルの抽出と査定の方法

</div>

## DisplayCAL

プロジェクト名:DisplayCAL  
ウェブサイト:<https://displaycal.net/>  

　Linux、macOS、Windowsの何れも、ユーザーインターフェイスから行います。
DisplayCALはArgyllCMSを使っており、トーンカーブや色空間、色域を含む、ICCプロファイルの詳細を表示することが出来ます。また、これらを画像や3D
HTML/VRML/X3Dとして書き出し、ウェブブラウザでシェアしたり閲覧したりすることも出来ます。

## ArgyllCMS

プロジェクト名:ArgyllCMS  
ウェブサイト:<https://www.argyllcms.com/>  
ドキュメンテーション (ICCプロファイルの打ち出し):<https://www.argyllcms.com/doc/iccdump.html>  
ドキュメンテーション (ICCプロファイルの抽出):<https://www.argyllcms.com/doc/extracticc.html>  

　Linux、macOS、Windowsの何れも、コマンドラインから行います。
　ArgyllCMSは画像ファイルからICCプロファイルを抽出し、ICCプロファイルの中身を人が読めるテキストに打ち出すことが出来ます。

- 抽出: `extracticc photo.jpg profile.icc`
- 画像で直接的に査定する: `argyll-iccdump -s photo.jpg`
- ICC fileを査定する: `argyll-iccdump profile.icc`

## ICC Examin

プロジェクト名:Oyranos  
ウェブサイト:<http://www.oyranos.org/icc-examin/>  

　Linux、macOS、Windowsの何れも、ユーザーインターフェイスから行います。
　ICC ExaminはICCプロファイルの詳細を3D空間で見たりすることも出来ます。

## colord

プロジェクト名:colord  
ウェブサイト:<https://www.freedesktop.org/software/colord/>  

　Linuxで使用、システムサービスやユーザーインターフェイスから行います。
　colordはICCプロファイルの詳細を表示できます。

## ExifTool

プロジェクト名:ExifTool  
ウェブサイト:<http://www.sno.phy.queensu.ca/~phil/exiftool/>  

　Linux、macOS、Windowsの何れも、コマンドラインから行います。
　ExifToolは、画像に埋め込まれたICCプロファイル、独立したICCプロファイルのどちらでも査定が出来ます。また、画像からICCプロファイルを抽出して他の画像に埋め込むことも出来ます。

- 抽出: `exiftool -icc_profile -b -w icc photo.jpg`
- 埋め込み: `exiftool "-icc_profile<=profile.icc" photo.jpg`
- 埋め込まれたICCプロファイルを査定: `exiftool -icc_profile:* photo.jpg`
- 独立したICCプロファイルを査定: `exiftool profile.icc`

## GIMP

プロジェクト名:GIMP  
ウェブサイト:<https://www.gimp.org/>  

　Linux、macOS、Windowsの何れも、ユーザーインターフェイスから行います。

- 抽出: GIMP 2.9で画像を開き,
  画像をクリックして、カラーマネジメント→カラープロファイルをファイルに保存と選択。

## ImageMagick

プロジェクト名:ImageMagick  
ウェブサイト:<https://www.imagemagick.org/script/index.php>  

　Linux、macOS、Windowsの何れも、コマンドラインから行います。

- 抽出: `convert photo.jpg profile.icc`

## iccToXml

プロジェクト名:IccXML  
ウェブサイト:<https://sourceforge.net/projects/iccxml/>  

　LinuxとWindowsで、コマンドラインから行います。廃れたプロジェクトです。
　iccToXmlはIccXMLプロジェクトの一部です。これを使ってICCプロファイルを人が読めるXMLに転換できます。

　転換: `iccToXml profile.icc profile.xml`

## ICC Profile Inspector

プロジェクト名:ICC Profile Inspector  
ウェブサイト:<http://www.color.org/profileinspector.xalter>  

　Windows（wineの使用が必要）でユーザーインターフェイスから行います。廃れたプロジェクトです。
