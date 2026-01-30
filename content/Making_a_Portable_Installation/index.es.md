---
title: Making a Portable Installation
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Cómo hacer una instalación portátil

</div>
<div class="headline">

RawTherapee y su carpeta de caché pueden funcionar de forma
independiente en cualquier dispositivo de almacenamiento masivo

</div>

## En Windows

Obtén la última versión de RawTherapee: como vas a hacerla *portátil*
(que no tenga que estar instalada en una carpeta concreta), no querrás
el archivo instalable, sólo el programa tal cual (comprimido).

Si la última versión en [la página web de
RawTherapee](http://www.rawtherapee.com/) está en formato simple
comprimido, sin un instalador, puedes saltarte el siguiente paso.

Si es un instalable tendrás que extraer primero los archivos de
RawTherapee:

- Si se trata de un instalable *Inno Setup* (con extensión `.exe`),
  obtén [innounp](http://innounp.sourceforge.net/) o
  [innoextract](http://constexpr.org/innoextract/) para desempaquetarlo.
- Si se trata de un instalable *MSI*, abre una ventana de línea de
  órdenes y escribe:

  
    msiexec /a RawTherapee.msi TARGETDIR="C:\TargetDir" /qb

Cambia el nombre del instalable *MSI* y la carpeta de destino según
convenga. Se permiten espacios en la carpeta `TargetDir`, ya que el
nombre está encerrado entre comillas.

Una vez tienes los archivos descomprimidos, por ejemplo en
`E:\RawTherapee` (donde `E:\` es la letra de unidad de tu dispositivo de
memoria flash USB, o donde sea que quieras situar el programa), abre el
archivo **`E:\RawTherapee\options`**, cambia la opción **`MultiUser`** a
**`false`** y guarda los cambios.

A partir de aquí, cuando ejecutes RawTherapee, este almacenará el caché
y los ajustes en subcarpetas relativas al ejecutable llamadas
**`mycache`** and **`mysettings`**, respectivamente (en el ejemplo, en
*`E:\RawTherapee\mycache`* y *`E:\RawTherapee\mysettings`*).

Consulta también la página [Carpetas usadas por
RawTherapee](File_Paths/es.md) sobre cómo establecer una
ubicación diferente para estas dos carpetas.

Cuando actualices RawTherapee, es recomendable que descomprimas la nueva
versión en una nueva carpeta y simplemente muevas *`mycache`* y
*`mysettings`* a esa carpeta.

## En Linux

Hacer que RawTherapee funcione en un medio portátil como un dispositivo
flash USB en varios ordenadores con Linux no es sencillo, debido a la
propia naturaleza de los sistemas Linux: mientras que la versión para
Windows de RawTherapee incorpora todas las librerías necesarias para
ejecutarse en cualquier versión de Windows, las distribuciones de Linux
difieren significativamente entre sí y como resultado, es poco probable
que una versión de RawTherapee compilada para una distribución
determinada funcione en otra diferente.

Una forma de evitar esto es usar una ***AppImage***: se trata de un
único archivo que contiene el ejecutable de RawTherapee junto con todos
los archivos necesarios para que se ejecute en cualquier distribución de
Linux.

Descárgala, hazla ejecutable y lánzala.

Independientemente de si usas la *AppImage* o una versión de RawTherapee
obtenida del gestor de paquetes de tu distribución, seguramente querrás
poder tener a disposición tu configuración y tus perfiles de
procesamiento de RawTherapee: para hacer una copia de seguridad de tu
configuración, copiarás la carpeta ***config*** de RawTherapee en tu
lápiz USB. Específicamente, tienes que copiar el archivo ***options***,
tu archivo ***camconst.json*** personalizado (si has creado uno) y
cualquier perfil personalizado de los tipos *PP3*, *ICC*, *DCP* y *LCP*.

El artículo [*Carpetas usadas por
RawTherapee*](File_Paths/es.md) describe dónde encontrarlos.
