---
title: Noise Reduction
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

Todo: übersetzen

Seite schon angelegt und Überschrift übersetzt, um sie zu referenzieren.

fherb
12.3.2017

------------------------------------------------------------------------

# Rauschreduktion

<figure>
<img src="/images/noisereduction2.jpg" title="noisereduction2.jpg" />
<figcaption>noisereduction2.jpg</figcaption>
</figure>

Not everyone's requirement for good noise reduction is the same. Some
like a completely clean, smooth result, while others prefer to have some
grain left over to give the photo a more film-like quality.
RawTherapee's powerful *Noise Reduction* tool caters to all your needs -
it lets you eliminate noise while retaining detail. It uses
[wavelets](http://en.wikipedia.org/wiki/Wavelet), a [Fourier
transform](https://en.wikipedia.org/wiki/Fourier_transform) and a
[median filter](https://en.wikipedia.org/wiki/Median_filter) to work its
magic. Read on to learn how to use it efficiently.

## Usage

When working with very noisy, high ISO images, it is recommended to use
the LMMSE or IGV demosaicing methods. They will prevent false maze
patterns from appearing, and prevent the image from looking washed-out
due to heavy noise reduction.

To find the best set of Noise Reduction values for your image:

1.  Check the sharpening tools to make sure that you're not sharpening
    any fine detail, because your noisy photo has no fine detail! All
    they would do is amplify the noise. If you're using *Contrast by
    Detail Levels* to give the image more depth, make sure that the
    first "*0 (Finest)*" slider, and probably the second one "*1*" too,
    are turned off.
2.  Zoom into the photo to 100% and find an area that has both sharp
    in-focus parts as well as large plain out-of-focus ones, so that you
    can prevent noise reduction from destroying details as you tweak it.
3.  Start by setting the *Luminance Detail* slider to 0,
4.  Decide whether you just want to work with the *Luminance* slider, or
    whether you want to use the Luminance Curve for finer control.
    Increase the slider or curve just until the luminance noise has been
    smoothed away.
5.  Because luminance noise is all gone now (though we haven't recovered
    any detail yet), we can see color noise very clearly. This is a good
    time to denoise the color channels.
    1.  Either by setting manually the sliders : Increase "*Chrominance
        (Master)*" to a level where chrominance noise is gone but color
        detail in small objects hasn't been lost. You can reduce or
        boost the effects of noise reduction on the red/green and
        blue/yellow channels by respectively lowering or raising the
        "*Chrominance - Red-Green/Blue-Yellow*" sliders.
    2.  Or by using the "automatic" mode
6.  Now increase the *Luminance Detail* slider to recover detail until
    you are happy with the noise:detail trade-off.

## Interface

### Method

Noise reduction can be carried out in the RGB or Lab color spaces.
Working in the Lab space gives you the advantage of keeping the color
independent of the luminance. The difference between Lab vs RGB mode is
often negligible if you just use luminance noise reduction (via the
"*Luminance*" and "*Luminance Detail*" sliders), and most evident when
carrying out strong chrominance noise reduction (via the "*Chrominance -
Master*" slider).

Closely examine large areas of strong saturation with fine detail - such
as the pattern on a colored shirt or the petal of a flower - as you
switch between the RGB and Lab modes.

\<gallery caption="Comparison of Noise Reduction Methods" perrow="4"\|
style="text-align: center"\> Image:Rt noisereduction 1
off-vs-rgb.jpg\|Disabled vs enabled (RGB mode). Image:Rt noisereduction
2 rgb-vs-lab.jpg\|RGB vs Lab. Image:Rt noisereduction 3 lmmse
off-vs-rgb.jpg\|Disabled vs enabled (RGB mode). Image:Rt noisereduction
4 lmmse rgb-vs-lab.jpg\|RGB vs Lab.

</gallery>

### Quality

"High" makes two noise reducing passes, each one with a different
algorithm, for higher quality at the cost of processing time.

- You can select in "Preferences \> Performance & Quality" the number of
  levels for the wavelet:
  - No: no extra level
  - One level or two levels: add this number to the referenced one. This
    increases the processing time, but also improves the chromatic noise
    processing, mostly the ugly noise "packets"

### Luminance panel

#### Luminance control

Here you can choose between 2 options for luminance control, either by
using the slider or by using a curve. both systems don't interact.

##### Luminance

This slider lets you control coarse smoothing of luminance.

##### Luminance Curve

![](Rt_nr_luminancecurve_books.jpg "Rt_nr_luminancecurve_books.jpg")
This curve lets you target areas of a specific luminance more precisely,
so you can have strong noise removal in the shadows while not touching
light parts at all. This is desirable as noise will generally be
stronger in the shadows than in the highlights. You can use the curve
alone or the the slider alone, but not both simultaneously.

#### Luminance - Detail

This slider is for detail recovery after application of the Luminance
noise reduction. It will recover the structure while not reintroducing
the noise, unless you set this value too high.

### Chrominance panel

#### Auto method

This method offers three or four choices according to the chosen
configuration in "Preferences \> Performance & Quality":

##### Tool mode - "Standard"

- - Manuel
  - Automatic global
  - Preview

##### Tool mode - "Expert"

- - Manuel
  - Automatic global
  - Auto multi-zones
  - Preview multi-zones

##### Preview noise

- An indicator "Preview noise" gives the estimated chromatic noise
  values, after "Chrominance" processing
  - Mean: estimate the average value of the noise, all channels taken
    together
  - High: estimate the highest value of the noise, all channels taken
    together

##### Manuel

- The three sliders and the curve - Chrominance curve - act on the full
  image. You control the image settings manually.

###### Chrominance - Master

Applies noise reduction to colour channels. If this slider is at 0,5,
the Delta sliders have no effect and the wavelet is not enabled.

###### Chrominance - Red-Green

Can be used to reduce or boost the effect of colour noise reduction in
the red-green channel ("a" in Lab)

###### Chrominance - Blue-Yellow

Can be used to reduce or boost the effect of colour noise reduction in
the Blue-yellow channel ("b" in Lab)

##### Automatic global

- The processing algorithm, which acts on the full image, depends on
  several cells spread out in the image (9 so far). For each cell, is
  calculated:
  - An everage noise level for the Red-Green channel and the Blue-Yellow
    channel;
  - a maximum noise level for the same channels

<!-- -->

- If you can't choose the place of the cells, you can choose their size
  (Preferences \> Performance & Quality \> Cell size):
  - Mini: 100x115 - Small: 250x287 - Medium: half the tiles size (by
    default) - Maxi: tiles size
  - The tiles are used in the noise processing to boost and reduce the
    RAM consumption, they have a size of about 700 pixels.
  - There is advantages and drawbacks in each mode:
    - The smaller the cells are, the faster the processing is, we can
      keep this case for homogeneous images
    - The larger the cells are, the closer we are of the real
      conditions.

<!-- -->

- You can also in "Preferences \> Performance & Quality \> Denoising
  level", choose a noise processing level: Low (by default) or standard.

<!-- -->

- Then, a weighting is made, taken into account the noise levels
  determined above, to adjust the three sliders (Master, Red-Green,
  Blue-Yellow) and update "Noise preview"

<!-- -->

- The image that appears in the "Preview panel", shows what it will look
  like in TIF or JPG output

<!-- -->

- The settings (sliders position) are the same whatever is the "Preview
  panel" position in the full image.

<!-- -->

- The settings are not stored in the pp3 files. If you want to re-use
  them for operations on profiles, you have to switch in "manual" mode

##### Preview

- This mode is obviously only operational with a zoom at 100% and over,
  it acts on the full image
- For each preview motion (moving in the image, zoom) the automatic
  denoising calculation is done
- It takes into account the operational window and calculates for this
  one, the medium noises of the Red-Green channel and the Blue-Yellow
  channel and the maxima for these two channels as well.
- This window is used as "selecting area"
- The three sliders "Master", Red-Green and Blue-Yellow as well as
  "Noise preview" are updated.
- The setting got by choosing an area is used for the full image.

<!-- -->

- If you select a TIF or JPG output from this selection and in zoom
  mode, the output image will match to the preview.
- About the "automatic" mode it is advised, after having chosen the
  preview area and checked the processing quality, to switch back in
  "manual" mode, if you want to keep this setting for other images.
- The option Preference \> Performance & Quality \> Denoising level" is
  operational.

##### Auto multi-zones

- This mode is only operational for a TIF/JPG output and is output
  enabled if and only if "Auto multi-zones" is selected.
- The processing is not plain in the full image, but each tile specific.
- The is no fully usable "Preview", but as you can read it in the
  "Preview multi-zones" section, a convenient help may allow the user to
  have a very good approximation of the final image by moving the
  preview in the full image.

<!-- -->

- The "Auto multi-zones" mode use the tiles that are used in the
  RawTherapee noise processing, to boost the processing and decrease the
  memory consumption.

<!-- -->

- The image is divided in tiles by the software, with a vertical and
  horizontal step of about 500 to 800 pixels.
- This give a number of tiles that, depending on the image size and the
  chosen option in "Preferences \> Performance & Quality \> Number of
  tiles", can vary from 12 to over 120.
- There is a tiles overlapping with a transition between a tile setting
  and the adjoining tiles ones. You have then not to worry about a
  possible difference between adjoining tiles.
- Each tile is processed independently, according to the cell size
  ("Preferences \> Performance & Quality"), and ends to a setting of the
  red-green and blue-yellow channels totally independant for each tile.
  if we could set a manual setting of the tiles (up to 120) we would
  have 120 different settings of "Master", 120 different settings of
  "red-green", 120 different settings of "blue-yellow"!
- This lead to a multiple processing of only one image with as many
  settings as there is tiles.
- It is however possible to modulate the result with the help of the
  "Preferences \> Performance & Quality \> Auto multi-zone smoothing"
  option. It offers four choices:
  - None: the processing described above is carried out
  - Low: a part of the other tiles processing is taken into account, but
    in a very low way
  - High: as above but more pronounced
  - Max - average of all the tiles: this mode works like "Automatic
    global", but instead of using 9 cells, it is the tiles number that
    replaces the cells number (accordingly these ones can vary from 12
    up to over 120).
- All the options of "Preferences \> Performance & Quality" are usable.

##### Preview multi-zones

- Identical to Preview
- But you have the possibility to evaluate with a very good
  approximation the result of "Auto multi-zones" with the help of the
  information given as a supplement to "Preview noise"
- Under the indications "Preview noise: Mean=xx High=yy", two lines are
  displayed:
  - The first one give the tile size in pixels, and its centre position
    on the full image.
  - The second one give the preview size in pixels, and its centre
    position on the full image. The preview size depends on several
    parameters: zoom, lateral windows size.
  - Try to adjust whatever is best the centres and the sizes by moving
    the preview with the mouse and by modifying the zoom. Be careful, we
    are in noise processing, and it is very rare there is strong
    discontinuities, so gaps of some pixels or dozens of pixels are
    acceptable.

#### Chrominance curve

This curve allows to aim more precisely specific chromaticity areas.

- As a reminder, chromaticity in L\*a\*b\* mode conveys the colour
  intensity. A low chromaticity will convey grey or drab tones, a high
  chromaticity will convey saturated colours.
- This curve modulates the "Master", "Red-Green" and "Blue-Yellow"
  sliders action by multiplying their values by the curve ordinate.
- For example, if the master slider is set to 30 and that the curve is
  at mid-hight, the equivalent result will be about 45.
- It is usable in all the modes: manual, automatic global, auto
  multi-zones and preview.
- It can be useful for example, (default setting) in "Automatic global"
  mode to boost the grey or drab areas that will have a setting often
  too weak due to the settings average value. These grey areas are those
  where the visible noise become unpleasant, on the contrary to the very
  saturated areas where the same noise level (less visible) is
  acceptable.
- Note that in some cases, you can also use as a complement to the
  sliders acting, the median filter "Chroma only" in order to avoid too
  hight wavelets values (impression of washed out colours details).

### Gamma

Gamma varies noise reduction strength across the range of tones. Smaller
gamma values let noise reduction affect all tones emphasizing the action
on shadows, while higher gamma values limit the effect to brighter tones
only.

### Quality

"High" makes two noise reducing passes for higher quality at the cost of
processing time.

### Median

<img src="/images/Rt_nr_median_books.jpg" title="Rt_nr_median_books.jpg"
width="900" alt="Rt_nr_median_books.jpg" /> Use this filter to remove
tiny, sharp-looking artifacts left-over from noise reduction. The
[median filter](https://en.wikipedia.org/wiki/Median_filter) replaces
each pixel with the median value of its neighboring pixels. The
contiguous group of pixels being sampled is called the "windows". This
window slides pixel by pixel over the entire image. You can choose the
size of this window using the "Median type" drop-down. The larger the
size, the longer it takes.

Available window sizes:

- 3x3 soft: treats 5 pixels in a 3x3 pixel window.

  
○●○

●●●

○●○

- 3x3: treats 9 pixels in a 3x3 pixel window.

  
●●●

●●●

●●●

- 5x5 soft: treats 13 pixels in a 5x5 pixel window.

  
○○●○○

○●●●○

●●●●●

○●●●○

○○●○○

- 5x5: treats 25 pixels in a 5x5 pixel window.

  
●●●●●

●●●●●

●●●●●

●●●●●

●●●●●

- 7x7: treats 49 pixels in a 7x7 pixel window.

  
●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

- 9x9: treats 81 pixels in a 9x9 pixel window.

  
●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

Sometimes it is possible to achieve higher quality running several
iterations with a small window size than one iteration with a large
window size.

When using the "Luminance only" and "Lab" methods, median filtering will
be performed just after the wavelet step in the noise reduction
pipeline. When using the "RGB" mode, it will be performed at the very
end of the noise reduction pipeline.

![](Rt_nr_median_zoom_books.jpg "Rt_nr_median_zoom_books.jpg") You may
wonder what use median filtering has other than the elimination of
pixels that strongly differ from their surrounding neighbors. One of
these benefits is a reduction in file size when saving to compressed
formats such as JPEG and PNG. Median filtering removes variations which
you will lose anyway if you downscale the image. You are also likely not
to see these variations if you print the image. Removing them using
median filtering can reduce the file size by even 40% (tested using JPEG
compression strength 92 with "balanced quality" [chroma
subsampling](https://en.wikipedia.org/wiki/Chroma_subsampling)), so give
it a try if file size is an issue.

You can also use the median filter "Chroma only" as a complement to the
wavelets processing. Doing so allows to reduce required values for the
wavelets processing and to avoid fading details too much.

#### Method

You have five methods at your disposal:

- Luminance only: works in L\*a\*b\* mode, but only affects the L\*
  channel
- Chroma only: works in L\*a\*b\* mode, but only affects the a\* and b\*
  channels
- Weighted L\* (Little) + a\*b\* (normal): works in L\*a\*b\* mode, but
  acts more weakly on the L\* channel
- L\*a\*b\*: works in L\*a\*b\* mode, with equality of the action on the
  three channels L\*, a\*, b\*
- RGB: works in RGB mode. In this mode the window size choice is limited
  to 3x3 soft, 3x3 and 5x5.
