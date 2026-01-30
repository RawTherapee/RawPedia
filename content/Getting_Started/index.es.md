---
title: Getting Started
contributors:
  - XavAL
weight: 1
---

<div class="pagetitle">

Por dónde empezar

</div>
<div class="headline">

Una introducción rápida para que empieces a sentirte cómodo en
RawTherapee

</div>

## ¿Qué es RawTherapee?

RawTherapee es un programa de procesamiento de imágenes en bruto (*raw*)
multiplataforma, publicado bajo la [Licencia Pública General GNU versión
3](https://www.gnu.org/licenses/gpl-3.0.en.html). En lugar de ser un
editor de imágenes de mapa de bits (o imágenes *ráster*) como
*Photoshop* o *GIMP*, o un programa de gestión de medios digitales como
*digiKam*, está específicamente dirigido a la postproducción de fotos
raw.

El programa original lo escribió Gábor Horváth de Budapest y un equipo
de personas de todo el mundo asumieron su desarrollo en 2010.

## Las distintas versiones de RawTherapee

Puedes descargar un instalador de RawTherapee desde
<http://rawtherapee.com/downloads> o desde tu gestor de paquetes de
Linux. Sin embargo, también puedes compilarlo tú mismo, si así lo deseas
o necesitas. En la [sección sobre
compilaciones](Main_Page/es#Compilación.md) de la página
principal de RawPedia tiene enlaces a instrucciones sobre cómo hacerlo.

En la página oficial hay muchas versiones disponibles para descargar,
además de un enlace a la documentación para generar las últimas
versiones *«en desarrollo»*: los programadores hacen continuamente
nuevas versiones de *desarrollo* y una o dos veces al año lanzan una
nueva versión *«estable»*. Esta versión *estable* está convenientemente
compilada y con todos los errores importantes conocidos ya corregidos.
Cualquier error que se encuentre en la versión *estable* será corregido
en las versiones de *desarrollo* posteriores y estas correcciones se
incluirán y acumularán hasta la siguiente versión *estable*, varios
meses después. Y así sucesivamente.

Las versiones de *desarrollo* son también donde se mejoran las
herramientas existentes y se añaden otras nuevas, aunque lleva tiempo
pulirlas y asegurar que funcionan bien nada más acabar de instalar el
programa. Así pues, por un lado las versiones de *desarrollo* siempre
tienen el mayor número de errores corregidos, pero por otro lado las
nuevas herramientas en estas versiones pueden estar muy poco pulidas,
además de que aparecerán nuevos errores.

Si deseas probar nuevas características, entonces hazte con la última
versión de *desarrollo*: podrás aprovechar las últimas correcciones de
errores y podrás probar nuevas herramientas, además de informar a los
programadores sobre problemas e ideas, aunque a costa de descubrir (y
sufrir) nuevos errores.

**Para un uso normal lo más recomendable es la última versión *estable*,
ya que en general te ofrece una experiencia más pulida.**

## Iniciando RawTherapee

La primera vez que inicies RawTherapee, verás la [pestaña del Explorador
de archivos](File_Browser/es.md) (que puede estar vacía).

\[\[<File:Rt_setm_fb.png%7Cthumb%7C1280px%7Cnone>\|**RawTherapee en el
"Modo Editor de Pestaña Única - pestañas verticales"**, mostrando:

<div class="captions_indent">

1- las secciones principales

2- los paneles del *Explorador de Archivos*

3- las miniaturas

4- los filtros

5- los botones de *zoom*

6- operaciones rápidas

7- las sub-pestañas del *Explorador de Archivos*

8- el menú contextual

</div>

\]\]

Arriba puedes ver el aspecto general de esta pestaña, con las siguientes
zonas:

1.  Secciones principales: tenemos el [*Explorador de
    archivos*](File_Browser/es.md) (activo en esta captura de
    pantalla), la *Cola de lotes*, el *Editor*, la *Barra de progreso*,
    el *Generador de Perfiles ICC*, la *Ayuda* y las *Preferencias*.

<!-- -->

1.  Paneles utilizados para navegar por los archivos y las carpetas.

<!-- -->

1.  Miniaturas de la carpeta actualmente abierta.

<!-- -->

1.  Filtros para mostrar únicamente las miniaturas que coincidan con
    determinados metadatos o estados de los archivos.

<!-- -->

1.  Botones para aumentar o disminuir el tamaño de las miniaturas (Zoom)
    y para mostrar/ocultar información en las miniaturas.

<!-- -->

1.  Operaciones habituales rápidas sobre la imagen.

<!-- -->

1.  Sub-pestañas del Explorador de Archivos:
    - Filtro (abierto en esta captura de pantalla)
    - Inspeccionar (para ver una vista previa de tamaño completo de una
      imagen JPEG, o en su caso de la imagen JPEG incrustada en un
      archivo raw),
    - Editar por lotes (para aplicar algún cambio a todas las imágenes
      seleccionadas)
    - Exportación rápida (de baja calidad y evita algunas herramientas,
      pero escribe en disco rápidamente - ¡no lo uses para la
      exportación final!).

<!-- -->

1.  Menú contextual al hacer clic con el botón derecho del ratón
    (normalmente lo usarás para aplicar algún perfil de procesamiento a
    todos los archivos seleccionados)

Para poder editar tus fotos necesitas indicarle a RawTherapee dónde
están almacenadas: utiliza el navegador del árbol de directorios, a la
izquierda de la pestaña *Explorador de archivos*, para llegar hasta
donde tengas almacenadas las fotos y ***haz doble clic*** en esa carpeta
para abrirla. Si sólo haces un *clic* únicamente seleccionarás la
carpeta, pero *«no abrás entrado»* en ella.

A continuación, haz *doble clic* en una foto para empezar a editarla.

## Edita tu primera imagen

La edición de las fotos se realiza en el [Editor de
imágenes](Editor/es.md).

Cuando abres por primera vez una foto, se aplica el procesado por
defecto (que en fotos raw será *Curva Auto Ajustada - ISO Bajo*, a no
ser que lo hayas cambiado en las *Preferencias*) y la miniatura del
*Navegador de Archivos* se actualizará con el resultado.

Pero en el caso de las fotos raw, dado que los datos no están procesados
(la palabra inglesa *«raw»* viene a significar *«crudo»* o *«sin
procesar»*), es posible que la imagen que veas en la *vista previa* no
sea lo que tu cámara te ha hecho ver en su visor: la propia cámara ha
*cocinado* (o procesado) esos datos raw de una manera muy concreta (que
depende de la marca de la cámara) y es posible que RawTherapee no los
haya *cocinado* de igual forma. Aunque te parezca sorprendente, no hay
*una única manera correcta* de procesar (o *cocinar*) una foto y tampoco
hay una única manera de procesar una foto. Aún así, si lo que deseas es
una imagen lo más parecida al resultado que te ofrece tu cámara, deberás
emplear la [*Curva de Tonos Auto
Ajustada*](Auto-Matched_Curve/es.md) y después afinar el
resultado con el resto de herramientas (para leer más información sobre
este tema, [pásate por este apartado de la documentación del
*Editor*](Editor/es#¡Mi_foto_raw_no_es_igual_que_el_JPEG_de_la_cámara!.md)).

**Y ahora tómate tu tiempo para echarle un vistazo a la pestaña del
Editor**.

<figure>
<img src="/images/Rt_setm_editor.png" title="Rt_setm_editor.png" />
<figcaption>Rt_setm_editor.png</figcaption>
</figure>

Fíjate en que hay pestañas dentro de esta pestaña (hacia la esquina
superior derecha): estas pestañas y los controles que hay debajo de
éllas son la ***Caja de Herramientas***. Probablemente tengas la primera
pestaña abierta y si pasas el ratón por encima de élla, verás que se
trata de la pestaña *Exposición*.

Debajo de esta barra de pestañas se encuentran las herramientas que
contiene la pestaña seleccionada. En el caso de *Exposición* son:
Exposición, *Sombras/Luces*, *Mapeo Tonal*, etc.

Si haces clic en en el nombre de una de ellas, se expandirá para que
puedas ver su contenido. Haz clic de nuevo y se contraerá. Haz clic con
el botón derecho del ratón en el nombre de una herramienta y esta se
expandirá, *y al mismo tiempo todas las demás se contraerán* (un atajo
que ahorra tiempo). A la izquierda del nombre de cada herramienta hay un
botón que te permite activarla/desactivarla (
![<File:Poweronsmall.png>](Poweronsmall.png "File:Poweronsmall.png") /
![<File:Poweroffsmall.png>](Poweroffsmall.png "File:Poweroffsmall.png")
). En algunos casos en vez de un botón de encendido hay un triángulo (
![<File:Expander-closed-small.png>](Expander-closed-small.png "File:Expander-closed-small.png")
) para desplegarla. Lee la sección [Comentarios Generales sobre Algunas
Herramientas de la Caja de
Herramientas](General_Comments_About_Some_Toolbox_Widgets/es#Herramientas.md)
para una explicación detallada.

Y antes de empezar a trabajar en una imagen, he aquí un consejo
importante: **¡No Te Asustes!** No vas a destruir ninguna de tus
preciadas imágenes si cometes un error. RawTherapee tiene algunas
características que te ayudan a proteger tus imágenes:

- RawTherapee edita de una forma no destructiva tus archivos raw. Esto
  significa que RawTherapee nunca jamás modificará el archivo raw en sí:
  todos los cambios se almacenan en archivos anexos. Puedes encontrar
  más información sobre éllos en el artículo [Perfiles de
  Procesamiento](Sidecar_Files_-_Processing_Profiles/es.md).

<!-- -->

- Cuando utilices el *Editor*, a la izquierda verás el panel del
  [*Historial*](editor/es#historial). Este panel muestra un
  listado de cada cambio que hayas realizado en tu imagen y para volver
  hasta el estado en que estaba la imagen en cualquier paso (incluso el
  momento en que la imagen se abrió), simplemente haz clic en la línea
  correspondiente del panel del Historial.

<!-- -->

- Debajo del panel del *Historial* verás el panel de
  [*Instantáneas*](editor/es#instantáneas). Este panel
  almacena el estado de todas las herramientas como en una
  "instantánea". Puedes ignorarlo por ahora, pero te será útil cuando
  adquieras experiencia con RawTherapee, ya que por ejemplo te permite
  editar fácilmente tu foto con un bonito y colorido aspecto y tomar una
  instantánea; luego puedes editarla de nuevo, llevarla a un hermoso
  aspecto en blanco y negro y tomar otra instantánea; y por fin
  compararlas con solo hacer clic en cualquiera de las dos instantáneas.
  (Nota: RawTherapee todavía no guarda instantáneas en el archivo *PP3*,
  pero lo hará en el futuro. Si tienes tres instantáneas que deseas
  conservar, de momento tendrás que hacer clic sucesivamente en éllas y
  guardar el archivo *PP3* de cada una con un nombre único).
- Como era de esperar, **Control-z** deshará el último cambio.

### Procedimientos Básicos

1.  Para comenzar haz clic en la pestaña *Color* (
    ![<File:Color-circles.png>](Color-circles.png "File:Color-circles.png")
    ) y expande la herramienta [*Balance de
    blancos*](White_Balance/es.md) mediante un clic sobre élla
    con el botón derecho del ratón. RawTherapee comenzará con el balance
    de blancos utilizado por tu cámara. Para ajustarlo puedes mover los
    controles deslizantes de *Temperatura* y *Tinte*, o usar el selector
    *Muestra de balance de blancos* (
    ![<File:Color-picker.png>](Color-picker.png "File:Color-picker.png")
    ) en un área gris neutro. Ajústalo al gusto.
2.  A continuación, ajusta la exposición yendo a la pestaña de
    *Exposición* (
    ![<File:Exposure.png>](Exposure.png "File:Exposure.png") ),
    desplegando la herramienta [*Exposición*](exposure/es).
    De momento, utiliza únicamente los controles deslizantes de
    *Compensación de exposición* y *Saturación*.
3.  Si tu imagen presenta ruido, cambia a la pestaña *Detalle* (
    ![<File:Detail.png>](Detail.png "File:Detail.png") ), amplía (haz
    zoom) al 100% utilizando el botón *Lupa* (
    ![<File:Magnifier-1to1.png>](Magnifier-1to1.png "File:Magnifier-1to1.png")
    ) o la tecla de acceso directo *«z»* (ya que los efectos de las
    herramientas de esta pestaña sólo son visibles en la vista previa
    ampliada al 100%) y activa la herramienta [*Reducción de
    Ruido*](Noise_Reduction/es.md) haciendo clic en el botón de
    encendido (
    ![<File:Poweroffsmall.png>](Poweroffsmall.png "File:Poweroffsmall.png")
    ), dejando por el momento los ajustes en sus valores por defecto.
    RawTherapee elimina automáticamente el ruido de color (ruido de
    «crominancia»). El ruido de luminancia se elimina
    [manualmente](noise_reduction/es#uso), aunque déjalo por
    ahora ya que el ruido de luminancia generalmente proporciona un
    aspecto agradable, granulado y similar al de una película. Como
    regla general, cuando utilices la reducción de ruido, no utilices la
    mejora de nitidez («Enfoque» o «Sharpening»). Reduce el zoom hasta
    ver la imagen completa, ya sea usando el botón
    ![<File:Magnifier-fit.png>](Magnifier-fit.png "File:Magnifier-fit.png")
    o usando la tecla *«f»*.
4.  Ahora corregirás la [*Geometría*](lens/geometry/es) y la
    composición de tu foto.
    - Primero nivela el horizonte, o corrige las cosas que deben ser
      verticales, como las farolas o los bordes de los edificios. Para
      hacerlo fácilmente, presiona la tecla *«s»* (o haz clic en el
      botón
      ![<File:Rotate-straighten.png>](Rotate-straighten.png "File:Rotate-straighten.png")
      ) y a continuación haz clic y arrastra sobre la vista previa para
      marcar una línea a lo largo del horizonte (o a lo largo del borde
      de un edificio). La imagen girará según el ángulo formado entre la
      línea recién marcada con la horizontal o vertical y
      automáticamente entrarás en la pestaña *Transformar* (
      ![<File:Transform.png>](Transform.png "File:Transform.png") ), con
      la herramienta *Lente/Geometría* desplegada.
    - Para recortar la foto, pulsa la tecla *«c»* (o utiliza el botón
      *Recortar* ![<File:Crop.png>](Crop.png "File:Crop.png") ) y haz
      clic y arrastra formando un marco sobre la vista previa que
      resaltará lo que quedará visible tras el recorte. Fíjate que la
      herramienta *Recortar* se activa automáticamente. No hay necesidad
      de «aplicar» el recorte, sino que se hace efectivo en el momento
      en que se dibuja. Es posible que quieras establecer la *Clase de
      guía de recorte* en *Ninguno*, si te molesta a la vista.
    - Por último reducirás el tamaño de la foto, porque ¿quién quiere
      subir un archivo JPEG de 10 MB a su red social? Activa la
      herramienta [*Cambiar tamaño*](resize/es) y déjala con
      la configuración predeterminada. **Ten en cuenta que el
      redimensionado sólo se aplica a la imagen en disco, no a la vista
      previa.**
5.  Ya está todo listo, [guárdala](saving/es) enseguida: haz
    clic en el botón *Guardar imagen actual* (
    ![<File:save.png>](save.png "File:save.png") ), o usa el método
    abreviado *«Ctrl+s»*. Guárdalo como un archivo JPG, Calidad a *92*,
    submuestreo *Balanceado* (estos son buenos ajustes generales). Elige
    la carpeta donde quieras guardarla y al cabo de unos segundos el
    archivo estará listo en la carpeta que hayas seleccionado. Si
    cierras RawTherapee, la configuración que has utilizado se guardará
    en un [*archivo adjunto
    PP3*](Sidecar_Files_-_Processing_Profiles/es.md) junto al
    archivo raw original (que no se ha modificado), de manera que en el
    futuro podrás volver a abrir la foto y conservar la configuración de
    las herramientas que utilizaste.

Ahora que ya has realizado un procesado básico y estás familiarizado con
los pasos a dar, recapitulemos pero con detalles más avanzados.

### Procedimientos Avanzados

Lee siempre el artículo de cada herramienta aquí (en RawPedia) antes de
usarla, para tener una comprensión completa de lo que haces. Los
artículos explican cómo funcionan las herramientas en RawTherapee junto
con algunos conceptos directamente relacionados con el programa y los
revelados, mientras que los conceptos generales no específicos de las
herramientas se dejan al usuario para que los encuentre en Wikipedia o
en cualquier otro lugar.

Asegúrate de repasar los [*Atajos de
Teclado*](Keyboard_Shortcuts/es.md).

El orden en que se ejecutan las herramientas dentro del motor de
RawTherapee es fijo, así que desde este punto de vista no importa en qué
orden se activa o desactiva una herramienta. Sin embargo, algunas
herramientas pueden tener un gran impacto en el resto de herramientas,
como por ejemplo cambiar la exposición puede requerir que reajustes el
tono de color; por otra parte algunas herramientas pueden requerir un
gran consumo de CPU para calcular la vista previa, haciendo que las
sucesivas actualizaciones de la vista previa sean lentas a partir de ese
momento, por lo que es recomendable que te ciñas a este orden general de
operaciones:

1.  Empieza por asegurarte de que el entorno de RawTherapee esté
    configurado correctamente, es decir:
    - Asegúrate de que RawTherapee utiliza el perfil de color correcto
      para tu monitor, si es que utilizas un flujo de trabajo con
      gestión del color (no tiene mucho sentido que no lo hagas).
      Comprueba las *Preferencias \> Gestión del color*. Es posible que
      tengas que cargar las curvas de calibración apropiadas en tu
      tarjeta gráfica si generaste el perfil de color del monitor a
      partir de éllas, aunque la forma en que puedes hacerlo no está al
      alcance de esta documentación.
    - Asegúrate de que la herramienta de *Gestión del color* esté
      configurada correctamente. Por lo general, los valores por defecto
      son los mejores (lee el artículo sobre la [*Gestión del
      color*](Color_Management/es.md)). Si en lugar de utilizar
      la matriz de color o los perfiles DCP o ICC incluídos con
      RawTherapee decides utilizar uno externo, por ejemplo un ICC hecho
      por tí mismo o un DCP de Adobe, lo primero que debes hacer es
      cargarlo. De lo contrario, si utilizas algunas herramientas y lo
      cargas a posteriori, puede que tengas que reajustarlas todas.
      Utiliza siempre un perfil de salida (en la mayoría de los casos el
      perfil por defecto, *RT_sRGB*). Si crees que es una buena idea
      seleccionar *Sin ICM: Salida sRGB*, estás equivocado.
2.  Si quieres utilizar una imagen de [*Campo
    plano*](Flat_Field/es.md) y/o una [*Toma
    Negra*](Dark_Frame/es.md), hazlo ahora, para evitar
    posteriores reajustes.
3.  Ahora ajusta el [*Balance de blancos*](white_balance/es)
    correcto. Puedes modificar primero la exposición si la imagen es
    demasiado oscura (o demasiado luminosa) para ver mejor los cambios
    en el balance de blancos.
4.  A continuación, ajusta la [*Exposición*](exposure/es),
    utilizando los controles deslizantes de *Compensación de Exposición*
    y *Nivel de Negro* para llevar la imagen a una apariencia correcta.
    Una vez que la imagen se vea bien, continúa con las *Curvas tonales*
    (al final de la herramienta *Exposición*). **Asegúrate de leer la
    sección [*Curvas Tonales*](exposure/es#curvas_tonales)**
    en el artículo sobre la *Exposición* para aprender por qué hay dos
    curvas y cómo usarlas correctamente: ¡son una herramienta muy
    potente!
5.  En la sección de *Procedimientos Básicos*, te hemos sugerido que
    utilices el control deslizante
    [*Saturación*](exposure/es#saturación) (en la herramienta
    *Exposición*). Ahora que ya has aprendido lo básico y estás
    explorando técnicas más avanzadas, te sugerimos que ya no uses el
    control deslizante de *Saturación*, sino que utilices la [*curva
    CC*](Lab_Adjustments/es#Curva_CC.md) de la herramienta
    [*Ajustes Lab*](lab_adjustments/es), ya que te
    proporciona un control más preciso.
6.  El orden del resto no está demasiado definido. Algunas herramientas
    influirán inevitablemente en otras. Sigue con la herramienta
    *Ajustes Lab* y, a continuación, con el resto de las herramientas de
    la pestaña *Exposición*.
7.  Continúa con las herramientas de la pestaña *Color* (
    ![<File:Color-circles.png>](Color-circles.png "File:Color-circles.png")
    ).
8.  Luego amplía al 100% y usa las herramientas de la pestaña *Detalle*
    ( ![<File:Detail.png>](Detail.png "File:Detail.png") ). Por lo
    general, no se debe ajustar la nitidez (*Enfoque*) si se está
    utilizando la reducción de ruido.
9.  Y por fin, reduce el zoom hasta ver la imagen completa y utiliza las
    herramientas de la pestaña *Transformar* (
    ![<File:Transform.png>](Transform.png "File:Transform.png") ). La
    razón por la que dejas estas herramientas para el final es que
    pueden hacer que la imagen de vista previa aparezca borrosa: para
    que la vista previa responda con fluidez, RawTherapee usa la imagen
    de vista previa que ves, a la resolución que ves (pequeña), para
    mostrar lo que hacen las herramientas. Cuando giras o de alguna
    forma cambias la geometría de una imagen pequeña, se produce un
    claro efecto de difuminado. Esto no es un problema a la hora de
    guardar la imagen en disco, ya que para éllo RawTherapee procesa la
    imagen a tamaño real (no la vista previa). Un proceso lento, pero de
    alta calidad.
10. Puedes editar los metadatos en la pestaña
    [*Metadatos*](metadata_copy_mode/es) (
    ![<File:Metadata.png>](Metadata.png "File:Metadata.png") ) en
    cualquier momento antes de guardar la imagen.
11. Guárdalo todo, ya sea directamente con el botón
    ![<File:save.png>](save.png "File:save.png") (en la parte inferior
    de la pantalla) cuando quieras guardar una sola foto, o a través de
    la [*Cola de lotes*](the_batch_queue/es) (
    ![<File:gears.png>](gears.png "File:gears.png") ) cuando quieras
    procesar y guardar muchas fotos. Léete el artículo [*Guardar
    imágenes*](Saving_Images/es.md).
