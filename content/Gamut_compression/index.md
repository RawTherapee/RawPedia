---
title: Gamut Compression
contributors:
  - Jdc
---

*Gamut Compression* Gamut is a tool which allows you to compress highly chromatic camera source colorimetry into a smaller gamut.

Out of gamut negative pixel values are problematic for working on images and should be avoided if possible.

Blue LED are perceive as highly colorful and colors like beetles, flowers and hummingbirds often over saturated.

This is not a gamut conversion : converting from one gamut to another does change the values of the pixels. 
However it does not actually change the colorimetric meaning of the pixel data. 
You could say that by converting between gamuts, you are changing frame of reference to the same colors.

This does not replace ‘highlight reconstruction’, but can at most complement it.

After compression the working profile is restored. Choose the workspace ‘Target Compression Gamut’ that will be used to set the gamut limits. Depending on the case you can choose:

The display gamut (sRGB, DCI P3,…).

The gamut of an output file for use by another software (Prophoto, Rec 2020…).

You can choose any working profile, preferably larger than the one for compression.

You have several settings available in addition to Target Compression Gamut:

- Threshold: controls the percentage of the outer gamut to affect. A value of 0.8 will compress out of gamut values into the outer 20% of the gamut. The inner 80% of the gamut core will not be affected.
  You can adjust the colors separately: for example if you wanted to protect magenta and yellow a little more than cyan, you could set the threshold a bit higher for cyan.

- Maximum Distance Limit: is the distance outside of the gamut boundary to compress to the gamut boundary. For example, a value of 1.2 will compress distance values of 1.2 to a value of 1.0. 
 Individual controls are given for each color component. They are named cyan, magenta and yellow because they actually control the max distance from the edge of the triangle (primaries related to the CIExy diagram), not the corner. For example, boosting the value of the cyan distance limit will increase the distance from which values are mapped to the edge between the blue and green corners of the triangle (primaries). The distance limits also control the RGB ratios of the compressed values, which affects the apparent hue.

- Power: Control the aggressiveness of the compression curve. Higher power values result in more compressed values distributed closer to the gamut boundary. This will increase the ‘color purity’ or
 ‘saturation’ once the image has been rendered through a display transform. Higher values have a smoother transition.

It is positioned in the pipeline (and writen in C++) just after the conversion to the working profile. So just after White Balance. I put this in the ‘Color’ Tab, just after ‘White Balance’. I wrote some tooltips that should make it easier to use.

**Generalized Hyperbolic Stretch - GHS**
GHS can also be considered a gamut compressor (see Selective Editing > Shadows/Highlights, Equalizer & GHS for more details on this tool's capabilities).

The system acts as a gamut compressor (a bit like 'Gamut Compression', but for the 3 RGB channels) and 'fits' the data into the gamut. Adjusting the (White Point linear) (for example, reducing it) will limit the maximum value. Adjusting the ‘Stretch Factor (D)’ and ‘Local Intensity (b)’ will allow you to focus on the area of ​​the image to be enhanced. If necessary to refine the colorimetry, you can use ‘Abstract profiles’ in particular the 'Custom (CIExy diagram)' part, 'Refine colors', Illuminants.


## Interface

- <figure>
  <img src="/images/Gamut-comp.jpg" title="Gamut Compression" />
  <figcaption>Gamut-comp.jpg</figcaption>
  </figure>


### Empirical adjustments Threshold & Maximum Distance Limit

The default settings (from Aces) are for a theoretical conversion between the ACES AP0 workspace and an ACES P1 target. 

On the other hand, these settings are relevant for cinema cameras. Of course, it's a matter of compromise.

What about for a still camera, such as a Nikon Z9 or Canon EOS R5 Mark II, etc.? What are the lighting sources at the time of shooting? LEDs, for example, can introduce very large out-of-gamut values—by a factor of 1 to 10.

What are we trying to achieve? Are we aiming to create a TIFF file for later use, or to adapt the image to a viewing screen, which itself has its own characteristics (SDR, HDR, peak luminance, etc.)?

Taking Colorchecker24 as a reference is, I think, an imperfect choice although I understand it as a possible model, because the colors of the Colorchecker24 are generally in sRGB, so if the user has a Rec2020 monitor... we're missing out...But we could discuss it endlessly.

In the case of RawTherapee, the default Working Profile is ProPhoto. Using numerous photos, I conducted various tests to provide the user with *"approximate values"* ​​based on the 'Target compression gamut'. These are indicative values, nothing more. It's up to you to adapt these values ​​to your own use, perception, and tastes.

Target compression gamut : **Rec2020**
- Threshold Cyan : 0.80
- Threshold Magenta: 0.79
- Threshold Yellow: 0.90

- Limits Cyan: 1.12
- Limits Magenta: 1.25
- Limits Yellow: 1.32

Target compression gamut : **Prophoto**
- Threshold Cyan : 0.86
- Threshold Magenta: 0.74
- Threshold Yellow: 0.90

- Limits Cyan: 1.17
- Limits Magenta: 1.24
- Limits Yellow: 1.30

Target compression gamut : **Adobe RGB**
- Threshold Cyan : 0.45
- Threshold Magenta: 0.81
- Threshold Yellow: 0.91

- Limits Cyan: 1.09
- Limits Magenta: 1.20
- Limits Yellow: 1.09

Target compression gamut : **sRGB**
- Threshold Cyan : 0.25
- Threshold Magenta: 0.82
- Threshold Yellow: 0.93

- Limits Cyan: 1.05
- Limits Magenta: 1.15
- Limits Yellow: 1.10

Target compression gamut : **DCI-P3**
- Threshold Cyan : 0.40
- Threshold Magenta: 0.87
- Threshold Yellow: 0.92

- Limits Cyan: 1.08
- Limits Magenta: 1.20
- Limits Yellow: 1.26




