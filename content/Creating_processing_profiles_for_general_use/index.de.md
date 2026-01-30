---
title: Creating processing profiles for general use
contributors:
  - Fherb
tags:
  - 'Processing Profiles'
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: completed
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Erstellung von Bearbeitungsprofilen für die allgemeine Verwendung

In RawTherapee werden die Sidecar-Files *Bearbeitungsprofile* bzw. auch
*Prozessprofile* genannt. Ein ganzes Bündel an solchen
Bearbeitungsprofilen wird mir RawTherapee mitgeliefert. So kannst du mit
einem bereits existierendem Look starten und dies nach eigenem Geschmack
modifizieren und somit etwas Zeit sparen. Ein Beispiel ist *Pop 1*. Es
wird dein Bild lebendiger machen, Schatten etwas anheben und Details
hervortreten lassen.

Du findest alle diese Standardprofile im Editor oben rechts über den
Bearbeitungswerkzeugen, wenn du das Aufklappmenü unter
*Bearbeitungsprofile* öffnest. Ebenso finden sich diese Profile in der
Dateiverwaltung im Kontextmenü der Miniaturbilder unter
*Profiloperationen \> Profil (selektiv) anwenden*.

Lies auch die Anleitung unter
[Bearbeitungsprofile](the_image_editor_tab/de#bearbeitungsprofile)
des Editors. Insbesondere auch bezüglich Teilprofilen und dem
Umschaltbutton
![<File:Profile-partial.png>](Profile-partial.png "File:Profile-partial.png")
/
![<File:Profile-filled.png>](Profile-filled.png "File:Profile-filled.png").

## Bearbeitungsprofile erstellen

![](Rt_filebrowser_customprofile_small.jpg "Rt_filebrowser_customprofile_small.jpg"))
an.\]\]
![](Rt_imageeditor_customprofile_cropped.jpg "Rt_imageeditor_customprofile_cropped.jpg")
Du kannst deine eigenen Bearbeitungsprofile erstellen und sie im
Aufklappmenü des Editors (unter *Bearbeitungsprofile* rechts oben)
einfügen lassen.

- Öffne ein geeignetes Foto von dem ausgehend du so ein Start-Profil
  anlegen möchtest.
- Du kannst mit der *Neutral*-Einstellung beginnen oder eines der
  mitgelieferten Standardprofile laden.
- Führe nun die gewünschten Einstellungen zur Bildentwicklung aus.
    
  Beachte hierbei: Je spezifischer die Einstellungen für dieses Foto
  ausfallen, desto weniger werden sie in der Anwendung auf andere Fotos
  funktionieren. Orientiere also auf bestimmte Einstellungen, die für
  eine größere Zahl ähnlicher Fotos geeignet erscheinen bzw. nur eine
  Ausgangsbasis darstellen, von der ausgehend diese Bilder fertig
  entwickelt werden.

  Hier einige Anwendungsfälle:

  Hat deine Kamera einen sehr rauscharmen Sensor, das Objektiv aber eine
  nicht so hohe Schärfe, könntest du die Einstellungen zum Schärfen des
  Bildes dafür passend einstellen und das Profil nun zukünftig auf alle
  Bilder anwende, die in dieser Kamera-Objektiv-Kombination aufgenommen
  wurden.

  Wenn anders herum deine Kamera ein relativ großes Rauschen bei z.B.
  ISO3200 besitzt, kannst du (nur) die Rauschunterdrückung entsprechend
  passend einstellen und das Profil dann auf alle Bilder anwenden, die
  mit genau diesem ISO-Wert aufgenommen wurden.
- Wenn du mit den Einstellungen der Werkzeugparameter fertig bis, klicke
  im Editor auf
  ![<File:Gtk-save-large.png>](Gtk-save-large.png "File:Gtk-save-large.png")
  *Profil speichern* (oben rechts unter *Bearbeitungsprofile*). Gib
  einen Namen ein, die Endung hängt RawTherapee automatisch an. Wenn du
  dieses Profil im Aufklappmenü erreichen möchtest, wähle zum Speichern
  den Pfad des *profile*-Ordners innerhalb des *config*-Pfades (s.
  [Konfigurations-Ordner](file_paths/de#konfigurations-ordner))
- Starte RawTherapee neu und dein neues Prozessfile erscheint im
  Aufklappmenü unter *Meine Profile*.

  

## Teil-Bearbeitungsprofile

[frame](image:selectprofileimportdlg_de_small.png)

Manchmal möchtest du vielleicht nur einen Teil der Einstellwerte
speichern. Zum Beispiel um zu vermeiden, dass geometrische Parameter,
wie Drehwinkel, Perspektive oder auch Beschnitt überschrieben werden,
wenn das Profil geladen wird.

Halte dafür während des Klicks auf
![<File:Gtk-save-large-dark.png>](Gtk-save-large-dark.png "File:Gtk-save-large-dark.png")
die Taste gedrückt. Nachdem du den Pfad und den Dateinamen vorgegeben
hast und auf *Speichern* gedrückt hast, öffnet sich eine Dialogbox, in
der du angeben kannst, welche Parameter gespeichert werden sollen.
(Genau so funktioniert es auch, wenn Du ein Profil laden willst, um nur
einzelne Werkzeugparameter daraus zu übernehmen.)

Reicht dir diese Selektion noch nicht aus und du möchtest vielleicht nur
einzelne Parameter und nicht gleich ganze Werkzeugsettings übernehmen
oder auch nur einen Wert in den IPTC-.Daten ändern, kannst du das File
nach dem Speichern in einem Texteditor öffnen und dort Parameter
entfernen. Siehe dazu auch [Teilprofile über die
Strg-Taste](The_Image_Editor_Tab/de#Teilprofile_.C3.BCber_die_Strg-Taste.md),
insbesondere die kleine Testaufgabe am Ende dieses Abschnitts und die
"Lösung" am Seitenende dort.

Denke beim Erstellen der Profile immer an das Ziel, damit universell
unterschiedliche Fotos bearbeiten zu können, die über bestimmte
Gemeinsamkeiten verfügen, jedoch nicht identisch sind. Setze also
möglichst ein Minimum an Einstellungen, um einen bestimmten Effekt zu
bekommen und belasse die anderen Parametern in den Grundeinstellungen
bzw. speichere sie nicht mit ab. Nutze also intensiv das Anlegen von
Teilprofilen, die ganz auf eine bestimmte Aufgabe zugeschnitten sind und
alle nicht unbedingt dafür notwendige Parameter weg lassen.

## "Default"-Bearbeitungsprofile für Raw und Nicht-Raw-Bilder

Beim Laden von bisher nicht bearbeiteten Fotos lädt RawTherapee ein
Standardprofil. Im frisch installierten RawTherapee ist das

- *Neutral* für Nicht-Raw-Fotos und
- *Default* für Raw-Fotos

Hier bedeutet *Neutral*, dass (fast) sämtliche Parameter so eingestellt
sind, dass das Bild beim Abspeichern dem Original entspricht. Bei
Nicht-Raw-Fotos ist das zu 100% so. Bei Raw-Fotos allerdings müssen auch
bei *Neutral* ein paar wenige Standardparameter angewendet werden, um
das rohe Pixelbild über das Demosaicing zu einem Drei-Kanal-Farbbild
umzuwandeln. Dazu gehört auch die Anwendung des Weißabgleichs. *Neutral*
verwendet dabei die von der Kamera abgespeicherten Werte. Mit *Default*
werden allerdings weitere Einstellungen auf das Raw-Foto angewendet.
Falls du bei Raw-Fotos auch mit *Neutral* beginnend deine
Bildentwicklung durchführen willst, stelle das in
![<File:Gtk-preferences.png>](Gtk-preferences.png "File:Gtk-preferences.png")
*Einstellungen \> Bildbearbeitung \>
Standard-Bildverarbeitungsparameter* um. Wenn du ein eigenes Profil für
alle Bilder als Startwert verwenden willst, vielleicht nur mit Autor-
und Copyrightinformationen, dann kannst du dein selbst erstelltes Profil
ebenfalls dort als Standard einstellen.
