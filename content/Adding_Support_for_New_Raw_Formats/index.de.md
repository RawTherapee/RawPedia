---
title: Adding Support for New Raw Formats de
contributors:
  - Fherb
tags:
  - 'General Information'
---

Created for referencing.

Todo-List / State:

- Translation: completed
- Content completely cleared: open, see discussion
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Unterstützung neuer Raw-Formate zufügen

Es ist relativ einfach eine perfekte Unterstützung neuer Kameras
hinzuzufügen. Du kannst das selbst erledigen oder du machst die
notwendigen Fotos und sendest sie zu uns. Wir können dann die
notwendigen Messungen selbst erledigen und die Unterstützung deiner
Kamera hinzufügen.

## Einführung

Um ein Raw-File richtig lesen zu können, müssen einige Dinge über das
verwendete Format bekannt sein. RawTherapee holt sich diese
Informationen von drei Orten:

- Aus dem integrierten
  [DCRaw](https://de.wikipedia.org/wiki/DCRaw)-Code,
- dem Raw-File selbst und
- aus dem Textfile mit der Bezeichnung *camconst.json*.

Die benötigten Informationen werden aus allen drei Quellen geholt, wobei
*camconst.json* die mit der höchsten Priorität ist. Wenn sich aus den
drei Quellen Informationen eventuell überschneiden, haben die Daten aus
*camconst.json* Vorrang.

*camconst.json* umfasst folgende Informationen für (möglichst) jede
Kombination aus Farbkanal, ISO und Blende eines jeden Kameramodells:

- Farbmatrizen für die [Standardbeleuchtung
  D65](http://en.wikipedia.org/wiki/Illuminant_D65) im DCRaw-Format
- Weiß- und Schwarzschwellen
- die rohe Ausschnittsgröße und der Offset um ungültige Zeilen und
  Spalten zu entfernen
- Größe und Offset des maskierten Bereichs aus denen Schwarzschwellen
  berechnet werden können

Deshalb ist *camconst.json* der Ort, wo einerseits schnell detaillierte
Unterstützung neuer Raw-Formate zugefügt werden kann, aber auch die
Unterstützung bereits vorhandener Kameras zu verbessern, falls sie in
DCRaw nur unvollkommen unterstützt werden.

## Benötigte Fotos

Um die erforderlichen Messungen für eine perfekte Kameraunterstützung zu
machen, benötigt man verschiedene Fotoserien mit spezifischen
Einstellungen:

- Jedes Foto muss vollständig, über das gesamte Bild hinweg
  überbelichtet sein! Du erreichst das, indem du die Kamera gegen eine
  helle Lichtquelle hältst. Zum Beispiel den Himmel oder eine Lampe.
  Zoome gegebenfalls hinein, falls das erforderlich ist und stelle die
  Belichtungszeit so groß ein, dass alle Bereiche im Bild vollständig
  überbelichtet sind. Verwende zum Fotografieren selbstverständlich das
  Raw-Format. Falls deine Kamera mehrere Raw-Betriebsarten unterstützt,
  nutze das, wo das Bild im größten Format vorliegt und wähle eine
  verlustlose Kompression, falls das einstellbar ist.

1.  Falls deine Kamera eine eingebaute Rauschminderung für das Raw
    besitzt (JPEG ist egal), dann schalte sie jetzt bitte ab. Mache nun
    eine Serie von Fotos, wie oben beschrieben (vollständig
    überbelichtet) für jeden ISO-Wert, der an der Kamera einstellbar
    ist. Die Blende soll auf 8 stehen und achte darauf, dass du genügend
    Licht hast, damit du die Überbelichtung deutlich erreichst, dabei
    aber eine Belichtungszeit von 1/2 Sekunde nicht überschreiten musst.
    Nehmen wir als Beispiel eine typische Kamera an, die folgende
    ISO-Einstellungen zulässt: ISO100, ISO200, ISO400, ISO800, ISO1600,
    ISO3200, ISO6400, ISO12800. Nimm in dem Fall also 8 Fotos auf.
    Neuere Kameras haben oft auch Zwischenwerte, wie ISO160, ISI320 usw.
    Nimm in so einem Fall auch für alle diese Zwischenwerte je ein Foto
    auf.
2.  Wenn Deine Kamera eine eingebaute Rauschminderung für Raw besitzt,
    dann schalte sie bitte jetzt ein und nimm eine zweite Serie von
    Bildern auf. Verfahre dabei wie oben, allerding stelle die Blende
    auf 5,6 und belichte grundsätzlich mit mindestens 2 Sekunden
    Belichtungszeit. Beim Beispiel von oben ergibt das weitere 8 Bilder.
3.  Einige Kameras skalieren die Raw-Informationen bei der Anwendung
    weit geöffneter Blende, insbesondere Canon und Nikon Modelle. Der
    einzige Weg sicher rauszubekommen, was die Kamera macht, ist, Fotos
    zu machen und sie auszumessen. Mache ein Foto mit dem Obejktiv, das
    dir zur Verfügung steht, welches die größte (also offenste) Blende
    besitzt. Also z.B. bei f/1,7 bei ISO100 und langer Belichtungszeit.
    Schalte dabei eine möglicherweise vorhandene Rauschreduzierung ab.
    Sende uns auch dieses Foto zusammen mit den Anderen. Sollten wir
    erkennen, dass die Kamera so eine Skalierung ausführt (oder du hast
    es schon selbst bemerkt), dann würden wir dich bitten, eine größere
    Serie von Fotos aufzunehmen. Und zwar für jeden ISO-Wert eine Reihe
    mit jedem vom Objektiv unterstützten Blendenwert (ideal 1/3
    Schritte), bei dem die Kamera diese Skalierung ausführen könnte (und
    wenigstens noch ein Blendenwert mehr). Und das wiederum
    grundsätzlich bei einer Belichtungszeit unter 1/2 Sekunde.

Das kann bedeuten, dass dies eine Menge Fotos werden. Die Handhabung von
Raw-skalierten Daten bei offenen Blenden ist in der Bildentwicklung
jedoch nicht sehr bedeutend. Lasse dich in so einem Falle nicht
entmutigen und zur Not sparst du dir diesen dritten Punkt. Die vorher
aufgenommenen Werte sind wichtiger. Wenn du aber Zeit und Lust hast (und
deine Kamera überhaupt solche Skalierungen ausführt), kannst du uns und
allen Nutzer damit einen Gefallen tun, diesen Effekt bei der
Bildberechnung zu berücksichtigen.

Betrachte die 3 Punkte als Prioritätenwertung: Das Wichtigste und
Mindeste, was benötigt wird, sind die Bilder aus Punkt 1. Punkt 2 und 3
hängen letztlich auch davon ab, was deine Kamera für Fähigkeiten
(Raw-Rauschminderung) oder Eigenschaften (Offenblenden-Skalierung)
besitzt. Bei Fragen erreichst du uns auch gerne über das
[Forum](http://rawtherapee.com/forum).

Bevor du uns die Bilder schickst, lohnt es sich so richtig, sie zu
komprimiere: Da sie durchweg überbelichtet sind, enthalten sie so viel
gleichartige Information, dass die Files extrem gepackt werden können.
Ehe du vielleich 1/4 Gigabyte Daten hoch lädst, kann es sein, dass sie
nach der Komprimierung nur noch um ein einziges Megabyte groß sind.
Außerdem sind alle Files in einem zip-File leichter zu hantieren beim
hoch- und runterladen.

Lade das komprimierte Archiv auf [filebin.net](http://filebin.net/) hoch
und sende uns den Link über unsere
[GitHub](https://github.com/Beep6581/RawTherapee/issues/new) Seite oder
im [Forum](http://rawtherapee.com/forum).

## Details

Exakte Informationen und detailiertere Hinweise über die benötigten
Bilder und Beschreibungen, wie sie aufzunehmen sind, findest du im
Kommentarteil am Beginn des *camconst.json*-Files. Online liegt es hier:
[<https://github.com/Beep6581/RawTherapee/blob/master/rtengine/camconst.json>](https://github.com/Beep6581/RawTherapee/blob/master/rtengine/camconst.json)
