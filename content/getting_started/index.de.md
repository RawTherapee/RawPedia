---
title: Getting Started
contributors:
  - Fherb
  - McCap
  - Pxlcore
  - marter001
tags:
  - 'General Information'
weight: 1
---

Todo-List / State:

- Translation: completed
- Content completely cleared: yes
- Expression and didactics checked: completed
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Einstieg

## Wie du das Handbuch verwenden solltest, um fix durchzustarten

Wir wissen, das der Erstnutzer von RawTherapee, wenn er nach der Installation sofort mit der Methode *trial-and-error* zu arbeiten
beginnt, sehr schnell derart frustriert sein kann, dass er RawTherapee so schnell es geht wieder deinstalliert. Das liegt nicht nur an der
Funktionsvielfalt, sondern am gesamten Bedienkonzept, dass weniger auf schnellen Start für Newbies konzipiert ist, sondern für effizientes
Arbeiten mit hunderten von Bildern an einem Abend. Auch Du wirst ganz fix in die Bedienung des Programms einsteigen. Wenn Du keine Lust darauf
hast, dass heute Dein Adrenalinspiegel unnütz steigt, dann lies bitte zuerst dieses Einsteiger-Kapitel des Handbuches und mach mit den ersten
Anleitungen gleich mit.

Ob, wann und wie intensiv Du den Rest des Handbuches liest, kannst Du schon am Ende dieses Kapitels und Deiner ersten Versuche sehr gut selbst einschätzen. Das Handbuch ist so gestrickt, dass du schon beim Lesen dieses Kapitels losmachen kannst und mit deinen ersten Erfahrungen
später tiefer in die Interna und damit in das gesamte Handbuch eintauchen kannst.

Nur - was wir nicht möchten - ist, dass Du irgendwann einmal bei der Nutzung dieses hervorragenden Raw- und Bildbearbeitungsprogramms stöhnst. Dafür arbeiten wir beim Zusammenstellen dieses Handbuchs. Und nun sei herzlich...

## Willkommen

RawTherapee ist ein plattformübergreifendes Bildverarbeitungsprogramm für Kamera-Roh-Datenformate (sogenannte "Raw-Files", aber nicht ausschließlich!), das unter der GNU General Public License Version 3 veröffentlicht wird. Ursprünglich von Gábor Horváth aus Budapest
entwickelt, wurde 2010 die Entwicklung von einem Team von Leuten aus der ganzen Welt übernommen. Statt ein reines Bitmap-Grafikeditor-Programm, wie z.B. Photoshop oder Gimp, oder eine Bildverwaltungsprogramm, wie digiKam, zu sein, ist RawTherapee speziell auf die Foto-Postproduktion ausgerichtet. Also die umfassende Bildverarbeitung nach der Aufnahme. Und diese Aufgabe erfüllt das Programm ausgezeichnet. RawTherapee ist als eines der leistungsstärksten Raw-Bilderverarbeitungssysteme bekannt.

## RawTherapee installieren

### Stabile Versionen
Die Installation erfolgt sehr einfach über die Installer von [rawtherapee.com/download (Windows,MacOS)](http://rawtherapee.com/downloads) oder über Paketmanager (Linux). Es ist auch möglich, RawTherapee aus den Quelldateien selbst zu
kompilieren. Links dazu sind hier zu finden: [selbst Kompilieren](/windows). [Eine portable Installation erstellen](/Making_a_Portable_Installation) ist ebenfalls möglich.

#### *Linux-Nutzer*
Falls du mit dem RawTherapee, dass dir im Linux-Repository deiner Linux-Distrubution angeboten wird, Stabilitätsschwierigkeiten hast, solltest du die Windows-Version mittels Wine verwenden. In der Windows-Version sind sämtliche Laufzeitbibliotheken enthalten, wie sie vom Entwicklungsteam verwendet werden. Die Linux-Distributionen binden RawTherapee, wie jede andere Software auch, in ihren eigenen Biotop ein, was zumindest bei RawTherapee nicht immer einwandfrei klappt.

### Entwicklungsversionen

Die Bereitstellung der Entwicklungsversionen zwischen den als stabil deklarierten Versionen mit dem Zusatz "dev" (aber auch frühere Versionen von RawTherapee) sind unter folgendem Link zu finden [Entwicklungsversionen](https://github.com/RawTherapee/RawTherapee/releases/tag/nightly-github-actions).

- Ab Version 5 werden Entwicklungsversionen für Windows 32 und 64 bit zur Verfügung gestellt ,
- für macOS nur teilweise und
- für Linux in den jeweiligen Paketmanagern. Bedeutet für Linux, dass die Verfügbarkeit vermutlich zwischen den einzelnen Distributionen sehr unterschiedlich ist.

Alternativ bietet sich natürlich immer der schon oben genannte Weg, sich den aktuellen Entwicklungsstand aus den Quellen selbst zu kompilieren. Gerade für Linux gar nicht grundsätzlich unüblich.
Für alle die vor haben, mit Entwicklungsversionen zu arbeiten, hier einige grundsätzliche Information zu der Art und Weise der Entwicklungsarbeit bei solchen Softwareprodukten:
Die eben beschriebenen Entwicklungsversionen, sogenannte "nightly builds", werden in unregelmäßigen Abständen zur Verfügung gestellt. Zumeist werden damit Fehler beseitigt aber auch neue Funktionen integriert.
In größeren Abständen werden daraus stabile Versionen mit einer neuen neuen Versionsnummer veröffentlicht, bei denen auch nahezu alle bis dahin bekannten Bugs ausgemerzt wurden.
Alle danach in dieser stabilen Version noch gefundenen Fehler werden dann wiederum mit in den folgenden Entwicklungsversionen ausgebessert.
Du bekommst in diesem Falle alle neuen Funktionen und frühere Bugs sind inzwischen entfernt. Nutze dies auch, um neue Bugs, Probleme oder auch neue Ideen den Entwicklern mitzuteilen. Ein unschätzbarer Wert zur Entwicklung des Projektes,
dessen Gewinner wir alle sind. - Jedoch: Für die ernsthafte Nutzung empfehlen wir, die letzte stabile Version zu verwenden. Vor allem, wenn du in kurzer Zeit viele Bildentwicklungen bearbeiten musst, ist es besser, auf neue Features zu verzichten, mit den wenigen inzwischen
hoffentlich bekannten Bugs der stabilen Version zu leben (wenn es sie denn gibt), als sich dem Risiko auszusetzen, mit einer neueren Version Überraschungen zu erleben.

### Abwärtskompatibilität

Zu beachten ist in dem Zusammenhang, dass sich das Format der sogenannten Sidecar-Files, also der Files mit den Einstellparametern zu jedem Bild, das parallel zum Bild abgespeichert wird, über die Entwicklungszeit zwischen den stabilen Versionen ändern kann und dieses Format der Entwicklungsversionen im ungünstigsten Falle weder aufwärts (zur nächsten stabilen Version) noch abwärtskompatibel zur letzten stabilen Version ist. Insbesondere kann nicht davon ausgegangen werden, dass die Sidecar-Files zwischen stabilen Versionen abwärtskompatibel sind. Aufwärtskompatibilität zwischen stabilen Versionen sollte aber immer gegeben sein.

## Starte RawTherapee

Wenn Dir die Programmoberfläche auf den ersten Blick recht ungewöhnlich im Vergleich zu anderer Software erscheint, dann lass Dir gesagt sein, dass RawTherapee nicht nur leistungsstarke Funktionen besitzt, sondern ganz darauf ausgerichtet ist, diese dem Nutzer so zu präsentieren, dass er damit ausgesprochen effizient umgehen kann. Wenn Du später hunderte Bilder in möglichst kurzer Zeit verarbeiten willst, wirst Du froh sein, wenn Dir das Programm Tricks und ein workflow-gerechtes Design bietet, das hilft, jeden überflüssigen Mausklick zu vermeiden.

![](Rt_setm_fb.png "Rt_setm_fb.png") 


Doch, lass uns endlich anfangen.

Beim ersten Start von Rawtherapee wird die Registerkarte [Dateiverwaltung](the_file_browser_tab) sichtbar und sehr wahrscheinlich leer sein (der Reiter der Registerkarte befindet sich ganz links oben). Suche in der Baumstruktur auf der linken Seite nach dem Ordner mit deinen Raw-Files und öffne diesen durch einen Doppelklick. Öffne dann ein Raw-Foto durch einen Doppelklick auf das Foto.

## Bearbeite dein erstes Bild

Sobald du ein Raw-Bild für die Bearbeitung öffnest, wirst du feststellen, dass die Vorschau nicht so aussieht, wie das JPEG-Bild, das die Kamera erzeugt hat. Der Artikel "[Heh! Mein Raw-Bild sieht anders aus als das aus der Kamera](The_Image_Editor_Tab/#heh-mein-raw-bild-sieht-anders-aus-als-das-kamera-jpg)"
beschreibt, warum das so ist. Sei an dieser Stelle nicht frustriert, dass es zu Beginn einiger Arbeitsschritte bedarf, um deinem Bild ein zumindest wieder vergleichbares Finish zu geben. Sobald du mit RawTherapee vertraut bist, wirst du dies recht schnell erledigen und in der Regel zu einem weit aus besser entwickelten Ergebnis kommen.

Die Bearbeitung erfolgt über die Registerkarte [Bildeditor](the_image_editor_tab) (den Editor-Reiter findest du ebenfalls links unter "1" and dritter Position). Das ist der Bereich um atemberaubende Kunstwerke zu erstellen - oder vielleicht auch nur, um Erste Hilfe für Schnappschüsse zu leisten.

![](Rt_setm_editor.png "Rt_setm_editor.png")

Nimm dir einen Moment Zeit, um dir die Registerkarte "Editor" anzusehen. Beachte, dass es weitere Registerkarten innerhalb des Editors gibt - auf der rechten Bildschirmseite oben befinden sich die zugehörigen Reiter zur Auswahl. Diese Reiter und die darunter befindlichen Steuerelemente sind der sogenannte Werkzeugkasten. Wahrscheinlich hast du dort noch den ersten Reiter geöffnet und wenn du die Maus über diesen Reiter führst (ohne zu klicken), wirst du einen sogenannten Tool-Tip-Text am Mauszeiger eigeblendet sehen, der dir sagt, dass dieser Reiter "Belichtung" heisst. Unterhalb dieser Register-Auswahl befinden sich alle Werkzeuge, die dieser Registerkarte thematisch zugeordnet sind - Belichtung, Schatten / Lichter, Dynamikkompression usw. Wenn du auf eine dieser Bezeichnungen klickst, wird der Bereich darunter erweitert und du kannst alle zugehörigen Bedienelemente sehen. Klickst du erneut diesen Werkzeugnamen an, wird dieser Bereich wieder ausgeblendet. Verwendest du beim Aufblenden der Steuerelemente die rechte, statt der linken Maustaste, werden beim Aufblenden unter diesem Werkzeug gleichzeitig alle Bedienelemente unter den anderen Werkzeugen ausgeblendet - ein zeit- und platzsparendes Verfahren beim ständigen Wechsel zwischen der umfangreichen Zahl an Bedienelementen aller Werkzeuge zusammen genommen.

Auf der linken Seite neben dem Werkzeugnamen befindet sich in vielen Fällen das kleine Symbol eines Netzschalters. Mit ihm kannst du u.a. die Wirkung des Werkzeugs ein- oder ausschalten. 
Dort, wo sich kein "Netzschalter" befindet, steht ein kleines Dreieck, das nur den ein- oder aufgeklappten Zustand der Bedienelemente anzeigt. Mehr hierzu findest du unter [Allgemeine Bemerkungen über die Verwendung der Werkzeuge](General_Comments_About_Some_Toolbox_Widgets).

Gehe nun mal durch alle Tabs, öffne einige Werkzeuge und du wirst von der Vielfalt an Bearbeitungsmöglichkeiten überwältigt sein. Aber fühle dich dadurch nicht erschlagen: Für die grundlegenden Bearbeitungsschritte wirst du anfangs mit einer beschränkten Anzahl an
Bedienelementen aus kommen. Je nach Vorwissen, Erfahrung, Lernfortschritt und deiner persönlichen Einstellung zu der Frage, wie viel Perfektion du Deinen Bildern zukommen lassen möchtest (ist ja auch eine Zeitfrage), steigst du dann auch in die auf den ersten Blick
manchmal kompliziert wirkenden Bearbeitungswerkzeuge ein. Einige Werkzeuge ermöglichen untereinander auch alternative Eingriffe für das gleiche Bearbeitungsziel. Eines der Herausstellungsmerkmale von RawTherapee ist diese alternative Implementierung von Algorithmen, die
durchaus zum Experimentieren und Vergleichen der Wirkung einlädt. Ebenso die teils hohe Zahl an Parametern eines Werkzeugs. Nutzer stellen damit gewöhnlich ihren ganz persönlichen Workflow zusammen. 

In anderen(zumeist kommerziellen) Produkten ist die theoretisch mögliche Einstellvielfalt eingeschränkt oder mit fest programmierten Automatismen versehen, um durch diese scheinbare Vereinfachung mehr neue Nutzer zum Kauf des Produktes zu bewegen. 
RawTherapee benötigt diese gewinnoptimierende Herangehensweise nicht. Mach dir also keine Sorgen, wenn du mit RawTherapee startest und diese Funktions- und Einstellungsvielfalt mit anderen Produkten vergleichst. Nimm dir bei den ersten Bildern Zeit, erforsche die Funktionen und nutze dabei vor allem auch die Funktion der Anzeige von Tool-Tip-Texten der Bedienelemente und Werkzeuge (also Maus nur drüber fahren). Deren Übersetzung und Inhalt hat sich mit der Version 5 noch mal ein ganzes Stück weiter verbessert.

Für die Steilheit deiner Lernkurve sind dann auch wir mit der Erstellung dieses Handbuches verantwortlich.

Bevor du mit der Bildbearbeitung startest, an dieser Stelle noch ein wichtiger Hinweis: **Keine Panik!** Es besteht keine Gefahr, dass du während der Bearbeitung irgend etwas an deinen Bildern zerstörst, falls du einen Fehler machst. RawTherapee besitzt einige Eigenschaften die Dir helfen, deine Bilder zu schützen:

- RawTherapee arbeitet mit einem sogenannten nicht-destruktiven Bearbeitungsverahren. Das bedeutet, dass RawTherapee nie das eigentliche Bild-File (Raw-File, oder eines der anderen unterstützten Formate) selbst bearbeitet oder irgend etwas in dieses File schreibt.
  Alle Bearbeitungseinstellungen am Bild werden in einem sogenannten Sidecar-File abgelegt. Sidecar bedeutet "Beiwagen", was hier meint, dass jedes Bild einen solchen Beiwagen als separates File zur Seite gestellt bekommt, und die Informationen darin bei einem späteren Aufruf von RawTherapee bzw. des betreffenden Bildes automatisch mit eingelesen werden. Du kannst im Artikel [Sidecar-Files - Prozessprofile](Sidecar_Files_-_Processing_Profiles) weitere Information darüber finden. Das Sidecar-File wird im Zusammenhang mit RawTherappe auch oft als *Profildatei* bezeichnet.
- Wenn du den Bildeditor verwendest, findest du auf der linken Seite einen Bereich, der mit [Historie](/the_image_editor_tab#historie) überschrieben ist. Dieser Bereich zeigt sämtliche einzelnen Änderungen der Werkzeugparameter während deiner Bearbeitung als Tabelle in der Reihenfolge deiner Änderungen an. Um zu irgend einem Schritt (einschließlich des ersten Schrittes: das Laden des Bildes) zurückzukehren, brauchst du nur auf den entsprechenden Eintrag in der Historie klicken.
- Unterhalb der Historie befindet sich der Bereich [Schnappschüsse](/the_image_editor_tab#schnappschüsse).
  Du kannst das erst mal überspringen. Aber du wirst dies recht praktisch finden, wenn du mit RawTherapee einige Erfahrungen gesammelt hast. Dieser Bereich speichert den aktuellen Stand der Einstellungen aller Werkzeuge in Form eines "Schnappschusses". Dies erlaubt dir zum Beispiel dein Bild zuerst in einen schönen farbigen Look zu bringen und von diesen Einstellungen einen Schnappschuss zu machen, während du dann das Bild in einen schönen Schwarz-Weiß-Look bringst und auch davon einen Schnappschuss anfertigst. Und dann kannst du einfach durch wechselweises Anklicken der beiden Schnappschüsse beide Varianten miteinander vergleichen. RawTherapee speichert diese Schnappschüsse (noch) nicht im Sidecar-File (.pp3)!, für die Zukunft ist das aber geplant. Wenn du also das Programm schließt oder ein anderes Bild zur Bearbeitung öffnest, wird nur der zu diesem Zeitpunkt aktive Zustand aller Werkzeuge im Sidecar-File abgelegt. Auch die Historie vergisst das Programm zu diesem Zeitpunkt, da auch sie nicht mitgespeichert wird. Wenn du trotzdem alle Schnappschüsse aufheben möchtest, dann aktiviere nacheinander die Schnappschüsse und speichere diese dabei in eigene SideCar-Files, die du unterschiedlich benennst. Nutze dazu jeweils den Button "Profil speichern" ganz oben rechts über dem Werkzeugbereich unter "Bearbeitungsprofile".)
- Und, wie du vielleicht erwartest, Strg-z nimmt die zuletzt getätigte Änderung zurück. Es wird also in der Historie ein Schritt nach oben gesprungen.

### Grundlagen

1.  Öffne das Raw-Foto. RawTherapee lässt es automatisch ähnlich wie das JPEG aus deiner Kamera aussehen. Wenn du mit dem Ergebnis zufrieden bist, bist du fertig. Andernfalls lies weiter.

2.  Klicke auf die ![<File:/images/Color-circles.png>](Color-circles.png "File:/images/Color-circles.png") Farbregisterkarte und erweitere das Werkzeug [Weißabgleich](white_balance) durch Klicken mit der rechten Maustaste (oder verwende das [Tastenkürzel](keyboard_shortcuts)). RawTherapee startet mit dem von deiner Kamera verwendeten Weißabgleich. Die meisten Einstellungen des Weißabgleichs erfordern das Verschieben der Schieberegler *Farbtemperatur* und *Tönung* oder die Verwendung des ![<File:/images/Color-picker.png>](Color-picker.png "File:/images/Color-picker.png") *Farbwählers* auf einen neutral grauen Punkt. 

3.  Als nächstes korrigiere die Belichtung, indem du auf die Registerkarte ![<File:/images/Exposure.png>](Exposure.png "File:/images/Exposure.png") (Belichtung) gehst, erweitere das Werkzeug [Belichtung](exposure) und stelle die Parameter so ein, dass dein Bild nach deinem Geschmack optimal ausgeleuchtet ist. Verwende jetzt erst mal nur die Regler Belichtungskorrektur und Sättigung.

4.  Falls dein Bild verrauscht ist, gehe auf die Registerkarte ![<File:/images/Detail.png>](Detail.png "File:/images/Detail.png") (Details). Zoome jetzt mit dem Button ![<File:/images/magnifier-1to1.png>](magnifier-1to1.png "File:/images/magnifier-1to1.png") oder der Taste "z" auf 100%. Beachte: Die Bildveränderungen, die du mit den Werkzeugen auf dieser Registerseite ausführst, sind nur bei einer Darstellung mit 100% oder darüber in der Vorschau sichtbar.
    Und natürlich auf dem fertigen, abgespeicherten Bild. Aktiviere nun auf dieser Registerkarte das Werkzeug [Rauschreduzierung](noise_reduction) (den kleinen "Netzschalter" links neben der Schrift "Rauschreduzierung" anklicken; er wechselt von Dunkel- auf Hellgrau). Das Werkzeug besitzt bereits voreingestellte Parameter, die mit der Aktivierung wirksam werden. So mindert RawTherapee automatisch das Farbrauschen (Chrominanz) mit einer voreingestellten Stärke. Die Reduzierung des Helligkeitsrauschens ist in den Standardeinstellungen zunächst abgeschaltet. Ein gewisses Restrauschen der Helligkeit verleiht dem Bild in der Regel einen angenehmen, leicht körnigen, filmähnlichen Look. Als allgemeine Regel gilt, wenn du die Rauschreduktion verwendest, dann nutze nicht gleichzeitig die Funktion "Schärfung".
    Zoome jetzt wieder heraus, sodass du das ganze Bild siehst. Nutze hierzu das Mausrad, den Button ![<File:/images/magnifier-fit.png>](magnifier-fit.png "File:/images/magnifier-fit.png") oder die Taste "f" auf der Tastatur.

5.  Nehmen wir an, du möchtest jetzt noch dein Bild etwas bezüglich [Linsen- und Geometriekorrektur](/lens-&-geometry) bearbeiten und dann das Bild noch beschneiden und in der Auflösung reduzieren. Was im Einzelnen zu tun ist, hängt natürlich von deinem Foto ab. Wir beschreiben hier mal exemplarisch einige Schritte, die aber fast immer benötigt werden: 
   - Korrigiere zuerst die Ausrichtung des Bildes. Dies kannst du recht einfach erledigen, wenn du als Hilfslinie eine geeignete gerade senkrechte oder vertikale Kante im Bild vorfindest. Zum Beispiel ein Horizont, eine Straßenlaterne oder eine Hauskante. (Oder du "denkst" dir aus dem Gefühl heraus eine solche Hilfslinie, wenn im Bild keine passende Kante zu finden ist. Das Augenmaß ist in diesem Fall nicht zu unterschätzen.) Das Verfahren ist in dem Fall sehr einfach: Drücke "s" auf der Tastatur (oder den Button ![](/images/rotate-straighten.png "File:/images/rotate-straighten.png")), und dann ziehe mit der Maus eine Leitlinie entlang dieser
      ausgewählten (oder gedachten) Kante im Bild. Das Bild wird von RawTherapee automatisch ausgerichtet. Gleichzeitig wird rechts die Registerkarte ![<File:/images/Transform.png>](Transform.png "File:/images/Transform.png") (Transformieren) geöffnet und das Werkzeug "Objektivkorrekturen"
      aufgeklappt. Dort kannst du die Drehung auch über eine Winkelangabe ausführen. Und darunter ist mittels beschriftetem Button die dritte Möglichkeit zu finden, das Zeichnen der Leitlinie zu aktivieren.
   - Um das Bild nun zu beschneiden, drücke die Taste "c" oder verwende den Button ![<File:/images/crop.png>](/images/crop.png "File:/images/crop.png") und ziehe ein Rechteck entsprechend des Bildausschnitts auf den beschnitten werden soll. Auch in diesem Fall wird das passende Werkzeug ["Ausschnitt"](crop) im Werkzeugkasten angesprungen
      und aktiviert. Gewöhnlich schaltet RawTherapee dabei ein geeignetes festes Seitenformat zu, was du daran merkst, dass du das Rechteck nicht beliebig ziehen kannst. Ist das ungünstig, deaktiviere in den Werkzeugeinstellungen die Funktion "Format". Du kannst dort auch entsprechend deiner Arbeitsweise die Darstellung von Hilfslinien einstellen oder ganz abschalten.
   - Abschließend nehmen wir an, dass du dein Bild herunterskalieren möchtest. Wer möchte schon ein 10MB JPEG z.B. in sein soziales Netzwerk hochladen? Wenn du die vorherigen Schritte ausgeführt hast, befindest du dich rechts bereits im entsprechenden Register Transformieren ![<File:/images/Transform.png>](Transform.png "File:/images/Transform.png")).
      Gehe dort auf das Werkzeug "Skalieren" und aktiviere auch dieses über den kleinen "Netzschalter". Belasse es für diesen Versuch bei den Standardeinstellungen. Seit der Version 5 kannst du hier auch einen zusätzlichen Schärfungsschritt nach der Skalierung aktivieren. Beachte aber, dass weder die Skalierung, noch diese abschließende Schärfung in der Vorschau zu sehen sind. Derzeit (Stand 03/2017, Version 5.0) ist ein genauer Abgleich der Schärfungsfunktion nur dadurch möglich, dass du das Bild, wie gleich nachfolgend beschrieben, abspeicherst und den Effekt danach überprüfst.

6.  Du bist mit der Bearbeitung fertig. Lass uns das Bild nun [speichern](/saving_images). Klicke auf den Button ![<File:/images/save.png>](save.png "File:/images/save.png") (Bild speichern) oder verwende die Tasten Strg+s als Abkürzung. Eine gute "Allgemein-Einstellungen" für die meisten Zwecke ist, wenn du für das JPEG-Format die Qualität auf 92 und die Komprimierung auf "Ausgeglichen" stellst. Wähle den Ordner in den du das Bild abspeichern möchtest und belasse es hier bei der Grundeinstellung der Verarbeitungsmethode "Sofort speichern". Drücke Ok und nach einigen Sekunden liegt das fertig "entwickelte" Bild in dem angegebenen Ordner. Und mit den Standardeinstellungen auch ein .pp3-Sidecar-File mit den eingestellten Werkzeugparametern, wie sie bei diesem Export verwendet wurden. Wie weiter oben schon erwähnt: Zu jeder Zeit, auch wenn du jetzt RawTherapee schließt, liegen die aktuellen Einstellwerte der Werkzeuge des Editors als [PP3 Sidecar-File](Sidecar_Files_-_Processing_Profiles) auch immer "neben" dem originalen (Raw-)Bild, das du gerade im Editor geöffnet hast bzw. hattest, also im gleichen Ordner (zumindest mit den Standardeinstellungen). Wenn du das Bild in Zukunft erneut öffnest, werden diese zuletzt verwendeten Parameter wieder geladen.

Nun, da du die grundlegenden Bearbeitungsschritte kennengelernt hast, lasse uns jetzt etwas weiter vertiefende Details betrachten.

### Vertiefung

#### Allgemeine Hinweise zum Einstieg

Bemühe dich, zu Beginn zu jedem Werkzeug auch den entsprechenden Artikel auf RawPedia durchzulesen, um ein Verständis dafür zu bekommen, was das Werkzeug tut und wie du es konfigurieren kannst. Das ist oftmals effizienter, als mit Trial-and-Error vorzugehen. Manche Werkzeuge haben es in sich. Allein schon auf Grund der zahlreichen einstellbaren Parameter. Im Artikel wirst du sofort sehen, welche Parameter entscheidend für die Funktion sind und welche du vielleicht vorerst links liegen lassen kannst.

Die Artikel beschreiben, wie die Werkzeuge innerhalb RawTherapees arbeiten. Konzepte zur Arbeitsweise der Algorithmen, die allgemeingültig sind und nicht nur speziell mit RawTherapee zu tun haben, werden in der Regel nicht innerhalb der Werkzeug-Artikel beschrieben. Nutze in dem Fall andere Medien, wie zum Beispiel Wikipedia. Zu einigen allgemeineren Punkten, die für die Arbeit mit RawTherapee wichtig sind, gibt es aber auch einige wenige Seiten unter der Rubrik [Allgemeine Informationen](/_index#allgemeine-informationen) innerhalb der RawPedia.

Warst du schon mal auf der Seite [Tastatur-Kürzel](keyboard_shortcuts)?

#### Automatische Abarbeitungsreihenfolge der Werkzeuge bei der Bildberechnung

Falls Du Dich gerade über die Überschrift wunderst: Es gibt einen großen Unterschied darin, in welcher Reihenfolge Du nacheinander Dein Bild mit den Werkzeugen bearbeitest und wie dann RawTherapee daraus Dein Bild berechnet. Egal nämlich, in welcher Reihenfolge du die Werkzeuge benutzt und konfigurierst, ein- und wieder ausschaltest, dabei hin und her springst oder ein Werkzeug wiederholt in seinen Einstellungen veränderst: Die Abarbeitungsreihenfolge von RawTherapee bei der aktuell angezeigten Vorschau des Bildes, wie auch bei der Berechnung des fertigen Bildes, ist absolut fest kodiert. Bei der Bildberechnung ist es also völlig egal, ob Du mit den Werkzeugen "von vorn oder hinten" beginnst. Aber: Trotzdem hängen natürlich die Werkzeuge in der Bildwirkung miteinander zusammen. Wenn du zum Beispiel die Belichtung änderst, kann es sein, dass du darauf hin den Farbton (neu) abstimmen musst. Halte Dich deswegen in der Regel an die folgenden Empfehlungen.

#### Tipps zur Bearbeitungsreihenfolge

1.  Achte zu Beginn darauf, dass RawTherapees Umgebung richtig eingestellt ist. Das heißt:
   - Stelle sicher, dass RawTherapee dein Monitor-Farbprofil benutzt, wenn du mit Farbaufnahmen arbeitest. Prüfe dazu "Einstellungen" -> "Farbmanagement". Den Button für die "Einstellungen" findest du ganz links unten ![<File:/images/preferences.png>](Preferences.png "File:/images/Preferences.png"). Es kann notwendig sein, dass du auch das entsprechende Kalibrierungsprofil in deinem Betriebssystem der Grafikkarte zuweist. Dieses ganze Thema der Farbkalibrierung und -profile ist äußerst komplex. Wenn du dich ernsthaft mit der "Bildproduktion" beschäftigst oder die Absicht hast, über einen Dienstleister größere Abzüge ausdrucken oder ausbelichten zu lassen, solltest du dich aber mit diesem Thema befassen, um später keine bösen Überraschungen zu erleben. Thematisch liegt das Ganze aber größtenteils ausserhalb der "inhaltlichen Reichweite" von RawTherapee, weswegen hier in RawPedia nicht vollständig in der notwendigen Tiefe darauf eingegangen wird. Ziehe bitte entsprechende Veröffentlichungen zu Rate, wenn du sehr exakt abgeglichene Bilder benötigst. Und in diesem Zusammenhang:
   - Stelle sicher, dass das Farbmanagement-Werkzeug korrekt konfiguriert ist. Für gewöhnlich sind die Standardeinstellungen optimal. Lies dazu die Artikel [Farbmanagement](color_management) und [Farbmanagement (Zusatz)](color_management_addon).
      Wenn du dich, anstatt die mit RawTherapee mitgelieferten Farbmatrix bzw. DCP oder ICC Profile zu nutzen, dafür entscheidest, ein Externes zu nutzen, zum Beispiel ein selbst angefertigtes DCP oder eines von Adobe, dann lade das zu allererst, bevor du etwas anderes tust. Sonst kann es sein, dass
      du einige der Farb-Werkzeuge neu abgleichen musst. Nutze immer ein Ausgabeprofil ("Farbmanagement" \> "Ausgabeprofil") - in den meisten Fällen das Standardprofil "RT_sRGB". Im englischen Handbuch heißt es an dieser Stelle etwas schnippig: "Wenn du denkst, dass du schlau bist, indem du "No ICM: sRGB Output" wählst, irrst du dich." - Ziehe also vor irgendwelchen Abweichungen von den Standardeinstellungen möglichst umfangreich alle erreichbaren Dokumentationen zu Rate.

2.  Wenn du in deinem Workflow für ein betreffendes Bild ein [Weißbild](flat_field) und/oder [Dunkelbild](dark_frame) verwenden willst, dann tue es jetzt, um eine spätere Neujustierung zahlreicher Parameter anderer Werkzeuge zu vermeiden.

3.  Setze jetzt den korrekten [Weißabgleich](white_balance). Du kannst zuvor aber auch erst die Belichtung korrigieren, falls das Bild für diesen Schritt zu dunkel oder zu hell ist, um den richtigen Wert für den Weißabgleich zu finden.

4.  Als nächstes gleiche die [Belichtung](exposure) ab. Verwende dazu zuerst die Regler für "Belichtungskorrektur" und "Schwarzwert", um das Bild in den gewünschten Bereich "zu schieben".
    (Schaue dabei auch schon mal oben links auf das Histogramm.) Hast du  die Belichtung des Bildes da, wo du sie haben willst, dann setze mit der Justierung der beiden Tonwertkurven fort. Falls du schon einmal mit Tonwertkurven in anderen Programmen gearbeitet hast und weißt, wie sie funktionieren, lies trotzdem den [Abschnitt Tonwertkuven](Exposure#tonwertkuven) und du wirst lernen, warum es in RawTherapee zwei Tonwertkurven gibt und wie man sie am besten verwendet. Beide zusammen genommen sind sie ein sehr wirksames Werkzeug!

5.  Im Grundlagenabschnitt weiter oben haben wir vorgeschlagen, den [Sättigungs-Regler](exposure#sättigung) innerhalb des Werkzeugs "Belichtung" zu verwenden. Jetzt, nachdem du die Grundlagen schon beherrschst, kannst du damit beginnen, fortgeschrittenere Techniken auszuprobieren. Wie bei vielen anderen Werkzeugen und Reglern, gibt es für die Einstellung der Sättigung auch verschiedene Herangehensweisen. Wir empfehlen, den beschriebenen Sättigungsregler nicht mehr zu verwenden und statt dessen die leistungsstärkere [CC-Kurve](Lab_Adjustments#cc-kurve) im Werkzeug [Lab-Anpassungen](lab_adjustments). Dies gibt uns eine gefühlvollere Einstellmöglichkeit.

6.  Die Vorgabe der Reihenfolge der restlichen Einstellungen kann man als zunmehmend "unscharf" bezeichnen. Von der hier weiter vorgeschlagene Reihenfolge kann nun zunehmend abgewichen werden. 
    Einige Werkzeuge werden ^andere unvermeidlich beeinflussen. Achte also auch darauf, dass du manche Einstellungen zusammen mit anderen iterativ mehrfach durchlaufen solltest, wenn das erforderlich wird, bis du die gewünschte Bildwirkung erreichst. Fahre jetzt mit den weiteren Reglern und Kurven im Werkzeug [Lab-Anpassungen](lab_adjustments) fort, wenn das für dein Bild erforderlich ist. Und wende dann je nach Bedarf den Rest der Einstellmöglichkeiten in der Registerkarte "Belichtung" an. 

7.  Verwende als nächstes die Werkzeuge aus dem Register  ![](/images/color-circles.png) (Farbe). Beachte dabei, dass die genaue Einstellung von Farbtönen sehr empfindlich auf Änderungen der Belichtung und weiterer Einstellungen reagiert, die die Helligkeit von Bildteilen beeinflussen. Hebe dir also die Justierung von Farbtönen bis zu letzt auf.

8.  Zoome nun, wie schon oben beschrieben, auf 100% und nutze die Werkzeuge des Registers  ![](/images/detail.png)  (Details). Denke daran: Nicht schärfen, wenn die Rauschminderung verwendet wird. Beide Funktionen arbeiten etwa im gleichen feinen Auflösungsbereich und beißen sich in ihrer Funktion gegeneinander. Wenn du die Schärfe erhöhen willst, ist es oft möglich, dies scheinbar für's Auge dadurch zu erreichen, in dem Du die Kontraste der mittelgroßen Details etwas anhebst ("Details" \> "Detailebenenkontrast" bzw. alternativ "Wavelet" \> "Kontrast"). Ab Version 5 kannst Du auch beim Abspeichern deines Bildes und damit nach dem Herunterskalieren schärfen. Das ist im Workflow auch der optiomale Zeitpunkt, da die Schärfung mit den typischen Parametern Radius und Intensität sinnvollerweise immer auf die endgültige Ausgabeauflösung abgegelichen werden sollte.

9.  Abschließend zoome wieder heraus und nutze erst jetzt die Werkzeuge des Registers ![](/images/Transform.png) (Transformieren). Der Grund, diese Werkzeuge erst zum Schluss anzuwenden, liegt in der Berechnung des Vorschaubildes: Um dich bei der Arbeit mit dem Programm nicht unnötig auszubremsen, werden die Transformationsalgorithmen für das Vorschaubild zeit-optimiert
    berechnet. Das führt unter Umständen zu einem geringfügig verschwommenen Vorschau-Bild, dass du vielleicht fälschlicherweise mit einigen anderen Werkzeugen auszugleichen versuchst. Beim Speichern des fertigen Bildes werden jedoch die Transformationen selbstverständlich in höchster Qualität ausgeführt. Ein Ausgleich der scheinbaren Weichheit des Vorschaubildes durch dich kann dadurch im Endergebnis zu einem ungewollten Ergebnis führen. - Aber, auch wenn du mit der Bearbeitung am Ende angekommen bist und vielleicht endlich fertig werden willst, vergiss trotzdem nie die Transformationswerkzeuge durchzugehen und, wenn notwendig, anzuwenden. Ein z.B. sehr gering schräg stehendes Ergebnis oder eine seitlich ins Bild hineinragende Hand kann die resultierende Bildwirkung erheblich beeinträchtigen.

10. Die Meta-Daten deines Bildes kannst du auch editieren. Gehe dazu auf das Register ![](/images/metadata.png) (Metadaten). Wenn du hier Änderungen vornimmst, musst du aber unbedingt in den Voreinstellungen eine Option deaktivieren, sonst werden die Werte beim Speichern nicht übernommen: Gehe in "Einstellungen" -> "Bildbearbeitung" -> "Metadaten" und entferne den Haken vor "Exif/XMP unverändert in die Ausgabedatei übernehmen". Ist der Haken gesetzt, werden grundsätzlich die originalen Daten ohne Änderungen für das im Folgenden abzuspeichernde Bild übernommen.

11. Speichere jetzt das Ergebnis. Entweder direkt, wie schon oben beschrieben als einzelnes Foto, oder lege es in die sogenannte [Warteschlange](the_batch_queue) ab und lasse die Fotos erst am Ende in einem Rutsch fertigstellen, um dich nicht zwischendurch auszubremsen, wenn du weitere Bilder bearbeiten oder das gleiche Bild mit anderen Einstellungen ein weiteres mal speichern willst. Die Berechnung deines Fotos kann unter Umständen mehrere Minuten dauern, wenn deine Bearbeitung sehr umfangreich ist, das Bild sehr groß ist und du auch rechenintensive Werkzeuge, wie zum Beispiel die Rauschminderung, verwendet hast.

## Das war schon mal viel Stoff, Danke Dir, dass du bis hierhin durchgehalten hast!

Wir, die an diesem Handbuch schreiben, bemühen uns, Dich optimal zu unterstützen. Das ist sehr mühsam für uns. Und es ist dann schade und aufwändig, Fragen in Foren zu beantworten, die nur daraus resultieren, unsere Arbeit am Handbuch links liegen gelassen zu haben. Du weißt, wie man sich gut informiert. Und Du bist deshalb besonders gern von uns eingeladen, Dich bei wichtigen Fragen in Foren oder bei erfahrenen Anwendern zu melden, die RawTherapee zu einem Teil ihrer Webpräsenz gemacht haben.

Wir wünschen Dir nun viel Spaß und Erfolg und immer eine Portion Experimentierfreude!

## PS: Hardware für RawTherapee

Für einen Einsteiger-Artikel seien ausnahmsweise noch einige Randinformationen erlaubt:
Falls Du mit RawTherapee allgemein in die Bearbeitung von Deinen Fotos einsteigst, weil Dir die Kamera-JPEGs nicht (mehr) so richtig gut erscheinen, stellt sich schnell die Frage nach der passenden Hardware.
Hier ein paar grundlegende Infos:

### Rechenleistung

Wie schon oben beschrieben, werden die Algorithmen der Transformationswerkzeuge in der Vorschau etwas *gröber* berechnet, als im fertigen Bild. Und auch die Werkzeuge unter *Details* werden nur für den am Bildschirm dargestellten Bildausschnitt bei 100%-Darstellung und darüber berechnet. Das führt dazu, dass die Bearbeitung auch schon mit aktuellen Mittelklasse-Laptops absolut zufriedenstellend klappt. Dazu kommt, dass Du Deine Bilder nicht sofort in die Endberechnung schicken musst, sondern sie in die Warteschlange legen kannst, um erst mal mit den nächsten Bildern weiterzuarbeiten. Damit kannst Du auch bei niedriger Rechenleistung hunderte Bilder an einem Abend bearbeiten.

Aber Du wirst sie in dieser Menge nicht so fix auf soziale Medien, Webspace oder dergleichen hochladen können. Einige Algorithmen, vor allem auch die sehr zu empfehlende Rauschminderung, beansprucht am Ende, wenn das endgültige Bild berechnet werden soll, ein gewisses Maß an
Rechenkapazität. Wenn Du darauf angewiesen bist, hin und wieder recht kurzfristig in der Nacht nach einem Event schon Deine Bilder *zu liefern*, dann wirst Du mit dem oben genannten Laptop keine Freude haben. RawTherapee nutzt Hyperthreading sehr gut. Aber lass Dir gesagt
sein, dass auch ein schneller und gut gekühlter Prozessor mit 4 Kernen und Hyperthreading an einem Bild schnell mal mehr als eine Minute rechnet. 120 Bilder zu einer Minute sind schon 2 Stunden Rechenzeit! -

Also: Nutze die Warteschlange und lass den Rechner dann über Nacht heiß durchlaufen. Und wenn Du sehr viel fixer sein willst, dann investiere,
was das Sparbuch her gibt. Aber, dann lasse Dir Deine Bilder auch bezahlen. ;-)

Arbeitsspeicher: RawTherapee läuft auch mit 32-Bit Betriebssystem und/oder 4 GB RAM. Aber bitte lies dir [Was tun bei Speicherplatzmangel?](The_Floating_Point_Engine/#Was_tun_bei_Speichmangel?) durch.

### Monitor

Größe: Du wirst schnell merken: Je größer der Monitor und je geringer der Pixelabstand, um so effizienter kannst Du arbeiten. RawTherapee auf einem 4k-Monitor macht Freude. Auch unter Win7, dass nicht gerade dafür bekannt ist, solche Monitore mit Schriftskalierung usw. besonders gut zu unterstützen. RawTherapee darauf macht richtig Freude und steigert die Effizienz. Wenn Du einen Laptop nutzt, ist ein Zweitbildschirm dieser Klasse durchaus zu empfehlen.

Qualität: Falls Du Deine Bilder ausschließlich im Web Leuten präsentierst, die sie sich auch nur auf dem Monitor ansehen, dann lehne Dich zurück: Dein Monitor kann noch so gut Farben darstellen, und so gut das natürlich für die Bildentwicklung erst mal ist, die Leute, die Deine Bilder betrachten, machen mit ihren unabgeglichenen Bildschirmen, es wird sich wohl überwiegend um Smartphones handeln, alles zur Kracke.
Im Gegenteil: Wenn Du an einem abgeglichenen Monitor die Bilder justierst, kommen sie auf den fast immer viel zu blau eingestellten Geräten Deiner Betrachter generell viel kälter als gewollt. In dem Fall nimm irgend einen Monitor, lasse ihn auch vergleichbar kühl eingestellt und arbeite damit. Das reicht!

Aber, nicht nur, wenn Du Perfektionist bist, sondern Deine Bilder Du selbst oder Deine Nutzer auf Papier bringen wollen, dann solltest Du Dir Zeit nehmen und Dich mit Farbprofilen beschäftigen. Beim Kauf von Hardware gibt es dabei zwei Level:

- Monitore aus dem Consumer-Bereich, für die Du ein Farbprofil-File aus guter Quelle bekommen kannst.
- Monitore, die speziell für Bildbearbeitung hergestellt werden.

Letztere sind natürlich teurer. Aber bei denen kannst Du Dich auch beruhigt zurücklehnen, wenn Du einen lukrativen Auftrag bekommst, wo höchste Qualität gefordert wird. Und wenn Du schon alle Kameras und Objektive gekauft hast, die es gibt, und Deine Bessere Hälfte auch nichts gegen weitere Investionen hat, dann schlage zu, wenn Du z.B. einen guten Eizo bekommen kannst. Oder Du bist Profi. Dann weißt Du selbst genau, was Du brauchst und investieren willst.

Wir anderen, die für's Hobby mit begrenztem Budget rechnen müssen, kommen mit einigen Consumer-Modellen auch sehr gut hin, solange wir ein Farbprofilfile mit den dazu gehörenden Einstellungen des Monitors bekommen. (Zum Profil gehören immer auch die Einstellwerte für Helligkeit, Kontrast, Farbe, Gamma.) Das ist aber auch das Problem:
Solche Profile werden in diesem Segment selten vom Hersteller bereitgestellt. In diesem Fall schau mal <a href="http://www.tftcentral.co.uk/articles/icc_profiles.htm" target="_blank" rel="noopener noreferrer"> [auf dieser Seite] </a> vorbei.

Hier werden unzählige Profile veröffentlich. Dieses Archiv ist sehr bekannt und sehr häufig verlinkt. Falls Du hier für Deinen Wunschmonitor ein Profil findest, ist das schon mal nicht schlecht. Aber: Es gibt keine Gewähr. Da die Profile von Nutzern zugearbeitet werden, gibt es keine Garantie dafür, dass ein Profil professionell erstellt wurde und tatsächlich stimmt. Außerdem bleibt es jedem Hersteller überlassen, von heute auf morgen in ein und das selbe Gehäuse ein neues Display zu versenken. Aber betrachten wir die Sache anders herum: Für Monitore, die Du in diesem Archiv nicht findest, wirst Du kaum die Chance haben, überhaupt ein Profil zu bekommen, solange Du Dir nicht selbst das notwendige Messequipment zulegst, um Deinen Monitor zu kalibrieren.
Letztes ist jedoch auch nicht zu empfehlen, da deren Messfehler trotz Preise von einigen hundert Euro zum Teil erheblich sind. - Statt in Consumer-Monitor plus Messequipment zu investieren, kaufe in so einem Budget-Fall lieber einen von Haus aus abgeglichenen Monitor!

### Backup-Medium

Ein Punkt, der gern vergessen wird. Du bist vielleicht nicht nur im Besitz einmaliger Fotos. Du steckst auch unheimlich viel Zeit in die Entwicklung mit RawTherapee. Eine externe Festplatte ist das Mindeste, was Du generell nach getaner Arbeit als Backupmedium anschließt und das Backup startest.
Empfehlenswert wäre aber ein NAS als Backupmedium, das Du über Dein Home-Netzwerk erreichst, z.B. per WLAN, ohne extra etwas anstöpseln zu müssen.

#### Timeline

Um jetzt auch noch das Backup mit *Timeline* laufen zu haben, ohne es ständig mit der Hand zu starten, nutze passende Software. Mit 'nem Mac gibt es schon lange eine gute Backupmöglichkeit mit Timeline. Auch mit anderen Betriebsystemen musst Du nicht darauf verzichten. Weißt Du was das ist, ein Timeline-Backup? Wenn Du das nicht hast und nur den aktuellen Stand auf dem Backupmedium abgleichst, sind von Dir gelöschte Files am gleichen Abend auch auf Deinem Backup-Medium gelöscht. Mit Timeline bleiben sie eine gewisse Zeit dort noch erhalte. Auch frühere Arbeitsstände findest Du einige Zeit später nochmal wieder und kannst sie restaurieren. Völlig ohne Wertung, nur als Anregung, was so möglich
ist: Genie Timeline (für Windows), Synology Cloud Backup (beim Einsatz eines Synology-NAS). Bitte recherchiere selbst, was für Dich optimal geeignet ist. Gar kein Backup ist die (kostenmäßig und zeitmäßig) optimale Lösung. Aber Du solltest dann absolut nicht zu Wehmut neigen. ;-)
