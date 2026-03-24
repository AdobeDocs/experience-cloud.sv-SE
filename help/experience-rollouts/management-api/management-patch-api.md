---
title: API för hanteringskorrigering
description: Använd API:t för Experience Rollouts för PATCH för att uppdatera enskilda fält i en funktionsflagga, funktionsgrupp eller funktionsgrupp mellan team utan att skicka hela objektet.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# API för hanteringskorrigering {#management-patch-api}

Med PATCH API kan du uppdatera specifika fält för en funktionsflagga, funktionsgrupp eller funktionsgrupp som fungerar i flera team utan att skicka hela objektet i begärandetexten. Detta är användbart för riktade uppdateringar som att ändra en målgruppsregel, växla läge eller justera en variationsprocent.

## Feature flag PATCH {#feature-flag-patch}

Uppdaterar ett eller flera fält i en funktionsflagga.

| | |
|---|---|
| **Slutpunkt** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **Metod** | PATCH |

### Begäranrubriker {#ff-request-headers}

Alla begäranden kräver de rubriker som beskrivs i de [gemensamma kraven](feature-management-apis-overview.md#common-requirements).

### Sökvägsparameter {#ff-path-param}

| Parameter | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `featureFlagId` | Heltal | Det numeriska ID:t för funktionsflaggan som ska uppdateras. | Ja |

### Begärandetext {#ff-request-body}

Skicka bara de fält som du vill uppdatera. Svaret returnerar alltid det fullständiga uppdaterade funktionsflaggobjektet.

**Exempel - endast uppdateringsbeskrivning:**

```json
{
  "description": "Updated description"
}
```

**Exempel - ta bort befintlig publik:**

```json
{
  "audience": null
}
```

**Exempel - lägg till en ny publik när det inte fanns någon:**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Exempel - uppdatera en befintlig målgruppsregel:**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Exempel - ändra läge och variationsprocent:**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>När du uppdaterar en befintlig målgruppsregel ska du inkludera regelns `id` (tillgängligt från GET-funktionssvaret) för att uppdatera den. När du uppdaterar variationer bör du ta med variantens `id` för att undvika att skapa en dubblett.

### Svar {#ff-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det fullständiga uppdaterade funktionsflaggobjektet. |
| `400` | Ogiltig nyttolast. |
| `403` | Otillräckliga behörigheter. |
| `417` | Konflikt vid samtidig uppdatering. Hämta den aktuella funktionen och försök igen. |

## Funktionsgrupp PATCH {#feature-group-patch}

Uppdaterar ett eller flera fält i en funktionsgrupp. Begäran- och svarsstrukturen är densamma som funktionsflaggan PATCH - bara slutpunkten skiljer sig.

| | |
|---|---|
| **Slutpunkt** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **Metod** | PATCH |

## Teamövergripande funktionsgrupp PATCH {#ctfg-patch}

Uppdaterar ett eller flera fält i en funktionsgrupp för flera team. Använder slutpunkten för version 2.

| | |
|---|---|
| **Slutpunkt** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **Metod** | PATCH |

## Se även {#see-also}

* [Hanterings-API för funktionsflaggor](feature-flags-management-api.md)
* [API för hantering av funktionsgrupper](feature-group-management-api.md)
* [API:er för versionshantering](release-management-apis.md)
* [Översikt över API:er för funktionshantering](feature-management-apis-overview.md)
