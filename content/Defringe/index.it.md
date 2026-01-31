---
title: Defringe
contributors:
  - Andrea.romagnoli
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

[thumb](image:defringe.jpg)
[thumb](image:defringe_curve.png) Le frange viola sono una
forma di aberrazione cromatica assiale (o longitudinale) e appaiono su
spigoli scuri adiacenti a zone luminose a causa della messa a fuoco
sbagliata, delle imperfezioni delle lenti o semplicemente (ma più
tecnicamente) a causa della natura delle lenti che non concentrano tutti
i colori sul stesso piano. Poiché le lenti sono ottimizzate per mettere
a fuoco sullo stesso piano la luce visibile delle lunghezze d'onda più
lunghe, le lunghezze d'onda più brevi, le più lontane da quelle
ottimizzate per l'obiettivo (cioè viola, lunghezze d'onda viola sul lato
più corto dello spettro visibile) possono colorare visibilmente le
regioni oscure quando le aree luminose sono di intensità sufficiente.
Questo strumento dovrebbe essere in grado di rimuovere efficacemente la
maggior parte di questi difetti.

Il defringing viene applicato sia nello spazio Lab che nello spazio
CIECAM02 (se CIECAM02 è abilitato). Di conseguenza, l'abilitazione di
CIECAM02 può portare a risultati di defringing leggermente diversi,
soprattutto quando si utilizza la curva "Hue".

## Descrizione dell'interfaccia

### Raggio

I bordi di forte errore cromatico (viola) vengono soppressi mediando su
un intorno del raggio specificato.

### Soglia

Imposta una soglia per l'applicazione di defringing.

### Hue

Puoi utilizzare la [curva
piatta](General_Comments_About_Some_Toolbox_Widgets/it#The_Flat_Curve.md)
della "Tonalità" per specificare i colori *Defringe*. L'asse orizzontale
rappresenta l'intervallo di colori e l'asse verticale la forza della
rimozione delle frange. Ciò consente di limitare l'azione ad una gamma
specifica di colori senza influenzare i colori di altre tonalità.

Se trascini un puntino viola in alto conservando il resto dei colori in
basso, le frange viola verranno rimosse con una massima forza, mentre
altri colori non saranno interessati.
