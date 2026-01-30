---
title: Batch Adjustments - Sync
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

# Batch-Bearbeitung

Wenn Du bei der Bearbeitung von Fotos richtig effektiv werden möchtest,
ist der Inhalt dieses Artikels für dich besonders wichtig.

Stapelverarbeitung ist ein alternativer Begriff für Funktionen, die in
einem Zug auf gleich mehrere Objekte angewendet werden. Im Prinzip ist
auch die Abarbeitung der Warteschlange faktisch ein Batch-Prozess.
Gemeint ist hier aber die tatsächlich gemeinsame **Be**arbeitung
(editieren) mehrerer Fotos oder das Übertragen eines Bearbeitungsprofils
auf mehrere Fotos. Andere Software verwendet hier auch den Begriff
*synchronisieren*. Wohlgemerkt: Es geht um die geschickte *Verteilung*
von Werkzeugeinstellungen auf mehrere Bilder und nicht um die
*Ver*arbeitung eines Fotos. Es müsste in gutem deutsch also
*Stapel**be**arbeitung* heißen.

In RawTherapee gibt es dazu zwei Wege. Zum einen lassen sich Settings
einzelner oder aller Werkzeuge von einem Foto auf mehrere Andere
**übertragen**. Also die klassische
*[Copypaste](http://www.stupidedia.org/stupi/Copypaste)-Methode*. Zum
Anderen ist es aber auch möglich, Bilder tatsächlich **parallel zu
bearbeiten**.

**Hinweis zum Selektieren:** In diesen Verfahren arbeitest du auch in
der Dateiverwaltung und dem Filmstreifen des Editors. Um mehrere
Miniaturbilder dort zu selektieren, nutze die üblichen intuitiven
Funktionen, die auch von fast allen grafischen Betriebssystem bekannt
sind:

- Um mehrere Bilder einzeln auszuwählen, halte die Strg-Taste gedrückt
  und klicke auf die Bilder.
- Um gleich einen ganzen Bereich auszuwählen, klicke auf das erste Bild,
  halte dann die Umschalt-Taste gedrückt und klicke auf das letzte Bild
  in dieser "Liste".

### Copypaste - Kopieren von Werkzeugeinstellungen

RawTherapee besitzt eine Zwischenablage, mit der aktuelle
Werkzeugeinstellungen übertragen werden können. Die bekannten
Windows-Tastenkombinationen für
[Copypaste](http://www.stupidedia.org/stupi/Copypaste), also Strg+C und
Strg-V, werden auch hier verwendet, übertragen die Daten aber nicht über
die Betriebssystem-eigene Zwischenablage. Das funktioniert im Editor
(auch in Verbindung mit dem Filmstreifen) und in der Dateiverwaltung.
Der Editor hat hierfür sogar zwei [Buttons ziemlich oben
rechts](The_Image_Editor_Tab/de#Zwischenablage_f.C3.BCr_Bearbeitungsprofile.md).
Im Filmstreifen und der Dateiverwaltung gibt es die Funktionen im
Kontextmenü. Die genannten Tastenkombinationen funktionieren aber
überall.

Der Anwendungsfall ist typisch für Bilder aus einem Shooting: Es gibt
Bildeigenschaften, wie Weißabgleich, Belichtung, Rauschverhalten bei
konstant hohem ISO usw., die sind für alle Bilder eines Shots sehr
ähnlich. In so einem Fall bearbeite beim ersten Bild im Editor nur diese
Gemeinsamkeiten zu einem guten Zwischenresultat und *verteile* mit
dieser Methode diese Grundeinstellungen auf alle ähnlichen Bilder. Du
hast nun für die verbleibenden Bearbeitungsschritte, die durchaus sehr
bildspezifisch sein können, einen guten Startpunkt für sämtliche Bilder
des Shootings.

Wie gesagt, findest Du die Funktionen zum Kopieren und einfügen auch in
den Kontextmenüs des Filmstreifens und in denen von ausgewählten Bildern
in der Dateiverwaltung. Dort heißen die Punkte: *Profiloperationen \>
Profil kopieren* und *Profiloperationen \> Profil einfügen*.

#### *Selektiv einfügen*

[frame](image:selectprofileimportdlg_de_small.png)

Willst Du nicht alle Werkzeugeinstellungen übertragen, sonder nur von
ganz speziellen Werkzeugen, dann

- drücke statt *Strg-v* die Kombination *Strg+Umschalt+V*
- oder wähle im Kontextmenü des Miniaturbildes *Profiloperationen \>
  Profil selektiv einfügen*

In beiden Fällen öffnet sich ein Dialogfeld, in dem Du die Werkzeuge,
deren Einstellungen übertragen werden sollen, auswählen kannst.

#### *Die Hacker-Methode*

Manchmal lohnen sich in speziellen Fällen auch ein paar mehr Handgriffe:

Falls Du mit der Selektion einzelner Werkzeuge noch nicht zufrieden bist
und nur ganz spezielle Parameter kopieren willst:

- Speichere das Bearbeitungsprofil (durchaus schon *vorselektiert*)
- Öffne es in einem einfachen Editor (es muss ein Editor sein, der keine
  Steuer- oder Formatierungszeichen einfügt und die Kodierung
  beibehält).
- Lösche dort alle Parameterzeilen, die Du nicht übertragen möchtest.
  Und speichere das Profil.
- Lade ein Bild in den Editor
- Öffne das editierte Profil (*Profil aus Datei laden*) - Leider gibt es
  diese Lade-Funktion nicht im Kontextmenü von Dateimanager und
  Filmstreifen

<div style="clear: both">
</div>

### Sync - Parallel-Bearbeitung mehrerer Bilder

Und es geht noch einen Zahn fixer: Du kannst tatsächlich auch mehrere
Bilder gleichzeitig bearbeiten!

Diese Funktion gibt es **nur in der Dateiverwaltung**. Der große
Nachteil dabei ist, dass Du den Bearbeitungserfolg nur in den kleinen
Miniaturbildern sehen kannst. Derzeit zeigt in der Dateiverwaltung die
rechte Registerkarte *Prüfen* nur Informationen aus dem unbearbeiteten
Bild an (Raw: eingebettetes JPEG). *Prüfen* dient derzeit ausschließlich
der Vorselektion.

Falls du nicht nur einen großen Monitor hast, sondern auch einen
schnellen Rechner, kannst du dir die Parallelverarbeitung so richtig
versüßen: *Einstellungen \> Dateiverwaltung \> Einstellungen des
Festplatten-Cache für Miniaturbilder \> Maximale Höhe der
Miniaturbilder*. Stelle den Wert z.B. auf 600. Auf einem 4k-Monitor gern
auch höher. - Optimiere die Einstellungen an Hand der Performance des
Rechners. Der Speicherplatz (Cache), in den die Miniaturbilder
vorübergehend abgelegt werden, ist wohl eher das kleinste Problem. Wenn
du leistungsfähige Hardware hast, gibt der Monitor die Grenzen vor.
Probiere aus, was für Dich passt. Wenn Du an dieser Stelle in bessere
Hardware investierst, gehörst du zu der Gruppe der Poweruser. Als
Gelegenheitsnutzer übertreibe es nicht: das oben beschriebene
Batch-Verfahren benötigt diese Performance nicht, ist aber in vielen
Fällen ausreichend effizient. Und mit der Sync-Parallelverarbeitung
kannst du auch nicht alles machen. Sämtliche *Detail*-Funktionen
arbeiten nur mit 100% Vorschaubildern. Bei Schärfung, Rauschminderung
usw. musst du also am Einzelbild arbeiten und kannst das Ergebnis über
das selektive Bearbeitungsprofil auf alle Fotos deines Batches anwenden.

#### *Benutzung*

In der Dateiverwaltung befindet sich im rechten Bildbereich der Reiter
*Entwickeln*. Er holt die komplette Werkzeugkiste aus dem Editor in die
Dateiverwaltung. Selektiere im mittleren Bereich alle Bilder, die Du
gleichzeitig bearbeiten möchtest (s. oben) und vertraue bei sehr groß
gestellten Miniaturbildern Deiner Rechenleistung.

Beachte dabei, dass vor allen Einstellwerten eine Checkbox steht. Die
drei möglichen Optionen dabei sind:

`[ ]` abgeschaltet

`[✓]` eingeschaltet

`[-]` Werte unterscheiden sich über alle selektierten Bilder

Meist wird im dritten Fall die Checkbox gleich abgeschaltet. Willst du
den Wert aber nun für mehrere Bilder ändern, musst du ihn wieder
zuschalten. Doch was passiert nun beim Verschieben eines Reglers, wenn
die Werte bisher unterschiedlich waren? Lies weiter um zu verstehen, was
passiert und wie man es beeinflussen kann:

**Der große Unterschied**:

Im Einzelbild-Editor veränderst Du die Einstellwerte immer absolut. Das
ist kein Problem, weil der Wert beim Bildaufruf immer schon dort steht,
wie du ihn zuletzt hast stehen lassen.

Wählst du aber im Sync-Mode mehrere Fotos aus, können die Parameter der
einzelnen Bilder auf unterschiedlichen Werten stehen. Änderst Du nun
einen solchen Wert für alle ausgewählten Bilder: Was soll passiere?

- Soll der Parameter in allen Bilder auf den neuen Einstellwert
  springen? Er hat dann in all den gemeinsam editierten Bildern den
  gleichen Wert.
- Oder soll nur die *Veränderung* des Parameters auf den aktuellen Wert
  für jedes einzelne Bild addiert werden?

Im zweiten Fall werden alle Bilder bezüglich dieses Parameters, den du
gerade angefasst hast, nicht *gleichgeschaltet*. Zum Beispiel beim
Weißabgleich kann eine *Gleichschaltung* fatale Folgen haben.

Um das noch etwas anschaulicher zu erklären, ein einfaches Beispiel:

Nehmen wir an, du hast zwei Bilder. Das Zweite war völlig unterbelichtet
und du hast es einzeln schon um 3 Lichtwerte in der Belichtung
angehoben. Bearbeitest du nun beide Bilder synchron und bist der
Meinung, dass beide noch um 0,5 Lichtwerte abgedunkelt werden sollten,
passiert Folgendes:

- entweder beide Bilder werden um 0,5 Lichtwerte dunkler oder
- das erste Bild wird um 0,5 Lichtwerte dunkler, das Zweite aber um 3,5
  Lichtwerte.

Im zweiten Fall steht in *Einstellungen \> Stapelverarbeitung \>
Belichtungskorrektur* der Schalter auf *Setzen*. Im ersten Fall steht er
aber auf *Hinzu* (addieren). Vermutlich wünschst Du den ersten Fall: Das
Bild wird immer ausgehend von seinen aktuellen Einstellungen um einen
bestimmten Betrag korrigiert. Dies ist in den Standardeinstellungen auch
die Einstellung bei der Belichtung. Es gibt aber auch Anwendungsfälle,
wo eine andere Wirkung gewünscht ist. **Demzufolge:**

Wenn Du gern im Sync-Mode arbeiten möchtest, achte auf diese
unterschiedliche Reglerinterpretationen und prüfe unter *Einstellungen
\> Stapelverarbeitung* die Einstellung der einzelnen Schalter für die
vielen Werkzeuge.

Im *Hinzu*-Modus bewirkt übrigens der kleine *Reset*-Schalter "Standard
wiederherstellen", dass der bisherige Wert jedes einzelnen Bildes auf
den Anfangswert vor der Batch-Bearbeitung zurück gesetzt wird. Also nur
der *Hinzu*-Wert wird also auf 0 gesetzt. Damit wird vermieden, dass für
alle gewählten Bilder der Standardwert gleich zurück auf *Anfang*
gesetzt wird. *Anfang* ist hier statt dessen nur der Beginn der
aktuellen Batch-Verarbeitung.

Lies dazu sinnvollerweise auch noch die zugehörige [Konfiguration in den
Programmeinstellungen](Preferences/de#Registerkarte_Stapelverarbeitung.md).

### Tipp zum Thema

Wenn Du von einem Event zurück an den Rechner kommst, die Speicherkarten
deiner Kameras eingelesen hast, befinden sich viele unbearbeitete Fotos
auf deinem System. Sinnvollerweise sortierst du sicher zuerst die Bilder
aus, die aus bestimmten Gründen nicht entwickelt werden sollen. Zurück
bleiben womöglich immer noch hunderte Aufnahmen. Die hier beschriebenen
Batch-Methoden eignen sich optimal, um vielleicht 80% der Bearbeitung zu
schaffen, bevor du anfängst, die einzelnen Bilder in Details zu
finishen.

Die Frage ist, wie kommst du möglichst schnell dazu, die ersten 80% der
Bildverarbeitungsparameter abzuarbeiten? Die Batch-Methoden sind dazu
die eine Hälfte, Strukturierung in den Arbeitsablauf zu bringen.
Trotzdem müsstest Du immer noch für die Batch-Verarbeitung innerhalb
eines Ordners eine Teilmenge aus hunderten Fotos selektieren, um die
jeweiligen Batch-Einstellungen vorzunehmen. Das ergibt eine endlose
Sucherei, welches Bild für welche Korrektur mit welchem Bild
gleichzeitig bearbeitet werden kann. Gleichzeitig hat RawTherapee mit
der Darstellung hunderter Miniaturbilder in dem ausgewählten Ordner zu
kämpfen.

Löse das Problem:

1.  Schiebe nach dem Shooting alle Bilder in einen Ordner. (eventuell
    schon getrennt nach Kameras, falls du mehrere benutzt hast)
2.  Schmeiß daraus weg, was nicht zu gebrauchen ist
3.  Sortiere den Rest in Unterordner ein: Selektiere nach "Bildtyp".
    Alles, was in etwa gleich belichtet ist, etwa den gleichen
    Farbeindruck besitzt, ... in jeweils einen Unterordner.  
    Hast du nur relativ wenige unterschiedliche "Bildtypen", kannst du
    sie auch statt zu verschieben, mit den Farbmarkern versehen.
4.  Gehe jetzt mittels der Batchverfahren in die einzelnen Order. In der
    Regel kannst du nun gleich alle Bilder zur Sync-Verarbeitung oder
    zum Profilverteilen selektieren. All die Bildveränderungen der
    gleich typisierten Bilder in einem Unterordner dürften größtenteils
    identisch sein. Du erspartst dir bei der jeweiligen Selektion die
    Sucherei in hunderten Fotos.  
    Hast du dich statt dessen für die Variante mit den Farbmarkern
    entschieden, nutze hier die Filterfunktionen. Du findest sie oben in
    der [Dateiverwaltung](the_file_browser_tab/de) und auch
    im Editor in der Werkzeugleiste des
    [Filmstreifens](the_image_editor_tab/de#der_filmstreifen).
5.  Wenn es die Zielqualität der Bilder erfordert, gehe jetzt jedes
    einzelne Bild zum Finishing durch. Zumindest die Wahl des passenden
    Ausschnitts ist ein Schritt, der für jedes Bild einzeln entschieden
    werden muss.

Für die Vorauswahl und die Einsortierung kannst du RawTherapee
verwenden. Liefert dein Kamerahersteller aber einen Treiber für das
Raw-Format, so dass du es in einem beliebigen Ordner anzeigen kannst,
kannst du die Vorsortierung auch mit einem gewöhnlichen Datei-Explorer
übernehmen.
