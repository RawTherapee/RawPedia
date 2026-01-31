---
title: Color Toning
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Virado de color

</div>
<div class="headline">

Virados o virajes de partes concretas de la foto

</div>

## Introducción

La técnica del ***Virado*** (o *Viraje*) se empleó en la fotografía en
blanco y negro para prolongar la vida de las fotos mediante la
sustitución de las sales de plata por otro compuesto, o mediante la
adición de un pigmento. Al mismo tiempo, también se conseguía crear un
efecto monocromático o a veces bicromático muy estético.

En RawTherapee también puedes crear tus propios [virajes en blanco y
negro](Black-and-White/es#Virajes_en_blanco_y_negro.md), pero en
este documento sólo se explica cómo aplicar el coloreado de areas de la
foto en las imágenes en color.

Sin embargo, aunque en la herramienta hay varios métodos de aplicar
virajes, dado que la mayoría son muy limitados, aleatorios o incluso
incomprensibles, sólo se explican dos de ellos: las ***Zonas de
Corrección de Color**'' y la***Mezcla L\*a\*b\***'': el primero es un
método muy versátil y potente de crear virajes en las zonas que desees,
mientras que el segundo te permite escoger tonalidades exactas para los
virajes.

## Los Virados y el perfil de trabajo

**Una consideración muy importante** antes de empezar a realizar un
*Viraje* (o a un nivel más general cualquier modificación de los tonos
de la imagen): **debes tener claro qué *perfil de trabajo* vas a usar en
tu procesado, elegirlo y no volver a cambiarlo**, pues los colores
generados por RawTherapee dependen de este *perfil de trabajo* y si lo
cambias una vez hayas aplicado un *Viraje*, tanto el tono elegido como
los límites de las máscaras también cambiarán.

<figure>
<img src="/images/colortoning_workingprofile.jpg"
title="colortoning_workingprofile.jpg" />
<figcaption>colortoning_workingprofile.jpg</figcaption>
</figure>

<div class="img-comp-wrapper">
<div class="thumbinner thumbcompare tnone" style="width: 589px">

<imgcomp img1='colortoning_dome-prophoto.jpg' img2='colortoning_dome-srgb.jpg'  width=589 />

<div class="thumbcaption">

En esta imagen se ha creado una máscara para seleccionar las cúpulas
azules, con la intención de darles un tono azul más intenso.  
**A la izquierda:** puedes ver la imagen procesada con el perfil de
trabajo ProPhoto  
**A la derecha:** al procesado anterior únicamente se le ha cambiado el
perfil de trabajo a sRGB. Puedes apreciar un ligero cambio de tono y
sobre todo un reborde blanco alrededor de la cúpula superior. Además
verás algo más de «textura», que probablemente sea debida al cambio de
la máscara.

</div>
</div>
</div>

## Zonas de Corrección de Color

Este método es el más potente dentro de la herramienta y con él puedes
controlar prácticamente todos los aspectos de un viraje: desde qué
cantidad de color se añadirá, pasando por la creación de máscaras para
aplicarlo sólo a determinadas zonas, hasta la corrección de la
luminosidad final de la foto.

Sin embargo, no podrás escoger el tono exacto de viraje, ni podrás
invertir automáticamente una máscara para aplicar un viraje a una zona
de la foto y otro distinto al resto de la foto.

Además, podrás ***teñir*** los tonos de la imagen, pero en general no
podrás ***sustituirlos***: en este sentido, *teñir* significa añadir un
color que se mezclará con otro (por lo que *teñir* con azul un color
amarillo dará como resultado un tono verde). Si necesitas sustituir un
color por otro, no te queda más remedio que usar el [método de la
*mezcla L\*a\*b\**](#La_mezcla_L.2Aa.2Ab.2A.md) o usar un
programa externo.

Dicho esto, debes tener en cuenta que los resultados variarán entre
imágenes (a veces de forma notable) y que la herramienta no responde
igual con imágenes raw que con imágenes de *mapa de bits* (JPEG o PNG).
Por ello aquí tienes algunas ideas que te orientarán un poco:

- en imágenes de mapa de bits las mezclas de colores se ajustan más a lo
  que instintivamente puedes esperar (rojo+verde=amarillo)
- en imágenes raw los virajes rojos siempre darán una dominante de color
  más intensa que los azules
- en imágenes raw el viraje será más o menos intenso dependiendo de lo
  brillante que sea el color original: las muy altas luces tomarán una
  dominante más tenue que los medios tonos
- en imágenes raw los tonos saturados casi no sufrirán variación (en
  especial los azules)
- en imágenes raw a veces las mezclas de colores no te darán el color
  que esperas: por ejemplo, un viraje magenta sobre un color azul
  intenso no te dará un azul violáceo, sino un tono azul distinto

### El tono del viraje

En la herramienta lo primero que puedes elegir es el tono del virado,
aunque el gráfico es un poco ambiguo con los colores al mostrar tonos
muy apagados, así que aquí tienes la cuadrícula equivalente con **los
colores aproximados que apreciarás si aplicas esos tonos a un gris
medio**: ![](Cielab_8x8.png "Cielab_8x8.png")

Como nota cabe decir que dependiendo de donde pongas el punto de control
del viraje, así será el tono resultante, es decir, el color de cada
cuadro es sólo orientativo, ya que cada pixel del gráfico representa un
color distinto. El tono que ves en la cuadrícula es el que obtendrás con
el pixel central de cada cuadro.

Por ejemplo, al seleccionar el pixel de la esquina inferior izquierda
obtendrás este viraje:

<div>

- <figure>
  <img src="/images/colortoning_png.png" title="colortoning_png.png" />
  <figcaption>colortoning_png.png</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_png-to-blue.png"
  title="colortoning_png-to-blue.png" />
  <figcaption>colortoning_png-to-blue.png</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_tint.png" title="colortoning_tint.png" />
  <figcaption>colortoning_tint.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/colortoning_raw.jpg" title="colortoning_raw.jpg" />
  <figcaption>colortoning_raw.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_raw-to-blue.jpg"
  title="colortoning_raw-to-blue.jpg" />
  <figcaption>colortoning_raw-to-blue.jpg</figcaption>
  </figure>

</div>

### El control de la luminosidad y la saturación

A la hora de crear el viraje primero puedes escoger el tono que teñirá
la zona enmascarada de la imagen mediante la cuadrícula, para después
decidir lo luminosa o contrastada que quedará mediante estos tres
deslizadores:

- ***Exposición***: el efecto global es el de un desplazamiento del
  histograma hacia la izquierda (valores por debajo de *1.000*) o hacia
  la derecha (valores por encima de *1.000*). Los valores de los píxeles
  se multiplican por el valor del deslizador, por lo que el *0* sigue
  siendo *0* hagas lo que hagas. Equivale a un cambio en la exposición
  de la foto (siempre que los valores por defecto de la *compensación* y
  la *gamma* no se modifiquen).
- ***Compensación***: se modifica uniformemente el valor de cada píxel,
  con lo que el resultado es un aumento o disminución global de la
  luminosidad. Sin embargo, lo hace conservando en gran medida los
  valores de las luces (hay poca variación en las luces).
- ***Gamma***: números por debajo de *1.000* harán que la imagen aumente
  su luminosidad (más en los tonos medios que en las sombras y luces),
  mientras que números por encima de *1.000* la oscurecerán (de nuevo
  más en los tonos medios que en las sombras y luces). Es un ajuste
  tradicional de la *gamma* de la imagen, pero con la posibilidad de
  aplicarlo sólo a la zona enmascarada.

Cada parámetro actúa sobre los canales independientemente. La formula
para calcular el valor final de cada canal de los píxeles es:

\[\[<File:colortoning_pixel>
values.png\|class=formulae\|none\|thumb\|496px\|

<big>**V<small>f</small>**</big>: valor final  
<big>**V<small>0</small>**</big>: valor inicial  
<big>**exp**</big>: valor de la *Exposición*  
<big>**comp**</big>: valor de la *Compensación*  
<big>**gamma**</big>: valor de la *Gamma*

\]\]

Una vez corregida la luminosidad de toda la imagen o de la zona afectada
por la máscara, la ***Saturación*** aumentará *la cantidad de color* (la
*saturación* o *cromaticidad*) en el resultado de todo el proceso
previo. Es decir, aumentará la saturación global (de todos los canales a
la vez) de la zona enmascarada.

Su rango va desde *-100* (completamente desaturado) hasta *100*
(saturación máxima para la herramienta).

### Virajes por canales

Por defecto se aplican los virajes en todos los canales de la imagen,
pero tienes la posibilidad de aplicar todo lo anterior a un solo canal
(rojo, verde o azul).

Si decides usar esta función debes saber que los resultados no son en
absoluto intuitivos, ya que realizas el viraje sobre un solo canal
mediante un color de la cuadrícula, por lo que el resultado final
normalmente no será lo que esperes: se añade o rebaja la componente del
canal, lo cual supone cambios en los colores de la imagen, no tinciones
del color escogido.

Aún así, aquí van una serie de pautas para guiarte un poco:

- al aplicar el viraje de color al canal azul, sólo se aplican las
  variaciones del canal **b\*** (coordenadas verticales), mientras que
  la posición del punto a lo largo del canal **a\*** (coordenadas
  horizontales) se ignora.
- al aplicarlo al canal verde, las variaciones principales son las del
  canal **a\***, mientras que el canal **b\*** sólo modifica ligeramente
  el canal verde con valores de **a\*** negativos y los tres canales de
  forma ligera con valores de **a\*** positivos.
- con el canal rojo las variaciones principales también son las del
  canal **a\***, mientras que el canal **b\*** sólo modifica ligeramente
  el canal rojo con valores de **a\*** positivos y los tres canales de
  forma ligera con valores de **a\*** negativos.

### Los ecualizadores gráficos

Estos gráficos sirven para que selecciones («enmascares») las zonas de
la imagen que vas a virar. Puedes usarlos en solitario, o combinar sus
efectos para ajustar mejor la zona donde se realizará el viraje (por
ejemplo, en las zonas más saturadas, con tonos cálidos y en sombra).

Por defecto en la parte superior de cada gráfica tienes una línea blanca
con dos puntos que indican qué píxeles se teñirán: cuando la línea está
en la parte superior del gráfico, los tonos, grados de saturación o
luminosidades situados en la vertical serán virados, mientras que si
está en la parte inferior, los píxeles no se teñirán con el viraje.

Dispones de tres ecualizadores:

- **ecualizador de Tono**: seleccionas los tonos (los «colores») sobre
  los que realizarás el viraje. En el eje horizontal ves dónde están
  situados los distintos colores.
- **ecualizador de Saturación**: seleccionas cómo de saturados o pastel
  deberán ser los colores para virarlos. Hacia la izquierda están los
  tonos más desaturados («pastel») y hacia la derecha los más saturados.
- **ecualizador de Luminosidad**: seleccionas las luminosidades que vas
  a virar. A la izquierda tienes las zonas de sombra. Alrededor de 1/5
  del gráfico desde la izquierda encontrarás el *gris medio* (¡ojo, no
  está en medio del gráfico!) y a la derecha las luces.

<div>

- <figure>
  <img src="/images/colortoning_hue-eq.jpg" title="colortoning_hue-eq.jpg" />
  <figcaption>colortoning_hue-eq.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_chr-eq.jpg" title="colortoning_chr-eq.jpg" />
  <figcaption>colortoning_chr-eq.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_lum-eq.jpg" title="colortoning_lum-eq.jpg" />
  <figcaption>colortoning_lum-eq.jpg</figcaption>
  </figure>

</div>

Puedes añadir y [editar los
parámetros](General_Comments_About_Some_Toolbox_Widgets/es#Valores_de_entrada/salida_de_los_puntos_de_control.md)
de tantos puntos de control como desees, con lo que puedes escoger con
precisión los colores y luminosidades que se virarán y crear máscaras
complejas que ajusten mucho las zonas donde aplicar el viraje. Pero como
ya se ha dicho, lo que no puedes escoger con precisión es el tono del
viraje.

Y después de haber creado la máscara, puedes afinar aún más mediante el
**Difuminado de la máscara**, que creará un gradiente en los bordes para
que el viraje se integre mejor con el resto de la imagen.

Para ver mejor el efecto de este difuminado, puedes **Mostrar la
máscara**, con lo que verás la imagen cubierta de amarillo intenso allí
donde se aplicará el viraje. Y las zonas difuminadas presentarán un
degradado que te indicará hasta dónde se mezclará el viraje con el resto
de la foto.

### Listado de virajes

En la parte superior de la herramienta tienes un listado de los
distintos virajes que has creado, con sus parámetros básicos:

- **a**: la coordenada *a\** del tono de viraje seleccionado, convertida
  a un rango entre *0.000* y *1.000* *(los colores están codificados en
  el espacio de color L\*a\*b\*)*.
- **b**: la coordenada *b\** del tono de viraje seleccionado, convertida
  a un rango entre *0.000* y *1.000*.
- **S**: el valor del control deslizante de la Saturación
- **s** (minúscula): el valor de la Exposición
- **o**: el valor de la Compensación
- **p**: el valor de la Gamma

Puedes añadir (<img src="/images/add-small.png" title="add-small.png" width="16"
alt="add-small.png" />), eliminar
(<img src="/images/remove-small.png" title="remove-small.png" height="16"
alt="remove-small.png" />), mover una posición hacia arriba
(<img src="/images/arrow-up-small.png" title="arrow-up-small.png" height="16"
alt="arrow-up-small.png" />), o hacia abajo
(<img src="/images/arrow-down-small.png" title="arrow-down-small.png" height="16"
alt="arrow-down-small.png" />) los distintos virajes, además de duplicar
(<img src="/images/arrow-right-small.png" title="arrow-right-small.png"
height="16" alt="arrow-right-small.png" />) el viraje que tengas
seleccionado.

Este último botón puede resultar muy útil, ya que aunque no puedes
invertir automáticamente un viraje, sí que puedes duplicarlo y después
ir editando cada punto de control de cada ecualizador, de forma que lo
que antes no estaba seleccionado para virarlo, ahora sí lo estará.

## La mezcla L\*a\*b\*

Este método también se basa en colores codificados en el *espacio de
color L\*a\*b\**, pero la diferencia que lo hace preferible al método de
las *Zonas de Corrección de Color* es que aquí podrás escoger qué tono
exacto tendrá el viraje.

Además, en este caso sí que podrás sustituir los colores por el tono del
viraje (no simplemente *teñirlos*).

Sin embargo en la mayoría de los casos el método de las *Zonas de
Corrección de Color* es mucho más predecible y controlable en la mayoría
de los casos. En contraste, si queremos aplicar un viraje monocromático
que afecte a toda la gama de luminancias con el método de la *mezcla
L\*a\*b\**:

<div>

- <figure>
  <img src="/images/colortoning_blend-red1.png"
  title="colortoning_blend-red1.png" />
  <figcaption>colortoning_blend-red1.png</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_blend-red2.png"
  title="colortoning_blend-red2.png" />
  <figcaption>colortoning_blend-red2.png</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_blend-blue1.png"
  title="colortoning_blend-blue1.png" />
  <figcaption>colortoning_blend-blue1.png</figcaption>
  </figure>

- <figure>
  <img src="/images/colortoning_blend-blue2.png"
  title="colortoning_blend-blue2.png" />
  <figcaption>colortoning_blend-blue2.png</figcaption>
  </figure>

</div>

En todos los ejemplos anteriores la *curva de Opacidad* se ha situado en
la parte superior de la gráfica a todo lo ancho (el viraje se aplica al
100% en toda la gama de luminancias) y se ha dejado la opción
*Protección automática de saturación* activada (que es como la
encontrarás por defecto).

Si desactivas la protección de la saturación, los resultados variarán en
mayor o menor medida, pero igualmente habrá un cambio de tonalidad
dependiendo de dónde se encuentren los puntos de control. Por esto mismo
a pesar que puedes seleccionar el tono exacto del viraje, en realidad el
resultado final dependerá mucho de dónde estén situados finalmente los
puntos de control.

A pesar de todo, puede que sea un método interesante en determinados
casos, por lo que se explica brevemente a continuación:

- la ***curva de Color*** muestra la luminancia en horizontal y los
  matices del viraje en vertical. Las dos líneas verticales delimitan
  las áreas principales resultantes.
- por defecto la herramienta tiene dos puntos de control: puedes añadir
  tantos como quieras, pero como mínimo siempre habrán dos.
- el único tipo de curva recomendable es la de ***Cromaticidad
  Estándar***, que es el seleccionado por defecto y no te permite
  modificar la curva (no hay curva que modificar). Los cambios en los
  tonos son automáticos según los colores seleccionados con los puntos
  de control.
- la ***curva de Opacidad*** determina con qué intensidad se aplica el
  viraje a las distintas luminosidades de la imagen. Puede variar entre
  *0* (no se aplica viraje; la curva está en la parte inferior del
  gráfico) a *1* (se aplica todo el viraje; la curva está en la parte
  superior del gráfico).
- el tono gris medio de las fotos está localizado en un punto alrededor
  de 1/5 desde la izquierda de la *curva de Color*.
- el valor de la ***Saturación*** (la máxima intensidad del viraje)
  puede ajustarse automáticamente (por defecto) o manualmente. En este
  último caso podrás ajustar los deslizadores de *Umbral* e
  *Intensidad*.

Por fin, **para introducir un matiz concreto de viraje**, deberás seguir
estos pasos:

1.  comprueba el *perfil de trabajo* que estás usando y [después del
    viraje **no lo
    cambies**](#Los_Virados_y_el_perfil_de_trabajo.md)
2.  averigua qué matiz tiene el color que te interesa para el viraje:
    habitualmente lo encontrarás en Internet, bien obteniéndolo de una
    fotografía que te guste, bien de una muestra de color con sus
    valores RGB (o con [notación
    hexadecimal](https://es.wikipedia.org/wiki/Colores_web)). En
    cualquier caso lo más habitual será que estén codificados en el
    *espacio de color sRGB*. **Debes asegurarte en qué espacio de color
    se han codificado**. Por ejemplo, te gusta una muestra que tiene el
    color `#02f356` en sRGB.
3.  abre GIMP y crea una imagen nueva rellena con el color de la muestra
    (**asegúrate que la imagen tiene el mismo espacio de color que la
    muestra**).
4.  si tu *perfil de trabajo* no tiene el mismo espacio de color que la
    muestra, en GIMP convierte la imagen al espacio de color que estés
    usando. Por ejemplo a ProPhoto.
5.  con el *selector de color* de GIMP (*color picker* en inglés), haz
     +
    <img src="/images/mouse_left-click.png" title="mouse_left-click.png" height="26"
    alt="mouse_left-click.png" /> en la imagen y aparecerá el cuadro de
    diálogo del *selector de color*. Si no está mostrado por defecto, en
    una de las dos listas desplegables selecciona **HSV** y toma nota
    del valor de **H**. Con la muestra del ejemplo, una vez convertida
    la imagen a ProPhoto, `H: 140.3º`.
6.  divide el valor anterior por *360*. Valor ProPhoto de la muestra:
    `0.38972` (debes anotar 5 valores decimales).
7.  [edita el punto de control que deba tener ese
    tono](General_Comments_About_Some_Toolbox_Widgets/es.md) y
    en el campo **`O:`** introduce el resultado de la división. En el
    ejemplo, `O: 0.38972`.
8.  procede de manera análoga con todos los puntos de control y tonos
    que necesites.

## Interacción con la herramienta Simulación de película

Si quieres realizar un viraje después de haber activado la [Simulación
de película](Film_Simulation/es.md), en el caso de que sigas con
una imagen en color todas las herramientas de *Virado de color* estarán
disponibles directamente.

Sin embargo, si la *Simulación de película* es en *blanco y negro*, es
preciso que actives también la herramienta *Blanco y negro* para poder
usar las herramientas de *Virado de color*.
