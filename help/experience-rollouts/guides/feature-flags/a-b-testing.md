---
title: A/B-testning med funktionsflaggor
description: Lär dig hur du kör A/B-tester med funktionsgrupper i Adobe Experience Rollouts genom att konfigurera flera varianter för en uppsättning funktionsflaggor.
exl-id: bb849049-229c-40ff-bbfe-7996f868bcc3
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# A/B-testning med funktionsflaggor {#a-b-testing}

A/B-tester i Experience Rollouts utförs med **funktionsgrupper**. Genom att konfigurera mer än en variant i en funktionsgrupp kan du leverera olika versioner av en funktion till olika delar av målgruppen och jämföra resultaten.

## Förutsättningar {#prerequisites}

* Du har åtkomst till konsolen - se [Logga in på konsolen](../console/log-in-to-the-console.md)
* Du ingår i ett team och programmet ingår
* Du har rollen **Utvecklare** eller **Ägare av produktreleaser**
* Du har skapat de funktionsflaggor som ska testas - se [Skapa din första funktionsflagga](create-your-first-feature-flag.md)

## Steg 1: Skapa en funktionsgrupp med flera varianter {#create}

1. Navigera till **Funktionstestning > Funktionsgrupper** och välj **Ny funktionsgrupp**.
2. Ange en titel, nyckel och beskrivning i **Grundläggande information**.
3. Ange en **procentuell utrullning** för att definiera hur mycket av publiken som deltar i testet.
4. Ange **Varianter** till ett värde som är större än ett (till exempel två varianter för ett klassiskt A/B-test).
5. Se [Ange en funktionsgrupp som gradvis ska rullas ut](set-feature-group-gradual-rollout.md) för att förstå hur exponeringsprocenten fördelas mellan olika varianter.

## Steg 2: Ange målgrupp {#audience}

Lägg till målgruppsvillkor på fliken **Målgrupp** och välj de program som ska inkluderas. Funktionsgrupper kan omfatta flera program i samma team.

>[!NOTE]
>
>Om du vill rikta in dig på externa användare i ett A/B-test måste du ha rollen **Product Release Owner**. Rollen Utvecklare är sandlådebaserad och begränsad till privat testning.

## Steg 3: Lägg till funktioner per variant {#features}

Under fliken **Funktioner** har varje variant en egen flik. Lägg till lämpliga funktionsflaggor för varje variant för att definiera de olika upplevelser du vill jämföra.

>[!IMPORTANT]
>
>En funktionsflagga kan bara användas med en metod i taget - funktionsflagga, funktionsgrupp eller release. Om du lägger till en flagga i en funktionsgrupp tas alla målgrupps- eller procentangivelser som anges direkt på flaggan bort.

## Steg 4: Spara och aktivera {#save}

Spara inställningarna för funktionsgruppen. När du är redo att starta testet ställer du in funktionsgruppen på det aktiva läget.

## Se även {#see-also}

* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [Ange att en funktionsgrupp ska rullas ut gradvis](set-feature-group-gradual-rollout.md)
* [Analyser](analytics.md)
