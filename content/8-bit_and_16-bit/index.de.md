---
title: 8-bit and 16-bit de
contributors:
  - Fherb
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: yes
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# 8- und 16-Bit Pixelinformation

*(Dieser Artikel befasst sich ausschließlich mit der Pixelauflösung der
von RawTherapee eingelesenen und abgespeicherten Files. Die
Bildberechnungen dazwischen finden ausschließlich in
32-Bit-Gleitkommaarithmetik statt.)*

Im Bezug auf Bildformate bedeuten 8-Bit, dass ein Programm oder ein
Dateiformat die Information eines Farbkanals (rot, grün und blau) pro
Pixel mit 8 einzelnen [Bits](https://de.wikipedia.org/wiki/Bit)
darstellt, die zusammen ein [Byte](https://de.wikipedia.org/wiki/Byte)
ergeben. Dieses Byte kann positive Ganzzahlen im Bereich von 0 bis 255
darstellen. Alle 3 Farbbyte zusammen genommen benötigen also 24 Bit zur
Speicherung eines Bildpunktes. (Bei Programmen und Bilddateien, die
Transparenz unterstützen, kommt noch ein weiteres Byte für das Maß der
Transparenz des Pixels hinzu. Dies wird manchmal fälschlicherweise als
32 Bit Farbtiefe bezeichnet. RawTherapee unterstützt keine Transparenz,
weil Transparenz für Grafiküberlagerungen mit Bildern oder Hintergründen
verwendet wird und nicht für Fotos. Ein paar detailliertere Infos dazu
folgen noch mal ganz unten in diesem Artikel.)

## Raw oder JPEG aus der Kamera?

Die meisten modernen Raw-fähigen Kameras verwenden 12- oder 14-bit
Analog-Digitalwandler bei der Bildaufnahme. Das bedeutet, dass bei
Nutzung von Formaten mit 8-Bit pro Farbkanal, wie bei JPEG,
Informationsverlust auftritt. Allerdings können typische Bildformate,
wie eben JPEG oder auch TIFF, PNG usw., auf Grund der Gammakurve, mit
der die Helligkeitsinformationen beim Speichern vom linearen in einen
logarithmischen Zusammenhang umgerechnet werden, erhebliche
Helligkeitsunterschiede (Dynamikbereich) bis über 17 Lichtwerte
enthalten. Das ist ein ganzes Stück mehr, als 14-Bit-Wandler mit
theoretisch 14 Lichtwerten in der Lage sind zu verarbeiten. Durch die
Logarithmierung mit der Gammafunktion ist es also möglich, auch in
8-Bit-Farbkanälen von JPEG Rauschen in dunklen Bildbereichen zu sehen,
obwohl das Bild ausreichend belichtet wurde. Die Logarithmierung schiebt
sozusagen helle Lichtwerte "zusammen", während in dunklen Bildbereichen
die Auflösung gestreckt wird. Das bedeutet aber auch, dass wir damit in
den Lichtern Helligkeitsauflösung verlieren, die der Kamerasensor
auflösen konnte. Praktisch ist das alles kein Problem, wenn man davon
aus geht, dass man das Kamera-JPEG eigentlich nicht noch einmal weiter
verarbeitet. In einem modernen Entwicklerprogramm, wie RawTherapee, kann
man aber durchaus viel bessere Ergebnisse erzielen, als die Kamera mit
Ihrer Automatik. Nicht nur Erste Hilfe bei Fehlbelichtungen leisten.
Doch das funktioniert nur dann wirklich gut, wenn die gesamte
Information des Analog-Digital-Wandlers, von der Kamera im Raw-File
gespeichert, zur manuellen Bildentwicklung verwendet werden kann. Sonst
kann es bei der Bearbeitung schnell passieren, dass wir in hellen
Bildbereichen, z.B. Himmmel mit Wolken, Helligkeitsstufen erkennen
können. Mit einem Raw-Entwickler ist es damit auch möglich, bei der
Aufnahme rauschoptimiert mit dem sogenannten Verfahren *[Exposing to the
right](https://en.wikipedia.org/wiki/Exposing_to_the_right)* zu
arbeiten. Die gewollte Überbelichtung in speziellen Aufnahmesituationen
korrigieren wir dann beim Entwickeln wieder. Das ist aber aus den oben
erklärten Günden eben nur mit dem Kamera-Raw-Bild und nicht mit dem JPEG
der Kamera zu empfehlen.

## Pixelinformationen im Raw-File

Übrigens gibt es im Raw-File noch keine 3 Farbkanäle. Jedes Pixel wird
als reiner Grauwert abgelegt. Das liegt daran, dass ein Sensorpixel
nicht 3 Farben zugleich erkennen kann. Statt dessen bekommen die
einzelnen Pixel auf dem Sensor Filter in den 3 Grundfarben nach einem
bestimmten Muster. Erst mit der Kenntnis dieses Musters kann
RawTherapee, wie alle Bildentwicklerprogramme, Farbinformationen
interpretieren. Mit dem sogenannten
[Demosaicing](Demosaicing/de.md) berechnet RawTherapee aus
beieinander liegenden Pixeln den 3-kanaligen Farbton für jedes Pixel.
Dieser Schritt ist eine Interpolation. Das heißt z.B. das die
Grün-Information an der Stelle, wo ein Pixel im Sensor mit einem
Rot-Filter versehen war, aus den umliegenden Pixeln mit Grün-Filter
abgeschätzt wird. Dazu gibt es verschiedene Interpolationsalgorithmen.
Weiteres dazu findest Du im Artikel
[Demosaicing](Demosaicing/de.md). Aber somit braucht es Dich
nicht wundern, dass ein Raw-Bild etwa nur 1/3 so groß ist, wie ein
daraus entwickeltes (unkomprimiertes) TIFF-Bild mit 16-bitigen
Farbkanälen. Selbst ein TIFF mit 8-Bit pro Farbkanal muss unkomprimiert
das 1,5-fache der Größe des Raw haben. Der Vergleich gilt aber natürlich
nur, wenn die Kamera das Raw-Bild nicht auch komprimiert ablegt. Sonst
verschieben sich die Relationen.

## Bilder aus RawTherapee speichern

Sobald Du ein Bild in RawTherapee fertig entwickelt hast steht die
Frage, in welchem Format und damit auch in welcher Farbauflösung Du das
Bild abspeichern möchtest. Die Auswahl von 8- oder 16-Bit gibt es
allerdings nur bei den Formaten
[TIFF](https://de.wikipedia.org/wiki/Tagged_Image_File_Format) und
[PNG](https://de.wikipedia.org/wiki/Portable_Network_Graphics). Bei
[JPEG](https://de.wikipedia.org/wiki/JPEG) jedoch nicht. JPEG gibt es
nur mit 8-Bit-Farbkanälen. Ganz abgesehen, dass JPEG verlustbehaftet
abspeichert (aber dadurch auch viel Speicherplatz spart).

Immer dann, wenn Du vor hast, Dein Bild in einem anderen Programm
weiterzuverarbeiten und dieses Programm intern durchweg mit 16-Bit
Farbtiefe bzw. Gleitkomma rechnet, wie zum Beispiel
[PhotoLine](https://www.pl32.de/) und so langsam bewegt sich auch
[Gimp](https://www.gimp.org/) in die Richtung der vollständigen
16Int/32Float-Fähigkeit, dann speichere für dieses Zwischenformat
unbedingt in 16-Bit Farbkanalauflösung!

In der Regel wird TIFF im unkomprimierter Version eher in anderen
Programmen importierbar sein, als in komprimierter Variante. Das ist ein
Erfahrungswert. Da TIFF letztlich ein Containerformat ist, unterstützen
die Bibliotheken, die die Softwareentwickler für ihre Programme
verwenden, nicht alle möglichen TIFF-Interpretationen. 8- und 16-Bit
Farbtiefe und unkomprimiert sollte als kleinster gemeinsamer Nenner
immer unterstützt werden. Achte auch darauf: Einige verwendete
Softwarebibliotheken unterstützen nicht das Schreiben von
Metainformationen. Deshalb ist es nicht selten, dass Programme bei der
Ausgabe diese Metainformationen verwerfen. Wenn Du Deinen Workflow mit
verschiedener Software zusammenstellst, achte anfangs auf solche
Kompatibilitätsdinge.

Neben TIFF gibt es noch PNG als ein Format, dass ebenfalls zum
Datenaustausch mit vielen Programmen geeignet ist. 8-Bit, wie auch
16-Bit Farbtiefe. Die verwendeten Bibliotheken unterstützen dabei
(nahezu?) grundsätzlich die Komprimierung. Da wir mit Fotos und nicht
mit Grafiken arbeiten, ist das Maß der Komprimierung in PNG und TIFF
recht begrenzt. Je nach Foto und Rauschanteil kann man mit 5...30%
"Eindampfen" rechnen. Mit PNG verschwinden aber wiederum auch alle
Metainformationen
([Exif](https://de.wikipedia.org/wiki/Exchangeable_Image_File_Format),
[IPTC](https://de.wikipedia.org/wiki/IPTC-IIM-Standard),
[XMP](https://de.wikipedia.org/wiki/Extensible_Metadata_Platform)), da
diese Metadaten in diesem Format nicht unterstützt werden.

Wenn Du Bilder im Web veröffentlichst, wirst Du in der Regel um JPG
nicht herum kommen. Mit den neuen, nicht nur hochauflösenden Monitoren,
sondern vor allem mit hohem Kontrastverhältnis, kommen 8-Bit Farbtiefe
nun tatsächlich langsam an die Grenzen und Du musst damit rechnen, dass
schwache Farb- und Helligkeitsverläufe leicht stufig dargestellt werden.
Das einfachste, was Du dagegen machen kannst, ist gleichzeitig recht
simpel: Lasse Helligkeitsrauschen und sogar ein klein wenig Farbrauschen
im Bild. Dadurch ergibt sich ein
[Dithering](https://de.wikipedia.org/wiki/Dithering_(Bildbearbeitung)),
dass die scheinbare Farb- und Schattierungsauflösung vergrößert. Achte
aber in einem solchen Fall immer darauf, das JPG nahezu mit 100%
Qualität zu exportieren. Es wird dadurch zwar deutlich größer, ist aber
immer noch sehr viel kleiner als ein PNG, dass die Browser auch
akzeptieren würden. Ohne die hohe Exportqualität wird das für das
Dithering notwendige farbige Restrauschen wieder entfernt. Und du musst
darauf hoffen, dass die Content Managment Systeme die Bilder beim meist
verwendeten automatischen Skalieren, nicht wieder mit einer niedrigeren
Qualitätsstufe dem Nutzer zusenden.

Für das Web könntest Du auch in einem externen Programm ein TIFF oder
PNG in ein [JPEG 2000](https://de.wikipedia.org/wiki/JPEG_2000)
umwandeln. Dieses Format verstehen Browser und es unterstützt 16-Bit
Farbtiefe. Es hat sich bisher allerdings noch nicht so recht durchsetzen
können. Aus einem einfachen Grund nutzt uns das derzeit auch wenig: Die
meisten Monitore arbeit mit sRGB auf 8-Bit-Basis. Auch werden auf sehr
vielen Web-Seiten Content Managment Systeme verwendet, die die Bilder
selbsttätig für den Anwender herunter skalieren. Auch hier ist
vermutlich auf lange Sicht noch 8-Bit Farbtiefe präsent. Demzufolge
bringt es derzeit leider nahezu nichts, im Web mit JPEG 2000 zu
arbeiten. Die Webtools, wie die Monitore sind halt vor allem für den
0-8-15-Endverbraucher ausgelegt. Nicht für Foto-Puristen.

## Ein paar Zusatzinformationen

Bei der Benennung von Bildfiles bezüglich ihrer Farbauflösung gibt es
einigen Wirrwar. Da wird von 8-Bit, 16-Bit, 32-bit gesprochen, aber
inzwischen auch von 48-Bit, 64-Bit und 32-Bit Gleitkomma. Das folgende
sind Hintergrundinformationen. Du musst das für die Arbeit mit
RawTherapee nicht lesen. Aber vielleicht interessiert es Dich doch
einmal.

Bevor wir Dich jetzt ganz konfuss machen, merke dir diese ersten
*Einstiegsregeln* für Farbfotos:

`8-Bit und 24-Bit meint das Gleiche: 8-Bit ist ein Farbkanal in Ganz-Zahlen. Für alle 3 Kanäle ergeben sich also 24 Bit.`

`Das Gleiche gilt für 16-Bit (ein Kanal als Ganzzahl) und 48-Bit (3 Farbkanäle eines Pixels zusammen genommen).`

`RawTherapee rechnet hingegen mit 32-Bit-Gleitkomma. Bedeutet also 96-Bit für 3 Gleitkommazahlen, die nur im RAM benötigt werden. Abgespeichert wird hingenen wieder mit 24/48Bit pro Pixel.`

### Details

Obwohl man es auch anders tun könnte (L\*a\*b zum Beispiel), wird in den
üblichen Fileformaten JPEG, TIFF, PNG... die Bildinformation in genau
den 3 Grundfarben getrennt abgespeichert. Und zwar für jedes Pixel. Wenn
man diese 3 Grundfarben später wieder kombiniert, also einfach
gesprochen, übereinander legt, dann kommt das Farbbild wieder zum
Vorschein.

Wir sagen *8 Bit pro Kanal*, wenn wir meinen, dass ein Pixel durch 3
Werte in den 3 Grundfarben Rot, Grün und Blau beschrieben wird, jeweils
mit 8 Bit Auflösung, also einem Byte, also möglichen 256 Stufen
abgespeichert wird. Ein reines Graustufenbild mit 8-Bit Farbtiefe
benötigt dagegen nur 1 Byte pro Pixel, um die möglichen 256 Stufen
abzubilden. In TIFF z.B. gibt es die Möglichkeit, so ein Bildformat auch
abzulegen.In der Regel wird ein Graustufenbild, wie in JPEG, trotzdem
mit 3 Farben abgespeichert. Hier hat jeder Kanal pro Grau-Schritt den
gleichen Wert, wie die 2 anderen Kanäle. Weiter oben wurde aber schon
die Frage der Stufenbildung angesprochen. Und die Lösung mittels
Dithering. Wenn Du trickreich arbeitest, kannst Du ein Graustufenbild
mit 3 Farbkanälen zu je 8 Bit mit einer scheinbar höheren
Schattierungsauflösung ablegen. Siehe oben: Nutze Dithering dazu.
Überlagere eine geringe Menge Farbrauschen. Schwarz-Weiß- aber auch
Farbdrucker sind ein allgegenwärtiges Beispiel für diese Methode. Deren
Firmware nutzt dieses Verfahren, stufenfrei Verläufe drucken zu können.
Dort brauchen wir uns nicht selbst drum zu kümmern.

Wir waren bei 8-Bit-Helligkeits- bzw. Farbausflösung. Ist das das
Gleiche, wie 24 Bit? Klar: Bei 24-Bit werden die 3 Farbkanäle zu je 8
Bit zusammengezählt. Ein Farbpixel hat also eine 24-Bit-Farbauflösung.
Stellt man sich vor, und das ist ein übliches Verfahen, das jede der
drei Farben eine Koordinate im 3-Dimensionalen Raum darstellt, können
wir auch tatsächlich 2^24 verschiedene Punkte, also
Farb-/Helligkeitswerte ansteuern. Das sind über 16 Millionen
unterschiedliche Werte. Und trotzdem kann ein solches Bild noch stufig
aussehen? Ja. Denn beschränken wir uns auf einen allmähligen Verlauf,
also eine flache Linie in diesem 3D-Farbraum, dann kann das Auge selbst
bei dieser hohen Auflösung noch Unterschiede stufig wahrnehmen.
Vorausgesetzt, die Flächen einer Stufe sind groß genug. Dithering ist
dabei der Trick, diese Flächen in leichtes Kräuseln zu ändern und uns
damit die Stufen verschwimmen zu lassen.

So. Jetzt kennen wir die 8-Bit- und 24-Bit-Variante. 32-Bit-Bilder, die
mittels PNG und TIFF (nicht JPEG) abgespeichert sind, gibt es nun aber
auch noch. Hier ist aber ein weiteres Byte (also 8 Bit) enthalten, dass
nichts zur Farbauflösung beiträgt. Es repräsentiert einen
Transparenzwert. Man kann ein Bild also über ein Anderes legen (z.B. tut
das der Webbrowser) und man sieht noch etwas hindurch. Wie viel, sagt
der Alpha-Kanal. Aber wie gesagt: Bei Fotos trägt dieser Wert nichts
bei. Hier sind faktisch 24-Bit und 32-Bit gleichwertig, da die
Transparenz immer auf 0% steht.

Es gibt aber trotzdem noch einen 32-Bit-Farbkanal. Der ist, im Gegensatz
zu 16 Bit, nicht als Festkommawert üblich, sondern es ist eine
Gleitkommazahl. Das sind die Farbkanäle in RawTherapee während der
Bildberechnung. Speichert (im RAM) oder berechnet man nun ein solches
Pixel, sind wiederum 3 Kanäle notwendig. In diesem Fall haben wir also
sogar ein 96-Bit-Pixel. Aber, einfach ist das Leben: Das gibt es hier
nur im Arbeitsspeicher während der Bildberechnung. Sonst nicht. Können
wir also (fast) gleich wieder vergessen und dafür die frei werdende
neuronale Speicherzelle im Gehirn mit der nächsten Information füllen:

Nehmen wir uns nun noch 16-Bit pro Farbkanal vor: Hier wird in in der
Regel (Ausnahme siehe unten) mit Festkomma gearbeitet und abgespeichert,
also natürlichen Zahlen. 16-Bit entspricht einem Farbkanal. Ein Pixel
benötigt aber wieder 3 davon. Deshalb wird hier auch von 48-Bit
gesprochen. (In den seltenen Fällen eines zusätzlichen
16-Bit-Transparenzkanals ergibt sich ein 64-Bit Pixel.)

Aber es gab weitere findige Softwareentwickler. Bei HDR-Bildern will man
ja sehr viel Schattierungsinformation unterbringen. Man kann das mit
16-Bit Ganzzahl, hat dann aber maximal 2^16 Stufen im Farbkanal. Oder
man tut das mit 16-Bit-Gleitkomma. Dies ist nicht so hoch auflösend, wie
32-Bit-Gleitkomma und unsere Prozessoren rechnen auch nicht mit
16-Bit-Gleitkomma. Wenn man aber einen hohen Dynamikbereich abspeichern
möchte und nicht unnütz Speicherplatz verbrauchen möchte, kann man
tatsächlich auf die Idee kommen, statt mit 32-Bit eine Gleitkommazahl
auch nur mit 16-Bit abzuspeichern. Und das ist immer noch recht
hochauflösend. Gesagt, getan. Es gibt also auch ein HDR-Format mit 3
Farbkanälen zu 16-Bit-Gleitkomma, welches ebenfalls 48 Bit benötigt. Und
dann natürlich auch so benannt wird.

Haben wir Dich jetzt vollständig konfus gemacht? Durch die
Mehrdeutigkeiten muss man beim Lesen immer genau aufpassen. Der Kontext
legt fast immer genau fest, welche Auflösung und Kodierung gemeint ist.
Mit RawTherapee haben wir es mit 2 Farbauflösungs-Formaten zu tun die
abgespeichert werden können: 3x8Bit Ganzzahl und 3x16Bit Ganzzahl. Dem
entspricht die *Summe der Farbinformation* von 24 Bit und 48 Bit.
Berechen tut RawTherapee hingegen mit 3x32Bit-Gleitkomma. - Alles klar
mit Dir? Und es geht immer noch eine Stufe komplizierter. Aber nicht
mehr hier.

[Category:General](Category:General.md)
