---
title: Använd sammanhang i målgruppsregler
description: Lär dig hur du använder kontextvariabler i målgruppsregler för funktionsflaggor och funktionsgrupper i Adobe Experience Rollouts.
exl-id: 0367f475-9209-4d53-86b4-a739a73a23a7
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Använd sammanhang i målgruppsregler {#context-in-audience-rules}

Kontextvariabler är värden som tillhandahålls av klientprogrammet vid körning. De gör att du kan rikta in dig på användare baserat på dynamisk sessionsnivåinformation som användarens aktiva språk, enhetstyp eller programtillstånd.

Kontextvariabler är relevanta för webb- och mobilklienter.

## Så här fungerar sammanhangsvariabler {#how-context-works}

Programmet skickar kontextvariabler till Experience Rollouts när en funktionsflagga utvärderas. Du definierar regler i konsolen som kontrollerar dessa värden, och plattformen använder dem vid tidpunkten för utvärderingen för att avgöra om användaren är berättigad.

## Sammanhangsvariabeltyper {#variable-types}

### Fördefinierad (lista) typ {#predefined-type}

En sammanhangsvariabel med en fast uppsättning tillåtna värden, till exempel en lista med språk eller länder.

Tillgängliga operatorer: **Är**, **är inte lika med**, **finns**, **In**

### Heltalstyp {#integer-type}

En kontextvariabel som innehåller ett numeriskt värde.

Tillgängliga operatorer: **Större än**, **Större än eller lika med**, **Är**, **Mindre än**, **Mindre än eller lika med**

### Strängtyp {#string-type}

En kontextvariabel som innehåller ett frihandstextvärde.

Tillgängliga operatorer: **Är**, **är inte lika med**

## Lägga till en kontextvariabel {#adding-context-variable}

Så här lägger du till en kontextvariabel i en målgruppsregel:

1. Öppna funktionsflaggan eller funktionsgruppen i konsolen.
2. Gå till fliken **Målgrupp**.
3. Lägg till ett nytt villkor under **Kontext**.
4. Markera kontextvariabeln, operatorn och värdet.

Om den kontextvariabel du behöver inte visas i listan kan du skapa en ny på ett självbetjäningssätt från konsolens kontextvariabelhanteringsavsnitt.

## Se även {#see-also}

* [Målgrupp i funktionsflaggor och funktionsgrupper](audience-in-feature-flags-and-feature-groups.md)
* [Lägg till procentregler i målgruppskriterier](adding-percentage-rules.md)
