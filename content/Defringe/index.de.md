---
title: Defringe
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

# Farbsaum entfernen

[thumb](image:defringe.jpg)
[thumb](image:defringe_curve.png) Purple fringes are a form
of axial (or longitudinal) chromatic aberration, and appear along dark
edges adjacent to bright areas due to incorrect focus, lens
imperfections, or simply (but more technically) due to the nature of
lenses not focusing all colors on the same plane. As lenses are
optimized to focus visible light of longer wavelengths on the same
plane, those shorter wavelengths farther away from the ones the lens was
optimized for (i.e. purple, violet - wavelengths on the shorter side of
the visible spectrum) can visibly tint dark regions when the bright
areas are of sufficient intensity. This tool should be able to
effectively remove most of them.

Defringing is applied either in the Lab or the CIECAM02 space (if
CIECAM02 is enabled). Consequently, enabling CIECAM02 may lead to
slightly different defringing results, especially when using the *Hue*
curve.

## Interface Description

### Radius

Strong chromatic edge fringes are suppressed by averaging over a
neighborhood of the specified radius.

### Threshold

Sets a threshold for the application of defringing.

### Hue

You can use the *Hue* [flat
curve](General_Comments_About_Some_Toolbox_Widgets#The_Flat_Curve.md)
to specify which colors *Defringe* should target. The horizontal axis
represents the range of colors, and the vertical axis the strength of
fringe removal. This allows you to limit the action to a specific range
of colors without affecting colors of other hues.

If you place a purple dot at the top and keep the rest of the colors at
the bottom, purple fringes will be removed with a maximal strength while
other colors will not be affected.
