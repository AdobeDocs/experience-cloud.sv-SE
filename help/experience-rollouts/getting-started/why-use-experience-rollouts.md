---
title: Varför använda upplevelseutrullningar
description: Läs om de viktigaste användningsområdena för Adobe Experience Rollouts, från selektiv funktionstestning till samordnade versioner av flera program.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Varför använda upplevelseutrullningar {#why-use}

Upplevelseutrullningar är det rätta verktyget när ni behöver styra vilka som ser en funktion och när - oavsett om ni testar under utvecklingen, validerar med en delmängd av användarna eller samordnar en stor release för flera team.

## Vanliga användningsområden {#use-cases}

**Selektiv testning under utveckling**
Testa en funktion mot din egen session medan andra utvecklare fortsätter att arbeta utan att påverkas. Ingen komplex kodförgrening krävs.

**Mellanlagrad utrullning med användarfeedback**
Släpp en funktion först för en liten grupp användare. Samla in feedback, åtgärda problem och utöka sedan målgruppen gradvis före en fullständig release.

**gradvis utrullning till produktion**
Öppna en ny funktion stegvis - 1 %, 10 %, 50 % och sedan 100 % av användarna. Övervaka prestanda och användarsvar i varje steg. Om något går fel stänger du av det omedelbart.

**Hantering av backend-belastning**
fasa ut en utrullning stegvis för att undvika plötsliga trafiktoppar på backend-tjänster, i stället för att utsätta alla användare för en ny funktion samtidigt.

**Samordnade versioner av flera program**
Aktivera en funktion samtidigt i flera program och team för en viss användargrupp. Upplevelseutrullningar säkerställer enhetlighet över hela uppspelningsytan.

**Uppskjutna versioner**
Driftsätt kod i produktionen i förväg och aktivera sedan funktionen i ett visst ögonblick - till exempel i början av en produktlanseringshändelse - utan att behöva ändra koden i sista minuten.

**Avsluta switch**
Om ett problem upptäcks efter att produkten släppts stänger du av funktionen omedelbart utan någon snabbkorrigering eller omdistribution.
