---
title: The File Browser Tab
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

![](Rt_setm_fb.png "Rt_setm_fb.png") Il Navigatore è la scheda in cui
vedere le foto, permette di selezionare le foto da modificare o eseguire
operazioni in sequenza. È composto dalle seguenti parti:

- Il pannello sinistro
  - Il pannello "Risorse" con i collegamenti della cartella principale,
    ai lettori di schede USB, alla cartella predefinita "immagini" del
    sistema o alle cartelle personalizzate.
  - Il navigatore è un browser della struttura dei file che è possibile
    utilizzare per navigare nelle cartelle contenenti le foto.
    RawTherapee non complica le cose richiedendo l'importazione di foto
    in un database come altri software.
- Il pannello di destra
  - La scheda "Filtro" consente di visualizzare solo le foto che
    corrispondono ai parametri specificati.
  - La scheda "Ispeziona" mostra una miniatura in una scala fissa del
    100% dell'immagine in cui si passa il cursore del mouse, l'immagine
    è il JPEG incorporato nel file raw o l'immagine stessa se lo scatto
    non è in formato raw.
  - La scheda "Modifica Batch" consente di applicare le impostazioni
    dello strumento all'immagine o alle immagini selezionate. Ciò
    consente di abilitare rapidamente alcuni strumenti in molte foto
    contemporaneamente.
  - La scheda "Esporta veloce" consente di elaborare in modo rapido le
    immagini selezionate ignorando alcuni strumenti anche se sono
    abilitati nei profili di elaborazione di tali immagini in modo da
    ottenere un'anteprima rapida dei file raw per esempio per eliminare
    gli scatti che sono sfocati o fuori fuoco.
- Il pannello centrale mostra le miniature della cartella attualmente
  selezionata.

È possibile nascondere i singoli pannelli utilizzando "Mostra/Nascondi
il pannello sinistro
![<File:Panel-to-left.png>](Panel-to-left.png "File:Panel-to-left.png")"
e "Mostra/nascondi il pannello destro
![<File:Panel-to-right.png>](Panel-to-right.png "File:Panel-to-right.png")
"- vedere la pagina [Scorciatoie da
Tastiera](Keyboard_Shortcuts/it.md).

Quando si apre una cartella, RawTherapee genera le miniature delle foto
nel pannello centrale. La prima volta che si apre una cartella piena di
file in formato raw, RawTherapee leggerà ogni file e creerà una
miniatura basata sull'immagine JPEG incorporata (ogni foto raw ha
un'immagine JPEG incorporata, a volte anche alcune di diverse
dimensioni). Questo può richiedere un po 'di tempo sulle cartelle con
centinaia di foto, ma accade solo per la prima volta. Tutte le volte
successive che si seleziona una cartella precedentemente aperta,
RawTherapee leggerà le miniature dalla sua cache, se esistono, e questo
permetterà una visualizzazione molto veloce delle miniature.

L'immagine JPEG incorporata in ciascuna foto raw è identica all'immagine
JPEG prodotta dalla fotocamera che si otterrebbe se si scatta in
modalità JPEG (o in modalità "RAW + JPEG"). Questo JPEG non è
rappresentativo dei dati raw effettivi, perché la fotocamera applica
tutti i tipi di modifiche all'immagine JPEG, ad esempio aumentando un pò
l'esposizione, aumentando la saturazione, il contrasto, la nitidezza
etc.

Dopo aver iniziato a modificare una foto, la relativa miniatura nella
scheda "Navigatore" verrà sostituita da quella visualizzata
nell'anteprima nella scheda "Editor" e ogni modifica viene riportata
nella miniatura. Le miniature vengono memorizzate nella cache per un
rapido accesso futuro. Se si desidera tornare all'immagine JPEG
incorporata come miniatura, fare clic con il pulsante destro del mouse
sulla miniatura (o nella selezione delle miniature) e selezionare
"Operazioni di profilo di elaborazione \> Cancella".

Utilizza le icone dello zoom nella barra degli strumenti superiore del
Navigatore per rendere le miniature più piccole o più grandi. Ogni
miniatura utilizza una memoria (RAM), quindi è consigliabile non
impostare troppo le dimensioni delle anteprime ("Preferenze\> Navigatore
\> Massima altezza delle miniature").

Puoi filtrare le foto visibili utilizzando i pulsanti nel *Navigatore* o
*[Sequenza di
immagini](The_Image_Editor_Tab/it#The_Filmstrip.md) e usando la
casella*Trova*oppure il tab*Filtro''. I possibili usi sono:

- Mostra solo foto non aggiornate,
- Mostra solo le foto bracketed + 2EV,
- Mostra solo le foto classificate con 5 stelle,
- Mostra solo le foto con una gamma ISO specifica,
- Mostra solo le foto con un'estensione NEF.

## Regolazioni batch - Sincronizzazione

## Cancellazione dei file

Poiché RawTherapee è un programma cross-platform, ha un proprio cestino,
indipendente da quello del tuo sistema.

### Utilizzo del cestino di RT

Per spostare i file nel cestino, utilizzare l'opzione "Sposta nel
cestino" ![<File:Trash.png>](Trash.png "File:Trash.png") nell'angolo in
alto a destra di ciascuna miniatura o fare clic con il pulsante destro
del mouse su una selezione di file e scegliere "Operazioni file \>
Sposta nel cestino ". Questi file vengono quindi contrassegnati come nel
cestino, ma non vengono eliminati dal disco rigido.

- Per nascondere tutti i file contrassegnati come nel cestino, fare clic
  sul pulsante "Mostra solo immagini non cancellate"
  ![<File:Trash-hide-deleted.png>](Trash-hide-deleted.png "File:Trash-hide-deleted.png")
  nella barra degli strumenti superiore.
- Per visualizzare il contenuto del cestino, fare clic sul pulsante
  "Mostra contenuto del cestino"
  ![<File:Trash-show-full.png>](Trash-show-full.png "File:Trash-show-full.png").
- Mentre stai visualizzando il contenuto del cestino, una nuova finestra
  "Elimina definitivamente i file dal cestino"
  ![<File:Trash.png>](Trash.png "File:Trash.png") appare alla sinistra
  delle miniature - da usare per eliminare tutti i file del cestino dal
  disco rigido .
- Fare clic sul pulsante "Cancella tutti i filtri"
  ![<File:Filterclear.png>](Filterclear.png "File:Filterclear.png") per
  tornare alla vista predefinita.

### Eliminazione dall'hard disk

Per eliminare i file dal disco rigido senza utilizzare il cestino, fare
clic con il pulsante destro del mouse su un file o su una selezione di
file e scegliere "Operazioni file\> Elimina" o "Elimina con uscita dalla
coda". Entrambe le opzioni eliminano la foto selezionata e il suo file
sidecar dal disco rigido, ma "Elimina con l'uscita dalla coda" elimina
anche l'immagine salvata il cui nome di file corrisponde al modello che
è attualmente impostato nel Tab Coda di Sviluppo nel campo "Usa lo
schema".
