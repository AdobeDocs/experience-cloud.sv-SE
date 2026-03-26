---
title: Funktioner och funktionsgrupper
description: Lär dig mer om skillnaderna mellan funktionsflaggor och funktionsgrupper i Adobe Experience Rollouts och när du ska använda respektive.
source-git-commit: c654ca1507abcefcff84cef9f99830042939805d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Funktioner och funktionsgrupper {#features-feature-groups}

Upplevelseutrullningar ger två artefakter för att hantera rollouts för funktioner. Vilken som är rätt beror på omfånget och antalet funktioner.

## De två artefakterna {#artifacts}

**Funktionsflagga**
Den mest atomiska enheten. Styr en enskild funktion för ett enstaka program. Kan aktiveras eller inaktiveras för en angiven målgrupp.

**Funktionsgrupp**
En samling funktionsflaggor som tillhör samma team. Tillåter hantering av flera flaggor i flera program som en enda enhet.

## Jämförelse {#comparison}

| | Funktionsflagga | Funktionsgrupp |
|---|---|---|
| **Roll som krävs för att hantera målgrupp** | Ägare till produktreleaser | Ägare till produktreleaser |
| **Program** | Enkelt | Flera (samma team) |
| **Omfattande målgruppskriterier** | ✓ | ✓ |
| **Procentandel av utrullning** | Kombinerat med alla målgruppskriterier | Kombinerat med alla målgruppskriterier |
| **A/B-testning** | ✓ | ✓ |
| **Självbetjäning** | ✓ | ✓ |
| **Granskningsspår** | ✓ | ✓ |

## När ska du använda {#when-to-use}

| Scenario | Använd |
|---|---|
| Testa eller rulla ut en enda funktion för ett program | **Funktionsflagga** |
| Samordna flera funktioner i samma team, live samtidigt | **Funktionsgrupp** |

## Se även {#see-also}

* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
