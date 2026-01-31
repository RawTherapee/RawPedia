---
title: CIECAM02
contributors:
  - Andrea.romagnoli
  - DrSlony
tags:
  - 'Tool Description'
  - 'Advanced Tab'
---

Di J.Desmis

## Circa CIECAM02

### Introduzione - storia

Da molti anni, gli uomini cercano di modellare i colori, la sua
percezione da parte dei popoli. Molti lavori sono stati fatti negli anni
dalla Medio Evo, ma è solo a partire dal XIX secolo, poi nel ventesimo
secolo che sono state fatte le scoperte principali.

Non sono uno specialista della fisiologia del sistema visivo umano, né
un ricercatore nel complesso dominio della colorimetria. Ho raccolto
alcune informazioni basilari che sono state essenziali per la
comprensione, sono così diventato un lettore interessato e ho arricchito
le mie conoscienza grazie al Web e agli elementi che ho raccolto.

Di solito nella fotografia, usiamo modelli (con più di) di 50 anni: RGB
e i derivati (HSV, HSL, CMYK, ...), XYZ e Lab e i suoi derivati (Luv,
Lch). Non mi soffermo sul modello RGB, conosciuto da tutti, dipende
dalla periferica e non tiene conto di nessun CAM (modello di aspetto del
colore). La definizione di XYZ (1931) del CIE è stata la prima tappa
della « Commission Internationale de l'Éclairage » (CIE - Commissione
Internazionale sull'Illuminazione) verso una descrizione dei colori
percepiti dalla visione umana. Riassumendo, un colore può essere
caratterizzato dai suoi valori X, Y e Z ottenuti da una combinazione di
3 valori, detto «tristrimulus», da un «osservatore standard CIE»
generato da una «distribuzione dello spettro di potenza» del colore
stesso. Questo modello è stato ripreso in RawTherapee, in particolare in
termini di bilanciamento del bianco ... Questo modello non tiene conto
del CAM, ma è un salto straordinario in avanti, perché ora possiamo
modellare un colore in termini cognitivi.

Il modello Lab è stato progettato nel 1976 dalla CIE derivandola dal
modello XYZ, caratterizzando un colore con un parametro di intensità
corrispondente alla luminanza e due parametri di crominanza che
descrivono il colore. È stato studiato in modo specifico in modo che la
distanza calcolata tra i colori corrisponda alle differenze percepite
dall'occhio umano. Il modello Lab è ben radicato in RawTherapee, è
utilizzato come base per la maggior parte degli strumenti: risoluzione,
rimozione rumore, mappatura dei toni, aggiustamenti Lab, ecc. Integra
alcune caratteristiche di un CAM, ma i vantaggi sono insufficienti. Il
modello CIECAM02, deriva dal modello CIECAM97 e attinge al lavoro di
G.Hunt, è il primo modello comunemente utilizzabile nella fotografia,
perché è invertibile ... e relativamente "semplice", può tener conto di
altri aspetti puramente cognitivi e si basa sul lavoro di molti
ricercatori sulla base di campioni di persone che valutano parametri
diversi, come:

1.  contrasto simultaneo: variazione dell'aspetto colorato di un oggetto
    a seconda delle caratteristiche colorimetriche dell'ambiente
    circostante. Ad esempio, lo stesso colore verrà percepito in modo
    diverso su uno sfondo bianco o scuro. Più sarà scuro lo sfondo, più
    dovremo aumentare i colori ...
2.  effetto di Hunt: l'occhio percepisce maggiore colorazione
    (saturazione) con maggiore luminanza. Un oggetto appare più vivido e
    contrastante in piena luce che in ombra.
3.  effetto di Stevens: aumento del contrasto percepito con la
    luminanza. Quando la luminanza aumenta, i colori scuri sembrano
    ancora più scuri e i colori luminosi appaiono ancora più luminosi.
4.  effetto Helmholtz-Kohlrausch's: dipendenza della luminosità rispetto
    alla luminanza e alla cromaticità. Gli oggetti colorati appaiono più
    luminosi degli oggetti acromatici con la stessa luminanza. I colori
    più saturi appaiono più luminosi.
5.  Adattamento cromatico: regolazione del sistema di visione umana ad
    alcuni stimoli di colore. L'adattamento cromatico ci permette di
    interpretare un colore a seconda dell'ambiente spaziale e temporale.
    È un effetto fondamentale da utilizzare per il CAM.

L'adattamento cromatico è la capacità del sistema visivo umano di
adattarsi alle mutevoli condizioni di illuminazione. In altre parole, ci
adattiamo al colore della sorgente luminosa per preservare meglio il
colore degli oggetti. Ad esempio, sotto la luce incandescente, una carta
bianca appare gialla. Tuttavia, abbiamo la capacità di modellare
automaticamente la luce giallastra in modo da vedere come carta bianca.
Il mondo intorno a noi sarebbe molto complicato se gli oggetti
cambiassero il colore ogni volta che la sorgente luminosa cambia
leggermente. Dall'alba del tempo, dobbiamo essere in grado di sapere se
un frutto è maturo, sia il mattino, il pomeriggio o la sera.
L'adattamento cromatico rende questo possibile. Ma può anche essere la
fonte di molte illusioni ottiche. Penso che la maggioranza degli utenti
RT conosca, almeno per nome, il precedente modello di adattamento
cromatico, chiamato "Bradford". ecc.

Nota: qui non ci sarà alcuna questione di "Munsell Correction" perché
CIECAM02 è, in linea di principio, costruito intorno alle tabelle di
Munsell ... quindi questa correzione viene presa in considerazione,
anche se il modello ha delle carenze!

I miei primi pensieri su CIECAM02 risalgono al 2007 e lo sviluppo di un
foglio di calcolo per ottenere i migliori risultati nello sviluppo dei
"profili di input" della ICC. All'inizio del 2012, ho inviato una
richiesta agli utenti: "Possiamo avere colori di riferimento - tavolozza
dei colori - (pelle, cielo, ..) che consentirebbe un migliore
bilanciamento del bianco attraverso un processo di
confronto/iterazione". Ho anche lavorato al concetto di CRI (Color
rendering index - Indice di rendimento dei colori) che riflette la
differenza di illuminanti rispetto ad un illuminatore di base ... Più
basso è il CRI, peggio la resa sarà con una stessa temperatura di colore
vedi: [Color_Management/fr](color_management/fr))

Basato su CIECAM02, la patch contiene gli elementi di base necessari per
lavorare questi due punti, ma manca di un elemento essenziale, non
facile da sviluppare: una pipetta. Ho da tempo considerato CIECAM02, non
come sconfitta, ma come qualcosa di difficile da implementare ... e con
un bonus piuttosto piccolo rispetto a Lab. La richiesta di Michael Ezra,
che mi ha sorpreso in un primo momento, mi ha spinto a riaprire il file;
la scoperta del plug-in per Photoshop è stato per me da esempio, di
CIECAM02. Ora sono convinto che, anche se il modello non è perfetto (per
alcune immagini, il suo utilizzo è quasi impossibile!), è comunque il
più efficace in termini di gestione del colore. Il modulo che propongo è
un punto di partenza. Dai dati di CIECAM02, è possibile sviluppare una
serie di funzionalità simili a quelle già sviluppate in RT (correzioni
Lab con varie curve, mappatura dei toni, ecc.). Probabilmente con
notevoli progressi in termini di qualità.

La mancanza di una documentazione efficace aggiunge la complessità ...
Alcuni punti di vista sono personali (possono essere contaminati da
errori?). Se uno specialista legge queste righe, sarò felice di cambiare
il mio testo e i miei algoritmi!

### Alcune definizioni

1.  Luminosità (Brightness) \[brillantezza - brilliance\] (CIECAM02):
      
    La quantità di luce percepita da uno stimolo = indicatore che uno
    stimolo appare più o meno luminoso, luminoso.
2.  Chiarezza (Lightness) \[luminanza - luminance\](Lab, CIECAM02):
      
    La chiarezza di uno stimolo rispetto alla luminosità di uno stimolo
    che appare bianco in condizioni di visualizzazione simili.

    Si noti che in RT, il termine “brightness”("luminosità") si applica
    per “Llightness” ("hiarezza")! Dovrai creare una patch per
    rinominare la "brightness" in "lightness" negli strumenti
    "esposizione", "Correzioni Lab" ecc.
3.  Angolo di tonalità e tonalità (in parte in Lab, CIECAM02):
      
    Il grado a cui uno stimolo può essere descritto come simile a un
    colore descritto come rosso, verde, blu e giallo.
4.  Vividezza (Colorfulness) (CIECAM02):
      
    La quantità percepita di colore rispetto al grigio = indicatore che
    uno stimolo sembra essere più o meno colorato.
5.  Cromaticità (Chroma) (Lab, CIECAM02):
      
    La "colorazione" di uno stimolo rispetto alla luminosità di uno
    stimolo che appare bianco in condizioni identiche.
6.  Saturazione (CIECAM02):
      
    Colorazione di uno stimolo relativo alla propria luminosità.

Riassumere :

1.  Cromaticità = (Vividezza) / (Luminosità del bianco)
2.  Saturazione = (Vividezza) / (Luminosità)
3.  Chiarezza = (Luminosità) / (Luminosità del bianco)
4.  Saturazione = (Cromaticità) / (Chiarezza)
      
      
    = \[(Vividezza) / (Luminosità del bianco)\] x \[(Luminosità del
    bianco) / (Luminosità)\]

    = (Vividezza) / (Luminosità)

CIECAM02 sviluppa e utilizza diversi tipi di variabili correlate che
consentono l'utilizzo di questi concetti:

J: chiarezza, è corrispondente alla L (Lab)

C: cromaticità, vicino a C (Lab)

h: angolo di tonalità, vicino a H (Lab)

H: tonalità. Un colore può essere descritto dalla composizione di 2
colori di base tra 4 (rosso, giallo, verde, azzurro), ad es. 30B70G o
40R60Y.

Q: luminosità

M: vividezza

ac, bc: corrispondono al a e b (Lab)

Perché la saturazione oltre ad altre variabili vicine? Ecco una
citazione di un testo di Robert Hunt (2001):

  
  
''“I colori sono percepiti in base a tre caratteristiche: la tonalità di
colore, la luminosità e la colorazione (vividezza colore), la tonalità
non ha una versione relativa, ma la luminosità ha chiarezza e la
colorazione o vividezza ha la saturazione. I correlati della cromaticità
sono ampiamente usati nelle formule di differenza di colore, ma la
saturazione attualmente svolge una piccola parte nella scienza e nella
tecnologia dei colori. Questo è forse perché in molte industrie i
campioni piatti vengono visualizzati in illuminazione uniforme per la
valutazione delle differenze di colore e in questo caso la cromaticità è
il contribuente appropriato per i campioni con piccolo angolo di
visione. Per i campioni di grande angolo visivo, tuttavia, la misura di
saturazione può essere più appropriata per l'uso. Nel mondo reale, è
comune per gli oggetti solidi essere visto in illuminazione direzionale;
in queste circostanze, la saturazione è un percezione più utile della
cromaticità perché la saturazione rimane costante nelle ombre.
Nell'immagine, gli artisti e gli operatori di computer-grafica
utilizzano ampiamente una serie di colori di saturazione costante.
Nell'immagine ottica, la saturazione può essere un importante della
percezione in grandi aree oscure. Il lavoro sperimentale recente ha
fornito una misura correlata molto migliore della saturazione ".

## I 3 processi

Tre processi consentono l'uso di CIECAM, i loro nomi dipendono da ogni
progettista. Ho fatto una sintesi (ricordiamo: questo documento non è un
corso, o una tesi sulla CIECAM ... ma un aiuto alla sua comprensione e
all'utilizzo).

### Processo 1

Usano generalmente nomi come "origine", "avanti", "input", "source" ...
ho scelto il termine "sorgente", che corrisponde alle condizioni di
ripresa e il processo prevede di riportare le condizioni e i dati in una
zona "normale" . Con "normale" intendo condizioni medie o standard di
dati, vale a dire senza prendere in considerazione le correzioni CIECAM,
ad es. "surround = media", bilanciamento del bianco D50!

### Processo 2

Corrisponde al trattamento di variabili correlate (J C h H Q M s a b)
per vari scopi: agisce sulla chiarezza(J), luminosità (Q), cromaticità
(C), saturazione (s), livello di colore (vividezza M), angolo di
tonalità h, così come ac e bc. È possibile costruire un software di
editing delle immagini attorno a queste variabili ...

Nel caso di questa patch per RT, ho arbitrariamente selezionato 4 gruppi
di algoritmi:

1.  JC aggiungendo una funzione di contrasto;
2.  Js, come sopra
3.  QM
4.  Tutti: tutti i parametri compreso h.

Questi moduli sono semplici, più a scopo pedagogico che cercare di
risolvere i problemi della colorimetria, anche se i risultati sono, a
mio parere, eccellenti.

Ho completato questo processo con:

1.  doppia"curva", agendo sui contrasti J (chiarezza) o Q (luminosità),
    il cui principio è simile alle curve doppie di "esposizione";
2.  scelta per le curve di colore tra cromaticità, saturazione e livello
    di colore (vividezza).
      
    Potremmo aggiungere altri algoritmi basati sulla trasformazione di
    Fourier o sostituire le funzioni equivalenti di RT ...

### Processo 3

In genere vengono utilizzati nomi come "inversa", "rovesciata", "uscita"
o "condizioni di visualizzazione". Ho scelto "condizioni di
visualizzazione", che riflette il supporto su cui verrà visualizzata
l'immagine finale (monitor, TV, proiettore, ...), nonché il suo
ambiente. Questo processo prende i dati dal processo 2 e li "fornisce"
al supporto di uscita prendendo in considerazione le condizioni di
visualizzazione e l'ambiente circostante. Nota: qui troviamo evidenza
della differenza di visualizzazione tra una foto stampata e un'immagine
visualizzata su un monitor - anche se la stampante è ben calibrata e con
buone condizioni di visualizzazione (osservazione)! Una foto stampata
viene spesso visualizzata in un album, spesso su sfondo nero, in
condizioni di scarsa illuminazione ... e spesso con luce al tungsteno.
L'originale sarà visto su un monitor con uno sfondo chiaro e un
illuminatore D50 ... Non si tratta di cambiare l'output della "stampa",
ma di adattare l'uscita del "monitor, TV ...". Vale a dire, ma qui si
ferma il confronto, che ci rendiamo conto di effettuare qualcosa di
simile al processo detto soft-proofing, ma non è un caso perché è lo
scopo di CIECAM. Prendiamo in considerazione le impostazioni specificate
in "Preferenze" (punto bianco del dispositivo di uscita \[schermo TV,
proiettore ...\]) e la sua luminosità media \[% grigio\]. Teniamo in
considerazione anche la luminosità della stanza in cui l'osservazione si
realizza e la luminanza relativa del dispositivo di visualizzazione (più
o meno nero). Sintesi semplificata di ciò che RT consente con la patch
corrente:

1.  caso generale dell'utente che utilizza RT per vedere il suo sviluppo
    ... che dovrebbe rappresentare il 95% dei casi. In questo caso, le
    "condizioni di visualizzazione" corrispondono all'ambiente di lavoro
    di RT, ad esempio:
    - il punto bianco del monitor è impostato su 6000K
    - monitor calibrato, quindi Yb = 18
    - ma in accordo con:
      - il "tema" selezionato in "Preferenze/Generale" (quasi nero o
        grigio), devi cambiare "surround"
      - la posizione del monitor (su uno sfondo neutro o scuro), devi
        cambiare "surround"
      - illuminazione della stanza, che cambierà nel tempo, dovrai
        cambiare "la visualizzazione della luminosità di adattamento L":
        ad es. di notte senza illuminazione, "L" sarà vicino a 0 o 1, e
        al contrario di giorno in una stanza luminosa, "L" sarà prossimo
        a 1000
2.  caso non comune, ma possibile, perché l'ho già fatto, uso RT e la TV
    di famiglia per mostrare le immagini. Le "condizioni di visione"
    saranno diverse e adattate ad ogni caso; si dovrebbe riesaminare
    ciascuno dei punti precedenti per analizzare: il punto bianco della
    TV, il Yb della TV (empirico?), un diverso "surround" perché
    generalmente guardiamo la TV con uno sfondo opaco e con
    un'illuminazione ridotta della stanza .
3.  se si sta preparando una serie di fotografie per una mostra: si deve
    "analizzare", in modo professionale, le condizioni di
    visualizzazione sul sito e informarsi sull punto bianco del
    proiettore, la sua calibrazione (?), la luminosità della stanza il
    giorno dell'esposizione, ecc ... In RT, l'utente imposta le
    "condizioni di visualizzazione" per soddisfare le condizioni
    dell'esposizione e produce i corrispondenti jpeg (o TIFF)
4.  ecc.
5.  è per questo che impostare la maggior parte delle impostazioni per
    il processo \#3 (Device Output) in "Preferenze" non è un errore, ma
    appare simile ad impostare il profilo del monitor che dipende dal
    monitor ...

## dati

Quali sono i dati presi in considerazione e quali delle
semplificazioniche ho (arbitrariamente) fatto? Come adattarle?

- **Yb**: Yb è la luminanza relativa dello sfondo! Con questo, siamo
  molto avanzati! In particolare viene espresso in % di grigio. Un
  grigio del 18% corrisponde ad una luminanza di fondo espressa in CIE L
  del 50%.

:\* per il processo \#3, se il monitor è calibrato, è possibile avere un
valore di Yb vicino a 18 o 20. Se il televisore o il proiettore, che
sembra difficile da calibrare, sembra scuro o chiaro, potete regolare
questo valore empiricamente . Dipende dal supporto di visualizzazione e
può essere considerato costante per un insieme di foto nelle stesse
condizioni di osservazione. Se si desidera modificare questo valore,
passare a "Preferenze/Gestione del colore/dispositivo di uscita della
luminanza Yb (%)"

:\* per il processo \#1, è molto più complesso perché:

:\*\* un'immagine ha raramente un'esposizione costante e piccole
variazioni di luminanza

:\*\* Ho messo il modulo CIECAM alla fine del processo Lab, poco prima
della conversione RGB e degli invii al dispositivo di output, quindi
possiamo supporre che l'utente abbia utilizzato vari strumenti di RT per
rendere l'immagine una "media" dell'istogramma

  
  
Quindi ho arbitrariamente fatto Yb inaccessibile calcolandolo dalla
luminanza media dell'immagine. Naturalmente, se in futuro RT integra le
pipette per separare le aree dell'mmagine (buio, normale, luminoso ...),
allora sarebbe possibile immettere diversi valori Yb. Ad esempio su
un'immagine possiamo vedere tre aree:

- standard, che corrisponde alla luminanza media dell'immagine con un Yb
  impostato al 20%;
- sottoesposto (contorni approssimati delineati dalla pipetta ...), dove
  la luminanza sarebbe calcolata e sarebbe, ad esempio, come risultato
  Yb = 5%;
- sovraesposta, dove Yb sarebbe alto come il 70% ..

- **La** : La è il fattore di adattamento della luminanza assoluta!
  Ancora una volta, siamo molto avanzati ora!

:\*Nel processo \# 1, corrisponde alla luminanza durante la ripresa. Per
esempio. se si effettua una foto all'ombra, "La" sarà prossima a
2000cd/m2; se fai scatti interni, "La" varia a seconda
dell'illuminazione da 20 a 300cd/m2 ... Nella riproduzione, questi
valori possono essere anche più bassi

:\*'''”Luminosità delle scene" e la casella di controllo "Auto"
(processo \# 1):

:\*\*Se la casella di controllo è abilitata, La viene calcolata con i
dati Exif (velocità dell'otturatore, velocità ISO, numero F, copertura
esposizione della fotocamera) e anche il cursore di Raw White Point e
Exposure compensation

:\*Nel processo \# 3, corrisponde alla luminanza del luogo in cui viene
fatta l'osservazione. Quando calibrate il monitor, ti viene chiesto
questo valore ... o ti viene offerta la scelta di utilizzare una sonda.
Ordini di grandezza da 15 a 100 dovrebbero risolvere la maggior parte
dei casi. Ma ad esempio. per una proiezione teatrale al buio, può
portare a valori inferiori (1-10)

:\*Questi 2 valori di "La" sono regolabili in RT, nello strumento "CIE
Color Appearance Model 2002"

- **Surround**

  
Di nuovo, ho fatto semplificazioni ...

- per il processo \# 1, questi dati riflettono alcune condizioni di
  ripresa, come foto in un museo con uno sfondo scuro o riprese in
  ritratto su sfondo nero. Di solito l'utente di RT avrà corretto le
  deviazioni dalla sua percezione grazie ai suoi numerosi strumenti.
  Tuttavia, ho aggiunto una casella di controllo "Surround (scena)
  scura", che può essere attivata se necessario. Il suo utilizzo
  schiarirà l'immagine (ricorda: questo processo porta i dati "torna
  alla normalità")
- questi dati riflettono l'ambiente dell'immagine durante la
  visualizzazione. Più sarà scuro il contesto, più sarà necessario
  aumentare il contrasto dell'immagine. La variabile "surround" non
  agisce come una curva di D-lighting o di tono, ma cambia anche i
  colori nell'asse rosso-verde e giallo-blu. Se la luminosità
  dell'ambiente è superiore al 20%, scegli "media", altrimenti adatta
  alle tue condizioni, ad es. Le impostazioni di RT
  (Preferenze/Generale/Seleziona tema) influiscono sul rendering finale.
  Questa impostazione è accessibile tramite "Surround
  (visualizzazione)". Più oscuro sarà il circondario, maggiore sarà il
  contrasto contemporaneo dell'immagine.

- **White-points model**

:\*“WB RT + output” : qui abbiamo fiducia nel bilanciamento del bianco
di RT per il processo \# 1; CIECAM utilizza D50 come riferimento: il
bilanciamento del bianco di RT riporta le condizioni ad un equivalente
D50, mentre per il processo \# 3, sarà necessario - come necessario -
impostare il punto bianco del dispositivo di uscita. Vai a "Preferenze /
Gestione colori / Impostazioni dispositivo di uscita bianca (monitor,
TV, proiettore)" e seleziona un illuminante nell'elenco (è sufficiente?
Non ho idea delle caratteristiche dei proiettori, della luce, della
temperatura ...)

:\*WB RT+CAT02 + output” : per il processo \# 3, siamo nella stessa
situazione precedente; per il processo \# 1, si effettua una
miscelazione tra il bilanciamento del bianco di RT e CAT02 che utilizza
le impostazioni che costituiscono una soluzione in cui si combinano i
due effetti (RT e CAT02). È possibile modulare l'azione di CAT02 agendo
sul cursore "adattamento CAT02". Probabilmente dovrai cambiare le
impostazioni della bilancia del bianco di RT per trarre vantaggio dai
vantaggi "mix", altrimenti gli effetti si aggiungono.

:\*CAT02 è un adattamento cromatico, converte i valori XYZ di
un'immagine i cui punti bianchi sono Xw0, Yw0, Zw0, nei nuovi valori XYZ
il cui punto bianco diventa XW1, Yw1, ZW1; l'algoritmo utilizzato è
simile a quello di Von Kries, quindi diverso dalla correzione di RT che
tiene conto dei moltiplicatori dei canali!

- **”CAT02 adaptation” e la casella di controllo “Auto”**

:\*vedi sopra per l'utilizzo di "WB CAT02 + output"

:\*tuttavia, anche quando il "modello di punto bianco" è impostato su
"uguale", questo cursore può essere utile. Di solito la casella di
controllo "auto" deve essere controllata e CIECAM calcola un
coefficiente interno "D" che viene utilizzato per un altro scopo
rispetto all'adattamento cromatico. Il risultato è un valore superiore a
0,65 (65%); è possibile deselezionare la casella che modifica il
processo \# 1, gli effetti possono essere inaspettati ...

## Algoritmo

Puoi scegliere tra JC, JS, QM (naturalmente ci sono altre possibili
combinazioni!) oppure "All" che elenca tutte le possibili impostazioni
(ho arbitrariamente escluso "h" così come "ac" e "bc" dagli algoritmi
JC, JS, QM). L'uso più comune (se si può utilizzare questo termine per
CIECAM) è JC, quindi agire sui cursori per ottenere il rendering
desiderato ... che ricordo dipende dal dispositivo di visualizzazione,
dal suo ambiente, dalle impostazioni e dalla luminosità della stanza .

- **Algoritmo “JC”**
  - J simula la luminosità- vicino a L (Lab) - e C simula la
    cromaticità, vicino alla cromaticità c di (Lch). Ma, differenza
    importante, J e C tengono conto degli "effetti" (contrasto
    simultaneo, Hunt, Stevens, ecc ...) a differenze delle correzioni
    Lab e RGB.
  - J varia nell'intervallo \[0-100\] e corrisponde ad un valore
    relativo della luminosità (allo stesso modo L o Value ...) e
    teoricamente C nell'intervallo \[0-180\] (può essere superiore)
  - I due cursori che utilizzano J e C possono variare da -100 a +100
    con azioni analoghe alla "Luminosità" (da rinominare "Chiarezza") e
    "Cromaticità" dei cursori "Regolazioni Lab".
  - con l'algoritmo "JC", è possibile controllare i toni della pelle,
    l'azione è simile al controllo fornito nelle "Regolazioni Lab"
  - Il cursore "contrasto" modula l'azione di "J" con una curva "S", che
    tiene conto della luminosità media dell'istogramma "J".

<!-- -->

- **Algoritmo “JS”**

  
È simile a JC, ma:

- - la cromaticità viene sostituita dalla saturazione (CIECAM). Ma per
    quale scopo? Cito di nuovo un estratto del testo da parte di G.Hunt
    Per i campioni di grande angolo sotteso, però, un correlato di
    saturazione può essere più appropriato da utilizzare. Nel mondo
    reale, è comune vedere gli oggetti solidi con illuminazione
    direzionale; in queste circostanze la saturazione è un percezione
    più utile della cromia perché la saturazione rimane costante nelle
    ombre. Nell'immagine, gli artisti e gli operatori di
    computer-grafica utilizzano ampiamente una serie di colori di
    saturazione costante. Nell'immagine ottica, la saturazione può
    migliorate la percezione in grandi aree oscure. Recenti lavori
    sperimentali hanno fornito un correlato molto migliorato della
    saturazione.
  - Il controllo della tonalità della pelle è meno "fine" che con "JC",
    risulta globalmente più ampia nei rossi

<!-- -->

- **Algoritmo QM**
  - qui usiamo 2 variabili Q ("luminosità") e M ("Vividezza") che non
    sono dati relativi, ma assoluti. Prendiamo in considerazione la
    luminosità del bianco. È facile capire che lo stesso bianco "J =
    100" apparirà più luminoso al sole che in una stanza oscura ...
  - la luminosità del bianco tiene conto dei seguenti parametri (scena):
    "luminosità adattamento La", "adattamento CAT02" e "Yb" (attualmente
    non regolabile)
  - in uso comune, il controllo è più difficile che con "JC", ma offre
    opportunità per immagini ad alto contrasto e apre la porta per
    l'elaborazione HDR
  - Il controllo della tonalità della pelle è meno "fine" che con "JC",
    globalmente più ampia nei rossi
  - Il "contrasto" ovviamente agisce in modo diverso, in quanto prende
    in considerazione Q diversamente da J.

<!-- -->

- **Algoritmo Tutto**
  - è possibile controllare tutte le variabili CIECAM: cromatografia J,
    Q, C, saturazione s, livello M colore, contrasto J, contrasto Q,
    angolo tonalità h, protezione toni pelle (agisce solo su C)

## Curve di tono e colore

### Curve

- Come nel modulo "esposizione" sono disponibili 2 curve di ton, che
  agisceno sulla chiarezza "J" e sulla luminosità "Q". È possibile
  utilizzare solo una curva o entrambi, mettendo finalmente "chiarezza"
  e "luminosità". Attenzione, le curve "luminosità" possono facilmente
  portare a risultati fuori dai limiti! "Luminosità" è una scala
  assoluta, mentre la "chiarezza" è una scala relativa, lo stesso "J"
  apparirà bianco più direttamente illuminato dal sole che nell'ombra,
  che viene preso in considerazione dalla "luminosità" (Q). Così le
  ombre e i punti salienti saranno resi diversamente dalle curve
  "chiarezza" e "luminosità".
- sono presenti anche una serie di curve "cromia" con 3 scelte: la
  cromaticità (la più comune), la saturazione e la vividezza. Queste 3
  curve vengono utilizzate per regolare il parametro scelto in base a se
  stesso, ad es. modulare la saturazione per evitare che i colori già
  saturi sfuggano alla gamma. Per queste tre curve, il cursore
  "protezione dei toni rossi e pelle" è operativo, è più adatto alle
  tonalità della pelle in modalità "cromia". Raccomando di utilizzare la
  modalità "parametrica" ​​che consente di distinguere in base al livello
  di saturazione dei colori. Nota: Tutte le combinazioni di queste curve
  (cromaticità, saturazione, vividezza) e cursori (cromaticità,
  saturazione, vividezza) non sono possibili senza complicare troppo il
  codice, per cui in alcuni casi alcuni cursori sono disabilitati.

### Istogrammi nella curva di tono

Gli istogrammi della curva di tonalità nel tool *CIE Color Appearance
Model 2002* possono mostrare i valori prima o dopo l'applicazione di
CIECAM02. Per visualizzare i valori dopo le regolazioni CIECAM02,
attivare l'opzione "*Mostra istogrammi di output CIECAM02 nelle curve*".
Se disabilitato, gli istogrammi mostrano i valori prima di CIECAM02.

### istogrammi nella curva di colore

L'istogramma nella curva di colore mostra la distribuzione del colore
(saturazione/vividezza) in base all'intensità del colore
(saturazione/vividezza) o della cromaticità in modalità Lab. Più
l'istogramma viene spostato a destra, più i colori più saturi sono
vicini ai limiti della gamma. Più l'istogramma viene spostato a
sinistra, più i colori sono opachi, tendenti al grigio.

L'ascissa rappresenta il valore della cromaticità
(saturazione/vividezza) o cromaticità (in modalità Lab). La scala delle
ascisse è "aperta".

Come al solito, l'ordinata rappresenta il numero di pixel coinvolti.

## Controllo Gamut (Lab + CIECAM)

- questa casella di controllo vincolerà i dati nell'area di lavoro.
  Avrei potuto eseguire questa azione in modalità CIECAM (processo \#
  3), ma avrei notevolmente rallentato il sistema
- L'algoritmo usato è lo stesso che in "Regolazioni Lab", funziona in
  colorimetria relativa. Penso che le differenze con le regolazioni Lab
  che potrebbero essere prodotte in modalità CIECAM sono minime.
- Alcune regolazioni del codice CIECAM vengono eseguite quando è
  abilitato "Controllo Gamut".

## Codice, precisione di calcolo e tempo di lavorazione

Il codice per i processi \# 1 e \# 3 è rigorosamente quello di CIECAM02
(M.Fairchild, Billy Biggs, ...) che ho adattato e ottimizzato a RT,
nonché i miglioramenti alla correzione di gamut da Changjun Li, Esther
Perales, M Ronnier Luo e Francisco Martínez-Verdú.

I processi \# 1 e \# 3 sono simmetrici e impilano molti calcoli a
virgola mobile. L'uso della "doppia precisione" è obbligatoria, quindi
il tempo di elaborazione cresce di circa 1 secondo per mega. Dopo un
ampio test, abbiamo appurato che l'utilizzo della precisione singola
invece della doppia è consentito per l'elaborazione senza sacrificare la
qualità dell'immagine È possibile modificare questa impostazione in
"Preferenze/Gestione del colore"

In termini di precisione, ho voluto effettuare alcuni controlli
confrontando una serie di dati prima e dopo CIECAM; le differenze sono
molto piccole, ad es. un valore di ingresso XYZ di 6432.456 ha un valore
di output di 6432.388, che è corretto.

## Limitazioni di CIECAM02

Questo modello non è perfetto e vengono identificate le seguenti
limitazioni. Possono condurre alcune immagini a elaborarle
correttamente:

- abbiamo già visto questo per le impostazioni di Yb;
- CIECAM02 non è uno spazio di lavoro come sRGB o Prophoto, o
  addirittura Lab. Quindi è difficile controllare la gamma. CIECAM è
  anche conosciuto per i suoi problemi di stretta gamma, per questo
  motivo potrebbero verificarsi dei risultati imprevisti ai limiti se si
  sta spingendo troppo i cursori (J, C, s ...); ciò può portare in
  situazioni critiche (nelle alteluci, ...) con apparse di macchie nere
  o bianche in queste aree. Non esitate a utilizzare gli strumenti di RT
  (evidenziare il recupero, evidenziare la ricostruzione, ridurre i
  disturbi dell'impulso, ...) nelle aree bruciate o nere (punti bianchi
  e neri crudi, evitare spostamenti di colore, ...)
- grandi spazi di lavoro (widegamut, prophoto, ...) possono portare, in
  alcuni casi, a zone nere, mentre non appaiono in sRGB (rallentamento
  della gamma di CIECAM).
- Le immagini rumorose influenzeranno CIECAM, che penseranno che i punti
  colorati siano realtà; è per questo che ho messo CIECAM dopo "denoise"
- il modello CIECAM favorisce i "coni" e prende scarsamente conto dei
  "bastoncelli", il che significa che la visione periferica è
  scarsamente presa in considerazione.
- Quindi, con CIECAM, non aspettatevi di trovare una cura per immagini
  "difficili" (sovraesposizione, saturazione del sensore, ecc.). Ma per
  immagini "normali" (che sono la maggioranza), i progressi sembrano più
  che significativi.
- Eccetera...

Forse vedremo un giorno che apparirà CIECAMxx che potrebbe superare le
mancanze di CIECAM02?

## I 12 principi di CAM da R.Hunt

1.  Il modello dovrebbe essere il più completo possibile, in modo che
    possa essere utilizzato in una varietà di applicazioni; ma in questa
    fase, solo gli stati statici di adattamento dovrebbero essere
    inclusi, a causa della grande complessità degli effetti dinamici.
2.  Il modello dovrebbe coprire un'ampia gamma di intensità di stimoli,
    dai colori dell'oggetto molto scuri a quello luminoso. Ciò significa
    che la funzione di risposta dinamica deve avere un massimo e non può
    essere una semplice funzione logaritmica o di potenza.
3.  Il modello dovrebbe coprire un'ampia gamma di intensità di
    adattamento, dai bassi livelli scotopici, come avviene nella foto di
    stelle, a livelli molto elevati di fotopia, come ad esempio in
    presenza di luce solare. Ciò significa che la visione dei
    bastoncelli dovrebbe essere inclusa nel modello; ma molte
    applicazioni considerano la visione dei bastoncelli trascurabile, il
    modello dovrebbe essere utilizzabile in una modalità che non include
    la visione dei bastoncelli.
4.  Il modello dovrebbe coprire un'ampia gamma di condizioni di
    visualizzazione, inclusi sfondi di diversi fattori di luminosità e
    di ambienti scuri, chiari e medi. È necessario coprire i diversi
    ambienti a causa del loro uso diffuso in schermi proiettati e
    auto-luminosi.
5.  Per la facilità d'uso, le sensibilità spettrali dei coni dovrebbero
    essere una trasformazione lineare delle funzioni CIE x, y, z o x10,
    y10, z10 e la funzione V'() deve essere utilizzata per la
    sensibilità spettrale dei bastoncelli. Poiché spesso i dati
    fotometrici scotopici sono spesso sconosciuti, occorre prevedere
    metodi per fornire valori approssimativi scotopici.
6.  Il modello dovrebbe essere in grado di fornire un qualsiasi grado di
    adattamento tra completa e nessuna, per i fattori cognitivi e per
    l'effetto Helson-Judd.
7.  Il modello dovrebbe dare previsioni di tonalità (sia come angoli di
    tonalità, sia come tonalità di colore), luminosità, leggerezza,
    saturazione, cromia e vividezza colore.
8.  Il modello dovrebbe essere in grado di essere azionato in modalità
    inversa.
9.  Il modello non dovrebbe essere più complicato di quanto sia
    necessario per soddisfare i requisiti di cui sopra.
10. Ogni versione semplificata del modello, destinata a particolari
    applicazioni, dovrebbe dare le stesse previsioni come il modello
    completo per alcune serie di condizioni specificate.
11. Il modello dovrebbe dare previsioni di aspetto colore che non sono
    notevolmente peggiori di quelle fornite dal modello che è migliore
    in ogni applicazione.
12. Una versione del modello dovrebbe essere disponibile per
    l'applicazione a colori non correlati (quelli visibili in ambienti
    scuri isolati da altri colori).

## Alcuni link

CIECAM02 Wikipedia [1](http://it.wikipedia.org/wiki/CIECAM02)

Modello di Aspetto Colore - Fairchild
[2](http://www.cis.rit.edu/fairchild/PDFs/AppearanceLec.pdf)

Mémoire Laborie ENS Louis Lumière
[3](http://www.ens-louis-lumiere.fr/fileadmin/recherche/Laborie-photo-2007-mem.pdf)
