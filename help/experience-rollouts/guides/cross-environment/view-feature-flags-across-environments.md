---
title: Visa funktionsflaggor i olika miljöer
description: Lär dig hur du visar status för funktionsflaggor i alla länkade miljöer för ett program i Adobe Experience Rollouts.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Visa funktionsflaggor i olika miljöer {#view-flags-across-environments}

När du har länkat dina programinstanser mellan miljöer visar Experience Rollouts statusen för varje funktionsflagga i alla länkade miljöer direkt på sidan med funktionsflaggor. Detta ger en enda vy där du kan jämföra flagglägen, t.ex. om en flagga är PÅ i scenen och AV i produktionen, utan att byta miljö.

## Förutsättningar {#prerequisites}

Programinstanserna måste länkas mellan olika miljöer innan statusen för olika miljöer visas. Se [Koppla miljöer till ett program](associate-environments.md) för installationsanvisningar.

## Så här fungerar det {#how-it-works}

När du navigerar till **Funktioner och releaser > Funktionsflaggor** och väljer ett program som har länkade instanser, visas ytterligare kolumner för varje länkad miljö på listsidan. Varje kolumn visar det aktuella läget för funktionsflaggan i den miljön.

Funktionsflaggor matchas i olika miljöer med hjälp av deras **nyckel**, inte med hjälp av deras namn. Detta innebär:

* En flagga kan ha olika visningsnamn i varje miljö, förutsatt att nyckeln är densamma.
* Namnet som visas i varje miljökolumn är det namn som används i den miljön.

## Använd skiftläge {#use-case}

Ett typiskt arbetsflöde är att utveckla och testa en funktionsflagga i en lägre miljö (till exempel Stage) och sedan kontrollera dess status innan konfigurationen befordras till Production. Med synlighet för olika miljöer kan du bekräfta att flaggan är korrekt konfigurerad på scenen innan du importerar den till produktion - allt inifrån produktionskonsolen.

## Se även {#see-also}

* [Koppla miljöer till ett program](associate-environments.md)
* [Importera funktionsflaggor](import-feature-flags.md)
* [Koncept för flera miljöer](cross-environment-concept.md)
