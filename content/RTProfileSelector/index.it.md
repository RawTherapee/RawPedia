---
title: RTProfileSelector
contributors:
  - Andrea.romagnoli
tags:
  - 'Processing Profile Scripts'
---

**RTProfileSelector** è un plugin RawTherapee che seleziona
automaticamente i profili di elaborazione personalizzati (file .pp3) in
base alle regole definite dall'utente. Le regole sono set di campi Exif
e valori che vengono confrontati con i valori effettivi estratti dai
file raw la prima volta che si aprono in RawTherapee.

Alcune cose che puoi automatizzare in RawTherapee tramite
RTProfileSelector:

- Assegnare i propri profili di elaborazione personalizzati per abbinare
  approssimativamente le impostazioni della fotocamera (ad esempio
  "monochrome"/"bianco e nero", "vivid color", "modalità film" ecc.)
- Impostare i parametri di riduzione del rumore in RawTherapee secondo
  il modello della fotocamera e il valore ISO
- Assegnare i profili di correzione dell'obiettivo (LCP) in base
  all'obiettivo e alla fotocamera utilizzata

RTProfileSelector è scritto in C++ 11 e compila sia su Windows che su
Linux. Il codice sorgente e l'eseguibile di Windows possono essere
scaricati dal suo [GitHub
repository](https://github.com/marcapelini/RTProfileSelector).
RTProfileSelector utilizza
[ExifTool](http://www.sno.phy.queensu.ca/~phil/exiftool/) per estrarre
metadati dalle immagini.

Per le procedure di installazione e la documentazione in linea, visita
la sezione [wiki](https://github.com/marcapelini/RTProfileSelector/wiki)
del progetto.
