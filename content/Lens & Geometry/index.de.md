---
title: Lens Geometry
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Transform Tab'
---

Todo: übersetzen

Seite angelegt und Überschrift übersetzt, um sie zu refernzieren

[fherb](user:fherb) ([talk](user_talk:fherb))
12.3.2017

------------------------------------------------------------------------

# Linsen- und Geometriekorrektur

To keep the preview fast, RawTherapee uses the preview image of the
current zoom level when applying these transformations. Because of this,
the preview image can become soft. Lets assume you are editing a Nikon
D700 image: 4256×2832px (that's 12.1 megapixels), and the preview
image's size is 600x400px. Rotating it 5° will not be the same as
rotating the full 12.1Mp image and then scaling it down to 600x400px.
The former will be softer than the latter, though rotating the former
will take less time than rotating the latter, which is why RawTherapee
does that. But don't worry, when saving the image RawTherapee uses the
full resolution image, so it will be sharp. If you zoom the preview in,
then RawTherapee will use this higher resolution preview image when
calculating the transformation, so to see what the saved file will look
like, just zoom in to 100%
[image:Gtk-zoom-100.png](image:gtk-zoom-100.png).

## Auto-Fill

<img src="/images/Lensgeometry_bluehorse_barrel_distortion_correction.jpg"
title="Lensgeometry_bluehorse_barrel_distortion_correction.jpg"
width="900"
alt="Lensgeometry_bluehorse_barrel_distortion_correction.jpg" /> <img
src="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg"
title="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg"
width="900"
alt="Lensgeometry_bluehorse_barrel_distortion_correction_autofill.jpg" />
This option will upscale or downscale the photo to the extent that the
whole image fits within the image boundaries with no black borders
visible.

When correcting images that suffer from [barrel
distortion](https://en.wikipedia.org/wiki/Distortion_(optics)),
"Auto-fill" will perform downscaling to fit as much of the re-projected
image as possible into the image boundaries, so that you don't
unnecessarily lose any parts of the image. Conversely if the image
suffers from pincushion distortion, "Auto-Fill" will upscale the
corrected image to fill the frame without black borders around the
periphery.

  
== Auto-Crop == <img
src="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg"
title="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg"
width="900"
alt="Lensgeometry_bluehorse_autocrop_after_distortion_correction.jpg" />
<img src="/images/Lensgeometry_bluehorse_autocrop_after_rotation.jpg"
title="Lensgeometry_bluehorse_autocrop_after_rotation.jpg" width="900"
alt="Lensgeometry_bluehorse_autocrop_after_rotation.jpg" />
"[image:Crop-auto.png](image:crop-auto.png) Auto-Crop" is
available when "Auto-fill" is disabled. When activated, it will not
cause image interpolation, but instead will crop away the empty space
left by the distortion correction or image rotation.

  
== Rotate == [900px](image:rotate.jpg) Rotate the image
between -45° and +45°. Use the
"[image:Straighten.png](image:straighten.png) Select Straight
Line" button to set either a vertical or a horizontal image alignment.
Use the mouse to draw this line - click and hold mouse to start, move to
draw a new vertical or horizontal axis and release to engage image
rotation.

  
== Perspective ==
<img src="/images/perspective_horizontal.jpg" title="perspective_horizontal.jpg"
width="900" alt="perspective_horizontal.jpg" />
<img src="/images/perspective_vertical.jpg" title="perspective_vertical.jpg"
width="900" alt="perspective_vertical.jpg" />

Horizontal  
When your picture was taken while you were slightly off-center of the
object, you can correct this (within certain limits) with the horizontal
slider.

Vertical  
Very useful to correct 'falling lines', e.g. when photographing
architecture. Higher values for both sliders produce heavy distortion,
so use with care. Or don't care at all and have fun!

  
== Lens Correction Profile == Adobe provides and offers tools to create
and share what are called Lens Correction Profiles. These are text files
which describe the distortion, vignetting and chromatic aberrations (CA)
of a lens, so that simply loading this file in LCP-capable software such
as RawTherapee will correct these issues. Select an [Adobe
LCP](http://www.adobe.com/products/photoshop/extend.displayTab2.html#resources)
file (read the guide on [how to get LCP
profiles](How_to_get_LCP_and_DCP_profiles.md)) to automatically
correct geometric distortion, vignetting and lateral chromatic
aberrations.

The Lens Correction Profile tool's distortion correction feature can be
used together with the manual [Distortion
Correction](Lens/Geometry#Distortion_Correction.md) tool, and
the vignetting correction feature can be used together with the manual
[Vignetting Correction](lens/geometry#vignetting_correction)
tool. This lets you use the manual controls in addition to the LCP
profile for artistic reasons or if the LCP fails to sufficiently correct
a parameter (which happens on some extreme distortion occasions, like
with some heavily distorting compact cameras). Be careful that you don't
overdo the distortion and vignetting correction by forgetting to turn
the manual tools off if you use the LCP equivalents. The vignetting
correction feature however is linked to the [Flat
Field](Flat_Field.md) tool, so that when you select a flat-field
image then the LCP's vignetting correction will have no effect.

The following restrictions apply:

- Distortion, vignetting and chromatic aberration correction are all
  supported in raw files, but only distortion correction is supported in
  non-raw files.
- While distortion correction is visible in the full image preview,
  chromatic aberration and distortion correction are not reflected in
  the detail crop windows, only in the fully processed result image.
  Auto-filling is also not supported.
- Chromatic aberration correction is only supported if the Exif
  information contains the focus distance (e.g. in DNGs from Nikon
  files).
- Auto-Fill is disabled when an LCP with distortion correction is
  enabled, otherwise the preview may become distorted - see [bug
  1791](https://github.com/Beep6581/RawTherapee/issues/1791).
- To keep the preview fast and responsive, the main preview image is
  used to show the effects of the LCP. As this image is small (exactly
  the size you see), fixing the distortions will make it appear a little
  blurry. This has no effect on your saved image, which will be sharp,
  and so will the zoomed-to-100% preview. Only the zoomed-out preview
  that will look soft. See [feature request
  2186](https://code.google.com/p/rawtherapee/issues/detail?id=2186).

As with any other tool, you can apply an LCP to multiple images either
by including it in the processing profile (see [Creating processing
profiles for general
use](Creating_processing_profiles_for_general_use.md)), or by
selecting multiple images where the same lens was used (you can use the
Metadata Filter in the File Browser tab to make this easier) and
applying the LCP from the File Browser tab.

Raw images from bridge-type cameras often show very strong vignetting in
the corners, and strong distortion, while the JPEG images do not show
this. The way these cameras deal with the vignetting problem is by
fixing the distortion which pushes the corners further out beyond the
image borders. They are then simply cropped off. Do not expect to fix
this strong corner vignetting problem seen in bridge-type cameras by
using LCP profiles - often the corners do not contain any actual image
data, just the blurred, dark corners of your lens hood. Do as the camera
does, and eliminate vignetting by fixing the distortion which will push
the vignetting out of view. Make sure *Auto-fill* is enabled, so that
the parts which get pushed out of view remain discarded.

  

## Distortion Correction

[framed](image:rt_distortion_correction.png) Corrects lens
distortion. A negative number corrects barrel distortion, a positive
value will correct pincushion distortion. You can place a grid over the
image by activating [Crop](crop) (without cropping) and using
"*Guide Type \> Grid*". This may serve as a guide to correct lens
distortion.

The "*Automatic*" button only works if your camera corrected the
distortion of the JPEG image embedded in the raw file (most cameras
embed a JPEG image in every raw file, and some cameras correct the
distortion of that image too). What this feature does is it looks at the
JPEG image and, if it was corrected, tries to fix distortion in the raw
image by making it match the JPEG image. There are two limitations:

- If the JPEG image was not distortion-corrected by your camera, this
  button will have no effect.
- If the JPEG image is insufficiently corrected or over-corrected, so
  will the results be, but as the computed correction will be shown on
  the *Amount* slider, you can further refine it manually.

  

## Chromatic Aberration Correction

<img src="/images/chromatic_aberration_auto1.jpg"
title="chromatic_aberration_auto1.jpg" width="900"
alt="chromatic_aberration_auto1.jpg" />
<img src="/images/chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" width="900"
alt="chromatic_aberration_auto2.jpg" /> This "Chromatic Aberration
Correction" tool in the *Transform* tab works on the image **after**
demosaicing. The [Chromatic Aberration](chromatic_aberration)
tool in the *Raw* tab works on the image **before** demosaicing.

Chromatic aberration can be corrected by using the "Red" and "Blue"
sliders. Normally you won't see any chromatic aberration in the
fit-to-screen preview, therefore it is highly recommended to open a
detail window
[image:New-detail-window.png](image:new-detail-window.png) or
to zoom the main preview in to 100%
[image:Gtk-zoom-100.png](image:gtk-zoom-100.png) or more when
you attempt this kind of correction. As in other software tools, this
algorithm eliminates moderate chromatic aberration quite well. Do not
expect miracles with images having extremely high chromatic aberration -
garbage in, garbage out.

  
== Vignetting Correction == Vignetting means light fall-off in the
corners of the image, making them darker than the center. One of the
differences between a cheap telephoto lens and an expensive one is that
the former is likely to produce vignetting, while the latter will not
(or less). The "Vignetting Correction" tool is meant to correct
vignetting caused by the lens, regardless of the
[Crop](crop). This tool is not intended for artistic
vignetting; use the [Vignetting Filter](vignetting_filter)
tool for that.

Amount  
Setting the "Amount" slider to a positive value brightens the four edges
of the images to correct the classical vignetting. Setting it to a
negative value darkens them.

Radius  
Influences how much of the image beginning from the edges will be
brightened or darkened. Lower values: area of darkening is bigger;
higher values: area of darkening is smaller.

Strength  
Amplifies the settings of the "Amount" and "Radius" sliders. Set
"Amount" to -100, "Radius" to 50 and move "Strength" from 1 to 100 to
see how this works.
