---
title: Sharpening
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

Page prepared for referencing only. --[fherb](user:fherb)
([talk](user_talk:fherb)) 12:48, 14 March 2017 (MST)

------------------------------------------------------------------------

# Schärfung

Note: The *Sharpening* tool is computed **before** the *Resize* tool, so
if you set a resize value and were planning to adjust a post-resize
sharpness, it will not be possible at the moment. But if you resize your
image by a factor of 0.5 for example, you might want to double your
sharpening radius value. Unfortunately, sharpening cannot be previewed
at scales lower than 1:1.

## Unsharp Mask

[Unsharp masking](https://en.wikipedia.org/wiki/Unsharp_mask) (USM) is a
technique used to increase the apparent
[acutance](https://en.wikipedia.org/wiki/Acutance) (edge contrast) of an
image, making it appear clearer, even though it technically does not
really sharpen the image. It makes use of several phenomena of the human
visual system in order to accomplish this effect, such as the [Cornsweet
illusion](https://en.wikipedia.org/wiki/Cornsweet_illusion) and [Mach
bands](https://en.wikipedia.org/wiki/Mach_bands). Though unsharp masking
in other software is eas ily prone to causing
[halos](https://en.wikipedia.org/wiki/Haloing), RawTherapee has a unique
threshold slider which allows you to achieve a superb sharpening effect
without a minimal risk of halos.

### Radius

The Radius determines the size of the details being amplified and,
consequently, relates to the width of the sharpening halo. In general
the quality of sharpening is best if the sharpening radius is smaller.
For low ISO images that are in focus and without motion blur a value of
0.5-0.7 is satisfactory.

### Amount

The *Amount* parameter controls the strength of the sharpening.

### Threshold

[image:Usm_threshold.png](image:usm_threshold.png) The
*Threshold* tool helps to suppress noise amplification and haloing and
to confine sharpening to a desired tonal range. The Threshold tool
allows one to create a curve via which the sharpening is applied. The
vertical axis corresponds to opacity: 0% at the bottom (transparent,
sharpening not visible), 100% at the top (opaque, sharpening visible).
The horizontal axis corresponds to luminosity: select the tonal range
that will get sharpened - the darkest tones are on the left, progressing
to white tones on the right. As mentioned in the tooltip, to move each
of the points in the threshold tool individually, hold the Shift key
before clicking on a point with your mouse. Holding the Ctrl key while
moving a point with the mouse allows for very fine movements.

When moving the right pair of sliders to the left side, sharpening is
reduced in the highlights. When moving the left pair of sliders to the
right side, sharpening is reduced in the shadows and minimizes
amplification of dark noise.

The default threshold values will protect from over-sharpening and
haloing in most cases and limit the sharpening effect to mid-tones. In
the example screenshot, the blackest tones have no USM applied, then USM
is applied to a broad range of tones from dark to light, and the
strength of USM gradually drops off from maximal at the mid-tones to
none at the whitest tones, so as to prevent noise amplification and
haloing.

### Sharpen Only Edges

If you activate "*Sharpen only edges*" then uniform areas will not be
sharpened. This is useful when sharpening noisy photos.

Two new sliders appear as well:

#### Radius

The *Radius* is used for noise detection. If the noise is low, a lower
radius can be used, and vice-versa. A higher radius slows down the image
processing.

#### Edge Tolerance

*Edge Tolerance* determines how much a pixel has to differ from its
neighbor to be considered as an edge and not as noise. It is very
similar to the USM *Threshold* parameter and has a high impact on the
visual quality. For low ISO (low noise) images use 1000 or less, for
high ISO images use 2500-3000 or even more.

### Halo Control

*Halo Control* is used to avoid halo effects around light objects when
sharpening too aggressively. When activated, a new slider appears:

#### Amount

At 100 it works at maximum, reducing the visual impact of the USM
filter.

## RL Deconvolution

[RL
deconvolution](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
is named after the makers of this algorithm, Richardson and Lucy. Here
it is assumed that the image suffers from a Gaussian blur (like when
applying a Gaussian filter) which might be produced by the lens, motion,
etc. In reality the blur might come close to a Gaussian blur, but not
exactly. Therefore some artifacts like halos might occur when you try to
remove the Gaussian blur.

### Radius and Amount

You can define the *Radius* of the gaussian blur you want to remove.
When you set the Amount to 100 the gaussian blur will be removed
completely, but as this gives a harsh result a lower setting is
recommended.

### Damping and Iterations

The Damping is used to avoid sharpening of noise on smooth areas. As
deconvolution cannot be done perfectly at the first time several
Iterations are necessary. How much is changed between each iteration is
defined by the Richardson-Lucy algorithm. The more iterations are used
the more perfectly the gaussian blur is removed, but with each iteration
the speed decreases and the danger of halo artifacts rises. Normally you
don't want to remove the gaussian blur perfectly due to personal visual
taste and speed. The default settings should be fine most of the time.
