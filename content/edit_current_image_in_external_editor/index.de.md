---
title: Edit Current Image in External Editor
contributors:
  - Fherb
tags:
  - 'General Information'
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Das aktuelle Bild im externen Editor weiterbearbeiten

RawTherapee ist ein Bildentwickler. Der Schwerpunkt liegt hier beim
Finishing eines Bildes ausgehend vom Rohbild, ohne lokal, zum Beispiel
mit Masken, zu arbeiten. Hast Du mehr mit dem Bild vor, möchtest du es
vielleicht mit einem Grafik-Programm, wie [Gimp](http://www.gimp.org),
[Fotoxx](http://kornelix.net/fotoxx/fotoxx.html),
[Photoline](http://www.pl32.de),
[PaintShop](http://www.paintshoppro.com) oder
[Photoshop](http://de.wikipedia.org/wiki/Adobe_Photoshop)
weiterbearbeiten? Oder einem Programm übergeben, das spezielle Filter
bereit stellt, wie z.B. dem ganz aufs Entrauschen spezialisierten
Programm [Neat Image](http://ni.neatvideo.com)? Wie wäre es mit der
Übergabe an [XnView/XnViewMP](http://www.xnview.com/de/xnviewmp),
[IrfanView](http://http://www.irfanview.de/) oder
[ImageMagick](http://www.imagemagick.org/script/index.php), um z.B. das
Bild sofort in ein Format zu konvertieren, dass RawTherapee nicht
unterstützt. Beachte hierbei: Einige Programme unterstützen keine 16 Bit
Farbauflösung. Übergeben wird das Bild immer als TIFF mit 16 Bit
Farbtiefe pro Kanal.

## Externes Programm konfigurieren

![](ExternEditorCfg_de.png "ExternEditorCfg_de.png") Natürlich kannst du
dein Bild auf ganz normalem Weg abspeichern und dann mit dem Programm
deiner Wahl wieder öffnen. Mit der hier beschriebenen Technik kannst du
das Bild ziemlich unmittelbar übergeben und in dem anderen Programm
sofort weiter arbeiten. Denn RawTherapee wird nicht nur dein Bild für
eine Weiterverarbetung speichern, sondern das Programm auch gleich
versuchen aufzurufen. Dazu musst du den Aufruf aber in RawTherapee
parametriert haben.

Falls Du Gimp oder Adobe Photoshop verwendest, kennt RawTherapee den
Aufruf und du musst nur den Installationspfad einstellen. Dies findest
Du unter
![<File:Gtk-preferences.png>](Gtk-preferences.png "File:Gtk-preferences.png")
*Einstellungen \> Allgemein \> Externer Editor*. Für andere Programme
kannst du im letzten Punkt direkt den Kommandozeilenaufruf eintragen.
Ein Leerzeichen und den Namen des Bildfiles hängt RawTherapee dann
automatisch an.

Hier einige Beispiele unter Windows:

`C:\Program Files (x86)\IrfanView\i_view32.exe`  
`C:\Program Files\XnViewMP\xnviewmp.exe`  
`C:\ProgramsPortable\Photoline\PhotoLine64.exe`  
`C:\Program Files\Neat Image Standalone\NeatImage.exe`

Hier einige Beispiele unter Linux (getestet mit Kubuntu):

`/usr/bin/gimp`  
`/usr/bin/okular`  
`/usr/bin/display-im6`  
`/usr/bin/fotoxx`

Ist unter Linux die Zielanwendung ein Windowsprogramm, dass unter Wine
installiert wurde, sieht so ein Pfad etwas länger aus (hier am Beispiel
NeatImage):

`/home/meinName/.wine/drive_c/Program Files/Neat Image/NeatImage.exe`

### Mit Linux unter Wine

Nutzt du RawTherape unter Linux Wine, funktioniert der Aufruf nicht ganz
so einfach, da das temporäre Verzeichnis von RawTherapee als
Windows-Laufwerk interpretiert und z.B. Gimp, direkt in Linux
installiert (also nicht die Windows-Variante unter Wine), damit nichts
anfangen kann. Lösung: Wir müssen den Standardordner für temporäre
Dateien in Windows (also Wine) ändern. Wir legen ihn auf den
Linux-Standardordner */tmp*:

- Öffne die Windows-Registry von Wine auf der Linux-Kommandozeile mit

`wine regedit`

- Wechsle dort zu *HKEY_CURRENT_USER\Environment*
- Doppelklicke auf den Schlüssel *TEMP* (nicht *TMP*)
- Ändere nun den Pfad von *C:\users\allesMeine\Temp* zu **/tmp**
  (Wichtig: Kein Backslash \\ für den Root-Ordner, sondern ein normaler
  Schrägstrich **/** , wie unter Linux üblich.)
- Registry schließen und RawTherapee starten (bzw. RawTherapee neu
  starten, wenn es offen war)
- Gimp zum Beispiel rufst du nun mit der Zeile **/usr/bin/gimp** auf.
  (Auch hier die Ordner-Trennzeichen wie in Linux üblich schreiben. Also
  genau so, wie die Beispiele oben.)

Ist das Zielprogramm ebenfalls ein Windowsprogramm, dass du unter Wine
installiert hast, kanst du entweder den vollen Linux-Pfad angeben, wie
oben, oder den Windowspfad. Zum Vergleich mit oben:

`C:/Program Files/Neat Image/NeatImage.exe`

## Externen Editor aufrufen

Hast du dein Bild soweit, dass du es extern weiterverarbeiten willst,
brauchst du nur den Button
[image:Image-editor.png](image:image-editor.png) *Bild im
externen Editor öffnen* drücken. Das Bild wird von RawTherapee berechnet
und dann das eingestellte Programm gestartet.

## Müll beseitigen

Das File, das RawTherapee übergibt, wird mit dem nächsten Aufruf des
Editors nicht überschrieben, sondern es wird ein anderer Name verwendet.
Fotos von hoch auflösenden Kameras erreichen schnell die 100
MByte-Marke. Nutzt du diese Funktion mehrfach, sammeln sich schnell
Daten im Gigabyte-Bereich. Je nach Betriebssystem liegen diese
Übergabe-TIFFs an unterschiedlichen Stellen. Im Normalfall handelt es
sich um einen [vom Betriebssystem vorgegebenen temporären Ordner, den
RawTherapee verwendet](File_Paths/de#Tempor.C3.A4rer_Ordner.md).
