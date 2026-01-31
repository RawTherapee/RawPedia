---
title: Tone Mapping
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Mapeo tonal

</div>

__TOC__

## Introducción

<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 700px">

<imgcomp img1='ikon.jpg' img2='ikon-tm.jpg'  width=700 />

<div class="thumbcaption">

**Izquierda:** la imagen en color antes de ser procesada con la
herramienta.

**Derecha:** vista de la imagen después de aplicarle el *mapeo de
tonos*.

Puedes observar el aumento general de la luminosidad, pero también el
aumento del «grano» de la imagen, así como la pérdida de las sutilezas
de los degradados. Además los tonos cambian en mayor o menor medida.

</div>
</div>
</div>

Esta herramienta sirve para mejorar la percepción de las zonas oscuras y
subir el contraste en los detalles, sin permitir que las luces se quemen
fácilmente. Es decir, se realiza un *mapeo tonal* para comprimir el
rango dinámico de la foto, con el objetivo de evitar que exceda el rango
dinámico del método de salida (pantalla o papel).

Ofrece mejores resultados con imágenes de alto rango dinámico, bien sean
HDR puro, o imágenes raw con buen rango dinámico (mayor que la pantalla
o el papel impreso).

Para conseguir esto la detección de características de la imagen y la
aplicación de las modificaciones se realizan en varios niveles de
detalles: una capa base, detalles gruesos, detalles medios y detalles
finos.

Sin embargo, al realizar su trabajo la herramienta también cambia los
tonos («colores») originales de la imagen: no es que se hagan más o
menos brillantes, sino que cambian de tono. Y aunque en general esto no
supondrá ningún problema, es mejor que lo tengas en cuenta.

Además, al activar la herramienta la imagen sufre un aumento general de
la luminosidad (más acusado en las sombras, pero también en las luces),
los pequeños detalles se acentúan y el resultado es una imagen
granulosa. No con ruido añadido, sino con detalles más groseros, más
aparentes. Esto es debido al aumento de contraste en la luminosidad,
pero también al aumento del contraste de color.

Nota: el mapeo tonal necesita una gran cantidad de memoria (RAM) y hace
uso intensivo de la CPU.

## Los controles para el mapeo de tonos

Los diferentes deslizadores de la herramienta controlan distintos
aspectos del mapeo, pero también interactúan entre éllos:

- **Gamma**: desplaza las modificaciones hacia las sombras o hacia las
  luces altas. A la derecha (valores por encima de **1.00**) la imagen
  se oscurece y a la izquierda (por debajo de **1.00**) se aclara.
- **Discriminación de bordes**: este parámetro afecta a la sensibilidad
  a los bordes. Cuanto mayor sea su valor, más probable será que un
  cambio de luminosidad sea considerado como un «borde» y el reparto de
  los detalles entre los distintos niveles cambiará. Por éllo la
  intensidad del efecto de la herramienta será mayor en toda la imagen
  (en más cantidad de detalles y ópticamente con más intensidad global
  en la foto, puesto que al aplicarse sobre más zonas, el efecto es más
  notable).
- **Escala**: este deslizador controla en qué niveles se aplicarán con
  más fuerza las modificaciones. Es decir, cuanto mayor sea el valor
  escogido, mayor tamaño deberá tener un detalle para que sea
  modificado. Además en zonas con mucha luminosidad, cuanto mayor es la
  *Escala* más probable es que aparezcan posterizaciones debido al
  recorte de las luces. Sin embargo hasta cierto límite se puede mitigar
  el posterizado subiendo el valor de la *Gamma*.
- **Iteraciones de reponderación**: modifica el reparto de intensidades
  de la herramienta en cada nivel, con lo que a veces ayuda a evitar la
  generación de halos. El uso de un número mayor que cero dará los
  mejores resultados si la *Discriminación de bordes* se pone a *1*.
  Cuando este valor de la *Discriminación de bordes* es mayor , pueden
  empezar a aparecer artefactos en los bordes con alto contraste.
- **Intensidad**: controla la fuerza del efecto global. Si incrementas
  la intensidad las sombras y tonos medios se aclaran mientras las luces
  altas se mantienen casi en el mismo nivel, de forma que se preserve la
  luminosidad promedio de la imagen. De este modo se evita que la imagen
  tenga un aspecto desvaído.

## Las diferencias entre Intensidad positiva e Intensidad negativa

En esta herramienta, dependiendo de si la *Intensidad* es positiva o es
negativa, el resultado global será muy distinto y el resto de
deslizadores cambiarán su efecto (a veces de forma notable).

Con **valores de intensidad positivos**:

- al activar la herramienta los tonos medios y las sombras se aclaran.
- Gamma: a la derecha oscurece la imagen y a la izquierda la aclara.
- Discriminación de bordes: valores altos amplian el rango dinámico,
  mientras que valores bajos lo comprimen.
- Escala: básicamente oscurece las sombras.
- Iteraciones de reponderación: en general cuantas más iteraciones más
  altas son las luces (llegando a quemarlas) y más oscuras son las
  sombras, pero sin apenas cambios en los medios tonos.

Con **valores de intensidad negativos**:

- al activar la herramienta los tonos medios y las sombras se oscurecen.
- Gamma: a la derecha aclara la imagen y a la izquierda la oscurece.
- Discriminación de bordes: valores altos reducen el rango dinámico,
  mientras que valores bajos lo amplían, aunque el efecto es más
  moderado que con valores de *Intensidad* positivos. En general se
  observa que las luces bajan un poco y las sombras suben algo, mientras
  que los tonos medios se igualan.
- Escala: con valores altos de *Discriminación de bordes*, la *Escala*
  prácticamente no afecta al resultado.
- Iteraciones de reponderación: intensifica aún más la homogeneización
  de los tonos medios.
