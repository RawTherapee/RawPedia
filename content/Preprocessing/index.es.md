---
title: Preprocessing
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Procesado Previo

</div>
<div class="headline">

Operaciones previas al desentramado de la imagen

</div>

## Introducción

Antes de efectuar el [*desentramado*](demosaicing/es) de la
foto, RawTherapee realiza una serie de pasos previos que preparan los
datos para convertirlos a RGB.

En general estos preparativos sólo son aplicables a sensores con [filtro
de Bayer](https://es.wikipedia.org/wiki/Mosaico_de_Bayer), a excepción
de la [supresión de píxeles «muertos» o
bloqueados](#Filtro_de_píxeles_bloqueados.2Fdañados.md), que
funciona también con los [sensores
X-Trans](https://en.wikipedia.org/wiki/Fujifilm_X-Trans_sensor).

Hay varios ajustes de *procesado previo* y están divididos en dos partes
en la interfaz de usuario (ambas en la pestaña *Raw*): una parte aparece
como la herramienta ***Procesado previo**'' principal (que afecta a
archivos raw de todos los tipos) y la otra aparece dentro de la
herramienta***Sensor con matriz de Bayer**'' (que sólo afecta a archivos
raw de cámaras con filtro de Bayer).

## Procesado previo en sensores con matriz de Bayer

### Filtro de ruido en bandas

El *ruido en bandas* es un tipo de distribución del ruido, que aparece
en la imagen como bandas horizontales y/o verticales y es especialmente
visible en las zonas oscuras.

Es debido al ruido generado por la electrónica interna y la que rodea al
sensor durante el proceso de lectura del valor de cada fotodiodo, línea
por línea o columna por columna. Es un problema complejo y muy
particular de cada modelo de cámara: por ejemplo es típico en
determinadas cámaras Canon, mientras que es casi inexistente en algunas
cámaras Nikon. Sin embargo no debes obsesionarte con él, ya que si no lo
ves en la foto, no tienes por qué intentar corregirlo (no es apreciable
en todas las fotos).

Puedes ver ejemplos del aspecto del ruido en bandas en [esta publicación
del foro de
*MagicLantern*](http://www.magiclantern.fm/forum/index.php?topic=10111.msg105001#msg105001).

En la herramienta podrás ver dos controles:

- ***Filtro de ruido en bandas***: un deslizador para establecer la
  intensidad del filtro. Escoge una zona de la foto donde se vean
  claramente las bandas y procura ir subiendo el valor del deslizador
  poco a poco hasta que las líneas o bandas desaparezcan.
- ***Dirección***: si escoges una dirección concreta el algoritmo se
  centrará en élla y evitarás la pérdida de detalles a causa del
  filtrado. Los valores posibles son *Horizontal*, *Vertical*, *Ambos*
  (valor por defecto) y *Horizontal únicamente en líneas EADF*.

<div>

- <figure>
  <img src="/images/banding_original.jpg" title="banding_original.jpg" />
  <figcaption>banding_original.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/banding_horizontal.jpg" title="banding_horizontal.jpg" />
  <figcaption>banding_horizontal.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/banding_vertical.jpg" title="banding_vertical.jpg" />
  <figcaption>banding_vertical.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/banding_both.jpg" title="banding_both.jpg" />
  <figcaption>banding_both.jpg</figcaption>
  </figure>

</div>

### Equilibrado de verdes

<figure>
<img src="/images/645D_amaze_crosshatch_pattern.jpg"
title="645D_amaze_crosshatch_pattern.jpg" />
<figcaption>645D_amaze_crosshatch_pattern.jpg</figcaption>
</figure>

Los sensores de algunas cámaras (por ejemplo Olympus, Panasonic, Canon
7D y algunas cámaras de formato medio) usan filtros verdes levemente
diferentes en los dos canales verdes del [mosaico de filtros de
color](https://es.wikipedia.org/wiki/Mosaico_filtro_de_color).

Habitualmente esto no es una característica de diseño, sinó más bien el
resultado de un proceso de fabricación impreciso cuando se aplican los
filtros de color a la superficie del sensor. Por ejemplo, un filtro
verde puede recibir una pequeña contaminación del filtro rojo, y el otro
filtro verde contaminarse del filtro azul.

El ***Equilibrado de verdes*** suprime los artefactos de interpolación
producidos por los algoritmos de desentramado que asumen una respuesta
idéntica de los dos canales de verde. El deslizador fija el umbral de
diferencia entre valores verdes vecinos, estableciendo un porcentaje por
debajo del cual se equilibrarán esos valores.

Ajusta un valor lo suficientemente alto para que desaparezca el
reticulado, pero no mayor. El algoritmo de desentramado DCB es muy
sensible a la separación de verdes, por lo que es bueno usarlo para
tratar de encontrar el mejor valor.

El equilibrado de verdes también se puede usar para corregir la
*«separación de verdes»* causada por la *diafonía*: por ejemplo, si usas
un objetivo gran angular de una cámara de película montado en tu cámara
digital, la luz entrante podría llegar con un ángulo tan bajo, que algo
de luz pasaría por un filtro de color y sería captada en un píxel vecino
que pertenece a un canal de color diferente. Esto es la *diafonía*.

Como uno de los canales verdes tiene vecinos azules y el otro canal
verde tiene vecinos rojos, el primero recibirá diafonía del azul, y el
segundo del rojo. De ahí que se «separen» y puedan producir reticulados.
En esta situación, también los canales rojo y azul sufrirán diafonía,
pero como sólo se contaminarán de verde, no habrá «separación» en esos
canales (todos los rojos estarán igualmente teñidos de verde y todos los
azules estarán teñidos sólo de verde).

La diafonía leve no tendrá ningún efecto visible si se equilibran los
verdes, mientras que la diafonía intensa aparecerá como colores tenues y
desaturados (ya que los canales de colores han sido mezclados). Observa
que en general la diafonía no se produce sin una fuerte dominante de
color, por lo que en este caso también te interesará usar la
[*Corrección de campo plano*](flat-field/es).

### Filtro para líneas de Enfoque Automático por Detección de Fase (EADF)

<figure>
<img src="/images/Pdaf_lines_filter_sony.png" title="Pdaf_lines_filter_sony.png"
width="785" />
<figcaption>Pdaf_lines_filter_sony.png</figcaption>
</figure>

Las cámaras con *Enfoque Automático por Detección de Fase (EADF)* son
propensas a producir artefactos de tiras de líneas al fotografiar
escenas con contraluz y destellos visibles. Algunas cámaras Sony *sin
espejo con objetivos intercambiables* (conocidas como [*EVIL*, *DSLM* o
*Mirrorless*](https://es.wikipedia.org/wiki/C%C3%A1mara_sin_espejo_de_objetivos_intercambiables))
son conocidas por sufrir este problema.

Activa el ***Filtro para líneas de EADF*** para corregir o disimular
estos artefactos.

### Bandas por EADF en cámaras Nikon

Varias cámaras Nikon *sin espejo con objetivos intercambiables* usan el
*Enfoque Automático por Detección de Fase* (*EADF)* y como el resto de
cámaras con esta tecnología generan líneas en las imágenes. Sin embargo
en este caso las cámaras realizan un filtrado para mitigar los
artefactos de las bandas de EADF.

El problema es que este filtrado interno resulta excesivo y produce
**bandas por EADF**: líneas más oscuras en áreas de sombra.

<figure>
<img src="/images/Pdaf_banding_nikon.png" title="Pdaf_banding_nikon.png"
width="811" />
<figcaption>Pdaf_banding_nikon.png</figcaption>
</figure>

Con estas cámaras la casilla *Filtro de líneas EADF* no corrige las
bandas de EADF, por lo que tendrás que usar el ***Filtro de ruido en
bandas**'' para reparar los artefactos en bandas de EADF con la
dirección puesta a***Horizontal sólo en líneas EADF**''.

## Procesado previo en todo tipo de sensores

Cualquier tipo de sensor puede sufrir fallos en la electrónica y acabar
con píxeles que no responden a los cambios de luminosidad. RawTherapee
puede tratar de corregir estos píxeles automáticamente, o a través de un
fichero que los localiza uno tras otro.

### Filtro de píxeles bloqueados/dañados

<figure>
<img src="/images/Rt-43_hotdead1.jpg" title="Rt-43_hotdead1.jpg" width="646" />
<figcaption>Rt-43_hotdead1.jpg</figcaption>
</figure>

Esta herramienta suprime [píxeles bloqueados y
muertos](https://es.wikipedia.org/wiki/Píxel_muerto), reemplazándolos
por un promediado de los píxeles vecinos.

Los **píxeles bloqueados** aparecen como puntos brillantes y saturados.
Cada uno de ellos es el resultado de un fotodiodo del sensor produciendo
una respuesta mayor de lo que debería.

El tamaño y forma de estos puntos depende del método de *desentramado*
elegido, entre otras herramientas. Por ello los *píxeles bloqueados* no
sólo aparecen como puntos de un único píxel, sinó también como pequeñas
cruces de 3x3 píxeles, o gotas ligeramente mayores.

Los píxeles bloqueados están presentes en todas las cámaras, pero lo
habitual es que sólo los veas en fotografías de larga exposición. En
general las exposiciones mayores que **dos segundos** son propensas a
tener este problema. También los verás en sensores que se calientan.

Por otra parte, los **píxeles «muertos»** aparecen como puntos negros (o
cruces, o gotas).

Son el resultado de fotodiodos averiados en el sensor y por tanto el
tiempo de exposición no tiene ninguna influencia sobre ellos: si un
fotodiodo está averiado todas las fotos tendrán el *píxel «muerto»* en
el mismo lugar.

Debido a que su posición es estática y siempre están presentes si se usa
el mismo cuerpo de cámara, se pueden corregir no sólo usando el *Filtro
de píxeles bloqueados/dañados* automático, sinó también añadiendo sus
coordenadas a un archivo *.badpixels* como se explica a continuación.

### Listado de píxeles defectuosos

RawTherapee puede corregir las imágenes de cada modelo de cámara
mediante una lista de ***píxeles defectuosos*** (píxeles que siempre son
negros, blancos, o se han bloqueado en un color). Para ello necesita
leer un archivo de texto con las coordenadas raw absolutas de estos
píxeles: **cada línea especifica un píxel con sus posiciones
`x`<space>`y`<Intro>** (primero la columna, después un espacio blanco, a
continuación la fila y para acabar el final de línea o *Intro*).

Nota Importante: por defecto RawTherapee recorta algunos píxeles
alrededor de los bordes de la imagen raw (ya que no pueden interpolarse
correctamente), así que si obtienes las coordenadas de píxel a partir de
una imagen exportada por RawTherapee, ten cuidado con el desplazamiento
introducido por este recorte. **Debes sumar 4 a cada coordenada para
sensores Bayer y 7 para sensores X-Trans**. O como alternativa puedes
especificar el desplazamiento (`4` para Bayer, `7` para X-Trans) en la
primera línea del texto (añade el número adecuado y después el final de
línea o *Intro*).

**El archivo debe estar situado en tu [*carpeta de imágenes de negro
base*](Preferences/es#Carpetas.md) (en *Preferencias \>
Procesamiento de imágenes \> Imagen de negro base*) y nombrarlo
exactamente como la marca y modelo de tu cámara:
*`marca modelo.badpixels`***.

Averigua cómo nombra RawTherapee la cámara abriendo una imagen raw que
desees corregir en el *Editor* y, tras activar la *Información rápida*
(<img src="/images/info.png" title="info.png" width="22" alt="info.png" />),
mira la marca y modelo que se muestra superpuesta a la imagen. Por
ejemplo: `Pentax K200D.badpixels`.

Si tienes fotos de dos cámaras del mismo modelo, también puedes
especificar los números de serie de cada cámara para distinguirlas
(búscalos en los datos *Exif*):  
***`marca modelo serie.badpixels`***.

Si has seguido los pasos correctamente y el programa aún no reconoce el
listado, puedes verificar si está leyendo tu archivo *`.badpixels`*:

- cierra RawTherapee
- edita el archivo
  [*options*](file_paths/es#la_carpeta_con_las_configuraciones)
  en un editor de texto y cambia *Verbose=false* a ***Verbose=true***
- [arranca RawTherapee desde la consola de
  comandos](Command-Line_Options/es#Arrancar_la_interfaz_gráfica_de_RawTherapee.md)
- abre la foto que quieres corregir y observa la salida de texto en la
  consola: si ves un mensaje similar a ***Pentax K10D.badpixels not
  found***, entonces deberás anotar el nombre exacto que necesita
  RawTherapee (incluyendo espacios en blanco) y cambiar el nombre del
  archivo *`.badpixels`*
- cuando funcione correctamente, recuerda cambiar de nuevo a
  *Verbose=false*

Los píxeles de la *lista de píxeles defectuosos* siempre se corregirán
en todas las fotos procesadas, en tanto la marca y modelo de la cámara
coincidan con el nombre del archivo *`.badpixels`*.

### Programas para la detección de píxeles defectuosos

Existen programas de ayuda para la detección y generación de la lista de
todos de píxeles defectuosos:

Dead Pixel Test  
  
<http://www.starzen.com/imaging/deadpixeltest.htm> (sitio web original,
actualmente inexistente)

Sitio web espejo:
<https://web.archive.org/web/20140725130003/http://www.starzen.com/imaging/deadpixeltest.htm>

Aplicación: <http://rawtherapee.com/mirror/deadpixeltest.zip> *(Este
archivo está [libre de
virus](https://www.virustotal.com/en/file/11e7a0db897fd3ad9f3e24c97c73b178cfe9f9d246e3dadfe57113318e2def06/analysis/1421736881/))*.

Pixel Fixer  
  
<http://www.pixelfixer.org/>

*Recuerda tener en cuenta el desplazamiento del recorte de 4 ó 7 píxeles
si es necesario*.

### El umbral de detección automática

<figure>
<img src="/images/Rt-43_hotdead2_artifacts.jpg"
title="Rt-43_hotdead2_artifacts.jpg" width="969" />
<figcaption>Rt-43_hotdead2_artifacts.jpg</figcaption>
</figure>

Dado que analizando sólo una foto es imposible detectar los píxeles
bloqueados y «muertos» con absoluta certeza (a diferencia de analizar
una serie entera de fotos), hay que encontrar el equilibrio entre la
corrección adecuada y los [falsos
positivos](https://es.wikipedia.org/wiki/Falso_positivo_y_falso_negativo).

El deslizador de ***Umbral*** te permite ajustar la sensibilidad de la
detección automática: los valores bajos hacen que la detección sea más
agresiva, pero los falsos positivos pueden producir artefactos. Si
observas que aparece cualquier artefacto al activar el *Filtro de
píxeles bloqueados/dañados*, aumenta gradualmente el valor del *Umbral*
hasta que desaparezcan.
