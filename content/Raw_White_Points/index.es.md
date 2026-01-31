---
title: Raw White Points
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Nivel de Blancos en el archivo Raw

</div>
<div class="headline">

Corrigiendo el punto donde se recortarán las luces

</div>

En las fotografías digitales, la luz que llega a los fotoreceptores del
sensor se transforma en señales digitales que se codifican mediante
números: los valores de cada canal RGB. Sin embargo por varias razones
(como el ruido) no es conveniente usar todos los valores posibles
después de la conversión y por encima de determinado valor los canales
se *saturan*. El valor a partir del cual los canales ya no aceptan
valores más altos y se empiezan a recortar se llama ***Nivel de blancos
raw*** (o *Nivel de blancos en el archivo raw*).

Los valores por defecto usados por RawTherapee provienen de `dcraw`,
pero no es raro que estos sean demasiado altos. Por esto mismo es muy
necesario aportar datos precisos desde el propio RawTherapee, como se
explica en el [*Soporte para nuevos
formatos*](Adding_Support_for_New_Raw_Formats/es#Niveles_de_blanco_y_de_negro.md).

Si el *Nivel de blancos raw* es muy alto las luces recortadas aparecerán
con una dominante rosa o magenta, en lugar de blanco puro. Si por el
contrario es muy bajo, RawTherapee recortará los canales demasiado
pronto y perderás detalles en las luces, aunque la foto tendrá un color
correcto y la *Reconstrucción de luces* dará mejores resultados.

En cualquiera de los casos, puedes corregirlo mediante esta herramienta:
si el deslizador se sitúa por encima de ***1.00*** reducirás el nivel de
saturación (los valores de los píxeles se recortarán antes), mientras
que si está por debajo de ese valor, los píxeles podrán aceptar valores
más altos en cada canal.

Y aunque la corrección del *Nivel de blancos raw* corrije todos los
canales por igual, debes saber que hay cámaras que tienen diferentes
puntos de saturación para los diferentes canales, a pesar que las
diferencias suelen ser muy pequeñas, por lo cual no debería haber
problemas.

Por otra parte, la corrección [de *campo
plano*](Flat_Field/es.md) en algunos casos también puede reducir
los valores raw, de tal forma que las luces recortadas («quemadas»)
tendrán una dominante de color magenta o rosa. Sin embargo no deberías
tener problemas para corregirlo con esta herramienta.
