---
title: Capture Sharpening
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Nitidez en captura

</div>

## Qué es

La herramienta ***Nitidez en captura*** ayuda a recuperar detalles
borrosos causados por efectos ópticos en el sensor de la cámara, que
pueden ser debidos a la
[difracción](https://es.wikipedia.org/wiki/Difracción_(física)), al
[filtro
antialiasing](https://es.wikipedia.org/wiki/Filtro_antialiasing), o a
otras fuentes de [difuminado de tipo
Gaussiano](https://es.wikipedia.org/wiki/Desenfoque_gaussiano).

Se aplica al archivo raw inmediatamente después del desentramado y
modifica los datos con una gamma lineal, para limitar la generación de
halos. Esto significa que **sólo funcionará en archivos raw**.

## ¿Es la herramienta definitiva para el aumento de la nitidez?

Aunque pueden obtenerse excelentes resultados con los ajustes
predeterminados, esta herramienta no está pensada para ser la única
utilizada en el aumento de la nitidez. Más bien debería ser considerada
como un primer paso necesario para mejorar la distinción entre ruido y
detalles, antes de procesar la imagen con otras herramientas en el
circuito de revelado. Por lo tanto, puede usarse junto con otros métodos
tales como la *Máscara de nitidez* o la *Deconvolución*.

La combinación de estas herramientas dependerá de lo que estés
intentando conseguir y de lo que sea aceptable a causa de los artefactos
generados. También dependerá del tamaño final de la imagen y de si va a
ser impresa o no. Esto es debido a que en ambos casos es posible que
puedas aplicar un aumento de nitidez más intenso, sabiendo que no será
tan aparente en la imagen final.

Aquí tienes dos combinaciones típicas de la *Nitidez en captura* con
otras herramientas de aumento de nitidez:

- con la *Máscara de nitidez*: usa un radio pequeño en esta herramienta
  y vigila los artefactos a medida que aumentas la nitidez.
- con la *Deconvolución*: busca un valor apropiado del radio (mediante
  prueba y error, para evitar halos generados por la deconvolución) y
  escoge un umbral de contraste alto, de modo que sólo se realcen los
  detalles y bordes más definidos. Esto te permitirá minimizar los
  frecuentes artefactos que genera esta herramienta). Probablemente
  también necesites aplicar una mayor cantidad de aumento de nitidez.

## Cómo funciona (ajustes)

Cualquier cambio en los ajustes se aplica a la imagen entera,
independientemente del nivel de ampliación de la vista previa, por lo
que dependiendo de tu sistema, el procesamiento de los cambios puede
tardar algo de tiempo. No obstante, una vez hechos los cambios, puedes
ampliar la vista previa y moverte por ella sin ningún retardo de
procesamiento adicional.

También puedes usar la *Máscara de contraste de nitidez*: las áreas
blancas aumentarán su nitidez, mientras que las negras no lo harán. La
máscara es visible tanto en la *Vista previa* como en el panel del
*Navegador*.

### Umbral de contraste

De forma predeterminada, la herramienta analiza la imagen y calcula un
umbral, para evitar aumentar la nitidez del ruido.

Puedes dejar activado el cálculo del *Umbral automático de contraste*, o
puedes desactivarlo y ajustarlo según tus necesidades: si mueves el
deslizador a la derecha, significa que los detalles deberán tener mayor
contraste para que puedan aumentar su nitidez. Los valores altos del
*Umbral de contraste* también reducen la cantidad de aumento de nitidez
aplicada al ruido, que tiende a tener un contraste más bajo.

### Radio

Cuando se produce un desenfoque en cámara, la resolución efectiva ya no
depende del tamaño del píxel: en lugar de eso, tiene un radio que
aumenta en proporción a la cantidad de desenfoque.

El propósito de esta herramienta es reducir este desenfoque, tratando de
estimar automáticamente el radio necesario para contrarrestar el efecto.

<div>

- <figure>
  <img src="/images/Clematis_original.png" title="Clematis_original.png" />
  <figcaption>Clematis_original.png</figcaption>
  </figure>

- <figure>
  <img src="/images/Clematis_good_radius.png" title="Clematis_good_radius.png" />
  <figcaption>Clematis_good_radius.png</figcaption>
  </figure>

</div>

También puedes elegir ajustar tú mismo el radio, teniendo en cuenta que
si el valor es demasiado bajo, no habrá suficiente aumento de nitidez y
si es demasiado alto, producirá halos intensos en los bordes. No olvides
que sólo estás intentando deshacer el desenfoque en cámara.

<div>

- <figure>
  <img src="/images/Clematis_good_radius.png" title="Clematis_good_radius.png" />
  <figcaption>Clematis_good_radius.png</figcaption>
  </figure>

- <figure>
  <img src="/images/Clematis_bad_radius.png" title="Clematis_bad_radius.png" />
  <figcaption>Clematis_bad_radius.png</figcaption>
  </figure>

</div>

Aunque el radio predeterminado es perfecto en la mayor parte de los
casos, puede haber escenarios donde necesites ser aún más cuidadoso para
evitar el ruido y el exceso de nitidez. Por ejemplo, cuando se va a
procesar una imagen en programas diseñados para apilado de enfoque,
imágenes astronómicas, imágenes de super alta resolución, etc. En esos
casos, puede ser mejor desactivar el cálculo automático del radio y
ajustarlo manualmente a un valor más bajo para evitar artefactos
(comprueba los resultados ampliando la vista previa de la imagen). No
habrá tanto aumento de nitidez, pero habrá menos o ningún artefacto que
pudiera ser realzado por el procesamiento subsiguiente en otros
programas.

Observa también que si estás editando un archivo raw de larga exposición
(con *«píxeles bloqueados»*), el cálculo automático del radio funciona
mucho mejor con el *Filtro de píxeles bloqueados* activo (ubicado en la
pestaña *Raw*):

<div>

- <figure>
  <img src="/images/Renon_hotpixels.png" title="Renon_hotpixels.png" />
  <figcaption>Renon_hotpixels.png</figcaption>
  </figure>

- <figure>
  <img src="/images/Renon_nohotpixels.png" title="Renon_nohotpixels.png" />
  <figcaption>Renon_nohotpixels.png</figcaption>
  </figure>

</div>

### Aumento del radio en las esquinas

A menudo las imágenes están más difuminadas en las esquinas que en el
centro. El deslizador *Aumento del radio en las esquinas* permite
compensar esto, aumentando o disminuyendo el radio en estas áreas.

Moviéndolo a la derecha aumenta la nitidez en las áreas exteriores, y
moviéndolo a la izquierda reducirá la nitidez en esas áreas.

### Iteraciones

Una vez el radio se ha calculado o ajustado manualmente, la herramienta
lleva a cabo una serie de procesos para tratar de compensar cualquier
desenfoque.

Es un tratamiento iterativo, que producirá artefactos si se realiza
demasiadas veces: el proceso se realiza sobre el resultado de la
iteración anterior, con lo que cualquier artefacto se amplificará
sucesivamente. Si marcas la casilla *Límite automático de iteraciones*,
se limitará el número de iteraciones, aunque también puedes ajustarlo
manualmente usando el deslizador *Iteraciones*.

## Prerrequisitos

Para obtener el máximo de esta herramienta, es necesario que el nivel de
blanco de la cámara sea correcto, especialmente si la imagen tiene
transiciones abruptas entre luces altas recortadas y no recortadas. Si
tienes problemas, por favor consulta la sección sobre *Niveles de
blanco* en [Adición de soporte para nuevos formatos
raw](Adding_Support_for_New_Raw_Formats/es.md).
