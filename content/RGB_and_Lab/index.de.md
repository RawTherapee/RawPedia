---
title: RGB and Lab
contributors:
  - Fherb
tags:
  - 'General Information'
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: completed
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# RGB und Lab

![](RGB_Cube_Show_lowgamma_cutout_b.png "RGB_Cube_Show_lowgamma_cutout_b.png")
![](Lab_color_space.png "Lab_color_space.png")
*[RGB](https://de.wikipedia.org/wiki/RGB-Farbraum)* und *[CIE
L\*a\*b\*](https://de.wikipedia.org/wiki/Lab-Farbraum)* (oder einfach
"*Lab*") sind zwei unterschiedliche
[Farbräume](https://de.wikipedia.org/wiki/Farbraum), bzw. Arten, Farben
zu beschreiben.

Viele Leute wundern sich, dass es einen Unterschied macht,
*[Helligkeit](https://de.wikipedia.org/wiki/Helligkeit_(Farbe))*,
*[Kontrast](https://de.wikipedia.org/wiki/Kontrast)* und
*[Farbsättigung](https://de.wikipedia.org/wiki/Farbs%C3%A4ttigung)* im
RGB-Farbraum zu korrigieren und *Helligkeit*, *Kontrast* und
*[Farbart](https://de.wikipedia.org/wiki/Farbart)* im Lab-Farbraum. Der
RGB-Farbraum besteht aus den 3 Kanälen (Raumkoordinaten) Rot, Grün und
Blau. Lab hingegen besitzt die gleiche Information in den 3 Komponenten
*Helligkeit (L)* und den beiden Farb-Komponenten *a\** und *b\**.

Die Helligkeit bei Lab von der Farbinformation zu trennen, kommt unserem
Sehempfinden nach der ersten Verarbeitung im Sehzentrum des Gehirns
deutlich näher, als die drei Grundfarben, die viel weiter *vorn*, an den
Zapfen in der Netzhaut, vorhanden sind. Die Information aus der Kamera
selbst kommt dabei der Darstellung der Information in den Zapfen nahe.
Wenn wir aber das Bild im Raw-Entwickler bearbeiten, sehen wir es nicht
mehr aus dem Blickwinkel des Kamerasensors oder der Zapfen in unserer
Netzhaut, sondern schon in einer Wahrnehmensebene, die sämtliche
neuronale Vorverarbeitung im Gehin durchlaufen hat. An der Stelle, wo
diese Information vom Gehirn bereits mit Gefühlen und Erinnerungen
verknüpft wird. An dieser Stelle trennen wir in der Wahrnehmung die
Empfindungen nicht mehr in 3 einzelne Grundfaren, wir trennen sie zuerst
in Helligkeits-Kontrast-Informationen (Konturen) und in reine
Farbinformationen. (Abgesehen davon, dass wir natürlich Tonwerte auch
mit Helligkeitsempfinden vergleichen, wenn wir sie absolut bewerten
wollen.) Diese Differenzierung ergibt sich für uns, wie auch für Tiere
aus der Notwendigkeit, möglichst schnell und fehlerfrei Objekte erkennen
zu können. Diese bilden sich vorzugsweise durch Kanten und Muster ab.
Erst, wenn diese Information nicht mehr ausreicht, nutzen wir Farben zur
weiteren Differenzierung. Nicht umsonst haben wir, bzw. unsere
Vorfahren, lange Zeit mit Schwarz-Weiß-Filmen recht gut leben können.
Wäre es nicht so, wäre das Kino erst mit dem Farbfilm entstanden.

Wenn wir Lab als Farbraum betrachten ist weiterhin interessant, dass wir
selbst ausgesprochen viele Grüntöne unterscheiden können. Deutlich mehr
als in den Grundfarben Rot und Blau. Unser Hauptwahrnehmungsschwerpunkt
liegt bei Grün. Während die Komponenten Rot und Blau in einem relativ
großen Bereich der Beimischung die empfundenen Grüntöne beeinflussen,
bis dann über Gelb und Türkis die Wahrnehmung von Rot und Blau beginnt.
Ganz abgesehen davon, dass es Violett als Farbe, der eine bestimmte
Wellenlänge zugeordnet werden kann, gar nicht gibt. Violett ist weder
*blauer als blau* noch *röter als rot*. Violett ist, wenn man aus weißem
Licht den Grünanteil entfernt. Eine Farbe, die wir nur dadurch *sehen*
weil unsere Farbwahrnehmung mittels dreier Zapfen erfolgt, die im
Empfindlichkeitsbereich Rot, Grün und Blau liegen. Diese Farben gibt es
im Sinne der Physik ja tatsächlich. Violett gibt es hingegen nicht. Es
gibt keine Wellenlänge, die der Farbe Violett entspricht. Und im
Regenbogen gibt es Violett auch nur, weil der Wassertropfen kein Prisma
ist, sondern sich auf der blauen Seite nochmals Rot untermischt. Teils
überlagern sich da auch ganze Spektren, was zu Interferenzerscheinungen
führt. Und in diesem Mischbereich empfinden wir eben an passender Stelle
auch Violett. - Soviel nur zum Thema Farblehre. Es geht darum zu
verstehen, warum ausgerechnet der Farbraum Lab als *Steuerraum* zur
Bildverbesserung sinnvoll ist.

Die Farbwerte a\* und b\* hingegen sind sehr schwierig zu fassen. Man
kann sich unter bestimmten Werten nur schwer eine Farbe vorstellen. Wie
aber auf den Bildern rechts zu sehen ist, ist mit diesen beiden Werten
ein Farbton innerhalb eines Helligkeitsniveaus sehr fein auswählbar. Für
getrennte Korrekturen von Helligkeit/Kontrast/Sättigung auf der einen
Seite und dem eigentlichen Farbwert auf der Anderen, eignet sich Lab
besonders gut.

Warum unterschieden sich nun Helligkeits- und Kontrastregler gegenüber
RGB und Lab?

Beide Parameter sollten unabhängig von der Farbe sein und sich nur auf
die Helligkeit bzw. deren Verlauf zwischen Schwarz und Weiß auswirken.
Das tun sie auch. Die Transformation zwischen den beiden Farbräumen
führt aber dazu, dass ein Helligkeitsregler mit einem Einstellwert von
z.B. 30% im RGB-Farbraum (also im Werkzeug *Belichtung*) eine andere
Helligkeit erzeugt, wie der Helligkeitsregler im Werkzeug
*Lab-Anpassung*. Das Gleiche gilt für den Kontrastregler. Auch die
Farbsättigung ist anders skaliert. Denn im Lab-Farbraum wird der
Bezugsgröße *Grün* ein höheres Gewicht gegeben. Vor allem beim
Sättigungsregler ergibt sich der Unterschied, dass *mehr* Sättigung in
Lab eher allgemein *frischere* Farben ergeben, im RGB-Farbraum dieser
Regler aber eher dazu neigt, dass der Bildeindruck *wärmer* wird. In den
folgenden Bildern gibt es Vergleichsmöglichkeiten bezüglich der Regler
in beiden Farbräumen:

<div align="center">

<File:colorspace_flowers_900_1_neutral.jpg> \| Neutral
<File:colorspace_flowers_900_2_rgb_lightness.jpg> \| RGB Helligkeit +30
<File:colorspace_flowers_900_3_lab_lightness.jpg> \| Lab Helligkeit +30
<File:colorspace_flowers_900_4_rgb_contrast.jpg> \| RGB Kontrast +45
<File:colorspace_flowers_900_5_lab_contrast.jpg> \| Lab Kontrast +45
<File:colorspace_flowers_900_6_rgb_saturation.jpg> \| RGB Sättigung +25
<File:colorspace_flowers_900_7_lab_chromaticity.jpg> \| Lab
Chromatizität +25 <File:colorspace_flowers_900_8_vibrance.jpg> \|
Pasteltöne (Dynamik-Werkzeug) +25

</div>

Man könnte jetzt mit vielen Worten beschreiben, wo Du Unterschiede
zwischen dem Verhalten der Regler im RGB-Farbraum (also unter
*Belichtung*) und im Lab-Farbraum findest. Probiere es selbst aus.
Bekomme ein Gefühl, bei welchen Situationen Du welche Regler verwendest,
um Deinem Ziel bei der gegebenen Bildvorlage näher zu kommen. Ganz
abgesehen davon, dass man Helligkeit und Kontrast nicht nur mit Reglern,
sondern auch mit den Tonwertkurven unter *Belichtung* aber eben auch mit
Kurven im Lab-Farbraum beeinflussen kann.

[Category:General](category:general)
