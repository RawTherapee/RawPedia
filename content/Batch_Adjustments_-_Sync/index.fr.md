---
title: Batch Adjustments - Sync fr
contributors:
  - Lebarhon
tags:
  - 'General Information'
---

<div class="pagetitle">

Ajustements par lot - Sync

</div>

RawTherapee autorise la définition des paramètres pour le traitement de
nombreuses photos en même temps lors des ajustements par lots, ou sync,
généralement selon deux méthodes. Il permet le copier-coller, partiel ou
total, d'un [profil de
traitement](Sidecar_Files_-_Processing_Profiles/fr.md) (une
collection de paramétrages d'outils), à un nombre quelconque d'images.
Il permet aussi de sélectionner un nombre quelconque d'images et
d'appliquer n'importe quel outil à l'ensemble d'entre elles en une fois
(sync). Regardons de plus près ces deux méthodes.

Les deux méthodes impliquent de faire une sélection des photos
auxquelles vous désirez appliquer le traitement. Elle est réalisée à
l'aide des combinaisons standard de touches : Shift + clic pour
sélectionner une suite d'images, Ctrl + clic pour sélectionner des
images individuellement, ou Ctrl + A pour tout sélectionner. Les deux
méthodes sont réalisées depuis [L'onglet Navigateur de
fichiers](The_File_Browser_Tab/fr.md). La méthode
"copier-coller" peut aussi se faire depuis [La bande
film](The_Image_Editor_Tab/fr#La_bande_film.md).

<noinclude>== Copier-coller ==</noinclude> <includeonly>===
Copier-coller ===</includeonly> Copier et coller un profil de traitement
sur une sélection d'images est une tâche très commune. Supposons une
série de photos, par exemple des prises en studio, des portraits de
mariage, ou des photos macro brackétées. toutes les images d'une même
série sont très similaires, utilisant le même objectif, le même ISO, la
même balance des blancs et auront le même usage final. Cela signifie
qu'elles nécessitent les mêmes paramètres de traitement, la même
réduction de bruit, la même reprise de netteté et de distorsion, etc.
Pour traiter le lot, ce qui se fait en général est d'ouvrir n'importe
quelle image de la série dans [L'onglet
Editeur](The_Image_Editor_Tab/fr.md) et de la peaufiner à votre
goût. Cela fait, vous allez appliquer le profil de traitement de cette
image à toutes les autres de la même série. Pour cela, allez dans
[L'onglet Navigateur de fichiers](the_file_browser_tab/fr),
cliquer droit sur cette photo et sélectionner "*Opérations sur les
profils \> Copier le profil*", puis sélectionner les images auxquelles
on souhaite appliquer ce profil, clic droit sur n'importe laquelle
d'entre elles, et choisir "*Opérations sur les profils \> Coller le
profil*". En une seule opération rapide, vous avez dupliqué les mêmes
paramètres sur toute la série d'images.

De plus, RawTherapee permet de n'appliquer qu'une partie du profil, par
exemple seulement l'outil de redimensionnement. Pour cela choisir
"*Opérations sur les profils \> Coller partiellement* au lieu de
"Coller".

<noinclude>== Sync ==</noinclude> <includeonly>=== Sync
===</includeonly> RawTherapee permet aussi d'appliquer instantanément un
outil à une sélection d'images. La fonctionnalité équivalente est
appelée "Sync" dans d'autres logiciels. cette méthode est intéressante
lorsque vous n'avez pas besoin d'avoir un aperçu précis des
modifications, par exemple lorsque vous n'avez besoin que d'un
"Redimensionnement" d'une sélection de photos, car lorsque vous
travaillez dans l'onglet Navigateur de fichiers, votre seul aperçu sont
les petites et imprécises vignettes. Cette méthode ne peut être réalisée
que dans l'onglet Navigateur de fichiers car vous avez besoin d'accéder
au panneau des outils dédiés aux lots (le panneau à droite).

Quand vous êtes dans l'onglet Navigateur de fichiers, sélectionnez les
images que vous désirez traiter par lot (Sync), puis utilisez le panneau
d'outils à droite pour réaliiser les ajustements. Vos peaufinages
peuvent soit remplacer ceux qui existent déjà (mode "Remplace") ou bien
s'y ajouter (mode "Ajoute"). Par exemple, si vous sélectionnez deux
photos, la première ayant une compensation d'exposition de +1 IL et la
deuxième n'en ayant pas, et vous appliquez une compensation d'exposition
de + 0,6 IL, alors la première photo aura au final une compensation
d'exposition de + 1,6 IL en mode "Ajoute" et de + 0,6 IL en mode
"Remplace". La deuxième photo aura une compensation d'exposition de +
0,6 IL dans les deux modes. Vous pouvez décider quels outils doivent
fonctionner en mode "Ajoute" et en mode "Remplace" dans l'onglet
[Traitement par lot de la fenêtre
Préférences](Preferences/fr#L'onglet_Traitement_par_lot.md).
