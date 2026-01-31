---
title: Color Management
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Gestión del color

</div>
<div class="headline">

La gestión de color es el sistema con el que conseguimos que las
imágenes presenten los mismos colores en cualquier medio en el que se
muestren.

</div>

__toc__

## Por qué es necesaria

<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 550px">

<imgcomp img1='noprofile.jpg' img2='profiled.jpg'  width=550 />

<div class="thumbcaption">

La imagen de la izquierda no tiene aplicado ningún perfil de entrada,
mientras que a la derecha se muestra la misma imagen una vez aplicado el
perfil de entrada correcto. Fíjate en los cambios de tono visibles en
todos los tonos pero especialmente en el azul, verde y amarillo

</div>
</div>
</div>

Si has *revelado* alguna foto te habrás dado cuenta que a pesar de los
ajustes que hagas a las imágenes, estas no aparecen en el monitor o la
impresora con los colores que tenía la escena original. También puedes
haber observado que, para una misma imagen, el aspecto de los resultados
en pantalla no es igual que en la impresora, ni tampoco entre diferentes
marcas y modelos del mismo dispositivo (sea pantalla o impresora).

Si te preguntas cómo conseguir siempre resultados con colores fieles a
la escena y con la misma apariencia tanto en la pantalla como en el
papel impreso, la respuesta la tienes en la gestión del color en
fotografía.

**La gestión del color procura obtener una buena correspondencia de
colores entre dispositivos y es una parte muy importante para todo
fotógrafo, ya que de ella depende todo el procesado desde la captura
hasta la presentación (impresa o en pantalla) de las fotos.**

## La problemática de la gestión del color

En teoría trabajar con colores digitales no debería ser difícil, puesto
que sólo se trata de usar las matemáticas para modificarlos: añade 10 de
rojo, quita 25 de verde y ya está... Pero no, no es tan fácil ni rápido:
nuestro sistema ojo-cerebro realiza complejas transformaciones
psicofísicas que nos ayudan a relacionarnos con el mundo en el que
vivimos, haciendo cambios en los datos reales que reciben nuestros ojos
para que tengamos la información que necesitamos. Por ejemplo: tenemos
una mayor sensibilidad a la claridad que a los colores, por lo que
todavía podemos ver al atardecer aunque no apreciemos bien los tonos.
Además sólo podemos ver una cierta gama de colores, no más allá del
violeta (ultravioletas), no por debajo del rojo (infrarrojos).

Aún más, los sensores de las cámaras no reaccionan a la luz como lo hace
nuestro complejo ojo-cerebro: los diferentes fotodiodos no son sensibles
a la misma gama de colores que nuestras células de la retina, ni captan
la luz con la misma intensidad. Esto es, el sensor captura la luz de
forma lineal, mientras que el ojo-cerebro transforma la luz capturada
para realzar las sombras sin perder mucha información de las luces (es
decir que no tiene una respuesta lineal a la luz).

Además, lo que nuestros ojos realmente hacen es escanear pequeñas áreas
de nuestro campo visual y enviar las *instantáneas* parciales a nuestro
cerebro, que las une en una especie de mosaico
[HDR](https://es.wikipedia.org/wiki/Imágenes_de_alto_rango_dinámico).

<figure>
<img src="/images/CIExy_color_gamut_diagram.jpg"
title="CIExy_color_gamut_diagram.jpg" />
<figcaption>CIExy_color_gamut_diagram.jpg</figcaption>
</figure>

Por si lo anterior no fuera suficiente, para nuestros ojos a veces 2+2
no es 4 y por ejemplo el doble de intensidad de un color no lo
percibimos como «el doble de color». Sin embargo, para un sensor captar
el doble de luz sí implica el doble de color y su respuesta lineal se
proyecta en el [diagrama de cromaticidad
CIExy](https://es.wikipedia.org/wiki/Espacio_de_color_CIE_1931). *Pero
[no olvides que este diagrama en concreto no representa cómo apreciamos
y diferenciamos los colores con nuestros
ojos](#Los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")*.

Por su lado, los sensores de las cámaras son capaces de capturar un
cierto [rango de
colores](#los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")
que normalmente se representan como un triángulo dentro del diagrama de
cromaticidad. Además tienes las pantallas que te permiten ver las
imágenes y que también son capaces de mostrar sólo un cierto rango de
colores (otro triángulo, o
[*gamut*](https://es.wikipedia.org/wiki/Gama_de_color)). Por último,
cuando estés contento con tus imágenes querrás imprimirlas en un
dispositivo que también tiene su propio rango de colores (*gamut*). Y
ninguno de ellos coincide con los demás: por ejemplo un sensor puede ser
más sensible a los azules o los naranjas, pero no puede capturar algunos
de los verdes más saturados, mientras que las impresoras ofrecen cianes
y magentas más saturados que las pantallas, que por su lado pueden ser
capaces de mostrar verdes saturados sin problemas.

Todas estas disparidades hacen que resulte harto complicado «acoplar»
los colores en los distintos dispositivos para que sean parecidos a *lo
que nuestro cerebro dice que vemos*.

La manera que tiene RawTherapee de gestionar todo esto es mediante
**perfiles de color**.

## Los perfiles de color en RawTherapee

Un perfil de color es un conjunto de datos que utilizarás para convertir
con precisión el rango de colores usados por unos dispositivos en el
rango usado por otros dispositivos. En particular, un perfil siempre
está ligado a un [espacio de
color](#los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")
concreto que limita la cantidad total de colores posibles una vez
seleccionas ese perfil.

En la gestión de color todo funciona alrededor de un conjunto de colores
de referencia y para cada dispositivo debes emplear un perfil de color
que traduzca entre las peculiaridades de ese dispositivo y los colores
de referencia.

### Una analogía

Cada vez que haces una cosa aunque no te des cuenta en realidad estás
haciendo muchas cosas una tras otra, igual que RawTherapee. Digamos que
estás mirando un objeto: tus ojos están capturando luz, que tu retina
transforma en señales eléctricas, que después interpreta tu cerebro y
transforma en algo que entiendes. Por último le dices a alguien lo que
acabas de ver.

Si te paras a pensarlo hay una serie de transformaciones en todo ese
proceso: una desde la retina a las neuronas, otra desde las señales
eléctricas de las neuronas a la interpretación del cerebro y otra desde
el cerebro a la boca. De igual forma trabaja un programa de procesado
raw.

Ahora imagina que tienes una imagen que quieres procesar con
RawTherapee:

- tendrás que decirle al programa cómo se codificó esa imagen (cómo se
  transformó desde colores de la vida real a colores digitales): esto lo
  consigues designando el **perfil de entrada** apropiado en la
  herramienta de Gestión del Color
- también tendrás que decidir si el perfil interno que usa el programa
  para sus cálculos es adecuado o no: éste es el **perfil de trabajo**.
  Aunque por defecto el perfil es ProPhoto, puedes elegir cualquier
  otro, aunque es mejor que sea lo suficientemente grande (Rec2020,
  ACES, ...)
- mientras estás editando la imagen, lo más probable es que quieras ver
  interactivamente lo que estás consiguiendo: le debes indicar al
  programa un **perfil adecuado para tu pantalla**, de manera que una
  copia de la imagen interna se convierte a otra que puede ser mostrada
  en pantalla. Y no te preocupes, ya que la imagen interna no se
  modifica en absoluto en este proceso. Es sólo para que puedas ver lo
  que haces
- por último, seguro que deseas una copia del resultado final y para
  conseguirla debes indicarle a RawTherapee el **perfil de salida**, que
  dependerá del destino de la imagen (la pantalla si la vas a subir a la
  web, una impresora, ...)

Todo ésto es necesario porque las imágenes digitales se codifican con
tres colores (rojo, verde y azul) y cada sensor fija esos colores en
tonos distintos (colores básicos más o menos saturados), así que
RawTherapee debe saber cómo transformar esos colores básicos para que
todos los dispositivos tengan los mismos colores de referencia. Y si
hablamos de impresión, la codificación es en cuatro colores (cian,
magenta, amarillo y negro), pero el proceso es análogo: la mezcla de los
cuatro colores en cualquier impresora debe dar el mismo tono.

### Los cinco tipos de perfiles de color y la interfaz del programa

En RawTherapee puedes configurar los siguientes tipos de perfiles:

- **de entrada**: sirve para indicarle al programa cómo convertir los
  colores de la imagen raw en colores estándar. Habitualmente
  seleccionarás el perfil que coincida con la cámara que ha captado la
  foto, o el instrumento que haya generado la imagen
- **de trabajo**: define el espacio de color en el que RawTherapee
  trabajará internamente con la foto. Únicamente define los límites de
  los colores posibles con los que trabajar, sin tener en cuenta ningún
  otro dato existente en el perfil seleccionado (gamma, curva de tono,
  ...). Es decir, únicamente tiene en cuenta los colores primarios del
  perfil
- **de salida**: es el perfil que define el rango de colores de la
  imagen final, así como la gamma aplicada a la imagen. Es importante
  seleccionar bien el perfil adecuado según el destino que vaya a tener
  la imagen (la pantalla, la impresora, otro programa para editar aún
  más la imagen, ...)
- **de pantalla**: este perfil se emplea para aprovechar al máximo las
  capacidades de color de tu pantalla. Sin embargo, si vas a publicar la
  imagen en internet para verla en pantalla, deberás tener cuidado con
  este perfil.  
  En general la gestión de color en los navegadores es un tema casi
  secundario (*Firefox* es una excepción, ya que cuenta con una gestión
  decente, pero no es trivial configurarla) y en concreto el problema
  que existe en *Chrome/Chromium* es bastante sangrante: tal y como está
  programado (al menos hasta la versión 85) no hay manera de que acepte
  nada de un perfil personalizado que no sean los 3 colores primarios.
  La gamma (o TRC) será siempre la del espacio de color sRGB.  
  Esto, que puede parecer un tema sin consecuencias, significa que si
  creas un perfil ICC personalizado para tu pantalla (algo muy
  recomendable y que precisa de un
  [colorímetro](https://www.fotonostra.com/glosario/espectrofotometro.htm)
  o un
  [espectrofotómetro](https://www.fotonostra.com/glosario/espectrofotometro.htm))
  y lo utilizas tanto en el sistema operativo como en RawTherapee, los
  revelados que veas en RawTherapee no serán iguales a los que muestre
  *Chrome/Chromium*. El resultado típico en estos navegadores será más
  oscuro y con algunas tonalidades algo diferentes. La única solución
  actual es crear un perfil personalizado para la pantalla forzando el
  TRC estándar de sRGB.
- **de prueba de impresión**: la prueba de impresión en pantalla
  (*soft-proofing*, en inglés) está dedicada a simular los colores que
  imprimirás con el procesado actual (siempre asumiendo que has
  especificado un perfil de color de impresora que simule correctamente
  la combinación de tu impresora con el papel que utilizas). Para
  obtener la máxima calidad de impresión, tras ajustar tu foto usando la
  prueba de impresión en pantalla, debes seleccionar como perfil de
  salida uno con un tamaño suficiente que albergue todos los colores que
  puede generar la impresora. Normalmente esto implicará exportar con el
  perfil ProPhoto, o incluso el ACESp0. De esta forma la imagen se podrá
  imprimir sin perder ningún tono.

Una vez has configurado todos estos perfiles, podrás usar los siguientes
botones:

- ![<File:gamut-hist.png>](gamut-hist.png "File:gamut-hist.png") Rango
  de colores (*gamut*): botón ligado a los perfiles *de trabajo* y *de
  salida*. Modifica el cálculo de la forma del histograma y los los
  valores RGB, HSV y L\*a\*b\* mostrados en el panel de navegación. Si
  está desactivado (
  <img src="/images/gamut-hist-off.png" title="gamut-hist-off.png" width="21"
  alt="gamut-hist-off.png" /> , por defecto) tanto el histograma como
  los valores de los píxeles en el panel emplearán el perfil de salida.
  En cambio si el botón está activado (
  <img src="/images/gamut-hist.png" title="gamut-hist.png" width="21"
  alt="gamut-hist.png" /> ) veremos el histograma y los valores con los
  que trabaja el motor del programa codificados en el espacio de color
  del perfil de trabajo. Además también verás cambios en la cantidad de
  píxeles mostrados como «recortados»
- ![<File:gamut-warning.png>](gamut-warning.png "File:gamut-warning.png")
  Colores fuera de Rango (*out-of-gamut*): botón ligado a los perfiles
  *de impresión*, *de salida* y *de pantalla*
- ![<File:gamut-softproof.png>](gamut-softproof.png "File:gamut-softproof.png")
  Prueba de impresión (*soft-proofing*): botón ligado a los perfiles *de
  impresión* y *de pantalla*

Estos dos últimos botones pueden actuar solos o en conjunto, según estas
combinaciones:

- ![<File:gamut-softproof.png>](gamut-softproof.png "File:gamut-softproof.png")
  <big>**+**</big>
  ![<File:gamut-warning-off.png>](gamut-warning-off.png "File:gamut-warning-off.png")
  <big>**+**</big> hemos establecido un perfil de impresora: simula los
  colores que se imprimirán (dentro de los límites de los colores que la
  propia pantalla es capaz de mostrar)
- ![<File:gamut-softproof.png>](gamut-softproof.png "File:gamut-softproof.png")
  <big>**+**</big>
  ![<File:gamut-warning-off.png>](gamut-warning-off.png "File:gamut-warning-off.png")
  **<big>+</big> no hay** perfil de impresora: en la previsualización
  verás los colores que tendrá la imagen al exportarla, pero siempre
  dentro de lo que la propia pantalla es capaz de mostrar (si exportas
  con un perfil de salida «más grande» que el perfil de la pantalla,
  nunca verás correctamente los colores más saturados)
- ![<File:gamut-softproof.png>](gamut-softproof.png "File:gamut-softproof.png")
  <big>**+**</big>
  ![<File:gamut-warning.png>](gamut-warning.png "File:gamut-warning.png")
  <big>**+**</big> has establecido un perfil de impresora: tonos fuera
  de rango de lo que puede imprimir la impresora
- ![<File:gamut-softproof.png>](gamut-softproof.png "File:gamut-softproof.png")
  <big>**+**</big>
  ![<File:gamut-warning.png>](gamut-warning.png "File:gamut-warning.png")
  **<big>+</big> no hay** perfil de impresora: tonos fuera del rango
  delimitado por el perfil de salida
- ![<File:gamut-softproof-off.png>](gamut-softproof-off.png "File:gamut-softproof-off.png")
  <big>**+**</big>
  ![<File:gamut-warning.png>](gamut-warning.png "File:gamut-warning.png")
  : tonos fuera de rango de lo que puede mostrar la pantalla con su
  perfil

Todas estas combinaciones son útiles para comparar el rango de colores
de la fotografía que ves en la previsualización del programa y lo que
obtendrás en pantalla o en la impresora al exportar la imagen. En
especial es útil ver que zonas de la foto tienen tonos tan saturados que
serán recortados al exportarla.

### Fuera de rango (*«out of gamut»*), Recorte (*«clipping»*) y Conversiones del rango de colores (*«rendering intents»*)

Hasta ahora has pasado de un rango de tonos a otro con exactitud gracias
a los perfiles de color. Pero, ¿qué pasa si los colores existentes en un
rango no se pueden convertir porque no caben en el rango de destino? En
este caso tendrás que decidir si pierdes esos colores o los comprimes
para que quepan.

#### Colores Fuera de Rango

![](sRGBvsRec2020_OOGpixel.jpg "sRGBvsRec2020_OOGpixel.jpg")Debido a la
capacidad del sensor o también durante el revelado de la foto, es
posible que algunos colores no existan en el espacio de color
seleccionado. A estos colores se les llama ***colores fuera del rango de
tonos*** (del inglés: *out of gamut colors*). Es posible que la misma
foto tenga colores fuera de rango en un espacio de color y no tenga
ninguno en otro espacio de color.

En general, aunque la mayoría de los colores capturados en las
fotografías tienen una fuerte tendencia a caer dentro del espacio de
color sRGB, con una baja cantidad de colores fuera de él, no es extraño
que mientras proceses una imagen los cálculos internos envíen los
colores de los píxeles más saturados bastante más allá del rango de
colores de sRGB. Así que es recomendable usar un perfil de trabajo más
grande que el perfil de salida. Por ejemplo: Rec2020.

El objetivo es que por extremos que sean los procesados todos los
colores de la imagen final sigan dentro de los límites del espacio de
color elegido: mientras trabajes con una imagen, los matices alrededor
de los límites de un espacio de color pequeño se moverán dentro y fuera
de sus límites, así que la idea es que con un espacio de color más
grande será más difícil que tengas colores *fuera de rango*.

Esto es especialmente importante cuando envías imágenes para imprimir,
ya que con buenas impresoras no es raro que su rango de colores exceda
incluso el rango de AdobeRGB (al menos en algunos colores).

#### Recorte de tonos

**El *recorte de tonos* es el mecanismo para ajustar aquellos valores de
píxel que exceden los límites establecidos.**

![](clippingRT.jpg "clippingRT.jpg") El método más crudo de recorte es
simplemente ignorar cualquier valor por encima del máximo. Y aunque en
esencia esto es lo que ocurre en todo tipo de algoritmos de recorte,
RawTherapee tiene un sistema más sofisticado que evita aberraciones o
[artefactos](https://es.wikipedia.org/wiki/Artefacto_(error_de_observación)):
cuando un canal de color (R, G o B) sobrepasa el valor máximo permitido
se realiza una reducción ponderada en todos los canales, de manera que
el tono del píxel no cambia, aunque al final no resulte tan brillante
como cabría esperar por el procesado realizado. Es decir, una vez que un
canal llega al límite ya no se incrementan más los valores de ningún
canal, aunque los otros aún no hayan llegado al máximo valor.

El problema de cualquier recorte está en que una operación posterior al
mismo puede llevar el valor de un canal recortado por debajo del máximo,
lo cual implicaría que al final habría pérdida o modificación de
detalles:

- supongamos que tienes el **color inicial (1146,180,60)** en un rango
  que no permite valores superiores a *255*: según el método de recorte
  de RawTherapee **el color recortado es (255,40,13)** (tal como puedes
  ver en el ejemplo anterior).
- si en un procesado posterior rebajas el canal rojo desde **1146**
  hasta **220**, si no hubiera habido recorte el color sería el
  **(220,35,12)**
  <img src="/images/220-35-12.jpg" title="220-35-12.jpg" width="20"
  alt="220-35-12.jpg" />
- sin embargo al recortar los colores según el método de RawTherapee, el
  color resultante es el **(49,8,2)**
  <img src="/images/49-8-2.jpg" title="49-8-2.jpg" width="20" alt="49-8-2.jpg" />
  (el mismo tono, pero bastante más oscuro de lo esperado)

Como se puede entender, los ejemplos anteriores son el resultado de
procesados bastante radicales, pero en un procesado más *«normal»* el
cambio en los colores recortados sigue produciéndose (normalmente hacia
tonos más oscuros).

Aparte de este recorte matemático, en RawTherapee existe otra operación
que consiste en eliminar los datos cuyo valor sea **mayor a 65365**, no
teniendo este límite nada que ver con ningún espacio de color, sino con
determinadas herramientas que necesitan saber qué valores máximo y
mínimo ofrecerán tras sus operaciones. Se trata del **«Recorte de
colores fuera de gama»**, localizado en la herramienta ***Exposición***.

En realidad debería llamarse algo así como ***«Recorte de valores
superiores a 65365 en todas las herramientas que usen curvas»**'' y**no
tiene nada que ver con los*colores fuera de rango**'', sino con la
programación de los algoritmos para las curvas, que artificialmente
tienen un límite de 65535. Estamos hablando de herramientas como la
Curva de tonos, CIECAM02, Difuminado, Negativo de película y la mayoría
de módulos que trabajan con L\*a\*b\*, entre otros.

Dado lo extenso del problema dentro del programa y mientras los
programadores lo solucionan, **lo más recomendable es dejar activado el
*«Recorte de colores fuera de gama»* y al mismo tiempo seleccionar un
perfil de trabajo grande** (al menos Rec2020, aunque ProPhoto, el perfil
por defecto, puede ser aún mejor).

Sin embargo los perfiles muy grandes engloban *colores imposibles*
(*«colores»* que no podemos ver) y en ciertos casos y con procesados
extremos pueden generarse artefactos o resultados inesperados. A pesar
de éllo, los perfiles con rangos de color amplios son la mejor opción.
**No es recomendable emplear sRGB o AdobeRGB como perfiles de trabajo**.

#### Los Tipos de Conversión del rango de colores

![](rendering_conversion.jpg "rendering_conversion.jpg")Además de poder
generar *colores fuera de rango* a lo largo del revelado, si tu perfil
de trabajo tiene un rango de colores bastante amplio (lo cual es muy
aconsejable), a la hora de exportar la imagen con un perfil con un rango
más pequeño, inevitablemente habrán colores que quedarán fuera del rango
de destino.

Puesto que la intención de todo fotógrafo es conseguir una imagen
determinada, perder colores a la hora de exportar no es una buena
opción. Por ello existe un sistema que intenta acoplar los colores de la
imagen revelada dentro del rango de colores de la imagen exportada: la
***conversión del rango de colores***.

Básicamente se trata de 4 métodos que pretenden satisfacer la intención
del fotógrafo a la hora de generar la imagen final: hay dos de tipo
*colorimétrico* (que son lo más fieles posible a los colores originales)
y otros dos de tipo *perceptual* (que intentan amoldarse a como
percibimos los colores):

- conversión ***colorimétrica absoluta***: reproduce los colores en base
  al *punto blanco* del espacio de color inicial y simplemente recorta
  los tonos que exceden (que están fuera de rango) el espacio de color
  de destino. Se utiliza casi en exclusiva para hacer pruebas de
  impresión, o para conseguir que dos impresoras distintas impriman los
  colores con el mismo tono
- conversión ***colorimétrica relativa***: en este caso los colores
  fuera de rango también se recortan, pero ajustándolos al *punto
  blanco* del espacio de color de destino. Además procura que la imagen
  pierda el mínimo posible de saturación de colores. Por todo ello no
  suele ser una buena opción para imprimir, especialmente cuando la
  diferencia de tamaño entre los espacios de color es importante
- conversión ***perceptual***: los colores se comprimen en conjunto para
  que todos quepan en el espacio de color de destino, pero además
  manteniendo las distancias relativas entre ellos, es decir que los
  degradados se perciben con la misma suavidad y contraste que
  originalmente, aunque bastante más desaturados. Sin embargo puede ser
  la mejor opción a la hora de imprimir una imagen
- conversión ***de saturación***: es parecido a la conversión
  *perceptual* pero sin perder tanta saturación, a costa de no respetar
  la fidelidad a los colores originales. Sólo se considera recomendable
  para gráficos donde la fidelidad de los colores no es importante

En general la mejor opción suele ser la *conversión colorimétrica
relativa*, ya que nuestros ojos no son tan sensibles a las diferencias
entre colores muy saturados como a las diferencias entre tonos pastel.
Además, al respetar los tonos pastel lo máximo posible, el resultado
final será muy parecido a la previsualización de RawTherapee (excepto en
los tonos más saturados o fuera de rango).

Sin embargo si vas a imprimir las fotos, dependerá bastante de la
impresora y del papel que utilices, ya que por ejemplo con un papel mate
(que tiende a desaturar los colores) la conversión perceptual quizá sea
demasiado desaturada y debas optar por la colorimétrica relativa.

### ¿Cómo configurar RawTherapee para usar perfiles personalizados?

Cuando quieras configurar los perfiles básicos, o necesites usar algún
tipo de perfil distinto a los que vienen con RawTherapee, tendrás que
indicarle al programa cómo encontrarlos. Esto se consigue en la
configuración del programa, aunque no siempre se puede hacer desde la
interfaz gráfica, como puedes leer a continuación.

#### La carpeta de perfiles

Dentro de la configuración del programa, en
`Gestión del color > Carpeta con perfiles de color ICC`, le indicarás al
programa en qué carpeta de tu sistema están guardados los perfiles ICC
que quieres usar y no vienen incluídos en RawTherapee.

Es muy conveniente que esta carpeta esté dentro de la ruta de tus
carpetas de usuario: `Users > TuNombreDeUsuario` tanto en macOS como en
Windows. Esto te evitará una buena cantidad de problemas con los
permisos de acceso a los perfiles (si no tienes los permisos adecuados,
no podrás ver tus perfiles).

#### El perfil del monitor

Una vez has establecido qué carpeta contendrá tus perfiles personales y
puesto que ya estás en el lugar apropiado, el siguiente paso es decirle
a RawTherapee qué perfil necesita tu pantalla para que muestre los
colores correctamente. Lo harás en
`Gestión del color > Monitor > Perfil de color predeterminado`.

También puedes optar por usar el perfil de color que usa el sistema
operativo (que en principio debería ser el adecuado para el monitor) y
seleccionar uno u otro método dependerá de varios factores, así que
tendrás que probar si ves alguna diferencia entre éllos. Pero ante la
duda, selecciona directamente el fichero ICC de tu perfil.

En cualquier caso dado, lo importante que es un buen perfil de pantalla
es más que conveniente que generes un [perfil
personalizado](https://www.diversidadyunpocodetodo.com/displaycal-calibracion-y-perfilado-pantalla/#3_Calibrar_o_Ajustar_un_monitor_Calibracion_y_Perfilado),
pero teniendo en cuenta [el problema existente con los
navegadores](#los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md).

Además, si tu sistema operativo es macOS, es imprescindible que leas la
[nota para la configuración de la pantalla en
macOS](Preferences/es#Pantalla.md).

#### El perfil de la impresora

En la misma pestaña de las opciones también podrás especificar qué
perfil usarás para imprimir las fotos:
`Gestión del color > Impresora (prueba de color) > Perfil de color`.

Si bien RawTherapee no puede imprimir directamente tus fotos, sí que [te
mostrará qué colores se imprimirán
correctamente](#los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md)
seleccionando los botones adecuados de la interfaz.

#### Añadir un perfil de trabajo personalizado

El programa te permite especificar perfiles de trabajo personalizados
mediante un archivo de texto con formato
[JSON](https://es.wikipedia.org/wiki/JSON). El archivo debe llamarse
`workingspaces.json` y puede estar ubicado en:

- la carpeta de perfiles ICC, establecida en
  [`Preferencias > Gestión de color > Carpeta con perfiles de color ICC`](preferences/es#color_management_tab)
- la carpeta de perfiles de color del propio RawTherapee:
  - en Windows: `CarpetaDeInstalaciónDeRawTherapee\iccprofiles`
  - en Linux:
    - si lo has instalado usando tu gestor de paquetes, o lo has
      compilado tú mismo con `BUILD_BUNDLE=OFF`:
      `/usr/share/rawtherapee/iccprofiles`
    - si lo has compilado tú mismo con `BUILD_BUNDLE=ON`:
      `CarpetaDeInstalaciónDeRawTherapee/iccprofiles`
  - en macOS:
    `/Applications/RawTherapee.app/Contents/Resources/iccprofiles`

Es posible que dentro de estas carpetas encuentres otras dos: `input` y
`output`, que albergan los perfiles de entrada y salida respectivamente.

En cuanto al contenido del archivo `workingspaces.json`, podrás
indicarle al programa el perfil ICC adecuado, o directamente los valores
de los colores primarios de ese perfil (al fin y al cabo RawTherapee
sólo leerá esos valores del archivo ICC).

Si le indicas el nombre del archivo el texto queda así:

    {"working_spaces": [
        {
            "name" : "MyProPhotoRetocado",
            "file" : "/ruta/hasta/mis/perfiles/ProPhotoRet.icc"
        }
    ]}

En cambio con la matriz de colores primarios (los valores RGB de cada
color primario):

    {"working_spaces": [
        {
            "name" : "MyProPhotoRetocado",
            "matrix" : [0.79771, 0.28806, 0.00000, 0.13516, 0.71187, 0.00002, 0.03133, 0.00008, 0.82489]
        }
    ]}

Si el campo *matrix* está presente, el campo *file* se ignora. Si sólo
está presente *file*, la matriz de colores primarios se extrae del
perfil ICC.

Si indicas los valores de los colores primarios, ten en cuenta que
deberán estar adaptados al punto blanco D50. Si no sabes cómo hacerlo o
no quieres complicarte demasiado, simplemente utiliza el fichero ICC.

Por último, no olvides ni por un momento que el perfil de trabajo define
el espacio de color empleado por el motor del programa: todas las
operaciones se realizarán en ese espacio de color, así que debes
asegurarte que el perfil es apropiado para usarlo como espacio de
trabajo.

### ¿Cómo configurar la gestión de color en cada imagen?

Para un procesado correcto de tus imágenes, además de haber configurado
correctamente las opciones de la gestión del color en las Preferencias,
en cada foto deberás elegir una serie de perfiles que te permitirán
conseguir unos colores fidedignos.

#### El perfil de entrada

Un archivo raw contiene un volcado de los valores de luz [captados y
cuantificados](demosaicing/es#introducción.md) por el sensor y
su electrónica.

El papel del perfil de entrada es convertir estos valores en nuevos
valores de un espacio de color conocido
[CIELab](https://es.wikipedia.org/wiki/Espacio_de_color_CIE_1931) o
[CIEXYZ](https://es.wikipedia.org/wiki/Espacio_de_color_CIE_1931). para
asegurar que todos los colores de la escena capturada se reproducen
fielmente en cualquier medio.

A la hora de elegir el perfil adecuado tienes varias opciones, desde no
usar ninguno hasta seleccionar uno que hayas creado tú mismo.

Ahora podrás leer la información más relevante sobre su uso en
RawTherapee, pero tienes más información en el capítulo sobre [sus
particularidades](#particularidades_del_perfil_de_entrada.md),
más abajo.

##### Sin perfil de color

Con esta elección no se aplicará ningún perfil de color de entrada: los
archivos raw mostrarán el color RGB nativo de la cámara y sólo se
realizará el desentramado y la corrección del balance de blancos.

Por otro lado a los archivos no-raw tampoco se les aplicará ningún
perfil de entrada (y tampoco su corrección gamma), por lo que tendrán
una apariencia brillante.

**No es una opción recomendada y sólo sirve para casos muy
específicos.**

##### Cámara estándar

Con esta opción el programa busca el perfil automáticamente en varios
lugares, para elegir el que cree más apropiado:

- en el código interno de RawTherapee
- en el propio archivo raw
- en un archivo instalado junto con RawTherapee, llamado `camconst.json`

En el caso de encontrar varios perfiles válidos, en general se priorizan
los valores del fichero `camconst.json`, salvo en algunos archivos raw
en formato DNG en los que se toman los datos necesarios de la propia
imagen raw.

Para las fotos que no requieren de la máxima precisión de color (como la
fotografía de paisaje) este perfil será suficiente y en general
correcto. Además, si vas a exportar imágenes para procesarlas en una
aplicación de alto rango dinámico, u otra aplicación que necesite una
respuesta de color lineal y predecible, necesitarás usar este perfil o
un perfil ICC a medida.

##### Perfil para la cámara (seleccionado automáticamente)

Aquí RawTherapee también busca automáticamente el mejor perfil, a partir
de la marca y modelo de cámara obtenidos de los metadatos de la foto.

A *grosso modo* la idea es similar a la anterior opción, excepto que
ahora se seleccionará un perfil de entrada **DCP** o **ICC**, que pueden
proporcionar colores más precisos que el perfil de cámara estándar.

Si existieran perfiles DCP e ICC, el programa preferirá los perfiles
DCP. Si por el contrario no existiera ningún archivo de perfil DCPo ICC,
RawTherapee desactivará esta opción y seleccionará el perfil de cámara
estándar.

##### A medida

Aquí puedes especificar un perfil de entrada a medida, que será siempre
un fichero ICC o DCP y que idealmente habrás creado tú mismo para tu
cámara concreta (no un fichero genérico para el modelo de tu cámara). El
fichero deberá estar situado en la [carpeta de
perfiles](#la_carpeta_de_perfiles.md) especificada en las
Preferencias.

En general los perfiles ICC correctamente creados servirán perfectamente
para todas tus fotografías, siempre que la iluminación de las escenas
sea luz natural cercana al mediodía, o similar. Esto se debe a ciertas
limitaciones de diseño de la especificación ICC.

En los casos en que las escenas tengan iluminación mixta, o muy distinta
a la luz natural del mediodía (interiores, amaneceres, atardeceres,
fotografía nocturna, ...), la mejor opción sería un buen perfil DCP,
puesto que técnicamente está más capacitado para corregir la temperatura
de color de la iluminación.

En cualquier caso, si los perfiles son de alta calidad, elegir uno u
otro no debería suponer una diferencia visual apreciable.

En el caso de elegir un perfil **DCP**, tendrás la oportunidad de
activar o desactivar estas opciones:

- **Iluminante**: los mejores perfiles contienen datos acerca de la luz
  diurna (normalmente del [iluminante
  D65](http://www.glosariografico.com/iluminante_estandar_d65)) y de la
  luz incandescente (normalmente del [iluminante
  A](http://www.glosariografico.com/iluminante_estandar)), aunque
  algunos perfiles tendrán sólo datos de luz diurna. Si el perfil que
  seleccionas tiene ambos iluminantes podrás escoger cuál de los dos
  usar, o podrás dejar al programa que interpole los datos en base a la
  temperatura de color seleccionada en el balance de blancos.
- **Curva de tono**: algunos perfiles DCP contienen una curva de tono
  que habitualmente intenta imitar el aspecto de las imágenes JPEG
  generadas por la cámara. Así que si quieres ver exactamente cuál es la
  apariencia de color prevista por el diseñador del perfil, deberás
  activar la opción. Esta casilla estará desactivada para perfiles que
  no contegan una curva de tono.

Si el perfil DCP tiene una etiqueta de *copyright* con el valor **Adobe
Systems**, independientemente de si contiene una curva de tono o no,
RawTherapee creará automáticamente una curva de tono con una forma
idéntica a la de la curva de Adobe Camera Raw. De este modo el uso del
perfil DCP en RawTherapee dará los mismos resultados que el uso de ese
perfil DCP en Lightroom. Por eso la casilla de verificación *Curva de
tono* no se desactivará cuando uses un perfil DCP sin una curva
incorporada, siempre y cuando la etiqueta de *copyright* tenga el valor
descrito.

- **Tabla base**: esta opción añade correcciones que mejoran el
  resultado que obtendrías con el perfil de cámara estándar. Si la
  desactivas, básicamente es como si usaras el perfil de cámara
  estándar.
- **Tabla de búsqueda**: mediante esta tabla se le añade a la imagen un
  aspecto concreto distinto a la escena original (más saturado,
  envejecido,
  [posterizado](https://es.wikipedia.org/wiki/Posterización), ...).
- **Exposición de partida**: esta opción modifica el valor de exposición
  de la imagen raw, de forma que en la previsualización veas una imagen
  igual de brillante que la imagen JPEG realizada por la cámara. Esta
  modificación del valor de exposición se realiza *entre bastidores*,
  sin que se vea la modificación en el deslizador de Exposición.

##### Guardar imagen de referencia

Pulsando este botón RawTherapee guarda una imagen TIFF con gamma lineal,
sin aplicarle ni el perfil de entrada ni el perfil de salida.

Este archivo puede usarse para crear un perfil de entrada **a medida**
ajustado a tu cámara (tal como se explica en [*Cómo crear perfiles
ICC*](How_to_create_ICC_profiles/es.md)). Para éllo puedes
utilizar el programa **ArgyllCMS** para crear perfiles ICC, o el
programa **DCamProf** para crear perfiles tanto ICC como DCP.

Las transformaciones de recorte, cambio de tamaño y rotación sí se
aplicarán a la imagen resultante lo que permite que ésta sea más
manejable por el software que la reciba. Por ejemplo, ArgyllCMS es muy
quisquilloso y exige que en la imagen sólo sea visible la carta de
color.

Si lo deseas también puedes elegir exportar con el balance de blancos
aplicado o sin él. En el caso de perfiles ICC, deberías exportar con el
balance de blancos aplicado, pero si tienes previsto generar un perfil
DNG o una matriz de color al estilo de **dcraw**, debes exportar *sin
aplicar el balance de blancos*.

#### El perfil de trabajo

El perfil de trabajo especifica el espacio de color con el que el motor
del programa realizará los cálculos internos. Por defecto es ProPhoto,
que en general es un buen perfil para todo tipo de fotografías.

Pero ten en cuenta que el perfil de trabajo solamente especificará los
colores primarios del espacio de color: el valor gamma no cambiará, ya
que el circuito de revelado de RawTherapee calcula en coma flotante sin
codificación gamma (o sea gamma = 1.0).

A continuación se muestran los rangos de colores (delimitados por
triángulos de color gris) de todos los perfiles de trabajo que puedes
elegir por defecto en RawTherapee. La representación se basa en el
espacio de color CIELuv, que es más acorde a lo que nuestros ojos
captan:

<div>

- <figure>
  <img src="/images/acesap0_gamut.jpg" title="acesap0_gamut.jpg" />
  <figcaption>acesap0_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/acesap1_gamut.jpg" title="acesap1_gamut.jpg" />
  <figcaption>acesap1_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/best_gamut.jpg" title="best_gamut.jpg" />
  <figcaption>best_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/beta_gamut.jpg" title="beta_gamut.jpg" />
  <figcaption>beta_gamut.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/bruce_gamut.jpg" title="bruce_gamut.jpg" />
  <figcaption>bruce_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/large_gamut.jpg" title="large_gamut.jpg" />
  <figcaption>large_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/medium_gamut.jpg" title="medium_gamut.jpg" />
  <figcaption>medium_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/rec2020_gamut.jpg" title="rec2020_gamut.jpg" />
  <figcaption>rec2020_gamut.jpg</figcaption>
  </figure>

</div>
<div>

- <figure>
  <img src="/images/srgb_gamut.jpg" title="srgb_gamut.jpg" />
  <figcaption>srgb_gamut.jpg</figcaption>
  </figure>

- <figure>
  <img src="/images/wide_gamut.jpg" title="wide_gamut.jpg" />
  <figcaption>wide_gamut.jpg</figcaption>
  </figure>

</div>

Y ahora una imagen con la comparación de varios de los rangos de colores
más grandes:

<figure>
<img src="/images/big_gamuts_comparison.jpg"
title="big_gamuts_comparison.jpg" />
<figcaption>big_gamuts_comparison.jpg</figcaption>
</figure>

#### El perfil de salida

Aquí especificas el perfil de color de salida, es decir, el que se
incorporará a la hora de exportar la imagen: la foto guardada será
convertida a este espacio de color y el perfil de salida se integrará en
los metadatos.

El aspecto visual que le da el perfil de salida a la imagen exportada no
siempre puede verse en la vista previa: puedes apreciar los tonos fuera
de rango con los botones *Colores fuera de rango* y *Prueba de
impresión*, pero nunca verás cómo es la imagen si la codificas con un
perfil de rango amplio como Rec2020 (al menos no hasta que existan
monitores con tal capacidad de representación de colores).

RawTherapee incorpora de serie varios perfiles de salida hechos a
medida, en las versiones 2 y 4 del estándar ICC: RawTherapee está mejor
preparado para mostrar perfiles ***v2*** en pantalla, mientras que los
***v4*** aún siendo técnicamente superiores, sólo son capaces de leerlos
las aplicaciones modernas programadas para éllo. Si tienes dudas, usa
los *v2*, pero si vas a enviar tus fotos a un laboratorio de impresión o
vas a crear imágenes de alto rango dinámico (HDR), usa los *v4*.

Los perfiles de salida son los mismos que los perfiles de trabajo:
RT_ACES-AP0, RT_ACES-AP1, RT_Best, RT_Beta, RT_Bruce, RT_Large,
RT_Medium, RT_Rec2020, RT_sRGB y RT_Wide. La diferencia aquí es que se
tienen en cuenta todas las características del perfil (como su gamma) y
no sólo los colores primarios.

De todas formas, aunque los perfiles que vienen con el programa son de
buena calidad, debes tener en cuenta un detalle muy importante: **todos
éllos están codificados con una gamma similar a la de sRGB**. Es decir,
excepto el propio perfil sRGB, los demás **no respetan los estándares
oficiales**.

La codificación gamma hoy en día sólo se emplea para optimizar el uso de
los bits de información disponibles en imágenes de 8-bits, o también
para optimizar el ancho de banda empleado a la hora de transmitir
imágenes. En este sentido la codificación gamma empleada en el perfil de
salida no es demasiado importante, siempre que el aparato o programa que
decodifique la imagen aplique una buena gestión del color (o sea, que
convierta correctamente los colores de la imagen codificada a su propio
espacio de color).

El problema con la codificación gamma incorrecta llega si la imagen es
procesada directamente sin ninguna gestión del color, o con una gestión
incorrecta. Por ello es conveniente (aunque no imprescindible) descargar
[estos perfiles creados por Elle
Stone](https://github.com/ellelstone/elles_icc_profiles/archive/master.zip),
descomprimir el archivo en [tu carpeta de
perfiles](#la_carpeta_de_perfiles.md) y seleccionar los
adecuados en RawTherapee:

- los perfiles acabados en **g10** tienen una gamma lineal:
  **gamma=1.0**
- los perfiles acabados en **g18** tienen una gamma equivalente al
  estándar de ProPhoto: **gamma=1.8**
- los perfiles acabados en **g22** tienen una gamma equivalente al
  estándar de AdobeRGB: **gamma=2.2**
- los perfiles acabados en **srgbtrc** tienen una curva de gamma
  equivalente al muy especial estándar de sRGB
- los perfiles acabados en **rec709** tienen una gamma equivalente al
  estándar de video FullHD
- los perfiles acabados en **labl** tienen una gamma perceptualmente
  uniforme, basada en el espacio de color L\*a\*b\*

El perfil de salida recomendado si guardas tus imágenes en un formato de
8 bits y deseas publicarlas en la web es **RT_sRGB**.

Si no seleccionas ningún perfil, la imagen se codificará en **sRGB**,
pero no se incorporará el perfil en los metadatos. En general el resto
de programas interpretarán esta carencia de perfil como *sRGB*, pero es
más seguro incluir el perfil *RT_sRGB* en la imagen para garantizar en
lo posible que se muestre correctamente en cualquier aplicación.

Los perfiles con rangos de colores más grandes, como **RT_Large**,
generalmente se usan cuando exportas tu imagen con una profundidad de 16
bits o mayor, para continuar editándola en otra aplicación.

Si vas a enviar tu imagen a imprimir también es recomendable un perfil
de salida de rango amplio, ya que muchas impresoras tienen rangos de
color que exceden en ciertos colores incluso a AdobeRGB (**RT_Medium**).

## Más detalles

### Perfiles, Conversiones y el Error de cuantificación

![](quantification.png "quantification.png")Mientras trabajas con tus
fotos, lo ideal sería que usaras un perfil de trabajo (un [espacio de
color](#Los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink"))
que fuera mucho más grande que el [rango de
colores](#Los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")
de cualquier sensor pantalla o tipo de impresora. Incluso uno que
englobara toda la gama de colores que tus ojos pueden ver (el espacio de
color **ACESp0**).

Pero entonces te enfrentarías a la conversión entre perfiles y la
fidelidad de los colores después de cada transformación: hay un problema
llamado **error de cuantificación**, que en términos generales significa
que al convertir un valor de una escala (por ejemplo de 0 a 100) a otro
valor con una escala distinta (por ejemplo de 0 a 65535), el valor
resultante no es equivalente al valor inicial.

El origen del problema viene de codificar los colores primarios dentro
de los perfiles mediante [valores
hexadecimales](https://es.wikipedia.org/wiki/Sistema_hexadecimal): al
transformar los valores de los colores primarios de valores
hexadecimales a valores decimales (y viceversa) existen ligeros
desajustes y al final los tonos varían ligeramente. Y este cambio puede
llegar a ser visible a tus ojos.

Sin embargo la tendencia general es aceptar que en los programas que
trabajan internamente con números de [32 bits en coma
flotante](the_floating_point_engine/es.md) (como RawTherapee),
estos cambios son inapreciables para el ojo humano así que no debes
preocuparte por este problema al elegir un perfil de trabajo.

### Perfiles de color ICC vs DCP

Un perfil de color **ICC** define cómo convertir el color de una imagen
a colores estándar de referencia y viceversa. Para ello normalmente
utiliza como referencia la luz blanca del mediodía (denominada
*iluminante estándar D50*) y aplica fórmulas matemáticas para modificar
el aspecto de los colores según sea la temperatura de color de la luz
ambiente en la fotografía (la temperatura de color del *Balance de
blancos*). También puedes encontrar perfiles ICC con un iluminante
estándar distinto (*iluminante D65*, *iluminante A*, ...).

Por otro lado, un perfil de color **DCP** viene a hacer lo mismo, pero
de distinta forma: para empezar, un buen perfil DCP tendrá definidos
*dos iluminantes distintos* (normalmente *D65* y *A*), utilizará un
[espacio de
color](#los_espacios_de_color_y_los_rangos_de_colores_(gamuts) "wikilink")
muy conocido y empleado (ProPhoto) y podrá contener un mecanismo para
darle automáticamente a las fotografías unas tonalidades determinadas.

Así pues, si hacen lo mismo, ¿cuál elegir?

Esto va a depender mucho del tipo de fotografías que vayas a revelar:

- si son paisajes o fotografías realizadas a la luz natural del
  mediodía, entonces un buen perfil ICC es una muy buena opción, pues la
  iluminación ambiente coincide con el iluminante de referencia
- si vas a revelar fotos con todo tipo de condiciones de iluminación
  interiores (atardecer, mediodía, mixta, ...), un buen perfil DCP será
  tu mejor opción, puesto que al tener dos iluminantes de referencia se
  pueden realizar interpolaciones para reproducir los colores lo más
  correctamente posible
- además, en el estándar de los perfiles ICC no se especifica en qué
  punto del revelado se debe aplicar la corrección de color, así que
  estás a expensas de que los programadores sepan exactamente dónde
  situar la conversión de color. Sin embargo en el estándar de los
  perfiles DCP sí se indica cómo y cuándo aplicar la conversión del
  color

En RawTherapee un buen perfil ICC correctamente empleado y un buen
perfil DCP dan prácticamente los mismos resultados. Por lo que, si no
dispones de un perfil ICC, puedes confiar en los perfiles DCP incluídos
en el programa.

Por el contrario, si estás buscando la más absoluta perfección en la
reproducción del color (por ejemplo para catalogar o duplicar obras de
arte), necesitarás un proceso bastante exigente y complejo que queda
fuera del alcance de este documento.

### Particularidades del perfil de entrada

A continuación tienes una lista de algunos aspectos particulares de
determinadas opciones en el perfil de entrada:

1.  cuando selecciones la opción ***Sin perfil de color*** no se
    aplicará ningún perfil de color de entrada, por lo que:
    - los archivos *raw* mostrarán el color RGB nativo de la cámara.
      Solamente se realizará el desentramado y se corregirá el balance
      de blancos
    - los archivos *no-raw* se mostrarán sin aplicar a la visualización
      ningún perfil de entrada que puedan tener embebido y tampoco se
      aplicará ninguna corrección gamma, lo que significa que
      habitualmente tendrán una apariencia brillante
2.  al seleccionar ***Cámara estándar*** RawTherapee busca la matriz de
    color apropiada para la cámara:
    - una matriz de color es una matriz de 3x3 valores constantes, que
      se multiplican por los valores de los colores RGB nativos de la
      cámara para convertirlos en colores lo más fieles posible a la
      escena original. Por ejemplo: quizá el fotodiodo rojo del sensor
      no capta un rojo totalmente equivalente a la realidad, así que
      esta matriz se encargará de corregir esta desviación para que los
      resultados sean fieles a la escena
    - una matriz de color funciona óptimamente (es decir, proporciona
      los colores más precisos posibles) cuando el balance de blancos
      está cercano a aquel para el que se calibró la matriz. En el caso
      de la matriz *cámara estándar* la calibración se realizó para el
      *iluminante D65*, o sea para una *temperatura de color* de 6500ºK
      (no te preocupes si el balance de blancos está un poco apartado de
      ese valor, ya que de todos modos los colores serán razonablemente
      precisos)
    - cuando el archivo raw está en formato DNG y la etiqueta *Exif*
      `Software (0x0131)` **no empieza** con la cadena de caracteres
      `Adobe DNG Converter` y el archivo **contiene** una etiqueta
      `ColorMatrix2`, entonces se prioriza el valor de esta etiqueta
      sobre el resto de opciones (`camconst.json` y el código interno de
      RawTherapee)
3.  con el ***Perfil para la cámara seleccionado automáticamente***, el
    perfil funciona en el rango normal de valores desde el negro hasta
    el recorte del blanco, pero si activas la reconstrucción de las
    luces se añadirán nuevos datos por encima del nivel de recorte. Si
    posteriormente llevas esos nuevos datos al espacio visible (por
    ejemplo con una exposición negativa), ese rango no quedará cubierto
    de manera natural por el perfil. Sin embargo, RawTherapee extenderá
    linealmente el perfil para cubrir también esos valores, dándoles la
    misma corrección que los colores más brillantes contenidos en el
    rango normal y que tengan el mismo tono y saturación
4.  en la opción ***A medida**'', cuando hayas seleccionado un***perfil
    DCP**'':
    - ![](Screenshot_20180810_163036.png "Screenshot_20180810_163036.png")
      en la ***Curva de tono DCP*** el modo de curva utilizado es el
      mismo que el modo [Similar a
      película](Exposure/es#film-like.md) de la herramienta
      *Exposición*, lo que significa que puedes reproducir el efecto
      usando las curvas de esta herramienta.  
      Cuando se aplica contraste con una curva *Similar a película* la
      apariencia de los colores cambiará y la saturación global
      aumentará, excepto en los colores brillantes, cuya saturación
      disminuirá.  
      En algunos perfiles DCP incluídos en RawTherapee se emplea la
      misma curva que por defecto usa Adobe Camera Raw y ![la puedes
      descargar](dcp_tone_curve.rtc "la puedes descargar") para usarla
      en la herramienta *Curva de tonos*, dentro de *Exposición*.  
      Además, si el perfil DCP tiene una etiqueta de *copyright* con el
      valor `Adobe Systems`, e independientemente de si contiene una
      curva de tono o no, RawTherapee la creará automáticamente con una
      forma idéntica a la de la curva de Adobe Camera Raw. Esto se debe
      a que de este modo el uso del perfil DCP en RawTherapee dará los
      mismos resultados que el uso de ese perfil DCP en Lightroom. Por
      éso no se desactivará la casilla de verificación *Curva de tono*
      cuando uses un perfil DCP sin una curva incorporada, siempre y
      cuando la etiqueta de *copyright* tenga el valor descrito
    - la ***Tabla base DCP*** te permite activar la tabla de búsqueda
      del `HueSatMap`, que se utiliza para añadir correcciones no
      lineales superpuestas a la matriz básica. Este es un control para
      usuarios avanzados y a menos que quieras únicamente el resultado
      de la matriz básica pura, deberías dejarlo activado. La casilla
      aparece en gris si el perfil cargado no dispone de una tabla
      `HueSatMap`
    - la ***Tabla de búsqueda DCP*** te permite activar la tabla de
      búsqueda `LookTable`, que está destinada a añadir un aspecto
      subjetivo superpuesto, generalmente junto con una curva de tono
      incorporada en el perfil. Es decir, si desactivas la curva DCP y
      la *Tabla de búsqueda*, es posible que obtengas un perfil
      colorimétrico neutro, siempre que el perfil DCP se haya diseñado
      para ello, lo cual no siempre es el caso (si el perfil DCP tiene
      tanto la *Tabla de búsqueda* como la *Tabla base*, es probable que
      sí sea el caso; pero si sólo tiene una *Tabla de búsqueda*,
      probablemente no dará colores correctos si la desactivas).
      Desactivar elementos individuales de un perfil DCP se considera
      ajustes avanzados: normalmente dejarás estos elementos activados
    - el formato DCP tiene una etiqueta de *Reproducción del Negro*
      (`Black Render`, en inglés). Esta etiqueta indica si se debe
      realizar la substracción automática del negro, pero RawTherapee la
      ignora: puedes realizar la substracción del negro con la
      herramienta [***Raw \> Puntos
      Negros***](Raw_Black_Points/es.md), o con el deslizador
      [***Nivel de negro***](exposure/es#black) en la
      herramienta *Exposición*. Como muchos de los perfiles de Adobe
      indican la substracción automática del negro y Adobe Camera
      Raw/Lightroom la realizan, en esos casos RawTherapee presentará la
      imagen con algo menos de contraste y sombras más brillantes
5.  en la opción ***A medida**'' cuando hayas seleccionado un***perfil
    ICC**'':
    - los perfiles ICC más antiguos no es probable que funcionen bien en
      RawTherapee: lo normal es que la imagen aparezca extremadamente
      oscura con los perfiles ICC no soportados
    - algunos perfiles ICC aplican una curva de tono y reducen la
      saturación de las luces más brillantes, a fin de obtener un
      aspecto más parecido a la película. Estos perfiles posiblemente no
      funcionen bien junto con la [Recuperación de las
      luces](Exposure/es#highlight_reconstruction.md). Si
      observas un cambio radical de contraste al aplicar un perfil ICC,
      significa que este ha aplicado una curva de tono y por tanto no
      debes usarlo junto con la *Recuperación de las luces*
    - si usas los perfiles ICC de *Capture One*: RawTherapee aplica los
      perfiles ICC de entrada antes de los ajustes de exposición, ya que
      la intención es que sólo se usen para que los colores sean más
      precisos y no para obtener una apariencia determinada. Por el
      contrario, los perfiles ICC de Capture One contienen una
      apariencia subjetiva, lo que significa que usualmente contienen
      sesgos de matiz, por ejemplo para aumentar la saturación en las
      sombras. En ese caso, si tu imagen está subexpuesta y le aumentas
      la exposición algunos pasos, al haberse aplicado esos sesgos de
      matiz antes de afinar la exposición, provocarán que los colores
      sean erróneos después del ajuste. En otras palabras, no obtendrás
      la misma apariencia que en Capture One. En consecuencia, se
      recomienda ajustar correctamente la exposición en la cámara cuando
      vayas a revelar usando perfiles ICC de Capture One. También
      deberás aplicar una curva RGB [Similar a
      película](Exposure/es#film-like.md) apropiada, ya que
      estos perfiles se han diseñado para usarse junto con una curva de
      este tipo.

### Dónde conseguir perfiles de color

Si instalas las versiones de prueba de los programas *Capture One* o
*Adobe Camera Raw* (incluído en *Adobe Photoshop*), conseguirás una
extensa colección de perfiles para la mayoría de las cámaras del
mercado.

En <img src="/images/COne-logo.png" title="COne-logo.png" width="32"
alt="COne-logo.png" /> **Capture One** seguramente los podrás encontrar
dentro de:

- en <img src="/images/macOS-logo.png" title="macOS-logo.png" width="34"
  alt="macOS-logo.png" /> **macOS** pueden estar en dos lugares:
  - dentro de la carpeta
    `Users>TuNombreDeUsuario>Library>ColorSync>Profiles` (ten en cuenta
    que esta carpeta está oculta, así que, mientras estás en el
    *Finder*, deberás presionar la tecla y seleccionar la carpeta
    *Library*)
  - dentro de una carpeta contenida en el paquete del programa: ves a
    **Aplicaciones\>Capture One**, haz en el icono del programa y
    selecciona *Mostrar contenido del paquete*. Después dirígete a
    `Contents>Frameworks>AppCore.Framework>Versions>A>Resources>Profiles>Input`
- en <img src="/images/Windows-logo.png" title="Windows-logo.png" width="32"
  alt="Windows-logo.png" /> **Windows** los encontrarás en
  `Users\TuNombreDeUsuario\Appdata\CaptureOne\Color profiles`

En <img src="/images/ACR-logo.jpg" title="ACR-logo.jpg" width="32"
alt="ACR-logo.jpg" /> **Adobe Camera Raw**:

- en <img src="/images/macOS-logo.png" title="macOS-logo.png" width="34"
  alt="macOS-logo.png" /> **macOS**: dentro de la carpeta
  `Users>TuNombreDeUsuario>Application>Support>Adobe CameraRaw>CameraProfiles`
  (ten en cuenta que esta carpeta está oculta, así que, mientras estás
  en el *Finder*, deberás presionar la tecla y seleccionar la carpeta
  *Library*)
- en <img src="/images/Windows-logo.png" title="Windows-logo.png" width="32"
  alt="Windows-logo.png" /> **Windows** pueden estar en dos lugares:
  - dentro de la carpeta `C:\ProgramData\Adobe CameraRaw\CameraProfiles`
  - dentro de la carpeta
    `Users\TuNombreDeUsuario\Appdata\Roaming\Adobe CameraRaw\CameraProfiles`

Con <img src="/images/NX-D-logo.png" title="NX-D-logo.png" width="32"
alt="NX-D-logo.png" /> **Nikon Capture NX-D** también podrás obtener muy
buenos perfiles para cámaras Nikon, aunque la explicación de dónde
encontrarlos está en la página [Cómo conseguir perfiles ICM de
Nikon](How_to_get_nikon_icm_profiles/es.md).

E incluso [puedes crear tú mismo tus perfiles de color
ICC](How_to_create_ICC_color_profiles/es.md).

### Los espacios de color y los rangos de colores (*gamuts*)

![](luzvisible.jpg "luzvisible.jpg")La visión humana (lo que percibimos
intelectualmente) es una composición realizada por el cerebro, que
mezcla los estímulos que captan los ojos, las experiencias que hemos
tenido en el pasado y lo que esperamos recibir de esos estímulos (*lo
que queremos ver*). Se trata del resultado de un complejo sistema
psico-físico que nos ayuda a sobrevivir en el mundo que habitamos. En
concreto los colores no existen en el mundo real. Esto significa que lo
que llamamos «colores» son sólo la interpretación que realiza nuestro
cerebro de las [ondas
electromagnéticas](https://es.wikipedia.org/wiki/Espectro_electromagnético)
que alcanzan la retina.

Nuestra retina es capaz de captar y discernir ondas electromagnéticas
dentro del rango de longitudes de onda entre unos 380 nm y unos 780 nm
(o incluso entre unos 300 nm y unos 830 nm, no hay un límite claro).

Las estructuras que captan la luz son los conos (captan los colores o
tonos) y los bastones (captan la luminosidad de la escena o su
*«brillo»*) y parece ser que la comunicación con el cerebro se realiza
mediante 3 tipos de señales: una para la luminosidad y dos más que
definen diferencias de color. Estas parecen ser: por un lado una señal
*informa* de las diferencias entre el azul y el amarillo, mientras que
la otra señal *informa* de las diferencias entre el verde y rojo.

La [CIE (Comisión Internacional de la Iluminación)](http://cie.co.at)
estableció una equivalencia entre cómo los ojos (los conos) captan la
luz y una fórmula matemática: crearon las [funciones
triestímulo](http://redgeomatica.rediris.es/carto2/arbolB/cartoB/Bcap5/5_6_2.htm),
que definen las combinaciones de tres valores primarios para conseguir
todos los colores visibles. A partir de estas funciones se establecieron
los espacios de color
[CIEXYZ](http://recursos.cnice.mec.es/fp/artes/ut.php?familia_id=5&ciclo_id=1&modulo_id=6&unidad_id=191&menu_id=2286&padre_id=0&submenu_id=3887&pagestoyen=29&ncab=5.2.1&contadort=28)
y posteriormente
[CIELab](http://recursos.cnice.mec.es/fp/artes/ut.php?familia_id=5&ciclo_id=1&modulo_id=6&unidad_id=191&menu_id=2286&padre_id=0&submenu_id=3887&pagestoyen=29&ncab=5.2.1&contadort=28).

Estos espacios definen los colores tal y como los perciben nuestros
ojos, siendo *independientes del medio en el que se muestren* (papel,
pantalla, ...). Son los llamados ***espacios de color independientes de
los dispositivos***.

Un **espacio de color** es un sistema de representación del color que
define los colores posibles dentro de unos límites definidos: el espacio
de color define exactamente cuáles son los colores primarios (los
«ceros» de cada terna de colores), que establecen los límites que ningún
color puede rebasar. Es decir, no pueden haber números negativos ni
valores que excedan los límites del triángulo generado por los tres
colores primarios: si los colores se definen con números entre *0* y
*255*, ningún color puede tener valores superiores a *255*. Si el rango
es *(0, 65365)*, ningún color puede superar el valor *65365*. Y si los
valores están entre *0.0* y *1.0*, ningún color puede tener ningún valor
superior a *1*.

Y aunque la definición anterior se basa en un modelo de color, o sea en
fórmulas matemáticas, también es posible definir un espacio de color de
forma arbitraria (como ha hecho *Pantone*, con su lista de nombres o
números que representan colores).

Aún así, **el rango de colores o gamut de un espacio de color es la
cantidad de colores que puede representar respecto a un espacio de
referencia** (CIEXYZ o CIELab).

Pero no debes confundir este concepto con **el rango de colores que un
dispositivo es capaz de ofrecer**: para un dispositivo su propio rango
de colores es la cantidad de colores que es capaz de ofrecer dentro de
un espacio de color dado (el subconjunto de colores que puede generar).

En cualquier caso estos rangos suelen representarse como triángulos,
aunque en el caso de las impresoras la forma es más irregular.

La representación más habitual se basa en el **diagrama CIExy**, que es
matemáticamente preciso y muestra los colores de una forma lineal: cada
valor numérico se sitúa en una coordenada bidimensional lineal, por lo
que el color (10, 25) estará 5 unidades más arriba en el gráfico que
(10, 20). Sin embargo, tal como demostró [David MacAdam con sus
elipses](http://rgbcmyk.com.ar/es/gutenberg/gdc/1-9-uniformidad-perceptual),
este diagrama no es adecuado para mostrar nuestra percepción de los
colores, que es de naturaleza logarítmica (para nuestros ojos el primer
color *no estará 5 unidades más arriba que el segundo*), así que se creó
un diagrama perceptualmente más adecuado a nuestra visión: el **diagrama
CIELuv**.

<figure>
<img src="/images/1931-to-1976.jpg" title="1931-to-1976.jpg" />
<figcaption>1931-to-1976.jpg</figcaption>
</figure>

Aunque lo más típico es ver los triángulos de los rangos de colores en
diagramas CIExy, nos resulta más intuitivo ver qué colores abarca cada
rango si se representa en diagramas CIELuv. De esta forma podemos
apreciar mejor la diferencia visual, lo que nos puede ofrecer un rango
de colores frente a otro (*¿es capaz de generar más verdes o más rojos
uno que otro, o son similares?*).

Sea como fuere, podemos asimilar el concepto del rango de color a la
paleta de un pintor, donde éste mezcla diferentes proporciones de una
serie de colores básicos para obtener una determinada cantidad de
colores posibles: todos los colores surgen de la mezcla de los colores
básicos, pero no puede haber ningún color que no se pueda generar con la
mezcla de esos mismos colores básicos (*aunque éso no significa que no
existan otros colores, sino simplemente que no se pueden generar con
esos colores básicos*).

Y ahora podemos considerar los 2 tipos fundamentales de modelos de
color: el *modelo aditivo* (los colores se combinan hasta conseguir el
blanco) y el *modelo sustractivo* (los colores se combinan hasta
conseguir el negro).

El **modelo de color RGB** es del tipo de síntesis aditiva y en base a
sus tres colores primarios rojo (R), verde (G) y azul (B), se usa en
monitores, escáneres y cámaras digitales para crear una representación
digital del color de una escena o de un documento.

Por su parte, el **modelo de color CMYK** es del tipo de síntesis
sustractiva y es el empleado comúnmente por las impresoras, que plasman
una fotografía en el papel (u otro soporte) usando pigmentos de varios
colores, normalmente cyan (C), magenta (M) y amarillo (Y), a los que se
les añade el negro (K) para mejorar la calidad de las sombras y los
negros (los pigmentos no son perfectos y aunque en teoría proporciones
iguales de los tres colores primarios deberían producir negro puro, en
la práctica esto no es posible).

Además existen otros modelos de color basados en otras propiedades del
color como **HSL** (tono o *Hue*, saturación o *Saturation* y claridad o
*Lightness*) y **HSV** (tono o *Hue*, saturación o *Saturation* y valor
o *Value*).

Pero debes entender que cada modelo de color tiene sus propias
definiciones de primarios, por lo que aunque a veces encuentres la misma
palabra, su significado a la hora de mezclar colores es distinto en un
modelo o en otro. Por éllo al ajustar los mismos valores en distintos
modelos el resultado es diferente.

Si quisieras pasar de un modelo de color a otro existen transformaciones
matemáticas que lo permiten, pero no es un asunto trivial y
habitualmente la conversión no es perfecta (los colores no serán
exactamente los mismos).

Por fin, empleando el modelo de color RGB se han creado una variedad de
espacios de color, cada uno indicado para un propósito concreto, pero
todos éllos **ligados a un dispositivo**. Esto significa que por ejemplo
no podemos generar de la misma forma el espacio sRGB en una pantalla que
en una impresora, porque la pantalla utiliza aditivamente los colores
rojo, verde y azul, mientras que la impresora emplea sustractivamente
los tintes cian, magenta y amarillo. Por ésto para presentar los mismos
colores incluídos en el espacio sRGB en ambos dispositivos, los procesos
internos serán distintos. La misma consideración se puede hacer con
AdobeRGB, ProPhoto, ACES, etc.

Y para evitar confusiones, **los espacios de color no son los perfiles
de color**: un *perfil de color* contiene la definición de un *espacio
de color* en su interior, pero también contiene otra serie de datos
necesarios para la gestión del color, como por ejemplo la forma de
convertir ese espacio de color en el espacio de color de referencia
(empleando el *PCS*, o espacio de conexión de perfiles, *Profile
Connexion Space*).

### La corrección gamma

La [codificación gamma, compresión gamma, o simplemente
gamma](http://www.guillermoluijk.com/article/gamma/index.htm)\] es una
operación no lineal que se usa para codificar y decodificar la
luminancia o los valores triestímulos en sistemas de vídeo o imagen. Se
puede expresar matemáticamente así:

<figure>
<img src="/images/gamma_formula.png" title="gamma_formula.png" />
<figcaption>gamma_formula.png</figcaption>
</figure>

Valores de gamma menores que 1 se usan para codificar comprimir una
imagen, mientras que los valores de gamma mayores que 1 se usan para
decodificarla (expandirla). Es decir, para que la gamma sea útil debe
existir un proceso de codificación y otro de decodificación, de manera
que la imagen se restaure para poder verla.

Por ejemplo, en el caso de la representación de una imagen *previamente
codificada* en un monitor:

- <big>**V<small>in</small>**</big> sería el valor digital del píxel
  normalizado a 1
- <big>**V<small>out</small>**</big> representa la luminancia resultante
  del píxel
- <big>**A**</big> es el valor del control de contraste
- y <big>**B**</big> el nivel de negro la luminancia cuando
  <big>**V<small>in</small>=0**</big>

Sin embargo, a pesar de la creencia popular, **la gamma no se usa para
ajustar la imagen digital a como nosotros la percibimos en la vida
real**. En realidad hoy en día se emplea para:

- aprovechar mejor el número limitado de niveles cuando la imagen se
  guarda con 8 bits por canal: en este caso cada canal sólo puede tener
  256 niveles
- mantener la compatibilidad con los dispositivos más antiguos

En el primer caso se tiene en cuenta que la visión humana es más
sensible a los tonos oscuros que a los tonos brillantes: *vemos mejor
con poca luz que a pleno sol*. Como la codificación digital reparte los
tonos de una forma distinta (la mitad de los bits de una imagen se
destinan a los píxeles más brillantes), al final nos encontramos que los
tonos más oscuros sólo disponen de unos pocos niveles (3-4 de un total
de 255) para definir las sombras, lo cual es claramente insuficiente. Y
la codificación gamma lo que hace en la práctica es elevar la
luminosidad de las zonas oscuras sin casi modificar las luces, con lo
que al final disponemos de más niveles para codificar las sombras y
evitar posterizaciones. Después, al decodificar la imagen se devuelve
cada tono *a su sitio* y las pérdidas generadas en las luces son
imperceptibles al ojo.

En el caso de los dispositivos, la industria simplemente no puede asumir
implantar un nuevo sistema de codificaciones lineales, porque
automáticamente dejarían obsoletas la mayoría de pantallas, impresoras,
... Así pues, se sigue codificando/decodificando aunque las pantallas
digitales en realidad (casi) no lo necesitarían.
