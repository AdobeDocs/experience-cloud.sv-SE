---
title: Hanterings-API för funktionsflaggor
description: API-referens för Experience Rollouts-funktionen flaggar hanterings-API:t, inklusive slutpunkter för att hämta, skapa, uppdatera och ta bort funktionsflaggor för ett program.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 1%

---


# Hanterings-API för funktionsflaggor {#feature-flags-management-api}

Med API:t för hantering av funktionsflaggor kan du programmässigt skapa, läsa, uppdatera och ta bort funktionsflaggor för dina program i Experience Rollouts.

**Bassökväg:** `/m/api/v1/mgmt/feature`

Alla begäranden kräver de rubriker som beskrivs i de [gemensamma kraven](feature-management-apis-overview.md#common-requirements).

## Hämta alla funktionsflaggor {#get-all-features}

Hämtar alla funktionsflaggor för ett angivet program.

| | |
|---|---|
| **Slutpunkt** | `GET /m/api/v1/mgmt/feature` |
| **Metod** | GET |

### Frågeparametrar {#get-all-query-params}

| Parameter | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `clientId` | Heltal | Numeriskt ID för programmet. Se [Hämta klient-ID](get-client-id.md). Krävs om `imsClientId` inte anges. | Villkorlig |
| `imsClientId` | Sträng | Klient-ID i strängformat för programmet. Krävs om `clientId` inte anges. | Villkorlig |
| `nonReleaseFeature` | Boolean | Ange till `true` om du vill inkludera oberoende funktionsflaggor som inte är associerade med någon grupp eller release. Krävs för API-baserade arbetsflöden. | Ja |

### Svar {#get-all-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten innehåller en lista med funktionsflaggobjekt. |

Svarstexten innehåller en `features`-matris. Varje element är ett funktionsflaggsobjekt med fälten som beskrivs i [FeatureDTO-objektreferensen](#featuredto-object).

**Exempelsvar:**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## Hämta funktionsflagga via ID {#get-feature-by-id}

Hämtar en enda funktionsflagga med dess numeriska ID.

| | |
|---|---|
| **Slutpunkt** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **Metod** | GET |

### Svar {#get-by-id-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är ett enda [FeatureDTO-objekt](#featuredto-object). |
| `400` | Ogiltigt funktions-ID. |

## Skapa funktionsflagga {#create-feature}

Skapar en ny funktionsflagga.

| | |
|---|---|
| **Slutpunkt** | `POST /m/api/v1/mgmt/feature` |
| **Metod** | POST |

### Begärandetext {#create-request-body}

Begärandetexten är ett [FeatureDTO-objekt](#featuredto-object). Följande fält krävs för att skapa:

| Fält | Obligatoriskt | Anteckningar |
|---|---|---|
| `name` | Ja | Funktionsflaggnyckel. Max 50 tecken. Mönster: `^[a-zA-Z0-9_.-]*$` |
| `clientId` | Ja | Numeriskt program-ID. Se [Hämta klient-ID](get-client-id.md). |
| `state` | Ja | `"enabled"` eller `"disabled"` |

### Svar {#create-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten innehåller `{ "generatedFeatureId": <id> }`. |
| `400` | Ogiltig nyttolast. |
| `403` | Otillräcklig behörighet för den här klienten eller målgruppsregeln. |
| `417` | Användare med rollen Utvecklare kan inte spara en funktion med en offentlig regel - minst en målgruppsregel krävs. |

**Exempelbegäran:**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## Uppdatera funktionsflagga {#update-feature}

Uppdaterar en befintlig funktionsflagga. Skicka det fullständiga [FeatureDTO-objektet](#featuredto-object) inklusive fältet `id`.

| | |
|---|---|
| **Slutpunkt** | `PUT /m/api/v1/mgmt/feature` |
| **Metod** | PUT |

### Svar {#update-response}

| Status | Beskrivning |
|---|---|
| `200` | Lyckades. Svarstexten är det uppdaterade FeatureDTO-objektet. |
| `400` | Ogiltig nyttolast. |
| `403` | Otillräckliga behörigheter. |
| `417` | Konflikt vid samtidig uppdatering. Hämta den aktuella funktionen först och försök igen med det senaste `version`-värdet från `params`. |

## Ta bort funktionsflagga {#delete-feature}

Tar bort en funktionsflagga med dess numeriska ID.

| | |
|---|---|
| **Slutpunkt** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **Metod** | DELETE |

### Svar {#delete-response}

| Status | Beskrivning |
|---|---|
| `204` | Lyckades. Ingen svarsbrödtext. |
| `403` | Otillräckliga behörigheter. |

## Referens för FeatureDTO-objekt {#featuredto-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Funktionsflagga-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `name` | Sträng | Funktionsflaggnyckel (returneras i API-svar). Max 50 tecken. Mönster: `^[a-zA-Z0-9_.-]*$` | Ja (skapa) |
| `clientId` | Heltal | Numeriskt program-ID. | Ja |
| `state` | Sträng | `"enabled"` eller `"disabled"` | Ja |
| `meta` | Sträng | Base64-kodade metadata returneras med funktionen i API-svar. Max 1024 tecken. | Nej |
| `description` | Sträng | Visa beskrivning. Max 225 tecken. | Nej |
| `audience` | Array | Lista över målgruppsregler. Se [FeatureRule-objekt](#featurerule-object). Använd [Hämta önskade målgruppskriterier](get-audience-criteria.md) för att generera detta. | Nej |
| `variations` | Array | Lista med varianter. Max 3. Se [FeatureVariation-objekt](#featurevariation-object). | Nej |
| `params` | Objekt | Ytterligare metadata. Nycklar som stöds: `label` (visningsnamn i användargränssnittet), `tags` (strängmatris). | Nej |
| `release` | Objekt | Releasammanslutning. `null` om flaggan inte finns i en grupp. Skrivskyddad. | Nej |

### FeatureVariation-objekt {#featurevariation-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Variations-ID. Krävs endast för uppdateringsanrop. | Villkorlig |
| `variantName` | Sträng | Variantnamn. Fasta värden: `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | Ja |
| `variantPercentage` | Decimal | Procentandel av publiken som tar emot den här varianten. Måste vara större än 0 och högst 100, med upp till 2 decimaler. | Ja |

### FeatureRule-objekt {#featurerule-object}

| Fält | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `id` | Heltal | Regel-ID. Krävs endast för uppdateringsanrop. Ange till `null` när en ny regel läggs till. | Villkorlig |
| `criteria` | Objekt | Villkorsobjekt som definierar målgruppsregeln. Se [Villkorsobjekt](#condition-object). | Ja |

### Villkorsobjekt {#condition-object}

| Fält | Typ | Beskrivning |
|---|---|---|
| `and` | Array\&lt;condition\> | Alla villkor måste vara sanna. |
| `or` | Array\&lt;condition\> | Minst ett villkor måste vara sant. |
| `not` | Villkor | Det här villkoret måste vara falskt. |
| `attr` | Sträng | Användarattributet som ska utvärderas (till exempel `COUNTRY`, `LOCALE`). |
| `operator` | Sträng | Jämförelseoperatorn (till exempel `EQ`, `IN`, `LT`). |
| `val` | Sträng | Det värde som ska jämföras med. |
| `meta` | Objekt | Valfria metadata för villkor. `desc` fältet anger visningsetiketten i användargränssnittet. |

Antingen `and`, `or` eller `not`, eller en kombination av `attr`, `operator` och `val` måste anges i varje villkor.

## Se även {#see-also}

* [Översikt över API:er för funktionshantering](feature-management-apis-overview.md)
* [API för hanteringskorrigering](management-patch-api.md)
* [Hämta klient-ID för ett program](get-client-id.md)
* [Hämta önskade målgruppskriterier](get-audience-criteria.md)
