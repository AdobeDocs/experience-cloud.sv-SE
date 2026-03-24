---
title: Hantera program
description: Lär dig hantera program i Adobe Experience Rollouts, inklusive att lägga till nya program och förstå teamets ägarskap.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Hantera program {#manage-applications}

Ett **program** i Experience Rollouts representerar tjänsten eller produkten som du vill kontrollera med funktionsflaggor. Innan ditt team kan skapa funktionsflaggor måste du ta med minst ett program till konsolen.

## Vem kan hantera program? {#permissions}

Endast medlemmar med rollen **Admin** kan lägga till eller ändra program. Kontakta teamadministratören om du inte har den här rollen.

## Lägga till ett program {#add-application}

Om du vill lägga till ett program i ditt team kan du läsa [Anpassa programmet](onboard-your-application.md) för steg-instruktioner.

## Teamägarskap {#team-ownership}

Varje program ägs av exakt ett team. Endast medlemmar i det teamet kan hantera programmets funktionsflaggor.

Den här ägarskapsmodellen påverkar även hur du strukturerar funktionsgrupper:

* **Inom ditt team** - En produktversionsägare kan gruppera funktionsflaggor för program som ägs av samma team. Se [Funktionsgrupper för att styra flera funktioner](../../concepts/feature-groups-to-control-multiple-features.md).
* **Över flera team** - Om du behöver gruppera funktionsflaggor från program som ägs av olika team kan du använda en teamövergripande funktionsgrupp som kräver rollen **Funktionsadministratör**.

## Se även {#see-also}

* [Anpassa applikationen](onboard-your-application.md)
* [Funktionsgrupper som styr flera funktioner](../../concepts/feature-groups-to-control-multiple-features.md)
* [Användarroller](../teams/user-roles.md)
