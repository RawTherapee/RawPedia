---
title: How to get LCP and DCP profiles
contributors:
  - Fherb
tags:
  - 'General Photography'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Wie werden LCP- und DCP-Profile erstellt?

Adobe's Lens Correction Profiles (LCP, for correcting distortion,
vignetting and chromatic aberration) and DNG Color Profiles (DCP, input
color profiles) come bundled with [Adobe DNG
Converter](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Windows).
You can also get LCP profiles with [Adobe Lens Profile
Downloader](http://www.adobe.com/products/photoshop/extend.displayTab2.html#resources),
or easily [make your own using Adobe Lens Profile
Creator](#Make_your_own_using_Adobe_Lens_Profile_Creator.md) by
following the steps below.

## Linux

This short guide will assume you used ~/wine-dng/ as your WINEPREFIX.
The default WINEPREFIX is ~/.wine/ but it is more robust to use a custom
and non-hidden one. For more information, see the last paragraph titled
"For your information - wine prefix" on the [How to convert raw formats
to DNG](How_to_convert_raw_formats_to_DNG.md) page.

### From Adobe DNG Converter

A large collection of DCP and LCP profiles come bundled with Adobe DNG
Converter.

1.  Follow the steps in the [Linux section of the "How to convert raw
    formats to DNG"
    article](How_to_convert_raw_formats_to_DNG#Linux.md) to
    install [Adobe DNG
    Converter](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Windows)
    in Linux.
2.  Find generic **LCP** profiles for your camera under:
      
        "$HOME/wine-dng/drive_c/users/Public/Application Data/Adobe/CameraRaw/LensProfiles/1.0/"

        "$HOME/wine-dng/drive_c/users/Public/Application Data/Adobe/CameraRaw/LensProfiles/1.0/"

    or generic **DCP** profiles under:

        "$HOME/wine-dng/drive_c/users/Public/Application Data/Adobe/CameraRaw/CameraProfiles/Adobe Standard/"

    or try the 'effect' DCP profiles (landscape, portrait, etc) under:

        "$HOME/wine-dng/drive_c/users/Public/Application Data/Adobe/CameraRaw/CameraProfiles/Camera/"
3.  Copy the relevant profiles to a different folder for easy access,
    for example to `~/profiles/`

### From Adobe Lens Profile Downloader

You could also use Adobe's Lens Profile Downloader. For the exact code
how to install it, refer to the [Linux section of the "How to convert
raw formats to DNG"
article](How_to_convert_raw_formats_to_DNG#Linux.md).

1.  Install [wine](http://www.winehq.org/)
2.  Install Adobe Air. The latest version that works is 1.5.3, do not
    update to a newer one!
    <http://airdownload.adobe.com/air/win/download/1.5.3/AdobeAIRInstaller.exe>
3.  Download the Lens Profile Downloader:
    <http://www.adobe.com/support/downloads/detail.jsp?ftpID=5492>
4.  Run the Lens Profile Downloader in Adobe Air.
      
        WINEPREFIX=$HOME/wine-dng wine "$HOME/wine-dng/drive_c/Program Files (x86)/Common Files/Adobe AIR/Versions/1.0/Adobe AIR Application Installer.exe"

    If Air asks you to update, don't. Then open the
    Adobe_Lens_Profile_Downloader_1_0_1.air file from it. I installed it
    to `c:\alpd`
5.  Run the Adobe Lens Profile Downloader to get the profiles you want:
      
        WINEPREFIX=$HOME/wine-dng wine "$HOME/.wine/drive_c/alpd/Adobe Lens Profile Downloader/Adobe Lens Profile Downloader.exe"
6.  The profiles you have downloaded via the Lens Profile Downloader can
    be found here, cunningly renamed to a hash to make your life more
    difficult:
      
        "$HOME/wine-dng/drive_c/users/YOU/Application Data/Adobe/CameraRaw/LensProfiles/1.0/Downloaded/"

### Make your own using Adobe Lens Profile Creator

It is very easy to make your own LCPs, all you really need is to print a
page.

1.  Install Adobe Lens Profile Creator
      
    <https://www.adobe.com/support/downloads/product.jsp?product=193&platform=Windows>

    Follow the instructions above to install it in Linux using
    [wine](http://www.winehq.org/).
2.  Read the friendly manual to learn how to make high quality LCPs
      
    <http://www.adobe.com/special/photoshop/camera_raw/lensprofile_creator/lensprofile_creator_userguide.pdf>

## Windows

### From Adobe DNG Converter

1.  Install the latest [Adobe DNG
    Converter](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Windows)
2.  Find **LCP** profiles for your camera under:
      
    `%ALLUSERSPROFILE%\Adobe\CameraRaw\LensProfiles\1.0`

    or generic **DCP** profiles under:

    `%ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Adobe Standard\`

    or try the 'effect' **DCP** profiles (landscape, portrait, etc)
    under:

    `%ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Camera\`
3.  Copy the relevant profiles to a different folder for easy access.

### From Adobe Lens Profile Downloader

1.  Install the latest [Adobe Lens Profile
    Downloader](http://www.adobe.com/support/downloads/detail.jsp?ftpID=5492).
2.  Run the Adobe Lens Profile Downloader to get the profiles you want.
3.  The profiles you have downloaded via the Lens Profile Downloader can
    be found here, cunningly renamed to a hash to make your life more
    difficult:
      
    `%APPDATA%\Adobe\CameraRaw\LensProfiles\1.0\Downloaded\`
4.  Copy the relevant profiles to a different folder for easy access.

### Make your own using Adobe Lens Profile Creator

It is very easy to make your own LCPs, all you really need is to print a
page.

1.  Install Adobe Lens Profile Creator
      
    <https://www.adobe.com/support/downloads/product.jsp?product=193&platform=Windows>
2.  Read the friendly manual to learn how to make high quality LCPs
      
    <http://www.adobe.com/special/photoshop/camera_raw/lensprofile_creator/lensprofile_creator_userguide.pdf>

## Download

[TooWaBoo](https://discuss.pixls.us/users/toowaboo)
[made](http://rawtherapee.com/oldforum/viewtopic.php?p=44462#p44462) two
LCPs by hand for de-fishing the Samyang 8mm lens, tailored to the APS-C
sensor size used by Nikon, Pentax and Sony. Might need tweaking for
Canon.

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Panini.lcp"
  title="File:Samyang 8mm APS-C Panini.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Panini.lcp</figcaption>
  </figure>

  
Set Distortion Correction = 0, Auto-fill = unchecked

- <figure>
  <img src="/images/Samyang_8mm_APS-C_Rectilinear.lcp"
  title="File:Samyang 8mm APS-C Rectilinear.lcp" />
  <figcaption><a href="File:Samyang">File:Samyang</a> 8mm APS-C
  Rectilinear.lcp</figcaption>
  </figure>

  
Set Distortion Correction = -0.5, Auto-fill = unchecked
