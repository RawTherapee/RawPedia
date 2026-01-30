---
title: RTProfileSelector
contributors:
  - Fherb
tags:
  - 'Processing Profile Scripts'
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: completed
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

Der **RTProfileSelector** ist ein RawTherapee-plugin, dass basierend auf
Nutzer-definierten Regeln automatisch vom Nutzer erstellte Prozessfiles
(.pp3-Files) auswählt. Diese Regeln sind Sets von Exif-Feldern und
-Werten die mit den aktuellen Werten abgeglichen werden, die aus den
Raw-Files beim erstmaligen Öffnen gewonnen werden.

Hier ein paar Dinge, die mit dem RTProfileSelector automatisiert werden
können:

- eigene Prozessfiles an ungefähre Kameraeinstellungen binden
- Rauschminderungsparameter entsprechend des Kamera-Models und des
  ISO-Wertes setzen
- Linsenkorrekturprofile (LCP) basierend auf Linsen- und Kameramodell
  auswählen

RTProfileSelector ist in C++11 geschrieben und unter Windows und Linux
compiliert. Quellcode und Windows-Exe können vom
[Git-Repository](https://github.com/marcapelini/RTProfileSelector)
herunter geladen werden. RTProfileSelector verwendet
[ExifTool](http://www.sno.phy.queensu.ca/~phil/exiftool/) um die
Metadaten aus Bildern zu extrahieren.

Zur Installation und für die Dokumentation siehe das [Wiki des
Projekts](https://github.com/marcapelini/RTProfileSelector/wiki).

Möglicherweise werden die [Dynamischen
Bearbeitungsprofile](Dynamic_processing_profiles/de.md) die
Funktionalität des *RTProfileSelector* ersetzen.
