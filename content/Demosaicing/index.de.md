---
title: Demosaicing
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

Page prepared for referencing only. -- fherb
12:48, 14 March 2017 (MST)

------------------------------------------------------------------------

# Demosaicing

"Entmosaikieren", "Mosaikauseinandernehmung",
"Bildsensordaten-zu-Rastergrafik-Wandlung". Es gibt dafür bisher keine
deutsche Übersetzung. Was gemeint ist, kann aber gut [in Deutsch
beschrieben](https://de.wikipedia.org/wiki/Demosaicing) werden.

![](Chipincamera.jpg "Chipincamera.jpg")
![](Bayer_pattern_on_sensor.svg "Bayer_pattern_on_sensor.svg")
![](Bayer_pattern_on_sensor_profile.svg "Bayer_pattern_on_sensor_profile.svg")
Most digital cameras today use a [color filter
array](https://en.wikipedia.org/wiki/Color_filter_array) over their
sensors. To display such raw files their data needs to be
[demosaiced](http://www.cambridgeincolour.com/tutorials/camera-sensors.htm).
Cameras with a [Foveon X3
sensor](https://en.wikipedia.org/wiki/Foveon_X3_sensor) (Sigma) do not
have color filter arrays and so do not need demosaicing. Demosaicing is
why opening a raw file always takes a bit longer than opening a
[JPEG](https://en.wikipedia.org/wiki/JPEG) or
[TIFF](https://en.wikipedia.org/wiki/TIFF) file, where the data is
already 'display-ready'. RawTherapee offers several demosaicing
algorithms, each with its own characteristics. The differences between
them are often very subtle - one might need to zoom in to 200-400% to
discern them - but since the program works on a pixel-by-pixel basis and
demosaicing is the basis upon which all other tools work, the choice of
demosaicing algorithm can have a visually significant effect when
combined with other tools, such as the sharpening ones. The choice of a
certain algorithm influences, among other things, the quality of very
fine details in the image, whether false maze patterns will appear, and
decides how well colored edges are rendered.

RawTherapee supports demosaicing images from sensors with [Bayer
filters](https://en.wikipedia.org/wiki/Bayer_filter) and [Fujifilm
X-Trans
filters](https://en.wikipedia.org/wiki/Bayer_filter#Fujifilm_.22X-Trans.22_filter).
If you take a look inside the "Raw" tab, you will notice there are two
tools: "Sensor with Bayer Matrix" and "Sensor with X-Trans Matrix". The
settings in one of these two tools have no influence over the settings
in the other - if you open a raw image from a Bayer-type sensor, only
the settings from the "Sensor with Bayer Matrix" tool will be used, the
settings from the "Sensor with X-Trans Matrix" tool will be ignored, and
vice versa if you open a raw image from an X-Trans type sensor. For
simplicity, we will describe both here.

## Method

The following demosaicing algorithms are available for raw files from
Bayer sensors:

- AMaZE
- IGV
- LMMSE
- EAHD
- HPHD
- VNG4
- DCB
- AHD
- Fast
- Mono
- None

The following demosaicing algorithms are available for raw files from
X-Trans sensors:

- 3-Pass
- 1-Pass
- Fast
- Mono
- None

<div align="center">

Image:Demosaicing city1 amaze.png\|AMaZE Image:Demosaicing city1
igv.png\|IGV Image:Demosaicing city1 lmmse.png\|LMMS Image:Demosaicing
city1 eahd.png\|EAHD Image:Demosaicing city1 hphd.png\|HPHD
Image:Demosaicing city1 vng4.png\|VNG4 Image:Demosaicing city1
dcb.png\|DCB Image:Demosaicing city1 ahd.png\|AHD Image:Demosaicing
city1 fast.png\|Fast Image:Demosaicing city1 none.png\|None

</div>

Which demosaicing method should you use?

This page aims to tell you as much about the various algorithms as is
relevant to a photographer, but there is no much to say as the
explanations would quickly become technical and of a programmatical and
mathematical nature. After reading though this article you should know
that LMMSE and IGV are to be used on high ISO photos and that for the
majority of other cases you should stick with the default AMaZE method,
but of course you are free to explore for yourself and to test each
method out on your own raw files. It is of no use reading an article
somewhere on the internet which claims that some specific method is best
because in their test that method was the sharpest, as the performance
of each method depends specifically on the sensor in your camera and
even on ISO, so keeping our suggestions in mind, run your own test and
make up your own mind!

RawTherapee versions 4.2.91 and newer always use the demosaicing method
you choose regardless of zoom level. RawTherapee versions older than
4.2.91 use the Fast algorithm to initially open the image for editing.
After this, the selected demosaicing method is applied when the image is
zoomed to 100% magnification or when the detail window is opened. The
selected method is also used for batch processing. It is not recommended
to select the Fast method for the final conversion, as it is a
low-quality algorithm for display purposes.

**AMaZE** (Aliasing Minimization and Zipper Elimination) is the default
demosaicing method, as it yields the best results in most cases. In
RawTherapee versions 2.4 and older VNG4 used to be the preferred
algorithm for Olympus cameras, as AMaZE didn't exist yet and VNG4
eliminated certain maze pattern artifacts that might have been created
by the other methods, but with the introduction of the AMaZE method in
RawTherapee version 3.0 Olympus users might prefer that instead.

**DCB** produces similar results to AMaZE. AMaZE can often be slightly
superior in recovering details, while DCB can be better at avoiding
false colors especially in images from cameras without anti-aliasing
filters.

When working with very noisy, high ISO images in conjunction with the
[Noise Reduction](noise_reduction) tool, it is recommended to
use the **LMMSE** or **IGV** demosaicing methods. They will prevent
false maze patterns from appearing, and prevent the image from looking
washed-out due to heavy noise reduction.

If you use a medium format technical camera with near-symmetrical wide
angle lenses such as the Schneider Digitar 28mm or 35mm it's likely that
your file will contain some crosstalk, especially if the lens is shifted
(due to the low angle of incoming light from these lenses some light
leaks over to the next pixel on the sensor), and in this case you can
get mazing artifacts with AMaZE and DCB because of green channel
separation caused by the crosstalk. If you, via adapters, combine a
mirrorless camera with a wide angle lens designed for film, you may also
get crosstalk. It can then be better to use the more robust **VNG4**
algorithm (Variable Number of Gradients) which handles this situation
well, at the cost of some fine detail. An alternative is to enable green
equilibration to even-out the green channel differences.

**AHD** (Adaptive Homogeneity-Directed), **EAHD** (Horvath's AHD) and
**HPHD** (Heterogeneity-Projection Hard-Decision) are old methods which
are generally slow and inferior to the other methods.

**None** means no demosaicing is performed. This can be useful for
diagnostics, but you would not use it for photography.

**Mono** is only useful for users of either monochrome cameras, or
cameras with the color filter array removed.

**Fast** is a very fast but simple and low quality demosaicing method,
not recommended.

**3-Pass** is a demosaicing method for cameras with X-Trans sensors
(Fuji). It runs three passes over the image which leads to sharper
results though you can only see this on low ISO photos. It is slower
than 1-Pass.

**1-Pass** is a demosaicing method for cameras with X-Trans sensors
(Fuji). It is faster than the 3-Pass method though a bit inferior in
quality, though this difference is only visible in low ISO shots, so if
speed is an issue you can use this method on high ISO shots with no
visual difference in quality.

### False Color Suppression Steps

Sets the number of median filter passes applied to suppress demosaicing
artifacts when applying the demosaicing algorithm. False colors
(speckles) could be introduced during the demosaicing phase where very
fine detail is resolved. False color suppression is similar to color
smoothing. The luminance channel is not affected by this suppression.

False colors are generally more apparent in images from cameras without
anti-aliasing filters. Note that it is foremost the chosen demosaicing
algorithm which is the deciding factor in how prominent will be the
false color problem with which you will have to deal. In some situations
it may be better to change the demosaicing algorithm than to enable
false color suppression, as the latter reduces color resolution.

### How to Find the Best Demosaicing Method

[thumb](image:demosaicing_city1_example_bad.jpg) Zoom in to
at least 100% (1:1) and try all the demosaicing algorithms, see which
works best for you. Try them on sharp photos with fine detail and tiny
patterns, such as the wavy and repetitive fabric of a sweater (watch for
maze pattern artifacts), a distant brick wall, a distant round road sign
(watch for aliasing along the round edges), and test with both low and
high ISO shots. Use photos from your own camera; what's best for Nikon
raw images may not be what's best for Olympus ones.

### Monochrome Kameras

A monochrome camera has the same light filter in front of all pixels,
that is you get a black-and-white image and no demosaicing is required.
Some of these cameras have no infrared filter and are thus sensitive to
infrared light, which can be used for creative black and white
photography.

RawTherapee supports monochrome cameras, but the user interface is not
adapted for it so when you load a monochrome file all color tools will
still be enabled (they won't do anything meaningful of course). You will
have to live with that, monochrome cameras are rare so we won't put any
major effort into making the user interface morph into reduced
monochrome-only version.

There are a few additional factors to consider when working with
monochrome files: some monochrome cameras report that they have only a
single monochrome channel and a neutral color matrix, like Leica M
Monochrom, while others report RGB channels in a bayer configuration
(like Phase One IQ260 Achromatic, or IR-modified cameras). If the camera
reports only one channel, RawTherapee recognizes this and won't perform
any demosaicing (the demosaicer selection is still enabled but does not
do anything), and everything works normally. However, if the camera
reports as an RGB bayer camera, demosaicing will be performed and a
color matrix will be applied. To disable this, you should select the
"Mono" demosaicing option, and select "No profile" as [input
profile](Color_Management#Input_Profile.md) in the Color
Management panel.
