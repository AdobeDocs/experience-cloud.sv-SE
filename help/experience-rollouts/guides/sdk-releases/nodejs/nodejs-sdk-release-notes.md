---
title: Node.js Versionsinformation för SDK
description: Versionsinformation för Experience Rollouts Node.js SDK, inklusive en ändringslogg med nya funktioner, förbättringar och felkorrigeringar för alla publicerade versioner.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Node.js Versionsinformation för SDK {#nodejs-sdk-release-notes}

På den här sidan listas versionshistoriken för Experience Rollouts Node.js SDK. Mer information om integrationsinställningar finns i [Integreringsguiden för Node.js i SDK](nodejs-sdk-integration-guide.md).

## Version 1.0.10 {#v1-0-10}

**Felkorrigeringar och socketförbättringar**

* Åtgärdat `ESOCKETTIMEDOUT`-undantag utlöstes under schemalagda cacheuppdateringar. Parametern `maxSockets` har tagits bort från `featureRequestHttpParams` och `ingestAnalyticsHttpParams` i `createInstance()`.
* Korrigerade ett fel där cacheable-klienter felaktigt markerades som icke-cacheable efter HTTP 304-svar (inte ändrade).
* Borttagen `isReleaseBitEnabled()` - den här metoden stöds inte längre.
* Förbättrade loggningsresultat för bättre diagnostik.
* Test- och disponeringsmappar ingår inte längre i det publicerade npm-paketet.

## Version 1.0.5 {#v1-0-5}

**Stabilitetsförbättringar**

Allmänna korrigeringar för cachelagring av uppdateringshantering och edge-fall för SDK-initiering.

## Version 1.0.3 {#v1-0-3}

**Inledande stabil version**

Första produktionsutgåvan av Node.js SDK som stöder hämtning av autentiserade, anonyma och standardflaggor för fullständig utrullning.

## Se även {#see-also}

* [Integreringsguide för Node.js SDK](nodejs-sdk-integration-guide.md)
* [Versionsinformation för Java SDK](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
