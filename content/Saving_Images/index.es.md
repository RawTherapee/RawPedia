---
title: Saving Images
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Guardar imágenes

</div>
<div class="headline">

RawTherapee nunca alterará tu archivo raw original

</div>

## Guardar (exportar) las imágenes

Cuando estás contento con el procesado de tu imagen puedes *exportarla*,
o como se dice en RawTherapee, simplemente *guardarla*. Aunque en
realidad lo que harás será generar una nueva imagen a la que se le
aplicará todo el procesado: **la imagen raw no se modifica en ningún
momento**.

Hay un par de maneras de *guardar* una imagen desde la pestaña del
[*Editor*](the_image_editor_tab/es):

- ![<File:Save.png>](Save.png "File:Save.png") ***Guardar
  inmediatamente*** desde la pestaña *Editor*,
- ![<File:Gears.png>](Gears.png "File:Gears.png") ***Guardar usando la
  [Cola](queue/es)***,

### Guardar inmediatamente

![](Saveas_immediately.jpg "Saveas_immediately.jpg")En la pestaña
*Editor*, si pulsas en el botón del disquete
![<File:Save.png>](Save.png "File:Save.png") en la parte inferior
izquierda del área de previsualización, o usas el atajo de teclado  + ,
RawTherapee te ofrecerá por defecto la opción de ***Guardar
inmediatamente*** tu imagen.

El funcionamiento es como en un cuadro de diálogo estándar *Guardar
como*: puedes seleccionar el nombre y la ubicación y el formato del
archivo de salida (RawTherapee añadirá automáticamente la extensión,
basándose en el formato elegido) y asímismo las opciones propias de cada
formato. También puedes decidir si quieres que se guarde el perfil de
procesamiento junto con la imagen de salida y si el programa debe añadir
un sufijo al nombre cuando ya haya uno igual en el disco.

Puesto que *Guardar inmediatamente* implica procesar completamente la
foto antes de grabarla en el disco, RawTherapee responderá más
lentamente a cualquier ajuste u operación que puedas tratar de hacer
mientras está ocupado guardando. Por ello tienes la opción de poner el
archivo ***al principio/final de la cola de procesamiento***.

![](Saveas_toqueue.jpg "Saveas_toqueue.jpg")En estos casos, verás que se
activa una opción extra: ***Forzar las opciones de guardado***, que
obliga al programa a utilizar las opciones de tipo de archivo y sus
características especificados en este cuadro de diálogo, en lugar de
utilizar las opciones especificadas en la pestaña de [*la cola de
procesamiento*](Queue/es#Ajustes_de_la_cola.md).

Por omisión en este cuadro de diálogo estará seleccionada la carpeta
donde guardaste la última imagen que exportaste, pero para tu comodidad,
se añade automáticamente un atajo a la carpeta que contiene la imagen
original en el panel de favoritos (a la izquierda del cuadro de
diálogo). Si quieres guardar la imagen en la carpeta donde está el
original, pulsar sobre este favorito te ahorrará tener que navegar
manualmente hasta esa ubicación.

\+ es un atajo para el botón *Aceptar*.

### Poner a la cola de procesamiento

Mientras estés en el *Editor*, si pulsas sobre el icono de los
engranajes [<file:gears.png>](file:gears.png) o seleccionas
*Poner al principio/final de la cola de procesamiento* en el cuadro de
diálogo *Guardar*, tu imagen se situará en la [cola de archivos
pendientes de procesar](Queue/es.md).

Igualmente, si estás en el *Navegador de archivos* puedes hacer clic
derecho y en el menú contextual seleccionar *Poner en la cola*.

En cualquier caso, si has enviado las fotos a la cola simplemente
*poniéndolas en la cola*, RawTherapee las procesará con los ajustes
especificados en la pestaña *Cola*. Por otro lado, si has activado la
opción de *Forzar las opciones de guardado*, el programa usará las
opciones del cuadro de diálogo, ignorando los ajustes de la pestaña
*Cola*.

## Cómo se nombran los archivos

Si tu archivo raw original se llamaba `photo_1000.raw`, el nombre del
archivo exportado será `photo_1000.jpg` (o `.tif`, o `.png`). Es decir,
el mismo nombre con la extensión apropiada.

Si has guardado el [perfil de
procesamiento](Queue/es#Ajustes_de_la_cola.md) junto a la
imagen, este archivo tendrá el mismo nombre que el archivo exportado,
más una extensión extra `.pp3` (por ej. `photo_1000.jpg.pp3`).

Por defecto, si al darle nombre a un archivo ese nombre ya existe, se
añadirá un número extra al final del nombre: si el archivo
`photo_1000.jpg` ya existiera, el nuevo archivo sería renombrado a
`photo_1000-1.jpg`. Si este último también existiera, sería renombrado a
`photo_1000-2.jpg`. Y así sucesivamente.

En cuanto a los archivos de los *perfiles de procesamiento*, siguen
teniendo el mismo nombre base que la imagen, así que tendríamos:
`photo_1000-1.jpg.pp3`, `photo_1000-2.jpg.pp3`, etc.

Por último, si en el cuadro de diálogo *Guardar imagen actual*
desactivas *Añadir automáticamente un sufijo cuando el archivo ya
existe*, el programa sobreescribirá la imagen existente.
