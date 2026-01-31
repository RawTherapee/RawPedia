---
title: Black-and-White
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Color Tab'
---

<div class="pagetitle">

Blanco y Negro

</div>

<figure>
<img src="/images/bw_high-key.jpg" title="bw_high-key.jpg" />
<figcaption>bw_high-key.jpg</figcaption>
</figure>

__TOC__

*<small>La fotografía en clave alta anterior, por cortesía de
[Photography Blog](http://www.photographyblog.com)</small>*

## Fotografías monocromáticas

Se trata de imágenes que básicamente tienen un sólo color o tono, aunque
habitualmente se refieren a las tradicionales imágenes en blanco y
negro, con o sin [viraje de tono](https://es.wikipedia.org/wiki/Virado)
aplicado. Sin embargo en RawTherapee las fotografías en blanco y negro
siguen siendo fotos con 3 canales de color en lugar de 1 sólo («son
fotos en color que sólo muestran diferentes tonos de gris»).

En esta herramienta se habla exclusivamente de imágenes en blanco y
negro y sus virajes.

En general primero debes generar y ajustar la imagen en blanco y negro
con uno de los tres métodos disponibles y los ajustes de la gamma.
Después puedes querer realizar virajes (introducir dominantes de color)
y finalmente puedes ajustar las curvas de luminancia.

En cualquier caso, si tu interés principal es imitar el resultado que
conseguirías con papel fotográfico y un revelado concreto, lo más
recomendable es que emplees la herramienta [*Simulación de
película*](Film_Simulation/es.md).

## Creando las imágenes en Blanco y Negro: los diferentes métodos

<div class="img-comp-wrapper img-comp-right">
<div class="thumbinner thumbcompare tnone" style="width: 582px">

<imgcomp img1='bw_conversion_before.jpg' img2='bw_conversion_after.jpg'  width=582 />

<div class="thumbcaption">

**Izquierda:** la imagen en color antes de ser procesada con la
herramienta.

**Derecha:** vista de la imagen después de ser convertida a blanco y
negro.

</div>
</div>
</div>

La herramienta *Blanco y Negro* te ofrece tres métodos a la hora de
realizar la conversión: ***Desaturación***, ***Ecualizador de
luminancia**'' y***Mezclador de canales**''.

Sin embargo también puedes crear imágenes monocromáticas mediante:

- el deslizador [*Saturación*](exposure/es#saturación) de la
  herramienta [*Exposición*](exposure/es), ajustándolo a
  *-100*
- el deslizador
  [*Cromaticidad*](lab_adjustments/es#cromaticidad) de la
  herramienta [*Ajustes L\*a\*b\**](lab_adjustments/es),
  ajustándolo a *-100*
- activando la herramienta [*Simulación de
  película*](Film_Simulation/es.md) y seleccionando un filtro en
  blanco y negro (película Ilford, Kodak, Fuji...)
- con la herramienta [*Mezclador de
  Canales*](Channel_Mixer/es.md) (por ejemplo, ajustando todos
  los deslizadores con el mismo valor)

Si decides emplear esta herramienta, los valores de *«a\*»* y *«b\*»* en
los *Ajustes L\*a\*b\** se ponen *a cero* para conseguir grises
perfectos, ya que el procesado *L\*a\*b\** se realiza al final del
circuito de revelado y podría interferir en los resultados deseados.

Además la herramienta [*Virado de color*](color_toning/es)
tiene una vinculación especial con la herramienta *Blanco y Negro*, como
se explicará más adelante.

### Desaturación

Con este método a cada píxel se le asigna en sus tres canales (R=G=B) el
valor de luminancia resultante de calcular la fórmula:
<img src="/images/luminance_value.png" title="luminance_value.png" height="35"
alt="luminance_value.png" />. Esto asegura una imagen gris totalmente
neutra, pero sin ninguna posibilidad de ajustar a nuestro gusto las
tonalidades directamente en la herramienta.

Nota: los otros dos métodos de desaturación en Rawtherapee dan tonos de
gris distintos debido a sus diferentes algoritmos. En *Exposición* es el
canal *S* del espacio de color *HSV* el que se pone a *0*. En *Ajustes
L\*a\*b\** es la cromaticidad
(<img src="/images/chroma.png" title="chroma.png" height="35" alt="chroma.png" />)
la que se pone a *0*.

### Ecualizador de luminancia

![](bw-lumeq.jpg "bw-lumeq.jpg") Este método usa una [*curva
plana*](General_Comments_About_Some_Toolbox_Widgets/es#The_Flat_Curve.md),
que permite modificar la luminancia en función del matiz de la foto
original en color. Es decir, ajustar la luminancia de cada matiz por
separado.

Aquí es muy útil el cuentagotas
(![<File:crosshair-node-curve.png>](crosshair-node-curve.png "File:crosshair-node-curve.png")):
pincha con él un área de tonos que quieras oscurecer y añadirás un nuevo
punto de control en la curva. Muévelo hacia abajo para oscurecer (o
hacia arriba para aclarar) el tono gris correspondiente al matiz
seleccionado.

Puedes actuar con sutileza para ajustar mínimamente los tonos que
necesites, o emplear cambios profundos para modificar radicalmente la
estética de la foto.

Además, si estás pensando en realizar un viraje, quizá sea interesante
ser más radical, ya que el mayor contraste suele ir bien en las imágenes
viradas.

### Mezclador de canales

El *Mezclador de canales* es un arma de doble filo: tiene aspectos
interesantes como la simulación de filtros de color para blanco y negro
o las plantillas de efectos preestablecidos (para mejorar paisajes,
retratos o fotos con alto contraste, por ejemplo). Pero debes hilar muy
fino con los ajustes, o aparecerán efectos inesperados, ilógicos o
artefactos.

En general lo que puedes conseguir con este método lo puedes conseguir
también usando otras herramientas que modificarán los tonos gris de la
imagen (no producirán virajes), por lo que en principio **no se trata de
un método recomendable**. Sin embargo, si necesitas la simulación de
filtros de color, o si deseas realizar casi todos los ajustes desde una
única herramienta, puedes aventurarte a usarlo.

#### Botón Auto

Este botón equilibra los tres canales primarios (R, G, B) para que
tengan el mismo peso relativo en la foto.

Probablemente no notarás gran diferencia entre el aspecto por defecto y
con los canales recalculados. Además forzará el cambio al *Ajuste
predefinido RGB Relativo*.

#### Ajustes predefinidos

Son una serie de ajustes fijos de los tres canales, con diferentes
valores según el *Ajuste predefinido* que escojas. En el caso de los
ajustes «con nombre», no se trata de valores que no se puedan introducir
a mano, sino simplemente atajos para hacerte la vida un poco más fácil.
Sin embargo, al seleccionar uno de estos ajustes, no podrás cambiar los
valores de los canales.

En el caso de los ajustes con libertad de modificar los canales, tenemos
los *Relativos* y los *Absolutos*: con los *Relativos* el programa
intenta controlar que los tonos no se desmadren y empiecen a aparecer
zonas quemadas y/o subexpuestas. Pero en el caso de los *Absolutos*, no
hay ningún control y se modificarán directamente los valores de los
píxeles, con lo que será fácil introducir recortes, pero tendrás un
mayor poder de decisión sobre lo que va a ocurrir en la imagen.

Invariablemente podrás ver bajo la lista de selección de los *Ajustes
predefinidos* los valores finales de los porcentajes de variación de
cada canal (R, G y B), así como el total tras sumarlos.

En cualquiera de estos tipos de ajustes podrás elegir si trabajas con
**3 canales (RGB)** o con **6 canales (RNAmVCAzPM**, o Rojo Naranja
Amarillo Verde Cian Azul Púrpura Magenta), si bien en este último caso
al ajustar un canal secundario, lo que harás en realidad es ajustar los
tres primarios a la vez, con distintas intensidades.

Por último, algo que debes tener muy en cuenta para evitar sorpresas
desagradables: en los ajustes *Absolutos* los porcentajes resultantes
podrán sumar más o menos del 100% (desde *-300%* hasta *600%*). Sin
embargo en los ajustes *Relativos* la suma está forzada a ser *100%*, lo
cual en general no supone ningún problema, pero si mezclas valores
negativos y positivos en una imagen, ocurrirá lo siguiente: **cuando la
suma de los valores sea *0%* (*10%, -2%, -8%*), al bajar un punto más la
suma negativa (*10%, -2%, -9%*) la imagen se invierte. Lo que antes era
blanco ahora es negro y viceversa.**

#### Filtro de color

El filtro de color imita las fotografías tomadas con un filtro coloreado
delante del objetivo.

Estos filtros permiten el paso de un color específico mientras que
bloquean en más o menos cuantía [el color
opuesto](https://es.wikipedia.org/wiki/Círculo_cromático). En
consecuencia, tienen un impacto en la luminancia de esos colores.

Por ejemplo, un filtro rojo oscurece los tonos azules y aclara los
rojos.

## Corrección gamma y curvas de luminancia

Los deslizadores de ***corrección gamma*** de los canales RGB permiten
llegar a una aproximación del aspecto de una foto en papel fotográfico
(«duro», «normal», «suave»): moviéndolos hacia la izquierda (valores
negativos) la imagen se oscurece y adquiere más contraste; si los mueves
hacia la derecha (valores positivos) la imagen se hace más brillante,
menos contrastada y se «suaviza».

Pero si te fijas, cuando uses ProPhoto como espacio de trabajo, el canal
azul será menos activo: para ver mejor el efecto de este canal, usa el
espacio de trabajo sRGB.

Solo con estos controles de *corrección gamma* ya puedes conseguir
buenos resultados, pero si añades las capacidades de las *curvas de
luminancia*, podrás afinar mucho más la progresión de tonos grises y el
grado de contraste de la imagen.

Las ***curvas de luminancia*** modifican los niveles de gris de la
imagen en función de la luminosidad de los píxeles. Se usan de la misma
manera y dan el mismo resultado final que las descritas en la
herramienta [*Exposición*](exposure/es), permitiéndote
refinar los resultados y haciéndolos independientes de los ajustes
hechos en otras partes.

Mientras que la ***curva «Antes»***tiene 4 formas de calcular el tono
gris a partir de los valores RGB (*B/N estándar, B/N promediado
estándar, B/N como la película, B/N mezcla de saturación y valor''),
la***curva «Después»**'' no tiene opciones, ya que esta curva modifica
la imagen cuando ya está en blanco y negro.

## Virajes en blanco y negro

No debes olvidar que aunque estás trabajando en una imagen en blanco y
negro, todavía dispones de los tres canales (R, G y B) activos y es el
programa el que les da el mismo valor para que se vean tonos de gris.
Así pues, todavía puedes hacer
[virajes](https://es.wikipedia.org/wiki/Virado) para modificar los tonos
de la imagen.

En la fotografía clásica el proceso se basaba en sustituir o teñir las
sales de plata de la foto por compuestos de diferentes colores. En la
fotografía digital el proceso se basa en modificar los canales de color
para que los píxeles dejen de verse gris y pasen a ser de un color
determinado.

En RawTherapee, tras activar la herramienta *Blanco y Negro*, la mayoría
del resto de herramientas influirán más o menos en los tonos grises que
aparecerán en la imagen, mientras que hay unas cuantas que serán capaces
de «influir en el color» de la imagen en blanco y negro:

- cuando únicamente tienes la foto convertida a blanco y negro, estas
  herramientas cambiarán el tono de la imagen:
  - *ondículas \> imagen residual \> equilibrio de matiz y color*
    (tonalidades en distintas zonas)
  - *ciecam \> condiciones de visualización \> temperatura, tono*
    (introduce una dominante general)
  - *viraje de color* (tonalidades en distintas zonas)
- en cambio, tras realizar un viraje a la foto en blanco y negro,
  cualquier modificación del color realizada con las herramientas *curva
  de tono, curvas RGB, curvas HSV, simulación de película (en color),
  supresión de neblina* y en general cualquier herramienta que cambie
  los tonos (los colores) de la imagen, cambiarán también el matiz del
  viraje, ya que la foto seguirá siendo en color (aunque la veamos en
  blanco y negro).

**El método recomendado para realizar virajes en RawTherapee es usar la
herramienta *Viraje de color*.**

Sin embargo actualmente esta herramienta no está del todo pulida y
tendrás que saber qué usar, cómo y cuándo: para empezar debes saber que
en casi todos los métodos aquello que afecta a las luces, afecta a las
**muy altas** luces (esto significa que afectará a menos zonas de las
que podrías esperar).

Los diferentes métodos disponibles tienen su utilidad y a veces sus
defectos:

1.  **Mezcla L\*a\*b\***: en principio puede parecer un método sencillo,
    ya que sólo requiere situar puntos de control a lo largo de una
    curva, seleccionar arriba/abajo el tono del viraje y en horizontal
    la luminosidad en la que se aplicará el color. Pero es difícil
    ajustar bien el tono que quieres y en qué luminosidad se aplicará.
    Además no hay medios tonos: el corte es bastante abrupto alrededor
    de valores de canal de *120-130*.
2.  **Deslizadores RGB**: se trata de seleccionar el tono de viraje con
    el punto de control superior y la saturación (intensidad) del color
    con el punto de control inferior. Mediante el deslizador de
    *Balance* se puede modular en parte la zona de transición (los
    medios tonos), pero el cambio es bastante rápido (la zona de
    transición es estrecha incluso con *Balance: -100*). Además, con el
    *Balance* a *-100*, todavía hay viraje en las sombras. Y con el
    viraje totalmente desaturado en las luces, la zona de transición
    todavía es una mezcla entre el color de las sombras y el de las
    luces (sombras azules + luces amarillas pero desaturadas al 100% =
    medios tonos verdes que dan paso a luces grises).
3.  **Curvas RGB**: **NO ES UN MÉTODO RECOMENDABLE EN ABSOLUTO**. No es
    intuitivo lo que hace, y hasta puedes obtener una mezcla de colores
    que funciona de este modo: desde el color de las sombras se pasa a
    un tono medio-desaturado, después se mezclan los colores en una
    estrecha franja de medios tonos, para a continuación ir al tono
    semi-desaturado de las luces, que llega al color saturado
    seleccionado, para pasar en las más luces al blanco. En otras
    circunstancias la zona de transición (con mezcla de colores) es muy
    estrecha y con un color intenso. Como se ha dicho no es
    recomendable: teniendo otros métodos, perder el tiempo en este no
    parece lógico.
4.  **Balance de color sombras/medios tonos/luces**: **NO ES UN MÉTODO
    RECOMENDABLE**. Con suerte encontrarás una mezcla de valores que te
    den un viraje medio decente. **TODOS LOS DESLIZADORES MODIFICAN EL
    TONO DE TODAS LAS LUMINANCIAS**. Así que tras modificar las sombras
    a tu gusto, cuando vayas a las luces o los medios tonos, estos
    modificarán lo que hayas hecho para las sombras. Y así
    sucesivamente.
5.  **Saturación con 2 colores**: similar a *Deslizadores RGB*, pero con
    menos transición en medios tonos (es prácticamente inexistente) y
    además el viraje en las luces es para las muy altas luces. El resto
    lo copa el viraje para las sombras y además es excesivamente fácil
    introducir artefactos de color.
6.  **Cuadrícula de corrección de color L\*a\*b\***: sirve para virajes
    de un solo color, con un respeto razonable de las muy altas luces
    (que se ven bastante blancas). Si no quieres imitar lo más
    correctamente posible el color de un viraje clásico, mediante la
    mezcla de los colores seleccionados por los dos puntos de control
    (el blanco y el negro), puedes obtener virajes agradables.
7.  **Zonas de corrección de color**: para virajes que no quieran imitar
    a los virajes químicos clásicos, **ESTE ES EL MÉTODO MÁS
    RECOMENDABLE**. Tienes todo el poder de las máscaras, con control
    sobre el tono del viraje, lo claro u oscuro que quedará (imitando
    p.ej. virajes que reducen el contraste de la foto), la transición
    entre las zonas enmascaradas (viradas) y las que no, ... Además de
    una selección directa del color del viraje y la saturación de ese
    color. Sin embargo se hace difícil realizar virajes con dos colores,
    ya que es complicado que las máscaras para ambos colores se ajusten
    correctamente.

En resumen, para virajes no demasiado complicados no tienes por qué
buscar en otro lugar: si empleas los métodos que no están
desaconsejados, podrás obtener buenos efectos. Pero si buscas imitar lo
mejor posible los virajes clásicos, el proceso es algo más laborioso,
como se explica a continuación.

## Flujo especial de trabajo para virajes clásicos

\[\[<File:classic-toning_collage.jpg%7Cthumb%7Cright%7C850px%7CLos>
virajes clásicos:  

<div class="captions_indent">

**1- Viraje al Azul de Prusia**  
**2- Viraje al cianotipo**  
**3- Viraje al cobre**  
**4- Viraje a la gelatina de plata**  
**5- Viraje al oro**  
**6- Viraje al paladio**  
**7- Viraje a la plata**  
**8- Viraje al platino**  
**9- Viraje al selenio**  
**10- Viraje sepia**

</div>

\]\] Los virajes químicos tienen unas tonalidades específicas que por
razones históricas, o simplemente por gusto estético, son deseables a la
hora de imitarlas en el mundo digital.

Para usar las tablas de virajes que puedes encontrar en internet,
deberás usar la herramienta *Curvas RGB* para introducir los valores
indicados en las «fórmulas».

Puesto que no existe equivalente en la herramienta *Virado de color*, no
queda más remedio que exportar la imagen en blanco y negro y después
cargarla en el *Editor* para aplicar apropiadamente el viraje en las
*Curvas RGB*.

Sin embargo, dado el modo en que RawTherapee está programado, es vital
usar como perfil de trabajo el mismo que aquel con el que se haya
exportado la imagen. Así que el proceso es como sigue:

1.  procesa la imagen para tener un resultado en blanco y negro adecuado
    para el posterior viraje (por ej., con el suficiente contraste y
    gama de grises)
2.  exporta en un formato de **16bits** (*tiff* o *png*) **estableciendo
    el *perfil de salida* idéntico al *perfil de trabajo*** (anota si es
    necesario el *perfil de salida* que has usado)
3.  carga en el *Editor* la imagen en blanco y negro y establece el
    *perfil de trabajo* con el mismo perfil que has exportado la imagen
    en blanco y negro (**este paso es muy importante**)
4.  ves a la herramienta *Curvas RGB* y edita las curvas de cada canal,
    o mejor aún carga [los perfiles que te
    ofrecemos](http://rawpedia.rawtherapee.com/classic-toning.zip)
    (tienes perfiles para imágenes exportadas en sRGB, en Rec2020 y en
    ProPhoto)
5.  exporta de nuevo la imagen en el formato y la profundidad de bits
    que desees

Si has exportado la imagen en blanco y negro con un perfil de color
distinto a los tres que te ofrecemos, debes tener en cuenta que las
«fórmulas» que encontrarás en la red generalmente están pensadas para
imágenes codificadas en sRGB y con un rango de valores entre *0* y *255*
(8 bits). Sin embargo RawTherapee necesita los valores para las curvas
en el rango \[0, 1\], así que tendrás que convertir los valores tanto en
el rango como en el espacio de color.

El problema con RawTherapee actualmente es que si no realizas esta
conversión, los colores del viraje no serán correctos y obtendrás unos
tonos claramente distintos a los deseados.

Si quieres un viraje doble (por ejemplo sepia en las sombras y tonos
medios, con plata en las luces), puedes probar a editar la curva del
viraje sepia y cambiar los valores de los tonos más claros por los
valores del viraje plata (aunque lo más probable será que tengas que
ajustar los valores para conseguir un resultado más integrado con el
viraje de base). Es algo laborioso, pero se puede conseguir.
