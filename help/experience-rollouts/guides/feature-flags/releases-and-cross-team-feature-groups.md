---
title: Releaser och teamöverskridande funktionsgrupper
description: Lär dig skillnaden mellan releaser och funktionsgrupper för flera team i Adobe Experience Rollouts och när de ska användas för samordnade driftsättningar för flera team.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Releaser och teamöverskridande funktionsgrupper {#releases-and-cross-team}

Både releaser och teamöverskridande funktionsgrupper har stöd för samordnade lanseringar i flera team och program. Det rätta valet beror på era krav på cachning, målgruppsanpassning och hur mycket kontroll ni vill ha över processen.

## Teamövergripande funktionsgrupper {#cross-team-feature-groups}

Med en funktionsgrupp för flera team kan ni paketera funktionsflaggor från program som ägs av olika team och hantera dem med omfattande målgruppskriterier.

Viktiga egenskaper:

* **Självbetjäning** - Ingen supportbegäran krävs för att skapa en
* **Rikt målgruppsanpassning** - Stöder alla målgruppskriterier (profilattribut, kontextvariabler, procentuell utrullning)
* **Ingen begränsning** för det nummer du kan skapa
* **Ingen cachelagring** - Utvärderingar av funktionsflaggor kräver ett API-anrop. Cachelagring på SDK-nivå stöds inte

Instruktioner om hur du skapar steg för steg finns i [Skapa en funktionsgrupp för flera team](create-cross-team-feature-group.md).

## Utgåvor {#releases}

En release är avsedd för stora, samordnade starter där cachelagring på SDK-nivå krävs. Releaser använder tokenbaserad målgruppsanpassning för autentisering.

Viktiga egenskaper:

* **Kräver en supportförfrågan** - Versioner är inte helt självbetjänade. Kontakta Experience Rollouts-support för att skapa en.
* **SDK-cachning** - Alla versionsdata cachelagras lokalt i SDK-servern, vilket reducerar API-anrop
* **Begränsade målgruppskriterier** - Målgruppsregler baseras på autentiseringstoken (land, e-post, användar-ID, procent osv.)
* **Begränsade aktiva releaser** - Det kan finnas ett begränsat antal aktiva releaser i taget; du kan planera att stänga eller basera releaser inom tre månader

## Jämförelse {#comparison}

| | Teamöverskridande funktionsgrupp | Frigör |
|---|---|---|
| Självbetjäning | ✓ | Kräver supportbegäran |
| Rika målgruppskriterier | ✓ | Begränsad |
| A/B-tester | ✗ | ✗ |
| SDK cachning | ✗ | ✓ |
| Aktiv gräns | Ingen gräns | Begränsad |

## Rekommendation {#recommendation}

Om ditt användningsexempel omfattar omfattande målgruppsanpassning och självbetjäningshantering kan du använda en **funktionsgrupp för flera team**. Om dina backend-tjänster kräver cachelagring på SDK-nivå och de enklare villkoren för publicering är tillräckliga, använder du en **release**.

## Se även {#see-also}

* [Funktioner, funktionsgrupper och releaser](features-feature-groups-releases.md)
* [Skapa en funktionsgrupp för flera team](create-cross-team-feature-group.md)
* [Begär en release](request-a-release.md)
