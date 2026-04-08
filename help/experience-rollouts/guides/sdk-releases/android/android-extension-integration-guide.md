---
title: Experience Rollout-tillägg för Android integreringsguide
description: Lär dig hur du integrerar tillägget Experience Rollout med Adobe Experience Platform Mobile SDK på Android.
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 1%

---


# Experience Rollout-tillägg för Android {#android-extension-integration-guide}

Den här guiden beskriver hur du integrerar tillägget Experience Rollout med Adobe Experience Platform Mobile SDK på Android.

## Förutsättningar {#prerequisites}

Innan du implementerar tillägget Experience Rollout måste du se till att du har:

* En mobil egenskap konfigurerad i [Adobe Experience Platform Data Collection](https://experience.adobe.com/#/data-collection)
* Tillägget Experience Rollout har installerats och konfigurerats i din mobila egenskap
* Ett Adobe Experience Cloud-organisations-ID
* SDK: API 21 (Android 5.0 Lollipop)

## Tilläggsberoenden {#extension-dependencies}

Tillägget Experience Rollout kräver följande Adobe Experience Platform-tillägg:

| Tillägg | Beskrivning | Obligatoriskt |
|---|---|---|
| Mobile Core | Tillhandahåller grundläggande funktioner, inklusive konfiguration och händelsebearbetning | Ja |
| Livscykel | Samlar in programlivscykel och sessionsdata för Mobile SDK | Ja |
| Edge Network | Möjliggör kommunikation med Adobe Experience Platform Edge Network | Ja |
| Edge Identity | Hanterar användaridentitet för Edge Network | Ja |

Se till att dessa tillägg är installerade i din mobila datainsamling och ingår i dina appberoenden.

## Konfigurera tillägget för upplevelseutrullning i datainsamling {#configure}

### Installera tillägget {#install-extension}

1. Logga in på [Adobe Experience Platform Data Collection](https://experience.adobe.com/#/data-collection).
1. Markera fliken **Taggar** och välj din mobila egenskap.
1. Navigera till **Tillägg** > **Katalog**.
1. Sök efter **tillägget för upplevelseutrullning** och välj **Installera**.
1. Konfigurera tilläggsinställningarna:

   | Inställning | Beskrivning |
   |---|---|
   | Sandbox | Adobe Experience Platform-sandlådan som innehåller din Experience Rollout-konfiguration |
   | Program-ID | En unik identifierare för programmet i Experience Rollout |
   | Datauppsättnings-ID | Adobe Experience Platform-datauppsättnings-ID för analyshändelsedata |

1. Välj **Spara**.
1. Uppdatera konfigurationen genom att följa [publiceringsprocessen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview).

### Hämta miljöfil-ID {#environment-file-id}

1. Navigera till **Miljö** i din mobila egenskap.
1. Markera kryssruteikonen under kolumnen **Installera** för din miljö.
1. I dialogrutan **Installationsanvisningar för mobila enheter** kopierar du **miljöfil-ID**.

## Lägg till tillägget för upplevelseutrullning i din app {#add-to-app}

### Lägg till beroenden {#add-dependencies}

Lägg till Mobile SDK-beroenden i ditt projekt. Tillägget Experience Rollout kräver Mobile Core och de Edge-relaterade tilläggen som listas nedan.

#### Använda Övergång med strukturlista (rekommenderas) {#gradle-bom}

Lägg till följande beroenden i appens `build.gradle.kts`-fil:

```kotlin
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation(platform("com.adobe.marketing.mobile:sdk-bom:3.+"))

    // Required extensions
    implementation("com.adobe.marketing.mobile:core")
    implementation("com.adobe.marketing.mobile:lifecycle")
    implementation("com.adobe.marketing.mobile:edge")
    implementation("com.adobe.marketing.mobile:edgeidentity")

    // Experience Rollout extension
    implementation("com.adobe.marketing.mobile:rollout")
}
```

#### Använda Gråskala (Groovy) {#gradle-groovy}

```groovy
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')

    // Required extensions
    implementation 'com.adobe.marketing.mobile:core'
    implementation 'com.adobe.marketing.mobile:lifecycle'
    implementation 'com.adobe.marketing.mobile:edge'
    implementation 'com.adobe.marketing.mobile:edgeidentity'

    // Experience Rollout extension
    implementation 'com.adobe.marketing.mobile:rollout'
}
```

>[!IMPORTANT]
>
>För produktionsprogram rekommenderar Adobe att du använder explicita versionsnummer i stället för dynamiska versioner. Mer information finns i [Hantera övertoningsberoenden](https://docs.gradle.org/current/userguide/dependency_management.html).

### Lägg till behörigheter {#add-permissions}

Lägg till följande behörigheter i din `AndroidManifest.xml`-fil:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### Initiera SDK {#initialize-sdk}

Initiera Mobile SDK i din `Application`-klass innan du anropar någon Experience Rollout-API:er. Använd miljöfil-ID:t från din mobila egenskap med `MobileCore.initialize` så att appen hämtar de rollout-inställningar som du publicerade i datainsamlingen.

#### Använda MobileCore.initialize {#mobile-core-initialize}

Denna API är tillgänglig från och med Android BOM version 3.8.0 och registrerar automatiskt tillägg och aktiverar livscykelspårning.

>[!IMPORTANT]
>
>Använd bara `LoggingMode.ERROR` för produktionsappar. Använd inte `DEBUG` eller `VERBOSE` i releaseversioner.

**Kotlin**

```kotlin
import android.app.Application
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.MobileCore

class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        MobileCore.setLogLevel(LoggingMode.ERROR)

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID")
    }
}
```

**Java**

```java
import android.app.Application;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;

public class MainApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        MobileCore.setLogLevel(LoggingMode.ERROR);

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID", null);
    }
}
```

### Registrera klassen Application {#register-application}

Registrera din `Application`-klass i `AndroidManifest.xml`:

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## Utvärderingssammanhang {#evaluation-context}

`FeatureEvaluationContext` innehåller målattribut (används för matchning av rollout-regel) och valfri identitet (används för analys).

| Metod | Obligatoriskt | Beskrivning |
|---|---|---|
| `withIdentity(namespace, id)` | Nej | Första argumentet: identitetsnamnområde (se [Adobe Identity namespaces](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)). Andra argumentet: identitetsvärde. Inkludera detta när du vill att namnutrymmet och ID ska representeras i analysen för utvärderingen. Om det inte anges används ECID som standard i analysen. Detta används inte för att fatta beslut om aktivering av funktioner. |
| `withAttributes(map)` | Nej | `Map<String, List<String>>`. Nyckel är det kontextattributnamn som används av dina utrullningsregler (till exempel `locale`, `platform`, `appVersion`, `deviceType`). Värde är en lista över möjliga attributvärden för den aktuella användaren/sessionen (till exempel `["en_US"]` eller `["phone"]`). |

**Kotlin**

```kotlin
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext

val attrs = mapOf(
    "locale" to listOf("en_US"),
    "platform" to listOf("ANDROID"),
    "appVersion" to listOf("3.0.0")
)

val ctx = FeatureEvaluationContext.builder()
    .withIdentity("Email", "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Java**

```java
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

Map<String, List<String>> attrs = new HashMap<>();
attrs.put("locale", Arrays.asList("en_US"));
attrs.put("platform", Arrays.asList("ANDROID"));
attrs.put("appVersion", Arrays.asList("3.0.0"));

FeatureEvaluationContext ctx = FeatureEvaluationContext.builder()
        .withIdentity("Email", "customer@example.com")
        .withAttributes(attrs)
        .build();
```

### Exempel på riktningsattribut {#sample-attributes}

| Attribut | Beskrivning | Exempelvärden |
|---|---|---|
| `locale` | Användarens språk | `["en_US"]`, `["fr_FR"]` |
| `platform` | Plattforms-ID | `["ANDROID"]` |
| `appVersion` | Programversion | `["3.0.0"]` |
| `deviceType` | Enhetstyp | `["phone"]`, `["tablet"]` |

## API-referens {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` returnerar om en upplevelseutrullningsfunktion är aktiverad eller inaktiverad för den angivna kontexten. Skicka `featureKey`, en `FeatureEvaluationContext` (valfria målinriktningsattribut och valfri identitet för analyser) och ett återanrop. Se [Utvärderingssammanhang](#evaluation-context).

**Signatur**

*Kotlin*

```kotlin
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<Boolean>
)
```

*Java*

```java
Rollout.isFeatureEnabled(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<Boolean> callback);
```

**Parametrar**

| Parameter | Typ | Beskrivning |
|---|---|---|
| `featureKey` | Sträng | Funktionsnyckel som ska utvärderas i upplevelseutrullning |
| `evaluationContext` | FeatureEvaluationContext | Inkludera målattribut och valfri identitet för analyser efter behov. Använd `FeatureEvaluationContext.builder().build()` för en tom kontext. Se [Utvärderingssammanhang](#evaluation-context). |
| `callback` | AdobeCallback&lt;Boolean> | Anropas med `true` om funktionen är aktiverad, annars `false`. Du kan också skicka `AdobeCallbackWithError<Boolean>` för att hantera `fail(...)`. |

**Exempel**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<Boolean> {
        override fun call(isEnabled: Boolean?) {
            if (isEnabled == true) {
                showNewCheckout()
            } else {
                showDefaultCheckout()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<Boolean>() {
        @Override
        public void call(Boolean isEnabled) {
            if (Boolean.TRUE.equals(isEnabled)) {
                showNewCheckout();
            } else {
                showDefaultCheckout();
            }
        }
    }
);
```

### getFeature {#get-feature}

`getFeature` returnerar den utvärderade funktionsnyttolasten för den angivna kontexten. Använd detta API när du behöver mer än bara aktiverat/inaktiverat och vill ha metadata eller värden för funktioner.

**Signatur**

*Kotlin*

```kotlin
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<FeatureEvaluationResult>
)
```

*Java*

```java
Rollout.getFeature(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<FeatureEvaluationResult> callback);
```

**Parametrar**

| Parameter | Typ | Beskrivning |
|---|---|---|
| `featureKey` | Sträng | Funktionsnyckel som ska utvärderas i upplevelseutrullning |
| `evaluationContext` | FeatureEvaluationContext | Inkludera målattribut och valfri identitet för analyser efter behov. Använd `FeatureEvaluationContext.builder().build()` för en tom kontext. Se [Utvärderingssammanhang](#evaluation-context). |
| `callback` | AdobeCallback&lt;FeatureEvaluationResult> | Anropas med den utvärderade funktionens nyttolast. Kan vara `null` när funktionen inte hittas. Du kan också skicka `AdobeCallbackWithError<FeatureEvaluationResult>` för att hantera `fail(...)`. |

**Svar**

*FeatureEvaluationResult*

| Fält | Typ | Beskrivning |
|---|---|---|
| `id` | Int | Identifierare för numeriska funktioner |
| `key` | Sträng | Funktionsnyckel |
| `releaseKey` | Sträng? | Släpp tangenten för den här funktionen när den är tillgänglig |
| `meta` | Sträng? | Visa metadata som en JSON-sträng när den är tillgänglig |
| `analyticsParam` | AnalyticsParam? | Analysinformation om den utvärderade funktionen |

*AnalyticsParam*

| Fält | Typ | Beskrivning |
|---|---|---|
| `releaseId` | Int | Identifierare för numerisk release |
| `featureId` | Int | Identifierare för numeriska funktioner |
| `variantId` | Sträng? | Variant-ID |

**Exempel**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<FeatureEvaluationResult> {
        override fun call(feature: FeatureEvaluationResult?) {
            val meta = feature?.meta
            if (!meta.isNullOrEmpty()) {
                applyMetaDrivenExperience(meta)
            } else {
                showFallbackExperience()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<FeatureEvaluationResult>() {
        @Override
        public void call(FeatureEvaluationResult feature) {
            String meta = feature != null ? feature.getMeta() : null;
            if (meta != null && !meta.isEmpty()) {
                applyMetaDrivenExperience(meta);
            } else {
                showFallbackExperience();
            }
        }
    }
);
```

### refreshCache {#refresh-cache}

Som standard synkroniserar tillägget Experience Rollout regelbundet de senaste rollout-reglerna och -funktionerna från servern enligt ett schema som du kan konfigurera. Om du behöver en uppdatering tidigare än nästa schemalagda synkronisering, anropar du `refreshCache` för att framtvinga en uppdatering. Vanliga fall är bland annat efter inloggning eller när apptillståndet ändras på ett sätt som bör påverka målsättningen.

**Syntax**

*Kotlin*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

Returnerar versionssträngen för Experience Rollout-tillägget.

**Syntax**

```kotlin
Rollout.extensionVersion(): String
```

**Exempel**

*Kotlin*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## API-sammanfattning {#api-summary}

| API | Returnerar |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext` har målattribut för regler och valfri identitet för analyser. Se [Funktionsutvärdering](#is-feature-enabled). | Booleskt via återanrop |
| `getFeature(featureKey, evaluationContext, callback)`. Returnerar den utvärderade funktionsnyttolasten för den angivna kontexten. Se [getFeature](#get-feature). | FeatureEvaluationResult via återanrop |
| `refreshCache()` | void |
| `extensionVersion()` | Sträng |

## Se även {#see-also}

* [Mobilappar](../../integrate/mobile-applications.md)
* [Integreringssteg](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
