---
title: Getting Started
contributors:
  - Leixet
weight: 1
---

## Benvingut

El RawTherapee és un programa de processament d'imatges en cru (raw)
multiplataforma, publicat sota una llicència GNU GPL v3. Va ser escrit
originalment per en Gábor Horváth de Budapest, i el desenvolupament es
va dur a terme durant el 2010 per un equip de gent d'arreu del món.
Enlloc de ser un editor de gràfics de trama com el Photoshop o el GIMP,
o un programa de gestió de recursos digitals com el digiKam, està
específicament enfocat en la postproducció de fotografies en cru (raw,
d'ara en endavant). I ho fa molt bé; com a mínim, el RawTherapee és un
dels programes de processament d'imatges raw més potent.

## Instal·lació del RawTherapee

Els usuaris poden baixar l'instal·lador del RawTherapee de
<http://rawtherapee.com/downloads> o del seu gestor de paquets. De tota
manera també és possible compilar-se'l un mateix, si voleu o ho
necessiteu. A la [pàgina principal de la
RawPedia](Main_Page/ca#Compilació.md) trobareu enllaços a
instruccions de com fer-ho.

Hi ha disponibles moltes versions per baixar, i aquest paràgraf intenta
explicar la diferència entre elles a persones que no estan
familiaritzades en com funciona un sistema de versions
«rolling-release». Creem noves versions de «desenvolupament» gairebé
diariament, i un o dos cops l'any publiquem una nova versió «estable»,
que va molt ben empaquetada amb tots els errors importants coneguts
solucionats. Tots els errors que es trobin a la versió estable seran
subseqüentment solucionats a les noves versions de desenvolupament, i
s'aniran acumulant fins la següent publicació estable uns mesos després,
i així successivament. Aquestes versions de desenvolupament també són
les que s'utilitzen per millorar eines existents i afegir-ne de noves,
tot i que això requereix temps per polir-les i assegurar-se que
funcionin bé des d'un principi. Per una banda, les versions de
desenvolupament tenen el nombre més alt d'errors solucionats, però per
l'altra les noves eines d'aquestes versions poden funcionar malament o
no estar del tot polides i poden aparèixer nous errors. Si voleu provar
les noves funcions, opteu per l'última versió de desenvolupament;
obtindreu l'avantatge de tenir tots els últims errors solucionats i
podreu provar les noves eines i informar-nos de problemes i idees que
tingueu, amb el cost de descobrir nous errors. Per un ús general us
recomanem l'última versió estable que us donarà una experiència general
més polida.

## Inici del RawTherapee

![](Rt_setm_fb.png "Rt_setm_fb.png") El primer cop que inicieu el
RawTherapee veureu la [pestanya del navegador de
fitxers](The_File_Browser_Tab/ca.md), i pot estar buida. Cal que
indiqueu al RawTherapee on estan les vostres fotos raw. Utilitzeu
l'arbre de directoris a l'esquerra de la pestanya del *Navegador de
fitxers* per trobar l'emmagatzematge de les vostres fotos raw i feu
doble clic a la carpeta per obrir-la. Després feu doble clic en una foto
raw per començar a editar-la.

## Edició de la primera imatge

Un cop obriu una foto raw per editar-la, veureu que la previsualització
no es mostra igual que el fitxer JPEG que us ofereix la càmera.
L'article «[Ui! La meva foto raw es veu diferent que el JPEG de la
càmera](The_Image_Editor_Tab#Eek.21_My_Raw_Photo_Looks_Different_than_the_Camera_JPEG/ca.md)»
ho explica

L'edició es porta a terme a la pestanya de l'[editor
d'imatges](The_Image_Editor_Tab/ca.md). Aquí és on treballareu
amb el RawTherapee per crear impressionants obres d'art; o potser
simplement aplicar els primers auxilis a les vostres instantànies.
![](Rt_setm_editor.png "Rt_setm_editor.png") Preneu-vos un moment per
xafardejar aquesta pestanya d'edició principal. Observeu que hi ha
pestanyes dins d'aquesta pestanya; a la dreta de la pantalla cap a dalt.
Aquestes pestanyes i els controls que hi ha a sota són les caixes
d'eines. Potser teniu la primera pestanya oberta i, si passeu el ratolí
per sobre, veureu que s'anomena Pestanya d'exposició. A sota d'aquestes
pestanyes hi ha les eines que conté la pestanya seleccionada: Exposició,
Foscos/Clars intensos, Mapejat de tons, etc. Si feu clic en una d'elles
s'ampliarà i en podreu veure el contingut. Torneu a clicar-hi i es
reduirà. Feu-hi clic amb el botó dret i s'ampliarà alhora que la resta
es reduiran (una drecera força útil). A l'esquerra de l'etiqueta de cada
eina hi ha un botó d'encesa/apagat que us permet activar o desactivar
l'eina, o en alguns casos, enlloc del botó d'encesa/apagat hi ha un
triangle d'ampliació. Llegiu la secció «Eines» de l'article [Comentaris
generals sobre alguns ginys de la caixa
d'eines](General_Comments_About_Some_Toolbox_Widgets/ca#Eines.md)
per una explicació detallada. Navegueu per les pestanyes i quadres fins
que us sentiu totalment aclaparat per tot el que hi ha.

Abans que comenceu a treballar en una imatge, aquí teniu alguns consells
importants – **No patiu!** No hi ha cap perill que destruïu cap de les
vostres preuades imatges si cometeu un error. El RawTherapee té algunes
funcions que us ajudaran a protegir les vostres fotos:

- El RawTherapee edita els fitxers raw de forma no destructiva. Això vol
  dir que el RawTherapee no modificarà absolutament mai el propi fitxer
  raw. Tots els canvis es desen en fitxers laterals. Podeu trobar més
  informació d'aquests fitxers a l'article [Fitxers laterals - Perfils
  de processament](Sidecar_Files_-_Processing_Profiles/ca.md)
- Quan utilitzeu l'Editor d'imatges veureu el quadre
  [Historial](the_image_editor_tab/ca#historial) a
  l'esquerra. Aquest quadre us mostra una pila de tots els canvis que
  heu anat fent a la imatge. Per tornar enrere a qualsevol pas (incloent
  el moment en què s'ha obert la imatge per primera vegada), feu clic a
  la línia en qüestió del quadre d'Historial.
- A sota el quadre d'Historial veureu un quadre
  d'[Instantànies](the_image_editor_tab/ca#instantànies).
  Podeu ignorar-lo per ara, però el trobareu molt útil quan aneu
  adquirint experiència amb el RawTherapee. Aquest quadre desa l'estat
  de totes les eines com una «instantània». Això us permet, d'una forma
  fàcil, per exemple, retocar la vostra foto fins que tingui un aspecte
  bonic i acolorit, prendre'n una instantània, tornar-la a retocar per
  obtenir un agradable aspecte blanc i negre i prendre'n una altra
  instantània; llavors podeu comparar les dues versions de la imatge
  fent clic a cada instantània. (Nota: el RawTherapee encara no desa les
  instantànies als fitxers PP3, ho farà en un futur. Si teniu tres
  instantànies que voleu mantenir, haureu de fer-hi clic i desar un
  fitxer PP3 per a cadascuna amb un nom únic.)
- Com podeu esperar, Control+Z desfà l'últim canvi. (D'acord, no és
  tecnologia punta però segueix sent útil!)

### Aspectes bàsics

1.  Comenceu fent clic a la
    ![<File:Colour.png>](Colour.png "File:Colour.png") Pestanya Color i
    amplieu l'eina [Balanç de blancs](white_balance/ca)
    fent-hi clic amb el botó dret. El RawTherapee comença amb el balanç
    de blancs utilitzat per la vostra càmera. La major part dels ajustos
    de balanç de blancs es fan movent els controls de Temperatura i
    Tint, o utilitzant el
    ![<File:Gtk-color-picker.png>](Gtk-color-picker.png "File:Gtk-color-picker.png")
    Selector puntual de Balanç de blancs en un pedaç sense color (gris
    neutre). Toqueu-los per provar.
2.  Després, modifiqueu l'exposició anant a la
    ![<File:Exposure.png>](Exposure.png "File:Exposure.png") Pestanya
    Exposició, ampliant l'eina [Exposició](exposure/ca) i
    ajustant-la al vostre gust. Per ara, utilitzeu només els controls de
    Compensació d'exposició i Saturació.
3.  Si la vostra imatge té soroll, canvieu a la
    ![<File:Detail.png>](Detail.png "File:Detail.png") Pestanya Detall,
    amplieu a 100% ja sigui utilitzant el botó
    ![<File:Gtk-zoom-100.png>](Gtk-zoom-100.png "File:Gtk-zoom-100.png")
    o la drecera de teclat «z», perquè els efectes de les eines
    d'aquesta pestanya només es veuen en una previsualització ampliada
    al 100% (i evidentment en la imatge desada), i activeu l'eina
    [Reducció de soroll](noise_reduction/ca) utilitzant, per
    ara, els paràmetres per defecte. El RawTherapee ha eliminat
    automàticament el soroll de color (crominància). El soroll de
    luminància s'elimina [manualment](noise_reduction/ca#ús),
    així que de moment deixeu-lo, ja que el soroll de luminància
    normalment ofereix un aspecte granulat, com de pel·lícula, força
    agradable. Com a norma general, quan utilitzeu la reducció de soroll
    no utilitzeu l'enfocament. Reduïu l'ampliació per veure la imatge
    sencera, ja sigui utilitzant el botó
    ![<File:Gtk-zoom-fit.png>](Gtk-zoom-fit.png "File:Gtk-zoom-fit.png")
    o la drecera de teclat «f».
4.  Ara heu decidit que voleu arreglar la
    [geometria](lent/geometria) i composició de la vostra
    foto.
    - Primer anivelleu l'horitzó, o corregiu les coses que haurien de
      ser verticals, com fanals o parets d'edificis. Per fer-ho
      fàcilment, premeu la tecla «s» del teclat (el mateix que fer clic
      al botó
      ![<File:Straighten.png>](Straighten.png "File:Straighten.png")), i
      feu clic i arrossegueu la línia seguint l'horitzó o seguint el
      límit d'un edifici, sobre la previsualització. La imatge girarà
      d'acord amb la línia marcada i se us obrirà automàticament la
      ![<File:Transform.png>](Transform.png "File:Transform.png")
      Pestanya Transformació.
    - Per escapçar la foto, premeu la drecera de teclat «c» (o utilitzeu
      el botó ![<File:Crop.png>](Crop.png "File:Crop.png")) i feu clic i
      arrossegueu la zona que voleu escapçar sobre la previsualització;
      veureu que l'eina [Escapçat](crop/ca) s'activa
      automàticament. No és necessari «aplicar» un escapçat; té efecte
      tan bon punt el dibuixeu. Potser voleu establir el «Tipus de guia»
      d'escapçat a «cap» si és un problema.
    - Finalment, voleu reduir la mida de la foto, perquè qui vol
      carregar un fitxer JPEG de 10Mb a les xarxes socials? Activeu
      l'eina [Redimensiona](resize/ca) i deixeu-la en els
      paràmetres per defecte. Veureu que l'efecte de redimensionar només
      s'aplica a la imatge desada, no a la previsualització.
    - Ja esteu, anem a [desar-la](saving/ca) de seguida. Feu
      clic al botó
      ![<File:Gtk-save-large.png>](Gtk-save-large.png "File:Gtk-save-large.png")
      Desa la imatge actual, o utilitzeu la drecera de teclat Ctrl+s.
      Deseu-la com fitxer JPG, amb qualitat «92», submostratge a
      «balancejat». Aquesta és una configuració completa. Trieu la
      carpeta on voleu desar-la, i en uns segons el vostre fitxer estarà
      a punt a la carpeta que hagueu seleccionat. Si tanqueu el
      RawTherapee, la configuració que heu utilitzat es desarà al
      [fitxer lateral
      PP3](Sidecar_Files_-_Processing_Profiles/ca.md) al costat
      del fitxer raw, així que podeu tornar-lo a obrir més endavant i
      mantenir els paràmetres de les eines que heu utilitzat.

Ara que ja heu passat per uns ajustaments fotogràfics bàsics i que us
heu familiaritzat amb aquests passos, recapitulem els passos però amb
detalls més avançats.

### Aspectes avançats

Llegiu sempre l'article de cada eina aquí a la RawPedia abans
d'utilitzar-la, per entendre clarament el que fa. Els articles expliquen
com funcionen les eines al RawTherapee, mentre que els conceptes
generals no específics del RawTherapee es deixen a mercè que l'usuari
els trobi a la Viquipèdia o en altres llocs.

Assegureu-vos de mirar les [Dreceres de
teclat](Keyboard_Shortcuts/ca.md).

L'ordre de les eines dins el canal de procés del motor del RawTherapee
està programat internament, de manera que, des d'aquest punt de vista,
és igual quan activeu o desactiveu una eina. De tota manera algunes
eines poden tenir un gran impacte en d'altres eines, per exemple canviar
l'exposició pot requerir que hagueu de tornar a ajustar la coloració, i
algunes eines poden demanar un ús elevat del processador per calcular la
previsualització fent que les actualitzacions d'aquesta siguin llavors
molt lentes, així que és per aquest motiu que suggerim aquest ordre
d'operacions:

1.  Comenceu per assegurar-vos que l'entorn del RawTherapee està
    correctament configurat, és a dir:
    - Assegureu-vos que el RawTherapee utilitza el perfil de color del
      vostre monitor si utilitzeu un flux de treball amb gestió de
      color. Comproveu-ho a Preferències \> Gestió del color. Potser
      també caldrà que carregueu les corbes de calibració apropiades a
      la vostra targeta gràfica si heu construit el perfil de color del
      monitor a sobre d'ella; com ho heu de fer ja es troba fora de
      l'abast del RawTherapee.
    - Comproveu que l'eina de Gestió del color està configurada
      correctament. Normalment els paràmetres per defecte són els
      millors. Llegiu els articles [Gestió del
      color](Color_Management/ca.md) i [Complement de gestió del
      color](Color_Management_addon/ca.md). Si enlloc
      d'utilitzar la matriu de color o els perfils DCP o ICC inclosos al
      RawTherapee decidiu utilitzar-ne un d'extern, per exemple un DCP
      fet a mida o un d'Adobe, carregueu abans de fer cap altra cosa, si
      no és probable que hagueu de tornar a ajustar algunes de les eines
      de color. Utilitzeu sempre un perfil de sortida; en la majoria
      dels casos el que hi ha per defecte, RT_sRGB. Si us creieu llestos
      seleccionant "Sense ICM: Sortida sRGB", esteu equivocat.
2.  Si voleu utilitzar una imatge de [Camp
    pla](Flat_Field/ca.md) i/o [Marc
    fosc](Dark_Frame.md), feu-ho ara, per evitar haver de tornar
    a ajustar paràmetres.
3.  Ara establiu el [Balanç de blancs](white_balance/ca)
    correcte. Podeu ajustar l'exposició abans si la imatge és massa
    fosca (o massa brillant) per veure els canvis en el balanç de
    blancs.
4.  A continuació, ajusteu l'[Exposició](exposure/ca),
    utilitzant els controls de Compensació d'exposició i de Negre per
    aconseguir que la imatge tingui l'aproximació correcta. Un cop la
    tingui, continueu amb les dues corbes de to. Assegureu-vos de llegir
    la secció [Corbes de to](exposure/ca#corbes_de_to) a
    l'article d'Exposició per aprendre perquè n'hi ha dues i quina és la
    millor manera d'utilitzar-les; són una eina molt útil!
5.  A la secció Aspectes bàsics d'aquí sobre us hem suggerit que
    utilitzeu el control de
    [Saturació](exposure/ca#saturació) (a l'eina
    d'Exposició). Ara que ja heu après els aspectes bàsics i esteu
    explorant tècniques més avançades, us suggerim que ja no utilitzeu
    més el control de Saturació, i que en el seu lloc utilitzeu la
    [Corba CC](lab_adjustments/ca#corba_cc) de l'eina
    [Ajustaments Lab](lab_adjustments/ca), molt més potent i
    que us ofereix un control més fi.
6.  L'ordre del que queda no és clar. Algunes eines influenciaran
    inevitablement a les altres. Seguiu amb l'eina [Ajustaments
    Lab](Lab_Adjustments/ca.md) i després la resta de les eines
    de la Pestanya Exposició.
7.  Després utilitzeu l'eina [Wavelet](wavelet) a la
    ![<File:wavelet.png>](wavelet.png "File:wavelet.png") Pestanya
    Wavelet.
8.  A continuació utilitzeu les eines de la
    ![<File:Colour.png>](Colour.png "File:Colour.png") Pestanya Color.
    L'eina de [Coloració](color_toning) específicament és
    molt sensible als canvis d'exposició, millor que la deixeu pel
    final.
9.  Després amplieu al 100% i utilitzeu les eines a la
    ![<File:Detail.png>](Detail.png "File:Detail.png") Pestanya Detall.
    Per norma general, no utilitzeu l'Enfocament si esteu utilitzant la
    Reducció de soroll.
10. Finalment, reduïu l'ampliació de nou i utilitzeu les eines de la
    ![<File:Transform.png>](Transform.png "File:Transform.png") Pestanya
    Transformació. La raó de deixar això pel final és que pot provocar
    que la imatge de previsualització aparegui borrosa, ja que perquè la
    previsualització respongui correctament, el RawTherapee utilitza
    aquesta imatge de previsualització que veieu a la resolució que
    veieu (petita) per mostrar el que fan les eines, i quan gireu o
    canvieu la geometria d'una petita imatge, hi ha un suavitzat clar.
    Això no és cap problema quan deseu la imatge, ja que en aquest punt
    el RawTherapee fa el seu processament amb la imatge a mida completa,
    que és més lent però d'alta qualitat.
11. Deseu, ja sigui directament quan vulgueu desar només una foto, o a
    través de la [Cua de lots](the_batch_queue/ca) quan
    vulgueu processar moltes fotos.

Podeu editar les metadades a la
![<File:Meta.png>](Meta.png "File:Meta.png") Pestanya Meta en qualsevol
moment. Per què els canvis que feu a la pestanya Meta tinguin efecte a
la imatge desada, comproveu que la opció «Preferències \> Processament
d'imatge \> Còpia Exif/IPTC/XMP sense canvis al fitxer de sortida» no
està marcada. Si està marcada, els canvis que feu a la pestanya Meta
s'ignoraran a la imatge desada.
