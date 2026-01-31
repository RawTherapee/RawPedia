---
title: RGB Curves
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Curvas RGB

</div>
<div class="headline">

Curvas de color para procesados avanzados

</div>

__TOC__

## Curvas de color para cada canal RGB

La herramienta ***Curvas RGB*** es una de las pocas herramientas que
puedes encontrar en casi cualquier programa de revelado o retoque
fotográfico.

Gracias a ella puedes realizar un ajuste fino sobre el color de la
imagen, hacer que las luces sean más cálidas o las sombras más frías,
ajustar los niveles de blancos o de negros, igualar los colores de una
secuencia de varias fotos, añadir una dominante de color a la foto
entera, aclarar u oscurecer una gama de colores, etc.

Para conseguirlo básicamente editarás la curva de cada canal, que
comenzará siendo una línea recta diagonal.

## Modo RGB

Es el modo por defecto.

Esencialmente, la línea diagonal de cada curva representa la luminosidad
de los píxeles en el eje horizontal y el tono que se añadirá a la foto
en el eje vertical.

Para realizar un ajuste simplemente haz clic
(<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" />) en el punto que desees del gráfico y
añadirás un punto de control a la línea diagonal. A continuación
desplázalo hacia arriba o hacia abajo: hacia arriba introducirás una
dominante del color del canal. Hacia abajo introducirás una dominante
del color complementario (en el canal rojo, dominante cián; en el canal
verde, dominante magenta; en el canal azul, dominante amarilla).

<figure>
<img src="/images/RGBcurves_tone.jpg" title="RGBcurves_tone.jpg" />
<figcaption>RGBcurves_tone.jpg</figcaption>
</figure>

Si necesitas una curva más precisa sobre un rango de luminosidades,
entonces sólo tienes que añadir más puntos de control sobre la curva y
ajustarlos convenientemente.

Para añadir puntos de control en zonas específicas de la imagen (y no en
zonas del gráfico, como se ha explicado antes), puedes usar el *selector
de color*
(<img src="/images/Crosshair-node-curve.png" title="Crosshair-node-curve.png"
width="22" alt="Crosshair-node-curve.png" />) como sigue: tras activar
el botón ves a la imagen y haz  +
<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" /> . Si sueltas el botón del ratón, añadirás
un punto de control en la curva. Si no sueltas el botón del ratón y
arrastras el puntero hacia arriba o hacia abajo, moverás simultáneamente
el punto de control recién creado hacia arriba o hacia abajo.

Si aún necesitaras un control más preciso de los puntos de control,
puedes activar la edición de los valores inicial y resultante de los
puntos de control mediante el botón
<img src="/images/Edit-point.png" title="Edit-point.png" height="26"
alt="Edit-point.png" /> . Tras activarlo, haz clic derecho
(<img src="/images/mouse_right-click.png" title="mouse_right-click.png"
height="26" alt="mouse_right-click.png" />) sobre el punto de control
que vayas a modificar. Entonces podrás introducir un valor de
luminosidad preciso en el campo «**E:**» y un valor modificado en el
campo «**S:**». Si el valor de ambos campos es el mismo, el punto de
control permanecerá sobre la diagonal (no habrá cambio alguno). Si el
valor resultante *S* es mayor que el inicial, el punto de control se
situará por encima de la diagonal y la imagen tendrá una dominante del
color del canal en el que estés trabajando. Si el valor de *S* es menor
que el inicial, el punto de control se situará por debajo de la diagonal
y la dominante será del color complementario al canal en el que estés
trabajando.

En cualquier caso, no es mala idea ajustar primero la *Exposición* antes
de hacer ninguna corrección de color.

## Modo luminosidad

Para activarlo debes activar la opción ***Modo luminosidad***.

El propósito de este modo es alterar la luminosidad de los canales RGB,
mientras se mantiene en lo posible el color de la imagen: al modificar
la curva de un canal, hasta cierto punto sólo cambiarán los tonos de ese
canal (los rojos en el canal rojo, etc) haciéndose más oscuros (el punto
de control hacia abajo) o más luminosos (el punto de control hacia
arriba). Sin embargo, será casi inevitable que el resto de colores
también cambien en cierta medida, puesto que normalmente serán mezclas
variables de los tres canales.

El efecto es, en cierto modo, similar a los cambios en el valor, *V*,
del [*Ecualizador HSV*](hsv_equalizer/es), pero es más suave
y afecta a una mayor extensión de matices, no siendo tan selectivo.

## Virajes clásicos en Blanco y Negro

Tal como se explica en la herramienta de [*Blanco y
Negro*](Black-and-White/es#Flujo_especial_de_trabajo_para_virajes_clásicos.md),
a la hora de recrear un viraje químico clásico es imprescindible el uso
de las *Curvas RGB*, pero mediante un flujo de trabajo específico.

Si estás interesado en esta técnica, no dejes de leer la documentación
sobre la herramienta de *Blanco y Negro*.
