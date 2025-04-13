---
title: How to get LCP and DCP profiles
contributors:
  - DrSlony
  - Patdavid
  - XavAL
---

<div class="pagetitle">

How to Get LCP and DCP profiles

</div>

A large collection of LCP (Adobe Lens Correction Profiles - for
correcting lens distortion, vignetting and chromatic aberration) and DCP
(DNG Color Profiles - camera input color profiles) come bundled with
[Adobe DNG
Converter](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows).

This section explains how to install Adobe DNG Converter and where to
find the DCP and LCP profiles.

__FORCETOC__

## Linux

We will be using `$HOME/wine-dng` as the Wine prefix.

- Find **LCP** profiles for your camera under:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/LensProfiles/1.0/"

- Find standard **DCP** profiles under:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Adobe Standard"

- Find camera 'style' **DCP** profiles (portrait, landscape, vivid, etc)
  under:

  
    "$HOME/wine-dng/drive_c/ProgramData/Adobe/CameraRaw/CameraProfiles/Camera/"

Copy the relevant profiles to a different folder for easy access, for
example to `~/profiles/`

## Windows

1.  [Download Adobe DNG Converter for
    Windows](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows).
2.  Install Adobe DNG Converter

- Find **LCP** profiles for your camera under:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\LensProfiles\1.0"

- Find standard **DCP** profiles under:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Adobe Standard

- Find camera 'style' **DCP** profiles (portrait, landscape, vivid, etc)
  under:

  
    %ALLUSERSPROFILE%\Adobe\CameraRaw\CameraProfiles\Camera

Copy the relevant profiles to a different folder for easy access.

## Community-Made

[TooWaBoo](https://discuss.pixls.us/u/toowaboo) made two LCPs by hand
for de-fishing the Samyang 8mm lens, tailored to the APS-C sensor size
used by Nikon, Pentax and Sony. Might need tweaking for Canon.

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
