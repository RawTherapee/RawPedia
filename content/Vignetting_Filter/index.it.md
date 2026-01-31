---
title: Vignetting Filter
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

![](Vignette-filter_4.00_50_50.png "Vignette-filter_4.00_50_50.png") Il
filtro è destinato ad aggiungere una vignettatura artistica alla tua
immagine. Questo filtro di vignettatura viene posizionato rispetto al
ritaglio, se viene utilizzato il ritaglio.

Per correggere la vignettatura causato dalla caduta della luce
dell'obiettivo (contrariamente a questo filtro che non è per la
correzione ma per l'effetto artistico), utilizzare [Correzione
Vignettatura](Lens/Geometry/it#Vignetting_Correction.md) nella
scheda Transforma, nello strumento Lente/Geometria. Ancora meglio,
utilizzare lo strumento [Flat Field](flat_field/it).

## Forza

La quantità di scurimento del filtro si applica in stop. La forza piena
è raggiunta negli angoli dell'immagine. Se si applica un valore negativo
gli angoli verranno illuminati invece che scuriti.

## Scia

Il cursore della scia controlla la larghezza della punta. Se a 0 solo
gli angoli saranno smussati e il resto dell'immagine non sarà
influenzato dal filtro. A 50 il pennello raggiunge la metà del centro e
il resto è inalterato, e a 100 raggiunge tutta l'immagine fino al
centro.

<File:Vignette-filter_4.00_00_50.png%7Cpenello=0>
<File:Vignette-filter_4.00_99_50.png%7Cpennello=100>

## Rotondità

Il cursore di arrotondamento controlla la geometria del filtro. A 0 la
forma è rettangolare (con angoli arrotondati), a 50 è un ellisse e a 100
è circolare. Si noti che se l'immagine è quadrata, l'ellisse sarà invece
un cerchio, quindi la forma non cambierà nel range da 50 a 100.

<File:Vignette-filter_4.00_50_00.png%7Crotondità=0>
<File:Vignette-filter_4.00_50_99.png%7Crotondità=100>
