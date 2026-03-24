---
title: Adobe Experience Rollouts
description: Lär dig hur du använder Adobe Experience Rollouts för att leverera funktioner på ett säkert och gradvis sätt med kontrollerade utrullningar, funktionsflaggor och målinriktad målgruppshantering.
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: 65effd7e3b12404359e3693820bbf9e5080bea03
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Adobe Experience Rollouts {#experience-rollouts-home}

Med Adobe Experience Rollouts kan produktteamen leverera nya funktioner gradvis och säkert - utan omdistributioner eller driftavbrott. Du definierar vem som ser vad, när och i vilken takt. Om något går fel stänger du av funktionen direkt. Om det går bra kan ni utöka publiken enligt ert schema.

## Vad du kan göra

**Styr vilka som ser nya funktioner.** Målreleaser för specifika användare, organisationer, regioner eller anpassade attribut. Börja med en liten grupp, validera upplevelsen och utöka sedan - allt från konsolen, utan kodändringar.

**Kör A/B-experiment.** Leverera olika varianter till olika målgruppssegment och mät vilka som fungerar bättre. Använd resultatet för att fatta välgrundade produktbeslut före en fullständig version.

**Minska versionsrisken.** Dela upp stora ändringar i mindre, kontrollerade rollouter. Om ett fel eller prestandaproblem uppstår inaktiverar du bara den påverkade funktionen - resten av programmet förblir stabilt.

**Koordinera mellan team.** Med funktionsgrupper för olika team kan flera team delta i en enda samordnad release där var och en hanterar sina egna funktionsflaggor samtidigt som de delar ett gemensamt lanseringsschema och målgrupp.

## Använd din första funktion

Det börjar med tre steg att få värde från upplevelseutrullningar:

1. **Konfigurera ditt team och program** - [Begär åtkomst](guides/console/request-access.md) till konsolen och [anslut sedan programmet](guides/applications/onboard-your-application.md) så att Experience Rollouts vet vilka klienter som ska betjänas.

2. **Skapa och publicera en funktionsflagga** - Följ guiden [Skapa din första funktionsflagga](guides/feature-flags/create-your-first-feature-flag.md) för att definiera en flagga, ange din ursprungliga målgrupp och publicera den i din miljö.

3. **Integrera med ditt program** - Anslut din app till API:t för upplevelseutrullningar eller SDK så att den kan hämta och använda funktionsflaggor vid körning. Börja med [integreringsstegen](guides/integrate/integration-steps.md) för programtypen.

När din första flagga är aktiv kan du förfina dess målgrupp, konfigurera en gradvis utrullning och marknadsföra den genom [releaselägen](guides/feature-flags/release-states.md) från sparad till fullständig utrullning.

## Behöver du hjälp?

Om något inte beter sig som förväntat innehåller [felsökningsguiden](guides/support/troubleshooting.md) de vanligaste problemen. Om du vill ha mer information [kontaktar du support](guides/support/contact-support.md).
