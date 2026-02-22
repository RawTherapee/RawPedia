---
title: Premier Pas
translationKey: getting-started
contributors:
  - Lebarhon
tags:
  - 'General Information'
weight: 1
---


## Bienvenue

RawTherapee est un programme de traitement des images raw
multi-plateformes, édité sous la Licence Publique Générale (General
Public License) GNU, version 3. Il était à l'origine écrit par Gábor
Horváth de Budapest, puis le développement a été repris en 2010 par une
équipe de personnes du monde entier. Plutôt que d'être un éditeur
d'image par points tels que Photoshop ou GIMP, ou un gestionnaire
d'albums numériques comme Digikam, il est spécialisé dans le
post-traitement des photos raw (on dit aussi plus simplement
"traitement"). Et il le fait très bien, RawTherapee est au minimum l'un
des plus puissants programmes de traitement des fichiers raw
disponibles.

## Obtention de RawTherapee

Si vous souhaitez participer aux tests de la version de dernière minute,
voir l'article [Téléchargement - Versions de
développement](/download#versions_de_développement).

## Démarrage de RawTherapee

![](Rt_setm_fb.png "Rt_setm_fb.png") (actuellement ouvert), File
d'attente, Éditeur et Préférences. 2- Panneaux utilisés pour la
navigation dans les dossiers et fichiers. 3- Vignettes du dossier
actuellement ouvert. 4- Filtres pour limiter l'affichage des vignettes
aux seules qui répondent à certaines métadonnées ou états. 5- Zoom des
vignettes et infos. 6- Opérations rapides sur les images. 7-
Sous-onglets du Navigateur de fichiers: Filtre (actuellement ouvert),
Inspecter (pour visualiser l'aperçu JPEG intégré en plein format),
Édition par lot (pour appliquer des réglages à toutes les images
sélectionnées) et Export rapide (basse qualité et escamote certains
outils mais sauvegarde rapide - a ne pas utiliser pour une sauvegarde
principale !). 8- Menu contextuel du clic droit (a utiliser typiquement
pour appliquer un profil de traitement à tous les fichiers
sélectionnés).\]\]

Lorsque vous démarrez RawTherapee, vous voyez [Le Navigateur de
fichiers](/The_File_Browser_Tab), et il se peut qu'il soit
vide. Vous devez préciser à RawTherapee l'endroit où sont stockées vos
photos raw. Utiliser la navigation dans l'arborescence des fichiers, sur
la gauche dans l'onglet "Navigateur de fichiers", pour rechercher votre
dossier de photos raw et le double cliquer pour l'ouvrir. Puis double
cliquer sur une photo raw pour l'éditer.

## Editez votre première image

Commençons par un rappel. Une photo raw contient un amas de données
générées par le capteur, elles constituent la majeure partie du fichier
raw. Ces données du capteur ne ressemblent pas à une image, en fait,
elles ne ressemble à rien, ce sont des données brutes (raw en anglais),
d'où le nom. Elles doivent être "cuisinées" pour ressembler à l'image
que vous avez vue dans le viseur. L'appareil photo cuisine les données
raw pour un faire une belle image qui est enregistrée dans un fichier
JPEG à l'intérieur du fichier raw (assurément, même si vous utilisez le
mode "RAW" seul, par opposition au mode "RAW+JPEG"). En raison de ce
fait fondamental que les données sont "raw", une photo raw n'a pas qu'un
seul aspect correct, l'aspect donné par votre appareil n'est pas
"l'aspect parfait", ni le seul possible. Cependant, beaucoup de
photographes souhaitent utiliser "l'aspect donné par l'appareil" comme
point de départ pour les ajustements ultérieurs et RawTherapee rend cela
possible.

Lors de l'affichage dans [Le Navigateur de
fichiers](/The_File_Browser_Tab) d'une photo raw qui n'a
jamais encore été éditée dans RawTherapee, la vignette de la photo
s'appuie sur l'image JPEG intégrée dans le fichier raw, c'est exactement
la même image que vous voyez affichée sur votre appareil photo et dans
la plupart des autres logiciels. Une fois cette photo ouverte dans
[L’Éditeur](the_image_editor_tab), RawTherapee crée une
nouvelle vignette basée sur les données raw actuelles. Puisque la
création d'une image depuis les données raw demande de la "préparation",
et puisque vous n'avez pas encore édité manuellement cette image,
RawTherapee la traite en utilisant les paramètres du [profil de
traitement par défaut pour les photos
raw](/Preferences#Paramètres_de_traitement_d'image_par_défaut).
A partir de ce moment, la vignette de la photo n'est plus basée sur le
JPEG intégré mais sur les données raw actuelles. La vignette reflète
maintenant les modifications que vous faites sur l'image dans l’Éditeur.

L'édition est réalisée dans
[L'Editeur](the_image_editor_tab/fr). C'est ici que vous
travaillez avec Rawtherapee pour créer de stupéfiants chefs d’œuvres
graphiques, ou peut-être plus simplement pour apporter les premiers
soins à vos prises de vues. Lors de l'ouverture d'une photo raw dans
l'Éditeur pour la première fois, le [profil de traitement par défaut
pour les photos
raw](/Preferences#paramètres-de-traitement-dimage-par-défaut)
est appliqué, lequel depuis RawTherapee 5.4 est réglé sur "Auto-Matched
Curve - ISO Low" (a moins que vous ne l'ayez changé dans les
Préférences) et il règle automatiquement votre photo raw pour qu'elle
ressemble au JPEG fourni par l'appareil photo. Il y parvient en
analysant l'image JPEG créée par l'appareil et qui est intégrée dans le
fichier raw, et en adaptant la courbe tonale pour y correspondre. La
plupart du temps, la correspondance est très proche. Dans de rares cas,
cela peut échouer. Voir l'article [Auto-Matched
Curve](/auto-matched_curve) pour plus de détailes.

{{< figure src="/images/rt_setm_editor.png" >}}

Prenez le temps de faire le tour de cet onglet Editeur.

Remarquez qu'il y a des onglets à l'intérieur de cet onglet, à droite de
l'écran, vers le haut, ces onglets ainsi que les curseurs de contrôle
en-dessous forment la boite à outils. A la première utilisation, vous
avez certainement le premier onglet d'ouvert et si vous le survolez avec
la souris, vous découvrez qu'il s'appelle l'onglet Exposition. En
dessous de ce choix d'onglets, se trouvent les outils contenus par
l'onglet choisi : Exposition, Ombres/Hautes lumières, Compression
tonale, etc. Si vous cliquez sur l'un d'eux, il se déploie et permet de
voir son contenu. Cliquez de nouveau, il se referme. Cliquez droit sur
l'un des outils, et celui_ci s'ouvre alors que tous les autres se
ferment, un raccourci pour gagner du temps. A gauche de chaque titre
d'outil, il y a le bouton d'activation
![](/images/power-on-small.png)
marche /
![](/images/power-off-small.png)
arrêt) qui vous autorise d'activer ou de désactiver ledit outil, ou dans
certains cas, à la place du bouton d'activation, il y a l’icône
triangulaire
![](/images/expander-closed-small.png)
d'ouverture/fermeture de l'outil. Lire le chapitre [Outils de la page
Commentaires généraux à propos de certains éléments d'interface
grapPowerhique (Widgets) de la boite à
outils](/General_Comments_About_Some_Toolbox_Widgets/#outils)
pour des explications détaillées.

Naviguez au travers des onglets et des panneaux jusqu'à vous sentir
totalement ébloui par tout ce qui existe.

Avant de commencer à travailler sur une image, voici un bon conseil :
**Ne pas paniquer !** Vous ne risquez pas de détruire par erreur l'une
de vos images primées. RawTherapee possède certaines spécificités pour
vous aider à protéger vos images :

- RawTherapee procède à une édition non destructive de vos fichiers raw.
  Cela signifie que jamais, non jamais, RawTherapee ne modifiera le
  fichier raw lui-même. Toutes les modifications sont enregistrées dans
  des fichiers accolés. Vous pouvez en savoir plus à ce sujet dans la
  page de Rawpedia [Fichiers accolés – Profils de
  traitement](/Sidecar_Files_-_Processing_Profiles).
- Lors de l'utilisation de l'Editeur, vous pouvez voir le panneau
  [Historique](/the_image_editor_tab#historique) sur la
  gauche. Ce panneau affiche la pile de l'historique de tous les
  changements réalisés sur l'image. Pour revenir à n'importe quelle
  étape des modifications (y compris celle originale du premier
  chargement de l'image), il suffit de cliquer sur la ligne
  correspondante dans le panneau de l'historique.
- Sous le panneau Historique, il y a le panneau
  [Captures](/the_image_editor_tab#captures). Vous pouvez
  l'oublier pour l'instant, mais vous le trouverez pratique avec un peu
  plus d'expérience de RawTherapee. Ce panneau enregistre l'état de tous
  les outils à un moment donné sous forme d'une "capture". Cela vous
  permet par exemple de facilement peaufiner votre photo en une image
  agréable et colorée et de prendre une capture, puis de la modifier en
  un charmant noir et blanc et de prendre une nouvelle capture puis de
  comparer les deux simplement en cliquant sur chaque capture. (Note:
  RawTherapee n'enregistre pas encore les captures dans les fichiers
  PP3, il le fera dans le futur. Si vous désirez sauvegarder trois
  captures, vous devez cliquer dessus et sauvegarder à chaque fois un
  fichier PP3 sous un même nom).
- Comme vous le supposez sans doute, Contrôle-z annule la dernière
  modification.

### Fondamentaux

1.  Ouvrir la photo raw. RawTherapee la présente automatiquement
    ressemblant à la photo de sortie de l'appareil. Si le résultat vous
    satisfait, vous avez terminé. Sinon, continuez la lecture.
2.  Cliquer sur l'onglet Couleur
    ![](/images/color-circles.png)
    puis ouvrir l'outil [Balance de blancs](/white_balance)
    par un clic droit (ou utilisez le [raccourci
    clavier](/Keyboard_Shortcuts) ). RawTherapee va
    démarrer avec la balance des blancs utilisée par votre appareil
    photo. Le plus souvent, le réglage de la balance Powerdes blancs
    exige d'agir sur les curseurs Température et Teinte, ou d'utiliser
    la pipette Point de mesure
    ![](/images/color-picker.png)
    sur une zone sans couleur (gris neutre). Ajuster à son goût.
3.  Ensuite, régler l'exposition en allant dans l'onglet Exposition
    ![](/images/exposure.png) ouvrir
    l'outil [Exposition](/exposure) et ajuster à son goût.
    Pour l'instant, se limiter aux curseurs Compensation d'exposition et
    Saturation.
4.  Si votre photo est bruitée, passez sur l'onglet Détail
    ![](/images/detail.png), zoomez à 100%
    soit à l'aide du bouton
    ![](/images/magnifier-1to1.png)
    ou à l'aide du raccourci clavier , car les effets des outils de cet
    onglet ne sont visibles dans l'aperçu que si celui-ci est zoomé à
    100% (et visibles aussi bien sûr dans l'image sauvegardée), et
    activez l'outil [Réduction du bruit](/noise_reduction)
    en cliquant sur le bouton d'activation
    ![](/images/power-on-small.png),
    laissant pour l'instant les paramètres à leur valeur par défaut.
    RawTherapee a enlevé automatiquement le bruit de couleur
    (chrominance). Le bruit de Luminance est retiré
    [manuellement](/noise_reduction#usage), mais laissez le
    pour l'instant, car le bruit de luminance procure un bel aspect
    présentant du grain comme avec le film. En règle générale, avec
    l'utilisation de la réduction du bruit, ne pas utiliser l'outil
    Netteté. Zoomer arrière pour visualiser toute l'image soit avec le
    bouton
    ![](/images/magnifier-fit.png)
    ou avec la raccourci clavier .
5.  Maintenant on peut passer à l'amélioration de la
    [géométrie](/lens/geometry) et de la composition de la
    photo.
    - Commencer par régler l'horizon, ou bien des choses qui doivent
      être verticales comme des lampadaires de rue ou des arêtes
      d'immeuble. Pour effectuer cela facilement, appuyer sur la touche
      "s" du clavier (même action que le bouton
      ![](/images/rotate-straighten.png)),
      et cliquer-glisser sur l'aperçu pour tracer une ligne le long de
      l'horizon ou le long de l'arête de l'immeuble. L'image pivotera en
      conséquence et vous serez automatiquement amené dans l'onglet
      Transformation
      ![](/images/transform.png).
    - Pour recadrer la photo, appuyer sur le raccourci clavier (ou bien
      utiliser le bouton ![](/images/crop.png))
      et cliquer-glisser sur l'aperçu pour former le cadre; vous
      remarquerez que l'outil [Recadrage](/crop) s'active
      automatiquement. Il est inutile d'"appliquer" un recadrage, il
      prend effet dès l'instant où il est tracé. Pour adapter la vue à
      la zone recadrée, vous pouvez zoomer en utilisant le raccourci
      clavier , ou + pour adapter l'image entière. Vous pouvez choisir
      "Aucun" pour le "Type de guide" s'il pose problème.
    - Enfin, vous pouvez diminuer la résolution car vous ne pouvez pas
      envoyer une image JPEG de 10Mo sur votre réseau social. Activez
      l'outil [Redimensionnement](/resize) et l'outil
      [Netteté après
      redimensionnement](/Resize#netteté-après-redimensionnement)
      et laissez les valeurs par défaut. Le redimensionnement n'est
      appliqué que sur l'image enregistrée, pas sur l'aperçu, aussi vous
      ne verrez aucun changement dans l'aperçu lors de l'activation de
      ces outils.
6.  Vous en avez terminé, [Enregistrez](/saving) dès
    maintenant. Cliquez sur le bouton Enregistrer l'image courante
    ![](/images/save.png), ou bien utilisez le
    raccourci clavier +. Enregistrez au format JPG en gardant les
    paramètres par défaut (qualité à "92", sous-échantillonnage à
    "Équilibre"). Ce sont de bons réglages universels. Choisir un
    dossier où vous désirez placer l'enregistrement, et après quelques
    secondes votre fichier sera prêt dans le dossier choisi. Si vous
    fermez RawTherapee, les paramètres utilisés seront enregistrés dans
    un [fichier accolé
    PP3](/Sidecar_Files_-_Processing_Profiles) placé auprès
    du fichier raw, ainsi, à l'avenir vous pouvez ré-ouvrir la photo raw
    et reprendre les paramètres des outils utilisés.

Maintenant que vous avez découvert les réglages fondamentaux en
photographie et que vous vous êtes familiarisé avec les différentes
étapes, reprenons ces étapes avec des réglages plus élaborés.

### Avancé

Toujours lire ici sur Rawpedia la documentation d'un outil avant de
l'utiliser pour bien comprendre ce qu'il fait. Les articles expliquent
le fonctionnement des outils dans RawTherapee, alors que la découverte
des concepts généraux non spécifiques à RawTherapee est laissée à
l'initiative des utilisateurs avec l'aide de Wikipedia ou autre.

Bien connaître les [Raccourcis
clavier](/Keyboard_Shortcuts).

L'ordre de traitement des outils à l'intérieur du pipeline du moteur de
RawTherapee est codé en dur, ainsi, de ce point de vue, cela n'a pas
d'importance que vous activiez ou désactiviez un outil. Cependant,
certains outils peuvent provoquer des impacts importants sur d'autres
outils, par exemple, la modification de l'exposition peut nécessiter de
retoucher le virage partiel, et certains outils peuvent monopoliser
toute la puissance du processeur pour calculer l'aperçu rendant le
rafraichissement très lent, pour ces raisons nous vous suggérons de bien
suivre cet ordre général des opérations :

1.  Commencez par vous assurer que l'environnement de RawTherapee est
    correctement configuré, c'est à dire :
    - Vous assurer que RawTherapee utilise le profil couleur de votre
      écran si vous utilisez un processus avec gestion de la couleur.
      Vérifier dans Préférences \> Gestion de la couleur. Il peut aussi
      être utile de charger les courbes de calibration appropriées dans
      votre carte graphique si vous les utilisez pour construire le
      profil couleur de votre écran, la façon de procéder sort du cadre
      de RawTherapee.
    - Vous assurer que l'outil Gestion de la couleur est correctement
      configuré. En général les valeurs par défaut conviennent. Lire les
      pages [Gestion de la couleur](/color_management) et
      [Gestion de la couleur -
      Supplément](/Color_Management_addon). Si au lieu
      d'utiliser un profil matrice couleur ou DCP ou ICC livrés avec
      RawTherapee vous décidez d'utiliser un profil externe, par exemple
      un DCP fait par vous même ou bien de chez Adobe, chargez le en
      premier, sinon, vous aurez probablement à revenir sur certains
      outils traitant la couleur. Toujours utiliser un profil de sortie,
      le plus souvent celui par défaut : RT_sRGB. Si vous pensez bien
      faire en sélectionnant "Pas d'ICM : sortie sRGB", vous faites
      erreur.
2.  Si vous avez l'intention d'utiliser une image [Champ
    Uniforme](/Flat_Field) et/ou [Trame
    Noire](/Dark_Frame), faites le maintenant pour éviter
    de recommencer certains réglages.
3.  Régler maintenant la [Balance des
    Blancs](/White_Balance). Vous pouvez régler
    l'exposition avant si l'image est trop foncée ou trop claire pour
    voir les effets de la balance des blancs.
4.  Régler maintenant l'[Exposition](/exposure), à l'aide
    des curseurs Compensation d'exposition et Noir pour amener l'image
    dans la bonne fourchette. Une fois dans la bonne fourchette,
    continuer en utilisant les deux courbes tonales. Bien lire [le
    chapitre Courbe Tonale](/Exposure#courbes-tonales) dans
    la page Exposition pour comprendre la raison pour laquelle il existe
    deux courbes et apprendre à s'en servir. Ce sont de formidables
    outils !
5.  Dans la section "Fondamentaux" ci-dessus nous avons suggéré
    l'utilisation du curseur
    [Saturation](/exposure#saturation) (dans l'outil
    Exposition). Maintenant que vous connaissez les fondamentaux et que
    vous explorez des techniques plus évoluées, nous vous conseillons de
    ne plus utiliser le curseur Saturation, mais de le remplacer par la
    plus performante [Courbe
    CC](/Lab_Adjustments#courbe-cc) de l'outil [Ajustements
    Lab](/Lab_Adjustments), car elle autorise un contrôle
    plus fin.
6.  L'ordre pour le reste n'est pas défini. Certains outils vont
    inévitablement en influencer d'autres. Continuer avec l'outil
    [Ajustements Lab](/lab_adjustments) puis le reste des
    outils de l'onglet Exposition.
7.  Puis les outils de l'onglet Couleur
    ![](/images/color-circles.png).
8.  Zoomer maintenant à 100% et utilisez les outils de l'onglet Détail
    ![](/images/detail.png). En général, ne
    pas utiliser la Netteté si vous utilisez la Réduction du bruit.
9.  Enfin, zoomer arrière de nouveau et utiliser les outils de l'onglet
    Transformation
    ![](/images/transform.png). La
    raison pour laquelle ces outils sont utilisés en dernier est qu'ils
    peuvent rendre l'aperçu d'apparence légèrement floue floue, car dans
    le but de garder l'aperçu réactif, RawTherapee utilise une
    résolution très faible pour montrer l'action de l'outil, et quand
    vous tournez ou appliquez des modifications de géométrie à une
    petite image, c'est évidemment plus rapide. Il n'y pas de problème
    pour la sauvegarde car à ce niveau RawTherapee réalise le traitement
    sur l'image en pleine résolution, ce qui est lent mais garanti la
    plus haute qualité.
10. Vous pouvez à tout moment éditer les métadonnées dans l'onglet
    ![](/images/metadata.png)
    [Meta](/metadata_copy_mode) a tout moment avant de
    sauvegarder.
11. Enregistrer, soit directement
    [<file:save.png>](file:save.png) lorsque vous désirez
    enregistrer une photo seule, ou bien via
    [<file:gears.png>](file:gears.png) [La file
    d'attente](/the_batch_queue) lorsqu'il y a plusieurs
    photos. Voir l'article [Enregistrer les
    images](/saving_images)
