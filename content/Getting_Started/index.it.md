---
title: Getting Started
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
weight: 1
---

## Benvenuto

RawTherapee è un'applicazione di elaborazione immagini
multi-piattaforma, rilasciata sotto la licenza GNU General Public
License Version 3. E' stata scritta in origine da Gábor Horváth di
Budapest, e dal 2010 lo sviluppo ha visto il contributo di un team di
persone provenienti da tutto il mondo. Piuttosto che essere un editor di
grafica raster come Photoshop o GIMP o un programma di gestione di
immagini digitali come digiKam, è destinato esattamente alla
post-produzione di immagini raw. E questo, come minimo, rende
RawTherapee uno dei programmi di elaborazione più potenti disponibili.

## Installare RawTherapee

L'utente può installare RawTherapee eseguendo il download da
<http://rawtherapee.com/downloads>. Tuttavia è anche possibile compilare
da soli il programma se lo si vuole. Questo il link [Pagina Principale
RawPedia](Main_Page/it#Compiling.md) con le istruzioni su come
farlo.

Sono disponibili diverse versioni per il download, e questo paragrafo
cercherà di spiegare la differenza tra queste alle persone che non
conoscono come funziona un sistema di versione di rilascio continuo.
Sono realizzate nuove versioni di "sviluppo" quasi ogni giorno e una o
due volte l'anno viene rilasciata una nuova versione "stabile",
realizzata con tutti i bug importanti risolti. Eventuali bug trovati
nella versione "stabile" verranno successivamente corretti nelle nuove
versioni di sviluppo e queste accumuleranno le correzioni fino alla
prossima release "stabile" diversi mesi più tardi. Queste versioni di
"sviluppo" sono anche quelle che migliorano gli strumenti esistenti e ne
aggiungono di nuovi, anche se ci vuole tempo per perfezionarle e per
assicurarsi che funzionino bene come voluto. Da un lato, le versioni
"sviluppo" hanno sempre il maggior numero di bug corretti, ma d'altra
parte i nuovi strumenti in queste versioni possono essere non
funzionanti e non corretti e nuovi bug verranno visualizzati. Se vuoi
provare nuove funzionalità, scarica l'ultima versione di "sviluppo" -
puoi approfittare di tutte le correzioni più recenti e potrai provare
nuovi strumenti e segnalarci problemi e idee al fine di scoprire nuovi
bug. Per uso generale si raccomanda l'ultima versione "stabile" che
offre un'esperienza generalmente più corretta.

## Avvio RawTherapee

![](Rt_setm_fb.png "Rt_setm_fb.png") (attualmente aperto), la Coda di
sviluppo, L'Editor e le Preferenze. 2- Pannelli utilizzati per la
navigazione in file e cartelle. 3- Miniature della cartella attualmente
aperta. 4- Filtri per limitare le miniature mostrate solo a quelle che
corrispondono ad alcuni criteri o filtri. 5- Ingrandimento e
informazioni sulle miniature. 6- Operazioni rapide dell'immagine. 7-
Sotto scheda del Navigatore: Filtro (attualmente aperto), Ispezione (per
visualizzare un'anteprima JPEG incorporata), Batch Edit (per applicare
un'impostazione a tutte le immagini selezionate) e Esportazione Veloce
(bassa qualità e bypass di alcuni strumenti per salvataggio veloce - da
non utilizzare per il salvataggio tipico!). 8- Fare clic con il pulsante
destro del mouse sul menu contestuale (in genere verrà utilizzato per
applicare un profilo di elaborazione a tutti i file selezionati).\]\] La
prima volta che si avvia RawTherapee, verrà visualizzata la scheda
[Navigatore](the_file_browser_tab/it) e potrebbe essere
vuota. Devi indicare a RawTherapee dove sono memorizzate le tue foto
raw. Utilizza il browser dell'albero di directory a sinistra nella
scheda *Navigatore* per andare alla tua cartella di foto raw e fai
doppio clic sulla cartella per aprirla. Quindi fai doppio clic su una
foto raw per iniziare a modificarla.

## Sviluppare la prima immagine

Una volta aperta una foto raw per la modifica, noterai che l'anteprima
non sembra uguale a quella del file JPEG prodotto dalla fotocamera.
L'articolo "[Eek! La mia foto raw sembra diversa rispetto dalla foto
JPEG della
fotocamera](The_Image_Editor_Tab/it#Eek.21_My_Raw_Photo_Looks_Different_than_the_Camera_JPEG.md)"
spiega perché.

La modifica viene eseguita nella scheda [Editor di
Immagini](The_Image_Editor_Tab/it.md). È qui dove lavorare con
RawTherapee per creare opere d'arte mozzafiato o forse solo applicare la
prima correzione ai tuoi scatti.
![](Rt_setm_editor.png "Rt_setm_editor.png") Prendi un attimo per
guardare intorno a questa scheda Editor principale. Tieni presente che
ci sono schede all'interno di questa scheda - a destra dello schermo in
alto. Queste schede e questi controlli sono la Casella degli strumenti.
Probabilmente hai la prima scheda aperta e, se scorri il mouse sopra,
troverai che si chiama "Esposizione". Al di sotto della linguetta scelta
ci sono gli strumenti che la scheda contiene - Esposizione, Ombre/Alte
luci, Tone Mapping etc. Se si fa clic su uno di essi si espanderà in
modo da poter visualizzare i contenuti. Fai clic di nuovo e si chiuderà.
Fai clic con il pulsante destro su uno strumento e questo si espanderà
mentre tutti gli altri saranno collassati - un collegamento per
risparmiare tempo. A sinistra di ogni etichetta dello strumento c'è un
pulsante di alimentazione che consente di attivarlo o meno oppure in
alcuni casi invece di un pulsante di alimentazione è presente un
espansore triangolare. Leggete la sezione [Considerazioni Generali su
Alcuni
Strumenti](General_Comments_About_Some_Toolbox_Widgets/it#Tools.md)
per una spiegazione dettagliata. Sfoglia le schede e i pannelli finché
non ti senti totalmente sopraffatto da tutto ciò che è disponibile.

Prima di iniziare a lavorare su un'immagine un consiglio importante -
*'Non spaventarti!'* Non c'è nessun pericolo di distruggere le tue
immagini anche se si commette un errore. RawTherapee ha alcune funzioni
che ti aiutano a proteggere le tue immagini:

- RawTherapee rende non distruttivo la modifica dei file raw. Ciò
  significa che RawTherapee non cambierà mai il file raw. Tutte le
  modifiche vengono memorizzate nei file sidecar. Potete scoprire di più
  su di loro nell'articolo [Sidecar Files - Profili di
  sviluppo](Sidecar_Files_-_Processing_Profiles/it.md).
- Quando si utilizza l'editor di immagini, verrà visualizzato il
  pannello [Cronologia](the_image_editor_tab/it#history) a
  sinistra. Questo pannello mostra una pila di tutte le modifiche
  apportate all'immagine. Per tornare indietro a qualsiasi passo (anche
  al primo quando l'immagine è stata caricata per la prima volta), fai
  clic sulla riga corrispondente nel pannello Cronologia.
- Nel pannello Storia, verrà visualizzato un pannello
  [Istantanee](the_image_editor_tab/it#snapshots). Puoi
  tralasciarlo per ora, ma lo troverai utile quando guadagnerai
  esperienza con RawTherapee. Questo pannello memorizza lo stato di
  tutti gli strumenti come "istantanee". Ciò consente di modificare, ad
  esempio, la tua foto con un aspetto piacevole e colorato e fare
  un'istantanea, quindi modificarla nuovamente in un bel look bianco e
  nero e fare un'istantanea, quindi confrontarle semplicemente facendo
  clic sulle istantanee. (Nota: RawTherapee non salva le istantanee nel
  file PP3, ma lo farà in futuro. Se hai tre istantanee che desideri
  conservare, dovrai cliccare su di esse e salvare un singolo file PP3
  ogni volta con un nome diverso).
- Come ci si può aspettare, Control-z annullerà la modifica precedente.
  (OK, it's not rocket science but it's still handy!)

### Elaborazione base

1.  Inizia con un clic sulla scheda Colore
    ![<File:Colour.png>](Colour.png "File:Colour.png") e espandi lo
    strumento [Bilanciamento del bianco](white_balance/it)
    con un clic del pulsante destro. RawTherapee inizia con il
    bilanciamento del bianco utilizzato dalla fotocamera. La maggior
    parte delle regolazioni del bilanciamento del bianco comporta lo
    spostamento dei cursori della temperatura e della tinta, è possbile
    fare in modo automatico la regolazione utilizzando il selettore
    puntiforme del bianco
    ![<File:Gtk-color-picker.png>](Gtk-color-picker.png "File:Gtk-color-picker.png")
    su una piccola area uniforme e di colore grigio neutro. Infine
    regolare a piacere.
2.  Poi correggi l'esposizione passando alla scheda Esposizione
    ![<File:Exposure.png>](Exposure.png "File:Exposure.png"), espandendo
    lo strumento [Esposizione](exposure/it) e regolandolo a
    piacere. Per ora, utilizza semplicemente i cursori Compensazione
    esposizione e Saturazione.
3.  Se l'immagine è rumorosa, passa alla scheda
    ![<File:Detail.png>](Detail.png "File:Detail.png") Dettagilo,
    zoommare al 100% usando il pulsante
    ![<File:Gtk-zoom-100.png>](Gtk-zoom-100.png "File:Gtk-zoom-100.png")
    o usando il tasto di scelta rapido "z" perché gli effetti degli
    strumenti in questa scheda sono visibili solo con l'immagine
    ingrandita (e naturalmente nell'immagine salvata) e abilitare lo
    strumento [Riduzione Rumore](noise_reduction/it)
    utilizzando per ora le impostazioni predefinite. RawTherapee rimuove
    automaticamente il rumore di colore (crominanza). Il rumore di
    luminosità viene rimosso in
    [manuale](noise_reduction/it#usage), anche se di default
    lo lascia perché il rumore di luminanza in genere conferisce un
    aspetto piacevole, granuloso e cinematografico. Come regola
    generale, quando si utilizza la riduzione del rumore non utilizzare
    la nitidezza. Per vedere l'intera immagine usa il pulsante
    ![<File:Gtk-zoom-fit.png>](Gtk-zoom-fit.png "File:Gtk-zoom-fit.png")
    o utilizza il tasto di scelta rapida "f".
4.  Ora dovresti sistemare la [geometria](lens/geometry/it) e
    la composizione della tua foto.
    - Per prima cosa imposta il livello orizzontale oppure correggi le
      linee che dovrebbero essere verticali, come lampade stradali o
      bordi delle costruzioni. Per farlo, premi il tasto "s" sulla
      tastiera (uguale a quello cliccato sul pulsante
      ![<File:Straighten.png>](Straighten.png "File:Straighten.png") e
      fai clic e trascina sull'anteprima una linea lungo l'orizzonte o
      lungo il bordo di un edificio. La tua immagine ruoterà di
      conseguenza e sarai automaticamente condotto nella scheda
      ![<File:Transform.png>](Transform.png "File:Transform.png")
      Trasforma.
    - Per ritagliare la foto, premi il tasto di scelta rapida "c" sulla
      tastiera (oppure usa il pulsante
      ![<File:Crop.png>](Crop.png "File:Crop.png") viene automaticamente
      abilitato. Non c'è bisogno di "applicare" un taglio - è efficace
      nel momento in cui si disegna. Potrebbe essere necessario
      impostare il tipo di guida "Crop" su "none" se questo non è
      corretto.
    - Infine, puoi ridimensionare la foto, perché magari la vuoi
      caricare come JPEG da 10 MB su un'applicazione social. Attiva lo
      strumento [Ridimensiona](resize/it) e lascialo alle
      impostazioni predefinite. Nota che l'effetto di ridimensionamento
      è applicato solo all'immagine salvata, non all'anteprima.
5.  Ora che è tutto impostato, puoi eseguire
    [salva](saving/it) subito. Fai clic sul pulsante
    ![<File:Gtk-save-large.png>](Gtk-save-large.png "File:Gtk-save-large.png")
    Salva l'immagine corrente, oppure utilizza la scorciatoia da
    tastiera Ctrl + s. Salva come file JPG con qualità "92", campionata
    con metodo "bilanciato". Queste sono delle buone impostazioni.
    Scegli una cartella dove lo desideri, e dopo qualche secondo il tuo
    file sarà pronto nella cartella selezionata. Se si chiude
    RawTherapee, le impostazioni utilizzate verranno salvate in un file
    [sidecar file
    PP3](Sidecar_Files_-_Processing_Profiles/it.md) accanto al
    file raw, in modo da poter aprire nuovamente la foto raw in futuro e
    conservare le impostazioni usate fino a quel momento.

Ora che hai familiarità con i passaggi di base per la correzione delle
foto, ripetiamo i passi ma con dettagli più avanzati.

### Avanzato

Leggete sempre l'articolo di ciascun strumento su RawPedia prima di
utilizzarlo, per avere una chiara comprensione di ciò che fa. Gli
articoli spiegano come gli strumenti funzionano in RawTherapee, mentre i
concetti generali che non sono specifici a RawTherapee potete trovarli
su Wikipedia o altrove.

Assicuratevi di vedere il paragrafo delle [Scorciatoie di
tastiera](Keyboard_Shortcuts/it.md).

L'ordine degli strumenti all'interno della pipeline del motore
RawTherapee è prestabilito, quindi da questo punto di vista non importa
quando si abilita o disabilita uno strumento. Tuttavia, alcuni strumenti
possono avere un grande impatto su altri strumenti, ad esempio cambiare
l'esposizione potrebbe richiedere di aggiustare la tonalità del colore
mentre alcuni strumenti potrebbero richiedere un sacco di potenza della
CPU per calcolare l'anteprima e questo rendere gli aggiornamenti
dell'anteprima molto lenti, quindi per questo motivo vi suggeriamo di
rispettare questo ordine generale di operazioni:

1.  Iniziare assicurandosi che l'ambiente di RawTherapee sia impostato
    correttamente, ovvero:
    - Assicurarsi che RawTherapee utilizzi il profilo di colore del
      monitor se utilizzate un flusso di lavoro gestito (color-managed
      workflow). Selezionare per questo Preferenze\> Gestione colori.
      Potrebbe anche essere necessario caricare le curve di calibrazione
      appropriate nella scheda grafica, se hai creato il profilo del
      colore del monitor, anche se come farlo è fuori dall'ambito di
      RawTherapee.
    - Assicurarsi che lo strumento Color Management sia configurato
      correttamente. Normalmente i valori predefiniti sono i migliori.
      Leggete gli articoli [Gestione
      Colore](Color_Management/it.md). Se, invece di utilizzare
      la matrice di colore oppure i profili DCP o ICC forniti con
      RawTherapee, si decide di utilizzarne uno esterno, ad esempio un
      DCP creato da Adobe, è necessario caricarlo come prima cosa,
      altrimenti potrebbe essere necessario ricalibrare alcuni degli
      strumenti dei colori. Utilizzare sempre un profilo di output -
      nella maggior parte dei casi il valore predefinito, RT_sRGB. Se
      pensi di essere intelligente selezionando "No ICM: sRGB Output",
      ti sbagli di sicuro.
2.  Se si desidera utilizzare gli strumenti [Flat
    Field](Flat_Field/it.md) e/o [Dark
    Frame](Dark_Frame/it.md), meglio farlo ora per evitare una
    nuova regolazione.
3.  Impostare ora il corretto [Bilanciamento del
    bianco](White_Balance/it.md). È possibile risolvere
    l'esposizione in primo luogo se l'immagine è troppo scura (o troppo
    luminosa) per vedere le modifiche del bilanciamento del bianco.
4.  Regolare l'[Esposizione](exposure/it) utilizzando
    l'opzione Compensazione dell'esposizione e i cursori dei neri per
    migliorare l'immagine nelle ombre. Una volta compensato i neri,
    continuare con l'utilizzo di entrambe le curve di tono. Assicuratevi
    di leggere la sezione [Curva di
    Tono](Exposure/it#Tone_Curves.md) nell'articolo Esposizione
    per scoprire perché ci sono due e come utilizzarle al meglio: sono
    uno strumento molto potente!
5.  Nella sezione Base di cui sopra abbiamo suggerito di utilizzare il
    cursore [Saturazione](exposure/it#saturation) (nello
    strumento Exposure). Ora che stiamo esplorando le tecniche più
    avanzate, ti consigliamo di non utilizzare più il cursore di
    saturazione e utilizzare invece la più potente [Curca
    CC](Lab_Adjustments/it#CC_Curve.md) nel tool [Correzioni
    Lab](Lab_Adjustments/it.md) in quanto ti dà molto più
    controllo.
6.  L'ordine del resto non è importante. Alcuni strumenti influenzeranno
    inevitabilmente altri. Continua con lo strumento [Correzioni
    Lab](Lab_Adjustments/it.md) e poi il resto degli strumenti
    nella scheda Esposizione.
7.  Quindi utilizzare lo strumento [Wavelet](wavelet/it)
    nella scheda Wavelet
    ![<File:wavelet.png>](wavelet.png "File:wavelet.png").
8.  Quindi utilizzare gli strumenti nella scheda Colore
    ![<File:Colour.png>](Colour.png "File:Colour.png"). Lo strumento
    [Tonalità del Colore (Color Toning)](color_toning/it) è
    particolarmente sensibile ai cambiamenti dell'esposizione, quindi
    lasciatelo per ultimo.
9.  Adesso ingrandisci al 100% e utilizza gli strumenti nella scheda
    Dettagli ![<File:Detail.png>](Detail.png "File:Detail.png").
    Generalmente, non aumentare la nitidezza se stai utilizzando la
    riduzione del rumore.
10. Infine, ridimensiona di nuovo e utilizza gli strumenti nella scheda
    Trasforma
    ![<File:Transform.png>](Transform.png "File:Transform.png"). Il
    motivo per cui questi sono lasciati per ultimi è che possono rendere
    l'immagine di anteprima sfocata privilegiando la reattività,
    RawTherapee utilizza quella stessa immagine di anteprima che vedi
    alla stessa risoluzione per mostrare ciò che gli strumenti fanno
    quando sono applicati, e quando si ruota o si cambia la geometria di
    un'immagine c'è un chiaro ammorbidimento. Questo non è un problema
    durante il salvataggio, in quanto RawTherapee fa la sua elaborazione
    sull'immagine di dimensioni complete, il metodo è lento ma di alta
    qualità.
11. Infine salva direttamente quando si desidera salvare una singola
    foto o tramite [Coda di sviluppo (Batch
    Queue)](The_Batch_Queue/it.md) quando si desidera elaborare
    molte foto.

È possibile modificare i metadati in qualsiasi momento nella scheda Meta
![<File:Meta.png>](Meta.png "File:Meta.png"). Perchè le modifiche
apportate nella scheda Meta abbiano effetto sull'immagine salvata
assicurati che "Preferenze\> Elaborazione immagine\> Copia Exif/IPTC/XMP
invariato al file di output" non sia selezionata. Se è selezionata le
modifiche apportate nella scheda Meta saranno ignorate nell'immagine
salvata.
