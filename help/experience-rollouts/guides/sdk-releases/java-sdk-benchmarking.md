---
title: SDK prestandatester
description: Granska Java SDK-jämförelseresultat för Adobe Experience Rollouts, inklusive svarstidsmått för olika antal funktionsflaggor under normala inläsningsförhållanden.
source-git-commit: 8b8b5db1a28af3a3ac29aecf26482f70eb84c714
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 6%

---


# SDK prestandatester {#sdk-benchmarking}

Experience Rollouts Java SDK är ett prestandatest för att ge integrerande team en tillförlitlig uppskattning av de resurser och svarstider som förväntas när SDK körs i deras infrastruktur.

## Testmiljö {#test-environment}

Benchmarking utfördes på en Spring Boot-applikation med följande fasta konfiguration:

* **CPU-kärnor:** 8
* **JVM-minne:** 4096 MB

## Testantaganden {#test-assumptions}

Följande villkor var konstanta för alla körningar av referensvärden:

* Testade funktionsflaggor: 8 till 128
* Kontextvariabler per funktionsflagga: 2 (typ `STRING`, längd 36 tecken)
* Genomsnittlig belastning: 15 000 begäranden per minut (RPM)
* Aktiva trådar: 100

## Resultat {#results}

Tabellen nedan visar den 99,99:e percentilsvarstiden för `getFeatures()` anrop när antalet funktionsflaggor ökar:

| Antal funktionsflaggor | Kontextvariabler per flagga | Svarstid (ms, p99.99) |
|---|---|---|
| 8 | 2 | &lt; 0.5 |
| 16 | 2 | &lt; 0.5 |
| 32 | 2 | &lt; 0.5 |
| 64 | 2 | &lt; 1 |
| 128 | 2 | &lt; 1 |

## Tolka resultaten {#interpretation}

Riktmärkena ovan representerar prestanda under de specifika testförhållanden som beskrivs. Eftersom SDK körs inuti programmets infrastruktur varierar de faktiska svarstiderna beroende på vilka faktorer som är specifika för din miljö:

* CPU och antal kärnor
* JVM-stackstorlek och skräpinsamlingsbeteende
* Trådtillgänglighet och kontextväxling
* Aktuell systembelastning vid begäran

Använd dessa siffror som en planeringsbas i stället för som garanterade prestandamål för produktionsmiljön.

## Se även {#see-also}

* [Integreringsguide för Java SDK](java/java-sdk-integration-guide.md)
* [Versionsinformation för Java SDK](java/java-sdk-release-notes.md)
* [SDK](../integrate/sdks.md)
