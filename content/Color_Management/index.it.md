---
title: Color Management
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

## Profilo di input

### Nessun profilo

Non verrà applicato alcun profilo di colore di input. La matrice di
colore usa "1" lungo la diagonale e "0" ovunque.

- I file Raw mostreranno il colore RGB nativo della fotocamera. Saranno
  solo demosaiced e bilanciati in bianco.
- I file non raw verranno visualizzati senza applicare alcun profilo di
  input embedded, inclusi nessuna correzione gamma, il che significa che
  appariranno brillanti.

Questa caratteristica è generalmente utile solo per scopi didattici e
scientifici. Ad esempio se la fotocamera ha registrato colori al di
fuori delle gamut convenzionali, non utilizzare profili di ingresso
assicura che non si verifichi alcun ritaglio di colore.

### Camera Standard

Cerca e utilizza una matrice di colore dal file DNG, da camconst.json,
codificato in RawTherapee o da
[dcraw](https://en.wikipedia.org/wiki/Dcraw), qualunque cosa trovi
prima, in questo ordine.

Una "matrice di colore" è una matrice di valori costanti 3x3 che si
moltiplica con i colori nativi RGB della telecamera per convertirli in
colori il più naturale possibile. Una matrice di colori funziona meglio
(cioè fornisce colori più precisi) quando il bilanciamento del bianco è
simile a quello per cui è stata calibrata la matrice. La matrice
standard della fotocamera è calibrata per illuminante
[D65](https://en.wikipedia.org/wiki/Illuminant_D65), vale a dire 6500K.
Non preoccuparti se il bilanciamento del bianco è abbastanza lontano da
quello, però, il colore sarà ragionevolmente accurato comunque.

Per applicazioni in cui il colore molto accurato o calibrato
precisamente non è di grande importanza, come la fotografia
paesaggistica, la matrice di colori fornirà buoni colori. Un vantaggio
dell'elaborazione della matrice di colore rispetto alle conversioni DCP
e ICC della tabella di ricerca è che è puramente lineare, cioè un colore
scuro e un colore brillante della stessa tonalità e saturazione sono
tradotti nello stesso modo. Questo lo rende robusto e può essere la
scelta migliore se si esporterà le immagini per l'elaborazione in
un'applicazione HDR o in un'altra applicazione quando è importante una
risposta a colori lineare prevedibile.

### Profilo della macchina fotografica

Utilizza il profilo di input DCP specifico per la fotocamera di
RawTherapee che consente di fornire colori più precisi rispetto alla
matrice standard (e ricade nei profili legacy ICC se non è disponibile
un DCP). Disponibile per alcune telecamere, questi profili vengono
memorizzati nella cartella /dcpprofiles (o di sistema
/iccprofiles/input) e vengono ripristinati automaticamente in base alla
corrispondenza del modello e della marca esatta della fotocamera, come
appare nella sezione info dell'editor nel nome del file , per esempio
"Canon EOS 5D Mark III.dcp".

In altre parole, se è selezionato "*Auto-matching camera profile*",
RawTherapee cercherà di fare quanto segue, in questo ordine:

1.  individuare un profilo DCP in /dcpprofiles
2.  se DCP non è trovato, individuare un profilo ICC in /iccprofiles\*
3.  se non si trovano DCP e ICC, tornare alla matrice di colore standard
    della fotocamera.

Se si desidera contribuire a un profilo della fotocamera, DCP è il
formato preferito.

Alcuni dei profili RawTherapee sono illuminati singolarmente
(Daylight/D50), mentre altri sono illuminati a doppia (Daylight/D50 e
Tungsten/StdA). Alcuni includono una curva di tono, altri non lo fanno.
Si sforzano di ottenere colori accurati (cioè non un "aspetto"
specifico). I colori più accurati verranno realizzati per i
bilanciamenti bianchi vicino agli illuminanti di calibrazione.

I profili della fotocamera funzionano nell'intervallo normale, dal nero
ai bianchi. Se si abilita la ricostruzione delle alteluci, i nuovi dati
vengono aggiunti al di sopra del livello di ritaglio e se lo si
inserisce nello spazio visibile (ad esempio per esposizione negativa),
tale campo non sarà coperto naturalmente dal profilo. Tuttavia,
RawTherapee estenderà linearmente il profilo per coprire anche questa
gamma, i colori avranno la stessa correzione dei colori più brillanti
della stessa tonalità e della saturazione nell'intervallo normale.

### Personalizzato

Specificare un profilo DNG personalizzato (DCP) o ICC immagazzinato nel
computer.

DCP è un formato appositamente progettato per i profili della fotocamera
e RawTherapee dovrebbe supportare il più recente standard DNG (dove è
definito DCP), pertanto è possibile utilizzare tutti quelli forniti
tramite il convertitore DNG di Adobe.

I profili ICC d'altra parte sono più complicati. I profili ICC possono
essere utilizzati per molteplici scopi (stampanti, display ecc.) E
poiché non sono progettati specificamente per la profilazione delle
fotocamere, i fornitori diversi hanno scelto diversi approcci per i loro
profili ICC. In pratica ciò significa che l'immagine di input deve
essere pre-elaborata in un modo specifico per far funzionare il profilo.
Il profilo stesso manca di informazioni su come eseguire questa
pre-elaborazione, il che significa che se si utilizza un profilo di
terze parti RawTherapee non può fare la pre-elaborazione prevista; i
risultati variano.

#### supporto DCP di terze parti

Un profilo DNG della fotocamera, DCP, è il formato preferito della
fotocamera per RawTherapee. Tutti gli elementi della 1.4 DNG sono
supportati, ad eccezione del tag rendering nero (vedi sotto). Un DCP può
essere un profilo di matrice pura, può avere un LUT (tipicamente 2.5D)
per migliorare la precisione colorimetrica e quindi può avere una curva
embedded e una "look table" all'inizio. Può anche aggiungere un'offset
di esposizione. Tutti questi elementi possono essere cambiati tramite le
caselle di controllo. Tuttavia, anche se è possibile, alcuni profili di
terze parti sono stati progettati per produrre il colore previsto con
qualsiasi altra cosa che tutti gli elementi abilitati. Ad esempio, la
curva di tonalità stessa modifica l'aspetto del colore in modo da
disattivare una curva di tonalità incorporata per ottenere un profilo
lineare non è possibile contare sul fatto che il colore sia come
previsto.

Il profilo tipico di terze parti proviene da Adobe Camera Raw/Lightroom
e RawTherapee li supporta. Molti della curva di tonalità di mancanza di
profilo di Adobe, ma nel mondo di Adobe, non significa che non sia
applicata alcuna curva di tono, ma che dovrebbe essere applicata la
curva di default di Adobe. RawTherapee individuerà quindi i profili
Adobe (dalla stringa di copyright) e aggiunge la curva di default a
quelle (che è possibile modificare con la casella di controllo della
curva di tono).

Il convertitore DNG di Adobe può aggiungere un "esposizione baseline" al
file DNG. DCP di Adobe sono progettati per funzionare con l'esposizione
di base e quindi producono un'uscita predefinita che corrisponde alla
stessa luminosità e contrasto dei JPEG propri della fotocamera.
RawTherapee può rispettare questa esposizione di base (NON E
'IMPLEMENTATO), ma questo è naturalmente disponibile solo quando si apre
un file DNG convertito dal convertitore DNG di Adobe. Se si apre invece
un file raw nativo non esiste un'esposizione di base e il DCP di Adobe
può quindi eseguire un rendering troppo luminoso o scuro. È possibile
regolare semplicemente con il cursore di esposizione ovviamente.

Il formato DCP ha anche un tag nero di rendering. Ciò indica se il
convertitore raw dovrebbe eseguire una sottrazione "automatica" nera o
meno. RawTherapee ignora questo tag, è possibile eseguire una
sottrazione manuale manuale con il cursore nero. Poiché molti dei
profili di Adobe indicano la sottrazione automatica nera e Adobe Camera
Raw/Lightroom lo farà, RawTherapee comparerà in questi casi rendere un
po 'più basso contrasto e più ombre più luminose.

#### supporto ICC di terze parti

RawTherapee ha un supporto specifico per i profili ICC forniti in
dotazione con Capture One e Nikon NX2, in modo da funzionare bene. I
profili ICC più vecchi non funzioneranno bene (in genere l'immagine
diventa estremamente scura con i profili ICC non supportati).

Alcuni profili ICC applicano una curva di tono e desaturano le luci
luminose per un aspetto più "filmico". Questi profili potrebbero non
funzionare bene insieme a [Ricostruzione
alteluci](Exposure/it#Highlight_Reconstruction.md). Se vedi un
cambiamento radicale nel contrasto quando applica il tuo profilo ICC, ha
applicato una curva di tonalità e quindi non dovresti utilizzarlo
insieme a [Ricostruzione
alteluci](Exposure/it#Highlight_Reconstruction.md).

A differenza dei profili DCP, l'elaborazione del profilo ICC può causare
ritagli di colori estremamente saturi durante la conversione. In pratica
questo è raramente un problema, ma ancora DCP dovrebbe essere
considerata la scelta primaria se disponibile.

Nota sull'utilizzo dei profili ICC di Capture One: RawTherapee applica
l'ICC prima delle regolazioni dell'esposizione, in quanto l'intenzione è
che i profili della fotocamera siano utilizzati solo per rendere la
fotocamera più precisa, non per applicare un look particolare (si
progetta l'aspetto usando gli strumenti) . I profili ICC di Phase One
contengono tuttavia un aspetto soggettivo, il che significa che
contengono tipicamente "variazioni di tonalità", ad esempio la
saturazione nelle ombre aumenta un po'. Ciò significa che se si dispone
di un file sotto esposto e lo si incrementa di qualche stop, le tonalità
delle ombre sono state applicate sull'immagine scura prima della
regolazione dell'esposizione e saranno quindi in luoghi sbagliati dopo
la correzione di esposizione, cioè non si ha lo stesso aspetto nella
Fase One's Capture One. Pertanto è consigliabile disporre della giusta
esposizione dalla fotocamera quando si utilizzano i profili ICC di
fase 1. È inoltre opportuno applicare un'appropriata curva di pellicola
RGB ad esempio utilizzando l'attrezzo della curva, poiché quei profili
ICC sono stati progettati per essere utilizzati insieme a quello.

Siamo consapevoli che le ICC di LUT dovrebbero essere tipicamente
applicate dopo l'esposizione (proprio come vengono applicati i
Looktables di DCP) e che supporterebbero ad esempio i profili Capture
One meglio. Questo può essere risolto in una versione futura.

### DCP illuminatore

Alcuni dei profili RawTherapee sono illuminati singolarmente
(Daylight/D50), mentre altri sono illuminati a doppia (Daylight/D50 e
Tungsten/StdA). Se viene caricato un profilo dual-illuminant,
l'impostazione "DCP Illuminant" sarà attivata e si può scegliere
l'illuminatore da utilizzare. Lo standard DCP effettivo (parte dello
standard DNG) non fornisce questa scelta, ma invece viene calcolata
un'interpolazione tra i due illuminanti in base al bilanciamento del
bianco scelto (ci sarà solo un'interpolazione se il bilanciamento del
bianco è tra entrambi gli illuminanti , altrimenti viene scelto il più
vicino). Questa modalità "interpolata" è l'impostazione predefinita di
"DCP Illuminant" e per qualsiasi uso normale non è necessario
modificarlo.

Tuttavia, è possibile scegliere di basare il rendering del colore su uno
degli illuminanti specifici. In alcuni casi ciò potrebbe produrre un
colore più piacevole. Può anche essere interessante per scopi
diagnostici per vedere quanto grande (o piccola) differenza c'è nel
rendering dei colori tra gli illuminanti, ma, come detto, per uso
generale questa impostazione dovrebbe essere intatta.

### Utilizza la curva di tono di DCP

Alcuni DCP contengono una curva di tono che può essere utilizzata per
aggiungere contrasto e luminosità per fornire un aspetto filmico. Questo
è utilizzato principalmente per i profili che simulano le impostazioni
del produttore della fotocamera. La casella di controllo della curva di
tonalità sarà disabilitata per i profili che non contengono una curva di
tono.

La modalità di curva utilizzata dalla curva del tono DCP è la stessa
della modalità "[Esposizione \[come
film](Esposizione_[come_film.md)", che consente di riprodurre
l'effetto utilizzando le curve di tono dello strumento Esposizione in
modalità film . Quando viene applicato il contrasto con una curva
cinematografica, l'aspetto dei colori cambia e la saturazione
complessiva è aumentata, ad eccezione dei colori vivaci che invece sono
de-saturati. Alcuni profili che presentano curve incorporati sono
pre-corretti per questa modifica dell'aspetto dei colori e non
forniranno quindi l'aspetto previsto senza la curva applicata. La
maggior parte comunque funzionerà bene senza la curva di tono applicata
in particolare se si aggiunge una curva simile utilizzando le curve
dello strumento Esposizione, ma se si desidera vedere esattamente come
il progettista del progetto ha inteso i colori da visualizzare, è
necessario abilitare la curva di tono.

Mentre il profilo di colore dell'ingresso viene applicato nelle prime
fasi della [pipeline toolchain](toolchain_pipeline), la curva
del tono DCP viene applicata in un secondo momento in un punto dopo lo
strumento Esposizione.

### Utilizza la tabella base di DCP

Questo abilità la tabella DCP "HueSatMap" utilizzata per aggiungere
correzioni non lineari prima dell'applicazione della matrice di base.
Questa è un'impostazione utente avanzata e a meno che non si desideri
solo il risultato della matrice pura dovrebbe essere impostato. È
disattivato se il profilo caricato manca di una tabella HueSatMap.

### Utilizza la tabella di visualizzazione di DCP

Ciò consente l'utilizzo della tabella di ricerca DCP "LookTable" che
intende aggiungere un look soggettivo generalmente insieme a una curva
di tonalità incorporata. Ciò significa che se si disattiva la curva DCP
e il looktable è possibile ottenere un profilo "colorimetrico" neutro,
se il DCP è stato progettato in un modo diverso (se il DCP ha sia una
tabella di visualizzazione che una tabella di base è probabile che è, ma
se ha solo un tavolo di sguardo probabilmente non funzionerà bene con
esso disabilitato). La disattivazione di singoli elementi DCP è
considerata impostazioni utente avanzate, normalmente si lascia
impostata.

### Usare l'offset dell'esposizione DCP

Il DCP può indicare un'offset di esposizione corrispondente ad un offset
del cursore di esposizione. Lo scopo di questo è di solito per fare in
modo che la luminosità dell'immagine corrisponda alla luminosità dei
JPEG propri della fotocamera, che può essere utile se si sta riprendendo
con l'esposizione automatica. Attualmente questo offset viene applicato
"in modo non visibile" in modo da non vederlo sul cursore di
esposizione.

Si noti che se si utilizzano i profili proprietari di Adobe, si prevede
che anche il tag "esposizione di base" del DNG viene applicato (l'offset
del profilo viene aggiunto in cima). Attualmente non esiste alcun
supporto per il tag DNG, pertanto è necessario individuarlo da solo
(usando exiftool per esempio) e impostare l'offset utilizzando il
cursore di esposizione se si desidera ottenere la stessa luminosità come
in Adobe Camera Raw.

### Salva l'immagine di riferimento per la profiling

Facendo clic su questo pulsante viene salvata un'immagine TIFF lineare
prima di applicare il profilo di input. Questo file può essere
utilizzato per la creazione di un nuovo profilo ICC della fotocamera. Ci
sono diversi software commerciali per fare profili ICC, ma è anche
possibile utilizzare l'Argyll gratuito e open-source. Per i profili DNG
esiste DCamProf come un'alternativa open source.

Sarà applicato il taglio, la ridimensionamento e la trasformazione
(ruotare) in modo da poterli utilizzare per rendere l'output più
gestibile dal software di ricezione. Ad esempio Argyll è molto esigente
e non vuole altro che il bersaglio di prova visibile nell'immagine.

È anche possibile scegliere se si desidera esportare con bilanciamento
del bianco applicato o no. Per i profili ICC è necessario esportare con
il bilanciamento del bianco applicato, ma se si intende creare un DNG
Profile ColorMatrix (o una matrice di colore in stile DCRAW) è
necessario esportare senza.

## Profilo di lavoro

Il profilo di lavoro predefinito è ProPhoto e non deve essere modificato
per un uso normale.

Il profilo di lavoro specifica lo spazio di lavoro che è lo spazio
colore utilizzato per i calcoli interni, ad esempio per calcolare la
saturazione, la luminosità/il contrasto RGB e le regolazioni della curva
del tono, la crominanza, ecc.

Quando RawTherapee si basava sulla matematica intera, era saggio non
utilizzare uno spazio di lavoro più ampio di quello assolutamente
necessario per ottenere la massima precisione nei calcoli. Tuttavia, al
giorno d'oggi RawTherapee è a virgola mobile e dalla versione 4.0.12 il
profilo di lavoro predefinito è ProPhoto (gamut molto grande) e non c'è
motivo di cambiare questo per uso normale.

Alcuni tipi di curva di tonalità cambiano i risultati abbastanza
drasticamente per i colori altamente saturi a seconda del profilo di
lavoro. Se hai difficoltà adattare i colori all'interno della gamma di
output, puoi sperimentare la modifica.

Si noti che il profilo di lavoro specificerà solo i primari rossi, verdi
e blu, la gamma non cambia in quanto la pipeline di trasformazione
RawTherapee è a virgola mobile senza una codifica gamma (ovvero gamma =
1.0). Alcuni strumenti (come curve e istogrammi) continueranno ad essere
visualizzati con una gamma (di solito gamma sRGB) che è codificato per
lo strumento e rimane lo stesso indipendentemente dal profilo di lavoro.

## Profilo di uscita

Specificare il profilo colore di output; l'immagine salvata verrà
trasformata in questo spazio colore e il profilo verrà incorporato nei
metadati. Gli effetti del profilo di uscita sull'immagine non possono
essere visualizzati nell'anteprima.

RawTherapee consente di specificare i profili della classe di
periferiche "input" (ad es. Profilo della fotocamera), "display" e
"output" (ad es. Stampante) con uno spazio colore RGB, in quanto
RawTherapee salva solo immagini RGB. I profili elencati in questa
combinazione sono quelli che vengono forniti in dotazione con
RawTherapee e quelli situati nella cartella impostata in
Preferenze\>[Gestione
Colore](Preferences/it#Color_Management_Tab.md).

La funzionalità soft-proofing è dedicata alla simulazione del rendering
della stampante. Consente di visualizzare in anteprima quale sarà la tua
immagine quando viene stampata, supponendo che utilizzi un profilo
stampante che simula correttamente la stampante e la combinazione di
carta. Per ottenere la migliore qualità di stampa, dopo aver eseguito
una correzione della foto utilizzando l'impermeabilizzazione, è
necessario selezionare il profilo della stampante come profilo di output
e salvare l'immagine utilizzando. Ciò assicura che l'immagine sia
codificata usando lo spazio colore della stampante direttamente dalla
rappresentazione interna di RawTherapee di un punto a virgola mobile di
alta qualità, anziché essere salvata ad un'immagine a 8 bit in sRGB ad
esempio e quindi successivamente convertita nel profilo della stampante
sarebbe abbastanza perdente.

Gli indicatori principali dell'istogramma, del navigatore e del ritaglio
utilizzeranno il profilo di lavoro o di uscita, a seconda
dell'impostazione in Preference\>
[Generale](preferences/it#general_tab).

RawTherapee viene fornito con una serie di profili di produzione di alta
qualità su misura:

RT_sRGB  
Similar to sRGB

Gamma close to sRGB: g=2.40, slope=12.92

RT_sRGB_gBT709  
Similar to sRGB

Gamma BT709: g=2.22, slope=4.5

RT_sRGB_g10  
Similar to sRGB

Linear gamma g=1.0, slope=0

RT_Medium_gsRGB  
Similar to AdobeRGB1998

Gamma close to sRGB: g=2.40, slope=12.92

RT_Large_gsRGB  
Similar to ProPhoto

Gamma close to sRGB g=2.40, slope=12.92 (close to "Melissa" used by
Lightroom)

RT_Large_gBT709  
Similar to ProPhoto

Gamma BT709: g=2.22, slop=4.5

RT_Large_g10  
Similar to ProPhoto

Linear gamma g=1.0, slope=0

Rec2020  
Wide gamut, larger than AdobeRGB but smaller than ProPhoto

Gamma BT709: g=2.22, slope=4.5

Il profilo di output raccomandato quando si sta salvando a un formato a
8 bit e / o pubblicato sul web è RT_sRGB. Se non è selezionato nessun
profilo, nessuno verrà incorporato, il che significa che è "implicito"
sRGB, anche se è più sicuro incorporare RT_sRGB in termini di
ottimizzazione dell'immagine nelle varie applicazioni.

RT_sRGB è una versione *'di qualità superiore'* del profilo sRGB
standard, che sorprende che è incoerente tra le implementazioni. RT_sRGB
è stato realizzato su RawTherapee da Jacques Desmis e ha 4096 punti LUT,
a differenza dei profili sRGB di 1024 punti di qualità inferiore. Le
applicazioni che non sono gestite a colori e non sfrutteranno RT_sRGB
ritorneranno su sRGB.

I profili di output a largo campo come RT_Large_gsRGB vengono
generalmente utilizzati se si esporta in un formato a profondità a 16
bit o superiore per ulteriori modifiche in un'altra applicazione. Se
invierai l'immagine per la stampa, si consiglia anche un profilo di
output di ampia gamma, in quanto alcune stampanti possono avere gamut di
larghezza (almeno in alcuni colori).

È necessario disporre di un monitor di larghezza di gamma se si desidera
lavorare con profili di larghezza di gamma, altrimenti si sta volando al
buio.
