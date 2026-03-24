---
title: Datorprogram
description: Lär dig hur du integrerar Adobe Experience Rollouts i ett datorprogram med funktionens API V2.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Datorprogram {#desktop-applications}

Datorapplikationer kan integreras med Experience Rollouts genom att göra direkta REST API-anrop. Använd **funktions-API V2** för skrivbordsklienter.

Se **GET Feature API V2** i API:t för funktioner i den här handboken för fullständig API-referens.

## Integrationskrav {#requirements}

Skrivbordsklienter måste

* **Hedra TTL-värdet** som returnerades i API-svaret. TTL definierar hur länge klienten ska cachelagra funktionsflaggdata innan API:t anropas igen. Implementera ett testfall som validerar det här beteendet för att säkerställa att äldre programversioner försätts i viloläge korrekt när inga funktionsflaggor hanteras.
* **Hantera HTTP-felscenarier smidigt**. Bygg i en reservfunktionsuppsättning så att programmet fortsätter att fungera om API:t inte är tillgängligt för tillfället.
* **Underhåll en detaljerad integreringstestplan** som omfattar både TTL-värdet och felhanteringskraven ovan.

## Program-ID {#app-id}

Skrivbordsklienter kan använda en **produktkod och produktversion** som programidentifierare när API anropas, i stället för ett vanligt klient-ID.

## Se även {#see-also}

* [Integreringssteg](integration-steps.md)
* [Starthandbok](startup-guide.md)
