---
title: Dynamic processing profiles
contributors:
  - Andrea.romagnoli
tags:
  - 'Processing Profiles'
---

A volte un singolo profilo di elaborazione predefinito "statico" non è
sufficiente a coprire tutti i casi di utilizzo. Ad esempio, la quantità
di riduzione del rumore da applicare varia in base all'impostazione
degli ISO della Fotocamera. Un altro esempio è il tipo e la quantità di
correzioni delle lenti necessarie, ovviamente dipendenti dall'obiettivo
utilizzato.

Per gestire tali casi, RawTherapee offre una funzionalità che consente
di creare un profilo di elaborazione predefinito "dinamicamente", basato
sui metadati dell'immagine in fase di elaborazione (ad esempio nome
della fotocamera e dell'obiettivo, velocità dell'otturatore, valore ISO
e così via) .

Ciò avviene definendo un insieme di "regole di profilo dinamico". Ogni
regola dispone di un [profilo di elaborazione
(parziale)](Creazione_processing_profiles_for_general_use.md)
più alcune condizioni dei metadati dell'immagine che definiscono se la
regola è applicabile. Quando un'immagine viene modificata per la prima
volta, viene analizzato l'elenco delle regole e tutti i profili
corrispondenti vengono combinati (nell'ordine indicato, in modo che le
regole successive possono superare quelle precedenti) per creare il
profilo di elaborazione iniziale.

Per attivare la funzionalità, [profilo di elaborazione
predefinito](Preferences#Default_Processing_Profile.md) deve
essere impostato su "(Dynamic)". Le regole sono definite nella sezione
[Dynamic Profile
Rules](Preferences#Dynamic_Profile_Rules_Tab.md) della finestra
delle preferenze.

Le regole di profilo dinamico lavorano sui seguenti metadati immagine:

macchina fotografica  
il nome della fotocamera (incluso il marchio) come mostrato nella
sovrapposizione di informazioni sull'immagine dell' [Editor di
Immagine](The_Image_Editor_Tab.md). Se attivo, per impostazione
predefinita questa voce provoca la regola applicabile solo alle immagini
scattate con la telecamera specificata qui (salvo che la
capitalizzazione della stringa viene ignorata). Tuttavia, se la voce
inizia con il prefisso <code>re:\</ code\>, il resto della stringa verrà
interpretato come [espressione
regolare](https://en.wikipedia.org/wiki/Regular_expression) da
utilizzare per la corrispondenza. Ad esempio, una regola con il valore
Camera impostato su <code>re:SONY ILCE- \[56\] .00\</ code\> verrà
applicato a tutte le fotocamere Sony Alpha a5xxx e a6xxx.

<!-- -->

lente  
il nome dell'obiettivo completo. Come sopra, è possibile utilizzare
un'espressione regolare partendo dal prefisso <code>re:\</ code\>

<!-- -->

ISO  
la gamma dei valori ISO

<!-- -->

Apertura  
la gamma delle aperture dell'obiettivo (misurata in f / stop)

<!-- -->

Lunghezza focale  
la gamma delle lunghezze focali utilizzate (in mm)

<!-- -->

otturatore  
l'intervallo di velocità dell'otturatore in secondi (ad esempio, entrare
0.03 per una velocità di 1/30")

<!-- -->

Compensazione dell'esposizione  
la gamma delle compensazioni di esposizione.

Di seguito viene mostrato uno screenshot.

<figure>
<img src="/images/dynamic-profile-rules-screenshot.png"
title="File:dynamic-profile-rules-screenshot.png" />
<figcaption><a
href="File:dynamic-profile-rules-screenshot.png">File:dynamic-profile-rules-screenshot.png</a></figcaption>
</figure>
