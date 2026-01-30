---
title: Making a Portable Installation
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

# Eine portable Installation erstellen

RawTherapee und der Cache-Ordner können in sich geschlossen auf einem
USB-Medium oder einem beliebigen anderen Massenspeichergerät gespeichert
werden.

## Für Windows

Nimm die neueste Version von RawTherapee. Weil wir eine portable
Installation haben wollen benötigen wir nicht den Installer sondern nur
das reine, gezippte Programm. Wenn die neuste Version auf unserer
Webseite ohne Installer, in einfacher gezippter Form vorliegen sollte,
dann kannst Du diesen Schritt übergehen (Stand 03/2017: das ist nicht
der Fall, ein Installer wird verwendet). Wenn der Installer aber
enthalten ist, musst du zuerst die RawTherapee-Files extrahieren:

- Wenn es sich um einen Inno-Setup-Installer handelt, dann ist die
  Dateierweiterung des Installationsprogramms *.exe* (**Stand
  03/2017**). Lade in so einem Fall
  [innounp](http://innounp.sourceforge.net/) oder
  [innoextract](http://constexpr.org/innoextract/) herunter und entpacke
  damit das Installationsprogramm.

<!-- -->

- Falls es sich aber um einen MSI-Installer handelt (das ist mit Stand
  03/2017 für die Windows-Installationen nicht der Fall, könnte sich
  aber zukünftig ändern), dann verwende das Kommandozeilenprogramm
  *msiexec*:
    
      msiexec /a RawTherapee.msi TARGETDIR="C:\ZielVerzeichnis" /qb

  Ersetze dabei den Namen des MSI-Installers (hier also das
  *RawTherapee.msi*) mit dem aktuell gültigen Namen und ersetze auch das
  Zielverzeichnis (hier *C:\ZielVerzeichnis*) mit dem von dir
  gewünschten Verzeichnis.

Abschließender Schritt:

- Nehmen wir an, dass du das entzippte Programm im Verzeichnis
  **E:\RawTherapee** gespeicht hast (**E:\\** sei der Laufwerksbuchstabe
  z.B. eines USB-Mediums). Dann öffne das File
  **E:\RawTherapee\options** in einem Editor und setze die Option
  **MultiUser** auf **false**. Auf diese Art wird der Cache-Ordner auf
  einen Sub-Ordner des Installationsordners gestellt.

## Für Linux

Im Gegensatz zu Windows, wo alle benötigten Bibliotheken im
mitgelieferten Programm enthalten sind, ist eine portable Variante auf
Grund der Eigenheiten von Linux dort sehr schrierig zu erstellen.
RawTherapee wird für die einzelnen Linux-Distributionen separat gepackt
und ist über die Abhängigkeiten zu Bibliotheken der Distribution sehr
eng mit einer solchen Distribution verknüpft. Es ist unwahrscheinlich,
dass RawTherapee auf einer Distribution als portable eingerichtet, auch
auf einer anderen Distribution läuft.

Was aber gut funktioniert: Auf allen Zielsystemen zwar RawTherapee mit
den dort vorhandenen Paketmanagern separat installieren, jedoch die
Konfigurationsdateien auf einem tragbaren Speichermedium ablegen.
Sichere dazu auf ein portables Medium den RawTherapee-Ordner *config*.
Insbesondere benötigst Du das "*options*"-File, das Nutzer-File
"*camconst.json*", falls Du es erstellt hast, und sämtliche
nutzerspezifischen PP3, ICC, DCP and LCP Profilefiles. Der
[Dateipfade](file_paths/de)-Artikel beschreibt, wo diese
Files jeweils zu finden sind.
