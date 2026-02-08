---
title: CIECAM02
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Advanced Tab'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

Page added for referencing. -- fherb
13:08, 14 March 2017 (MST)

------------------------------------------------------------------------

By J.Desmis

## Über CIECAM02

### Introduction - history

Since many years now, men tries to model colors, its perception by
peoples. Lots of work has been done through out the years since the
Middle-Age, but it's only starting from the 19th century, then in the
20th one that has been made the main discoveries.

I'm not a specialist of the physiology of the human visual system,
neither a researcher in the complex domain of colorimetry. I've I took
some minimum information that seem essential to understanding, up to the
interested reader to expand it thanks to the Web and the elements I’ve
joined.

Commonly in photography, we use (more than) 50 years old models : RGB
and its derivative (HSV, HSL, CMYK,...), XYZ, and Lab and its derivative
(Luv, Lch). I won't comeback on the RGB model, known by everyone, it is
dependent of the peripheral and doesn't take into account any CAM (color
appearance model). The CIE's definition of XYZ (1931) was the first step
of the « Commission Internationale de l'Éclairage » (CIE - International
Commission on Illumination) towards a human description of the colors
faithful to the human vision. To summarize, a color can be characterized
by its 3 X, Y and Z values, obtained by a combination of « tristrimulus
values », « CIE standard observer » and the base color's « spectral
power distribution ». This model has been taken up in RawTherapee,
particularly in terms of white balance... This model doesn't take into
account any CAM, but it's an extraordinary leap forward, because we now
can model a color in cognitive terms.

The Lab model has been designed in 1976 by the CIE by derivating it from
the XYZ model, it characterize a color with an intensity parameter
corresponding to the luminance and two chrominance parameters that
describe the color. It has been specifically studied so that the
computed distance between colors correspond to the differences perceived
by the human eye. The Lab model is well established in RawTherapee, it
is used as a basis for most of the tools : sharpening, denoising, tone
mapping, Lab adjustments, etc.. It integrate some characteristics of a
CAM, but the benefits are sketchy. The CIECAM02 model, derived from
CIECAM97 and using G.Hunt's work, is the first commonly usable model in
photography, because it is invertible... and relatively « simple », it
can take into account other than purely cognitive aspects and is based
on the work of many researchers on the basis of sample of persons who
evaluate different parameters, like :

1.  simultaneous contrast : variation of the colored appearance of an
    object depending on the colorimetric characteristics of its close
    environment. For example, the same color will be perceived
    differently on a white or dark background. The darker the background
    will be, the more we'll have to boost colors...
2.  the Hunt's effect : increased seen coloration (colorfulness) with
    luminance. An object appears more vivid and contrasty in full light
    than in shade.
3.  the Stevens' effect : augmentation of the perceived contrast with
    the luminance. When the luminance increases, the dark colors looks
    like even darker and the luminous colors appears even more luminous.
4.  Helmholtz-Kohlrausch's effect : dependence of the brightness in
    relation to the luminance and chromaticity. Colored objects appear
    lighter than the achromatic objects with the same luminance. The
    most saturated colors appear brighter.
5.  Chromatic adaptation : adjustment by the human vision system of some
    color stimuli. The chromatic adaptation let us interpret a color
    depending on its spatiotemporal environment. It's an essential
    effect to be taken care of by a CAM.

The chromatic adaptation is the human visual system's ability to adjust
to changing illuminant conditions. In other words, we adapt to the color
of the light source to better preserve the color of objects. For
example, under incandescent light, a white paper appears yellow.
However, we have the ability to automatically model the yellowish light
so we see as white paper. The world around us would be very complicated
if the objects changed color whenever the light source changes even
slightly. Since the dawn of time, we must be able to know whether a
fruit is ripe, would it be the morning, afternoon or evening. The
chromatic adaptation makes it possible. But it can also be the source of
many optical illusions. I think the majority of RT users know, at least
by name, the previous model of chromatic adaptation, called “Bradford”.
etc.

Note : there will be no question here of "Munsell Correction" because
CIECAM02 is, by principle, built around Munsell's tables... so this
correction is taken into account, even if the model has shortcomings!

My first thoughts about CIECAM02 dates back to 2007, and the development
of a spreadsheet, for best results in the development of ICC “input
profiles”. Early 2012, I addressed a request from users: "can we have
reference colors - color palette - (skin, sky, ..) which would allow a
better white balance through a comparison/iteration process". I also
worked on the concept of CRI (Color rendering index) which reflects the
difference of illuminants compared to a base illuminant... The lower the
CRI is, worse the rendering will be with an identical color temperature
see : [Color_Management/fr](color_management/fr))

Based on CIECAM02, the patch contains the necessary basic elements to
work these two points, but it lacks an essential element, not easy to
develop : a pipette. I have long considered CIECAM02, not as a gimmick,
but as something difficult to implement... and with a quite small bonus
compared to Lab. The request of Michael Ezra who surprised me at first,
led me to re-open the file; the plug-in for Photoshop was a discovery
for me by the example, of CIECAM02. I am now convinced that even if the
model is not perfect (for some pictures, its use is almost impossible!),
it is today the most undeniable (effective) in terms of color
management. The module I am proposing is an "initiation". From the data
of CIECAM02, it is possible to develop a series of features similar to
those already developed in RT (Lab adjustments with various curves,
tone-mapping, etc.). Probably with significant advancements in terms of
quality.

The lack of effective documentation adds to the complexity... Some
points of view are personal (can be tainted by errors?). If a specialist
reads these lines, I'll be happy to change my text and my algorithms!

### Some definitions

1.  Brightness \[brilliance\] (CIECAM02) :
      
    The amount of perceived light from a stimulus = indicator that a
    stimulus appears as more or less bright, light.
2.  Lightness \[luminance\] (Lab, CIECAM02) :
      
    The clarity of a stimulus relative to the brightness of a stimulus
    that appears white under similar viewing conditions.

    Note that in RT, the“brightness” term applies to “Lightness” ! You
    will need to make a patch to rename “brightness” to “lightness” in
    the “exposure”, “Lab adjustments”, etc... modules.
3.  Hue and hue angle (partly in Lab, CIECAM02) :
      
    The degree to which a stimulus can be described as similar to a
    color described as red, green, blue and yellow.
4.  Colorfulness (CIECAM02) :
      
    The perceived amount of color relative to gray = indicator that a
    stimulus appears to be more or less colored.
5.  Chroma (Lab, CIECAM02) :
      
    The “coloration” of a stimulus relative to the brightness of a
    stimulus that appears white under identical conditions.
6.  Saturation (CIECAM02) :
      
    Coloration of a stimulus relative to its own brightness.

To summarize :

1.  Chroma = (Colorfulness) / (Brightness of White)
2.  Saturation= (Colorfulness) / (Brightness)
3.  Lightness= (Brightness) / (Brightness of White)
4.  Saturation= (Chroma) / (Lightness)
      
      
    = \[(Colorfulness) / (Brightness of White)\] x \[(Brightness of
    White) / (Brightness)\]

    = (Colorfulness) / (Brightness)

CIECAM02 develops and uses several types of correlated variables that
allow the use of these concepts :

J : lightness or clarity, close to L (Lab)

C : Chroma, close to C (Lab)

h : hue angle, close to H (Lab)

H : hue. A color can be described by the composition of 2 base colors
between 4 (red, yellow, green, blue), e.g. 30B70G or 40R60Y.

Q : brightness

M : colorfulness

ac, bc : close to a and b (Lab)

Why the saturation in addition to other close variables? Here is a quote
from a text by Robert Hunt (2001) :

  
  
*“Of the three basic color perceptions, hue, brightness and
colorfulness, hue has no relative version, but brightness has lightness,
and colorfulness has chroma and saturation. Correlates of chroma are
widely used in color difference formulae, but saturation currently plays
little part in color science and technology. This is perhaps because in
many industries, flat samples are viewed in uniform lighting for the
evaluation of color differences, and in this case chroma is the
appropriate contributor for samples of small angular subtense. For
samples of large angular subtense, however, a correlate of saturation
may be more appropriate to use. In the real world, it is common for
solid objects to be seen in directional lighting; in these
circumstances, saturation is a more useful percept than chroma because
saturation remains constant in shadows. In imaging, artists and
computer-graphics operators make extensive use of series of colors of
constant saturation. In optical imaging, saturation can be an important
percept in large dark areas. Recent experimental work has provided a
much improved correlate of saturation.“*

## The 3 processes

Three processes allow the use of CIECAM, their names depends on each
designer. I've made a synthesis (reminder: this document is not a
course, or a thesis on CIECAM... but an aid to its understanding and
use).

### Process 1

Names like “origin”, “forward”, “input”, “source” are generally used...
I finally chose “source”, which corresponds to shooting conditions and
how to bring back the conditions and data to a “normal” area. By
“normal”, i mean medium or standard conditions and data, i.e. without
taking into account CIECAM corrections, e.g. “surround = average”, D50
white balance !

### Process 2

It corresponds to the treatment of correlated variables (J C h H Q M s a
b) for various purposes : action on lightness (J), brightness (Q),
chroma (C), saturation (s), color level (colorfullness M), the hue angle
h, as well as ac et bc. It is quite possible to build an images editing
software around those variables...

In the case of this patch for RT, I arbitrarily selected 4 groups of
algorithms :

1.  JC by adding an contrast function ;
2.  Js, as above
3.  QM
4.  All: all parameters including h.

These modules are simple, more for pedagogical purpose than trying to
solve the problems of colorimetry, even if the results are in my opinion
excellent.

I completed this process by :

1.  double “curves”, acting on contrasts J (lightness) or Q
    (brightness), whose principle is similar to the double curves of
    “exposure” ;
2.  a choice for color curves between chroma, saturation and color level
    (colorfulness).
      
    We could add other algorithms based on the Fourier transform, or
    replacing equivalent functions of RT...

### Process 3

Names like “inverse”, “reverse”, “output” or “viewing conditions” are
generally used. I've chose “viewing conditions”, which reflects the
media on which the final image will be viewed (monitor, TV, projector,
...), as well as its environment. This process will take the data from
the process 2 and “bring them” to the support so that the viewing
conditions and environment are taken into account.

Note: we find here the explanation of the rendering difference between a
printed photo and a picture viewed on a monitor - even if the printer is
a high-end and well calibrated one: the viewing (observation)
conditions! A printed photo will often viewed in an album, often on a
black background, in low light... and often tungsten lighting. The
original will be seen on a monitor with a light background, and a D50
illuminant... There is no question of changing the “print” output, but
to adapt the “monitor, TV...” output.

That is to say, but here stops the comparison, that we realize something
like soft-proofing, but it's not the case because it's the purpose of
CIECAM. We takes into account the settings specified in “Preferences”
(white point of the output device \[screen TV, projector...\] and its
average luminance \[% gray\]. We also takes into account the luminance
of the room in which the observation is made, as well as the relative
luminance of the visualization device's environment (more or less
black).

Simplified synthesis of what RT allows with the current patch :

1.  general case of the user who uses RT to see his development... that
    should represent 95% of the cases. In this case, “viewing
    conditions” corresponds to the RT work environment, e.g.:
    - monitor's white point set to 6000K
    - calibrated monitor, so Yb=18
    - but according to :
      - the selected “theme” in “Preferences / General” (almost black or
        gray), you have to change “surround”
      - the monitor's location (on a neutral or dark background), you
        have to change “surround”
      - lighting of the room, that will change with time, you'll have to
        change “adaptation luminosity viewing La” : e.g. at night
        without lighting up, “La” will be close to 0 or 1, and on the
        contrary by day in a bright room, “La” will be close to 1000
2.  less common case, but possible, because I've already done it, I use
    RT and the family TV to show pictures as well as RT's possibilities.
    The “viewing conditions” will be different and to be adapted to each
    case ; you'll have to review each of the points above with possibly
    different settings: TV's white point, TV's Yb (empirical?), a
    different “surround” because we generally look at the TV with a dull
    background, and with a reduced room's illumination.
3.  you want to prepare a series of photographs for an exhibition: in
    this case, in a professional manner, we will "see" viewing
    conditions on site and ask for data like the projector's white
    point, calibration (?), the room's brightness on the day of the
    exposition, etc... In RT, the user will set "viewing conditions" to
    suit the exposition's conditions, and produce X corresponding jpeg
    (or TIFF)
4.  etc.
5.  that's why I put most of the settings for the process \# 3 (Output
    Device) in "Preference" is not an error, but appears similar setting
    as the monitor profile that depends on the monitor...

## Data

Which data are taken into account and which simplifications I
(arbitrarily?) made? How to adjust them? :

- **Yb** : Yb is the relative luminance of the background ! With that,
  we're much advanced ! Specifically it is expressed in % of gray. A 18%
  gray corresponds to a background luminance expressed in CIE L of 50%.

:\* for process \#3, if your monitor is calibrated, you can easily have
a value of Yb close to 18 or 20. If your TV or projector, that seems
difficult to calibrate, seems dark or light, you can adjust this value
empirically. It depends on the visualization support and can be
considered as constant for a set of photos and in a condition of
observation. If you want to change this value, go to “Preferences /
Color Management / Yb luminance output device (%)”

:\*for process \#1, it's much more complex because:

:\*\*an image has rarely a constant exposure and small luminance
variations

:\*\*I placed the CIECAM module at the end of the Lab process, just
before the RGB conversion and the sends to the output device, so we can
assume that the user has used various tools of RT to make the image have
an "average" histogram

  
  
So I arbitrarily made Yb inaccessible by calculating it from the average
luminance of the image. Of course, if in the future RT integrates
pipettes to separate the image areas (dark, normal, bright...) then it
would be possible to enter several Yb values. For example on an image we
could see three areas :

- standard, which corresponds to the average luminance of the image with
  a Yb set to 20%;
- underexposed (approximate contours delineated by the pipette...),
  where the luminance would be calculated and would e.g. give as a
  result Yb=5%;
- overexposed, where Yb would be as high as 70%..

- **La** : La is the adaptation field's absolute luminance ! Again,
  we're much advanced now !

:\*In process \#1, it corresponds to the luminance when shooting. E.g.
if you make a photo in the shade, “La” will be close to 2000cd/m2; if
you make interior shots, “La” will vary depending on the lighting from
20 to 300cd/m2... In reproduction, these values may be even lower

:\***”Scene luminosity” and the “Auto” checkbox** (process \#1):

:\*\* If Checkbox enabled, La is calculated with Exif data (shutter
speed, ISO speed, F number, Camera Exposure comprensation) and also Raw
White Point and Exposure compensation slider

:\*In process \#3, it corresponds to the luminance of the place in which
is made the observation. When you calibrate your monitor, you are asked
for this value... or you are offered the choice of using a probe. Orders
of magnitude from 15 to 100 should resolve most cases. But e.g. for a
theatrical projection in the dark, it can lead to lower values (1-10)

:\*These 2 values of “La” are adjustable in RT, in the “CIE Color
Appearance Model 2002” tool

- **Surround**

  
Again, I have made simplifications...

- for process \#1, this data reflects some shooting conditions, such as
  photos in a museum with a dark background, or portrait shooting on a
  black background. Usually RT's user will have corrected the deviations
  from its perception thanks to its numerous tools. However, I've added
  a checkbox “Surround (scene) dark”, which can be activated if
  necessary. Its use will lighten the image (recall: this process bring
  the data “back to normal”)
- this data reflects the surroundings of the image when viewing. The
  darker the surrounding will be, the more you'll have to increase the
  contrast of the image. The “surround” variable is not acting as a
  D-lighting or tone curve, it also changes the colors in the red-green
  and blue-yellow axis. If the environment's luminance is greater than
  20%, choose “average”, otherwise adapt to your conditions, e.g. RT's
  settings (Preferences / General / Select theme) will affect the final
  rendering. This setting is accessible by “Surround (viewing)”. The
  darker the surrounding will be, the higher will be the image's
  simultaneous contrast.

- **White-points model**

:\*“WB RT + output” : here we trust RT's white balance for the process
\#1; CIECAM uses D50 as a reference: RT's white balance bring back the
conditions to a D50 equivalent, while for process \#3, it will be
necessary - as needed - to set the white point of the output device. Go
to "Preferences / Color Management / Settings white output device
(monitor, TV, projector)" and select an illuminant in the list (is it
sufficient? I have no idea about the characteristics of projectors,
light, temperature...)

:\*WB RT+CAT02 + output” : for process \#3, we are in the same situation
than above; for process \#1, a mix is made between RT's white balance
and CAT02 that is using its settings, which makes a solution where the
two effects (RT and CAT02) are combined. You can modulate the action of
CAT02 by acting on the “CAT02 adaptation” slider. You'll probably have
to change RT's white balance settings to benefit from the “mix”
advantages, otherwise the effects does add themselves.

:\*CAT02 is a chromatic adaptation, it converts the XYZ values of an
image whose white points is Xw0, Yw0, Zw0, in new XYZ values whose white
point becomes XW1, Yw1, ZW1 ; the algorithm used is similar to the one
from Von Kries, therefore different from RT's correction that takes into
account the channels multipliers !

- **”CAT02 adaptation” and the “Auto” checkbox**

:\*see above for the usage of “WB CAT02 + output”

:\*however, even when “white point model” is set to “equal”, this slider
can be useful. Usually, the “auto” checkbox must be checked and CIECAM
calculates itself an internal “D” coefficient that is used for other
purpose than the chromatic adaptation. The result is a value greater
than 0.65 (65%); you can uncheck the box that will alter process \#1,
the effects can be unexpected...

## Algorithm

You can choose between JC, JS, QM (of course there are other possible
combinations!), or “All” which lists all the possible settings (I
arbitrarily excluded “h” as well as “ac” and “bc” from the 3 algorithms
JC, JS, QM). The most common use (if one can use that term for CIECAM)
is JC, then act on the sliders to get the desired rendering... which I
recall depends on the display device, its environment, its settings and
the brightness of the room.

- **“JC” algorithm**
  - J simulates the lightness – close to L (Lab) – and C simulates the
    chroma, near the c (Lch) chromaticity. But, important difference, J
    and C take into account the “effects” (simultaneous contrast, Hunt,
    Stevens, etc...) which is not the case of Lab and even less RGB.
  - J varies in the \[ 0-100 \] range and corresponds to a relative
    value of the brightness (likewise L, or Value...) and theoretically
    C in the \[ 0-180 \] range (it can be higher)
  - The two cursors using J and C may vary from -100 to +100 with
    actions similar to the “Brightness” (to be renamed “Lightness”) and
    “Chromaticity” of “Lab adjustments” sliders.
  - with the “JC” algorithm, a skin tones control is possible, the
    action is similar to the similar cursor from “Lab adjustments”
  - The "contrast" cursor modulates the action of "J" with an "S" curve,
    which takes into account the histogram 's average brightness "J".

<!-- -->

- **“Js” algorithm**

  
It is similar to JC, but :

- - the chroma is replaced by the saturation (CIECAM). But for which
    purpose? I'm quoting again an excerpt of the text from G.Hunt For
    samples of large angular subtense, however, a correlate of
    saturation may be more appropriate to use. In the real world, it is
    common for solid objects to be seen in directional lighting; in
    these circumstances saturation is a more useful percept than chroma
    because saturation remains constant in shadows. In imaging, artists
    and computer-graphics operators make extensive use of series of
    colors of constant saturation. In optical imaging, saturation can be
    an important percept in large dark areas. Recent experimental work
    has provided a much improved correlate of saturation.
  - Skin tones control is less "fine" than with "JC", globally wider in
    the reds

<!-- -->

- **“QM” algorithm**
  - here we use 2 variables Q (“brightness”) and M (“Colorfulness”) that
    are not relative data, but absolute. We takes into account the
    white's brightness. It is easy to realize that the same white
    "J=100" will appear brighter in the sun than in a dark room...
  - the white's brightness takes into account the following parameters
    (scene) : “adaptation luminosity La”, “CAT02 adaptation” and “Yb”
    (currently not adjustable)
  - in common use, the control is more difficult than with "JC", however
    it provides opportunities for high contrast images and opens the
    door for HDR processing
  - Skin tones control is less "fine" than with "JC", globally wider in
    the reds
  - The “contrast” obviously acts different, since it takes into account
    Q differently than J.

<!-- -->

- **“All” algorithm**
  - you can control all the CIECAM variables: J, Q, C chroma, saturation
    s, M color level, J contrast, Q contrast, hue angle h, skin tones
    protection (acts on C only)

## Tone curves and color

### Curves

- you have – likewise in the “exposure” module – a set of 2 tone curves,
  which acts on the “J” lightness and “Q” brightness. You can use one
  curve only or both, by eventually mixing “lightness” and “brightness”.
  Beware, “brightness” curves can easily lead to out of bounds results!
  "Brightness" is an absolute scale, while “Lightness” is a relative
  scale, the same “J” white will appear whiter directly illuminated by
  the sun than in the shade, which is taken into account by "brightness"
  (Q). Thus shadows and highlights will be rendered differently by the
  “lightness” and “brightness” curves.
- you also have a set of “chroma” curve with 3 choices: chroma (the most
  common), saturation and colorfulness. These 3 curves are used to
  adjust the chosen parameter according to itself, e.g. modulate the
  saturation to avoid that the already saturated colors goes out of
  gamut. For these 3 curves, the “red and skin tones protection” cursor
  is operational, it is more suitable for skin tones in the “chroma”
  mode. I recommend using the “parametric” mode that allow to
  differentiates according to the colors's saturation level. Note: All
  “chroma curves” combinations (chroma, saturation, colorfulness) and
  sliders (chroma, saturation, colorfulness) are not possible without
  overly complicating the code, that's why in few cases some sliders are
  grayed out.

### Histograms in Tone Curves

The tone curve histograms in the *CIE Color Appearance Model 2002* tool
can show values before or after CIECAM02 is applied. To view the values
after CIECAM02 adjustments, enable the "*Show CIECAM02 output histograms
in curves*" option. If disabled, the histograms show values before
CIECAM02.

### Histograms in the Color Curve

The histogram in the Color curve shows the distribution of chroma
(saturation/colorfulness) according to the intensity of the chroma
(saturation/colorfulness) or chromaticity in Lab mode. The more the
histogram is shifted to the right, the more saturated colors are close
to the limits of the gamut. The more the histogram is shifted to the
left, the more the colors are dull.

The abscissa represents the value of the chroma
(saturation/colorfulness) or chromaticity (in Lab mode). The abscissa
scale is "open".

As usual, the ordinate represents the number of pixels involved.

## Gamut control (Lab + CIECAM)

- this checkbox will constrain the data into the workspace. I could
  perform this action in CIECAM mode (process \#3), but it would have
  considerably slowed down the system
- The used algorithm is the same than in "Lab adjustements", it works in
  relative colorimetry. I think that differences with what could be
  produced in CIECAM mode are minimal.
- Some adjustments of the CIECAM code are made when “Gamut control” is
  enabled..

## Code, calculation accuracy and processing time

The code for processes \#1 and \#3 is strictly the one of CIECAM02
(M.Fairchild, Billy Biggs, ...) that I've adapted and optimized to RT,
as well as improvements to the gamut correction by Changjun Li, Esther
Perales, M Ronnier Luo and Francisco Martínez-Verdú.

The processes \#1 and \#3 are symmetrical and stacks many floating point
calculations. The use of “double” is mandatory, hence important
processing time of about 1 second per Mpix. After extensive testing, we
have insights that using float instead of double racing acceleration
allowed for processing without sacrificing image quality You can change
this setting in "Preferences / Color Management"

In terms of accuracy, I wanted to make some checks by comparing a series
of data before and after CIECAM ; the differences are very small, e.g.
an XYZ input value of 6432.456 has an output value of 6432.388, which is
correct.

## Limitations of CIECAM02

This model is not perfect, and the following limitations are identified.
They can lead for certain images to process them correctly :

- we have already seen this for the Yb settings ;
- CIECAM02 is not a workspace as sRGB or Prophoto, or even Lab. So it is
  difficult to control the gamut. CIECAM is even known for its problems
  of narrow gamut, that's why unexpected results may occur to the limits
  if you're pushing up too much the sliders (J, C, s …) ; this may lead
  in critical situations (highlights, ...) to black or white spots in
  these areas. Do not hesitate to use RT's tools (highlight recovery,
  highlight reconstruction, impulse noise reduction, ...), or burned or
  black areas (raw white and black points, avoid color shift, ...)
- large workspaces (widegamut, Prophoto, ...) can lead, in some cases,
  to black areas while they won't appear in sRGB (narrowness of CIECAM's
  gamut).
- The noisy images will influence CIECAM, which will think that the
  colored dots are realities; that's why I placed CIECAM after “denoise”
- the CIECAM model favors "cones" and takes sparsely into account the
  "sticks", which means that peripheral vision is sparsely taken into
  account.
- So, with CIECAM, do not expect to find a cure for "difficult" pictures
  (overexposure, sensor's saturation, etc...). But for "normal" images
  (which is the majority), advances that seem more than significant.
- Etc...

Maybe we'll see one day CIECAMxx appearing that could overcome the lacks
of CIECAM02 ?

## The 12 principles of CAM by R.Hunt

1.  The model should be as comprehensive as possible, so that it can be
    used in a variety of applications; but at this stage, only static
    states of adaptation should be included, because of the great
    complexity of dynamic effects.
2.  The model should cover a wide range of stimulus intensities, from
    very dark object colors to very bright self-luminous color. This
    means that the dynamic response function must have a maximum, and
    cannot be a simple logarithmic or power function.
3.  The model should cover a wide range of adapting intensities, from
    very low scotopic levels, such as occur in starlight, to very high
    photopic levels, such as occur in sunlight. This means that rod
    vision should be included in the model; but because many
    applications will be such that rod vision is negligible, the model
    should be usable in a mode that does not include rod vision.
4.  The model should cover a wide range of viewing conditions, including
    backgrounds of different luminance factors, and dark, dim, and
    average surrounds. It is necessary to cover the different surrounds
    because of their widespread use in projected and self-luminous
    displays.
5.  For ease of use, the spectral sensitivities of the cones should be a
    linear transformation of the CIE x , y , z or x 10 , y 10 , z 10
    functions, and the V’() function should be used for the spectral
    sensitivity of the rods. Because scotopic photometric data is often
    unknown, methods of providing approximate scotopic values should be
    provided.
6.  The model should be able to provide for any degree of adaptation
    between complete and none, for cognitive factors, and for the
    Helson- Judd effect, as options.
7.  The model should give predictions of hue (both as hue-angle, and as
    hue-quadrature), brightness, lightness, saturation, chroma, and
    colorfulness.
8.  The model should be capable of being operated in a reverse mode.
9.  The model should be no more complicated than is necessary to meet
    the above requirements.
10. Any simplified version of the model, intended for particular
    applications, should give the same predictions as the complete model
    for some specified set of conditions.
11. The model should give predictions of color appearance that are not
    appreciably worse than those given by the model that is best in each
    application.
12. A version of the model should be available for application to
    unrelated colors (those seen in dark surrounds in isolation from
    other colors).

## Some links

CIECAM02 Wikipedia [1](http://en.wikipedia.org/wiki/CIECAM02)

Color Appearance Model - Fairchild
[2](http://www.cis.rit.edu/fairchild/PDFs/AppearanceLec.pdf)

Mémoire Laborie ENS Louis Lumière
[3](http://www.ens-louis-lumiere.fr/fileadmin/recherche/Laborie-photo-2007-mem.pdf)
