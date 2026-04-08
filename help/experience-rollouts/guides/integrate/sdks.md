---
title: SDK
description: Läs mer om SDK-arkitekturen i Adobe Experience Rollouts och det mobila SDK-tillägget för Android.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# SDK {#sdks}

Experience Rollouts innehåller SDK:er för integrering av funktionsflaggor i era program. På den här sidan beskrivs SDK-arkitekturen och de tillgängliga alternativen.

## SDK-arkitektur {#architecture}

Alla Experience Rollouts SDK:er har samma kärnarkitektur:

* **Initiering** - SDK konfigureras vid start och registreras med tjänsten Experience Rollouts.
* **Funktionsåterställning** - SDK hämtar funktionsflaggdata och utvärderar flaggor lokalt.
* **Cachelagring** - SDK cachelagrar funktionsflaggdata och uppdaterar dem på ett konfigurerbart avsökningsintervall (TTL).
* **Felhantering** - Om tjänsten inte är tillgänglig fortsätter SDK att leverera funktionsflaggsutvärderingar från det lokala cacheminnet.

## Tillgängliga SDK:er {#available-sdks}

### Android-tillägg {#android-extension}

Experience Rollout-tillägget för Android kan integreras med Adobe Experience Platform Mobile SDK.

Installationsanvisningar finns i [Integreringsguiden för Android-tillägg](../sdk-releases/android/android-extension-integration-guide.md).

>[!NOTE]
>
>Ytterligare SDK-alternativ för webben och andra mobilplattformar håller på att förberedas och kommer snart att finnas tillgängliga. Kontakta din Adobe-representant för att få hjälp med tidig åtkomst.

## Se även {#see-also}

* [Integreringsguide för Android-tillägg](../sdk-releases/android/android-extension-integration-guide.md)
* [Webbtjänster](web-services.md)
* [Integreringssteg](integration-steps.md)
