---
title: GET Feature API V3
description: API-referens för API:t för funktionen Experience Rollouts, som används för att hämta funktionsflaggor för webb- och mobilprogram.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---


# GET Feature API V3 {#get-feature-api-v3}

Funktionens API V3 är den primära slutpunkten för hämtning av funktionsflaggor i webb- och mobilprogram. Den returnerar de funktioner och releaser som en användare är berättigad till, baserat på användarens identitet och målgruppsreglerna som konfigurerats i konsolen.

**Slutpunkt:** `GET {HOST}/fg/api/v3/feature`

Använd `https://p13-stage.adobe.io` för scenen och `https://p13n.adobe.io` för produktion.

## Begäran {#request}

### Begäranrubriker {#request-headers}

| Sidhuvud | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `x-api-key` | Sträng | Programmets API-nyckel från Adobe Developer Console. Måste etableras separat för Stage och Production. | Ja |
| `Authorization` | Sträng | **Krävs inte** för oautentiserade scenarier. Använd `Bearer <AccessToken>` för autentiserade användare. Använd `Bearer <ServiceToken>` för cachelagringsscenarier på serversidan för SDK. | Nej |
| `x-adobe-uuid` | Sträng | Ett unikt besökar- eller enhets-ID. Används för att stödja procentuell utrullning för oautentiserade användare och för att bibehålla en likformighet mellan sessioner och oautentiserade till autentiserade övergångar. | Nej |

### Frågeparametrar {#query-parameters}

| Parameter | Typ | Beskrivning | Obligatoriskt |
|---|---|---|---|
| `clientId` | Sträng | Klient-ID:t för ditt program, enligt introduktionen i Experience Rollouts-konsolen. | Ja |
| `ignore_rf` | Boolean | Om `true` ignoreras versionsflaggorna och alla releaser för klienten returneras. Standard: `false`. | Nej |
| `rf` | Sträng | Frisläpp flagga. Används endast när `ignore_rf` är `false`. | Nej |
| `meta` | Boolean | Om `true` inkluderas metadata för varje funktion i svaret, som returneras som ett nyckel/värde-par där värdet är Base64-kodat. Standard: `false`. | Nej |
| `userId` | Sträng | Kräver en tjänsttoken. GUID för den användare som du vill hämta funktionsflaggor för. | Nej |
| *Kontextparametrar* | Ej tillämpligt | Alla frågeparametrar som inte listas ovan behandlas som en kontextvariabel och används för att utvärdera målgruppsregler. Skicka flera värden som `?key1=val1&key2=val2`. Exempel: `?clientLanguage=ja_JP&contractCurrency=JPY`. | Nej |

## Svar {#response}

### Svarsstatuskoder {#response-status}

| Statuskod | Beskrivning |
|---|---|
| `200 OK` | Funktionsflaggsdata som returneras i svarstexten. |
| `304 Not Modified` | Det ETag som klienten skickade matchar det senaste servertillståndet. Behandla detta som en no-op - inga ändringar behöver göras. |
| `400 Bad Request` | `clientId` har inte registrerats eller så har begäran fel format. |
| `403 Forbidden` | Ogiltig API-nyckel eller så prenumererar programmet inte på API:t för upplevelseutrullningar i Adobe Developer Console. |

### Svarshuvuden {#response-headers}

| Sidhuvud | Beskrivning |
|---|---|
| `x-request-id` | En unik begärandeidentifierare för felsökning. Inkludera detta i alla supportförfrågningar. |
| `ETag` | En token som representerar det aktuella servertillståndet för den här användarens funktioner. Skicka det här värdet som `If-None-Match` i efterföljande begäranden. Om läget inte har ändrats returnerar API:t `304`. |
| `x-adobe-fg-poll-interval` | TTL (i sekunder) för klientens lokala cache. Anropa bara om API:t när intervallet har gått ut. |

### Svarstext {#response-body}

Svaret är ett JSON-objekt med följande fält på den översta nivån:

| Fält | Typ | Beskrivning |
|---|---|---|
| `api_version` | Sträng | API-version. Internt fält - ingen bearbetning krävs. |
| `json_version` | Sträng | JSON-schemaversion. Internt fält - ingen bearbetning krävs. |
| `ttl` | Heltal | Cachelagra TTL i sekunder. Samma värde som svarsrubriken `x-adobe-fg-poll-interval`. Standard: 300. |
| `caching_enabled` | Boolean | Om `true` används utförs funktionsutvärderingen lokalt på klienten. Om `false` utförs utvärderingen på serversidan för varje begäran. |
| `client_analytics_params` | Objekt | Analyskonfiguration för programmet. Se [client_analytics_params-fält](#client-analytics-params) nedan. |
| `releases` | Array | Lista över releaser och funktionsflaggor som användaren är berättigad till. Se [släpper fält](#releases-fields) nedan. |

#### client_analytics_params-fält {#client-analytics-params}

| Fält | Beskrivning |
|---|---|
| `app_id` | Programmets numeriska ID. |
| `safe_event_required` | `true` om återmarknadsföringshändelser är aktiverade för den här klienten. |
| `analytics_required` | `false` i V3-svar. |

#### frigör fält {#releases-fields}

| Fält | Beskrivning |
|---|---|
| `release_name` | Namnet på den release eller funktionsgrupp som användaren är berättigad till. |
| `bit_index` | Frisläppningsbitens index. Negativa värden indikerar läget Full Rollout. |
| `features` | En matris med funktionsflaggnycklar som användaren är berättigad till. En funktionsnyckel returneras bara om användaren är berättigad och flaggan är i aktiverat läge. Det här är det primära fältet som programlogiken ska byggas runt. |
| `meta` | Valfria Base64-kodade metadata som är associerade med funktionen. Avkoda innan du använder. |
| `release_analytics_params` | En array med metadataobjekt för analys för varje lämplig funktion. Se [release_analytics_params-fält](#release-analytics-params) nedan. `features` är tomt i kontrollgruppsscenarier. |

#### release_analytics_params-fält {#release-analytics-params}

| Fält | Typ | Beskrivning |
|---|---|---|
| `app_id` | Heltal | Program-ID. |
| `release_id` | Heltal | Versions-ID. |
| `bit_index` | Heltal | Frigör bitindex. Föråldrat. |
| `variant_id` | Heltal | `0` om användaren är i kontrollgruppen. Annars är det inte noll. |
| `feature_id` | Heltal | Internt funktions-ID. |
| `f_key` | Sträng | Funktionsflaggnyckel. |

## Exempelbegäran och svar {#sample}

### Exempelbegäran {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Exempelsvar - användare i testgrupp {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### Exempelsvar - användare i kontrollgrupp {#sample-response-control}

När en användare finns i kontrollgruppen är `features`-arrayen tom och `variant_id` är `0`:

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## Se även {#see-also}

* [GET Feature API V2](get-feature-api-v2.md)
* [Webbprogram](../guides/integrate/web-applications.md)
* [Mobilappar](../guides/integrate/mobile-applications.md)
* [Integreringssteg](../guides/integrate/integration-steps.md)
