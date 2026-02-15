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
* A persistent problem, once you're no longer in Raw mode, is that the 'Preview', apart from 'fit to screen', is often different from the TIF/JPG output. Furthermore, the appearance varies significantly depending on the zoom level and the tools used. This is a pipeline design flaw... that hasn't been resolved (the consolation is that this problem, to varying degrees, is found in other software as well)... So you just have to live with it.
* There are also the effects of fads; yesterday everyone was talking about "XXX", then "YYY"...and now "ZZZ", and since it's present elsewhere, why isn't it being developed in RT? This doesn't mean that "ZZZ" is better than "XXX".
* RT also has the unique characteristic of employing certain specific algorithms or processing methods. People may like it or dislike it, criticize it or approve of it, and compare it to what exists elsewhere. Before condemning, compare apples to apples (you wouldn't compare a chicken and a fish). I'm referring in particular to: CIECAM, Auto WB temperature correlation, Selective Editing, Wavelets, Abstract Profiles, etc.

### In summary: some principles
+ Start processing an image with no settings other than the default ones in 'Neutral', to avoid any side effects.
+ Use the maximum possible range for Raw data, this means that: 
  - The Black Point at the beginning of processing should be as close as possible to what the sensor allows.
  - The highest measurable values ​​on the sensor must be recorded at the White Point. Furthermore, it is desirable to be able to recover, as best as possible, the data lost when values ​​created by overexposure have saturated the sensor (see: Highlight reconstruction > Color Propagation  - which, contrary to what its name suggests, also allows data to be retrieved in very low light conditions).
+ Finding the best color balance is crucial before starting any treatments. The longer you wait, the greater the risk of 'contaminating' other methods.
+ Make the most of the possibilities in Raw mode, whether it be the demosaicing method, the improvement of sharpness and noise treatment, the correction of black points and chromatic aberrations, etc.
+ Control (and compress if necessary) the gamut at the beginning and end of the process.
+ Using the concept of a pre-tone mapping, which makes an image usable or (acceptable) for further processing. That is to say:
  - Bring the black point close to zero, to increase contrast and use the entire range of data.
  - Bring the White point as close as possible to 1: out-of-gamut data can have very high values ​​(3, 5 or 10), and all methods are more efficient when in the interval [0 1].
  - Implementing an asymptotic process that allows us to get closer to the white point, without reaching it - and even less going beyond it.
  - This principle is included in 'Selective Editing > Equalization & Pre-tone mapping': The first RT-spot used must always be (if of course there is a need) a Pre-tone mapper in Global mode.
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

This is partly due to the pipeline - the order in which operations are actually carried out, not the order in which you do them.
[Pipeline](/toolchain_pipeline)

You can use the tools to reduce noise, make crops, modify geometry, wavelets, etc.

But of course, there are no prohibitions; these are only general recommendations. Each image may be a special case.

#### Recommendations
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
  - In the latter case, make sure that 'Clip out-of-gamut colors' is disabled.
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
  - Tone Response Curve [AP - TRC](/color_management/#trc---tone-response-curve)
  - Contrast Enhancement [AP-CE](/color_management/#contrast-enhancement), in particular how it works [Presets](/color_management/#each-preset-contains-a-selection-of-decomposition-levels), and [Characteristics](/color_management/#the-contrast-enhancement-module-has-the-following-characteristics)
  - Illuminant White Point [AP - IWP](/color_management/#illuminant---white-point)
  - Primaries [AP - Prim](/color_management/#primaries) 
+ Selective Editing > Blur/Grain & Denoise > Denoise [SE-denoise](/local_adjustments/#selective-editing----blurgrain--denoise--denoise)
+ Color Appearance & Lighting (Advanced Tab) [CIECAM](/ciecam02)

## The tutorials
The first tutorial, 'Best Shadows & Highlights Techniques', is the most detailed in its explanation of each method or tool (except for noise reduction). To avoid overloading the other tutorials with repetition, prior knowledge of the explanations will be assumed.

### Game Changer - Best Shadows & Higlights techniques 

In this tutorial, we will see how to use various tools to avoid or remove artifacts. Propose one solution among others to simultaneously brighten shadows, control highlights, and create a dramatic effect.
The image is difficult, and the question is: what should be done with it? Emphasize the dramatic aspect? Lighten or darken the shadows? There are as many answers as there are people.

This image is a real challenge: usually we struggle with highlights, but here there are both highlights and, above all, very (very) low highlights, where the values ​​are very close to zero, even at zero for the Red channel, the Green channel, and a very small value for the Blue channel, or even at zero for all three channels.

Beyond the aesthetic aspect of the result, there is above all a technical challenge in terms of methods.

I deliberately chose extreme settings to show that even with a 'degraded' starting image it is possible to obtain a more than acceptable result, for example the "Contrast Enhancement" values ​​are huge.

 [Some principles](/tutorials/#in-summary-some-principles)

 [Recommandations](/tutorials/#recommendations)

 [Specific tools used](/tutorials/#specific-tools-used)

**Image selection**
+ [Raw Image](https://discuss.pixls.us/t/show-your-best-shadow-highlight-techniques/55731)
+ This file is licensed [Creative Commons, By-Attribution, Share-Alike](https://creativecommons.org/licenses/by-sa/4.0/).

- pp3 file 1: [First example with Color Propagation](1q8a5461.cr3-jd-std.pp3 "first-cp.pp3")
- pp3 file 2: [Second example with Color Propagation and blur](1q8a5461.cr3-jd-blur.pp3 "second-cp-blur.pp3")

**Image : neutral**
+ Here is a screenshot of the image in 'neutral' mode with 'Lockable Color Pickers'. You can immediately see that the photographer has underexposed the overall frame to avoid overexposing the sunset sky. Despite this choice, potential artifacts are already appearing in the area of ​​the sky near the power pole. See also the histogram in 'linear' mode.
<figure>
<img src="neutral-1.jpg" title="neutral-1.jpg" width="500" />
<figcaption>Image - Neutral</figcaption>
</figure>

If you examine:
+ The Raw histogram, it's not 'abnormal' except for very few values ​​outside the shadows. The blue channel is dominant.
+ The Metadata: the camera used is a recent 24x36 camera - Canon EOS R6 with a good quality 50mm f/1.8 lens, open to 2.8. ISO = 100. Shooting in 'auto' mode.
+ The data is in the 'black' part of the image: in short, there are two groups: values ​​with R=0.4%, G=0.4%, and B=0.4%, and others with R=0%, B=0%, and G=0%. In Lab mode, there are values ​​with L=0, a=1, and b=-4 (which is theoretically impossible).
+ As soon as we want to act on something, we see (of course, with the help of the histogram, the soft proofing, and of course, the examination of the image), many artifacts appear:
  - In the deep shadows, numerous 'green dots' appear.
  - The area near sunset is dotted with artifacts of several types.
  - The transition zones in the sky, between the reddish clouds and the blue, show very poor transitions.

**Learning objective:**

The user will understand the ‘Game changer’ approach discussed in this tutorial:
+ The role of Raw Tabs tools, in particular to combat artifacts
+ The importance of Color Propagation, including in (very) deep shadows.
+ The importance of Gamut Compression.
+ White Balance optimization - Temperature correlation.
+ The role of Graduated Filter.
+ The importance and settings of Abstract Profile - with a reasoned use of primaries
+ The combined use of Selective Editing > Generalized Hyperbolic Stretch (GHS) & Michaelis-Menten (MM) and 2 Excluding Spots.
+ The use of Color Appearance & Lighting and the possible corrections of the 3 channels R, G, B.

I will present two possible processing methods using two pp3 files. I will describe the first; the reader can discover the second for themselves. The essential difference lies in the 'Color Propagation' and 'Raw Black Points' settings.

I've separated the tools as they appear in the interface, but it would be more accurate to refer to them as Raw processes. From my perspective, tools like 'Color Propagation', which is activated immediately after assigning the 'Working Profile', and 'White balance Temperature correlation', which is activated immediately after demosaicing, fall under the 'Raw' category.

Do not attempt to reduce noise, whether using in 'Capture Sharpening', 'Presharpening denoise', 'Postsharpening denoise', or 'Noise reduction' (Detail tab); you will only degrade the image. The only option, if desired, is to add an additional RT-Spot to the sky (or part of the sky) using 'Selective Editing > Blur/Grain & Denoise > Denoise'.

#### Raw tools

##### Demosaicing
+ The choice of Amaze+VNG4 allows for good detail rendering of structures and a possible reduction of artifacts in flat areas.
+ False color suppresion steps: setting it to 4 slightly reduces artifacts

##### Raw Black points
The 'Dehaze' system designed by Ingo Weirich suggests here, due to the difference between the values ​​R=0, G=0, B=0 and the very low values ​​R=0.4%, G=0.4%, B=0.4%, that it's a haze problem... I think that's not the case. We're dealing with data corruption here... just like what happens in highlights.

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

##### Chromatique Aberration Correction
+ We can reduce some minor artifacts caused by Chromatic Aberration by manually adjusting the red and blue channels
<figure>
<img src="chromatic-aber.jpg" title="chromatic-aber.jpg" width="300" />
<figcaption>Chromatic Aberration Correction</figcaption>
</figure>

##### Preprocess White Balance
I chose "Camera" which seems to give a better result. During the Raw pre-processing, when nothing is determined, it's necessary to choose a temperature to quantify the data. This is either the 'Camera' value present in the Exif, or a rough calculation done with 'Automatic RGB Grey'.
<figure>
<img src="prepro-wb-1.jpg" title=prepro-wb1.jpg" width="300" />
<figcaption>Preprocess WB</figcaption>
</figure>

##### Capture Sharpening
+ Activating Capture Sharpening works without any problems. The contrast threshold is not set to zero. It will recover details lost due to in-camera blurring.
<figure>
<img src="capture-shar.jpg" title="captur-shar.jpg" width="300" />
<figcaption>Capture Sharpening</figcaption>
</figure>


#### Color Propagation
+ Observing the reaction of the modules mentioned in the recommendations, the contribution of "Color Propagation" is small on the 'numbers', but not negligible. On the other hand, and this is its initial role, it allows the recovery of 'lost' data in highlight, but also in very low light.
+ If you try another tool in 'Highlight reconstruction', such as 'Inpaint opposed' you will see that it has no effect on very low lights.
+ The first example is without the 'Blur' slider in 'Color Propagation' being activated. This slider allows you to adjust the transitions between 'recovered' (and therefore lost) areas and healthy areas. This also led to a change in the 'Raw Black Points' setting.
  - [Recommandations](/tutorials/#recommendations)

#### White Balance - Temperature correlation
+ To fully utilize the capabilities of "White Balance Auto temperature correlation", you can activate the corresponding checkbox in Preferences > Color Management
<figure>
<img src="prefer-wbauto.jpg" title="prefer-wbauto.jpg" width="500" />
<figcaption>Preferences - Color Management</figcaption>
</figure>

+ Once this choice is made, you can select 'Close to full CIE diagram', because clearly with this sky we are beyond the reflected colors and the default selection 'Medium sampling - near Pointers's Gamut'.
+ You can also check 'Remove 2 pass algorithms' which seems to give a slightly more 'dramatic' result (but that's a matter of perspective). 
+ You could also, but it doesn't seem necessary here, use 'Green refinement' which can in some cases compensate for the algorithm's shortcomings.
<figure>
<img src="white-bal-auto-1.jpg" title="white-bal-auto-1.jpg" width="300" />
<figcaption>White Balance - Temperature correlation</figcaption>
</figure>

+ The automatic calculation always performs two passes: the first with the base results, and a second to try to get closer to D50, thus avoiding color adaptation (which can be done in "Automatic Symmetric" mode using Color Appearance & Lighting). The choice is up to the user. Among the criteria is the 'Correlation factor'; the smaller it is, the better. The other criterion is the 'Size', which is the number of colors found to be significant for comparison with the reference spectral colors (approximately 400). The larger the 'Size', the better.

#### Gamut Compression
+ As a reminder, this algorithm does not perform a "conversion" but compresses the data to the output profile (in linear mode, without gamma). It will ensure, at _a minima_, that the data will be within the gamut. Hence the importance of examining the histogram in mode 'gamma-corrected **output profile**'
<figure>
<img src="gamut-comp-1.jpg" title="gamut-comp-1.jpg" width="300" />
<figcaption>Gamut Compression</figcaption>
</figure>

+ I made a few small changes to the default settings, but you can try modifying all 3 'Threshold' values ​​as well as 'Rolloff & Power'.

#### Selective Editing - Five RT-Spots

##### The first - Equalization & Pre-Tone Mapping - Michaelis-Menten (MM)
<figure>
<img src="michaelis-1.jpg" title="michaelis-1.jpg" width="300" />
<figcaption>Michaelis-Menten Global mode</figcaption>
</figure>

+ I used this module (MM) rather than (GHS), not because it's simpler, but because, unlike GHS, it doesn't rely on an algorithm to calculate 'Linear White Point', and especially 'Linear Black point' in this case. When I designed GHS, I assumed that a reduced value of 0.001 was negligible; however, it isn't here, in this very specific image, and necessitates a manual correction (in negative) of the Black point. A smaller value, for example 0.000001, should have been used, but that would break compatibility.
+ Note the preferred use of the two 'hyperbolic' parameters - Output scale (S) and Knee strength (K). Exposure (Ev) is considered only as an adjustment.
+ Note the use of checkboxes (uncheck them all first). Start with 'Subtract linear black'; you'll see the histogram compress towards the left, even with the work done beforehand in the Raw section. Then activate 'Linear dynamic range'; the histogram will be compressed by roughly 1.18 (see the values ​​displayed below). The asymptote for highlights will be better defined, and contrast and saturation will increase.
+ The other settings - which are also important - are part of the chain of mastering gamut and artifacts.

##### The second - Equalization & Pre-Tone Mapping - Generalized Hyperbolic Stretch (GHS)
<figure>
<img src="ghs-plus-1.jpg" title="ghs-plus-1.jpg" width="600" />
<figcaption>GHS lightens the shadows</figcaption>
</figure>

+ Choose a Normal RT-Spot 'Rectangle', with a small Scope value, so as not to interfere with the sky. Of course, DeltaE and transitions apply; the limits of the RT-spot are of little importance.
+ Due to RT issues with the Preview, set the image to 'fit to screen', and enable 'Auto Black point & White point'. Then disable it.
+ Activate 'Auto Symmetry point (SP)'.
+ Adjust 'Stretch factor (D)' and 'Local intensity (b)' to achieve the desired effect.

##### The third - Color & Light - Excluding Spot
<figure>
<img src="color-light-excl-1.jpg" title="color-light-excl-1.jpg" width="600" />
<figcaption>Excluding spot - remove artefacts - changes color</figcaption>
</figure>

+ This Spot Exclusion will undo all changes and allow you to add more. It will remove (at least partially) some of the artifacts and amplify the sky color to make it more dramatic.
+ Note the use of 'Color correction grid'


##### The fourth - to reduce artifacts
<figure>
<img src="exclu-1.jpg" title="exclu-1.jpg" width="400" />
<figcaption>Excluding spot - remove artefacts</figcaption>
</figure>

##### The fifth Equalization & Pre-Tone Mapping - Standard - (GHS) increases the dramatic aspect of the sky
<figure>
<img src="ghs-moins-1.jpg" title="ghs-moins-1.jpg" width="600" />
<figcaption>GHS - Inverse mode - increases the dramatic aspect of the sky</figcaption>
</figure>

+ To enhance the dramatic effect of the sky, I used GHS's 'Inverse' mode, which allows it to either reverse the image or reduce contrast and highlights. That's what was done here.
+ Note the need to switch the complexity mode to 'Standard' to have the 'Inverse' mode available.
+ Activate 'Auto Symmetry point (SP)'.
+ Adjust 'Stretch factor (D)' and 'Local intensity (b)' to achieve the desired effect.

#### Graduated Filter
<figure>
<img src="grad-fil-1.jpg" title="grad-fil-1.jpg" width="600" />
<figcaption>Graduated Filter - increases the dramatic aspect of the sky</figcaption>
</figure>

+ Nothing new here, I'm using a tool that's been around in RT for a long time. I could have used the same tool found in Selective Editing associated with each tool, but except for 'fit to screen', it's sensitive to the Preview's dimensions.
+ I positioned it to increase the contrast (more dramatic effect) between the clouds and the rest of the image.

#### Abstract Profile
I'll proceed in two steps. First, adjust the tones and check for any potential excesses in the histogram and gamut. Second, have some fun with the 'Primaries & Illuminants' module.

##### TRC Adjust the tones - Contrast Enhancement
<figure>
<img src="ap-trc-contrast-1.jpg" title="ap-trc-contrast-1.jpg" width="600" />
<figcaption>Abstract Profiles - TRC and Contrast Enhancement</figcaption>
</figure>

+ Note the gamma and slope settings (which is a seamless function) that connect a straight line with a slope value of 'Slope' to a parabolic curve with a 'Gamma' value. You are manipulating the balance of shadows and highlights.
+ The other settings are fairly intuitive. Note the importance of 'Attenuation threshold' which acts asymptotically on highlights.
+ For Contrast Enhancement, note the very high value of both Contrast profile (5), which leads to modifying the contrast from 2x2 pixel groups up to 1024x1024 (if the size of your Preview allows it), and the curve which is almost at its maximum. The system uses only wavelets, and only for signal processing. 'Normally' as it is designed, it should not (or very little) generate artifacts. The goal here is to make the whole image more dramatic (it is certain that for a portrait, or traditional images, the basic settings are sufficient).

###### RGB Max - informations
Provides information on out-of-limit RGB values. Values greater than 1 clearly indicate that we are out of gamut whereas for values less than 1, we cannot say whether the image is within gamut or not because it depends, for example, on the luminance. This check is performed at the end of the Abstract Profile and takes into account all parameters. The ‘Attenuation threshold’ slider can be used to limit the RGB values.

Changes made to 'Color Appearance and Lighting', 'Final Gain and Gamut Compression' are not taken into account. 

###### Final RGB Max & Final Saturation Max - informations
Provides information on out-of-limit RGB values and RGB saturation. Values greater than 1 for ‘Final RGB Max’ and ‘Final Saturation Max’ clearly indicate that we are out of gamut whereas for values less than 1, we cannot say whether the image is within gamut or not because it depends, for example, on the luminance. This check is performed at the end of the processing pipeline and takes into account all parameters. Changes made in Color Appearance & Lighting and in Final Gain & Gamut Compression are taken into account.

Adjusting the Gain (Ev) and Gamut Compression (Target Gamut and Power) settings will allow you to see the impact of these adjustments. You should also observe the histogram, which takes into account the output profile therefore the gamma. This data, which is directly related to the RGB values ​​and Saturation and is in the Working Profile, is in linear mode.

The data is only displayed if Target Gamut is enabled, or if Gain (Ev) is not equal to 0.


##### Primaries & Illuminants
The objective here is twofold:
+ Accentuate the dramatic aspect of the image by strongly increasing the colors in the reds and yellows.
+ To show that primaries can also be used in RT (this was initially one of the goals of Abstract profile, to allow color effects).
<figure>
<img src="ap-prim-1.jpg" title="ap-prim-1.jpg" width="300" />
<figcaption>Abstract Profiles - Primaries & Illuminants</figcaption>
</figure>

+ Note that I used polar coordinates to make this modification of the primaries. I could have done it directly with the CIExy diagram, or in linear mode.
+ Note that if instead of increasing the saturation, I had reduced it, we would have gone outside the CIExy diagram, hence the generation of imaginary colors.
+ Note that I've changed the 'White point' of the internal ICC profile to D41. When you change it, you change the dominant color. The primary rotation is done from this 'new' White point.

#### Color Appearance & Lighting
I would like to remind you that this concept is one of the most advanced methods for color management. It is a Color Appearance Model, based on the work of researchers from around the world; its first version (in the form of an Excel spreadsheet) dates back to 1997. Its current name is CIECAM16 (published in 2020).

+ It takes into account (I'm simplifying drastically):
  - The concepts of 'scene' (source) and 'viewing' (display).
  - The separation into 3 processes, with image processing in the middle.
  - The shooting conditions (e.g., Absolute luminance), viewing conditions (the image does not look the same in a dark or bright environment...).
  - Numerous physiological aspects such as simultaneous contrast, etc.

In this tutorial, I will present it briefly in 2 parts: 
+ The main settings.
+ Those dedicated to modifying each R, G, B channel to finely retouch colors or simulate films.

##### CIECAM - main settings
<figure>
<img src="ciecam-scene-images-1.jpg" title="ciecam-scene-images-1.jpg" width="300" />
<figcaption>CIECAM Scene & Image Adjustments</figcaption>
</figure>

+ I chose not to adjust the automatic settings (Chromatic Adaptation Scene, Absolute luminance, Mean Luminance (Yb%), Surround).
+ I chose 'Lightness + Chroma' and modified the values ​​as shown in the attached image.

<figure>
<img src="ciecam-curves-viewing-1.jpg" title="ciecam-curves-viewing-1.jpg" width="300" />
<figcaption>CIECAM Curves & Viewing Conditions</figcaption>
</figure>

+ I chose not to adjust the automatic settings (Chromatic Adaptation Viewing, Absolute luminance, Mean Luminance (Yb%), Surround). But this is where you can (must) adapt the image you see to the Viewing conditions (yours).

##### CIECAM - Red Green Blue
+  You can modify each R, G, B channel to finely retouch colors or simulate films:
  - Rotate each color by degrees.
  - Change the saturation (s) in the sense of a CAM (Color Appearance Model).
  - Change the brightness (Q) with a curve that allows you to adapt the contrast and brightness to each situation.

+ As a reminder, in CIECAM there are a total of 9 variables, 6 of which are accessible to the user in RT: Lightness (J), Brightness (Q), Saturation (s), Chroma (C), Colorlness (M), and Hue rotation (h). They are interdependent. For example Chroma = saturation * saturation * brightness.

<figure>
<img src="red-green-blue-1.jpg" title="red-green-blue-1.jpg" width="300" />
<figcaption>CIECAM Red Green Blue</figcaption>
</figure>

+ For this challenging image, I made a point of moderating the settings to avoid artifacts.

#### Appearance of the result at the end of treatment
+ Of course, nothing is perfect, and there remain small artifacts only visible during softproofing.
+ I wanted to make the image as dramatic as possible, perhaps even going too far. But let's remember the objectives; this is first and foremost an educational approach.

<figure>
<img src="final-1.jpg" title="final-1.jpg" width="800" />
<figcaption>Game Changer - Final Image</figcaption>
</figure>


### Game Changer - How to Process a Sunset
This first tutorial aims to explain the concept of a ‘Game changer’ here applied to a sunset.

In this tutorial, we will see how to use:
+ Generalized Hyperbolic Stretch (GHS) in 2 modes: RGB Standard & RGB Luminance.
+ Michaelis-Menten (MM).
+ Abstract Profile (AP).
+ Color Appearance & Lighting.

Of course, other tools are necessary; we will see them later.

Image selection:
Image n°5 IMGP2426.DNG from the Rawtherapee Processing Challenge feedback (begin 2024)

[Raw Image](https://drive.google.com/file/d/17R3iBq08s71DuDRiv9T6TzlJVsxqBISo/view)

Raw file (Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License)

This image seems innocuous at first glance, a typical sunset. The image is generally underexposed, and the sun doesn’t appear overexposed.

- pp3 file 1: [First example with Generalized Hyperbolic Strech - RGB Luminance](i2426-ghs-lum.pp3 "i2426-ghs-lum.pp3")
- pp3 file 2: [Second example with Generalized Hyperbolic Strech - RGB Standard](i2426-ghs-std.pp3 "i2426-ghs-std.pp3")
- pp3 file 3: [Third example with Michaelis-Menten](i2426-mm.pp3 "i2426-mm.pp3")

 [Some principles](/tutorials/#in-summary-some-principles)

 [Recommandations](/tutorials/#recommendations)

 [Specific tools used](/tutorials/#specific-tools-used)

**Learning objective**

The user will understand the ‘Game changer’ approach discussed in this tutorial:
+ The role of ‘GHS’ or 'MM' in the linear portion of the data, which can be considered a ‘Pre-tone-mapper’
+ The role of ‘Abstract Profile’, which prepares the data for use in the output (screen, TIFF/JPG).
+ Minimize the use of other tools, aside from those essential for the proper functioning of RawTherapee, GHS, MM, and AP, and reduce back-and-forth navigation within the GUI.
+ Highlight the tools to avoid and those that can be beneficial.
+ The settings (sliders, checkboxes, etc.) are provided for illustrative purposes. They are not intended to provide perfect settings, but rather to show the way forward.

#### First step: GHS - MM  and necessary adjustments
+ Deactivate everything, switch to ‘Neutral’ mode
+ Activate ‘Capture Sharpening’ (Raw Tab): check that ‘Contrast threshold’ displays a value other than zero. Otherwise, it means it is not operational (noisy image). Resolving this potential problem related to noisy images will be covered in a later tutorial.
+ The image was taken outdoors at sunset, therefore with a daylight illuminant, so there is no problem setting the white balance (Color Tab) to ‘Automatic & refinement > Temperature correlation’.
+ In the Exposure Tab, disable ‘Clip out-of-gamut colors’, enable ‘Highlight reconstruction’, and zoom the image to 100% while examining the sun. Try ‘Inpaint Opposed’, ‘Blend’, and ‘Color Propagation’. For each case, re-enable ‘Clip out-of-gamut colors’ and observe the differences. The image without artifacts (I think?) is with ‘Color Propagation’ and ‘Clip out-of-gamut colors’ disabled. Try ‘Blur’ (Color Propagation) to see if artifacts at transitions appear or disappear. ‘Blur’ is finally set to 0.

#### Using Generalized Hyperbolic Stretch (GHS)

##### Preamble

I won’t compare it to other tone mappers in RawTherapee or other software, using tables or a pros/cons list. That would be tedious and probably not very interesting from a user’s perspective. I will simply (given the lack of documentation) draw your attention to the specific points that are crucial:
+ Setting the ‘White point (linear)’ (WP)  and ‘Black point (linear)’ (BP) is THE first fundamental aspect of its operation. It is done entirely in linear mode (unlike Black Ev and White Ev). It is dynamic, meaning that each new session (for example, when creating a second RT Spot) recalculates and triggers the GHS algorithm. Consequently, the values ​​are always accurate (at least in theory). Preferably, use the ‘Auto Black point & White point’ checkbox (except in Inverse mode). This setting is only accessible if ‘Stretch factor (D)’ is between 0.001 and 0.002. These very low values ​​will have little effect on the image, but they allow adjustments to ‘White Point (linear)’ and ‘Black Point (linear)’ and enable the GHS algorithm to function
+ To understand how this works in the simplest way possible, let’s assume that the base data, before the calculation and implementation of ‘BP’ and ‘WP’, is in the range [0, 1] (this is rarely the case)… If the ‘auto’ setting for ‘BP’ is 0.05 and ‘WP’ is 3.05. This means that if we do nothing, the actual data after the ‘Color Propagation’ action would be 0.05 for the BP (resulting in a loss of contrast due to an excessively high black point) and a WP of 3.05, which will be incompatible (or very poorly handled) by the majority of Rawtherapee’s algorithms, which are not at all designed to work with huge values, often resulting in data clipping, color drift, etc. The RGB data will be transformed by dividing the actual values ​​by a factor equal to the difference between ‘WP’ and ‘BP’, which here is 3.05 - 0.05, therefore 3. This means that the data we saw in the ‘Preview’ which was in the range [0, 1] becomes [0, 0.33]. The image becomes extremely dark, but the sun enters the gamut with a value of 1.
+ The second factor to consider, and one that caused me a lot of problems, is determining the ‘Symmetry Point (SP)’ value. Theoretically, this is the peak of the luminance in the histogram in linear mode. In astrophotography software, the user clicks on an area that seems most promising. This seems quite obvious: the brightest nebulae located near stars. The ‘SP’ is then adjusted to the value found. In the case of general-purpose images, I challenge anyone to find the area where the histogram (luminance portion) has its maximum in both Working Profile and Linear modes. This ‘SP’ is THE second key point that determines how the algorithm works. It has little to no relation to mid-grey. GHS’s complex calculations use a variety of complex hyperbolic functions, depending on the values ​​of ‘SP’, ‘Stretch factor (D)’, and especially ‘Local Intensity (b)’. These functions provide an asymptote to the luminance for highlights and adjust the amplitude range (increasing or decreasing) of the data within the interval [0-1] to make the image acceptable. By default, leave the ‘Symmetry point (SP)’ slider checkbox set to Automatic.
+ Of course, I suggest you try modifying these ‘auto’ settings and changing ‘Color Propagation’ to something else. Uncheck the ‘auto’ boxes, set ‘Stretch factor (D)’ to 0.001 (default), change ‘SP’, and change ‘WP’ and ‘BP’. … Just to see the effects and potentially find better settings.
+ The ‘GHS Curve Visualization’ has very little relation to a ‘Tone curve’, it only reflects the action of hyperbolic functions and not the direct action on tones.

##### Adjusting ‘Stretch factor (D)’ and ‘Local Intensity (b)’
‘Stretch factor (D)’ will stretch (and compress) the image data according to the areas. It is a logarithmic function (but has absolutely no relation to Filmic or Log encoding). You will notice that there are only positive values ​​– we are working in ‘positive space’. If you want to use the equivalent of negative values ​​(which is impossible with a Log function), you must switch to ‘Inverse GHS’ mode, which activates ‘negative space’ mode. We will see this later.
’Local intensity (b)’ will localize the effect of Stretch. Depending on its value, hyperbolic functions of very different natures will modify the data (the only point in common with Sigmoid is the term hyperbolic). 

##### The advantage of doing multiple stretches
Rather than attempting a single stretch, in the case of images with a high WP (3 to 5), which will require a high 'Stretch factor (D)', or where the user will have difficulty locating the area where action should be prioritized, it is better to perform two stretches. The first, with moderate values, will place the data in the interval [0-1], while the second will allow for better localization of the action.

+ Note that GHS settings can cause data (depending on the GHS settings) to fall outside the [0, 1] range, both in linear and output data. Constantly monitor the histogram in both modes (working profile - linear and output profile - gamma) and make any necessary corrections.
+ In ‘Stretch Regularization & Midtones’, you ca set the value (LC) – the local contrast – to zero to avoid artifacts in the sun area. Local contrast can be addressed later in Abstract Profile.
+ To see the effects, instead of a single ‘Stretch factor (D)’ with high values, you can try constructing the stretch using two RT-spots. The first with lower (D) and (b) values. The second with values ​​adjusted to your preference. You’ll see that for this second RT-spot, the values ​​of (BP) will be close to zero, and those of (WP) very close to 1.0 (minor adjustments are possible). The image will be different, the sun less prominent.

###### First Spot - GHS
<figure>
<img src="first-ghs-2.jpg" title="first-ghs-2.jpg" width="300" />
<figcaption>GHS - first spot - Low Strech factor</figcaption>
</figure>

###### Second Spot - GHS
<figure>
<img src="second-ghs-2.jpg" title="second-ghs-2.jpg" width="300" />
<figcaption>GHS - second spot</figcaption>
</figure>

##### Inverse GHS
This function, not available in Selective Editing’s ‘Basic’ complexity mode, allows you to undo previous actions on all (somewhat oddly) or part of the image. It works similarly to ‘negative space’.

The selection of the ‘WP’ and ‘BP’ is manual… Move closer to [0, 1] if it isn’t already.
In the case of the processed image, I created a second RT-spot in normal mode, in the form of a rectangle. Its purpose is to reduce the effect in the sky area without significantly affecting the sun. It resembles (somewhat) a Graduated Filter. The center was placed on a cloud, with the Scope set to 25. The center of the spot is positioned relatively far in the image. Of course, you can change the position of the RT-spot, Scope, and Transition in Selective Editing > Settings.

Sliders like ‘Stretch factor (D)’ work in reverse. They reduce contrast, darkening the image.

<figure>
<img src="inv-ghs-2.jpg" title="inv-ghs-2.jpg" width="300" />
<figcaption>GHS - Inverse</figcaption>
</figure>

##### Six methods available - two recommended
Six methods available (RGB Luminance, RGB Standard, Lightness & chromaticity (Lab),Luminance (HSL), Saturation (HSL), Hue (HSL)). Two are recommanded:
+ RGB Luminance : the three channels R, G, B are used equally. To control the system, an equivalent luminance is calculated, attempting to take into account WP values ​​above 1.
+ RGB Standard (default) : the three channels R, G, B are used equally.

They will differ in how they render very high highlights, which are out of gamut. The choice between the two depends on the images and your preference.
An example in RGB Luminance mode for the first RT-spot

##### LMS Matrix conversion
Performs the entire GHS processing, including Matrix conversion either AgX or JzAzBz or Cat16. For JzAzBz and Cat16 you have the choice between a transformation in RGB mode or in XYZ mode (preferably).
* To allow this matrix to be enabled or disabled, the 'Stretch factor (D)' must be between 0.001 and 0.002 and 'Auto Black point and White point' disabled.
* You need to re-enable 'Auto Black point and White point' to recalculate the values ​​of 'BP', 'WP' and 'Symmetry point (SP)'.

#### Using Michaelis-Menten (MM)
This algorithm is much simpler than GHS. It often provides almost the correct settings on the first try. However, it cannot operate in 'Inverse' mode. Like GHS, it requires adjustments to the 'Black points (linear)' and 'White points (linear)'. 

For the sake of simplicity, it is only offered in RGB Standard mode, i.e. the 3 channels Red, Green, Blue used in the same way.

##### MM Settings
This tone mapper uses the Michaelis-Menten equation, which is borrowed from biochemistry to describe enzyme kinetics. In image processing, it creates a smooth, saturating curve that is useful for tone mapping.
* Exposure: Adjusts the input image brightness.
* Output scale (S): Controls the maximum asymptotic value of the curve; essentially the output white level.
* Knee strength (K): Determines the “knee” of the curve. Lower values result in a sharper transition to the compressed highlight region.
* Saturation: Adjusts color saturation post-tone mapping.
* Output max clamp: Sets the final clipping point for the output values.
* JDx Matrix : the JDx checkbox allows the user to choose either the default or the JDx LMS transformations. LMS is a color space transform which represents the response (sensitivity) of the three types of cone cell in the human eye at long, medium, and short wavelengths.These transformations are matrices that modify each of the R G B channels for each individual pixel, giving priority to certain dominant colors depending on the selected option
  - Unchecked: leaves the data unchanged (default).
  - JDx: accentuates each of the R G B channels by acting on X Y Z such that the LMS data is perceived as being more colorful.

The two settings to prioritize are Output scale (S) and Knee strength (K) ; these are the ones that directly affect the hyperbolic function.

##### MM - Subtract linear black & Linear dynamic range - Attenuation threshold
As in GHS, these two settings, which I wanted to be simpler, are essential for the proper functioning of the algorithm.
+ Subtract linear black: reduces the linear black point values ​​to almost zero. This makes optimal use of the available data by increasing overall contrast and reducing haze effects.
+ Linear dynamic range: allows you to include any data outside the color gamut (in the case of sunsets for example). Enabling ‘Highlight reconstruction’ > Color Propagation can provide a significant improvement.

In addition:
+ Attenuation threshold: uses an exponential function to reduce highlights likely to cause gamut overshoot.

<figure>
<img src="first-mm-2.jpg" title="first-mm-2.jpg" width="300" />
<figcaption>First Spot : Michaelis-Menten - Settings</figcaption>
</figure>

##### MM - Darken the clouds - inverse GHS
<figure>
<img src="inv-ghs-mm-2.jpg" title="inv-ghs-mm-2.jpg" width="300" />
<figcaption>Second Spot : Inverse GHS</figcaption>
</figure>

#### A preview at the end of Game Changer
To give the user a glimpse of the possibilities of each of these 'pre-tone mappers', here is the result at the end of the Game Changer process. We will then see how to process Abstract Profile and Color Appearance & Lighting.

##### Sunset GHS - RGB Luminance
<figure>
<img src="sunset-ghs-lum.jpg" title="sunset-ghs-lum.jpg" width="600" />
<figcaption>Sunset GHS RGB Luminance</figcaption>
</figure>

##### Sunset GHS - RGB Standard
<figure>
<img src="sunset-ghs-std.jpg" title="sunset-ghs-std.jpg" width="600" />
<figcaption>Sunset GHS RGB Standard</figcaption>
</figure>

##### Sunset MM
<figure>
<img src="sunset-mm.jpg" title="sunset-mm.jpg" width="600" />
<figcaption>Sunset MM</figcaption>
</figure>




