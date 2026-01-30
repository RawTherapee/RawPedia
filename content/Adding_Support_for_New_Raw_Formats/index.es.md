---
title: Adding Support for New Raw Formats es
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Añadir compatibilidad con nuevos formatos Raw

</div>
<div class="headline">

O cómo ayudar a los programadores a que las fotos de tu nueva cámara se
puedan revelar en RawTherapee

</div>

## Introducción

Para que RawTherapee sea compatible con un formato raw se necesita lo
siguiente:

- poder decodificar el archivo raw para que el programa tenga acceso a
  los datos y metadatos almacenados en la imagen. Ésto lo hace o bien el
  código de un programa incorporado en RawTherapee llamado ***dcraw***,
  o bien un código personalizado que también forma parte de RawTherapee.
- poder interpretar los datos de la imagen. Ésto puede subdividirse en:
  - medir los [***niveles de
    blanco***](#Niveles_de_blanco_y_de_negro.md) (y a veces los
    ***niveles de negro***) de los datos decodificados de la imagen, ya
    que cada cámara considera de forma diferente qué es el blanco
    absoluto (y a veces el negro absoluto). Los*niveles de blanco'' se
    miden usando fotos denominadas***tomas en blanco**''.
  - determinar dónde se sitúa la imagen en la matriz de fotodiodos del
    sensor de la cámara (el [***recorte
    raw***](#Recorte_raw.md)).
  - crear un [***perfil de entrada***](#perfil_de_entrada)
    que reproduzca los colores con exactitud.

Tendrás que tomar las fotografías, pero no necesitarás esforzarte por
comprender o llevar a cabo la medición: nosotros lo podemos hacer por
ti.

## Almacenamiento y lectura de la información

RawTherapee busca la información relacionada con interpretar los datos
de la imagen (los niveles de negro y de blanco, la matriz de color, y
algunos otros detalles, pero no el perfil de entrada) en tres sitios:

- en el código de dcraw, que está incorporado en RawTherapee
- en el propio archivo raw
- en un archivo de texto instalado con RawTherapee, llamado
  **`camconst.json`**

En general siempre se priorizan los valores obtenidos de `camconst.json`
sobre los de otras fuentes, aunque si:

- el archivo raw está en formato DNG
- además la etiqueta Exif `Software` (`0x0131`) no comienza con la
  cadena de caracteres `Adobe DNG Converter`
- y el archivo contiene una etiqueta `ColorMatrix2`

entonces se priorizará el valor de esta última etiqueta.

Si por algún motivo has editado el archivo `camconst.json` mientras se
ejecutaba RawTherapee, reinicia el programa para que los cambios tengan
efecto.

## Niveles de blanco y de negro

El sensor de una cámara está compuesto de millones de minúsculos
elementos fotosensibles llamados fotodiodos y cada uno mide la
intensidad de la luz que incide sobre él, registrando esa intensidad
como un número: cuanta más luz, más alto será el número. El grueso del
archivo raw consiste en un listado de estas medidas.

Cada fotodiodo tiene un nivel por debajo del cual no puede detectar luz.
Puede ser que le llegue algo de luz, pero será demasiado débil para
poder registrar una señal. Esto se denomina ***nivel de negro***, y no
siempre es 0.

También hay un nivel por encima del cual el fotodiodo ya no registrará
un cambio de intensidad de la luz, aunque la luz siga intensificándose:
éste es el ***nivel de blanco***. Decimos que un fotodiodo que no puede
registrar luz más brillante está completamente saturado, y a este estado
se le denomina **recorte** en el revelado: la señal se limita a un valor
máximo aunque la luz pueda generar un valor más alto.

Valiéndose de este hecho, los niveles de blanco se miden en fotografías
completamente sobreexpuestas, llamadas ***tomas en blanco***: al
sobreexponer o *«quemar»* las luces, se fuerza a que los fotodiodos
registren el valor máximo que pueden captar.

Algunos modelos de cámara usan los mismos valores de niveles de blanco y
de negro independientemente de otros ajustes, mientras que en otros
modelos estos niveles dependen de otros factores, tales como la
*sensibilidad ISO*. Necesitamos fotos tomadas en todo el rango de
valores ISO para determinar ésto.

Además algunas cámaras tienen incorporada una reducción de ruido, que a
menudo se denomina *Reducción de Ruido en Larga Exposición* (o algo
similar) y esta característica podría afectar a los niveles de blanco y
de negro. Si la activas, normalmente actúa cuando el tiempo de
exposición está por encima de 1 segundo. Los pasos que explicaremos más
adelante indicarán cuándo activarla o desactivarla.

Por fin, los niveles de blanco en algunos modelos de cámara cambian en
función de la apertura del objetivo, pero generalmente esto sólo ocurre
a plena apertura. Para evitar que ésto se convierta en un problema,
**ajusta la apertura a f/5.6 o mayor** salvo que se indique lo
contrario.

Para más información de detalle relativa a las fotografías necesarias y
las instrucciones sobre cómo medirlas, puedes leer los comentarios
incluidos en el archivo
[**camconst.json**](https://github.com/Beep6581/RawTherapee/blob/dev/rtengine/camconst.json)

### Cómo disparar tomas en blanco

**Dispara las fotos raw en modo manual (M)**.

Si tu cámara tiene varios modos raw, usa el modo de mayor calidad, sin
recorte del área del sensor utilizada y con *compresión sin pérdida* si
es posible.

Cada foto debe estar completamente sobreexpuesta en toda la extensión de
la imagen. Por éllo, no importa el sujeto de la toma, ya que todo
quedará blanco, pero es más fácil conseguir ésto si apuntas la cámara
hacia el cielo o a una bombilla blanca. No importa si el cielo está
soleado o nublado, *pero no apuntes la cámara hacia el sol, ya que
podrías dañar el sensor*.

No importa qué objetivo utilices, pero será más fácil lograr que toda el
área de la imagen quede sobreexpuesta si no es un gran angular.

### Grupos de fotos que necesitamos

Hemos dividido las imágenes necesarias en tres grupos, de modo que cada
grupo subsiguiente mejorará la calidad de la decodificación del nuevo
formato, pero también necesitará más esfuerzo por tu parte y por la
nuestra. En la mayoría de los casos, sólo necesitarás fotografiar los
dos primeros grupos.

Todos los grupos requieren fotografiar *tomas en blanco* completamente
sobreexpuestas.

Los grupos son:

1.  Si tu cámara tiene *Reducción de Ruido en Larga Exposición*,
    **desactívala**. Ajusta la apertura a **f/5.6 o mayor**. Toma una
    serie de fotografías, **una por cada valor ISO** que tenga tu
    cámara, asegurándote de **no exceder un tiempo de exposición de 1
    segundo**. A modo de ejemplo, podrías generar 8 fotos para ISO 100,
    200, 400, 800, 1600, 3200, 6400 y 12800. La mayor parte de cámaras
    incluyen valores ISO intermedios, como ISO 160, o ISO 320, por lo
    que si quieres mejorar la precisión del *nivel de blanco*, tendrás
    que fotografiar también estos valores intermedios.
2.  Si tu cámara tiene *Reducción de Ruido en Larga Exposición*,
    **actívala**. Toma una segunda serie de fotos, como se ha descrito
    en el punto anterior, pero esta vez **asegúrate que el tiempo de
    exposición en todos los casos es de al menos 2 segundos**, no menos.
    Siguiendo el ejemplo anterior, ésto generará otras 8 o más fotos. En
    la mayoría de los casos estos dos grupos deberían ser suficientes.
3.  Algunas cámaras escalan los valores raw para aperturas más grandes
    (valores *f/* más bajos), particularmente algunos modelos de Canon y
    Nikon. La única manera de saber con toda seguridad si tu cámara hace
    ésto es tomar una foto y medirla. Saca una foto como se ha descrito
    anteriormente, pero **usando la máxima apertura de tu objetivo**,
    por ejemplo f/1.7 a ISO100 **con la Reducción de Ruido en Larga
    Exposición desactivada** y envíanosla junto con el resto de fotos.  
      
    Si detectamos que hay escalado raw (o si tú mismo lo detectas, si
    haces tu propias mediciones), te pediremos que hagas una serie de
    fotos extra usando un tiempo de exposición de menos de 1 segundo,
    desde la máxima apertura que tenga tu lente en saltos de 1/3 de
    paso, hasta llegar a una apertura donde ya no se haga escalado raw.
    Esto puede significar tener que hacer muchas fotos. El manejo del
    escalado raw provocado por las aperturas grandes no es muy
    importante, así que no te preocupes demasiado: no es imprescindible
    hacerlo incluso si tu cámara realmente hace escalado raw, pero si
    dispones del tiempo, será mejor comprobarlo.

Como se ha indicado en el punto 1, el mínimo imprescindible será una
serie de unas 8 fotos, aunque te recomendamos que también tomes las
fotos del punto 2, con lo que obtendrás 16 o más fotos, más la foto de
la prueba de escalado raw del punto 3.

Si encontramos que tu cámara hace escalado raw, podrías además tomar las
series necesarias descritas en el punto 3, pero como esto puede
significar un gran número de fotos (más de 50), no es probable que las
hagas.

Comprime todas estas fotos, súbelas a un servicio de alojamiento de
archivos (como [filebin.net](http://filebin.net)) y envíanos el enlace
completo, ya sea a nuestra página de [cuestiones de
GitHub](https://github.com/Beep6581/RawTherapee/issues/new), o bien al
[foro de RawTherapee](https://discuss.pixls.us/c/software/rawtherapee).

Por último: las fotos totalmente recortadas (sólo hay píxeles
completamente blancos) pueden alcanzar tasas de compresión asombrosas,
no olvides comprimirlas (con *7-Zip*, *ZIP*, *bzip2* o cualquier otro)
antes de subirlas. Como ejemplo, 10 imágenes raw de una cámara Sony 7M2,
completamente recortadas, con la *Reducción de Ruido en Larga
Exposición* desactivada, ocupan 234 MB, pero si las comprimes con ZIP,
obtendrás un archivo de 1 MB.

### Renombrado de las fotos

A fin de simplificar el trabajo con estas imágenes de *toma en blanco*,
los nombres de archivo deberían distinguir las fotos por **Reducción de
Ruido en Larga Exposición**, **apertura** e **ISO**.

La utilidad ***ExifTool*** puede renombrarlas automáticamente:

`exiftool '-FileName<${marca}_${modelo}_${ReducciónRuidoEnLargaExposicion}_${apertura}_${iso}%-c.%le' dir`

## Recorte raw

El recorte raw se puede determinar a partir de cualquier fotografía; no
se necesitan fotos adicionales.

Consiste en averiguar los tamaños de la área activa y la área total del
sensor, que siempre es un poco mayor que la área activa. Los fotodiodos
adicionales que no se incluyen en la foto sirven para facilitar el
desentramado en los bordes de la imagen, de modo que no se generen
artefactos.

## Perfil de entrada

Para cada modelo de cámara se necesita un *perfil de entrada* para poder
reproducir los colores de la escena con exactitud.

Puedes leer el ''[capítulo sobre los perfiles de
entrada](Color_Management/es#El_perfil_de_entrada.md) para saber
más sobre éstos perfiles y leer los artículos "[Cómo crear perfiles de
color ICC](How_to_create_ICC_color_profiles/es.md)" y "[Cómo
crear perfiles de color
DCP](How_to_create_DCP_color_profiles/es.md)" para saber cómo
hacer las tomas de una carta de color que nos permitan crear un perfil
de color para tu modelo de cámara.
