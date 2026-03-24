---
title: Ange en funktion som gradvis ska rulla ut
description: Lär dig hur du konfigurerar en procentuell, gradvis utrullning av en funktionsflagga i Adobe Experience Rollouts.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Ange en funktion som gradvis ska rulla ut {#gradual-rollout-feature}

Den procentuella utrullningen för en funktionsflagga har konfigurerats på fliken **Grundläggande information**. Du kan justera det här värdet uppåt eller nedåt när som helst när utrullningen fortskrider.

## Så här fungerar det {#how-it-works}

När du anger en procentuell utrullning - till exempel 25 % - exponeras den procentandelen av din definierade publik för funktionen. Den återstående procentandelen placeras i kontrollgruppen **kontrollgruppen**, som får standardupplevelsen.

Du kan öka eller minska procentandelen över tiden för att utöka eller minska utrullningen. Om du minskar procentandelen till 0 % inaktiveras funktionen för alla i publiken utan att flaggan tas bort.

## Se även {#see-also}

* [gradvis utrullning](../../concepts/gradual-rollout.md)
* [Ange att en funktionsgrupp ska rullas ut gradvis](set-feature-group-gradual-rollout.md)
* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
