---
title: File Paths
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

RawTherapee utilizza una cartella "cache" per archiviare i file
temporanei che sono facili da eliminare e una cartella "config" che
memorizza le impostazioni di RawTherapee, i profili di elaborazione
personalizzati e altri file modificabili dall'utente. Queste cartelle
risiedono in un luogo speciale, descritto di seguito, e hanno un nome
che inizia con la parola "RawTherapee" opzionalmente seguito da un
suffisso. Questo suffisso è impostato dalla persona che ha fatto la
build di RawTherapee che stai utilizzando. Alcuni esempi:

- RawTherapee
- RawTherapee**4.2**
- RawTherapee**5**
- RawTherapee**5-dev**
- RawTherapee**_test**
- e altre possibili combinazioni che iniziano per "RawTherapee"

La prima parte, "RawTherapee", è predefinita. La seconda parte, il
suffisso, è lasciato alla persona che ha fatto la versione. Potrebbe
essere specifico, come "5.0-gtk2-123-g87654321", potrebbe essere
generale, come "5", potrebbe essere qualsiasi altra cosa, come "_test"
o potrebbe non essere impostata. Suggeriamo che i rilasci stabili di
RawTherapee non usino affatto un suffisso, mentre tutte le versioni di
sviluppo utilizzano "5-dev" - speriamo che la persona che ha fatto la
build lo tenga in considerazione.

## Configurazione

La cartella di configurazione di RawTherapee contiene:

- i file delle preferenze "options", che contiene tutte le impostazione
  specificate in [Preferences](preferences),
- la cartella "batch", dove sono memorizzati i [Profili di
  sviluppo](Sidecar_Files_-_Processing_Profiles/it.md) delle
  foto che sono processate nella [Coda di
  sviluppo](The_Batch_Queue/it.md),
- il file editabile
  [camconst.json](adding_support_for_new_raw_formats), dove
  vengono definiti i dettagli specifici dei formati raw che devono
  essere elaborati (questo sovrascrive i valori del file camconst.json
  di sistema),
- i ruoli dei [Profili
  dinamici](Dynamic_processing_profiles/it.md),
- e la cartella dei profile "profiles" dove è possibile salvare i
  [Profili di
  sviluppo](Sidecar_Files_-_Processing_Profiles/it.md) personali
  che appariranno nell'elenco a discesa di RawTherapee.

È necessario includere questa cartella nei backup in modo da poter
recuperare tutte le impostazioni e profili di elaborazione
personalizzati se si installa RawTherapee in un nuovo sistema.

Posizione predefinita per la cartella di configurazione RawTherapee
(cercare il prefisso "RawTherapee \*" come descritto in precedenza):

Windows XP  
`%USERPROFILE%\Local Settings\Application Data\`

Windows 7, 8 and 10  
`%LOCALAPPDATA%`

Linux  
`~/.config/`

macOS  
`~/Library/Application Support/RawTherapee/config/`

Sotto il menu 'Go' del Finder, fare clic su 'Vai alla cartella' (comando
Comando+Shift+g), quindi è possibile digitare/incollare qualsiasi
percorso a cui si desidera navigare, anche se è nascosto.

## Cache

La cartella di cache di RawTherapee contiene diversi gruppi di elementi,
in cui ciascun insieme è composto da:

- una miniatura,
- un istogramma,
- metadati,
- un file sidecar .pp3,
- e opzionalmente un profilo incorporato.

Per impostazione predefinita, RawTherapee mantiene fino a 20 000 insieme
di cache. Tieni d'occhio la cartella "cache" che nel tempo può aumentare
notevolmente di dimensione! Ciò è dovuto principalmente alle anteprime
memorizzate nella sottocartella "immagini". Eliminare la sottocartella
"immagini" è sicuro, non perderai alcuna impostazione dell' immagine,
RawTherapee dovrà solo rigenerare le miniature.

Posizione predefinita per la cartella di cache di RawTherapee (cercare
il prefisso "RawTherapee \*" come descritto in precedenza):

Windows XP  
`%USERPROFILE%\Local Settings\Application Data\`

Windows 7, 8 and 10  
`%LOCALAPPDATA%`

Linux  
`~/.cache/`

macOS  
`~/Library/Application Support/RawTherapee/cache/`

Sotto il menu 'Go' del Finder, fare clic su 'Vai alla cartella' (comando
Comando+Shift+g), quindi è possibile digitare/incollare qualsiasi
percorso a cui si desidera navigare, anche se è nascosto.

## Cartelle di configurazione e cache personalizzate

Anche se il percorso e il nome delle cartelle di cache e di
configurazione sono codificati in RawTherapee, a partire dalla versione
4.0.12.33 è possibile modificarli in qualsiasi percorso **assoluto**
utilizzando le variabili di ambiente `RT_SETTINGS` e `RT_CACHE`. Come
farlo dipende dal tuo sistema operativo, perciò basta cercare su
internet su "come impostare variabili d'ambiente in
*<il tuo sistema operativo>*".

Per esempio:

Windows  
`RT_SETTINGS=%LOCALAPPDATA%\rawtherapee\4.2`

`RT_CACHE=C:\Users\Bob\AppData\Local\rtcache`

Linux e macOS  
`RT_SETTINGS=/home/bob/.config/rawtherapee/4.2`

`RT_CACHE=/home/bob/junk/rtcache`

## Profili di sviluppo

Per creare i tuoi [Profili di
sviluppo](File_Sidecar_-_Profili_di_elaborazione/it.md) per
visualizzarli nell'elenco "Profili di sviluppo" di RawTherapee, devono
essere salvati nella cartella "profiles" che troverete nella cartella
"config" come sopra descritto.

## Cartella Temporanea

Lo strumento "[Edita l'immagine corrente in programmma
esterno](Edit_Current_Image_in_External_Editor/it.md)" memorizza
l'immagine in una cartella temporanea:

Windows  
La posizione predefinita è specificata con la variabile di ambiente
`$TEMP`, usualmente `%LOCALAPPDATA%/Temp`

Se non è specifica la variabile di ambiente `$TEMP`, viene usato `C:\`.

Linux e macOS  
La locazione predefinita è specificata con la variabile di ambiente
`$TMPDIR`, usualmente `/tmp`

Se non è specifica la variabile di ambiente `$TMPDIR`, viene usato
`/tmp`.
