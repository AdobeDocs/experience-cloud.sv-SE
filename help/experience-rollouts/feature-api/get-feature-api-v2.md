---
title: GET Feature API V2
description: API-referens för Experience Rollouts Feature API V2, som används för att hämta funktionsflaggor för skrivbordsprogram.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 1%

---


# GET Feature API V2 {#get-feature-api-v2}

Funktionens API V2 är utformat för integrering med skrivbordsprogram. Den hämtar funktionsflaggor och releasedata för den autentiserade användaren, stödproduktkod och produktversion som programidentifierare, förutom ett vanligt klient-ID.

**Slutpunkt:** `GET {HOST}/fg/api/v2/feature`

Använd `https://p13-stage.adobe.io` för scenen och `https://p13n.adobe.io` för produktion.

## Begäran {#request}

### Begäranrubriker {#request-headers}

| Sidhuvud | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `x-api-key` | Sträng | Programmets API-nyckel från Adobe Developer Console. Måste etableras separat för Stage och Production. | Ja |
| `Authorization` | Sträng | `Bearer <AccessToken>` eller `Bearer <ServiceToken>`. | Ja |
| `x-adobe-uuid` | Sträng | Ett unikt besökar- eller enhets-ID. Används för procentuell utrullning i oautentiserade scenarier och för att upprätthålla sessionens varaktighet. | Nej |

### Frågeparametrar {#query-parameters}

| Parameter | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `clientId` | Sträng | Klient-ID för programmet, enligt introduktionen i Experience Rollouts-konsolen. Flera värden kan skickas: `clientId=C1&clientId=C2`. | Nej |
| `p` | Sträng | Produkt, version, plattform, språksträng (PVPL-format). Exempel: `PHSP:17.0:WIN:en_US`. Flera värden kan skickas: `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. Endast produktkod och produktversion används vid utvärderingen. | Nej |
| `meta` | Boolean | Om `true` returneras Base64-kodade metadata för varje funktion. Standard: `false`. | Nej |
| *Kontextparametrar* | Ej tillämpligt | Alla ytterligare nyckelvärdepar behandlas som en kontextvariabel för utvärdering av målgruppsregler. Exempel: `clientLanguage=ja_JP&contractCurrency=JPY`. | Nej |

>[!NOTE]
>
>Minst en av `clientId` eller `p` krävs för att identifiera programmet.

## Svar {#response}

### Svarsstatuskoder {#response-status}

| Statuskod | Beskrivning |
|---|---|
| `200 OK` | Funktionsflaggsdata som returneras i svarstexten. |
| `304 Not Modified` | ETag matchar det aktuella servertillståndet. Behandla som en no-op - inga ändringar behöver göras. |
| `401 Unauthorized` | Auktoriseringstoken är ogiltig. |

### Svarshuvuden {#response-headers}

| Sidhuvud | Beskrivning |
|---|---|
| `x-request-id` | En unik begärandeidentifierare för felsökning. Inkludera detta i alla supportförfrågningar. |
| `ETag` | Token som representerar användarens aktuella funktionstillstånd. Skicka som `If-None-Match` i efterföljande begäranden. Returnerar `304` om den inte ändras. |
| `x-adobe-fg-poll-interval` | TTL i sekunder för klientens lokala cache. Anropa bara om API:t när intervallet har gått ut. |

### Svarstext {#response-body}

Svaret är ett JSON-objekt med följande fält på den översta nivån:

| Fält | Typ | Beskrivning |
|---|---|---|
| `api_version` | Sträng | API-version. Internt fält - ingen bearbetning krävs. |
| `json_version` | Sträng | JSON-schemaversion. Internt fält - ingen bearbetning krävs. |
| `ttl` | Heltal | Cachelagra TTL i sekunder. Standard: 300. |
| `clients` | Objekt | Mappa klient-ID:n (eller PVPL-strängar) till versionsdata. Varje nyckel innehåller fälten som beskrivs nedan. |

#### Svarsfält per klient {#per-client-fields}

| Fält | Beskrivning |
|---|---|
| `releases` | En lista över releaser som användaren är berättigad till. Se [släpper fält](#releases-fields) nedan. |
| `client_analytics_params` | Konfigurationsobjekt för analys. Se [client_analytics_params-fält](#analytics-fields) nedan. |

#### frigör fält {#releases-fields}

| Fält | Beskrivning |
|---|---|
| `release_name` | Namn på releasen eller funktionsgruppen. |
| `bit_index` | Frigör bitindex. Föråldrat. Kan vara `null` eller negativt beroende på frisläppningsstatus. |
| `features` | En matris med funktionsflaggnycklar som användaren är berättigad till. En funktionsnyckel visas bara om användaren är berättigad och flaggan är aktiverad. |
| `meta` | Base64-kodade metadata som tillval. Avkoda innan du använder. |
| `release_analytics_params` | Analysmetadata för berättigade funktioner. `features` är tomt i kontrollgruppsscenarier. |

#### release_analytics_params-fält {#release-analytics-params}

| Fält | Typ | Beskrivning |
|---|---|---|
| `app_id` | Heltal | Program-ID. |
| `release_id` | Heltal | Versions-ID. |
| `bit_index` | Heltal | Föråldrat. |
| `variant_id` | Heltal | `0` om kontrollgruppen, annars inte noll. |
| `feature_id` | Heltal | Internt funktions-ID. |
| `f_key` | Sträng | Funktionsflaggnyckel. |

#### client_analytics_params-fält {#analytics-fields}

| Fält | Typ | Beskrivning |
|---|---|---|
| `app_id` | Heltal | Program-ID. |
| `safe_event_required` | Boolean | `true` om återmarknadsföringshändelser är aktiverade. |
| `analytics_required` | Boolean | `false` om analys är inaktiverad eller om standardflöde används, `true` om Kinesis-flöde är aktiverat. |

## Exempelbegäran och svar {#sample}

### Exempelbegäran {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Exempelsvar {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## Se även {#see-also}

* [GET Feature API V3](get-feature-api-v3.md)
* [Datorprogram](../guides/integrate/desktop-applications.md)
* [Integreringssteg](../guides/integrate/integration-steps.md)
