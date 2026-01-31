---
title: Exposure
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

## Livelli Automatici

Lo strumento "Livelli Automatici" analizza l'istogramma e quindi regola
i controlli nella sezione Esposizione per ottenere un'immagine ben
esposta.

Utilizza solo i cursori "Compensazione esposizione", "Compressione
Alteluci", "Ricostruzione Alteluci", "Livello del nero", "Luminosità" e
"Contrasto".

Pensate alle regolazioni dei Livelli Auto come un buon punto di
partenza. Sono state regolate per funzionare meglio con uno "scatto
tipico", quindi il risultato dovrebbe essere generalmente esteticamente
gradito, d'altronde il programma non conosce il tuo gusto o le tue
aspettative, quindi non sempre sarà vero. Ad esempio, si potrebbe
ottenere una foto troppo chiara (cioè non tipica), nel qual caso si deve
personalizzare i valori delle correzioni.

È possibile reimpostare tutti i cursori nella sezione Esposizione
facendo clic sul pulsante Reset. Le curve di tono non vengono toccate.

## Tosaggio %

*Livelli automatici* utilizza il valore del *Tosaggio %* per regolare
l'esposizione. Questo numero definisce la percentuale di pixel dei punti
bianchi e neri dall'istogramma che possono essere ritagliati (ossia che
possono andare fuori scala fissando un valore massimo o minimo
rispettivamente). Il valore minimo è 0.00, il valore massimo è 0.99.
Valori più alti aumentano il contrasto, valori più piccoli lo riducono.

## Evidenziare la ricostruzione

Utilizza *Riicostruzione Alteluci* (HR) per cercare di ripristinare i
dettagli sovraesposti nei file raw. Tenta di ripristinare le regioni con
punti ritagliati dell'immagine raw, basandosi sul fatto che i tre canali
in un file raw non si bloccano contemporaneamente e quindi una regione
mancante (tagliata) in un canale potrebbe essere presente in uno degli
altri canali di colore. Utilizzando il metodo "Propagazione colore", può
anche indovinare i dati tagliati usando dati vicini dai canali non
ritagliati, se presenti. Ricorda che questo strumento viene utilizzato
per la ricostruzione delle alteluci, mentre se si desidera solo
comprimere le alteluci che sono state tagliate a causa dell'uso, ad
esempio, di *Compensazione dell'esposizione*, utilizzare il cursore
[Compressione Alteluci](exposure#highlight_compression) (HC).
Il pulsante *Auto Levels* abilita automaticamente *Ricostruzione
Alteluci* se necessario.

Sono disponibili quattro diversi metodi di ricostruzione:

1.  Ripristino di luminosità
      
    I dettagli recuperati saranno grigi neutri.

    Sono consigliati nella maggior parte dei casi valori di
    *Compressione Alteluci* minori di 100.
2.  Propagazione di colore
      
    Questo è il metodo di ripristino più potente. Oltre a ripristinare
    la luminosità, *Color Propagation* tenta di ripristinare le
    informazioni di colore per "propagare" il colore conosciuto
    circostante nell'area rimanente mancante. Questo metodo funziona
    meglio sulle piccole aree sovraesposte e può fare miracoli sulla
    pelle sovraesposta. La sua debolezza è che può talvolta "propagare"
    i colori errati, a seconda degli elementi di immagine che circondano
    le luci soffuse oppure i colori possono diffondersi in pattern
    indesiderati. È anche computazionalmentee pesante e quindi più lento
    degli altri metodi.

    Funziona bene anche con valori "*Compressione Alteluci*" molto alti
    (sotto i 500).
3.  CIELab
      
    Riduce il canale di luminanza e tenta di ripristinare
    successivamente i colori.

    Sono consigliati nella maggior parte dei casi valori di
    *Compressione Alteluci* minori di 100.
4.  Miscela

  
Tenta di indovinare i colori dei canali colorati tagliati interpolando i
colori delle aree vicine non tagliate .

\#: Sono consigliati nella maggior parte dei casi valori di
*Compressione Alteluci* minori di 100.

## Compensazione dell'esposizione

I valori del cursore Compensazione esposizione (EC) sono valori ISO. Ciò
significa che un valore di +1 equivale a una stop di sovraesposizione
(+1 EV, valore di esposizione, noto anche come +1 LV, valore della
luce). Se si effettuano due foto, una senza correzione (EV = 0) e una
sottoesposta di uno stop (EV = -1), è possibile effettuare entrambe le
foto corrispondenti impostando la compensazione dell'esposizione per la
foto sovraesposta a -1 oppure per la fotografia sotto sottosposta a +1.

Date un'occhiata all'istogramma mentre si sposta questo cursore.
Spostandolo a destra sposta l'intero istogramma a destra. Ciò significa
che questo cursore modifica il punto nero (a sinistra dell'istogramma) e
il punto bianco (a destra).

Se si tenta di ridurre l'esposizione di una foto che contiene il
ritaglio, si noterà che le aree ritagliate diventano grigio piatto.
Abilitando "*Ricostruzione alteluci*" impedirà la dominanza di questo
aspetto grigio piatto cercando di recuperare le informazioni dai
restanti canali non tagliati.

Se hai usato RawTherapee per un po', potresti notare che hai quasi
sempre bisogno di una compensazione di esposizione positiva - come se
tutte le tue foto siano sottoesposte. Non preoccuparti - questo è
normale. La maggior parte delle fotocamere sottoespone intenzionalmente
per preservare le alteluci (anche se alcuni altri processori raw non lo
fanno).

Per l'utente interessato ad approfondire l'argomento segue una
descrizione tecnica di come EV = 0 si riferisce ai dati raw: mentre EV =
0 equivale a 1,0 in guadagno (ovvero non cambia), vi è un guadagno di
base dipendente dal bilanciamento del bianco applicato prima
dell'esposizione. Questo guadagno di base viene calcolato in modo tale
che il canale di colore con la gamma più piccola sia sufficiente a
raggiungere il valore massimo. Anche se tutti i canali raw hanno la
stessa gamma nel file raw, il bilanciamento del bianco li equilibrerà
(temperature inferiori significa più guadagno sul rosso, maggiori
guadagni sull'azzurro) in modo da non tagliare allo stesso livello. Il
guadagno di base solleva il canale più piccolo in modo sufficiente per
assicurarsi che a EV = 0 nessuna altaluce sia tagliata. Poiché il
bilanciamento del bianco cambia il guadagno del canale raw, il guadagno
di base cambia come effetto collaterale quando viene cambiato il
bilanciamento del bianco. Per i grandi cambiamenti del bilanciamento del
bianco si può pertanto vedere un lieve cambiamento di luminosità
nell'immagine. Si noti che il guadagno di base riguarda i valori massimi
che i canali possono rappresentare, ovvero se non vi è alcun taglio di
valori per le alteluci del raw, nessuna luce raggiungerà il livello
massimo a EV = 0.

## Compressione Alteluci

Il cursore Compressione Alteluci (HC) può essere utilizzato per
recuperare le alte luci in una foto, utile per le aree di
"sovrapposizione" (o bruciatura) leggermente sovraesposte. Mentre lo
strumento "Ricostruzione Alteluci" consente di "ricostruire" i dati
mancanti nel file raw, contando sul fatto che i tre canali in un file
raw non si bloccano allo stesso tempo e quindi una regione tagliata
(clipped) in un canale può essere indovinata dai dati attuali di uno
degli altri canali di colore, questo strumento di "Compressione
Alteluci" funziona solo su dati già presenti - che quindi non sono stati
persi in modo irreversibile al momento della ripresa. Se l'immagine
originale non ha aree tagliate, ma a causa dell'azione, ad esempio,
dell'esposizione viene bruciate un'area di alteluci, è possibile
utilizzare *Compressione Alteluci* per comprimere queste regioni
ritagliate. In quanto tale, funziona non solo su file raw ma anche su
immagini normali.

Per vedere se la tua foto contiene aree sovraesposte, fai clic
sull'icona di indicazione evidenziata in alto
![Image:Warnhl.png](Warnhl.png "Image:Warnhl.png") a destra della
finestra dell'immagine. Le aree sovraesposte appaiono in nero.

<figure>
<img src="/images/Hra_0.jpg" title="Hra_0.jpg" />
<figcaption>Hra_0.jpg</figcaption>
</figure>

<figure>
<img src="/images/Hra_0_chi.jpg" title="Hra_0_chi.jpg" />
<figcaption>Hra_0_chi.jpg</figcaption>
</figure>

Trascinando il cursore *Compressione Alteluci* a destra, l'intensità
delle alte luci diminuirà. Affinché la compressione evidenziata funzioni
al meglio, è necessario attivare anche l'opzione Ricostruzione Alteluci.
Ciascuno dei metodi HR ha i suoi punti forti e deboli, come spiegato in
precedenza. La propagazione di colore è il metodo più probabile per
produrre risultati belli quando il cursore HC è significativamente
superiore a 100. Per gli altri metodi di solito si desidera mantenere il
cursore HC intorno o sotto 100 - guardare l'istogramma e l'anteprima!

![](Hra_125_ba.jpg "Hra_125_ba.jpg") Per scoprire il valore HC ottimale,
è possibile utilizzare l'istogramma. Negli screenshot sopra, quello che
vedete sono nuvole sovraesposte sopra il vulcano Teide a Tenerife.
Quando si aziona il cursore del mouse sull'area sovraesposta,
l'indicatore dei valori dei pixel (nel pannello *Navigatore*, sotto
l'anteprima piccola) mostra che la luminosità (L) è a 100 e l'istogramma
mostra che tutti i canali sono tagliati (vedere le zone rosse, verdi e
blu nell'angolo in alto a destra dell'istogramma, significa che ci sono
tanti pixel di valore massimo che sono fuori scala). Aumenta il cursore
HC finché i canali rossi, verdi e blu dell'istogramma non si schiacciano
più contro l'estremità destra dell'istogramma - si desidera che
tocchino, ma non lo superino. È possibile abilitare l'icona "Indicazione
di evidenziazione ritagliata"
![Image:Warnhl.png](Warnhl.png "Image:Warnhl.png") prima di spostare il
cursore HC verso l'alto. Una volta che le aree nere dell'indicatore
scompaiono dalle parti bianche che si desidera compresse, anche quando
la luminosità di questi pixel scende da L = 100 a L = 99, ci si deve
fermare. Non aumentare ulteriormente il cursore HC, perché ora le aree
bianche inizierebbero a diventare grigie. Non si desidera che diventino
grigie. Questo renderebbe la foto piatta. In questo esempio, le aree
nere dell'indicatore sono scomparse quando imposta HC è stato impostato
a 125.

![](Hra_toomuch_histogram.png "Hra_toomuch_histogram.png") In linea di
principio, l'istogramma di un'immagine correttamente sviluppata deve
toccare entrambe le estremità - il nero e il fondo bianco. Non farlo
significa che l'immagine è stata sviluppata in modo errato. Questo è
vero per la maggior parte delle foto, le uniche eccezioni sono le foto
di scene che non dispongono di una gamma dinamica, come le scene
nebbiose. Se si aumenta troppo il cursore HC, i bianchi diventano grigi
mentre l'istogramma non tocca più l'estremità massima. Esempi di foto
sovrastampate possono essere facilmente trovate su Internet. Sembrano
orribili, non farlo! Recuperare ciò che è necessario, ma ciò che è
rimasto deve restare bianco.

RawTherapee offre più modi per affrontare le alteluci bruciate.
L'effetto collaterale di tutti questi metodi è quello di togliere la
luminosità delle foto, in quanto risultano più "piatte" o "sbiadite".
Evidenziare la compressione è molto utile se utilizzata con moderazione,
ma ricorda che non è possibile ripristinare ciò che non c'è nel raw,
quindi una volta che si nota che le aree bianche completamente tagliate
diventano grigi, è necessario ridurre la quantità di compressione finché
queste aree ritornino ad essere ancora una volta bianche. Per creare la
migliore uscita possibile, alimentare RawTherapee il miglior ingresso
possibile - quindi esponii bene prima di tutto!

## Soglia di Compressione Alteluci

Il cursore Compression Alteluci della soglia di compressione imposta il
punto in cui il cursore HC inizia a implementare la compressione. Un
valore di 0 significa che la soglia è zero: la compressione dei dati
avviene su tutta la gamma di tonalità. 100 imposta la soglia appena al
di sotto del punto bianco, in modo che tutti i punti cromatici compressi
siano compressi nella sommità superiore. In pratica, quando questo
slider è impostato su 0 vengono compressi molti più punti luminosi.

## Livello del Nero

Utilizzare questo per impostare il punto nero. Vedere il lato sinistro
dell'istogramma quando si tocca il cursore. Valori maggiori di 0
renderanno l'immagine più scura, i valori negativi schiariranno le parti
dell'ombra della foto.

## Compressione delle Ombre

Il cursore *Compressione Ombra* attenuava l'effetto del cursore *Livello
del nero*. Il valore massimo di 100 dà un'immagine meno scura. Questo
cursore ha effetto solo quando il cursore *'Livello del nero* è
impostato su un valore diverso da 0. Utilizzo pratico di questo
dispositivo di scorrimento *Copressione delle ombre* è quello di
ottimizzare l'intensità dell'ombra dell'immagine.

## Luminosità

Questo cursore applica una curva di tono codificato per aumentare o
abbassare le tonalità della foto, con conseguente immagine più o meno
luminosa. La stessa curva di tono viene applicata separatamente per
ciascun canale R, G e B. Il punto nero e il punto bianco mantengono le
loro posizioni.

## Contrasto

Questo cursore aumenta o riduce il contrasto della foto. Applica una
curva di contrasto centrata al livello di luminanza medio. Le tonalità
al di sopra della media vengono sollevate (abbassate), mentre le
tonalità al di sotto della media sono abbassate (sollevate). La stessa
curva di contrasto viene applicata separatamente a ciascun canale R, G e
B.

## Saturazione

Questo slider rende la foto più o meno satura. In termini più tecnici,
regola la saturazione dell'immagine applicando un moltiplicatore al
livello di saturazione di pixel nello spazio colore HSV.

## Curve di tono

Qui è possibile costruire le tue curve di tono. Lavorano
contemporaneamente su tutti e tre i canali R, G e B (quindi non è
possibile lavorare solo sul canale R).

Sono disponibili due curve di tono, che possono essere progettate con
vari tipi di curva e applicati in modi diversi, come illustrato di
seguito. Facendo clic sull'icona della curva si nasconde la curva
dall'interfaccia - ma non si disattiva la curva.

L'istogramma visualizzato come sfondo della curva mostra i livelli
dell'immagine così come elaborata fino a quel punto della pipeline di
elaborazione. Noterete che si differenzia dall'istogramma principale che
mostra i livelli dell'immagine finale, alla fine della pipeline.

Mentre è possibile utilizzare solo una curva di tono per eseguire le
regolazioni, è possibile ottenere un controllo finito più sottile se si
utilizzano due curve contemporaneamente. L'uso tipico di entrambe le
curve è quello di aumentare la luminosità utilizzando la prima curva e
di diminuirla utilizzando la seconda. È simile a creare una curva S su
una sola curva, ma dovrebbe risultare più comodo effettuare regolazioni
più fini utilizzandole entrambi senza rischiare di entrare facilemente
nella "zona pericolosa" dove i colori divengono irrealistici.

È possibile salvare una curva su disco. Fai clic sull'icona *Salva la
curva corrente*
![Image:Gtk-save-large-dark.png](Gtk-save-large-dark.png "Image:Gtk-save-large-dark.png")
accanto al grafico e assegna un nome. Utilizza l'icona "Carica una curva
dal file" ![Image: Gtk-open.png](_Gtk-open.png "Image: Gtk-open.png")
per riapplicare questa curva ad un altro file. Utilizza la funzione
"Reimposta curva lineare" ![Image:
Gtk-undo-ltr.png](_Gtk-undo-ltr.png "Image: Gtk-undo-ltr.png") per
eliminare tutti i punti creati e per ripristinare la curva lineare
neutra. Puoi anche "copiare" l'immagine ![Image:
Gtk-copy.png](_Gtk-copy.png "Image: Gtk-copy.png") e *Incollare*
![Image: Gtk-paste.png](_Gtk-paste.png "Image: Gtk-paste.png") da/per
gli appunti di RawTherapee, questo permette applicare rapidamente una
curva identica anche ad un altro strumento.

Puoi utilizzare tanti punti di controllo in una curva come preferisci.

È possibile definire diverse curve per tutti i tipi di curva se si
desidera, ma solo quello selezionato nel menu a discesa verrà applicato
alla foto.

La curva e l'istogramma sono sempre visualizzati con gamma sRGB,
indipendentemente dal profilo di lavoro o di uscita. Ciò significa che
l'area d'ombra è espansa e l'area delle Alteluci è compressa per meglio
corrispondere alla percezione umana.

### Curva lineare

Questo rappresenta l'immagine inalterata (o lineare), quindi senza
alcuna curva di tono applicata. Disabilita la curva.  

### Curva personalizzata

Questo è un classico tipo di curva, presente anche in molti altri
programmi. La parte sinistra del grafico rappresenta i toni più scuri,
la parte destra rappresenta i toni più luminosi della foto. Fare clic
sulla curva per contrassegnare un punto e trascinarlo con il mouse per
cambiare le tonalità. Trascinando il punto verso il basso l'immagine
diventa più scura, mentre trascinandolo verso l'alto rende la foto più
luminosa. La linea diagonale punteggiata segna lo stato lineare o
inalterato della foto. Tenere premuto il tasto **Control** per
rallentare il movimento. Tenere premuto il tasto **Shift** per
schioccare il punto sugli elementi chiave: valore massimo, valore
minimo, valore medio (cioè scattato alla linea diagonale o orizzontale
punteggiata), stesso valore del punto precedente, stesso valore del
prossimo punto e per il tipo *Gabbia di controllo*, la linea che
attraversa i punti precedenti e successivi. Eliminare un punto sulla
curva trascinandolo fuori dall'area di editor.

Il punto in alto a destra rappresenta le aree più luminose della foto.
Trascinare tale punto verticalmente verso il basso per rendere le luci
meo luminose; spostalo orizzontalmente a sinistra per rendere le aree
chiare più luminose, forse a costo di qualche sovraesposizione.

Il punto in basso a sinistra rappresenta le aree più scure della foto.
Spostare quel punto orizzontalmente a destra per rendere la foto più
scura, forse a costo di qualche sottoesposizione. Spostarla
verticalmente in modo da rendere più chiare le ombre.

Inverti la linea diagonale (da basso a sinistra e da alto a destra in
alto a sinistra e in basso a destra) per produrre un'immagine
negativa.  
![](curve_custom_s.png "curve_custom_s.png") Un uso tipico della curva
personalizzata è costruire una cosiddetta *curva S*. Segna tre punti
nelle rispettive "coordinate" (1,1), (2,2) e (3,3) rispettivamente.
Trascinare il punto a (1,1) un po 'più basso e il punto a (3,3) un po'
più alto. La tua immagine otterrà più "grinta" in questo modo. Se la
curva S è simmetrica, vale a dire se si sposta il punto prima posto a
1,1 per la stessa quantità di quello che hai impostato a 3,3 ma nella
direzione opposta, allora l'effetto sarà identico alla manipolazione
della " Cursore "Contrasto".  

### Curva Parametrica

![](Curve_parametric_s.png "Curve_parametric_s.png") Questa curva
presenta quattro cursori e tre punti di controllo. I cursori vengono
utilizzati per controllare rispettivamente le alte luci, le luci, i
colori scuri e le ombre (qui le ombre indicano le zone molto scure
prossime al nero). Spostando il mouse sui quattro cursori apparirà una
zona evidenziata attorno la curva che rappresenta quale parte della
curva è alterata dal cursore. Spostare il cursore dell Alteluci a
sinistra per rendere le luci meno luminose, spostarla a destra per
renderle più luminose. Il cursore *Luci* modifica i colori chiari, ma
non le luci nello stesso modo come il cursore delle Alteluci, così come
il cursore *Livello del nero*: spostandolo a destra schiarisce i toni
scuri, spostandolo a sinistra li oscura. Il cursore *Ombre* funziona
come il cursore *Livello del nero*, ma solo sulle parti più scure della
foto. È possibile costruire nuovamente la curva S stilizzata sopra,
anche se la curva parametrica fornisce meno controllo "estremo" sulla
forma della curva. Questa modalità, tuttavia, ha i propri vantaggi, in
quanto le curve possono essere modellate in modo ben controllato. Si
noti che l'utilizzo di questi cursori può avere una profonda influenza
sul contrasto complessivo dell'immagine.

Usa, se necessario, i tre punti di controllo sotto la curva. Determinano
quale punto della curva sarà interessato quando si sposta i cursori.
Spostando il punto centrale di controllo a destra, l'immagine diventa
più scura (la forma della curva cambia di nuovo, così come l'area scura
attorno alla curva), spostandola a sinistra rende l'immagine più
luminosa. Spostando il punto di controllo sinistro a destra scurisce le
aree scure, spostandolo verso sinistra le schiarisce. Muovendo il punto
di controllo destro a destra rende le luci più luminose, spostandolo a
sinistra scurisce le aree chiare.

Utilizzare i pulsanti*Reset to default*
![Image:Gtk-undo-ltr.png](Gtk-undo-ltr.png "Image:Gtk-undo-ltr.png")
accanto ai cursori per ripristinare i singoli cursori, utilizzare lo
stesso pulsante nella parte superiore della curva di tonalità per
ripristinare tutti e quattro i cursori e i punti di controllo a lineare
(zero).  

### Gabbia di controllo

![](Curve_control_cage_s.png "Curve_control_cage_s.png") A prima vista
questo tipo di curva sembra molto simile alla curva *Custom*, ma ci sono
alcune differenze però. Con la curva *Custom*, la curva tocca tutti i
punti di controllo. Questo non è il caso della curva *Gabbia di
Controllo*. Per visualizzarlo, fai clic su qualche punto sulla linea e
sposta il punto nero verso sinistra o verso destra. Ora la curva passa
vicino al punto nero, ma non la tocca. Un'altra differenza è che la
*gabbia di controllo* consente una sezione retta della curva, mentre non
è possibile eseguire questa funzione con la curva "Custom". La curva
*Gabbia di controllo* richiede almeno tre punti per questo (quindi
cinque in totale). Tenendo premuto il tasto **Shift** mentre si trascina
un punto, aiuterà a creare facilmente una retta allineando il punto
sulla linea fatta dal punto precedente e successivo (sulla linea
visualizzati in rosso). Ora fai un nuovo punto tra i due più sinistra e
spostalo. Come si può vedere, solo la parte sul lato sinistro si muove,
non il resto della curva.  

## Modalità curva

Accanto a ciascun tipo di curva, troverete un selettore di combinazione
*Curve Mode*. Ciò consente di scegliere l'algoritmo che verrà utilizzato
per la curva corrispondente. La modalità curva avrà un forte effetto
sull'aspetto dei colori, soprattutto se si utilizza una curva di
miglioramento del contrasto (curva S). Questo può essere utilizzato per
l'effetto creativo, ma può per alcuni scopi o stili causare modifiche di
colore indesiderate a seconda di quale modalità si sceglie. Scegli una
modalità che sia adatta al tuo gusto e alle esigenze specifiche della
foto a portata di mano. Combinando due curve diverse nella curva di tono
1 e 2 è possibile ottimizzare ulteriormente l'aspetto.

### Standard

Questa è la modalità più semplice (e l'unica disponibile nelle versioni
precedenti di RawTherapee e si trova in qualche forma nella maggior
parte dei software di elaborazione immagini): i valori di ciascun canale
RGB vengono modificati dalla curva in una "corrispondenza", cioè la
stessa curva è applicata a tutti i canali.

L'inconveniente di questa modalità è che, ad esempio, considerando una
forma di curva a S per ottenere un maggior contrasto, un colore
arancione con un alto valore di rosso e verde e un basso valore di
azzurro tendono a spostarsi verso il giallo, perché la componente rossa
e verde verra' sollevata, mentre quella blu sarà abbassata.

In generale una curva S aumenta la separazione dei canali e aumenta così
la saturazione, che è un comportamento simile a come reagisce il colore
di una pellicola al contrasto. Questo, insieme alla semplicità di
implementazione, ha reso il tipo di curva popolare nei convertitori raw
ed è spesso l'unica alternativa disponibile in un software meno
flessibile.

### Standard pesato

È possibile utilizzare questo metodo per limitare il passaggio del
colore della curva standard, anche se non lo sopprime completamente.
Tenendo in conto l'esempio precedente, questo metodo aumenterà il primo
componente (rosso) e modificherà anche linearmente la componente verde e
blu sollevandoli. Concludiamo con 3 valori (R, g e b) mentre abbiamo
solo elaborato il componente rosso.

Questo processo viene poi fatto per la componente verde e blu, quindi
alla fine del processo, concludiamo 9 valori (R, g, b / r, G, b / r, g,
B). I valori della stessa componente vengono quindi mescolati insieme,
che producono il colore risultante con un cambiamento di colore meno
evidente.

### Pellicola

La curva cinematografica fornisce un risultato molto simile al tipo
standard (vale a dire un forte aumento della saturazione con un maggior
contrasto), ma la tonalità RGB-HSV è costante, ovvero ci sono meno
problemi di spostamento del colore. Questo tipo di curva è stato
progettato da Adobe come parte di DNG ed è quindi quello utilizzato da
Adobe Camera Raw e Lightroom.

### Fusione Saturazione/Valore

Questa modalità è generalmente più adatta per gli scatti high-key (toni
chiari) ma può essere utilizzata anche per l'effetto creativo in altre
foto. Viene calcolato il valore medio dei tre componenti e la curva
viene applicata a questo valore, dando un guadagno positivo o negativo.
Il colore viene convertito nella rappresentazione HSV, della tonalità,
della saturazione e del valore, quindi se il guadagno è positivo, il
pixel è condotto linermente al Valore = 1 e Saturazione = 0, la tonalità
è conservata. Se il guadagno è negativo, il pixel è portato linearmente
al Valore = 0, mentre la Saturazione e Tonalitò sono conservati.

Il risultato è molto simile a una curva di luminanza nello spazio Lab
(cioè varia il contrasto senza influenzare la tonalità o la
saturazione). Le curve che aumento il contrasto generano un aspetto che
sarà in genere un po' desaturato. Questo non è dovuto al fatto che la
curva desatura i colori, ma perché nella visione umana il contrasto e la
saturazione sono strettamente accoppiati, quindi la stessa immagine con
maggiore contrasto richiede che anche la saturazione sia aumentata per
conservare lo stesso aspetto.

### Luminanza

Ogni elemento del pixel viene incrementato dallo stesso fattore, in modo
che il colore e la saturazione siano stabili, il risultato è molto
simile al colore originale. Tuttavia, le curve che aumentano il
contrasto possono comunque portare a un aspetto leggermente desaturato
per la stessa ragione descritta per la modalità della curva di fusine
saturazione/valore. Se si desidera contrastare manualmente la
desaturazione, utilizzare il cursore Cromatico L\*a\*b\* è un modo più
naturale per farlo rispetto all'utilizzo del cursore di saturazione
basato su RGB.

Nonostante la visualizzazione dell'istogramma R, G e B (fuso) sullo
sfondo della curva, la curva opera sui valori di luminanza, dove
[Relative Luminance](https://en.wikipedia.org/wiki/Relative_luminance) Y
= R \* 0.2126729 + G \* 0,7151521 + B \* 0,0721750 In primo luogo viene
ottenuto il relativo valore di luminanza di un pixel, quindi la curva
viene applicata a quel valore, viene calcolato il fattore di
moltiplicazione tra prima e dopo e questo fattore viene applicato a
ciascun componente R, G e B. Questo è in contrasto con gli altri metodi
in cui la curva viene applicata separatamente a ciascuna componente R, G
e B.

### Percettivo

Questa modalità manterrà l'aspetto originale del colore per la tonalità
e la saturazione, vale a dire se ad esempio si applica una curva a S,
l'immagine otterrà un contrasto più elevato, ma le tonalità resteranno
uguali e l'immagine non sembrerà più o meno satura rispetto
all'originale. È particolarmente utile stabilire un piacevole contrasto
di base senza distorcere i colori forniti da un profilo della fotocamera
che non applica una curva stessa (se si utilizza un profilo di terze
parti che applica una curva che in genere è già mappato percepito con
tecniche analoghe descritte qui).

L'algoritmo funziona come segue: analizza la curva per ottenere un
valore di contrasto che viene utilizzato come base per scalare la
cromaticità (saturazione) in modo che più contrasto sia abbinato a più
saturazione e viceversa. Poiché il contrasto e la saturazione sono
strettamente accoppiati nella visione umana, questa scala è necessaria
per rendere la saturazione "apparente" dei colori costante. Ci sono
ulteriori raffinamenti come l'aumento della saturazione più nelle ombre,
e meno per i colori già altamente saturi, anche questo corrisponde a
fenomeni di visione umana in modo che l'effetto netto sia sempre quello
che i colori appaiono invariati. Negli estremi estremi in prossimità del
punto di bianco, l'algoritmo si fonde sul bianco (come le curve
standard) rendendo un colore meno fedele ma più pratico per l'output
reale poiché il colore più brillante del supporto di stampa (schermo o
carta) è comunque bianco.

Tuttavia è da tenere presente che il modello percettivo non è perfetto e
non può essere perfetto. Questa è solo una curva, il contenuto
dell'immagine non viene analizzato e non vengono apportate modifiche
localizzate. Ciò significa ad esempio che per una curva a S un grande
cielo blu piatto (basso contrasto locale) può apparire leggermente più
saturo dell'originale. Se si desidera eseguire i confronti A/B non si
confrontano affiancati, poiché l'occhio verrà confuso dai due livelli di
contrasto visualizzati simultaneamente e poi la saturazione non apparirà
la stessa, ma conviene aspettare pochi secondi perchè l'occhio possa
adattarsi al colore.

Se si desidera aggiustare ulteriormente la saturazione manualmente, è
generalmente meglio utilizzare il cursore Chroma in Lab (oltre alle
curve di cromaticità presenti sempre in Lab).

A causa delle molteplici componenti dell'algoritmo è notevolmente più
lento rispetto alle altre modalità della curva, e la frequenza di
aggiornamento molto lenta.
