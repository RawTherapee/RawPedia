---
title: File Paths
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

# Dateipfade

RawTherapee verwendet einen Cache-Ordner für temporäre Files, die ganz
sicher am Ende der Arbeit mit dem Programm gelöscht werden können.
Weiterhin wird ein Konfigurations-Ordner verwendet, in dem RawTherapee
Einstellungen und Nutzer-Bearbeitungsprofile ablegt. Diese Ordner werden
an bestimmten Stellen im Dateisystem platziert (s. unten) und beginnen
immer mit *RawTherapee* und (optional) gefolgt von einer Erweiterung.
Wie diese Erweiterungen heißen, hängt von dem ab, der die jeweilige
RawTherapee-Version erstelt hat, die du gerade verwendest. Beispiele
sind (waren):

- RawTherapee
- RawTherapee**4.2**
- RawTherapee**5**
- RawTherapee**5-dev**
- RawTherapee**_test**

Wobei der erste Teil *RawTherapee* fest im Programmcode hinterlegt ist.
Der zweite Teil kann durchaus länger sein (*5.0-gtk2-123-g87654321*).
Bei den stabilen Versionen sollten solche Erweiterungen, wie *dev* oder
*test* nomalerweise nicht dabei sein.

## Konfigurations-Ordner

Der *config*-Ordner enthält

- das *options*-File, welches alle Deine Programmeinstellungen aus
  [image:Gtk-preferences.png](image:gtk-preferences.png)
  Einstellungen enthält,
- den *batch*-Ordner mit allen temporär gültigen
  [Bearbeitungsprofilen](sidecar_files_-_processing_profiles/de)
  der Bilder, die du in die
  [Warteschlange](the_batch_queue/de) gelegt hast und
- den *profiles*-Ordner, in den du deine Nutzer-Bearbeitungsprofil-Files
  ablegst, die du direkt in RawTherapees Auswahlliste sehen möchtest.

Denke vielleicht daran, diese Ordner in deine Backups aufzunehmen. Und
vor allem sie auf ein neues System bzw. eine neue Installation zu
übertragen, falls du mit RawTherapee auf einen neuen Rechner umziehen
solltest oder RawTherapee neu installierst.

Hier nun die System-abhängigen Standard-Ordnerbezeichnungen. Beachte
dabei immer den Prefix *RawTherapee*, wenn du die Ordner auf deinem
System suchst:

"*Config*" in Windows XP  
`%USERPROFILE%\Local Settings\Application Data\`

"*Config*" in Windows 7, 8 and 10  
`%LOCALAPPDATA%\`

"*Config*" in Linux  
`~/.config/`

"*Config*" in OS X  
`~/.config/`

Unter dem *Finder* wähle den Menüpunkt 'Gehe zu', klicke auf 'Gehe zum
Ordner' (Kürzel Command+Umschalt+G), du kannst dort dann jeden Pfad
eintragen, zu dem du gehen möchtest, auch wenn er vom System versteckt
wird.

## Cache

Der *Cache*-Ordner enthält aus Effizienzgründen bezüglich der
Performance bei der Arbeit mit dem Programm zeitweise folgende Objekte:

- Miniaturbilder,
- Histogramme,
- Metadaten,
- Sidecar-Files, also Bearbeitungsprofile und
- optional eingebettete Profile.

Standardmäßig hält RawTherapee bis zu 20.000 zwischengespeicherte
Datenobjekte im Cache. Behalte also unter Umständen den *cache*-Ordner
im Auge, wenn es eng auf der Festplatte wird. Dieser Ordner kann
zeitweise recht groß werden. Im Wesentlichen verbrauchen die
zwischengespeicherten Miniaturbilder der aufgerufenen Raw-File-Ordner
diesen Platz. Diese liegen innerhalb des *cache*-Ordner im Verzeichnis
*images*. Du kannst diesen *images*-Ordner jeder Zeit ruhigen Gewissens
löschen, ohne irgendwas zu verlieren. RawTherapee erstellt danach alle
die Miniaturbilder darin neu, die benötigt werden. Der Cache-Ordner ist
sozusagen nur ein Mittel, um in der Arbeit mit dem Programm "billigen"
Speicherplatz gegen deine teure "Zeit", also kurze Reaktionszeiten des
Programs, einzutauschen.

Standardwerte für diese Ordner (suche dort die Einträge, die mit
"RawTherapee\*" beginnen):

"*Cache*" in Windows XP  
`%USERPROFILE%\Local Settings\Application Data\`

"*Cache*" in Windows 7, 8 and 10  
`%LOCALAPPDATA%\`

"*Cache*" in Linux  
`~/.cache/`

"*Cache*" in OS X  
`~/.cache/`

Unter dem *Finder* wähle den Menüpunkt 'Gehe zu', klicke auf 'Gehe zum
Ordner' (Kürzel Command+Umschalt+G), du kannst dort dann jeden Pfad
eintragen, zu dem du gehen möchtest, auch wenn er vom System versteckt
wird.

## Benutzerkonfiguration und Cach-Ordner

Obwohl der Pfad und der Name der Cache- und Konfigurationsordner hart
kodiert sind, kannst du beide durch einen anderen **absoluten** Pfad
ersetzen, indem du die Umgebungsvariablen `RT_SETTINGS` und `RT_CACHE`
anpasst. Wie, ist abhängig vom Betriebssystem und dessen Version. Um das
für dein System heraus zu bekommen, nutze die Internet-Suche am besten
mit der Suche nach "Umgebungsvariable setzen in
*<dein Betriebssystemname>*".

Unabhängig davon *wie* sie in deinem Betriebssystem gesetzt werden, hier
einige Beispiele, auf *was* sie gesetzt werden könn(t)en:

Windows  
`RT_SETTINGS=%LOCALAPPDATA%\rawtherapee\5.0`

`RT_CACHE=C:\Users\Mirabella\AppData\Local\rtcache`

Linux and OS X  
`RT_SETTINGS=/home/jacqueline/.config/rawtherapee/5.0`

`RT_CACHE=/home/jacqueline/junk/rtcache`

## Bearbeitungsprofil-Files (Sidecar-Files)

Wenn du deine eigenen
[Bearbeitungsprofile](sidecar_files_-_processing_profiles/de)
zentral ablegen möchtest, damit du sie jederzeit in RawTherapees Menü
der Bearbeitungsprofile abrufbereit hast (z.B. Kontextmenü
*Profiloperationen \> Einfügen*), dann speichere sie im Ordner
*profiles*, der sich innerhalb des Konfigurationsordners befindet (s.
oben).

## Temporärer Ordner

Falls Du in RawTherapee ein externes Programm zur Bearbeitung
konfiguriert hast, dass du direkt zur Weiterverarbeitung verwendest
([Externer
Editor](Edit_Current_Image_in_External_Editor/de.md)), legt
RawTherapee ein *Übergabefile* im Format TIFF an, das von diesem
Programm automatisch geladen wird (, wenn es richtig konfiguriert ist).
Beachte, das bei heute üblichen Bildgrößen in 3 Farben und 16 Bit
Farbtiefe so ein File eine Größenordnung von 100MByte einnehmen kann, da
es nicht komprimiert ist. Die Files werden bei der Übergabe auch nicht
überschrieben sondern es werden immer wieder neue Files angelegt. Nutzt
du diese Funktion, ist nicht nur entscheidend, dass der Pfad auf ein
Medium zeigt, dass besonders schnell ist, sondern dass du auch
regelmäßig (automatisch oder mit der Hand) auf Bildleichen untersuchen
solltest. Idealer Weise liegt das Verzeichnis in einem Ordner, dass von
Betriebssystem regelmäßig geleert wird. Um hier Einfluss zu nehmen,
benötigst du die Information, wo RawTherapee dieses Verzeichnis
verortet:

Windows  
Default ist, was in der `$TEMP`-Umgebungsvariablen steht. Für gewöhnlich
also `%LOCALAPPDATA%/Temp`

Wenn die `$TEMP`-Umgebungsvariable nicht gesetzt ist, wird `C:\`
verwendet.

Linux and OS X  
Default ist, was in der `$TMPDIR`-Umgebungsvariablen steht. Gewöhnlich
ist das `/tmp` .

Falls die `$TMPDIR`-Umgebungsvariablen nicht gesetzt ist, wird `/tmp`
verwendet.

<!-- -->

Linux, mit RawTherapee als Windowsprogramm unter Wine  
Willst du den temporären Ordner von Linux verwenden, gehe bitte so vor,
wie unter [Mit Linux unter
Wine](Edit_Current_Image_in_External_Editor/de#Mit_Linux_unter_Wine.md)
beschrieben.
