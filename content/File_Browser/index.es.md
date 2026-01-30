---
title: File Browser
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

El Navegador de Archivos

</div>
<div class="headline">

En esta pestaña es donde revisas tus fotos, seleccionas las que quieres
editar, o editas un grupo de fotos todas a la vez.

</div>

## La ventana del Navegador de Archivos

\[\[<File:Rt_setm_fb.png%7Cthumb%7C1280px%7Cnone%7CRawTherapee> en el
**modo Editor de Pestaña Única - Pestañas Verticales**, mostrando:  

<div class="captions_indent">

**1- Secciones principales:** Explorador de archivos (abierto en esta
captura de pantalla), Cola de lotes, Editor, Barra de progreso,
Generador de Perfiles ICC, Ayuda y Preferencias.  
**2- Paneles** utilizados para navegar por los archivos y las
carpetas.  
**3- Miniaturas** de la carpeta actualmente abierta.  
**4- Filtros** para mostrar únicamente las miniaturas que coincidan con
determinados metadatos o estados de los archivos.  
**5- Botones para aumentar o disminuir el tamaño de las miniaturas**
(Zoom) y para mostrar/ocultar información en las miniaturas.  
**6- Operaciones rápidas** sobre la imagen.  
**7- Sub-pestañas del Explorador de Archivos:** ***Filtro*** (abierto en
esta captura de pantalla), ***Inspeccionar*** (para ver una vista previa
de tamaño completo de una imagen JPEG, o en su caso de la imagen JPEG
incrustada en un archivo raw), ***Editar por lotes*** (para aplicar
algún cambio a todas las imágenes seleccionadas) y ***Exportación
rápida*** (de baja calidad y evita algunas herramientas, pero escribe en
disco rápidamente - ¡no lo uses para la exportación final!).  
**8- Menú contextual** al hacer clic con el botón derecho del ratón
(normalmente lo usarás para aplicar algún perfil de procesamiento a
todos los archivos seleccionados)

</div>

\]\]

Consta de las siguientes zonas o ***paneles***:

- **El panel izquierdo**:
  - en su parte superior verás las ***Ubicaciones***, donde hay enlaces
    a tu carpeta personal, a los lectores USB, a la carpeta para *fotos*
    por defecto del sistema y a carpetas que hayas seleccionado y
    añadido
  - en la parte inferior verás un típico navegador en árbol, que puedes
    usar para llegar hasta las carpetas donde guardas tus fotos:
    RawTherapee no te exige que importes las imágenes en una base de
    datos
- **El panel derecho**:
  - la pestaña ***Filtro*** te permite especificar unos parámetros para
    que veas únicamente las fotos que los cumplan
  - la pestaña ***Inspeccionar*** muestra una vista previa a escala real
    (con el *zoom* al 100%) de la imagen sobre la que tengas el cursor.
    La vista previa mostrará la imagen JPEG más grande incorporada en el
    fichero raw, o la propia imagen si el cursor está sobre una foto que
    no sea raw
  - la pestaña ***Revelar*** te permite procesar todas las imagenes
    seleccionadas con las herramientas del *Editor de Imágenes*. Gracias
    a esto podrás aplicar el efecto de una herramienta rápidamente a
    varias fotos a la vez
  - la pestaña de ***Exportación Rápida*** te permite procesar
    rápidamente las fotos seleccionadas, pero sin aplicar determinadas
    herramientas aunque estén activadas en el perfil de procesado de
    esas imágenes. De esta forma puedes conseguir una vista previa
    rápida de las imágenes raw, por ejemplo para eliminar las fotos
    borrosas o desenfocadas.
- **El panel central**: muestra las miniaturas de la carpeta actualmente
  abierta.

### Cómo ocultar los paneles

Puedes ocultar los paneles laterales mediante los botones
*Mostrar/Ocultar el panel izquierdo*
![<File:Panel-to-left.png>](Panel-to-left.png "File:Panel-to-left.png")
y *Mostrar/Ocultar el panel derecho*
![<File:Panel-to-right.png>](Panel-to-right.png "File:Panel-to-right.png")
(échale un vistazo a la página [Atajos de
Teclado](Keyboard_Shortcuts/es.md) para ver estos y otros
atajos).

### Trabajar con las miniaturas de las fotos

Cuando abres una carpeta, RawTherapee genera las miniaturas de las fotos
que haya, las guarda en la
[caché](https://es.wikipedia.org/wiki/Caché_(informática)) y las muestra
en el panel central.

La primera vez que abres una carpeta con fotos raw, RawTherapee leerá
cada archivo y generará una miniatura basada en la imagen JPEG
incrustada. Esto implica que puede tardar un poco en mostrar todas las
miniaturas si hay cientos de fotos, pero solo ocurre la primera vez que
abres la carpeta. A partir de entonces, cada vez que vuelvas a esa
carpeta, RawTherapee leerá las miniaturas de su caché (si existe), por
lo que será mucho más rápido al mostrar las miniaturas.

Todas las fotos raw tienen una imagen JPEG incrustada, e incluso hay
imágenes raw que tienen varias imágenes JPEG de distintos tamaños.
Además, estas imágenes incrustadas son idénticas a las que obtendrías de
la cámara si hubieras disparado en *modo JPEG*, o en *modo RAW+JPEG*.
Pero no olvides que este JPEG no es representativo de los datos
existentes en la foto raw, porque la cámara aplica todo tipo de ajustes
a los datos RAW para conseguir la imagen JPEG (como aumentar ligeramente
la exposición, retocar la saturación, el contraste, la nitidez, ...).

Desde el momento en que abres una foto en el *Editor*, la miniatura del
*Explorador de Archivos* se actualiza con la vista previa que ves en el
*Editor* y cada ajuste que realices se verá reflejado en la miniatura.
Si alguna vez quieres volver a ver en la miniatura la imagen JPEG
incrustada, haz clic con el botón derecho en la miniatura (también
funciona si tienes varias miniaturas seleccionadas) y pincha en
***Operaciones con perfiles \> Borrar perfil***.

Utiliza los iconos de *zoom* de la barra superior para aumentar o
disminuir las miniaturas, pero como cada miniatura necesita una cantidad
de memoria RAM, es recomendable que su tamaño no sea demasiado grande
(***Preferencias \> Explorador de archivos \> Altura máxima de las
miniaturas***).

### Filtrando las fotos mostradas en el panel central

Para mostrar sólo determinadas fotos puedes filtrarlas mediante los
botones de la barra superior del *Explorador de archivos*, usando la
caja de texto ***Buscar:**'' (arriba a la derecha del panel central), o
con la pestaña***Filtro**''. Se puede usar por ejemplo para:

- mostrar únicamente las imágenes que aún no se han editado,
- mostrar las imágenes con un horquillado de +2EV,
- mostrar aquellas imágenes con 5 estrellas,
- mostrar solo las fotos captadas con un rango de valores ISO
  determinados,
- mostrar solo las fotos con extensión NEF.

## Borrar Archivos

Como RawTherapee es un programa multiplataforma se ha programado con
propia papelera, independiente de la del sistema operativo.

### Cómo Usar la Papelera

Para enviar archivos a la papelera, usa el botón **Mover a la papelera**
![<File:trash-empty.png>](trash-empty.png "File:trash-empty.png") que
hay en la esquina superior derecha de cada miniatura, o también puedes
seleccionar los archivos a eliminar, hacer clic derecho sobre una
miniatura y a continuación hacer clic en ***Operaciones con archivos \>
Mover a la papelera***. Los archivos se marcarán como que están en la
papelera, pero aún no se habrán borrado del disco:

- para ocultar todos los ficheros marcados como que están en la
  papelera, haz clic en el botón **Mostrar solo las imágenes no
  borradas**
  ![<File:trash-hide-deleted.png>](trash-hide-deleted.png "File:trash-hide-deleted.png")
  de la barra superior
- para ver qué tienes en la papelera, haz clic en el botón **Mostrar el
  contenido de la papelera**
  ![<File:trash-full-show.png>](trash-full-show.png "File:trash-full-show.png")
- mientras estés viendo el contenido de la papelera, aparecerá un nuevo
  botón **Borrar definitivamente los archivos de la papelera**
  ![<File:trash-empty.png>](trash-empty.png "File:trash-empty.png") a la
  izquierda de las miniaturas (úsalo para borrar del disco todas las
  imágenes de la papelera)
- haz clic en el botón **Quitar todos los filtros**
  ![<File:filter-clear.png>](filter-clear.png "File:filter-clear.png")
  para volver a la vista previa normal

### Borrar del Disco

Para borrar archivos del disco **sin usar la papelera**, haz clic
derecho en un fichero (o una selección de ficheros) y después haz clic
en **Operaciones con archivos \> Borrar** (o en **Borrar con salida de
la cola**).

Ambas opciones borran la foto y su archivo adjunto del disco. Sin
embargo, **Borrar con salida de la cola** también borra la imagen con el
mismo nombre que se encuentre en la dirección establecida en la pestaña
de la *Cola*, en el campo ***Usar plantilla:***.
