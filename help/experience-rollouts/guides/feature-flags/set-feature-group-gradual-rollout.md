---
title: Ange att en funktionsgrupp ska rullas ut gradvis
description: Lär dig hur du konfigurerar en procentuell, gradvis driftsättning för en funktionsgrupp i Adobe Experience Rollouts.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Ange att en funktionsgrupp ska rullas ut gradvis {#gradual-rollout-feature-group}

Den procentuella utrullningen för en funktionsgrupp har konfigurerats på fliken **Grundläggande information**. Du kan justera det här värdet uppåt eller nedåt när som helst när utrullningen fortskrider.

## Så här fungerar det {#how-it-works}

När du anger en procentuell utrullning - till exempel 60 % - exponeras den procentandelen av din definierade målgrupp för funktionsgruppen. De återstående 40 % placeras i **kontrollgruppen**, som får standardbeteendet.

Om du har konfigurerat flera varianter (för A/B-testning) fördelas exponeringsprocenten jämnt över varianter. Exempel: 60% exponering med tre varianter ger 20% per variant, med 40% i kontrollgruppen.

Du kan när som helst öka eller minska procentandelen för att expandera, minska eller pausa utrullningen.

## Se även {#see-also}

* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [A/B-testning med funktionsflaggor](a-b-testing.md)
* [gradvis utrullning](../../concepts/gradual-rollout.md)
