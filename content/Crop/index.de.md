---
title: Crop
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Transform Tab'
---

Todo: übersetzen

Seite angelegt und Überschrift übersetzt, um zu referenzireren.

fherb
12.3.2017

------------------------------------------------------------------------

# Ausschnitt

The only difference between the crop tool in RawTherapee and that in
other programs is that the cropped-off area is never discarded - this
means that once you draw the crop you don't need to click any "OK"
button to apply it - it's done. You will see the masked cropped-off area
in the preview, but it will not appear in the saved image. Go to
"[Preferences](preferences) \> General \> [Crop mask
color/transparency](Preferences#Default_Theme.md)" to change the
color and transparency of the masked area around the crop.

Activate crop-placing mode by clicking the "Select Crop" button in the
tool panel, the ![<File:Crop.png>](Crop.png "File:Crop.png") button in
the [Editor's](the_image_editor_tab) top toolbar, or the
appropriate [keyboard shortcut](keyboard_shortcuts), then
create the crop by clicking and dragging over the preview with your
mouse. Use the **Shift** key to move the crop over the image. Resize a
crop by placing the mouse on one of the sides or corners. To clear the
crop, activate crop-placing mode again (via the keyboard shortcut or
either of the buttons mentioned above), and click anywhere in the
preview without dragging.

Use *Guide Type* to select popular guides to help you in composition
while cropping, and a horizontal (landscape) or vertical (portrait)
orientation. By default, as of version 4.2.214, RawTherapee
automatically detects and uses the same crop orientation as the
orientation of your image - the "As Image" option.

The PPI value does not change any physical property of the image, it
only sets metadata which describes the intended print size of the
current crop (or the whole photo if there is no crop). For prints up to
13x18cm (5x7 inch), 300PPI is a good choice; bigger prints can have less
pixels per inch.

## Aspect Ratios

![](Sensor_sizes_overlaid_inside.svg "Sensor_sizes_overlaid_inside.svg")
![](SensorSizes.svg "SensorSizes.svg")
![](Vector_Video_Standards2.svg "Vector_Video_Standards2.svg") Use "Fix
ratio" to set the crop to a fixed ratio.

3:2  
Classic negatives have this ratio, as do
[APS-C](https://en.wikipedia.org/wiki/APS-C)
[DSLR](https://en.wikipedia.org/wiki/Digital_single-lens_reflex_camera)
cameras.

4:3  
The [Four Thirds
System](https://en.wikipedia.org/wiki/Four_Thirds_system).

16:9  
The [1080p](https://en.wikipedia.org/wiki/1080p) and
[720p](https://en.wikipedia.org/wiki/720p)
[high-definition](https://en.wikipedia.org/wiki/High-definition_video)
video format, and due to this the most common computer monitor aspect
ratio since 2010.

16:10  
The most popular computer monitor aspect ratio between 2005-2009. Still
popular in tablets.

24:65 XPan  
Hasselblad's medium-format cameras.

1.414 DIN EN ISO 216  
[1.414 DIN EN ISO 216](https://en.wikipedia.org/wiki/ISO_216) is the
standard paper size ratio such as A4, B5, etc.

8.5:11  
The [US Letter](https://en.wikipedia.org/wiki/Letter_(paper_size)) size.

11:17 - Tabloid  
A common [tabloid newspaper
format](https://en.wikipedia.org/wiki/Tabloid_(newspaper_format)).

45:35 - ePassport  
Guides to help you crop a portrait for a [biometric
passport](https://en.wikipedia.org/wiki/Biometric_passport). Official
measurements do not specify exact ratios, just min/max measurements
within which the eyes and chin-crown distance must lie. The guides
represent the averages of those distances. The first horizontal guide is
for the crown, the second is roughly for the nostrils, the third is for
the chin. "On the photo, the face must be between 29mm and 34mm from the
bottom of the chin to the crown (the top of the head, not the top of the
hair)."
[1](http://www.homeoffice.gov.uk/agencies-public-bodies/ips/passports/information-photographers/).
