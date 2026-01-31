---
title: Defringe
contributors:
  - XavAL
tags:
  - 'Tool Description'
  - 'Detail Tab'
---

<div class="pagetitle">

Eliminación de bordes púrpura

</div>

__TOC__

## El problema

![](fringes.jpg "fringes.jpg")Los «bordes púrpura» (en inglés *«purple
fringing»*) son la denominación usual para un artefacto muy concreto que
se muestra como un borde de color violeta-púrpura-magenta siguiendo los
bordes con mayor contraste de la foto. Es especialmente notable su
aparición en contraluces con un fondo muy luminoso de luz natural.

Este problema y otros similares son causados por las [aberraciones
cromáticas](https://www.xatakafoto.com/trucos-y-consejos/aberracion-cromatica-que-es-y-varios-consejos-para-evitarla),
aunque es razonablemente fácil corregir o al menos reducir su aparición
en la imagen final. Para ello es muy recomendable que emplees la
herramienta [*Aberraciones
cromáticas*](Chromatic_Aberration/es.md) antes de activar la
*Eliminación de bordes púrpura*.

En RawTherapee, esta herramienta se aplica ya sea en el espacio
L\*a\*b\* o en el CIECAM02/16 (si este último está activado). En
consecuencia, la activación de CIECAM02/16 puede producir que esta
herramienta de resultados levemente diferentes, especialmente si se usa
la curva de *Matiz*.

## La herramienta

La ***Eliminación de bordes púrpura*** es una herramienta sencilla y muy
poderosa para eliminar una buena cantidad de «bordes coloreados»
(púrpura, verde, amarillo, rojo, azul, ...) de las imágenes. Ajustando
con precisión los distintos controles podrás incluso llegar a eliminar
estos artefactos de forma que parezca que nunca estuvieron ahí. Sin
embargo es necesario insistir que es muy recomendable usarla tras haber
activado la herramienta *Aberraciones cromáticas*.

### Los controles

Los bordes coloreados se suprimen promediando los píxeles problemáticos
con los píxeles de su alrededor, a una distancia igual al ***Radio***
especificado: cuanto mayor sea el *Radio*, más cantidad de píxeles se
verán afectados por la herramienta. Visto de otro modo: cuanto mayor sea
el borde púrpura, mayor deberá ser el *Radio* para cancelar el problema.

El ***Umbral*** establece cómo de contrastados deberán ser los píxeles
para que se les aplique la herramienta: cuanto mayor es el valor del
*Umbral*, mayor deberá ser el contraste para que RawTherapee considere
que debe eliminar un borde coloreado.

Puedes usar la [curva
plana](General_Comments_About_Some_Toolbox_Widgets/es#Curva_plana.md)
***Matiz*** para especificar qué bordes coloreados eliminará la
herramienta: el eje horizontal representa el rango de colores y el eje
vertical la intensidad de la eliminación de bordes cromáticos. Esto te
permite limitar la acción a un rango específico de colores sin afectar a
colores de otros matices.

### Ejemplos prácticos

1.  Para empezar es necesario aclarar que **debes ser bastante sutil** a
    la hora de ajustar los distintos controles, puesto que si te quedas
    corto se verán restos del borde púrpura, mientras que si te pasas,
    generarás otro tipo de artefactos.  
      
    ![](defringe-2much.jpg "defringe-2much.jpg")
2.  A la hora de eliminar la mayoría de bordes de distintos colores,
    **es útil elevar un píxel todos los puntos de control de la curva de
    *Matiz***, de manera que se activa la eliminación de bordes en todos
    los colores, pero respeta en gran medida los colores de la foto. De
    todas formas, si debes recurrir a este tipo de curva es que la
    óptica o las condiciones de la escena están bastante alejadas de lo
    óptimo, así que también debes esperar algún tipo de pérdida general
    de tonos en la foto.  
      
    ![](defringe-1px.jpg "defringe-1px.jpg")![](defringe-1pxcurve.jpg "defringe-1pxcurve.jpg")
3.  Aunque **a veces no es recomendable usar la curva de *Matiz*
    anterior**.  
      
    ![](defringe-1px_notsuitable.jpg "defringe-1px_notsuitable.jpg")
4.  Y no olvides que todos los bordes coloreados no tienen por qué
    eliminarse con la herramienta *Eliminación de bordes púrpura*: en
    casi todas las ocasiones deberás aplicar antes la reducción de
    *Aberraciones cromáticas*, ya que es automática y elimina gran parte
    de los artefactos.  
      
    ![](defringe+ca.jpg "defringe+ca.jpg")
