---
title: Color Toning
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

## Informazioni sul Color Toning

La prima domanda che si pone è: Qual è la definizione, o cosa si intende
con "Color Toning" o "Split Toning"? Infatti, quando si consulta il Web,
generalmente scopriamo qualcosa di simile: "Color Toning consiste nel
colorare un'immagine in bianco e nero in modo diverso in base alla
luminosità, ad esempio per colorare le luci in giallo e le ombre in blu.

Estendendo il concetto, possiamo mettere sotto la stessa definizione:

1.  tonificare un'immagine a colori consente di aggiungere un colore
    dominante all'immagine. Sarà possibile modificare questo colore
    dominante nelle alteluci dell'immagine e/o nelle ombre.
2.  per estendere la tonalità all'intero spettro di luminanza, e non
    solo, in modo restrittivo, alle alteluci e alle ombre.

In RawTherapee, due tipi di algoritmi cercano di soddisfare i principi
sopra definiti:

1.  "miscelazione da colori campione": in questo caso, un valore
    cromatico viene ponderato in base a una formula come: *"output hue"
    = "input hue" + ("target hue" - "input hue") \* balance* dove
    l'equilibrio è un coefficiente tra 0 e 1. Possiamo facilmente
    trovare dei riferimenti su questo tipo di algritmi.
2.  "Aggiunte e riduzioni nei canali RGB": in questo caso, in base alla
    luminanza (alteluci, mezzitoni, ombre), ogni canale viene
    amplificato contemporaneamente riducendo le altre due. per esempio.
    un'azione sul canale rosso per una determinata gamma di luminanza,
    aumenterà il canale "R" di X% e, allo stesso tempo, i canali "G" e
    "B" verranno ridotti di X%. Notare che non è un "miscelatore dei
    canali". Non ho trovato alcun riferimento a questo tipo di
    algoritmo, ma studiando il comportamento del modulo "Color Balance"
    di Photoshop, penso di fornire un algoritmo che crea risultati
    simili.

Dall'esperienza, il primo tipo di algoritmo darà buoni risultati di
tonificazione dei colori per immagini a colori, ma non è facilmente
prevedibile e non è così buono per le immagini in bianco e nero, anche
se, ovviamente, offre risultati soddisfacenti. Questo algoritmo è
incorporato in due modi diversi - nessuno è migliore dell'altro - che
danno diversi risultati:

1.  Modalità RGB: ad ogni canale R, G e B viene applicato l'algoritmo
    descritto in (i).
2.  Modalità Lab: ad ogni componente di colore "a" (canale rosso/verde)
    e "b" (canale blu/giallo) viene applicato l'algoritmo spiegato in
    (i). Questa modalità consente, in base alle scelte proposte (menù),
    una predicibilità normale o un'importante creatività.

Il secondo tipo di algoritmo può avere tre usi basati sul cursore
"Forza":

1.  usando valori bassi, l'utente può simulare un "bilanciamento del
    colore" e modificare accuratamente il colore del tono
2.  utilizzando valori elevati, l'utente potrà, in modalità "colore",
    ottenere risultati simili come l'algoritmo "blend", ma con meno
    creatività
3.  utilizzando valori elevati, l'utente potrà, in modalità in bianco e
    nero, ottenere forti effetti speciali

## I diversi metodi

### Metodi "blend"

I metodi "blend" sono suddivisi in "blending L\*a\*b\*" che usa sia
componenti cromatici lab "a" che "b" e "cursori RGB / curve RGB" che
utilizzano lo stesso algoritmo RGB ma differiscono per l'interfaccia
utente. Il metodo Lab isola la componente di colore dalla luminanza,
mentre i due metodi RGB agiscono indirettamente sulla luminanza. Questa
differenza spiega in parte il divario comportamentale tra questi metodi.

Anche se l'interfaccia è diversa (cursori o curve), i due metodi RGB
utilizzano solo un tipo di opacità (gestione della miscelazione dei
colori), mentre la modalità Lab offre quattro di essi. Il primo
"Standard chroma" è simile a quello utilizzato nelle "curve RGB". Gli
altri tre permettono effetti speciali.

Le curve usate sono curve piane speciali.

1.  la curva di colore mostra la luminosità in ascissa e le tonalità di
    destinazione in ordinata. le due linee verticali delimitano le
    principali aree risultanti. spostando:
2.  \* le posizioni delle linee verticali;
3.  \* la forma della curva;
4.  \* le scelte di toni di destinazione;
      
    otterrai risultati diversi
5.  La curva di opacità (L\*a\*b\* miscelazione\> Cromia Standard o
    Curve RGB) visualizza la luminanza in ascissa e opacità in ordinata
    (chiamata anche Balance) che traduce il modo in cui vengono
    assemblate le tonalità originali (immagine) e la tonalità di
    destinazione in questo caso, il valore di opacità varia da 0 a 1.
    Più alta sarà la curva, più la miscelazione sarà vicino alla
    tonalità di destinazione. Quando si imposta la curva di opacità su
    0, l'immagine rimane invariata.

L'impostazione della saturazione (l'intensità massima dell'effetto) può
essere regolata:

1.  Manuale, in questo caso la casella "Automatico" non è selezionata. È
    possibile spostare i due cursori "Threshold" e "Strength".
2.  Automaticamente, in questo caso viene selezionata la casella
    "Automatico". Un algoritmo tiene conto dello spazio colore (sRGB,
    Adobe, Prophoto ...) e della saturazione dei pixel di immagine per
    determinare i valori migliori per "Threshold" e "Strength".
      
    Le impostazioni sono ovviamente senza alcun effetto per le immagini
    convertite in bianco e nero.

#### "Fusione L\*a\*b\*" particolarità

##### Special chroma

Qui la curva piatta viene sostituita da una curva diagonale. I due
componenti cromatici "a" e "b" (Lab) vengono modificati con la stessa
ampiezza. Se si sposta la curva sotto la diagonale, si introducono
valori di opacità negativi, che porteranno effetti speciali spesso
imprevedibili

##### Speciale a\* e b\*

Qui la curva piatta viene sostituita da due curve diagonali. I due
componenti cromatici "a" e "b" (Lab) sono individualmente modificati da
due diverse curve. Il primo agisce solo sulla componente "a" (Lab), cioè
sulla dimensione rosso-verde. il secondo agisce solo sulla componente
"b" (Lab), cioè sulla dimensione blu-gialla. Se si sposta la curva (s)
sotto la diagonale, si introducono valori di opacità negativi, che
porteranno effetti speciali spesso imprevedibili.

##### Cromia Speciale a '2 colori'

Qui, come nella "cromatura speciale", la curva piatta viene sostituita
da una curva diagonale. I due componenti cromatici "a" e "b" (Lab)
vengono modificati con la stessa ampiezza. Se si sposta la curva sotto
la diagonale, si introducono valori di opacità negativi, che porteranno
effetti speciali spesso imprevedibili.

La differenza con "Chroma speciale" consiste nell'utilizzare la curva di
colore. In "Chroma speciale", l'intero colore della curva = f
(Luminance) viene utilizzato, nel caso "Cromia Speciale a 2 colori",
vengono utilizzate solo le due tonalità concentrate dalle linee
verticali.

#### Specificità dei cursori RGB

L'obiettivo ergonomico cercato è quello di essere molto simili a
Lightroom (come per il modo "colori di saturazione 2")

Sono disponibili due cursori a due livelli, il primo per le alteluci, il
secondo per le ombre. Per ciascuno dei due cursori è possibile impostare
la tonalità desiderata e la forza: quando impostato su 0, i due cursori
di forza non cambiano nulla all'immagine.

Il cursore "Bilanciamento" consente di impostare l'equilibrio tra luci
alte e basse. Muovendolo verso sinistra (valori negativi) aumenta
l'azione sulle alteluci, mentre a destra (valori positivi) aumenta
l'azione sulle ombre.

### "Aggiunta" dei metodi

#### Color Balance Ombre / Mezzitoni/ alteluci

Questo metodo è molto simile al modulo Photoshop "Color Balance", sia
nella modalità di funzionamento che nel rendering.

È possibile agire in modo diverso sulle alteluci, sulle tonalità
intermedie e sulle ombre.

Ogni cursore agisce su un colore e il suo colore complementare: Rosso e
Ciano, Verde e Magenta, Blu e Giallo

Il cursore "Forza" consente di impostare la sensibilità del sistema:

1.  con valori bassi - meno di 50 - è possibile utilizzare questo
    strumento per modificare l'equilibrio dei colori dell'immagine,
    modificando così l'intera miscelazione per dare una correzione
    cromatica generalizzata,
2.  con valori medi, è possibile utilizzare questo strumento come una
    tonifica colore,
3.  con valori elevati, è possibile utilizzare questo strumento come
    tonificazione in bianco e nero, interagendo con lo strumento
    [Compendio Bianco e Nero](black-and-white_addon/it) (i
    parametri di algoritmo interni sono diversi per un colore o
    un'azione in bianco e nero)

Selezionare "Conserva luminosità" per evitare qualsiasi modifica dei
valori di luminosità nell'immagine durante la modifica del colore.
Questa opzione consente di preservare l'equilibrio del suono
nell'immagine.

#### Saturazione a 2 colori

Questo metodo è vicino a ACR e Lightroom, sia nella modalità di
funzionamento che nel rendering.

È destinato prevalentemente a cambiare la tonalità, anche se può essere
utilizzato in interazione con lo strumento [Compendio Bianco e
Nero](Black-and-White_addon/it.md).

Vengono messi a disposizione due cursori a due livelli, la prima per le
alteluci e il secondo per le ombre. Per ciascuno dei due cursori è
possibile modificare la tonalità desiderata e la forza: se impostato su
zero, i cursori di forza impediscono qualsiasi modifica dell'immagine.

Il cursore "Bilanciamento" consente di bilanciare l'azione tra alta e
bassa luminosità. Spostandolo a sinistra (valori negativi) aumenta
l'azione neille alteluci, a destra (valori positivi) aumenta l'azione
sulle ombre.

Il dispositivo di scorrimento "Forza" consente di impostare l'intero
sistema sensibilità.

Selezionare "Conserva luminosità" per evitare qualsiasi modifica dei
valori di luminosità nell'immagine durante la modifica del colore.
Questa opzione consente di preservare l'equilibrio del suono
nell'immagine.

## Bianco e nero

E 'grazie all'utilizzo del tool [Compendio Bianco e
Nero](Black-and-White_addon/it.md), in particolare
[Equalizzatore di
Luminosità](Black-and-White_addon/it#Luminance_Equalizer.md) -
allo strumento "Color Toning" in particolare [Bilanciamento del
colore](#Color_Balance_Shadows_/_Midtones_/_Highlights.md) -
otterrete gli effetti speciali più pronunciati (in bianco e nero).

## Simulazione di film

- Nel caso del colore [simulazione di
  pellicola](Film_Simulation/it.md), tutti gli strumenti "Color
  Toning" sono direttamente disponibili.
- Nel caso di bianco e nero [simulazione di
  pellicola](Film_Simulation/it.md), è obbligatorio abilitare lo
  strumento "Bianco e Nero". Il metodo
  [desaturazione](black-and-white_addon/it#desaturation) è
  quasi neutro e consente l'utilizzo diretto delle simulazioni in bianco
  e nero in tutti gli strumenti "Color Toning", ma senza essere in grado
  di utilizzare gli effetti speciali del Strumento "Bianco e Nero".
