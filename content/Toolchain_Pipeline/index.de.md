---
title: Toolchain Pipeline
contributors:
  - Fherb
tags:
  - 'General Information'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Die Prozessverarbeitungskette

This page details the order in which RawTherapee processes images. Users
can learn how to better use the tools, knowing what happens when in the
pipeline, and programmers can use this reference to quickly find the
right place in the code to insert new tools and to find which files a
given tool resides in.

<https://code.google.com/p/rawtherapee/issues/detail?id=2233>

List of all tools in RawTherapee:

    Generic/Main preview
      Input profile
      Monitor Color Profile
      Working profile
      Output profile
      Clipping indication
      Red/Green/Blue/Luminosity/Focus mask previews
      Colorimetric intent
    ---
    Exposure
      Highlight Reconstruction
    Shadows/Highlights
    Tone Mapping
    Vignette Filter
    Graduated Filter
    Lab Adjustments
      L, a, b
      LH, CH, HH, CC, LC, CL
    CIECAM02
    ---
    Sharpening
    Edges
    Microcontrast
    Impulse Noise Reduction
    Noise Reduction
    Defringe
    Contrast by Detail Levels
    ---
    White Balance
    Vibrance
    Channel Mixer
    Black-and-White
    HSV Equalizer
    Film Simulation
    RGB Curves
    Color Toning
    Color Management
    ---
    Crop
    Resize
    Lens/Geometry
      Rotate
      Perspective
      Lens Correction Profile
      Distortion Correction
      Chromatic Aberration Correction
      Vignette Correction
    ---
    Sensor with Bayer matrix
      Demosaicing
      Raw Black Points
      Preprocessing
      Chromatic Aberration
    Sensor with X-Trans matrix
      Demosaicing
      Raw Black Points
    Raw White Points
    Preprocessing
    Dark Frame
    Flat-Field

------------------------------------------------------------------------

Order of tools

Dark Frame Subtraction

Flat Field Correction
[RawImageSource::processFlatField](http://code.google.com/p/rawtherapee/source/browse/rtengine/rawimagesource.cc#1270)

Read Bad Pixels from .badpixel file (bp1)

Get Hot Pixels from Darkframe (bp2)

Scale Colors (internal, no tool)

Vignetting correction from lcp (only if Flat Field correction is
disabled)

Raw Hot/Dead Pixel Detection (bp3)

Interpolation of all Hot/Dead Pixels collected in bp1, bp2 and bp3

Green equilibration

Line Noise Filter [RawImageSource::CLASS
cfa_linedn](http://code.google.com/p/rawtherapee/source/browse/rtengine/cfa_linedn_RT.cc#42)

Raw CA correction
[RawImageSource::CA_correct_RT](http://code.google.com/p/rawtherapee/source/browse/rtengine/CA_correct_RT.cc#105)

------------------------------------------------------------------------

For now, this is a stub to test GraphViz and LaTeX/MathML.

GraphViz test diagram 1:
<graphviz border='frame' format='png' caption='Graph for example no. 1'>
digraph example1 {Hello-\>World} </graphviz>

GraphViz test diagram 2:
<graphviz renderer='neato' caption='Graph for example no. 2'> graph
example2 {

` run -- intr;`  
` intr -- runbl;`  
` runbl -- run;`  
` run -- kernel;`  
` kernel -- zombie;`  
` kernel -- sleep;`  
` kernel -- runmem;`  
` sleep -- swap;`  
` swap -- runswap;`  
` runswap -- new;`  
` runswap -- runmem;`  
` new -- runmem;`  
` sleep -- runmem;`

} </graphviz>

LaTeX math test: $f(x) = x^2\,$
