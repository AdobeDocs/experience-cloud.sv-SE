---
title: Hämta önskade målgruppskriterier
description: Lär dig hur du skapar rätt JSON-struktur för målgruppskriterier som kan användas i API:erna för Experience Rollouts-hantering med hjälp av konsolen och GET funktions-API:n.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Hämta önskade målgruppskriterier {#get-audience-criteria}

Målgruppsfältet i hanterings-API:erna använder ett strukturerat JSON-format som kan vara komplext att skriva för hand. Rekommenderat tillvägagångssätt är att skapa önskad målgrupp med konsolen och sedan hämta dess JSON-representation via API:t.

## Steg {#steps}

Följ de här stegen för att få JSON för önskat målgruppsvillkor:

1. I konsolen Experience Rollouts skapar du en temporär funktionsflagga med de målgruppskriterier som du vill använda i ditt API-anrop.
2. När du har sparat bör du anteckna funktionens flagga-ID från webbläsarens URL. ID:t visas i URL:en efter klient-ID:t. I `.../feature-flags/1191/22080` är till exempel funktions-ID `22080`.
3. Anropa [Get Feature by ID](feature-flags-management-api.md#get-feature-by-id)-slutpunkten med detta funktions-ID.
4. Leta reda på fältet `audience` i svar-JSON. Detta innehåller den exakta målgruppsstrukturen du behöver.
5. Kopiera värdet `audience` och ta bort attributet `id` från varje regelobjekt. Använd detta i ditt anrop till API för funktionen Skapa eller Uppdatera.

## Exempel {#example}

När GET `/m/api/v1/mgmt/feature/22080` har anropats innehåller svaret:

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

Om du vill använda detta i ett Create feature-anrop tar du bort fältet `id` från målgruppsobjektet:

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## Se även {#see-also}

* [Hanterings-API för funktionsflaggor](feature-flags-management-api.md)
* [Hämta klient-ID för ett program](get-client-id.md)
* [API för hanteringskorrigering](management-patch-api.md)
