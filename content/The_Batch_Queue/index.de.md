---
title: The Batch Queue
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

# Die Warteschlange

Die Warteschlange mag eine primitive Funktion der Endverarbeitung sein.
Trotzdem hat sie parallel zur Dateiverwaltung und dem Editor einen
gleichwertig hohen Stellenwert als dritte oberste Registerkarte
bekommen. Das ist nicht verwunderlich. Im gesamten Workflow ist sie
nicht nur der letzte Schritt, sondern der Schritt, wo die Maschine
durchaus über mehrere Stunden selbständig arbeitet und der Nutzer
erwartet, dass er sämtlichr Ergebnisse seiner vorherigen Arbeit, die
ebenfalls Stunden dauerte, in bester Qualität erhält. So sehr die
Warteschlange für den Nutzer auch nur wie ein Stapel
Entwicklungsberechnungen erscheint.

## Wozu eine Warteschlange für das Speichern?

An einigen Stellen im Handbuch wurde bereits darauf hin gewiesen, dass
die endgültige, hoch-qualitative Bearbeitung eines Bildes einige Zeit in
Anspruch nehmen kann. Einige komplexere Filter, die vielleicht erst das
Bild in einen anderen mathematischen Raum umrechnen müssen oder sehr
viel Information um ein Pixel herum bearbeiten müssen, um genügend
Information für den neuen Wert des Pixels berechnen zu können,
beanspruchen die CPU. RawTherapee verwendet effiziente Algorithmen, die
auch sämtliche Prozessorkerne und Hyper-Threading ausnutzen. Theoretisch
könnte sich RawTherapee dabei selbst bremsen, um für den Nutzer genügen
Performance für die Bearbeitung der nächsten Fotos bereitzustellen. Aber
vielleicht möchte der Nutzer gerade lieber möglichst schnell das
Ergebnis. Softwareentwickler können nun verschiedene Annahmen treffen
und für viele Szenarien eine gute Performance erreichen. Aber alles hat
seine (Automatik-)Grenzen.

Man hat deshalb den Ansatz gewählt, dem Benutzer bei der
rechenintensiven Arbeit genau 2 Optionen zu lassen:

- Entweder wird das Speichern eines Bildes sofort ausgeführt und dafür
  die maximale Rechenleistung zur Verfügung gestellt, oder
- die Berechnung wird auf einen Zeitpunkt verschoben, wo der Nutzer
  nicht mehr am Rechner arbeitet.

Ersteres ist im Editor unter *Bild speichern* erreichbar: Der Nutzer
startet die Berechnung und muss nun erst mal warten, bis das Bild fertig
ist. (Oder sich mit einem lahmen Rechner rumschlagen.)

Die zweite Variante ist die Warteschlange: Der Nutzer fügt die
Berechnung eines Bildes hinzu, arbeitet ungehindert weiter und startet
zum Ende hin sämtliche Aufträge in der Warteschlange. Und nutzt den
Rechner dann erst mal nicht weiter. - Natürlich bleibt der Rechner
weiter nutzbar. Aber eine effiziente Bildbearbeitung, die für das
Vorschaubild ebenfalls hohe Rechenlast in einigen Spitzen benötigt,
beißt sich so nicht mit der Verarbeitung der Bilder.

Selbstverständlich ließe sich das CPU-intensive Bildberechnen so in
Scheiben einteilen, dass trotzdem die gefühlte Performance des Nutzers
bei der Bildbearbeitung bestehen bleibt. Da hierzu aber eine sehr
intensive Kommunikation mit dem Betriebssystem und seinem Verhalten
notwendig ist und RawTherapee für mehrere Plattformen entwickelt wird,
wäre so eine Implementation äußerst aufwändig. Die Entwickler sind
deshalb den Weg gegangen, den wohl die meisten Nutzer auch mitgehen:
Zeitliche Trennung von Bildbearbeitung und Bildberechnung. - So steht
dir ohne irgendwelche Klimmzüge und Bugs immer die volle Rechenleistung
zur Verfügung, wenn Du vor dem Bild sitzt. Der Rest passiert wärend
einer Kaffee- oder Tee-Pause oder über den Rest der verbleibenden Nacht.
Bei maximaler Auslastung der CPU.

## Zufügen von Bildern zur Warteschlange

Dieser Schritt wurde bereits im Artikel
[Speichern](saving/de) behandelt. Dort gibt es auch einige
Informationen zu den zur Verfügung stehenden Zielformaten. Die Parameter
für die Zielformate mit dem Speicher-Button
![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png")
im Editor sind identisch mit den Parametern, die in der Warteschlange
eingestellt werden können. Vergleiche also bitte mit Artikel
[Speichern](saving/de).

Mit dem Button
![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png")
im Editor kannst du für das betreffende Bild die Ausgabeparameter
einzeln vorgeben. Legst Du statt dessen das Bild im Editor mit
![Image:processing.png](processing.png "Image:processing.png") direkt in
die Warteschlange, wird es so gespeichert, wie du es in der
Registerkarte der Warteschlange global vorgibst. Diese Vorgabe kannst du
auch erst unmittelbar vor dem Start der Abarbeitung der Warteschlange
treffen.

## RawTherapee abgestorben - Alles futsch?

Natürlich bemühen sich die Entwickler, RawTherapee so stabil dem Nutzer
zu übergeben, wie es geht. Die aktuelle Version 5.0 zeichnet sich ganz
besonders durch hohe Stabilität aus. Aber der Worst-Case kann ja doch
einmal eintreten: RawTherapee reagiert nicht mehr. Ist nun die Arbeit
von Minuten oder Stunden verloren? Muss ich alle Bilder noch mal in die
Warteschlange geben?

Genau dieses Risiko, dass vor allem bei einer permanenten
Softwarefortentwicklung zu Tage tritt, hat das Team um RawTherapee
ausgezeichnet gelöst: Sämtliche Bildbearbeitungsschritte landen
unmittelbar im Bearbeitungsprofil, dass als Sidecar-File dem Raw
beigestellt wird. Und mit der Warteschlange gestaltete es sich ebenso:
Sobald ein Bild mit seinen Parametern der Warteschlange zugefügt wurde,
wird das abgespeichert. Egal, ob du nun das Programm zwischendurch
schließt, oder es doch in einer bestimmten Version dazu neigen sollte,
unerwartet den Geist aufzugeben: Nach dem erneuten Öffnen ist auch die
Warteschlange wieder im aktuellen Zustand. - Eine der
Basisanforderungen, wenn Nutzer die Software tatsächlich produktiv
einsetzen. Also mit Verträgen, die an Geld und Termine gebunden sind. -
Keine Software gibt hierfür eine Garantie. Aber RawTherapee zeigt seit
Jahren, dass der produktive Einsatz kein Problem ist. Obwohl kostenlos
und obwohl durch eine freie Entwicklergemeinde fortentwickelt.

## Ausgabeverzeichnis - Ziel-Einstellungen für die Resultate aus der Warteschlange

Wenn Du möchtest, kannst du sämtliche Bilder der Warteschlange,
unabhängig in welchem Ordner die Original-Raws stehen, die du bearbeitet
hast, in ein und den selben Zielordner schreiben. Wähle in diesem Fall
*In dieses Verzeichnis speichern* und gib den Zielordner vor.

Viele Nutzer mögen aber die peniblere Variante: Die bearbeiteten Bilder
werden z.B. in Unterordner unterhalb der Originale abgelegt. Und die
Benennung dieser Unterordner (oder Ordner an einem anderen Speicherort)
sollen entsprechend der Quelle geschickt benannt werden. Nutze in so
einem Fall *Dynamisches Verzeichnis verwenden*. Im dahinter stehenden
Feld kannst das Muster vorgeben, wie die berechneten Bilder abgelegt
werden. Der Tooltipp-Text dieses Feldes gibt ausreichend Informationen,
die das Prinzip und die möglichen Variablen beschreiben:

`Die folgenden Variablen können verwendet werden:`  
<b>`%f`</b>`, `<b>`%d1`</b>`, `<b>`%d2`</b>`, ..., `<b>`%p1`</b>`, `<b>`%p2`</b>`, ..., `<b>`%r`</b>`, `<b>`%s1`</b>`, `<b>`%s2`</b>`, ...`  
  
`Diese Variablen beinhalten bestimmte Teile des Verzeichnispfades, in welchem sich das Bild befindet, oder Attribute des Bildes.`  
  
`Wenn zum Beispiel `<b><i>`/home/tom/photos/2010-10-31/dsc0042.nef`</i></b>` geöffnet wurde, dann haben die Variablen den folgenden Inhalt:`  
<b>`%d4`</b>` = `<i>`home`</i>  
<b>`%d3`</b>` = `<i>`tom`</i>  
<b>`%d2`</b>` = `<i>`photos`</i>  
<b>`%d1`</b>` = `<i>`2010-10-31`</i>  
<b>`%f`</b>` = `<i>`dsc0042`</i>  
<b>`%p1`</b>` = `<i>`/home/tom/photos/2010-10-31`</i>  
<b>`%p2`</b>` = `<i>`/home/tom/photos`</i>  
<b>`%p3`</b>` = `<i>`/home/tom`</i>  
<b>`%p4`</b>` = `<i>`/home`</i>  
  
`Wenn Sie die Ausgabedatei in dasselbe Verzeichnis wie das Originalbild speichern wollen, dann wählen Sie:`  
<b>`%p1/%f`</b>  
  
`Wenn Sie die Ausgabedatei in ein Unterverzeichnis mit dem Namen "`<i>`converted`</i>`" schreiben wollen, dann wählen Sie:`  
<b>`%p1/converted/%f`</b>  
  
`Wenn Sie die Ausgabedatei im Verzeichnispfad "`<i>`/home/tom/photos/converted`</i>`" speichern wollen, dort jedoch in einem mit dem Namen des Ursprungsverzeichnisses betitelten Unterverzeichnis, dann wählen Sie:`  
<b>`%p2/converted/%d1/%f`</b>  
  
`Die Variable `<b>`%r`</b>` enthält die Bewertung des Bildes.`

## Die Bearbeitung der Warteschlange steuern

Du kannst übrigens die Bearbeitungsreihenfolge ändern: Die
Miniaturbilder lassen sich über kleine Pfeile in der Reihenfolge
umsortieren. Du kannst auch einzelne Bilder aus der Warteschlange wieder
entfernen.

Zum Start der Bearbeitung nutze den klassischen *Play*-Button
[image:Gtk-media-play.png](image:gtk-media-play.png) links
oben.

Wenn du nur eine Arbeitspause machst, kannst du die Warteschlange schon
mal der CPU übergeben und den Vorgang anhalten, wenn du mit der
Bearbeitung der nächsten Fotos weiter machen willst. Denn, wo ein
*Play*-Button ist, ist auch ein *Stop*-Button nicht weit:
[image:Gtk-media-stop.png](image:gtk-media-stop.png).

Für den Fall, dass Du an einer leistungsstarken *Maschine* arbeitest,
und feststellst, dass dich der CPU-aufwendige Prozess der finalen
Bildberechnungen doch nicht bei der Bearbeitung der folgenden Bilder
stört: Die Option *Automatisch starten* öffnet das Ventil, durch den der
Stapel der Bilder läuft, ohne dass du den *Play*-Button drücken musst.
Sobald du ein Bild in die Warteschlange gelegt hast, rechnet der
Prozessor los. Prüfe unter deinen Bedingungen, wie gut du dann noch
arbeitsfähig bist. Normalerweise ist diese Option deaktiviert.

Wie schon oben genannt: Wenn du den Rechner aus machen willst, oder auch
nur Stromausfall ist: Die Warteschlange bleibt bis zu einem Neustart von
RawTherapee erhalten. Du kannst jederzeit fortsetzen. RawTherapee
entfernt erst dann ein Bild aus der Warteschlange, wenn es vollständig
gespeichert ist.
