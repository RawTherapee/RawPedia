---
title: Sharpening
contributors:
  - Andrea.romagnoli
  - DrSlony
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

Nota: Lo strumento *Nitidezza* viene calcolato **prima** dello strumento
*Ridimensiona*, quindi se si imposta un valore di ridimensionamento e si
sta progettando di regolare la nitidezza post-resize, non sarà possibile
in quel momento. Ma se si ridimensiona l'immagine di un fattore di 0,5,
ad esempio, si potrebbe desiderare di raddoppiare il valore di raggio di
nitidezza. Purtroppo, la nitidezza non può essere visualizzata in
anteprima con una scala inferiore a 1:1.

## Maschera di contrasto

[Maschera di contrasto](https://en.wikipedia.org/wiki/Unsharp_mask)
(USM) è una tecnica utilizzata per aumentare l'apparente
[acutanza](https://en.wikipedia.org/wiki/Autility) (contrasto dei bordi)
di un l'immagine, rendendola più chiara, anche se tecnicamente non
rafforza l'immagine. Essa utilizza diversi fenomeni del sistema visivo
umano per realizzare questo effetto, come ad esempio la [illusione di
Cornsweet](https://en.wikipedia.org/wiki/Cornsweet_illusion) e [Mach
bands](https://en.wikipedia.org/wiki/Mach_bands). Anche se la
mascheratura in altri software è semplice può causare
[aloni](https://en.wikipedia.org/wiki/Haloing), RawTherapee ha un
cursore di soglia univoco che consente di ottenere un effetto di
nitidezza superba senza un minimo rischio di aloni.

### Raggio

Il raggio determina la dimensione dei dettagli che saranno amplificati
e, di conseguenza, si riferisce alla larghezza dell'alone di nitidezza.
In generale la qualità della nitidezza è migliore se il raggio di
nitidezza è più piccolo. Per le immagini a bassa ISO che sono a fuoco e
senza sfocatura di movimento, un valore di 0,5-0,7 è soddisfacente.

### Qauntità

Il parametro *Quantità* controlla la forza della nitidezza.

### Soglia

[image: Usm_threshold.png](image:_usm_threshold.png) Lo
strumento *Soglia* aiuta a sopprimere l'amplificazione e la formazione
di aloni oltre a limitare la ntidezza ad una gamma tonale desiderata. Lo
strumento Soglia permette di creare una curva attraverso cui viene
applicata la nitidezza. L'asse verticale corrisponde all'opacità: 0% sul
fondo (trasparente, nitidezza non visibile), 100% in alto (opaco,
ntidezza visibile). L'asse orizzontale corrisponde alla luminosità:
selezionare la gamma tonale che verrà dettagliata - i toni più scuri si
trovano a sinistra, avanzando verso i toni bianchi a destra. Come
indicato nella tooltip, per spostare singolarmente ciascuno dei punti
dello strumento di soglia, tenere premuto il tasto Maiusc prima di fare
clic su un punto con il mouse. Tenendo premuto il tasto Ctrl durante lo
spostamento di un punto con il mouse, è possibile ottenere movimenti
molto fini.

Quando si sposta la coppia di cursori di destra verso il lato sinistro,
l'affilatura viene ridotta nele alte luci. Quando si sposta la coppia di
sinistra dei cursori sul lato destro, la nitidezza viene ridotta nelle
ombre e riduce al minimo l'amplificazione del rumore delle ombre.

I valori di soglia predefiniti proteggono dalla sovrastima della
nitidezza e dalla formazione di aloni nella maggior parte dei casi e
limitano l'effetto di nitidezza alle tonalità intermedie. Nell'esempio
degli screenshot, ai toni più scuri non è stato applicato USM, mentre
l'USM viene applicato ad una vasta gamma di toni dal buio alla luce e la
forza di USM scende gradualmente dal massimo al mezzo tono a nessuno ai
toni delle alteluci, in modo da impedire l'amplificazione del rumore e
la formazione di aloni.

### Definisci solo i bordi

Se si attiva *Definisci solo i bordi*, le zone uniformi non vengono
cambiate. Questo è utile quando si rendono nitide le foto rumorose.
Selezionandolo appaiono anche due nuovi cursori:

#### Raggio

Il *raggio* viene usato per rilevare il rumore. Se il rumore è basso, è
possibile utilizzare un raggio inferiore e viceversa. Un raggio più alto
rallenta l'elaborazione delle immagini.

#### Tolleranza bordi

La *Tolleranza bordi* determina quanto un pixel deve differire dal suo
vicino per essere considerato un bordo e non come rumore. È molto simile
al parametro USM *Soglia* e ha un forte impatto sulla qualità visiva.
Per le immagini a bassa ISO (a basso rumore) utilizzare 1000 o meno, per
le immagini ISO ad alta velocità utilizzare 2500-3000 o anche di più.

### Controllo dell'alone

*Controllo dell'alone* è usato per evitare effetti degli alni intorno
agli oggetti luminosi quando si aumenta la nitidezza in modo troppo
aggressivo. Quando è attiva, viene visualizzato un nuovo cursore:

#### Quantità

A 100 funziona al massimo, riducendo l'impatto visivo del filtro USM.

## Deconvoluzione RL

[deconvoluzione
RL](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
è il nomedato dai creatori di questo algoritmo, Richardson e Lucy. Qui
si suppone che l'immagine soffre di una sfocatura gaussiana (come quando
si applica un filtro Gaussiano) che potrebbe essere prodotto
dall'obiettivo, dal moto, ecc. In realtà la sfocatura potrebbe
avvicinarsi ad una sfocatura gaussiana, ma non esattamente. Pertanto,
alcuni effetti indesiderati come gli aloni potrebbero verificarsi quando
si tenta di rimuovere la sfocatura gaussiana.

### Raggio e quantità

È possibile definire il "Raggio" della sfocatura gaussiana che si
desidera rimuovere. Quando si imposta l'importo a 100, la sfocatura
gaussiana verrà rimossa completamente, ma poiché questo dà un risultato
duro, si consiglia una impostazione più bassa.

### Damping e Iterazioni

Lo smorzamento viene utilizzato per evitare la che la nitidezza produca
del rumore su aree uniformi. Poiché la deconvoluzione non può essere
fatta perfettamente alla prima volta, sono necessarie diverse operazioni
di Iterazione. Quanto viene cambiato tra ogni iterazione è definito
dall'algoritmo Richardson-Lucy. Più iterazioni vengono utilizzate più
perfettamente la sfocatura gaussiana viene rimossa, ma con ogni
iterazione la velocità diminuisce e il pericolo degli artefatti e aloni
aumenta. Normalmente non si desidera eliminare perfettamente la
sfocatura gaussiana a causa del gusto e della velocità visive personali.
Le impostazioni predefinite dovrebbero essere benissimo la maggior parte
del tempo.
