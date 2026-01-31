---
title: Dark-Frame
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Imagen de Negro Base

</div>
<div class="headline">

Imagen para eliminar el ruido que no corresponde a la escena
fotografiada

</div>

## Introducción

El **negro base** es la imagen más oscura que es capaz de generar el
sensor y depende de su diseño y de la electrónica que le acompaña.

Mediante la [substracción del *negro
base*](https://es.wikipedia.org/wiki/Campo_oscuro) mejorarás las
imágenes corrigiendo el [ruido
térmico](https://es.wikipedia.org/wiki/Ruido_de_Johnson-Nyquist), el
[ruido de corriente de
oscuridad](https://es.wikipedia.org/wiki/Corriente_de_oscuridad) y el
[ruido de patrón
fijo](https://es.wikipedia.org/wiki/Sensor_CMOS#Comparación_con_otros_sensores).
Sin embargo no es efectivo contra el ruido de [valores
ISO](https://es.wikipedia.org/wiki/Escala_de_sensibilidad_fotográfica)
altos, debido a la diferente naturaleza aleatoria de este.

## La herramienta

Si bien los otros tipos de ruido son estables, el ruido térmico no es
homogéneo y aumenta con el incremento de la exposición y para mitigar
este efecto puedes captar una (o más) fotos realizadas en las mismas
condiciones que el resto, pero con la tapa del objetivo puesta.
Básicamente se trata de tomar fotos sin captar ninguna escena.

Las limitaciones de esta herramienta son que sólo se pueden usar como
imágenes de *negro base* aquellas captadas con el mismo modelo de cámara
y preferiblemente tomadas en torno al mismo momento y con los mismos
ajustes que la foto de la que han de ser substraídas. Como todo esto
simplemente es cuestión de poner la tapa del objetivo y pulsar el
disparador sin cambiar ningún ajuste de la cámara, no debería suponer
ningún problema.

Además, puedes incluir una o varias *tomas negras*, pero RawTherapee
sólo extrae de éllas todas las posiciones con píxeles bloqueados, es
decir, blancos. Los pixeles muertos (negros) no se consideran, aunque
siempre es mejor esto que usar sólo el [*Filtro de píxeles
bloqueados/muertos*](Preprocessing/es#Filtro_de_píxeles_bloqueados.2Fdañados.md).

Si quieres seleccionar una única imagen como *toma negra*, simplemente
selecciona la imagen raw adecuada con la herramienta.

En cambio con más de una toma RawTherapee calculará un promedio entre
ellas y esto reducirá mucho más el ruido, por lo que es mejor tomar 4-6
imágenes de *negro base* en las mismas condiciones que la foto
realizada.

Para usar varias tomas de *negro base* debes proceder como sigue:

- dentro de las *Preferencias*, escoge la [carpeta de *tomas de negro
  base*](Preferences/es#Carpetas.md) adecuada, dónde guardarás
  todas las *tomas negras* de todas tus fotos
- copia o mueve tus *tomas negras* a esta carpeta. Puedes hacerlo con el
  navegador de archivos de tu sistema operativo o en el *Navegador de
  archivos* de RawTherapee (clic derecho y selecciona *Imagen de negro
  base \> Mover a la carpeta de imágenes de negro base*)
- activa la casilla ***Selección automática*** y deja que RawTherapee
  escoja las fotos que encajan mejor con la foto que estás editando

## Método de búsqueda de las mejores tomas de Negro Base

RawTherapee escoge la mejor coincidencia entre la foto editada y su
imagen de *negro base* buscando la coincidencia exacta con:

- el fabricante de la cámara
- el modelo de cámara
- sensibilidad ISO usada
- velocidad de obturación

En caso de encontrar imágenes coincidentes, explora la lista buscando la
menor distancia temporal entre fotos.

Si encuentra más de una toma exactamente con las mismas propiedades,
usará un promedio entre éllas.

De lo contrario, si no se encuentran coincidencias explorará la lista
entera buscando la menor diferencia en ISO y velocidad de obturación.
