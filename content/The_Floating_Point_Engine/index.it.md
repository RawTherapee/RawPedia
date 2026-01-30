---
title: The Floating Point Engine
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

RawTherapee 4 effettua tutti i calcoli in notazione a 32 bit [virgola
mobile](https://en.wikipedia.org/wiki/Floating_point) (a differenza di
molti altri convertitori che utilizzano interi a 16-bit come \[https: //
en. wikipedia.org/wiki/Dcraw dcraw\] e anche in RawTherapee fino alla
versione 3.0), quindi niente viene arrotondato e perso.

I convertitori classici funzionano con numeri interi a 16 bit. Un canale
di pixel ha valori compresi tra 0-65535 e 16 bit (i convertitori per
aumentare la precisione moltiplicano in genere i valori della fotocamera
da 12 a 14 bit per riempire l'intervallo a 16 bit). I numeri non hanno
frazioni, per esempio non esiste alcun valore tra 102 e 103. In
contrasto, i numeri a virgola mobile memorizzano un valore in una gamma
molto più ampia con una precisione di 6-7 cifre significative. Ciò
consente, in particolare nelle alte luci, il recupero dei valori più
elevati. Consente inoltre migliori risultati nella catena di
elaborazione temporanea senza perdere informazioni. I valori espressi in
frazioni aiutano anche a smussare le transizioni di colore per impedire
la formazione di bande di colore. E non meno importante, il calcolo in
virgola mobile rende la vita più facile per gli sviluppatori che non
devono preoccuparsi tanto degli errori di arrotondamento quando
sviluppano algoritmi di elaborazione immagine per RawTherapee.

L'inconveniente è che i numeri a virgola mobile richiedono esattamente
due volte lo spazio RAM dell'intero a 16 bit. Insieme al crescente
numero di megapixel delle fotocamere digitali, un sistema operativo a 32
bit può facilmente esaurire la memoria e causare il crash di
RawTherapee. Pertanto, un sistema operativo a 64 bit è fortemente
consigliato per la stabilità. Se si verificano problemi con RT in un
sistema a 32 bit, provare quanto segue:

- Come regola generale, evitare di disporre di cartelle con troppe foto
  raw in quanto ogni foto occupa la memoria quando viene visualizzata
  nella scheda Navigatore di RawTherapee. Provare a non avere più di 100
  foto per cartella.
- RawTherapee utilizza molta RAM mentre si utilizza la scheda
  Navigatore, pertanto evitare di aprire la scheda mentre si elaborano
  le foto.
- In Windows usare almeno 4 Gigabyte. Vedere "[4-Gigabyte Tuning:
  BCDEdit e
  Boot.ini](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)"
  per una spiegazione di ciò che è e leggere la guida su come farlo in
  "[Come impostare l'avvio a 3GB in Windows XP e
  Vista](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)".
- Chiudere altri programmi mentre si lavora in RawTherapee.
- Chiudi la scheda Editor immagine quando hai finito di modificare per
  liberare la memoria.
- Disattivare "auto-start" nella coda di sviluppo. Basta aggiungere le
  foto alla coda di sviluppo una volta che hai finito di modificarle
  tutte e quindi avviarla. Utilizzare la coda di sviluppo, non
  utilizzare il pulsante di salvataggio immediato.
- Utilizzare una directory con poche o nessuna foto prima di avviare la
  coda di sviluppo.
- È possibile liberare una certa memoria eliminando (o spostando in una
  diversa cartella o rinominando qualcosa di simile a .unusedicc) tutti
  i profili .icc in iccprofiles\input per le fotocamere che non si
  utilizzano.
- Assicurarsi che le directory Frame Dark e la directory dei Flat Field
  in Preferenze non fanno riferimento a cartelle contenenti file raw se
  non si utilizzano Dark-frames o Flat-fields.
- Gli strumenti più costosi per la memoria sono [Tone
  Mapping](Tone_Mapping/it.md), [Contrasto per livelli di
  dettaglio (CbDL)](Contrast_by_Detail_Levels/it.md) e
  [Ricostruzione Alte
  luci](Exposure/it#Highlight_Reconstruction.md) utilizzando
  "Color Propagation", quindi potrebbe essere necessario evitare di
  utilizzarli se la vostra macchina e il sistema operativo hanno poche
  risorse.

[Category:General](category:general)
