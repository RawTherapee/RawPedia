---
title: Haze Removal
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Eliminación de neblina

</div>

## Introducción

El *«efecto neblina»* suele ser debido a haber captado una escena
brumosa, aunque también puede ser debido a disparar con un teleobjetivo
«largo» (de 200mm o más), o con un objetivo que ofrezca muy bajo
contraste (típico de objetivos muy antiguos y con menos correcciones
ópticas que los actuales).

A veces puedes querer eliminar completamente la neblina porque enmascara
la escena, aunque otras sólo querrás reducirla ligeramente porque añade
un toque «atmosférico» o artístico a la foto.

Con esta herramienta, al eliminar la neblina atmosférica normalmente
incrementarás la saturación y resaltarás el detalle.

Sin embargo aunque puede que quites dominantes de color, también puedes
añadir una dominante azul, o (según los ajustes) puede que introduzcas
areas con una coloración inexistente en la escena real.

<figure>
<img src="/images/haze_removal.jpg" title="haze_removal.jpg" />
<figcaption>haze_removal.jpg</figcaption>
</figure>

## Uso

Ajusta la ***Intensidad*** y la ***Profundidad*** según tus necesidades:
para un efecto más intenso emplea valores de *Intensidad* altos,
mientras que en un punto medio controlarás en qué medida eliminas la
neblina, pudiendo dejar una cierta cantidad que añadirá valor estético a
la imagen sin enmascarar demasiado los detalles.

![](haze_removal-depth_map.jpg "haze_removal-depth_map.jpg") Mediante el
deslizador de *Profundidad* controlarás en qué zonas se aplica la
herramienta: en fotografías con zonas evidentes de «primer plano»,
«plano medio» y «fondo», con valores bajos modificarás el *primer plano*
y conforme aumentes el valor del deslizador, irás modificando el *plano
medio* hasta el *fondo*.

Puedes visualizar las áreas más afectadas activando el ***Mapa de
profundidad***: cuanto más claro sea el color, más se quitará la neblina
en esa zona, de forma que empezando con un valor de *Profundidad: 0*
(que desactiva la herramienta), al ir subiendo el valor irás viendo como
cada vez más zonas se enmascaran de blanco, donde se aplicará la
herramienta con mayor intensidad.

Sin embargo, aprenderás enseguida que la herramienta suele modificar
toda la imagen en mayor o menor medida y en el *Mapa de profundidad*
enseguida verás que toda la imagen se cubre de un tono blanquecino,
indicando que la imagen al completo será modificada en mayor o menor
medida por la herramienta.

Por otro lado el deslizador ***Saturación*** te permite controlar cuánto
aumenta la herramienta la intensidad de los colores: hacia la izquierda
el resultado se acerca más a simplemente eliminar la neblina, mientras
que hacia la derecha además se incrementa la saturación global. Y
también descubrirás que con valores muy agresivos, en ocasiones
introducirás dominantes de color donde antes había una neblina espesa:

<figure>
<img src="/images/haze_removal-color_cast.jpg"
title="haze_removal-color_cast.jpg" />
<figcaption>haze_removal-color_cast.jpg</figcaption>
</figure>
