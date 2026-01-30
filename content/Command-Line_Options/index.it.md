---
title: Command-Line Options
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

## Spiegazione

  
`<`i caratteri`>` racchiudono i parametri che che è possibile
modificare.

`[`parentesi quadre`]` specificano che il parametro non è obbligatorio.

Il simbolo pipe `|` indica una scelta di uno o l'altro.

Il simbolo meno `-` indica una gamma di valori possibili tra uno e
l'altro.

Dalla versione di RawTherapee 5.1 sono forniti due programmi eseguibili.

### RawTherapee GUI

Usa questa applicazione per avviare il programma con la versione
grafica.

Utilizzo:

  
`rawtherapee `<selected dir>

  
Avvia [il Navigatore](the_file_browser_tab) nel percorso
indicato.

`rawtherapee `<file>

  
Avvia [il Navigatore](the_image_editor_tab) con l'immagine
indicata.

<!-- -->

  
`-w`

  
Non apre la console di Windows. Questa opzione è disponibile solo in
Windows. Se si passano i parametri all'eseguibile RawTherapee apre una
finestra di console in modo che si possa vedere l'output dettagliato
dell' esecuzione. Normalmente Windows chiude questa console subito dopo
che RawTherapee è terminato. Per consentirti di vedere l'output abbiamo
aggiunto un prompt che si blocca in attesa di premere un tasto prima di
chiudere la console. Specificando `-w` nessuna console verrà aperta e
pertanto non è necessaria alcuna pressione del tasto. Utile se si
desidera richiamare `rawtherapee.exe` in batch, ad esempio da uno script
PowerShell. Si prega di notare che `-w` non avrà alcun effetto per le
build di "Debug" in cui verrà aperta una finestra di console a meno che
non si sia già avviato RawTherapee da una finestra di console.

<!-- -->

  
`-v`

  
Stampa la versione di RawTherapee e esce.

<!-- -->

  
`-R`

  
Modalità "remota", disponibile da RawTherapee 5.2. Quando si apre
un'immagine usando "Apri con" o passando il suo nome di file come
argomento, senza utilizzare l'opzione `-R` RawTherapee si apre in
modalità "no-Navigatore" - in questa modalità mancano le schede
Navigatore e Coda di sviluppo e il pulsante Preferenze. Utilizzando la
nuova modalità `-R`, RawTherapee si aprirà in un'istanza piena.
L'utilizzo di <code>-R\</ code\> consente anche di aprire un'immagine in
un'istanza già in esecuzione di RawTherapee, se l'istanza è stata
avviata utilizzando `-R`. La modalità No-Navigatore esiste per motivi
storici quando i requisiti RAM erano più alti e la stabilità era
peggiore. Ora che l'utilizzo della memoria di RawTherapee è ottimizzato
e può aprire in modo rapido e affidabile le cartelle con migliaia di
immagini, gli utenti possono preferire la modalità `-R` per impostazione
predefinita.

<!-- -->

  
`-h -?`

  
Mostra questi comandi.

### RawTherapee CLI (Interfaccia a riga di comando)

Usa questa versione per avviare l'applicazione con la sola linea di
comando. E' possibile trovare tutti i comandi per elaborare le tue foto
senza nessuna interfaccia grafica.

Utilizzo:

  
<code>rawtherapee-cli <options> -c

<dir>

\|<files></code>

  
Converte i file in batch con i parametri predefiniti se non è stata
specificata alcuna <opzione>.

<!-- -->

  
`-w`

  
Non apre la console di Windows (come descrizione precedente con la
stessa opzione per RT con interfaccia utente).

Altre opzioni utilizzate con `-c`:

  
<code>rawtherapee-cli \[-o

<output>

\|-O

<output>

\] \[-q\] \[-a\] \[-s\|-S\] \[-p <files>\] \[-d\] \[-j\[1-100\]
\[-js\<1-3\>\]\|\[-b\<8\|16\>\] \<\[-t\[z\] \| \[-n\]\]\] \[-Y\] \[-f\]
-c <input></code>

<!-- -->

  
`-c `<files>

  
Specifica uno o piu immagini o percorsi.

Quando si specifica un percorso, RawTherapee cerca le immagini contenute
con l'estenzione impostata (vedi l'opzione `-a`).

L'opzione `-c` deve sempre essere l'ultima.

<!-- -->

  
<code>-o <file>\|

<dir>

</code>

  
Seleziona un file o percorso di uscita.

Salva il file di output accanto al file di input se -o non è
specificato.

<!-- -->

  
<code>-O <file>\|

<dir>

</code>

  
Seleziona un file o percorso di uscita e copia i file PP3 nello stesso
percorso.

Salva il file di output accanto al file di input se -O non è
specificato.

<!-- -->

  
<code>-q<file>\|

<dir>

</code>

  
Modalità di avvio rapido. Non carica i file memorizzati nella cache per
accelerare l'avvio.

<!-- -->

  
<code>-a<file>\|

<dir>

</code>

  
Processa tutti i tipi di file di immagine supportati quando si specifica
una cartella, anche quelli non selezionati in Preferenze\> Navigatore\>
Estensioni riconosciute.

<!-- -->

  
`-s`

  
Utilizza il file sidecar esistente per costruire i parametri di
elaborazione, ad esempio per photo.raw dovrebbe essere un file
photo.raw.pp3 nella stessa cartella. Se il file sidecar non esiste,
verranno utilizzati valori neutri.

<!-- -->

  
`-S`

  
Identico a `-s` ma non usatelo se non esiste il file sidecar.

<!-- -->

  
`-p <file.pp3>`

  
Specificare il profilo di elaborazione da utilizzare per tutte le
conversioni. È possibile specificare diversi profili di elaborazione con
diverse opzioni "-p \<file.pp3\>" come si desidera, ciascuna andrà a
sovrascrivere quella precedente, come spiegato di seguito.

<!-- -->

  
`-d`

  
Usa il file PP3 predefinito specificato in
"[Preferences](main_page#preferences) \> [Image
Processing](Image_Processing_Tab.md) \> [Default Processing
Profile](Image_Processing_Tab#Default_Processing_Profile.md)"

<!-- -->

  
`-j[1-100]`

  
Specifica il formato di uscita JPEG (predefinito, se -t o -n non sono
impostati).

Opzionale, specifica la compressione 1-100 (valore predefinito: 92).

<!-- -->

  
`-js<1-3>`

  
Specifica i parametri del formato JPEG [chroma
subsampling](http://en.wikipedia.org/wiki/Chroma_subsampling), dove:

  
1 = Migliore compressione: 2x2, 1x1, 1x1 (4:2:0)

  
Chroma dimezzata verticalmente e orizzontalmente.

2 = Bilanciato: 2x1, 1x1, 1x1 (4:2:2)

  
Chroma dimezzata orizzontalmente.

3 = Migliore qualità: 1x1, 1x1, 1x1 (4:4:4)

  
Nessun sottocampionamento del chroma.

<!-- -->

  
`-b<8|16>`

  
Specifica la profondità colore per canale (16 bit predefinito).

Si applica solo all'uscita TIFF e PNG, JPEG è sempre 8.

<!-- -->

  
`-t[z]`

  
Specifica i parametri del formato TIFF (16-bit se`-b8` non è impostato).

Non compresso per impostazione predefinita, o compressione ZIP con 'z'.

<!-- -->

  
`-n`

  
Specifica i parametri del formato PNG (16-bit se`-b8` non è impostato).

La compressione è codificata al livello 6.

<!-- -->

  
`-Y`

  
Sovrascrive output se presente.

<!-- -->

  
`-f`

  
Usa la coda di sviluppo per velocizzare l'esportazione.

I file PP3 possono essere incompleti, RawTherapee imposterà i valori
come segue:

1.  Viene creato un nuovo profilo di elaborazione utilizzando valori
    neutri,
2.  Con l'opzione `-d` i valori vengono sovrascritti da quelli trovati
    nel profilo predefinito di elaborazione raw o non raw,
3.  Se sono state impostate una o più opzioni `-p`, i valori vengono
    sovrascritti da quelli trovati in questi profili di elaborazione,
4.  Se sono impostate le opzioni `-s` o `-S`, i valori vengono alla fine
    sovrascritti da quelli trovati nei file sidecar. I profili di
    elaborazione vengono elaborati nell'ordine specificato sulla riga di
    comando.

## Redirect Output

Per reindirizzare l'output di RawTherapee in un file di testo, è
necessario avviarlo da una console e aggiungere il codice di
reindirizzamento come segue:

Windows (cmd.exe)  
`rawtherapee.exe > rtlog.txt 2>&1`

Linux  
`rawtherapee &> rtlog.txt`

## Esempi

### Esempio 1

Esempio in Linux per elaborare una singola immagine raw "photo.raw" nel
percorso tmp, utilizzando il file sidecar "photo.raw.pp3" durante la
conversione, salvare nella stessa cartella "foo.tif" e sovrascrivere il
file "foo.tif" se esiste:

`rawtherapee-cli -o /tmp/foo.tif -s -t -Y -c /tmp/photo.raw`

### Esempio 2

Nell'esempio seguente, supponiamo che si desideri elaborare rapidamente
tutte le tue foto raw dalla cartella /tmp/jane01 in una sottocartella
web usando il profilo predefinito come base, usando il profilo sidecar
se esiste, ma con la rimozione di alcuni tag Exif (ad es. il numero di
serie della fotocamera) e l'aggiunta di alcuni tag IPTC (ad esempio i
tuoi parametri di copyright abituali), oltre a ridimensionare e affinare
l'immagine per il web (diffondere più righe per chiarezza):

`rawtherapee-cli -o /tmp/Jane01/web -p ~/profiles/iptc.pp3 -s -p ~/profiles/exif.pp3 -p ~/profiles/web.pp3 -t -Y -d -c /tmp/Jane01/`

Il profilo di elaborazione sarà costruito come segue:

1.  Viene creato un nuovo profilo utilizzando i valori predefiniti
    (hard-coded in RawTherapee),
2.  questo viene sovrascritto da quello del profilo raw predefinito
    (`-d`),
3.  poi viene sovrascritto da quello trovato in iptc.pp3,
4.  quindi sovrascritto da quello trovato nel file sidecar (`-s`) se
    esiste, in modo da poter forzare alcuni tag IPTC anche se già
    impostati da iptc.pp3,
5.  quindi sovrascritto adesso da quello trovato in exif.pp3, in modo da
    poter forzare il profilo per cancellare alcuni tag,
6.  infine sovrascritto da quello trovato in web.pp3 per ridimensionare
    e aumentare la nitidezza dell'immagine e assicurarsi che l'area
    colori color output sia sRGB.

Come potete vedere, la posizione del commutatore `-s` indica quando
caricare il profilo del sidecar rispetto agli altri parametri `-p`.
Questo non è il caso per il parametro `-d`.

### Esempio 3

Nel terzo esempio, vedremo quanto tempo ci vuole per elaborare ogni file
raw in una cartella, supponendo che ogni foto raw abbia un
corrispondente profilo di elaborazione e scarta ogni file di output:

`time { for f in /home/user/photos/2011-11-11/*.raw; do rawtherapee-cli -o /dev/null -S -t -Y -c "$f"; done }`
