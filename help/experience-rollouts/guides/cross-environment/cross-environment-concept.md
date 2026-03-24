---
title: Koncept för flera miljöer
description: Läs om hur du med funktionerna för olika miljöer i Adobe Experience Rollouts kan länka program mellan olika miljöer och hantera funktionsflaggor på ett enhetligt sätt, från utveckling till produktion.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Koncept för flera miljöer {#cross-environment-concept}

Med funktioner för olika miljöer kan ni länka era programinstanser till olika distributionsmiljöer - som QA, Stage och Production - och hantera funktionsflaggor på ett enhetligt sätt i alla applikationer från Experience Rollouts.

## Problemet med miljööverskridande lösningar {#problem}

Utan miljölänkning är varje programinstans i Experience Rollouts helt oberoende av dess motsvarigheter i andra miljöer. Detta skapar flera friktionspunkter:

* Ett program med namnet `my-app` på scenen har ingen relation till `my-app` i produktionen - de behandlas som separata, icke-relaterade program.
* Du kan inte visa status för en funktionsflagga på scenen när du arbetar i produktion. Du måste växla miljöer manuellt för att jämföra flagglägen.
* Om du vill importera en konfiguration med en funktionsflagga från en lägre miljö till en högre måste du återskapa den manuellt.

## Vad är det som fungerar i olika miljöer? {#what-it-enables}

Genom att länka programinstanser mellan miljöer kan teamet

* Definiera vilken av programmets distributionsmiljöer som miljöerna i Experience Rollouts ska mappas till
* Använd anpassade miljöetiketter (till exempel `Dev`, `Staging`, `Prod`) som matchar teamets namnkonventioner
* Visa status för en funktionsflagga i alla länkade miljöer från en enda vy
* Importera funktionsflaggor från en lägre miljö till en högre med några klick - utan att behöva återskapa dem manuellt

## Hur miljöer är strukturerade {#environment-structure}

Experience Rollouts har två plattformsmiljöer: **Stage** och **Production**. Ditt program kan dock ha fler miljöer, till exempel QA, Förproduktion och Produktion. Tack vare länkningen mellan olika miljöer kan du bestämma var varje programmiljö finns:

* QA- och mellanlagringsmiljöer kan finnas på scenen Experience Rollouts eller i produktionsmiljön.
* Produktionsmiljöer måste ligga i produktionsmiljön Experience Rollouts.

Den här flexibiliteten innebär att du inte tvingas in i en mappning som passar alla.

## Nästa steg {#next-steps}

* [Koppla miljöer till ett program](associate-environments.md) - konfigurera länkarna mellan programinstanserna
* [Visa funktionsflaggor i olika miljöer](view-feature-flags-across-environments.md) - övervaka flaggstatus i alla länkade miljöer
* [Importera funktionsflaggor](import-feature-flags.md) - höj upp funktionsflaggor från lägre till högre miljöer
