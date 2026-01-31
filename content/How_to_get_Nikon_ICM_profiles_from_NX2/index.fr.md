---
title: How to get Nikon ICM profiles from NX2
contributors:
  - Lebarhon
tags:
  - 'General Photography'
---

<span style="color: #000000; background: none; overflow: hidden; page-break-after: avoid; font-size: 2.0em; font-family: Georgia,Times,serif; margin-top: 1em; margin-bottom: 0.25em; line-height: 1.3; padding: 0; border-bottom: 1px solid #AAAAAA;">Comment
obtenir des profils Nikon ICM à partir de NX2</span>

<span style="color: red; font-size: 3.5em">OBSOLETE TO BE DELETED - replaced by "How to get Nikon ICM profiles/fr"  

</span>

<span style="color: red">OBSOLETE</span> : <span style="color: red"> Cet page est obsolète. Elle n'est valide que pour l'ancienne version de ViewNX 2. A moins que quelqu'un ne prenne en charge sa mise à jour pour le fonctionnement avec les versions actuelles de ViewNX 2, elle sera supprimée.</span>  

Capture NX 2 et View NX sont des logiciels propriétaires pour Windows
fournis pour les appareils photo Nikon et sont capables de développer
avec précision des images raw en accord avec le rendu de l'appareil
photo. En arrière plan, les deux programmes génèrent des profils ICC qui
incorporent des recettes pour les changements de tonalité en fonction
des réglages. Ces profils peuvent être utilisés par RawTherapee pour
arriver à un rendu presque identique, en suivant la même recette. Les
profils ICC d'entrée de Nikon sont des programmes propriétaires et ne
peuvent pas être distribués. Heureusement, ce logiciel extrait et génère
les profils d'entrée à la volée dans un répertoire temporaire au cours
de son exécution. Veuillez utiliser ces profils dans le respect de la
licence des logiciels Nikon. Ce procédé fonctionne avec les versions
enregistrées et les versions d'essai de Capture NX 2 et View NX.

1.  Vous devez d'abord installer Capture NX 2 (la version 2.3.8 fut
    testée, la version d'essai est suffisante), mais View NX 2 (gratuit)
    devrait aussi convenir
2.  Ouvrez le fichier NEF dans Capture NX 2 et regardez dans ce
    répertoire caché :
      
    `%APPDATA%\Local\Temp\Nkn`<random strings>`.tmp`

    Les profils ICC temporaires seront créés dans ce répertoire, ils
    ressemblent à cela :

    `Nkx_D90_962_1_03_0_00_10_00_00_00_05_00_0200_0_0_476.icm`

    Sous Windows XP, le chemin est différent :

    `%TEMP%\Nkn`<random string>`.tmp`
3.  Sous "Contrôle de l'image" (Picture Control), cliquer sur le bouton
    "Lancer l'utilitaire" (Launch Utility). Pendant que l'utilitaire
    fonctionne, les profils apparaîtront temporairement dans les
    répertoires indiqués ci-dessus. Ils apparaissent ici car Nikon
    applique des profils génériques à vos images, ils sont appelés
    paramètres de "contrôle de l'image" ("picture control”  settings).
    Par exemple, Capture NX 2 possède les profils "neutral", "standard"
    et "monochrome". Pour les utiliser avec RawTherapee, vous devez
    savoir que Nikon génère différents profils ICM avec chaque
    paramétrage différent. Pour faciliter les choix, les paramètres
    "neutral", "standard", "vivid" et "paysage" sembles similaires,
    excepté l'augmentation de la saturation et du contraste. Vous
    devriez être capable d'ajuster les courbes tonales de RawTherapee et
    donc de vous satisfaire du profil "neutral" comme point de départ.

**Note**: D'autre paramètres peuvent aussi générer de nouveaux fichiers
ICM ! Vous devez être particulièrement conscient que les photos prises
en lumière artificielle ont un profil différent, et utiliser de tels
profils pour des photos prises en lumière du jour conduira à des
couleurs dominantes. D-lighting modifie considérablement le contraste.
En cas de doute, ouvrez l'image particulière pour laquelle vous désirez
le profil de couleur dans NX 2, et utilisez ce profil dans RawTherapee.
Le plus souvent, un profil de couleur générique sera suffisant.
