---
title: Funktioner, funktionsgrupper och releaser
description: Lär dig mer om skillnaderna mellan funktionsflaggor, funktionsgrupper, teamöverskridande funktionsgrupper och releaser i Adobe Experience Rollouts och när de ska användas.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Funktioner, funktionsgrupper och releaser {#features-feature-groups-releases}

Experience Rollouts innehåller fyra artefakter för att hantera rollouts för funktioner. Vilken som är rätt beror på omfattningen av er utrullning, antalet medverkande team och vilka målgruppsanpassningsfunktioner ni behöver.

## De fyra artefakterna {#artifacts}

**Funktionsflagga**
Den mest atomiska enheten. Styr en enda funktion för ett enstaka program som ägs av ett team. Kan aktiveras eller inaktiveras för en angiven målgrupp.

**Funktionsgrupp**
En samling funktionsflaggor som tillhör samma team. Gör det möjligt att hantera flera flaggor i flera program i ett team som en enda enhet.

**Teamövergripande funktionsgrupp**
Utökar funktionerna i en grupp för flera team och program. Självbetjäning och stöd för avancerade målgruppskriterier, men stöder inte cachelagring.

**Utgåva**
Utformad för stora, koordinerade rollouter för flera team och program. Använder autentiseringsbaserad målgruppsanpassning. Stöder cachelagring på SDK-servern.

## Jämförelse {#comparison}

| | Funktionsflagga | Funktionsgrupp | Teamöverskridande funktionsgrupp | Frigör |
|---|---|---|---|---|
| **Roll som krävs för att hantera målgrupp** | Ägare till produktreleaser | Ägare till produktreleaser | Funktionsadministratör | Versionshanteraren |
| **Program** | Enkelt | Flera (samma team) | Flera (team emellan) | Flera (team emellan) |
| **Team** | Enkelt | Enkelt | Samarbeta | Samarbeta |
| **Omfattande målgruppskriterier** | ✓ | ✓ | ✓ | Begränsad |
| **Procentandel av utrullning** | Kombinerat med alla målgruppskriterier | Kombinerat med alla målgruppskriterier | Kombinerat med alla målgruppskriterier | Kombinerat med fasta målgruppskriterier |
| **A/B-testning** | ✓ | ✓ | ✗ | ✗ |
| **Cachelagring i server-SDK** | Endast standardflaggor för På/av | Ingen cachelagring | Ingen cachelagring | Alla versioner cachelagrade lokalt |
| **Självbetjäning** | ✓ | ✓ | ✓ | Kräver supportbegäran |
| **Granskningsspår** | ✓ | ✓ | ✓ | ✓ |

## När ska du använda {#when-to-use}

| Scenario | Använd |
|---|---|
| Testa eller rulla ut en enda funktion för ett program | **Funktionsflagga** |
| Samordna flera funktioner i samma team, live samtidigt | **Funktionsgrupp** |
| Samordna funktioner i olika applikationer i olika team, med avancerad målinriktning | **Teamövergripande funktionsgrupp** |
| Stor samordnad release för flera team, med cachelagring på SDK-nivå | **Utgåva** |

## Se även {#see-also}

* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [Skapa en funktionsgrupp för flera team](create-cross-team-feature-group.md)
* [Releaser och teamöverskridande funktionsgrupper](releases-and-cross-team-feature-groups.md)
