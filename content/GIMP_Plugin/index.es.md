---
title: GIMP Plugin
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

El plugin para GIMP

</div>
<div class="headline">

Es posible abrir imágenes raw en GIMP usando RawTherapee como un plugin

</div>

## Requisitos

- RawTherapee v.5.3 o superior
- GIMP v.2.9.6 o superior
- El ejecutable de RawTherapee debe poder encontrarse a partir de la
  [variable de
  entorno](https://es.wikipedia.org/wiki/Variable_de_entorno#UNIX_/_GNU/Linux)
  `$PATH`. Este será el caso si has instalado RawTherapee para todo el
  sistema. Si no fuera así deberás añadir su localización a mano antes
  de intentar abrir un archivo raw con GIMP.

## Cómo editar archivos raw en GIMP

Simplemente abre un archivo raw desde GIMP.

![](gimp_rtselect.jpg "gimp_rtselect.jpg")Al hacerlo GIMP buscará el
programa por defecto para revelar este tipo de archivos en el `$PATH` y
se abrirá automáticamente una ventana del editor establecido en las
preferencias de GIMP. Si pretendes que RawTherapee sea este programa por
defecto, deberás seleccionarlo en la lista de programas posibles (dentro
de las *preferencias* del propio GIMP). Ten en cuenta que dependiendo
del
[tema](https://docs.gimp.org/2.10/es/gimp-pimping.html#gimp-prefs-theme)
que tenga GIMP, es posible que no veas claramente qué programa raw está
seleccionado.

Cuando arranque RawTherapee, verás que estás en la ventana del
[*Editor*](editor/es), con cualquier revelado previo
realizado a la imagen ya cargado. Además te dará la bienvenida un cuadro
de diálogo indicándote que has arrancado RawTherapee mediante el plugin:
![](gimp_rtpluginwelcome.jpg "gimp_rtpluginwelcome.jpg")

Y tal y como dice el cuadro de diálogo, cuando cierres RawTherapee la
imagen se exportará y enviará automáticamente a GIMP.
