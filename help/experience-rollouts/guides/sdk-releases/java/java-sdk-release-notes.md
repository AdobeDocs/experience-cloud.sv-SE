---
title: Versionsinformation för Java SDK
description: Versionsinformation för Experience Rollouts Java SDK, inklusive en ändringslogg med nya funktioner, förbättringar och felkorrigeringar för alla publicerade versioner.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Versionsinformation för Java SDK {#java-sdk-release-notes}

På den här sidan visas versionshistoriken för Experience Rollouts Java SDK. Mer information om integrationsinställningar finns i [Integreringsguiden för Java SDK](java-sdk-integration-guide.md).

## Version 4.0.6 {#v4-0-6}

**Kontrollera gruppdata i svar**

Nu kan du hämta variant- och kontrollgruppsdata i SDK-svaret, vilket matchar beteendet i REST-funktionens API:er. Om du vill aktivera det här lägger du till `.includeControlGroup()` i `FloodgateConfiguration`-verktyget.

## Version 4.0.5 {#v4-0-5}

**Stabilitets- och prestandaförbättringar**

Mindre interna förbättringar för cache-uppdatering, tillförlitlighet och hantering av anslutningar.

## Version 4.0.4 {#v4-0-4}

**Förbättringar av principen Försök igen**

Förbättrat standardbeteende för nya försök vid tillfälliga tjänstfel.

## Version 4.0.3 {#v4-0-3}

**Felkorrigeringar**

Allmänna stabilitetskorrigeringar för kantfall vid asynkron initiering.

## Version 4.0.1 (Beta) {#v4-0-1-beta}

**Beta version av SDK 4.x**

Introducerat DX-klientstöd, DX-regionskonfiguration och stöd för AEP (sandbox).

## Version 3.1.0 {#v3-1-0}

**Direktuppspelningsstöd för DX-klienter**

SSE-baserad strömning har lagts till för att meddela SDK-kunder om flagguppdateringar i nära realtid.

## Version 3.0.x {#v3-0-x}

**Kravet Java 11 introducerades**

Från och med version 3.0.0 kräver SDK JDK 11 eller senare. Tidigare versioner har stöd för JDK 8+.

Introducerade stöd för målgrupper efter referens för DX-klienter, vilket gör att återanvändbara målgruppsdefinitioner kan refereras av ID i funktionsenheter.

## Version 2.x {#v2-x}

**Klientsupport som inte kan nås (från 0.8)**

Klienter som inte är cachelagrade kan anropa `getFeature()` live i stället för att läsa från SDK-cachen. SDK fortsätter att avfråga i bakgrunden och växlar till cachebaserad visning när klienten blir tillgänglig.

Ytterligare 2.x-förbättringar innehöll nya alternativ för att skapa (`alwaysCache()`, `neverCache()`, stöd för anpassade HTTP-klienter och exekverare), funktioner och frisläppa nyckelfiltrering samt personifierad hämtning av användare.

## Version 1.x {#v1-x}

Initial release-serie. Stöd för JDK 8+, integrering av Maven-beroenden och grundläggande hämtning av autentiserade och anonyma funktionsflaggor.

## Se även {#see-also}

* [Integreringsguide för Java SDK](java-sdk-integration-guide.md)
* [Node.js Versionsinformation för SDK](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
