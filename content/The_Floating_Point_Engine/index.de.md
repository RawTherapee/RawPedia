---
title: The Floating Point Engine
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

# Gleitkomma-Berechnung in RawTherapee

RawTherapee rechnet grundsätzlich in hoch genauer
32-Bit-[Gleitkomma](https://de.wikipedia.org/wiki/Gleitkommazahl)-Rechnung.
Ganz im Gegensatz zu 16-Bit-Integer-Berechnungen, die derzeit immer noch
in vielen Anwendungen, wie z.B. im Raw-Konverter
[DCRaw](https://de.wikipedia.org/wiki/DCRaw) verwendet werden. Das
Gleitkommaverfahren stellt sicher, dass unabhängig vom Absolutwert, z.B.
eines Pixelhelligkeitswertes, die Berechnung immer mit der gleichen Zahl
signifikanter Stellen ausgeführt wird. Das heißt also, kleine Werte,
z.B. dunkle Pixelwerte, werden mit genau so viel Auflösung verrechnet,
wie sehr helle Pixel. Durch die 32-Bit-Technik ist dabei die verwendete
Auflösung so hoch, dass Rundungsfehler selbst bei vielen
aufeinanderfolgenden Filterberechnungen (Bildverarbeitungsfunktionen)
absolut keine im Bild sichtbare Rolle spielen oder irgendwelche
Artefakte, Rauschen oder Informationsverluste hinterlassen.

Klassische Raw-Konverter arbeiten mit 16-Bit-integer-Verarbeitung. Das
liegt daran, dass bei früheren Prozessorgenerationen die
Ganzzahlrechnung deutlich weniger Zeit benötigte, als die
Gleitkommarechnung. Die Softwareentwickler waren also bemüht, Auflösung
und Rechengeschwindigkeit gegeneinander zu optimieren. Das ist heute
nicht mehr notwendig und RawTherapee hat deshalb vollständig auf
Gleitkommarechnung umgestellt.

Wenn Du denkst, das die Kamera ja sowieso nur mit 12 bis 14 Bit
Auflösung arbeitet, dann vergiss nicht, dass die Filterfunktionen im
Programm sehr viele Informationen verwenden, um dann ein Bild in Deiner
gewünschten Qualität zu berechnen. Dafür reicht es nicht, mit 16 Bit
Festkommawerten zu rechnen. Es ergeben sich sehr kleine, wie sehr große
Zwischenwerte, die mit 16 Bit dann nicht mehr ausreichend genau
aufgelöst werden. Bei Gleitkomma passt sich die Auflösung eines Wertes
immer automatisch an den Absolutwert dieser Größe an. Und es sind auch
keine Tricks des Softwareentwicklers nötig, um in solchen Fällen
möglichst wenig Informationen zu verlieren. Bei Gleitkomma ist die
Auflösung immer konstant hoch (bezogen auf die Dekaden das
Dezimalsystem) und wird mit jedem Rechenschritt wieder neu auf ihren
auflösungstechnischen Maximalwert skaliert.

Speicherbedarf: 32 Bit Gleitkomma benötigen genau Faktor 2 mehr als 16
Bit-Berechnungen. Nach dem [Demosaicing](demosaicing/de)
haben wir dann sogar 3 Stück 32-Bit-Werte pro Pixel. Während der
Berechnung des Bildes müssen unter Umständen gleichzeitig auch mal 2
Felder der Bildinformationen angelegt werden, um das Bild Schritt für
Schritt durchzurechnen. Nehmen wir heutige hochauflösende Kameras zum
Standard (paar'n 30 MPixel ist nicht selten, aber es gibt im
Mittelformatbereich auch schon über 100 Megapixel und es gibt
zusammengesetzte Panoramafotos), ist auf einem 32-Bit-System unter
Umständen die maximal adressierbare Speichergröße erreicht
(Beispielrechnung als Faustformel leicht skalierbar: 100M-Pixel mal 3
Farbwerte \* 4 Byte ergeben für ein einziges Bild-Datenfeld im RAM 1,2
Gigabyte. Also Pixelzahl mal 12 ergibt Byte pro Bild.). RawTherapee
stürzt also bei sehr großen Bildern unter Umständen wegen des fehlenden
Arbeitsspeichers ganz "gezielt" ab, weil das Betriebssystem die
Speicherverwaltung überwacht und die Notbremse zieht.
Speicherplatzprobleme können aber auch an anderen Stellen auftreten. Zum
Beispiel, wenn RawTherapee einen Bilderordner darstellt. Insofern ist
bei einer derartigen Nutzung ein 64-Bit-System unbedingt vorzuziehen.

## Was tun bei Speichmangel?

Für die Leute, die noch mit 32-Bit-Systemen arbeiten müssen oder nur 4
Gigabyte Speicher im Rechner haben, gibt es folgende Tipps, den
Speicherraum für die Arbeit mit RawTherapee zu optimieren:

- Eine allgemeine Regel ist, dass in einem Bearbeitungsordner nicht mehr
  als 100 Bilder liegen sollten, damit in der Dateiverwaltungsansicht
  kein Speicherplatzmangel herrscht.
- Öffne die Dateiverwaltungsansicht auch nicht, wenn Bilder berechnet
  werden (Speichern läuft bzw. Bilder in der Warteschlange werden gerade
  abgearbeitet).
- Nutze einen Trick, um unter Windows auch die letzten Megabyte für
  Anwendungen frei zu geben: [4-Gigabyte Tuning: BCDEdit and
  Boot.ini](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)
  und [How to set the /3GB Startup Switch in Windows XP and
  Vista](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)
- Schließe alle anderen Programme
- Schalte in der Warteschlange "Automatisch starten" ab. Starte die
  Abarbeitung erst, wenn Du weder Bilder bearbeitest, noch planst, die
  Dateiverwaltungsansicht mit vielen Bildern im Ordner nochmal zu
  öffnen.
- Nutze die Warteschlange zur Bildverarbeitung und nicht den
  Speichern-Button im Editor, denn dann erfolgt das Berechnen während
  des geöffneten Editors (s. oben)
- Etwas Platz kann geschaffen werden, indem Du im Ordner
  ...\iccprofiles\input all die \*.icc Profilfiles löschst, die Du für
  deine Kamera(s) nicht benöigst. Oder benenne sie. Zum Beispiel in
  \*.icc.unused .
- In den Einstellungen sollten die Ordner für Dunkel- und Weißbilder
  nicht auf einen Ordner zeigen, in dem Raw-Bilder enthalten sind, wenn
  Du Dunkel- und Weißbilder gar nicht verwendest.
- Die Werkzeug mit den höchsten Arbeitsspeicherverbräuchen sind
  *Dynamikkompression*, *Kontrast nach Detailstufen* und die *Lichter
  rekonstruieren* mit der Methode "Farbübertragung". Verwende die
  Funktion notfalls nicht, wenn Dein Rechner zu knapp bemessen ist.

[Category:General](category:general)
