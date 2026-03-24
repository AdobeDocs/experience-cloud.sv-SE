---
title: Integreringsguide för Node.js SDK
description: Lär dig hur du integrerar Experience Rollouts Node.js SDK i din backend-tjänst för att hämta och utvärdera funktionsflaggor.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Integreringsguide för Node.js SDK {#nodejs-sdk-integration-guide}

Experience Rollouts Node.js SDK är ett serversidesbibliotek som är avsett för Node.js-tjänster. Funktionsflaggdata cachelagras lokalt och flaggor utvärderas utan synkrona API-anrop för varje begäran.

>[!NOTE]
>
>SDK Node.js är endast avsett för serverbruk. För webbprogram på klientsidan anropar du funktionens API V3 REST-slutpunkt direkt.

## Förutsättningar {#prerequisites}

Innan du integrerar Node.js SDK måste du se till att du har:

* Ett Node.js-program på serversidan
* En **API-nyckel** och **tjänsttoken** som hämtats via Adobe Developer Console - se [Prenumerera på API-programmet](../../integrate/subscribe-to-api-application.md)
* Ditt **klient-ID för programmet** som är registrerat i Experience Rollouts-konsolen - se [Anlita ditt program](../../applications/onboard-your-application.md)

## Installera SDK {#install}

Lägg till SDK i ditt projekts `package.json`:

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

Kräv det sedan i koden:

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## Initiera SDK {#initialize}

Anropa `createInstance()` en gång när programmet startas:

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## Hämta funktionsflaggor {#retrieve-features}

Funktionsflaggor returneras asynkront i ett återanrop. Välj lämplig metod baserat på din användarkontext.

### Autentiserad användare {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### Anonym användare {#anonymous-user}

När ingen token för användaråtkomst är tillgänglig använder du en versionsflagga eller utelämnar token för att få fullständiga releaser:

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### Standardversioner för fullständig utrullning {#default-releases}

När varken en åtkomsttoken eller en versionsflagga har angetts returnerar SDK funktioner i läget **Fullständig utrullning** eller **Baslinje**:

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## Kontrollera om en funktion är aktiverad {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## Aktivera felsökningsloggning {#debug-logging}

Om du vill aktivera utförliga SDK-loggar skickar du en loggningsinstans på felsökningsnivå när `createInstance()` anropas:

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## Se även {#see-also}

* [Node.js Versionsinformation för SDK](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Prenumerera på API-programmet](../../integrate/subscribe-to-api-application.md)
* [Integreringssteg](../../integrate/integration-steps.md)
