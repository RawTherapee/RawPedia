---
title: Tone Mapping
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

Gli effetti di questo strumento sono visibili a qualsiasi livello di
zoom. Tuttavia, a causa della natura dell'algoritmo, solo lo zoom
anteprima di 1:1 (o più) corrisponde perfettamente all'immagine salvata.
Se si esegue lo zoom inferiore di 1:1, si dovrebbe essere consapevoli
che l'anteprima può corrispondere molto bene o meno all'immagine
salvata, a seconda dei cursori "*Blocco ai bordi*" and "*Scala*".
Leggere la sezione "[Come ottenere l'anteprima fedele dell'immagine
salvata](Tone_Mapping/it#Come_ottenere_l'anteprima_fedele_dell'immagine_salvata.md)".
Utilizza una finestra di dettaglio (fare clic sull'icona [image:
New-detail-window.png](image:_New-detail-window.png.md) sotto
l'opzione [pannello di anteprima
principale](The_Image_Editor_Tab/it#Pannello_di_anteprima_principale.md))
per controllare una parte dell'immagine o zoommare l'anteprima
principale al 100% (chiamato anche 1: 1)
[image:Gtk-zoom-100.png](image:gtk-zoom-100.png).

------------------------------------------------------------------------

![](Rt407-ba-tonemapping-hdr-cropped.jpg "Rt407-ba-tonemapping-hdr-cropped.jpg")
Lo strumento di mappatura del tono può essere utilizzato per sollevare
le aree scure della foto in modo da impedire il sorgere di artefatti e
può essere utilizzato per estinguere o sopprimere i dettagli per rendere
la foto più "sognante". Tone Mapping regola il contrasto globale di
un'immagine in modo diverso dal contrasto locale. In particolare, è
molto utile per diminuire il contrasto a grandi dimensioni mantenendo (o
aumentando) il contrasto di piccola scala. Il metodo utilizzato è tratto
da *Edge-Preserving Decompositions for Tone e Detail Manipulation* con
alcune modifiche.

Nota: la mappatura dei toni richiede molta memoria (RAM) ed è
computazionalmente pesante.

## Come ottenere l'anteprima fedele dell'immagine salvata

Image:Rt tm preview.jpg\|Blocco ai Bordi = 1,40 e Scala = 0,10 durante
la modifica, ma la scala è impostata a 1,00 subito prima del
salvataggio. Image:Rt tm saved.jpg\|Usando questo trucco, l'anteprima
corrisponde molto bene all'immagine salvata.

Gli effetti di questo strumento dipendono fortemente dalla dimensione
dell'immagine di ingresso. Per mantenere l'anteprima rapida, RawTherapee
alimenta ogni strumento con l'immagine visualizzata nell'anteprima alla
stessa risoluzione dell'anteprima, non l'originale, che potrebbe essere
enorme (tuttavia, quando si salva un'immagine, utilizza l'originale, e
il salvataggio richiede più tempo). L'elaborazione di un'immagine
900x600 è molto più veloce di quella di un 7360x4912, ad esempio. Gli
effetti collaterali di questo fatto sono che l'anteprima zoomata
potrebbe non corrispondere all'immagine salvata, a seconda dei cursori
"*Blocco ai bordi*" and "*Scala*".

I valori predefiniti per questo strumento sono Blocco ai bordi = 0.5 e
Scale = 0.10. Questi valori generano solitamente buoni risultati e
un'anteprima che rispecchia abbastanza l'immagine salvata. Se si
desidera modificare questi valori, è necessario elaborare l'immagine
completa ogni volta che si modifica per assicurarsi che i loro effetti
sull'uscita salvata siano quelli che avete in mente. Un modo semplice
per semplificare questa operazione è impostare un visualizzatore di
immagini come"[External
editor](Preferences/it#External_Editor.md)", quindi basta
premere il tasto Ctrl + e per far lavorare RawTherapee l'immagine e
visualizzare automaticamente in il tuo visualizzatore di immagini.

Ricorda che se si ingrandisce l'anteprima al 100%, corrisponderà
perfettamente all'immagine salvata indipendentemente da quali valori di
scorrimento utilizzate.  

## Descrizione dell'interfaccia

### Forza

Questo controlla la forza dell'effetto complessivo. A partire dalla
versione 4.2.156, aumentando la forza, le ombre vengono schiarite e le
alteluci sono leggermente scurite in modo da preservare la luminanza
media dell'immagine impedendo così l'aspetto slavato.

### Gamma

Gamma sposta l'azione del tone mapping nelle ombre o nelle alteluci.

### Blocco ai Bordi

Questo parametro influenza la sensibilità ai bordi. Maggiore è e più
probabile che un cambiamento di illuminazione sia considerato un
"bordo". Se impostato a zero il tone mapping avrà un effetto simile a
[unsharp masking](https://en.wikipedia.org/wiki/Unsharp_masking).

### Scala

Questo controllo si basa sulla differenza tra il contrasto "locale" e
"globale"; maggiore è il dettaglio da evidenziare e maggiore deve essere
impostato per essere incrementato. Vedere la nota sopra sull'influenza
che questa impostazione ha sull'anteprima rispetto all'immagine salvata.

### Iterazioni di Ribilanciamento

In alcuni casi, il tone mapping può generare un aspetto fumetto e in
alcuni casi rari possono apparire aloni morbidi ma larghi. Aumentando il
numero di iterazioni di ribilanciamento è possibile ridurre questi
problemi. Quando vengono usate le utilizzateiterazioni di
ribilanciamento, i risultati migliori saranno ottenuti se il parametro
di arresto del bordo è impostato su uno (dettagli tecnici: questo
risultato è stimato con la norma-1 (differenza) dello smussamento
(smoothness) utilizzando iterativamente i minimi quadrati ribilanciati).
Gli artefatti nei bordi ad alto contrasto possono cominciare ad apparire
quando questo valore è impostato su 1,8 o più.
