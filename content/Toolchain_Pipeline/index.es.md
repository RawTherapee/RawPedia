---
title: Toolchain Pipeline
contributors:
  - XavAL
tags:
  - 'General Information'
---

<div class="pagetitle">

Circuito de revelado

</div>
<div class="headline">

El orden de aplicación de las herramientas al exportar la imagen

</div>

## Introducción

Todo lo que le ocurre a una imagen en RawTherapee, desde que la abres
hasta que se muestra en pantalla o se guarda, tiene lugar en un orden
preestablecido: los datos fluyen de un módulo a otro sin que hayan
duplicidades y sin que se pueda cambiar su orden. Es lo que llamamos
**circuito de revelado**.

RawTherapee contiene cuatro circuitos, empleados en:

- las miniaturas
- el navegador y la imagen mostrada cuando arrastras la imagen para ver
  otra zona de la foto
- la vista previa
- el procesado completo a la hora de exportar la imagen mediante el
  botón *«Guardar como»* o mediante la cola de procesado

## El *circuito* o *cadena de revelado*

En la siguiente lista puedes ver el orden simplificado de operaciones a
la hora de revelar una foto:

<div class="nested-numbering">

1.  Preprocesado
    1.  Imagen de negro base
    2.  Campo plano
    3.  Píxeles muertos
    4.  Píxeles bloqueados
    5.  Escalado de colores (interno, no hay herramienta en la interfaz)
    6.  Punto negro en Raw
    7.  Corrección de distorsión del objetivo
    8.  Equilibrado de verdes
    9.  Filtro de ruido en bandas
    10. Corrección de aberración cromática
    11. Punto blanco en Raw
    12. Histograma Raw
    13. Preparación de Auto Exposición
2.  Desentramado
3.  Retinex
4.  Recuperación de luces
5.  Equilibrio de blancos
6.  Recorte
7.  Conversión entre espacios de color
8.  Reducción de ruido
9.  Eliminación de neblina
10. Compresión del rango dinámico
11. Curva de tono auto-ajustada
12. Curva de reproducción de tonos (TRC)
13. Procesado RGB
    1.  Mezclador de canales
    2.  Curva de tono
    3.  Luces
    4.  Sombras
    5.  Curvas RGB
    6.  Curvas HSV
    7.  Virado de color
    8.  Simulación de película
    9.  Blanco y negro
    10. Cuadrícula de corrección L\*a\*b\*
    11. Sombras/Luces L\*a\*b\*
    12. Contraste local L\*a\*b\*
14. Procesado L\*a\*b\*
    1.  Herramienta de ajuste local: desdibujado y ruido, reducción de
        ruido, vivacidad, contraste por niveles de detalle, difuminado,
        contraste local, enfoque, retinex, exposición, color y luz,
        evitar cambio/variación de colores
    2.  Ajustes L\*a\*b\*
    3.  Vivacidad
    4.  Rejilla de corrección de color L\*a\*b\*
    5.  Filtro de viñeteado
    6.  Filtro graduado de densidad neutra
    7.  Mapeo tonal
    8.  Reducción de ruido impulsivo
    9.  Cancelar borde púrpura
    10. Bordes
    11. Microcontraste
    12. Nitidez
    13. Contraste por niveles de detalle
    14. Niveles de Ondícula
    15. Difuminado
    16. Modelo de apariencia de color CIECAM02-16
    17. Cambio de tamaño
    18. Nitidez tras cambio de tamaño
15. Conversión final L\*a\*b\* ➡ RGB

</div>
