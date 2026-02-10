---
title: Adding Support for New Raw Formats
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

Aggiungere il un supporto per un nuovo formato raw in RawTherapee è
semplice. Puoi farlo da solo o puoi prendere le foto necessarie e
inviarle per farci le misure e aggiungere il supporto alla tua
fotocamera.

## Introduzione

Leggere correttamente un file raw richiede di acquisire alcune
informazoni e RawTherapee cerca queste informazioni in tre punti:

- Nel codice dcraw incorporato,
- Nel file raw stesso,
- In un file di testo chiamato camconst.json

Le informazioni necessarie sono raccolte da tutti questi tre punti e il
file camconst.json è il più importante. Se si verifica una
sovrapposizione di informazioni, camconst.json ha la priorità.

camconst.json consente di impostare quanto segue:

- Matrici di colore per [Illuminante
  D65](http://en.wikipedia.org/wiki/Illuminant_D65), in formato dcraw,
- livelli dei bianchi e dei neri,
- dimensione del ritaglio e posizione con cui rimuovere righe e colonne
  spurie,
- dimensioni dell'area e offset da cui è possibile calcolare i livelli
  dei neri

per ogni combinazione di canale di colore, ISO e apertura per una
determinata macchina fotografica. Per questo motivo, camconst.json serve
sia per aggiungere rapidamente un supporto dettagliato a nuovi formati
raw sia per migliorare il supporto per le fotocamere non perfettamente
gestite da dcraw.

## Foto necessarie

Per eseguire le misurazioni necessarie per un supporo perfetto , è
necessario eseguire diverse serie di foto con impostazioni specifiche:

- Ogni foto deve essere totalmente esagerata ovunque! Rivolgi la
  fotocamera ad una sorgente luminosa (ad esempio il cielo, una
  lampada), zoomando se necessario e aumentando il tempo di esposizione
  finché tutto non viene completamente sovraesposto. Naturalmente scatta
  in modalità raw. Se la fotocamera dispone di diverse modalità raw,
  utilizzane una, non tagliata, senza compressione se possibile.

1.  Se la fotocamera ha una riduzione del rumore integrata, disattivala.
    Prendi una serie di foto come sopra descritto, una foto per ogni
    valore ISO che la tua fotocamera supporta, assicurandosi di non
    superare un tempo di esposizione di 0.5s, utilizzando un'apertura di
    f/8. Ad esempio, per una fotocamera tipica con valori: ISO100,
    ISO200, ISO400, ISO800, ISO1600, ISO3200, ISO6400, ISO12800, si
    otterrebbero 8 foto. Le nuove fotocamere spesso includono valori ISO
    intermedi, ad es. ISO160, ISO320, ecc. Se la fotocamera include tali
    valori ISO, è importante scattare anche con questi valori.
2.  Se la fotocamera ha una riduzione del rumore integrata, adesso
    utilizzala. Prendete una seconda serie di foto come descritto in
    precedenza, una foto per ogni valore ISO che la fotocamera supporta,
    assicurandosi che il tempo di esposizione in tutti i casi sia almeno
    2 secondi, non meno, utilizzando un'apertura di f/5.6. Quest per
    avere la stessa sequanza di foto del caso precedene (8 foto).
3.  Alcune fotocamere scalano valori raw per aperture più grandi, in
    particolare i modelli Canon e Nikon. L'unico modo per sapere se la
    tua fotocamera fa questo è sicuramente prendere una foto e
    misurarla. Scatta una foto utilizzando l'apertura più grande della
    tua lente, ad es. f/1.7, a ISO100 con una lunga esposizione e con la
    riduzione del rumore spenta, e invialo a noi insieme al resto degli
    scatti. Se rileviamo che è presente una scalatura del formato raw (o
    se lo rilevi da solo se fai le tue misurazioni), ti chiederemo di
    scattare una serie di foto ad ogni valore ISO differente di 1 stop,
    con un tempo di esposizione inferiore a 0,5 secondi all'apertura più
    grande della tua lente supporta e con differenze di 1/3 di diaframma
    fino a una apertura in cui la scalatura raw non è più eseguita.
    Questo potrebbe significare molte foto. La gestione della scalatura
    raw causata da grandi aperture non è molto importante, quindi non si
    sentono troppo sconvolti, non è necessario farlo se la fotocamera
    non scala gli scatti, ma se hai il tempo e pazienza allora sarebbe
    meglio controllarlo.

Come minimo, dovresti realizzare una serie di circa 8 foto del punto 1.
Si raccomanda di scattare foto per entrambi i punti 1 e 2, per un totale
di 16 foto, oltre alla foto di prova della scala raw del punto 3 Se si
scopre che la fotocamera esegue la scalatura raw, è possibile aggiungere
la serie necessaria descritta al punto 3, ma poiché potrebbe significare
molte foto (ad esempio 50 o più), non è necessario.

Comprimi tutte queste foto, caricale su
[filebin.net](http://filebin.net/) e inviaci il link completo tramite la
nostra pagina
[GitHub](https://github.com/Beep6581/RawTherapee/issues/new) o nel
[Forum](http://rawtherapee.com/forum).

Le foto possono avere dimensioni strabilianti, non dimenticate di
comprimerle (7-Zip, ZIP, bzip2, qualunque cosa) prima di caricare! Ad
esempio, 10 file raw di Sony 7M2 a lunga esposizione e con la riduzione
del rumore disabilitata pesano 234 MB, ma compresse in formato ZIP
soltanto 1 MB.

## Dettagli

Per una precisa documentazione, dettagliata delle foto e delle
istruzioni necessarie per misurarle, leggere i commenti all'interno del
file camconst.json:
<https://github.com/Beep6581/RawTherapee/blob/dev/rtengine/camconst.json>
