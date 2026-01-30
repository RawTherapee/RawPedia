---
title: RGB and Lab
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

![](RGB_Cube_Show_lowgamma_cutout_b.png "RGB_Cube_Show_lowgamma_cutout_b.png")
![](Lab_color_space.png "Lab_color_space.png")
*[RGB](https://en.wikipedia.org/wiki/RGB_color_space)* and *[CIE
L\*a\*b\*](https://en.wikipedia.org/wiki/Lab_color_space)* (o
semplicemente "*Lab*") sono due diversi [spazi
colore](https://en.wikipedia.org/wiki/Color_space), o modi di descrivere
i colori.

Molte persone si chiedono quali siano le differenze tra la regolazione
della lumiinosità, del contrasto e della saturazione nello spazio colore
RGB, o la luminosità, il contrasto e la cromaticità nello spazio colore
L\*a\*b\*. RGB opera su tre canali: rosso, verde e blu. Lab è una
conversione delle stesse informazioni a un componente di luminosità L\*
e due componenti di colore - a\* e b\*. La luminosità viene mantenuta
separata dal colore, in modo da poterla regolare senza influenzare i
colori. La "luminosità" è progettata per approssimare la visione umana,
che è molto sensibile al verde, ma meno all'azzurro. Se si modifica
nello spazio Lab, il risultato spesso sembra più corretto per l'occhio,
cnservando i colori. In generale possiamo dire che quando si aumenta la
saturazione nello spazio Lab, i colori risultano più "freschi" mentre
utilizzando la stessa quantità di saturazione in RGB si ottengono colori
"più caldi".

<div align="center">

<File:colorspace_flowers_900_1_neutral.jpg> \| Neutral
<File:colorspace_flowers_900_2_rgb_lightness.jpg> \| RGB Lightness +30
<File:colorspace_flowers_900_3_lab_lightness.jpg> \| Lab Lightness +30
<File:colorspace_flowers_900_4_rgb_contrast.jpg> \| RGB Contrast +45
<File:colorspace_flowers_900_5_lab_contrast.jpg> \| Lab Contrast +45
<File:colorspace_flowers_900_6_rgb_saturation.jpg> \| RGB Saturation +25
<File:colorspace_flowers_900_7_lab_chromaticity.jpg> \| Lab Chromaticity
+25 <File:colorspace_flowers_900_8_vibrance.jpg> \| Vibrance +25

</div>

La differenza tra il cursore "Luminosità" nella sezione
"[Esposizione](exposure/it)" (nello spazio RGB) e nella
sezione "[Lab](lab_adjustments/it)" è sottile.
Un'impostazione di +30 della *Luminosità* in RGB produce un'immagine
complessivamente più luminosa di quando si utilizza un'impostazione
identica di +30 della "Luminosità" in Lab. I colori in Lab sono
piuttosto saturi. Il contrario è vero per i cursori "Contrasto"; quando
si utilizza un contrasto di +45 in RGB i colori risultano chiaramente
più caldi rispetto all'impiego dello stesso incremento di +45 del
*Contrasto* in Lab. Il contrasto è quasi lo stesso con le due
impostazioni. Utilizza entrambi i cursori per regolare la saturazione
e/o il contrasto dell'immagine. Per quanto riguarda i cursori
*Saturazione* /*Cromaticità*, impostando il cursore RGB *Saturazione* a
-100 si ottiene un'immagine in bianco e nero che sembra avere un filtro
rosso applicato mentre con la stessa variazione della *Cromaticità* in
Lab si ottiene un'immagine in bianco e nero più neutra. I valori di
saturazione positiva RGB portano a spostamenti di tonalità (maggiore è
il valore, più è visibile lo spostamento), mentre i valori positivi
*Cromaticità* il Lab aumentano i colori mantenendo corretti le loro
tonalità, rendendo così un risultato nitido e pulito. La cromaticità del
laboratorio (tramite il cursore *Cromaticità* o *Curve CC*) è il metodo
consigliato per aumentare i colori.
