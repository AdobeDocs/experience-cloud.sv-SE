---
title: Använd företagsorganisationsdata i målgruppsregler
description: Lär dig hur du använder företagsorganisations-ID:n som målgruppskriterier i Adobe Experience Rollouts för att rikta dig till specifika kundorganisationer.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# Använd företagsorganisationsdata i målgruppsregler {#enterprise-org-data}

Experience Rollouts har stöd för målgruppsanpassade användare baserat på deras företags-ID. På så sätt kan ni introducera funktioner för specifika kundorganisationer innan de blir allmänt tillgängliga.

## Lägga till en organisation i en målgruppsregel {#adding-org-rule}

Företagsgruppsanpassning är tillgängligt på fliken **Målgrupp** under **Målgruppsregler > Profil > Företag**.

Två sorttyper stöds:

### DME-organ {#dme-orgs}

DME-organ identifieras av deras organisations-ID. När du skapar regeln anger du bara organisations-ID:t - inkludera ingen auth-källa.

### DMA-organ {#dma-orgs}

DMA-organ använder org-ID:n i formatet `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG`. När du anger ett DMA-organisations-ID:

* Använd det fullständiga organisations-ID:t inklusive suffixet `@ADOBEORG`.
* Ange `ADOBEORG` i versaler.

**Exempel:** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## Viktiga anteckningar {#important-notes}

* Organisationsbaserad målgruppsanpassning utvärderas mot den organisation som är associerad med användarens autentiserade session. Se till att användaren är inloggad på rätt organisation vid testning.
* Om en organisation som du väntar dig att hitta inte visas i målgruppsvillkoren, eller om funktioner inte returneras som förväntat för en viss organisation, kontaktar du Experience Rollouts support.
* Scen- och produktionsmiljöer kan skilja sig åt i vilka organ som är tillgängliga. Testa målgruppsreglerna på scenen innan du marknadsför till Production.

## Se även {#see-also}

* [Målgrupp i funktionsflaggor och funktionsgrupper](audience-in-feature-flags-and-feature-groups.md)
* [Uppdatera publiceringsregler](../feature-flags/update-release-audience-rules.md)
* [Komplexa målgruppsregler](complex-rules.md)
