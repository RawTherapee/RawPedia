---
title: Noise Reduction
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<figure>
<img src="/images/noisereduction2.jpg" title="noisereduction2.jpg" />
<figcaption>noisereduction2.jpg</figcaption>
</figure>

Non tutti i requisiti per una buona riduzione del rumore sono gli
stessi. Ad alcuni piace un risultato completamente pulito e liscio,
mentre altri preferiscono avere qualche granello lasciato per dare alla
foto una qualità più filmosa. Il potente strumento di riduzione del
rumore di RawTherapee soddisfa tutte queste esigenze: consente di
eliminare il rumore mantenendo i dettagli. Utilizza
[wavelets](http://en.wikipedia.org/wiki/Wavelet), e la [Trasformata di
Fourier](https://en.wikipedia.org/wiki/Fourier_transform) e un [wiki
/Median_filter filtro mediano](https://en.wikipedia.org/) per esprimere
la sua magia. Continua a leggere per imparare ad usarlo in modo
efficiente.

## Utilizzo

Quando si lavora con immagini ad alti ISO molto rumorose, è
consigliabile utilizzare i metodi di demosaicizzazione LMMSE o IGV.
Questi metodi prevengono la comparsa di false strutture (pattern) a
labirinto e impedisce all'immagine di sembrare slavata a causa di una
forte riduzione del rumore.

Per trovare l'insieme migliore dei valori di riduzione del rumore per
l'immagine:

1.  Controllare gli strumenti di nitidezza per assicurarsi di non
    evidenziare tutti i dettagli particolari, perché la foto rumorosa
    non ha dettagli precisi! Tutto quello che invece fanno è amplificare
    il rumore. Se si sta usando *Contrasto da Livelli di dettaglio* per
    realizzare un'immagine con più profondità, assicuratevi che il primo
    cursore **'0 (Finest)**' e probabilmente il secondo '*'1*" , sono
    spenti.
2.  Ingrandire la foto al 100% e scoprire un'area che ha sia parti a
    fuoco nitide che ampie zone uniformi, così come grandi piani fuori
    fuoco, in modo da impedire che la riduzione del rumore cancelli i
    dettagli mentre lo si applica.
3.  Inizia impostando il cursore "'Dettaglio di Luminanza' 'su 0,
4.  Decidere se si desidera lavorare solo con il cursore ' Luminance'' o
    se si desidera utilizzare la Curva di Luminance per un controllo più
    fine. Aumentare il cursore o la curva solo finché il rumore di
    luminanza non è stato levigato.
5.  Poiché il rumore di luminanza è tutto esaurito (anche se non abbiamo
    ancora ripreso alcun dettaglio), possiamo vedere il rumore del
    colore molto chiaramente. Questo è un buon momento per denoicizzare
    i canali di colore.
    1.  Impostando manualmente i cursori: aumentare '*'Chrominance
        (Master)*" ad un livello dove il rumore di crominanza è
        cancellato, ma i dettagli di colore nei piccoli oggetti non sono
        stati persi. È possibile ridurre o aumentare gli effetti della
        riduzione del rumore sui canali rosso/verde e blu/giallo
        rispettivamente abbassando o sollevando i cursori
        "*Chrominance - Red-Green / Blue-Yellow*".
    2.  Oppure utilizzando la modalità "automatica"
6.  Aumentare ora il cursore "'Luminance Detail''' per recuperare
    dettagli fino a che non siate soddisfatti del rumore: dettagli
    off-off.

## Interfaccia

### Metodo

La riduzione del rumore può essere effettuata negli spazi di colore RGB
o Lab. Lavorare nello spazio Lab offre il vantaggio di mantenere il
colore indipendente dalla luminanza. La differenza tra la modalità Lab e
RGB è spesso trascurabile se si utilizza solo la riduzione del rumore di
luminanza (tramite i cursori ""Luminance"" e "*Luminance Detail) e più
evidente quando si effettua una forte riduzione del rumore di crominanza
tramite il cursore "*Chrominance - Master''".

Esamina esattamente grandi aree di forte saturazione con dettagli
sottili - come il pattern su una camicia colorata o il petalo di un
fiore - mentre passerete tra le modalità RGB e Lab.

\<gallery caption="Comparison of Noise Reduction Methods" perrow="4"\|
style="text-align: center"\> Image:Rt noisereduction 1
off-vs-rgb.jpg\|Disabled vs enabled (RGB mode). Image:Rt noisereduction
2 rgb-vs-lab.jpg\|RGB vs Lab. Image:Rt noisereduction 3 lmmse
off-vs-rgb.jpg\|Disabled vs enabled (RGB mode). Image:Rt noisereduction
4 lmmse rgb-vs-lab.jpg\|RGB vs Lab.

</gallery>

### Qualità

"Alta" fa due passaggi di riduzione del rumore, ognuno con un algoritmo
diverso, per una qualità superiore al costo del tempo di elaborazione.
Puoi selezionare in "Preferenze\> Performance & Quality" il numero di
livelli per il wavelet:

- No: nessun livello extra
- Un livello o due livelli: aggiungere questo numero al riferimento. Ciò
  aumenta il tempo di elaborazione, ma migliora anche l'elaborazione del
  rumore cromatico, per lo più i "pacchetti"

### Pannello di luminosità

#### Controllo luminosità

Qui è possibile scegliere tra 2 opzioni per il controllo della
luminosità, utilizzando il cursore o utilizzando una curva. Entrambi i
sistemi non interagiscono.

##### Luminanza

Questo cursore consente di controllare il profilo grossolana della
luminanza.

##### Curva di luminosità

![](Rt_nr_luminancecurve_books.jpg "Rt_nr_luminancecurve_books.jpg")
Questa curva consente di individuare più precisamente le aree di una
luminanza specifica, in modo da poter avere una forte rimozione del
rumore nelle ombre e non toccare affatto le parti chiare. Ciò è
auspicabile in quanto il rumore generalmente sarà più forte nelle ombre
che nei punti illuminati. È possibile utilizzare la curva da sola o il
solo cursore, ma non entrambi contemporaneamente.

#### Luminanza - Dettaglio

Questo cursore è per il recupero di dettaglio dopo l'applicazione della
riduzione del rumore Luminance. Recupera la struttura mentre non
reintroduce il rumore, a meno che tu non imposta questo valore troppo
alto.

### pannello di crominanza

#### Metodo automatico

Questo metodo offre tre o quattro scelte secondo la configurazione
scelta in "Preferenze\> Performance & Quality":

##### Modalità strumento - "Standard"

- - Manuale
  - Globale automatico
  - Anteprima

##### Modalità strumento - "Esperto"

- - Manuel
  - Globale automatico
  - Automatico multi-zona
  - Anteprima multi-zona

##### Rumore di anteprima

- Un indicatore "Rumore di anteprima" fornisce i valori di rumore
  cromatici stimati, dopo l'elaborazione "Chrominance"
  - Media: stimare il valore medio del rumore, tutti i canali presi
    insieme
  - Alto: stimare il valore più alto del rumore, tutti i canali presi
    insieme

##### Manuale

- I tre cursori e la curva - la curva di Chrominance - agiscono
  sull'immagine completa. È possibile controllare manualmente le
  impostazioni dell'immagine.

###### Chrominance - Master

Applica la riduzione del rumore ai canali di colore. Se questo cursore è
a 0,5, i cursori Delta non hanno alcun effetto e il wavelet non è
abilitato.

###### Chrominance - Red-Green

Può essere utilizzato per ridurre o aumentare l'effetto della riduzione
del rumore di colore nel canale rosso-verde ("a" in Lab)

###### Chrominance - Blue-Yellow

Può essere utilizzato per ridurre o aumentare l'effetto della riduzione
del rumore di colore nel canale blu-giallo ("b" in Lab)

##### Globale automatico

- L'algoritmo di elaborazione, che agisce sull'immagine completa,
  dipende da diverse celle distribuite nell'immagine (9 finora). Per
  ogni cella, viene calcolato:
  - Un livello di rumore assoluto per il canale Red-Green e il canale
    Blue-Yellow;
  - un livello di rumore massimo per gli stessi canali

<!-- -->

- Se non è possibile scegliere il luogo delle celle, è possibile
  scegliere la dimensione (Preferenze\> Performance & Quality\>
  Dimensione cellulare):
  - Mini: 100x115 - Piccolo: 250x287 - Medio: metà delle dimensioni
    delle piastrelle (per impostazione predefinita) - Maxi: dimensioni
    delle piastrelle
  - Le piastrelle vengono utilizzate nell'elaborazione del rumore per
    aumentare e ridurre il consumo di RAM, con una dimensione di circa
    700 pixel.
  - Ci sono vantaggi e inconvenienti in ogni modalità:
    - Più piccole sono le celle, più veloce è l'elaborazione, possiamo
      mantenere questo caso per immagini omogenee
    - Più grandi sono le celle, quanto più siamo prossimi alle
      condizioni reali.

<!-- -->

- Puoi anche selezionare "Livello di denoising" in Preferenze\>
  Performance & Quality\> Livello di compensazione. Scegliere un livello
  di elaborazione del rumore: basso (per impostazione predefinita) o
  standard.

<!-- -->

- Poi, viene effettuato una ponderazione, tenuto conto dei livelli di
  rumore determinati sopra, per regolare i tre cursori (Master,
  Rosso-Verde, Blu-Giallo) e aggiornare "Anteprima del rumore"

<!-- -->

- L'immagine visualizzata nel pannello "Anteprima" mostra quali saranno
  le immagini TIF o JPG

<!-- -->

- Le impostazioni (posizione dei cursori) sono uguali qualunque sia la
  posizione "Anteprima" nell'immagine completa.

<!-- -->

- Le impostazioni non vengono memorizzate nei file pp3. Se si desidera
  riutilizzarli per operazioni su profili, è necessario passare in
  modalità "manuale"

##### Anteprima

- Questa modalità è ovviamente solo operativa con uno zoom al 100% e
  oltre, agisce sull'immagine completa
- Per ogni movimento di anteprima (movimento nell'immagine, zoom) viene
  eseguito il calcolo automatico di denoising
- Prende in considerazione la finestra operativa e calcola per questo, i
  rumori medi del canale Red-Green e il canale Blu-Giallo e il massimo
  per questi due canali.
- Questa finestra viene utilizzata come "area di selezione"
- I tre cursori "Master", Red-Green e Blue-Yellow e "Anteprima di
  rumore" vengono aggiornati.
- L'impostazione ottenuta scegliendo un'area viene utilizzata per
  l'immagine completa.

<!-- -->

- Se selezionate un'uscita TIF o JPG da questa selezione e in modalità
  zoom, l'immagine di uscita corrisponderà all'anteprima.
- A proposito della modalità "automatica", si consiglia di passare in
  modalità "manuale" dopo aver scelto l'area di anteprima e controllata
  la qualità di elaborazione, se si desidera mantenere questa
  impostazione per altre immagini.
- L'opzione Preference\> Performance & Quality\> Livello di allarme è
  operativa.

##### Multi-zone auto

- Questa modalità è operativa solo per un'uscita TIF / JPG ed è uscita
  abilitata se e solo se è selezionata "Multi-zone auto".
- L'elaborazione non è calcolata nell'immagine completa, ma per ogni
  piastra specifica.
- L'anteprima non è completamente utilizzabile, ma come è possibile
  leggerla nella sezione "Anteprima multi-zone", una comoda guida può
  consentire all'utente di avere una buona approssimazione dell'immagine
  finale spostando l'anteprima in piena Immagine.

<!-- -->

- La modalità "Auto multi-zone" utilizza le piastrelle utilizzate
  nell'elaborazione del rumore RawTherapee, per aumentare l'elaborazione
  e ridurre il consumo di memoria.

<!-- -->

- L'immagine è divisa in piastrelle dal software, con un passo verticale
  e orizzontale di circa 500 a 800 pixel.
- Ciò dà un certo numero di piastrelle che, a seconda della dimensione
  dell'immagine e dell'opzione scelta in "Preferenze\> Prestazioni e
  qualità\> Numero di piastrelle", possono variare da 12 a oltre 120.
- C'è una sovrapposizione di piastrelle con una transizione tra
  un'impostazione delle piastrelle e quelle delle piastrelle adiacenti.
  Non ci si deve preoccupare di una possibile differenza tra le tessere
  adiacenti.

Ogni piastra viene elaborata in modo indipendente, in base alla
dimensione della cella ("Preferenze\> Performance & Qualità") e termina
ad una impostazione dei canali rosso-verde e giallo-blu completamente
indipendenti per ogni piastrella. Se potessimo impostare un'impostazione
manuale delle piastrelle (fino a 120) avremmo 120 impostazioni diverse
di "Master", 120 diverse impostazioni di "rosso-verde", 120 impostazioni
diverse di "blu-giallo"!

- Questo porta a una elaborazione multipla di un'unica immagine con
  tutte le impostazioni esistenti.
- È comunque possibile modulare il risultato con l'aiuto delle opzioni
  "Preferenze\> Performance & Quality\> Auto multi-zone smoothing".
  Offre quattro scelte:
  - Nessuno: viene eseguita la lavorazione sopra descritta
  - Basso: si tiene conto di una parte delle altre lavorazioni di
    piastrelle, ma in modo molto basso
  - Alto: come sopra ma più pronunciato
  - Max - media di tutte le piastrelle: questa modalità funziona come
    "Globale automatico", ma invece di utilizzare 9 celle, è il numero
    di piastre che sostituisce il numero delle celle (di conseguenza
    queste possono variare da 12 a 120).
- Tutte le opzioni di "Preferenze" Performance & Quality "sono
  utilizzabili.

##### Anteprima multi-zone

- Identico all'anteprima
- Ma hai la possibilità di valutare con una buona approssimazione il
  risultato di "Multi-zone auto" con l'aiuto delle informazioni fornite
  come supplemento a "Anteprima rumore"
- Sotto le indicazioni "Rumore di anteprima: Medio= xx Alto= yy",
  vengono visualizzate due righe:
  - Il primo fornisce la dimensione delle piastrelle in pixel e la sua
    posizione centrale sull'immagine completa.
  - Il secondo dà la dimensione di anteprima in pixel e la sua posizione
    centrale sull'immagine completa. La dimensione dell'anteprima
    dipende da diversi parametri: zoom, dimensioni delle finestre
    laterali.
  - Cercate di regolare qualunque sia il migliore dei centri e delle
    dimensioni spostando l'anteprima con il mouse e modificando lo zoom.
    Fare attenzione, siamo in elaborazione del rumore, ed è molto raro
    che ci siano forti discontinuità, perciò sono accettabili lacune di
    alcuni pixel o dozzine di pixel.

#### Curva di crominanza

Questa curva consente di mirare più precisamente aree specifiche di
cromaticità.

- Come promemoria, la cromaticità in modalità L\*a\*b\* trasmette
  l'intensità del colore. Una bassa cromaticità trasmette toni grigi,
  un'alta cromaticità trasmetterà colori saturi.
- Questa curva modula l'azione dei cursori "Master", "Red-Green" e
  "Blue-Yellow" moltiplicando i loro valori mediante l'ordinata curva.
- Ad esempio, se il cursore master è impostato su 30 e la curva è a
  mezza altezza, il risultato equivalente sarà di circa 45.
- È utilizzabile in tutti i modi: manuali, globali automatici,
  multi-zone auto e anteprima.
- Può essere utile, ad esempio, (impostazione predefinita) in modalità
  "Automatico globale" per aumentare le aree grigiastre o i grigi che
  avranno un'impostazione spesso troppo debole a causa del valore medio
  delle impostazioni. Queste aree grigie sono quelle in cui il rumore
  visibile diventa spiacevole, al contrario delle zone molto saturate
  dove è ammesso lo stesso livello di rumore (meno visibile).
- Si noti che in alcuni casi è possibile anche utilizzare come
  complemento i cursori che agiscono, il filtro mediano "Chroma only",
  al fine di evitare valori troppo elevati di wavelets (impressioni dei
  colori dettagliati).

### Gamma

Gamma varia la forza di riduzione del rumore in tutta la gamma dei toni.
I valori gamma più bassi consentono che la riduzione del rumore
influenza tutti i toni enfatizzando l'azione sulle ombre, mentre i
valori gamma più alti limitano l'effetto solo a toni più luminosi.

### Mediana

<img src="/images/Rt_nr_median_books.jpg" title="Rt_nr_median_books.jpg"
width="900" alt="Rt_nr_median_books.jpg" /> Utilizza questo filtro per
rimuovere gli artefatti minuscoli e affilati che vanno dalla riduzione
del rumore. Il [median
filter](https://en.wikipedia.org/wiki/Median_filter) sostituisce ogni
pixel con il valore mediano dei pixel vicini. Il gruppo contiguo di
pixel che vengono campionati viene chiamato "finestre". Questa finestra
presenta pixel per pixel sull'intera immagine. Puoi scegliere la
dimensione di questa finestra utilizzando il menu a discesa "Mediano".
Maggiore è la dimensione, più tempo richiede.

Dimensioni finali disponibili:

- 3x3 soft: treats 5 pixels in a 3x3 pixel window.

  
○●○

●●●

○●○

- 3x3: treats 9 pixels in a 3x3 pixel window.

  
●●●

●●●

●●●

- 5x5 soft: treats 13 pixels in a 5x5 pixel window.

  
○○●○○

○●●●○

●●●●●

○●●●○

○○●○○

- 5x5: treats 25 pixels in a 5x5 pixel window.

  
●●●●●

●●●●●

●●●●●

●●●●●

●●●●●

- 7x7: treats 49 pixels in a 7x7 pixel window.

  
●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

●●●●●●●

- 9x9: treats 81 pixels in a 9x9 pixel window.

  
●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

●●●●●●●●●

A volte è possibile ottenere una qualità superiore eseguendo diverse
iterazioni con una piccola dimensione della finestra di una iterazione
con una grande dimensione della finestra.

Quando si utilizzano i metodi "Luminance only" e "Lab", il filtraggio
medio verrà eseguito subito dopo il passaggio wavelet nella pipeline di
riduzione del rumore. Quando si utilizza la modalità "RGB", verrà
eseguita alla fine della tubazione di riduzione del rumore.

![](Rt_nr_median_zoom_books.jpg "Rt_nr_median_zoom_books.jpg") Si può
chiedere che cosa utilizzi il filtraggio mediano non sia l'eliminazione
di pixel che si differenziano fortemente dai loro vicini circostanti.
Uno di questi vantaggi è una riduzione della dimensione del file quando
si salva in formati compressi come JPEG e PNG. Il filtraggio mediano
elimina le variazioni che si perderà comunque se si riduce l'immagine. È
anche probabile che non si vedano queste variazioni se si stampa
l'immagine. La rimozione usando filtri mediani può ridurre la dimensione
del file di ben 40% (testato con la forza di compressione JPEG 92 con
"qualità equilibrata" [chroma
subsampling](https://en.wikipedia.org/wiki/Chroma_subsampling)), perciò
provate se la dimensione del file è un problema.

È inoltre possibile utilizzare il filtro mediano "Chroma only" come
complemento per l'elaborazione di wavelet. In questo modo è possibile
ridurre i valori richiesti per l'elaborazione delle wavelet e evitare
particolari di dissolvenza.

#### Metodo

Voi disponete di cinque metodi a disposizione:

- Luminance only: funziona in modalità L\*a\*b\*, ma riguarda solo il
  canale L \*
- Solo Chroma: funziona in modalitàL\*a\*b\*, ma riguarda solo i canali
  a\* e b\*
- Ponderato L\* (piccolo) + a\*b\* (normale): funziona in modalità L \*
  a\* b\*, ma agisce più debolmente sul canale L \*
- L\*a\*b\*: funziona in modalità L\*a\*b\*, con uguaglianza dell'azione
  sui tre canali L , a\*, b
- RGB: funziona in modalità RGB. In questa modalità la scelta della
  finestra è limitata a 3x3 soft, 3x3 e 5x5.
