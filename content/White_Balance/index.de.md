---
title: White Balance
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Color Tab'
---

Todo: übersetzen

Angelegt, um die Seite zu referenzieren

[fherb](user:fherb) ([talk](user_talk:fherb))
12.3.2017

------------------------------------------------------------------------

# Weißabgleich

Digital images generally consist of a mixture of the three primary
colors: red, green and blue. For various reasons you can read about
in-depth elsewhere, the red, green and blue values which serve as the
starting point in any raw photo development program need to be corrected
in various ways before they resemble the scene photographed. One of
those corrections is based on setting the correct white balance - making
things which should be white (or neutral gray) appear white (or neutral
gray), otherwise they will have a color cast. White balancing works by
multiplying each of the color primaries by a different amount, until you
get a satisfactory result. In order to make this operation more
human-friendly, the multipliers are controlled by easier to understand
temperature and tint sliders (and a red/blue equalizer for photos taken
in unusually 'cold' or 'warm' environments - read about it below), and
you can have them automatically set the correct values by using the
"Spot WB" pipette on an area of the photo which should have a neutral
color.

Having an incorrect white balance gives the image a color tint,
typically warmer (orange), or colder (blue). Some people use this for
creative effect. There are various tools and operations which rely on
the assumption that the white balance of the image is correct, for
example highlights recovery, skin or sky hue targetting, etc. You should
not make creative color tints using the white balance tool, but rather
use it for making white what should be white, and then use any of the
other tools in RawTherapee to add a desired color tint for creative
effect.

## Interface Description

### Method

White balance can be set in different ways: Camera, Auto, Custom, or a
host of presets for different light sources.

- [image:Wb-camera.png](image:wb-camera.png) Camera

  
Takes the white balance used by the camera. If you shoot only in raw (so
no raw+JPG), put the white balance settings of your camera on Auto. This
should generally give good results.

- [image:Wb-auto.png](image:wb-auto.png) Auto

  
Automatically corrects the white balance, by assuming that the average
color of the scene is neutral gray. Works well for a wide range of
scenes, and can be a good starting point for manual adjustments.

- [image:Wb-custom.png](image:wb-custom.png) Custom

  
Set your own color temperature and green tint by moving the two sliders
and/or using the Spot WB tool.

- Light source presets
  - [image:Wb-sun.png](image:wb-sun.png) Daylight (Sunny)
  - [image:Wb-cloudy.png](image:wb-cloudy.png) Cloudy
  - [image:Wb-shade.png](image:wb-shade.png) Shade
  - [image:Wb-tungsten.png](image:wb-tungsten.png) Tungsten
  - [image:Wb-fluorescent.png](image:wb-fluorescent.png)
    Fluorescent
  - [image:Wb-lamp.png](image:wb-lamp.png) Lamp
  - [image:Wb-led.png](image:wb-led.png) LED
  - [image:Wb-flash.png](image:wb-flash.png) Flash

### Spot WB

When you click on the Spot WB button
[image:Gtk-color-picker.png](image:gtk-color-picker.png)
(shortcut: **w**), the cursor changes into a pipette when it's over the
preview. Click on a gray or neutral area to determine the correct white
balance. The gray/neutral area may not be clipped, otherwise readings
will be off. You may use the picker several times on different places in
the photo, until you find a spot that leads to a suitable reading. Use
the *Size* drop-down box to change the size of the pipette. This tool
can be used as well inside a detail window. Right-click to cancel the
tool and to get the regular cursor back.

### Temperature and Tint

Moving the Temperature slider to the left makes the image cooler
(bluish), moving it to the right makes it warmer (yellowish). Moving the
Tint slider to the left makes the image purplish, moving it to the right
greenish.

### Blue/Red Equalizer

Allows to deviate from the normal behavior of "white balance", via
increase or decrease of the ratio between red and blue. This can be
useful when shooting conditions are far from the standard illuminant
(e.g. underwater), or are far from conditions where calibrations were
performed, where the matrices or ICC profiles are unsuitable.

## White balance connection to exposure

The white balance is described in temperature and tint, but will for raw
images internally be translated into weights of the red, green and blue
channels. The weights will be adjusted so that the channel with the
smallest weight reaches clipping in the working space (usually ProPhoto
RGB) when the raw channel is clipped. In other words, with exposure set
to 0.0 and no highlight recovery enabled the full visible range is fully
defined by the raw backing. As white balance changes the weights you may
see a slight exposure change if you make drastic changes.
