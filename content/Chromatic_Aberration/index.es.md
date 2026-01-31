---
title: Chromatic Aberration
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Correción de Aberraciones Cromáticas

</div>

__TOC__

## Introducción

![](Light_dispersion_conceptual_waves-small.gif "Light_dispersion_conceptual_waves-small.gif")
Cuando la luz cambia entre medios con índices de refracción diferentes
(como ocurre en el cambio de aire a vidrio y viceversa) se produce un
desvío del ángulo en el que viajan los rayos. Además, cuando diferentes
colores de luz se propagan a diferentes velocidades en un medio, el
índice de refracción depende de la longitud de onda y a este fenómeno se
le conoce como *dispersión*.

Un ejemplo muy conocido de este efecto es el del prisma de vidrio, que
dispersa un haz de luz blanca en un arco iris de colores: cada longitud
de onda sufre un cambio de dirección distinto.

Los objetivos fotográficos se componen de varios vidrios y a pesar de
ser de muy alta calidad, no refractan todas las longitudes de onda con
los mismos ángulos. Debido a esto, los colores se *«enfocan»* (se
proyectan) en puntos del sensor distintos a los esperados y a estas
diferencias se les llaman [**aberraciones
cromáticas**](https://www.digitalcamaralens.com/Html/Articulos/Aberraciones%20Cromaticas%20laterales/ACS%20Laterales.htm),
que pueden ser de dos tipos:

- *aberración cromática longitudinal*: también conocida como *aberración
  cromática axial*, es la incapacidad de un objetivo para enfocar
  diferentes colores en el mismo plano focal. Normalmente sólo la luz
  verde está bien enfocada en el sensor, mientras que las luces azul y
  roja se enfocan ligeramente por delante o detrás del sensor y no se
  ven con nitidez. Estas aberraciones se dan en toda la imagen.
- *aberración cromática transversal (o lateral)*: la luz que incide de
  forma oblicua en el objetivo genera esta aberración cromática. En este
  caso todos los colores están enfocados en el mismo plano, pero el
  tamaño de la imagen depende de la longitud de onda (las distintas
  longitudes de onda generan imagenes enfocadas unas mayores que las
  otras). Estas aberraciones no existen en el centro de la imagen y van
  siendo progresivamente mayores hacia la periferia de la foto.

![](chromatic_aberration_auto1.jpg "chromatic_aberration_auto1.jpg")
Ambas aberraciones se suelen dar a la vez y generan halos o bordes
coloreados de muy distintos tonos, aunque los más típicos son los
púrpuras, verdes, azules, amarillos y rojos. Además, se pueden observar
con más claridad en zonas donde hay un buen contraste entre detalles
(entre zonas claras y oscuras).

Además, al no enfocar los 3 componentes de un color en el mismo punto,
se genera una imagen tanto más difusa como importantes son las
aberraciones generadas por el objetivo: **las aberraciones cromáticas
provocan una pérdida irreversible de nitidez y de fidelidad del color en
toda la imagen**: a pesar de que RawTherapee elimina los bordes
coloreados de forma muy eficaz, en realidad no hay manera de devolver la
fotografía a la apariencia original de la escena.

En general ni siquiera los objetivos de alta gama se libran por completo
de este tipo de aberraciones y la borrosidad generada provoca que al
usar la *Máscara de nitidez* aparezcan rápidamente artefactos y zonas de
transición abruptas.

<figure>
<img src="/images/chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" />
<figcaption>chromatic_aberration_auto2.jpg</figcaption>
</figure>

## La corrección de las aberraciones cromáticas en RawTherapee

La herramienta ***Corrección de la Aberración Cromática*** se sitúa en
la pestaña *Raw* y sólo funciona en imágenes captadas mediante sensores
con [filtro de Bayer](https://es.wikipedia.org/wiki/Mosaico_de_Bayer):
modifica la imagen **antes** del desentramado.

En cambio si necesitas corregir la aberración cromática de fotos
procedentes de cámaras con sensores X-Trans (Fuji), deberás usar la
[Corrección de aberración
cromática](Lens/Geometry/es#Corrección_de_aberraión_cromática.md)
situada en la herramienta *Lente/Geometría*, dentro de la pestaña
*Transformar*: en este caso la corrección se realiza **después** del
desentramado.

La diferencia entre uno y otro método radica en que corregir las
aberraciones antes del desentramado puede mejorar la calidad de este
último.

En ambas herramientas verás unos deslizadores *«Rojo»* y *«Azul»* que
sirven para la corrección, pero la herramienta para los archivos tipo
*«Bayer»* es más completa y presenta más controles.

Para usarlas es conveniente ampliar la imagen por encima del *100%* y
combinar esta corrección con la [*Eliminación de bordes
púrpura*](Defringe/es.md).

## Deslizadores Rojo y Azul

Ambos deslizadores son los responsables de eliminar los bordes de color
indeseados: cuando tienes bordes rojo y azul alrededor de los objetos,
emplearás el deslizador ***Rojo**'', mientras que si son azul y
amarillo, emplearás el deslizador***Azul**''. Sin embargo en la práctica
emplearás ambos en todas las ocasiones, aunque uno con más intensidad
que el otro.

Si los deslizadores *Rojo* y *Azul* están a cero, el resultado es el
mismo que «desactivar» la herramienta.

Además, no pueden usarse al mismo tiempo que la *Corrección automática*.

## Corrección automática

**Cuando la «Corrección automática» está activada** los deslizadores
*Rojo* y *Azul* se desactivan y **se efectúa una detección y corrección
automática** de la aberración cromática.

![](CA_manual.jpg "CA_manual.jpg") Además, mientras que la corrección
manual aplica un valor constante en toda la imagen, la corrección
automática divide la imagen en pequeños bloques y aplica en cada uno los
valores que sean necesarios para eliminar la aberración cromática en esa
zona concreta. Por esta razón normalmente la corrección automática
funciona mejor que la manual y los valores de corrección automática no
pueden mostrarse en los deslizadores.

Sin embargo hay situaciones en las que la corrección automática es
incapaz de eliminar las aberraciones en lo más mínimo (no las reconoce
como tal), por lo que no queda más remedio que desactivarla y corregir
«a mano». Pero en estos casos las correcciones deberán ser fuertes, por
lo que es más que posible que corrigiendo un problema generes otros,
provocando aberraciones inexistentes en otras zonas de la foto. Así que
mientras ajustas los deslizadores deberás ir comprobando que no generes
problemas que antes no tenías.

Además, no olvides que la *Corrección de Aberraciones Cromáticas* es
conveniente usarla en conjunto con la herramienta [*Eliminación de
bordes púrpura*](Defringe/es.md). Ninguna de las dos es una
herramienta «pura» a la hora de eliminar uno u otro tipo de aberración
cromática y en realidad se complementan muy bien: esta herramienta
elimina una gran cantidad de aberraciones cromáticas de forma automática
(salvo casos extremos) y le facilita mucho el trabajo a la *Eliminación
de bordes púrpura*. Al mismo tiempo, la *Eliminación de bordes púrpura*
es capaz de afinar el trabajo de la *Corrección de Aberraciones
Cromáticas*. La forma de combinarlas depende en gran medida de cada
fotografía, pero usadas juiciosamente son muy potentes y solventan una
buena parte del problema de las aberraciones cromáticas.

## Iteraciones

Este ajuste sólo está disponible si está activada la *Corrección
automática*.

La *Corrección automática* es conservadora y suele dejar trazas de
aberraciones, por lo que puede iniciar el proceso de búsqueda y
corrección hasta 5 veces. Cada proceso es una iteración que da una
imagen resultante y este resultado es el punto de partida de la
siguiente iteración.

Normalmente con 2 iteraciones suele ser suficiente, aunque en ocasiones
pueden hacer falta más. Sin embargo ten en cuenta que cuantas más veces
realices el proceso, en determinados casos es posible que introduzcas
artefactos que antes no existían.

## Evitar el cambio de color

Un efecto secundario inherente a la herramienta *Corrección de
Aberraciones Cromáticas* es un ligero cambio de color en toda la imagen,
que habitualmente es inapreciable, pero en ocasiones es notable. Por
esto existe la opción de ***Evitar el cambio de color***: corrije los
pequeños desvíos de color producidos, devolviéndolos al tono inicial.

Sin embargo existe una limitación conocida e importante para la
herramienta: en determinadas situaciones, especialmente con fuertes
aberraciones cromáticas, alto contraste y zonas con detalles intrincados
(como ramaje de árboles con el cielo como fondo, aunque no sólo en estos
casos), el algoritmo no calcula correctamente la corrección e introduce
un halo más o menos fuerte de color magenta (puede ser en otros tonos).
En estos casos es mejor desactivar esta opción y aceptar los ligeros
cambios de tono de la corrección de aberraciones:

<figure>
<img src="/images/CA_pinkhalo.jpg" title="CA_pinkhalo.jpg" />
<figcaption>CA_pinkhalo.jpg</figcaption>
</figure>
