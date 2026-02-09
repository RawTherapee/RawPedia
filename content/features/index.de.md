---
title: Features
contributors:
  - Fherb
tags:
  - 'General Information'
weight: 2
---

Todo-List / State:

- Translation: completed
- Content completely cleared: open, see discussion
- Expression and didactics checked: completed; but uncleared content yet
  open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Eigenschaften und Funktionen

RawTherapee besitzt nicht nur eine sehr große Funktionsvielfalt,
ausgereifte Algorithmen auf Basis klassischen Wissens über Farbtheorien
und modernster Wissenschaft und immer mit hohe Bearbeitungsqualität,
sondern ist im Design der Oberfläche ganz speziell für eine effiziente
Nutzung ausgelegt. Dass die Oberfläche für den Nutzer aus der
klassischen Windows- und Mac-Welt auf den ersten Eindruck sehr
ungewöhnlich wirkt, hat darin seinen Grund. Betrachten wir hier nun alle
Details, die uns dieses Programm bietet:

## Allgemein

- Es werden selbstverständlich alle Standardfunktionen angeboten, die
  man von einem Raw-Entwicklerprogramm erwartet und - noch viele mehr.
- Das Abspeichern der Bilder über eine Warteschlange, die später als
  Batch-Prozess gestartet wird, ermöglicht es dem Nutzer, sich in seiner
  Arbeit nicht von der CPU ausbremsen zu lassen, da er die Bilder im
  Hintergrund warten lässt bis er den Batchprozess (nach Arbeitsende,
  z.B. über Nacht) anstößt.
- [Gleitkommazahlen](https://de.wikipedia.org/wiki/Gleitkommazahl)-Engine -
  Das einzige Raw-Entwicklungsprogramm auf dem Markt, dass sämtliche
  Berechnungen in präziser Gleitkomma-Arithmetik ausführt und somit
  Rundungs- und Informationsverluste in sämtlichen Funktionen vermieden
  werden.
- Auf [Streaming SIMD
  Extensions](https://de.wikipedia.org/wiki/Streaming_SIMD_Extensions)
  optimierte Programmierung für eine höhere leistungsmäßige Ausnutzung
  moderner CPUs
- Das [Farbmanagement](https://de.wikipedia.org/wiki/Farbmanagement)
  verwendet die plattformübergreifende Software
  [LittleCMS](https://de.wikipedia.org/wiki/LittleCMS) in Version 2 für
  eine präzisere Farbbehandlung, die eine gezielte Steuerung des
  Farbraumes bei der Bearbeitung und Ausgabe ermöglicht.
- Für das [DNG-Format (Digitals
  Negativ)](https://de.wikipedia.org/wiki/Digital_Negative) wird auch
  das Lesen und die Dynamikkompression von HDR-Bilder (16-, 24-, 32-bit
  Gleitkomma) unterstützt.
- Der File-Browser unterstützt farbiges Taggen, Suchen (Dateinamen),
  Filtern nach Metadaten (File-Typ, Kamera-Modell, Objektiv-Modell und
  Foto-Parameter)
- DCP- und [ICC-](https://de.wikipedia.org/wiki/ICC-Profil)Farbprofile
  werden unterstützt (präzisere Farben bzw. zum Nachempfindes des
  Kamera-Looks von Kamera-JPEGs)
- Eine ständig eingeblendete Historie-Liste erlaubt, den Überblick über
  bisher durchgeführte Einstellung zu behalten, und lässt es zu,
  zwischen den verschieden bisherigen Arbeitsständen hin und her zu
  springen.
- In einem Schnappschuß-Feld kann man sämtliche Einstellungen an einem
  Bild mehrfach in Form verschiedener Settings hinterlegen und somit
  verschieden Versionen der Bildbearbeitung immer wieder aufrufen
  (Speichern der Schnappschüsse mit dem Bild derzeit noch nicht möglich)
- RawTherapee besitzt eine flexible Nutzeroberfläche in der Teile leicht
  ein- und ausgeblendet werden können, um den zur Verfügung stehenden
  Bildschirmbereich optimal auszunutzen, was im Ganzen die Effizienz bei
  der Bearbeitung verbessert.

------------------------------------------------------------------------

- Easily pan around photos much larger than your screen thanks to pan
  rate amplification, eliminating the need for numerous and fidgety
  mouse movements,

------------------------------------------------------------------------

- Hoch- und runterscrollen der Werkzeuge im rechten Fenster mittels der
  mittleren Maustast ist sicher entkoppelt von der Verstellung von
  Parametern: Um Parameter mit der mittleren Maustaste zu ändern, muss
  zusätzlich noch die Shift-Taste gedrückt werden. Dadurch kann es nicht
  passieren, dass beim Scrollen versehentlich Parameter verstellt
  werden.
- Trotz der vielen einstellbaren Parameter aller Werkzeuge auf einer
  Registerkarte kann sehr effizient zwischen diesen Parametern
  gewechselt werden, ohne die ganze Spalte immer wieder auf- und
  abzuscrollen: Rechte Maustaste auf den Namen eines Werkzeug zeigt
  dessen Parameter an und schließt gleichzeitig die Anzeige der
  Parameter aller anderen Werkzeuge dieser Registerkarte.
- Vorher/Nachher-Ansicht zum Vergleich der letzten Änderung zum Zustand
  davor
- Unterstützung/Anwendung von PP3-Prozessfiles
  ([Sidecar-Files](https://de.wikipedia.org/wiki/Filialdatei)) im Ganzen
  oder nur auswählbare Teile davon
- Anzeige der einzelenen Kanäle Rot, Grün, Blau, Helligkeit und
  Fokusmaske in der Vorschau möglich
- Anzeige der einzelnen Kanäle Rot, Grün, Blau,
  [CIELAB-](https://de.wikipedia.org/wiki/Lab-Farbraum)Helligkeit,
  Farbsättigung und Raw-Pixel-Werte im Histogramm
- Anzeige von Übersteuerung der Farbkanäle ([Color
  clipping](https://en.wikipedia.org/wiki/Clipping_(photography))) in
  der Voransicht
- Für den Schnell-Export gibt es eine eigene Registerkarte (in der
  Dateiverwaltung).
- Zahlreiche Tastatur-Kürzel ermöglichen eine hohe
  Bearbeitungsgeschwindigkeit durch den Nutzer.
- Kommmandozeilen-Unterstützung, um RawTherapee mit Skripten zu steuern
  oder von anderen Programmen aus direkt aufzurufen
- Unterstützung der meisten Kameramodelle (Raw-Format)
- Neue Raw-Formate werden auch dadurch unterstützt, indem das
  [camconst.json](adding_support_for_new_raw_formats/de)-File
  im Text-Editor vom Nutzer angepasst werden kann. (Work-Around für
  neuste Kameras, die erst nach dem Erscheinen der letzte
  RawTherapee-Version herausgekommen sind und ein neues proprietäres
  Format des Herstellers mitbringen. Aber auch für absolute
  Kameraexoten.)
- Akustische Meldung, wenn CPU-intensive Arbeiten erledigt sind (zum
  Beispiel die Warteschlange abgearbeitet ist)
- Erhält die
  [IPTC-](https://de.wikipedia.org/wiki/International_Press_Telecommunications_Council)
  und
  [XMP-](https://de.wikipedia.org/wiki/Extensible_Metadata_Platform)Tags
  der Files
- RawTherapee lässt sich an das Farb-Schema des verwendete
  Betriebssystems anpassen oder erlaubt auch ein persönlich gewähltes
  Farbschema.
- Die Programmoberfläche wird derzeit für fast 30 verschiedenen Sprachen
  bereitgestellt.

## Belichtung und Farbe

- Die "Automatische Belichtungseinstellung", ein Button innerhalb des
  Belichtungs-Werkzeugs, setzt einen guten Ausgangspunkt für die weitere
  Bearbeitung. (Eine seltene Ausnahme in RawTherapee: Ein Algorithmus,
  der das Bild analysiert und daraufhin Werkzeugparameter voreinstellt.)
- Verschiedene recht wirksame Methoden, um Zeichnung in Schatten und
  Lichtern wieder herzustellen
- Ein Vignettierungsfilter, der sich als Stilmittel (unabhängig zur
  Objektivkorrektur des gesamten Bildes) nur auf den gewählten
  Bildausschnitt auswirkt.
- Selbstverständlich gibt es einen Grauverlaufsfilter.
- Ein Pipetten-Werkzeug lässt sich für spezifische Kurven verwenden, um
  einen Punkt aus dem Bild auszuwählen und damit einen
  korrespondierender Einstellpunkt in einer Kurve zu setzen.
- Zwei RGB-Tonwert-Kurven, jede davon mit 4 Einstellmethoden, um Farbe
  und Belichtung in beispielloser Art zu steuern.
- Bildanpassungen auf Basis von Kurven in den Farbräumen
  [HSV](https://de.wikipedia.org/wiki/HSV-Farbraum) (Farbwert, Sättigung
  und Hellwert) und [RGB](https://de.wikipedia.org/wiki/RGB-Farbraum)
  (Rot, Grün und Blau)
- Für die getrennte Kontrolle von Farben und Leuchtdichte im
  [Lab-Farbraum](https://de.wikipedia.org/wiki/Lab-Farbraum):
  - L\*-Kurve zur Steuerung der Helligkeit
  - a\*-Kurve zur Steuerung der Farbe auf der Verbindungslinie zwischen
    Rot-Violett auf der einen und Grün auf der anderen Seite
  - b\*-Kurve zur Steuerung der Farbe auf der Verbindungslinie zwischen
    Gelb auf der einen und Blau auf der anderen Seite
  - LH-Kurve zur Steuerung der Leuchtdichte als Funktion des Farbtons
  - CH-Kurve zur Steuerung der Farbsättigung als Funktion des Farbtons
  - HH-Kurve zur Steuerung des Farbtons mit sich selbst
  - CC-Lurve zur Steuerung der Farbsättigung mit sich selbst
  - LC-Kurve zur Steuerung der Leuchtdichte als Funktion der
    Farbsättigung
  - CL-Kurve zur Steuerung der Farbsättigung als Funktion der
    Leuchtdichte
- Vermeidung von Farbverschiebungen unter Verwendung des
  [Munsell-Farbsystems](https://de.wikipedia.org/wiki/Munsell-Farbsystem)

------------------------------------------------------------------------

- Steuerung der "Lebendigkeit, Vitalität" (im Englischen: Vibrance) -\>
  ist Tone Mapping / Dynamik-Kompression damit gemeint?
- Vibrance control,

------------------------------------------------------------------------

- Erhalt der natürlichen Hauttöne
- [Dynamikkompression](https://de.wikipedia.org/wiki/Tone_Mapping)
  basierend auf der Methode "[edge-preserving
  decomposition](http://www.cs.huji.ac.il/~danix/epd/)" für ein
  natürliches Aussehen (Tipp: Benutze das Werkzeug gern regelmäßig, auch
  bei gut ausbelichteten Fotos. Aber wähle dann nur eine konservativer
  Intensität. Der Vorgabewert von RawTherapee ist in den meisten Fällen
  bei gut ausbelichteten Fotos um Faktor 2 und mehr zu hoch gewählt.)
- [Weißabgleich](https://de.wikipedia.org/wiki/Wei%C3%9Fabgleich) -
  Startwert: Kamera, aber auch automatisch, vorgegebene Werte, manuell
  oder mittels Grauwert-Pipette
- Farbkanal-Mixer
- Schwarz-Weiß-Konvertierung mit unterschiedlichen Methoden
- Kontrolle der Farbtöne mit unterschiedlichen Methoden
- Farbinterpolation des Raw-Bildes
  ([Demosaicing](demosaicing/de)) auch für
  [Monochrom-Kameramodelle](demosaicing/de#monochrome_kameras)
  möglich (also Abschaltung der Farbzuweisung zum Pixelmosaik)
- Anpassung an das [CIECAM02](https://de.wikipedia.org/wiki/CIECAM02)
  Farberscheinungsmodell. Viele Werkzeuge, wie
  [Dynamikkompression](tone_mapping/de),
  [Schärfung](sharpening/de), [Farbsaum
  entfernen](Defringe/de.md) und weitere, sind so angepasst,
  dass sie in diesen Modus arbeiten, [sobald er
  aktiviert](CIECAM02/de.md) wurde.
- Farbmanagement

## Detail-Funktionen

- Verschiedene Schärfungsmethoden:
  - Die
    [Unscharf-Maskierung](https://de.wikipedia.org/wiki/Unscharfmaskierung)
    bietet einen einzigartigen und wirkungsvollen Regler, um Details
    herauszuarbeiten, während Halos vermieden werden.
  - Das [RL Deconvolution
    Verfahren](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
    vermindert Schleier.
  - Schärfung wahlweise auch nur für Kanten
  - Anhebung des Mikrokontrastes im unmittelbaren Pixelumfeld
  - Kontrast nach Detailstufen (die erste, länger zurückliegende
    Implementation auf Basis der Wavlet-Dekomposition mit festen 5
    Detail-Stufen)
- Sehr wirksames Minderungsverfahren des Farb- und Helligkeitsrauschens
  (auch schon auf Wavelet-Basis implementiert)
- Impuls-Rauschminderungsverfahren (holt "ausgerissene Pixel" zurück)
- Farbsaumentfernung

## Spezielle Werkzeuge für verschiedene Detailierungsgrade (Wavlet-basierte Bearbeitung)

Ab Version 5 wurde eine eigene Werkzeugkategorie eingeführt, die mittels
Wavelet-Dekomposition (Aufteilung der Bildinformation auf verschiedene
Detaillierungsgrade) folgende Eingriffe auf das Bild in Abhängigkeit vom
Detailierungsgrad zulässt:

- Kontrast (auf alles oder nur auf Lichter und Schatten)
- Farbintensität
- Farbtönung
- Rauschminderung
- Kantenschärfung
- Gamut-Korrektur
- Minderung von Artefakten im Himmel
- "Restbild"-Belichtungseinstellungen ("Restbild" meint die nach der
  Dekomposition verbleibende großflächige Bildinformation)
- Kontrastkorrekturen als Endretusche

## Transformationsmöglichkeiten

- Perspektiv-Korrektur (stürzende Linien oder seitliche Verzerrungen)
- Adobes Linsenkorrekturprofile werden unterstützt (Verzerrung,
  [Vignettierung](https://de.wikipedia.org/wiki/Vignettierung),
  [Chromatische
  Aberration](https://de.wikipedia.org/wiki/Chromatische_Aberration))
- Verzeichnungskorrektur (positive und negative rotationssymmetrische
  tonnenförmige Verzerrungen)
- Korrektur der Chromatischen Aberration (nach dem Demosaicing)
- Vignettierungskorrektur (positiv, wie negativ) auf das gesamte Bild
  (also zur tatsächlichen Objektivkorrektur im Gegensatz zum
  Vignettierungsfilter (s. oben))

## Demosaicing Verfahren

- AMaZE,
- IGV and LMMSE **zur Anwendung mit der Rauschminderung, um
  Labyrinthmuster zu vermeiden**
- EAHD,
- HPHD,
- VNG4,
- DCB,
- AHD,
- Mono,
- Fast.

## Werkzeuge, die **vor dem Demosaicing** eingreifen

- Zeilenrauschfilter
- Weiß- und Schwarzpunkt-Abgleich
- Dunkelbild-Subtraktion (eliminiert spezielle Arten von Rauschen und
  hot-Pixel)
- Weißbild-Korrektur (engl. "flat field correction") zum einfachen
  Korrigieren von Vignettierung, Farbstichen durch Objektive sowie Staub
  auf dem Sensor
- manuelle oder automatische Korrektur der Farbfehler (Aberration) von
  Objektiven

[Category:General](category:general)
