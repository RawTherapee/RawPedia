---
title: Edges and Microcontrast
contributors:
  - Andrea.romagnoli
  - DrSlony
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

A differenza di *[Maschera di
contrasto](Sharpening/it#Unsharp_Mask.md)*, *Bordi* è un vero
algoritmo di nitidezza. Non introduce aloni, può essere utilizzato in
qualche misura su immagini rumorose, e funziona nello spazio Lab.
*Bordi* evidenzia solo i bordi e può essere coadiuvato
con*Microcontrasto* per migliorare la struttura.

## Bordi

iterazioni  
Quanti passaggi l'algoritmo fa. Numeri troppi alti possono produrre un
effetto di posterizzazione.

Quantità  
Quanti pixel adiacenti verranno utilizzatiper definire un bordo. I
valori più grandi portano a bordi più nitidi.

Solo luminosità  
Lavora solo sul canale L\*; i canali a\* e b\* non sono toccati.

Maggiori informazioni qui:
<https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en>

## Microcontrasto

Quantità  
Uniformità  

Una matrice 3x3 è più adatta per immagini nitide.
