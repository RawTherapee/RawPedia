---
title: Bit Depth es
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Profundidad de bits

</div>
<div class="headline">

La codificación de las imágenes según la definición que deban tener los
colores.

</div>

## Introducción

A menudo escucharás o leerás términos como *«8-bit»*, *«16-bit»*,
*«24-bit»*, *«32-bit»*, *«64-bit»* y *«96-bit»* al hacer referencia a
imágenes digitales: están relacionados con la cantidad máxima de colores
distintos que puede contener una foto.

Cada píxel de una imagen digital puede contener uno o más canales de
color: las imágenes *en escala de grises* sólo necesitan un canal *(un
valor de 0 podría representar el negro puro, 255 podría representar el
blanco puro y los valores intermedios representarían tonos grises entre
el blanco y el negro)*, mientras que por ejemplo las imágenes *en color
RGB* necesitan tres canales *(uno define el rojo, otro el verde y otro
el azul)*. Por otro lado, el valor de cada canal define sólo la
intensidad de un color, mientras que el color del píxel resulta de la
combinación de los tres canales (según el [Modelo de Color
RGB](https://es.wikipedia.org/wiki/RGB)), por lo que no hay nada
intrínsecamente verde en el número del canal verde de un píxel. Ese
número simplemente indica que el pixel tiene una parte de tres que es
verde.

Y aunque en general pensemos en 3 canales por píxel, este podría constar
de más de tres canales: por ejemplo podría contener información sobre un
canal *«alfa»* (que describe la transparencia) o un canal *infrarrojo*
(que algunos escáneres soportan).

Resumiendo, cuanto mayor sea la profundidad de bits en que una imagen se
codifique, mayores podrán ser los números de cada canal, mayor será la
cantidad de combinaciones posibles entre esos canales y por tanto, con
más precisión se podrá definir un color, a costa de exigir cálculos más
largos, más memoria RAM y más espacio de almacenamiento.

## Bits por..., ¿qué?

La profundidad de bits se expresa como la cantidad de bits de
información necesarios para escribir los datos de color: **bits por
píxel** (BPP) indica la cantidad de bits necesarios para guardar toda la
información del color de un píxel, mientras que **bits por canal** (BPC)
indica los bits necesarior para guardar la información de un solo canal
de color.

Un ejemplo: el [formato
JPEG](https://es.wikipedia.org/wiki/Joint_Photographic_Experts_Group)
suele guardar las imágenes con una precisión de 8 bits por canal,
utilizando tres canales, para un total de 24 bits por píxel. El [formato
TIFF](https://es.wikipedia.org/wiki/TIFF) admite varias profundidades de
bits, por ejemplo 32 bits por canal para un total de 96 bits por píxel.

Lo recomendable es que al nombrar la profundidad de bits, indiques lo
que estás describiendo para no dejar lugar a dudas. Ejemplo de
ambigüedad: si alguien dice que *tiene una imagen de «32 bits»*,
¿significa que la imagen tiene *32 bits por canal*, o que tiene *4
canales de 8 bits* cada uno?

## La precisión de los colores

En la práctica, para nuestras imágenes, ¿qué diferencia hay entre una
profundidad de bits y otra?: **cuantos más bits se empleen para definir
un color, más parecido será el color digital al color real**.

La profundidad de bits afecta principalmente a las sombras, debido a la
forma en que se codifican los colores: cada color está definido mediante
una mezcla de rojo, verde y azul. Poniendo como ejemplo una imagen de 8
bits y el color naranja, pueden escogerse muchos valores cuando se
codifica el naranja brillante, pero hay muy pocos valores disponibles
para codificar el naranja oscuro; es decir, sólo los 3-4 valores más
bajos de cada canal pueden ser usados para definir (codificar) el
naranja oscuro, lo cual significa que sólo existen unos pocos valores
posibles para codificar todo un rango de tonos oscuros.

**Cuanto mayor sea la profundidad de bits, más colores se pueden definir
y se evita la
[posterización](https://es.wikipedia.org/wiki/Posterización).**

Con números:

- Una precisión de 1 bit por canal significa que **sólo hay 1 bit para
  establecer un valor**. Un bit solo puede ser 0 o 1, por lo que sólo se
  pueden establecer dos valores, que normalmente significarán **blanco o
  negro**.
- Una precisión de 2 bits por canal significa que **hay 2 bits
  disponibles para establecer el valor de cada canal**. Como hay dos
  bits y cada uno puede ser 0 o 1, **hay un total de 4 valores
  posibles**:

<!-- -->

     [00] = 0
     [01] = 1
     [10] = 2
     [11] = 3

  
Si usamos *0* para representar el negro y *3* para representar el
blanco, hay dos tonos adicionales de gris que se pueden establecer.

- Una precisión de 8 bits por canal significa que **hay 8 bits que
  pueden establecer hasta 256 valores**:

<!-- -->

     [0000 0000] = 0
     [0000 0001] = 1
     (...)
     [1111 1110] = 254
     [1111 1111] = 255

  
Si usamos *0* para representar el negro y *255* para representar el
blanco, nos quedan 254 valores para establecer los tonos de gris
posibles. Esto es lo que usan los archivos JPEG: 8 bits por canal, con 3
canales de color.

- *En general es suficiente si utilizas esta profundidad para guardar
  tus fotografías en el [Espacio de color
  sRGB](https://es.wikipedia.org/wiki/Espacio_de_color_sRGB)*, sin
  posterización visible. Así que, obviamente puedes usarla cuando
  guardes las fotografías que ya estén listas para que las vean a través
  de internet.
- Sin embargo, *esta profundidad de bits no es adecuada para fotografías
  que no estén acabadas de procesar* (lo que se suele llamar **formato
  intermedio**), ni para fotografías acabadas (o **formato final**)
  cuando existe la posibilidad de que tengas que modificar la fotografía
  en un futuro, ya que corres el riesgo de introducir artefactos de
  posterización dependiendo de la intensidad de los ajustes que pudieras
  realizar.
- *Una profundidad de 8 bits no es suficiente para reproducir una escena
  de alto rango dinámico* con gamma lineal y sin posterización. Es
  decir, en teoría se podrían utilizar 8 bits para describir una escena
  de alto rango dinámico con una gama lineal, pero los tonos asignados a
  cada valor estarían tan separados que se produciría una enorme
  posterización. Por ejemplo, supongamos que en una fotografía capturas
  un día soleado en el campo, con una relación de contraste de
  1.000.000:1. Si decides que el negro debe ser el 0 y el blanco el
  nivel de contraste 1.000.000, podrías asignar el valor 0 al 0 y el
  valor 255 al 1.000.000; sin embargo, entonces sólo quedarían 254
  valores de la codificación en 8 bits, a los que tendrías que asignar
  el resto de 999.999 niveles de contraste de la escena original.

- Una profundidad de 16 bits por canal (con números enteros) significa
  que **tenemos números binarios con 16 ceros y/o unos**. Con las
  combinaciones posibles **se pueden establecer 65536 valores**:

<!-- -->

     [0000 0000 0000 0000] = 0
     [0000 0000 0000 0001] = 1
     (...)
     [1111 1111 1111 1110] = 65534
     [1111 1111 1111 1111] = 65535

  
Las cámaras digitales suelen capturar la luz con una profundidad de 12 ó
14 bits, pero debido al ruido y a la imprecisión de la electrónica, los
valores más bajos son de dudosa calidad. 16 bits por canal son
suficientes para la mayoría de las necesidades fotográficas, incluyendo
el uso en *formatos intermedios* (si deseas pasar una imagen de un
programa a otro sin pérdida de detalles).

- La profundidad de 16 bits [en coma
  flotante](https://es.wikipedia.org/wiki/Coma_flotante), también
  conocida como [coma flotante de media
  precisión](https://en.wikipedia.org/wiki/Half-precision_floating-point_format),
  se distribuyen de una manera más adecuada para el muestreo de luz que
  la misma imagen en 16 bits con números enteros. Su representación
  binaria ya no se realiza simplemente con **0** y **1** y **puede
  establecer valores entre -65504 y +65504**.

  
La mayor precisión de los números *en coma flotante* se debe a que:

- la visión humana es más sensible a pequeños cambios en los tonos
  oscuros que a pequeños cambios en los tonos brillantes;
- nuestros ojos responden a la luz de una manera logarítmica *(la luz
  debe ser 10 veces más intensa para que podamos verla el doble de
  brillante)*;
- los reflejos especulares, que pueden ser los elementos más brillantes
  de una escena (por ejemplo, el sol reflejándose en el pomo de una
  puerta), no necesitan ser definidos con la misma precisión que los
  demás tonos;
- en la notación en coma flotante de 16 bits, **los valores se
  distribuyen más apretadamente en los tonos más oscuros** (valores más
  bajos) que en los más claros (valores altos), lo que permite una
  definición más precisa de los tonos más relevantes para nuestros ojos.

- Una imagen de 32 bits [en coma
  flotante](https://es.wikipedia.org/wiki/Coma_flotante) **puede
  representar 4.300 millones de valores por canal** y requiere
  aproximadamente el doble de espacio en disco que una imagen de 16
  bits. Sus altos requerimientos de procesador, memoria y espacio en
  disco provocan que pocos programas sean compatibles con las imágenes
  de 32 bits.

## La Gamma y la profundidad de bits

La [codificación gamma](https://es.wikipedia.org/wiki/Corrección_gamma)
puede utilizarse al guardar las imágenes, de manera que al usarla los
valores se modificarán asignando más cantidad en el rango de las sombras
que en el rango de las luces. Esto es importante en codificaciones de 8
bits, porque se respetan los tonos oscuros al asignarles artificialmente
más valores para codificarlos (lo cual se ajusta mejor a la sensibilidad
que tiene el ojo humano: apreciamos mejor los cambios de tono en las
zonas oscuras).

Con este artificio se consigue que un JPEG de 8 bits pueda mostrar hasta
<img src="/images/gamma_log.png" title="gamma_log.png" width="153"
alt="gamma_log.png" /> pasos de rango dinámico, lo cual excede los 14
pasos de las mejores cámaras actuales. Esto explica por qué a veces se
puede ver el ruido de las sombras de una cámara incluso en un JPEG de 8
bits.

Sin embargo, debido a la distribución no lineal de los valores (mayor
densidad de valores en las sombras, menor densidad en la luces),
perdemos precisión en las zonas brillantes en comparación con el archivo
raw (con los valores grabados de forma lineal por la cámara). De todas
formas en la práctica esto no es un problema siempre que el archivo
generado sea el definitivo y que no se vaya procesar más.

Por otra parte, **cuando guardes con tasas de bits más altas** y
especialmente con precisión de *coma flotante*, la gamma puede llegar a
ser contraproducente y **será mejor que emplees una gamma lineal**
(*1.0*).

## Si sigues con el procesado después de RawTherapee

Una vez que hayas procesado una foto en RawTherapee y te dispongas a
[guardarla](saving_images/es), siempre tendrás la misma duda:
qué formato de archivo, qué profundidad de bits por canal, [qué perfil
de color](Color_Management/es#El_perfil_de_salida.md) y [qué
gamma](Color_Management/es#La_corrección_gamma.md) usar.

**Si después de exportarlas en RawTherapee piensas postprocesar tus
fotos en un programa de edición de imágenes de 16 bits, es mejor
guardarlas en un formato de 16 bits sin pérdidas (*lossless*)**.

RawTherapee puede guardar imágenes con una precisión de 16 bits con
números enteros (denominada "TIFF (16-bit)" o "PNG (16-bit)" en el
cuadro de diálogo Guardar), así como con una precisión de 16 bits en
coma flotante (denominada "TIFF (16-bit float)") y hasta con 32 bits en
coma flotante. **El formato TIFF sin comprimir de 16 bits con números
enteros es el recomendado como formato intermedio**, ya que es el más
rápido de guardar en el disco y además es ampliamente aceptado
(soportado) por otros programas. Los archivos de 32 bits tienen
aproximadamente el doble de tamaño y no son bien soportados por otros
programas.
