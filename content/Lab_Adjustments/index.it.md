---
title: Lab Adjustments
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

Dati tecnici del tool Vividezza RawTherapee, in inglese:

  
[Strumento Vividezza di
RawTherapee](http://jacques.desmis.perso.neuf.fr/RT/vibrance2.html)

Ulteriori riferimenti dettagliati, in francese:

  
["Aggiustamenti Lab" e "vividezza"
addittiva](http://jacques.desmis.perso.neuf.fr/RT/Labadj_vibr.html)

["Colorimetria"](http://jacques.desmis.perso.neuf.fr/RT/ColorRT2_6.html)

![](Lab_color_space.png "Lab_color_space.png")
[Lab](https://en.wikipedia.org/wiki/Lab_color_space) (chiamato anche
CIELAB o L\*a\*b\*) è uno spazio colore tridimensionale progettato per
approssimare la visione umana, anziché lo spazio colore RGB che modella
l'output dei dispositivi fisici e non della percezione visiva umana.
Consente di mantenere il tono (chiamato anche luminosità o valore)
separato dal colore, in modo da poterlo regolare senza cambiare il
colore.

- Il componente L corrisponde alla percezione umana della luminosità.
- Il componente a definisce la componente di colore verde/magenta.
- Il componente b definisce la componente di colore giallo/blu.

## Luminosità

Quando si utilizza il cursore Luminosità nella sezione Lab, una curva di
tono viene applicata al canale L dello spazio colore Lab. Come con il
dispositivo di scorrimento della luminosità nella sezione Esposizione,
il punto nero e il punto bianco non si muovono.

## Contrasto

Il cursore di contrasto in Lab aumenta o diminuisce il contrasto della
foto, applicato nuovamente al canale L. In termini tecnici: questo
cursore applica una curva di contrasto centrata al livello medio della
luminosità. Le tonalità al di sopra della media vengono sollevate
(abbassate), mentre le tonalità al di sotto della media sono abbassate
(sollevate).

## Chromaticità

Il cursore Lab Chromaticità aumenta o diminuisce la cromaticità
dell'immagine, applicando una curva di contrasto ai canali a e b dello
spazio Lab. L'impostazione di questo cursore a -100 elimina tutto il
colore, rendendo l'immagine in bianco e nero. Il modo migliore per
convertire un'immagine in bianco e nero è utilizzare lo strumento
dedicato "Bianco e Nero" (Black and White, B&W) nella scheda *Colore*.

## Tonalità B&W

La casella di controllo "*Tonalità B&W*" è deprecata dalla versione
4.0.12 e viene sostituita con lo strumento "[Bianco e
Nero](Black-and-White/it.md)*situato nella scheda*Colore''. Per
la compatibilità all'indietro, quando si apre i profili di elaborazione
in cui è stata utilizzata la "Tonalità B&W", il cursore "'Chromaticità
verrà automaticamente impostato su -100, fornendo lo stesso effetto.

## Evita il Color Shift

Adatta i colori dell'immagine nella gamma dello spazio colore di lavoro
e applica la [Munsell
correction](https://en.wikipedia.org/wiki/Munsell_color_system) per
mantenere la purezza del colore.

## Limita LC ai toni rossi e all'incarnato

Quando abilitato, limita gli effetti indesiderati della curva "Luminanza
secondo Cromaticità" (*LC*), in modo da rendere la pelle più chiara
(aumentando la luminosità della pelle) senza compromettere
l'abbigliamento e lo sfondo del modello.

## Protezione toni rossi e dell'incarnato

Quando abilitato, gli effetti del cursore Chromaticità e della curva CC
non verranno applicati ai colori della pelle, in modo da aumentare la
cromaticità della foto senza causare la comparsa della sovrasaturazione.

## Curve

Le regolazioni Lab forniscono una ricchezza di curve per alterare
l'aspetto dell'immagine. Di seguito le spiegazioni illustrate di ogni
curva.

### Curva L

![](Lab_L_BA.jpg "Lab_L_BA.jpg") La curva L permette di controllare la
luminosità dell'uscita in base alla luminosità dell'input, L = f (L).
L'istogramma sulla curva L riflette la luminosità prima delle
regolazioni del Lab. Questa curva consente di controllare la luminosità
senza influenzare il colore.

Una curva a forma di S applicata al canale L aumenta il contrasto
dell'immagine. Allo stesso tempo questo porta ad un aspetto
apparentemente desaturato. Le compensazioni di cromatismo possono essere
utilizzate per compensare questo effetto.  

### Curve "a" e "b"

Le curve "a" e "b" consentono di controllare rispettivamente i canali
"a" e "b" basati sui canali "a" e "b", a = f (a) e b = f (b).

Come indicato dalle barre di colore, la curva "a" consente di spostare i
colori tra verde e magenta e la curva "b" di passare tra blu e giallo.
Ciò può essere utilizzato per applicare effetti tonificanti di colore.  

#### Tonalità Colore in Bianco e Nero

La tonalità di un colore in un'immagine in bianco e nero può essere
eseguita usando uno dei due metodi: il metodo consigliato e intuitivo è
quello usando lo strumento [Tonalità
colore](Color_Toning/it#Black_and_White.md) insieme allo
strumento Bianco e Nero. L'altro metodo meno potente utilizza le curve
a\* e b\* dello strumento Correzioni L\*a\*b\* una volta che l'immagine
è desaturata. Il motivo per cui ancora descriviamo come farlo senza
utilizzare gli strumenti Tonalità Colore e Bianco e Nero è che questi
strumenti sono aggiunte relativamente nuove a RawTherapee e forse stai
ancora usando una versione precedente che manca di questi strumenti,
sono solo curiosi di quali sono le tue opzioni.

Leggete la tonalità del colore di un'immagine in bianco e nero il modo
consigliato sulla pagina dello strumento [Tonalità
Colore](Color_Toning#Black_and_White.md) questa sezione descrive
come farlo utilizzando le curve a\* e b\*.

In primo luogo è necessario rendere l'immagine in bianco e nero. Fai
questo utilizzando uno dei metodi disponibili: utilizzando lo strumento
Bianco e nero o diminuendo la saturazione nello strumento Esposizione
oppure diminuendo la cromaticità nello strumento Regolazioni L\*a\*b\*.
Ogni strumento porta ad un effetto diverso in quanto funziona in modi
diversi e in diversi spazi di colore. È solo una questione di gusto. Una
volta che l'immagine viene ridotta in scala di grigi, è possibile dare
all'immagine un tono utilizzando le curve a\* e b\*. Per copiare solo
una tonalità di colori da un'immagine all'altra, copiate il profilo di
elaborazione corrente negli appunti [Immagine:
Gtk-copy.png](Immagine:_Gtk-copy.png.md), quindi incollatelo
parzialmente facendo clic con il pulsante destro di una foto nel
*Navigatore* e selezionate "*Operazioni sui Profili di Sviluppo \>
Incolla - parziale*", oppure dalla scheda *Editor Immagine* con un
Ctrl+click in "*Incolla profilo dagli appunti*"
[image:Gtk-paste.png](image:gtk-paste.png) per incollare solo
la sezione delle *Regolazioni L\*a\*b\** del profilo. Nota che anche
altre sezioni nelle sezioni *Regolazioni L\*a\*b\** saranno incollate.
In alternativa, le curve a\* e b\* possono essere copiate e incollate
singolarmente. Questo è un altro motivo per utilizzare il metodo
consigliato, perché è più facile e preciso copiare e incollare gli
strumenti Tonalità colore e Bianco e Nero.  

### Curva LH

![](Lab_LH_BA.jpg "Lab_LH_BA.jpg") La curva LH (luminosità in base alla
tinta) consente di modificare la luminosità in base alla tonalità. Per
alleggerire i colori della particolare tonalità, sollevare il punto
desiderato sulla curva LH e per scurire abbassarlo.  

### Curva CH

![](Lab_CH_BA1.jpg "Lab_CH_BA1.jpg") La curva CH (cromatica in base alla
tonalità) consente di controllare la cromaticità dell'uscita in base
alla tonalità di ingresso, C = f (H). Utilizzando questa funzione, è
possibile aumentare o mutare la gamma di colori selezionati.  

### Curva HH

![](Lab_HH_BA.jpg "Lab_HH_BA.jpg") La curva HH (tonalità in base alla
tonalità) consente di modificare la tonalità di una tonalità
specificata. Ad esempio, si potrebbe spostare i rossi per diventare più
arancioni spostando il punto rosso fino a quando la linea orizzontale
spessa che appare come il punto viene trascinata diventa il colore
desiderato. RawTherapee ha due curve HH, uno negli strumenti Lab nella
scheda Esposizione e uno nello strumento HSV nella scheda Colori. La
curva HH negli strumenti Lab ha una gamma più limitata rispetto alla
curva HH nell'equalizzatore HSV, per consentire regolazioni più fini.
L'intervallo è compreso tra il colore precedente e quello successivo, ad
esempio il verde potrebbe essere cambiato nell'intervallo di giallo e
blu (come si può vedere nella curva dello screenshot sopra). Questo è
utile, ad esempio, per l'ottimizzare il tono della pelle, rimuovendo un
aspetto pallido verdastro spostando i rossi e giallando un pò verso il
magenta.  

### Curva CC

La curva CC (cromatica secondo la cromaticità) consente di controllare
la cromaticità dell'uscita in base alla cromatica di ingresso, C = f
(C). L'istogramma sulla curva CC riflette la cromatica prima della
regolazione. Ciò consente di regolare separatamente la cromaticità dei
pixel di bassa e alta saturazione, in modo da aumentare la saturazione,
se necessario, senza causare la chiusura di zone già saturate.

Image:Lab_CC_BA1.jpg\|Aumenta la cromaticità bassa, cambia alta
cromaticità. Image:Lab_CC_BA2.jpg\|Cambia cromaticità bassa.
Image:Lab_CC_BA3.jpg\|Cambia cromaticità bassa.

È possibile utilizzare il pulsante Mostra/Nascondi nell' istogramma di
cromaticità ![Image:HistChro.png](HistChro.png "Image:HistChro.png")
oltre all'istogramma per aiutarti a visualizzare gli effetti della tua
curva CC nell'aggiornamento dell'istogramma e per aiutarti a trovare il
valore massimo prima di iniziare a ritagliare i colori .

Image:Lab_CC_hist_neutral.png\|Istogramma chromaticità con curva CC
neutra. Image:Lab_CC_hist_clipped.png\|Istogramma chromaticità a
forchetta con una curva CC trppo forte.

Gli screenshot mostrano l'aspetto dell'istogramma della cromaticità per
l'immagine neutra e cosa succede quando si esagera troppo con la
cromaticità (potete farlo usando il cursore Chromaticità o, come nella
schermata, scorrendo il punto di destra in alto a snistra della Curva
CC: tenendo premuto il tasto Maiusc mentre si scorre il punto aiuterà a
mantenere il punto in alto).

Per trovare la massima potenzialità cromatica che puoi applicare senza
provocare picchi indesiderati, che appariranno come regioni improvvise e
piatte di colore nell'immagine, simili a quelle di posterizzazione,
basta fare clic su Mostra/Nascondi nell'istogramma di cromaticità se non
l'hai fatto già, e poi lentamente aumentare la cromaticità fino a quando
si nota che l'istogramma comincia a puntarsi. Naturalmente la curva non
deve essere lineare.

### Curva LC

La curva LC (luminosità secondo cromaticità) consente di controllare la
luminosità dell'uscita in base alla cromaticità di ingresso, L = f (C).
Puoi utilizzarlo sui ritratti per illuminare la pelle

Image:Lab LC BA1.jpg\|Schiarisce le zone di bassa cromaticità. Image:Lab
LC BA2.jpg\|Schiarisce le tonalità della pelle.

L'azione della curva LC è modulata dalla casella di controllo *Limita LC
ai toni rossi e all'incarnato*. Così la curva LC fornisce un controllo
complesso dell'immagine, alterando la luminosità basata sulla
cromaticità dell'immagine e puntando anche su una gamma di tonalità
specificata. Con questa opzione abilitata, la luminosità delle tonalità
rossa e della pelle è influenzata, ad esempio consentendo di rendere la
pelle più chiara e nascondere le rughe e le macchie conservando il
colore dei vestiti e dello sfondo del modello. Quando è disabilitato, la
curva LC agisce anche su altri colori allo stesso modo.

La colorazione della barra sull'asse orizzontale della curva LC cambia
per riflettere a quali colori la curva si applica, come scelto dallo
stato della casella di controllo Limita LC a rosso e toni della pelle.

### Curva CL

La curva CL (cromaticità secondo luminosità) consente di controllare la
cromaticità in uscita in base alla luminosità dell'input, C = f (L).
Permette di controllare separatamente la cromaticità delle regioni
dell'immagine in base alla loro luminosità, in modo da poter diminuire
la cromaticità delle ombre se sono rumorose o per scopi artistici o
aumentare la cromaticità delle tonalità scure e medie senza
compromettere la luminosità del cielo.

Image:Lab CL BA1.jpg\|Aumenta la cromaticità delle aree chiare senza
saturare colori saturi. Image:Lab CL BA2.jpg\|La cromatica delle ombre e
delle tonalità intermedie aumenta senza saturare il cielo.
