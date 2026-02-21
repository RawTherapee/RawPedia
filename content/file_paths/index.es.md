---
title: File Paths
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Carpetas usadas por RawTherapee

</div>

__TOC__

## Las carpetas «ocultas» del programa

RawTherapee se instala en una carpeta que depende del sistema operativo
y se ejecuta desde allí, pero para su funcionamiento habitual crea o
emplea otra serie de carpetas en distintos lugares de tu sistema de
archivos:

- la carpeta de ***caché***: usada para almacenar archivos temporales
  que pueden borrarse sin riesgos
- la carpeta ***config***: que almacena tus ajustes de RawTherapee,
  perfiles de procesamiento y otros archivos editables por el usuario
- la carpeta de ***perfiles de procesamiento personalizados***: que
  puede ser la misma carpeta genérica de perfiles de procesamiento,
  incluída dentro de la carpeta *config*, pero que es recomendable que
  sea una carpeta situada dentro del árbol de subdirectorios del usuario
  (`/home/NombreDeUsuario`, `C:\Usuarios\NombreDeUsuario`, ...)

Como veremos a continuación, estas carpetas residen en una ubicación
especial y tienen un nombre que suele empezar por *RawTherapee*, seguido
habitualmente por un sufijo (este sufijo lo estableció la persona que
realizó la compilación de RawTherapee que estás usando).

Algunos ejemplos de los nombres que puedes encontrar son:

- RawTherapee
- RawTherapee **5.9**
- RawTherapee **5**
- RawTherapee **5-dev**
- RawTherapee**_test**
- y otras posibilidades, casi siempre empezando por *RawTherapee*

Si compilas tu mismo el programa, podrías encontrar nombres como
"5.8-2305-gbf734321" (la versión de base-el número de *commit*-el número
*hash*).

Normalmente las versiones estables de RawTherapee no usan ningún sufijo.

## La carpeta de caché

La *carpeta caché* de RawTherapee contiene conjuntos de elementos de
caché (un conjunto por imagen), los cuales consisten en:

- una miniatura,
- metadatos,
- un archivo de parámetros (el perfil de procesamiento),
- y opcionalmente un perfil de color embebido.

Por defecto, RawTherapee mantiene hasta 20.000 conjuntos de caché. Echa
un vistazo a la carpeta *caché*, ya que con el tiempo su tamaño puede
aumentar considerablemente. Esto se debe en buena parte a las miniaturas
de las imágenes, que se almacenan en la subcarpeta `images`. Borrar esta
subcarpeta es seguro: no perderás ningún ajuste de imagen y RawTherapee
simplemente tendrá que regenerar las miniaturas.

Las ubicaciones por omisión de la carpeta cache de RawTherapee son:

- Windows XP:  
  `%USERPROFILE%\Local Settings\Application Data\`
- Windows 7, 8 y 10:  
  `%LOCALAPPDATA%`
- Linux:  
  `home/NombreDeUsuario/.cache/`
- macOS:  
  `~/Library/Application Support/RawTherapee/cache/`  
  Bajo el menú *Ir* del buscador, haz clic en *Ir a carpeta* ( ); aquí
  podrás escribir o pegar cualquier nombre de carpeta a la que quieras
  navegar, incluso si está oculta.

## La carpeta con las configuraciones

La carpeta con las distintas confguraciones de RawTherapee contiene:

- la carpeta ***batch***, que almacena [perfiles de
  procesamiento](Sidecar_Files_-_Processing_Profiles/es.md)
  temporales de las fotos que has enviado a la
  [Cola](queue/es),
- la carpeta ***HaldCLUT***,
- la carpeta ***profiles***, donde puedes guardar tus [perfiles de
  procesamiento
  personalizados](Sidecar_Files_-_Processing_Profiles/es#Cómo_crear_tus_propios_perfiles_de_procesamiento.md)
  si deseas que aparezcan en la lista desplegable de RawTherapee.
- las reglas de ***[perfiles
  dinámicos](Dynamic_processing_profiles/es.md)***,
- el archivo ***options***, que contiene todos los ajustes que hayas
  hecho en las [Preferencias](preferences/es),
- el archivo
  ***[camconst.json](adding_support_for_new_raw_formats/es)***
  editado por el usuario (en el que habrás definido detalles de cómo
  debe tratarse un formato raw específico). La existencia de este
  archivo hace que se ignoren los valores del archivo *camconst.json*
  incluídos en RawTherapee al instalarlo.

Las ubicaciones de la carpeta config de RawTherapee (consulta [el
prefijo *RawTherapee\** descrito
anteriormente](#Las_carpetas_«ocultas»_del_programa.md)) son:

- Windows XP:  
  `%USERPROFILE%\Local Settings\Application Data\`
- Windows 7, 8 y 10:  
  `%LOCALAPPDATA%`
- Linux:  
  `~/.config/`
- macOS:  
  `~/Library/Application Support/RawTherapee/config/`

Puedes incluir esta carpeta en tus copias de seguridad, de modo que
puedas recuperar intactos todos tus ajustes y perfiles personalizados de
procesamiento, si instalas RawTherapee en un nuevo sistema.

## Carpetas config y cache personalizadas

Puedes hacer que RawTherapee use una carpeta config personalizada,
estableciendo la variable de entorno `RT_SETTINGS` a un valor
**absoluto** de una carpeta *en la que tengas permisos de lectura y
escritura*, y del mismo modo puedes usar una carpeta caché
personalizada, estableciendo la variable de entorno `RT_CACHE`.

Cómo hacerlo depende de tu sistema operativo, así que bastará con que
busques en internet *«cómo establecer variables de entorno
en*<EscreibeAquíElNombreDeTuSistemaOperativo>»''.

Algunos ejemplos:

- En Windows:  
  Nombre de variable: `RT_SETTINGS`, valor:
  `%LOCALAPPDATA%\rawtherapee\5.7`  
  Nombre de variable: `RT_CACHE`, valor: `Z:\rawtherapee\cache`
- En Linux y macOS:  
  `RT_SETTINGS=/home/bob/.config/rawtherapee/5.7`  
  `RT_CACHE=/home/bob/junk/rtcache`

## Perfiles de procesamiento personalizados

Si creas tus propios [perfiles de procesamiento
personalizados](Sidecar_Files_-_Processing_Profiles/es#Cómo_crear_tus_propios_perfiles_de_procesamiento.md),
para que aparezcan en la lista desplegable *Perfiles de procesamiento*
de RawTherapee, debes guardarlos en la carpeta *profiles*, que
encontrarás dentro de la carpeta *config*, [como se ha descrito
anteriormente](#La_carpeta_con_las_configuraciones.md).

## Carpeta temporal

La herramienta **[Editar la Imagen Actual en un Programa
Externo](Edit_Current_Image_in_External_Editor/es.md)** almacena
los archivos provisionales en una carpeta temporal:

- Windows: la ubicación por omisión es la que contiene la variable de
  entorno `$TEMP`, que normalmente es **`%LOCALAPPDATA%/Temp`**  
  Si no tienes establecida la variable de entorno `$TEMP`, se usará
  `C:\`.
- Linux y macOS: la ubicación por omisión es la que contiene la variable
  de entorno `$TMPDIR`, que normalmente es **`/tmp`**  
  Si no tienes establecida la variable de entorno `$TMPDIR`, se usará
  `/tmp`
