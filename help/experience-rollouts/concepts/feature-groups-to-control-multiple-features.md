---
title: Funktionsgrupper som styr flera funktioner
description: Lär dig hur funktionsgrupper i Experience Rollouts gör att ni kan paketera och hantera relaterade funktionsflaggor i olika program som en enda enhet.
exl-id: dfeb7eff-34f1-4cb5-9c3e-a40d1eda3016
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Funktionsgrupper som styr flera funktioner {#feature-groups}

En [funktionsflagga](what-is-a-feature-flag.md) styr en enskild funktion. När du behöver hantera flera relaterade funktionsflaggor tillsammans - och se till att de når samma målgrupp - använder du en **funktionsgrupp**.

## Vad en funktionsgrupp gör {#what-it-does}

En funktionsgrupp innehåller flera funktionsflaggor och gör att du kan tillämpa en enda målgruppsregel på alla samtidigt. Detta är användbart när en enskild användarriktad funktion sträcker sig över flera program eller tjänster.

Ta till exempel en samarbetsfunktion som innefattar ändringar i ett datorprogram, en mobilapp och en serverdelstjänst. Genom att skapa en funktionsgrupp med flaggor från alla tre programmen kan du öppna funktionen för 1 % av användarna - och se till att användarna ser en enhetlig upplevelse på alla tre ytorna samtidigt.

## Gruppering mellan program {#cross-application}

Funktionsgrupper har stöd för funktionsövergripande hantering för flera program. Relaterade flaggor mellan flera program kan grupperas tillsammans.

