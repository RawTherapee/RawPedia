---
title: White Balance
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Color Tab'
---

Le immagini digitali consistono generalmente in una miscela dei tre
colori primari: rosso, verde e blu. Ovviamente è possibile leggere
maggiori dettagli sull'argomento altrove, i valori rossi, verdi e blu
che servono da punto di partenza in qualsiasi programma di sviluppo
della fotografia raw devono essere corretti in vari modi prima di
assomigliare alla scena fotografata. Una di queste correzioni è basata
sull'impostazione del bilanciamento del bianco corretto, perché le cose
che dovrebbero essere bianche (o grigio neutro) appaiono bianche (o
grigio neutro), altrimenti avranno una dominante di colore. Il
bilanciamento del bianco moltiplica ciascuno dei primari di colore con
una quantità diversa, fino a ottenere un risultato soddisfacente. Per
rendere questa operazione più umana, i moltiplicatori sono controllati
da dei cursori della temperatura e della tinta (e un equalizzatore
rosso/blu per le foto scattate in ambienti insolitamente "freddi" o
"caldi" - leggere di seguito) e si può impostarne i valori corretti
automaticamente usando la pipetta "Spot WB" in un'area della foto che
dovrebbe avere un colore neutro.

Un bilanciamento del bianco errato dà all'immagine una tinta di colore,
tipicamente più calda (arancio) o più fredda (blu). Alcune persone usano
questo per effetto creativo. Esistono vari strumenti e operazioni che si
basano sull'assunto che il bilanciamento dell'immagine sia corretto, ad
esempio recuperando le alte luci, la taratura del colore della pelle o
del cielo, ecc. Non utilizzare lo strumento di bilanciamento del bianco
per tinte particolari, ma utilizzarlo piuttosto per rendere bianco
quello che dovrebbe essere bianco e quindi utilizzare uno qualsiasi
degli altri strumenti di RawTherapee per aggiungere una tinta di colore
desiderata per l'effetto creativo.

## Descrizione dell'interfaccia

### Metodo

Il bilanciamento del bianco può essere impostato in modi diversi:
fotocamera, auto, personalizzato o una serie di preset per diverse
sorgenti luminose.

- [image:Wb-camera.png](image:wb-camera.png) Fotocamera

  
Usa il bilanciamento del bianco impostato dalla fotocamera. Se scatti
solo in raw (quindi non JPG + raw), conviene settare le impostazioni
della bilanciamento del bianco della fotocamera su Auto. Questo dovrebbe
generalmente dare buoni risultati.

- [image:Wb-auto.png](image:wb-auto.png) Auto

  
Corregge automaticamente il bilanciamento del bianco, supponendo che il
colore medio della scena sia grigio neutro. Funziona bene per una vasta
gamma di scene e può essere un buon punto di partenza per le regolazioni
manuali.

- [image:Wb-custom.png](image:wb-custom.png) Personalizzato

  
Permette di impostare la propria temperatura colore e tinta verde
spostando i due cursori e/o utilizzando lo strumento Spot WB.

- Preselezioni di sorgenti luminose
  - [image:Wb-sun.png](image:wb-sun.png) Luce diurna
    (Soleggiato)
  - [image:Wb-cloudy.png](image:wb-cloudy.png) Nuvoloso
  - [image:Wb-shade.png](image:wb-shade.png) Ombra
  - [image:Wb-tungsten.png](image:wb-tungsten.png) Tungsteno
  - [image:Wb-fluorescent.png](image:wb-fluorescent.png)
    Fluorescente
  - [image:Wb-lamp.png](image:wb-lamp.png) Lampada
  - [image:Wb-led.png](image:wb-led.png) LED
  - [image:Wb-flash.png](image:wb-flash.png) Flash

### Spot WB

Quando si fa clic sul pulsante Spot WB
[image:Gtk-color-picker.png](image:gtk-color-picker.png)
(collegamento: **w**), il cursore cambia in pipetta quando è sopra
l'anteprima. Fare clic su un'area grigia o neutra per determinare il
bilanciamento del bianco corretto. L'area grigia/neutra non può essere
tagliata, altrimenti le letture saranno spente. È possibile utilizzare
il selettore più volte in luoghi diversi nella foto, fino a trovare un
punto che porta ad una lettura adeguata. Utilizza la casella a discesa
*Dimensione* per modificare la dimensione della pipetta. Questo
strumento può essere utilizzato anche all'interno di una finestra di
dettaglio. Fare clic con il pulsante destro del mouse per annullare lo
strumento e tornare indietro al cursore normale.

### Temperatura e tinta

Spostando il cursore della temperatura verso sinistra il dispositivo
compie il raffreddamento dell'immagine (bluastro), spostandolo verso
destra, rende più caldo (giallastro). Spostando il cursore Tinta a
sinistra, l'immagine è porpora, spostandola a destra verde.

### Blue/Red Equalizer

Consente di deviare dal comportamento normale del "bilanciamento del
bianco", aumentando o diminuendo il rapporto tra rosso e blu. Ciò può
essere utile quando le condizioni di ripresa sono lontane
dall'illuminatore standard (ad esempio sott'acqua) o sono lontano dalle
condizioni in cui sono state eseguite le calibrazioni, in cui le matrici
o i profili ICC non sono idonei.

## Collegamento del bilanciamento del bianco all'esposizione

Il bilanciamento del bianco è descritto in temperatura e tinta, ma per
le immagini raw si traduce in pesi dei canali rossi, verdi e blu. I pesi
verranno regolati in modo che il canale con il più piccolo peso
raggiunga il ritaglio nello spazio di lavoro (di solito ProPhoto RGB)
quando il canale raw viene tagliato. In altre parole, con l'esposizione
impostata a 0.0 e nessun ripristino delle alteluci impostato, l'intero
campo visibile è completamente definito dal supporto raw. Quando il
bilanciamento del bianco cambia i pesi, si può vedere un leggero
cambiamento dell'esposizione se si apportano drastiche modifiche.
