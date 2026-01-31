---
title: Impulse Noise Reduction
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Reducción de ruido impulsivo

</div>
<div class="thumb tright">
<div class="thumbinner" style="width: 642px;">

![](impulse-noise.jpg "impulse-noise.jpg")
![](impulse-noise.gif "impulse-noise.gif")

<div class="thumbcaption tcap-es">

En este ejemplo aumentado al 300% puedes observar la cantidad de píxeles
afectados que se corrijen con la herramienta.

</div>
</div>
</div>

El ***Ruido impulsivo*** es un tipo de ruido común en las imágenes
digitales y no tiene nada que ver con el contenido de la imagen: siempre
es independiente de la imagen y se distribuye aleatoriamente.

Este ruido puede tener valores fijos (blanco o negro, o «sal y
pimienta») o valores aleatorios (niveles de gris aleatorios), pero
aparecerá en cualquier punto de la imagen y no tendrá conexión con los
píxeles a su alrededor, por lo que destacará de su entorno. Por esto
mismo cuando es visible, es bastante molesto. Sin embargo, dado que se
trata de píxeles individuales, para verlo claramente tendrás que ampliar
bastante la imagen (al 200-300% como mínimo).

El origen del problema parece ser que es debido a la compresión de la
imagen, a la falta de transmisión de la señal, a problemas con la
circuitería del sensor, o en cualquier caso a factores que no tienen que
ver con la escena o la trayectoria óptica de la imagen (con el
objetivo).

Y no debes confundir el ruido de «sal y pimienta» (normalmente
consistente en píxeles blancos o negros) con los píxeles bloqueados
(*«hot pixels»*, que normalmente serán de un color puro saturado) o los
píxeles dañados («muertos», *«dead pixels»*, que son negros). Los píxels
bloqueados y dañados se producen por una razón muy diferente y deben
tratarse usando el [*Filtro de píxeles
bloqueados/dañados*](Preprocessing/es#Filtro_de_píxeles_bloqueados.2Fdañados.md).

La herramienta tiene un único deslizador para ajustar el umbral hasta el
cual se aplicará la supresión. Puedes entenderlo casi como un control de
la intensidad de eliminación de ruido, con la característica que si te
excedes, puedes arruinar el aspecto de la foto, ya que el algoritmo
considerará casi cualquier píxel demasiado brillante o demasiado oscuro
respecto a su entorno como un píxel incorrecto:

<figure>
<img src="/images/impulse-noise_2much.jpg" title="impulse-noise_2much.jpg" />
<figcaption>impulse-noise_2much.jpg</figcaption>
</figure>
