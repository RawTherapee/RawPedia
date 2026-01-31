---
title: Tone Mapping
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Exposure Tab'
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

# Dynamikkompression

The effects of this tool are visible at any zoom level. However, due to
the nature of the algorithm, only the 1:1 (or more) preview zoom will
match the saved image perfectly. If you are zoomed out at less than 1:1,
you should be aware that the preview can match the saved image very well
or not so well, depending on the "*Edge Stopping*" and "*Scale*"
sliders. Read the "[Getting the preview to match the saved
image](Tone_Mapping#Getting_the_preview_to_match_the_saved_image.md)"
section below. Use a detail window (click on the
[image:New-detail-window.png](image:new-detail-window.png)
icon under the [main preview
panel](The_Image_Editor_Tab#The_Preview_Panel.md)) to inspect a
part of the image, or zoom the main preview to 100% (also called 1:1)
[image:Gtk-zoom-100.png](image:gtk-zoom-100.png).

------------------------------------------------------------------------

![](Rt407-ba-tonemapping-hdr-cropped.jpg "Rt407-ba-tonemapping-hdr-cropped.jpg")
The Tone Mapping tool can be used to lift the dark areas of your photo
in a way that prevents halos from appearing, and it can be used to bring
out or suppress detail, to make the photo more crisp or more 'dreamy'.
Tone mapping adjusts the global contrast of an image differently from
the local contrast. Specifically, it's very useful for decreasing large
scale contrasts while preserving (or boosting) small scale contrasts.
The method used is taken from *Edge-Preserving Decompositions for Tone
and Detail Manipulation* with some modifications.

Note: tone mapping requires a lot of memory (RAM) and is CPU-intensive.

## Getting the preview to match the saved image

Image:Rt tm preview.jpg\|Edge Stopping=1.40 and Scale=0.10 while
editing, but Scale is set to 1.00 just before saving. Image:Rt tm
saved.jpg\|Using this trick, the preview matches the saved image very
well.

The effects of this tool highly depend on the size of the input image in
the engine's toolchain. To keep the preview fast, RawTherapee feeds each
tool with the image you see in the preview at the same resolution as the
preview, not the original, huge one (however, when you save an image, it
uses the original, huge one, which is why saving takes longer).
Processing a 900x600 image is much faster than processing a 7360x4912
one, for instance. The side-effects of this are that the zoomed-out
preview may not match the saved image, depending on the "*Edge
Stopping*" and "*Scale*" sliders.

You will find that the default values for this tool are Edge
Stopping=1.40 and Scale=1.00. These values generally lead to great
results, but specifically the Scale value is the one which leads to
differences between the zoomed-out preview and saved image. If you set
Scale=0.10 (the minimum) while tweaking your zoomed-out photo in
RawTherapee, and then, just before saving it, you change it to
Scale=1.00, the saved image will match the zoomed-out preview very well.
Use this trick to get the preview to match the saved image. It works
best when Edge Stopping is around 1.40. Remember that if you zoom the
preview to 100%, it will perfectly match the saved image regardless of
what slider values you use.  
==Interface Description ==

### Strength

This controls the strength of the overall effect. As of version 4.2.156,
as you increase the strength, shadows are raised and highlights are
slightly lowered in a way which aims to preserve the average luminance
of the image thereby preventing the washed-out look.

### Gamma

Gamma moves the action of tone-mapping to shadows or highlights.

### Edge Stopping

This parameter affects sensitivity to edges. The greater it is the more
likely an illumination change is to be considered an "edge". If set to
zero tone mapping will have an effect similar to [unsharp
masking](https://en.wikipedia.org/wiki/Unsharp_masking).

### Scale

This control gives meaning to the difference between "local" and
"global" contrast; the greater it is the larger a detail needs to be in
order to be boosted. See the note above on the influence this setting
has on the preview vs the saved image.

### Reweighting Iterates

In some cases tone mapping may result in a cartoonish appearance, and in
some rare cases soft but wide halos may appear. Increasing the number of
reweighting iterates will help fight some of these problems. When more
than zero reweighting iterates are used, the best results will be had if
the edge stopping parameter is set to one (technical detail: this
results in a 1-norm approximation of the smoothness using iteratively
reweighted least squares). Artifacts in high contrast edges may begin to
appear when this value is set to about 1.8 or higher.
