---
title: Edit Current Image in External Editor
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

La funzione "*Modifica immagine corrente in editor esterno*" consente di
elaborare completamente l'immagine corrente in RawTherapee e aprirla
immediatamente in qualsiasi programma esterno. È possibile utilizzare
questa funzionalità per inviare facilmente l'immagine ad un editor di
immagini come GIMP o Photoshop per ulteriori elaborazioni oppure è
possibile impostarlo per inviare l'immagine a un visualizzatore di
immagini in modo che con un solo clic di un pulsante si visualizzino
l'immagine finale di alta qualità.

Il pulsante per inviare l'immagine ad un'applicazione esterna
[image:Image-editor.png](image:image-editor.png) si trova in
basso a sinistra del pannello di anteprima. Quando si utilizza questa
funzionalità, RawTherapee elabora l'immagine e la salva come un TIFF
intero a 16 bit codificato con gamma alla [Percorsi e
file](File_Paths/it#Temporary_Folder.md). Questi file intermedi
risultano al di fuori del controllo di RawTherapee, quindi non si
eliminano automaticamente quando si chiude RawTherapee, è bene tenere
presente questo problema e eliminarli manualmente.

Devi essere consapevole del fatto che GIMP-2.8 e seguenti non riescono a
gestire immagini a 16 bit, in modo che li ridurrà a 8 bit. Dovresti
anche sapere che GIMP-2.8 e seguenti scartano tutti i dati Exif da file
TIFF! Questo è un bug di GIMP, non di RawTherapee. GIMP 2.9 e superiori
gestiscono immagini con maggioe profondità di bit (fino a 64 bit per
canale!), Conservano tutti i metadati e sono piuttosto stabili, quindi
ti consigliamo [GIMP 2.9 o
superiore](http://www.gimp.org/downloads/get).

È possibile specificare l'editor esterno della scelta in
"*[Preferenze\>Generale\>Editor
Esterno](Preferences#External_Editor.md)*". Fare clic sul
collegamento per ulteriori informazioni sulla specifica di un editor
esterno.
