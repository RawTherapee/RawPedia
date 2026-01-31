---
title: Demosaicing
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Desentramado

</div>
<div class="headline">

La regeneración de la escena: de datos raw a imágenes RGB

</div>

## Introducción

![](Chipincamera.jpg "Chipincamera.jpg") La mayoría de cámaras digitales
usan un [sensor](sensor_with_bayer/x-trans_matrix/es) que
contiene millones de elementos sensibles a la luz, llamados
*fotodiodos*. Sin embargo, esos fotodiodos generan únicamente una carga
eléctrica, por lo que no existe aún el concepto de color.

Para reconocer el color, se sitúa un [mosaico de filtros de
color](Sensor_with_Bayer/X-Trans_Matrix/es#Matrices_de_Filtros_de_Color_.28CFAs.29.md)
sobre el sensor, de modo que determinados fotodiodos registren
longitudes de onda de luz específicas mientras ignoran el resto. Es
decir, por ejemplo los fotodiodos que capturan el color verde no
capturan ningún color más (ni rojo, ni azul).

Los únicos mosaicos de color compatibles con RawTherapee son el
***[filtro de
Bayer](Sensor_with_Bayer/X-Trans_Matrix/es#Filtro_de_Bayer.md)**''
y
el***[X-Trans](sensor_with_bayer/x-trans_matrix/es#filtro_x-trans)**''.

En el caso del *filtro de Bayer* hay el doble de fotodiodos verdes que
de rojos o azules, así que la mitad de datos (fotodiodos) del canal
verde no tiene datos y las tres cuartas partes de los fotodiodos de los
canales rojo y azul tampoco tendrán datos (sólo 1 de cada 4 fotodiodos
es rojo o azul).

En el caso del *filtro XTrans* hay 20 verdes, 8 azules y 8 rojos: algo
menos de la mitad del canal verde y algo más de las tres cuartas partes
de los canales rojo y azul no tienen datos. Con este tipo de filtro en
principio se pierde *«resolución cromática»* en favor de la *«resolución
espacial»*. Sin embargo en teoría la *resolución cromática* es como
mínimo equiparable a la *matriz de Bayer* porque en cada fila y columna
hay filtros de los 3 colores, de forma que la
[interpolación](https://es.wikipedia.org/wiki/Interpolaci%C3%B3n) puede
«adivinar» mejor los tonos de la escena.

Por lo tanto, regenerar una escena a partir de los datos de una cámara
con un sensor *Bayer* o *X-Trans* no es inmediato: el mosaico de puntos
con distintos colores primarios debe convertirse en una imagen en color
convincente, teniendo cada píxel el conjunto de 3 valores RGB. Este
proceso se llama ***desentramado***.

Sin embargo no hay ningún método de *desentramado* perfecto, que
regenere exactamente la escena original: **todos los métodos parten de
información incompleta y se basan en «adivinar» lo mejor que pueden los
datos que faltan**.

En cuanto a la *«resolución espacial»*, es decir el registro de los
detalles de la escena, el canal que más información ofrece es el verde,
pero alrededor de la mitad de los datos se han perdido:

<div>

- <figure>
  <img src="/images/demosaic_details_amaze.jpg"
  title="demosaic_details_amaze.jpg" />
  <figcaption>demosaic_details_amaze.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_details_sensor.jpg"
  title="demosaic_details_sensor.jpg" />
  <figcaption>demosaic_details_sensor.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_details_red.jpg" title="demosaic_details_red.jpg" />
  <figcaption>demosaic_details_red.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_details_green.jpg"
  title="demosaic_details_green.jpg" />
  <figcaption>demosaic_details_green.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_details_blue.jpg"
  title="demosaic_details_blue.jpg" />
  <figcaption>demosaic_details_blue.jpg</figcaption>
  </figure>

</div>

En cuanto a la *«resolución cromática»*, es decir el registro de los
tonos originales de la escena, la cantidad de datos perdidos (o no
registrados, alrededor de 3 de cada 4 de cada canal rojo o azul)
significa que en mayor o menor medida todos los algoritmos generan
artefactos cromáticos. Es decir, los cálculos son erróneos y el color
resultante es incorrecto:

<div>

- <figure>
  <img src="/images/demosaic_false_color_amaze.jpg"
  title="demosaic_false_color_amaze.jpg" />
  <figcaption>demosaic_false_color_amaze.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_false_color_sensor.jpg"
  title="demosaic_false_color_sensor.jpg" />
  <figcaption>demosaic_false_color_sensor.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_false_color_red.jpg"
  title="demosaic_false_color_red.jpg" />
  <figcaption>demosaic_false_color_red.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_false_color_green.jpg"
  title="demosaic_false_color_green.jpg" />
  <figcaption>demosaic_false_color_green.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_false_color_blue.jpg"
  title="demosaic_false_color_blue.jpg" />
  <figcaption>demosaic_false_color_blue.jpg</figcaption>
  </figure>

</div>

## Métodos de desentramado

RawTherapee ofrece varios algoritmos de desentramado, cada uno de ellos
con sus propias características. Además están divididos en dos
categorías: los algoritmos para sensores de tipo *Bayer* y los que son
para sensores de tipo *X-Trans*. Al cargar la imagen en el *Editor* el
programa presentará únicamente los adecuados al sensor de la cámara.

En cualquier caso, las diferencias entre los algoritmos de cada grupo en
general son sutiles, por lo que si vas a reducir el tamaño de la imagen
al final del procesado, lo más probable es que no veas ningún cambio
entre uno y otro método. Por ello puedes necesitar ampliar la imagen al
100% o más para distinguir qué cambia.

No obstante, como la imagen desentramada constituye la base sobre la que
opera el resto de herramientas, **la elección del algoritmo de
desentramado correcto tendrá un efecto visual significativo en el
resultado final**, especialmente cuando la observes de cerca, la
imprimas a gran tamaño o simplemente emplees muchas herramientas con
procesados intensos.

Las variaciones más visibles entre unos y otros algoritmos de
desentramado son la calidad de la representación de los detalles finos,
el tratamiento del ruido, la creación de artefactos en forma de patrones
similares a laberintos, rayas o cruces y la distinta gestión de las
luces y reflejos especulares.

A continuación puedes observar las diferencias entre los algoritmos
principales de RawTherapee para sensores con *matriz de Bayer* (con sus
valores por defecto). Se han obviado los algoritmos de la *familia AHD*,
por ser menos eficientes y estar incluídos básicamente por razones
históricas:

<div>

- <figure>
  <img src="/images/demosaic_amaze.png" title="demosaic_amaze.png" />
  <figcaption>demosaic_amaze.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_amaze+bilinear.png"
  title="demosaic_amaze+bilinear.png" />
  <figcaption>demosaic_amaze+bilinear.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_amaze+vng4.png" title="demosaic_amaze+vng4.png" />
  <figcaption>demosaic_amaze+vng4.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_rcd.png" title="demosaic_rcd.png" />
  <figcaption>demosaic_rcd.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_rcd+bilinear.png"
  title="demosaic_rcd+bilinear.png" />
  <figcaption>demosaic_rcd+bilinear.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_rcd+vng4.png" title="demosaic_rcd+vng4.png" />
  <figcaption>demosaic_rcd+vng4.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_dcb.png" title="demosaic_dcb.png" />
  <figcaption>demosaic_dcb.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_dcb+bilinear.png"
  title="demosaic_dcb+bilinear.png" />
  <figcaption>demosaic_dcb+bilinear.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_dcb+vng4.png" title="demosaic_dcb+vng4.png" />
  <figcaption>demosaic_dcb+vng4.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_lmmse.png" title="demosaic_lmmse.png" />
  <figcaption>demosaic_lmmse.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_igv.png" title="demosaic_igv.png" />
  <figcaption>demosaic_igv.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_vng4.png" title="demosaic_vng4.png" />
  <figcaption>demosaic_vng4.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/demosaic_fast.png" title="demosaic_fast.png" />
  <figcaption>demosaic_fast.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_mono.png" title="demosaic_mono.png" />
  <figcaption>demosaic_mono.png</figcaption>
  </figure>

- <figure>
  <img src="/images/demosaic_none-sensor.png" title="demosaic_none-sensor.png" />
  <figcaption>demosaic_none-sensor.png</figcaption>
  </figure>

</div>

*Grosso modo*, **para los sensores tipo *Bayer***, ***AMaZE*** suele ser
el mejor método para imágenes con valores ISO bajos, mientras que
***LMMSE**'' o***IGV**'' son mejores en el caso de valores ISO altos.

A pesar de esto, cada método tiene sus particularidades y es mejor que
pruebes varios antes de decidirte por uno al procesar una imagen:

<div class="tlist">
<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 477px">

<imgcomp img1='demosaic_amaze+ca.png' img2='demosaic_amaze.png'  width=477 />

<div class="thumbcaption">

**Lado izquierdo:** la imagen desentramada con *AMaZE*.

**Lado derecho:** La misma imagen, con el mismo desentramado y la
*Corrección de Aberraciones Cromáticas* activada. Puedes ver líneas
diagonales oscuras a lo largo de los bordes, especialmente alrededor del
área de luces.

</div>
</div>
</div>
</div>

:\* **AMaZE** *(Aliasing Minimization and Zipper Elimination)* es el
método de desentramado predeterminado, ya que en la mayoría de los casos
produce los mejores resultados. Sin embargo *AMaZE* tiene tendencia a
generar artefactos muy visibles en las diagonales con alto contraste.
Este efecto es particularmente notable al activar la [*Corrección de
Aberraciones Cromáticas*](Chromatic_Aberration/es.md), ya que
aparecen líneas oscuras a 45º en los bordes de alto contraste. Además,
este algoritmo no trabaja demasiado bien junto a la [*Nitidez en
captura*](Capture_Sharpening/es.md).

:\* **RCD** *([Ratio Corrected
Demosaicing](https://github.com/LuisSR/RCD-Demosaicing))* hace un
trabajo excelente en bordes redondeados, preserva casi el mismo nivel de
detalle que *AMaZE*, pero el aspecto general es más difuminado, menos
nítido. Este método es el más rápido entre *AMaZE, RCD* y *DCB* y es muy
recomendable para valores de ISO de bajos a medios.

:\* **DCB** produce resultados similares a *RCD*, pero suele exagerar
los contrastes y saturaciones de algunos píxeles en bordes de alto
contraste, produciendo artefactos bastante visibles. Sin embargo elegir
entre *RCD* y *DCB* estará en función de cada imagen (a veces un método
funciona mejor que el otro, o al revés). Este método te permite elegir
el número de ***Iteraciones**'' que se aplicarán durante el
desentramado, de forma que se refine el resultado. Además, la
opción***Mejora DCB**'' también afina el resultado especialmente en las
zonas de alto contraste.

:\* **LMMSE** *(Linear Minimum Mean Square Error Estimator)* es el
método recomendado para valores ISO altos, o cuando la imagen es muy
ruidosa. Evita la aparición de artefactos «en laberinto» y que la imagen
parezca desvaída debido a una reducción de ruido intensa. Y con la
opción ***Pasos de Mejora LMMSE*** se añaden grados de mejora en la
reducción de artefactos y el aumento de la [relación
señal-ruido](https://es.wikipedia.org/wiki/Relaci%C3%B3n_se%C3%B1al/ruido).

:\* **IGV** es similar a *LMMSE* y es bastante efectivo para mitigar
patrones moiré. La elección entre uno y otro método dependerá de la
imagen, aunque *IGV* tiene tendencia a generar píxeles oscuros (*puntos
negros*) y a ser un poco más «grosero» con los degradados. Por otra
parte, *IGV* necesita mucha menos memoria y tiempo de proceso que
*LMMSE*, por lo que este último cambia automáticamente a *IGV* si no hay
suficiente memoria disponible.

:\* **VNG4** *(Variable Number of Gradients)* genera gran cantidad de
artefactos en las zonas con buen contraste y normalmente es mejor
emplearlo únicamente como segundo método en el [desentramado
dual](#Desentramado_dual_y_Umbral_de_contraste.md). En este caso
realza mucho menos el ruido de las zonas menos contrastadas que el
algoritmo principal. Por otro lado, en los casos en que hay
contaminación del color del filtro de un fotodiodo en los fotodiodos
vecinos, puedes usar *VNG4* a costa de perder los detalles más finos y
la aparición de artefactos de colores falsos, aunque es posible que sea
mejor opción emplear el [*Equilibrado de
verdes*](Preprocessing/es#Equilibrado_de_verdes.md).

:\* **Bilineal** es un método usado únicamente en el [desentramado
dual](#Desentramado_dual_y_Umbral_de_contraste.md), ya que es de
inferior calidad al resto de métodos. Normalmente emplearás el método
*VNG4*, pero en el caso del procesado de imágenes para video,
normalmente miles de ellas a la vez, el método *Bilineal* es mucho más
rápido y al reproducir el video las diferencias con VNG4 serán apenas
perceptibles.

:\* **[Desplazamiento de
Píxeles](#Desplazamiento_de_Píxeles_.28Pixel_Shift.29.md)**
*(Pixel Shift)*: cada vez más cámaras *tipo Bayer* soportan múltiples
tomas en modo *Pixel Shift*, que consiste en capturar cuatro fotos
desplazando el sensor un píxel cada vez, en un movimiento circular y
luego guardar las cuatro tomas en un mismo archivo raw más grande. De
esta forma cada fotodiodo registra los 4 colores del filtro (2 verdes, 1
rojo y 1 azul). RawTherapee combina todas las tomas en una sola imagen,
al tiempo que enmascara automáticamente los objetos en movimiento,
reduciendo el nivel de ruido y aumentando la nitidez de la imagen. Si
seleccionas este método pero el archivo raw no tiene esta
característica, RawTherapee realiza el desentramado mediante el método
*AMaZE*.

:\* **Rápido** es un método de desentramado muy rápido, pero simple y de
baja calidad.

:\* **Monocromático**: útil [para usuarios de cámaras
monocromas](#El_desentramado_con_sensores_monocromos.md), o
cámaras con el mosaico de filtros de color eliminado.

:\* **Ninguno**: no se realiza ningún desentramado y muestra el mosaico
del archivo raw. Puede ser útil para diagnósticos, pero no lo usarás
para fotografía.

**Para las cámaras X-Trans**, el método ***3 iteraciones + rápido*** es
generalmente el mejor.

La diferencia fundamental entre 3 y 1 iteraciones la podrás encontrar en
los bordes con alto contraste, que están mejor resueltos con 3
iteraciones. Aún así, dependiendo del tamaño final de la imagen, la
diferencia es mínima.

Donde sí hay diferencias palpables es al usar un solo método de
desentramado o dos (*desentramado dual*): en las zonas de menor
contraste tanto el método de *3 iteraciones* como el de *1 iteración*
suelen dar artefactos en forma de pequeñas líneas aleatorias
horizontales o verticales, mientras que al hacer un *desentramado dual*
añadiendo el método *rápido*, esas zonas mejoran mucho.

<div>

- <figure>
  <img src="/images/x-trans_nofast.jpg" title="x-trans_nofast.jpg" />
  <figcaption>x-trans_nofast.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/x-trans_fast.jpg" title="x-trans_fast.jpg" />
  <figcaption>x-trans_fast.jpg</figcaption>
  </figure>

</div>

Si las fotografías tienen valores de ISO bajos, las diferencias entre 1
y 3 iteraciones son más notables, aunque cuantas más iteraciones, más
lento es el desentramado. Si las fotografías tienen valores de ISO
altos, puedes usar el método de ***1 iteración + rápido*** sin
problemas, pues probablemente no notarás pérdida de calidad y el
procesado será más rápido.

## Desentramado dual y Umbral de contraste

Los algoritmos habituales de *desentramado* realizan sus cálculos en la
imagen raw completa, con lo que habitualmente generan artefactos de
distintos tipos: unos algoritmos son mejores que otros en ciertas áreas
(con poco contraste, con mucho ruido, con colores falsos, ...), pero
casi ninguna imagen presenta las mismas características en toda su
extensión.

Por otra parte, **los métodos de *desentramado dual*,
como***AMaZE+VNG4***, te permiten procesar áreas de alto contraste
usando un algoritmo y áreas de bajo contraste usando el otro
algoritmo**. Normalmente las áreas de alto contraste equivalen a zonas
con detalles nítidos, mientras que las de bajo contraste suelen tener
detalles difusos o áreas planas, como por ejemplo el cielo.

La desventaja es que la imagen debe ser desentramada dos veces, por lo
que tarda más tiempo que usando un único método.

Puedes usar como algoritmos principales para áreas de alto contraste:
*AMaZE, RCD* y *DCB*.

Por su parte, los algoritmos para las áreas de bajo contraste son:
***VNG4*** y ***Bilineal***. *VNG4* será el mejor en la mayoría de los
casos, pero si necesitas un procesado más rápido aunque con algo menos
de calidad, puedes seleccionar *Bilineal*.

Y para que ambos métodos se coordinen bien debes usar el ***Umbral de
contraste***, que será el valor de contraste límite para aplicar uno u
otro método de *desentramado*. Este deslizador incluye una casilla que,
al marcarla, calcula un nivel óptimo automáticamente.

## El desentramado con sensores monocromos

Una cámara monocroma genera imágenes en blanco y negro y no necesitan
desentramado.

Además, algunas de estas cámaras no tienen filtro infrarrojo y por tanto
son sensibles a la luz infrarroja, característica útil en la fotografía
creativa en blanco y negro.

RawTherapee soporta las cámaras monocromas, pero la interfaz de usuario
no está específicamente adaptada para ellas, por lo que cuando cargues
un archivo monocromo, *todas las herramientas de color seguirán estando
disponibles*.

Y debes tener en cuenta que hay algunos factores adicionales a
considerar cuando se trabaja con archivos monocromos:

- algunas cámaras monocromas indican que sólo tienen un único canal
  monocromo y una matriz de color neutra (como la *Leica M Monochrom*)
- otras cámaras informan que tienen canales RGB en una configuración
  *Bayer* (como la *Phase One IQ260 Achromatic*, o cámaras modificadas
  para infrarrojos).

Si la cámara indica que sólo tiene un canal, RawTherapee lo reconoce, no
realizará ningún desentramado (la selección de desentramado sigue
activa, pero no hace nada) y todo funcionará normalmente.

Sin embargo, si la cámara se identifica como una cámara RGB de *Bayer*,
por defecto RawTherapee realizará el desentramado y aplicará un *perfil
de color de entrada*. Para evitarlo debes seleccionar el método de
desentramado ***Monocromático*** y seleccionar [***Sin perfil de
color***](Color_Management/es#Sin_perfil_de_color.md) como
*perfil de entrada* en la herramienta *Gestión del color*.

## Bordes recortados

El *desentramado* suele basarse en analizar los píxeles que rodean al
píxel que se está procesando.

Cuando se desentrama un píxel situado en el borde superior de la imagen
raw no habrá píxeles por encima de él, por lo que no es posible
procesarlo del mismo modo y con la misma calidad que los píxeles
rodeados de un número de píxeles suficientemente grande. Algo similar
ocurre con el resto de bordes de la imagen.

La mayor parte de convertidores raw recortan unas pocas filas y columnas
alrededor de la periferia de la imagen, como hace RawTherapee de forma
predeterminada. No obstante, puedes anular este recorte, manipulando el
valor del ***Borde recortado***. Si se ajusta a *0* no habrá recorte y
RawTherapee hará lo que pueda para desentramar los píxels del borde,
¡aunque pueden aparecer artefactos!

En general, deberías dejar este ajuste a su valor predeterminado y
cambiarlo a *0* sólo si es absolutamente necesario, por ejemplo cuando
proceses tomas raw DNG de [1080p](https://en.wikipedia.org/wiki/1080p) y
necesites preservar el número de píxeles (1920x1080).

## Sub-imagen

Algunos archivos raw contienen más de una imagen. Al editar una de estas
imágenes, aparece la opción de ***Sub-imagen***, que te permite editar
una de las imágenes contenidas, o combinarlas todas de una u otra forma.

Algunas cámaras *Fujifilm EXR* soportan el *modo SN* en el momento de la
captura, que significa *Prioridad a la Relación Señal a Ruido*. Al
editar una de estas imágenes raw, la lista desplegable de sub-imágenes
te permitirá seleccionar el *modo SN*, que mezcla píxeles de ambas
sub-imágenes mediante un promediado. Esto reducirá el ruido de la imagen
final.

Hay otras cámaras que te permiten realizar [*Desplazamiento de
Píxeles*](#Desplazamiento_de_Píxeles.md), por lo que habrán
varias sub-imágenes conteniendo los datos de cada toma y que podrás
combinar para obtener una imagen con más definición y menos artefactos.

En cualquier caso, si el método de desentramado es *Desplazamiento de
Píxeles*, la sub-imagen seleccionada será la base para la corrección de
objetos en movimiento. Si es cualquier otro método de desentramado, la
sub-imagen seleccionada será la que se procesará.

## Pasos de supresión de colores falsos

Ajusta cuántas veces se aplicará un filtro de
[mediana](https://es.wikipedia.org/wiki/Mediana_(estadística)) para
reducir o suprimir los artefactos que genera el algoritmo de
desentramado: los colores falsos surgen [durante la fase de
desentramado](#Introducción.md), al resolver el detalle muy
fino.

La ***Supresión de colores falsos*** consiste en igualar los colores de
los píxeles sospechosos de tener colores falsos con los colores de los
píxeles vecinos. Cuantos más *pasos* se establezcan, el radio de los
píxeles vecinos considerados será mayor (se tendrán en cuenta píxeles
cada vez más alejados). El canal de luminancia no se ve afectado por
esta supresión.

En muchas situaciones puede ser más recomendable cambiar el algoritmo de
desentramado que activar la supresión de colores falsos, pues esta
última reduce la *«resolución cromática»*.

## Desplazamiento de Píxeles *(Pixel Shift)*

### ¿Qué es y para qué sirve el *desplazamiento de píxeles*?

Algunas cámaras permiten realizar fotografías en modo *Pixel Shift*, que
captura cuatro tomas con el sensor desplazado un píxel cada vez en un
movimiento circular (determinados modelos toman hasta 16 fotos),
mientras el [filtro de
color](Sensor_with_Bayer/X-Trans_Matrix/es#Matrices_de_Filtros_de_Color_.28CFAs.29.md)
permanece quieto. Posteriormente guardan cada toma en su propio archivo
raw, que después se tiene que combinar en un solo archivo raw más grande
con programas externos (como por ejemplo [esta herramienta de Alberto
Griggio](https://github.com/agriggio/make_arq)), o bien directamente las
guardan todas juntas en un solo archivo.

La gran ventaja de este método es que al final cada fotodiodo a captado
los 3 colores, con lo que se aumenta tanto la *resolución cromática* (la
capacidad de distinguir los colores) como la *resolución espacial* (la
capacidad de distinguir los cambios de luminosidad) y además al fusionar
todas las fotos se llega a [reducir el nivel de
ruido](https://es.wikipedia.org/wiki/Sobremuestreo). Sin embargo, no
debes confundirte: la foto no tendrá más «resolución» (más megapíxeles),
sinó que será capaz de resolver (definir) mejor los detalles y los
colores.

**RawTherapee es capaz de combinar todas las tomas en una sola imagen,
al tiempo que enmascara automáticamente los objetos en movimiento,
reduce el nivel de ruido y aumenta la nitidez de la imagen.**

<figure>
<img src="/images/pixelshift_details.jpg" title="pixelshift_details.jpg" />
<figcaption>pixelshift_details.jpg</figcaption>
</figure>

A pesar de ello, dado que este modo se suele ver en cámaras de alta
gama, como ya disponen de sensores y electrónica de muy buena calidad,
la diferencia entre las fotos sin *desplazamiento de píxeles* y las que
sí lo tienen es escasa y será difícil apreciarla con una ampliación
menor del 100%. Además, **para que esta técnica tenga éxito es
imprescindible realizar las fotos sobre un trípode muy estable y con un
buen objetivo**. De cualquier otra forma la mejora conseguida será
mínima.

Por otra parte, cuando sí haya mejoras podrás observar una mayor
definición en los detalles más finos y en los degradados, menor cantidad
de ruido, menor incidencia del
[muaré](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_muar%C3%A9), así
como una gran reducción de falsos colores. En ocasiones también verás
tonos ligeramente más saturados.

Y por último, donde sí notarás mucho la diferencia será cuando realices
un procesado intensivo de la foto, especialmente si vas a realizar algún
tipo de apilado ([apilado de
enfoque](https://es.wikipedia.org/wiki/Apilamiento_de_enfoque),
[imágenes astronómicas](https://es.wikipedia.org/wiki/Astrofotografía),
[imágenes de super alta
resolución](https://es.wikipedia.org/wiki/Superresolución), ...), o
cuando imprimas en gran formato: cualquier tipo de artefacto introducido
por los algoritmos de *desentramado* habituales será inevitablemente
amplificado por las herramientas que se usen en el procesado.

<div>

- <figure>
  <img src="/images/rcd_vng4.png" title="rcd_vng4.png" />
  <figcaption>rcd_vng4.png</figcaption>
  </figure>

- <figure>
  <img src="/images/pixelshift_nomtn.png" title="pixelshift_nomtn.png" />
  <figcaption>pixelshift_nomtn.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/rcd_vng4_fc1_cac1_cs.png" title="rcd_vng4_fc1_cac1_cs.png" />
  <figcaption>rcd_vng4_fc1_cac1_cs.png</figcaption>
  </figure>

- <figure>
  <img src="/images/pixelshift_nomtn_fc1_cac1_cs.png"
  title="pixelshift_nomtn_fc1_cac1_cs.png" />
  <figcaption>pixelshift_nomtn_fc1_cac1_cs.png</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/rcd_vng4_100.jpg" title="rcd_vng4_100.jpg" />
  <figcaption>rcd_vng4_100.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/pixelshift_nomtn_100.jpg" title="pixelshift_nomtn_100.jpg" />
  <figcaption>pixelshift_nomtn_100.jpg</figcaption>
  </figure>

</div>

### El muaré

[Este
artefacto](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_muar%C3%A9) es
consecuencia directa de [convertir en datos digitales la señal
analógica](https://es.wikipedia.org/wiki/Aliasing) de la escena que
fotografíes. Por tanto habrá situaciones en que sea [difícil o imposible
de
evitar](Sensor_with_Bayer/X-Trans_Matrix/es#Filtro_de_Bayer.md).

Cuando el muaré lo genera el algoritmo de *desentramado*, en las
fotografías se muestra como zonas o manchas con menor detalle, con
colores falsos o con patrones repetitivos. En estos casos el
*desplazamiento de píxeles* lo elimina muy eficazmente.

<div>

- <figure>
  <img src="/images/stamp_rcd.jpg" title="stamp_rcd.jpg" />
  <figcaption>stamp_rcd.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/stamp_pixelshift.jpg" title="stamp_pixelshift.jpg" />
  <figcaption>stamp_pixelshift.jpg</figcaption>
  </figure>

</div>

### Igualar el brillo de las sub-imágenes

Cuando se combinan las tomas, si todas las sub-imágenes no tienen la
misma luminosidad (o sea, si la iluminación de la escena ha cambiado
aunque sea poco), habitualmente se generarán artefactos que
posteriormente pueden hacerse patentes al incrementar la nitidez de la
foto.

Al activar esta opción, todas las sub-imágenes se igualan en luminosidad
a aquella que se haya seleccionado en el [selector de
*Sub-imagen*](#Sub-imagen.md).

Si las fotos tuvieran zonas sobreexpuestas, elige la toma más luminosa
para evitar dominantes magenta en las zonas *quemadas*, o bien activa la
*detección de movimiento*.

También tienes la opción de igualar cada canal RGB individualmente o
todos por igual.

### Eliminar los objetos en movimiento

Las fotografías combinadas mediante *Desplazamiento de píxeles* pero
donde no se ha tenido en cuenta el posible movimiento en la escena, son
una mezcla simple de todas las sub-imágenes, con lo que se consigue
mejor definición de detalles y colores, así como menos ruido.

Sin embargo, **a no ser que estés realizando tomas de estudio con todos
los factores bajo control (iluminación, vibraciones, movimientos, ...),
siempre habrán zonas que se muevan o que tengan cambios de
iluminación**. Aunque sea sólo un poco.

Cuando activas la ***Corrección de movimiento***, las partes «movidas»
(las que se están moviendo durante la exposición) se sustituyen por la
versión desentramada de la [*sub-imagen*
seleccionada](#Sub-imagen.md). Es decir, toda la imagen se trata
mediante el *desplazamiento de píxeles*, excepto las zonas en
movimiento, que se tratan mediante un *desentramado* de [*mosaico de
Bayer*](Sensor_with_Bayer/X-Trans_Matrix/es#Filtro_de_Bayer.md).
Así pues, es fácil entender que en esas zonas sustituidas pierdes las
ventajas del *desplazamiento de píxeles*, pero a cambio puedes llegar a
eliminar los objetos emborronados por el movimiento.

<figure>
<img src="/images/motion-mask_sub-images.jpg"
title="motion-mask_sub-images.jpg" />
<figcaption>motion-mask_sub-images.jpg</figcaption>
</figure>

<div>

- <figure>
  <img src="/images/motion-mask_moving.jpg" title="motion-mask_moving.jpg" />
  <figcaption>motion-mask_moving.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/motion-mask_no-moving.jpg"
  title="motion-mask_no-moving.jpg" />
  <figcaption>motion-mask_no-moving.jpg</figcaption>
  </figure>

</div>

La *Corrección de movimiento* tiene tres opciones:

- ***Desactivada***: la imagen es una combinación simple de las 4
  sub-imágenes
- ***Automática***: los valores empleados los decide automáticamente
  RawTherapee y no tendrás opción de elegir ningún ajuste
- ***Personalizada***: tú decidirás los mejores valores de cada ajuste,
  dependiendo de lo que necesite la imagen

#### La máscara de movimiento

En el momento que actives la *Corrección de movimiento* RawTherapee
detectará qué áreas son sospechosas de haber sufrido cambios entre las
sub-imágenes. Éstas diferencias pueden ser debidas a movimiento de
objetos en la escena o a cambios en la iluminación de ciertas partes de
la foto, por lo que habrán áreas que parecerán «distintas» entre
sub-imágenes.

Para ver qué zonas son las que el programa a detectado, debes activar la
opción ***Mostrar la máscara de movimiento*** y hasta que la desactives
RawTherapee cubrirá las zonas con movimiento mediante una máscara de
color verde.

Si además activas ***Mostrar solamente la máscara de movimiento***, la
imagen se ocultará y verás una versión monocromo de la máscara.

<div>

- <figure>
  <img src="/images/motion-mask_green.jpg" title="motion-mask_green.jpg" />
  <figcaption>motion-mask_green.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/motion-mask_mono.jpg" title="motion-mask_mono.jpg" />
  <figcaption>motion-mask_mono.jpg</figcaption>
  </figure>

</div>

Siempre es buena idea mostrar la máscara mientras cambias los ajustes,
de forma que veas los cambios más claramente. Y recuerda que los píxeles
enmascarados serán los que vengan del *desentramado* de la sub-imagen
elegida, mientras que el resto vendrán del *desplazamiento de píxeles*.

Además, **mientras estés mostrando únicamente la máscara podrás
exportarla a una imagen**, con lo que podrás utilizarla posteriormente
en programas de retoque.

Para exportar la máscara actívala y además muestra *sólo la máscara*.
Entonces exporta la imagen. Sin embargo el resultado no será en tonos de
gris y tendrá ciertas tonalidades en los degradados (por ejemplo de
color violeta). Será conveniente que la conviertas a escala de grises en
el programa de destino.

##### El método de desentramado

Tienes 4 métodos de desentramado de la sub-imagen para las zonas en
movimiento, de [entre todos los
posibles](#Métodos_de_desentramado.md) en RawTherapee:

- AMaZE
- AMaZE + VNG4
- DCB + VNG4
- LMMSE

##### Comprobar canales

A la hora de analizar la imagen para detectar movimiento, escogerás qué
canales raw se utilizan: bien el canal verde, bien los canales rojo y
azul, o bien ambos a la vez.

Si desactivas ambas opciones, el efecto será el mismo que desactivar la
*Corrección de movimiento*.

La calidad de la detección variará según las opciones que escojas y esto
dependerá siempre de la imagen que estés procesando.

##### Rellenar los huecos

Cuando se genera la máscara de movimiento es posible que existan
pequeñas zonas dentro de un área más amplia que no tienen movimiento.
Aunque esto es perfectamente normal, es posible que aparezcan artefactos
al cambiar entre *desplazamiento de píxeles* e imagen desentramada. Por
ello esta opción rellena esos huecos y se desentrama toda el área.

#### Difuminado de la máscara

Para que la combinación entre las partes de la foto con movimiento y las
estáticas sea suave tienes el ***Difuminado de la máscara***, que al
aplicarlo
[difuminará](https://es.wikipedia.org/wiki/Desenfoque_gaussiano) los
bordes de la máscara y mezclará ambas reproducciones de la foto.

Y para controlar su alcance tienes el ***Radio de difuminado***: cuanto
más alto, mayor será el tratamiento que sufrirá la máscara para intentar
una fusión adecuada entre la imagen desentramada y la de *desplazamiento
de píxeles*.

Sin embargo el propio proceso de suavizado de los límites de la máscara
provoca que esta «se encoja», con lo que irá modificando su forma según
aumentes el *radio de difuminado*. Además, mediante el mismo
procedimiento las zonas más pequeñas de la máscara se desvanecerán.

<div>

- <figure>
  <img src="/images/motion-mask_noblur.jpg" title="motion-mask_noblur.jpg" />
  <figcaption>motion-mask_noblur.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/motion-mask_blur1.jpg" title="motion-mask_blur1.jpg" />
  <figcaption>motion-mask_blur1.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/motion-mask_blur3.jpg" title="motion-mask_blur3.jpg" />
  <figcaption>motion-mask_blur3.jpg</figcaption>
  </figure>

</div>

Y con radios de difuminado muy altos, los artefactos provocados por el
movimiento empiezan a aparecer de forma muy notoria (la máscara ha
perdido «sensibilidad»). Por ello no es aconsejable usar radios altos a
no ser que sea imprescindible.

<figure>
<img src="/images/motion-mask_blur23.jpg" title="motion-mask_blur23.jpg" />
<figcaption>motion-mask_blur23.jpg</figcaption>
</figure>

En el caso de necesitar usar el *difuminado de la máscara*, además de
ser necesario realizar todos los cambios con la máscara a la vista,
puesto que el propio difuminado tiene tendencia a reducir la detección
en algunas zonas, deberás ir ajustando [la zona de
transición](#Las_transiciones_suaves.md) para volver a incluir
las zonas necesarias y la [sensibilidad de la
detección](#La_sensibilidad_de_la_detección_de_movimientos.md)
para detectar mejor el movimiento.

#### Las transiciones suaves

Independientemente del *radio de difuminado* escogido, las
***Transiciones suaves*** procuran evitar cambios bruscos entre las
zonas con movimientos detectados y las zonas inmóviles.

Para ello crea una *zona de influencia* de la máscara, incluyendo
posibles artefactos debidos al movimiento y cercanos a la máscara, pero
que son más sutiles y no han sido previamente detectados. Este añadido
es semitransparente, para combinar ambas versiones de la foto.

Cuanto más bajo sea el valor de esta opción, menor será la capacidad de
detección de las transiciones y menor peso tendrá la imagen desentramada
en la combinación. Por el contrario, cuando llegas a *1.0*, únicamente
se muestra la versión desentramada de la sub-imagen seleccionada. Con el
valor por defecto (*0.70*) la integración de las imágenes suele ser
óptima.

#### La sensibilidad de la detección de movimientos

La herramienta localiza y selecciona las áreas dónde sospecha que ha
habido cambios en la imagen y genera una máscara.

Por defecto la ***Sensibilidad*** tiene una capacidad de detección que
funciona bastante bien con los valores ISO nativos del sensor
(normalmente entre 50 y 200 ISO) y en el deslizador se establece como
*0*. Es decir, *0* no significa que no haya detección de movimiento,
sinó que es el valor que se considera más apropiado en la mayoría de los
casos.

Un valor mayor en este deslizador aumenta las zonas detectadas con
«movimiento» (con cambios), lo cual implica que en esas zonas no se
aprovechará el *desplazamiento de píxeles*. Por el contrario, un valor
menor implica que sólo las zonas con cambios más notables se detectarán
y empezarán a observarse artefactos en la forma de partes de la foto
donde se ve una trama similar al *mosaico Bayer*.

Para valores ISO altos es recomendable aumentar la *Sensibilidad*,
aunque siempre con la máscara activada y poco a poco.

<div>

- <figure>
  <img src="/images/motion-mask_sens-5.jpg" title="motion-mask_sens-5.jpg" />
  <figcaption>motion-mask_sens-5.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/motion-mask_sens5.jpg" title="motion-mask_sens5.jpg" />
  <figcaption>motion-mask_sens5.jpg</figcaption>
  </figure>

</div>

#### Usar la mediana para las partes en movimiento

En lugar de usar la sub-imagen seleccionada para las zonas con
movimiento, RawTherapee emplea la mediana de todas las sub-imágenes.

Esto tiene como ventaja que elimina los objetos que están en distintos
sitios *en todas las sub-imágenes*, así como emborrona los objetos que
se mueven despacio (que se superponen).

Sin embargo, si la superposición no es ligera, es decir que el objeto no
se mueve tan despacio, aparecen artefactos como dobles imágenes o partes
del objeto en movimiento en la imagen final.

<figure>
<img src="/images/motion-mask_median.jpg" title="motion-mask_median.jpg" />
<figcaption>motion-mask_median.jpg</figcaption>
</figure>

## Cómo seleccionar el mejor método de desentramado

En realidad no hay un método de *desentramado* netamente mejor que los
otros y la elección va a depender de cada fotografía, de su contraste,
iluminación, tonos (colores), presencia de líneas rectas y diagonales,
ruido, ...

Un posible sistema para encontrar qué método funciona mejor con la foto
que estés procesando es:

- amplía la imagen *al menos* al 100% (1:1) y céntrala en la zona más
  importante de la foto
- escoge otras zonas importantes de la foto y añade varias [*ventanas de
  detalle*](Editor/es#ventana_de_detalle.md)
  (<img src="/images/window-add.png" title="window-add.png" height="26"
  alt="window-add.png" />) con una ampliación de al menos el 100%. De
  esta forma puedes tener una idea general de cómo queda la fotografía,
  aunque no la veas toda en pantalla
- prueba todos los algoritmos de desentramado y escoge el que mejor
  funcione con la foto

A la hora de escoger qué incluir en las *ventanas de detalle*, son
importantes:

- las zonas de detalles finos y patrones diminutos (como el tejido de un
  suéter)
- los patrones artificiales repetitivos (como paredes de ladrillo)
- puntos de luz brillantes (como una señal de tráfico o una farola
  encendida)
- bordes muy contrastados (como bordes de zonas oscuras contra el cielo
  brillante de fondo)
- zonas más o menos sin detalles pero con ruido (como en las fotos con
  valores ISO altos)
- zonas con líneas rectas delgadas y muy juntas (como un cercado de
  tablones de madera visto a lo lejos)
- líneas irregulares pero muy finas (como el cabello encrespado o las
  ramas finas de un árbol con el cielo brillante de fondo)

Por último, es importante que recuerdes que **el mejor método de
desentramado para una foto no tiene por qué serlo para todas**. Y
también que **no hay ningún método de desentramado perfecto: todos
mostrarán algún defecto o problema en tu foto**, así que debes escoger
el que menos defectos genere.
