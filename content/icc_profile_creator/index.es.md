---
title: ICC Profile Creator
contributors:
  - XavAL
  - DrSlony
tags:
  - 'General Information'
---

<div class="pagetitle">

El generador de perfiles ICC

</div>
<div class="headline">

Para obtener tus propios perfiles ICC con características personalizadas

</div>

## Introducción

Según el [International Color Consortium Consorcio Internacional del
Color](http://www.color.org/index.xalter), el propósito de los perfiles
ICC es *proporcionar un formato multiplataforma para la creación y la
interpretación de datos de color*.

Los tipos posibles de perfiles ICC son:

- perfiles de entrada: los perfiles que se emplean para gestionar los
  datos procedentes de cámaras, escáners, ...
- perfiles de monitor (pantalla): son los empleados para enviar los
  datos de color a las pantallas, de forma que puedan mostrar los
  colores correctamente
- perfiles de salida: que generan los colores necesarios para enviarlos
  a dispositivos como impresoras y registradores de película
- perfiles de enlace de dispositivos: son un tipo especial de perfil en
  el que no hay una conversión de colores, sino que los colores
  originales se traducen directamente a otros colores. También se puede
  usar para englobar todos los cambios realizados por dos o más perfiles
  en uno solo, de forma que el tratamiento entre un dispositivo concreto
  (por ejemplo una cámara de una marca y modelo concretos) y otro
  también concreto (por ejemplo una impresora de una marca y modelo,
  junto a un papel de una marca y modelo) sean más rápidos. Se utiliza
  habitualmente en procesos de preimpresión, especialmente para
  salvaguardar el nivel de negro en las impresiones.
- perfiles abstractos: no dependen de ningún dispositivo y se usan para
  modificar o realzar algunos colores (o todos) de la imagen. En
  concreto estos perfiles no se usan para realizar conversiones, sino
  para
  [*asignarlos*](https://docs.gimp.org/es/gimp-image-assign-color-profile.html)
  a una imagen. Este tipo de perfil nunca podrá adjuntarse a una imagen
  (no irá embebido en los datos de la imagen)
- perfiles de espacio de color: empleados para convertir entre espacios
  de color, por ejemplo para guardar o transportar imágenes en un
  espacio de color determinado
- perfiles de colores con nombre: cada color tiene un nombre concreto
  que es el que usarán los programas de edición (en lugar del trío RGB)

Mediante el *Generador de Perfiles ICC* RawTherapee sólo puede generar
***perfiles de pantalla***, aunque éstos también los podrás usar como
*perfiles de trabajo* o *de salida*, si lo deseas.

## Como usar el Generador de Perfiles

<figure>
<img src="/images/Rt59_icc_profile_creator.jpg"
title="Rt59_icc_profile_creator.jpg" />
<figcaption>Rt59_icc_profile_creator.jpg</figcaption>
</figure>

Para acceder al cuadro de diálogo del *Generador de Perfiles* tienes que
hacer clic en el botón que encontrarás junto a los de *Preferencias* y
*Ayuda* (<img src="/images/gamut-plus.png" title="gamut-plus.png" height="26"
alt="gamut-plus.png" />), en el extremo izquierdo o superior de la
ventana de RawTherapee.

A pesar de que no puedes establecer absolutamente todos aspectos de un
perfil ICC con esta herramienta, sí que puedes ajustar los más
importantes para un fotógrafo: los *colores primarios*, la *curva de
reproducción de tonos* y el *iluminante*.

En todos éllos puedes elegir entre varias opciones de ajustes estándar,
e incluso en los *colores primarios* y la *curva de reproducción de
tonos* puedes establecer valores según tus necesidades.

Puedes generar perfiles que cumplen los estándares ICC en sus versiones
2 y 4, pero *sólo podrás usar primarios personalizados y cambiar el
iluminante por defecto si generas perfiles de la versión 4*.

Por último, para que los perfiles generados estén disponibles para su
uso en RawTherapee, guárdalos en la carpeta personalizada para perfiles
de color de tu sistema operativo, como está establecida en [Preferencias
\> Gestión de color](Preferences/es#Gestión_de_Color.md).

### Los Colores Primarios

*Colores primarios* son aquellos colores «puros» que no pueden generarse
mediante la mezcla de otros colores. En la síntesis aditiva de colores
(la que emplean las pantallas) los colores primarios son el rojo, el
verde y el azul: a partir de ellos se pueden generar el resto de
colores.

En un [espacio de
color](Color_Management/es#Los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")
los *colores primarios* son los que definen el triángulo de los posibles
colores existentes en ese espacio de color. En otras palabras: su *Rango
de colores*.

En el *Generador de perfiles ICC* la localización de esos colores
primarios la especificas mediante unas coordenadas correspondientes al
[diagrama de cromaticidad CIExy de
1931](https://es.wikipedia.org/wiki/Espacio_de_color_CIE_1931).

### La Curva de Reproducción de Tonos (*TRC*)

La
[*TRC*](http://www.jpereira.net/gestion-de-color-articulos/la-reproduccion-tonal-curvas-oecf)
básicamente se trata de una curva que modifica los valores iniciales o
de entrada de la imagen hacia otros valores, que serán los que se
grabarán en la imagen de salida.

Habitualmente es lo que se llama la
[*«gamma»*](color_management/es#la_corrección_gamma) del
perfil y cabe recordar que en las imágenes exportadas no se usa **«para
ajustar la imagen digital a como nosotros la percibimos en la vida
real»**: no olvides que en la *gestión del color* siempre hay dos
perfiles en juego, uno para indicar cómo se ha codificado la imagen y
otro para convertir esos datos en otros que el dispositivo de destino
pueda entender. Es decir, los colores originales se mantienen y la
codificación sólo es un *«medio de transporte»*.

Sin embargo, dado que el perfil que generes aquí puedes llegar a
[asignarlo](https://docs.gimp.org/es/gimp-image-assign-color-profile.html)
en una imagen (dentro de GIMP, por ejemplo), sí es importante que
consideres cuidadosamente qué gamma te interesa en tu perfil, puesto que
al *asignarlo* a una imagen cambiarás su aspecto irreversiblemente:
cuando *asignas* un perfil de color, no cambias los valores RGB de cada
píxel pero estás cambiando su significado, ya que cada píxel será
automáticamente de otro color (has cambiado los colores primarios) y al
cambiar la gamma, cada píxel será más oscuro o más claro que
inicialmente (dependiendo de la forma de la curva *TRC*).

A parte de poder elegir curvas de gamma *puras* (*standard_g2.2* y
*standard_g1.8*) donde la curva se rige por una fórmula simple, también
puedes elegir otras más complejas, con una parte inicial recta seguida
de una curva ([un ejemplo típico de este tipo de curvas es la del
espacio de color
sRGB](http://www.apratizando.com/2013/11/guia-completa-e-indolora-para-programadores-sobre-xyz-rgb-icc-xyy-and-trcs)).
Y además también puedes generar tu propia curva mixta:

- el deslizador *Gamma* establece [el exponente de la curva
  gamma](Color_Management/es#La_corrección_gamma.md). Define
  cuán acentuada será la parte curvada
- el deslizador *Slope* establece la pendiente de la parte recta de la
  curva

Una vez establecidos los dos valores, el generador calcula el punto en
el que ambas fórmulas (la de la parte recta y la de la parte curva)
coinciden y donde se unen una a la otra.

### El Iluminante

En resumen, **el iluminante es el color blanco de referencia de los
colores del perfil**.

En fotografía se llama
[*Iluminante*](http://www.glosariografico.com/iluminante) a una fuente
de luz teórica que cumple con determinados requisitos y que en general
trata de estandarizar determinados tipos de iluminación a los que
estamos habituados (por ejemplo, el [*iluminante estándar
D50*](http://www.glosariografico.com/iluminante_estandar_d50), que
describe las condiciones medias de iluminación al mediodía en Europa
Occidental).

Este *iluminante* es el que le da su tono al color blanco «puro» y sobre
el que pivotan el resto de colores: por ejemplo, con una luz
incandescente el «blanco» es en realidad un tono anaranjado y todos los
demás colores se tiñen de un tono anaranjado, puesto que hacen
referencia a ese «blanco» *no tan puro*. Así pues, **este dato es básico
a la hora de generar un perfil**.

Si bien el iluminante en relación al cual se codificarán los colores es
el **Iluminante estándar D50**, puedes especificar otro distinto de los
de la lista y el *generador de perfiles* añadirá la ***adaptación
cromática*** necesaria para convertir los colores desde D50 hasta el
iluminante seleccionado.
