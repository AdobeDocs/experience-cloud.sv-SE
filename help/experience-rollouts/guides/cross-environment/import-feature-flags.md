---
title: Importera funktionsflaggor
description: Lär dig hur du importerar funktionsflaggor från en lägre miljö till en högre miljö i Adobe Experience Rollouts för att undvika att återskapa flaggkonfigurationer manuellt.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Importera funktionsflaggor {#import-feature-flags}

Med upplevelseöverrullningar kan du importera funktionsflaggor från en lägre miljö (till exempel Stage) till en högre miljö (till exempel Production). På så sätt slipper du återskapa flaggkonfigurationer manuellt, vilket minskar risken för att konfigurationen växlar mellan miljöer.

## Förutsättningar {#prerequisites}

Om du vill använda importarbetsflödet måste programinstanserna länkas mellan olika miljöer. Se [Koppla miljöer till ett program](associate-environments.md).

## Steg 1: Gå till målmiljön och programmet {#step-1}

Logga in på konsolen för **målmiljön** - den miljö du vill importera flaggorna *till*. Välj det program som du vill importera flaggor till i programlistrutan på sidan Funktionsflaggor.

>[!IMPORTANT]
>
>Den aktuella miljön och det valda programmet måste vara **målet**, inte källan. Om du till exempel vill importera en flagga från scenen till produktionen loggar du in på produktionskonsolen och väljer produktionsprogrammet.

## Steg 2: Öppna importdialogrutan {#step-2}

Välj **Importera funktionsflaggor**. En dialogruta öppnas med källmiljö och program, ifyllda i förväg baserat på de länkade miljöer som konfigurerats för ditt program. Om det behövs kan du ändra källmiljö och program från listrutorna i dialogrutan.

## Steg 3: Välj de funktionsflaggor som ska importeras {#step-3}

I listan med funktionsflaggor i källmiljön väljer du de flaggor du vill importera. Du kan markera en, flera eller alla flaggor samtidigt.

## Steg 4: Hantera befintliga flaggor (om det behövs) {#step-4}

Om det redan finns en funktionsflagga med samma nyckel i målmiljön kommer Experience Rollouts att be dig bekräfta om du vill skriva över den. Granska den befintliga flaggkonfigurationen innan du bekräftar. Om du skriver över ersätts målflaggans inställningar med inställningarna från källan.

## Viktiga anteckningar {#important-notes}

Tänk på följande när du importerar funktionsflaggor:

* Importerade flaggor är alltid inställda på läget **AV** i målmiljön, oavsett deras tillstånd i källmiljön. Du måste aktivera dem manuellt efter importen.
* Om en flagga har schemalagts att aktiveras vid ett framtida datum och en framtida tidpunkt i källmiljön, överförs schemat **inte**. Du måste ange ett nytt schema i målmiljön om det behövs.

## Se även {#see-also}

* [Koppla miljöer till ett program](associate-environments.md)
* [Visa funktionsflaggor i olika miljöer](view-feature-flags-across-environments.md)
* [Koncept för flera miljöer](cross-environment-concept.md)
