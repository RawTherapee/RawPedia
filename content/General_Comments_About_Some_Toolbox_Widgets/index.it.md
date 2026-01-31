---
title: General Comments About Some Toolbox Widgets
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
---

**Questo articolo è importante** - alcune cose possono sembrare scontate
se sei un utente esperto, ma alcune cose sicuramente non sono conosciute
e conoscerle ti permetterà di utilizzare RawTherapee più velocemente e
più facilmente. Prenditi cinque minuti per leggerlo!

<hr>

Il pannello sul lato destro dell'anteprima contiene i controlli per
tutti gli strumenti disponibili in RawTherapee. Possono fare molto,
forse anche di più di quanto si possa desiderare! Se sei nuovo a
RawTherapee o nuovo per l'elaborazione raw in generale, non sentirti
sopraffatto, perché non c'è bisogno di toccare tutti questi cursori per
ottenere risultati decenti. In questa sezione troverai una breve
descrizione di tutti gli strumenti disponibili, scheda dopo scheda.

## Pannelli

Un pannello è un elemento a scomparsa che contiene pulsanti, strumenti,
istogrammi, ecc. La scheda Editor contiene tre pannelli principali:
quello a sinistra che contiene la cronologia, quello a destra che
contiene gli strumenti e se sei in "Modalità editor singolo" quella in
alto che contiene [Seguenza
immagini](The_Image_Editor_Tab/it#The_Filmstrip.md). Possono
essere nascosti con i piccoli pulsanti freccia o utilizzando i [tasti di
scelta rapida](Keyboard_Shortcuts/it.md), lasciando più spazio
per l'anteprima dell'immagine.

È possibile utilizzare la rotellina del mouse per scorrere in su/giù in
modo sicuro i pannelli senza timore di modificare accidentalmente un
cursore, in quanto RawTherapee richiede di tenere premuto il tasto
Maiusc mentre si utilizza la rotellina del mouse se si desidera
manipolare un cursore o passare attraverso le opzioni in un menu a
discesa (chiamato "combobox").

## Strumenti

RawTherapee dispone di molti strumenti e ogni strumento dispone di uno o
più controlli, o [widgets](https://en.wikipedia.org/wiki/Widget_(GUI)),
che puoi spostare o spingere o far scorrere per fare qualcosa con il
programma. Esse sono suddivise tra le schede Esposizione, Dettaglio,
Colore, Wavelet, Transform, Raw e Metadati. Ad esempio nella scheda
Esposizione ci sono strumenti che si occupano dell'esposizione, come lo
strumento Esposizione e lo strumento Ombre/Alte luci, la scheda Colore
ha lo strumento di bilanciamento del bianco e così via.

Poiché ci sono tanti strumenti, noterete che lo spazio dello schermo
verticale è prezioso, e a volte, è necessario nascondere alcuni
strumenti per vedere gli altri. RawTherapee semplifica quest'operazione.
Facendo clic con il pulsante destro del mouse su un titolo dello
strumento, lo espande e comprime tutti gli altri strumenti della stessa
scheda. Apprezzerai questa scorciatoia quando prenderai in
considerazione il tempo che avresti speso manualmente per richiudere gli
strumenti aperti...

A sinistra della maggior parte dei titoli degli strumenti c'è un
pulsante che consente di abilitare o disattivare lo strumento
corrispondente. Il concetto di essere abilitato o disabilitato non ha
sempre senso - ad esempio che cosa significherebbe avere lo strumento
bilanciamento del bianco disabilitato? Deve sempre essere utilizzato un
bilanciamento del bianco: in questo modo questi strumenti invece di un
pulsante attivato/disattivato usano semplicemente un simbolo a triangolo
per consentirti di espanderli o di comprimerli. Infine, noterai che
nella scheda Navigatore selezionando più foto, il pulsante di
alimentazione può assumere un terzo stato che sembra solo metà
abilitato - questo stato, chiamato "incoerente", significa che lo
strumento in questione non è abilitato in tutte le foto selezionate.

![Tool disabled.](expanderDisabled.png "Tool disabled.") Tool disabled.

![Tool enabled.](expanderEnabled.png "Tool enabled.") Tool enabled.

![Tool inconistent.](expanderInconsistent.png "Tool inconistent.") Tool
inconistent.

![Tool collapsed.](expanderClosed.png "Tool collapsed.") Tool collapsed.

![Tool expanded.](expanderOpened.png "Tool expanded.") Tool expanded.

## Sliders

Ogni cursore ha tre valori nella memoria:

- Il valore corrente, quando si sposta il cursore in qualsiasi
  posizione,
- Il valore "predefinito", quello impostato dal programmatore come
  predefinito. Può essere richiamato facendo clic sul pulsante 'Reset',
- Il valore "iniziale", il valore del profilo utilizzato quando
  l'immagine è stata caricata nell'editor. Può essere richiamato con
  **Control-click** sul pulsante 'Reset'.

Come scritto in precedenza, se si desidera spostare un cursore o
posizionarsi su un combobox con la rotella del mouse, si deve
contemporaneamente tenere premuto il tasto Maiusc, altrimenti invece di
spostare il cursore si scorrazzerà su/giù nel pannello.

## Curve Editors

RawTherapee dispone di tre tipi di editor di curve - Curve di soglia,
Curve di tono e Curve piatte. Sono presentate qui di seguito insieme ad
alcuni indicatori generali.

### Curve di soglia

Le curve di soglia sono le più semplici. Sono usate per indicare a uno
strumento RawTherapee i toni (oppure i colori o i valori di saturazione)
che si desidera elaborare (o elaborare in modo diverso).

Ad esempio, considerare l'editor della curva di soglia sullo strumento
Detail -\> [Nitidezza](sharpening/it).
![](_Sharpening_Threshold.png "_Sharpening_Threshold.png")
L'impostazione mostrata indica che lo strumento di nitidezza aumenta
rapidamente l'affilatura nelle aree scure (la linea ripida a sinistra),
mantiene a pieno la nitidezza attraverso le tonalità intermedie (l'area
piatta) e poi spegne lentamente la nitidezza nelle alte luci (lunga
discesa verso il basso). Il trascinamento di uno dei punti di controllo
sposterà il pendio che porta in su o in giù a partire dal punto. Per
spostare solo il punto, ma non la pendenza nel suo insieme, tenere
premuto il tasto shift mentre si trascina.

In alto a destra c'è un pulsante di reset che ripristina il valore
predefinito.

**Attenzione:** reimpostare la curva è considerata una modifica della
curva, quindi se hai appena modificato la curva e premi erroneamente il
pulsante *Reset*, non c'è modo di ripristinare la curva. (Ctrl-z passerà
ad un punto precedente nell'elenco *Storia*, non alla modifica della
curva). Questo commento si applica anche alle curve di tono e curve
piatte.

Troverete anche Curve di soglia utilizzate negli strumenti [Contrasto da
Dettaglio Livelli](Contrast_by_Detail_Levels/it.md) e
[Vivacità](vibrance/it).

Potresti aver notato che le curve di soglia sono in realtà costituite da
poche righe piuttosto che da una curva. Se questo ti dà fastidio, ti
consigliamo di fare una pausa prima di passare a Curve piatte.

### Commenti generali su curve di tono e curve piatte

Le curve di tono e curve piatte sono più potenti delle curve soglia e
dispongono di alcuni controlli che non sono necessari sulle curve
soglia.

Ogni editor di curva di tono o piatta ha un pulsante per selezionare il
suo tipo. E' il cosiddetto pulsante 'Toggle', cioè rimarrà selezionato o
verrà liberato dopo ogni clic su di esso. Attivando/disattivando il
pulsante della curva verrà rispettivamente visualizzato/nascosto
l'editor associato. Questo è molto utile e consente di risparmiare un
sacco di spazio durante la gestione di gruppi di curve (ad esempio,
vedere l'editor della curva di Lab).

Queste curve hanno un pulsante Reset a destra che ripristina solo la
curva visualizzata (o il pulsante premuto).

Hanno anche uno strumento pipetta e un nodo in/out per input dei valori,
che meritano sezioni proprie.

  

#### Pipetta

[thumb](image:rt_pipette_2_lab_ba.jpg) La maggior parte delle
curve in RawTherapee ha un pulsante pipetta [image:
editmodehand.png](image:_editmodehand.png.md). Questa
funzionalità è un ottimo modo per specificare le tonalità, i toni e le
aree di una particolare saturazione, e utilizzarla renderà più semplice
e veloce l'elaborazione delle tue immagini. Diciamo che si desidera
modificare la tonalità viola di un fiore, per renderla più rossa. Senza
la pipetta, dovresti indovinare il colore esatto della tonalità,
altrimenti la gamma interessata di tonalità sarebbe troppo larga e
potresti finire per cambiare qualcosa che non volevi cambiare. Con la
pipetta, basta cliccare sul fiore e un punto compare nella curva
relativa. È possibile modificare questo punto a piacimento, sapendo che
rappresenta la tonalità esatta desiderata.

Lo strumento pipetta può essere attivato per ogni curva, semplicemente
facendo clic su di esso. Ora, quando si posiziona il cursore sopra
l'anteprima principale, noterete che una linea verticale (o quattro
linee verticali) apparirà nel pannello della curva. Questa linea
rappresenta il valore di interesse del pixel che si sta analizzando. Per
inserire un punto di regolazione nella curva per il valore di interesse
in cui si passa sopra, basta un Ctrl+clic con il tasto sinistro
nell'anteprima e un punto viene visualizzato nella curva. È possibile
regolare tale punto senza lasciare l'area di anteprima, tenendo premuto
il pulsante sinistro del mouse dopo aver posizionato il punto sulla
curva e muovendo il mouse verso l'alto e verso il basso si sposterà di
conseguenza il punto verso l'alto e verso il basso. Ricordiamo che
tenendo premuto Ctrl durante la modifica di un punto della curva
diminuisce la velocità del mouse in modo da poter regolare finemente i
punti, ma di solito non avrai bisogno di questo, quindi dopo aver
premuto Ctrl+clic tasto sinistro per posizionare il punto, lasciare
Ctrl, ma tenere premuto il pulsante sinistro del mouse.

Per disattivare la pipetta, fare clic con il pulsante destro del mouse
ovunque nell'area di anteprima oppure fare nuovamente clic sul pulsante
della pipetta.

Non è necessario disattivare la pipetta della curva precedente per
utilizzarla su una nuova curva, solo attivarla come al solito e la
vecchia si disattiva automaticamente.

  

#### Nodo in/out Curva di Valore

Introdotto nella versione 4.2.192, ogni curva di valore ha un nodo
in/out di input. Ad esempio, è possibile utilizzare questo strumento per
abbinare i valori del nodo su una foto di un target a colori con valori
di patch noti.

Lo strumento funziona con i nodi e il modo migliore per creare questi
nodi è utilizzare la pipetta. Per questo esempio, inizieremo con una
curva senza nodi e ne creeremo alcuni utilizzando la pipetta. Fai clic
sul pulsante [image: Gtk-edit.png](image:_gtk-edit.png)
vicino alla curva e fai clic sul pulsante [image:
editmodehand.png](image:_editmodehand.png.md) della pipetta. Ora
vedrete i valori "I" (in) e "O" (out) visualizzati sotto la curva.
Corrispondono al punto sotto il cursore del mouse se lo si muove sopra
la curva. Spostare il cursore sopra l'anteprima dell'immagine. Dal
momento che si attiva la pipetta, basta fare un Ctrl + click su un punto
nell'area dell'anteprima per inserire un nodo nella curva corrispondente
al valore di quel punto (qualunque sia il valore, ad esempio per la
curva L\*, il valore è il valore della luminosità del pixel dove è stato
prelevato il valore dall'anteprima e il valore di output è il valore
trasformato dalla curva). Fatto quindi Ctrl + clic su un punto
nell'anteprima, un nodo appare nella curva. Per modificare i valori di
in/out del nodo, fare clic con il pulsante destro del mouse sul nodo. Si
trasforma in rosso con un anello rosso intorno a esso. Ora puoi
modificare i valori di in/out e vedere il movimento del nodo in tempo
reale. Una volta terminata la modifica, fare clic con il pulsante destro
del mouse ovunque all'interno dell'area della curva diversa dal nodo per
uscire dalla modalità di modifica dei nodi o semplicemente fare
nuovamente clic sul pulsante di modifica del valore del nodo per
disattivarlo.

### Curve di tono

Le curve di suono sono un pò misconosciute poiché, mentre alcune sono
utilizzate per regolare i toni, altri sono usati per regolare la
saturazione, la cromaticità o altre proprietà. Il loro scopo è quello di
mappare un valore di ingresso (sull'asse orizzontale o X) ad un valore
di uscita (misurato sull'asse verticale o Y). Se la matematica non è il
tuo forte, non ti preoccupare - dopo una breve esperienza, tutti
sviluppano rapidamente una comprensione intuitiva.

<figure>
<img src="/images/Tone_Curve.png" title="Tone_Curve.png" />
<figcaption>Tone_Curve.png</figcaption>
</figure>

Ad esempio, considerare la figura a destra - parte dello strumento
[Esposizione](exposure/it). La parte sinistra del grafico
rappresenta i toni più scuri, la parte destra rappresenta i toni più
luminosi della foto. È possibile vedere che la parte inferiore sinistra
della curva è stata spostata verso l'alto. Ciò provoca l'aumento delle
aree scure. Allo stesso modo, la porzione destra in altro della curva è
stato abbassata, tagliando le aree luminose.

La figura mostra il menù contestuale delle diverse curve. Le curve di
tono consentono quattro modi diversi di manipolare la curva:

- **Lineare:** Il tipo di default - una linea retta che non comporta
  alcuna modifica ai valori di input. Matematicamente si può concludere
  che è il grafico di y = x. Per tutti impostare il controllo sulla
  curva lineare serve per "spegnere" la curva.
- **Custom:** Il tipo più comunemente visto in altri software. Fare clic
  per trascinare un punto di controllo in qualsiasi punto della curva e
  quindi trascinare il punto di controllo per modificare la forma della
  curva. Il punto in alto a destra rappresenta le aree più luminose
  della foto. Trascinare tale punto verticalmente verso il basso per
  rendere le luci meno luminose; spostalo orizzontalmente a sinistra per
  rendere le aree luminose più brillanti, forse a rischio della
  sovraesposizione delle alte luci. Il punto in basso a sinistra
  rappresenta le aree più scurea della foto. Spostare quel punto
  orizzontalmente a destra per rendere la foto più scura, forse a costo
  di qualche sottoesposizione. Spostarla verticalmente in modo da
  rendere più chiari gli scuri.
- **Parametric:** Consente di utilizzare cursori piuttosto che
  trascinare direttamente la curva. Per il tipo di curva parametrica,
  facendo clic sul pulsante destro del mouse sopra il selettore di zona
  (![Image:
  Parametric_curve_bar.png](_Parametric_curve_bar.png "Image: Parametric_curve_bar.png"))
  ripristina la posizione delle maniglie ai valori predefiniti. (Si
  ripristinerà anche il pulsante di ripristino globale.)
- **Gabbia di controllo:** A prima vista questo tipo di curva assomiglia
  molto alla curva personalizzata, ma ci sono grosse differenze. Con la
  curva personalizzata, la curva tocca tutti i punti di controllo.
  Questo non è il caso della curva a gabbia di controllo - i punti di
  controllo attirano la curva verso di loro ma la curva non riesce
  effettivamente ad oltrepassarli. Un'altra differenza è che la gabbia
  di controllo consente una sezione retta della curva, mentre non è
  possibile farlo con la curva personalizzata. La curva a gabbia
  necessita di almeno tre punti per questo (quindi cinque in totale).
  Tenendo premuto il tasto Maiusc mentre si trascina un punto, aiuterà a
  creare facilmente una linea retta tracciando il punto sulla linea
  fatta dal punto precedente e successivo (visualizzato in rosso dallo
  strumento "snap to"). Molti utenti preferiscono le curve a Gabbia di
  Controllo alle altre.

### La curva piatta

[frame](image:flat_curve_justcurve.png) Un certo numero di
strumenti in RawTherapee utilizza la *curva piatta*:

- [Lab Adjustments](lab_adjustments)
  - [LH](lab_adjustments#lh_curve)
  - [CH](lab_adjustments#ch_curve)
  - [HH](lab_adjustments#hh_curve)
- [Defringe](defringe)
  - [Hue](defringe#hue)
- [HSV Equalizer](hsv_equalizer)
  - [H](hsv_equalizer#h)
  - [S](hsv_equalizer#s)
  - [V](hsv_equalizer#v)

È molto semplice da usare una volta che lo si capisce, come esempio,
quindi, utilizziamolo [HSV Equalizer](hsv_equalizer) nella
scheda Colore [image:colour.png](image:colour.png). Facciamo
clic sull'icona del menù a discesa [image:
Drop-down.png](image:_Drop-down.png.md) accanto al pulsante
H(ue) e scegliamo "*Minima/Maxima control points*" [image:
CurveType-controlPoints.png](image:_CurveType-controlPoints.png.md)
. Appariranno sei punti sulla linea orizzontale al centro e sei linee
verticali che attraversano questi puntini. Si noti che queste righe sono
colorate; da sinistra a destra: rosso, giallo, verde, acqua, blu e
magenta. Ora fatto clic sul primo punto rosso (il cursore cambia in una
piccola mano) lo si sposta leggermente verso l'alto e verso il basso.
Risultato: i colori rossi cambiano rapidamente a verde, azzurro e
magenta quando il cursore viene spostato verso l'alto e verso il rosa,
il blu e il verde quando si è spostato verso il basso.

Notare che una nuova linea orizzontale viene visualizzata quando si
trascina un punto di colore e viene visualizzata la modifica del colore.
L'asse verticale rappresenta i colori di input mentre l'asse orizzontale
i colori di uscita.

Quando si fa clic e si trascina una linea verticale (la linea, non il
punto!), il primo movimento determinerà il tipo di movimento: verticale
o orizzontale (quindi fai attenzione a questo primo movimento se vuoi
avere un risultato prevedibile). Se si desidera spostare il punto in
entrambe le direzioni contemporaneamente, fai clic e trascina il punto
stesso. Per spostare il punto solo in una direzione (solo
orizzontalmente o solo in verticale) è possibile utilizzare la funzione
'snap to' tenendo premuto il tasto Maiusc durante lo spostamento del
punto.

[frame](image:flat_curve_zoom.png) È facile vedere se un
punto è sul suo valore neutro (cioè sulla linea centrale) perché il
colore del punto sarà verde. Non appena sposta un punto dal suo valore
neutro, cambia colore in nero.

Il [HSV Equalizer](hsv_equalizer) si avvolge sull'asse
orizzontale, quindi la linea verticale destra è uguale alla linea
sinistro. È possibile vedere questo trascinando la linea rossa sul lato
sinistro un pò a sinistra. Ora il punto sinistro del grafico è nella
stessa posizione del punto giusto. Tenendo premuto il tasto **Shift**
mentre trascinate un punto, non fa modificare lungo l'asse orizzontale,
utile per prevenire salti accidentali di curva in luoghi difficili come
ai bordi.

È possibile eliminare i punti trascinandoli dal campo dell'editor. È
possibile aggiungere punti facendo clic su un punto della curva. Quando
si posiziona il mouse su uno dei punti, viene visualizzato un indicatore
giallo e blu. Posiziona il mouse su quello giallo e il cursore cambia in
una freccia sinistra. Ora puoi trascinare questo punto a sinistra per
modificare la pendenza della curva. Allo stesso modo ma al contrario per
l'indicatore blu.

Per avere un'idea di come funziona questo editor, elimina tutti i colori
lasciandone solo due (ad esempio rosso e giallo) e sposte il grafico in
giro, modifica la pendenza e osserva cosa succede alla foto.

E' possibile ripristina la curva *Hue* a "*Lineare*" (nessuna modifica)
facendo clic sull'icona di reset
[image:Gtk-undo-ltr.png](image:gtk-undo-ltr.png) accanto al
pulsante *Valore*. Per confrontare gli effetti della curva "Hue" con
lineare: passare tra "*Lineare*" e "*Minima/Maxima punti di controllo*"
nel menu a discesa accanto a questo pulsante oppure utilizzare l'elenco
di cronologia sul lato sinistro dello schermo.

È possibile salvare una curva per un utilizzo successivo facendo clic
sul pulsante del disco. Si noti che solo la curva H, S o V effettiva
(visualizzata) viene salvata, non tutte e tre in una volta, quindi non
date alla curva un nome come my_hsv perché non le descrive tutte ma solo
la curva H, S o V visualizzat, quindi forniamo ai file un nem più
corretto quale my_hue, my_sat e my_val. L'estensione verrà aggiunta
automaticamente, "*.rtc*".

## L'area di anteprima

L'anteprima è progettata per mostrarvi il risultato più realistico
possibile, tuttavia bisogna tenere presente che più un'immagine è più
grande, più occorre per elaborarla. Per motivi di velocità, l'anteprima
degli effetti della maggior parte degli strumenti non viene calcolata
sull'immagine di dimensioni complete (che richiederebbe lo stesso tempo
del salvataggio dell'immagine, rendendo impossibile utilizzare cursori e
curve), ma sull'immagine di anteprima di dimensioni della tua area di
anteprima. Molti strumenti, ad esempio lo strumento
[Esposizione](exposure/it), possono essere applicati ad
un'immagine di qualsiasi dimensione e i loro effetti saranno identici
indipendentemente dalla dimensione dell'immagine su cui vengono
applicati. Tuttavia, alcuni strumenti dipendono dalla dimensione, ad
esempio tutti gli strumenti della scheda Dettagli, il che significa che
se applicate uno di questi strumenti ad un'immagine di dimensioni
complete e ad una versione più piccola e riduce l'immagine piena alla
dimensione dell'immagine più piccola, le due immagini non corrispondono.
Per motivi di velocità, RawTherapee deve utilizzare la piccola immagine
di anteprima in modo che l'esperienza di modifica degli strumenti possa
essere veloce e fluida, ma ciò significa che gli effetti degli strumenti
dipendenti dalla dimensione non sarebbero esatti quando vengono
applicati ad una piccola anteprima zoomata. Abbiamo deciso di
disattivare completamente gli effetti di anteprima di questi strumenti a
livelli di zoom inferiori al 100% o mantenere gli effetti di anteprima
attivi ma avvisarvi che ciò che vedete a livelli di zoom inferiore al
100% può essere impreciso a seconda delle impostazioni degli strumenti
(ad esempio [Mappa dei Toni](tone_mapping/ti) e
[Wavelet](wavelet/it) possono essere precisi a livelli di
zoom inferiori al 100% oppure possono essere imprecisi, a seconda delle
impostazioni. Saprai quali strumenti sono questi perché sono
contrassegnati da un'icona "1:1" ![icona zoom 100
dell'identificatore.](zoom-100-identifier.png "icona zoom 100 dell'identificatore.")
accanto ai loro nomi. RawPedia spiega quanto preciso l'anteprima sia per
tutti gli strumenti interessati nella pagina di ciascun strumento.
