---
title: Game Changer
contributors:
  - Jdc
tags:
  - 'Tool Description'
  - 'Tutorials'
toc: true
---

## Introduction : What is a "Game changer"?

‘Game changer’ - in French, the term ‘bouleverseur’ suits me well as a translation: it aims to change the usual way of thinking and acting in terms of image processing. Before changing the way we do things, we must first agree on the way we see things. In french a great sociologist, now deceased, said : "L'accord sur ma manière de faire est avant tout un accord sur la manière de voir" (Jean-Daniel Reynaud : 1926 - 2019).

This concept isn't about forcing you to change your image processing methods, but rather about trying a different approach based on principles that solve (at least partially, I believe) difficult image processing problems, using new concepts and methods. I'm not talking about tools here, but meta-methods: how to proceed and why this processing method is preferable to another for this type of image. There isn't a single method that works in all cases, but rather principles based on specific objectives.


### A bit of history - the implications of the context
* RT was conceived and created by a single man, Gabor Horvatz, in 2006. This is a fantastic achievement. However, this has consequences: the GUI interface has remained the same, prioritizing what was good, given the knowledge available at the time in 2006. 
* Today, the powerful modules are scattered across the different Tabs, and for my part, I almost never use them (with the exception of 'Highlight reconstruction') in the first two 'Tabs'.
* Other improvements have made some modules that were very good 10 years ago a little less so. I'm thinking of the excellent "Dynamic Range Compression" (which is mathematically complex), which is slow and resource-intensive...
* There are also the effects of fads; yesterday everyone was talking about "XXX", then "YYY"...and now "ZZZ", and since it's present elsewhere, why isn't it being developed in RT? This doesn't mean that "ZZZ" is better than "XXX".
* RT also has the unique characteristic of employing certain specific algorithms or processing methods. People may like it or dislike it, criticize it or approve of it, and compare it to what exists elsewhere. Before condemning, compare apples to apples (you wouldn't compare a chicken and a fish). I'm referring in particular to: CIECAM, Auto WB temperature correlation, Selective Editing, Wavelets, Abstract Profiles, etc.

### In summary: some principles
+ Start processing an image with no settings other than the default ones in 'Neutral', to avoid any side effects.
+ Use the maximum possible range for Raw data, this means that: 
  - The Black Point at the beginning of processing should be as close as possible to what the sensor allows.
  - The highest measurable values ​​on the sensor must be recorded at the White Point. Furthermore, it is desirable to be able to recover, as best as possible, the data lost when values ​​created by overexposure have saturated the sensor (see: Highlight reconstruction > Color Propagation)
+ Finding the best color balance is crucial before starting any treatments. The longer you wait, the greater the risk of 'contaminating' other methods.
+ Make the most of the possibilities in Raw mode, whether it be the demosaicing method, the improvement of sharpness and noise treatment, the correction of black points and chromatic aberrations, etc.
+ Control (and compress if necessary) the gamut at the beginning and end of the process.
+ Using the concept of a pre-tone mapping, which makes an image usable or (acceptable) for further processing. That is to say:
  - Bring the black point close to zero, to increase contrast and use the entire range of data.
  - Bring the White point as close as possible to 1: out-of-gamut data can have very high values ​​(3, 5 or 10), and all methods are more efficient when in the interval [0 1].
  - Implementing an asymptotic process that allows us to get closer to the white point, without reaching it - and even less going beyond it.
+ Towards the end of the process, it is possible to adjust the tones and contrasts, assuming that the image at this stage has no major defects (with the exception of images taken with exotic illuminants such as LEDs, which may require the use of primaries). This method should allow visualization of the effects on the acceptable limits for the data and the gamut.
+ At the very end of the process, it allows the implementation of the concepts of 'Scene' (source) and Viewing (display): taking into account the conditions of shooting and final viewing, taking into account the physiological aspects, allowing each R, G, B channel to be retouched to better balance or modify the colors.

Some current tools should be avoided – or at the very least, the user should be aware of the consequences of their choices:
+ Exposure compensation.
+ Auto-Matched Tone Curve.
+ Tone curve.
+ Auto Levels.
+ All sliders below 'Exposure compensation'
+ ...

Other tools must be used with caution, as they can interfere - it is almost impossible to review the pipeline - on Game Changer:
+ Haze removal
+ Contrast By Detail Levels
+ ... 

Prefer their equivalent in Selective Editing, taking care to place them "after" the pre-tone mapping.

You can use the tools to reduce noise, make crops, modify geometry, wavelets, etc.

But of course, there are no prohibitions; these are only general recommendations. Each image may be a special case.

**Recommendations**
+ It is best to alternate between viewing the histogram in linear mode with the Working profile, and in Output profile mode with a gamma.
<figure>
<img src="hist-lin-gam.jpg" title="hist-lin-gam.jpg" width="300" />
<figcaption>Histogram Linear or Gamma</figcaption>
</figure>

+ It is advisable to observe gamut spillovers with Softproofing - set to your personal profile.
<figure>
<img src="out-gamut.jpg" title="out-gamut.jpg" width="300" />
<figcaption>Softproofing out-of-gamut colors</figcaption>
</figure>

+ You can control the data at the time you implement a tool, these are just possible examples of values (uncorrelated with each other):
  - Gamut Compression: Maximium achromatique value: 3.2, then R:3.2 G:1.4 B=1.8 -- Estimated Cyan:1.5 Magenta:2.2 Yellow:2.8
  - Michaelis-Menten : Subtrack black = 0.05 White point=3.1
  - Generalized Hyperbolic Strech: RGB values- R:3.3 G:1.2 B=1.9
  - Abstract Profiles : RGB max = 0.92 - Final RGB Max = 0.62 - Final Saturation Max = 0.75
+ 'Normally', if everything was within the gamut, and if no processing caused it to be exceeded, the values ​​should all be within the interval [0 1]
+ If you find values (for the maximum) ​​for Gamut Compression, Michaelis-Menten, Generalized Hyperbolic Stretch:
  - That are less than 1 or close to 1. It's likely that Highlight reconstruction > Color Propagation (or Inpaint Opposed) won't help. In that case, disable it.
  - If these same values ​​are much greater than 1, for example 3.5 or 8, or more, the use of Color Propagation is recommended, and consequently it should not be disabled.
  - In the latter case, make sure that "Clip out-of-gamut colors" is disabled.
<figure>
<img src="color-propag.jpg" title="color-propag.jpg" width="300" />
<figcaption>Color Propagation - Clip out-of-gamut colors</figcaption>
</figure>

### Specific tools used
As of February 2026 - to be updated.
Apart from tools that have been around for many years, but are not always well known, I highlight new ones, or those that seem preferable to me:
+ Capture Sharpening (Raw Tab) - With Pre and Post sharpening denoise  [Capture Sharpening](/capture_sharpening/)
+ Color Propagation in Highlight reconstruction (Exposure Tab) [Highlight Reconstruction](/exposure/#highlight-reconstruction)
+ White Balance > Automatic & Refinement > Temperature correlation (Color Tab) [Temperature Correlation](/white_balance/#the-temperature-correlation-algorithm)
+ Gamut Compression (Color Tab) [Gamut Compression](/gamut_compression)
+ Selective Editing > Equalization & Pre-Tone Mapping : Generalized Hyperbolic Stretch (GHS) & Michaelis-Menten (MM) [GHS & MM](/local_adjustments/#generalized-hyperbolic-stretch-and-michaelis-menten)
+ Abstract Profile (Color Tab) [AP](/color_management/#abstract-profiles)
+ Color Appearance & Ligting (Advanced Tab) [CIECAM](/ciecam02)

## The tutorials

### Game Changer - How to Process a Sunset
To do

### Game Changer - Using LED's image
To do

### Game Changer - Noisy Image
To do

### Game Changer - A complete process on a user Rocks image
To do

### Game Changer - Using harvest mouse
To do

### Game Changer 

### Game Changer - Best Shadow & Higlight techniques 
In this tutorial, we will see how to use various tools to avoid or remove artifacts. Propose one solution among others to simultaneously brighten shadows, control highlights, and create a dramatic effect.
The image is difficult, and the question is: what should be done with it? Emphasize the dramatic aspect? Lighten or darken the shadows? There are as many answers as there are people.

**Image selection**

+ [Raw Image](https://discuss.pixls.us/t/show-your-best-shadow-highlight-techniques/55731)
+ This file is licensed [Creative Commons, By-Attribution, Share-Alike](https://creativecommons.org/licenses/by-sa/4.0/).

**Learning objective:**

The user will understand the ‘Game changer’ approach discussed in this tutorial:
+ The role of Raw Tabs tools.
+ The importance of Gamut Compression.
+ White Balance optimization - Temperature correlation.
+ The role of Graduated Filter.
+ The importance and settings of Abstract Profile
+ The combined use of Selective Editing > Generalized Hyperbolic Stretch (GHS) & Michaelis-Menten (MM) and 2 Exluding Spots.
+ The use of Color Appearance & Lighting and the possible corrections of the 3 channels R, G, B.

#### Raw tools

**Demosaicing**
+ The choice of Amaze+VNG4 allows for good detail rendering of structures and a possible reduction of artifacts in flat areas.
+ False color suppresion steps: setting it to 4 slightly reduces artifacts

**Raw Black points**
+ First, try the "Dehaze" checkbox; you'll see the sliders move to the right, the histogram expands, especially to the left (the shadow areas), and the image is brighter and more colorful: Red:+1, Green 1:+7, Green 2:+7, Blue:+2.
+ Second, increase the settings (by unchecking the 'Dehaze' box) : Red:+3, Green 1:+14, Green 2:+8, Blue:+5. You will again notice a more vivid image, a better utilized histogram, and a reduction in artifacts.

<figure>
<img src="raw-tools.jpg" title="raw-tools.jpg" width="300" />
<figcaption>Demosaicing & Raw Black Points</figcaption>
</figure>

Below, you can see the influence of Raw Black Point on the image at the end of the process.
+ Note the difference on the horizontal axis, close to zero.
+ Note that the overall histogram is better filled.
<figure>
<img src="rawblack-0.jpg" title="rawblack-0.jpg" width="300" />
<figcaption>Histogram without Raw Black point</figcaption>
</figure>

<figure>
<img src="rawblack-1.jpg" title="rawblack-1.jpg" width="300" />
<figcaption>Histogram with Raw Black point</figcaption>
</figure>

+ Be **very careful**, these settings are very sensitive and can contribute to making the images unusable.