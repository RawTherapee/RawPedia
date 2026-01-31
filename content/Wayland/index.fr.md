---
title: Wayland
contributors:
  - Lebarhon
tags:
  - 'Troubleshooting'
---

<div class="pagetitle">

Wayland

</div>

Les utilisateurs de Wayland, un protocole informatique qui définit la
communication entre un serveur d'affichage (appelé compositeur Wayland)
et ses clients, peuvent subir des aléas d'affichage au niveau de
l'interface utilisateur de RawTherapee; par exemple toutes les boites de
dialogue (telles que le sélecteur du Profile de traitement, la liste
déroulante Simulation de film, etc.) ne fonctionnent correctement que la
première fois qu'elles sont utilisées, puis ne répondent plus jusqu'au
redémarrage de RawTherapie. Ce n'est pas un bogue de RawTherapee.

Les rapports indiquent que la cause vient d'une incompatibilité entre
GTK+ et le compositeur Wayland.

Les utilisateurs des distributions suivantes ont le plus de chances
d'être affectés :

- Fedora \>=25
- Ubuntu 17.10 (Ubuntu 18.04 revenu à X11 en raison des problèmes de
  Wayland)

Il est conseillé aux utilisateurs concernés de :

- Essayer de basculer sur le compositeur Weston.
- Revenir à X11 si les problèmes persistent.

Pour plus d'informations :

  
<https://fedoraproject.org/wiki/How_to_debug_Wayland_problems>

Notez que certaines informations contenues dans le document ci-dessus
peuvent ne pas être à jour.
