---
title: GIMP Plugin
contributors:
  - Andrea.romagnoli
tags:
  - 'General Information'
---

In questo articolo viene descritto come sia possibile aprire in GIMP le
immagini raw utilizzando RawTherapee.

Viene descritto il metodo solo per Linux. Gli utenti di Windows e MacOS
sono invitati a contribuire.

# Requirements

- RawTherapee 5.2
- GIMP 2.9.5
- The `file-rawtherapee` plugin

# Installazione

1.  Forse in futuro il programma di installazione di RawTherapee o anche
    GIMP stesso conterrà il plugin. Per ora devi compilarlo da solo.
    - Se già hai il [codice
      sorgente](Linux#Clone_the_source.md), vai nella cartella
      `tools/gimp-plugin`.
    - Se non hai il codice sorgente, scarica i file da:
      [`file-formats.h`](https://raw.githubusercontent.com/Beep6581/RawTherapee/dev/tools/gimp-plugin/file-formats.h)
      e[`file-rawtherapee.c`](https://github.com/Beep6581/RawTherapee/raw/dev/tools/gimp-plugin/file-rawtherapee.c)
2.  Compila il plugin: `gimptool-2.0 --build file-rawtherapee.c`
3.  Installa il plugin compilato. Trova la cartella dei plugins di GIMP,
    esegui GIMP e vedi in Preferences \> Folders \> Plug-Ins. Per
    esempio:
    - Installa solo per l'utente corrente:
      `cp file-rawtherapee ~/.config/GIMP/2.9/plug-ins`
    - Installa per tutti gli utenti:
      `sudo cp file-rawtherapee /usr/lib/gimp/2.0/plug-ins`
4.  Accertati che il programma trovi il plugin di `rawtherapee` e
    `rawtherapee-cli` che l'eseguibile si trovi in `$PATH`:
    - Se è stato installato RawTherapee in tutto il sistema utilizzando
      un gestore di pacchetti, probabilmente è tutto impostato.
    - Se si esegue RawTherapee da una cartella personalizzata, ad es.
      `~/programs/rt` allora ci sono due opzioni:

    1.  Edita con sudo il file `/etc/environment` e aggiungi una riga
        che contiene il percorso corretto:
        `export PATH=$PATH:$HOME/programs/rt`
    2.  Crea un link del programma nella cartella /usr/bin:
        `sudo ln -s ~/programs/rt/rawtherapee /usr/bin/rawtherapee && sudo ln -s ~/programs/rt/rawtherapee-cli /usr/bin/rawtherapee-cli`
5.  Infine imposta GIMP. Vai in Modifica\>Preferenze\>Importa Immagine e
    assicurati che "Raw Importer" è impostato sul plugin di RawTherapee.
6.  Finito.

# Utilizzo

Per aprire un file raw da GIMP. Si dovrebbe aprire automaticamente una
finestra di editor di RawTherapee con cui è possibile modificare il file
raw. Quando si chiude la finestra, l'immagine viene importata in GIMP.
