---
title: Black-and-White addon
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

## I metodi diversi

### Osservazioni generali

Lo strumento Black-and-White è organizzato in tre metodi, ognuno dei
quali produce un risultato diverso in bianco e nero.

1.  Desaturation;
2.  Equalizzatore di Luminanza
3.  Miscelatore di Canale

Si prega di notare che Rawtherapee può produrre immagini in bianco e
nero senza l'utilizzo di questo strumento:

1.  impostando il cursore
    [Saturazione](exposure/it#saturation) nello strumento
    [Esposizione](exposure/it) della scheda Esposizione a
    -100;
2.  impostando il cursore
    [Cromaticità](lab_adjustments/it#_chromaticity) nella
    scheda [Correzioni Lab](lab_adjustments/it) a -100;
3.  attivando [Simulazione film](film_simulation/it) in
    bianco e nero (pellicole Ilford, Kodak, Fuji ...)

Tuttavia solo i metodi presenti nell'attuale strumento consentono di
ottenere la massima possibilità di conversione in bianco e nero.

Per un tono grigio perfetto, tranne nel caso di [Color
Toning](Color_Toning/it.md), come "Correzioni Lab" vengono
trattati alla fine della pipeline, i valori di "a" e "b" nelle
[Correzioni Lab](adjustments_lab/it) della scheda
"Esposizione" sono impostati su zero.

Notare anche l'interazione con lo strumento [Color
Toning](Color_Toning/it.md), vedere sotto [Color
Toning](Color_Toning/it.md).

### Desaturazione

Questo metodo funziona in modo tale che per ogni pixel (R=G=B) viene
dato un valore equivalente di luminanza di L=0.299\*r + 0.587\*g +
0.114\*b. Questo assicura un'immagine grigia totalmente neutra.

Nota: gli altri 2 metodi di desaturazione in Rawtherapee (citati sopra)
danno altri risultati a causa di diversi algoritmi. In "Esposizione" è
il canale "S" da HSV impostato su 0. In "Correzoni Lab" è la cromaticità
C=sqrt (a\*a+b\*b) impostata su 0.

### Equalizzatore di Luminanza

Questo metodo utilizza una [curva
piatta](General_Comments_About_Some_Toolbox_Widgets#The_Flat_Curve.md),
che consente di modificare la luminanza in base alla tonalità.

L'algoritmo utilizza una conversione rgb==\>LCH \[modifica L basata su
H\]==\>rgb con controllo del gamut.

A differenza di altri software commerciali che agiscono solo su un
numero limitato di colori con cursori, è possibile interagire su tutta
la gamma di colori con Rawtherapee.

Infine, i valori R, G, B sono impostati allo stesso livello per
garantire un tono grigio perfetto.

Esiste un controllo di gamma, ma non ti impedisce di ottenere effetti
speciali molto buoni, spingendo la curva a valori estremi.

Qui la pipetta è molto utile. Ad esempio, scegliete con la pipetta
un'area di tono che si desidera scurire. Questo aggiunge un punto di
controllo sulla curva. Spostare questo punto di controllo verso il basso
per scurire (o verso l'alto per alleggerire) questo tono.

### Miscelatore di canale

A prima vista questo metodo sembra essere molto complesso!

C'è tuttavia una semplice spiegazione: questo metodo utilizza un mixer
di canali per gestire con cura l'equilibrio tra i diversi componenti di
colore dell'immagine, per conciliare la distribuzione delle luci, delle
tonalità intermedie e delle ombre. Consente di prendere una percentuale
di ciascun canale (R, G, B) e metterli insieme!

Il lettore sensibile con una mente matematica noterà che la somma dei 3
canali dovrebbe essere del 100% per evitare di tagliare le alteluci. Lo
stesso lettore cercherà solo valori positivi (perché sono logici) e
nessun valore negativo.

Ma non lasciare che questo blocchi la tua creatività, apri la tua mente
:

`a) valori oltre il 100%; `

`b) valori negativi. `

`Con queste due possibilità che è necessario sperimentare, è possibile creare effetti speciali e filtri di colore come infrarossi, ma anche alcune impostazioni comuni quali paesaggi, ritratto, contrasto, ecc.`

#### Componenti del miscelatore di canale

##### Presets

Consente di scegliere tra:

- impostazioni predefinite (contrasto normale, alto contrasto,
  luminosità, ritratto, paesaggio, alta e bassa sensibilità,
  panchromatica, iper pancromatica, ortokromatica, infrarossi);
- impostazioni a disposizione dell'utente in base a quattro criteri:

## The different methods

### General remarks

The Black-and-White tool is organized in three methods, each producing a
different black and white result.

1.  Desaturation;
2.  Luminance Equalizer
3.  Channel Mixer

Please note that Rawtherapee can produce black-and-white images without
the use of this tool:

1.  by setting the [Saturation](exposure#saturation) slider
    in the [Exposure](exposure) tool of the Exposure tab to
    -100;
2.  by setting the
    [Chromaticity](lab_adjustments#chromaticity) slider in
    the [Lab Adjustments](lab_adjustments) tab to -100;
3.  by enabling [Film Simulation](film_simulation) in black
    and white (films Ilford, Kodak, Fuji...)

Nevertheless only the methods in the current tool gives you the maximum
of possibilities for a black-and-white conversion.

For a perfect gray tone, except in the case of [Color
Toning](Color_Toning.md), as "Ajustements Lab" are treated at
the end of the pipeline, the values of “a” and “b” in the [Lab
Adjustments](Lab_Adjustments.md) of the "Exposure" tab are set
to zero.

Note also the interaction with the [Color
Toning](Color_Toning.md) tool, see [Color Toning
section](#Color_Toning.md) below.

### Desaturation

This method works in such a way that for each pixel (R=G=B) is given an
equivalent luminance value of L=0.299\*r + 0.587\*g + 0.114\*b. This
ensures a totally neutral gray image.

Note: the other 2 methods of desaturation in Rawtherapee (quoted above)
give other results due to different algorithms. In "Exposure" it is
channel “S” from HSV that is set to 0. in "Lab Adjustments" it is
chromacity C=sqrt(a\*a+b\*b) that is set to 0.

### Luminance Equalizer

This method use a [flat
curve](General_Comments_About_Some_Toolbox_Widgets#The_Flat_Curve.md),
that allows to modify the luminance based on hue.

The algorithm uses a conversion rgb==\>LCH \[modifying L based on
H\]==\>rgb with gamut control.

Unlike some other commercial software that act only on a limited number
of colors with sliders, you can interact on the whole color palette with
Rawtherapee.

Finally, the R, G, B values are set at the same level to ensure a
perfect gray tone.

There is a gamut control, but it doesn't prevent you to obtain very good
special effects by pushing the curve to extreme values.

Here, the pipette is very useful. For example, choose with the pipette a
tone area you want to darken. This adds a control point on the curve.
Move this control point downwards to darken (or upwards to lighten) this
tone.

### Channel Mixer

At first sight this method seems to be very complex !

There is however a simple explanation: this method uses a channel mixer
in order to carefully manage the balance between the different color
components of the image, to reconcile the distribution of the lights,
mid-tones and shadows. It amounts to take a percentage of each channel
(R,G,B) and put them together !

The sensible reader with a mathematical mind will notice that the sum of
the 3 channels should be 100% to avoid clipped highlights. The same
reader will look only for positive values (because they are logical) and
no negative values.

But don't let this stop your creativity, open your mind to :

` a) values over 100%; `

`b) negative values.`

`With these two possibilities that you have to experiment with, you can create special effects and color filters such as infrared, but also some common settings such as landscapes, portrait, contrast, etc.`

#### Components of the channel mixer

##### Presets

It allows to choose between:

- predefined settings (Normal contrast, High contrast, Luminance,
  Portrait, Landscape, High and Low Sensitivity, Panchromatic, Hyper
  Panchromatic, Orthochromatic, Infrared);
- settings at user disposal based on four criteria:

1.  **Absolute RGB**: offre all'utente di mescolare i tre canali R, G e
    B senza alcun controllo per i limiti. È possibile inserire valori
    positivi o negativi con una somma inferiore, pari o superiore al
    100%.
2.  **RGB relativo**: offre all'utilizzatore di mescolare i tre canali
    R, G e B, ma con il controllo dei limiti. È possibile inserire
    valori positivi o negativi, ma la somma sarà sempre stata costretta
    al 100%. Per esempio. se impostate R = 10%, G = 10%, B = 30%, questo
    viene tradotto in R = 20%, G = 20%, B = 60%. Questa modalità è
    quella predefinita per tutte le impostazioni predefinite come
    "Paesaggio": R = 66% G = 24% B = 10%. RGB relativo è l'impostazione
    più intuitiva e semplice, soprattutto se non si imposta valori
    negativi.
3.  **Absolute ROYGCBPM**: (per Rosso Arancione Giallo Verde Ciano Blu
    Viola Magenta). Questo mixer "speciale" offre 2 opzioni
    interessanti:
    - Modificare i colori complementari: in questo caso, se si agisce su
      un cursore "OYCPM", viene eseguita automaticamente una correzione
      sui colori di base (R, G, B);
    - algoritmo OYCPM: se impostato su "Lineare", ha una risposta
      rigorosa proporzionale alla forza desiderata e agisce direttamente
      e proporzionalmente sui 2 colori basici, ad esempio Arancione
      agisce su rosso e verde; Se impostato su "Effetti speciali", si
      introduce un effetto divertente nella conversione di Orange in
      rosso e verde (risposta non lineare e forse anche su Blue in base
      ai valori dei cursori).

      
    Questa è l'impostazione meno intuitiva ma con possibilità di
    creatività massime
4.  **Relativo ROYGCBPM**: come sopra, ma con un controllo di limite al
    100% per i 3 canali di base R, G, B

##### Filtro Colore

Il filtro a colori simula le riprese con un filtro colorato posto
davanti all'obiettivo. Questi filtri riducono la trasmissione di un
colore specifico e quindi hanno un impatto sulla luminanza. Per esempio.
un filtro rosso scura un cielo blu e alleggerisce i rossi. Questo filtro
funziona come un moltiplicatore per le impostazioni effettuate con
"preset".

##### Auto

Questo pulsante attiva un algoritmo che calcola sull'intera immagine e
strettamente equilibrare i 3 canali di base R, G, B per dare loro gli
stessi pesi relativi.

#### Avvertenze

- Si noterà l'incidenza della sintonia finale del mixer di canale dopo
  aver effettuato tutte le impostazioni in Presets (tra cui "Regola
  colore complementare" e "Algorithm OYCPM ") La linea sotto Presets
  visualizza 4 numeri, ad es .: R=37,2% G=-82,3% B=126,6% Total=155%. In
  questo caso, la luminosità dell'immagine globale supererà quella
  originale del 55% e ogni pixel ha moltiplicato i propri valori - prima
  di mescolare - dai 3 dati precedenti.
- Per i valori positivi nella modalità relativa, il risultato è
  prevedibile ... È la modalità usuale per questo miscelatorre di
  canali. Puoi trovare sui valori web del film in bianco e nero che
  simula, ad esempio. "Ilford Delta 100: 21,42,37", ecc.
- Al contrario, nel modo assoluto, i valori negativi, l'utilizzo dei
  cursori "OYCPM" e l'algoritmo "Effetti speciali" possono portare a
  risultati inaspettati: schermo nero, manufatti, ...

## Correzione della Gamma

È possibile modificare la rappresentazione dei toni per ciascun canale
(R, G, B) utilizzando i cursori gamma. Questo comando simula
approssimativamente il rendering della carta sotto l'ingranditore (duro,
normale, morbido). Spingendo i cursori verso sinistra (valori negativi)
scurisce l'immagine e dà maggiore contrasto, spingendo verso destra
(valori positivi) ammorbidisce l'immagine. Avviso: non c'è un errore nel
canale Blu: quando si utilizza Prophoto come spazio di lavoro, il canale
blu è meno attivo. Utilizza lo spazio di lavoro di sRGB per visualizzare
l'effetto.

## Curva 'Prima' e curva 'Dopo'

Queste curve vengono utilizzate allo stesso modo e hanno lo stesso
risultato finale di quelle descritte nella sezione [Curve di
tono](Exposure/it#Tone_Curves.md) dello strumento
[Esposizione](exposure/it). Permettono di personalizzare lo
strumento Black-and-White, che lo rende indipendente dalle impostazioni
fatte altrove. Avviso: il "curva Dopo" ha solo una modalità, in quanto
l'immagine è in bianco e nero!

## Color Toning

- È possibile utilizzare [Color Toning](color_toning/it) con
  lo strumento Black-and-White per effetti speciali. È inoltre possibile
  utilizzare [Color Toning](color_toning/it) con simulazioni
  di pellicola in bianco e nero, ma a condizione che sia abilitato lo
  strumento in bianco e nero.
- L'architettura (i vari ordini di utensili nella pipeline di
  elaborazione), gli algoritmi "Color toning" e "Black-and-White" sono
  stati adattati per darvi il massimo degli effetti uniti.
- È possibile agire contemporaneamente su tutte le possibilità di
  "Tonifica colore", tuttavia [Bilanciamento Colore
  Ombre/Mezzitoni/Alteluci](Color_Toning/it#_Colour_Balance_Shadows/Midtones/Highlights.md)
  offre la maggior parte delle possibilità.
- Provare a passare da [Bilanciamento Colore
  Ombre/Mezzitoni/Alteluci](Color_Toning/it#Color_Balance_Shadows_/_Midtones_/_Highlights.md)
  e ad es. [Miscelazone
  L\*a\*b\*](Color_Toning#"L*a*b*_blending".md), provate i
  cursori gamma e le curve nello strumento "Bianco e nero".
- Naturalmente dovete passare attraverso una serie di prove e errori di
  iterazioni se state cercando effetti speciali.
