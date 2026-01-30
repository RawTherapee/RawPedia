---
title: The Batch Queue
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

Apri una foto per modificarla, modificala, e clicca su *Salva l'immagine
corrente*
![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png"),
aggiungila alla coda di elaborazione e fai clic su *OK*. Vai alla scheda
*Coda di sviluppo*. Vedrai la tua foto lì, in attesa di essere
elaborata.

Il pannello *Formato file* risiede nel lato superiore destro della
scheda *Coda di sviluppo*. È possibile salvare in JPG (8 bit per
canale), TIFF (8 o 16 bit per canale) e PNG (anche 8 o 16 bit per
canale). Puoi anche selezionare *Salvare i parametri di elaborazione con
l'immagine* - questa opzione scrive un file sidecar con tutte le
modifiche apportate a quella foto in un file di testo normale. Questo
file avrà lo stesso nome di file della tua foto, ma avrà un'estensione
".pp3".

È possibile impostare dove si desidera che l'immagine JPG, PNG o TIFF
risultante venga salvata immettendo un modello appropriato nel campo
*Usa lo schema* nel pannello *Cartella di destinazione*. Per scoprire
come creare un modello, posizionato il mouse sopra la casella di
controllo *Usa lo schema* e si apre una descrizione con una spiegazione:

<code>

`Puoi usare le seguenti stringhe di formattazione:`  
<b>`%f`</b>`, `<b>`%d1`</b>`, `<b>`%d2`</b>`, ..., `<b>`%p1`</b>`, `<b>`%p2`</b>`, ..., `<b>`%r`</b>`, `<b>`%s1`</b>`, `<b>`%s2`</b>`, ...`  
  
`Queste stringhe di formattazione si riferiscono alle diverse parti del percorso della foto, ad alcuni attributi della foto o ad un indice di sequenza arbitrario nel lavoro in sequenza. Ad esempio, se la foto in fase di elaborazione ha il seguente percorso:`  
<b><i>`/home/tom/photos/2010-10-31/dsc0042.nef`</i></b>  
`il significato delle stringhe di formattazione è:`  
<b>`%d4`</b>` = `<i>`home`</i>  
<b>`%d3`</b>` = `<i>`tom`</i>  
<b>`%d2`</b>` = `<i>`photos`</i>  
<b>`%d1`</b>` = `<i>`2010-10-31`</i>  
<b>`%f`</b>`  = `<i>`dsc0042`</i>  
<b>`%p1`</b>` = `<i>`/home/tom/photos/2010-10-31/`</i>  
<b>`%p2`</b>` = `<i>`/home/tom/photos/`</i>  
<b>`%p3`</b>` = `<i>`/home/tom/`</i>  
<b>`%p4`</b>` = `<i>`/home/`</i>  
  
<b>`%r`</b>` sarà sostituito dal grado della foto. Se la foto non è classificata,% r verrà sostituita da '0'. `  
`Se la foto è nel cestino,% r verrà sostituito da 'x'.`  
<b>`%s1`</b>`, `<b>`%s2`</b>`, ecc. saranno sostituiti da un indice di sequenza che è imbottito da 1 a 9 cifre. `  
`L'indice di sequenza inizia ogni volta che viene avviata l'elaborazione della coda e viene incrementato di uno per ogni immagine elaborata.`  
  
`Se si desidera salvare l'immagine di uscita dove risiede l'originale, scrivere:`  
<b>`%p1/%f`</b>  
  
`Se si desidera salvare l'immagine di output in una directory denominata "`<i>`mioPercorso`</i>`" situata nella cartella dell'immagine aperta, scrivere:`  
<b>`%p1/mioPercorso/%f`</b>  
  
`Se si desidera salvare l'immagine di output in una directory denominata "`<i>`/home/tom/photos/converted/2010-10-31`</i>`", scrivi:`  
<b>`%p2/home/tom/photos/converted/2010-10-31/%d1/%f`</b>

</code>

In alternativa, è possibile salvare direttamente in una directory
specifica, ma nel lungo periodo è molto più facile utilizzare un
modello.

Sulla sinistra si vede un pulsante di elaborazione *Start/Stop* e una
casella di controllo *Avvio automatico*. Se l'opzione *Avvio automatico*
è abilitata, ogni volta che una cifra viene inviata alla coda,
l'elaborazione avrà inizio immediatamente. Di solito non è desiderabile,
in quanto questo impegnerà la CPU per lo sviluppo delle foto nella coda
e pertanto tutti gli strumenti applicati mentre la coda è in esecuzione
richiederanno molto più tempo per essere eseguiti in modo da poter
vedere il loro effetto in l'anteprima - RT diventa lento. Se l'opzione
*Avvio automatico* non è selezionata, è necessario attivare manualmente
la coda facendo clic sul pulsante *Avviare l'elaborazione* una volta
pronta per farlo. Puoi mettere in pausa la coda premendo il pulsante
''Stop processing' , ma RawTherapee finirà comunque di elaborare la foto
corrente.

È possibile eliminare il contenuto della coda di elaborazione facendo
clic con il pulsante destro del mouse su una miniatura e scegliendo
"*Seleziona tutto\>Annulla il processo*".

È possibile uscire dal programma e riavviarlo più tardi; la coda di
sviluppo sarà ancora presente. La coda può anche sopravvivere a un crash
di RawTherapee, poiché le informazioni sulla coda di sviluppo vengono
scritte su disco ogni volta che aggiungi una foto, ogni volta che una
foto viene elaborata e ogni volta che una foto viene eliminata.
