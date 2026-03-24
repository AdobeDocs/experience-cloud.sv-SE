---
title: API för hantering av funktionsgrupper
description: API-referens för Experience Rollouts-API:t för hantering av funktionsgrupper, inklusive slutpunkter för att hämta, skapa, uppdatera, ta bort och styra utrullningsplaner för funktionsgrupper.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 3%

---


# API för hantering av funktionsgrupper {#feature-group-management-api}

Med API:t för hantering av funktionsgrupper kan du programmässigt skapa, läsa, uppdatera och ta bort funktionsgrupper i Experience Rollouts, inklusive automatiserade och A/B-testplaner.

**Bassökväg:** `/m/api/v1/mgmt/group`

Alla begäranden kräver de rubriker som beskrivs i de [gemensamma kraven](feature-management-apis-overview.md#common-requirements).

## Hämta alla funktionsgrupper {#get-all-groups}

Hämtar alla funktionsgrupper för din organisation.

| | |
|---|---|
| **Slutpunkt** | `GET /m/api/v1/mgmt/group` |
| **Metod** | GET |

### Frågeparametrar {#get-all-query-params}

| Parameter | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `myOrg` | Boolean | Ange till `true` om du vill inkludera organisationsinformation. | Ja |
| `includeClientInfo` | Boolean | Ange till `true` om du vill inkludera programinformation för varje grupp. | Ja |

### Svar {#get-all-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är en array med funktionsgruppsobjekt. |

## Hämta funktionsgrupp efter ID {#get-group-by-id}

Hämtar en enda funktionsgrupp med dess numeriska ID.

| | |
|---|---|
| **Slutpunkt** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **Metod** | GET |
| **Frågeparameter** | `includeAnalyzeInfo=true` (valfritt - lägger till analysdata i svaret) |

### Svar {#get-by-id-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är ett funktionsgruppsobjekt. |
| `400` | Ogiltigt ID för funktionsgrupp. |

## Skapa funktionsgrupp {#create-group}

Skapar en ny funktionsgrupp med en manuell, automatiserad eller A/B-testningstyp.

| | |
|---|---|
| **Slutpunkt** | `POST /m/api/v1/mgmt/group` |
| **Metod** | POST |

### Begärandetext {#create-request-body}

Begärandetexten använder [funktionsgruppsobjektet](#feature-group-object). `rolloutType` i `params` är obligatoriskt och fastställer nyttolastens struktur.

**Exempel - manuell utrullning:**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

### Svar {#create-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det funktionsgruppsobjekt som skapats. |
| `400` | Ogiltig nyttolast - mer information finns i [felmeddelanden](#error-messages). |
| `403` | Otillräckliga behörigheter. |

## Uppdatera funktionsgrupp {#update-group}

Uppdaterar en befintlig funktionsgrupp. Skicka samma struktur som skapandebegärandetexten, inklusive fältet `id`.

| | |
|---|---|
| **Slutpunkt** | `PUT /m/api/v1/mgmt/group` |
| **Metod** | PUT |

### Svar {#update-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det uppdaterade funktionsgruppsobjektet. |
| `400` | Ogiltig nyttolast. |
| `403` | Otillräckliga behörigheter. |

## Ta bort funktionsgrupp {#delete-group}

Tar bort en funktionsgrupp med dess numeriska ID.

| | |
|---|---|
| **Slutpunkt** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **Metod** | DELETE |

### Svar {#delete-response}

| Status | Beskrivning |
|---|---|
| `204` | Lyckades. Ingen svarsbrödtext. |
| `403` | Otillräckliga behörigheter. |

## Objektreferens för funktionsgrupp {#feature-group-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Funktionsgrupp-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `name` | Sträng | Funktionsgruppnyckel. Max 50 tecken. Mönster: `^[a-zA-Z0-9_.-]*$` | Ja (skapa) |
| `clients` | Array | Program som är associerade med gruppen. Varje post måste innehålla `id` och `imsClientId`. | Ja |
| `status` | Sträng | `"SAVED"` eller `"PUBLISHED"` | Ja |
| `type` | Sträng | Alltid `"group"` för funktionsgrupper. | Ja |
| `org` | Objekt | Organisationsinformation. `id` måste ingå. | Ja |
| `params` | Objekt | Gruppparametrar. `rolloutType` är obligatoriskt (`"manual"`, `"automated"` eller `"ab-testing"`). Stöder även `label` och `tags`. | Ja |
| `audience` | Array | Målgruppsregler för manuella utrullningstyper. | Nej |
| `variations` | Array | Lista med varianter. Se [FeatureGroupVariation-objekt](#featuregroupvariation-object). | Nej |
| `phaseRollOutPlan` | Objekt | Fas-utrullningsplan. Krävs för automatiserade tester och A/B-testningstyper. Se [PhaseRollOutPlan-objekt](#phaserolloutplan-object). | Villkorlig |
| `description` | Sträng | Valfri visningsbeskrivning. Max 225 tecken. | Nej |

### FeatureGroupVariation, objekt {#featuregroupvariation-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Variations-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `variantName` | Sträng | Variantnamn. Hårdkodad till `"Variant 1"`. | Ja |
| `variantPercentage` | Decimal | Procentandel av publiken som tar emot den här varianten. Måste vara större än 0 och högst 100. | Ja |

### Objektet PhaseRollOutPlan {#phaserolloutplan-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `phaseRollOutBlocks` | Array | Ordnad lista över fasblock och vänteblock. Det sista blocket måste vara ett fasblock. | Ja |
| `rollOutPlanState` | Sträng | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` eller `"ABORTED"` | Ja |

Varje block i `phaseRollOutBlocks` är antingen ett **fasblock** (`isPhaseBlock: true`) som innehåller en `phaseRule` med målgruppskriterier eller ett **vänteblock** (`isPhaseBlock: false`) som innehåller en `waitRule` med antingen en `waitDuration` (relativ) eller `executionDate` (fast tidsstämpel).

## Felmeddelanden {#error-messages}

| Villkor | Status | Felmeddelande |
|---|---|---|
| Ogiltigt eller tomt namn | 400 | `Error: Invalid value for release name.` |
| Tomma målgruppskriterier | 400 | `Error: Release is not valid` |
| Flera variationer för automatiserad text | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| Publicerad grupp utan klienter | 400 | `Error: At least one client must be associated with enabled feature group.` |
| Det sista blocket i planen är inte ett fasblock | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| Vänteblockets tidsinställningar är felaktiga | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| Inkonsekventa vänteblocktyper | 400 | `Error: Wait block should be of same type.` |
| Redigera ett aktiverat fasblock | 400 | `Error: Activated phase block should not be changed` |
| Tom utrullningstyp | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| Phase plan skickad med manuell typ | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| Schemat har skickats med PUBLISHED-status | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## Se även {#see-also}

* [Översikt över API:er för funktionshantering](feature-management-apis-overview.md)
* [Hanterings-API för funktionsflaggor](feature-flags-management-api.md)
* [API för hanteringskorrigering](management-patch-api.md)
