---
title: Editor
contributors:
  - DrSlony
  - Hombre
  - Lebarhon
  - XavAL
  - Thanatomanic
  - Benitoite
tags:
  - 'General Information'
toc: true
---

![](rt_55_trains.png)

## Introduction

The Image Editor tab is where you tweak your photos. By default
RawTherapee is in "Single Editor Tab Mode, Vertical Tabs" (SETM/VT)
which is more memory-efficient and lets you use the
[Filmstrip](#the-filmstrip) (described below). You can
switch to "Multiple Editor Tabs Mode" (METM) by going to "[Preferences \> General \> Layout](/preferences#layout)", however each
Editor tab will require a specific amount of RAM relative to the image
size and the tools you use, and also the Filmstrip is hidden in this
mode, so we recommend you first give SETM a try.

## The Preview Panel

The central panel shows a preview of the image being edited. This
preview is generated from raw data if such is available. It reflects the
adjustments made by the tools in the
[Toolbox](#toolbox). Note that the effects of some
tools are only accurately visible when you are zoomed in to 1:1 (100%)
or more; these tools are marked in the interface with a "1:1" icon
![Zoom 1:1](one-to-one-small.png "Zoom 1:1") alongside the tool's name.

When opening an image, RawTherapee loads the tool settings from the
sidecar file if one exists, else it applies a default sidecar file as
specified in "[Preferences \> Image Processing \> Default Processing
Profile](/preferences#default-processing-profile)". When you
close the image (which happens automatically if you open a different
image or if you close RawTherapee) the current tool settings are
automatically saved to a sidecar file as specified in "[Preferences \> Image Processing \> Processing Profile Handling](/preferences#processing-profile-handling)".

### Eek! My Raw Photo Looks Different than the Camera JPEG

When opening a raw photo you may notice that it looks different from
your camera's JPEG, or from what other software show when viewing the
same raw photo. In some cases this difference is minute, but in other
cases it could be significant - the image could be darker, lack
contrast, be less sharp and more noisy. What gives?

There are three things you must know first to understand what is
happening here:

1.  Your camera does not show you the real raw data when you shoot raw
    photos. It processes the raw image in many ways before presenting
    you with the histogram and the preview on your camera's display.
    Even if you set all the processing features which your camera's
    firmware allows you to tweak to their neutral, "0" positions, what
    you see is still not an unprocessed image. Exactly what gets applied
    depends on the choices made by your camera's engineers and company
    management, but usually this includes a custom tone curve,
    saturation boost, sharpening and noise reduction. Some cameras,
    particularly low-end ones and [Micro Four-Thirds
    system](http://en.wikipedia.org/wiki/Micro_Four_Thirds_system), may
    also apply lens distortion correction to not only fix [barrel and
    pincushion
    distortion](http://en.wikipedia.org/wiki/Distortion_(optics)#Radial_distortion)
    but also to hide dark corners caused by severe
    [vignetting](http://en.wikipedia.org/wiki/Vignetting) or by the
    [lens hood](https://en.wikipedia.org/wiki/Lens_hood). Most cameras
    also underexpose every photo you take by anywhere from -0.3EV to
    -1.3EV or more, in order to gain headroom in the highlights. When
    your camera (or other raw editing software) processes the raw file
    it compensates for this by increasing exposure compensation by the
    same amount.
2.  When shooting a raw photo, most cameras embed within the raw file a
    full-resolution JPEG image with tone curves and other adjustments
    applied. Some raw files contain as many as three JPEG images
    differing only in resolution. Most cameras offer storing photos in
    one of three modes: "RAW", "JPEG", or "RAW+JPEG". The embedded JPEG
    image discussed here is stored within the raw file even in just
    "RAW" mode! When you open raw files in other software, what you are
    usually seeing is **not** the raw data, but the embedded, processed
    JPEG image! Examples of software which are either incapable of or
    which in their default settings do not show you the real raw data:
    [IrfanView](http://en.wikipedia.org/wiki/IrfanView),
    [XnView](http://en.wikipedia.org/wiki/XnView),
    [Gwenview](http://en.wikipedia.org/wiki/Gwenview),
    [Geeqie](http://en.wikipedia.org/wiki/Geeqie), [Eye of
    GNOME](http://en.wikipedia.org/wiki/Eye_of_GNOME),
    [F-Spot](http://en.wikipedia.org/wiki/F-Spot),
    [Shotwell](http://en.wikipedia.org/wiki/Shotwell_(software)),
    [gThumb](http://en.wikipedia.org/wiki/GThumb), etc. It is worth
    mentioning at this point that if you shoot in "RAW+JPEG" mode then
    you could in fact be wasting space on your memory card and gaining
    nothing for it, as your raw files most likely already contain an
    embedded JPEG identical to the external one saved in "RAW+JPEG"
    mode.
3.  Most raw development programs (programs which do read the real raw
    data instead of just reading the embedded JPEG) apply some
    processing to it, such as a base tone curve, even at their most
    neutral settings, thereby making it impossible for users to see the
    real, untouched contents of their raw photos. Adobe Lightroom is an
    example. Comparing RawTherapee's real [neutral](neutral)
    image to a pseudo-neutral one from these other programs will expose
    the differences.

RawTherapee, on the other hand, is capable of showing you the real raw
image in the main preview, leaving the way you want this data processed
up to you. When you use the "[Neutral](neutral)" processing
profile you will see the demosaiced image with camera white balance in
your working color space with no other modifications. You can even see
the non-demosaiced image by setting the [demosaicing
method](Demosaicing#Method.md) to "None".

To provide you with a more aesthetically pleasing starting point,
RawTherapee by default uses the [Auto-Matched
Curve](Auto-Matched_Curve.md) processing profile, which
automatically generates a tone curve to make the tones of the raw image
match those of the embedded JPEG, if one exists. If one does not exist,
you can use the [Standard Film Curve](standard_film_curve)
processing profile, which applies a curve which looks good in most
cases. Choose the sub-type (ISO Low/Medium/High) depending on how noisy
your image is.

### Scrollable Toolbars

The toolbars above and below the main preview hold a certain number of
buttons and other widgets which might not fit on lower resolution
screens.

### Preview Background Color

<figure>
<img src="/images/Rt59_preview_background_all.png"
title="Rt59_preview_background_all.png" />
<figcaption>Rt59_preview_background_all.png</figcaption>
</figure>

The background color of the preview panel may be changed to allow you to
better judge how the image tones will appear when the saved image is
viewed on a website (or image viewer, or print) of a similar background
color.

This choice also applies to the cropped-off area, if the image is
cropped. See "[Preferences \> General \> Appearance \> Crop mask
color](Preferences#Appearance.md)".

Available options:

- theme-based (see [Preferences \> General \>
  Appearance](Preferences#Appearance.md)),
- black,
- [L\* middle grey](https://en.wikipedia.org/wiki/Middle_gray),
- white.

### Preview Channel

<figure>
<img src="/images/Rt59_preview_channel_all.png"
title="Rt59_preview_channel_all.png" />
<figcaption>Rt59_preview_channel_all.png</figcaption>
</figure>

The preview can be toggled to show one of the following channels:

- red,
- green,
- blue,
- luminosity, which is calculated as 0.299\*R + 0.587\*G + 0.114\*B.

Preview of individual channels may be helpful when editing RGB curves,
planning black/white conversion using the channel mixer, evaluating
image noise, etc. Luminosity preview is helpful to instantly view the
image in black and white without altering development parameters, to see
which channel might be clipping or for aesthetic reasons.

### Preview Mask

<figure>
<img src="/images/Rt59_preview_mask_all.png"
title="Rt59_preview_mask_all.png" />
<figcaption>Rt59_preview_mask_all.png</figcaption>
</figure>

Available options:

- Focus mask, which shows which areas are in focus (based on how sharp
  they appear),
- Sharpening contrast mask, which visualizes the mask which decides
  which areas are affected by sharpening. See [Sharpening \> Contrast
  Mask](Sharpening#Contrast_Mask.md).
- Clipped shadow indication.
- Clipped highlight indication.

<figure>
<img src="/images/Preview_6_focus_2.jpg"
title="Focus mask indicating the focusing plane" />
<figcaption>Focus mask indicating the focusing plane</figcaption>
</figure>

The focus mask is designed to highlight areas of the image which are in
focus. Naturally, focused areas are sharper, so the sharp areas are
highlighted. The focus mask is more accurate on images with a shallow
depth of field, low noise and at higher zoom levels. To improve
detection accuracy for noisy images, evaluate at smaller zoom, around
the 10-30% range. The current implementation analyzes the preview image,
which is rescaled from the original captured size down to what you see
on screen. When zoomed less than 100%, the preview image is downscaled,
a side-effect of which is the apparent reduction of noise. You can take
advantage of this to help identify truly sharp details, rather than
noise itself which may introduce a false micro texture. At the same
time, downscaling compresses larger scale details into a smaller size,
and it may introduce aliasing artifacts, both of which could lead to
false positives. You can increase your confidence by viewing the mask at
various zoom levels. It is not always fault proof, but can be helpful in
many cases. Due to these caveats, be sure to double-check your images if
you decide to delete them based on the focus mask.

### Detail Window

The "New detail window" button
![<File:Window-add.png>](Window-add.png "File:Window-add.png"), situated
below the main preview next to the zoom buttons, opens a new viewport
over the main preview of an adjustable size and of adjustable zoom. This
lets you work on the photo zoomed-to-fit while examining several areas
of interest at a 100% zoom (or even more). The benefit of using this
feature is particularly important to users with slower machines, though
not only them, as the zoomed-out main preview takes a shorter amount of
time to update than if you were to zoom it to 100% because working at a
zoom level less than 100% excludes certain slow tools, such as Noise
Reduction, while the little detail windows zoomed to 100% do include all
tools and are fast to update because of their small size. This allows
you can use the main preview for your general exposure tweaks where it
is necessary to see the whole image, and one or more detail windows to
get sharpening and/or noise reduction just right.

### Preview Refresh Delay

Changing any tool's parameters sends a signal for the preview image to
be updated accordingly. Imagine what would happen if there was no "delay
period", and you dragged, for example, the exposure compensation slider
from 0.00 to +0.60. A signal would be sent to update the preview for
every single change of that value - for +0.01, +0.02, ... +0.59, +0.60.
Updating the preview 60 times would be completely unnecessary and
actually take longer than it takes you to move the slider. This is
especially true for more complicated tools, such as noise reduction,
where a preview update can take even a second (depending on your CPU and
preview size). The solution is for RawTherapee to wait for a very short
period from the moment you stop moving a slider (you don't have to let
go of it, pausing movement is enough) until the moment it sends a signal
for the preview to be refreshed.

We have introduced two parameters which control the length of this
waiting period:

AdjusterMinDelay  
Default value = 100ms.

This is used for tools with a very fast response time, for example the
exposure compensation slider.

AdjusterMaxDelay  
Default value = 200ms.

This is used for tools with a slow response time, for example the
CIECAM02 sliders.

You can adjust both of these values in the options file in the [config
folder](File_Paths.md).

## The Left Panel

To the left is a panel which optionally shows the main histogram
("*Preferences \> General \> Layout \> Histogram in left panel*"), and
always shows the *Navigator*, *History* and *Snapshots*. You can hide
this panel using the ![Hide left panel
icon](panel-to-left.png "Hide left panel icon") hide icon, or its
[keyboard shortcut](keyboard_shortcuts).

### Main Histogram

<figure>
<img src="/images/Rt57_histogram_wide_labeled.png"
title="Rt57_histogram_wide_labeled.png" />
<figcaption>Rt57_histogram_wide_labeled.png</figcaption>
</figure>

<figure>
<img src="/images/RT57_histogram_ani.gif" title="RT57_histogram_ani.gif" />
<figcaption>RT57_histogram_ani.gif</figcaption>
</figure>

<figure>
<img src="/images/Rt_histogram_rgbindicator.png"
title="Rt_histogram_rgbindicator.png" />
<figcaption>Rt_histogram_rgbindicator.png</figcaption>
</figure>

A histogram in photography is a graphical representation of the number
of pixels of a given value. Typically the horizontal axis represents the
range of possible values while the vertical axis represents the count of
pixels with that value. The axes need not be linear - RawTherapee can
also scale the histogram logarithmically.

Regardless of the photo's bit depth, the histogram itself has a
precision of 256 sampling bins. To understand this, let us look at the
example of a 16-bit image using integer precision. Its range of possible
values spans from 0 to 65535 (2^16 = 65536 possible values, and since 0
is a possible minimum value then the maximum value is 65535). Drawing a
histogram using 16-bit precision would mean that it would need to be
65535 pixels wide to faithfully represent the data, and no screen today
is anywhere near that wide. Instead, all pixels with values from 0 to
255 (65535/256\*1) are grouped into the first "bin". The second bin
consists of a count of all pixels with values from 256 to 511
(65535/256\*2). The third bin represents values 512 to 767
(65535/256\*3). And so on until bin 256. This happens regardless of the
input image's bit depth - and RawTherapee's engine uses 32-bit
floating-point precision anyway.

The main histogram can simultaneously show one or more of the following:

- ![<File:Histogram-red-on-small.svg>](Histogram-red-on-small.svg "File:Histogram-red-on-small.svg")
  the red channel,
- ![<File:Histogram-green-on-small.svg>](Histogram-green-on-small.svg "File:Histogram-green-on-small.svg")
  the green channel,
- ![<File:Histogram-blue-on-small.svg>](Histogram-blue-on-small.svg "File:Histogram-blue-on-small.svg")
  the blue channel,
- ![<File:Histogram-silver-on-small.svg>](Histogram-silver-on-small.svg "File:Histogram-silver-on-small.svg")
  CIELab luminance,
- ![<File:Histogram-gold-on-small.svg>](Histogram-gold-on-small.svg "File:Histogram-gold-on-small.svg")
  [chromaticity](http://en.wikipedia.org/wiki/Chromaticity).
- ![<File:Histogram-bayer-on-small.svg>](Histogram-bayer-on-small.svg "File:Histogram-bayer-on-small.svg")
  red, green and blue channels of the source raw image before
  demosaicing.

The histogram shows the channels listed above using the gamma-corrected
output profile when the gamut button
![<File:Gamut-hist.png>](Gamut-hist.png "File:Gamut-hist.png") is
disabled (default), or using the working profile when the button is
enabled. The status of this button also affects the values shown in the
Navigator panel, as well as the clipped shadow
![<File:Warning-shadows.png>](Warning-shadows.png "File:Warning-shadows.png")
and
![<File:Warning-highlights.png>](Warning-highlights.png "File:Warning-highlights.png")
highlight indicators. It does not affect the raw histogram.

Like water in a pipeline, image data flows through RawTherapee from the
input file through various stages, most of which the user can control,
to the output. The output could be the image saved in a file, or the
image displayed on your screen. Each stage affects the color data. The
histogram allows you to visualize this data at several stages. By
default, the histogram shows color data as it will appear if you save
the output image, including processing done at all intermediate stages.
By enabling the gamut button
![<File:Gamut-hist.png>](Gamut-hist.png "File:Gamut-hist.png") you can
peak at the data at the early stage where it gets converted into the
working space. You can even look at the raw data before any
transformations or demosaicing are applied.

Let's examine the large histogram example above. Though it actually
shows four histograms (red, green, blue and luminance), focus on one
histogram at a time. The horizontal axis represents the possible values
of the histogram, where "A" are the darkest values possible, "C" the
mid-tones, and "E" the brightest possible values. The position of the
histogram line on the vertical axis represents how many pixels have that
value. We can see that there are zero pixels in the red channel with
values around "A" (from zero to very dark), because the histogram line
lies right along the bottom. There is a significant number of pixels
where the red channel is dark (between A and B), and a significant
number where it is light (around D). Then, importantly, there is a spike
at the right end of the histogram, at E - it tells us that a large
number of pixels have maximal red values - they are clipped.

Generally speaking, you should care when clipping occurs on skin, and
not care when it's due to [specular
highlights](https://en.wikipedia.org/wiki/Specular_highlight). If a
histogram shows clipping, and if you care about the clipped regions, you
should start by establishing where the clipping occurs. Check the raw
histogram - are any channels clipped? If yes, then maybe [highlight
reconstruction](Exposure#Highlight_Reconstruction.md) can help.
If the raw histograms are not clipped, then all the required information
is intact, and it is some stage downstream in the pipeline which causes
clipping. Ensure your working profile's gamut is large enough by
enabling the gamut button
![<File:Gamut-hist.png>](Gamut-hist.png "File:Gamut-hist.png") to see
histograms at the working profile stage of the pipeline. You might want
to temporarily apply the [Neutral](neutral) profile to
disable all the tools while checking, then revert. If your working space
is not causing clipping (the default working space is ProPhoto and it's
huge), then it's likely your adjustments which are causing clipping.
Reduce exposure, go easy on the curves, use dynamic range compression if
necessary.

Knowing how to read a histogram is a basic and very useful skill, as it
can point out issues with your image regardless of how dim or
miscalibrated your monitor may be.

To help you visualize the data, the histogram (as of RawTherapee 5.5)
has three modes which scale the data in the x and y axes differently:

- ![<File:Histogram-mode-linear-small.png>](Histogram-mode-linear-small.png "File:Histogram-mode-linear-small.png")
  Linear-linear mode. You find gridlines at halves, quarters, eighths
  and sixteenths, depending on the size of the histogram.
- ![<File:Histogram-mode-logx-small.png>](Histogram-mode-logx-small.png "File:Histogram-mode-logx-small.png")
  Linear-log mode. The x-axis is linear, the y-axis and the horizontal
  gridlines are scaled logarithmically. The position of the gridlines
  still corresponds to the halves, quarters, etc.
- ![<File:Histogram-mode-logxy-small.png>](Histogram-mode-logxy-small.png "File:Histogram-mode-logxy-small.png")
  Log-log mode. Both the x- and y-axes are scaled logarithmically. The
  gridlines are not scaled logarithmically, but correspond to
  [stops](https://en.wikipedia.org/wiki/Exposure_value) - with every
  gridline the value doubles, so there are lines for the values 1, 3, 7,
  15, 31, 63, and 127 (`pow(2.0,i) - 1)`).

When there is a disproportionately bright area relative to the rest of
the image, it will show up as a spike in the histogram. If you want to
show this on a histogram with a linear y axis, the spike may push the
lesser values down the y-axis, making them difficult to see. Switch to
one of the log modes to scale the data and help you get a better
overview of all values.

The histogram can be moved to the left/right panel from "*Preferences \>
General \> Layout \> Histogram in left panel*".

#### Raw Histograms

Raw files contain a dump of data captured by the sensor and quantified
by the analog-to-digital converter. The raw file as a container has a
bit depth of its own, typically 16-bit, while the data it contains could
have a lower bit depth - typically it is 12-bit (0-4096) or 14-bit
(0-16384). To display the data from a raw file as an image, one of the
several key bits of information required to process the data correctly
are the black and white levels. The black level is not necessarily 0, as
the sensor and camera electronics produce digital noise, so the noise
floor may lie for instance at 512. The white level is also not
necessarily 16384; it depends on various things, and may lie for
instance at 16300. For more information, see the articles
[Demosaicing](demosaicing) and [Adding Support for New Raw
Formats](Adding_Support_for_New_Raw_Formats.md) (especially the
header of the `camconst.json` file). The black and white level values
used by RawTherapee are hierarchically set by looking in several places:
in `dcraw.c`, inside the raw file's metadata, and in `camconst.json`
(latter takes precedence). Furthermore, the user can tweak the raw
[black](raw_black_points) and
[white](raw_white_points) levels from within RawTherapee.

The raw histograms show data after black level subtraction. The right
end of the histogram is anchored on the white level. The raw histograms
are affected by the detected black and white levels as well as by the
black and white level adjustments made by the user in RawTherapee.

When examining the raw histogram, you may also want to set the
demosaicing method to "none". This will reveal the sensor pattern in the
preview, and also cause the [Navigator](editor#navigator)
panel to show the raw RGB values of the pixel currently being hovered
over. These values are affected by the detected black and white levels
as well as by the black level adjustments made by the user in
RawTherapee, but they are not affected by the white level adjustments
("white-point correction") made by the user in RawTherapee.

### Waveform

In RawTherapee, the waveform is a special representation of the RGB
channels which shows the position of the image pixels horizontally and
the value of each pixel vertically. The number of pixels having the same
position and value is indicated by the intensity.

In greater detail:

- each column represents a group of columns in the image. For example,
  if the waveform has 256 columns and the image is 5376 pixels wide,
  each column of the waveform represents 21 columns of the image. From
  left to right, the columns show the analysis of the corresponding
  groups of 21 columns in the image
- the analysis of the pixel values **is performed on the final image**,
  that is, taking into account [the output
  profile](https://rawpedia.rawtherapee.com/Color_Management#Output_Profile)
- for each column, the R, G, and B values of the pixels are placed
  vertically. The greater the channel value of the pixel, the higher it
  is placed in the column. Each channel of a pixel is placed according
  to its value (the three values do not have to be together)
- when several channels coincide at the same point on the waveform,
  their colors blend. For example, yellow points come from additive
  blending of the red and green channels
- the more pixels of a group that have the same channel value (therefore
  they all represent the same point in the waveform), the brighter or
  more intense the color of that channel will be. Suppose, in the
  previous example in a group of 21 columns of the image, there is a set
  of 300 pixels with a red channel value of 180 and another set of 40
  pixels with a value of 57. When showing them in the waveform, the
  first set will have a red point brighter than the second. They will be
  located in the same column, but the first point will be higher and
  brighter than the other one. Additionally, you have a small slider to
  the left of the waveform to change the brightness of the points (if
  you do not see it, you should toggle the button to show the display
  options
  […](https://rawpedia.rawtherapee.com/images/c/c5/Histogram-ellipsis-small.png)).
  Increasing the brightness of the points, you will be able to better
  see when there are overexposed or underexposed pixels (at the top or
  bottom of the waveform)

<figure>
<img src="/images/Waveform.jpg" title="Waveform.jpg" />
<figcaption>Waveform.jpg</figcaption>
</figure>

If you look carefully at the waveform you will see some dashed
horizontal lines. They represent the position of the values 1, 3, 7, 15,
31, 63, and 127 (same as the vertical dashed lines in the histogram) and
also the values 0 (although this line is obscured by the line for 1) and
255 (the uppermost dashed line). The waves never reach the lower or
upper limits of the graph. This way the clipped values can be seen
better.

Just like the histogram, you can independently activate or disable the
three RGB channels and the luminosity, and also the bar that indicates
the channel values of the image pixel currently under the mouse pointer.

In the example photo, you can see there are two distinct areas. To the
left, a padlock with contrasty areas and different shades of color. To
the right, we have gray wood that darkens towards the image border. Most
of the waves are located in the lower part of the graph because the
image has low luminosity (the average luminosity tends to a middle gray
or a little darker).

In the case of the gray wood, you can see in the waveform that on the
right side (corresponding with the location of the door) there is one
thick descending white line. It is white because the wood has a neutral
gray tone and the three channels of the pixels have similar values which
create white when mixed. It is thick because there are different shades
of gray (different values) in the wood texture. The line has a clear
tendency to go down to the right where the wood is darker.

The peak that is on the left side comes from the padlock, with green and
red channels more or less equal (generating a yellow area) and the blue
channel is lower, coinciding with the brass tone of the padlock. The
small cyan streak above the peak and at the top of the waveform comes
from the overexposed reflection of the padlock shackle. Finally, the
abrupt change in the white line at the left part of the waveform
represents the large contrast between the edge of the door frame and the
deep shade between the frame and door.

<span id="rgb-parade"></span>

### RGB Parade

![](Parade.jpg "Parade.jpg") This is the same as the waveform, but with
the color channels separated in to three adjacent graphs.

In this form, you can better see what happens with each channel, without
the blending of colors or some channels blocking others. The
disadvantage is that it is somewhat more difficult to identify a column
of a channel in the corresponding area of the image because the graphs
are narrower.

In the example, you can see the overexposed areas of the padlock
correspond to the green and blue channels.

<span id="vectorscopes"></span>

### Vectorscopes

The *vectorscopes* are graphical representations of the image pixel
colors. Every pixel is represented as a white point located at the
position of the graph corresponding with the hue and saturation.

In the same way as with the waveform, the *vectorscopes* are calculated
with the colors in the exported image, that is, based on the
[<https://rawpedia.rawtherapee.com/Color_Management#Output_Profile>
output
profile](https://rawpedia.rawtherapee.com/Color_Management#Output_Profile_output_profile.md).

In RawTherapee, there are two types of *vectorscopes*:

- the ***H-S Vectorscope***: shows pixel colors based on the
  [<https://en.wikipedia.org/wiki/HSL_and_HSV> HSL color
  model](https://en.wikipedia.org/wiki/HSL_and_HSV_HSL_color_model.md).
  The more saturated colors are located closer to the edges of the
  graph, which represent the limits of the *output color space* and is
  useful to estimate the number of pixels that are outside the color
  gamut, or about to go outside.
- the ***H-C Vectorscope***: shows the colors based on the
  [<https://en.wikipedia.org/wiki/CIELAB_color_space#Cylindrical_model>
  Lch color space](https://en.wikipedia.org/wiki/cielab_color_space#cylindrical_model_lch_color_space).
  It is useful to estimate the saturation of colors as we perceive it
  with our eyes, that is, how “intense” or “washed-out” we perceive the
  colors. The closer to the edges the white points are, the more
  saturated the colors are.

The saturation can be understood as the amount of color there is in a
hue, relative to the maximum for that hue (the “purest” hue), that is,
the percentage of the pure color that the observed color has. The
“average” person usually understands the “colors” as the hue with 100%
saturation. In the color spaces used in the vectorscopes, these “colors”
are found along the edges of their color ranges (similar to the CIExy
diagram). The difference between HSL and Lch is that the latter
represents the colors in a way that is closer to how we see them.

In the ***H-S Vectorscope*** the saturated colors at 100% (or almost)
are located near the edges of the circle as white spots, indicating
colors that are completely saturated or are already clipped. The
concentric circles in the graph indicate a saturation of 25%, 50%, 75%,
or 100% (in the outermost circle). This vectorscope is a good way to see
how many pixels are outside (or almost outside) the color space of the
*output profile*.

![](hsvectorscope.jpg)

In this vectorscope you will see that there are three axes that point to
the colors red, yellow, green, cyan, blue, and magenta.

In the image analysis, the saturated pixels are shown near the larger
circle, between the colors yellow and red (top right).

The rest of the pixels are distributed and with different “amounts of
color” (saturation), represented as white areas of a more or less
intense color, depending on the number of pixels in that area.

![](hsvectorscope_oog.jpg)

By activating the “show out-of-gamut colors” button you will see a cyan
mask that highlights the out-of-gamut pixels.

In the ***H-C Vectorscope*** the concentric circles represent the chroma
values 32, 64, 96, and 128. The further towards the edges a color is
located, the more saturated it is.

The chroma values are calculated with the values a\* and b\* from the
L\*a\*b\* coordinates that you can see in the *Navigator* panel using
the formula:

![](chroma.png)

In this example you see the more saturated colors reaching approximately
the value 85. Specifically, they are the red and yellow tones.

![](hcvectorscope_oog.jpg)


However, keep in mind that the three-dimensional color space is not
regular (they are not spheres or cubes) and therefore to correctly
estimate the clipped colors you should combine more than one analysis
method.

Additionally, you can see a diagonal line at the top right. This line
indicates the average Caucasian skin hue. In a portrait, hovering the
mouse pointer over a medium skin tone, the graph should mark the pixel
around this line. Otherwise, there is a color cast on the skin that you
would be interested in removing.

### Navigator

The *Navigator* panel shows a thumbnail of the currently opened image,
and RGB, HSV and Lab values of the pixel your cursor is currently
hovering over.

The values shown in the main histogram and Navigator panel are either
those of the working profile or of the gamma-corrected output profile,
depending on the state of the gamut button
![](gamut-hist.png) located
in the toolbar above the main preview. When the gamut button is enabled
the working profile is used, otherwise the gamma-corrected output
profile is used.

By clicking on the values in the Navigator you can cycle between these
three formats:

- \[0-255\]
- \[0-1\]
- \[%\]

RawTherapee 5.1 onward can show the real raw photosite values. To see
them, set the Navigator to use the \[0-255\] range, apply the
Neutral [processing profile](/sidecar_files_-_processing_profiles), then set the
[Demosaicing](/demosaicing) method to "None". The Navigator
will show the real raw photosite values after black level subtraction
within the range of the original raw data.

### History

The History panel contains a stack of entries which reflect each of your
image editing actions. By clicking on the entries you can step back and
forth through the different stages of your work.

An entry is added each time you adjust a *different* widget - multiple
edits to the same widget are stored as one entry. For example, adjusting
the exposure compensation slider from "0" to "0.3" and then to "0.6"
will result in one entry being stored with a final value of "0.6".
Likewise, when adjusting a curve, all individual control point
adjustments are grouped into one history entry. Should you wish to store
the adjustments as two (or more) history entries, you will have to split
them by adjusting some other widget. For example, assuming a curve is in
"Film-like" mode and you want to keep to that way: adjust several
control points on the curve, then toggle the curve mode from "Film-like"
to "Standard" and then back to "Film-like" to create a new history
entry, and then continue adjusting the curve.

The history stack is not saved - it is lost as soon as you close the
Editor tab. None of your adjustments are lost though, as the final state
of all tools is saved in the [sidecar file](/sidecar_files_-_processing_profiles), ready to be used
the next time you open that image.

### Snapshots

Under the *History* panel is a panel called *Snapshots*. Its use is in
that you can save a snapshot of the photo with all the adjustments up to
that point in time, and then proceed to further modify your photo to
give it a different appearance, saving new snapshots at every moment you
feel you might have reached a version of your photo worth saving. Once
you have two or more snapshots, you can just click on them to flip
through the different versions and stick with whichever one you like
best. In the future, the snapshots will be saved to the PP3 sidecar
file. For now, the history and snapshots are lost when you load a new
photo in the *Image Editor* or close RawTherapee.

## The Right Panel

To the right is a panel which optionally shows the main histogram and
*Processing Profiles* selector ("*Preferences \> General \> Layout \>
Histogram in left panel*"), and always shows the
[Toolbox](#toolbox). You can hide this panel using the ![](panel-to-right.png) hide icon,
or its [keyboard shortcut](/keyboard_shortcuts).

### Processing Profile Selector

The Processing Profiles panel allows you to apply, save, load, copy and
paste processing profiles, partially or in full.


![](processing-profiles-selector.png)


Read the [Sidecar Files / Processing
Profiles](/sidecar_files_-_processing_profiles) page for more
information.

### Toolbox

The *Toolbox*, in the right panel, contains all the tools you use to
tweak your photos. Each tool has its own RawPedia article.

## Editor Tab Modes

RawTherapee allows you to work on photos in two modes:

- *Single Editor Tab Mode* (SETM), where you work only on one photo at a
  time, and each photo is opened in the same *Editor* tab. There is a
  horizontal panel called the
  *[Filmstrip](#the-filmstrip)* at the
  top of the *[Editor](#the-filmstrip)*
  tab showing the rest of the photos in that folder for easy access.
  There are *Previous Image* and *Next Image*
  ![](nav-prev.png)
  ![](nav-next.png) buttons in
  the bottom toolbar (and [keyboard shortcuts](/keyboard_shortcuts) for them) to switch to the
  previous/next image.
- *Multiple Editor Tabs Mode* (METM), where each photo is opened in its
  own *[Editor](#the-filmstrip)* tab. The
  *[Filmstrip](#the-filmstrip)* is hidden
  in this mode and there are no previous/next buttons. Having multiple
  photos opened at the same time requires more RAM.

Try both modes and see which one suits you best. To do that, click on
the *Preferences* icon ![Preferences icon](preferences.png) in the bottom-left or top-right
corner of the RT window, choose "*General \> Layout*" and set *Editor
Layout* to your preferred choice.

Use this *Preferences* window to select a different language for the
user interface, to choose a different color theme, change the font size,
etc.

It is also possible to start RawTherapee in no-File-Browser-mode
(without the *File Browser* tab) by specifying RawTherapee to open an
image from your operating system's file browser (in other words,
right-click on a photo and select "*Open With \> RawTherapee*"), or by
using the image filename as an argument when starting RawTherapee from
the command line (`rawtherapee /path/to/some/photo.raw`). This mode was
introduced for people with little RAM as not having a *File Browser* tab
means RawTherapee uses a little less memory, however in practice the
amount of memory saved is little and the usability cost outweighs the
little benefit, so it is likely to be removed in the future (see [issue 2254](https://code.google.com/p/rawtherapee/issues/detail?id=2254)).

## The Filmstrip

![](rt_filmstrip_21_toolbar-visible.jpg "rt_filmstrip_21_toolbar-visible.jpg")

![](rt_filmstrip_21_toolbar-hidden.jpg "rt_filmstrip_21_toolbar-hidden.jpg")

If you use *Single Editor Tab Mode* ("*Preferences \> General \>
Layout*") you can display a horizontal panel above the preview, this is
called the *Filmstrip*. It contains thumbnails of all images in the
currently opened album, and is synchronized with the currently opened
image so that you can use [keyboard shortcuts](/keyboard_shortcuts) or the previous ![Open previous image icon](nav-prev.png "Open previous image icon") and next
![Open next image icon](nav-next.png "Open next image icon") image
buttons to open the previous/next image without needing to go back to
the *[File Browser](/file_browser)* tab.

As of RawTherapee version 4.2.10, you can hide the Filmstrip's toolbar
to save screen space. There are two ways of doing this: one way just
toggles the toolbar on/off without resizing the filmstrip to the new
height, and the other way does the same but also automatically resizes
the filmstrip's height. Both are invoked via [keyboard shortcuts](/keyboard_shortcuts) only. As resizing the
filmstrip's height will trigger a refresh of the image preview and this
might take a while if using CPU-hungry tools like noise reduction while
zoomed in at 100%, the mode that doesn't resize has been implemented for
users with slow machines. Users with fast machines will find the
auto-resizing mode more helpful.

## Monitor Profile and Soft-Proofing

The widgets under the main preview in RawTherapee 5 allow you to apply a
monitor color profile to the preview image. This enables users who have
calibrated and profiled their monitors to get an instant and accurate
preview of their work, whether you're staying in sRGB or working in a
wide gamut. Note: OS X users are limited to sRGB and will not get an
accurate preview otherwise ([see discussion](https://discuss.pixls.us/t/wide-gamut-preview-in-os-x/2481)),
while users of Linux and Windows will get a correct wide-gamut preview.

Go to Preferences \> [Color Management](/preferences#color-management-tab) and point the
"Directory containing color profiles" to the folder into which you saved
your monitor and printer ICC profile. Restart RawTherapee for the
changes to take effect. Now you will be able to select your monitor's
color profile in the combo-box under the preview. Use the "Relative
Colorimetric" rendering intent unless you have a good reason otherwise.

One can also enable soft-proofing of the preview. This will show you
what your image will look like once it gets transformed by the printer
profile set in Preferences \> [Color
Management](/preferences#color-management-tab). If you want to
adjust an image for printing and you have an ICC profile for your
printer-paper combination you could set that as your output profile,
enable "Black point compensation" in Preferences so that the blackest
black in your image will match the blackest black your printer-paper
combination is capable of reproducing, then enable soft-proofing. You
will see what your image will look like if you print it. This allows you
to make adjustments and get an instant preview of the result, saving you
time and ink on test prints.

The icon with exclamation mark next to the soft-proofing button will
gray out areas that cannot be reproduced by your printer, i.e. areas
where you will loose details.

You should have a calibrated and profiled monitor in order for the
soft-proofing preview to be accurate.

The items you see in the monitor profile combo-box (under the main
preview) and in the printer profile combobox (in Preferences \> [Color Management](/preferences#color-management-tab)) are ICC files
located in a folder which you can point RawTherapee to by going to
"[Preferences](/preferences) \> [Color Management](/preferences#color-management-tab) \> Directory
containing color profiles".
