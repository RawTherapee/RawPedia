---
title: Command-Line Options
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Parámetros de línea de órdenes

</div>
<div class="headline">

Las diferentes tareas que se pueden realizar dede la línea de comandos

</div>

## Las diferentes opciones

En RawTherapee la ***línea de comandos**'' (o***línea de órdenes**'') es
un instrumento muy potente para realizar determinadas acciones, siendo
en muchas ocasiones incluso más rápido que realizarlas en la interfaz
gráfica.

Desde la línea de comandos podremos:

- arrancar la interfaz gŕafica
- ejecutar el programa en modo texto, especificando una serie de
  opciones según la tarea a realizar
- enviar el resultado del trabajo realizado por RawTherapee a un fichero
  de texto

### Convenciones tipográficas utilizadas

A lo largo del documento se mostrarán ejemplos de código que incluirán:

- **`<`**` paréntesis en ángulo `**`>`** : indican los parámetros que
  puedes cambiar
- **`[`**` corchetes `**`]`** : significan que el parámetro no es
  obligatorio
- la *pleca* (*pipe*, en inglés) **`|`** : indica la elección de un
  valor o el otro
- el guión **`-`** : denota un rango de valores posibles, desde un valor
  hasta el otro

### Arrancar la interfaz gráfica de RawTherapee

Desde el propio terminal podemos arrancar interfaz gráfica y además
especificar algunos parámetros:

- **`rawtherapee -h`** o **`rawtherapee -?`** : muestra las opciones de
  línea de órdenes disponibles, sin lanzar el programa. En el terminal
  verás este resultado (en este caso en Linux; siempre en inglés):

<!-- -->

    An advanced, cross-platform program for developing raw photos.

      Website: http://www.rawtherapee.com/
      Documentation: http://rawpedia.rawtherapee.com/
      Forum: https://discuss.pixls.us/c/software/rawtherapee
      Code and bug reports: https://github.com/Beep6581/RawTherapee

    Symbols:
      <Chevrons> indicate parameters you can change.

    Usage:
      rawtherapee <folder>           Start File Browser inside folder.
      rawtherapee <file>             Start Image Editor with file.


    Options:
      -v Print RawTherapee version number and exit
      -R Raise an already running RawTherapee instance (if available)
      -h -? Display this help message

- **`rawtherapee -v`** : muestra el número de versión de RawTherapee,
  sin arrancar el programa

<!-- -->

    RawTherapee, version 5.9

- **`rawtherapee -R`** : puedes arrancar el programa con o sin esta
  opción, o también puedes abrir una imagen usando la orden *Abrir con*
  de tu sistema operativo, o pasando como un parámetro el nombre de un
  archivo. Los resultados en uno u otro caso son:
  - si no usas la opción `-R`, RawTherapee se abrirá en el modo **sin
    Explorador de archivos**: este modo carece de las pestañas
    *Explorador de archivos* y *Cola*, así como de los botones *Modo de
    pantalla completa*, *Preferencias*, *Ayuda* y *Generador de perfiles
    ICC*. Su existencia se debe a razones históricas, cuando las
    necesidades de memoria RAM eran mayores y el programa era menos
    estable. Pero ahora que el uso de memoria de RawTherapee está
    optimizado y puede abrir de forma rápida y fiable carpetas con miles
    de imágenes, lo normal es que decidas usar siempre el modo `-R`
  - si usas el nuevo modo `-R`, RawTherapee se abrirá con todas las
    pestañas y opciones a tu disposición
  - si usas el modo `-R` mientras RawTherapee se está ejecutando, si el
    programa también se arrancó usando `-R`, entonces simplemente
    abrirás la imagen en el programa, sin arrancarlo de nuevo

<!-- -->

- **`rawtherapee -w`** : no abre el *Símbolo del Sistema* de Windows (el
  *Command-prompt*). En este sistema operativo, si pasas parámetros al
  ejecutable de RawTherapee, éste abre una ventana de *consola*, para
  que puedas ver información detallada de tu procesamiento. Tras cerrar
  RawTherapee, Windows intenta cerrar la consola inmediatamente después
  y para que puedas estudiar dicha información, existe un estado de
  espera que mantiene abierta la consola hasta que pulses una tecla.
  **Si añades `-w` no se abrirá la consola** y por tanto no se
  necesitará pulsar ninguna tecla. Esto es útil si deseas invocar
  `rawtherapee.exe` en un proceso por lotes, es decir, desde un guión de
  *PowerShell*. Ten en cuenta que `-w` no tendrá efecto en versiones de
  depuración (*debug*), en las que siempre se abrirá una consola salvo
  que arranques RawTherapee desde la propia línea de comandos

<!-- -->

- **`rawtherapee `<carpeta seleccionada>** : inicia el programa con el
  [Explorador de archivos](the_file_browser_tab/es) abierto
  dentro de la carpeta seleccionada

<!-- -->

- **`rawtherapee `<archivo>** : inicia el programa con el
  [Editor](the_image_editor_tab/es) abierto con el archivo
  indicado

### Trabajar con RawTherapee en la línea de órdenes

Podemos revelar fotos con RawTherapee sin arrancar la interfaz gráfica:
esto lo conseguimos mediante el ejecutable `rawtherapee-cli`.

El resultado de lanzar **`rawtherapee-cli -h`** es:

    RawTherapee, version 5.9, command line.
      An advanced, cross-platform program for developing raw photos.

      Website: http://www.rawtherapee.com/
      Documentation: http://rawpedia.rawtherapee.com/
      Forum: https://discuss.pixls.us/c/software/rawtherapee
      Code and bug reports: https://github.com/Beep6581/RawTherapee

    Symbols:
      <Chevrons> indicate parameters you can change.
      [Square brackets] mean the parameter is optional.
      The pipe symbol | indicates a choice of one or the other.
      The dash symbol - denotes a range of possible values from one to the other.

    Usage:
      rawtherapee-cli -c <dir>|<files>   Convert files in batch with default parameters.
      rawtherapee-cli <other options> -c <dir>|<files>   Convert files in batch with your own settings.

    Options:
      rawtherapee-cli[-o <output>|-O <output>] [-q] [-a] [-s|-S] [-p <one.pp3> [-p <two.pp3> ...] ] [-d] [ -j[1-100] -js<1-3> | -t[z] -b<8|16|16f|32> | -n -b<8|16> ] [-Y] [-f] -c <input>

      -c <files>       Specify one or more input files or folders.
                       When specifying folders, Rawtherapee will look for image file types which comply
                       with the selected extensions (see also '-a').
                       -c must be the last option.
      -o <file>|<dir>  Set output file or folder.
                       Saves output file alongside input file if -o is not specified.
      -O <file>|<dir>  Set output file or folder and copy pp3 file into it.
                       Saves output file alongside input file if -O is not specified.
      -q               Quick-start mode. Does not load cached files to speedup start time.
      -a               Process all supported image file types when specifying a folder, even those
                       not currently selected in Preferences > File Browser > Parsed Extensions.
      -s               Use the existing sidecar file to build the processing parameters,
                       e.g. for photo.raw there should be a photo.raw.pp3 file in the same folder.
                       If the sidecar file does not exist, neutral values will be used.
      -S               Like -s but skip if the sidecar file does not exist.
      -p <file.pp3>    Specify processing profile to be used for all conversions.
                       You can specify as many sets of "-p <file.pp3>" options as you like,
                       each will be built on top of the previous one, as explained below.
      -d               Use the default raw or non-raw processing profile as set in
                       Preferences > Image Processing > Default Processing Profile
      -j[1-100]        Specify output to be JPEG (default, if -t and -n are not set).
                       Optionally, specify compression 1-100 (default value: 92).
      -js<1-3>         Specify the JPEG chroma subsampling parameter, where:
                       1 = Best compression:   2x2, 1x1, 1x1 (4:2:0)
                           Chroma halved vertically and horizontally.
                       2 = Balanced (default): 2x1, 1x1, 1x1 (4:2:2)
                           Chroma halved horizontally.
                       3 = Best quality:       1x1, 1x1, 1x1 (4:4:4)
                           No chroma subsampling.
      -b<8|16|16f|32>  Specify bit depth per channel.
                       8   = 8-bit integer.  Applies to JPEG, PNG and TIFF. Default for JPEG and PNG.
                       16  = 16-bit integer. Applies to TIFF and PNG. Default for TIFF.
                       16f = 16-bit float.   Applies to TIFF.
                       32  = 32-bit float.   Applies to TIFF.
      -t[z]            Specify output to be TIFF.
                       Uncompressed by default, or deflate compression with 'z'.
      -n               Specify output to be compressed PNG.
                       Compression is hard-coded to PNG_FILTER_PAETH, Z_RLE.
      -Y               Overwrite output if present.
      -f               Use the custom fast-export processing pipeline.

    Your pp3 files can be incomplete, RawTherapee will build the final values as follows:
      1- A new processing profile is created using neutral values,
      2- If the "-d" option is set, the values are overridden by those found in
         the default raw or non-raw processing profile.
      3- If one or more "-p" options are set, the values are overridden by those
         found in these processing profiles.
      4- If the "-s" or "-S" options are set, the values are finally overridden by those
         found in the sidecar files.
      The processing profiles are processed in the order specified on the command line.

Además, como en el punto anterior, para Windows existe otra opción más:
**`rawtherapee-cli -w`** que realiza la misma función ya explicada en el
punto anterior.

En general el programa lo lanzarás con esta estructura:

'''<code>rawtherapee-cli <opciones> -c

<dir>

\|<archivos></code>'''

Si no especificas parámetros (*<opciones>*), entonces el programa usará
los valores por defecto que tiene en su código, pero siempre tendrás que
incluir los directorios (''

<dir>

*) o archivos (*<archivos>'') que quieres procesar.

Y el listado completo de opciones es:

**`rawtherapee-cli [-o `<salida>`|-O `<salida>`] [-q] [-a] [-s|-S] [-p `<archivos>`] [-d] [-j[1-100] [-js<1-3>]|[-b<8|16|16f|32>] <[-t[z] | [-n]]] [-Y] [-f] -c `<entrada>**

En esta plantilla `salida` y `entrada` se refieren a un listado de
archivos o de subdirectorios.

- **`-c `<entrada>** : **esta opción siempre debe ser la última**, es
  imprescindible y especifica uno o más archivos o carpetas que se
  tienen que procesar  
  Si especificas *carpetas*, RawTherapee buscará en ellas imágenes que
  tengan alguna de las extensiones de archivo activadas en
  *[Preferencias\>Explorador de Archivos\>Extensiones de archivo
  decodificadas](Preferences/es#Extensiones_de_archivo_decodificadas.md)*.  
  Esta opción puede verse modificada por la opción **`-a`**
- **`-o `<salida>** : selecciona el archivo o carpeta de salida. En el
  caso de que no incluyas esta opción, RawTherapee guarda el archivo de
  salida junto con el archivo de entrada
- **`-O `<salida>** : igual que la opción anterior, si incluyes la
  opción estableces el archivo o carpeta de salida y si no la incluyes
  la imagen de salida se guarda junto a la de entrada, pero esta vez
  además copia el archivo PP3 junto a la imagen procesada
- **`-q`** : esta opción activa el modo de arranque rápido (no carga los
  archivos de la caché para acelerar el arranque)
- **`-a`** : modifica la opción `-c` y procesa todos los tipos de
  archivo de imagen soportados por RawTherapee que haya en la carpeta
  especificada, *incluso los que no estén seleccionados en
  [Preferencias\>Explorador de Archivos\>Extensiones de archivo
  decodificadas](Preferences/es#Extensiones_de_archivo_decodificadas.md)*
- **`-s`** : usa el archivo de perfil de procesamiento (*pp3*) existente
  para ajustar los parámetros de procesamiento. Por ejemplo, para
  **foto.raw**, usará el perfil **foto.raw.pp3** de la misma carpeta. Si
  el archivo **pp3** no existe, se utilizarán los valores del perfil de
  procesamiento **Neutral**
- **`-S`** : igual que `-s`, pero la imagen no se procesa si el archivo
  de perfil de procesamiento no existe
- **`-p <archivo.pp3>`** : especifica el perfil de procesamiento a
  utilizar en todas las conversiones. Puedes especificar tantas opciones
  `-p <archivo.pp3>` como quieras, una tras otra. Cada una de ellas se
  acumulará sobre la anterior (como se explica al final de esta lista)
- **`-d`** : usa el archivo **pp3** (para imágenes raw o no-raw)
  indicado en *[Preferencias\>Procesamiento de imágenes\>Perfiles de
  procesamiento
  predeterminados](Preferences/es#Perfiles_de_procesamiento_predeterminados.md)*
- **`-j[1-100]`** : especifica que la salida estará en formato JPEG
  (formato de imagen por defecto, si no se han indicado `-t` ni `-n`).
  Opcionalmente puedes especificar el nivel de compresión entre 1 y 100
  (valor por defecto: **92**).
- **`-js<1-3>`** : especifica el parámetro [submuestreo de
  crominancia](https://es.wikipedia.org/wiki/Submuestreo_de_crominancia)
  de la imagen JPEG, donde:
  - 1 = Máxima compresión: 2x2, 1x1, 1x1 *(**4:2:0**)*  
    Crominancia reducida a la mitad vertical y horizontalmente
  - 2 = Equilibrado: 2x1, 1x1, 1x1 *(**4:2:2**)*  
    Crominancia reducida a la mitad horizontalmente
  - 3 = Máxima calidad: 1x1, 1x1, 1x1 *(**4:4:4**)*  
    Sin submuestreo de crominancia
- **`-b<8|16|16f|32>`** : especifica la profundidad de bits por canal  
  Por defecto serán **8 bits por canal** en imágenes JPEG y PNG.  
  Por defecto serán **16 bits con números enteros** para imágenes
  TIFF.  
  Puedes escoger entre *8 bits*, *16 bits con números enteros*, *16 bits
  con números en coma flotante* y *32 bits con números en coma
  flotante.*  
  En imágenes JPEG siempre serán *8 bits por canal*. *16 bits con
  números enteros* se aplicarán a imágenes PNG y TIFF. Las
  codificaciones con *números en coma flotante* sólo se aplicarán a
  imágenes TIFF
- **`-t[z]`** : especifica que la salida sea TIFF sin compresión, a no
  ser que se especifique `tz`, que forzará la compresión ZIP
- **`-n`** : especifica que la salida sea PNG comprimido (la compresión
  será siempre: *PNG_FILTER_PAETH, Z_RLE*)
- **`-Y`** : sobrescribe el fichero de salida, si ya existe uno con el
  mismo nombre
- **`-f`** : usa el *circuito de revelado de exportación rápida*
  personalizada.

Si tus archivos PP3 estan incompletos, RawTherapee establecerá el resto
de valores como sigue:

1.  Se crea un nuevo perfil de procesamiento, usando valores neutros,
2.  Si se usa la opción `-d`, los valores se substituyen por los que
    contengan los *perfiles de procesamiento por omisión* de archivos
    raw o no-raw (según el caso),
3.  Si se usa una o más opciones `-p`, los valores se sustituyen por los
    que tengan estos perfiles de procesamiento *(los perfiles de
    procesamiento se procesan en el orden especificado en la línea de
    comandos)*,
4.  Si se usan las opciones `-s` o `-S`, los valores se sustituyen
    finalmente por los que contengan los archivos de perfil de
    procesamiento.

### Redirección del informe de actividad

Como ya se ha dicho, RawTherapee va mostrando en la consola las
operaciones que va realizando. Si quisieras tener todo este informe en
un archivo de texto para revisarlo tranquilamente, debes iniciar el
programa añadiendo la redirección como sigue:

- en **Windows**:

**`rawtherapee.exe > rtlog.txt 2>&1`**

- en **Linux**:  
  **`rawtherapee &> rtlog.txt`**

## Ejemplos

### Ejemplo 1

En Linux:

- procesas un fichero individual que reside en **/tmp** y se llama
  **foto.raw**
- usas su archivo de perfil de procesamiento **foto.raw.pp3** durante la
  conversión
- lo guardas en la misma carpeta que **foo.tif**
- y sobreescribes el archivo *foo.tif*', si existe

**`rawtherapee-cli -o /tmp/foo.tif -s -t -Y -c /tmp/photo.raw`**

### Ejemplo 2

En el siguiente ejemplo:

- quieres procesar rápidamente todas tus fotos raw en la carpeta
  **/tmp/jane01**
- quieres enviar la salida a una subcarpeta web
- quieres usar como base el perfil por omisión
- quieres usar el archivo de perfil de procesamiento si existe, pero
  eliminando algunas etiquetas *Exif* (por ejemplo, el número de serie
  de la cámara) y añadiendo algunas etiquetas IPTC (como tus parámetros
  habituales de copyright)
- y además quieres cambiar el tamaño y enfocar la imagen para la web

**`rawtherapee-cli -o /tmp/Jane01/web -p ~/profiles/iptc.pp3 -s -p ~/profiles/exif.pp3 -p ~/profiles/web.pp3 -t -Y -d -c /tmp/Jane01/`**

El perfil de procesamiento se va modificando como sigue:

1.  se crea un nuevo perfil de procesamiento, usando los valores
    neutros,
2.  que luego se substituyen por los valores del perfil raw por omisión
    (`-d`),
3.  que luego se substituyen por los valores de **iptc.pp3**,
4.  que luego se substituyen por los valores del archivo de perfil de
    procesamiento (`-s`) si existe (para que puedas forzar algunas
    etiquetas *IPTC*, aunque ya se hayan establecido con *iptc.pp3*),
5.  que luego se substituyen por los valores de **exif.pp3** (para que
    puedas forzar que el perfil borre algunas etiquetas),
6.  que luego se substituyen por los valores de **web.pp3**, para
    cambiar el tamaño, enfocar la imagen y asegurarte que el espacio de
    color de salida es *sRGB*.

Como puedes ver, la posición del parámetro `-s` indica cuándo cargar el
archivo de perfil de procesamiento en relación a otros parámetros `-p`.
Este no es el caso del parámetro `-d`.

### Ejemplo 3

En Linux, quieres ver cuánto tarda en procesarse cada archivo raw en una
carpeta, asumiendo que cada foto raw tiene su perfil de procesamiento
correspondiente y descartando cada archivo de salida:

    time {
      for f in /home/NombreDeUsuario/Fotos/2020-11-11/*.raw;
        do rawtherapee-cli -o /dev/null -S -t -Y -c "$f";
      done
      }
