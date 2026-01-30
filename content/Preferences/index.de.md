---
title: Preferences
contributors:
  - Fherb
tags:
  - 'General Information'
---

Todo-List / State:

- Translation: completed without uncleared points
- Content completely cleared: no
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Einstellungen

Du kannst den Dialog zur Konfiguration der hier beschriebenen
Einstellungen jederzeit über das Symbol
[image:Gtk-preferences.png](image:gtk-preferences.png)
erreichen.

**Beachte: Auch in Version 5 ist dieses Icon in der Oberfläche nicht
enthalten, wenn du Rawtherapee so startest, dass ein Bildfile dem zu
startendem RawTherapee direkt übergeben wird (z.B. Kommandozeile oder
z.B. als *Standardprogramm* für Raw-Files).** Willst du die
Eigenschaften ändern, starte RawTherapee ohne die Übergabe eines
Bildfiles.

Beachte weiterhin: Bei einer Reihe von Einstellungen findest du den Text
***(erfordert Neustart)***. Wie du sicher erahnen kannst, wird eine
Konfiguration dort erst nach einem Neustart von RawTherapee aktiviert.
Manchmal fehlt direser Hinweis aber. Start neu, wenn sich nichts tun
sollte.

**Standardeinstellungen**

Bei den meisten Einstellmöglichkeiten, insbesondere der Oberfläche,
wirst du erkennen, dass der Standard in der überwiegenden Einsatzfälle
schon der optimale Wert ist. RawTherapee lässt dir trotzdem Alternativen
offen, damit du die Oberfläche auf deinen Workflow noch besser abstimmen
kannst. Bei den Bildern in diesem Handbuch, wie auch in vielen Tutorials
im Internet wirst du allerdings immer wieder die Standardeinstellung in
der Darstellung vorfinden. Mache dich also zuerst mit dem Standard
vertraut und passe erst dann die Einstellungen deinem speziellem
Workflow an.

## Button *Über*

Neben wichtigen Informationen zur aktuellen Version werden einige
weitere grundsätzliche Informationen zur Compilierung, zur Lizenz und
den beteiligten Entwicklern angezeigt.

## Registerkarte *Allgemein*

### Layout

Editor-Layout  
Die Oberfläche bietet dir 4 grundsätzliche Betriebsarten:

- Ein-Reitermodus
- Ein-Reiter-Modus (vertikale Reiter)
- Multi-Reitermodus
- Multi-Reitermodus (auf zweitem Monitor, wenn verfügbar)

Beachte, dass der Multi-Reitermodus zwar sehr bequem ist, gleichzeitig
mehrere Bilder zu bearbeiten. Allerdings benötigt dieser Modus auch
entsprechend mehr RAM. Solange History und Schnappschüsse noch nicht im
Sidecar-File eines Bildes abgelegt werden können, ist dieser Modus
jedoch wichtig, um bei der Bearbeitung mehrerer Bilder gleichzeitig auch
deren History und Schnappschüsse zu erhalten. Statte Deinen Rechner
entsprechend mit RAM aus, falls du den Multi-Reitermodus sehr extensiv
nutzt.

<!-- -->

Position des Kurven-Buttons  

:\* Oben

:\* Rechts

:\* Unten

:\* Links

  
Keine Ahnung, was das sein soll. :-/

<!-- -->

Histogramm linksseitig  
In der Standardeinstellung ist das Häkchen gesetzt. Das Histogramm kann
aber auch im Editor auf der rechten Seite angezeigt werden. Jedoch hat
die rechte Position den Nachteil, dass sie den Anzeigebereich der
Werkzeuge verringert.

<!-- -->

Einzeilige Toolbar  

<!-- -->

  
Keine Ahnung, was diese Einstellung bewirkt. :-/

<!-- -->

Das Arbeitsprofil zur Darstellung des Haupthistogramms verwenden  

<!-- -->

  
Keine Ahnung, was diese Einstellung bewirkt. :-/

<!-- -->

Toolbar oberhalb des Filmstreifens anzeigen  
Belendet im Editor-Fenster die Toolbar, die überwiegend zur Filterung
verwendet werden kann, über dem Filmstreifen ein.

<!-- -->

Werkzeugbereich  
**Keine vertikale Scrollbar**

Lasse den Punkt immer ausgeschaltet, falls Du nicht mit dem
Maus-Scroll-Rad arbeitest:

Du kannst im eingeschalteten Zustand die Werkzeugbox auf der rechten
Seite des Editors nicht mehr mittels Balken hoch und runter scrollen.
Der Scroll-Balken wird entfernt. Willst Du an untere Werkzeuge kommen,
musst du zuerst die Oberen wieder zu klappen. Und längere Werkzeuglisten
sind nur vollständig zu bedienen, wenn du das Scrollrad an der Maus
(oder Touch-Pad-Gesten) verwendest.

<!-- -->

  
**Symbole statt Text in Karteireitern**

Wenn abgeschaltet: Inkonsistente Einstellung (in Version 5): Alle
Werkzeugreiter im Editor oder der Dateiverwaltung werden gegen Texte
ausgetauscht. Nur das Wavelet-Tool behält sein Symbol. Lasse diese
Option eingeschaltet! Du lernst schnell die Bedeutung der Icons.
Außerdem hilft dir der Tool-Tipp-Text, wenn du mit der Maus über einen
der Reiter fährst.

### Sprache für Menüs und Dialoge

Systemsprache verwenden  
RawTherapee übernimmt die Systemeinstellung bei
64-Bit-Windows-Betriebssystemen.

<!-- -->

Sprache  

<!-- -->

  
**Deutsch**

Stelle das ein und gut. ;-) Wechsle auf *Englisch (UK)*, falls etwas
nicht funktioniert und du einen englischen Bugreport schreiben möchtest.
Dann siehst du, was die Entwickler unter einem speziellen Begriff
verstehen.

### Oberflächendesign

Oberflächendesign  
Gegenüber dem Standard *RawTherapee* hat TooWaBoo hier einen Standard
*TooWaBlue* etabliert, der etwas kontrastreicher die Einstellreglerwerte
und Icons hervorhebt. Eventuell kommen noch weitere Designs hinzu.

<!-- -->

Schriftart  
Setzt Schriftart und Größe für die Oberfläche.

RawTherapee bringt seinen eigenen Schriftfont mit. Damit ist ein
Arbeiten unter verschiedenen Betriebssystemen nicht von deren
Font-Voraussetzungen und -Interpretationen abhängig. Entsprechend der
Bildschirmauflösung und Pixeldichte des Bildschirms kann hier die
richtige Fontgröße eingestellt werden. Nachteil ist allerdings, dass der
Font nicht vom Betriebssystem skaliert und
"[gedithert](https://de.wikipedia.org/wiki/Dithering_(Bildbearbeitung))"
wird. Erscheint dir die Darstellung am Bildschirm ungeeignet oder zu
anstrengend, versuche hier verschiedene Einstellungen.

<!-- -->

Schriftart für den Farbwähler  
Das Farbwählerwerkzeug
[image:ColorPickerTool.jpg](image:colorpickertool.jpg) zeigt
im Bild die Werte der 3 Farbkanäle an. Die Darstellung dieser Anzeige
kann hier eingestellt werden.

<!-- -->

Farbe/Transparenz für Schnittmaske  
Wenn du dein Bild bescheidest, wird der Rand, der abgeschnitten wird,
anders dargestellt. Du kannst hier einstellen, ob der beschnittene Rand
als dunkle Transparenz des Bildeinhaltes dargestellt werden soll, oder
statt dessen ein Farbrahmen verwendet werden soll. In der Regel ist die
Grundeinstellung der abgedunkelten Transparenz ein ziemlich sinnvoller
Einstellwert, weil damit auch abgeschnittene Bilddetails noch schwach
dargestellt werden und es dir leichter fällt, den Beschnitt zu
korrigieren.

<!-- -->

Farbe der Navigationshilfe  
Im Navigator wird der aktuelle Bildausschnitt mittels Rahmen
dargestellt, und man kann ihn dort verschieben. Diese Einstellung legt
die Farbe dieses Rahmens fest.

### Anzeige zu heller/dunkler Bereiche

Für die mit den Icons [image:Warnhl.png](image:warnhl.png)
und [image:Warnsh.png](image:warnsh.png) zuschaltbare Anzeige
für zu helle oder dunkle Bildbereiche (Pixel) können hier die beiden
Schwellen eingestellt werden. Es werden hierbei die Pixelwerte des
fertigen Bildes entsprechend des eingestellten Ausgabeprofils verwendet.

### Navigation

Mausgeschwindigkeit beim Bewegen von Bildern  
Beim Verschieben eines Bildes im Editor mit der Maus, wird pro
"Mauspixel" das Bild um die hier eingestellte Anzahl von Bildpixeln
verschoben. Damit reicht eine geringere Mausbewegung aus, um auch bei
großen Bildern in hoher Auflösung das Bild recht weit hin und her zu
schieben. Der Effekt macht sich um so mehr bemerkbar, je stärker das
Bild gezoomt ist.

<!-- -->

Zoom und Bildposition merken  

<!-- -->

  
Keine Ahnung, was das bewirkt. :-/

### Externer Editor

Diese Konfiguration wird auf der Seite [Das aktuelle Bild im externen
Editor
weiterbearbeiten](Edit_Current_Image_in_External_Editor/de.md)
ausführlich beschrieben.

## Registerkarte *Bildbearbeitung*

### Standard-Bildverarbeitungsparameter

Für RAW-Dateien  
Hier kann ein Bildverarbeitungsprofil voreingestellt werden, dass
RawTherapee standardmäßig ausführt, wenn ein RAW-File das erste Mal
geöffnet wird. RawTherapee erkennt das erstmalige Öffnen daran, dass
noch kein Bildverarbeitungsprofil als Sidecar-File für dieses RAW-File
vorhanden ist. Standardwert nach Installation ist das Profil "Default".

<!-- -->

  
Wünschst du, dass RawTherapee keine einzige Veränderung am Bild vor
nimmt (ausser den Weißabgleich der Kamera zu übernehmen), dann wähle
hier "Neutral".

<!-- -->

Für Bilddateien  
Für alle Bilddateien, also Nicht-RAW-Bilder, kann hier ein
Bildverarbeitungsprofil eingestellt werden, dass RawTherapee genau dann
lädt, wenn zu dem betreffenden Bild noch kein Bildverarbeitungsfile
(Sidecar-File) im betreffenden Bildordner liegt. Standardwert nach der
Installation ist das Profil "Neutral", dass keinerlei Veränderungen am
Bild ausführt.

<!-- -->

Standardprofile verwenden  
Entfernst du das Häckchen, wird für alle Bilder das Profile "Neutral"
eingestellt.

### Benutzerdefinierter Bildprofilgenerator

Anwendungspfad  
Ein ausführbares Programm oder ein Script kann hier angegeben werden,
dass automatisch aufgerufen wird, wenn zu einem Bild erstmalig ein neues
Bildverarbeitungsprofil angelegt wird. Dazu wird ein
"Kommunikationsfile" im \*.ini-Stil (auch als Schlüsselfile bekannt) von
Rawtherapee erzeugt und dieses als Kommandozeilenparameter mit
angehangen. Dieses File enthält verschiedene Parameter zum Bild, mit der
die Anwendung oder das Script regelbasiert ein Bildverarbeitungsprofil
erzeugen kann.

<!-- -->

  
Diese Funktion ist sehr wirksam. Zum Beispiel können vom Programm oder
Script linsenabhängige Bildverarbeitungsprofil-Werte zur Korrektur von
Verzerrungen voreingestellt werden. Diese Funktionalität wird nur beim
ersten Aufruf eines Bildes ausgefüht, wenn noch kein
Bildverarbeitungsprofil vorhanden ist. Ausserdem kann man es mit der
Hand aus dem Kontextmenü heraus ausführen, das angezeigt wird, wenn man
in der Dateiverwaltung oder im Filmstreifen mit der Maus rechts auf ein
Miniaturbild klickt.

<!-- -->

  
Hinweis: Wenn Leerzeichen im Pfad enthalten sind, muss der Eintrag hier
in Anführungszeichen eingeschlossen werden.

<!-- -->

Format  
Hier wird festgelegt, wie der Inhalt im Kommunikationsfile abgelegt
wird.

### Behandlung der Bearbeitungsprofile

#### Verarbeitungsparameter zusammen mit Datei speichern (Sidecar)

Diese Methode ist der Standard: RawTherapee speichert alle Parameter der
Bildverarbeitung als pp3-File in das Verzeichnis der Quelle. Beim
nächsten Öffnen des Bildes wird automatisch dieses Bearbeitungsprofil
mit geöffnet und es alle Werkzeuge entsprechend wieder hergestellt.

#### Verarbeitungsparameter im Zwischenspeicher speichern

Gemeint ist der Cache-Ordner, den die RawTherapee-Installation
verwendet. Diese Option kann parallel oder alternativ zur Ersten gewählt
werden. Allerdings sind sämtliche Einstellungen verloren, wenn der
Cache-Ordner gelöscht wird oder RawTherapee als neue Instanz oder auf
einem anderen Rechner installiert wird.

In der Regel sollte die erste Option eingeschaltet und die Zweite
abgeschaltet werden.

Beachte:  
Bei der Verwendung des Cache als Ablageort der Bearbeitungsprofile kann
RawTherapee dort gespeicherte Profile nur so lange den Bildern richtig
zuordnen, wie diese sich im Verzeichnispfad an exakt der gleichen
Position befinden. Werden die Bilder verschoben oder auch nur ein Ordner
im Pfad umbenannt, erscheinen die Bilder wieder als unbearbeitet und man
muss sich mit der Hand das richtige Bearbeitungsprofile direkt im
Cache-Ordner herausangeln.

### Dunkelbild

Sollen Dunkelbilder der Kamera(s) verwendet werden, ist hier der Ordner
einzustellen, in dem diese abgelegt sind.

### Weißbild

Sollen Weißbilder der Kamera(s) verwendet werden, ist hier der Ordner
einzustellen, in dem diese abgelegt sind.

### Filmsimulation

Die Filmsimulation beruht auf sogenannten *Hald Color Look-Up-Tabellen*.
Hier wird der Ordner eingestellt, in dem diese abgelegt wurden. Weiteres
siehe in [Film Simulation](film_simulation/de).

### Metadaten

Wenn die Option *Exif/XMP unverändert in die Ausgabedatei übernehmen*
gesetzt ist (Standard), dann werden sämtliche Änderungen der Metadaten
in ![<File:Meta.png>](Meta.png "File:Meta.png") verworfen und es werden
die originalen Metadaten verwendet. Um Metadaten zu verändern, muss
diese Option deaktiviert werden.

## Registerkarte *Dateiverwaltung*

### Bildverzeichnis beim Programmstart

Stelle hier ein, welches Verzeichnis beim Starten von RawTherapee in der
Dateiverwaltung geöffnet werden soll.

### Bildinformationen und Miniaturbilder

Diese Einstellungen legen fest, welche Informationen zu den
Miniaturbildern angezeigt werden sollen.

Zeige das eingebettete JPEG als Miniaturbild, wenn die RAW-Datei noch nicht editiert wurde  
Als Standard ist diese Option eingeschaltet. Wichtig ist aber, sich
hierbei nicht verwirren zu lassen:

<!-- -->

  
Solange noch kein Profilbild angelegt ist, wird bei eingeschalteter
Option das verkleinerte Bild so angezeigt, wie die Kamera ihr
**JPEG-Bild (!)** entwickelt hat und nicht, wie das unbearbeitete Raw
aussieht. Sobald das Raw das erste Mal im Editor geöffnet wurde und ein
Profilfile angelegt wurde, wird hier nun das Raw in etwa so angezeigt,
wie sich das Bild nach der Entwicklung darstellt.

<!-- -->

  
Wenn die Option abgeschaltet ist, wird auch bei unbearbeiteten
Raw-Bildern der unbearbeitete Zustand in den Miniaturbildern angezeigt.

<!-- -->

  
**Empfehlung:**

<!-- -->

  
Wenn du mit der Dateiverwaltung vor der Entwicklung die Raw-Bilder
sichtest und sortierst bzw. bewertest, um die Bilder sinnvoll für die
Bearbeitung zu gruppieren, bzw. z.B. die ersten Belichtungskorrekturen
oder den Weißabgleich grob gleich in der Dateiverwaltung im
Batch-Verfahren durchführen willst, **dann ist es sinnvoll, diese Option
abzuschalten.**

### Menüoptionen

Diese Einstellungen betreffen die Kontextmenüs auf den Miniaturbildern
in der Dateiverwaltung und im Filmstreifen. Alle hier aufgeführten
Punkte sind immer Bestandteil des Kontextmenüs. Die selektierten Gruppen
werden dann allerdings als Untermenüs im Kontextmenü zusammengefasst.
Das macht das Kontextmenü kleiner, bedarf aber zwei Schritte zur
Auswahl.

Änderungen sind erst nach einem Neustart aktiv.

### Einstellungen des Festplatten-Cache für Miniaturbilder

Falls in der *Registerkarte Bildbearbeitung* unter *Behandlung der
Bearbeitungsprofile* die Option *Verarbeitungsparameter im
Zwischenspeicher speichern* ausgewählt ist, betreffen hier die Buttons
*Profile löschen* und *Alles löschen* auch die gespeicherten
Bearbeitungsprofile im Cache!

Du kannst eine andere Maximalgröße (in der Höhe) für die Miniaturbilder
in der Dateiverwaltung und im Filmstreifen einstellen. Vergrößere den
Wert, wenn du einen leistungsfähigen Rechner und einen großen bzw.
hochauflösenden Monitor hast. Du kannst so vor allem in der
Batch-Verarbeitung die Bilder besser beurteilen.

Wird die hier angezeigte Maximalanzahl der im Cache abgelegten Bilder
überschritten, werden Miniaturbilder gelöscht. Der einzige Nachteil
dabei: Wird ein Bild in der Dateiverwaltung oder im Filmstreifen
angezeigt, dessen Miniaturbild inzwischen aus dem Cache gelöscht wurde,
muss RawTherapee es dort neu erstellen.

Die Buttons dienen dazu, den Cache-Ordner aufzuräumen.

### Dateitypen anzeigen

Nur Dateien, deren Endung hier aktiviert sind, werden in der
Dateiverwaltung als Bild betrachtet und angezeigt. Es lassen sich
weitere Endungen hinzufügen.

## Registerkarte *Farbmanagement*

### ICC-Profil-Verzeichnis

Stele hier das Verzeichnis ein, in dem deine ICC-Profile für Monitor und
Drucker liegen.

### Monitor

Standardfarbprofil  
Wenn du für deinen Monitor ein ICC-Profil bekommen hast bzw. durch
Messung selbst erstellt hast, kannst du das hier einstellen. Beachte
dabei, auch die Einstellungen im Monitor-Menü genau so einzustellen, wie
du das bei der Erstellung des Profiles eingestellt hattest. Bei
Profilen, die mitgeliefert wurden oder die du anderweitig bekommen hast,
sollten diese Einstellwerte mit angegeben sein. Falsche Einstellungen
liefern falsche Farben.

<!-- -->

  
Unter **macOS** wird durch RawTherapee immer der sRGB-Farbraum
verwendet. Es lässt sich hier kein Profil auswählen. Die Verarbeitung
des Bildes durch das Betriebssystem vor der Ausgabe auf dem Monitor
korrigiert dann die Farben.

<!-- -->

Automatisch das für den aktuellen Monitor festgelegte Profil verwenden  
Diese Option wird derzeit **nur unter Windows unterstützt**. Hast du da
bereits das Profil ordentlich festgelegt, kannst du die Option setzen
und diese Einstellung für RawTherapee übernehmen. Beachte aber, dass bei
mehreren Monitoren hier immer das Profil des Hauptmonitors übernommen
wird. Nutzt du RawTherapee nicht auf dem Hauptmonitor, schalte diese
Funktion ab und stelle das Profil per Hand für diesen Monitor ein.

<!-- -->

  
Die **Linux**-Version unterstützt keine automatische
Profilkonfiguration. Nutzt du aber hier das ICC-Profil, mit dem der
Monitor kalibriert wurde, ist auch auch die Darstellung auf einem
Wide-Gamut-Monitor korrekt. Wenn du mehrere Monitore nutzt, stelle hier
das Profil des Monitors ein, auf dem du RawTherapee öffnest.

<!-- -->

Standard-Rendering-Intent  
Das Auswahlmenü lässt dich wählen, wie RawTherapee das ICC-Farbprofil
zur Transformation der Gamuts bzw. Farbräume verwendet. Der Grund dafür
liegt darin, dass auf dem Zielmedium unter Umständen nicht der gesamte
Farbraum des Bildes dargestellt werden kann. Mit Rendering-Intent wählst
du eines der Verfahren aus, mit denen dieses Problem bei der
Bildumrechnung auf das Ausgabemedium gelöst wird.

<!-- -->

  
Zur Erklärung gibt es hier nur eine "Kurzfassung". Für weiterreichende
Informationen, siehe hierzu bitte [Wikipedia: Rendering intent
(englische
Version)](https://en.wikipedia.org/wiki/Rendering_intent#Rendering_intent)
und [Wikipedia: Rendering Intent (deutsche
Version)](https://de.wikipedia.org/wiki/Rendering_intent).

:;Wahrnehmungsabhängig

  
  
Ist der Farbbereich des Bildes größer als der des Ausgabemediums, wird
der Farbbereich komprimiert, um ihn an den Gamut des Ausgabemediums
(-gerätes) bestmöglich anzupassen. Das kann zu einer etwas geringeren
Sättigung führen, der Farbton wird aber gehalten. Das Bild kann deshalb
unter Umständen etwas flau wirken.

<!-- -->

  
  
Die in ICC vorgesehene Variante *Sättigung* bzw. *Saturation* ist in
RawTherapee nicht vorgesehen, entspricht aber weitestgehend der
wahrnehmungsabhängigen Umrechnung.

:;Relativ farbmetrisch

  
  
Die Farben, die im Bild, wie im Medium dargestellt werden können, werden
zu 100% genau übertragen. Sind Farben des Bildes nicht auf dem
Ausgabemedium darstellbar, werden die nächstgelegenen Farbwerte
verwendet. Das kann in diesen Bereichen zu einer "Bündelwirkung" führen.
Der Weißpunkt wird dabei korrigiert.

:;Absolut farbmetrisch

  
  
Ähnlich *Relativ farbmetrisch*. Der Weißpunkt wird aber nicht
korrigiert. Wenn die Gamuts von Bild und Ausgabemedium in etwa
übereinstimmen, ist die Verwendung zu empfehlen. Diese Einstellung wird
auch verwendet, wenn ganz spezifische Farben (z.B. Stoff-Farben oder
Farben eines [Corporated
Design](https://de.wikipedia.org/wiki/Corporate_Design)) exakt
übernommen werden sollen. Diese müssen dafür aber natürlich im
darstellbaren Farbbereich des Ausgabemediums liegen.

<!-- -->

Schwarzpunkt-Kompensation  
Wenn ausgewählt (Standard), wird der Schwarzpunkt des Bildes auf das
Ausgabemedium angepasst. Das bedeutet, dass allein (!) der
Helligkeitskanal für das Ausgabemedium umgerechnet wird. Dieses
Verfahren erhält die Zeichnung in den Schatten, allerdings auf Kosten
der Farbtreue.

### Drucker (Soft-Proofing)

Für die Ausgabe auf Drucker oder Belichter kann hier analog zum Monitor
das passende Farbprofil ausgewählt werden, um auf dem Bildschirm (!) das
Rendering des gedruckten Bildes zu simulieren (Soft-Proofing). Damit das
funktioniert, muss auch das Farbprofil des Monitors richtig eingestellt
sein.

Für die einzelnen Einstellwerte siehe oben unter *Monitor*.

### CIECAM02-spezifische Einstellungen

Zu diesem Farberscheinungsmodell siehe bitte auch [Wikipedia
CIECAM02](https://de.wikipedia.org/wiki/CIECAM02).

Wiedergabegeräte, wie Monitore, Beamer, TV-Geräte, könnten nach dieser
Spezifikation einige Parameter besitzen, die hier eingestellt werden
können.

## Registerkarte *Stapelverarbeitung*

### Verhalten

Bilder als *Batch*, bzw. als *Stapel*, zu bearbeiten erlaubt,
Bildkorrekturen parallel für mehrere Bilder auszuführen. Dabei werden
nicht mehrere Bearbeitungsschritte hinterher auf einen Bilderstapel
angewendet, sondern die Bilder werden in der Dateiverwaltung zuerst
gemeinsam ausgewählt und jede Einstellung wird dann sofort auf die
Bilder übertragen. Das ist der Grund, weshalb in der Dateiverwaltung
auch sämtliche Werkzeuge angeboten werden, die auch im Editor vorhanden
sind. Siehe zu diesem Thema in die Seite
[Batch-Bearbeitung](batch_adjustments_-_sync/de).

In [Batch-Bearbeitung](batch_adjustments_-_sync/de) wird
beschrieben, was passieren kann, wenn mehrere Bilder angewählt sind,
aber ein Einstellwert in diesen Bildern verschiedene Werte besitzt: Ein
neuer Wert überschreibt den Bisherigen in allen Bildern gleichzeitig
(***setzen**''). Oder die neue Wertänderung wird auf den bisherigen wert
jedes einzelnen Bildes separat addiert (***hinzu**''). Auf dieser
Registerkarte kannst du nun für alle Werkzeuge einstellen, welche der
beiden Varianten verwendet werden soll:

*Hinzu*-Mode  
Parameteränderungen werden "relativ" auf den gleichen Parameter in allen
ausgewählten Bildern angewendet. Das heißt, vom bisherigen Wert um den
verstellten Wert "verschoben".

*Setzen*-Mode  
Sobald ein Parameter mit dieser Konfiguration angefasst und bewegt wird,
wird in allen selektierten Bildern dieser neue Wert absolut übernommen.
Egal, wo der Wert in den einzelnen Bildern bisher stand. Der
Einstellparameter wird sozusagen über alle gewählten Bilder
gleichgeschaltet. - Bei vielen Parametern ist das nicht das, was du
möchtest. Wähle den *Setzen*-Mode also mit Bedacht aus.

### Bestehende Ausgabedateien überschreiben

In der Regel sollte diese Option abgeschaltet sein. Speicherst du nun
ein Bild, dass schon existiert, hängt RawTherapee eine Zahl an den
Dateinamen, sodass das vorherige Bild nicht überschrieben wird. Wenn
z.B. "output.jpg" schon existiert, speichert RawTherapee das gleiche
Bild beim zweiten Mal unter dem Namen "output-1.jpg". Beim dritten Mal
unter "output-2.jpg" usw.

Wählst du diese Option aus, wird ein bisher schon ausgegebenes Bild,
dessen Dateiname beim Speichern wieder verwendet wird, überschrieben.
Wenn Du über die Warteschlange ein Bild z.B. in mehreren
Beschnittvarianten ausgeben möchtest, wird dir das bei eingeschalteter
Option nicht gelingen: Nur die letzte Variante bleibt auf der
Festplatte!

## Register *Performance und Qualität*

Die Beschreibung der Parameter ist im Englischen noch sehr lückenhaft.
Da keinerlei praktische Fakten daraus hervor gehen, bleibt dieser
Abschnitt vorerst unübersetzt.

------------------------------------------------------------------------

The "Performance" tab is only for people who know what they're doing. It
lets you poke under the hood and tweak the parameters of some tools.
These parameters take part in the balance between speed and stability.

### Maximum Number of Threads for Noise Reduction

The [Noise Reduction](noise_reduction) algorithm in
RawTherapee is very powerful. It is also quite CPU and memory intensive.
People with weak hardware who experience crashes caused by running out
of RAM may find that tweaking this parameter prevents those crashes, at
the cost of longer processing time.

[Noise Reduction](noise_reduction) has a baseline requirement
of 128MB of RAM for a 10 megapixel raw photo, or 512MB of RAM for a 40
megapixel one, and additionally 128MB of RAM per thread. The more
threads run in parallel, the quicker the computation, but higher the
memory requirement.

Most modern CPUs run two threads per physical core. Find out what CPU
you have and how many cores it has, multiply that by two, and you get
the maximum number of threads it would make sense to run simultaneously.
Let's call this number *T<sub>max</sub>*. You would not benefit from
running more threads than this - in fact you would likely suffer a small
speed penalty.

Setting this parameter to "0" will let your CPU figure out what
*T<sub>max</sub>* is, and use that. If you experience crashes due to
insufficient RAM, then you can calculate *T<sub>max</sub>* yourself and
use a number lower than that.

------------------------------------------------------------------------

## Registerkarte *Klänge*

Für einige öfters etwas länger andauernde Operationen lassen sich hier
Klänge einstellen, die abgespielt werden, wenn die Operation beendet
wurde. Dies wird derzeit nicht unter macOS unterstützt.

Aktivieren  
Gesetzt, werden die Klänge grundsätzlich aktiviert

Es können in den langen Eingabefeldern Wave-Files (\*.wav) inklusive
Pfad eingetragen werden.

Alternativ können folgende Kürzel für Systemklänge eingesetzt werden:

:; Windows:

:\* SystemAsterisk

:\* SystemDefault

:\* SystemExclamation

:\* SystemExit

:\* SystemHand

:\* SystemQuestion

:\* SystemStart

:\* SystemWelcome

:; Linux

:\* bell

:\* camera-shutter

:\* complete

:\* dialog-warning

:\* dialog-information

:\* message

:\* service-login

:\* service-logout

:\* suspend-error

:\* trash-empty

:\* possibly the name of any file in
`/usr/share/sounds/freedesktop/stereo/`

Der Klang im Feld *Bearbeitung abgeschlossen* wird nur abgespielt, wenn
ein Bearbeitungsvorgang länger als unter *Verzögerung in Sekunden*
vorgegeben dauerte.

### Sound-Probleme unter Linux

RawTherapee verwendet die Bibliothek libcanberra, um Klänge zu
produzieren. Falls auf deinem Rechner prinzipiell der Sound
funktioniert, nicht aber die Klänge von RawTherapee, dann kannst du die
Funktion von libcanberra mit folgendem Script testen:

  
Erstelle die Datei *hello_world.sh* mit folgendem Inhalt:

<!-- -->

     #!/bin/bash
     canberra-gtk-play -i phone-incoming-call -d "hello world"

  
und führe aus:

<!-- -->

     chmod +x hello_word.sh
     ./hello_word.sh

Wenn *hello_world.sh* Sound produziert, prüfe in RawTherapee indem du in
eins der Eingabefelder den Klang "phone-incoming-call" einträgst.

Probleme können vor allem auftreten, wenn pulseaudio installiert ist.
Prüfe auch Fehlermeldungen, die bei der Ausführung von *hello_world.sh*
auftreten. Und zur Not verzichte eher auf die RawTherapee-Klänge, wenn
dein Linux sonst optimal Musik oder ähnliches abspielt.
