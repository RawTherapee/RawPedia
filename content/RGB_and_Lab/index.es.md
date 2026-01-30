---
title: RGB and Lab
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

RGB y CIE L\*a\*b\*

</div>

## Sus características

![](RGB_Cube_Show_lowgamma_cutout_b.png "RGB_Cube_Show_lowgamma_cutout_b.png")
![](cielab.jpg "cielab.jpg")
*[**RGB**](https://en.wikipedia.org/wiki/RGB_color_space)* y *[**CIE
L\*a\*b\***](https://es.wikipedia.org/wiki/Espacio_de_color_Lab)* (o
simplemente ***CIELab**'', o***Lab**'') son dos [espacios de
color](https://es.wikipedia.org/wiki/Espacio_de_color) diferentes y sin
relación entre éllos.

Ambos describen los colores a su manera, pero mientras el modelo *RGB*
depende del destino de la imagen (un programa o un dispositivo), el
modelo *CIELab* actúa con independencia del destino de la foto.

*RGB* opera sobre tres canales: rojo, verde y azul.

*CIELab* expresa la misma información mediante una componente de
luminosidad (*L\**), y dos componentes de color (*a\** y *b\**). La
luminosidad se mantiene separada del color, con lo que se puede ajustar
uno de éllos sin afectar al otro. La *luminosidad* se diseñó para
aproximarla a la visión humana, que es muy sensible al verde, pero menos
sensible al azul.

## Sus diferencias

Mucha gente se pregunta qué diferencias hay entre ajustar la
luminosidad, el contraste y la saturación en el espacio de color
***RGB*** comparado con el espacio de color ***CIELab***: la herramienta
***Exposición*** se basa en el modelo *RGB*, mientras que la herramienta
***Ajustes L\*a\*b\**** se basa en el modelo *CIEL\*a\*b\**. Ambas
tienen ajustes similares, pero los resultados son algo distintos.

Si aumentamos la luminosidad en el espacio *CIELab*, con frecuencia el
resultado tendrá una apariencia más correcta a la vista y los colores
parecerán más «frescos» y saturados. Sin embargo, un cambio equivalente
en *RGB* hace que los colores parezcan algo más brillantes pero
«lavados».

<div>

- <figure>
  <img src="/images/colorspace_flowers_900_1_neutral.jpg"
  title="colorspace_flowers_900_1_neutral.jpg" />
  <figcaption>colorspace_flowers_900_1_neutral.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colorspace_flowers_900_3_lab_lightness.jpg"
  title="colorspace_flowers_900_3_lab_lightness.jpg" />
  <figcaption>colorspace_flowers_900_3_lab_lightness.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colorspace_flowers_900_2_rgb_lightness.jpg"
  title="colorspace_flowers_900_2_rgb_lightness.jpg" />
  <figcaption>colorspace_flowers_900_2_rgb_lightness.jpg</figcaption>
  </figure>

</div>

Ocurre lo contrario con el contraste: en la herramienta *Exposición* y
con un valor de *+45* los colores serán claramente más cálidos e
intensos que con el mismo ajuste en la herramienta *Ajustes L\*a\*b\**.
Sin embargo el contraste en sí será aproximadamente el mismo.

<div>

- <figure>
  <img src="/images/colorspace_flowers_900_5_lab_contrast.jpg"
  title="colorspace_flowers_900_5_lab_contrast.jpg" />
  <figcaption>colorspace_flowers_900_5_lab_contrast.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colorspace_flowers_900_4_rgb_contrast.jpg"
  title="colorspace_flowers_900_4_rgb_contrast.jpg" />
  <figcaption>colorspace_flowers_900_4_rgb_contrast.jpg</figcaption>
  </figure>

</div>

En cuanto a la *Saturación* (en la *Exposición*) y la *Cromaticidad* (en
los *Ajustes L\*a\*b\**), el ajuste de la *saturación* a *-100* produce
una imagen en blanco y negro con apariencia de haberle aplicado un
filtro rojo, mientras que la *cromaticidad* situada en el valor *-100*
produce una imagen en blanco y negro más neutra.

Los valores positivos de *saturación* causarán desviaciones del matiz
(cuanto mayor sea el valor en el deslizador, más se desviará el color
del tono original), mientras que los valores positivos de *cromaticidad*
intensificarán los colores manteniendo sus matices correctos, lo cual
proporciona un resultado nítido y limpio.

La *cromaticidad* de la herramienta *Ajustes L\*a\*b\** (mediante el uso
del deslizador *Cromaticidad* o de la *curva CC*) es el método
recomendado para intensificar los colores.

<div>

- <figure>
  <img src="/images/colorspace_flowers_900_7_lab_chromaticity.jpg"
  title="colorspace_flowers_900_7_lab_chromaticity.jpg" />
  <figcaption>colorspace_flowers_900_7_lab_chromaticity.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colorspace_flowers_900_6_rgb_saturation.jpg"
  title="colorspace_flowers_900_6_rgb_saturation.jpg" />
  <figcaption>colorspace_flowers_900_6_rgb_saturation.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colorspace_flowers_900_8_vibrance.jpg"
  title="colorspace_flowers_900_8_vibrance.jpg" />
  <figcaption>colorspace_flowers_900_8_vibrance.jpg</figcaption>
  </figure>

</div>
