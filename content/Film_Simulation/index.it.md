---
title: Film Simulation
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

![](Rt_haldclut_london.jpg "Rt_haldclut_london.jpg") Lo strumento
*Simulazione di film* consente di abbinare i colori della tua foto a un
riferimento scelto con un solo clic.

Per utilizzare questo strumento è necessario utilizzare alcune immagini
nella tabella *Hald Color Look-Up (Hald CLUT)*. Puoi scaricare la
*Collezione di simulazione di film RawTherapee* qui sotto o crea la tua.
La prima volta che si esegue questo strumento troverai un messaggio che
ti informa che devi puntare RawTherapee in una cartella che contiene le
immagini di riferimento utilizzate da questo strumento. Dopo aver
scaricato la *Collezione di simulazione di film RawTherapee* o creando
il proprio, vai a "Preferenze\> Elaborazione di immagini\> Simulazione
di film" e indica la cartella che li contiene. È necessario un riavvio
di RawTherapee.

## Per iniziare

È importante creare una cartella che utilizzerai solo per memorizzare
immagini Hald CLUT da scaricare o eseguite automaticamente. Non
memorizzare nient'altro in quella cartella. Il motivo per questo è che
RawTherapee esegue la scansione di questa cartella ogni volta che si
avvia, quindi se la cartella contiene più file di quanto necessario, si
verifica un *'tempo di avvio molto lento'* (potrebbe richiedere minuti).
Se utilizzi una versione RawTherapee dal febbraio 2016, sarai avvisato
se la scansione all'avvio richiede più di 10 secondi. Quando ciò accade,
basta fare clic sul pulsante nella finestra popup per interrompere la
scansione, quindi andare a "Preferenze\> Elaborazione di immagini\>
Simulazione film" per vedere quale cartella viene utilizzata e puntare
RawTherapee in una cartella che contiene solo immagini Hald CLUT niente
di più, oa una cartella vuota se non si desidera utilizzare lo strumento
di simulazione film.

Per darti un'idea di come il tempo di avvio è influenzato, RawTherapee
richiede circa 2,5 secondi per iniziare quando si utilizza una cartella
Hald CLUB vuota e circa 100 ms più a lungo, quando si utilizza una
cartella Hald CLUT contenente 500 file in essa (che è più che nella
nostra *RawTherapee Film Collection Simulation Collection*). Se però
doveste accidentalmente dire a RawTherapee che la cartella Hald CLUT è
`C:\Program Files (x86)`, quindi il tempo di avvio potrebbe richiedere
alcuni minuti. Come si può vedere, non c'è motivo di preoccuparsi quando
si utilizzano i CLUT di Hald finché si utilizza una cartella dedicata
come suggerito, mantenendo solo immagini Hald CLUT in esso.

## Come funziona

![](Hald_CLUT_Identity_12.png "Hald_CLUT_Identity_12.png") Questo
strumento utilizza immagini appositamente preparate in quello che viene
chiamato un modello Hald CLUT. Contiene tutti i colori possibili
tracciati in una specifica disposizione, modificata dallo stato
originale noto dell'immagine "Hald_CLUT_Identity.tif". Esegue la
scansione di ogni pixel dell'immagine Hald CLUT che si sceglie,
calcolando la differenza tra il colore di quel pixel e il colore del
pixel corrispondente nel file di identità, quindi modificando di
conseguenza il colore corrispondente alla tua foto. Se la tua foto
contiene i colori non presenti nell'immagine Hald CLUT, i colori
mancanti saranno interpolati in modo che la posterizzazione non si
verifichi.

Per una spiegazione completa, fare riferimento alla pagina di Eskil
Steenberg su Hald CLUT: <http://www.quelsolaar.com/technology/clut.html>

Per generare un'immagine di Hald a 16 bit a 12 livelli con ImageMagick,
eseguire questo comando in una console:  convertire hald: 12 -depth 16
-color spazio sRGB hald12_16bit.tif

## Caveat

Si consiglia di utilizzare ImageMagick per generare il file di identità
se è necessario generarlo, in quanto il programma per generarli su
www.quelsolaar.com ha un bug che può causare problemi con
evidenziazioni. Naturalmente puoi utilizzare il file di identità che
forniamo qui - è senza bug. Inoltre, si consiglia di utilizzare Hald
CLUT in formato TIFF se si utilizza RawTherapee-4.2.140 o più vecchio,
in quanto vi era un piccolo bug di gamma che ha reso l'immagine
leggermente più scura complessivamente. Questo errore è stato risolto
nella versione 4.2.141. Potresti ovviamente ignorare il problema se
utilizzi i CLUTI di Hald per scopi estetici, poiché la variazione della
luminosità è sottile e può essere facilmente compensata per utilizzare
il cursore o le curve di esposizione di RawTherapee o spiegarti come
parte dell'obiettivo di CLUT.

## Come fare

Questa sezione spiega come inserire il file identità di Hald CLUT in
modo che riproduca un rendering specifico di colore e leggerezza.

1.  Aprire una foto in RawTherapee o un altro programma di editing di
    immagini e modificarlo a piacimento. Ricorda che lo strumento di
    simulazione film può solo riprodurre i cambiamenti tonali globali,
    quindi non apportare modifiche locali: nessun contrasto locale,
    nessun mapping dei toni, ecc .; non apportare modifiche che muovano
    pixel - nessuna correzione della distorsione; non utilizzare la
    nitidezza o la riduzione del rumore; fare solo regolazioni tonali
    globali - cambiamenti di colore e saturazione, curve, livelli,
    colori e modalità film. Salvare il file sidecar o annotare le
    modifiche apportate in modo da poter riprodurre le modifiche nel
    passaggio successivo.
2.  Aprire l'immagine Hald CLUT dell'identità nello stesso programma e
    applicare lo stesso file sidecar o ripetere le stesse modifiche
    effettuate nel passaggio precedente.
3.  Salva questa immagine come un sRGB TIFF o PNG a 8 bit nella cartella
    Hald CLUT che indicaste RawTherapee. È ora pronto per l'uso.
    Riavviare RawTherapee in modo che la nuova Hald CLUT si visualizzi
    nell'elenco.

Anche se l'immagine di Hald CLUT contiene colori a precisione a 8 bit, i
valori mancanti verranno interpolati in modo che la posterizzazione non
si verifichi nella foto. In quanto tale, poiché non esiste una perdita
di qualità, si consiglia di utilizzare il file di identità di livello 12
e di memorizzare le immagini Hald CLUT create automaticamente nello
spazio colore sRGB, a 8 bit per canale. Vedere la sezione
[Caveat](film_simulation#caveat) sopra per aiutarti a
decidere se utilizzare il formato TIFF o PNG.

Se si applica questa Hald CLUT a una foto in RawTherapee e la foto
inaspettatamente e involontariamente diventa notevolmente più scura o
più leggera di quanto dovrebbe avere, allora è probabile che il
programma che hai eseguito attraverso ha fatto qualcosa con la gamma.
Per rimediare, devi annullare ciò che ha fatto quel programma. Provi a
generare i tuoi Hald CLUT a 12 livelli, ma invece di usare il colore
"sRGB" utilizzare solo "RGB".

### Avanzato - Identità del DNG

Alcuni programmi potrebbero non consentire l'apertura di un'immagine
TIFF. Se il programma supporta file DNG, e quelli demo-tagati a questo
(che cosa converte DNG di Adobe come "Lineare (Demosaiced)"), allora
puoi usare questo trucco. Utilizzando ImageMagick, ExifTool e i comandi
riportati di seguito, facendo uso del fatto che DNG è solo una forma di
TIFF, è possibile generare un'identità Hald CLUT in formato DNG:

    convert hald:12 -depth 16 -colorspace RGB -gravity NorthWest -splice 4x4 -gravity SouthEast -splice 4x4 foo.tif
    exiftool -DNGVersion=1.4.0.0 -PhotometricInterpretation='Linear Raw' foo.tif
    mv -v foo.tif Hald_CLUT_Identity_12.dng

I programmi di modifica Raw elimineranno un certo numero di righe e
colonne di pixel dai bordi dell'immagine per motivi tecnici per eseguire
la demo-sagiazione. Quante righe e colonne vengono scartate dipende
interamente dal programma. Devi capire questo. Un'identità a 12 livelli
Hald CLUT avrà precisamente 1728x1728 pixel. Quando si elaborano quel
CLUT in un programma i cui effetti di colore si sta cercando di emulare,
l'immagine salvata deve avere esattamente 1728x1728 pixel. Poiché stai
ingannando il programma nel pensare che funzioni su un file grezzo e
poiché probabilmente scarterà alcuni pixel intorno ai bordi, è
necessario capire esattamente quante righe e colonne di imbottitura sono
necessarie e aggiungerle all'immagine. RawTherapee taglia 4 pixel in
tutto quando si leggono file DNG demoedizzati, quindi il comando sopra
aggiunge una riga e una colonna di 4 pixel ai bordi inferiori e diritti,
poi un'altra riga e colonna di 4 pixel ai bordi superiore e sinistro.
Quando si apre questa immagine nel programma di destinazione, ingrandire
i bordi di ciascun lato e determinare se è necessario aggiungere più (o
rimuovere alcuni), quindi modificare il comando di conseguenza.

Una volta che hai confermato le configurazioni, apri semplicemente
questo DNG nel programma di destinazione e segui le fasi precedenti
nella sezione "Crea il tuo".

## Collezione di simulazione di film RawTherapee

Questo archivio contiene una raccolta di profili di simulazione di film
nella *Hald Color Look-Up Table (Hald CLUT) pattern*. Salvo diversa
indicazione nel nome del file, sono tutti nello spazio colore sRGB, a 8
bit per canale, nel formato di immagine PNG. La maggior parte di essi è
progettata per imitare i risultati di vari stock film, spinta e tirata
in vari modi o sbiadita nel tempo.

Applica queste immagini alle tue foto nel software Hald CLUT-capable,
come RawTherapee, per abbinare immediatamente i colori della tua foto al
riferimento scelto.

I suffissi +, ++, +++, -, --, --- si riferiscono alla forza del film
[spinto o tirato](https://en.wikipedia.org/wiki/Push_processing) durante
lo sviluppo (non lineari ) e "generico" si riferisce al tipo di
pellicola di solito venduto per il rebranding.

[Download](http://rawtherapee.com/shared/HaldCLUT.zip) (402MB!)  

<!-- -->

Changelog  
2015-09-20  
Added the "CreativePack-1" color collection.

Converted all TIFFs to PNG (except for the identity image).

2015-03-25  
The identity CLUT had a bug causing cyan colors in the highlights, it
has been replaced with a fixed one.

Numbered the files so they are sorted in the correct order when pushed
or pulled (--, -, normal, +, ++).

2014-08-25  
The first public release.

Re-organized into *Color* and *Black-and-White*, sub-folders sorted by
brand.

2014-08-15  
Expanded README.txt and added disclaimer.

2014-07-05  
The first internal release.

All images re-compressed with maximum lossless compression.

Learn more about Hald CLUTs here:

  
<http://www.quelsolaar.com/technology/clut.html>

<http://blog.patdavid.net/2013/08/film-emulation-presets-in-gmic-gimp.html>

<http://blog.patdavid.net/2013/09/film-emulation-presets-in-gmic-gimp.html>

Credits:

  
Pat David -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=5101>

Pavlov Dmitry -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=5592>

Michael Ezra -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=1442>

Disclaimer:

  
The trademarked names which may appear in the filenames of the Hald CLUT
images are there for informational purposes only. They serve only to
inform the user which film stock the given Hald CLUT image is designed
to approximate. As there is no way to convey this information other than
by using the trademarked name, we believe this constitutes fair use.
Neither the publisher nor the authors are affiliated with or endorsed by
the companies that own the trademarks.
