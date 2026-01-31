---
title: Color Management addon
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

## Concetti di colorimetria

Questo documento mira a diversi obiettivi riguardanti la colorimetria:

1. Riepilogare la procedura di elaborazione dei file raw da un punto di
vista colorimetrico e evidenziare i punti chiave e le lacune

2. Spiegare i principali passi dei passaggi per consentire all'utente
di poter pesare quello che è in gioco

3. Spiegare l'uso di alcune funzioni che potrebbero sembrare oscure per
i nuovi arrivati.

Nota: questo documento riguarda solo RawTherapee 4 e computa con numeri
reali, e non RawTherapee 3. Inoltre non tiene conto di possibili
malfunzionamenti (bug) ancora non risolti!

### Attenzione

- Questo documento non mira a trattare tutti gli aspetti della
  colorimetria che non sono specifici a RawTherapee, come ad esempio:
  - la stampa,
  - calibrazione del monitor.
- Tuttavia, si consiglia di calibrare gli schermi con uno dei tanti
  prodotti presenti sul mercato. Il profilo creato è solo per il monitor
  e non deve mai essere utilizzato in alcun modo come profilo di
  ingresso o profilo di output.
- In Windows, MacOS o Linux, un software come DispalGUI di Argyll,
  combinato con una sonda di qualità, anche vecchia (ad es. io possiedo
  la sonda DTP94 per la quale non esistono più \[?\] i driver per
  Windows) da ottimi risultati; il tempo di lavorazione è abbastanza
  lungo (circa un'ora).
- RawTherapee rileva automaticamente il profilo di sistema, tuttavia è
  possibile accedere alla schermata icc nome file in
  «Preferenze/Gestione colori/Profilo monitor»
- Il lettore avrà preferibilmente conoscenze minime sulla gestione del
  colore: matrici, RGB, XYZ, Lab, spazio colore, primari e profilo
  colorimetrico ... i lettori interessati possono leggere il sito web
  di B. Lindbloom [](http://www.brucelindbloom.com)
- È possibile configurare la visualizzazione dell'istogramma come pure
  il browser: per impostazione predefinita, i valori visualizzati
  tengono conto del "profilo di uscita". È possibile modificare questo
  comportamento in "Preferenze" e controllare "Utilizza profilo di
  lavoro per istogramma principale e navigatore"
- Naturalmente, questo documento è tutt'altro che esaustivo, il soggetto
  è complesso.

### elaborazione raw iniziale prima della conversione RGB

#### Leggere il file raw e utilizzare i suoi dati

- Il primo passo che viene eseguito essenzialmente su Dcraw (grazie a
  D.Coffin) consiste nella lettura di tutti i tipi di file raw, con la
  loro codifica proprietaria: profondità di dati, 12 o 14 bit,
  saturazione del sensore, bilanciamento del bianco .. e naturalmente
  dati rggb o rgbg;
- il bilanciamento del bianco predefinito è quello scelto dall'utente
  sulla sua macchina fotografica per le riprese!
- l'interpolazione (AMaZE, AHD, DCB ...) avviene dopo la modifica dei
  dati rgb (l'immagine può essere valutata visivamente su uno schermo):
  l'interpolazione non deve modificare la colorimetria (o molto poco) e
  questo avviene per tutte le interpolazioni esistenti in RawTherapee
  (deltaE94 a causa dell'interpolazione è approssimativamente 1, quindi
  trascurabile), d'altra parte, ai limiti (oltre le alteluci...) possono
  apparire artefatti per alcuni di essi.
- per dare loro un aspetto più realistico, questi dati rgb vengono
  modificati da una matrice di colori (da Adobe) o da un profilo DCP (da
  Adobe o RawTherapee) o da un profilo di input ICC, sui profili ICC
  torneremo in seguito per la loro elaborazione e utilizzo;
- I valori di rgb sono privi di spazio di colore - questo punto è
  essenziale (la scelta sRGB o AdobeRGB per esempio suggerita dalla
  fotocamera è per i file JPG)
- la gestione del colore viene elaborata: a) parzialmente con LCMS2, che
  ha fatto grandi miglioramenti e ora può lavorare usando il punto a
  virgola mobile evitando i clip di colori; b) computando direttamente
  (conversione di XYZ, Lab, RGB, gamma, ecc.)

#### Profili di input ICC: elaborazione, utilizzo, vuoti

- questi profili si applicano sia come profili esterni dopo la
  conversione RGB (come Capture NX2) ai dati rgb, in modo teoricamente
  senza [intento di
  rendering](https://en.wikipedia.org/wiki/Color_management#Rendering_intent)
  (relativa, assoluta, percezione , saturazione). Modificano i valori di
  Lab, ma non i rgb - gli istogrammi restano uguali, o come profili
  interni come RawTherapee (teoricamente senza [intento di
  rendering](https://en.wikipedia.org/wiki/Color_management#Rendering_intent));
- cercano di ridurre il divario tra i valori originali (quelli sensori)
  e un valore obiettivo, teoricamente perfetto;
- sono teoricamente corrispondenti: un dato illuminante (D50, C, ombra,
  ...), condizioni di ripresa del modello di prova, ripresa con
  obiettivi ...
- tuttavia, possiamo senza alcun problema, usarli finché rimani
  approssimativamente nello stesso ambiente, ad esempio. flash invece
  della luce del giorno, D55 invece di D50 ...
- elaborazione:

<figure>
<img src="/images/Mire468.jpg" title="Mire468.jpg" />
<figcaption>Mire468.jpg</figcaption>
</figure>

1.  scatta una foto di prova in condizioni ideali che corrispondano
    all'uso previsto (fuori, studio, ...);
2.  maggiore è la gamma di pattern di prova, migliore è il risultato, ad
    esempio il ColorChecker24 è vicino a sRGB, anche se fornisce buoni
    risultati nei casi abituali, come potrebbe valutare in modo efficace
    i colori reali che sono fuori dalla gamma sRGB (fiori, colori
    artificiali ...)?
3.  più alto è il numero di celle di test pattern, meglio il risultato è
    (migliore guida del profilo)
4.  Il modello di prova dei colori 468, progettato con un collega
    "Rouli", è oltre WideGamut per alcuni colori e possiede valori di
    luminanza bassi.
5.  per tua informazione, i risultati deltaE94 della mia D200, ottenuti
    con i 468 colori (NEF) su cui applico il profilo di input a
    matrice: a) matrice di colore originale (Dcraw) - (o risultati
    ottenuti con Camera Raw 6.6 e DCP): media = 4,37, deviazione
    standard = 1,82, massimo = 13,75; b) Profilo ICC, memorizzato nella
    cartella "Iccprofile" elaborato dal ColorChecker24 vicino a sRGB:
    media == 3.66, deviazione standard = 2.08, massima = 11.28; c)
    profilo ICC, elaborato da me dal modello di prova a colori con gamut
    molto ampio, vicino a WideGamutRGB: media == 2.05, deviazione
    standard = 1.44, massima = 8.8; d) naturalmente, nella maggior parte
    dei casi, il profilo creato con un ColorChecker24 (ICC o DCP) sarà
    sufficiente!
6.  scatta una foto di prova a circa 12 ore alla luce solare diretta
    (a), o in un tempo nuvoloso (b), nell'ombra (c) o con la luce del
    tungsteno (d) o con una luce dello studio di Solux (e) che abbia uno
    spettro molto vicino alla luce del giorno, oppure (f) un'altra luce
    corrispondente alle tue esigenze:
    1.  impostare la fotocamera in modalità manuale (esposizione ...);
    2.  impostare il bilanciamento del bianco su a) 5000K (o simile alla
        "luce del sole"); b) 6000K; c) 8000K; d) tungsteno 2850K; e) Sun
        4700K; f) ...;
    3.  assicurare che non ci sia riflesso;
    4.  scattare più foto ogni 1/3 EV;
    5.  assicura la parità di esposizione più perfetta tra il centro di
        prova e quattro lati.
7.  salvare i file raw in una cartella chiamata RawTherapee
8.  apri il raw con il profilo "neutro" pp3 e scegli "Prophoto" come
    "profilo di lavoro", in "Profilo di input", scegli "No profile"
9.  valutare l'esposizione da una delle celle grigie del modello di
    prova che la luminanza si trova tra L = 40 e L = 60 e studiare la
    differenza di esposizione tra i lati oscuri del test; scegli lo
    scatto con il miglior compromesso; fai nuovamente uno scatto se
    necessario.
10. impostare l'esposizione con "punto raw bianco-nero" - "punto bianco:
    corr.factor lineare" assicurando che "il punto bianco HL mantenendo
    corr (EV)" sia impostato su zero, in modo che il valore L del grigio
    la cella di riferimento è il più vicino possibile del riferimento.
11. aggiustare il bilanciamento del bianco con SpotWB, scegliendo una
    cella grigia (20 \<L \<80) di cui i valori "a" e "b" sono più vicini
    a zero (per questa operazione i valori "a" e "b" devono essere
    inferiore a 0,5, altrimenti, se la cella ha valori "a" e "b" vicino
    a 1, eseguire il tweak con i cursori "temperatura" e "tonalità"
    (vedi sotto le note sul bilanciamento del bianco) in modo da
    arrivare ai valori Lab delle celle di riferimento.
12. quindi fare clic su "Salva l'immagine di riferimento per la
    creazione di un profilo"
13. usa il tuo "profiler" che userà, secondo il produttore, i valori
    spettrali oi valori Lab o XYZ: genera un profilo di riproduzione per
    l'illuminatore corrispondente alle riprese (D50, D65, Solux ecc.).
14. naturalmente, alcuni "profilatori" (Profilemaker5, ecc.) consentono
    di elaborare profili che non sono profili «riproduzione» che
    riducono al minimo il deltaE94, ma profili che daranno un rendering
    specifico (ritratto, paesaggio, ecc.) agendo sulla curva di
    contrasto e sulla cromatica differenziata tra toni pastelli e
    saturi. Questi profili funzionano, ma dal mio punto di vista, sono
    fuori dalla mentalità di RawTherapee introducendo dei processi che
    tonificano e contrastano le lacune che non possono più essere
    corretti dai vari algoritmi. Tuttavia, questa scelta è possibile.

#### bilanciamento del bianco

##### Divario del bilanciamento del bianco

- Il bilanciamento del bianco è veramente operativo solo con l'utilizzo
  di "SpotWB" su un grigio perfetto (valori "a" e "b" impostati a zero),
  ma è quasi impossibile mettere un grafico grigio su ogni scatto
  (altrimenti per farlo come Alfred Hitchcock), se vuoi modificare
  l'equilibrio bianco della fotocamera, devi generalmente usare i
  cursori "Temperature" e "Tint";
- Ma i cursori hanno una gamma da 1500K a 25000K e la base di calcolo
  utilizzata corrisponde all'illuminazione D (Daylight) non è valida
  sotto 4000K (l'elaborazione è solo un'estrapolazione)

Inoltre i dati diventano falsi se l'illuminante è diverso dalla luce del
giorno (D), ad esempio l'illuminante "Blackbody" o "Fluorescente"

- Allora, mostrate cautela, grande cautela, quando sei fuori
  dall'illuminazione D (luce del giorno) e per temperature al di sotto
  di 4000K

<figure>
<img src="/images/illum1.jpg" title="illum1.jpg" />
<figcaption>illum1.jpg</figcaption>
</figure>

##### Principi

Scatto: Durante la ripresa, sono disponibili due opzioni fondamentali
per l'utente: a) Lavorare in modalità raw, in questo caso gli errori
sono autorizzati e sono possibili ritocchi con un software di
elaborazione raw, ad esempio RawTherapee; b) lavorare in modalità JPEG,
in questo caso se la scelta del bilanciamento del bianco sulla
fotocamera è diversa da quella reale, il ritocco è più difficile. Dare
maggiore importanza allo studio della modalità raw.

Tuttavia, una fotocamera possiede (essenziale per JPEG, utile per i raw)
diverse impostazioni del bilanciamento del bianco. Naturalmente queste
funzionalità variano da un modello all'altro, ma spesso troviamo:

- Una modalità "auto": la telecamera elettronica decide quale valore sia
  giusto da algoritmi fatti in casa. Questa modalità generalmente
  funziona abbastanza bene, tranne quando vi sono forti colori
  dominanti.
- Una modalità "manuale" in cui l'utente, per alcune marche, inserisce
  un valore di temperatura, ad es. 7000K. Questa scelta è fatta da un
  utente preparato, sulla base della sua esperienza.
- Una modalità "pre-impostata" dove l'utente può scegliere tra diverse
  situazioni predeterminate in "fabbrica": "sole", "ombra", "nuvoloso",
  "flash", "incandescente", "fluorescente" ...
- Nota: ogni marchio e modello hanno le proprie specificità, ad es. per
  la modalità fluorescente: a) Canon equipaggia le sue telecamere con
  una sola modalità; b) Fuji dà 3; c) Pentax dà 3; d) Nikon dà fino a 7
  (D3S, D300, ...); e) ecc.
- Nota inoltre: il valore "flash" differisce da un marchio all'altro, ad
  es. per: a) Nikon D300, l'illuminatore flash corrisponde a circa
  6400K; b) Leica R9, l'illuminatore flash corrisponde
  approssimativamente a 5500K; c) Sony A900, l'illuminazione flash
  corrisponde approssimativamente "ombra", cioè circa 7000K ...
- Naturalmente nella maggior parte dei casi la scelta del pre-set è
  abbastanza evidente, ma in altri casi l'utente non saprà cosa
  scegliere ... Infatti, durante una mostra, una visita al museo ecc.
  qual è l'illuminazione in uso?
- Tutte queste impostazioni agiscono sui moltiplicatori dei canali;
- Alla fine, durante una elaborazione raw, questa scelta verrà
  visualizzata in RawTherapee come "Camera".

##### Processing raw

RawTherapee consente 5 possibilità:

- «Macchina fotografica»: il software utilizza, se esistente, i dati
  EXIF di ripresa
- "Auto": il software valuta il bilanciamento del bianco ai dati "medi"
  su una base teorica neutra grigia;
- "Impostazioni preimpostate": come la sfumatura, la luce diurna,
  fluorescente, ecc.
- "Custom": l'utente può scegliere Temperature e Tint (vedere la sezione
  [Bilanciamento del bianco](#white_balance_gaps))
- «Spot WB»: l'utente seleziona un'area grigio neutrale come
  riferimento. Ciò significa deve essere presente una tavoletta grigio
  medio durante la ripresa.

##### Oggetto colorato - illuminante - osservatore

Semplificando, la colorimetria può essere sintetizzata in tre tipi di
dati:

- Oggetto colorato: caratterizzato dai suoi pigmenti (rosso, blu, ...)
  qualunque sia la sorgente luminosa. Può essere valutato con uno
  spettrometro, che darà una rappresentazione unica di esso
- Fonte Illuminante o Illuminazione: questi dati caratterizzano la
  natura della fonte di illuminazione (sole a mezzogiorno, ombra, flash,
  tungsteno, fluorescenti ...). È valutato da due dati: la sua
  distribuzione spettrale di potenza e la relativa temperatura
  correlata; attenzione! due fonti di illuminazione che hanno la stessa
  temperatura non sono identiche perché i loro dati spettrali sono
  diversi.
- Osservatore: eseguire il seguente test, osservare il colore di una
  parete dipinta, quindi quella del campione che è stato utilizzato per
  fare la scelta, si noterà che la sensazione di colore è diversa. CIE
  (Commissione Internazionale dell'Eclairage) definisce due
  "osservatori", 2 ° e 10 °, caratterizzati dall'angolo sotto il quale
  viene osservato il colore.

Per calcolare i valori osservati da un oggetto colorato, sotto
l'illuminatore X, è necessario tener conto nel calcolo dei dati
spettrali dell'oggetto, dell'illuminazione e dell'osservatore. Questi
valori XYZ sono specifici alla temperatura illuminante (ad esempio
6500K); a livello di software (Photoshop, RawTherapee ...) lo standard è
D50. Quindi, è necessario procedere ad un adattamento cromatico dai
valori XYZ (illuminante) all'XYZ (D50). Per questo, diversi metodi
esistono dal meno al più efficiente: Von Kries, Bradford, CIECAM02.

##### L'illuminatore diurna

Questo illuminante è stato oggetto di molti studi di Judd, MacAdam e
Wyszecki, da diverse centinaia di esempi. In breve, l'illuminatore "D" è
la somma di tre parti: S (lamda) = S0 (lamda) + M1 \* S1 (lamda) + M2 \*
S2 (lamda)

1.  una parte "fix", quindi questa è la media di tutti gli esempi
    esaminati;
2.  una prima parte "variabile", S1 che corrisponde alle variazioni "blu
    / giallo" dovute alla presenza o meno di nuvole o alla posizione e
    all'intensità del sole diretto;
3.  una seconda parte "variabile", S2 che corrisponde alle variazioni
    "rosa / verde" dovute alla presenza di umidità sotto forma di vapore
    o nebbia ...;
4.  in termini pratici, che possono essere scritti in una formula
    "semplice" che determina due valori x_D e y_D su una temperatura e
    una base illuminante

- x_D = 0.244063 + 0.0991 \* 103 / T + 2.9678 \* 106 / T2 -4.6070 \* 109
  / T3 per 4000K \<T \<7000K
- x_D = 0.237040 + 0.24748 \* 103 / T + 1.9018 \* 106 / T2 -2.0064 \*
  109 / T3 per 7000K \<T \<25000K
- y_D = -3,0 \* x_D2 + 2,87 \* x_D-0,275
- queste formule sono usate per calcolare i parametri M1 (x_D, y_D) e M2
  (x_D, y_D) di S (lamda) = S0 (lamda) + M1 \* S1 (lamda) + M2 \* S2
  (lamda) il caso finora in RawTherapee. In precedenza, in RawTherapee,
  i valori xD e yD sono stati utilizzati direttamente per calcolare i
  moltiplicatori dei canali, ora, questi valori vengono utilizzati per
  determinare i valori spettrali illuminanti alla temperatura T. Solo
  dopo vengono calcolati i secondi valori che consentono di determinare
  i moltiplicatori.

Due cose possono essere immediatamente notate:

- non esiste alcun riferimento "Daylight" sotto 4000K, la formula
  precedente utilizzata in RawTherapee (da 1200K a 4000K) è stata
  "inventata" per Ufraw;
- nulla impedisce di modificare RawTherapee per passare il valore
  massimo da 12000K a 25000K (fatto dal 2013)

##### "Blackbody" illuminante e "A: tungsteno"

L'illuminante A di CIE viene utilizzato per rappresentare la luce tipica
di un filamento domestico a bulbo di tungsteno. La sua relativa
distribuzione di potenza spettrale è quella di un radiatore Planck a una
temperatura approssimativa di 2856K. L'illuminante A di CIE può essere
utilizzato in qualsiasi applicazione di colorimetria che preveda l'uso
di una luce ad incandescenza, a meno che non ci siano ragioni specifiche
per utilizzare un altro illuminante.

L'illuminante "Blackbody" può essere caculated con la formula Planck che
è la generalizzazione dell'illuminante su una base T:

- S(lamda)= c1 \* pow(wavelength, -5.0)) / (exp(c2 / (wavelength \*
  blackbody_Temp)) – 1.0);

where the 2 values c1 and c2 match to: a) c1=2\*Pi\*h\*c2 h=Planck
constant c=light velocity ; b) c2=h\*c/k k=Boltzmann constant

Questo illuminante si unisce correttamente a circa 4000K con
l'illuminatore "Daylight" con scarti minimi. Ho quindi scelto per
RawTherapee di utilizzare l'illuminante "Blackbody" sotto 4000K e fino a
1500K (sembra che "ACR" ha fatto la stessa scelta).

##### Gli illuminanti fluorescenti

La standardizzazione ha previsto 12 illuminanti del suo tipo,
corrispondenti ai tubi di illuminazione venduti nei negozi:

- F1: Luce del giorno fluorescente - 6430K
- F2: Freddo fluorescente bianco - 4230K
- F3: Bianco fluorescente - 3450K
- F4: Bianco fluorescente caldo - 2940K
- F5: luce fluorescente - 6350K
- F6: Fluorescente luminoso bianco - 4150K
- F7: simulatore D65 - 6500K
- F8: simulatore D50 - 5000K
- F9: Bianco freddo deluxe - 4150K
- F10: Philips T85 - 5000K
- F11: Philips T84 - 4000K
- F12: Philips T83 - 3000K

Questi illuminanti (vedi [Bilanciamento del
bianco](#White_balance_gaps/it.md)) hanno una distribuzione
spettrale di potenza molto diversa tra loro e tra gli illuminanti "luce
del giorno" e "nero". Così non è consigliato sostituire - quando
un'illuminazione è fluorescente - l'illuminante in questione (ad esempio
F11 4000K) da un equivalente "Daylight 4000K".

<figure>
<img src="/images/Comp4000.jpg" title="Comp4000.jpg" />
<figcaption>Comp4000.jpg</figcaption>
</figure>

In realtà, il bilanciamento del bianco calcola sulla base dei dati
spettrali, due coefficienti xD, yD che modificano i moltiplicatori dei
canali: questo calcolo funge da calcolo integrale medio. Infatti, il
bilanciamento del bianco "medio" sarà esatto, ma i picchi o le lacune
dei dati spettrali, rispetto ad un ideale teorico (nero o luce del
giorno), porteranno a livello locale, per alcuni colori, delle sfumature
più o meno importanti.

Esiste un concetto denominato "CRI = Color Rendering Index" che traduce
la qualità dell'origine di illuminazione. Questo "CRI" è un numero
uguale a 100 per una fonte perfetta. Riteniamo che i valori oltre i 90
forniscano buoni risultati. per esempio.:

- Fluo F4 "bianco caldo": CRI = 51
- Clear Mercury Vapor: CRI = 17
- diversi LED con "CRI" tra 50 e 96
- Solux 4700: CRI = 92
- eccetera.

Questo concetto è incorporato (non utilizzato ancora) in RawTherapee con
le seguenti scelte:

- 20 colori di riferimento, 8 "standard" dalla Colorchecker24, 4
  tonalità della pelle, 4 grays (bianco-nero), 3 blues
- utilizzo di CIECAM02 per l'adattamento cromatico
- utilizzo di CIE Lab per calcolo deltaE

Per correggerlo (parzialmente) è sufficiente creare un [input
profile](#ICC_input_profiles_:_elaboration,_use,_gaps.md) con
l'origine di illuminazione desiderata e i dati spettrali corrispondenti.

##### Altri illuminanti

Altri illuminanti esistono, derivano dall'illuminante A e vicino alla
"luce del giorno"

- B e C che non ho incorporato in RawTherapee, ma è possibile farlo
- un illuminatore con uguale energia: "E"
- I lampadari dello studio (film, illuminazione scenica, musei, studio
  fotografico, ecc.) Denominati HMI, GTI, Solux 4700K, Giudice III,
  Solix4100K, Solux3500K ecc., Sono incorporati in RawTherapee.
- L'illuminante del LED, queste lampade spesso hanno grandi lacune nel
  blues. Alcuni di loro hanno caratteristiche molto soddisfacenti
- Gli illuminanti flash "proprietari" (Canon, Nikon, Pentax ...) e lampi
  da studio illuminanti, generalmente molto vicini alla luce del giorno,
  ma ognuno a temperature diverse. Ho fatto diversi raggruppamenti a
  5500K, 6000K e 6500K, circa i flash di studio, dovrebbe essere utile
  avere le loro caratteristiche: a) teoricamente dovrebbe essere utile
  avere i dati spettrali per ogni flash (non li ho), inoltre, questi
  dati variano in base al potere del flash ...; b) quindi ho preferito
  usare l'equivalente "luce del giorno".

Come si può vedere, la situazione non è semplice e pone molti problemi
al software di elaborazione raw, tra cui RawTherapee.

##### Diagrammi Illuminanti e Indice di Rendering Colore (CRI)

<File:I_llumD50.jpg%7CIlluminant> D50 (CRI=100 Sigma=0)
<File:I_llumA.jpg%7CIlluminant> A 2856K (CRI=100 Sigma=0)
<File:I_llumD150.jpg%7CIlluminant> D150 -15000K (CRI=100 Sigma=0)
<File:I_llumF1.jpg%7CIlluminant> Fluo F1 "daylight" 6430K (CRI=77
Sigma=10) <File:I_llumF2.jpg%7CIlluminant> Fluo F2 "coolwite"4230K
(CRI=64 Sigma=12) <File:I_llumF3.jpg%7CIlluminant> Fluo F3 "white" 3450K
(CRI=60 Sigma=12) <File:I_llumF4.jpg%7CIlluminant> Fluo F4 "warm white"
2940K (CRI=54 Sigma=11) <File:I_llumF5.jpg%7CIlluminant> Fluo F5
"daylight" 6350K (CRI=74 Sigma=12)

<File:I_llumF6.jpg%7CIlluminant> Fluo F6 "Lite white" 4150K (CRI=61
Sigma=13) <File:I_llumF7.jpg%7CIlluminant> Fluo F7 "D65 simulator" 6500K
(CRI=90 Sigma=2) <File:I_llumF8.jpg%7CIlluminant> Fluo F8 "D50 sylvania
F40" 5000K (CRI=94 Sigma=1.4) <File:I_llumF9.jpg%7CIlluminant> Fluo F9
"Cool white delux" 4150K - 4330K (CRI=89 Sigma=2)
<File:I_llumF10.jpg%7CIlluminant> Fluo F10 "Philips TL85" 5000K (CRI=72
Sigma=11) <File:I_llumF11.jpg%7CIlluminant> Fluo F11 "Philips TL84"
4150K - 4000K (CRI=77 Sigma=9) <File:I_llumF12.jpg%7CIlluminant> Fluo
F12 "Philips TL853" 3000K (CRI=72 Sigma=8)
<File:I_llumHMI.jpg%7CIlluminant> Lamp HMI 4800K (CRI=97 Sigma=1)

<File:I_llumCTI.jpg%7CIlluminant> Lamp GTI 5000K (CRI=90 Sigma=2)
<File:I_llumJudge.jpg%7CIlluminant> Lamp Judge III 5000K (CRI=92
Sigma=2) <File:I_llumSolux3500.jpg%7CIlluminant> Lamp Solux 3500K
(CRI=95 Sigma=2) <File:I_llumSolux4100.jpg%7CIlluminant> Lamp Solux
4100K (CRI=92 Sigma=2) <File:I_llumSolux4700.jpg%7CIlluminant> Lamp
SoluxNG 4700K - 4480K (CRI=97 Sigma=1)
<File:I_llumLED-LSI-lum2040.jpg%7CIlluminant> Lamp LED LSI Lumelex
2040 - 3000K(CRI=90 Sigma=2) <File:I_llumLED_CRSSP12.jpg%7CIlluminant>
Lamp LED CRS SP12 WWMR16 - 3050K(CRI=94 Sigma=3)

##### Algoritmo

Utilizzo l'algoritmo di base "Daylight": a) calcolo dei valori x_D e y_D
che vengono dati come parametri a M1 e M2 (lamda) = S0 (lamda) + M1 \*
S1 (lamda) + M2 \* S2 (lamda ) da cui differenziamo Xi, Yi, Zi per il
calcolo della matrice \[XiYiZi\] = \[observ2 ° xyz\] \[S (lambda)\],
quindi calcoleremo le modifiche dei modificatori dei canali mediante un
semplice calcolo della matrice \[mulrgb\] = \[sRGBd65_xyz\] XiYiZi\]
(lebarhon: no b)!)

- Ho usato opere di John Walker (dominio pubblico) e B.Lindbloom -
  aumentando l'accuratezza e la gamma spettrale - principalmente la
  funzione "Spectrum_to_xyz", conosciuta come "CIE_colour_match" che
  converte i dati spettrali (350 - 830nm) di un colore o un illuminatore
  in valori xBar, yBar, zBar (tramite i dati Observer 2 °). Ottieni i
  valori di output x e y.

Per quanto riguarda il nero, uso la formula Planck: l'aspetto tra le due
formule è molto buono con una leggera distanza tra i valori xD e yD a
4000K (che possiamo fare con l'istogramma tra 3995K e 40005K): a) 4000K:
xD = 0.382 yD = 0.383 (per le tue informazioni per 4500K: xD = 0.362 yD
= 0.370, per 7000K xD = 0.30 yD = 0.32, per 25000K xD = 0.25 yD = 0.25);
b) corpo nero 4000K: xD = 0,381 yD = 0,377;

Per gli altri illuminanti, le opere che ho eseguito in precedenza sulla
calibrazione (modello di prova 468 colori) mi hanno portato a cercare (e
scoprire) i dati spettrali illuminanti che ho selezionato (tungsteno,
fluorescenti, HMI, GTI, Solux ecc.)

=== rgb ==\> Conversione RGB - Spazio di lavoro "Profilo di lavoro" ===
Questa "conversione" converte i dati rgb (senza spazio colore) nello
spazio di lavoro scelto dall'utente.

Questi spazi di lavoro sono di 8 (che suonano più che sufficienti, o
anche troppo ...): sRGB, AdobeRGB, Prophoto, Widegamut, BruceRGB,
BetaRGB, BestRGB, Rec2020. tra questi 8 profili, 5 hanno una vasta
gamma: BetaRGB (origine B.Lindbllom), BestRGB, Rec2020, WideGamut e
Prophoto.

Durante questa conversione, una gamma interna è impostata da RawTherapee
che è sempre "gamma sRGB" cioè "gamma = 2.4 e pendenza = 12.92" (come
Lightroom, vedi successivamente)

Si noti che un altro software ha fatto altre scelte:

- Adobe con ACR suggerisce 4 scelte (AdobeRGB, ColorMatch, Prophoto e
  SRGB)
- Adobe con Lightroom: nessuna scelta, ma uno spazio modificato di
  Prophoto con una gamma sRGB (Melissa)
- DxO: nessuna scelta, ma uno spazio Adobe
- NX2: scelta negli spazi di uscita disponibili

Quale scegliere? Ampio dibattito in cui i sostenitori di piccoli spazi
confliggono con spazi ampi ... tra dati persi e dati falsi o immaginari.
Infatti, lo spazio più ampio (Prophoto) ospita, per costruzione, colori
invisibili o addirittura immaginari. Inoltre, nella zona blues, in
alcune circostanze, può generare artefatti.

Un buon spazio colore avrebbe una forma che tenga conto della gamma che
riduce al minimo lo spreco di spazio ... che significa che lo spazio
deve essere scelto a seconda di ogni immagine, uno spazio troppo ampio
potrebbe generare colori insaturi in casi estremi (nel lavoro profilo,
ma che verrà riprodotto durante la conversione in uscita ...). Tuttavia,
teoricamente, la gestione del colore deve rendere questa scelta
trasparente.

La mia risposta è pragmatica, scegli lo spazio che corrisponda al
meglio! ma su quale base?

- Facciamo essenzialmente stampe con una stampante che utilizza un
  driver CMYK? In questo caso non è veramente utile scegliere un profilo
  di gamut ampio.

<figure>
<img src="/images/GAMUTS.jpg"
title="rappresentazione di 4 profili o spazi gamut" />
<figcaption>rappresentazione di 4 profili o spazi gamut</figcaption>
</figure>

- Effettui stampe con una stampante a getto d'inchiostro di alta
  qualità? In questo caso, è meglio scegliere Prophoto (questo tipo di
  stampanti ha una gamma, che per alcuni colori è più ampia di
  WidegamutRGB), come profilo di lavoro, ma anche come profilo di output
  e, naturalmente, per scegliere il profilo della stampante corretto. ..
  su questa grafica, possiamo vedere la gamma di a) 3 spazi di colore
  abituali (sRGB in blu, AdobeRGB in rosa, WideGamut in giallo), b) il
  profilo ICC per il mio D200 in grigio, c) il profilo della stampante
  Epson e la sua carta gamut larga "3800MOABKOKOPELI_2431_V4".

<!-- -->

- Avete un monitor di altissima qualità che ha una gamma vicina a
  AdobeRGB o WideGamutRGB, in questo caso prende un profilo di gamma
  esteso.

Un modo piuttosto semplice per valutare il profilo minimo è quello di
utilizzare le statistiche fornite da "vibrance" in modalità di debug
(con verbose = true). Nella finestra RawTherapee.exe verrà visualizzato
un messaggio:

- Gamut: G1negat = x iter - G165535 = iter - G2negat = z iter - G265535
  = w iter
- se un valore (x o y) su 0 viene visualizzato per uno dei due G1,
  significa che l'immagine iniziale (con i controlli precedenti:
  contrasto, esposizione, ...) supera la gamma dello spazio scelto nel
  profilo di lavoro.
- se viene visualizzato un valore (z o w) superiore a 0 per uno dei due
  G2, il che significa che la saturazione impostata da "vibrance" ha
  superato la gamma.
- È a voi scegliere se vuoi mantenere questi valori (vedi sopra) o
  inserirli nella gamma (vibrance lo fai per te, così come "evitare il
  taglio dei colori" + "abilitare il limitatore di saturazione"), ma si
  perde i colori!
- la conversione rgb ==\> RGB consente di lavorare in "float" per
  preservare i negativi essenziali ei valori di oltre 65535.

### Lavora nello spazio colore scelto dall'utente (spazio di lavoro "Profilo di lavoro")

RawTherapee ha fatto la buona scelta di lavorare in modalità Lab (o dei
suoi simili Luv o Lch) o in modalità CIECAM02 e con numeri reali. Ciò
consente di preservare i migliori colori e gamut.

Le funzioni disponibili in "Esposizione" non modificano la tonalità, ad
eccezione di "Saturazione" che lo rendono per disfunzione della modalità
Lab (vedi che la sezione
\[\[#\]_"Correzione_Munsell"_Correzione_Munsell\|#\] "Correzione
Munsell" Correzione Munsell\]\]

Stessa cosa per gli "aggiustamenti del laboratorio", per il cursore
"Saturazione", con le curve "a" e "b" e tutte le curve che controllano
la cromaticità.

"Channel Mixer" e "Equalizzatore HSV" modificano fortemente la
colorimetria, da utilizzare con tutta la conoscenza delle conseguenze
sulla colorimetria. Le funzioni: contrasto, brigmento, curva di tono, ..
possono modificare fortemente la gamma (vedi sopra il controllo con le
statistiche fornite da "Vibrance")

### Che cosa succede quando siamo in un "Profilo di lavoro" o quando cambiamo di "Profilo di lavoro" o le impostazioni?

Quando siamo in un profilo stretto come sRGB, può sembrare evidente che
i colori saranno limitati a quelli forniti dal profilo! Quindi, se un
colore iniziale (il sensore uno, leggermente modificato
dall'interpolazione) è dentro sRGB, cosa succede quando aggiorniamo i
cursori e le curve ?:

- in modalità RGB (Esposizione), se si modifica la saturazione o la
  luminosità o il contrasto, lavoriamo in modalità rgb o nella sua linea
  derivata "hsv". Ciò significa che gli effetti risultanti dipendono
  dallo spazio di lavoro ((sRGB, AdobeRGB, Prophoto), i risultati
  saranno diversi quando ci trasferiamo da "sRGB" a "Prophoto", anche se
  rimaniamo all'interno dei limiti della gamma.
- in modalità Lab, se si modifica la luminosità, la cromaticità, il
  contrasto o le curve, modifichiamo direttamente i valori L, a, b, (o
  C, h). Ciò significa che se rimaniamo all'interno dei limiti della
  gamma, l'immagine sarà la stessa (entro i limiti della gestione del
  colore)

Quando supera la gamma - vale a dire l'immagine originale - agendo sui
cursori o sulle curve, cosa succede?

- prendiamo un esempio, un colore originale è L = 27 a = 2 b = -75;
  questo colore è nello spazio di Prophoto e vale R = 42 G = 52 B = 158
  e in sRGB R = -85 G = 69 B = 184 (R negativo significa fuori gamut).
  Se cambiamo il profilo di lavoro, è evidente che questo colore non può
  essere ripristinato; la conversione XYZ darà L = 32 a = 21 b = -67 e R
  = 0 G = 69 B = 184. Il colore avrà un aspetto diverso perché è
  completamente impossibile riprodurlo in uno spazio di colore più
  piccolo.
- secondo esempio, un colore all'interno di sRGB: L = 40 a = 42 b = -44,
  ossia RGB (sRGB) R = 133 G = 66 B = 166 e RGB (Prophoto) R = 102 G =
  64 B = 140: a) se appliciamo la saturazione (+30) in esposizione, i
  valori diventano - Prophoto - L = 36 a = 49 b = -49 e sRGB L = 38 a =
  47 b = -47, perché agiamo sul Valori RGB; b) se appliciamo la
  cromaticità negli aggiustamenti del Lab; I valori del laboratorio
  diventano L = 40 a = 55 b = -58 anche in sRGB rispetto a Prophoto,
  perché rimaniamo all'interno della gamma sRGB; c) Se scegliamo un
  colore abbastanza vicino ai limiti della gamma sRGB, ma all'interno
  della gamma: L = 40 a = 63 b = 37 e appliciamo la cromaticità +30, i
  valori Lab diventano - Prophoto L = 40 a = 81 b = 49 - possiamo notare
  che la tonalità è conservata (arctg (b, a)) e in sRGB L = 44 a = 69 b
  = 50 - la tonalità non è preservata.

### Cosa significa "Evita il cambiamento di colore"?

Se si applica a c) sopra, "Evita il cambiamento di colore", il sistema
cercherà di preservare la tonalità, applicando un valore relativo dei
valori di colorimetria. L = 40 a = 65 b = 38 (che porta al canale RGB G
= 0 ).

"Evita il cambiamento di colore" realizza due cose:

- provare a mettere fuori i dati del gamut del profilo di lavoro di
  questa gamma, dando priorità a una colorimetria relativa. Sono
  rilevati i valori dei negativi RGB e la cromaticità (e la luminanza
  pure) vengono modificati per raggiungere il valore 0.
- applicare una correzione "Munsell".

### La correzione "Munsell"

Obiettivo: dare all'utente la possibilità di correggere automaticamente
i colori talvolta falsi in modalità Lab quando si modifica la
saturazione, soprattutto nei blues-crimsons, reds-yellows e green
(correzione di tipo Munsell)

Questo obiettivo ha bisogno di creare 160 LUTf:

- questi LUTf attribuiscono ad ogni colore (in senso Munsell), ogni
  luminanza, tonalità di valori su base cromatica: 2, 3 o 4 punti sono
  impostati per le cromatiche \[0..180\] da 5, 45, 85, 125 o persino 139
  quando possibile. I valori intermedi sono interpolati linearmente.
  Questi LUT provocano una minima occupazione di memoria: ognuno ha tra
  45 e 140 voci, il che significa circa 16000 voci al totale ...
- i LUTf sono realizzati in quattro aree critiche, in cui la deriva
  rispetto alla modalità Lab è importante (blu-crimson, rosso-giallo,
  verde, rosso-cremisi), per le altre aree le lacune sono basse, in ogni
  caso molto sotto le possibilità delle matrici e dei profili ICC.
- questi LUTf hanno l'illuminante C come base (leggermente diversa da
  D50 o D65), ma a causa del fatto che lavoriamo su una base di gap e
  non su valori assoluti, l'errore di calcolo è molto basso (meno
  dell'1% della correzione , in ogni caso molto sotto le possibilità
  delle matrici e dei profili ICC).
- le correzioni delle tesi sono rapide, tuttavia stanno aumentando il
  tempo di elaborazione "vibrance" o "correzione del laboratorio" di
  circa il 10%.
- se è abilitata l'opzione "verbosa", possiamo vedere che appaiono per
  ogni tipo di correzione, il numero di pixel in questione e un'idea
  ruvida della dimensione di correzione (in radianti). Per i valori di
  correzione in radianti, il gap di colore nel deltaE94 è il seguente:

1.  correzione = 0.4 rad deltaE94 = 12 per blu-cimurio
2.  correction = 0.2 rad deltaE94 = 8 per il colore rosso-giallo
3.  correction = 0,1 rad deltaE94 = 3,7 per il verde
4.  correzione = 0,05 rad deltaE94 = 2 per rosso-crimson
5.  i valori massimi comuni della deriva possono raggiungere circa da
    0,05 radianti a 0,15 radianti per le modifiche medie di saturazione,
    i valori da 0,2 a 0,25 radianti non sono eccezionali.
6.  per informazioni, un deltaE94 inferiore a 1 è trascurabile, è
    notevole intorno a 2 o 3 e molto importante a 8 o 11.

<File:Munsell-Lab-L20.jpg%7CColours> drifts representation for L=20
<File:Munsell-Lab-L40.jpg%7CColours> drifts representation for L=40
<File:Munsell-Lab-L70.jpg%7CColours> drifts representation for L=70

### Spazio di uscita "Profilo di uscita"

#### Selezione dello spazio

La prima cosa da esaminare è: quali sono i profili di output installati
nel computer? Ciò dipende da: a) il sistema operativo (sul suo volto,
Linux non installa alcun profilo); b) gli altri software grafici
installati (Capture NX2, PhotoShop CS, DxO ecc.), ognuno dei quali
installa i profili proprietari, ad esempio NX2 installa alcuni
NksRGB.icm NkAdobe.icm ecc. che sono protetti da copyright ...; c) i
profili che è possibile scaricare sul web, ad esempio sui siti web Adobe
o B.Lindbloom.

In linea di principio consiglierei di controllare l'installazione o di
installare i profili di uscita corrispondenti ai profili di lavoro -
cioè \* .icm o \* .icc file fisicamente presenti sul tuo computer e che
non hanno nulla a che fare con la matrice di calcolo di "iccmatrices.h
". Se questi file sono mancanti, l'output TIFF o JPEG non può essere
fatto nei confronti di questi profili, ma sarà di default (se il file
RT_sRGB.icm è presente) eseguito nello spazio di output SRGB.

Questi profili hanno i seguenti nomi (possiamo trovare altri che
dispongono delle stesse caratteristiche o caratteristiche vicine), sono
generalmente protette da copyright e di conseguenza non possono essere
spediti con un software Open Source senza autorizzazione. Sono
disponibili sul Web: ProPhoto.icm; SRB Color Space profile.icm;
AdobeRGB1998.icc; BestRGB.icm; BetaRGB.icc; Bruce.icm; WideGamutRGB.icc.
Naturalmente puoi installare altri come CIE.icc; Colormatch.icc;
eccetera.

Devono essere installati nella cartella RawTherapee "Iccprofiles /
output" o in \\ windows \\ system32 \\ spool \\ drivers \\ color per
Windows e / usr / share / color / icc per gli altri sistemi.

Quando si sceglie un profilo di output, ad esempio AdobeRGB1998 e il
profilo di lavoro Prophoto, LCMS2 converti con un [Colourimetric
Intent](Preferences_#_Rendering_Intent.md) (scelto per
impostazione predefinita nelle opzioni RawTherapee: relative,
percettive, ...) i dati RGB dallo spazio di lavoro all'uscita spazio.

<figure>
<img src="/images/GamutL50.jpg" title="Gamut for a luminance L=50" />
<figcaption>Gamut for a luminance L=50</figcaption>
</figure>

<File:GamutL05.jpg%7CGamut> for a luminance L=5
<File:GamutL25.jpg%7CGamut> for a luminance L=25
<File:GamutL75.jpg%7CGamut> for a luminance L=75
<File:GamutL95.jpg%7CGamut> for a luminance L=95

Di corsi, le osservazioni sulla scelta dello spazio colore di output
sono simili a quelle relative allo spazio di lavoro (stampa, schermo,
...).

Si desidera stampare con una stampante a getto d'inchiostro di alta
qualità (ricorda: RawTherapee non dispone di un modulo di stampa
finora), è necessario utilizzare un software di terze parti (Photoshop
...), in questo caso raccomando caldamente un profilo di output Tipo
Prophoto o WideGamut.

Prestare attenzione tuttavia, le uscite JPG, quindi 8 bit, sono quasi
incompatibili - importante rischio di posterizzazione - con ampio spazio
di gioco (Prophoto, WideGamut ...).

#### File inviati

A causa dei diritti d'autore, ho spedito file specifici con LUT più
dettagliati che dovrebbero portare meno posterizzazioni nelle ombre.
Questi file sono un sottoprodotto di [Output
Gamma](#Output_Gamma.md) (vedi sotto)

- RT_sRGB.icm: similar (primary) to sRGB.icm standard with internal
  gamma close to sRGB: g=2.40 slope=12.92
- RT_sRGB_gBT709.icm: similar (primary) to sRGB.icm standard with
  internal gamma BT709: g=2.22 slope=4.5
- RT_sRGB_g10.icm: similar (primary) to sRGB.icm standard with internal
  gamma linear: g=1.0 slope=0
- RT_Middle_gsRGB.icc: similar (primary) to AdobeRGB1998.icc standard
  with internal gamma close to sRGB: g=2.40 slope=12.92
- RT_Large_gsRGB.icc: similar (primary) to ProPhoto.icm standard with
  internal gamma close to sRGB: g=2.40 slope=12.92 (close to "Melissa"
  used by Lightroom)
- RT_Large_gBT709.icc: similar (primary) to ProPhoto.icm standard with
  internal gamma BT709: g=2.22 slope=4.5
- RT_Large_g10.icc: similar (primary) to ProPhoto.icm standard with
  internal gamma linear: g=1.0 slope=0
- Rec2020.icm: new primaries - large gamut - with internal gamma BT709:
  g=2.22 slope=4.5

#### RawTherapee gap

L'utente può facilmente notare che l'output è leggermente diverso
dall'anteprima. Questo non è un output predefinito, ma è dovuto
all'elaborazione delle curve che catturano in considerazione la nozione
di TRC (profili ICC incorporati per modificare dall'interno il rendering
dei toni).

È una delle ragioni che mi ha portato a dare possibilità di uscite
"regolabili":

1.  oppure scegliendo un profilo di uscita con un'altra gamma;
2.  con una gamma regolabile (gamma e pendenza);

o forse per realizzare un'uscita lineare e adattarla in Photoshop ...

1.  (vedi ulteriori schizzi dell'istogramma)

#### Output Gamma

Dal mio punto di vista, l'Output Gamma è uno dei punti chiave di
un'uscita TIFF o JPEG di successo, per diversi motivi: poiché l'aggiunta
di icc / icm profili sopra - che sono direttamente derivati ​​e elaborati
da output gamma - questa opzione mostra un interesse meno importante
perché l'uso di questi "pseudo profili" nuovi Prophoto e SRGB porta
vantaggi simili a Output gamma quando si seleziona lo pseudo sRGB e
Prophoto! (vedi sopra). Questa opzione consente di compensare
parzialmente il gap RawTherapee (differenza tra output / anteprima)

L'ideale sarebbe stato quello di mettere Output gamma nel primo
processo, prima di Exposure, Highlights ricostruzioni, Shadows /
highlights, ecc. Schede; ma, ed è ciò che mi sembra un gap RawTherapee,
questa modifica si è rivelata impossibile senza portare importanti
manufatti: le diverse condutture RawTherapee si sovrappongono e la
colorimetria nella parte iniziale della lavorazione, sembra più fatta da
soli che nell'elaborazione professionale. .

Ho quindi scelto di implantare questo processo nella fase finale, cosa
che non è assolutamente incongruente (anche se penso che sarebbe meglio
in fase iniziale) Output Gamma sta per permettere:

- una valutazione dell'immagine per il software senza gestione del
  colore
- una modifica dell'immagine se si stampa in CMYK (ovviamente un
  software di terze parti).

\[Lebarhon: questa sezione non è affatto chiara, lo scrittore dice
innanzitutto "La gamma di output è un punto chiave per diversi motivi" e
poi "questa opzione mostra un interesse meno importante" e dove sono le
ragioni diverse?\]

#### Alcuni pensieri

La gamma agisce in maniera abbastanza simile a una combinazione tra
"Curve di esposizione" + "punto nero" + "curve di tono" presenti in
RawTherapee, ma modificare in modo più radicale il contrasto, la
ripartizione dell'istogramma, modificando contemporaneamente (quali
funzioni precedenti non possono fare), le curve TRC delle intestazioni
di file simili a un profilo ICC di input. Un mio amico, fotografo mi ha
detto di recente: "All'inizio ho pensato di poter simulare gamma con
contrasti e curve tonali ... ma il risultato è diverso".

Perché Adobe, con Lightroom, ha progettato "Melissa" che è uno spazio
colore Prophoto con una gamma sRGB, cioè una parte lineare fino a quando
r = 12,92 e poi una gamma di 2,4?

Perché D.Coffin è stato incorporato in Dcraw da molto tempo, una gamma
lineare e una gamma variabile?

In teoria, se la gestione del colore è perfetta, qualunque sia la gamma
di output (standard, variabile ...) l'immagine deve essere identica,
perché la gestione del colore usa i dati Lab (o XYZ) e quello che
chiamiamo PCS (Profil Connexion Space in D50 ); in pratica l'immagine
sembra identica, ma guardiamo nelle tonalità, possiamo vedere che ci
sono delle lacune, forse abbastanza basse, ma abbastanza per gli utenti
di RawTherapee avrebbero potuto dire: l'immagine di uscita è diversa da
quella di "anteprima".

D'altro canto, per il software che non gestisce i colori come molti
browser web (Chrome, ...) l'immagine di uscita dipenderà dalla gamma; è
quindi importante che RawTherapee consente di visualizzare il file di
output (softproofing). Oggi è necessario tener conto di diversi fattori:

- spazio di lavoro ("profilo di lavoro") conversione verso spazio di
  uscita (profilo di uscita): può sembrare ovvio che se l'immagine ha
  colori fuori dalla gamma per uno o due dei due spazi, se l'intervallo
  di spazi è diverso, allora rendering dell'immagine sarà diversa;
- la gestione del colore esistente o no: nel caso di RawTherapee o di un
  editor che gestisce i colori, le lacune (con spazi identici di output)
  saranno bassi ma tuttavia significativi; nel caso di software che non
  gestisca i colori, l'impatto gamma sarà molto importante.
- Possibilità di configurare l'impermeabilizzazione, l'intento e il
  punto nero.
- In seguito, deve essere abbastanza facile simulare una stampa
  convertendo l'output verso il profilo della stampante; si noti che in
  questo caso, una visione dei colori stampabili dovrebbe essere un
  importante vantaggio.

Quando RawTherapee avrà una funzione simile a Photoshop CS un "colore
resistente ai formati", verrà risolto il problema di visualizzazione di
Output gamma! questa funzione consente la "prova morbida", ad es. per
simulare l'aspetto che un file avrà in un sito web o su una stampante
CMYK.

#### Various Output Gamma

In the drop down list you have 7 pre-defined gamma:

- BT709: slope=4.5 gamma=2.2
- sRGB: slope=12.92 gamma=2.4
- linear: gamma=1.0
- standard:slope=0 gamma=1.8
- standard: slope=0 gamma=2.2
- High: slope=3.35 gamma=1.3
- Low: slope=6.9 gamma=2.6

BT709 "è meglio elaborare le tonalità (saranno meno grigie) di sRGB e
tanto più, 2.2 o 1.8

"Bassa" aumenterà il contrasto delle immagini piuttosto scadenti e
consente una migliore elaborazione postale per immagini sovrapposte

"Alto" al contrario diminuirà il contrasto ...

Lineare: consente un processo in Photoshop di immagini dinamiche molto
alte regolando le curve RGB in Photoshop (difficile esercizio ...)

Inoltre, è possibile utilizzare "gamma libera" che consente di collegare
i valori di pendenza e gamma a un determinato profilo di uscita, in modo
da poter, se desiderato, uscire dalle nuove uscite collegate ai nuovi
profili aggiunti icc / icm:

- sRGB con gamma standard 1.8
- WideGamut con gamma BT709
- sRGB con gamma: 2.2 e pendenza 6.5

Ad esempio, con gli stessi file NEF esistono diversi istogrammi con
varie gamma e come riferimento l'istogramma RawTherapee (anteprima) con
le stesse impostazioni (spazio di lavoro Prophoto, profilo "neutro",
profilo di uscita = Prophoto e gamma variabile).

![Anteprima Prophoto](_RT_prev_Prophoto.jpg "Anteprima Prophoto") [file:
GammaS.jpg](file:_GammaS.jpg.md)

Più l'istogramma viene spostato a sinistra più l'immagine appare scura
...

Inoltre, non è perché gli istogrammi sono strettamente identici che il
rendering delle immagini sarà identico. Infatti, la nozione "TRC" si
svolge anche per l'anteprima come per il file di output. Questo "TRC"
agisce sulle intestazioni di file (profilo ICC) e modifica i dati di
tono. Se il valore "TRC" del file di output è noto per certi, perché è
determinato dalle funzioni di file di output (Prophoto.icm, RT_srgb.icc,
...), penso che non sia la stessa cosa di "anteprima "... (vedere
ulteriori note sull'uscita sRGB).

Alcune persone potrebbero essere preoccupate, è "RT_SRGB" identico a
"sRGB_Color_Space_Profile" e diverso dall'anteprima. Inoltre, quali sono
gli effetti di un'altra gamma?

<File:RT_prev_sRGB.jpg%7CPreview> en SRGB <File:RT_sRGB.jpg%7COutput>
RT_sRGB <File:SRGB_color_space.jpg%7COutput> sRGB_Color_space_Profile
<File:RT_sRGB_gBT709.jpg%7COutput> sRGB gamma BT709
<File:RT_sRGBg23p8.jpg%7COutput> sRGB gamma=2.3 slope=8

#### Come utilizzarlo?

Per soddisfare un desiderio di semplicità, il profilo di output sarà un
derivato del profilo di lavoro, il profilo di output del box appare in
grigio. Ciò significa profilo di output = profilo di lavoro.

Ad esempio, si seleziona Profilo di lavoro = Prophoto e Free gamma = 2.1
e slope = 4.0.

Quindi si convalida un'uscita TIF o verso l'editor e si genera un file
TIF di output, con profilo Prophoto e gamma 2.1 / 4.0. Per aprire il
file in un editor esterno (ad es. Photoshop CS), apparirà "Preferire il
profilo incorporato: sRGB IEC61966-2.1 (RTH gamma BT709 simile a HP
sRGB)" che corrispondono al profilo RT_sRGB_gBT709 ma con una modifica
che noi esaminare ulteriormente.

Altrimenti, scegliete Working profile = sRGB e Free gamma = 2.3 e slope
= 10.0, genererai un TIFF con output sRGB e gamma 2.3 e slope = 10. Per
aprire il file in un editor esterno (ad es. Photoshop CS), apparirà
"Preferire il profilo incorporato: sRGB IEC61966-2.1 (RTH gamma BT709
simile a HP sRGB)" che corrispondono al profilo RT_sRGB_gBT709 ma con
una modifica che noi esaminare ulteriormente.

Se si attiva l'opzione (Photoshop CS): "Elimina il profilo incorporato",
il file TIFF verrà visualizzato con i nuovi valori RGB a causa dei nuovi
valori di gamma e di pendenza, ma l'aspetto dell'immagine sarà diverso
(mancanza di intestazioni di file).

L'algoritmo utilizza la funzione LCMS "CMSToneCurve":

- gli spazi di uscita sono calcolati dal loro primario (rosso, verde,
  azzurro), ad es. per Prophoto: p1 = 0,7347; p2 = 0,2653; p3 = 0,1596;
  p4 = 0,8404; p5 = 0,0366; p6 = 0,0001;
- i parametri gamma sono calcolati con la funzione "calcgamma" che, di
  conseguenza, con la gamma e la pendenza, determinerà 5 parametri da
  dare alla funzione destra LCMS2.

Quindi, creiamo un pseudo-profilo, tipo di RGB "Prophoto" e con una
gamma corrispondente a quella selezionata.

Ma qui troviamo un gap LCMS2 che crea questo profilo, non scrive il
profilo corrispondente nell'intestazione dei file perché funziona con
valori RGB e non con LUT / Lab. Teoricamente, dovrebbe avere più profili
con una gamma adattata e non solo. In pratica ho portato una grande
modifica all'uscita Gamma e ho lavorato attorno al gap LCMS2
applicando - dopo la conversione RGB, un profilo \* .icc che ha le
stesse caratteristiche che i profili \* .icc o \* .icm utilizzati da
Output Gamma ma dove i tag rTRC, gTRC, bTRC vengono calcolati con
"calcgamma".

Per migliorare la comprensione dell'elaborazione TIF in modalità
lineare, è possibile leggere il tutorial di Dcraw da Guillermo Luijk
<http://www.guillermoluijk.com/tutorial/dcraw/index_en.htm>

Da cui la necessità di avere nella cartella "Iccdirectory" i file "\*
.icc" e "\* .icm": BestRGB.icm; BetaRGB.icc; Bruce.icm; WideGamutRGB.icc
(e quindi i file ICIC / icm aggiunti per lo pseudo-Prophoto, Adobe, SRGB
in "Iccprofile / output").

#### Qualità dei profili RawTherapee

L'utente può chiedersi con ragione qual è la validità dei profili
RawTherapee (RT_sRGB, RT_Large, ...)?

Questi profili hanno le stesse caratteristiche che gli originali
(AdobeRGB1998, Prophoto, SrGB Color Space Profile) presentano solo
piccole differenze al livello primario e / o al punto bianco. Non hanno
alcuna incidenza sulla qualità e sul livello dell'output.

D'altro canto, il TRC ha più dettagliato LUT passando da 1024 punti a
4096 punti. Ciò ha per conseguenza - nel caso sRGB è la produzione più
frequente - un istogramma con meno ossa di pesce che può portare
posterizzazione nelle sfumature. Ecco per il confronto con la stessa
immagine, un ingrandimento dell'istogramma da 16 bit in luci basse, tra
profilo sRGB Color Space e RT_sRGB

<File:SRGB16bits.jpg%7Cpartial> 16 bits histogram
sRGB_color_space_profile <File:RT_sRGB16bits.jpg%7Cpartial> 16 bits
histogram RT_sRGB
