---
title: Vignetting Filter
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Filtro de viñeteado

</div>
<div class="headline">

O cómo oscurecer los bordes de la imagen

</div>

## La herramienta

<figure>
<img src="/images/Vignette-filter_4.00_50_50.jpg"
title="Vignette-filter_4.00_50_50.jpg" />
<figcaption>Vignette-filter_4.00_50_50.jpg</figcaption>
</figure>

El ***Filtro de viñeteado*** sirve para añadir un viñeteado artístico a
tu imagen o al recorte, si es que lo estás usando.

Para corregir el viñeteo producido por el objetivo (que también genera
bordes oscuros en la imagen), debes usar el filtro [*Corrección de
viñeteo*](Lens/Geometry/es#Corrección_de_viñeteo.md) de la
herramienta [*Objetivo y Geometría*](lens/geometry/es), en la
pestaña *Transformar*. O aún mejor: usa la herramienta de [*Campo
Plano*](Flat_Field/es.md).

## Los ajustes

### Intensidad

Es la cantidad de variación de la luminosidad que aplicará el filtro, en
«pasos de exposición». Los límites van desde un incremento de la
exposición de 6 pasos (***Intensidad: -6**'', con bordes más claros),
hasta una disminución de 6 pasos (***Intensidad: +6**'', con bordes más
oscuros).

La máxima intensidad se alcanza siempre en las esquinas de la imagen.

### Anchura del gradiente

Este deslizador controla la anchura o tamaño del gradiente:

- si seleccionas el ***0***, la transición entre las zonas modificada y
  no modificada será muy corta y definida, aunque no abrupta. Las
  modificaciones sólo alcanzarán los extremos de la foto.
- con un valor de ***50***, la transición se amplía un poco, pero la
  principal diferencia es que las modificaciones alcanzan hasta la mitad
  de la foto, dejando sólo la mitad central no afectada.
- con un valor alrededor de ***85*** las modificaciones prácticamente
  llegan al centro de la foto.
- con un valor de ***100***, el gradiente se amplía aún más y el círculo
  central de la foto también es modificado por el filtro, aunque con una
  intensidad bastante baja.

Como apunte, ten en cuenta que cuando aclares los bordes (valores
negativos), el gradiente será bastante más estrecho que cuando los
oscurezcas (valores positivos), por lo que el efecto del filtro no será
tan gradual.

<div>

- <figure>
  <img src="/images/Vignette-filter_4.00_00_50.jpg"
  title="Vignette-filter_4.00_00_50.jpg" />
  <figcaption>Vignette-filter_4.00_00_50.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/Vignette-filter_4.00_99_50.jpg"
  title="Vignette-filter_4.00_99_50.jpg" />
  <figcaption>Vignette-filter_4.00_99_50.jpg</figcaption>
  </figure>

</div>

### Redondez

Con este deslizador controlas la geometría del filtro:

- si lo pones a ***0***, la forma será rectangular con las esquinas
  redondeadas
- a ***50*** será una elipse encajada entre los bordes de la imagen
- a ***100*** será circular. Sin embargo, ten en cuenta que si tu imagen
  es cuadrada la elipse encajada será un círculo, por lo que la forma no
  cambiará entre los valores de ***50**'' a***100**''.

<div>

- <figure>
  <img src="/images/Vignette-filter_4.00_50_00.jpg"
  title="Vignette-filter_4.00_50_00.jpg" />
  <figcaption>Vignette-filter_4.00_50_00.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/Vignette-filter_4.00_50_99.jpg"
  title="Vignette-filter_4.00_50_99.jpg" />
  <figcaption>Vignette-filter_4.00_50_99.jpg</figcaption>
  </figure>

</div>
