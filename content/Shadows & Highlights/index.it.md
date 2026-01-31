---
title: Shadows Highlights
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

Utilizzare questo strumento per influenzare indipendentemente le luci e
le ombre dell'immagine.

## Maschera di nitidezza

\<gallery caption="Shadows/Highlights "Sharp mask" effect" style="clear:
both"\> <File:Sh_sm_1.jpg%7CImmagine> sorgente.
<File:Sh_sm_2.jpg>\|"Maschera di nitidezza" non attiva.
<File:Sh_sm_3.jpg>\|"Maschera di nitidezza" attiva.

</gallery>

Per separare le aree scure da quelle chiare, viene creata una maschera
di nitidezza (invisibile all'utente). Ci sono due algoritmi per farlo;
uno sfuma l'immagine mentre l'altro mantiene i bordi definiti tra le
zone chiare e quelle scure. Nessuno è "migliore", entrambi hanno i
propri meriti. L'approccio a maschera morbida può portare ad aloni, ma è
veloce. La maschera nitida è lenta, ma non provoca aloni, anche se può
causare manufatti ai bordi.

## Alteluci

Il cursore Alteluci rende meno luminose le parti più brillanti
dell'immagine senza toccare i toni più scuri. Per rendere più forte
l'effetto, utilizzare valori più alti. Un valore di scorrimento di 100
trasformerà i bianchi in grigio chiaro.

## Larghezza tonale per Alteluci

Questo cursore controlla la forza del cursore Alteluci. Valori più alti
danno un effetto più forte. Un valore di 100, combinato con Alteluci
100, rende i bianchi in grigio medio (probabilmente non è
desiderabile...).

## Ombre

Questo cursore schiarisce le ombre e applica un effetto che viene
chiamato "fill-light" (o "fill-flash") in altri programmi. Valori più
alti semplificano ulteriormente le aree dell'ombra.

## Larghezza tonale per le ombre

Questo cursore controlla la forza del cursore Ombre. Un valore massimo
di 100 fornisce l'effetto rischirimento ombre più forte.

## Contrasto locale

Contrasto locale è una regolazione del contrasto adattativa a seconda
del contrasto all'interno di un'area specificata. Aumenta il contrasto
in piccole aree mantenendo il contrasto globale (che può essere
impostato con i cursori di contrasto in Esposizione o Lab). L'immagine
risultante sarà più "tridimensionale". Questa funzionalità è molto utile
quando si dispone di un'immagine nebbiosa o si è scattato la propria
immagine attraverso una finestra. L'effetto è un pò simile a una
maschera di contrasto (unsharp mask) con un raggio alto e un piccolo
valore. Un'impostazione tra i 5 ei 20 funziona meglio per la maggior
parte degli scatti.

## Raggio

Il valore del cursore Raggio influenza i cursori Alteluci, Ombre e
Contrasto Locale. Maggiore è il raggio, più forte è l'effetto del
contrasto locale. Anche l'area effettiva dei cursori Alteluci e Ombre
aumenta.

Se sei annoiato, impostare i primi quattro cursori su 100 e giocare con
il contrasto locale per trasformare il tuo processore raw preferito in
una macchina ad effetti economica!
