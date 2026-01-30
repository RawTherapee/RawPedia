---
title: Batch Adjustments - Sync it
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

RawTherapee consente di aggiustare o sincronizzare le impostazioni di
elaborazione in molte foto contemporaneamente in due modi. Permette di
copiare e incollare, in parte o interamente, su un numero di immagini i
[Profili di
elaborazione](Sidecar_Files_-_Processing_Profiles.md) (una
raccolta di impostazioni di strumenti). Permette anche di, selezionato
un qualsiasi numero di immagini, di applicare qualsiasi strumento in
tutte contemporaneamente (sincronizzazione) e consente di fare questo in
due modi. Vediamo come.

Entrambi i modi comportano una selezione di foto su cui applicare il
profilo di elaborazione o le regolazioni. Le selezioni vengono
effettuate utilizzando combinazioni di tasti standard: Shift + clic per
selezionare un intervallo, Ctrl + clic per selezionare singole immagini
oppure Ctrl + A per selezionare tutto. Entrambe le modalità vengono
eseguite nella scheda [Navigatore](file_browser_tab). Il
metodo "copia e incolla" può essere eseguito anche tramite [Sequenza di
immagini](The_Image_Editor_Tab_#_The_Filmstrip.md).

<noinclude>== Copia e Incolla ==</noinclude> <includeonly>=== Copia e
Incolla ===</includeonly> Copiare e incollare un profilo di elaborazione
in una selezione di immagini è un compito molto comune. Supponi che hai
preso una serie di foto - ad esempio gli scatti in studio, i ritratti di
nozze o le foto macro. Tutte le immagini di ciascuna serie saranno molto
simili; probabilmente utilizzeranno la stessa lente, la stessa ISO, lo
stesso bilanciamento del bianco e finiscono per essere utilizzati allo
stesso scopo. Ciò significa che tutti probabilmente richiedono le stesse
impostazioni di elaborazione - la stessa riduzione del rumore, la stessa
nitidezza, la stessa correzione della distorsione dell'obiettivo e così
via.

Per elaborare il lotto selezionato, normalmente si apre un'unica
immagine di tutta la serie nella scheda [Editor di
immagini](The_Image_Editor_Tab.md) e si modifica a piacimento.
Una volta terminata la modifica, si applica il profilo di elaborazione
di questa immagine a tutte le altre immagini della stessa serie. A tale
scopo, si deve andare nella scheda
[Navigatore](file_browser_tab), fare clic con il pulsante
destro del mouse su questa foto e selezionare "Operazioni di profilo di
elaborazione\>Copia", quindi selezionare le immagini che si desidera
applicare a questo profilo e fare clic con il pulsante destro del mouse
su uno delle immagini (non importa quale) e selezionare "Operazioni di
profilo di elaborazione\>Incolla". Con un'operazione avete replicato le
stesse impostazioni dello strumento in tutta la serie di immagini, molto
velocemente.

Inoltre, RawTherapee consente di applicare solo una parte del profilo di
elaborazione copiato, ad esempio solo lo strumento "Ridimensionamento".
A tale scopo, utilizzare l'opzione "Operazioni di elaborazione dei
profili\>Incolla parziale" invece dell'opzione "Incolla".

<noinclude>== Sincronizza ==</noinclude> <includeonly>===
Sincronizza===</includeonly> RawTherapee consente di applicare
istantaneamente le modifiche degli strumenti a una selezione di
immagini. Funzionalità analoghe in altri software sono chiamate
"sincronizzazione". Questo metodo è utile per quando non è necessario
visualizzare un'anteprima precisa delle modifiche apportate, ad esempio
quando si desidera attivare lo strumento "Ridimensionamento" in una
selezione di foto, perché quando si lavora nella scheda Navigatore
l'unica anteprima sono le piccole e inesatte miniature. Questo metodo
può essere eseguito solo dalla scheda Navigatore perché è necessario
accedere agli strumenti batch di tale tabella (il pannello a destra).

Quando si trova nella scheda Navigatore, selezionare le immagini che si
desidera regolare (sincronizzazione), quindi utilizzare il pannello
strumenti a destra per eseguire le regolazioni. Le tue modifiche possono
sostituire quelle esistenti (modalità "modifica") oppure essere aggiunte
(modalità "Aggiungi"). Ad esempio se si selezionano due foto, una delle
quali è stata modificata precedentemente con compensazione
dell'esposizione + 1EV e l'altra senza modifiche, e si imposta
Compensazione dell'esposizione a + 0.6EV, la foto precedentemente
modificata finirebbe con la compensazione dell'esposizione a + 1.6EV in
modalità "Aggiungi" e solo + 0,6EV in modalità "Modifica". La foto che
non era stata precedentemente modificata avrebbe invece + 0,6EV in
entrambe le modalità. Puoi decidere quali strumenti dovrebbero
funzionare in quale modalità con [tab Sviluppo in
serie](Preferences#Batch_Processing_Tab.md) in Preferenze.
