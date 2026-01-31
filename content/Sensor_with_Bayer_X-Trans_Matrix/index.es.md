---
title: Sensor with Bayer X-Trans Matrix
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Sensores

</div>
<div class="headline">

Información general sobre los sensores y su tecnología

</div>

## Introducción

Las cámaras digitales contienen un *sensor* formado por millones de
elementos sensibles a la luz llamados
[***fotodiodos***](https://es.wikipedia.org/wiki/Fotodiodo).

Como estos fotodiodos no distinguen los colores, el sensor tiene una
[*matriz de filtros de color*
(*CFA*)](#Matrices_de_Filtros_de_Color_.28CFAs.29.md) para
captar los tonos de la escena, de modo que cada fotodiodo capta sólo una
longitud de onda concreta. El [*filtro
Bayer*](#Filtro_de_Bayer.md) es el más común, aunque también
existen otros filtros como el [*X-Trans*](#filtro_x-trans).
**Estos dos son los únicos filtros de color revelados por RawTherapee**,
mientras que el resto de filtros del mercado no son compatibles con el
programa.

Sin embargo, los datos que aporta el sensor sólo son una matriz con 3
colores repartidos entre los píxeles, por lo que antes de poder ver la
imagen los datos tienen que ser procesados mediante el
[*Desentramado*](demosaicing/es).

## Tecnología de los sensores

Un ***sensor*** es un instrumento capaz de captar luz y transformarla en
señales que acabarán convertidas en datos digitales.

De su calidad, diseño y tamaño depende en buena parte la calidad final
de la imagen generada por la cámara.

### Cómo funcionan los sensores

La luz se suele representar como pequeñas partículas que acumulan
energía: son los [fotones](https://es.wikipedia.org/wiki/Fot%C3%B3n).

Dependiendo de la energía que hayan acumulado, estos fotones se
desplazan con una determinada [longitud de
onda](https://es.wikipedia.org/wiki/Longitud_de_onda): cuanto mayor es
la energía acumulada, menor es su londitud de onda. Es decir, con mayor
cantidad de energía los fotones se agitan más rápidamente y la longitud
de onda es más corta. Además, la *intensidad de la luz* corresponde al
número de fotones presentes en el [flujo de la
iluminación](https://es.wikipedia.org/wiki/Flujo_radiante).

A su vez, nuestro complejo ojo-cerebro interpreta la energía con la que
llegan los fotones (las longitudes de onda) y la intensidad (la cantidad
de fotones) como colores con distintos grados de brillo y saturación.

![](Photoelectric_effect_in_a_solid_-_schematic_diagram.png "Photoelectric_effect_in_a_solid_-_schematic_diagram.png")
Por el contrario, un sensor no es más que un instrumento electrónico con
una matriz de elementos sensibles a la luz que al captar los fotones
liberan electrones, tantos más cuanto mayor sea la intensidad de la luz
y su longitud de onda (su energía).

Así pues, un fotodiodo (*sensel*, píxel) únicamente es capaz de generar
impulsos eléctricos, o visto de otro modo, únicamente genera imágenes en
escala de grises. Debido a esto sobre el sensor se sitúa una [matriz de
pequeños filtros de
color](#Matrices_de_Filtros_de_Color_.28CFAs.29.md), uno por
cada fotodiodo, de forma que el valor eléctrico generado corresponde
únicamente a una longitud de onda.

Tras haber capturado todos los fotones y generado los voltajes
correspondientes, la electrónica asociada del sensor los convierte a
valores digitales, que son con los que trabajarás en RawTherapee.

Por otra parte, cada fotodiodo puede «contener» una cantidad máxima de
esos electrones generados, llamado en inglés *Full Well Capacity*:
cuanto mayor es el tamaño del fotodiodo, más electrones podrá contener,
mayor será su sensibilidad a la luz, mejor su [*Indice Señal-Ruido*
(*Signal to Noise Ratio,
SNR*)](https://es.wikipedia.org/wiki/Relaci%C3%B3n_se%C3%B1al/ruido) y
mayor su [rango
dinámico](https://es.wikipedia.org/wiki/Rango_din%C3%A1mico#Rango_din%C3%A1mico_aplicado_a_la_%C3%B3ptica_(fotograf%C3%ADa)).

Es interesante insistir en que esta capacidad máxima de captación en
general está relacionada directamente con el tamaño del fotodiodo, así
que un sensor con mayor cantidad de píxeles no es necesariamente mejor,
a no ser que el tamaño del sensor (de sus fotodiodos) sea también más
grande.

### CCD y CMOS

Las tecnologías principales de los sensores se dividen en *«tipo CCD»* y
*«tipo CMOS»*.

Los sensores **CCD** presumen de ofrecer mejor calidad de imagen,
fotografías «congeladas» (sin distorsiones en los objetos en movimiento)
y menor nivel de ruido. En cambio los sensores **CMOS** son más rápidos
a la hora de transferir la imagen a la CPU de la cámara, son más baratos
y controlan mejor los artefactos producidos por las luces «quemadas».
Sin embargo la tecnología no deja de evolucionar y las diferencias son
cada vez menores, de manera que no hay ningún tipo de sensor realmente
mejor que el otro.

En cuanto a la velocidad de transferencia, el diseño de los CCDs hace
que los datos se envíen línea a línea a través de una única salida,
mientras que los CMOS son más rápidos porque envían los datos de forma
paralela (en grupos de columnas) a través de múltiples salidas. Y esta
salida múltiple puede generar bandas en la imagen, que podrás corregir
con el [*Filtro de ruido en
bandas*](Preprocessing/es#Filtro_de_ruido_en_bandas.md).

El propio proceso de salida de datos también genera ruido: los CCD
envían las señales fuera del sensor en formato analógico y
posteriormente se convierten a datos digitales, lo cual genera ruido.
Por el contrario los CMOS realizan la conversión a nivel de fotodiodo,
antes de realizar la transferencia, lo cual genera una cantidad menor de
ruido. En ambos casos RawTherapee puede mitigarlo o eliminarlo gracias a
la herramienta [*Imagen de Negro Base*](dark-frame/es).

Sin embargo, la cantidad de electrónica asociada a cada fotodiodo hace
que los sensores CMOS tengan menos sensibilidad a la luz que los CCD: la
electrónica refleja parte de la luz, o simplemente el fotodiodo debe ser
más pequeño para que la electrónica quepa en el sensor. Pero ya hay
tecnologías que mejoran la [eficiencia
cuántica](https://es.wikipedia.org/wiki/Eficiencia_cuántica) de los
diodos, como la [*Retroiluminación del
sensor*](#Tecnologías_de_mejora_del_sensor.md).

### Tecnologías de mejora del sensor

Además de las distintas formas genéricas de trabajar de los sensores,
los fabricantes están trabajando constantemente en distintas formas de
mejorar sus respuestas, como por ejemplo:

- **Micro-ópticas sin separaciones**: las *micro-ópticas* o
  *«micro-lentes»* son unas diminutas ópticas situadas encima de cada
  fotodiodo, de forma que concentran la luz y el fotodiodo la capta
  mejor. Una de las mejoras introducidas es que estas micro-ópticas
  están tocándose unas a otras, por lo que no se desperdicia nada de
  luz. Otra mejora las acerca más al fotodiodo, por lo que la eficiencia
  de la recepción es mejor. Ambas mejoras implican una reducción de
  ruido en la imagen.
- **Enfoque Automático por Detección de Fase (EADF) embebido en el
  sensor**: se trata de unas líneas de fotodiodos incluidos en la matriz
  del sensor, que se utilizan para mejorar la velocidad de enfoque
  automático de los objetivos. Mejora particularmente importante
  mientras se utiliza la *Vista previa en directo* o mientras se graban
  videos.
- **Pistas eléctricas de cobre**: que podrían llegar a llamarse
  *«cableado» de cobre*. Mejora la transferencia eléctrica, con lo que
  las *pistas* (los «cables») pueden ser más finas y queda más espacio
  libre para el fotodiodo, por lo que mejora la sensibilidad del sensor.
- **Retroiluminación del sensor**: conocido como *BSI* o *Exmor*.
  Básicamente toda la electrónica y las pistas eléctricas se sitúan bajo
  el fotodiodo, por lo que este no tiene obstáculos a la hora de captar
  la luz. Tecnología importante para múltiples características del
  sensor, como la reducción de ruido, mejora de la sensibilidad,
  capacidad de reducir los fotodiodos sin disminuir la calidad de la
  imagen, ...

### Anatomía del sensor

En general los sensores habituales constan de:

- micro-ópticas: dirigen la luz hacia el fotodiodo, aumentando la
  sensibilidad de este a la luz.
- matriz de filtros de color (CFA): que en la mayoría de las cámaras se
  trata de un filtro Bayer.
- filtro de paso bajo ([filtro anti
  solapamiento](https://es.wikipedia.org/wiki/Aliasing)): destinado a
  limitar el tamaño mínimo de los detalles de forma que no se generen
  [*patrones de muaré*](https://es.wikipedia.org/wiki/Patrón_de_muaré) u
  otros artefactos debidos a la presencia de detalles demasiado finos
  para el tamaño de los fotodiodos. Cada vez hay más cámaras sin este
  tipo de filtros.
- filtro de infrarrojos: para evitar que el sensor los capte e
  interprete que se trata de luz visible.
- circuitos electrónicos.
- fotodiodos.
- píxeles «negros»: todos los fotodiodos del sensor no se utilizan para
  generar la imagen, pues aquellos situados en la periferia normalmente
  están tapados para que no reciban luz y se usan para estimar la
  cantidad de [ruido de corriente de
  oscuridad](https://es.wikipedia.org/wiki/Corriente_de_oscuridad) de la
  foto.

## Matrices de Filtros de Color (CFAs)

Los fotodiodos de los sensores más habituales únicamente son capaces de
generar electrones, independientemente del color de la luz que capten
(de su longitud de onda). Por ello para ser capaz de distinguir los
tonos de la escena el sensor tiene una **matriz de filtros de color**
(**CFA**, del inglés *Color Filter Array*) situada encima de los
fotodiodos, de modo que cada fotodiodo capta sólo una longitud de onda
concreta.

<figure>
<img src="/images/Bayer_pattern_on_sensor_notext.png"
title="Bayer_pattern_on_sensor_notext.png" />
<figcaption>Bayer_pattern_on_sensor_notext.png</figcaption>
</figure>

### Filtro de Bayer

![](Bayer_matrix.png "Bayer_matrix.png") El ***filtro o matriz de
Bayer*** es el tipo de filtro más común en los sensores de imagen
digital y contiene el doble de elementos verdes que rojos o azules,
dispuestos en filas rojas y filas azules, con filtros verdes
intercalados.

Como resultado de este filtrado, la *«resolución cromática»* sufre
bastante, ya que sólo hay información del canal rojo o del canal azul
cada dos líneas. Sin embargo existen métodos de
[*desentramado*](demosaicing/es) muy sofisticados que
consiguen combinar los datos disponibles y regenerar en gran medida la
escena original.

Sin embargo, estos mismos métodos generan una serie de artefactos muy
difíciles de evitar:

<div class="tlist">

<figure>
<img src="/images/demosaic_artifacts.jpg" title="demosaic_artifacts.jpg" />
<figcaption>demosaic_artifacts.jpg</figcaption>
</figure>

- [muaré](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_muar%C3%A9): si
  la escena proyectada sobre el sensor tiene pequeños detalles con un
  tamaño similar o múltiplo del límite de resolución (el detalle más
  pequeño que puede distinguir el sensor), estos detalles pueden
  aparecer en la imagen como patrones o líneas repetidas, «marcas de
  agua», artefactos de color o píxeles dispuestos en un patrón
  laberíntico poco realista.
- colores falsos: normalmente este artefacto se manifiesta a lo largo de
  los bordes, donde se producen cambios abruptos o antinaturales en el
  color como resultado de una interpolación errónea.
- artefacto *en cremallera*: también se produce principalmente a lo
  largo de los bordes y se conoce como el «efecto cremallera». Se
  produce en un patrón de *«encendido y apagado»* a lo largo del borde.

</div>

Sin embargo, incluso con un sensor teóricamente perfecto que pudiera
capturar y distinguir todos los colores en cada fotodiodo, tanto el
muaré como otros artefactos podrían seguir apareciendo: se trata de una
consecuencia inevitable en cualquier sistema que codifique una señal
contínua mediante el [muestreo en intervalos
limitados](https://es.wikipedia.org/wiki/Aliasing).

Por ello la mayoría de los sensores digitales fotográficos incorporan el
[*filtro óptico de paso bajo
(OLPF)*](https://es.wikipedia.org/wiki/Filtro_antialiasing): se trata de
un filtro situado sobre el sensor que actúa difuminando cualquier
detalle potencialmente problemático (que sea más fino que la resolución
máxima del sensor).

### Filtro X-Trans

![](XTrans_matrix.png "XTrans_matrix.png") Esta matriz de color es un
diseño para las cámaras de Fujifilm y utiliza una nueva disposición de
los filtros, que se dice que imita a la película y está diseñado para
mejorar la captura de detalles, reducir los niveles de ruido, minimizar
los efectos del muaré y el falso color y a su vez, aumentar la
resolución al eliminar la necesidad de un *filtro de paso bajo*.

Además, los sensores X-Trans tienen una *«resolución cromática»*
mejorada debido a que todas las líneas horizontales y verticales
contienen al menos un píxel R, G y B.

En cambio, a pesar de todas las ventajas también tienen sus propios
problemas:

- con determinadas condiciones pueden generarse artefactos de
  destellos/rejillas de color púrpura en las fotos a contraluz. La
  apariencia de este efecto puede variar según los algoritmos de
  desentramado que se usen.
- tienen mayores requisitos de procesamiento debido a la disposición de
  los filtros de color.

### Otros

#### Foveon X3 (no compatible con RawTherapee)

Este sensor es único porque cada píxel de la imagen ha captado realmente
los 3 colores (R, G y B): tiene los fotodiodos dispuestos en 3 capas,
una sobre la otra y cada cual absorbiendo un color (más o menos). Por
esto no es necesario el *desentramado*.

Si bien la idea de que cada píxel reciba los 3 colores es deseable, la
tecnología necesaria para conseguirlo es muy compleja y en realidad cada
capa no absorbe únicamente un color:

- la capa superior, la que capta el color azul, en realidad capta los 3
  colores, aunque en mayor proporción el color azul
- la capa media, la verde, recibe luz filtrada sin azul pero también sin
  algo de verde y rojo, captando el fotodiodo el verde y algo del rojo
- la capa más profunda, la roja, recibe sólo luz roja, pero en menor
  cantidad que la que entró por el objetivo

Por ello posteriormente se deben realizar cálculos complejos para
separar o «purificar» los datos de cada capa.

Además, como las dos capas inferiores reciben menos cantidad de luz
(especialmente la roja), en el proceso de amplificar y equilibrar las
señales de los 3 colores se genera más ruido que en un sensor CMOS
típico, especialmente en situaciones de iluminación pobre.

En conjunto la complejidad de los cálculos y la deficiencia de luz en
las capas inferiores dan una fidelidad de color pobre y una imagen más
ruidosa. A cambio, la *«resolución espacial»* es mucho mayor, ya que la
luminosidad de cada píxel es real (se ha captado de verdad, no se ha
«adivinado» por interpolación) y por tanto la cantidad y fidelidad de
los detalles es mucho mayor.

#### Sensor «EXR» (descatalogado)

Se trata del sensor *Super CCD* creado por Fujifilm, quien diseñó varias
versiones de una disposición especial de los fotodiodos, que se
alineaban en diagonal, en lugar de en horizontal. Además también
introdujo otros fotodiodos más pequeños en la matriz, de forma que se
lograba mayor resolución o mayor rango dinámico (según la versión del
sensor).

#### Monocromo (Blanco y Negro)

Un sensor que genere imágenes en blanco y negro no tiene ningún filtro
de color, por lo que cada uno de sus fotodiodos captan el detalle real
de la escena, sin necesidad de desentramado alguno.

Por esto mismo, suponiendo un sensor de buena calidad, la *«resolución
espacial»* es muy superior a la que se puede obtener con cualquier
sensor en color: cada fotodiodo capta la luminosidad real de la escena,
en lugar de estimarla («adivinarla») a base de interpolaciones con los
píxeles vecinos. La excepción a esto podrían ser las cámaras con 3
sensores (uno para cada canal de color) y las cámaras con
*desplazamiento de píxeles (Pixel Shift)*. En cambio, a pesar de las
estrategias de marketing, un sensor Foveon *«de 39 MPx»* no dará la
misma *resolución espacial* que un sensor monocromo de 40 MPx, al no
tener la misma cantidad de fotodiodos: la diferencia de 1 MPx real no
supondría una diferencia discernible, pero lo cierto es que el sensor
Foveon tiene realmente mucha menor cantidad de fotodiodos (alrededor de
25 MPx) y esto sí causa una diferencia notable.

## Tamaños de sensor

Los sensores se agrupan en tamaños estándar expresados en pulgadas, a
excepción de lo que se llama ***fotograma completo***.

Estos tamaños en pulgadas **no indican el diámetro del sensor**, sinó
que están referidos a unos tamaños estándar de los [tubos de rayos
catódicos](https://es.wikipedia.org/wiki/Tubo_de_rayos_catódicos) de las
televisiones de los años 50: estos tubos tenían unos diámetros estándar
y los sensores actuales se aproximan vagamente a un diámetro aproximado
de 2/3 de esos tubos. Así pues, un sensor de 1" tiene una diagonal de
alrededor de 2/3" (aunque no es una proporción exacta, sinó
orientativa).

Los tamaños más usuales son:

- **Fotograma completo** o **36 x 24**: se trata de un tamaño idéntico
  al de los fotogramas de la clásica *película de 35mm*, que medía
  36x24mm. La gran ventaja de este tamaño es que con la misma resolución
  que sensores más pequeños los fotodiodos son más grandes, por lo que
  el [rango dinámico](https://es.wikipedia.org/wiki/Rango_dinámico)
  aumenta y la sensibilidad a la luz también es mayor
- **APS-C**: el tamaño más común en las cámaras no profesionales. Es
  alrededor de un 66% del tamaño del *fotograma completo*. Si utilizas
  objetivos para *fotograma completo* con estas cámaras, su distancia
  focal y su abertura deben multiplicarse por aproximadamente *1,5*
  (excepto con las cámaras Canon, que es *1,6*). Así pues un objetivo
  200/2,8 se convierte de manera efectiva en aproximadamente un 300/4,2
  (dependiendo del modelo de cámara). Por el contrario, un objetivo
  diseñado para sensores *APS-C* no debería usarse en cámaras de
  *fotograma completo*, ya que las imágenes presentarían un fuerte
  viñeteado
- **Cuatro Tercios** o **Micro Cuatro Tercios**: sensor típico de las
  [*cámaras sin visor
  óptico*](https://es.wikipedia.org/wiki/Cámara_sin_espejo_de_objetivos_intercambiables).
  Tiene un tamaño aproximado de un 25% del tamaño del *fotograma
  completo*
- Otros: *una pulgada*, *1/1.7*, *1/2.3*, etc. Se trata de sensores
  habituales en las cámaras de videovigilancia, cámaras compactas,
  cámaras de control de calidad, etc. Suelen ser los sensores necesarios
  para los objetivos con [*montura
  C*](https://es.wikipedia.org/wiki/Montura_C)
