---
title: Raw Black Points
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Raw Tab'
---

<div class="pagetitle">

Nivel de Negros en el archivo Raw

</div>
<div class="headline">

Corrigiendo el valor que define el negro absoluto en las fotos

</div>

En general el ***Nivel de negros raw*** (o *Nivel de negros en el
archivo raw*) es un valor bastante bien definido y no es usual que
tengas que corregirlo. De todas formas si la imagen tiene una dominante
de color y es más *apagada* de lo normal, es probable que el *Nivel de
negro raw* sea incorrecto. En casos leves la dominante de color
normalmente es más intensa en los tonos oscuros, pero puede ser difícil
de distinguir.

Cuando se procesa una imagen se convierten los *«valores numéricos raw»*
en *«valores RGB»*, estableciendo un nivel de base (el *«Nivel negro
raw»*) que se convertirá en el *«cero RGB»* y a partir del cual se
codifican todos los demás valores. Sin embargo por distintos motivos ese
«cero» no suele ser equivalente a no haber recibido luz. Es decir, que
por ejemplo el valor medido *512* se establece como *Nivel de negro raw*
y se convierte en el valor *RGB 0*, con lo que todos los valores raw
superiores a *512* se codificarán en RGB en función de este nuevo cero.

En RawTherapee tienes posibilidad de modificar los tres canales RGB por
separado, aunque para las cámaras con [filtro de
Bayer](https://es.wikipedia.org/wiki/Mosaico_de_Bayer) hay dos canales
de verde. Cuando son dos, de forma predeterminada están enlazados entre
sí con la casilla ***Vincular verdes***, pero si estos dos canales
tienen diferentes sensibilidades, puedes desvincularlos y ajustarlos
individualmente.

Estos deslizadores te permiten desplazar el cero hacia arriba o hacia
abajo:

- si los ajustas hacia arriba, lo que estás haciendo es disminuir el
  rango dinámico de la foto, forzando en principio a que los grises más
  oscuros se conviertan en negro y, conforme subas el valor de los
  deslizadores, más y más tonos grises se transformarán en negro. Si los
  ajustes son muy agresivos, puedes llegar a quedarte exclusivamente con
  las luces, siendo negra el resto de la foto. Además si los ajustes de
  los distintos canales no están equilibrados, introducirás fuertes
  dominantes de color en la foto.
- al bajar el valor de los canales, lo que estás haciendo es bajar el
  punto que se considera negro absoluto, el que se codificará como *RGB
  0*, por lo que a partir de ahí todos los valores de los píxeles en ese
  canal cambiarán: es decir, lo que antes era el negro (valor *0*)
  ahora, al disminuir el *Nivel de negros raw*, pasa a tener un valor
  superior. Ya no es negro. Y todos los valores por encima tampoco
  conservarán su nivel, sinó que serán más altos. Esto también conduce a
  que los colores de la imagen cambiarán, llegando a introducir una
  dominante de color a toda la imagen. Sin embargo, por mucho que bajes
  el *Nivel de negro raw*, llegará un momento en que ya no podrá ser
  menor: si inicialmente el negro estaba en el *valor raw 512*, podrás
  rebajarlo hasta el *valor raw 0*, pero no más allá (ninguna cámara
  registra valores negativos).

A pesar de todo, incluso cuando el *Nivel de negros raw* es correcto,
puede que quieras modificarlo para mejorar la calidad de los negros de
la foto. O como efecto secundario, al corregir los tonos negros también
eliminarás en parte la neblina existente en la foto.
