---
title: Schema
description: Lär dig hur du schemalägger en funktionsflagga, funktionsgrupp eller en teamövergripande funktionsgrupp så att den aktiveras automatiskt vid ett framtida datum och en framtida tidpunkt i Adobe Experience Rollouts.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---


# Schema {#schedule}

Schemaläggning är en valfri funktion som gör att du kan ange ett framtida datum och en framtida tidpunkt för att aktivera en funktionsflagga, funktionsgrupp eller funktionsgrupp mellan team automatiskt. Manuell aktivering/avstängning är fortfarande tillgängligt och behöver inte ersättas med ett schema.

Schemaläggning stöds för:

* Funktionsflaggor
* Funktionsgrupper
* Funktionsgrupper i flera team (schemalägger övergången till läget **Publicera**)

## Steg 1: Ange schemat {#set-schedule}

1. Öppna funktionsflaggan, funktionsgruppen eller teamets funktionsgrupp i konsolen.
2. Välj knappen **Schema** till höger på skärmen.
3. Ange **startdatum och starttid** i popup-fönstret och välj **tidszon**.

## Steg 2: Spara {#save}

Välj **Ange schema** och spara sedan inställningarna. Schemat börjar inte gälla förrän du sparar.

## När ett schema har angetts {#after-schedule-set}

När du har sparat det schemalagda datumet och den schemalagda tiden visas de i funktionsflaggan eller i funktionsgruppvyn.

Om du försöker växla på/av-läget manuellt medan ett schema är aktivt, visas en varning om du vill åsidosätta schemat eller avbryta åtgärden.

## På schemalagt datum och tid {#on-schedule}

Vid den schemalagda tidpunkten aktiveras funktionsflaggan eller funktionsgruppen automatiskt (flyttar till ON-läget). För funktionsgrupper som fungerar i flera team övergår läget till **Publicerad**.

När schemat har startats är knappen **Schema** inaktiverad. Scheman kan bara anges när funktionsflaggan eller funktionsgruppen är inaktiverad (eller sparad, för funktionsgrupper som fungerar i flera team).

## Se även {#see-also}

* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [Skapa en funktionsgrupp för flera team](create-cross-team-feature-group.md)
