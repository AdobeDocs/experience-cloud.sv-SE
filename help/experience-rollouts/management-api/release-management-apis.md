---
title: API:er för versionshantering
description: API-referens för API:er för Experience Rollouts-versionshantering, inklusive slutpunkter för att hämta, skapa och redigera releaser och funktionsgrupper för flera team.
exl-id: e8d1d025-0645-4cf2-921f-d94c9f71282d
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---

# API:er för versionshantering {#release-management-apis}

Med API:erna för versionshantering kan du hämta, skapa och redigera releaser och funktionsgrupper för olika team (CTFG) programmatiskt. Dessa API:er använder v2-hanteringsslutpunkten.

**Bassökväg:** `/m/api/v2/mgmt/release`

Alla begäranden kräver de rubriker som beskrivs i de [gemensamma kraven](feature-management-apis-overview.md#common-requirements), plus den rubrik som anges nedan.

## Ytterligare obligatoriskt sidhuvud {#additional-header}

| Sidhuvud | Beskrivning | Obligatoriskt |
|---|---|---|
| `x-user-context-org` | Det numeriska team-ID:t för din organisation. Du hittar det här värdet i Experience Rollouts-konsolen under dina teaminställningar. | Ja |

## Hämta release efter ID {#get-release}

Hämtar en enskild release eller en funktionsgrupp mellan team med hjälp av dess numeriska ID.

| | |
|---|---|
| **Slutpunkt** | `GET /m/api/v2/mgmt/release/{id}` |
| **Metod** | GET |

### Frågeparametrar {#get-query-params}

| Parameter | Typ | Beskrivning | Standard |
|---|---|---|---|
| `includePermissions` | Boolean | Inkludera behörigheter för att uppdatera eller ta bort den här versionen. | `true` |
| `includeOrg` | Boolean | Inkludera organisationsinformation för den här versionen. | `true` |
| `includeAnalyzeInfo` | Boolean | Inkludera analysinformation. | `false` |

### Svar {#get-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är ett frisläppningsobjekt - se [Frigör objektreferens](#release-object). |
| `400` | Ogiltigt release-ID eller felaktig begäran. |

## Skapa release {#create-release}

Skapar en ny release eller en funktionsgrupp för flera team.

| | |
|---|---|
| **Slutpunkt** | `POST /m/api/v2/mgmt/release` |
| **Metod** | POST |

### Begärandetext {#create-request-body}

Begärandetexten använder [Release-objektet](#release-object). `status` måste anges till `"SAVED"` för funktionsgrupper mellan team (`CROSS_TEAM_FEATURE_GROUP`-typ) eller `"DRAFT"` för standardversioner (`RELEASE`-typ) för att kunna skapas.

**Exempel - skapa funktionsgrupp för flera team:**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### Svar {#create-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det skapade släppobjektet. |
| `400` | Ogiltig nyttolast. |

## Redigera release {#edit-release}

Uppdaterar en befintlig eller teamövergripande funktionsgrupp. Skicka det fullständiga frisläppningsobjektet inklusive fältet `id`.

| | |
|---|---|
| **Slutpunkt** | `PUT /m/api/v2/mgmt/release/{id}` |
| **Metod** | PUT |

### Svar {#edit-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det uppdaterade versionsobjektet. |
| `417` | Konflikt vid samtidig uppdatering. Versionen ändrades mellan samtal från GET och PUT. Hämta den aktuella versionen och försök igen. |

## Frisläpp objektreferens {#release-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Versions-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `name` | Sträng | Versionsnamn. Max 50 tecken. Mönster: `^[a-zA-Z0-9_ ,.:()-]*$`. Måste vara unikt. | Ja |
| `description` | Sträng | Valfri beskrivning. Max 255 tecken. | Nej |
| `type` | Sträng | `"RELEASE"` för standardversioner; `"CROSS_TEAM_FEATURE_GROUP"` för funktionsgrupper mellan team. | Ja |
| `status` | Sträng | Frisläpp läge. För IMS: `"DRAFT"` vid skapande; `"DRAFT"`, `"SAVED"`, `"PUBLISHED"` vid uppdatering. För CTFG: `"SAVED"` vid skapande; `"SAVED"`, `"PUBLISHED"` vid uppdatering. | Ja |
| `clients` | Array | Program som är associerade med den här versionen. Varje post kräver `id` (numeriskt) och `imsClientId` (sträng). | Nej |
| `audience` | Array | Lista över målgruppsregler. Se [Villkorsobjekt](feature-flags-management-api.md#condition-object). | Nej |
| `variations` | Array | Lista över variationer. Endast 1 variant stöds under inskickandet. | Krävs för att skickas |
| `params` | Objekt | Frisläpp parametrar. Se [Parameterfält som stöds](#supported-params). | Krävs för att skickas |
| `org` | Objekt | Organisationsobjekt. `id` måste ingå. | Nej |

### Parameterfält som stöds {#supported-params}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `label` | Sträng | Visningsnamn. Max 50 tecken. | Ja |
| `tags` | Array\&lt;String\> | Valfria taggar. Max 50 tecken var. | Nej |
| `canContextOverridePUP` | Boolean | Om `true` används åsidosätts profilreglerna av kontextreglerna. Standard: `false`. | Ja |
| `isBetaRelease` | Boolean | Om `true` markeras detta som en betaversion. Standard: `false`. | Nej |

### Variationsobjekt {#variation-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Variations-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `variantName` | Sträng | Variantnamn. Max 50 tecken. | Ja |
| `variantPercentage` | Dubbel | Procentandel av publiken som tar emot den här varianten. Intervall: [0, 100]. | Ja |
| `features` | Array | Funktioner som ingår i den här varianten. Varje post måste innehålla `id`, `name`, `clientId` och `state`. | Nej |

## Se även {#see-also}

* [Översikt över API:er för funktionshantering](feature-management-apis-overview.md)
* [Hanterings-API för funktionsflaggor](feature-flags-management-api.md)
* [API för hantering av funktionsgrupper](feature-group-management-api.md)
