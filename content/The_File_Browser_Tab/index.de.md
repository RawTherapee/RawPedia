---
title: The File Browser Tab
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

# Die Registerkarte Dateiverwaltung

<figure>
<img src="/images/Rt_setm_fb.png" title="Rt_setm_fb.png" />
<figcaption>Rt_setm_fb.png</figcaption>
</figure>

Die Dateiverwaltung ist der Ort, wo Du Deine Fotos

- vorbetrachten kannst,
- zum Bearbeiten auswählen kannst oder auch
- Bearbeitungsoperationen als Batch für mehrer Fotos gleichzeitig
  durchführen kannst.

Die Dateiverwaltung besteht aus folgenden Komponenten:

- linker Bereich
  - Die Favoritenliste mit deinem Home-Verzeichnis, Laufwerken,
    USB-Karten-Leser, dem Standard-Bilder-Ordner des Systems und selbst
    dort abgelegte Nutzerordner.
  - Darunter befindet sich ein Dateibrowser in der Darstellung als Baum.
    Er dient der Navigation innerhalb der Ordnerstruktur auf deinen
    Medien. RawTherapee verkompliziert die Handhabung nicht, indem es
    dich zwingt, deine Bilder vor der weiteren Verarbeitung in eine
    Datenbank zu importieren, wie das bei anderer Software üblich ist.
    Deine Datenbank ist dein Dateisystem auf deinem Rechner oder auf
    Wechselmedien. Und Du kannst jederzeit mit jedem beliebigen
    Dateibrowser deine Bilder und Verzeichnise umsortieren, ohne dass
    das wesentlich für die Arbeit mit RawTherapee wäre.
  - Zwischen diesen beiden Feldern gibt noch einen + und einen - Button.
    Mit dem + Button kannst Du ein unten ausgewähltes Verzeichnis oben
    in die Favoritenliste zufügen. Mit dem - Button statt dessen ein
    oben markierten Ort aus der Liste wieder entfernen. Auch mit der
    *Verzeichnishistorie* kannst Du schnell auf zuletzt benutze Orte
    zurückgreifen.

<!-- -->

- rechter Bereich  
  Im rechten Bereich gibt es mehrere Registerkarten, die mit senkrecht
  stehenden Registerfahnen ausgewählt werden können:
  - Die *Entwickeln*-Registerkarte erlaubt, die Werkzeugeinstellungen
    gleichzeitig auf mehrere ausgewählte Bilder anzuwenden. Das erlaubt
    dir, einige Werkzeuge für viele Fotos auf einmal zu aktivieren und
    einzustellen.
  - Die *Prüfen*-Registerkarte zeigt eine Vorschau Deiner Bilder mit
    festen 100%, wenn du den Mauszeiger über die Bilder hinweg bewegst.
    Es wird dabei in einem Raw-Foto das gößte eingebettete JPEG
    verwendet, oder bei Nicht-Raw-Fotos dieses selbst. Es werden dabei
    noch keine Bildverarbeitungsschritte angewendet. Auch nicht, wenn du
    sie vorher unter *Entwickeln* eingeschaltet hast. Diese
    Registerkarte dient der Detailansicht beim Heraussuchen, Vorbewerten
    oder Sortieren von Bildern.
  - Die *Filter*-Registerkarte ermöglicht es, nur bestimmte Fotos
    einzublenden, die dem von Dir vorgegebenen Filterparametern
    entsprechen.
  - Mit der Registerkarte *Exportieren* kannst Du ausgewählte Bilder
    sofort exportieren und dabei Werkzeuge, die eventuell in den
    Sidecar-Files der Bilder schon eingestellt sind, abschalten. Damit
    ist es möglich, Vorschaubilder der Rohdaten auf schnellem Wege zu
    erstellen, um mit deren Hilfe besser, als es die Sicht in der
    Dateiverwaltung ermöglicht, einschätzen zu können, welche Bilder
    eventuell zu entfernen sind, weil sie z.B. verschwommen oder
    unscharf sind.

<!-- -->

- Die zentrale Arbeitsfläche zeigt alle Bilder des ausgewählten Ordner
  als kleine Miniaturbilder.

Du kannst den linken, wie den rechten Bereich vorübergehend ausblenden,
indem du die Buttons "Linkes Bedienfeld ein-/ausblenden
![<File:Panel-to-left.png>](Panel-to-left.png "File:Panel-to-left.png")"
oder "Rechtes Bedienfeld ein-/ausblenden
![<File:Panel-to-right.png>](Panel-to-right.png "File:Panel-to-right.png")"
drückst. Siehe dafür auch die Seite
[Tastatur-Kürzel](keyboard_shortcuts/de).

Wenn Du einen Ordner öffnest, erstellt RawTherapee für sämtliche Fotos
in diesem Ordner sofort Miniaturbilder, die im mittleren Bereich
angezeigt werden. Dazu wird bei Raw-Fotos das eingebettete JPEG Bild
verwendet. Einige Raw-Fotos können sogar mehrere JPEGs unterschiedlicher
Größe enthalten. Dafür muss RawTherapee alle Files in dem Ordner
nacheinander öffnen. Befinden sich viele Bilder im Ordner kann das eine
ganze Weile dauern. Das passiert aber nur beim ersten Mal, weil
RawTherapee alle dieser Miniaturansichten im eigenen Cache ablegt und
beim nächsten Zugriff auf diesen Ordner dann alle aus dem Chace lädt,
was deutlich schneller geht.

Das JPEG-Bild, dass in jedem Raw-Foto eingebettet ist, ist bis auf die
Auflösung identisch zu dem JPEG-Bild, dass die Kamera liefern würde,
wenn du im JPEG-Mode fotografiert hättest. Das Bild repräsentiert also
nicht die Raw-Daten im File, da die Kamera für das JPEG alle Arten von
Bildmanipulationen ausführt. Wie z.B. Belichtung anpassen, Sättigung
anheben, Kontrast ebenfalls, Schärfen usw.

Sobald Du ein Foto angefangen hast zu bearbeiten, wird seine
Miniaturansicht in der Dateiverwaltung mit dem ersetzt, was Du im
Editor-Vorschaufenster siehst. Gleichzeitig wird das Sidecar-File zu dem
Bild angelegt. Und jede Änderung, die im Editor ausgeführt wird, wird in
diesem Miniaturbild der Dateiverwaltung ebenso ausgeführt. Das
Miniaturbild wird auch sofort wieder im Cache für einen schnellen
erneuten Zugriff abgelegt. Wenn Du all die Einstellung im Sidecar-File
wieder zurücksetzen willst, dann klicke rechts auf das Miniaturbild
(oder wähle gleich mehrere aus) und wähle im Kontextmenü
"*Profiloperationen* \> *Profil löschen*". Dies entfernt das
Sidecar-File mit allen Deinen Bildeinstellungen der gerade ausgewählten
Bilder und gleichzeitig wird in der Miniaturansicht auch wieder das
eingebettet JPEG zur Anzeige verwendet.

Verwende oben in der Werkzeugleiste die Zoom-Icons *Miniaturbilder
verkleinern* bzw. *... vergrößern*, um die Miniaturbilder größer oder
kleiner darzustellen. Jedes Bild benötigt allerdings etwas
Arbeitsspeicher. Hast Du sehr viele Bilder in einem Ordner ist es
ratsam, diese Bilder nicht zu groß einzustellen ("*Einstellungen \>
Dateiverwaltung \> Maximale Größe der Miniaturbilder*").

Die sichtbaren Fotos können mittels mehrerer Methoden gefiltert werden:

- Innerhalb der Dateiverwaltung verwende die obere Werkzeugleiste.
- Im Editor verwende die Werkzeugleiste des
  [Filmstreifens](the_image_editor_tab/de#der_filmstreifen)
  (wenn in den Einstellungen eingeschaltet).
- Verwende das Suche-Feld ganz oben in beiden Registern (im Editor nur,
  wenn die Werkzeugleiste des Filmstreifens eingeschaltet ist).
- Oder nutze die Filter-Registerkarte in der Dateiverwaltung.

Mögliche Filter sind zum Beispiel:

- Zeige nur unbearbeitete Fotos
- Zeige nur Fotos, die mit +2EV aufgenommen wurden
- Zeige nur Fotos, die mit 5 Sternen bewertet sind
- Zeige nur Fotos, die in einem bestimmten vorgegebenen ISO-Bereich
  liegen
- Zeige nur Fotos, die die Dateierweiterung NEF besitzen

## Batch-Bearbeitung

RawTherapee besitzt einige Finessen, mit denen man gleichzeitig eine
ganze Reihe Bilder bearbeiten kann bzw. die Bearbeitung eines Bildes auf
eine Bildreihe im Ganzen oder teilweise übertragen kann. Es geht dabei
weniger darum, das Profil (aus dem Sidecar-File) eines Bildes einfach
nur zu kopieren. Es geht darum, einige Bearbeitungsschritte, die für
eine Serie von Bildern identisch ist, auf die betreffenden Bilder zu
übertragen, bevor man sie einzeln und nacheinander zuende entwickelt.

Dieser Prozess mag zur Einarbeitung noch nicht wichtig werden. Im
"produktiven Einsatz" sind solche Methoden aber sehr wichtig.

Die Batch-Arbeit erfolgt ebenfalls innerhalb der Dateiverwaltung.
Teilweise auch mit ersten Bearbeitungsschritten eines Bildes im Editor.
Gerade weil es so wichtig ist, die Methoden gut zu beherrschen, wird die
Batch-Verarbeitung im speziellen Artikel
[Batch-Bearbeitung](batch_adjustments_-_sync/de) behandelt.
