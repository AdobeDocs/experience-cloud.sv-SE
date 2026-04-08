---
title: Importera funktionsflaggor
description: Lär dig hur du importerar funktionsflaggor från en sandlåda till en annan i Adobe Experience Rollouts för att undvika att återskapa flaggkonfigurationer manuellt.
exl-id: 37c84d75-a565-4202-8c99-f630e05b6bb6
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Importera funktionsflaggor {#import-feature-flags}

Med Experience Rollouts kan du importera funktionsflaggor från en sandlåda (till exempel sandlåda 1) till en annan sandlåda (till exempel sandlåda 2). På så sätt slipper du återskapa flaggkonfigurationer manuellt, vilket minskar risken för konfigurationsväxling mellan sandlådor.

## Steg 1: Gå till målsandlådan och -programmet {#step-1}

Logga in på konsolen för sandlådan **destination** - sandlådan som du vill importera flaggor *till*. Välj det program som du vill importera flaggor till i programlistrutan på sidan Funktionsflaggor.

>[!IMPORTANT]
>
>Din aktuella sandlåda och det valda programmet måste vara **mål** - inte källan. Om du till exempel vill importera en flagga från sandbox 1 till sandbox 2 loggar du in på konsolen sandbox 2 och väljer sandbox 2.

## Steg 2: Öppna importdialogrutan {#step-2}

Välj **Importera funktionsflaggor**. En dialogruta öppnas med källsandlådan och -programmet, ifyllda i förväg baserat på tillgängliga program. Vid behov kan du ändra källsandlådan och -programmet från listrutorna i dialogrutan.

## Steg 3: Välj de funktionsflaggor som ska importeras {#step-3}

I listan med funktionsflaggor i källsandlådan väljer du de flaggor du vill importera. Du kan markera en, flera eller alla flaggor samtidigt.

## Steg 4: Välj status för funktionsflaggor som ska importeras {#step-4}

Använd listrutan för att välja hur funktionsflaggorna ska importeras - antingen **Aktiverad**, **Inaktiverad** eller i deras **aktuella läge**. Som standard importeras funktionsflaggor i läget **Inaktiverad**.

## Viktiga anteckningar {#important-notes}

Tänk på följande när du importerar funktionsflaggor:

* Om det redan finns en funktionsflagga med samma nyckel i målsandlådan importeras den inte.

## Se även {#see-also}

* [Funktioner och funktionsgrupper](../feature-flags/features-feature-groups-releases.md)
* [Skapa din första funktionsflagga](../feature-flags/create-your-first-feature-flag.md)
