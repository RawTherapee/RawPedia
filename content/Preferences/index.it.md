---
title: Preferences
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

Puoi accedere alla finestra delle Preferenze cliccando sul bottone
[image:Gtk-preferences.png](image:gtk-preferences.png) che si
trova in basso a sinistra della finestra di RawTherapee, oppure in alto
a destra, dipende dall'impostazione della [Modalità Scheda Sviluppo
Immagine](The_Image_Editor_Tab/it#Editor_Tab_Modes.md).

Nota: Quando si avvia RawTherapee non solo facendo clic sul
collegamento, ma passando un nome di file dell'immagine come argomento
in modo che l'immagine sia aperta direttamente, RawTherapee verrà
eseguito in "[senza
Navigatore](The_Image_Editor_Tab/it#Editor_Tab_Modes.md)". Il
pulsante Preferenze manca quando RawTherapee è in questa modalità.
Sbarazzarsi di questa modalità è nell'elenco TODO, vedi [issue
2238](https://github.com/Beep6581/RawTherapee/issues/2238). Per accedere
alle Preferenze, assicurati di avviare RawTherapee normalmente senza
passare un file per agomento.

## Informazioni

Mostra informazioni sulla versione corrente e sull'autore di
RawTherapee, i dettagli della build, i nomi degli sviluppatori e altri
sviluppatore oltre alla licenza in base alla quale RawTherapee è
pubblicato: [GPLv3](https://en.wikipedia.org/wiki/GPLv3)

## Tab Generale

### Disposizione

RawTherapee usa le seguenti modalità:

- Modalità a scheda singola
- Modalità a scheda singola, schede verticali
- Modalità a schede multiple
- Modalità a schede multiple (se presente secondo monitor)

Ricorda che se si utilizzano più schede "Modifica", ognuna richiede una
notevole quantità di RAM. Utilizza solo più schede Editor se hai
abbastanza RAM (esattamente quanto dipende da quale risoluzione sono le
immagini, quali strumenti utilizzati, quanti altri programmi eseguiti in
background, ecc.).

E' richiesto un riavvio del programma se si cambia una di queste opzioni
per avere effetto.

### Lingua predefinita

Seleziona una lingua per l'interfaccia utente.

Se vuoi contribuire all'aggiornando di una delle traduzioni o crearne
una nuova, vedi questo post:

  
<https://discuss.pixls.us/t/localization-how-to-translate-rawtherapee-and-rawpedia/2594>

E' richiesto un riavvio per cambiare la lingua del programma.

### Tema predefinito

<figure>
<img src="/images/Image_editor.png"
title="La scheda sviluppo immagine mostra: (1) il colore dello sfondo, (2) la maschera di ritaglio, (3) raccoglitori di colore bloccabili e (4) pulsanti che alternano il colore dello sfondo di anteprima tra nero, bianco e predefinito." />
<figcaption>La scheda sviluppo immagine mostra: (1) il colore dello
sfondo, (2) la maschera di ritaglio, (3) raccoglitori di colore
bloccabili e (4) pulsanti che alternano il colore dello sfondo di
anteprima tra nero, bianco e predefinito.</figcaption>
</figure>

- Scegli un tema per l'interfaccia utente. La maggior parte degli
  elementi di interfaccia utilizzerà il nuovo tema non appena si accetta
  con "OK", mentre altri si aggiornano solo dopo aver riavviato
  RawTherapee.

  
Il modo in cui la visione umana percepisce i colori dipende da vari
fattori, di particolare importanza per questo paragrafo, le proprietà
dell'area che circonda la regione osservata. Il modo in cui si
percepisce i colori di una fotografia visualizzata sullo schermo dipende
dai colori dell'area che circonda la fotografia. Potete leggere di più
su questo nel articolo [CIECAM02](ciecam02). Al fine di
mitigare gli errori che l'utente effettua durante la regolazione di una
foto, RawTherapee usa temi che utilizzano i colori di sfondo neutri.
Mentre tutti i temi sono basati su sfumature di grigio, il tema più
adatto per evitare di influenzare la percezione umana è "TooWaGrey -
Media Surround", disponibile dalla versione 5.2.1 in avanti.

- Scegli un carattere principale personalizzato e un carattere per il
  selezionatore di colori bloccabile nella finestra [Sviluppo
  Immagine](The_Image_Editor_Tab.md), contrassegnata con "3"
  nello screenshot.

<!-- -->

- "Il ritaglo della maschera colore trasparenza" regola il colore e la
  trasparenza dell'area esterna di una regione selezionata,
  contrassegnata da "2" nello screenshot. Facendo clic sul pulsante
  colorato, viene visualizzata una nuova finestra in cui è possibile
  selezionare un colore standard oppure fare clic su "Personalizzato"
  per specificare un nuovo colore. L'asse verticale regola la tonalità,
  mentre l'asse orizzontale regola la trasparenza. La trasparenza
  parziale è utile in quanto permette alla parte ritagliata della foto
  di rimanere un pò'visibile (2), in modo da poter spostare il ritaglio
  per trovare la migliore composizione (premi il tasto **Shift** e muovi
  il ritaglio con il mouse).

<figure>
<img src="/images/Image_editor_navigator.png"
title="La scheda Navigatore mostra: (1) il pannello Navigatore, (2) la guida del Navigatore che segna l&#39;area attualmente visibile nell&#39;anteprima principale quando si ingrandisce." />
<figcaption>La scheda Navigatore mostra: (1) il pannello Navigatore, (2)
la guida del Navigatore che segna l'area attualmente visibile
nell'anteprima principale quando si ingrandisce.</figcaption>
</figure>

- La "Guida del Navigatore" consente di regolare il colore della cornice
  (contrassegnata con "2" nel secondo screenshot) visibile nel pannello
  [Navigatore](the_image_editor_tab/it#navigator)
  (contrassegnato con "1") quando l'anteprima principale viene
  ingrandita.

### Indicazione di ritaglio

Quando l'ombra del ritaglio [image:
Warnsh.png](image:_Warnsh.png.md)/[image:
Warnhl.png](image:_Warnhl.png.md) è attivata nell'anteprima, le
aree che vengono tagliate in almeno un canale sono verniciate in un
colore solido. L'ombra di questo colore dipende dalla forza di taglio. I
valori di soglia determinano quando il ritaglio è considerato iniziato.
Gli indicatori di ritaglio vengono calcolati sull'immagine finale dello
spazio colore in uscita selezionato per quella immagine nel pannello
[Gestione colori](color_management/it#output_profile).

### Amplificazione dell'ingrandimento panoramico

Immagina di aprire un'immagine ad alta risoluzione e si ingrandisca al
100%. Per spostarsi in giro sull'immagine (si chiama "panoramica")
dovresti eseguire più movimenti del mouse (o avere un pad molto grande
del mouse!). RawTherapee ti aiuta in questo con l'utilizzo di
"amplificazione della frequenza di pan" - quando impostato su 5,
RawTherapee moltiplica ogni pixel che si accende per 5. Se si muove
normalmente il cursore 500 pixel in un movimento del mouse, avrai un
movimento di 2500 pixel nell'immagine se questa opzione è impostata su
5.

L'effetto è molto visibile con forti ingrandimenti, meno visibile con
piccoli ingrndimenti.

### Editor esterno

È possibile che RawTherapee invii l'immagine elaborata direttamente ad
un programma esterno, ad esempio un visualizzatore di immagini, un
editor di immagini o uno script. Lo si fa utilizzando l'opzione ![File:
Image-editor.png](_Image-editor.png "File: Image-editor.png") "[Modifica
immagine corrente in Editor
esterno](Edit_Current_Image_in_External_Editor/it.md)" nella
scheda Editor sotto l'anteprima principale, vedere l'articolo
[Salvataggio](saving/it). In Preferenze è possibile
personalizzare a quale programma deve essere inviata l'immagine
elaborata quando si fa clic sul pulsante.

- Windows

  
Se usi Windows, RawTherapee permette di impostare il percorso per GIMP,
Photoshop, e qualsiasi altro programma ("Linea di comando
personalizzata").

Il modo consigliato per impostare l'opzione GIMP prevede di indicare il
percorso `bin` che contiene l'eseguibile di GIMP, `gimp-2.*.exe`. Se
invece si utilizza una versione non ufficiale di GIMP in cui
l'eseguibile non dispone di tale nome, potrebbe essere necessario
utilizzare l'opzione di riga di comando.

Per l'opzione Photoshop, indicare la cartella che contiene l'eseguibile
Photoshop, `Photoshop.exe`

Per l'opzione a riga di comando, scrivere semplicemente il percorso
completo compreso l'eseguibile. Non preoccupatevi di spazi o dei
caratteri backslash. Le variabili di amiente come `%ProgramFiles%` non
sono supportate.

Esempi:

  
`C:\Program Files\Gimp-2.9\gimp-2.9.exe`

`C:\Program Files\Digital Light & Color\Picture Window Pro 6.0\pw60.exe`

- Linux

  
Se usi Linux, l'opzione GIMP è codificata in modo da trovare
l'eseguibile GIMP `gimp` ovunque.

Per l'opzione a riga di comando, scrivere semplicemente il percorso
completo compreso l'eseguibile. Potrebbe essere necessario racchiudere
l'intera riga in virgolette doppie se si devono passare degli argomenti,
vedere l'esempio. Variabili di ambiente come `~` oppure `$HOME` non sono
supportate.

Esempi:

  
`"/usr/bin/geeqie --remote"`

: Il comando precedente apre l'immagine in un'unica istanza di Geeqie. Si noti che è necessario racchiuderlo in virgolette doppie perché si passa l'opzione "--remote".  
  
`/home/bob/programs/luminance hdr/luminance-hdr`

: Il comand precedente apre il programma Luminance HDR. Non sono stati approvati argomenti o opzioni in modo che non richiedere virgolette.  

- macOS

  
Se usi macOS, l'opzione GIMP è codificata `open -a GIMP` come pure
l'opzione di Photoshop è codificata `open -a Photoshop`

A linea di comando, scrivi `open -a "Programma esterno"` dove
`"Programma esterno"` è il nome del programma che si vuole utilizzare
per aprire l'immagine. Racchiudere il nome del programma con virgolette
se contiene uno o più caratteri spazio.

Esempi:

  
`open -a "Adobe Photoshop CS6"`

: Il comando apre l'immagine in Adobe Photoshop CS6. Si noti che è necessario racchiuderlo in virgolette perché contiene caratteri spazio.  
  
`open -a "Affinity Photo Trial"`

: Il comando precedente apre la versione di prova di Photo Affinity. E' stato racchiuso tra virgolette a causa degli spazi del nome.  
  
`open -a "/My stuff/Programs/Pixel Mixer"`

: Il comando sopra apre un programma chiamato "Pixel Mixer" nella cartella "My stuff". Abbiamo indicazioni sul fatto che non è necessario scrivere il percorso completo al programma anche se non risiede nella cartella standard `/Applications/`.  

## Il Tab di elaborazione immagine

### Profili di sviluppo predefiniti

Specifica quale profilo viene utilizzato quando RawTherapee apre
un'immagine, raw o non raw. Una volta che hai creato il tuo profilo
predefinito, puoi utilizzare RawTherapee per salvarlo nella
sottocartella "*profiles*" della cartella "*config*". Puoi sapere dove
si trova leggendo la pagina [Percorsi dei
file](File_paths/it#Processing_Profiles.md).

Il profilo di sviluppo migliore per i file non-raw (come JPEG, TIFF or
PNG) è sicuramente "Neutral". Il profilo "Neutral" semplicemente legge
la foto così com'è, senza applicare nessuna modifica.

La voce speciale "(Dynamic)" attiva il supporto per [Profili di
elaborazione dinamici](Dynamic_processing_profiles/it.md).

Quando si fa clic con il pulsante destro del mouse su una miniatura e si
seleziona "Operazioni di profilo di elaborazione\>Ripristina su default"
RawTherapee applica qualunque profilo di elaborazione sia selezionato
come predefinito per quel tipo di immagine. Se l'impostazione
predefinita è impostata su "(Dynamic)", RawTherapee genera un profilo
dinamico quando si usa "Reset a default".

### Costruire Profili di elaborazione personalizzati

Il file eseguibile (o script) viene chiamato quando si deve generare un
nuovo profilo di elaborazione iniziale per un'immagine. Il percorso del
file di comunicazione (\* .ini style, a.k.a. "Keyfile") viene aggiunto
come parametro di riga di comando. Esso contiene vari parametri
necessari per l'eseguibile o lo script per consentire una generazione di
profilo di elaborazione basata su regole.

Questa caratteristica è molto potente; per esempio consente di impostare
parametri di correzione dell'obiettivo o riduzione del rumore in base
alle proprietà dell'immagine. Viene chiamata una sola volta nella prima
modifica dell'immagine o chiamata manualmente dal menu contestuale
quando fa clic con il pulsante destro del mouse su una miniatura nel
[Navigatore](the_file_browser_tab/it) o[Sequenza di
immagini](The_Image_Editor_Tab/it#The_Filmstrip.md)

<b>Nota:</b> Se si utilizza percorsi che contengono spazi, si è
responsabili dell'utilizzo di doppie virgolette.

### Gestori dei Profili di elaborazione

Quando selezionato "Salva i profili di elaborazione accanto al file di
input" RawTherapee scrive un file PP3 con tutte le modifiche apportate
alla tua foto accanto al file di input (raw). Questo rappresenta il tuo
lavoro (ad esempio, le impostazioni di risoluzione utilizzate) e può
essere ricaricato in un secondo momento.

Selezionare l'opzione "Salva i profili di elaborazione nella cache" crea
un file PP3 accanto all'immagine raw nella cache. Quando si seleziona
solo l'ultima opzione, è possibile che si perde le modifiche quando si
installa RawTherapee su un nuovo PC, per esempio.

Di solito è consigliabile salvare solo i parametri di elaborazione
accanto al file di input, poiché puoi, ad esempio, riprenderli insieme
con i tuoi scatti raws.

### Dark-Frame

Specificare la directory del disco rigido per cercare i dark frame per
una sottrazione di rumore a lunga esposizione. Il file con coordinate
che elenca i pixel difettosi deve essere inserito nella stessa directory
per la correzione automatica.

### Flat-Field

Specificare la directory del disco rigido per la ricerca delle immagini
di riferimento del Flat-Field.

### Film Simulation

Specifica il percorso che contiene i preset HaldCLUT della simulazione
pellicola. Leggi l'articolo [Siulazione
Pellicola](Film_Simulation/it.md) per maggiori informazioni.

### Metadati

L'opzione "Copy Exif/IPTC/XMP nel file di output" modifica il
comportamento di gestione di metadati di RawTherapee.

- Abilitato, copia le informazioni Exif (incluse le macro), XMP e IPTC
  dall'immagine di input all'immagine di output invariata. Vorrete
  mantenerlo abilitato se decidete di modificare l'immagine salvata da
  RawTherapee su un altro programma mantenendo così invariate la
  classificazione, la descrizione o la didascalia. Tuttavia, se si
  aggiungono, eliminano o modificano i metadati Exif o IPTC utilizzando
  la scheda "Meta" di RawTherapee, anche con questa opzione abilitata,
  le modifiche verranno perse - non saranno presenti nell'immagine
  salvata!
- Disabilitato, RawTherapee salverà solo i metadati nel file di output
  che è abilitato nella scheda "Meta" - per impostazione predefinita
  tutti i metadati sono abilitati. Se si aggiunge, elimina o modifica i
  metadati Exif (inclusi i macro), IPTC o XMP utilizzando la scheda
  "Meta" di RawTherapee, disattivare questa opzione.

## Tab delle regole dei Profili di sviluppo dinamici

Qui puoi specificare le tue regole per creare [Profili di sviluppo
dinamici](Dynamic_processing_profiles/it.md).

## Tab Navigatore

### Percorso delle immagini all'avvio

Nella parte superiore è possibile definire la directory di immagine da
utilizzare all'avvio. Potrebbe essere la directory di installazione di
RawTherapee, la directory ultima visitata, la directory principale o una
directory personalizzata.

### Navigatore / Opzioni Miniature

Queste opzioni determinano quali informazioni sono visibili nelle
miniature e come dovrebbe essere visualizzate.

### Opzioni del Menu contestuale

Regola il raggruppamento del menu contestuale con il pulsante destro del
mouse in [Navigatore](the_file_browser_tab/it) (e[Sequenza
Immagini](The_Image_Editor_Tab/it#The_Filmstrip.md)).

### Estensioni analizzate

Scegliere quali file vengono riconosciuti come immagini e visualizzare
nella [Scheda Navifatore](the_file_browser_tab). Tutte le
estensioni supportate sono impostate come predefinite. Possono essere
disattivati deselezionando la relativa casella. Se manca un'estensione
desiderata, è possibile aggiungerla facilmente utilizzando il pulsante
più.

### Opzioni di cache

Queste opzioni influenzano la velocità di caricamento e generazione di
anteprime. Queste opzioni sono abbastanza esplicative.

## Scheda Gestione Colore

La scheda "Gestione Colore" consente di definire la directory in cui si
trovano i profili ICC.

### Monitor

Dovresti definire qui il profilo ICC del tuo monitor quando hai fatto
una calibrazione. Se non lo fai, l'immagine potrebbe essere visualizzata
con colori sbagliati.

L'opzione "Utilizza il profilo di colore del monitor principale del
sistema operativo" è attualmente supportata solo su Windows e supporta
solo un monitor. Se si dispone di più monitor collegati, sarà sempre il
profilo del monitor principale (quello con la barra delle applicazioni).

Su macOS tutti i colori visualizzati sono dello [spazio
sRGB](https://en.wikipedia.org/wiki/SRGB) e quindi, se necessario,
convertiti dalla pipeline di colore nativo macOS per corrispondere alla
calibrazione dello schermo, se presente. Ciò significa che non è
possibile scegliere un profilo di colore del monitor su MACOS. I colori
verranno visualizzati correttamente, anche su più schermate, ma se si
dispone di uno schermo a gamma larga i colori visualizzati di
RawTherapee restano limitati a sRGB. Ciò tuttavia non influisce
sull'uscita, cioè si possono ancora produrre immagini con colori fuori
dello spazio sRGB.

La versione Linux non supporta il rilevamento automatico del profilo del
monitor, ma fintanto che carichi lo stesso profilo ICC utilizzato nella
calibrazione, i colori verranno gestiti e avrai il pieno utilizzo del
tuo monitor a gamma ampia, se ne hai uno. Se si dispone di più monitor
con profili diversi, è necessario scegliere un elemento primario per il
colore corretto e visualizzare la finestra RawTherapee.

Vedere sotto per Rendering Intent una compensazione Black Point.

### Stampante (Soft-Proofing)

È possibile selezionare qui il profilo di colore della propria stampante
o del servizio di stampa per simulare la visualizzazione dell'immagine
stampata.

Vedi sotto per Black Point Compensation.

### Intento di Rendering

Il menu a discesa "[Intento di
rendering](https://en.wikipedia.org/wiki/Rendering_intent#Rendering_intent)"
consente di scegliere come utilizzare i profili ICC per la traduzione
tra gamut o spazi colore.

Percentuale  
Se la gamma di colori della tua immagine è superiore a quella del
dispositivo di destinazione (monitor o stampante), allora viene
compressa per quanto possibile per adattarsi al gamut del dispositivo di
destinazione. Ciò potrebbe provocare un'immagine con una saturazione
ridotta, ma la tonalità è comunque mantenuta. Potrebbe sembrare un po'
meno brillante. Ma questo effetto non è molto visibile in quanto i
rapporti tra i colori rimangono gli stessi. Questo metodo è attivo per
impostazione predefinita (consigliato).

<!-- -->

Colorimetrico relativo  
I colori esistenti sia dell'immagine che del dispositivo vengono
mantenuti e mostrati perfettamente al 100% nel gamut di colore. Se il
colore non esiste all'interno della gamma di colori del dispositivo,
viene preso il valore più vicino possibile. Ciò potrebbe portare ad
alcuni effetti di "banding", particolarmente visibili nel cielo azzurro.
Il punto bianco verrà corretto.

<!-- -->

Colorimetrico assoluto  
Simile al colorimetrico relativo. Tenta di riprodurre i colori esatti
registrati nella scena originale. Il punto bianco non verrà corretto.
Normalmente viene utilizzato quando i gamut dell'immagine e del
dispositivo sono quasi uguali. Utilizzato quando è necessaria una
riproduzione esatta di colori specifici, ad es. tessuti o logo.

### Compensazione del punto di nero

Quando abilitato, il livello del punto nero dell'immagine di ingresso
viene spostato sul livello del punto nero dell'immagine in uscita in una
trasformazione di colore (ad esempio dal profilo di lavoro al profilo
del monitor). Significa che il canale di luminanza è compresso o
ampliato per adattarsi alle capacità del dispositivo di output. Questa
caratteristica manterrà i dettagli nelle ombre (evita le aree scure
piatte) a scapito di una minore correttezza del colore.

## Sceda di elaborazione in serie (Batch processing)

Batch processing è la capacità di elaborare nello stesso tempo le
diverse immagini della [Scheda
Navigatore](The_File_Browser_Tab/it.md). Ecco perché c'è un
pannello degli strumenti nel "Navigatore". Sembra lo stesso del pannello
degli strumenti della [Scheda modifica delle
immagini](The_Image_Editor_Tab/.md), ma poiché ti permette di
modificare molti file in una sola volta, ci riferiamo come "pannello
degli strumenti batch". Le caselle di controllo qui hanno tre stati:

`[ ]` Disabilitato

`[✓]` Abilitato

`[-]` I valori si differenziano tra le immagini selezionate.

L'elaborazione in Batch si realizza con la selezione di più di
un'immagine con i tasti **Shift** o**Control** nel
[Navigatore](the_file_browser_tab/it), e al conseguente
modifica delle immagini con gli strumenti del pannello degli strumenti
batch a destra. Il modo in cui i valori dei cursori vengono utilizzati
per modificare l'immagine dipende dalle opzioni impostate in questa
scheda "Elaborazione batch".

Quando si seleziona un'immagine singola, i cursori ottengono i valori
dei parametri di elaborazione di quella immagine specifica. Questi
possono essere i valori del profilo predefinito o dei valori dell'ultima
sessione di modifica di questa foto. Se l'immagine è attualmente in fase
di modifica nella [Scheda Modifica
Immagine](The_Image_Editor_Tab/it.md), i valori dell'editor
verranno riflessi in tempo reale nel pannello degli strumenti batch e
viceversa, quindi poni attenzione a quello che stai facendo.

Quando si seleziona più di un'immagine nel "File Browser", l'azione dei
cursori dello strumento dipende dalla modalità di elaborazione batch di
tale strumento. Gli strumenti non elencati funzionano come se fossero
nella modalità "Set".

La modalità "Aggiungi"  
Questa modalità può anche essere intesa come "relativa". Modificando i
cursori impostati sulla modalità "Aggiungi", il valore della modifica
viene aggiunto al valore esistente. Ad esempio, se si selezionano due
immagini tenendo premuto il tasto modificatore **Ctrl**, un'immagine che
ha un'opzione [Exposure#Exposure_Compensation Compensazione
Esposizione](Exposure#Exposure_Compensation_Compensazione_Esposizione.md)
-0,5 EV e l'altra che ha +1,0 EV, spostando Il cursore "Compensazione
dell'esposizione" fino a +0.3 comporterà un valore di -0,2 EV per la
prima immagine e +1,3 EV per il secondo.

<!-- -->

  
Utilizzando il pulsante "Reset" si sposta il cursore alla sua posizione
predefinita (zero) e quindi riprenderà il valore iniziale di quel
cursore per ogni immagine selezionata.

<!-- -->

La modalità "Set"  
Questa modalità può anche essere intesa come "assoluta". Modificando i
cursori impostati sulla modalità "Set", il valore della modifica verrà
impostato, irrilevante di quello che era il valore esistente. Se
utilizziamo lo stesso esempio precedente, spostando il cursore fino a
+0.3 EV risulterà un valore di +0.3 EV per entrambe le immagini.

<!-- -->

  
Utilizzando il pulsante "Reset" si sposta il cursore alla posizione
predefinita (diverso per ogni cursore) e quindi ripristina questo
parametro per ogni immagine.

<!-- -->

Sovrascrivi i file di output esistenti  
L'opzione "Sovrascrivi i file di output esistenti" imposta RawTherapee
per sovrascrivere le immagini esistenti. Se disattivato, le immagini
esistenti non verranno sovrascritte; allo scopo un numero di indice
viene aggiunto all'immagine che viene salvata.

per esempio. Se esiste "output.jpg" e l'opzione non è selezionata, la
nuova immagine verrà salvata come "output-1.jpg".

## Performance

La scheda "Performance" è solo per le persone che sanno cosa stanno
facendo. Permette di modificare i parametri di alcuni strumenti a basso
livello. Questi parametri prendono parte all'equilibrio tra velocità e
stabilità.

### Numero massimo di thread per la riduzione del rumore

L'algoritmo [Riduzione Rumore](noise_reduction/it) in
RawTherapee è molto potente. È anche abbastanza pesante nell'uso di CPU
e memoria. Le persone che hanno a disposizione un hardware con cui si
verificano errori causati dall'insufficienza di memoria RAM potrebbero
scoprire che abbassando questo parametro possono ridurre tali crash,
ovviamente con un costo maggiore di tempo di elaborazione.

[Riduzione Rumore](noise_reduction/it) ha un requisito di
base di 128 MB di RAM per una foto raw di 10 megapixel o 512 MB di RAM
per una da 40 megapixel e 128 MB di RAM per thread. Più thread
funzionano in parallelo, più veloce è il calcolo, ma è più elevato il
requisito di memoria RAM.

Le CPU più moderne gestiscono due thread per nucleo fisico. Conoscendao
la CPU e quanti core ha, moltiplicado questo numero per due si ottiene
il numero massimo di thread che ha senso impostare per essere in
esecuzione contemporaneamente. Chiamiamo questo numero *T
<sub>max</sub>*. Non si traggono vantaggi dal lanciare più thread di
questo parametro - in realtà probabilmente dovresti subire una piccola
penalità di velocità.

L'impostazione di questo parametro a "0" permetterà alla CPU di capire
quale sia il tipo *T <sub>max</sub>* e utilizzarlo. Se si verificano
inconvenienti dovuti a insufficienti RAM, è possibile calcolare
*T<sub>max</sub>* e utilizzare un numero inferiore.

## Tab Suoni

La scheda "Suoni" consente di impostare una notifica udibile quando
viene terminata un'operazione lunga. Attualmente è supportato solo su
Windows e Linux.

Il suono "elaborazione coda" viene riprodotto dopo l'ultima elaborazione
della [Coda di sviluppo](the_batch_queue/it). Il suono
"Elaborazione Modifica finita" viene riprodotto se l'elaborazione della
[Scheda Modifica Immagine](the_image_editor_tab) ha richiesto
più tempo del numero di secondi specificato.

I suoni possono essere disattivati disattivando la casella di controllo
"Abilita" o impostando campi con i riferimenti dei file audio a valori
vuoti.

Le caselle di testo "Al termine dell'elaborazione della coda" e "Al
termine dell'elaborazione di modifica" possono puntare a file wave
(.wav) oppure possono specificare uno dei seguenti valori:

Windows:  

- SystemAsterisk
- SystemDefault
- SystemExclamation
- SystemExit
- SystemHand
- SystemQuestion
- SystemStart
- SystemWelcome

Linux  

- bell
- camera-shutter
- complete
- dialog-warning
- dialog-information
- message
- service-login
- service-logout
- suspend-error
- trash-empty
- qualsiasi file sonoro in `/usr/share/sounds/freedesktop/stereo/`

### Problemi di suoni sotto Linux

RawTherapee si basa su libcanberra per produrre suoni.  
Se l'installazione del suono funziona ma RawTherapee non è in grado di
produrre suono,  
è possibile controllare direttamente se libcanberra funziona
correttamente eseguendo questo script di sistema:

    hello_world.sh
    --
    #!/bin/bash
    canberra-gtk-play -i phone-incoming-call -d "hello world"
    --

    chmod +x hello_word.sh
    ./hello_word.sh

Se hello_world produce un suono, puoi controllare il rawtherapee
impostando "call-in-call" in una delle caselle e provare a decodificare
un'immagine.

Possono verificarsi problemi se installato pulseaudio, hello_world
produrrà un messaggio di errore se questo accade, disattivatelo (ad
esempio: basandosi su alsa).
