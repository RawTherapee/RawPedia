---
title: Queue
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

La cola de procesamiento

</div>

## Introducción

Las imágenes se pueden [guardar](saving_images/es) de dos
maneras: puedes guardarlas inmediatamente
![<File:Save.png>](Save.png "File:Save.png") en la pestaña del *Editor*,
o añadirlas a la *cola de procesamiento por lotes*
![<File:Gears.png>](Gears.png "File:Gears.png"), que reside en la
pestaña *Cola*.

Si usas la opción *Guardar inmediatamente* RawTherapee se pondrá
inmediatamente a trabajar y como resultado, abrir y ajustar otras
imágenes en el *Editor* se realizará con cierta lentitud mientras la
imagen se esté guardando.

Por otro lado, el mecanismo de la *cola* te permite enviar imágenes
editadas y listas para ser guardadas a una cola virtual que puedes
arrancar en un momento posterior para que RawTherapee las procese. La
adición de las imágenes a la cola es instantánea, por lo que puedes
continuar editando otras imágenes sin ralentizaciones. Cuando hayas
acabado la edición y hayas puesto las imágenes en la cola, puedes
conmutar el interruptor
![<File:Queue_off.jpg>](Queue_off.jpg "File:Queue_off.jpg")
(desactivado) a ![<File:Queue_on.jpg>](Queue_on.jpg "File:Queue_on.jpg")
(activado) y dejar trabajar a RawTherapee.

Además, la cola es persistente: puedes salir de RawTherapee, volver a
arrancarlo más tarde y las imágenes situadas en la cola seguirán allí.
La cola puede incluso sobrevivir a un *«cuelgue»* del programa.

## Adición de imágenes a la cola

Hay tres maneras de añadir una imagen a la *cola*:

1.  Cuando hayas terminado de ajustar una imagen en el Editor, pulsa el
    botón ***Añadir imagen actual a la cola de procesamiento***
    (![<File:Gears.png>](Gears.png "File:Gears.png")).
2.  Pulsa el botón *Guardar imagen actual*
    (![<File:Save.png>](Save.png "File:Save.png")), ubicado también en
    la pestaña Editor, y selecciona ***Poner al principio/final de la
    cola de procesamiento***.
3.  Pulsa el botón derecho del ratón sobre una miniatura en el
    [*Explorador de archivos*](file_browser/es) o en la
    [*tira de imágenes*](editor/es#the_filmstrip) y
    selecciona ***Poner en la cola***. En este caso puedes haber
    seleccionado una sola imagen o varias (para enviarlas todas a la vez
    a la *cola*.

Independientemente del método que uses, cuando accedas a la pestaña
*Cola* verás tus fotos alineadas y listas para procesar. Aunque si
tenías la cola configurada para *Inicio automático*, es posible que el
programa haya terminado de procesar todas las imágenes antes de que
llegues a ver la cola.

## Ajustes de la cola

La cola tiene varios ajustes: el ***arranque automático***, el
***destino del archivo de salida**'' y el***formato**''.

### Arranque automático de la cola

Esta opción te permite decidir si al añadir las fotos a la cola se
procesarán inmediatemente, o bien se añadirán a la cola y el programa
esperará a que actives la ejecución manualmente.

### Carpeta de Destino de las imágenes

La carpeta de destino la puedes elegir directamente en el cuadro de
diálogo [*Guardar inmediatamente*](saving_images/es), aunque
en la pestaña *Cola* puedes crear dinámicamente la carpeta de destino y
el nombre del archivo gracias a la opción *Usar plantilla*, que
especifica el destino de la imagen exportada en función de la ubicación,
puntuación, estado de la papelera o posición en la cola de la imagen de
partida.

Supongamos que tenemos una imagen raw en:
**`/home/tom/photos/2010-10-31/photo1.raw`**

RawTherapee lo *«traduce»* internamente como: **`/%d4/%d3/%d2/%d1/%f`**

Siendo el significado de estos códigos para el formateo el siguiente:

<div class="coding-withstyle">

**%d4** = **home** *(el cuarto nivel de directorio por encima del lugar
donde esté el archivo raw)*

**%d3** = **tom** *(el tercer nivel de directorio por encima del lugar
donde esté el archivo raw)*

**%d2** = **photos** *(el segundo nivel de directorio por encima del
lugar donde esté el archivo raw)*

**%d1** = **2010-10-31** *(el primer nivel de directorio por encima del
lugar donde esté el archivo raw, o lo que es lo mismo, la carpeta donde
está el archivo raw)*

**%f** = **photo1** *(es el nombre del archivo raw, que se tomará como
plantilla para nombrar la imagen exportada)*

</div>

La profundidad máxima de la plantilla es hasta 9 niveles, es decir,
hasta **`%d9`**.

Los códigos anteriores están separados por *«la barra de directorio»*
(`/` o `\`, es indiferente), así que para no tener que escribir tantos
códigos y ahorrarnos añadir las barras de directorio, RawTherapee
también tiene atajos:

<div class="coding-withstyle">

**%p1** = /home/tom/photos/2010-10-31/ = **%d4+%d3+%d2+%d1** *(la ruta
completa de la carpeta donde está el archivo raw)*

**%p2** = /home/tom/photos/ = **%d4+%d3+%d2** *(la ruta desde el
directorio raíz hasta la carpeta **%d2**)*

**%p3** = /home/tom/ = **%d4+%d3**

**%p4** = /home/ = **%d4**

</div>

Y además tienes a tu disposición estos otros códigos:

<div class="coding-withstyle">

**%r**: se substituirá por la puntuación de la foto. Si la foto no tiene
puntuación, se usará *0*. Si la foto está en la papelera, se usará *x*.

**%s1, ..., %s9**: se substituirán por la posición inicial de la foto en
la cola en el momento del arranque de ésta. El número especifica la
cantidad de dígitos que se usarán en los números; por ejemplo, **%s3**
dará como resultado *007* en la séptima foto de la cola.

</div>

Así pues, si quieres guardar la imagen exportada:

- junto con la imagen de partida, escribe: **`%p1/%f`**
- igual que antes pero con un texto anexado al nombre del archivo raw,
  escribe: **`%p1/%f_texto_añadido`**
- en una carpeta llamada *exportadas*, situada dentro de la carpeta de
  la imagen raw, escribe: **`%p1/exportadas/%f`**
- en **`/home/tom/photos/exportadas/2010-10-31`** (una carpeta aparte
  con la misma estructura de fechas original), escribe:
  **`%p2/exportadas/%d1/%f`**
- en una carpeta en concreto, con el nombre del archivo raw, escribe:
  **`/ruta/hasta/las/imagenes/exportadas/%f`** (en Linux), o
  **`c:/ruta/hasta/las/imagenes/exportadas/%f`** (en Windows; da igual
  qué tipo de barra escribas)

### Formato de los archivos

Estos ajustes especifican las opciones propias de cada formato de
archivo y tienen efecto en todas las imágenes de la cola, excepto cuando
uses *Guardar imagen actual*
![<File:Save.png>](Save.png "File:Save.png"), selecciones *Poner al
principio/final de la cola de procesamiento* y actives la casilla
***Forzar las opciones de guardado***. En este caso se utilizarán los
ajustes establecidos en este cuadro de diálogo y se ignorarán los de la
pestaña *Cola*.

***Guardar los parámetros de procesamiento con la imagen*** guardará el
perfil de procesamiento junto con el archivo de salida. Esto es útil
cuando deseas guardar varias copias de la misma foto, cada una de ellas
con ajustes un poco diferentes.

## Ejecución de la cola

En la esquina superior izquierda de la pestaña Cola encontrarás un
interruptor
(![<File:Queue_off.jpg>](Queue_off.jpg "File:Queue_off.jpg")) y una
opción de *Arranque automático*:

1.  Si está activado *Arranque automático*, el procesado se iniciará tan
    pronto como se envíe una imagen a la cola. Normalmente no querrás
    que ocurra esto, ya que hacerlo RawTherapee usará la CPU para
    procesar las fotos de la cola, dejando muy poco tiempo de CPU para
    responder mientras ajustas otras fotos.
2.  Si no está activado *Arranque automático*, tendrás que arrancar la
    cola manualmente, accionando el interruptor
    (![<File:Queue_off.jpg>](Queue_off.jpg "File:Queue_off.jpg")).

Puedes pausar la cola accionando el interruptor
![<File:Queue_on.jpg>](Queue_on.jpg "File:Queue_on.jpg"): RawTherapee
terminará primero el procesado de la imagen actual antes de pausar la
cola.

## Vaciado de la cola

Puedes quitar una imagen específica de la cola pulsando el pequeño botón
***Cancelar trabajo***
![<File:Cancel-small.png>](Cancel-small.png "File:Cancel-small.png") en
la esquina de cada miniatura.

También puedes vaciar la cola completamente pulsando el botón derecho
del ratón sobre una miniatura, seleccionando *Seleccionar todo* y
después *Cancelar trabajo*; o usando el atajo de teclado  + para
seleccionar todas las miniaturas y a continuación pulsar la tecla del
teclado.
