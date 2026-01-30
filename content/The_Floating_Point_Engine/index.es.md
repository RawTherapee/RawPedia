---
title: The Floating Point Engine
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

El Motor de Coma Flotante

</div>
<div class="headline">

El corazón de RawTherapee y la precisión de sus cálculos

</div>

## Los cálculos en 32-bits con decimales

RawTherapee realiza todos los cálculos en 32-bits con precisión de [coma
flotante](https://es.wikipedia.org/wiki/Coma_flotante). Esto significa
que pueden haber hasta 9 decimales con precisión exacta, o más con una
precisión menor.

Los conversores clásicos trabajan con números enteros de 16-bits: cada
canal de un pixel tiene valores entre 0 y 65535 (para aumentar la
precisión, los conversores normalmente multiplican los valores raw de 12
ó 14-bits por un factor para ajustarlos a los 16-bits). En este caso los
números no tienen decimales, así que por ejemplo no existe ningún valor
entre 102 y 103.

Por el contrario los números en coma flotante tienen valores entre los
números enteros, lo cual ayuda especialmente en las luces: permite que
hayan valores decimales en la cadena de procesado y que no se pierda
información. Por esto mismo los valores decimales ayudan a suavizar los
degradados de color y prevenir las bandas de color ([el
posterizado](https://es.wikipedia.org/wiki/Posterización)).

La desventaja es la cantidad de memoria RAM que requieren los números en
coma flotante, que es exactamente el doble que la de los números
enteros. Esto, unido al constante incremento de los megapíxeles de los
sensores digitales, fácilmente puede agotar la cantidad de memoria libre
de un sistema operativo de 32-bits y causar el bloqueo de RawTherapee.
Por ello y para garantizar la estabilidad sólo se publican versiones
para sistemas operativos de 64-bits.

Si aún así necesitas usar una versión antigua de RawTherapee en un
sistema de 32-bits, a continuación tienes algunos consejos:

- ajusta el reparto de los 4 Gigabytes de memoria en Windows. Puedes
  leer *[«4-Gigabyte Tuning: BCDEdit and
  Boot.ini»](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)*
  (en inglés) para ver una explicación del problema. Y puedes descubrir
  cómo ponerlo en práctica leyendo *[«How to set the /3GB Startup Switch
  in Windows XP and
  Vista»](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)*
  (en inglés)
- cierra todos los programas cuando trabajes con RawTherapee
- utiliza el *[Editor de Pestaña
  Única](Preferencias#Distribución.md)*
- desactiva el inicio automático en la *[Cola](queue/es)*,
  añade las fotos a la cola como de costumbre y cuando estés listo para
  empezar a procesarlas, reinicia RawTherapee para liberar memoria (no
  habrá ninguna imagen abierta en el Editor). Entonces arranca el
  procesamiento de la *Cola*.
- asegúrate que RawTherapee [no carga imágenes de campo oscuro o de
  campo plano](Preferences/es#Directorios.md) si no las vas a
  usar
- evita tener más de algunos cientos de fotos en cada carpeta, ya que
  cada foto necesita un poco de memoria (miniatura, perfil ICC
  incrustado, etc).

## Necesidades de Memoria

Simplemente para abrir una imagen en el *Editor*, RawTherapee necesita
aproximadamente esta cantidad de memoria, en bytes:

- Imagen **NO-raw**
  - 8-bit:
    `(ancho * alto * 3) + (ancho * alto * 4) + (Ancho_de_vista_previa * Alto_de_vista_previa * 28)`
  - 16-bit:
    `(ancho * alto * 3 * 2) + (ancho * alto * 4) + (Ancho_de_vista_previa * Alto_de_vista_previa * 28)`
  - 32-bit:
    `(ancho * alto * 3 * 4) + (ancho * alto * 4) + (Ancho_de_vista_previa * Alto_de_vista_previa * 28)`
- **Raw**
  - `(ancho * alto * 4 * 2) + (ancho * alto * 12) + (Ancho_de_vista_previa * Alto_de_vista_previa * 28)`

Además se necesita algo de memoria extra, por ejemplo para generar las
miniaturas de otras imágenes existentes en la carpeta de la imagen
abierta.

La memoria necesaria para procesar y guardar una imagen depende de las
herramientas que uses y puede ser bastante diferente a lo indicado
antes, que solo es para abrir la imagen.

Por ejemplo: una foto raw de *2608x3892* píxeles mostrada en una vista
previa de *1304x973* píxeles consumirá unos *227 MBytes* de memoria nada
más abrirla en el *Editor*.

Como [regla
mnemotécnica](https://es.wikipedia.org/wiki/Regla_mnemotécnica): ***cada
salto duplica la cantidad de memoria necesaria***.

    Memoria para fotos raw = 2 * memoria fotos 32-bit = 4 * memoria fotos 16-bit = 8 * memoria fotos 8-bit
