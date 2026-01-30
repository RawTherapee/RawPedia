---
title: Sidecar Files - Processing Profiles
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

# Sidecar-Files - Bearbeitungsprofile

  
An vielen Stellen auch als *Prozessprofile* bezeichnet.

Diese Bearbeitungsprofile werden auch als
[Sidecar-Files](https://en.wikipedia.org/wiki/Sidecar_file) bzw. im
Deutschen auch als sogenannte
[Filialdateien](https://de.wikipedia.org/wiki/Filialdatei) bezeichnet,
die neben dem "bearbeiteten", aber trotzdem weiterhin völlig
unverändertem Originalfile abgelegt werden und die "Prozesswerte" für
die Bildverarbeitung enthalten. Unter Prozesswerten sind sämtliche
Einstellwerte der Bearbeitungswerkzeuge zu verstehen. RawTherapee
verändert also weder das Originalbild, noch schreibt es irgendwelche
Bearbeitungseinstellungen als Zusatzdaten in die Originalbild-Datei.
Erst durch die Bündelung aus originalem Bildfile (z.B. das Raw) und
diesem Sidecar- (Beiwagen-) File ergibt sich das Ausgangs"material" aus
dem RawTherapee dann das abzuspeichernde Bild berechnet. In anderen
Raw-Bearbeitungsprogrammen wird dieser Prozessdatensatz auch "Preset"
genannt. Aktuell bekommt das Sidecar-File die Dateiendung *.pp3*. In der
älteren Version 2 war dies noch die Endung *.pp2*.

Nicht immer steht so ein Prozessfile nur "neben" einem bestimmten Bild.
Sie können sich auch als Startwerte für noch unbearbeitete Bilder
eignen. Deshalb finden sich diese Prozessprofile an drei völlig
unterschiedlichen Stellen, obwohl sie immer gleich funktionieren:

- "Standardprofile"
    
  RawTherapee bringt bereits einen Satz von Profilen mit. Ihr Zweck
  besteht darin, einen guten Startpunkt zur Verarbeitung von Bildern zu
  liefern. Auch, um das Zusammenspiel der unterschiedlichen
  Werkzeugeinstellungen zu demonstrieren. Man findet diese
  Prozessprofile im Editor über den Werkzeugen unter
  *Bearbeitungsprofile \> Standardprofile*
- "Meine Profile"
    
  Wenn du bestimmte Profile öfters wiederverwenden willst, speichere sie
  im *config*-Ordner unter *profiles* (s. Seite
  [Dateipfade](file_paths/de#konfigurations-ordner)). Sobald
  dort Profile abgelegt sind, wird neben *Bearbeitungsprofile \>
  Standardprofile* auch der Eintrag *Meine Profile* angezeigt und man
  kann sie auf die gleiche bequeme Art laden, wie die mitgelieferten
  Standardprofile. In der Regel eignen sich selektive Profile (beim
  Speichern die Strg-Taste gedrückt halten) besonders gut, um nur ganz
  bestimmte Einstellungen eines oder weniger Werkzeuge in einem Profil
  für einen bestimmten Zweck vorzuhalten.
- Automatisch erstellte Profile
    
  Dies sind die eigentlichen, schon oben beschriebenen Sidecar-Files.
  Also jeweils der Satz an Werkzeugeinstellungen, der bei der
  Bearbeitung automatisch zu jedem Bild abgelegt wird. Zusätzlich zu den
  Werkzeugeinstellungen wird auch das Ranking (Sternchen), die
  Farbmarkierung und die "Im Papierkorb"-Information in diesem File mit
  abgelegt. Hingegen wird weder die Historie noch werden die
  Schnappschüsse der Werkzeugeinstellungen derzeit gespeichert.

\*: Der Rest dieser Seite befasst sich mit diesen automatisch erstellten
Profilen, wobei viele Details auch auf die beiden anderen Profilarten
(*Standardprofile* und *Meine Profile*) zutreffen.

Standardmäßig werden die Prozessfiles "neben" das Original abgelegt,
also in den gleichen Ordner. Dabei wird der Dateiname des Originals
wiederverwendet. Zum Beispiel wird zu "*katze.raw*" ein Prozessfile
"*katze.raw.pp3*" angelegt. Prozessfiles können aber auch in den
[zentralen Cache](file_paths/de#cache) abgelegt werden. Die
Umschaltung zwischen beiden Varianten erfolgt unter
![<File:Gtk-preferences.png>](Gtk-preferences.png "File:Gtk-preferences.png")
*Einstellungen \> Bildbearbeitung \> Behandlung der
Bearbeitungsprofile*. Es wird empfohlen, die Bearbeitungsprofile
zusammen mit den Bildern zu speichern. Beim Verschieben der Bilder
bleiben sie ihnen somit problemlos zugeordnet.

Beachte:  
Bei der Verwendung des Cache als Ablageort der Bearbeitungsprofile kann
RawTherapee dort gespeicherte Profile nur so lange den Bildern richtig
zuordnen, wie diese sich im Verzeichnispfad an exakt der gleichen
Position befinden. Werden die Bilder verschoben oder auch nur ein Ordner
im Pfad umbenannt, erscheinen die Bilder wieder als unbearbeitet und man
muss sich mit der Hand das richtige Bearbeitungsprofile direkt im
Cache-Ordner herausangeln.

## Auf- und Abwärtskompatibilität

Bearbeitungsprofile verändern sich von einer zur nächsten
RawTherapee-Version. Die Entwickler sind bestrebt, Abwärtskompatibilität
zu gewährleisten, was aber nicht immer vollständig möglich ist. So
können nicht nur neue Parameter hinzukommen, sondern auch Alte
überflüssig werden, wenn die Bildbearbeitungswerkzeuge weiterentwickelt
werden. Mit dieser Weiterentwicklung können sich die Default-Werte, im
Extremfall sogar die Bedeutung eines Wertes ändern. Ein Beispiel dafür
ist die deutliche Verbesserung des Rauschreduktionswerkzeugs von Version
3.0 zu 4.0.10, sodass ein bestimmter Einstellwert des
Luminanz(rauschunterdrückungs)parameters in beiden Versionen
unterschiedlich stark wirkt.

Wenn die Bearbeitungsprofile im Cache der jeweiligen Version gespeichert
werden (den Ort unter *Einstellungen* unterschiedlich konfiguriern),
können bei der Parallelinstallation unterschiedlicher
RawTherapee-Versionen auch unterschiedliche Bearbeitungsprofile für die
Bilder abgelegt werden, die sich dabei nicht gegenseitig stören. In so
einem Fall kann ein Bild auch später noch einmal bearbeitet und
gespeichert werden, indem man auf die damals verwendete
RawTherapee-Version zurück greift. Vorausgesetzt, der Cache wurde nicht
gelöscht. (Bei der Deinstallation also den Cache sichern, um ihn bei
einer erneuten Installation einer älteren Version dort wieder einfügen
zu können.) Ob das allerdings tatsächlich wünschenswert ist, sei
dahingestellt. Mit neueren Versionen, dem eigenen
Entwicklungsfortschritt und der Entwicklung des eigenen Geschmacks ist
zu erwarten, dass man das gleiche Bild inzwischen etwas anders
entwickeln würde, als einige Jahre zuvor. Beachte auch das Problem, dass
RawTherapee die Profile im Cache nicht mehr zuordnen kann, wenn sich der
Verzeichnispfad, in dem die Bilder liegen, auch nur geringfügig geändert
hat. Auf der Seite zu den [Dateipfaden](file_paths/de#cache)
findest du den Ort, wo sich der Cache befindet.

Wenn eine neue Haupt-Version von RawTherapee veröffentlicht wird kann es
sein, dass die Suffixe für den Konfigurations- und den Cache-Ordner
geändert werden. Das bedeutet, dass eine neue Version unter Umständen
die bisherigen Konfigurationen und aber auch die bisher angelegten
Prozessfiles nicht mehr sieht. Das klingt erst mal unerwünscht, hat aber
in so einem (eher seltenen) Fall gute Gründe:

- Abwärtskompatibilität. Es kann Änderungen im Verhalten eines Werkzeugs
  zwischen aktueller und vorhergehender Programmversion geben. Die
  Entwickler versuchen Abwärtskompatibilität dort zu gewährleisten, wo
  es möglich ist. Wenn das wirklich einmal ein Problem an einem Bild
  ist, verwende noch einmal die frühere Version für damit entwickelte
  Bilder und wechsle für alle neuen Bilder zur neusten Version. Durch
  die Umbenennung des Cache- und Konfigurationsordner kann es nicht
  passieren, dass du dort abgelegte Bearbeitungsprofile lädst, die mit
  der neuen Version falsch interpretiert werden.
- Einige Nutzer haben ihre Programmeinstellungen schon sehr lange nicht
  mehr überprüft. Bei neuen Versionen kann es besser gewählte
  Voreinstellungen geben, von der der Nutzer nichts mitbekommt, wenn er
  alte Einstellungen beibehält. Mit dieser Maßnahme, den
  Konfigurationsordner neu zu benennen, wird der Nutzer motiviert, die
  Programmeinstellungen wieder einmal komplett durchzusehen.
- Einige Nutzer haben auch noch nie in die Programmeinstellungen
  gesehen.
- Ältere Prozess- und Konfigurationsfiles könnten unter Umständen auch
  dazu führen, dass RawTherapee abstürzt. Wenn so ein Verhalten bekannt
  wird, wird es eigentlich auch gepatcht. Andernfalls führt diese
  Vorgehensweise mit frischem Cache- und Konfigurationsordner dazu,
  solche Probleme zu vermeiden.

Im Allgemeinen ist es zu empfehlen, eine bisherige Version nicht zu
updaten, sondern die neue Version an anderer Stelle im Programmordner
parallel zu installieren und auch den Cache- und den Konfigurationsorder
für diese Versionen getrennt zu halten. Das erleichtert vor allem in der
Umstellungsphase die Nutzung bzw. verringert das Risiko von Problemen,
wo vielleicht doch noch mal einige Bilder mit der älteren Version
überarbeitet werden sollen.
