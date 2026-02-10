---
title: Game Changer
contributors:
  - Jdc
tags:
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
  - The highest measurable values ​​on the sensor must be recorded at the White Point. Furthermore, it is desirable to be able to recover, as best as possible, the data lost when values ​​created by overexposure have saturated the sensor.
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

Other tools must be used with caution, as they can interfere - it is almost impossible to review the pipeline - on Game Changer:
+ Haze removal
+ Contrast By Detail Levels
+ ... 

Prefer their equivalent in Selective Editing, taking care to place them "after" the pre-tone mapping.

You can use the tools to reduce noise, make crops, modify geometry, etc.

But of course, there are no prohibitions; these are only general recommendations. Each image may be a special case.

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

### Game Changer - Best Shadow & Higlight techniques 
I will begin









