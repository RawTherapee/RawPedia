---
title: Edit Current Image in External Editor
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Edición de la imagen actual en un programa externo

</div>
<div class="headline">

Cómo enviar la imagen a otro programa para ver el resultado final o
seguir procesándola.

</div>

Esta función hace que RawTherapee revele completamente la imagen actual
y la abra inmediatamente en el programa externo que hayas establecido
(*[Preferencias \> General \> Editor
externo](Preferences/es#External_Editor.md)*).

Puedes usar esta característica para enviar fácilmente la imagen a un
editor de imágenes (como GIMP, o Photoshop) y seguir procesándola, o
para enviarla a un visor de imágenes, de modo que con un solo clic del
ratón puedas ver la imagen final en alta calidad.

El botón para enviar la imagen a una aplicación externa
![<File:palette-brush.png>](palette-brush.png "File:palette-brush.png")
está situado en la parte inferior izquierda de la ventana de
previsualización. Una vez que hagas clic en él, RawTherapee exportará tu
imagen como un archivo TIFF, codificado en números enteros de 16 bits y
aplicándole el [*perfil de
salida*](Color_Management/es#Los_cinco_tipos_de_perfiles_de_color_y_la_interfaz_del_programa.md),
guardándola en la [*carpeta
temporal*](File_Paths/es#Carpeta_Temporl.md).

Estos archivos temporales, debido a que están fuera del control de
RawTherapee, ***no se borran automáticamente*** cuando cierres el
programa, por lo que debes tener esto en cuenta y eliminarlos
manualmente.

Además, debes tener en cuenta que GIMP v.2.8 o inferior no puede editar
imágenes de *16 bits* (por lo que las convertirá a la baja a *8 bits*) y
tampoco reconoce los datos Exif de los archivos TIFF. Esto es una
limitación de GIMP, no de RawTherapee. GIMP v.2.9 o superior edita
imágenes de gran profundidad de bits (hasta *64 bits* por canal),
reconoce todos los metadatos y es bastante estable, por lo que es
aconsejable que [obtengas GIMP v.2.9 o
superior](http://www.gimp.org/downloads).
