---
title: Command-Line Options
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

# Aufruf über die Kommandozeile

Du kannst RawTherapee von der Kommandozeile aus mit einigen Optionen
starten. Damit sind zum Beispiel Script-gesteuerte Batch-Verarbeitungen
möglich.

## Symbolik

  
`<`Spitze Klammern`>` enthalten Parameter, die du ändern kannst.

`[`Eckige Klammern`]` bezeichnen einen Parameter der optional ist.

`|` steht als Trennzeichen für verschiedene Varianten.

`-` kennzeichnet einen Wertebereich ("von"`-`"bis").

# Verwendung

  
`rawtherapee `<Verzeichnis>

  
Startet auf der Registerkarte
[Dateiverwaltung](the_file_browser_tab/de) im angegebenen
Verzeichnis.

`rawtherapee `<File>

  
Startet direkt die
[Editor](the_image_editor_tab/de)-Registerkarte mit dem
angegebenen File.

## Option `-w` "keine Konsole öffnen"

(nur Windows-Betriebssystem)

  
  
**Verhindert das Öffnen der Konsole**

<!-- -->

  
  
Hintergrund: Normalerweise ist RawTherapee bei der Ausführung auf der
Kommandozeile recht "gesprächig". Ruft man RawTherapee als
Kommandozeilenbefehl mit Optionen auf, öffnet Windows eine Konsole und
führt RawTherapee darin aus. Dadurch kannst du sehen, was RawTherapee an
Informationen zurück gibt. Da am Ende aber Windows die Konsole sofort
schließt, hättest du keine Zeit mehr, um die Ausgaben des Programms zu
lesen. Aus dem Grund haben die Entwickler RawTherapee für Windows so
modifiziert, dass es am Ende der Bearbeitung in der Konsole auf einen
Tastendruck wartet. Drückst du dann eine Taste, beendet sich RawTherapee
und Windows schließt die Konsole.

Dieses Verhalten stört wiederum beim Aufruf aus einem Batchfile (z.B.
ein PowerShell Script) heraus. Hier soll der Nutzer ja gerade nicht
eingreifen. Mit der Option `-w` wird unter Windows verhindert, dass
RawTherapee in einer Konsole ausgeführt wird. Damit laufen Aufrufe von
RawTherapee auch unter Windows wieder ohne Eingriff des Nutzers durch.

## Option `-c` "Konvertiere"

Allgemeine Verwendung:

  
`rawtherapee `<Optionen>` -c `<Verzeichnis>`|`<Files>

  
Konvertiert mehrere Files oder einen ganzen Ordnerinhalt. Bei Aufruf
ohne Optionen werden Standardwerte verwendet.

**Beachte:** `-c` muss dabei **immer als letztes** hinter den
folgenenden möglichen Optionen stehen:

### Mögliche Optionen für die Konvertierung mit `-c`

**Verwendung:**

  
<code>rawtherapee \[-o

<output>

\|-O

<output>

\] \[-s\|-S\] \[-p \<File.pp3\>\] \[-d\] \[-j\[1-100\]
\[-js\<1-3\>\]\|\[-b\<8\|16\>\] \<\[-t\[z\] \| \[-n\]\]\] \[-Y\] -c
\<Quell-Verzeichnis\|Quell-Files\></code>

**Optionen:**

  
`-o `<Ziel-Ordner>`|`<Ziel-Filename>

  
Legt das Ausgabe-File bzw. den Ausgabe-Ordner fest.

`-O `<Ziel-Ordner>`|`<Ziel-Filename>

  
Legt das Ausgabe-File bzw. den Ausgabe-Ordner fest und kopiert das
verwendete pp3-File mit dort hin.

`-s`

  
Verwendet das PP3-Sidecar-File (Bearbeitungsprofil), dass zusammen mit
dem Ausgangsbild im gleichen Ordner liegt. Dazu muss das PP3-File den
Namen des Ausgangsbildes abbilden. Zu Foto.raw muss das PP3-File also
lauten: Foto.raw.pp3.

Fehlt das Sidecar-File, wird die Standardeinstellung für *Neutral*
verwendet.

`-S`

  
Wie `-s`, überspringt das Quellfile aber, anstatt *Neutral* zu
verwenden, falls das Sidecar-File fehlt.

`-d`

  
Statt des Profils *Neutral* wird für Raw- und Nicht-Raw-Fotos das
Standardprofil verwendet, dass unter *Einstellungen \> Bildbearbeitung
\> Standardbildverarbeitungsparameter* zuletzt eingestellt wurde.

`-j[1-100]`

  
*Standardwert*: 92, Gibt den Komprimierungswert für die Ausgabe in JPEG
vor. (JPEG ist der Standardwert für das Zielformat, wenn nichts anderes
vorgegeben wird.)

`-js<1|2|3>`

  
Gibt bei JPEG die Variante für die
[Farbunterabtastung](https://de.wikipedia.org/wiki/Farbunterabtastung)
vor:

  
1 = Beste Kompression: 2x2, 1x1, 1x1
[(4:2:0)](https://de.wikipedia.org/wiki/Farbunterabtastung#4:2:0_.282x2.2C1x1.2C1x1.29)

  
Farbe vertikal und horizontal halbiert.

2 = Ausbalanciert: 2x1, 1x1, 1x1
[(4:2:2)](https://de.wikipedia.org/wiki/Farbunterabtastung#4:2:2_.282x1.2C1x1.2C1x1.29)

  
Farbe nur horizontal halbiert.

3 = Beste Qualität: 1x1, 1x1, 1x1
[(4:4:4)](https://de.wikipedia.org/wiki/Farbunterabtastung#4:4:4_.281x1.2C1x1.2C1x1.29)

  
Keine Farbunterabtastung.

`-b<8|16>`

  
*Standardwert*: 16, Gibt die Farbkanaltiefe in Bit für die Formate TIFF
und PNG vor.

`-t[z]`

  
Gibt TIFF als Ausgabeformat vor. (Standard ist JPEG)

In der Form `-tz` wird das Bild in TIFF (verlustfrei) komprimiert
abgelegt. In der Form `-t` bleibt das Bild in TIFF unkomprimiert.

`-n`

  
Gibt PNG (verlustlos komprimiert) als Ausgabeformat vor. (Standard ist
JPEG)

`-Y`

  
Überschreibt das Ziel, falls schon vorhanden.

`-p <File.pp3>`

  
Legt ein Bearbeitungsprofil (PP3) fest, dass für alle Konvertierungen
verwendet wird. Die Option `-p <File.pp3>` kann mehrfach angegeben
werden.

Das angegebene Bearbeitungsprofil (PP3) oder unter besonderen Umständen
(ältere Version) auch das Sidecar-File können unvollständig sein. Das
tatsächlich verwendete Bearbeitungsprofil wird deshalb auf folgendem Weg
bestimmt:

1.  Das Ausgangs-Bearbeitungsprofil ist das, was den fest in RawTherapee
    kodierten Startwerten entspricht. Dies ist identisch mit dem Profil
    *Neutral*
2.  Falls Option `-d` gesetzt: Das in den Programmeinstellungen
    vorgegebene *Default*-Profil (getrennt für Raw-Files und
    Nicht-Raw-Bilder) überschreibt das Profil *Neutral* in den im
    *Default*-Profil vorhandenen Einstellungen.
3.  Die Bearbeitungsprofile, die mit der/den Option(nen) `-p` vorgegeben
    wurden bzw. das eventuell vorhandene Sidecar-File, falls es mit `-s`
    aktiviert wird, werden nacheinander in der Reihenfolge, wie sie in
    der Kommandozeile stehen, eingelesen. Die Parameter, die in den mit
    -p/-s übergebenen Profilen stehenden, ersetzen die bisher
    vorhandenen Parameterwerte.

Zum letzten Punkt: Wenn beispielsweise in der Kommandozeile angegeben
wird:

  
`-p first.pp3 -p second.pp3 -s -p fourth.pp3`

dann werden die Profilfiles in folgender Reihenfolge angewendet (das
Nachfolgende überschreibt also Werte aller Vorangegangenen):

1.  first.pp3
2.  second.pp3
3.  aktuellesFoto.raw.pp3
4.  fourth.pp3

## Standard-Ausgabe umleiten

Um zur Kontrolle die Ausgaben, die RawTherapee auf der Kommandozeile
während der Laufzeit erzeugt, in einem File abzuspeichern, können die
Umleitungen entsprechend der eingesetzten Betriebssysteme auf folgende
Art gesetzt werden:

Windows (cmd.exe)  
`rawtherapee.exe > rawthlog.txt 2>&1`

Linux  
`rawtherapee &> rawth.log`

## Beispiele

### Beispiel 1

Aufgabe: Konvertiere das File *Foto.raw* unter folgenden Bedingungen:

  
Betriebssystem: *Linux*

Ausgangsbild: */tmp/Foto.raw*

Sidecar-Bearbeitungsprofil (im gleichen Verzeichnis, wie das
Ausgangsbild): *Foto.raw.pp3*

Zielfile: */tmp/foo.tif*

Ersetze das Zielfile, falls vorhanden.

`rawtherapee -o /tmp/foo.tif -s -t -Y -c /tmp/Foto.raw`

### Beispiel 2

Aufgabe: Konvertiere sämtliche Bilder aus /tmp/jane01 für eine
Verwendung im Web und ändere Metainformationen:

  
Betriebssystem: *Linux*

Quellordner: */tmp/jane01*

Zielordner: */tmp/jane01/web*

Bearbeitungsprofil: Gehe von *Default* aus und wende ein Sidecar-File
an, wenn es existiert.

Entferne alle EXIF-Tags unter Verwendung von *~/profiles/exif.pp3*

Füge einige IPTC-Tags hinzu, wie z.B. Copyright-Informationen. Verwende
dazu *~/profiles/iptc.pp3*

Ändere die Bildgröße und schärfe danach entsprechend
*~/profiles/web.pp3*

`rawtherapee -o /tmp/Jane01/web -p ~/profiles/iptc.pp3 -s -p ~/profiles/exif.pp3 -p ~/profiles/web.pp3 -t -Y -d -c /tmp/Jane01/`

Das letztlich verwendete Bearbeitungsprofil wird folgendermaßen
gebildet:

1.  Fest kodierte Startwerte (Profil *Neutral*) geben den Ausgangspunkt
    vor.
2.  Wegen `-d` wird das in den Programmeinstellungen spezifierte
    Standardprofil darüber gebügelt.
3.  Wegen `-p ~/profiles/iptc.pp3` werden die dort enthaltenen Parameter
    zum Copyright übernommen.
4.  Wegen `-s` werden jetzt alle Einstellungen des Sidecar-Files
    übernommen.
5.  Wegen `-p ~/profiles/exif.pp3` werden die darin enthaltenen (leeren)
    Exif-Parameter übernommen.
6.  Wegen `-p ~/profiles/web.pp3` werden die darin enthaltenen Werte zur
    Änderung der Bildgröße und des nachfolgenden Schärfens übernommen.
7.  Wegen `-Y` wird ein möglicherweise vorhandenes Zielfile
    überschrieben

Während es völlig egal ist, wo die Option `-d` steht (hier ziemlich am
Ende), ist die Anordnung aller Optionen `-p` und `-s` entscheidend für
deren Anwendung bzw. Priorität: Nachfolgende Bearbeitungsprofile
überschreiben die Parameter vorangegangener. Aber *Neutral* ist in
dieser Reihenfolge immer der Startpunkt und *Default*, also `-d`, wird
immer unmittelbar danach an zweiter Stelle angewendet.

### Beispiel 3

Ebenfalls unter Linux nun ein Script, dass uns zeigt, wie lange die
Bearbeitung aller Raw-Files in einem Ordner dauert. Angenommen wird
hier, dass zu jedem Raw auch ein Sidecar-Bearbeitungsprofil vorhanden
ist. Da es nur um die Zeitdauer geht, wird das Ergebnis der
Bildbearbeitungen nirgendwohin geschrieben, sondern sogleich im
Linux-Nirwana /dev/null versenkt:

`time { for f in /home/user/photos/2011-11-11/*.raw; do rawtherapee -o /dev/null -S -t -Y -c "$f"; done }`
