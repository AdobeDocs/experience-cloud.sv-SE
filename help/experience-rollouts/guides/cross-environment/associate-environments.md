---
title: Koppla miljöer till ett program
description: Lär dig hur du länkar programinstanser mellan miljöer i Adobe Experience Rollouts så att du kan hantera funktionsflaggor på ett enhetligt sätt, från utveckling till produktion.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Koppla miljöer till ett program {#associate-environments}

Genom att länka programinstanser mellan miljöer blir det lättare att se och importera arbetsflöden mellan olika miljöer. Du måste ha rollen **Admin** för att konfigurera detta. Se [Användarroller](../teams/user-roles.md) om du behöver verifiera din roll.

Bakgrund till varför detta är användbart finns i [Koncept för flera miljöer](cross-environment-concept.md).

## Steg 1: Öppna programinställningarna {#step-1}

1. Logga in på Experience Rollouts-konsolen.
2. Navigera till **Admin > Program**.
3. Välj **Nytt program** om du vill ta in ett nytt program eller välj ett befintligt program om du vill redigera det.

## Steg 2: Konfigurera avsnittet Associerade miljöer {#step-2}

Bläddra till avsnittet **Associerade miljöer** i programformuläret. Varje rad i det här avsnittet definierar en av programmets distributionsmiljöer. Konfigurera följande fält för varje miljö:

| Fält | Beskrivning |
|---|---|
| **Miljö** | Välj en standardmiljöidentifierare i listan: QA1, QA2, STG1, STG2, PROD1 eller PROD2. Detta anger för Experience Rollouts om miljön är produktion eller inte, och avgör vilken färgkodning som används i konsolen. |
| **Miljöetikett** | Ett anpassat namn för den här miljön när ditt team refererar till den, till exempel `Dev`, `Staging` eller `Production`. Det här är ett frihandsritat formulär och behöver inte matcha standardidentifieraren. |
| **miljö för upplevelseutrullningar** | Plattformsmiljön (Stage eller Production) där den här programinstansen finns. Förifylld baserat på vilken konsol du befinner dig i. |
| **Program-ID** | Klient-ID för programinstansen i den här miljön. Fylls i automatiskt när du väljer ett program i listrutan. |

## Steg 3: Länka programinstanser mellan miljöer {#step-3}

Följ de här stegen för varje ytterligare miljö om du vill länka instanser mellan miljöer:

1. Skapa programinstansen i målmiljön (skapa till exempel QA-appen i scenkonsolen).
2. Återgå till programmet som du konfigurerar och lägg till en ny rad i **Associerade miljöer**.
3. I listrutan **Program-ID** väljer du den programinstans du just skapade. Taggen och etiketten för miljön fylls i automatiskt.
4. Välj **Uppdatera** att spara.

Upprepa den här processen för varje miljö som du vill länka, till exempel för att länka QA-, Stage- och Production-instanser för samma program.

## Viktiga anteckningar {#important-notes}

* QA- och Stage-miljöer kan finnas på antingen Experience Rollouts Stage eller Production Platform Environment.
* Produktionsmiljöer (PROD1, PROD2) kan bara hanteras i produktionsmiljön Experience Rollouts.
* Du kan bara länka till en lägre miljö från en högre. Från Production kan du till exempel länka till en scen- eller QA-instans, men det omvända är skrivskyddat.

## Se även {#see-also}

* [Koncept för flera miljöer](cross-environment-concept.md)
* [Visa funktionsflaggor i olika miljöer](view-feature-flags-across-environments.md)
* [Importera funktionsflaggor](import-feature-flags.md)
