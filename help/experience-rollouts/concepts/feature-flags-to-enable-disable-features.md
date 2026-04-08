---
title: Funktionsflaggor för att aktivera och inaktivera funktioner
description: Lär dig hur funktionsflaggor i Experience Rollouts gör att du kan styra funktionstillgänglighet, hantera beroenden och minska distributionsriskerna.
exl-id: 627775e8-9b17-4bc7-9565-07a438ae8ed7
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Funktionsflaggor för att aktivera och inaktivera funktioner {#feature-flags}

Med funktionsflaggor kan du aktivera och inaktivera programfunktioner under körning utan att behöva omdistribuera kod. De skiljer även koddistributioner från funktionstillgänglighet - ny kod kan distribueras till produktion bakom en flagga och aktiveras endast när du är redo.

Detta tillvägagångssätt minskar risken avsevärt. Utvecklarna kan bygga smidigt och tillförlitligt, samtidigt som produktteamen behåller kontrollen över timing och målgrupp för alla funktionsreleaser.

## Hantera beroenden under utveckling {#manage-dependencies}

Med funktionsflaggor kan du hantera beroenden när du testar i snabba utvecklingscykler. Utvecklarna lägger mindre tid på att lösa sammanslagningskonflikter och omfaktorisering och mer tid på att leverera funktioner.

Eftersom funktionstillgängligheten styrs utanför koden kan flera funktioner utvecklas parallellt - utan komplex förgrening. Enskilda funktioner kan återställas oberoende av varandra, utan att andra pågående funktioner påverkas.

## Mörka distributioner {#dark-deployments}

Eftersom aktivera och inaktivera beslut direkt utanför kodbasen kan du distribuera kod till produktionen samtidigt som funktionen är osynlig för slutanvändarna. Detta kallas en **mörk distribution**.

Med mörk driftsättning kan du tryggt skicka kod till produktionen, testa den i den aktiva miljön mot verkliga förhållanden och publicera koden när du vill - inte när driftsättningsschemat tvingar dig till det.

## gradvis utrullning {#gradual-rollout}

När du är redo att släppa kan du använda en funktionsflagga för att utföra en **gradvis utrullning**: öppna funktionen för 1 % av användarna, mäta feedback och prestanda och sedan öka progressivt.

Denna rullande strategi ger er bättre kontroll över den upplevelse ni ger och en snabbare feedback med verkliga användare, så att era team kan reagera snabbt före en fullständig release.

## Avsluta switch {#kill-switch}

Om en release inte fungerar som planerat - ofördelaktig feedback, ett fel eller ett prestandaproblem - kan du stänga av funktionen omedelbart med funktionsflaggan som en **dölj switch**. Ingen kodändring eller omdistribution behövs.

## Livscykel för funktionsflagga {#lifecycle}

En funktionsflagga i Experience Rollouts följer denna normala livscykel:

1. En utvecklare skapar en funktionsflagga och testar den separat utan att exponera den för andra användare.
2. En produktägare länkar en målgrupp till flaggan, vilket gör funktionen synlig för en definierad uppsättning externa användare.
3. Flaggan kan läggas till i en [funktionsgrupp](feature-groups-to-control-multiple-features.md) som ska hanteras tillsammans med relaterade flaggor.
