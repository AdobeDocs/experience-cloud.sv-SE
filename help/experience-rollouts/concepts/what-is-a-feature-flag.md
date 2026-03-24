---
title: Vad är en funktionsflagga?
description: Lär dig vilka funktionsflaggor som är och hur du kan aktivera och inaktivera programfunktioner under körning utan omdistribution.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Vad är en funktionsflagga? {#what-is-a-feature-flag}

En funktionsflagga är en mekanism som gör att du kan aktivera eller inaktivera funktioner i programmet under körning, utan att behöva omdistribuera kod.

Funktionen skiljer **koddistribution** från **funktionstillgänglighet** åt. Du kan skicka ny kod till produktion med funktionen dold bakom en flagga och sedan aktivera den när du vill - för alla användare eller för en viss delmängd.

Denna separation minskar avsevärt risken. Utvecklarna kan bygga och leverera kontinuerligt med minimala störningar, medan produktteamen behåller full kontroll över när och till vem en funktion blir synlig.

>[!NOTE]
>
>I Experience Rollouts är en funktionsflagga den mest atomiska enhetskontrollen. Den kan användas fristående för en enskild funktion, eller kombineras med andra flaggor i en [funktionsgrupp](feature-groups-to-control-multiple-features.md) eller [release](release-management.md).
