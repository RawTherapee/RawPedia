---
title: Shadows Highlights
contributors:
  - Lebarhon
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

<div class="pagetitle">

Ombres/Hautes lumières

</div>

## Introduction

Utilisez cet outil pour éclaircir les ombres ou assombrir les hautes
lumières d'une image.

Cette outil a reçu un nouveau moteur avec RawTherapee 5.5, il utilise
maintenant un [filtre "fast guided"](https://arxiv.org/abs/1505.00996)
sensible aux contours pour éviter les halos et opère par défaut dans
l'espace RVB pour préserver la saturation.

## Utilisation

A utiliser avec modération pour préserver un aspect naturel. Si la scène
photographiée présente une grande gamme dynamique (ombres très sombres
et hautes lumières très lumineuses) alors utiliser l'outil [Compression
de Plage Dynamique](Dynamic_Range_Compression/fr.md) pour
abaisser la gamme dynamique à un niveau plus facilement gérable, et
ensuite éventuellement appliquer l'outil Ombres/Hautes lumières par
dessus.

## Interface

### Espace colorimétrique

Ajuster les ombres et hautes lumières dans l'espace RVB préserve la
saturation de l'image qui en général demeure plus naturelle qu'en
travaillant dans l'espace L\*a\*b\*, lequel tend à dé-saturer certaines
zones. Cependant, dans certains cas, travailler dans l'espace RVB peut
sur-saturer les ombres, auquel cas vous devriez passer dans l'espace
L\*a\*b\*.

### Ombres

Permet d'éclaircir les parties les plus sombres de l'image

### Hautes lumières

Permet d'assombrir les parties les plus claires de l'image

### Amplitude tonale

L'amplitude tonale des hautes lumières permet de définir à partir de
quel niveau de clarté une zone sera affectée par le curseur hautes
lumières, et à partir de quel niveau d’assombrissement une zone sera
affectée par le curseur ombres. Bien que l'action mathématique impliquée
soit un peu plus compliquée, pensez à un histogramme, l'amplitude tonale
des hautes lumières spécifie l'étendue des tonalités depuis le blanc à
l'extrémité de l'histogramme qui seront affectées par le curseur hautes
lumières. Et l'amplitude tonale des ombres spécifie l'étendue des
tonalités depuis le noir à l'autre extrémité de l'histogramme qui seront
affectées par le curseur ombres. Plus l'amplitude tonale est importante
et plus les tonalités affectées sont nombreuses.

### Rayon

La valeur donnée par le curseur Rayon agit sur la zone d'action des
curseurs Ombres et Hautes lumières.
