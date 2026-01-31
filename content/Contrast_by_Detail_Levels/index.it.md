---
title: Contrast by Detail Levels
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

*Contrasto per Livelli di Dettaglio* utilizza la decomposizione wavelet
per decomporre l'immagine in sei livelli, ognuno regolato da un cursore.
Slider 0 (Finest) ha un raggio di 1 pixel, i cursori da 1 a 5 hanno un
raggio di circa 2, 4, 8, 16 e 32 pixel. Dando alcursore un valore
inferiore a 1,0 diminuisce il contrasto locale a quel livello, mentre
dandolo un valore più elevato lo aumenta. Così potete utilizzarlo per
aumentare la nitidezza percepita di un'immagine, per aumentare il
contrasto locale o per attenuare determinati livelli di dettaglio.

Dovresti ricordare che ridimensionare un'immagine ha un impatto diretto
sulla nitidezza percepita, così come la distanza di visualizzazione. In
termini pratici, questo significa che si dovrebbe utilizzare questo
strumento mentre si è zoomato più o meno a un livello rappresentativo
della dimensione finale dell'immagine e della distanza di
visualizzazione desiderata, quindi se si desidera stampare l'immagine ad
alta risoluzione su una tela di 90x60cm e ammirarla a 30 cm di distanza
allora ha senso ingrandire fino al 100% e modificare il cursore "0
(Finest)". Tuttavia, nella vita reale, tali stampe di grandi dimensioni
si appendono normalmente sulla parete e sono apprezzate dal divano a
pochi metri di distanza - in questo caso le impostazioni del livello di
dettaglio fine non avrà alcun effetto - i tuoi occhi non possono
distinguere il dettaglio da quella distanza. Lo stesso vale per le
immagini che si desidera ridimensionare (downscale) per l'utilizzo su
Internet o per e-mail ad amici o clienti - non solo si riduce la
risoluzione scalando, ma verranno visualizzati anche su dispositivi a
bassa risoluzione, probabilmente anche a schermo intero, per esempio su
un computer portatile, tablet o telefono. Anche in questo caso il gioco
con il livello di dettaglio "0 (Finest)" non farà differenza sul
risultato finale. La maggior parte dei cursori "3" e "4" avranno un
effetto praticamente utile.

<img src="/images/Rt_cbdl_100.jpg" title="Rt_cbdl_100.jpg" width="900"
alt="Rt_cbdl_100.jpg" /> Ad esempio, per rimuovere le macchie della
pelle pur mantenendo la struttura della pelle su questa foto a 10
megapixel, dove la tua intenzione è di visualizzarla a pieno formato e
da vicino (ad es. Galleria d'arte), zoomare al 100% e iniziare a
impostare i cursori come segue:  0 (Finest): 1.4  1: 1.4  2: 0,4  3: 0,4
 4 (Coarsest): 1.2  Toni di pelle Targetting/Protection: -75

<img src="/images/Rt_cbdl_25_1.jpg" title="Rt_cbdl_25_1.jpg" width="900"
alt="Rt_cbdl_25_1.jpg" /> Se vuoi ridimensionare la foto per usarla sul
web, dovresti ridurre di circa il 25%, che è più o meno la dimensione in
cui verrà visualizzata l'immagine. Utilizzando le impostazioni di cui
sopra possiamo ancora vedere che la pelle è liscia, ma se ripristini i
primi tre cursori a "1.0", non vedrai comunque alcuna differenza! La
ragione è che a questa risoluzione più piccola, i cambiamenti a questi
livelli vengono persi nel processo di riduzione della scala. Il
risultato sarebbe identico se hai salvato l'immagine a grandezza intera
e poi di seguito ridimensionata al 25% in un altro programma, quindi non
pensate che questo sia il problema di RawTherapee: questo è
semplicemente come lavora la nitidezza (risoluzione e
[acutance](https://en.wikipedia.org/wiki/Acutance)). Conoscendo questo,
se intendi solo condividere la versione ridotta della tua foto, puoi
risparmiare tempo semplicemente ignorando i primi tre cursori.

<img src="/images/Rt_cbdl_25_2.jpg" title="Rt_cbdl_25_2.jpg" width="900"
alt="Rt_cbdl_25_2.jpg" /> Inoltre, si può trovare che i cursori hanno
effetti che non sono immediatamente apparenti al 100% di zoom quando si
riduce le dimensioni dell'immagine. Ad esempio potresti scoprire che
l'uso del cursore "4 (Coarsest)" può alleggerire piacevolmente le ombre
dure, quindi impostarlo a 0,5 e ottimizzare a piacimento.

## Processo Individuazione Prima/Dopo *Bianco e Nero*

Questa combinazione consente di decidere quando in esecuzione verrà
eseguito lo strumento CbDL. Questo strumento era stato aggiunto a
RawTherapee molto tempo fa, e più recentemente è stato aggiunto lo
strumento Black-and-White, posto prima di CbDL in pipeline. Un risultato
imprevisto è che, se abilitato lo strumento B&W, allora non è possibile
utilizzare la Skin Cogenerazione/Protezione di CbDL perché un'immagine
in bianco e nero non ha informazioni sul colore della pelle. Questa
combinazione è stata aggiunta per rimediare all'inconveniente.
L'esecuzione dello strumento CbDL prima dello strumento B&W consente di
individuare i toni della pelle prima della conversione in bianco e nero.
Ti consigliamo di rimanere con l'opzione predefinita "Prima di bianco e
nero".

## Contrasto +/- e Neutrale

Utilizzare il pulsante "*Contrasto -*" per spostare tutti e cinque i
cursori per quantità predefinite a sinistra (riduzione del rumore).
Usate il pulsante "*Contrast +*" per spostare tutti e cinque i cursori
per quantità predefinite a destra (nitidezza). Utilizza il pulsante
"*Neutro*" per azzerare tutti i cursori su 0.

Sentitevi liberi di spostare anche i cursori individuali e controllate i
risultati nella finestra dei dettagli; potresti voler ingrandire fino al
200% o più per vedere meglio questo filtro.

Per gli scatti ISO (1600+), prova ad esempio facendo clic sul pulsante
"*Contrast*" e utilizzando [Sharpening](sharpening)\>
\[Sharpening/it#Unsharp Mask\|Maschera di contrasto\]\] con una quantità
di 80.

## Soglia

Il parametro "*Soglia*" viene utilizzato per impedire l'amplificazione
del rumore: se la luminanza di un pixel differisce solo un po' dai suoi
vicini (la differenza è inferiore alla soglia), allora non viene
affilata. È possibile impostare la soglia anche su 0 ma poi tutto sarà
affilato (anche il rumore).
