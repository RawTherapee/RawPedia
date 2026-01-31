---
title: Graduated Filter
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Filtro graduado

</div>
<div class="headline">

Emulación de filtros degradados de densidad neutra

</div>

__TOC__

## La herramienta

La herramienta ***Filtro graduado*** simula un filtro de densidad neutra
degradado como los empleados frente a los objetivos. Estos filtros
pueden usarse, por ejemplo, en fotografía de paisaje para limitar el
brillo del cielo sin modificar el resto de la imagen.

El efecto neto es una modificación de la exposición en una zona de la
imagen, otra zona sin modificar y en medio de las dos una zona
modificada mediante un gradiente.

## Los ajustes

### Intensidad

![](Graduated-filter_4.00_00_25_00_00.png "Graduated-filter_4.00_00_25_00_00.png")
Este control cambia la intensidad del filtro, en pasos de exposición.

Teniendo en cuenta la nomenclatura habitual de los filtros de densidad
neutra, estableciendo *1* es lo mismo que usar un filtro «ND2»: se
reduce a la mitad la luz en la imagen.

El ajuste posible va desde *-5* hasta *+5*. Es decir, se puede ajustar
desde «ND2» hasta «ND32» (5 pasos de abertura tradicionales,
oscureciendo la imagen) y además algo que no es posible en los filtros
reales: 5 pasos de abertura aclarando la imagen (incrementando la
exposición).

### Ángulo

![](Graduated-filter_4.00_45_25_00_00.png "Graduated-filter_4.00_45_25_00_00.png")
Permite rotar la dirección en la que se aplica el gradiente, de forma
similar a como harías con un portafiltro para filtros de cristal
cuadrados.  

### Anchura de gradiente

También podríamos llamarlo *Difuminado*.

Este deslizador controla la «anchura» del gradiente del filtro.

El valor *0* anula el gradiente, lo que produce un borde nítido que
puede ser útil como ajuste temporal mientras se elige la posición y el
ángulo del filtro.

Cualquier otro valor del deslizador (*\>0 - 100*) especifica la anchura
del gradiente como porcentaje de la diagonal de la imagen y este
porcentaje se reparte por igual a ambos lados de la línea definida por
el valor *0*.

<div>

- <figure>
  <img src="/images/Graduated-filter_4.00_00_10_00_00.png"
  title="Graduated-filter_4.00_00_10_00_00.png" />
  <figcaption>Graduated-filter_4.00_00_10_00_00.png</figcaption>
  </figure>

- <figure>
  <img src="/images/Graduated-filter_4.00_00_50_00_00.png"
  title="Graduated-filter_4.00_00_50_00_00.png" />
  <figcaption>Graduated-filter_4.00_00_50_00_00.png</figcaption>
  </figure>

</div>

### Centro X, Centro Y

Estos ajustes mueven horizontal (*X*) y verticalmente (*Y*) el centro
del gradiente del filtro (el centro que viene definido por la *Anchura
del gradiente=0*).

Con este mismo desplazamiento del centro también se desplaza el punto de
anclaje de la rotación, que siempre estará en el punto de la *Anchura
del gradiente=0*.

### Retícula

Al pulsar el botón de activación de la ***Retícula***
(<img src="/images/crosshair-adjust.png" title="crosshair-adjust.png" width="24"
alt="crosshair-adjust.png" />) se mostrará en la *Vista Previa* un
gráfico que representa todos los controles deslizantes excepto el de
*Intensidad*:

<figure>
<img src="/images/Grad-Filter-graticule.gif"
title="Grad-Filter-graticule.gif" />
<figcaption>Grad-Filter-graticule.gif</figcaption>
</figure>

Al pasar el puntero del ratón sobre cada una de las zonas activas del
gráfico, el icono del ratón cambiará para sugerirte qué podrás controlar
del filtro: el *Ángulo*, el *Degradado* o los *Centros*. Tan sólo
deberás hacer clic
(<img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
alt="mouse_left-click.png" />) y mantener pulsado mientras arrastras.
Las modificaciones serán interactivas: mientras ves instantáneamente el
resultado, los deslizadores cambiarán sus valores automáticamente.
