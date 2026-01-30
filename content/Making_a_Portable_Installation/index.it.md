---
title: Making a Portable Installation
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

RawTherapee e la propria cartella di cache possono essere memorizzati su
un'unità flash USB o su qualsiasi altro dispositivo di archiviazione di
massa in modo "auto-consistente".

## Per Windows

Ottieni l'ultima versione di RawTherapee. Dal momento che lo vogliamo
portatile, non vogliamo la versione autoinstallante, ma solo il
programma zippato. Se la versione più recente sul nostro sito web è in
formato zip senza l'installer, puoi saltare questo passaggio.
Altrimenti, se si tratta di un programma di installazione, è necessario
per prima cosa estrarre i file RawTherapee.

- Se si tratta di un programma di installazione (estensione .exe, tutte
  le più recenti versioni di Windows sono in questo formato), utilizzare
  [innounp](http://innounp.sourceforge.net/) o
  [innoextract](http://constexpr.org/innoextract/) per estrarlo.
- Se si tratta di un programma di installazione MSI (nessuna nuova
  versione di Windows lo utilizza al momento), aprire un prompt dei
  comandi e digitare:
    
      msiexec /a '''RawTherapee.msi''' TARGETDIR="'''C:\TargetDir'''" /qb

  Sostituire il nome del programma di installazione MSI e della
  directory di destinazione come desiderate. Sono consentiti anche gli
  spazi nel percorso di TargetDir perchè il percorso è racchiuso in
  virgolette.

Supponiamo di aver estratto l'archivio in **E:\RawTherapee**,
dove**E:\\** è la lettera dell'unità flash USB. Ora apri il file
**E:\RawTherapee\options** e imposta l'opzione **MultiUser** a
**false**. In questo modo, la directory della cache si trova in una
sottodirectory del percorso di installazione.

## Per Linux

Ottenere RawTherapee per installarlo su un supporto portatile come
un'unità flash USB su Linux non è semplice a causa della natura dei
sistemi Linux. Mentre la versione di RawTherapee di Windows viene
fornita in bundle con tutte le librerie richieste per eseguire su
qualsiasi versione di Windows, le distribuzioni di Linux differiscono
significativamente l'una dall'altra e come risultato una versione di
RawTherapee costruita per una distribuzione è improbabile che sia
eseguibile sotto una distribuzione diversa. Questo rende non semplice
poter disporre di una versione portatile che possa essere eseguita da
una chiavetta USB su qualsiasi distribuzione Linux, è però possibile
tenere i file di configurazione portatili e quindi installare
RawTherapee sulla macchina di destinazione utilizzando il gestore di
pacchetti della distribuzione, in quanto le build di RawTherapee sono
disponibile per la maggior parte delle distribuzioni. Potresti anche
metterlo su un'immagine USB live, se sei ambizioso:\]

Per eseguire il backup della configurazione, si deve copiare la cartella
*config* di RawTherapee sul dispositivo USB. In modo specifico, si deve
copiare il file "*options*", il file custom "*camconst.json*" , tutti i
profili PP3, ICC, DCP e LCP personalizzati. L'articolo [Percorsi dei
File](File_Paths/it.md) descrive dove trovarli.
