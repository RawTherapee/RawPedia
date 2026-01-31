---
title: Shadows Highlights
contributors:
  - McCap
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

`unfinished Tanslation`

Dieses Tool erlaubt es die Schatten oder Lichter unabhängig voneinander
zu verändern.

## Scharfe Maske

\<gallery caption="Schatten/Lichter" "Sharfe Maske" Effekt"
style="clear: both"\> <File:Sh_sm_1.jpg%7CDas> Ursprungsbild.
<File:Sh_sm_2.jpg>\|"Scharfe Maske" aus. <File:Sh_sm_3.jpg>\|"Scharfe
Maske" an.

</gallery>

Um die dunklen von den hellen Bereichen zu trennen, wird eine
helligkeitsbasierte Maske verwendet. Zwei unterschiedliche Algorithmen
erzeugen entweder eine scharfe Maske oder eine unscharfe Maske (siehe
Bild). Beide haben Vor- und Nachteile. Die unscharfe Maske ist
schneller, kann aber Halos erzeugen. Die scharfe Maske ist langsamer,
erzeugt aber keine Halos. Dafür können bei letzterer Kantenartefakte
auftreten, die bei genauerem hinsehen erst auffallen.

## Lichter

Der Lichter Regler macht die hellen Bereiche des Bilds dunkler ohne die
dunklen zu beeinflussen. Höhere Werte machen diese Bereiche dunkler. Ein
Wert von 100 macht weis zu hellem grau.

## Tonal Width for Highlights

This slider controls the strength of the Highlights slider. Higher
values give a stronger effect. A value of 100, combined with Highlights
100, turns the whites into middle gray (you probably won't want
that...).

## Shadows

This slider lifts the shadows and applies an effect that is sometimes
called 'fill-light' (or 'fill-flash') in other software. Higher values
lighten the shadow areas more.

## Tonal Width for Shadows

This slider controls the strength of the Shadows slider. A maximum value
of 100 gives the strongest 'lift shadows' effect.

## Local Contrast

Local Contrast is an adaptive contrast adjustment depending on contrast
within a specified area. It increases contrast in small areas while
keeping the global contrast (which can be set with the contrast sliders
in Exposure or Lab). The resulting image will look more
'three-dimensional'. This feature is very useful when you have a foggy
image or took your picture through a window. The effect is somewhat
similar to an unsharp mask with a high radius and a small value. A
setting between 5 and 20 works best for most shots.

## Radius

The value of the Radius slider influences the Highlights, Shadows and
Local Contrast sliders. The larger the radius, the stronger the effect
of local contrast. The effective area of the Highlights and Shadows
sliders also increases.

If you are bored, set the first four sliders to 100 and play with Local
Contrast to transform your favorite raw processor into a cheap effect
machine!
