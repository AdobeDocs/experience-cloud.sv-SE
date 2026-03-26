---
title: Schema
description: Lär dig hur du schemalägger en funktionsflagga, funktionsgrupp eller en teamövergripande funktionsgrupp så att den aktiveras automatiskt vid ett framtida datum och en framtida tidpunkt i Adobe Experience Rollouts.
exl-id: f8309daa-428b-41a0-8817-89c8f603bec8
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Schema {#schedule}

Schemaläggning är en valfri funktion som gör att du kan ange ett framtida datum och en framtida tidpunkt för att aktivera en funktionsflagga eller funktionsgrupp automatiskt. Manuell aktivering/avstängning är fortfarande tillgängligt och behöver inte ersättas med ett schema.

Schemaläggning stöds för:

* Funktionsflaggor
* Funktionsgrupper

## Steg 1: Ange schemat {#set-schedule}

1. Öppna funktionsflaggan eller funktionsgruppen i konsolen.
2. Välj knappen **Schema** till höger på skärmen.
3. Ange **startdatum och starttid** i popup-fönstret och välj **tidszon**.

## Steg 2: Spara {#save}

Välj **Ange schema** och spara sedan inställningarna. Schemat börjar inte gälla förrän du sparar.

## När ett schema har angetts {#after-schedule-set}

När du har sparat det schemalagda datumet och den schemalagda tiden visas de i funktionsflaggan eller i funktionsgruppvyn.

Om du försöker växla på/av-läget manuellt medan ett schema är aktivt, visas en varning om du vill åsidosätta schemat eller avbryta åtgärden.

## På schemalagt datum och tid {#on-schedule}

Vid den schemalagda tidpunkten aktiveras funktionsflaggan eller funktionsgruppen automatiskt (flyttar till ON-läget).

När schemat har startats är knappen **Schema** inaktiverad. Det går bara att ange scheman när funktionsflaggan eller funktionsgruppen är inaktiverad.

## Se även {#see-also}

* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
