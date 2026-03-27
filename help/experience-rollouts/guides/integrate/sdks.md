---
title: SDK
description: Läs mer om SDK-arkitekturen i Adobe Experience Rollouts och de tillgängliga SDK:erna för Java och Node.js.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# SDK {#sdks}

Experience Rollouts tillhandahåller SDK:er på serversidan för integrering av backend-tjänster. På den här sidan beskrivs SDK-arkitekturen och de tillgängliga alternativen.

## SDK-arkitektur {#architecture}

Alla Experience Rollouts SDK:er har samma kärnarkitektur:

* **Initiering** - SDK konfigureras via ett `createInstance()`-anrop som returnerar ett singleton-objekt.
* **Funktionsåterställning** - `getFeatures()`-metoden hämtar funktionsflaggsdata från SDK.
* **Cachelagring** - SDK cachelagrar svar från tjänsten Experience Rollouts. Cachehanteraren uppdaterar cachen i ett konfigurerbart avsökningsintervall (TTL).
* **Felhantering** - Om tjänsten returnerar 503 behåller cachehanteraren befintliga cachelagrade data och fortsätter att köra utvärderingar av funktionsflaggor. Om data inte har ändrats sedan det senaste anropet (304) uppdateras inte cachen.

## Förutsättningar {#prerequisites}

Innan du integrerar en SDK måste du ha följande:

1. **Program-ID** - Klient-ID:t för varje program som introduceras i Experience Rollouts-konsolen.
2. **Tjänsttoken** - Används av SDK för att anropa API:er för Experience Rollouts i bakgrunden.
3. **API-nyckel** - Används tillsammans med tjänsttoken för API-autentisering.

## Tillgängliga SDK:er {#available-sdks}

### Java SDK {#java-sdk}

Java SDK distribueras via Maven. Lägg till beroendet till projektets `pom.xml` som ska integreras. För fjädringsbaserade program ställer Maven-beroendet automatiskt in SDK-cachen innan programmet läses in helt.

Viktiga specifikationer för Java SDK:

* **JDK som stöds:** JDK 8 och senare
* **Klienter som inte kan nås:** Stöds från och med SDK version 0.8. För icke-cachelagrade klienter gör `getFeature()` ett live API-anrop i stället för att läsa från cache. SDK fortsätter att avfråga i bakgrunden och växlar till cachebaserad visning om klienten blir tillgänglig.

Installationsanvisningar finns i [Java SDK-integreringsguiden](../sdk-releases/java/java-sdk-integration-guide.md).

### Node.js SDK {#nodejs-sdk}

Node.js SDK distribueras via npm.

Installationsanvisningar finns i [Integreringsguiden för Node.js SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md).

## Se även {#see-also}

* [Webbtjänster](web-services.md)
* [Integreringssteg](integration-steps.md)
* [Integreringsguide för Java SDK](../sdk-releases/java/java-sdk-integration-guide.md)
* [Integreringsguide för Node.js SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
