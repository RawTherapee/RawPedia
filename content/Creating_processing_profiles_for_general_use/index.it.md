---
title: Creating processing profiles for general use
contributors:
  - Andrea.romagnoli
tags:
  - 'Processing Profiles'
---

## Creazione di profili di elaborazione

![](Rt_filebrowser_customprofile.jpg "Rt_filebrowser_customprofile.jpg")).\]\]
![](Rt_imageeditor_customprofile_cropped.jpg "Rt_imageeditor_customprofile_cropped.jpg")
nel [Editor di Immagine](the_image_editor_tab).\]\] È
possibile creare i propri profili di elaborazione e presentarli nel menù
a discesa [Selettore profili di
sviluppo](The_Image_Editor_Tab#Processing_Profile_Selector.md).

- Apri una foto per creare un buon punto di partenza per un profilo di
  elaborazione.
- Potresti iniziare con il profilo "Neutral" o apportare modifiche a uno
  qualsiasi degli altri profili che vengono forniti in dotazione con
  RawTherapee. Basta applicare il profilo desiderato alla tua foto.
- Esegui le modifiche che ti piace, ricordando che le modifiche più
  specifiche non potranno funzionare per tutte le foto bene perché ogni
  foto è diversa, quindi può funzionare bene per un caso ma potrebbe non
  funzionare bene per un altro se le foto si differenziano in modo
  significativo. Ad esempio, se la fotocamera ha un sensore a bassa
  rumorosità e la tua lente non è molto nitida, potrebbe probabilmente
  aumentare l'impostazione predefinita
  [risoluzione](sharpening) o, altrimenti, se la fotocamera
  ha un sensore rumoroso, è possibile applicare un certo livello di
  [riduzione del rumore](noise_reduction) per impostazione
  predefinita. Forse non si desidera che "[Livelli
  automatici](Exposure_#_Auto_Levels.md) sia abilitato per
  impostazione predefinita o forse se la fotocamera sottoespone tutte le
  foto raw di 0.6EV, in modo da poter impostare l'iniziale
  [compensazione
  dell'esposizione](Exposure_#_Exposure_Compensation.md) a +0.6.
  Forse si desidera modificare il profilo di input predefinito su
  "[Gestione Colore](color_management#custom) oppure
  impostare il nome nel campo" Autore "e l'URL del tuo sito nel campo
  "Origine"(vedere [numero
  2420](https://code.google.com/p/rawtherapee/issues/detail?id=2420))
  della [Scheda IPTC](iptc_tab). In genere vuoi lasciare il
  [bilanciamento del bianco](white_balance) impostato su
  "Macchina fotografica", perché se si imposta un valore personalizzato,
  appare solo come desiderato in fotografie che sono state girate in
  condizioni identiche di illuminazione - un valore di temperatura di
  6500 non sarà simile a una foto scattata alla luce del sole mentre lo
  sarà per una foto scattata in un giorno nuvoloso.
- Quando si è eseguito il tweaking, fare clic sull'icona *Salva profilo
  attuale* ![File:
  Gtk-save-large.png](_Gtk-save-large.png "File: Gtk-save-large.png")
  nel pannello *Profili di elaborazione*. Inserisci qualsiasi nome; non
  è necessario specificare l'estensione - RawTherapee lo aggiungerà per
  te. Per far apparire nell'elenco a discesa è necessario salvarlo nella
  sottocartella "profili" nella cartella "config", fare riferimento alla
  pagina [Percorsi dei file](file_paths) per scoprire dove si
  trova questa cartella nel sistema.
- Riavvia RawTherapee e ora il tuo nuovo profilo di elaborazione
  apparirà nell'elenco a discesa sotto "I miei profili".

  
