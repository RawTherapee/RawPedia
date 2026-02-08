---
title: Features
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
weight: 2
---

## Caratteristiche generali

- Tutte le caratteristiche standard che ti aspetteresti da uno
  sviluppatore raw e molto di più,
- Una coda di elaborazione in batch per rendere più veloce lo sviluppo
  di una foto, lasciando il grosso del lavoro della CPU in coda,
- Motore in [Floating
  point](https://en.wikipedia.org/wiki/Floating_point) - l'unico
  sviluppatore raw sul mercato che effettua tutti i calcoli in virgola
  mobile, in modo che nulla venga arrotondato e perso,
- Ottimizzazioni
  [SSE](https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions) per
  migliorare le prestazioni delle CPU moderne,
- [Gestione del colore](https://en.wikipedia.org/wiki/Color_management)
  utilizzando il sistema di gestione dei colori
  [LittleCMS](https://en.wikipedia.org/wiki/LittleCMS) v2 per una
  gestione del colore più precisa, fornendo il controllo sul
  funzionamento e lo spazio colore di uscita,
- Supporto per la lettura del formato DNG e la mappatura in virgola
  mobile dei toni HDR a 16, a 24 e 32 bit,
- Browser di file con etichette colorate, ricerca (del nome del file),
  filtraggio metadati (tipo di file, modello di fotocamera, tipo di
  lente, parametri foto)
- Supporto per i profili di colore DCP e
  [ICC](https://en.wikipedia.org/wiki/ICC_profile), per colori precisi o
  per replicare le immagini JPEG prodotte dalla fotocamera,
- Un pannello di cronologia per vedere facilmente quali cambiamenti hai
  fatto e tornare indietro ad un determinato punto,
- Un pannello di istantaneee per lavorare con più versioni diverse della
  stessa foto,
- Un'interfaccia utente flessibile in cui i pannelli e alcuni elementi
  possono essere adattati o nascosti,
- Facile navigazione nelle foto molto più grandi dello schermo grazie
  all'amplificazione del rapporto panoramico, eliminando la necessità di
  numerosi movimenti del mouse,
- Possibilità di scorrere i pannelli dei tools usando la rotella di
  scorrimento del mouse senza preoccuparsi di incorrere accidentalmente
  in errori oppure tenere premuto il tasto Maiusc mentre si utilizza la
  rotella di scorrimento del mouse per manipolare il regolatore su cui
  si muove sopra il cursore,
- Ottimizzazione dello spazio dello schermo facendo clic con il pulsante
  destro del mouse su uno strumento per mantenerlo visibile mentre
  chiude automaticamente gli altri,
- Una vista Prima/Dopo per confrontare la tua ultima modifica con
  qualsiasi elaborazione precedente,
- Supporto per i profili di elaborazione PP3 ([sidecar
  files](https://en.wikipedia.org/wiki/Sidecar_file)), intero e
  parziale,
- Mostra diversi canali in anteprima: rosso, verde, blu, luminosità e
  una maschera di messa a fuoco,
- Mostra vari canali nell'istogramma: rosso, verde, blu,
  [CIELAB](https://en.wikipedia.org/wiki/Lab_color_space) luminanza,
  cromaticità e raw,
- Indica nell'anteprima il [Color
  Clipping](https://en.wikipedia.org/wiki/Clipping_(photography)),
- Pannello di esportazione con opzioni di esportazione veloce,
- Tasti di scelta rapida per velocizzare il lavoro,
- Supporto della riga di comando per automatizzare RawTherapee
  utilizzando script o chiamarlo da altri programmi,
- Supporto per la maggior parte delle fotocamere,
- Supporta nuovi formati raw semplicemente modificando il file
  [camconst.json](camconst.json/it) in un editor di testo,
- Feedback audio per informare l'utente quando termina un compito
  intensivo di CPU, ad esempio quando la coda di sviluppo viene
  elaborata,
- Conservazione [1](https://en.wikipedia.org/wiki/IPTC%7CIPTC) e
  [2](https://en.wikipedia.org/wiki/Extensible_Metadata_Platform%7CXMP)
  di file pre-taggati,
- RawTherapee permette di utilizzare lo schema di colori di sistema ed è
  dotato di widget per provare gli schemi di colori personalizzati,
- Localizzazione in quasi 30 lingue.

## Esposizione e caratteristiche colore

- Lo strumento Livelli Automatici modifica le tue foto per fornire un
  buon punto di partenza,
- Vari metodi per il recupero e la ricostruzione delle ombre e delle
  alte luci,
- Filtro Vignettatura Post-Crop,
- Filtro graduato (GND),
- Strumento pipette che, se attivato per una curva specifica, consente
  di scegliere un punto sull'anteprima dell'immagine e quindi inserire
  su quella curca un corrispondente punto di regolazione,
- Due curve di tono RGB, ciascuna con quattro metodi di controllo, per
  un controllo senza precedenti dei colori e dell'esposizione,
- Regolazioni di Tonalità, Saturazione e Valore (HSV) e regolazioni
  della curva rossa, verde e blu (RGB)
- Ricchezza di regolazioni Lab per il controllo separato dei colori e
  della luminanza:
  - Curva L\* per il controllo della luminosità,
  - Curva a\* per controllare la posizione di un colore tra rosso e
    verde,
  - Curva b\* per controllare la posizione di un colore tra giallo e
    blu,
  - Curva LH per controllare la luminanza in funzione della tonalità,
  - curva CH per controllare la cromaticità in funzione della tonalità,
  - Curva HH per controllare la tonalità in funzione della tonalità,
  - Curva CC per controllare la cromaticità in funzione della
    cromaticità,
  - Curva LC per controllare la luminanza in funzione della cromaticità,
  - Curva CL per controllare la cromaticità in funzione della luminanza.
- Evita il cambiamento di colore (color shifting) usando [Munsell
  correction](https://en.wikipedia.org/wiki/Munsell_color_system),
- Controllo della vivacità colori,
- Conservazione delle tonalità naturali della pelle,
- [Tone mapping](https://en.wikipedia.org/wiki/Tone_mapping) basato su
  [edge-preserving decomposition](http://www.cs.huji.ac.il/~danix/epd/)
  per un aspetto naturale,
- [Bilanciamento del
  bianco](https://en.wikipedia.org/wiki/White_balance) - automatico,
  manuale o di una vasta gamma di fonti luminose predefinite,
- Mixer di canali,
- Conversione in bianco e nero,
- Diversi metodi di color toning,
- Supporto per fotocamere
  [monocromatiche](demosaicing/it#monochrome_cameras)
- Adattamento del modello di aspetto dei colori
  [CIECAM02](https://en.wikipedia.org/wiki/CIECAM02) ratificato dalla
  Commissione Internazionale sull'Illuminazione (CIE) per mantenere
  colori accurati e, data una serie di parametri di condizione di
  visualizzazione iniziale, convertire l'immagine in modo che possa
  sembrare lo stesso sotto le condizioni di visualizzazione target.
  L'elaborazione di immagini utilizzando CIECAM02 è abilitata tramite un
  certo numero di metodi, utilizzando le curve e i cursori. Una
  moltitudine di strumenti sono adatti per passare automaticamente alla
  modalità CIECAM02 quando sono in uso, tra cui [Tone
  Mapping](Tone_Mapping/it.md),
  [Nitidezza](sharpening/it),
  [Defringe](defringe/it), etc.
- Gestione del colore.

## Caratteristiche di Dettaglio

- Metodi diversi di nitidezza:
  - [Unsharp Mask](https://en.wikipedia.org/wiki/Unsharp_mask) con un
    cursore di soglia univoco e potente per ottenere dettagli evitando
    aloni,
  - [RL
    deconvolution](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
    per annullare la sfocatura,
  - [Bordi](https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en)
    vera risoluzione migliorando i bordi,
  - Microcontrasto per migliorare la struttura,
  - Contrasto con il metodo Detail Levels usando la decomposizione di
    wavelet in cinque livelli di dettaglio.
- Riduzione del rumore basata su wavelet molto potente negli spazi di
  colore RGB e Lab,
- Riduzione del rumore puntiforme per eliminare il rumore di tipo
  salt-and-pepper,
- Strumento Defringe per l'eliminazione di purple fringing (o altro
  colore).

## Caratteristiche di Trasformazione

- Correzione prospettica,
- Supporto profilo Adobe Correction Lens per la correzione automatica di
  distorsione, vignettatura e aberrazione cromatica,
- Correzione di distorsione,
- Correzione aberrazione cromatica post-demosaicizzazione,
- Correzione vignettatura pre-ritaglio.

## Caratteristiche Raw pre-demosaicizzazione

- Diversi metodi di demosaicizzazione per estrarre più dettagli
  possibile dalla tua foto raw:
  - AMAZE,
  - IGV e LMMSE per l'uso con riduzione del rumore per impedire maze
    patterns,
  - EAHD,
  - HPHD,
  - VNG4,
  - DCB,
  - AHD,
  - Mono,
  - Veloce.
- Filtro rumore linea,
- Regolazione punto bianco e nero,
- Sottrazione Dark Frame per eliminare alcune forme di rumore,
- Flat Field per correggere facilmente la vignettatura, il colore della
  lente e la polvere del sensore,
- Correzione automatica dell'aberrazione cromatica e manuale.

[Category:General](category:general)
