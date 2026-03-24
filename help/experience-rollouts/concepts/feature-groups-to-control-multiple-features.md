---
title: Funktionsgrupper som styr flera funktioner
description: Lär dig hur funktionsgrupper i Experience Rollouts gör att ni kan paketera och hantera relaterade funktionsflaggor i olika program som en enda enhet.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Funktionsgrupper som styr flera funktioner {#feature-groups}

En [funktionsflagga](what-is-a-feature-flag.md) styr en enskild funktion. När du behöver hantera flera relaterade funktionsflaggor tillsammans - och se till att de når samma målgrupp - använder du en **funktionsgrupp**.

## Vad en funktionsgrupp gör {#what-it-does}

En funktionsgrupp innehåller flera funktionsflaggor och gör att du kan tillämpa en enda målgruppsregel på alla samtidigt. Detta är användbart när en enskild användarriktad funktion sträcker sig över flera program eller tjänster.

Ta till exempel en samarbetsfunktion som innefattar ändringar i ett datorprogram, en mobilapp och en serverdelstjänst. Genom att skapa en funktionsgrupp med flaggor från alla tre programmen kan du öppna funktionen för 1 % av användarna - och se till att användarna ser en enhetlig upplevelse på alla tre ytorna samtidigt.

## Gruppering mellan program {#cross-application}

Funktionsgrupper har stöd för funktionsövergripande hantering mellan program så länge flaggorna tillhör **samma team** i Experience Rollouts. Ett team kan äga flera program, så att relaterade flaggor i alla dessa program kan grupperas tillsammans.

## Funktionsgrupper jämfört med releaser {#vs-releases}

| | Funktionsgrupp | Frigör |
|---|---|---|
| Omfång | Inom ett och samma team | Över flera team |
| Använd skiftläge | Koordinera flaggor i ditt team | Samordning mellan stora team för att starta |
| Behörighet krävs | Teamnivå | Högre (versionshanteraren) |

Om de funktionsflaggor som du vill gruppera tillhör program som ägs av olika team använder du en [release](release-management.md) i stället för en funktionsgrupp.
