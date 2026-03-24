---
title: Miljööversikt
description: Lär dig mer om scen- och produktionsmiljöerna i Adobe Experience Rollouts och när du ska använda respektive.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 1%

---


# Miljööversikt {#environments}

Med Experience Rollouts får du olika miljöer så att du kan validera funktionsflaggorna innan du marknadsför ändringarna till dina Live-användare.

## Tillgängliga miljöer {#available-environments}

| Miljö | Syfte |
|---|---|
| **Scen** | Testning och validering. Använd den här miljön för att konfigurera och testa funktionsflaggor innan du aktiverar dem i Produktion. |
| **Produktion** | Live-utrullningar. De funktionsflaggor som konfigureras här utvärderas mot din verkliga användarbas. |

>[!IMPORTANT]
>
>Ändringar som görs på scenen överförs inte automatiskt till Produktion. Funktionsflaggor och målgruppsregler måste konfigureras separat i varje miljö.

## Välja en miljö {#selecting}

När du har loggat in på Experience Rollouts-konsolen väljer du miljön från miljöväljaren högst upp i gränssnittet. Kontrollera att du arbetar i rätt miljö innan du skapar eller ändrar funktionsflaggor.

## God praxis {#best-practices}

Följ dessa rekommendationer för att undvika konfigurationsfel och skydda produktionspubliken:

* Skapa och testa alltid funktionsflaggor i **Stage** först.
* Validera målgruppsregler, procentuella utrullningar och målinriktningslogik på scenen innan du replikerar i produktionen.
* Använd [arbetsflödet mellan miljöer](../cross-environment/cross-environment-concept.md) för att visa och hantera flaggstatus i olika miljöer.

## Se även {#see-also}

* [Logga in på konsolen](log-in-to-the-console.md)
* [Koppla miljöer till ett program](../cross-environment/associate-environments.md)
* [Visa funktionsflaggor i olika miljöer](../cross-environment/view-feature-flags-across-environments.md)
