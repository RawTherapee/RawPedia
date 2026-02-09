---
title: Download
contributors:
  - XavAL
tags:
  - 'General Information'
weight: 3
---

<div class="pagetitle">

Descarga del programa

</div>

## Versiones estables

## Compilaciones de desarrollo

Las compilaciones de desarrollo se pueden descargar desde la página
[*«Automated
Builds»*](https://github.com/Beep6581/RawTherapee/releases/tag/nightly)
de GitHub. En ésta página verás varias posibilidades, según para qué
sistema operativo y con qué tipo de CPU funcione:

- los enlaces acabados en **.AppImage** son versiones portátiles
  (*portables*) para linux
- los enlaces acabados en **.exe** son archivos de instalación
  tradicionales para Windows
- los enlaces acabados en **_win64.zip** son versiones portátiles
  (*portables*) para Windows y deberás descomprimirlos allí donde desees
  que quede el programa (por ejemplo dentro de *`c:\temp`*, o de
  *`c:\archivos de programa`*)

Como podrás observar, además de las versiones en desarrollo también
tienes los correspondientes enlaces a las versiones estables.

## ¿Cuál es la diferencia entre las compilaciones de desarrollo y las estables?

Básicamente una vez publicada la última versión estable, se solucionará
cualquier error que se encuentre y esta solución será incluída en las
nuevas versiones de desarrollo. Este proceso se realiza contínuamente y
todas las soluciones encontradas se acumularán hasta que se publique la
siguiente versión estable, unos meses más tarde.

También utilizamos estas versiones de desarrollo para mejorar
herramientas existentes y añadir otras nuevas. Sin embargo por una parte
las versiones de desarrollo tendrán el número más alto de errores
solucionados, pero por otra parte las nuevas herramientas en estas
versiones pueden ser toscas y todavía sin pulir y además aparecerán
nuevos errores.

Si quieres probar nuevas características, descárgate la última versión
de desarrollo: tendrás la ventaja de tener solucionados muchos errores
recientes y también podrás probar nuevas herramientas. Además podrás
informarnos sobre los problemas que encuentres o sobre nuevas ideas,
pero al coste de descubrir errores aún sin solucionar.

**Para un uso general recomendamos la última versión estable**, que te
proporcionará una experiencia de usuario más limpia.

## ¿Cómo leer y entender los nombres de las compilaciones de desarrollo?

El nombre de los archivos tiene esta estructura:

`RawTherapee_rama_etiqueta-consolidación-hash_fecha(_versiónWin).extensión`

- antes de resolver problemas o introducir nuevas herramientas o
  funciones al programa, las pruebas se realizan en una *rama*
  (*«branch»*). La rama principal se llama **`dev`**. Una vez el nuevo
  código hace lo que se espera de él, se incorpora (*«merge»*) en la
  rama `dev`.
- la etiqueta o *«tag»*, es el número de versión (humanamente
  inteligible) de la última versión publicada, como por ejemplo
  **`5.8`**.
- cada vez que hay un cambio aceptado por los desarrolladores, éste se
  referencia con un número de compilación y un [*hash o
  resumen*](https://es.wikipedia.org/wiki/Función_hash) único en el
  momento de consolidar o confirmar el cambio
  ([*«commit»*](https://es.wikipedia.org/wiki/Commit)). El número de
  resumen tiene este aspecto: `2629-g7d763f7` y se refiere al número de
  compilación desde la última versión estable, más el número hash de
  dicha compilación.
- la *fecha* indica qué día se realizó la compilación.
- en el caso de las versiones para windows se añade **_Win64** para
  especificar que esa compilación no funcionará en sistemas operativos
  de 32 bits (RawTherapee ya no se compila en versiones de 32 bits).
- por último la *extensión* hace referencia a las mismas extensiones
  [comentadas más arriba](#compilaciones_de_desarrollo).

Así pues, a modo de ejemplo este nombre de archivo:
`RawTherapee_dev_5.8-2625-g6f7f41237_20201028_win64.zip` se refiere a la
compilación de desarrollo de `RawTherapee` número `2625` desde la
versión estable `5.8`, con identificador único `g6f7f41237`, realizada
el día 28 de octubre de 2020 (`20201028`), para el sistema operativo
Windows de 64 bits (`_win64`). Y además se trata de una versión portátil
(`zip`).
