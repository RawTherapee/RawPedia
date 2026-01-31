---
title: Edges and Microcontrast
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Bordes y microcontraste

</div>

__TOC__

## Bordes

Esta herramienta realiza un incremento de la nitidez (o el *«enfoque»*)
de aquellos bordes con suficiente contraste para que sean interpretados
como bordes *enfocados*. Es decir, mejora la nitidez de aquellos bordes
que ya están enfocados, ignorando los bordes y detalles que estén
desenfocados (difusos). Y como detalles importantes, no resalta el ruido
de la imagen ni genera halos en las zonas resaltadas.

Este tipo de mejora de la nitidez puede llegar a hacer que los bordes
tratados parezcan irreales, como recortes de un collage. Asímismo si los
ajustes son altos, los bordes resultantes se verán con *dientes de
sierra*
([*aliasing*](https://es.wikipedia.org/wiki/Aliasing#En_la_computación_gráfica))
bien marcados. Por esto debes ser muy cauto a la hora de aplicarlo en
imágenes con bordes curvos. Sin embargo **cuando predominen las líneas
rectas (especialmente si no son diagonales), es un método interesante de
mejora de nitidez, en especial si al final del procesado se reduce el
tamaño de la imagen**.

Los mejores resultados se condiguen con ajustes muy sutiles:

1.  **Iteraciones**: número de pasos que realiza el algoritmo. Un número
    alto produce un efecto
    [posterizado](https://es.wikipedia.org/wiki/Posterización) alrededor
    de los bordes modificados, aunque en bastantes ocasiones con un
    valor de *2* ya se observa este problema. En general **1-2
    iteraciones** dan los mejores resultados.
2.  **Cantidad**: número de píxeles adyacentes que se analizarán en
    busca de un borde. Los valores altos producen bordes más nítidos y
    un mayor efecto de *dientes de sierra*.
3.  **Sólo luminancia**: la herramienta trabaja en el espacio de color
    L\*a\*b\* y esta opción fuerza a que sólo se aumente la nitidez del
    **canal L\***, dejando los canales a\* y b\* intactos.

<figure>
<img src="/images/edges.jpg" title="edges.jpg" />
<figcaption>edges.jpg</figcaption>
</figure>

## Microcontraste

El *microcontraste* es un concepto polémico, pues siendo la distinción o
separación de un píxel respecto a sus inmediatos vecinos, hay gente que
dice que eso es simplemente *contraste*. Sin embargo, una imagen con
poco microcontraste tendrá muchos píxeles vecinos con valores similares,
dando una imagen con muchas zonas casi planas, casi sin detalles. Por el
contrario, una imagen con mucho microcontraste te permitirá distinguir
los más pequeños detalles hasta el nivel del píxel: podrás diferenciar
un píxel de sus vecinos.

Por esto mismo no es recomendable que consideres la herramienta
***Microcontraste*** como otro método de mejora de la nitidez, sino como
un método para mejorar la gradación tonal de las imágenes: se trata de
mejorar la distinción entre los diferentes tonos a nivel de píxel, para
que la imagen tenga mejores texturas y una *«profundidad»* de luces y
sombras equivalente a la que veríamos en directo en la escena.

El microcontraste es una propiedad bastante elusiva en las fotos que
depende de:

- en gran medida de la calidad del objetivo: hay objetivos calificados
  de excelentes que tienen un pobre microcontraste
- de las características del sensor: cómo de neutro es el blanco
  generado por el sensor, o si tiene una sensibilidad algo mayor en el
  rojo o el azul dando una ligera dominante de color, que al desentramar
  modifica o reduce el microcontraste
- si el sensor tiene un [*«filtro
  AA»*](https://es.wikipedia.org/wiki/Filtro_antialiasing), que elimina
  los detalles más finos
- si el objetivo no es capaz de diferenciar detalles tan finos como
  puede captar el sensor (un sensor con elevado número de Mpixels
  necesita objetivos de alta resolución)
- el tipo de algoritmo de desentramado: que puede reducir el
  microcontraste, según cómo realice la interpolación de los valores de
  los fotodiodos
- de si durante la toma han habido reflejos dentro del objetivo o
  incluso dentro de la cámara: en estos casos los negros se convertirán
  en gris oscuro y los blancos en gris claro, reduciendo los contrastes
- si has cerrado el diafragma para tener más profundidad de campo:
  cuanto mayor es el *número f* seleccionado, menor será el
  microcontraste en la foto
- si has cerrado demasiado el diafragma y has introducido
  [difracción](https://es.wikipedia.org/wiki/Difracción_(física)) en tus
  fotos

<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 877px">

<imgcomp img1='microcontrast-off.jpg' img2='microcontrast-on.jpg'  width=877/>

<div class="thumbcaption">

La herramienta *Microcontraste* en acción: si bien no debes esperar
cambios espectaculares, la sutil diferencia es claramente perceptible,
especialmente en los pelillos alrededor del capullo. La imagen es más
*«táctil»*, más ''«real».

</div>
</div>
</div>

En cualquier caso, una imagen con buen microcontraste tendrá un aspecto,
una *«calidad»* que resaltará sobre la misma imagen sin microcontraste
aplicado. Es un efecto muy sutil, casi imperceptible si no lo buscas,
pero definitivamente visible instintivamente y muy agradable.

Los controles de la herramienta son razonablemente progresivos y te
permiten escoger el balance preciso entre un aumento importante del
contraste a nivel de píxel y la prevención de generar o amplificar
artefactos:

- **Umbral de contraste**: define el contraste mínimo a partir del cual
  la herramienta actuará sobre los píxeles. Ten en cuenta que la
  diferencia inicial de contraste entre píxeles vecinos no será muy
  grande, así que si el deslizador está en un valor alto, probablemente
  no modifiques casi nada en la imagen.
- **Cantidad**: la intensidad del efecto. Cuanto más alta, mayor será la
  diferencia de tono entre píxeles (y visualmente será más aparente la
  diferencia).
- **Uniformidad**: hacia la izquierda el algoritmo trata de respetar en
  mayor medida los degradados iniciales, a costa de un efecto mucho más
  sutil. Hacia la derecha los contrastes se intensifican y se pierden un
  poco los degradados iniciales, haciéndolos más *«bruscos»*.
- **Matriz**: define el área que se estudiará para calcular el cambio de
  contraste. Dispones de dos opciones, una *matriz* (un área) de *3x3*
  píxeles alrededor del píxel estudiado, o una de *5x5* píxeles. Por
  defecto será de *5x5*, dando un efecto más intenso, pero si activas la
  casilla, cambiará a una matriz de *3x3*, que es más apropiada para
  imágenes ruidosas.

<figure>
<img src="/images/seagull-microcontrast.jpg"
title="seagull-microcontrast.jpg" />
<figcaption>seagull-microcontrast.jpg</figcaption>
</figure>
