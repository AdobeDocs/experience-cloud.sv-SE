---
title: gradvis utrullning
description: Se hur ni med hjälp av gradvis utrullning i Experience Rollouts kan fasa in leveransen av funktioner i produktionen på ett säkert sätt, med feedback i realtid och minimala risker.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# gradvis utrullning {#gradual-rollout}

En gradvis utrullning fasar in en ny funktion i produktionen stegvis i stället för att aktivera den för alla användare samtidigt. Det här sättet minskar riskerna, hjälper till att hantera backend-belastningen och skapar en tät feedbackslinga före den fullständiga versionen.

## Fördelar {#benefits}

**Säkerhetsnät**
Genom att släppa till en liten publik först kan du spåra feedback och övervaka beteenden i produktionen innan du expanderar. Om problem uppstår är effekten begränsad och funktionen kan stängas av omedelbart - utan kodändring eller omdistribution.

**Hantering av backend-belastning**
Om du öppnar en funktion för alla användare samtidigt kan serverbelastningen bli plötslig. En gradvis utrullning distribuerar trafikökningen över tid, vilket gör att infrastrukturen kan skalas smidigt.

**Återkoppling i realtid**
Varje fas av utrullningen får feedback från verkliga användare. Teamen kan agera utifrån den feedback som behövs - förbättra upplevelsen, åtgärda gränshascher eller justera meddelanden - före nästa fas.

## Så här fungerar det {#how-it-works}

Experience Rollouts innehåller detaljerade målinriktningsregler som ökar användarexponeringen steg för steg. En vanlig gradvis övergång kan följa detta mönster:

1. Aktivera funktionen för **1 %** användare
2. Övervaka feedback och prestanda
3. Expandera till **10%**, sedan **25%** och sedan till **50%**
4. Nå **100%** när förtroendet har etablerats

I varje steg kan en enskild åtgärd pausa utrullningen eller stänga av funktionen helt om något går fel.

## Se även {#see-also}

* [Funktionsflaggor för att aktivera och inaktivera funktioner](feature-flags-to-enable-disable-features.md)
* [Versionshantering](release-management.md)
