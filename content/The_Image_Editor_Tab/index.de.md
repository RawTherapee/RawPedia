---
title: The Image Editor Tab de
contributors:
  - Fherb
  - marter001
---

Todo-List / State:

- Translation: completed, but see discussion
- Content completely cleared: questions: see discussion
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Die Registerkarte Editor

<figure>
<img src="/images/rt-5-misty1.jpg"
title="Rt-5-misty1.jpg" />
<figcaption>Rt-5-misty1.jpg</figcaption>
</figure>


Die Registerkarte *Editor* ist der Ort in RawTherapee, an dem die einzelnen Bilder bearbeitet werden. Standardmäßig ist RawTherapee im Einreiter-Modus mit vertikalen Arbeitsbereichen rechts und links voreingestellt, oben verläuft der *Filmstreifen* (s. unten). Diese Einstellung ist sehr speichereffizient. In den Einstellungen kannst Du auch die praktische Ansicht *Multi-Reitermodus* auswählen, die jedoch in Abhängigkeit von der Bildgröße mehr RAM benötigt, und der *Filmstreifen* ist nicht nutzbar. Wir empfehlen, sich bei der Einarbeitung erst mal auf den Einreiter-Modus entsprechend der Standardeinstellung festzulegen.

## Der Vorschaubereich

Der zentrale Bereich auf dem Bildschirm ist der Vorschau des Bildes vorbehalten. Dieses Vorschaubild wird aus dem Raw-Bild (oder dem Ursprungsbild in einem alternativen Format) entsprechend der aktuellen Einstellungen der Werkzeuge berechnet. Wenn Du ein Bild lädst und es bereits ein Sidecar-File besitzt wird dieses ebenfalls geladen, die Werkzeuge entsprechend eingestellt und dementsprechend der Zustand bei der letzten Speicherung angezeigt. Wenn Du ein Raw-Foto erstmalig wählst, wird ein Profil angewendet, dass Du unter "*Einstellungen ->
Bildbearbeitung -> Standard-Bildbearbeitungsparameter -> Für Raw-Dateien*" einstellen kannst. Wer möglichst keine Voreinstellungen haben will, wählt dort in den Einstellungen das aus, was für Nicht-Raw-Bilder ("*Bilddateien*") vorgegeben ist: *(Neutral)*. Oder wähle eins der mitgelieferten Profile.

Beachte: Die Effekte einiger Werkzeuge sind nur in der 1:1 (100%)-Darstellung (und darüber) richtig sichtbar. Diese Werkzeuge werden grundsätzlich in der Zeile der Werkzeugüberschrift ganz rechts aussen mit **1:1** markiert. So sieht das aus: ![Zoom 1:1](/images/one-to-one-small.png "Zoom 1:1") - Unscheinbar, aber wichtig.

Das Bild, das du in der Vorschau siehst wird dem Farbraum des Arbeitsprofils entnommen und in das Monitorprofil umgewandelt, falls ein Monitorprofil geladen ist. Andernfalls wird sRGB als Standard voreingestellt. Diese Vorgaben berücksichtigten hingegen nicht die [Ausgabeprofil](color_management#ausgabeprofil)-Einstellung des Werkzeugs [Farbmanagement](color_management).

### Heh! Mein Raw-Bild sieht anders aus als das Kamera-JPEG

Wenn Du erstmals ein Raw-Foto im Editor öffnest, wirst du dich vielleicht heftig wundern, dass es sehr viel schlechter als das Kamera-JPEG oder das Vorschaubild aussieht. Möglicherweise auch im Vergleich mit anderer Software, mit der Du gerade RawTherapee vergleichst, sieht Dein Raw bei RawTherapee ganz schlimm aus. Was ist hier passiert? Ist RawTherapee kaputt, verrückt oder dein Bild hinüber?

**Nichts dergleichen!** Solange Du kein spezielles Profil für unbearbeitete Raw-Fotos in den "Einstellungen" zur Anwendung mit erstmals geöffneten Raw-Fotos voreingestellt hast (was nicht wirklich erforderlich ist), dann muss das Raw so aussehen. Ein Raw ist wie ein unbearbeitetes Negativ analoger Filme. Dem fehlen einfach ein paar Prozessschritte, die die Kamera in ihrem JPEG bereits erledigt hat. Und da dieses Kamera-JPEG auch in geringer Auflösung in dein Raw-File eingebettet wird, sieht auch das Vorschaubild ganz anders (häufig im ersten Moment sogar besser) aus.

Dinge, die du in diesem Zusammenhang wissen solltest:

  - Deine Kamera zeigt Dir nie die Originaldaten, wie sie der Sensor tatsächlich sieht. Die *rohen* (raw) Daten des Sensors werden zwar nach wenigen grundsätzlichen Schritten (z.B. Zeilenrauschfilterung) in das Raw-File geschrieben, die Kamera verarbeitet das Bild aber weiter bis zu dem Punkt, wo sie es als JPEG abspeichern würde. In Raw-Dateien speichert sie es auch ab, zumeist mit verringerter Auflösung, nur zum Zwecke der Vorschau. Aber nicht selten mit der ganzen Vorverarbeitung, die sie auch dem voll aufgelöstem Kamera-JPEG zugesteht. Auch die Bildvorschau und das Histogramm, was die Kamera anzeigt, resultieren normalerweise aus allen Prozessschritten bis zur Abspeicherung des Kamera-JPEGs. Das ist auch gut so. Bei der Aufnahme willst Du ja tatsächlich sehen, was Du mit dem Bild anfangen kannst. Würdest Du nur die Rohdaten sehen, wärst Du vielleicht mit den meisten Bildern unzufrieden bzw. würdest daraufhin Kameraeinstellungen wählen, die ungeeignet sind. Selbst wenn Du alle Kameraeinstellungen so wählst, dass du hoffst, die Kamera würde ihrerseits nichts dazuinterpretieren, entspricht das, was dir die Kamera zeigt bei weitem nicht dem, was im Raw steckt. Die Ingenieure der Kamerahersteller verwenden sehr viel Grips, um aus dem Raw, dem reinen Sensorabbild, mittels einer Reihe von Prozessschritten ein gutes Foto zu entwickeln. Tonwertkurven, Sättigungskorrektur, Schärfen, Rauschunterdrückung... Aber auch  Objektivkorrektur für Objektive des Kameraherstellers und ganz viele weitere Dinge werden in die Bildverarbeitung der Kamera eingebaut.
    Teilweise werden Belichtungsreihen aufgenommen oder bei modernsten Sensoren auch Informationen gewonnen, die eine gewisse HDR-Verarbeitung zulassen. Wir brauchen hier gar nicht noch weiter in die Details zu gehen: Das, was die Kamera zeigt und ins JPEG speichert ist erheblich vorverarbeitet. Im RAW-File hingegen stehen nur Sensordaten mit den geringsten Vorverarbeitungen, wenn überhaupt (zumindest das Zeilenrauschen wird bestmöglich entfernt, weil der Sensor dafür spezielle Pixel im Randbereich hat).
  - RawTherapee also das noch unbearbeitete Raw-Foto.
 
    Aber kein Problem. All die kamera-automatischen Bildanpassungen können wir mit RawTherapee in einer viel höheren Qualität nachholen und noch weiter verbessern. Jedes Raw-File enthält ein vorverarbeitetes JPEG der Kamera. Normalerweise ist es aus Platzgründen deutlich in der Auflösung verkleinert. Es gibt aber auch Kameras, wo voll aufgelöste JPEGs dabei sind oder JPEGs in mehreren Auflösungsstufen. Wenn du so ein Raw-File in einer anderen Software öffnest, kann es durchaus sein, dass sie dir gar nicht das Raw-Bild, sondern eins der JPEGs anzeigen. Bei den bekannten Bildwerkzeugen IrfanView und XnView ist das so. Aber auch bei Gwenview, Geegie, Eye, F-Spot, Shotwell und gThumb. Das ist auch kein Wunder: Diese Programme sind nicht dazu gedacht ein Raw zu einem fertigen Bild zu entwickeln.

  - Achtung: Falls Du im Aufnahmemodus mit der Einstellung "Raw+JPEG" fotografierst, muss das im Raw eingebettete JPEG nicht das Gleiche sein, wie das separat abgespeicherte JPEG. Um das Raw klein zu halten kann das darin eingebettete JPEG durchaus mit höherer Komprimierung, also geringerer Qualität enthalten sein. Oder die Entwickler haben sich etwas anderes Sinnvolles gedacht. Das eingebettete JPEG soll immer nur eine Hilfe sein, z.B. bei der Vorauswahl. Nie das vollwertig entwickelte Bild. 

    Falls Du für ein möglicherweise vereinfachtest Publishing über Nacht in soziale Medien ein Kamera-JPEG verwenden willst, um aber parallel dazu mit mehr Zeit auch noch richtig entwickelte Fotos mittels Raw zu machen, dann wähle unbedingt die Methode "Raw+JPEG" in der Kamera. Die im Raw eingebetteten JPEGs sind nicht uneingeschränkt für die weitere Nutzung gedacht. Auch, wenn das, wie oben beschrieben, zuerst den Anschein macht.

  - Die meisten Raw-Entwickler-Programe, also Programme, die tatsächlich die Raw-Daten einlesen und verarbeiten, führen schon mit dem Einlesen einige grundsätzliche Bearbeitungsschritte aus. In diesem Programmen siehst du auch am Anfang nie das tatsächliche, unbearbeitete Raw-Bild. Adobe Lightroom ist so ein Beispiel. Vergleichst Du nun das bei RawTherapee neutral eingelesene Bild mit einem dieser Programme, darfst Du Dich nicht wundern, wenn Unterschiede zu sehen sind. Das, was wir verhindern wollen, dass die Kamera schon unter irgend welchen Annahmen Vorverareitungsschritte ausführt, machen diese Programm im Nachhinein schon beim Einlesen.

  - RawTherapee hingegen ist so gestaltet, dass es in der Vorschau das reale Raw-Bild anzeigt und dir den Weg offen lässt das Bild nach deinen Wünschen zu verarbeiten. Wenn Du das "Neutral" Profil wählst, wird nur das [Demosaicing](demosaicing) ausgeführt und der Weißabgleich der Kamera verwendet. Es werden keine weiteren Modifikationen durchgeführt. Wenn du das Raw-Bild vor dem Demosacing sehehen willst, stelle beim Democaicing-Verfahren die Auswahl auf *none*. Damit du alternativ auch mit ästhetisch ansprechenderen Ausgangsparametern beginnen kannst, wird zu RawTherapee eine Sammlung von Profilen mitgeliefert. Nach der Installation ist ein Standardprofil *Default* für die Bearbeitung von Raw-Bildern voreingestellt. Es werden auch die Profile *Default ISO Medium* und *Default ISO High* mitgeliefert, die sich als Ausgangpunkt für mäßig oder stark verrauschte Bilder eignen.

Keines der mitgelieferten Profile, zumindest nicht in den bisherigen RawTherapee-Versionen, sind so gestaltet, dass sie den Look des Kamera-JPEGs imitieren. Warum nicht? Jede Kamera ist anders. Die Bildqualität einer Kamera mit ISO 1600 kann sehr viel mehr verrauscht sein, als die einer anderen Kamera mit geicher ISO-Einstellung. Auch verhält sich die eine Kamera bei der Darstellung der Farben anders als eine Andere. Selbst die gleiche Kamera kann sich unter verschiedenen Einstellungen anders verhalten. Wenn wir solche Profile anbieten würden,  würden wir Zugriff auf Raw-Files jedes Kamera-Modells benötigen, oft sogar mehrere Raw-Files für verschiedene Aufnahmeeinstellungen des gleichen Kameramodells. Und natürlich auch unzählige <a href="https://de.wikipedia.org/wiki/Personenstunde" target="_blank" rel="noopener noreferrer">Personenstunden</a>. Das mag vom Aufwand her für eine ganze Community möglich sein. Aber nicht für ein kleines Team. Und zu welchem Zweck, wenn RawTherapee letztlich den gleichen Look erzielen würde, wie das JPEG aus der Kamera? Es ist viel vernünftiger, dass du die Verwendung der leistungsstarken Werkzeuge in RawTherapee kennen lernst, um das Beste aus deinen Aufnahmen zu holen und dabei den Kamera-Look zu übertreffen.

Im September 2015 begannen wir unter Verwendung von <a href="https://torger.se/anders/dcamprof.html" target="_blank" rel="noopener noreferrrer">DCamProf</a> DCP Kamera-Profile mitzuliefern, die eine <a  href="https://torger.se/anders/dcamprof.html#tone_curves" target="blank" rel="noopener noreferrer">[optionale Tone-Kurve]</a>
enthalten. Diese Kurve wird entsprechend der Adobe Camera Raw Standard-Filmkurve modelliert, deren Ergebnis einen Kamera-ähnlichen Look liefert. Der Grund dafür ist, dass damit ein guter, dynamischer Startpunkt machbar ist (im Gegensatz zum flachen Bildeindruck mit dem *Neutral*-Profil), ohne dabei die [Automatische Belichtungseinstellung](Exposure#Automatische_Belichtungseinstellung) oder irgend ein anderes Werkzeug verwendet zu haben. Und, es ist völlig optional. Weiteres dazu findest Du im Artikel [Eingangsfarbprofil](color_management#eingangsfarbprofil).
Falls wir für deine Kamera ein DCP mit einer solchen Tonwertkurve mitliefern, dann ist die Checkbox *Farbe \> Farbmanagement \> Eingangsfarbprofil \> DCP \> Tonwertkurve*, einschaltbar. Wählst du *Neutral* als Profil, dann wird diese Tonwertkurve wieder abgeschaltet.

Während das Eingangsfarbprofil schon in einer frühen Stufe der [Prozesskette](toolchain_pipeline) verarbeitet wird, wird die DCP-Tonwertkurve erst nach dem Belichtungswerkzeug angewendet.

Du kannst dir ein Prozess-Profil selbst erstellen, dass ideal auf deine Kamera-Linsen-Kombination zugeschnitten ist und es als Standard für RawTherapee einstellen. Wie das funktioniert, findest du im Artikel [Erstellung von Prozess-Profilen für die allgemeine Verwendung](Creating_processing_profiles_for_general_use).

### Vorschau-Arten

Zusätzlich zur ganz normalen Vorschau unterstützt RawTherapee eine ganze Reihe anderer Vorschau-Arten, die dir beim Bearbeiten des Fotos helfen können. Diese Vorschau-Arten können mittels kleiner Buttons in der oberen Werkzeugleiste des Editors gesteuert werden. Oder du verwendest alternativ [Tastatur-Kürzel](keyboard_shortcuts). Es ist nur möglich, zu einem Zeitpunkt immer jeweils genau eine Vorschau-Art auszuwählen.
Die folgenden Vorschau-Arten werden unterstützt:

- nur Rot-Kanal,
- nur Grün-Kanal,
- nur Blau-Kanal,
- nur Helligkeits-Kanal, berechnet zu 0.299\*R + 0.587\*G + 0.114\*B,
- Fokusmaske (zeigt die Bereiche, die gut fokussiert sind)

<div>

<table cols=4 border=1 cellspacing=1 bgcolor=#fefefe>
<caption align="left">* Die Vorschau geht zurück in die Standarddarstellung, wenn die aktive Auswahl deaktiviert wird.</caption>

<thead>
<tr class="header">
<th><p>Bezeichnung</p></th>
<th><p>Tastatur-Kürzel</p></th>
<th><p>Button</p></th>
<th><p>Vorschau-Art</p></th>
</thead>

<tbody>
<tr class="odd">
<td style="padding:10px;"><p>Normal*</p></td>
<td></td>
<td><figure>
<img src="/images/preview_mode_1_regular.png" max-width:100% title="Image:preview mode 1 regular.png"/>
</figure>
</td>
<td><figure>
<img src="/images/preview_1_regular.jpg" height="60" title="Image:preview mode 1 regular.jpg">
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>nur Rot-Kanal</p></td>
<td style="text-align: center;"><p>r</p></td>
<td><figure>
<img src="/images/preview_mode_2_red.png" title="Image:preview mode 2 red.png" />
</figure></td>
<td><figure>
<img src="/images/preview_2_red.jpg" height="60" title="preview_2_red.jpg">
</figure></td>
</tr>
<tr class="odd">
<td style="padding:10px;"><p>nur Grün-Kanal</p></td>
<td style="text-align: center;"><p>g</p></td>
<td><figure>
<img src="/images/preview_mode_3_green.png" title="Image:preview mode 3 green.png" />
</figure></td>
<td><figure>
<img src="/images/preview_3_green.jpg" height="60" title="Image:preview 3 green.jpg">
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>nur Blau-Kanal</p></td>
<td style="text-align: center;"><p>b</p></td>
<td><figure>
<img src="/images/preview_mode_4_blue.png" title="Image:preview mode 4 blue.png" />
</figure></td>
<td><figure>
<img src="/images/preview_4_blue.jpg" height="60" title="Image:preview 4 blue.jpg">
</figure></td>
</tr>
<tr class="odd">
<td style="padding:10px;"><p>nur Helligkeits-Kanal</p></td>
<td style="text-align: center;"><p>v</p></td>
<td><figure>
<img src="/images/preview_mode_5_luminance.png" title="Image:preview mode 5 luminance.png" />
</figure></td>
<td><figure>
<img src="/images/preview_5_luminosity.jpg" height="60" title="Image:preview 5 luminosity.jpg">
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>Fokusmaske</p></td>
<td style="text-align: center;"><p>Shift+f</p></td>
<td><figure>
<img src="/images/preview_mode_6_focus.png" title="Image:preview mode 6 focus.png" />
</figure></td>
<td><figure>
<img src="/images/preview_6_focus.jpg" height="60" title="Image:preview 6 focus.jpg">
</figure></td>
</tr>
<caption align="left">* Die Vorschau geht zurück in die Standarddarstellung, wenn die aktive Auswahl deaktiviert wird.</caption>
</tbody>
</table>
</div>
<div>
<br>

#### Rot-, Grün-, Blau- und Helligkeits-Vorschau
Die Vorschau der einzelnen Farbkanäle ist in Situationen sinnvoll, wo du RGB-Kurven anpasst, eine Umwandlung in Schwarz-Weiß mit dem Kanalmixer planst, Bildrauschen auf die geeignete Entfernungsmethode untersuchst usw. Die Anzeige des Helligkeitskanals ist unter anderem hilfreich, wenn du ein Bild unmittelbar in Schwarz-Weiß darstellen willst, ohne die dazu notwendigen Entwicklungsparameter einzustellen, um z.B. vorab zu sehen, welcher Kanal aus ästhetischen Gründen übersteuert sein darf.
 
Wenn die Anzeigen für zu helle oder zu dunkle Bildbereich in diesen Vorschauarten eingeschaltet sind, werden zu dunkle Bereiche blau und zu helle Bereich rot dargestellt. Wie in der normalen Ansicht auch, ist die Helligkeit der Farbmarkierung Ausdruck für die Stärke der Unter- oder Übersteuerung.

#### Fokusmaske

<figure>
<img src="/images/preview_6_focus_2.jpg" width="50%" title="Die Fokusmaske zeigt die Fokus-Ebene">
</figure>

Die Fokusmaske dient zur Hervorhebung der Bereich im Bild, die scharf sind. Sie arbeitet auf solchen Bildern genauer, die eine geringe Schärfentiefe und geringes Rauschen besitzen. Ebenso bei Einsatz einer höheren Auflösung in der Vorschau. Bei Bildern mit hohem Bildrauschen empfiehlt es sich jedoch, die Auflösung der Vorschau in den Bereich 10-30% zu stellen. Solange die Fokusmaske eingeschaltet ist, dauert der Bildaufbau der Vorschau etwas länger.

Die aktuelle Implementierung dieser Funktion analysiert das Vorschaubild, das von der Originalgröße ausgehend skaliert ist. Durch das Skalieren zu geringerer Auflösung hin reduziert sich das Rauschen, was zur Identifikation tatsächlich scharfer Details führt, anstatt das Rauschen hervorzuheben, das ebenfalls eine Mikrostruktur besitzt. Gleichzeitig können größere Details im Bild beim Herunterskalieren aber auch sogenannte <a href="https://de.wikipedia.org/wiki/Alias-Effekt" target="_blank" ref="noopener noreferrer"> Aliasing-Artefakte </a> ausbilden, die dann falsch bewertet werden. Um Fehleinschätzungen zu reduzieren ist es deshalb in vielen Fällen sinnvoll, die Fokusmaske mit unterschiedlichen Zoom-Stufen zu betrachten.

**Warnung**: Prüfe Bilder deshalb zwei mal, bevor du dich nur an Hand der Fokusmaske entscheidest, sie zu löschen.

### Hintergrundfarbe der Vorschau

Für eine bessere Visualisierung des in der Vorschau dargestellten Bildbereiches und zur Erleichterung der Arbeit kann die Farbe des Bereiches, in den die Vorschau eingeschlossen ist, angepasst werden. Drei in der oberen Symbolleiste dicht übereinander liegende schmale Balken kennzeichnen 3 Buttons, mit denen sich der Hintergrund umschalten lässt:

<div>
<table cols=5 border=1 bgcolor="fefefe">
<thead>
<tr class="header">
<th><p>Preview<br />Hintergrund</p></th>
<th><p>Tastatur-Kürzel</p></th>
<th><p>Button</p></th>
<th><p>Vorschau Hintergrund<br />und Bildbeschnitt-Ansicht</p></th>
<th><p>Beschreibung</p></th>
</tr>
</thead>

<tbody>
<tr class="odd">
<td><p>basierend auf dem Oberflächendesign</p></td>
<td style="text-align: center;"><p>8</p></td>
<td><figure><img src="/images/previewback_theme.jpg" title="Image:previewback_theme.jpg"></figure></td>
<td><figure><img src="/images/previewback_flower_theme.png" title="Previewback_flower_theme.png" width="180"></figure></td>
<td><p>Die beschnittene Fläche eines Bildes wird mit einer auf das Design der Oberfläche abgestimmten Farbe maskiert.<br />Das Aussehen der Maske und die Transparenz lässt sich unter "<em>Einstellungen &gt; Allgemein &gt; Oberflächendesign &gt; Farbe/Transparenz für Schnittmaske</em>" einstellen.</p></td>
</tr>
<tr class="even">
<td><p>Schwarz</p></td>
<td style="text-align: center;"><p>9</p></td>
<td> <figure><img src="/images/previewback_black.jpg" title="Image:Previewback_black.jpg"></figure></td>
<td><figure><img src="/images/previewback_flower_white.png" width="180" title="Previewback_flower_white.png"> </figure> </td>
<td><p>Die beschnittene Fläche wird schwarz dargestellt.</p></td>
</tr>

<tr class="odd">
<td><p>Weiß</p></td>
<td style="text-align: center;"><p>0</p></td>
<td><figure><img src="/images/Previewback_white.jpg" title="Image:Previewback_white.jpg"></figure></td>
<td><figure><img src="/images/Previewback_flower_black.png" width="180" title="Previewback_flower_black.png"></figure></td>
<td><p>Die beschnittene Fläche wird weiß dargestellt.</p></td>
</tr>

</tbody>
</table>

</div>

### Detailfenster

Der *Neues Detailfenster öffnen*-Button ![Image:new-detail-window.png](new-detail-window.png "Image:new-detail-window.png") unterhalb der Vorschau neben den Zoom-Buttons öffnet ein kleines Ansichtsfenster (auch mehrere gleichzeitig) einstellbarer Größe und einstellbarem Zooms über der Hauptansicht. Das ermöglicht dir, mit einem geringen Zoom in der Hauptansicht zu arbeiten, während du interessierende Bereich gleichzeitig mit 100% Auflösung (oder auch mehr) überprüfen kannst. Die Lage des Ausschnitts kannst Du mit der Maus im Vorschaubild verschieben.

Der Vorteil liegt nicht nur bei Nutzern mit langsameren Rechnern darin, auf häufiges hinein- und herauszoomen vor allem dann verzichten zu können, wenn Werkzeuge aktiviert sind, die die Zoomwechsel in der Vorschau durch viel Rechenaufwand ausbremsen. Dazu gehört zum Beispiel die Rauschminderung. Sie und einige andere Werkzeuge werden nur in die Vorschauberechnung einbezogen, wenn mit 100% oder größer gearbeitet wird. Durch eine geringe Auflösung der Vorschau, aber einigen kleinen Detailfenstern, die auf 100% Zoom stehen, müssen diese rechenintensive Werkzeuge nur auf die kleinen Fenster angewendet werden. Das erlaubt dir, das große Vorschaubild zum Justieren von Einstellungen zu verwenden, die weniger rechenintensiv sind, zum Beispiel die Belichtung, wo es auch gar nicht darauf an kommt, Bilddetails zu prüfen. Während Du für das Schärfen oder die Rauschreduzierung die Voransicht so weit herausgezoomt stehen lässt und statt dessen direkt in den Detailansichten die Bildwirkung prüfst.
 
### Verzögerung des Auffrischens der Voransicht

Jede Änderung eines Werkzeugparameters sendet ein entsprechendes Signal zum Update der Voransicht. Stell Dir vor, es gäbe dafür keine Verzögerungszeit, wenn Du einen Regler, zum Beispiel für die Belichtung, von 0.0 auf +0.60 schiebst. Das Signal zur Neuberechnung des Vorschaubildes würde mit jedem minimalen Schritt, also 0.01, 0.02, ... 0.59, 0.60, gesendet und das Vorschaubild 60 mal neu berechnet, während Du den Regler verschiebst. Die Neuberechnung würde viel länger benötigen als Du zum Verschieben des Reglers. Noch extremer würde einige Werkzeuge mit noch deutlich höherem Rechenaufwand wirken. Um das zu verhindern, wird eine sehr kurze Verzögerungszeit gesetzt, während der Parameteränderungen eines Reglers ignoriert werden. Das Signal zur Neuberechnung der Voransicht wird erst gesendet, wenn für eine bestimmte Zeit keine Wertänderungen des Reglers registriert werden. Drehst (bzw. schiebst) du aber sehr langsam über längere Zeit an einem Regler, wäre auf diese Art gar keine Änderung der Vorschau zu sehen. Deshalb haben wir neben der Verzögerungszeit einen weiteren Parameter eingeführt, der vorgibt, wann trotz Reglerbewegung spätestens wieder ein Vorschaubild erzeugt wird.

Diese beiden Werte können nicht unter *Einstellungen* geändert werden. Wer sie eventuell aus Gründen der Performance seines Rechners ändern will, findet die Parameter im File *option* (ohne Dateiendung) im [Konfigurations-Ordner](file_paths#konfigurations-ordner) und kann sie dort mit einem Editor anpassen (File-Abschnitt *\[General\]*):

AdjusterMinDelay  
Standardwert = 100ms.

Das ist die Minmalzeit vor der Neuberechnung der Vorschau. Wird innerhalb dieser Zeit eine weitere Bedienung eines Reglers erfasst, wird das Bild noch nicht gezeichnet.

AdjusterMaxDelay  
Standardwert = 200ms.

Nach dieser Zeit wird jederzeit eine neue Vorschau berechnet, damit du auch bei langsamer Reglerbewegung die Wirkung in der Vorschau sehen kannst.

## Die linke Arbeitsfläche

Die linke Arbeitsfläche besteht aus den Komponenten

- Haupt-Histogramm (wahlweise auch auf der rechten Seite darstellbar) 
- Navigator
- Historie
- Schnappschuss

Die linke Arbeitsfläche kann temporär ausgeblendet werden (Button ![](/images/panel-to-left.png "Linkes Bedienfeld ein-/ausblenden")) bzw. [Tastatur-Kürzel](keyboard_shortcuts) **l** (das ist ein kleines L)).

### Haupt-Histogramm

![](/images/rt_histogram_crop_scale-off.png "Rt_histogram_crop_scale-off.png")
![](/images/rt_histogram_crop_scale-on.png "Rt_histogram_crop_scale-on.png")
![](/images/rt_histogram_raw.png "Rt_histogram_raw.png")
![](/images/rt_histogram_rgbindicator.png "Rt_histogram_rgbindicator.png")

Das Histogramm kann unter *Einstellungen \> Allgemein \> Layout \> Histogramm linksseitig* mit dem Wegnehmen des Häckchen auf die rechte Fensterseite verlegt werden.

Das Haupt-Histogramm kann die Kanäle 
- Rot ![](/images/histRedg.png "Image:histRed.png"),
- Grün ![](/images/histGreeng.png "Image:histGreen.png"),
- Blau ![](/images/histBlueg.png "Image:histBlue.png"),
- CIELab-<a href="https://de.wikipedia.org/wiki/Leuchtdichte" target="_blank" ref="noopener noreferrer">Leuchtdichte</a> ![](/images/histValueg.png "Image:histValue.png") und
- CIELab-<a href="https://de.wikipedia.org/wiki/Farbart" target="_blank" ref="noopener noreferrer">Farbart</a> ![](/images/histChrog.png "Image:histChro.png")

eines Fotos so darstellen, als würde es im aktuellen Zustand entwickelt werden (wenn ![Image:histRaw.png](/images/histRaw.png "Image:histRaw.png") abgeschaltet ist). Selbst der abschließende Beschnitt wird berücksichtigt und nur der verbleibende Bildteil für das Histogramm verwendet. Ob hierbei das Arbeitsprofil oder das Gamma-korrigierte Ausgabeprofil verwendet werden soll, legst Du unter *Einstellungen \> Allgemein \> Layout \> Das Arbeitsprofil zur Darstellung des Haupthistogramms verwenden* fest.

Benutze diese Informationen, um Übersteuerungen zu vermeiden. Falls das Raw-Bild keine Übersteuerungen enthält, aber das Endresultat, kannst du hier leicht die Kanäle identifizieren, die angepasst werden müssen und die notwendigen Schritte unternehmen, falls die Übersteuerungen unerwünscht sind.

Das Histogramm kann die Raw-Informationen vor irgendeiner Umwandlungen, wie Demosaicing, darstellen. Schalte dazu (![](/images/histRawg.png "Image:histRawg.png")) ein. Nutze diese Information um erkennen zu können, ob schon im Raw irgendwelche Übersteuerungen enthalten sind. Bis auf einige übersteuerte Lichter, die mit der Funktion *[Lichter rekonstruieren](Exposure#Lichter_rekonstruieren)* unter Umständen wieder hergestellt werden können, sind Übersteuerungen in den Raw-Informationen nicht wieder zu rekonstruieren.

Wenn im Bild große Flächen nahezu gleicher Helligkeit vorhanden sind, bildet sich im Histogramm für diesen Helligkeitswert eine sehr hohe Spitze ab, sodass die Histogrammkurven des Bildrestes bei einer linear skalierten y-Achse verschwindend klein dargestellt werden. Schalte in so einem Fall die Skalierung der y-Achse um (![](histFull.png "Image:histFull.png")). Ist die Skalierung "ein"-geschaltet werden höhere Werte im Vergleich zu kleinen Werten "nach unten" skaliert. So ist auch der Rest des Histogramms wieder gut sichtbar.

Du kannst den RGB-Indikator unterhalb des Histogramms anzeigen oder verbergen (![](/images/histBarg.png "Image:histBar.png")). Wenn Du mit dem Cursor über das Vorschaubild des Editors fährst, werden in diesem Indikator für das Pixel, das sich gerade genau unter dem Cursor befindet, die Orte der R-, G-, B- bzw. L-Werte im Histogramm markiert.

### Navigator

Der *Navigator* zeigt das gegenwärtig geöffnete Bild als Miniaturansicht an. Die Werte von RGB, HSV und Lab des genau unter dem Cursor befindlichen Pixels im Vorschaubild werden als Zahlen in 3 verschiedenen Formaten angezeigt. Jeder Klick in den Bereich mit den Werten RGB bzw. HSV schaltet das Format um:

- \[0-255\]
- \[0-1\]
- \[%\]

Für diese Werte gilt die gleiche Farbprofileinstellung, wie beim Haupt-Histogramm: *Einstellungen \> Allgemein \> Layout \> Das Arbeitsprofil zur Darstellung des Haupthistogramms verwenden*

<hr />

RawTherapee kann auch die echten raw photosite Werte anzeigen. Dazu muss die Navigator-Darstellung auf \[0-255\] stehen, das [Arbeitsprofil](Sidecar_Files_-_Processing_Profiles) auf "Neutral" gesetzt und das [Demosaicing](demosaicing) abgeschaltet werden

Damit sind die echten RAW-Werte nach der Schwarzlevel-Subtraktion sichtbar.

<hr />
<div style="clear: both">
</div>

### Historie

Unterhalb des *Navigators* folgt die Historie. Beginnend mit dem Laden des Bildes wird jede deiner Parameteränderungen in den Werkzeugen mitgeschrieben. Durch Anklicken kommst du also zu jedem Zwischenschritt zurück. Du kannst auch letzte Änderungen mit davor vergleichen, indem du die Historie wechselweise weiter oben und dann wieder weiter unten bzw. auf dem letzten Punkt anklickst. Setzt Du aber weiter oben mit der Arbeit fort, werden die nachfolgenden Schritte verworfen. Um mehrere Varianten fortzuentwickeln und später noch mal miteinander zu vergleichen, nutze das Schnappschuß-Feld darunter.

### Schnappschüsse

Unter der Historie kannst du mit Hilfe von *Schnappschüssen* Zwischenstände deiner Bearbeitung ablegen. Entweder, um sie mit den folgenden Bearbeitungsschritten wieder vergleichen zu können, zum Testen mehrere Bearbeitungsalternativen auf dem Weg zum finalen Bild, aber auch um grundsätzlich unterschiedliche Entwicklungen mit ein und dem selben Bild bis zu Ende zu führen.

Die aktuelle Historie wird im Schnappschuss nicht abgelegt. Nur der gesamte Parametersatz aller Werkzeuge. Rufst Du einen Schnappschuss wieder auf, dann ist das in der Historie ein neuer Bearbeitungsschritt. 

Wenn Du einen neuen Schnappschuß anlegst: Klicke gleich doppelt auf den automatisch erstellten Namen: Du kannst den Schnappschuss sinnvoll benennen.

Was derzeit noch nicht möglich ist: Der Schnappschuss lässt sich noch nicht mit im Sidecar-File zum Bild, also dem Prozessfile für die Bildverarbeitung, ablegen. Für die Zukunft ist das aber geplant. Denke also im Moment noch daran: Wenn Du das Bild im Editor wechselst, ist nicht nur die Historie weg, sondern auch die Schnappschüsse. Ebenso, wenn Du RawTherapee schließt.

Aber nichts, wo es keine Lösung gäbe: Du kannst die Schnappschüsse als einzelne Sidecarfiles speichern. Rufe dazu einen Schnappschuss auf (also anklicken). Die Werkzeuge werden entsprechend eingestellt. Du kannst nun diesen Zustand als Sidecar-(Prozess)-File speichern. Sinnvollerweise im Ordner des Bildes, wie das eigentliche, automatisch erzeugte Sidecar-File. Wie du das mit RawTherapee speicherst, wird hier im Handbuch gleich noch beschrieben: Ganz oben im rechten Bereich, noch über der Werkzeugkiste gibt es einen Button zum *Profil speichern*.

## Die rechte Arbeitsfläche

Wenn du dir das Histogramm nicht auf die rechte Arbeitsfläche gelegt hast, beginnt diese Spalte mit einer schmalen Leiste für die *Bearbeitungsprofile*.

Du kannst die gesamte rechte Bearbeitungsfläche zusammen mit dem Werkzeugkasten zeitweilig ausblenden. Nutze dazu den kleine Button ![](/images/panel-to-right.png "Rechtes Bedienfeld ein-/ausblenden")
oder das [Tastatur-Kürzel](keyboard_shortcuts) **Alt+l** (das ist ein kleines L).

### Bearbeitungsprofile

Alles, was Du mit den Werkzeugen einstellst, bildet zusammen das *Bearbeitungsprofil*, das zur Bildentwicklung als Setting verwendet wird. Es wird auch [Prozess-Profil bzw. Sidecar-File](Sidecar_Files_-_Processing_Profiles) genannt. Letztere Bezeichnung kommt daher, dass das Profil normalerweise
unmittelbar *neben* dem Bild im gleichen Ordner abgelegt wird und auch von RawTherapee automatisch als das Bearbeitungsprofil des betreffenden Bildes erkannt wird, wenn du ein Bild erneut lädts. Es gibt vor allem aber auch einige mitgelieferte Profile, die Du über das Auswahlfeld dieses Bereiches laden kannst. Der Sinn, die Bearbeitungseinstellungen neben dem Bild als eigenes File abzulegen, ist, dass RawTherapee nichts am Originalbild ändern soll. Also nicht nur inhaltlich, sondern auch nichts an den Metadaten. Um nun aber ohne Datenbank auszukommen, also nicht, wie das andere Softwarehersteller machen, gibt es diese Lösung mit den Sidecar-Files. Für ein paar mehr Informationen lies [Sidecar-Files - Bearbeitungsprofile](Sidecar_Files_-_Processing_Profiles).

#### *Teilprofile - Umschalter für das Verhalten beim Laden*

**Wichtig:** Dieser kleine Umschalter verändert das Verhalten von RawTherapee beim Laden von Profilen sehr wesentlich. Egal ob mitgelieferte Profile, Sidecar-Files, Profile aus der Zwischenablage usw.

Ein Bearbeitungsprofil selbst muss beim Speichern, wie beim Laden, nicht unbedingt sämtliche Parameter aller Werkzeuge enthalten. Das hat folgende Ursachen:

- Wenn Du den aktuellen Parametersatz aller Werkzeuge als
  Bearbeitungsprofil speicherst bzw. in die dafür vorgesehene
  Zwischenablage legst und dabei die Strg-Tast drückst (s. unten) kannst
  Du auswählen, ob Du das gesamte Setting ablegen willst oder nur
  bestimmte Teile davon.
- Wenn Du ein selbst abgespeichertes Bearbeitungsprofil für ein Bild
  lädst, kannst Du ebenfalls die Strg-Taste drücken und vorher
  auswählen, welche Bestandteile des Profils Du übernehmen möchtest.
- Mitgelieferte Profile, die nur bestimmte Wirkungen erzeugen sollen,
  umfassen ebenfalls kein vollständiges Setting.
- Du lädst ein Bearbeitungsprofil, dass Du in einer früheren
  RawTherapee-Version erstellt hast (als Sidecar-File zu irgend einem
  Bild oder durch händisches Speichern). Für in der Zwischenzeit neu
  hinzugekommene Werkzeuge gibt es dort auch noch keine Parameter.

RawTherapee zeigt für alle die Werkzeugparameter, die du auf diesem Weg
nicht mit lädst, folgendes Verhalten:

- Ist der Umschalt-Button **eingeschaltet** und sieht so aus: ![](/images/profile-filled.png), dann **werden alle Parameter**, die nicht über das Bearbeitungsprofil geladen werden (weil sie nicht enthalten sind oder von dir deaktiviert   wurden), **gelöscht** und durch fest kodierte Standardwerte von RawTherapee ersetzt!  
    
  \* Wenn du gerade ein Bild geladen hast und so ein Profil als Ausgangspunkt nehmen willst, stört das nicht oder kann von dir gewollt sein.

  Wenn du aber während der Bearbeitung auf diese Art ein Profil nachlädst, gehen sämtliche von dir vorher getroffenen Einstellungen verloren. (Die History behält sie aber natürlich. Du kannst also den Schritt rückgängig machen.) 
      
- Ist der Umschalt-Button ausgeschaltet und sieht so aus: ![](/images/profile-partial.png) , dann werden nur die gewünschten Parameter übernommen und alle Anderen bleiben da stehen, wo sie sind.

#### *Auswahlliste*

Mitgelieferte Profile, aber auch von dir Erstellte, die du regelmäßig verwenden willst, können über den breiten Button der Auswahlliste sehr schnell erreicht werden. Wo du dafür deine eigenen Bearbeitungsprofile ablegen musst, damit sie in dieser Liste angezeigt werden, findest du im Artikel [Dateipfade](file_paths).

#### *Bearbeitungsprofil einlesen und speichern*

Neben der Auswahlliste kann man mit Button ![](/images/gtk-open.png) ein solches Bearbeitungsprofil von beliebiger Stelle aus laden. Zum Beispiel das Bearbeitungsprofil, dass als Sidecar-File neben einem der Bilder liegt, die du vielleich gestern bearbeitet hast. Die aktuellen Einstellungen speicherst du mit diesem Button:
![](/images/gtk-save-large-dark.png)

Der Tooltipp-Text dieser Buttons verrät ein Feature, dass Du mit der Steuerungstaste erreichst, wenn Du sie genau in dem Moment gedrückt hältst, wenn du den Butten anklickst. Näheres dazu gleich.

#### *Zwischenablage für Bearbeitungsprofile*

Willst du ein aktuelles Bearbeitungsprofil, dass du gerade eingestellt hast, auf andere Bilder übertragen (auch teilweise), dann brauchst du es nicht erst abzuspeichern. Lege es mit ![](/images/edit-copy.png) in die Zwischenablage. Es handelt sich dabei nicht um die Zwischenablage deines Betriebssystems, sondern um eine reine RawTherapee-Funktion nur für Bearbeitungsprofile. Um das Profil auf ein inzwischen neu geladenes Bild anzuwenden klickst du ![](/images/edit-paste.png) an. Diese Funktionen sind auch in der Dateiverwaltung über das Kontextmenü ausgewählter. Kombiniere hier also Einzelbildbearbeitung mit Batch-Bearbeitung.

#### *Teilprofile über die Strg-Taste*

![](/images/selectprofileimportdlg_de_small.png)

In der Batchverarbeitung wird das auch *selektiv einfügen* bzw. *selektives anwenden* genannt:

Klickst du einen Button zum Speichern oder Einfügen (aus Datei oder Zwischenablage) an und hältst du dabei gleichzeitig die Strg-Taste gedrückt, öffnet sich im weiteren Verlauf ein zusätzliches Dialogfeld, indem du selektieren kannst, von welchen Werkzeugen du tatsächlich nur Parameter speichern oder laden willst. Zusammen mit der Zwischenablage und in Kombination mit der Batchverarbeitung kannst du die Bearbeitung vieler Fotos auf diese Art äußerst effizient gestalten. 

Bearbeitungsprofile im pp3-Format können übrigens auch mit einem gewöhnlichen Texteditor geöffnet und bearbeitet werden. Die Gliederung nach Werkzeugen und die Parameter sind faktisch selbsterklärend. Du kannst auch auf diese Art Profile bis auf die Basis von einzelnen Parametern herunter *selektiv* machen.

Kleiner Test: Baue dir ein Teil-Bearbeitungsprofil, dass nur deinen Urheberrechtshinweis und deinen Namen in den IPTC-Daten enthält. Hinweis: Willst du nicht, dass der Rest der IPTC-Daten beim Einlesen überschrieben wird, kommst du um eine händische Bearbeitung des Profils nicht herum. (Lösung am Ende der Seite)


### Werkzeugkiste
![](/images/toolboxtopview_de.png)

Die größte Fläche im rechten Bereich nehmen die Bildbearbeitzungswerkzeuge ein. Dieser Bereich besteht aus einigen Registerkarten, die du über die kleinen symbolischen Reiter oben erreichst. Für jedes dieser Werkzeuge gibt es einen einzelnen Artikel in der [Referenz](/_index.de.md).
Nutze den Tooltipp-Text, wenn du ohne zu drücken über die Reitersymbole fährst, falls du dir noch über den Inhalt der jeweiligen Registerkarten unsicher bist.

**Beachte:**

1.  Wenn Du die Werkzeuge aus dem Detail-Register ![](/images/detail_icon.png) verwendest, wird deren Wirkung nur im Vorschaubild angezeigt, wenn du es **mindestens mit 100% Auflösung** anzeigst.
2.  Falls du Metainformationen ![](/images/metadata.png) änderst oder einträgst, werden die
 - nie in das Quellfile (also z.B. das Raw, dass du gerade bearbeitest) übernommen, 
 - und auch nur dann in das gespeicherte Endresultat übernommen, wenn du unter ![](/images/preferences.png) *Einstellungen \> Bildbearbeitung \> Metadaten* den Punkt *Exif/XMP unverändert in die Ausgabedatei übernehmen* **deaktiviert** hast.


## Nur ein Reiter oder der *Multi-Reiter-Modus*

Nach der Installation ist RawTherapee so eingestellt, dass nur ein Bild zu einem Zeitpunkt bearbeitet werden kann. Dies ist der sogenannte - *Ein-Reitermodus*. Willst du aber lieber mehrere Bilder gleichzeitig zur Bearbeitung öffnen, dann ist der - *Multi-Reitermodus* das Mittel der Wahl.

Es gibt da einige wesentliche Unterschiede:

- Im Einreiter-Modus gibt es genau 1 Dateiverwaltung, 1 Warteschlange, 1 Editor-Fenster.
- Im Multi-Reitermodus dagegen, gibt es nicht nur 1 Editorfenster, sondern so viele, wie du über die Dateiverwaltung öffnest.
- Während es im Einreiter-Modus nur einen Editor mit einer History und einer Schnappschussliste gibt, gibt es im Multireitermodus quasi beliebig viele voneinander Unabhängige.
- Der Multireitermode benötigt sehr viel mehr Arbeitsspeicher! - Den einblendbaren Filmsteifen über dem großen mittleren Vorschaubild (und die Navigations-Buttons
  ![](/images/nav-prev.png "Image:nav-prev.png")
  ![](/images/nav-next.png "Image:nav-next.png") für den Filmstreifen bzw. Bilder im Ordner ganz unten im Editor) gibt es nur im Einreiter-Modus.

Eine sehr positive Eigenschaft von RawTherapee ist, dass du damit neben der Batch-Verarbeitung in der Dateiverwaltung für dich zwei ganz persönliche Möglichkeiten des Workflows wählen kannst. Bist Du ganz der Multitasking-Foto-Nerd mit entsprechend Arbeitsspeicher auf dem Mainboard, wird die extreme Workflowkombination *Multi-Reitermodus + ein ständiges Hin- und Her-wechseln in die Batch-Verarbeitung der Dateiverwaltungsregisterkarte* das Optimum sein. Das ist die Methode mit dem höchsten Bildverarbeitungsdurchsatz pro Arbeitszeit. Stressig, aber mit einiger Übung durchaus praktikabel.

Aber auch ohne den Anspruch auf Massendurchsatz: Falls Du lieber an mehreren, ähnlich belichteten Fotos gleichzeitig arbeiten willst, Parameter über die Zwischenablage zwischen den geöffneten Bildern hin und her tauschen möchtest - usw. - dann teste den Multi-Reitermodus. Er entbindet dich mehr. Nur auf den Filmstreifen musst du verzichten.

Diese Betriebsarten kannst du umstellen unter ![](/images/preferences.png "Image:preferences.png") *Einstellungen \> Allgemein \> Editor Layout*.

## Der Filmstreifen

![](/images/Rt_filmstrip_21_toolbar-visible.jpg "/images/Rt_filmstrip_21_toolbar-visible.jpg")

Den Filmstreifen kannst du nur im Einreiter-Modus verwenden (siehe oben). Er enthält Miniaturansichten aller Bilder im gewählten Ordner. Dies ist auch die Standardeinstellung nach der Installation. Der Filmstreifen enthält letztlich die Miniaturbilder, die Du auch in der Dateiverwaltung sehen kannst. Wenn du etwas eingearbeitet bist, probiere aber auch den Multi-Reitermodus aus (s. oben). Dann gibt es zwar diesen Filmstreifen als quasi Kopie der Dateiverwaltung nicht mehr, aber da die Dateiverwaltung auch nur einen Mausklick entfernt ist, benötigst du den Filmsteifen vielleicht nicht, um effizient zu arbeiten.

Wenn der Filmstreifen sichtbar ist (also im *Einreiter-Modus*), dann findest du ganz unten unter dem großen Vorschaubereich zwei Buttons, mit denen du dich selbst mit ausgeblendetem Filmstreifen von Bild zu Bild hangeln kannst: ![](/images/nav-prev.png "/Images/nav-prev.png")
und ![](/images/nav-next.png "Image:nav-next.png").

<hr />

Für eine größere Arbeitsfläche auf dem Bildschirm, kann die Werkzeugleiste über dem Filmstreifen ausgeblendet werden. Das kann auf zwei Wegen erreicht werden:
Die eine Methode schaltet lediglich die Symbolleiste ein oder aus, ohne die Höhe des Filmstreifens anzupassen, während die andere Methode dasselbe tut, aber zusätzlich automatisch die Höhe des Filmstreifens ändert.

![](/images/Rt_filmstrip_21_toolbar-hidden.jpg "/images/Rt_filmstrip_21_toolbar-hidden.jpg")

Beide Funktionen lassen sich ausschließlich über [Tastaturkürzel](Keyboard_Shortcuts.md) aufrufen. Da die Änderung der Filmstreifenhöhe eine Aktualisierung der Bildvorschau auslöst – was bei rechenintensiven Werkzeugen (wie der Rauschunterdrückung) und einer 100-%-Ansicht einige Zeit in Anspruch nehmen kann –, wurde der Modus ohne Höhenanpassung speziell für Nutzer mit langsameren Rechnern implementiert. Nutzer mit leistungsstarken Systemen dürften den Modus mit automatischer Höhenanpassung als praktischer empfinden.

<hr />


## Monitorprofil and Soft-Proofing ("Drucker-Simulation")

Ein breiter Auswahlbutton unterhalb der Vorschau erlaubt es dir, für das Vorschaubild auf ein Farbprofil für deinen Monitor zu wechseln. Das ermöglich Nutzern mit kalibriertem Monitor eine genauere Vorschau unabhängig davon, ob sie im sRGB- oder in einem vom Monitor unterstützten erweiterten Gamut-Farbraum arbeiten.
Beachte: Nutzer von OS x sind im Gegensatz zu Windows- oder Linux-Nutzern auf sRGB beschränkt.

Unter *Einstellungen \> Farbmanagement* kannst du unter *ICC-Profile-Verzeichnis* das Verzeichnis auswählen, in dem RawTherapee deine Farbprofile (Monitor, gegebenenfalls auch Drucker-ICC-Profil) findet. Unter *Monitor* kannst du auch gleich die Voreinstellungen beim Programmstart vorgeben. RawTherapee muss nach der Änderung des Pfades neu gestartet werden. Nutze als *Standard-Rendering-Intent* normalerweise *Relativ farbmetrisch*, wenn du keinen guten Grund hast, eine andere Einstellung zu treffen. Auch für diese Auswahl gibt es unter der Vorschau einen Button. Pass auf, dass du dort nicht versehentlich das Rendering umschaltest. 

Gleich neben diesen beiden Bedienelementen unter der Vorschau befindet sich ein weiterer Button, mit dem du das Soft-Proofing einschalten kannst. Das bedeutet, dass du auf dem Monitor die Farben so dargestellt bekommst, wie sie später beim Druck (bzw. Belichtung) erscheinen werden. Voraussetzung ist dabei nicht nur, das dein Monitor kalibriert ist und für den Monitor das richtige Farbprofil geladen ist, sondern dass du genau für den Drucker (Belichter), von dem du später dein Papierbild bekommst, ein ICC-Farbprofil besitzt (unter Umständen sogar speziell für das Papier, dass zum Druck verwendet wird). Das Profil stellst du dafür unter *Einstellungen \> Farbmanagement \> Drucker (Soft-Proofing) \> Farbprofil* ein. Mit der Option *Schwarzpunkt-Kompensation* wird am Monitor auch der richtige Grauwert für das "schwärzeste Schwarz" auf dem Drucker simuliert.

Wenn du dann Soft-Proofing über den Button aktivierst, wird dir im Vorschaubild simuliert, wie das Bild nach dem Druck aussieht. Das spart Tinte, Zeit bzw. Probleme, wenn du das Bild zum Druck in Auftrag gibst. Im letzteren Fall besorge dir das Drucker-Farbprofil beim ausgewählten Auftragnehmer. Schaltest du den Button rechts daneben mit dazu, werden im Bild sämtliche Pixel grau dargestellt, die laut Drucker-Farbprofil nicht gedruckt werden können. In diesem Bereichen wirst du vorhandene Bilddetails verlieren.

## Lösung zum Thema *Teilprofile über die Strg-Taste*

Inhalt einer möglichen urheberTxt.pp3:

`[Version]`  
`AppVersion=5.0-r1-gtk3`  
`Version=326`  
  
`[IPTC]`  
`Copyright=Alles MEINE!;`  
`Creator=Hans Fotonerd;`
