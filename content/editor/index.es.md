---
title: Editor
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

El Editor

</div>
<div class="headline">

El lugar donde revelarás tus fotos

</div>

## Introducción

<figure>
<img src="/images/Rt_setm_editor.png" title="Rt_setm_editor.png" />
<figcaption>Rt_setm_editor.png</figcaption>
</figure>

**La pestaña *Editor de imágenes* es el lugar donde retocas tus fotos**
y presenta las siguientes zonas:

<div class="tlist">

\[\[<File:Rt_setm_editor_areas.jpg%7Cframe%7Cright%7CLas> diferentes
áreas en el Editor:  

<div class="captions_indent">

**1. Las Barras de herramientas** de la vista previa  
**2. La Vista Previa**  
**3. El Historial y las Instantáneas**  
**4. El Navegador**  
**5. El Análisis de la Imagen**  
**6. Las Miniaturas**  
**7. Los Perfiles de Procesamiento**  
**8. Las herramientas**

</div>

\]\]

</div>

1.  **las Barras de herramientas** de la *Vista Previa*: que te permiten
    realizar tareas específicas, tienen botones de acceso directo a
    algunas herramientas de edición y es donde encontrarás botones para
    tareas más genéricas (maximizar la ventana, guardar la imagen,
    mostrar la imagen en un programa externo, ocultar/mostrar paneles,
    ...)
2.  **la Vista Previa**: es el área principal y en ella verás una
    previsualización del estado actual de tu foto con todas las
    modificaciones realizadas por las herramientas que hayas usado
3.  **el Historial y las Instantáneas**: en el historial verás los pasos
    que has ido dando a la hora de editar la imagen y con las
    instantáneas podrás guardar el procesado que hayas hecho hasta el
    momento de crear la instantánea
4.  **el Navegador**: donde puedes ver una versión reducida de la foto
    con un marco que te indica qué se está mostrando en la *Vista
    Previa*. Además, debajo de esta mini-imagen podrás ver los valores
    RGB, HSV y L\*a\*b\* del píxel que hay debajo del cursor (donde
    estás *«apuntando»* con el ratón)
5.  **el Análisis de la Imagen**: área que en la versión 5.9 puede
    mostrar un *histograma* clásico, un gráfico en forma de ondas
    (*análisis en forma de ondas*, *AFO*, o *«waveform»*), en forma de
    galería (*AFO por canales*, o *«parade»*), o un vectorscopio
    (*«vectorscope»*)
6.  **las Miniaturas**: una tira de contactos que muestra en un carrusel
    las imágenes presentes en la carpeta seleccionada
7.  **los Perfiles de Procesamiento**: donde puedes cargar o guardar
    perfiles de procesamiento incluídos en RawTherapee, o creados por tí
    mismo
8.  **las herramientas**: que te permitirán revelar y ajustar las
    imágenes a tu gusto

## ¡Mi foto raw no es igual que el JPEG de la cámara!

Recién instalado el programa esto no debería ocurrir, pero es posible
que cuando abras una foto raw en el Editor veas que su aspecto es
diferente al JPEG de tu cámara. Y también a menudo será peor (más
oscura, menos nítida, más apagada, con poco contraste, con más ruido,
...) que la misma foto raw abierta con otros programas.

A continuación te explicaremos los motivos de esta discrepancia, pero
por el momento puedes probar si consigues ese aspecto que deseas
haciendo clic en el botón de la [*Curva de Tonos
Auto-Ajustada*](Auto-Matched_Curve/es.md) y/o activando la
[*Curva de Tonos del perfil
DCP*](Color_Management/es#A_medida.md) (si la tiene).

La foto JPEG de tu cámara es distinta a la foto recién cargada en
RawTherapee porque:

- por algún motivo no se ha cargado ninguno de los [perfiles de
  procesamiento](Sidecar_Files_-_Processing_Profiles/es.md) que
  incluyen la *Curva de Tonos Auto-Ajustada*, o se ha cargado el perfil
  de procesamiento *Neutro*: tras instalar RawTherapee, el perfil de
  procesamiento predeterminado para procesar fotos raw es
  ***«Auto-Matched Curve - ISO Low»*** (*Curva de Tonos Auto-Ajustada,
  con sensibilidad ISO baja*). También se incluyen los perfiles
  ***«Auto-Matched Curve - ISO Medium»*** (*Curva de Tonos
  Auto-Ajustada, con sensibilidad ISO media*) y ***«Auto-Matched Curve -
  ISO High»*** (*Curva de Tonos Auto-Ajustada, con sensibilidad ISO
  alta*), que se han diseñado para ofrecer un buen punto de partida para
  fotos con ruido moderado y alto, respectivamente.
- el perfil DCP no tiene *Curva de Tonos*: si hubieras aplicado el
  perfil de procesamiento *Neutro* y al mismo tiempo activado la *Curva
  de Tonos* del perfil de entrada, pero la imagen todavía no se parece
  al JPEG de la cámara, puede que el perfil DCP esté alterado (que no
  funcione bien) o que la *Curva de Tonos* de ese perfil no se ajuste al
  procesado que realiza la cámara.
- la cámara realiza muchos procesos en la imagen raw antes de
  presentártela junto con el histograma en la pantalla digital de tu
  cámara (incluso si pones todos los ajustes de procesado de tu cámara a
  sus valores neutros), así que lo que verás no será una imagen «pura» y
  sin procesar:
  - los procesos aplicados dependen del diseño de tu cámara, pero
    normalmente incluyen una curva de tono personalizada, un aumento de
    la saturación y la nitidez y una reducción del ruido
  - algunas cámaras (en particular las de gama baja y las de [sistema
    Micro Cuatro
    Tercios](https://es.wikipedia.org/wiki/Micro_Cuatro_Tercios)) pueden
    aplicar también correcciones de distorsión del objetivo, para
    corregir no solamente las [distorsiones «de barrilete» y «de
    cojín»](https://es.wikipedia.org/wiki/Aberración_en_sistemas_ópticos#Distorsión_de_la_lente),
    sino también para ocultar problemas graves de
    [viñeteado](https://es.wikipedia.org/wiki/Viñeteado)
  - la mayoría de cámaras también subexponen cada foto que tomas entre
    -0.3EV y -1.3EV (o más), a fin de obtener espacio para las *luces*:
    cuando tu cámara (u otro programa) procesa el archivo raw, aumenta
    la compensación de exposición en la misma cantidad, haciendo que el
    brillo parezca correcto y con la esperanza de recuperar algunas
    luces en el proceso.
- cada archivo raw contiene en su interior al menos una imagen JPEG
  procesada (algunos archivos raw contienen hasta tres imágenes JPEG que
  sólo difieren en su resolución): cuando abres archivos raw en otros
  programas, lo que normalmente ves **no son los datos raw**, sino la
  imagen JPEG procesada y embebida por la cámara.
- la mayoría de programas de revelado raw (programas que leen los datos
  raw reales en lugar de leer solamente el JPEG embebido) aplican a los
  datos raw algún mínimo procesamiento (como una curva base de tono)
  incluso con sus ajustes más neutros, lo que hace prácticamente
  imposible que el usuario vea el contenido real e intacto de sus fotos
  raw. *«Adobe Lightroom»* es un ejemplo. La comparación de la imagen
  neutra de RawTherapee con una cuasineutra de uno de estos programas
  mostrará las diferencias.

Por su lado, RawTherapee se ha diseñado para mostrarte la imagen raw
real en el área de previsualización, dejando que seas tú quien decida
cómo se procesarán esos datos. Y esto puede significar que tus fotos
aparezcan oscuras y con ruido, mientras que la cámara (u otros
programas) puede aumentar el brillo y aplicar una reducción de ruido sin
que lo sepas.

Sin embargo y tal como ya se ha dicho, si lo deseas puedes activar la
*Curva de Tono* del perfil DCP (si la tiene) y obtener un resultado
similar al *aspecto de tu cámara*, ya que se trata de la curva
predeterminada para película de Adobe Camera Raw. De esta forma tendrás
un punto de partida con colores vivaces (a diferencia del aspecto plano
que se obtiene con el perfil de procesamiento *Neutro*), sin tener que
usar [Niveles automáticos](exposure/es#auto_levels) y sin
tener que tocar ninguna de las demás herramientas.

Algunos ejemplos de programas que son incapaces de mostrar (o que no los
muestran con sus ajustes predeterminados) los datos raw reales son,
entre otros: [IrfanView](https://es.wikipedia.org/wiki/IrfanView),
[XnView](https://es.wikipedia.org/wiki/XnView),
[Gwenview](https://es.wikipedia.org/wiki/Gwenview),
[Geeqie](http://en.wikipedia.org/wiki/Geeqie), [Eye of
GNOME](https://es.wikipedia.org/wiki/Eye_of_GNOME),
[F-Spot](https://es.wikipedia.org/wiki/F-Spot),
[Shotwell](https://es.wikipedia.org/wiki/Shotwell),
[gThumb](https://es.wikipedia.org/wiki/GThumb), etc. Vale la pena
mencionar en este momento que si disparas en modo ***RAW+JPEG***, a no
ser que personalices los ajustes de la imagen JPEG generada, en realidad
estás desperdiciando espacio en disco y no obteniendo nada a cambio, ya
que tus archivos raw ya contienen los archivos JPG embebidos.

## Las distintas zonas del Editor

### La Vista Previa

La zona central muestra una previsualización de tu foto generada a
partir de los datos raw, procesándolos para empezar con los ajustes del
[perfil de
procesamiento](Sidecar_Files_-_Processing_Profiles/es.md) usado
en el momento de abrir la foto (especificado en ***Preferencias \>
Procesamiento de imágenes \> Parámetros de procesamiento de imágenes
predeterminados***) y después con el resto de ajustes que hagas
manualmente.

La previsualización te mostrará el efecto de todos los ajustes que
hagas, aunque los efectos de algunas herramientas sólo serán visibles
cuando amplíes la imagen a escala ***1:1*** (100%) o mayor, lo cual se
indica en la interfaz con el icono ![Zoom
1:1](One-to-one-small.png "Zoom 1:1") junto al nombre de la herramienta.

Sin embargo, lo que veas en la *Vista Previa* será prácticamente lo
mismo pero no será exactamente la imagen final, debido a cómo está
programado RawTherapee: para acelerar la respuesta del programa y que no
sea demasiado lento al inicio del [circuito de
revelado](Toolchain_Pipeline/es.md) el motor del programa saca
una «instantánea» de los datos raw y es sobre esa instantánea sobre la
que se realizan todos los cambios que ves en la *Vista Previa*. Para ver
la imagen exactamente como será al exportarla, debes hacer clic en el
botón de [*editar la imagen actual en un programa
externo*](#editar_la_imagen_actual_en_un_programa_externo.md)
(<img src="/images/palette-brush.png" title="palette-brush.png" height="26"
alt="palette-brush.png" />).

Además, la actualización del estado de la foto no se realiza
instantáneamente para evitar hacer cálculos innecesarios mientras estás
ajustando las opciones (con un deslizador, por ejemplo): RawTherapee
espera un poco para asegurarse que has acabado de ajustar alguna cosa y
después actualiza la *Vista Previa*. Para definir cuánto tiempo espera,
en el archivo `options` (dentro de [la carpeta
***config***](File_Paths/es#La_carpeta_con_las_configuraciones.md))
existen dos parámetros que puedes ajustar a tu gusto:

- `AdjusterMinDelay`, con un valor predeterminado de *100ms*: se utiliza
  para herramientas con un tiempo de respuesta muy rápido, por ejemplo
  el deslizador de *Compensación de exposición*.
- `AdjusterMaxDelay`, con un valor predeterminado de *200ms*: se utiliza
  para herramientas con un tiempo de respuesta lento, por ejemplo los
  deslizadores de *CIECAM02/16*.

En cuanto a los colores de la imagen que ves en la *Vista Previa*, estos
se convierten desde el espacio de color del perfil de trabajo al espacio
de color del monitor (y si no se ha configurado en las *Preferencias*, a
sRGB). Pero no olvides que sólo se convierten para que puedas verlos
correctamente en tu pantalla, sin modificar la imagen que está
procesando el motor del programa. Dicho de otra forma: podrás exportar
la imagen en un espacio de color mayor al de tu pantalla, aunque los
colores que tu monitor no pueda mostrar los tendrás que imaginar.

En general la *Vista Previa* sólo muestra los colores con el perfil de
la pantalla, salvo cuando utilizas el botón de [*prueba de
impresión*](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md)
(<img src="/images/gamut-softproof.png" title="gamut-softproof.png" width="26"
alt="gamut-softproof.png" />), con el que se tienen en cuenta los
perfiles de salida y de impresión, según la combinación de botones y
ajustes.

### Las Barras de herramientas de la Vista Previa

Situadas encima y debajo de la *Vista Previa* hay dos barras de
herramientas con un buen número de botones que podrían no caber en
pantallas de baja resolución o si los paneles laterales son demasiado
anchos. Si la resolución de tu pantalla es demasiado baja algunos de los
elementos (botones o listas desplegables) pueden quedar ocultos. Para
verlos, simplemente sitúa el cursor del ratón sobre la barra de
herramientas y usa la rueda del ratón para desplazar el contenido de la
barra a izquierda o derecha. O también puedes ocultar uno o ambos
paneles laterales de manera que veas la barra entera.

Son muchas las tareas que puedes realizar con estos botones y por grupos
de izquierda a derecha y de arriba a abajo:

- <figure>
  <img src="/images/toolbar1.jpg" title="File:toolbar1.jpg" />
  <figcaption><a
  href="File:toolbar1.jpg">File:toolbar1.jpg</a></figcaption>
  </figure>

  
En ambas barras de herramientas encontrarás repartidos 3 botones que
ocultan
(<img src="/images/panel-to-left.png" title="panel-to-left.png" height="26"
alt="panel-to-left.png" /> botón activado, fondo negro) o despliegan
(<img src="/images/panel-to-right.png" title="panel-to-right.png" height="26"
alt="panel-to-right.png" /> botón desactivado, fondo gris) el panel
izquierdo, el panel derecho y la tira de contactos. Puedes usarlos o
utilizar sus respectivos atajos de teclado para gestionar el espacio que
queda para la [*Vista Previa*](#la_vista_previa).

<!-- -->

  
Con la mano (<img src="/images/hand-open.png" title="hand-open.png" height="26"
alt="hand-open.png" />) podrás desplazar la imagen de forma que puedas
ver la zona que quieras procesar, o los detalles que más interés tengan.
También puedes ver información básica sobre la imagen
(<img src="/images/info.png" title="info.png" height="26" alt="info.png" />),
cambiar el balance de blancos
(<img src="/images/color-picker.png" title="color-picker.png" height="26"
alt="color-picker.png" />), recortar la imagen
(<img src="/images/crop.png" title="crop.png" height="26" alt="crop.png" />),
enderezarla
(<img src="/images/rotate-straighten.png" title="rotate-straighten.png"
height="26" alt="rotate-straighten.png" />), hacer correcciones de
perspectiva (<img src="/images/perspective-vertical-bottom.png"
title="perspective-vertical-bottom.png" height="26"
alt="perspective-vertical-bottom.png" />) y todo esto tras haber
activado la *Vista Previa dual*
(<img src="/images/beforeafter.png" title="beforeafter.png" height="26"
alt="beforeafter.png" />), que mostrará la imagen antes (a la izquierda)
y después (a la derecha) de los últimos cambios en las herramientas, de
forma que puedas comparar la diferencia entre antes y después de las
modificaciones.

<!-- -->

  
Además, puedes añadir tantas *muestras de color*
(<img src="/images/color-picker-bars.png" title="color-picker-bars.png"
height="26" alt="color-picker-bars.png" />) en la imagen como necesites,
para poder ver los valores medios de cada grupo de píxeles muestreados:
en el círculo del icono de la muestra se verá el color promediado de los
píxeles seleccionados.

<!-- -->

  
Las siguientes operaciones con las *muestras de color* se realizarán
siempre con el botón
<img src="/images/color-picker-bars.png" title="color-picker-bars.png"
height="26" alt="color-picker-bars.png" /> seleccionado:

:\* para añadir una muestra, haz clic izquierdo
(<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" />) en la zona que te interese

:\* para mover la muestra a otra posición haz
<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" />, mantén pulsado y arrastra el ratón

:\* para borrar una muestra, sitúa el cursor sobre la muestra y haz clic
derecho (<img src="/images/mouse_right-click.png" title="mouse_right-click.png"
height="26" alt="mouse_right-click.png" />)

:\* para borrar todas las muestras, sitúa el cursor sobre una muestra y
haz  + <img src="/images/mouse_right-click.png" title="mouse_right-click.png"
height="26" alt="mouse_right-click.png" />

:\* para agrandar el área de muestreo, sitúa el cursor sobre la muestra
y haz  + <img src="/images/mouse_right-click.png" title="mouse_right-click.png"
height="26" alt="mouse_right-click.png" /> (hasta 5 veces)

:\* para disminuir el área de muestreo,  +
<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" /> (hasta 5 veces).

:\* los valores numéricos de las muestras podrán tener las mismas
unidades que se muestran en el [*Navegador*](#el_navegador) y
se actualizarán con cada cambio en los ajustes de las herramientas.
Además cada muestra podrá mostrar su propia unidad, independientemente
del resto de muestras: para seleccionar la que quieres que se muestre,
haz  +
<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" /> hasta que veas los valores RGB, HSV o
L\*a\*b\*

:\* si necesitas ver la imagen libre de puntos de muestreo, haz
<img src="/images/mouse_right-click.png" title="mouse_right-click.png"
height="26" alt="mouse_right-click.png" /> sobre el icono de *muestras
de color*
(<img src="/images/color-picker-bars.png" title="color-picker-bars.png"
height="26" alt="color-picker-bars.png" />) y este cambiará a modo
«inactivo»
(<img src="/images/color-picker-hide.png" title="color-picker-hide.png"
height="26" alt="color-picker-hide.png" />), ocultando (pero no
borrando) las muestras de la imagen. Haciendo clic derecho de nuevo
sobre el icono, las muestras volverán a aparecer donde las situaste

- <figure>
  <img src="/images/toolbar2a.jpg" title="File:toolbar2a.jpg" />
  <figcaption><a
  href="File:toolbar2a.jpg">File:toolbar2a.jpg</a></figcaption>
  </figure>

  
Los primeros cuatro botones te permiten seleccionar el color de fondo de
la *Vista Previa*
(<img src="/images/toolbar_background.jpg" title="toolbar_background.jpg"
height="26" alt="toolbar_background.jpg" />) para facilitar la
previsualización durante la edición y para ver mejor el recorte de la
imagen.

<!-- -->

  
Los modos posibles son:

<div class="grid-table-wrapper">

<table>
<thead>
<tr class="header">
<th class="tablegrid-caption"><p>El color de fondo de la Vista
Previa</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td role="columnheader"><p>Color de fondo</p></td>
</tr>
<tr class="even">
<td role="rowheader"><p>Basado en el tema<br />
de la interfaz</p></td>
</tr>
<tr class="odd">
<td role="rowheader"><p>Negro</p></td>
</tr>
<tr class="even">
<td role="rowheader"><p>Gris medio</p></td>
</tr>
<tr class="odd">
<td role="rowheader"><p>Blanco</p></td>
</tr>
</tbody>
</table>

</div>

  
  
Una vez que estés contento con el color de fondo también puedes
modificar la *Vista Previa* en sí misma
(<img src="/images/toolbar_channels.jpg" title="toolbar_channels.jpg" height="26"
alt="toolbar_channels.jpg" />), <span id="canales_de_color">mostrando
únicamente un canal de color</span> de la imagen, o el canal de
luminosidad. Sólo se puede mostrar un canal a la vez y la *Vista Previa*
vuelve al modo normal seleccionando de nuevo el canal activo.

<div class="grid-table-wrapper">

<table>
<thead>
<tr class="header">
<th class="tablegrid-caption"><p>Vista Previa de<br />
los canales de la imagen</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td role="columnheader"><p>Vista Previa</p></td>
</tr>
<tr class="even">
<td role="rowheader"><p>Vista Previa normal</p></td>
</tr>
<tr class="odd">
<td role="rowheader"><p>Canal Rojo</p></td>
</tr>
<tr class="even">
<td role="rowheader"><p>Canal Verde</p></td>
</tr>
<tr class="odd">
<td role="rowheader"><p>Canal Azul</p></td>
</tr>
<tr class="even">
<td role="rowheader"><p>Claridad (luminosidad)</p></td>
</tr>
</tbody>
</table>

</div>

  
  
Como es habitual en otros muchos programas, al activar un canal verás el
valor de ese canal en cada pixel, representado con un nivel de gris
tanto más claro cuanto más alto sea el valor: si en un rango de *0* a
*255* el valor del canal es *0*, se representará en la vista previa como
negro. Si es *255* se representará como blanco. Y un gris intermedio
para valores intermedios.

<figure>
<img src="/images/preview-ch_normal.jpg" title="preview-ch_normal.jpg" />
<figcaption>preview-ch_normal.jpg</figcaption>
</figure>

<div>

- <figure>
  <img src="/images/preview-r_red.jpg" title="preview-r_red.jpg" />
  <figcaption>preview-r_red.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/preview-g_green.jpg" title="preview-g_green.jpg" />
  <figcaption>preview-g_green.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/preview-b_blue.jpg" title="preview-b_blue.jpg" />
  <figcaption>preview-b_blue.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/preview-v_luminosity.jpg" title="preview-v_luminosity.jpg" />
  <figcaption>preview-v_luminosity.jpg</figcaption>
  </figure>

</div>

  
La *Vista Previa* de los canales individuales puede ser útil mientras se
editan las curvas RGB, al planificar la conversión a Blanco y Negro
usando el mezclador de canales, al evaluar el ruido de la imagen, para
ver qué canal puede estar recortado, etc.

- <figure>
  <img src="/images/toolbar2b.jpg" title="File:toolbar2b.jpg" />
  <figcaption><a
  href="File:toolbar2b.jpg">File:toolbar2b.jpg</a></figcaption>
  </figure>

  
La *Máscara de foco*
(<img src="/images/focusscreen-off.png" title="focusscreen-off.png" height="26"
alt="focusscreen-off.png" />) se ha diseñado para destacar zonas de la
imagen con buen contraste, ya que habitualmente las zonas enfocadas son
las que presentan detalles con mayor contraste.

<div class="tlist">

<figure>
<img src="/images/preview-focus.jpg" title="preview-focus.jpg" />
<figcaption>preview-focus.jpg</figcaption>
</figure>

</div>

  
Esta máscara es más precisa en imágenes con poca profundidad de campo,
ruido bajo y a niveles de ampliación altos, pero con imágenes ruidosas
evalúalas con niveles de ampliación entre el 10% y el 30%.

<!-- -->

  
Ten en cuenta que la previsualización se genera más lentamente con la
máscara de foco activada.

<div class="tlist tleft-list">

<figure>
<img src="/images/Preview_6_focus.jpg" title="Preview_6_focus.jpg" />
<figcaption>Preview_6_focus.jpg</figcaption>
</figure>

</div>

  
La implementación actual analiza la imagen de la *Vista Previa* tras
reescalar el tamaño original, lo cual reduce el ruido y ayuda a
identificar detalles realmente nítidos en lugar del ruido en sí. Al
mismo tiempo, el reescalado de la imagen comprime detalles de mayor
escala a un tamaño menor y puede introducir efectos de solapamiento
(*aliasing*).

<!-- -->

  
El proceso no siempre está libre de fallos y se pueden producir falsos
positivos o falsos negativos, aunque puedes aumentar la fiabilidad
viendo la máscara a varios niveles de ampliación. Sin embargo:
**Asegúrate de comprobar tus imágenes dos veces antes de decidir
borrarlas usando la máscara de foco como criterio**.

<!-- -->

  
De manera análoga al anterior botón, la *Máscara de contraste para el
aumento de nitidez*
(<img src="/images/contrastmask-off.png" title="contrastmask-off.png" height="26"
alt="contrastmask-off.png" />) resalta las zonas que serán modificadas
por las herramientas de mejora de la nitidez (*[Nitidez en la
captura](Capture_Sharpening/es#Nitidez_en_la_captura.md),
[Máscara de nitidez](sharpening/es#máscara_de_nitidez) y
[Deconvolución](sharpening/es#deconvolución)*)

<div class="tlist tleft-list">

<figure>
<img src="/images/preview-sharpmask.jpg" title="preview-sharpmask.jpg" />
<figcaption>preview-sharpmask.jpg</figcaption>
</figure>

</div>

  
Las zonas resaltadas tendrán un tono claro (blanco o de un color claro
similar al tono global de la imagen) que indicará qué píxeles se
modificarán, destacando sobre un fondo negro que indica que esas zonas
no serán modificadas por las herramientas.

<!-- -->

  
Las zonas que abarca la máscara se pueden controlar únicamente con el
deslizador de *Umbral de contraste* de cada herramienta, ya que es este
el que discrimina qué píxeles se modificarán y cuáles no.

<!-- -->

  
Sin embargo, debes tener en cuenta que para ver las máscaras de la
herramienta *Nitidez* (*Máscara de nitidez* y *Deconvolución*) deberás
ampliar la imagen hasta el 100% como mínimo. De lo contrario no verás
nada en la *Vista Previa* porque esta herramienta sólo se activa cuando
la imagen se ve al 100% o superior.

<!-- -->

  
Por el contrario, con la herramienta *Nitidez en la captura* podrás
tener la imagen con la ampliación que desees, la máscara siempre será
visible, dado que la herramienta siempre está activa, sea cual sea la
ampliación.

<!-- -->

  
En cuanto a los indicadores de *recorte en sombras*
(<img src="/images/warning-shadows.png" title="warning-shadows.png" height="26"
alt="warning-shadows.png" />) y *luces*
(<img src="/images/warning-highlights.png" title="warning-highlights.png"
height="26" alt="warning-highlights.png" />), te permiten ver resaltadas
las zonas de la imagen que son demasiado oscuras o demasiado brillantes.

<div class="tlist">

<figure>
<img src="/images/preview-clipped.jpg" title="preview-clipped.jpg" />
<figcaption>preview-clipped.jpg</figcaption>
</figure>

</div>

  
Las zonas recortadas se enmascaran en función de cuánto superan los
umbrales: para las sombras, la máscara va desde un gris claro hasta el
blanco. Tanto más blanca cuanto menores sean los valores RGB del pixel
recortado (el enmascaramiento destacará las zonas en las que los tres
canales de color alcanzan o están por debajo del umbral de sombras
especificado en las *Preferencias*).

<!-- -->

  
Para las luces, la máscara va desde un gris medio al negro y destacará
las zonas en las que **al menos un canal** alcanza o supera el umbral de
luces especificado en las *Preferencias*. Si quieres ver solamente dónde
están recortados los tres canales, activa el modo de *previsualización
de luminosidad* además del indicador de luces recortadas.

<!-- -->

  
Ambos recortes se calculan usando el perfil ICC establecido con el botón
del *Rango de color*
(<img src="/images/gamut-hist.png" title="gamut-hist.png" height="26"
alt="gamut-hist.png" />): si está desactivado el cálculo empleará el
[*Perfil de
Salida*](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md).
En cambio si el botón está activado empleará el [*Perfil de
Trabajo*](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md).

- <figure>
  <img src="/images/toolbar2c.jpg" title="File:toolbar2c.jpg" />
  <figcaption><a
  href="File:toolbar2c.jpg">File:toolbar2c.jpg</a></figcaption>
  </figure>

  
Estos botones sirven para realizar rotaciones y volteos a la imagen: los
dos primeros darán un cuarto de giro cada vez que los pulses, mientras
que los otros sirven para conseguir una *imagen espejo* del original
(espejo horizontal o espejo vertical).

- <figure>
  <img src="/images/toolbar3a.jpg" title="File:toolbar3a.jpg" />
  <figcaption><a
  href="File:toolbar3a.jpg">File:toolbar3a.jpg</a></figcaption>
  </figure>

  
La lista de selección sirve para seleccionar un perfil de color del
monitor distinto al establecido en las *Preferencias*. Esto puede ser
útil si deseas probar o usar un perfil diferente con unas fotos o
durante una sesión de revelado entera. Esta selección manual sólo estará
activa hasta que cierres el programa. Cuando vuelvas a abrir
RawTherapee, el valor por defecto del perfil del monitor volverá a estar
activo.

<!-- -->

  
Los elementos que veas en las listas del perfil del monitor serán los
nombres de los perfiles ICC ubicados en la carpeta especificada en:
*Preferencia\>Gestión de color\>Carpeta con perfiles de color ICC*. Si
has cambiado esta carpeta, debes reiniciar RawTherapee para que los
cambios tengan efecto.

<!-- -->

  
De forma similar puedes cambiar el [*Tipo de conversión del rango de
colores*](Color_Management/es#Los_Tipos_de_Conversión_del_rango_de_colores.md)
(<img src="/images/intent-relative.png" title="intent-relative.png" height="26"
alt="intent-relative.png" />), en caso de que lo necesites.

<div class="tlist">

<figure>
<img src="/images/preview-gamut.jpg" title="preview-gamut.jpg" />
<figcaption>preview-gamut.jpg</figcaption>
</figure>

</div>

  
Tal como se explica en la [*Gestión del
color*](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md),
con los botones de *Prueba de impresión*
(<img src="/images/gamut-softproof.png" title="gamut-softproof.png" height="26"
alt="gamut-softproof.png" />) y *Colores fuera de rango*
(<img src="/images/gamut-warning.png" title="gamut-warning.png" height="26"
alt="gamut-warning.png" />) puedes comprobar cómo se verán los colores
de la imagen interna (con la que trabaja RawTherapee) y cuáles no se
podrán mostrar en la imagen exportada, en la imagen de la *Vista Previa*
y en la imagen impresa (que dependen del *Perfil de salida*, el *Perfil
del monitor* y el *Perfil de impresión*, respectivamente). La máscara
resaltará los colores fuera de rango

<!-- -->

  
Para que los colores en pantalla sean precisos deberás tener [calibrado
y
perfilado](https://www.diversidadyunpocodetodo.com/displaycal-calibracion-y-perfilado-pantalla)
tu monitor, aunque si eres usuario de OS X y no utilizas un monitor con
calibración hardware interna, estarás limitado a ver las imágenes
codificadas en sRGB ([puedes consultar esta discusión en inglés sobre el
tema](https://discuss.pixls.us/t/wide-gamut-preview-in-os-x/2481)).

- <figure>
  <img src="/images/toolbar3b.jpg" title="File:toolbar3b.jpg" />
  <figcaption><a
  href="File:toolbar3b.jpg">File:toolbar3b.jpg</a></figcaption>
  </figure>

  
Las flechas izquierda y derecha sirven para abrir en el *Editor* las
imagenes anterior y posterior respectivamente a la que está abierta
actualmente. De esta forma no tienes que volver al *Navegador de
archivos* ni tener abierta la barra de *Miniaturas* para seleccionar la
siguiente imagen a editar.

<!-- -->

  
Las flechas verticales sirven para sincronizar la barra de *Miniaturas*
con la imagen abierta, de forma que verás su miniatura en la barra. Al
mismo tiempo, si usas los atajos de teclado podrás cancelar los filtros
que tengas activos (por ejemplo, dejar de ver sólo los archivos tif y
volver a ver todas las imágenes de la carpeta).

- <figure>
  <img src="/images/toolbar3c.jpg" title="File:toolbar3c.jpg" />
  <figcaption><a
  href="File:toolbar3c.jpg">File:toolbar3c.jpg</a></figcaption>
  </figure>

  
Los botones de ampliación (*«zoom»*) necesitan pocas explicaciones y de
izquierda a derecha sirven para *alejar*, *acercar*, encuadrar en la
*Vista Previa* la imagen completa, encuadrar la imagen recortada y
mostrar la imagen a *escala real* (al 100%, o 1:1). En todo momento al
lado de los botones tienes la escala en porcentaje a la que se muestra
la imagen en la *Vista Previa*.

<!-- -->

  
Además mientras tengas el puntero del ratón sobre la *Vista Previa*,
podrás acercar o alejar la imagen con la rueda central del ratón.

- <figure>
  <img src="/images/toolbar3d.jpg" title="File:toolbar3d.jpg" />
  <figcaption><a
  href="File:toolbar3d.jpg">File:toolbar3d.jpg</a></figcaption>
  </figure>

<div class="tlist">

<figure>
<img src="/images/preview-detail-window.jpg"
title="Las ventanas de detalle pueden tener el tamaño deseado y situarlas donde más te convenga. Además cada una puede tener su propio nivel de ampliación, independiente de las otras ventantas de detalle y de la Vista Previa. Cuando selecciones una, el área mostrada estará enmarcada por un recuadro rojo en la Vista Previa. En este ejemplo la ventana seleccionada es la inferior."
width="400" />
<figcaption>Las ventanas de detalle pueden tener el tamaño deseado y
situarlas donde más te convenga. Además cada una puede tener su propio
nivel de ampliación, independiente de las otras ventantas de detalle y
de la <em>Vista Previa</em>.<br />
Cuando selecciones una, el área mostrada estará enmarcada por un
recuadro rojo en la <em>Vista Previa</em>. En este ejemplo la ventana
seleccionada es la inferior.</figcaption>
</figure>

</div>

  
El botón de *Ocultar todos los paneles*
(<img src="/images/crossed-arrows-out.png" title="crossed-arrows-out.png"
height="26" alt="crossed-arrows-out.png" />) te permite maximizar el
área de *Vista Previa*

<!-- -->

  
Por su lado la <span id="ventana_de_detalle">*Ventana de detalle*</span>
(<img src="/images/window-add.png" title="window-add.png" height="26"
alt="window-add.png" />) abre una pequeña previsualización con un tamaño
y factor de ampliación ajustables. Esto te permite trabajar en la foto a
una escala que quepa en la previsualización, al tiempo que examinas
varias áreas de interés con una ampliación del 100% (o incluso más). E
incluso te permite procesar la imagen viéndola a escala real (al 100%)
mientras muestra varias zonas de interés que a esa ampliación nunca
podrían estar al mismo tiempo en la *Vista Previa*, por ejemplo a la
hora de ajustar la nitidez de la imagen.

<!-- -->

  
El mayor beneficio de esta característica se aprecia con máquinas
lentas, aunque también con máquinas más potentes, ya que la
previsualización con ampliaciones bajas tarda menos en actualizarse que
al 100% o mayor. Esto se debe a que el trabajo a escalas por debajo del
100% excluye ciertas herramientas lentas (como la *Reducción de ruido*),
mientras que en las pequeñas ventanas de detalle ampliadas al 100% sí se
incluyen todas las herramientas y debido a su pequeño tamaño se
actualizan rápidamente.

<!-- -->

  
Cuando selecciones una ventana de detalle
(<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" /> en la ventana de detalle) podrás cambiar
la escala con los pequeños botones de la ventana o con la rueda del
ratón. Al mismo tiempo, una vez seleccionada el programa indicará qué
zona muestra mediante un recuadro rojo.

<!-- -->

  
Para cambiar el encuadre de la ventana pincha y arrastra directamente en
su previsualización. Y aunque esto es útil para pequeños ajustes, si
tienes que cambiar la zona de detalle a otro punto alejado, es mejor que
pinches sobre el recuadro rojo de la *Vista Previa* y lo arrastres hasta
su destino.

- <figure>
  <img src="/images/toolbar4.jpg" title="File:toolbar4.jpg" />
  <figcaption><a
  href="File:toolbar4.jpg">File:toolbar4.jpg</a></figcaption>
  </figure>

  
El icono del disquete
(<img src="/images/save.png" title="save.png" height="26" alt="save.png" />) te
mostrará la ventana de [guardar inmediatemente la
imagen](Saving_Images/es#Guardar_inmediatamente.md), para
exportar la foto tal como está procesada en ese momento.

<!-- -->

  
Por el contrario si prefieres exportarla más tarde enviándola a la *Cola
de procesamiento*, el botón de *enviar a la cola*
(<img src="/images/gears.png" title="gears.png" height="26" alt="gears.png" />)
será el que necesites.

<!-- -->

  
Por fin, <span id="editar_la_imagen_actual_en_un_programa_externo">si
quieres editar la imagen tal como está procesada en un programa
externo<span>, usa el botón de la paleta de pintor
(<img src="/images/palette-brush.png" title="palette-brush.png" height="26"
alt="palette-brush.png" />). El editor que se abrirá dependerá de lo que
hayas especificado en ***Preferencias \> General \> Editor Externo***.

<!-- -->

  
La barra de progreso te indica si el programa está aplicando algún
procesado a la imagen que estás editando. En contraste, la barra de
progreso que ves al lado del *Creador de Perfiles ICC* indica que el
programa está trabajando con las imágenes en el *Navegador de archivos*
o en la *Cola de procesamiento*.

### El Historial y las Instantáneas

El panel del ***Historial*** contiene un listado de cada una de tus
acciones de edición en la imagen. Haciendo clic sobre las entradas
puedes avanzar o retroceder por las diferentes etapas de tu trabajo,
desde la primera entrada (que es la imagen tal como la has abierto en el
*Editor*), hasta el último paso que hayas dado.

Cada vez que ajustas un control *diferente*, se añade una entrada. Es
decir, que si ajustas varias veces el mismo control, simplemente se
cambiará su estado en la misma línea del *Historial*. Por ejemplo, el
ajuste del deslizador de *Compensación de exposición* de *0* a *0.3* y
luego a *0.6* resultará en una entrada con un valor final de *0.6*.

Del mismo modo, al ajustar una curva todos los ajustes de sus puntos de
control individuales se agrupan en una única entrada del *Historial*. Si
deseas guardar los ajustes como dos (o más) entradas, tendrás que
dividirlos ajustando entre ellos algún otro control. Por ejemplo,
imagina que quieres personalizar una curva en el modo *Similar a
película*: empieza ajustando varios puntos de control en la curva, luego
cambia el modo de la curva de *Similar a película* a *Estándar* y a
continuación de nuevo a *Similar a película* para crear una nueva
entrada en el *Historial* y a continuación continúa ajustando la curva.

El listado del *Historial* no se guarda: se pierde tan pronto como abres
otra imagen en el *Editor* o cierras el programa. No obstante, no se
pierde ninguno de tus ajustes, ya que se guarda el estado final de todas
las herramientas en el archivo del [perfil de
procesamiento](Sidecar_Files_-_Processing_Profiles/es.md), listo
para volver a usarlo la próxima vez que abras esa imagen.

Bajo el panel del *Historial* hay un panel llamado ***Instantáneas***.
Su utilidad reside en que puedes guardar una instantánea de la foto con
todos los ajustes hasta ese momento y luego seguir modificando tu foto
para darle una apariencia diferente, guardando instantáneas en cada
momento en que creas que has llegado a una versión de tu foto que vale
la pena conservar.

Una vez que tienes dos o más instantáneas, simplemente haciendo clic en
cada una de ellas podrás moverte de una a otra de las diferentes
versiones y quedarte con la que te guste más. En el futuro, las
instantáneas se guardarán en el archivo de perfil de procesamiento PP3.
Por ahora, el *Historial* y las *Instantáneas* se pierden cuando cargas
una nueva foto en el *Editor* o cierras RawTherapee.

### El Navegador

\[\[<File:navigator-panel.jpg%7Cright%7Cthumb%7C650px%7CEl> panel del
*Navegador* mostrando:  

<div class="captions_indent">

**·** la máscara semitransparente, indicando qué parte de la imagen se
ha recortado  
**·** el marco rojo, indicando qué zona de la imagen se muestra en la
*Vista Previa*  
**·** las dimensiones en píxeles de la imagen completa (incluída la zona
recortada)  
**·** la posición del puntero del ratón sobre el píxel de la imagen en
el que se leen los valores de los canales de color (el origen de
coordenadas es la esquina superior izquierda)  
**·** los valores RGB en un rango de 0 a 255  
**·** los valores HSV en porcentajes, excepto H que está en grados  
**·** los valores L\*a\*b\*

</div>

\]\] El panel del *Navegador* muestra una miniatura de la imagen
actualmente abierta y qué porción de ella se ve en la *Vista Previa*
mediante un marco rojo. También muestra con una máscara semitransparente
qué parte de la imagen se ha recortado.

Por defecto el marco es rojo y la máscara se basa *en el Tema*, aunque
puedes cambiar el color del marco en ***Preferencias \> General \>
Apariencia \> Color del marco del Navegador***y el color y la
transparencia de la máscara basada*en el Tema'' en***Preferencias \>
General \> Apariencia \> Color de la máscara de recorte**''.

Debajo de esta miniatura verás los valores RGB, HSV y L\*a\*b\* del
píxel sobre el que se encuentra el puntero del ratón. Los números
mostrados dependen del estado del botón de *Rango de color*
(<img src="/images/gamut-hist.png" title="gamut-hist.png" height="26"
alt="gamut-hist.png" />), pudiendo ser los del *Perfil de trabajo* o los
del *Perfil de salida*, es decir los valores de los píxeles con los que
trabaja internamente RawTherapee, o los valores de los píxeles en la
imagen exportada.

Además, haciendo clic sobre los valores RGB o HSV puedes cambiar entre
estos tres formatos (los valores L\*a\*b\* son fijos y no se pueden
cambiar de formato):

- **\[0-255\]**: cada canal puede tener hasta 256 valores distintos.  
  *Funciona en los 3 canales, tanto en RGB como en HSV*
- **\[0-1\]**: cada canal estará entre *0* y *1* con una precisión de 4
  decimales, es decir, cada canal puede tener hasta 10001 valores
  distintos.  
  *Funciona en los 3 canales, tanto en RGB como en HSV*
- **\[%\]**: cada canal tendrá un porcentaje con 1 decimal de precisión,
  es decir, cada canal puede tener hasta 101 valores distintos.  
  *Funciona en todos los canales excepto en el canal **H**, que
  representará el dato en grados del modelo de color HSV*

Por último, existe una manera de mostrar los valores raw reales de los
fotodiodos del sensor: configura el *Navegador* para que use el rango
*\[0-255\]*, aplica el *[perfil de procesamiento
Neutro](Sidecar_Files_-_Processing_Profiles/es.md)* y ajusta el
método de *[Desentramado](demosaicing/es)* a *«Ninguno»*. El
Navegador mostrará los valores raw reales después de la substracción del
nivel de negro.

### Análisis de la Imagen

A la hora de saber lo que estás haciendo con la imagen, aparte de la
*Vista previa* existen unos gráficos que te ayudarán a entender qué está
pasando con tu foto: ¿tienes zonas sobreexpuestas o subexpuestas?
¿Tienes colores tan saturados que no se mostrarán correctamente en la
imagen final? ¿Tienes dominantes de color? ¿Puedes aumentar la gama
dinámica de la imagen? Estas y otras preguntas se pueden contestar
analizando la imagen con dichos gráficos. Además, no importará si tu
pantalla tiene un color mediocre o decididamente incorrecto, pues los
datos analizados serán los mismos y los resultados también.

**Excepto cuando se indique expresamente lo contrario, todos los
gráficos de análisis de la imagen muestran los valores de los colores de
la imagen exportada, es decir, teniendo en cuenta el *perfil de
salida*.**

El panel de *Análisis de la Imagen* puede moverse al lado izquierdo o al
derecho de la ventana mediante la opción ***Preferencias \> General \>
Disposición \> Histograma en panel izquierdo***.

#### Histogramas

##### ¿Qué es un histograma?

En fotografía, un histograma es una representación gráfica del número de
píxeles que tienen un valor dado. Más específicamente un histograma
representa el número de píxeles con el valor de un canal concreto (R, G,
B o luminosidad).

El eje horizontal de este gráfico representa el rango de valores
posibles, mientras que el eje vertical representa el número de píxeles
que tienen ese valor.

##### Cómo leer y trabajar con el histograma

Saber cómo leer un histograma es una destreza básica y muy útil, ya que
puede señalar problemas en tu imagen independientemente de la
configuración de tu monitor o lo mal
[perfilado](https://www.diversidadyunpocodetodo.com/displaycal-calibracion-y-perfilado-pantalla)
que esté.

En la siguiente imagen podemos apreciar varias zonas, aunque la más
importante es la central, con el histograma propiamente dicho.

\[\[<File:histogram_labeled.jpg%7Cright%7Cframe%7CEl> **Histograma** con
diferentes zonas de información:  

<div class="captions_indent">

**A**, **B** y **C**: zona principal del histograma donde se muestran
los 3 canales (RGB) y la luminosidad  
**A**: zona donde se acumulan los píxeles con valores bajos,
correspondientes a las partes en sombra  
**B**: zona con píxeles de valores medios, donde encontraremos la
mayoría de los detalles de la foto  
**C**: zona con píxeles de valores altos, correspondientes a las luces  
**D**: aviso de recorte de canales (el cuadradito de color). En este
caso los canales azul, rojo y de luminosidad (en color gris claro)
presentan píxeles recortados o con valor *0*  
**E**: área de botones para seleccionar el tipo de gráfico y los canales
a representar  
**F**: botón para mostrar u ocultar los botones de los canales, el tipo
de escalado de los ejes de coordenadas y la barra de indicación RGB  
**G**: al activar el botón de la barra de indicación RGB se muestra bajo
el gráfico una pequeña barra que mostrará unas marcas de color  
**H**: marcas de color indicando dónde se localizan en el histograma los
valores RGB del píxel que haya justo debajo del puntero del ratón (sobre
la imagen)

</div>

\]\] Y aunque en realidad muestra cuatro histogramas juntos (el canal
rojo, el verde, el azul y el canal de luminosidad), los veremos como uno
solo porque todos ellos siguen el mismo patrón: el eje horizontal
representa los valores posibles del canal, entre *0* a la izquierda y
*255* a la derecha. Mientras tanto el eje vertical es simplemente la
suma de todos los píxeles cuyo canal tiene un valor determinado. Cuanto
más alto sea el gráfico en un punto (en un valor), más píxeles hay en la
foto con ese valor.

Siguiendo con la imagen de ejemplo, en **A** encontrarás los valores más
oscuros posibles (los más bajos), en **B** los tonos medios y en **C**
los valores más brillantes posibles.

Puedes ver que no hay ningún píxel con los valores más altos porque las
líneas a la derecha del histograma caen hasta la parte inferior del
gráfico. Sin embargo verás que hay un número significativo de píxeles
donde los canales azul y rojo tienen un valor de *0* (a la izquierda del
histograma), por lo que se muestran unos pequeños cuadrados del color
del canal indicando que hay un posible recorte de colores. Igualmente
hay un cuadrado de color gris claro, indicando que la luminosidad podría
estar sufriendo recortes.

*Decimos «podrían» porque el valor*0*es perfectamente válido en una
imagen y eso no significa que el píxel esté recortado. Sin embargo los
valores que por distintos motivos sean negativos sí se recortarán y se
dejarán en*0*. De manera análoga hablaríamos con los valores*255*y
superiores.*

![](Rt_histogram_rgbindicator.png "Rt_histogram_rgbindicator.png")También
puedes ver en **H** una barra con cuatro marcas (los tres canales y la
luminosidad), que irán moviéndose según muevas el ratón sobre la imagen:
indican los valores de los tres canales de color y el de la luminosidad
en el píxel que haya en ese momento debajo del puntero de ratón.

Y para estimar los valores de cada canal, tienes unas líneas
discontínuas en vertical repartidas a lo largo del histograma, que
indican los valores *1*, *3*, *7*, *15*, *31*, *63* y *127* (resultantes
de calcular *2<sup>n</sup>-1*). Si quieres ver los valores exactos,
puedes leerlos directamente en [el panel del
*Navegador*](#El_Navegador.md).

En este momento es conveniente no olvidar que independientemente de la
profundidad de bits de la foto, el gráfico del histograma tiene
únicamente hasta 256 posibles valores.

Esto significa que los valores reales dentro del motor del programa (que
tiene una precisión de coma flotante de 32 bits) se agruparán y
mostrarán en una sola columna por grupo. Y a pesar que se está perdiendo
exactitud, el análisis de la imagen sigue siendo perfectamente válido.

Continuando con la imagen de ejemplo, observarás que **B** no está en el
centro del gráfico y es que los ejes no tienen que ser necesariamente
lineales: RawTherapee también puede escalar el histograma
logarítmicamente e incluso puedes reajustar la posición de las líneas
discontínuas, de forma que veas mejor la información.

![](RT57_histogram_ani.gif "RT57_histogram_ani.gif") Para ayudarte a
visualizar los datos el histograma tiene tres modos, que escalan los
datos en los ejes *x* e *y* de forma diferente:

- ![<File:Histogram-mode-linear-small.png>](Histogram-mode-linear-small.png "File:Histogram-mode-linear-small.png")
  Modo lineal-lineal: las líneas discontínuas verticales se sitúan
  ocupando el doble de espacio que la anterior o la mitad de espacio que
  la siguiente línea. Es decir, los valores entre *128* y *255* ocupan
  la mitad derecha del gráfico. Los valores entre *64* y *127* ocupan la
  mitad de la parte izquierda. Entre *32* y *63* un cuarto del gráfico.
  Y así sucesivamente. Las líneas verticales no se pueden desplazar de
  su sitio.
- ![<File:Histogram-mode-logx-small.png>](Histogram-mode-logx-small.png "File:Histogram-mode-logx-small.png")
  Modo lineal-logaritmico: el eje *x* es lineal, el eje *y* (las líneas
  horizontales de la rejilla) se escalan logarítmicamente. La posición
  de las líneas horizontales se puede desplazar pinchando y arrastrando
  en el histograma. De esta forma puedes ver mejor los valores del
  gráfico con menos píxeles (donde la curva está cerca de la parte
  inferior del gráfico).
- ![<File:Histogram-mode-logxy-small.png>](Histogram-mode-logxy-small.png "File:Histogram-mode-logxy-small.png")
  Modo log-log: tanto el eje *x* como el *y* se escalan
  logarítmicamente. Al pinchar y arrastrar puedes llevar el gráfico a un
  punto donde puedas ver claramente la información que necesites. De
  esta forma puedes ver mejor la zona de las sombras, quitándole
  importancia a las luces en el gráfico.

El histograma principal puede mostrar simultáneamente uno o más de los
siguientes elementos:

- ![<File:Histogram-red-on-small.svg>](Histogram-red-on-small.svg "File:Histogram-red-on-small.svg")
  el canal rojo,
- ![<File:Histogram-green-on-small.svg>](Histogram-green-on-small.svg "File:Histogram-green-on-small.svg")
  el canal verde,
- ![<File:Histogram-blue-on-small.svg>](Histogram-blue-on-small.svg "File:Histogram-blue-on-small.svg")
  el canal azul,
- ![<File:Histogram-silver-on-small.svg>](Histogram-silver-on-small.svg "File:Histogram-silver-on-small.svg")
  la luminancia CIELab,
- ![<File:Histogram-gold-on-small.svg>](Histogram-gold-on-small.svg "File:Histogram-gold-on-small.svg")
  la [cromaticidad](https://www.hisour.com/es/chromaticity-26177/).
- ![<File:Histogram-bayer-on-small.svg>](Histogram-bayer-on-small.svg "File:Histogram-bayer-on-small.svg")
  los canales rojo, verde y azul de la imagen raw original antes del
  desentramado.

El histograma muestra los canales indicados anteriormente usando el
*perfil de salida* (con corrección gamma) cuando el botón de rango de
colores ![](Gamut-hist.png "Gamut-hist.png") está desactivado
(predeterminado), o usando el *perfil de trabajo* cuando el botón está
activado. El estado de este botón también afecta a los valores que se
muestran en el panel del *Navegador*, así como a los indicadores de
recorte de sombras ![](Warning-shadows.png "Warning-shadows.png") y
luces ![](Warning-highlights.png "Warning-highlights.png"). No afecta al
histograma raw.

Cuando hay una zona desproporcionadamente brillante en relación al resto
de la imagen, aparecerá como un pico en el histograma. Si deseas mostrar
esto en un histograma con un eje *«y»* lineal, el pico empujará los
valores con menor cantidad de píxeles hacia abajo en el eje *«y»*, lo
que los hará difíciles de ver. Si cambias a uno de los modos
logarítmicos podrás escalar los datos y obtener así una mejor visión de
conjunto de todos los valores (pincha y arrastra en el *histograma*).

##### Los avisos de recorte

Recuerda que en la columna *0* y en la columna *255* se pueden
representar bastantes píxeles y esto viene a cuento porque existe una
peculiaridad con los avisos de recorte del histograma: la gestión
adecuada del recorte de tonos en las fotografías es muy importante y los
avisos del histograma no son todo lo preventivos que deberían ser. Es
decir, se puede dar el caso de que hayan píxeles recortados en la imagen
y que el histograma no muestre ningún aviso.

![](clipping_highcontrast-nowarning.jpg "clipping_highcontrast-nowarning.jpg")En
esta imagen a contraluz se aprecia que mientras existen recortes de
tonos en las luces, en el histograma no se muestra ningún aviso. En
concreto la imagen muestra el canal rojo, con los recortes resaltados en
rojo (fíjate en los botones activados *canal rojo* y *indicación de
recorte en las luces*) y en el histograma únicamente se ven los picos en
todos los canales, pero sin aviso de recorte. Esto es debido a que el
histograma no muestra el aviso hasta que el pico alcanza la parte
superior de gráfico.

En general esta peculiaridad no supone un gran problema, puesto que las
zonas decididamente oscuras o brillantes de las fotos no ocuparán tantos
píxeles como para que degraden la imagen. Sin embargo en fotos *en clave
alta*, en *clave baja*, con contraluces, con nieve, nocturnas, o en
general con grandes contrastes, es recomendable vigilar bien las zonas
con tonos recortados. En términos generales, debes dar importancia a los
recortes que ocurren sobre la piel y no deben importarte cuando se deben
a [luces
especulares](https://es.wikipedia.org/wiki/Resaltado_especular).

Si un histograma muestra recortes y consideras importantes las regiones
recortadas, debes comenzar estableciendo dónde ocurre el recorte:

- comprueba el [*histograma raw*](#el_histograma_raw): ¿hay
  algún canal recortado? Si es así, la [recuperación de las
  luces](Exposure/es#Highlight_Reconstruction.md) posiblemente
  pueda ayudarte.
- si el *histograma raw* no está recortado: entonces toda la información
  necesaria está intacta y hay alguna etapa posterior al desentramado
  que es la que produce el recorte.
- asegúrate que el rango de color de tu perfil de trabajo es
  suficientemente grande activando el botón de rango de colores
  (![](Gamut-hist.png "Gamut-hist.png")), para ver los histogramas de la
  imagen mientras está en el circuito de revelado (con los datos que usa
  el motor del programa).
- es posible que quieras aplicar temporalmente el perfil
  [Neutro](neutral/es) para desactivar todas las herramientas
  mientras haces la comprobación, y luego volver atrás.
- si no es el *perfil de trabajo* el que causa el recorte (el *espacio
  de trabajo* predeterminado es ProPhoto, y es enormemente grande), es
  probable que tus ajustes en las herramientas lo estén provocando:
  reduce la exposición, no te excedas con las curvas y usa la compresión
  del rango dinámico si es necesario.

##### ¿Cómo es un «buen» histograma?

No hay ni «buenos» ni «malos» histogramas: cada uno está ligado a una
imagen y dependiendo de las características de esta, el histograma
tendrá una forma «lógica». Lo que no puedes ignorar es que cada
histograma te dará información de la fotografía a la que pertenece.

Si la foto que ves en la *Vista previa* es de tu agrado, el histograma
únicamente representará esa imagen, sin señalar lo «bien» o «mal» que
esté:

<div>

- <figure>
  <img src="/images/hist-church.jpg"
  title="Habitualmente leerás que un histograma «debe» tener los tonos (los valores de los píxeles) repartidos a todo lo ancho del gráfico. Dependiendo de tus gustos muchas veces esto será lo normal, pero aún así el objetivo no es conseguir un histograma con una determinada forma."
  height="683" />
  <figcaption>Habitualmente leerás que un histograma «debe» tener los
  tonos (los valores de los píxeles) repartidos a todo lo ancho del
  gráfico.<br />
  Dependiendo de tus gustos muchas veces esto será lo <em>normal</em>,
  pero aún así el objetivo no es conseguir un histograma con una
  determinada forma.</figcaption>
  </figure>

- <figure>
  <img src="/images/hist-seagull.jpg"
  title="Una fotografía puede estar bien expuesta, bien procesada y aún así no tener un gráfico «a todo lo ancho». En esta foto la mayor parte de los píxeles están oscuros, en gran parte para conseguir que la blancura de la gaviota resalte sobre el fondo. Si este es el resultado que buscabas, el histograma simplemente será un reflejo de la imagen y no indicará nada «malo»."
  height="683" />
  <figcaption>Una fotografía puede estar bien expuesta, bien procesada y
  aún así no tener un gráfico «a todo lo ancho».<br />
  En esta foto la mayor parte de los píxeles están oscuros, en gran parte
  para conseguir que la blancura de la gaviota resalte sobre el
  fondo.<br />
  Si este es el resultado que buscabas, el histograma simplemente será un
  reflejo de la imagen y no indicará nada «malo».</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/hist-coast.jpg"
  title="Lo que siempre hace un histograma es analizar los píxeles y ofrecer información acerca de la imagen. En este caso el canal azul está desplazado más a la derecha que el resto, lo que indica que la foto tiene una dominante azul. Si ese es tu deseo, la foto está perfecta. Si no es así, tienes la oportunidad de corregirlo."
  height="683" />
  <figcaption>Lo que siempre hace un histograma es analizar los píxeles y
  ofrecer información acerca de la imagen.<br />
  En este caso el canal azul está desplazado más a la derecha que el
  resto, lo que indica que la foto tiene una dominante azul.<br />
  Si ese es tu deseo, la foto está perfecta. Si no es así, tienes la
  oportunidad de corregirlo.</figcaption>
  </figure>

- <figure>
  <img src="/images/hist-bee.jpg" title="hist-bee.jpg" />
  <figcaption>hist-bee.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/hist-flower.jpg" title="hist-flower.jpg" />
  <figcaption>hist-flower.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/hist-swallow.jpg" title="hist-swallow.jpg" />
  <figcaption>hist-swallow.jpg</figcaption>
  </figure>

</div>

##### El histograma raw

Los *histogramas raw* muestran los datos de la imagen después de la
substracción del *nivel de negro*. El extremo derecho del histograma
corresponde al *nivel de blanco*. Por ello se ven afectados por los
niveles de blanco y negro detectados, así como por los ajustes de los
niveles de negro y de blanco realizados por el usuario en RawTherapee,
pero no les afectan los ajustes de *corrección del punto blanco*.

Al examinar el *histograma raw*, posiblemente quieras poner el método de
desentramado a *Ninguno*. Esto revelará el patrón del sensor en la
*Vista previa* y también hará que el panel del
[Navegador](editor/es#el_navegador) muestre los valores RGB
del píxel del sensor de la cámara sobre el que se encuentra el cursor
del ratón.

<figure>
<img src="/images/raw-hist-lin-log.jpg"
title="Los datos del sensor son lineales, pero si en el histograma usas el modo lineal, el gráfico se acumula en la zona izquierda. Esto es normal, aunque para ver qué a captado la cámara, no es demasiado útil.  El modo lineal-logarítmico (en el centro) ya facilita más el estudio del histograma, pero aún es difícil adivinar qué pasa en las sombras.  El modo log-log es el que permite observar mejor las zonas oscuras, a costa de perder un poco el detalle de las luces." />
<figcaption>Los datos del sensor son lineales, pero si en el histograma
usas el <em>modo lineal</em>, el gráfico se acumula en la zona
izquierda. Esto es normal, aunque para ver qué a captado la cámara, no
es demasiado útil.<br />
<br />
El <em>modo lineal-logarítmico</em> (en el centro) ya facilita más el
estudio del histograma, pero aún es difícil adivinar qué pasa en las
sombras.<br />
<br />
El <em>modo log-log</em> es el que permite observar mejor las zonas
oscuras, a costa de perder un poco el detalle de las luces.</figcaption>
</figure>

Si te preguntas qué es el nivel de negro o de blanco, sigue leyendo: los
archivos raw contienen un volcado de los datos capturados por el sensor
y cuantificados por el convertidor analógico-digital.

El archivo raw como contenedor tiene su propia profundidad de bits
(normalmente 16 bits), mientras que los datos que contiene pueden tener
una profundidad de bits menor: usualmente es de 12 bits (*0-4095*) o 14
bits (*0-16383*).

Para mostrar los datos de un archivo raw como una imagen, dos de las
informaciones clave necesarias para procesarlos correctamente son los
*niveles de negro y de blanco*. El *nivel de negro* no tiene por qué ser
necesariamente *0*, ya que el sensor y la electrónica de la cámara
producen ruido digital, así que el fondo de ruido puede estar, por
ejemplo, en el valor *512*. El *nivel de blanco* tampoco tiene por qué
ser necesariamente *16383*: depende de varias cosas y por ejemplo puede
recaer en el valor *16300*.

Para más información, consulta los artículos
[Desentramado](demosaicing/es) y [Añadir compatibilidad con
nuevos formatos Raw](Adding_Support_for_New_Raw_Formats/es.md)
(especialmente la cabecera del archivo `camconst.json`).

Los valores de los *niveles de negro y de blanco* se establecen
jerárquicamente buscándolos en varios lugares: en `dcraw.c`, dentro de
los metadatos del archivo raw y en el archivo `camconst.json` (este
último tiene prioridad). Además, el usuario puede retocar los [*niveles
de negro*](Raw_Black_Points/es.md) y [*niveles de
blanco*](Raw_White_Points/es.md) desde dentro de RawTherapee.

#### Analizador en Forma de Onda, AFO («waveform»)

En RawTherapee un *Analizador en Forma de Onda* (o *AFO*) es una
representación especial de los canales RGB, que muestra en horizontal la
posición de los píxeles de la imagen, en vertical el valor de cada píxel
y mediante un tono más vivo o más apagado, la cantidad de píxeles con
cada valor.

Vamos a desgranar esta definición:

- cada columna representa un grupo de columnas de la imagen: si por
  ejemplo el gráfico tiene 256 columnas y la imagen tiene 5376 píxeles
  de ancho, cada columna del *AFO* representa 21 columnas de la imagen.
  Así pues, de izquierda a derecha las columnas muestran el análisis de
  esos grupos de 21 columnas de la imagen de ejemplo
- el análisis de los valores de los píxeles **se realiza sobre la imagen
  final**, es decir, teniendo en cuenta [el perfil de
  salida](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md)
- para cada columna, los valores R, G y B de los píxeles se sitúan en
  vertical, es decir, cuanto mayor es el valor del canal de un píxel,
  más alto se situará en la columna de ese valor y cada canal de un
  píxel se situará donde le corresponda según su valor (no tienen por
  qué estar los tres valores juntos)
- ![](RGB_illumination.jpg "RGB_illumination.jpg")\]cuando varios
  canales coinciden en el mismo punto del *AFO*, sus colores se mezclan:
  por ejemplo, los puntos amarillos surgen de la mezcla aditiva de los
  canales rojo y verde
- cuantos más píxeles de un grupo tengan el mismo valor de un canal (por
  lo tanto todos se representan en el mismo punto del gráfico), más
  brillante o intenso será el color de ese canal. Así pues, supongamos
  que en el ejemplo anterior dentro de un grupo de 21 columnas de la
  imagen hay un conjunto de 300 píxeles con un valor del canal rojo de
  180 y otro conjunto de 40 píxeles con un valor de 57: a la hora de
  mostrarlos en el gráfico el primer conjunto tendrá un punto rojo mucho
  más vivo que el segundo, que será más oscuro. Estarán localizados
  dentro de la misma columna, pero un punto estará más alto y será más
  brillante que el otro. Además, tienes un pequeño control deslizante a
  la izquierda del *AFO* para cambiar el brillo de los puntos (si no lo
  ves, debes activar el botón para mostrar las opciones de visualización
  \[ ![text-middle](histogram-ellipsis-small.png "text-middle") \]).
  Aumentando el brillo de los puntos podrás ver mejor cuándo hay píxeles
  sobrexpuestos o subexpuestos (en la parte alta o baja del gráfico)

![](waveform.jpg "waveform.jpg")Además de lo dicho hasta ahora, si te
fijas bien en el gráfico verás unas líneas discontínuas horizontales:
representan la posición de los valores 1, 3, 7, 15, 31, 63 y 127 (igual
que las líneas discontínuas verticales en el histograma) y además los
valores 0 (aunque esta línea se confunde con la del 1) y 255 (la línea
discontínua superior). Es decir, las ondas nunca llegarán a los límites
inferior y superior del gráfico. De esta forma los valores recortados se
pueden ver mejor.

Y de la misma forma que en el histograma, aquí también se pueden activar
o desactivar independientemente los tres canales RGB y el de
luminosidad, además de la barra que indica qué valores tienen los
canales del píxel de la imagen que esté debajo del puntero del ratón.

En la foto de ejemplo puedes ver que hay dos zonas claramente
diferenciadas: a la izquierda un candado con áreas contrastadas y
distintos matices de color, mientras que a la derecha tenemos una madera
básicamente gris, que se va oscureciendo hacia el borde de la imagen.
Con esto, en general todas las ondas se sitúan en la parte baja del
gráfico porque la imagen tiene baja luminosidad (la luminosidad general
tiende a un gris medio o un poco más oscuro).

En el caso de la madera gris, en el *AFO* se ve que en la parte derecha
(coincidiendo con la posición de la puerta) hay una línea gruesa blanca
descendente: es blanca porque la madera tiene un tono gris neutro y los
tres canales de los píxeles tienen valores similares, que al mezclarse
generan el blanco. Es gruesa porque hay distintos tonos de gris
(distintos valores) en la textura de la madera. Y la línea tiene una
clara tendencia a descender hacia la derecha, dónde la madera es más
oscura.

Por su parte la cresta que se ve en la parte izquierda viene del
candado, con canales verdes y rojos más o menos igualados (generando el
área amarilla) y el canal azul más abajo, coincidiendo con el tono
amarillo latón del candado. La pequeña raya azul cián encima de la
cresta y en lo alto del gráfico viene del reflejo sobreexpuesto del
grillete del candado. Y por fin, el cambio abrupto en la línea blanca,
en la parte izquierda del *AFO*, es la representación del gran contraste
existente entre el borde del marco de la puerta y la sombra densa entre
marco y puerta.

#### AFO por Canales («parade»)

<figure>
<img src="/images/parade.jpg" title="parade.jpg" />
<figcaption>parade.jpg</figcaption>
</figure>

Se trata del mismo análisis anterior, pero con los canales de color
separados en tres gráficos contíguos.

De esta forma se puede apreciar mejor qué pasa con cada canal, sin que
se mezclen colores ni unos canales enmascaren a otros, aunque es algo
más complicado identificar una columna de un canal en la zona
correspondiente de la imagen, al ser los gráficos más estrechos.

En el ejemplo se ve que la zona sobreexpuesta del candado corresponde a
los canales verde y azul.

#### Vectorscopios («vectorscopes»)

Los *vectorscopios* son representaciones gráficas de los colores de los
píxeles de la imagen. Cada píxel se representa como un punto blanco
situado en la posición del gráfico con el color y saturación del píxel.

De la misma forma que ocurría en el *AFO*, los *vectorscopios* se
calculan en función de los tonos resultantes en la imagen exportada, es
decir, en base al [perfil de
salida](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md).

En RawTherapee hay dos tipos de *vectorscopio*:

- el ***Vectorscopio H-S***: que muestra los colores de los píxeles
  según el [espacio de color
  HSL](https://es.wikipedia.org/wiki/Modelo_de_color_HSL). Los colores
  más saturados se sitúan en la periferia del gráfico, que representa
  los límites del *espacio de color de salida* y es útil para estimar la
  cantidad de píxeles que están fuera del rango de colores (*«gamut»*),
  o están a punto de salir de rango.
- el ***Vectorscopio H-C***: que muestra los colores según el [espacio
  de color
  Lch](https://sensing.konicaminolta.us/mx/blog/entiendiendo-el-espacio-de-color-cie-lch/).
  Es útil para estimar la saturación de los colores tal y como la
  percibimos con nuestros ojos, es decir, cómo de «intensos» o «lavados»
  nos parecerán los colores. Cuanto más hacia la periferia están los
  puntos blancos, más saturados están los colores.

La saturación se puede entender como la cantidad de color que hay en un
matiz, en relación al máximo de color (al matiz más «puro»). Es decir,
el porcentaje de color puro que tiene el color que observamos. El humano
«de a pie» suele entender los «colores» como el matiz con un 100% de
saturación. Y en los espacios de color utilizados en los vectorscopios
estos «colores» se encuentran en la periferia de sus rangos de colores
(de manera similar a lo que ocurre en el diagrama CIExy). La diferencia
entre HSL y Lch es que este último representa los colores de una forma
más parecida a como nosotros «lo vemos».

En el ***Vectorscopio H-S*** los colores saturados al 100% (o casi) se
sitúan en la periferia del círculo como manchas blancas, indicando
colores que están completamente saturados o que ya han sido recortados.
Los círculos concéntricos del gráfico señalan una saturación del *25%*,
el *50%*, el *75%* y el *100%* (en el círculo exterior). Este
vectorscopio es una buena forma de ver qué cantidad de píxeles están
fuera de rango (o casi) del espacio de color incluído en el *perfil de
salida*.

<div>

- <figure>
  <img src="/images/HSvectorscope.jpg"
  title="En este vectorscopio verás que hay 3 ejes que señalan los colores rojo, amarillo, verde, cian, azul y magenta.  En el análisis de la imagen se muestran los píxeles saturados sobre el círculo más grande, entre los colores amarillo y rojo (arriba a la derecha).  El resto de píxeles están repartidos y con «cantidades de color» (saturación) diferentes, representados como zonas blancas de un color más o menos vivo, dependiendo de la cantidad de píxeles en esa zona."
  height="712" />
  <figcaption>En este vectorscopio verás que hay 3 ejes que señalan los
  colores rojo, amarillo, verde, cian, azul y magenta.<br />
  <br />
  En el análisis de la imagen se muestran los píxeles saturados sobre el
  círculo más grande, entre los colores amarillo y rojo (arriba a la
  derecha).<br />
  <br />
  El resto de píxeles están repartidos y con «cantidades de color»
  (saturación) diferentes, representados como zonas blancas de un color
  más o menos vivo, dependiendo de la cantidad de píxeles en esa
  zona.</figcaption>
  </figure>

- ![](HSvectorscope_OOG.jpg "HSvectorscope_OOG.jpg") verás una máscara
  de color cian que resalta los píxeles *fuera de rango*.\]\]

</div>

En el ***Vectorscopio H-C*** los círculos concéntricos representan los
valores 32, 64, 96 y 128 de croma («color»). Cuanto más hacia la
periferia se sitúe un color, más saturado estará, con la peculiaridad de
que este gráfico es más intuitivo para valorar la saturación.

Los valores de croma se calculan en base a los valores *a\** y *b\** de
las coordenadas L\*a\*b\* que puedes ver en el panel del *Navegador*,
mediante la fórmula:
<img src="/images/chroma.png" title="chroma.png" height="36" alt="chroma.png" />

<figure>
<img src="/images/HCvectorscope_OOG.jpg"
title="En este ejemplo ves los colores más saturados llegando aproximadamente al valor 85. En concreto son los tonos rojos y amarillos.  Sin embargo ten en cuenta que la forma tridimensional de los espacios de color no es uniforme (no son «esferas» o «cubos») y por esto para estimar correctamente los colores recortados debes combinar más de un método de análisis.  Además puedes ver una línea diagonal en la parte superior derecha: esta línea indica los colores de piel del humano caucásico medio. En un retrato, situando el puntero del ratón sobre un tono medio de piel, el gráfico debería marcar el píxel alrededor de esta línea. En caso contrario, hay una dominante de color sobre el tono de la piel que te interesaría eliminar."
width="900" />
<figcaption>En este ejemplo ves los colores más saturados llegando
aproximadamente al valor 85. En concreto son los tonos rojos y
amarillos.<br />
<br />
Sin embargo ten en cuenta que la forma tridimensional de los espacios de
color no es uniforme (no son «esferas» o «cubos») y por esto para
estimar correctamente los colores recortados debes combinar más de un
método de análisis.<br />
<br />
Además puedes ver una línea diagonal en la parte superior derecha: esta
línea indica los colores de piel del humano caucásico medio. En un
retrato, situando el puntero del ratón sobre un tono medio de piel, el
gráfico debería marcar el píxel alrededor de esta línea. En caso
contrario, hay una dominante de color sobre el tono de la piel que te
interesaría eliminar.</figcaption>
</figure>

### La Tira de contactos

Así como en la época de los rollos de película, los negativos y el
«cuarto oscuro» se realizaban [hojas de
contactos](https://es.wikipedia.org/wiki/Copia_por_contacto#La_hoja_de_contactos),
en RawTherapee tienes una fila con miniaturas de las fotos existentes en
la carpeta que tengas abierta. Y puesto que se trata de una sola fila y
no una hoja, le llamamos ***Tira de Contactos***.

Además está sincronizada con la imagen actualmente abierta, por lo que
puedes usar [atajos de teclado](keyboard_shortcuts/es) o
botones para pasar a la imagen anterior
(![](arrow2-left.png "arrow2-left.png")) o la siguiente
(![](arrow2-right.png "arrow2-right.png")) sin necesidad de volver a la
pestaña del *[Navegador de archivos](file_browser/es)*. E
incluso tiene su propia barra de herramientas, que se puede ocultar para
ahorrar espacio en pantalla: puedes hacer aparecer/desaparecer su barra
de herramientas sin cambiar la altura de la *Tira de contactos* (, útil
en ordenadores lentos), o puedes cambiar automáticamente la altura
dejando más espacio para la *Vista previa* ().

Sin embargo, sólo podrás ver la *Tira de contactos* si usas el [*Modo de
Editor de pestaña única*](#Modos_de_pestaña_del_Editor.md)
(***Preferencias \> General \> Disposición \> Disposición del
Editor***).

<figure>
<img src="/images/Rt_filmstrip_21_toolbar-visible.jpeg"
title="Rt_filmstrip_21_toolbar-visible.jpeg" />
<figcaption>Rt_filmstrip_21_toolbar-visible.jpeg</figcaption>
</figure>

<figure>
<img src="/images/Rt_filmstrip_21_toolbar-hidden.jpeg"
title="Rt_filmstrip_21_toolbar-hidden.jpeg" />
<figcaption>Rt_filmstrip_21_toolbar-hidden.jpeg</figcaption>
</figure>

### Los perfiles de procesamiento

La lista desplegable *Perfiles de procesamiento* te permite aplicar
[perfiles de
procesamiento](Sidecar_Files_-_Processing_Profiles/es.md)
incorporados o personalizados. Consulta el artículo [*Carpetas usadas
por RawTherapee*](File_Paths/es.md) para más información sobre
dónde residen estos *perfiles de procesamiento* en tu sistema.

**¡Pon atención al botón *Modo de procesamiento de perfiles*!**:

- Modo ***Rellenar***
  <img src="/images/Profile-filled.png" title="Profile-filled.png" height="26"
  alt="Profile-filled.png" />

  
Cuando el botón está activado verás el icono anterior. Al abrir un
perfil que no contenga información de todas las herramientas (lo que se
llama un *perfil parcial*), los valores que falten se completarán con
los valores predeterminados para las herramientas incorporados en el
código de RawTherapee.

Por ejemplo, si aplicas un *perfil parcial* que contiene solamente
ajustes de nitidez, todas las demás herramientas (como *Exposición*,
*Mapeo de tonos*, *Reducción de ruido*, *Cambiar tamaño*, etc.) pasarán
a tener sus valores predeterminados **y se aplicarán a la imagen**. Si
habías realizado algún tipo de procesado a la imagen con esas
herramientas, simplemente se sustituirán.

- Modo ***Preservar***
  <img src="/images/Profile-partial.png" title="Profile-partial.png" height="26"
  alt="Profile-partial.png" />

  
Si el botón está desactivado verás un icono con sólo dos entradas
resaltadas. Al abrir un *perfil parcial*, sólamente se aplicarán los
valores contenidos en el perfil, mientras que los que falten
permanecerán intactos.

Por ejemplo, si aplicas un perfil parcial que contiene solamente ajustes
de nitidez, sólo se aplicarán esos ajustes de nitidez y el resto de
herramientas se mantendrán sin cambios.

El estado de este botón será irrelevante si aplicas un perfil completo
(si contienen información de todas las herramientas), pero la mayoría de
perfiles incorporados en RawTherapee son parciales.

Dentro de la lista desplegable hay un perfil muy especial: el ***perfil
Neutro***. Se trata de un perfil que al aplicarlo reinicia todas las
herramientas dejándolas inactivas o con sus controles en estado neutro
(a *cero*). Aplicándolo puedes empezar desde cero con tu imagen, sin que
haya ningún procesado aplicado por defecto.

Y en esta misma zona verás una serie de iconos que te permitirán
*Guardar*, *Cargar*, *Copiar* y *Pegar* perfiles de procesamiento. Al
usarlos emplearás el modo *Rellenar*, es decir, se guardará la
información de todas las herramientas y sus valores.

Si quieres trabajar con *perfiles parciales*, deberás usar los botones
con la tecla (es decir,  +
<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" />). Así, en todos los casos verás un diálogo
**donde poder elegir qué herramientas se incluirán en el perfil** a la
hora de guardarlo, cargarlo y aplicarlo a la imagen, copiarlo en el
portapapeles, o pegarlo en una imagen nueva.

### La Caja de herramientas

La *Caja de herramientas*, en el panel derecho, contiene todas las
herramientas que utilizarás para procesar tus fotos.

Cada herramienta tiene su propio artículo en RawPedia y puedes acceder a
todos ellos desde [el índice principal](main_page/es).

## Modos de pestaña del Editor

De forma predeterminada, RawTherapee se abrirá en el modo ***Editor de
pestaña única, pestañas verticales***, que es más eficiente en términos
de consumo de memoria y permite el uso de la *Tira de contactos*
([descrita anteriormente](#la_tira_de_contactos)).

Sin embargo RawTherapee te permite trabajar sobre las fotos en cuatro
modos:

- ***Modo de Editor de pestaña única***: en el que trabajas solamente en
  una foto y cada foto nueva se abre en la misma pestaña *Editor*
  (cerrando la imagen que hubiese abierta). Las pestañas principales de
  RawTherapee las verás en la parte superior de la ventana, justo debajo
  de la barra de título de la aplicación. Permite el uso de la *Tira de
  contactos*.
- ***Modo de Editor de pestaña única, pestañas verticales***: igual que
  el anterior, pero las pestañas están en el margen izquierdo de la
  aplicación.
- ***Modo de Editor de pestañas múltiples***: la *[Tira de
  contactos](#La_Tira_de_contactos.md)* está oculta en este modo
  y no hay botones anterior/siguiente
  (![](arrow2-left.png "arrow2-left.png")
  ![](arrow2-right.png "arrow2-right.png")). Las pestañas principales
  están en la parte superior y cada foto abierta tiene su propia
  pestaña, pero si cierras todas las imágenes abiertas, no abrá pestaña
  de *Editor*. Si abres varias fotos al mismo tiempo, necesitarás más
  memoria RAM.
- ***Modo de Editor de pestañas múltiples en su propia ventana***: es
  similar al modo anterior, pero las pestañas del *Editor* se abren en
  una nueva ventana independiente del resto del programa. Esto es muy
  útil para situar el *Navegador de archivos* en un monitor y las fotos
  que quieras editar en otro monitor distinto.

Puedes cambiar al modo que desees en ***Preferencias \> General \>
Disposición \> Disposición del Editor***. **Pero no olvides reiniciar
inmediatamente el programa, o las pestañas harán cosas extrañas hasta
que lo hagas**.
