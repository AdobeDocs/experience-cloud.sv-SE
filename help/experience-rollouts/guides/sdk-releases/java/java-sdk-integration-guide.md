---
title: Integreringsguide för Java SDK
description: Lär dig hur du integrerar Experience Rollouts Java SDK i din serverdelstjänst för att hämta och utvärdera funktionsflaggor.
exl-id: 7c12bd6c-1883-4f1c-985f-a2b0432e61ce
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Integreringsguide för Java SDK {#java-sdk-integration-guide}

Experience Rollouts Java SDK är ett serversidesbibliotek som cachelagrar data för funktionsflaggor lokalt och utvärderar flaggor utan synkrona API-anrop för varje begäran. Den här guiden täcker nuvarande SDK (4.x).

## Förutsättningar {#prerequisites}

Innan du integrerar Java SDK måste du se till att du har:

* JDK 11 eller senare (krävs från SDK version 3.0.0 och framåt; tidigare versioner stöder JDK 8+)
* Ett Maven-baserat byggsystem
* Ett **API-nyckel** och **tjänsttoken**-klient-ID från ditt Adobe Developer Console-projekt - kontakta Experience Rollouts-support om du vill tillåtslista ditt klient-ID
* Ditt **klient-ID för programmet** som är registrerat i Experience Rollouts-konsolen - se [Anlita ditt program](../../applications/onboard-your-application.md)

## Lägg till Maven-beroendet {#maven-dependency}

Lägg till Experience Rollouts Java SDK i ditt projekts `pom.xml`:

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## Initiera SDK {#initialize}

SDK initieras en gång när programmet startas med `FloodgateClient.createInstance()`. Metoden tar ett `FloodgateConfiguration`-objekt som du skapar med konfigurationsverktyget.

### Implementera tjänsttoken-återanrop {#service-token-callback}

SDK använder ett återanropsgränssnitt för att hämta en ny tjänsttoken vid körning:

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### Skapa konfigurationsobjektet {#configuration}

Använd konfigurationsverktyget för att konfigurera SDK:

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

Använd `FgEnv.STG` för scenmiljön och `FgEnv.PRD` för produktion.

### Skapa klientinstansen {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## Hämta funktionsflaggor {#retrieve-features}

### Autentiserad användare {#authenticated-user}

Använd en IMS-åtkomsttoken för att hämta funktionsflaggor för den aktuella användaren:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Anonym användare {#anonymous-user}

För oautentiserade användare skickar du ett besökar-ID och en tjänsttoken:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Hämta en specifik funktionsflagga eller release {#specific-feature}

Så här hämtar du en funktionsflagga efter nyckel:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

Ersätt `.withFeatureKey()` med `.withReleaseKey()` om du vill hämta med frisläppningsnyckeln.

## Kontrollera om en funktion är aktiverad {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

För officiella kontroller:

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## Cachehantering {#cache-management}

SDK cache-lagrar flaggdata och uppdaterar dem i ett avsökningsintervall som anges per program i konsolen. Så här utlöser du en cacheuppdatering på begäran:

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### Icke-cachelagrade klienter {#non-cacheable}

För icke-cachelagrade klienter gör `getFeature()` ett live API-anrop varje gång. SDK fortsätter bakgrundsavsökningen och växlar till cachelagrad visning när klienten blir tillgänglig. Stöds från och med SDK version 0.8.

## Konfigurationsalternativ {#configuration-options}

Följande valfria konfigurationsmetoder är tillgängliga i verktyget:

| Alternativ | Metod | Beskrivning |
|---|---|---|
| Använd alltid cache | `.alwaysCache()` | Byter ut cachelagringssvaret från API:t; används för flaggor utan målgruppsregler |
| Inaktivera cachelagring | `.neverCache()` | Inaktiverar standardcachelagring. Användbart för anpassad logik för cacheuppdatering |
| Anpassad HTTP-klient | `.withHttpClient(client)` | Använd din egen HTTP-klient |
| Anpassad exekverare | `.withScheduledExecutorService(executor)` | Använd din egen schemalagda exekerare för bakgrundsavsökning |
| Inkludera kontrollgrupp | `.includeControlGroup()` | Returnerar kontrollgruppsdata i funktionssvaret |

## Hantera fel {#error-handling}

Radbryt `getFeatures()` anrop för att fånga upp SDK-undantag:

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## Se även {#see-also}

* [Versionsinformation för Java SDK](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Integreringssteg](../../integrate/integration-steps.md)
