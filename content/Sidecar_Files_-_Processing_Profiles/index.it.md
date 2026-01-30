---
title: Sidecar Files - Processing Profiles
contributors:
  - Andrea.romagnoli
tags:
  - 'Processing Profiles'
---

I profili di elaborazione([sidecar
files](https://en.wikipedia.org/wiki/Sidecar_file) con estensione PP3
per la versione 3 o PP2 per la versione precedente 2) sono file di testo
che contengono tutti gli strumenti e le impostazioni che RawTherapee
applica ad un'immagine. Se hai familiarità con altri elaboratori di
immagini raw, forse li conosci con il nome equivalente di "preset". I
profili di elaborazione provengono da tre fonti piuttosto diverse, anche
se funzionano esattamente nello stesso modo:

- "Profili predefiniti".
    
  RawTherapee viene fornito con un pacchetto di profili. Il loro scopo è
  dare un buon punto di partenza, per dimostrare come gli strumenti
  possono essere usati insieme. Sono quelli che si trovano nell'elenco a
  discesa [Selezione dei profili di
  elaborazione](The_Image_Editor_Tab#Processing_Profile_Selector.md)"
  nella scheda [Editor di immagini](the_image_editor_tab).
- "I profili personali".
    
  Quando si effettua un profilo di elaborazione che si desidera
  riutilizzare, ad esempio quello che funziona bene con la fotocamera e
  il tuo stile, è possibile salvarlo in modo che sia visualizzato anche
  nell'elenco a discesa Selezione del profilo di elaborazione, nel
  Sezione "I miei profili". Per farli apparire lì devono essere salvati
  nella cartella "profili" della cartella "config" - vedere l'articolo
  [Percorsi dei file](file_paths).
- Profili generati automaticamente.
    
  Ogni volta che si modifica un'immagine, le impostazioni degli
  strumenti che si è applicato a tale immagine vengono memorizzate in un
  profilo di elaborazione che è collegato a quella immagine (le
  informazioni sulla classifica, i contenuti del pannello di cronologia
  e gli snapshot non sono ancora memorizzati in questi file, vedere
  \[https : //code.google.com/p/rawtherapee/issues/detail? id = 473
  issue 473\]). Il resto di questa sezione tratta questo tipo di profilo
  di elaborazione, anche se molti dei commenti si applicano anche al
  primo tipo.

Per impostazione predefinita, il profilo di elaborazione di un'immagine
viene memorizzato accanto all'immagine di input (se si apre
"*kitty.raw*", verrà creato un nuovo file "*kitty.raw.pp3*", ma possono
anche essere memorizzati in una [cache centrale](file_paths).
Puoi scegliere se RawTherapee deve utilizzare la cache, scrivere il
profilo di elaborazione a fianco dell'immagine o entrambi i metodi,
dalle ""Preferenze\>Elaborazione immagine"". Ti consigliamo di
archiviare questi file accanto ai file di immagini di input in modo che
se si decide di spostare le immagini è possibile spostare facilmente i
profili di elaborazione insieme.

I profili di elaborazione si evolvono da una versione di RawTherapee
alla successiva. Ci sforziamo di garantire la compatibilità
all'indietro, ma questo non è sempre possibile. I profili di
elaborazione possono acquisire nuovi parametri o perdere quelli che sono
diventati obsoleti. Il comportamento degli strumenti può anche
evolversi, in cui i valori di default cambiano o in casi estremi il
significato di un valore viene interpretato in modo diverso; un
esempiolo strumento di riduzione del rumore, in cui un valore di
riduzione del rumore di luminanza di 10 in RawTherapee-3.0 avrebbe
portato ad un risultato diverso da quello in RawTherapee-4.0.10 dove
l'intero motore di riduzione del rumore è stato notevolmente migliorato.

Consolidare i profili di elaborazione in una cache consente di
memorizzare copie isolate dei profili di elaborazione per versione
specifica di RawTherapee. In tal caso, la cache può essere utilizzata
per rielaborare le foto in modo da ottenere la stessa uscita originaria
(ad esempio con una nuova dimensione o uno spazio colore di output)
utilizzando la stessa versione di RawTherapee in cui l'immagine è stata
modificata in origine . Se questo è auspicabile è discutibile. Si
consideri che lo scopo ultimo è elaborare più file raw possibile. Se un
anno dopo si desidera tornare ad un vecchio file raw, forse ottenere lo
stesso risultato di un anno prima non è l'idea migliore, perché le
capacità di RawTherapee potrebbero essere notevolmente migliorate in
quell'anno e il tuo gusto e la tua abilità potrebbero essere molto
migliorate. Tuttavia, eseguendo il backup di intere directory della
cache quando si installa una nuova versione di RawTherapee, si conserva
la possibilità di tornare ad una versione precedente di RawTherapee per
ottenere lo stesso risultato.

L'articolo [Percorsi dei file](file_paths) descrive dove è
possibile trovare le cartelle "*cache*" and "*config*" nel sistema.

Quando viene rilasciata una nuova versione di RawTherapee, può succedere
che viene usato un nuovo suffisso per le cartelle "*cache*" e
"*config*". Ciò significa che la nuova versione di RawTherapee non vedrà
i tuoi vecchi profili di configurazione o di elaborazione. Anche se
questo suona piacevole, ci sono buone ragioni quando decidiamo
(raramente) di farlo.

- Retrocompatibilità. Ci possono essere modifiche nel comportamento tra
  versioni vecchie e nuove di uno strumento specifico. Ad esempio, gli
  effetti dello strumento Auto Levels hanno cambiato (in meglio) tra le
  versioni 4.0.11 e 4.0.12, quindi se i tuoi vecchi profili di
  elaborazione lo avessero utilizzato, i risultati in 4.0.12 sarebbero
  un po' diversi e potrebbero richiedere una nuova regolazione. Abbiamo
  cercato di mantenere la compatibilità all'indietro dove possibile, ma
  non è stato possibile farlo ovunque. Questo non dovrebbe essere un
  problema, perché se si richiede un risultato identico è possibile
  continuare a utilizzare la vecchia versione di RawTherapee e
  utilizzare quella nuova per il lavoro futuro e, soprattutto, le tue
  abilità e il tuo gusto sono evolute nel tempo. vuoi esattamente gli
  stessi risultati che hai avuto anni fa quando puoi fare meglio adesso?
- Alcuni utenti non hanno controllato
  "[Preferenze](preferences)" per un lungo periodo, e il loro
  programma è sintonizzato per quello che funzionava con le precedenti
  versioni, non per quello ottimizzato per la versione attuale. Le
  nostre impostazioni predefinite sono buone, li teniamo aggiornati per
  rendere il look RawTherapee e le funzionalità sempre aggiorante,
  quindi talvolta è un'ottima

scelta aggiornare RawTherapee che motiverà gli utenti a esaminare anche
le nuove "[Preferenze](preferences)" .

- Alcuni utenti non hanno mai guardato all'interno di
  "[Preferenze](preferences)" e non conoscono alcune delle
  funzionalità che possono essere sbloccate. Come sopra, le impostazioni
  di default nuove attiveranno queste nuove possibiltà.
- Alcuni vecchi file di cache e di configurazione possono causare il
  crash di RawTherapee. Mentre abbiamo le soluzioni per i casi specifici
  di errori noti, è sicuro che ci saranno sempre casi sconosciuti che
  ancora causeranno instabilità. Partire da una cartella di cache e di
  configurazione pulita può ridurre questo problema.
