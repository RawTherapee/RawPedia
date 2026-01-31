---
title: Resize
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Transform Tab'
---

<div class="pagetitle">

Redimensionnement

</div>

<figure>
<img src="/images/Resize_tool_5.4-dev.png" title="Resize_tool_5.4-dev.png" />
<figcaption>Resize_tool_5.4-dev.png</figcaption>
</figure>

<figure>
<img src="/images/Resize-interpolation.png" title="Resize-interpolation.png" />
<figcaption>Resize-interpolation.png</figcaption>
</figure>

## Redimensionnement

Le redimensionnement fait parties des dernières choses appliquées lors
de l'enregistrement d'une image, cet outil opère après la plupart des
autres outils et transformations. Comme la réduction d'échelle d'une
image implique une perte de détails, cet outil comprend un composant
"Netteté post-redimensionnement" que vous pouvez utiliser pour rendre
l'image réduite plus vive.

Les effets de l'outil redimensionnement n'apparaissent pas dans
l'aperçu. Bien sûr, l'image sauvegardée est redimensionnée.

Limites du redimensionnement

- Elle est de 32x32px en réduction.
- La limite en agrandissement est de 16 fois la taille de l'image à
  partir de RawTherapee 5.5. Pour les versions antérieures à 5.4
  comprise, elles était de 4 fois la taille de l'image.

### Méthode

Le redimensionnement peut se réaliser suivant divers algorithmes, chacun
avec ses avantages et inconvénients. Nous avons réduit le choix aux deux
plus significatifs.

- Au plus proche

  
La méthode d'interpolation "Au plus proche" est conçue pour être
utilisée lorsque vous souhaitez agrandir une image dans le but de rendre
un détail donné plus grand sans introduire de pixels supplémentaires par
interpolation. Cela conserve les pixels tels qu'ils sont. C'est en
général utilisé pour l'agrandissement par puissance carrée de 2 (2x, 4x,
8x, 16x, etc.) dans le but d'amplifier certains détails sans introduire
de mélange entre les pixels. Le résultat aura un fort piqué, mais aussi
très pixellisé. Cette méthode n'est pas prévue pour être utilisée en
photographie quotidienne.

- Lanczos

  
Lanczos est la méthode de redimensionnement par défaut. Elle est conçue
pour être utilisée en photographie quotidienne et dans tous les cas sauf
pour celui exposé ci-dessus. Elle produit une image lisse, nette et de
haute qualité. Utilisable pour un redimensionnement de toute valeur.

### Préciser, Largeur et Hauteur

Vous pouvez préciser à quelle dimension porter l'image :

- Echelle

  
Faire ce choix si vous désirez réduire ou agrandir l'image par une
valeur spécifique.

par exemple, pour la réduire au quart de sa taille actuelle, mettre une
échelle de 0,25,

pour la rendre 4 fois plus grande, mettre une échelle de 4

- Largeur

  
Faire ce choix pour spécifier la largeur désirée en pixels et avoir la
hauteur adaptée en conservant les proportions.

- Hauteur

  
A utiliser pour spécifier la hauteur désirée en pixels, la largeur est
automatiquement adaptée pour conserver les proportions

- Boite englobante

  
Faire ce choix si vous désirez obtenir une image qui tienne dans une
certaine largeur et hauteur.

par exemple si vous désirez avoir la plus longue dimension de votre
image égale à 1000px, indépendamment du fait qu'il s'agisse d'un format
paysage ou portrait, configurez une boite englobante de 1000x1000px.

par exemple si votre image a pour dimensions 3000x2000 et que vous
désirez qu'elle tienne dans un écran de [1080p/Full
HD](https://fr.wikipedia.org/wiki/1080p), régler la boite englobante à
1920x1080 et votre image sera redimensionnée proportionnellement de
telle façon que la largeur ne dépassera pas 1920 pixels et la hauteur
1080.

### S'applique à

En général, on souhaite que la hauteur et la largeur s'applique à la
zone recadrée, cependant vous pouvez aussi souhaiter qu'elle s'applique
à l'image entière, bien que même dans ce cas, c'est l'image recadrée qui
est sauvegardée.

### Permettre l'agrandissement

Ce paramètre contrôle si l'outil de redimensionnement pourra agrandir
votre image ou bien seulement la diminuer. Si il est désactivé et que la
combinaison de la taille de l'image, du recadrage et du
redimensionnement est telle que l'image nécessiterait d'être agrandie
pour satisfaire votre objectif, ce paramètre empêchera l'agrandissement,
l’image restera à sa taille actuelle.

Ce paramètre fut introduit dans RawTherapee 5.5. Si vous utilisez dans
RawTherapee 5.5 des fichiers accolés de de versions antérieures, ce
paramètre sera automatiquement désactive.

## Netteté après redimensionnement

Redimensionner une image conduit souvent à une perte de netteté, il est
donc usuel de redonner du piqué à l'image après un redimensionnement.
Avec l'outil "Post-Resize Sharpening" (= Netteté post-redimensionnement)
vous pouvez enregistrer des images claires comme le cristal sans
complications ni travaux supplémentaires. Parce que cet outil traite
l'image après redimensionnement, il est impossible de prévisualiser ce
qu'il fera, mais ce n'est pas un problème car la procédure pour trouver
les bonnes valeurs est simple et directe.

Les valeurs par défaut sont efficaces mais si vous désirez les changer,
voici comment obtenir un aperçu de l'image :

1.  Travaillez votre image comme vous le feriez habituellement et
    activer l'outil redimensionnement (par exemple, en utilisant la
    méthode Lanczos, abaisser la résolution à une boite englobante de
    900x900px).
2.  Enregistrer l'image dans un format sans pertes tel que TIFF.
3.  Ouvrir ce TIFF enregistré dans RawTherapee, appliquer le profil de
    traitement Neutre si cela n'est pas fait automatiquement, et activer
    l'outil [Netteté](sharpening/fr) dans l'onglet Détail.
4.  Zoomer à 100% (1:1) et peaufiner le paramètres de l'outil Netteté
    jusqu'à obtenir un résultat satisfaisant. Ce sont les valeurs à
    utiliser dans l'outil Netteté post-redimensionnement.
5.  Revenir à l'image raw, activer l'outil Netteté
    post-redimensionnement et entrer les valeurs trouvées à l'étape
    précédente.

L'outil Netteté post-redimensionnement n'est disponible que si vous
utilisez la méthode de redimensionnement "Lanczos".

Etant donné que l'outil Netteté post-redimensionnement travaille de
façon identique à l'outil Netteté standard (sauf qu'il est placé à la
fin du processus), se reporter à l'article
[Netteté](sharpening/fr) pour en savoir plus sur le
fonctionnement des outils de netteté.
