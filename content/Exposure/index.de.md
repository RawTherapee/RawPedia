---
title: Exposure
contributors:
  - Fherb
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Belichtung

## Button *Auto* - Automatische Belichtungseinstellung

Dieses Werkzeug gehört zu den absoluten Ausnahmen in RawTherapee: Es
arbeitet automatisch!

Während bei nahezu allen Werkzeugen das Ziel oder der Geschmack des
Bearbeiters absolut entscheidend für die Einstellungen sind und deshalb
eine Automatik wenig Vorteil bringen könnte, gibt es für die
Belichtungskorrektur ein paar wenige Grundregeln, mit denen sich ein
Bild in vielen Fällen tatsächlich zielführend für die meisten
Anwendungen vorjustieren lässt. *Auto* analysiert das Histogramm und
setzt einige Parameter der Belichtung auf meist sinnvolle Werte:

- Belichtungskorrektur
- Lichterkompression
- Lichter rekonstruieren
- Schwarzwert
- Helligkeit
- Kontrast

Das Werkzeug bietet sich also als "Schnellstart" für die händische
Belichtungskorrektur an. Gerade im Sinne des empfohlenen Workflows, mit
dem Weißabgleich zu starten, kann ein vorheriger Tastendruck auf *Auto*
das Bild bei schwierig belichteten Fotos zumindest erst mal in einen
Belichtungsbereich bringen, in dem sich der Weißabgleich einfacher
machen lässt. Danach gehe man dann wieder in das Belichtungswerkzeug und
korrigiere abschließend. (Das Default-Profil, dass für Raw-Bilder nach
der Installation standardmäßig verwendet wird, führt übrigens *Auto*
aus. Im Gegensatz zum alternativ einsetzbaren Profil *Neutral*, dass
tatsächlich nichts weiter verändert, bis auf die Kameraeinstellungen des
Weißabgleichs zu übernehmen.)

Es gibt aber natürlich auch Fotos, wie High- bzw. Low-Key-Aufnahmen, wo
die Automatik nicht unbedint einen guten Einstellvorschlag bringt.

### Clip %

Die *Auto*-Funktion verwendet den Clip-Wert zum Abgleich der Belichtung.
In einem Bereich zwischen 0,00% und 0,99% kann man vorgeben, wie viele
"Prozent" an Pixeln nach der Korrektur rein Weiß bzw. Schwarz sein
dürfen. Clippen meint also: an den obersten und untersten darstellbaren
Helligkeitswert "anecken". Höhere Werte erhöhen damit den von der
Automaik eingestellten Kontrast.

## Button *Zurücksetzen*

... setzt alle Schieberegler zusammen zurück. Die Tonwertkurven werden
dabei aber nicht verändert.

## Lichter rekonstruieren

[250px](image:highlightreconstructionexample.png) Mit dieser
Funktion kann man (in Grenzen) im RAW-Bild eigentlich überbelichtete
Details wieder etwas zurückholen. Ob und wie gut das funktioniert hängt
vor allem davon ab, wie viel Informationen in den 3 Farbkanälen der
betreffenden Pixel noch steckt. Bei leichten Überbelichtung clippen
nicht unbedingt alle 3 Grundfarben gleichzeitig. *Lichter
rekonstruieren* versucht mit den Informationen aus den noch nicht
clippenden Farbkanäle bzw. je nach Methode auch aus umliegenden
Bereichen genügend Zeichnung im überbelichteten Bereich "abzuschätzen".
Ob und wie gut das gelingt, hängt jeweils vom Einzelfall und der
gewählten Methode ab.

Beachte:

  
Dieses Werkzeug dient (nur) dazu, bereits in der Raw-Aufnahme clippende
Bereiche zu *rekonstruieren*. Hast du z.B. durch die händische
Belichtungskorrektur Bildbereiche des resultierenden Bildes zum Clippen
gebracht, nutzt dir diese Funktion nichts. Verwende dann
*Lichterkompression*, um Zeichnung in den clippenden Bereichen
zurückzuholen.

Der *Auto*-Button aktiviert übrigens diese Funktion, falls notwendig.

Es stehen 4 verschiedene Methoden zur Auswahl, die bestimmen, wie die
Rekonstruktion berechnet wird. Teste jeweils, welche Variante das beste
Ergebnis im speziellen Fall bringt:

1.  *Luminanz wiederherstellen*
      
    Wiederhergestellte Details werden Neutral-Grau gezeichnet.

    In den meisten Fällen sollte dazu zusätzlich unter
    *Lichterkompression* ein Wert unter 100 eingestellt werden.
2.  *CIELab-Überlagerung*
      
    Reduziert im CIELab-Farbraum zuerst die Helligkeit (im betreffenden
    Bildbereich) und versucht danach, die Farben wiederherzustellen.

    In den meisten Fällen sollte dazu zusätzlich unter
    *Lichterkompression* ein Wert unter 100 eingestellt werden.
3.  *Farbübertragung* (In der englischen Sprachversion: *Color
    Propagation*)
      
    Diese Methode ist in der Regel die Wirkungsvollste. Zusätzlich zur
    Wiederherstellung der Helligkeit versucht der Algorithmus aus den
    Farbinformationen der umliegenden Bereiche die dort vorhandene
    Farbinformation in den wiederhergestellten Bereich hinein laufen zu
    lassen. Diese Methode arbeitet dabei am Besten, wenn es sich um
    kleine überbelichtete Bereiche handelt und kann wahre Wunder bei der
    Wiederherstellung von überbelichteten Haut-Bereichen vollbringen.

    Die Schwäche dieser Methode ist wiederum, auch hin und wieder
    falsche Farben vom Rand in den überbelichteten Bereich zu übernehmen
    oder unerwünschte Muster zu bilden.

    Diese Methode arbeitet gut mit sehr hohen Werten von
    *Lichterkompression* (unter 500).
4.  *Überlagerung*
      
    Bei dieser Methode werden die Werte der clippenden Farbkanälen aus
    den Kanälen der umliegenden nicht clippenden Pixel abgeschätzt, die
    in der Farbe vermutlich am ehesten denen im clippenden Bereich
    entsprechen.

    Hierbei werden für die *Lichterkompression* wieder Werte unter 100
    empfohlen.

  

## Belichtungskorrektur

Der am *Belichtungskorrektur*-Regler angezeigte Wert basiert auf
[Lichtwert](https://de.wikipedia.org/wiki/Lichtwert)-Schritten.
Bedeutet, ein Wert von z.B. +1,0 entspricht einem vollen Blendenschritt
in Richtung weiter geöffnete Blende. Oder auch einer
Belichtungszeitverdopplung. Oder einer Verdopplung der
"Filmempfindlichkeit", also von z.B. einer ISO 400 Einstellung auf ISO
800. Ebenso oft auch als +1 EV (exposure value) oder als +1 LV (light
value = Lichtwert) bezeichnet.

Durch diese Normierung ist es zum Beispiel möglich, zwei Fotos, die mit
einem Belichtungs-Unterschied von 1EV, also z.B. einem vollen
Blendenschritt Differenz, aufgenommen wurden, wieder völlig
übereinstimmend zu korrigieren.

Um besser zu verstehen, was dieser Regler tut, betrachte das Histogramm
eines Fotos und bewege den Regler. Bewegst du ihn nach rechts,
verschiebt sich auch das Histogramm nach rechts, also hin zu höheren
Helligkeiten. Es verschiebt sich dabei der Schwarzpunkt (ganz links) und
der Weißpunkt (ganz rechts). In umgekehrter Richtung analog.

Wenn du versuchst, die Belichtung eines Fotos, dass übersteuerte
Bereiche (auch als *clipping*, *klippen*, also *an der Klippe anstoßen*,
bezeichnet) besitzt, zu verringern, wirst du sehen, dass der
übersteuerte Bereich anfangs flach-weiß war und dann flach-grau wird.
Die Aktivierung von "*Lichter rekonstruieren*" kann das in gewissen
Grenzen verhindern, indem Information aus in diesem Bereich noch nicht
übersteuerten Farbkanälen zur Wiederherstellung verwendet.

Wenn du RawTherapee eine Weile verwendest wirst du vielleicht
feststellen, dass du die Belichtungskorrektur immer wieder benötigst,
weil offenbar alle Bilder schwach unterbelichtet sind. Das ist normal.
Die meisten Kameras sind so eingestellt, dass sie bewusst leicht
unterbelichten, um bei der kamerainternen Bildverarbeitung zum JPEG
genügend Zeichnung wiederherstellen zu können, auch, wenn die
automatische oder manuelle Belichtung bei der Aufnahme nicht ganz exakt
eingestellt war.

Für Nutzer, die an den Interna Interesse haben, hier noch einige
technische Details, wie EV = 0 in Bezug auf die Rohdaten zu verstehen
ist:

  
Während EV = 0 einer Verstärkung von 1.0 entspricht (also keine
zusätzliche Verstärkung oder Abschwächung) gibt es eine vom Weißabgleich
abhängigen Verstärkungseffekt, der in der gesamten Bildberechnung vor
den Berechnungen des Belichtungs-Werkzeugs ausgeführt wird. Beim
Weißabgleich wird sicher gestellt, dass trotz der Korrektur kein
Farbkanal so verstärkt wird, dass er am Maximalwert anstößt, also dass
er nicht übersteuert wird. Obwohl alle Raw-Farbkanäle den selben Bereich
im File besitzen, wird der Weißabgleich sie insgesamt so ausbalancieren,
dass sie nicht übersteuern (wenn sie nicht schon vor dem Weißabgleich
übersteuert waren). Weißabgleich bedeutet, dass z.B. bei zu niedriger
Farbtemperatur der Rotkanal gegenüber dem Blaukanal verstärkt wird. Die
Basisverstärkung erhöht dabei den kleinsten Kanalwert gerade so, dass
sichergestellt ist, dass bei EV = 0 keine Lichter ausfressen, also keine
der 3 Raw-Farbkanalwerte übersteuert sind. Da also beim Weißabgleich die
einzelnen Farbkanäle entsprechend verstärkt oder abgeschwächt werden,
ändert sich als Nebeneffekt auch die Basisverstärkung des gesamten
Bildes. Bei stärkeren Weißabgleichveränderungen sind also
Helligkeitsänderungen des Bildes zu beobachten.

Die Basisverstärkung bezieht sich dabei also immer auf die Maximalwerte
in den Kanälen. Das heißt, ist im Raw-Bild kein Kanal übersteuert, wird
auch nach dem Weißabgleich bei einem Belichtungskorrekturwert von EV = 0
das Bild in keiner Farbe übersteuert sein.

## Lichterkompression

Dieser Einstellregler kann verwendet werden, um Zeichnung in Lichtern
hervorzuholen, die zu schwach ist bzw. durch die EInstellung von
Bearbeitungswerkzeugen inzwischen überbelichtet dargestellt wird.

Dabei ist wichtig, den wesentlichen Unterschied zum Werkzeug *Lichter
rekonstruieren* zu kennen:

  
Wenn bereits einzelne Farbkanäle im Raw an ihrem zahlenmäßigen
Maximalwert "anstoßen", sie also tatsächlich übersteuert sind, ist nur
das Werkzeug *Lichter rekonstruieren* in der Lage, die betreffenden
Pixel aus dem Übersteuerungsbereich zurück zu holen. Was natürlich nur
geht, wenn nicht schon alle 3 Farbkanäle übersteuert sind.

Wenn hingegen die Farbkanäle im Raw-Bild noch nicht übersteuert sind, ab
schon so hell kurz vor der Übersteuerung, dass die darin gespeicherte
Zeichnung im Bild nicht mehr zu erkennen ist, dann hilft
*Lichterkompression*, diese Zeichnung wieder sichtbarer zu machen. Genau
so hilft *Lichterkompression*, wenn erst unter Verwendung der
verschiedenen Bearbeitungswerkzeuge Lichter übersteuert werden. Also
auch hier: nicht schon im Raw überbelichtet waren.

Um zu sehen, ob das aktuell bearbeitete Bild schon Bereiche besitzt, die
übersteuert sind, klicke auf das Icon
![Image:Warnhl.png](Warnhl.png "Image:Warnhl.png") rechts oben.
Überbelichtete Bereiche oder solche, die schon ziemlich dicht an der
Überbelichtung dran sind, werden dann schwarz hervorgehoben. (Ab welchem
Helligkeitswert dieser Indikator aktiv wird, kann in den Einstellungen
ausgewählt werden: Allgemein \> Anzeige zu heller/dunkler Bereiche \>
Lichter-Schwelle)

<figure>
<img src="/images/Hra_0.jpg" title="Hra_0.jpg" />
<figcaption>Hra_0.jpg</figcaption>
</figure>

<figure>
<img src="/images/Hra_0_chi.jpg" title="Hra_0_chi.jpg" />
<figcaption>Hra_0_chi.jpg</figcaption>
</figure>

Wenn der Einstellregler der Lichterkompression nach rechts bewegt wird,
wird die Intensität der Lichter vermindert.

------------------------------------------------------------------------

Thats not clear! Highlight recontruction is for clipping raw color
channels. Compression works with unclipping raw data. ??? :

For highlight compression to work best you must also enable *Highlight
Reconstruction*. Each of the HR methods has its strong and weak points,
as explained above. Color Propagation is the most likely method to
produce good-looking results when the HC slider is significantly over
100. For the other methods you will usually want to keep the HC slider
around or below 100 - watch the histogram and the preview!

------------------------------------------------------------------------

![](Hra_125_ba.jpg "Hra_125_ba.jpg") To find out the optimal HC value,
you can make use of the histogram. In the screenshots above, what you
see are overexposed clouds above the Teide volcano in Tenerife. When
hovering the mouse cursor over the overexposed area, the pixel values
indicator (in the *Navigator* panel, under the little preview) shows
that lightness (L) is at 100, and the histogram shows that all channels
are clipped (see the red, green and blue squares in the top-right corner
of the histogram, they mean that there are so many pixels of maximum
value that they are off-scale). Increase the HC slider until the red,
green and blue channels in the histogram no longer squash up against the
right end of the histogram - you want them to touch it, but not to cram
up against it. You can enable the *Clipped highlight indication* icon
![Image:Warnhl.png](Warnhl.png "Image:Warnhl.png") before moving the HC
slider up. Once the indicator's black areas disappear from the white
parts you want compressed, which is also when the lightness of those
pixels drops from L=100 to L=99, you stop. Don't increase the HC slider
any more, because now the hopelessly-lost white areas would start
turning gray. You don't want them to turn gray. That would make the
photo look dull. In this example the indicator's black areas disappeared
when I set HC to 125.

![](Hra_toomuch_histogram.png "Hra_toomuch_histogram.png") As a rule,
the histogram of a correctly developed image should touch both ends -
the black and the white end. Not doing so means the image was
incorrectly developed. This is true for the vast majority of photos, the
only exceptions being photos of scenes which lack dynamic range, such as
misty scenes. If you increase the HC slider too much, then whites turn
gray as your histogram no longer touches the maximum end. Examples of
photos that have been over-compressed can be easily found on the
internet. They look horrible, don't do that! Recover what you can, but
what's clipped beyond repair should stay white.

RawTherapee offers more ways to deal with blown highlights. The
side-effect of all these methods is that they also take away some of the
brilliance of the photos, as they get more 'flat' or 'dull' as a result.
Highlight compression is very useful when used with moderation, but
remember that you cannot recover what is not there to begin with, so
once you notice that the completely clipped white areas become gray you
should reduce the compression amount until these areas become white once
more. To create the best possible output, feed RawTherapee the best
possible input - so expose well in the first place!

## Highlight Compression Threshold

The Highlight Compression Threshold slider sets the point where the HC
slider starts implementing compression. A value of 0 means the threshold
is zero: data compression occurs over the whole range of tonalities. 100
sets the threshold at one stop below the white point, so all the
compressed highlights are squeezed into the top stop. In practical
terms, more highlights are compressed when this slider is set to 0.

## Black

Use this to set the black point. See the left side of the histogram move
when you touch the slider. Values greater than 0 will make the image
darker, negative values will lighten up the shadow parts of the photo.

## Shadow Compression

The *Shadow Compression* slider 'dampens' the effect of the *Black*
slider. The maximum value of 100 gives a less dark image. This slider
only has effect when the *Black* slider is set to a value other than 0.
Practical use of this *Shadow Compression* slider is to fine-tune the
shadow intensity of the image.

## Lightness

This slider applies a hard-coded tone curve to lift or lower the
tonalities of the photo, resulting in a more or less light image. The
same tone curve is applied separately to each R, G and B channel. The
black point and the white point keep their positions.

## Contrast

This slider increases or reduces the contrast of the photo. It applies a
contrast curve centered at the average luminance level. Tonalities above
the average are lifted (lowered), while tonalities below the average are
lowered (lifted). The same contrast curve is applied separately to each
R, G and B channel.

## Saturation

This slider makes the photo more or less saturated. In more technical
terms, it adjusts the saturation of the image by applying a multiplier
to the saturation level of pixels in the HSV color space.

## Tonwertkuven

Here you can construct your own tone curves. They work on all three R, G
and B channels at the same time (so you can't work on the R channel
only).

There are two tone curves available, which can be designed with various
curve types, and applied in several different modes all explained below.
Clicking on the curve icon hides the curve from the interface - it does
not disable the curve.

The histogram displayed as the curve's background shows you the levels
of the data as it flows into the curve at that point in the processing
pipeline. You will notice that it differs from the main histogram which
shows you the levels of the final image, at the very end of the
pipeline.

While you are free to use only one tone curve to make your adjustments,
you can gain much finer tonal control if you use two curves at once. The
typical use of both curves is to lower values using the first curve, and
to raise values using the second one. It is similar to creating an S
curve in one of them, but you should be able to make finer adjustments
by using both without entering too fast in the "danger zone" where your
colors becomes unrealistic.

You can save a curve to disk. Click on the *Save current curve* icon
![Image:Gtk-save-large-dark.png](Gtk-save-large-dark.png "Image:Gtk-save-large-dark.png")
next to the graph and give it a name. Use the *Load a curve from file*
icon ![Image:Gtk-open.png](Gtk-open.png "Image:Gtk-open.png") to apply
this curve later to another file. Use the *Reset curve to linear* button
![Image:Gtk-undo-ltr.png](Gtk-undo-ltr.png "Image:Gtk-undo-ltr.png") to
delete all the points you created and to reset the curve to
neutral/linear. You can also *Copy*
![Image:Gtk-copy.png](Gtk-copy.png "Image:Gtk-copy.png") and *Paste*
![Image:Gtk-paste.png](Gtk-paste.png "Image:Gtk-paste.png") curves
to/from RawTherapee's own clipboard, which comes in very useful if you
want to quickly apply an identical curve to a different tool.

You can use as many control points in a curve as you like.

You can define different curves for all curve types if you like, but
only the one that is selected in the dropdown menu will be applied to
the photo.

The curve and histogram is always displayed with sRGB gamma, regardless
of working or output profile. This means that the shadow range is
expanded and highlights compressed to better match human perception.

### Linear Curve

This represents the unaltered (or linear) image, so without any tone
curve applied. It disables the curve.  

### Custom Curve

This is a classic type of curve, seen in many other programs as well.
The left part of the graph represents the darker tones, the right part
represents the brighter tones of the photo. Click on the curve to mark a
point and drag it with the mouse to change tonalities. Dragging the
point down makes the image darker, while pushing it up makes it
brighter. The dotted diagonal line marks the linear or unaltered state
of the photo. Press and hold the **Control** key to slow down the
movement. Hold the **Shift** key to snap the point to key elements:
maximum value, minimum value, middle value (i.e. snapped to the diagonal
or horizontal dotted line), same value of the preceding point, same
value of the next point, and for the *Control Cage* type, the line going
through the previous and next points. Delete a point on the curve by
dragging it out of the editor area.

The top-right point represents the brightest areas in the photo. Drag
that point vertically down to make the highlights less bright; move it
horizontally to the left to make bright areas brighter, perhaps at the
cost of some overexposure.

The bottom-left point represents the darkest areas in the photo. Move
that point horizontally to the right to make the photo darker, perhaps
at the cost of some underexposure. Move it vertically up to make the
darks lighter.

Flip the diagonal line (from bottom-left and top-right to top-left and
bottom-right) to produce a negative image.  
![](curve_custom_s.png "curve_custom_s.png") A typical usage of the
custom curve is to construct a so-called *S-curve*. Mark three points at
the 'coordinates' (1,1), (2,2) and (3,3) respectively. Drag the point at
(1,1) somewhat lower and the point at (3,3) a bit higher. Your image
will get more 'punch' this way. If your S-curve is symmetrical, i.e. if
you move the point you first placed at 1,1 by the same amount as the one
you placed at 3,3 but in the opposite direction, then the effect will be
identical to manipulating the *Contrast* slider.  

### Parametric Curve

![](Curve_parametric_s.png "Curve_parametric_s.png") This curve presents
four sliders and three control points. The sliders are used to control
highlights, lights, darks and shadows respectively (shadows mean deep
darks here). Move the mouse over the four sliders and a dark area under
the curve tells you which slider alters what part of the curve. Move the
Highlights slider to the left to make highlights less bright, move it to
the right to make them brighter. The *Lights* slider moves the lights
but not the highlights in the same way as above, as does the *Darks*
slider: moving it to the right lightens the dark tones, moving it to the
left darkens them. The *Shadows* slider works as the *Darks* slider, but
only on the darkest parts of the photo. You can again construct the
above mentioned stylized S-curve, although the parametric curve gives
you less 'extreme' control over the form of the curve. This mode,
however, has its own benefits, as curves can be shaped in a well
controlled manner. Note that using these sliders can have a profound
influence on the overall contrast of the image.

Use, if needed, the three control points under the curve. They determine
what point of the curve will be affected when moving the sliders. Moving
the middle control point to the right makes the image darker (the form
of the curve changes again, as does the dark area around the curve),
moving it to the left makes the image brighter. Moving the left control
point to the right darkens the dark areas somewhat, moving it to the
left lightens them, again somewhat. Moving the right control point to
the right makes the highlights brighter, moving it to the left darkens
the highlights.

Use the *Reset to default* buttons
![Image:Gtk-undo-ltr.png](Gtk-undo-ltr.png "Image:Gtk-undo-ltr.png")
next to the sliders to reset individual sliders, use the same button at
the top of the tone curve section to reset all four sliders and the
control points to linear (zero).  

### Control Cage

![](Curve_control_cage_s.png "Curve_control_cage_s.png") At first sight
this curve type looks very much like the *Custom* curve, but there are
some differences though. With the *Custom* curve, the curve touches all
the control points. This is not the case with the *Control Cage* curve.
To see this, click somewhere on the line and move the black point to the
left or to the right. Now the curve passes nearby the black point, but
doesn't touch it. Another difference is that the *Control Cage* allows
for a straight section of the curve, while you can't do this with the
*Custom* curve. The *Control Cage* curve needs at least three points for
that (so five in total). Holding down the **Shift** key while dragging a
point will help you to easily create a straight line by snapping the
point to the line made by the previous and next point (displayed in red
by the *Snap to* tool). Now make a new point between the two most left
ones and move it. As you can see, only the part on the left side moves,
not the rest of the curve.  

## Curve Mode

Next to each curve type, you'll find a *Curve Mode* combobox selector.
This will let you choose the algorithm that will be used for the
corresponding curve. The curve mode will have a strong effect on the
appearance of colors, especially if you use a contrast-enhancing curve
(S-curve). This can be used for creative effect, but can for some
purposes or styles cause undesired color changes depending which mode
you choose. Choose a mode that suits your specific taste and needs for
the photo at hand. By combining two different curves in tone curve 1 and
2 you can further fine-tune the look.

### Standard

This is the most basic mode (and the only one available in older
versions of RawTherapee and is found in some shape or form in most
image-related software): the values of each RGB channel are modified by
the curve in a basic "correspondence" method, that is the same curve is
applied to all channels.

The drawback of this mode is that e.g. considering an S-curve shape to
get more contrast, an orange color with a high value of red and green
and a low value of blue will tend to shift toward yellow, because the
red and green component will be raised, while the blue one will be
lowered.

In general an S-curve will increase separation of the channels and thus
increase saturation, which is a similar behavior to how color film
reacts to contrast. This together with the simplicity of implementation
has made the curve type popular in raw converters in general and is
often the only alternative available in less flexible software.

### Weighted Standard

You can use this method to limit the color shift of the standard curve,
even if it won't suppress it entirely. Keeping the previous example,
this method will raise the first component (red), and will also linearly
alter the green and blue component by raising them too. We end up with 3
values (R, g and b) while we have only processed the red component.

This process is then done for the green and blue component, so at the
end of the process, we end up with 9 values (R,g,b / r,G,b / r,g,B).
Values of the same component are then mixed together, which will produce
the resulting color with a smaller color shift.

### Film-Like

The film-like curve provides a result highly similar to the standard
type (that is strong saturation increase with increased contrast), but
the RGB-HSV hue is kept constant - that is, there are less color-shift
problems. This curve type was designed by Adobe as a part of DNG and is
thus the one used by Adobe Camera Raw and Lightroom.

### Saturation and Value Blending

This mode is typically better suited for high-key shots, but can be used
for creative effect in other photos as well. The average value of the
three component is computed, and then the curve is applied to this
value, giving a positive or negative gain. The color is converted to its
Hue, Saturation and Value representation, then if the gain is positive,
the pixel is linearly targeting Value = 1 and Saturation = 0, the Hue is
preserved. If the gain is negative, the pixel is linearly targeting
Value = 0, Saturation and Hue are preserved.

The result is highly similar to a luminance curve in Lab space (that is
change contrast without affecting hue or saturation). For
contrast-increasing curves the look will typically be slightly
desaturated. This is not really because the curve desaturates the colors
but because that in human vision contrast and saturation is tightly
coupled, so the same image with higher contrast requires higher
saturation to appear to have the same.

### Luminance

Each component of the pixel is boosted by the same factor so color and
saturation is kept stable, that is the result is very true to the
original color. However contrast-increasing curves can still lead to a
slightly desaturated look for the same reason as described for the
Saturation and Value Blending curve mode. If you want to manually
counter-act the desaturation, using the L\*a\*b\* Chromaticity slider is
a more neutral way of compensating for it than using the RGB-based
saturation slider.

Despite showing the R, G and B histogram (merged) in the background of
the curve, the curve operates on luminance values, where [Relative
Luminance](https://en.wikipedia.org/wiki/Relative_luminance) Y =
R\*0.2126729 + G\*0.7151521 + B\*0.0721750 First the relative luminance
value of a pixel is obtained, then the curve is applied to that value,
the multiplication factor between before and after luminance is
calculated, and then this factor is applied to each R, G and B
component. This is in contrast to the other methods where the curve is
applied to each R, G and B component separately.

### Perceptual

This mode will keep the original color appearance concerning hue and
saturation, that is if you for example apply an S-curve the image will
indeed get increased contrast, but the hues will stay the same and the
image doesn't look more or less saturated than the original. It's
specifically useful to establish a pleasing baseline contrast without
distorting the colors provided by a camera profile that doesn't apply a
curve itself (if you use a third-party profile that does apply a curve
it's typically already perceptually mapped with similar techniques as
described here).

The algorithm works the following way: it analyses the curve to get a
contrast value, which is used as base to scale chroma (saturation) such
that more contrast leads to more saturation and the other way around. As
contrast and saturation is tightly coupled in human vision this scaling
is necessary to make saturation *appear* constant. There are further
fine-tunings such as increase saturation more in the shadows, and less
for colors that are already highly saturated, also this corresponds to
human vision phenomena so the net effect it that the colors appear
constant. In the extreme highlights close to the white point the
algorithm blends over to white (like the standard curves) which is less
true to color but more practical for real output as the brightest color
of the output media (screen or paper) is white.

However do keep in mind that the perceptual model is not perfect and
cannot be perfect. This is only a curve, image content is not analyzed
and no localized changes are made. This means for example that for an
S-curve a large flat blue sky (low local contrast) may appear slightly
more saturated than the original. If you want to make A/B comparisons
don't compare side by side as the eye will then be confused by the two
contrast levels viewed simultaneously and then saturation will not
appear the same, but instead swap and let the eye adapt for a few
seconds.

If you want to further fine-tune the saturation manually it's generally
best to use the Lab chroma slider (and chroma curves).

Due to the many components in the algorithm it's considerably slower
than the other curve modes so refresh rate may suffer.
