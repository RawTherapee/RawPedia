---
title: Color Management
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Color Tab'
---

Todo: übersetzen

Seite angelegt, um darauf refernzieren zu können

fherb
12.3.2017

------------------------------------------------------------------------

# Farbmanagement

## Eingangsfarbprofil

### Kein Profil

No input color profile will be applied. The color matrix will use "1"
along the diagonal and "0" everywhere else.

- Raw files will show the camera's native RGB color. They will only be
  demosaiced and white-balanced.
- Non-raw files will be displayed without any embedded input profile
  applied, including no gamma correction, which means they will look
  bright.

This feature is generally only useful for didactic and scientific
purposes. For example if the camera has recorded colors far outside of
the conventional gamuts, using no input profile ensures that no color
clipping occurs.

### Camera Standard

Looks for and uses a color matrix from the DNG file, from camconst.json,
hard-coded in RawTherapee, or from
[dcraw](https://en.wikipedia.org/wiki/Dcraw), whichever one it finds
first, in that order.

A *color matrix* is a matrix of 3x3 constant values which is multiplied
with the camera's native RGB colors to convert them to colors which are
as natural as possible. A color matrix works best (i.e. provides more
accurate colors) when the white balance is close to what the matrix was
calibrated for. The camera standard matrix is calibrated for
[D65](https://en.wikipedia.org/wiki/Illuminant_D65), i.e. 6500K. Do not
worry if the white balance is quite far off from that though, color will
be reasonably accurate anyway.

For applications where the most accurate and fine-tuned color is not of
highest importance, such as landscape photography, the color matrix will
provide good colors. An advantage of color matrix processing compared to
lookup table-based DCP and ICC conversions is that it's purely linear,
i.e. a dark and a bright color of the same hue and saturation is
translated the same way. This makes it robust and may be the best choice
if you will be exporting images for processing in an HDR application or
other application when a predictable linear color response is important.

### Auto-Matched Camera Profile

Uses RawTherapee's camera-specific DCP input profile that can provide
more accurate colors than the standard matrix (and fall back to legacy
ICC profiles if no DCP is available). Available for some cameras, these
profiles are stored in the /dcpprofiles directory (or legacy
/iccprofiles/input) and are automatically retrieved based on matching
the exact make and model of the camera as it appears in the info section
in the Editor to the filename, e.g. "Canon EOS 5D Mark III.dcp".

In other words, if "*Auto-matched camera profile*" is selected,
RawTherapee will try to do the following, in this order:

1.  locate a DCP profile in /dcpprofiles
2.  if DCP is not found, locate an ICC profile in /iccprofiles
3.  if DCP and ICC are not found, revert to the camera standard color
    matrix.

If you want to contribute a camera profile, DCP is the preferred format.

Some of RawTherapee's profiles are single-illuminant (Daylight/D50),
while others are double-illuminant (Daylight/D50 and Tungsten/StdA).
Some include a tone curve, others do not. They strive for accurate
colors (i.e. not a specific "look"). Most accurate colors will be
achieved for white balances close to the calibration illuminants.

Camera profiles work in the normal range, from black up to clipping. If
you enable highlight reconstruction, new data is added above the
clipping level and if you bring it into visible space (by negative
exposure for example), that range will not be naturally covered by the
profile. However, RawTherapee will linearly extend the profile to cover
this range too, colors there will get the same correction as the
brightest colors of the same hue and saturation in the normal range.

### Custom

Specify a custom DNG Profile (DCP) or ICC camera input profile stored on
your computer.

DCP is a format specially designed for camera profiles and RawTherapee
should support the most recent DNG standard (where DCP is defined), so
you can for example use all those provided via Adobe's DNG converter.

ICC profiles on the other hand are more tricky. ICC profiles can be used
for a multitude of purposes (printers, displays etc) and since they're
not designed specifically for camera profiling, different vendors have
chosen different approaches for their ICC profiles. In practice this
means that the input image must be pre-processed in some specific way
for the profile to work. The profile itself lacks information of how to
do this pre-processing, which means that if you are using a third-party
profile RawTherapee may not do the expected pre-processing; results will
vary.

#### Third-party DCP support

A DNG Camera Profile, DCP, is the preferred camera profile format for
RawTherapee. All elements of the 1.4 DNG specification is supported,
with the exception of the black render tag (see below). A DCP can be a
pure matrix profile, it can have a LUT (typically 2.5D) to improve the
colorimetric accuracy, and then it can have an embedded curve and a
separate "look table" on top. It may also add an exposure offset. All
those elements can be toggled via checkboxes. However, although it is
possible few third-party profiles have been designed to produced the
intended color with anything else than all their elements enabled. For
example, the tone curve itself changes color appearance so if you
disable an embedded tone curve to get a linear profile you can't count
on that the color is as intended.

The typical third party profile would come from Adobe Camera Raw /
Lightroom, and RawTherapee supports them. Many of Adobe's profile lack
tone curve, but in Adobe's world that does not mean that no tone curve
should be applied but that Adobe's default curve should be applied.
RawTherapee will therefore identify Adobe profiles (from the copyright
string) and add the default curve to those (which you can toggle with
the tone curve checkbox).

Adobe's DNG converter may add a "baseline exposure" to the DNG file.
Adobe's DCP are designed to work with that baseline exposure and then
produce a default output which is about the same brightness and contrast
as the camera's own JPEGs. RawTherapee can honor this baseline exposure
(NOT YET IMPLEMENTED), but this is of course only available when opening
a DNG file converted by Adobe's DNG converter. If you instead open a
native raw file there will be no baseline exposure and Adobe's DCP may
then make a too bright or dark rendering. You can simply adjust with the
exposure slider of course.

The DCP format also has a black render tag. This indicates if the raw
converter should do "automatic" black subtraction or not. RawTherapee
ignores this tag, you can do manual black subtraction with the black
slider. As many of Adobe's profiles indicate auto black subtraction and
Adobe Camera Raw / Lightroom does it, RawTherapee will in comparison in
those cases render a bit lower contrast and brighter shadows.

#### Third-party ICC support

RawTherapee has specific support for ICC profiles bundled with Capture
One and Nikon NX2, so those should work well. Older ICC profiles are not
likely to work well though (typically the image becomes extremely dark
with unsupported ICC profiles).

Some ICC profiles apply a tone-curve and desaturate bright highlights
for a more "film-like" look. Those profiles may not work well together
with [Highlight
Reconstruction](Exposure#Highlight_Reconstruction.md). If you
see a radical change in contrast when you apply your ICC profile it has
applied a tone-curve and then you should not use it together with
[Highlight
Reconstruction](Exposure#Highlight_Reconstruction.md).

Unlike DCP profiles, ICC profile processing may cause clipping of
extremely saturated colors during conversion. In practice this is rarely
if ever a problem, but still DCP should be considered the primary choice
if available.

Note on using Capture One ICC profiles: RawTherapee applies the ICC
before exposure adjustments, as the intention is that camera profiles
should only be used to make the camera more accurate, not really to
apply a look (you design the look using the tools instead). Phase One's
ICC profiles contain a subjective look though, which means that they
typically contain "hue twists", for example saturation in the shadows
are increased a bit extra. This means that if you have an underexposed
file and push it a few stops those hue twists have been applied on the
dark image before exposure adjustment and will thus be in the wrong
places after pushing, that is you don't get the same look as in Phase
One's Capture One. Therefore it's recommended to have the right exposure
out of the camera when using Phase One ICC profiles. You should also
apply a suitable RGB "film curve" for example by using the curve tool,
as those ICC profiles are designed to be used together with that.

We are aware that LUT ICCs should typically be applied after exposure
(just as DCP Looktables are applied), and that would support for example
Capture One profiles better. This may be fixed in a future version.

### DCP Illuminant

Some of RawTherapee's profiles are single-illuminant (Daylight/D50),
while others are double-illuminant (Daylight/D50 and Tungsten/StdA). If
a dual-illuminant profile is loaded the "DCP Illuminant" setting will be
enabled and you can choose which illuminant to use. The actual DCP
standard (part of the DNG standard) does not provide this choice, but
instead an interpolation between the two illuminants is calculated based
on the chosen white balance (there will only be an interpolation if the
white balance is in-between both illuminants, otherwise the closest is
picked). This "interpolated" mode is the default setting of "DCP
Illuminant" and for any normal use you do not need to change this.

You can however choose to base the color rendering on one of the
specific illuminants. In some cases this might produce more pleasing
color. It can also be interesting for diagnostic purposes to see how
large (or small) a difference there is in color rendering between the
illuminants, but, as said, for general use this setting should be
untouched.

### Use DCP's Tone Curve

Some DCPs contain a tone curve which may be used to add contrast and
brightness to provide a film-like look. This is mainly used for profiles
simulating camera maker settings. The tone curve checkbox will be
disabled for profiles which do not contain a tone curve.

The curve mode used by the DCP tone curve is the same as the Exposure
tool's "[film-like](exposure#film-like)" mode, meaning you
can reproduce the effect using the Exposure tool's tone curves in
film-like mode. When contrast is applied with a film-like curve the
appearance of the colors will change and overall saturation is
increased, except for bright colors which instead are de-saturated. Some
profiles which have curves embedded are pre-corrected for this color
appearance change and will thus not provide the intended look without
the curve applied. Most will however work well without the tone curve
applied especially if you add a similar curve yourself using the
Exposure tool's curves, but if you want to see exactly how the profile
designer intended the colors to look you should enable the tone curve.

While the input color profile is applied at the first stages of the
[toolchain pipeline](toolchain_pipeline), the DCP tone curve
is applied later in the pipeline at some point after the Exposure tool.

### Use DCP's base table

This enables the DCP "HueSatMap" lookup table which is used to add
non-linear corrections on top of the basic matrix. This is an advanced
user setting and unless you want only the pure matrix result should
leave it on. It's grayed out if the loaded profile lacks a HueSatMap
table.

### Use DCP's look table

This enables the DCP "LookTable" lookup table which is intended to add a
subjective look on top generally together with an embedded tone curve.
That is if you disable the DCP curve and looktable you may get a neutral
"colorimetric" profile, if the DCP was designed that way which is not
always the case (if the DCP has both a look table and a base table it's
likely that it is, but if it only has a look table it will probably not
work well with it disabled). Disabling individual DCP elements are
considered advanced user settings, normally you would leave this on.

### Use DCP's baseline exposure offset

The DCP may indicate an exposure offset that corresponds to an offset of
the exposure slider. The purpose of this is typically to make the
brightness of the image match the brightness of the camera's own JPEGs,
which can be useful if you're shooting with auto-exposure. Currently
this offset is applied "under the surface" so you don't see it on the
exposure slider.

Note that if you are using Adobe's proprietary profiles those are
expecting that the DNG's "baseline exposure" tag is applied too (the
profile's offset is added on top). Currently there is no support for the
DNG tag so you need to find that out on your own (using exiftool for
example) and then set that offset using the exposure slider if you want
to get the exact same brightness as in Adobe Camera Raw.

### Save Reference Image for Profiling

Clicking this button saves a linear TIFF image before the input profile
is applied. This file can then be used for profiling, i.e. creating a
new ICC camera profile. There are various commercial software out there
to make ICC profiles, but you can also use the free and open-source
Argyll. For DNG profiles there is DCamProf as an open-source
alternative.

Cropping, resizing and transform (rotate) will be applied so you can use
that to make the output more managable by the receiving software. Argyll
is very picky for example and want no more than the test target visible
in the image.

You can also choose if you want to export with white balance applied or
not. For ICC profiles you should export with white balance applied, but
if you intend to make a DNG Profile ColorMatrix (or a DCRAW style color
matrix) you should export without.

## Working Profile

The default working profile is ProPhoto and should not be changed for
normal use.

The working profile specifies the working color space, which is the
color space used for internal calculations, for instance for calculating
saturation, RGB brightness/contrast and tone curve adjustments,
chrominance, etc.

When RawTherapee was based on integer math it was wise to not use a
larger working space than absolutely needed to get the best precision in
the calculations. However nowadays RawTherapee is floating point and
since version 4.0.12 the default working profile is ProPhoto (very large
gamut), and there's for normal use no reason to change this.

Some tone curve types will change results quite drastically for highly
saturated colors depending on working profile. If you have trouble
fitting colors within the output gamut you can experiment with changing
it.

Note that the working profile will only specify the red, green and blue
primaries, gamma will not change as RawTherapee's processing pipeline is
floating point with no gamma encoding (that is gamma = 1.0). Some tools
(like curves and histograms) will still display with a gamma (usually
sRGB gamma) which is hard-coded for the tool and stays the same
regardless of working profile.

## Ausgabeprofil

Specify the output color profile; the saved image will be transformed
into this color space and the profile will be embedded in the metadata.

RawTherapee 5 lets you only specify "display" device class profiles with
RGB color space, because RawTherapee can actually only save RGB images.
Profiles listed from this combo-box are the bundled one and those
located in the folder set in Preferences \> [Color
Management](Preferences#Color_Management_Tab.md).

The main histogram, navigator and clipping indicators will use either
the working or the output profile, depending on your setting in
Preference \> [General](preferences#general_tab).

RawTherapee comes bundled with a number of custom-made high quality
output profiles:

RT_sRGB  
Similar to sRGB

Gamma close to sRGB: g=2.40, slope=12.92

RT_sRGB_gBT709  
Similar to sRGB

Gamma BT709: g=2.22, slope=4.5

RT_sRGB_g10  
Similar to sRGB

Linear gamma g=1.0, slope=0

RT_Medium_gsRGB  
Similar to AdobeRGB1998

Gamma close to sRGB: g=2.40, slope=12.92

RT_Large_gsRGB  
Similar to ProPhoto

Gamma close to sRGB g=2.40, slope=12.92 (close to "Melissa" used by
Lightroom)

RT_Large_gBT709  
Similar to ProPhoto

Gamma BT709: g=2.22, slop=4.5

RT_Large_g10  
Similar to ProPhoto

Linear gamma g=1.0, slope=0

Rec2020  
Wide gamut, larger than AdobeRGB but smaller than ProPhoto

Gamma BT709: g=2.22, slope=4.5

The recommended output profile when you're saving to an 8-bit format
and/or publishing to the web is RT_sRGB. If no profile is selected, none
will be embedded, which means that "sRGB" is implied, though it is safer
to embed RT_sRGB in terms of getting your image displayed properly in
various applications.

RT_sRGB is a **higher quality** version of the standard sRGB profile,
which surprisingly is inconsistent between implementations. RT_sRGB was
custom-made for RawTherapee by Jacques Desmis and has 4096 LUT points,
as opposed to the lower quality 1024 point sRGB profiles. Applications
that aren't color managed and won't take advantage of RT_sRGB will fall
back on sRGB.

Wide-gamut output profiles such as RT_Large_gsRGB are generally used if
you export to a 16-bit or higher bit-depth format for further editing in
another application. If you will be sending your image for printing, a
wide-gamut output profile is also recommended, since some printers may
have wide gamuts (at least in certain colors).

You should have a wide-gamut monitor if you want to work with wide-gamut
profiles, otherwise you're flying in the dark.
