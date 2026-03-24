---
title: Lägen för upplevelseutrullningar
description: Läs om de två målinriktningslägena i Adobe Experience Rollouts - målgruppsanpassning på användarnivå och målinriktning på organisationsnivå - och när ni ska använda varje.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Lägen för upplevelseutrullningar {#modes}

Upplevelseutrullningar ger två olika målinriktningslägen för funktioner. De har olika syften för versionskontroll och är utformade för en viss typ av tillämpning eller användningsfall.

>[!TIP]
>
>Välj läge baserat på vad du styr: enskilda användarsessioner eller organisation och omfång för miljön.

## Målgruppsanpassning på användarnivå {#user-level}

### Ökning {#user-level-overview}

Målgruppsanpassning på användarnivå gör det möjligt att lansera funktioner på individuell användarnivå. Det har stöd för exakt målinriktning efter specifika användare, interna testare, kanarieanvändare och procentuella gradvisa driftsättningar.

Det här läget passar bäst för program som behöver variera upplevelsen baserat på vem som är inloggad.

### När ska du använda {#user-level-when}

Använd målgruppsanpassning på användarnivå när du vill:

* Aktivera en funktion för specifika användare
* Kör A/B-försök
* Testa kanyler med en liten grupp före en större utrullning
* Dra gradvis igång en funktion utifrån en procentandel användare
* Finjustera upplevelsen baserat på enskilda användarattribut (t.ex. e-postdomän eller profildata)

### Begränsningar {#user-level-limitations}

Målinriktning på användarnivå är inte utformat för följande scenarier:

* Kontrollerar inte funktioner på organisations-, miljö- eller regionnivå
* Inte avsett för aktivering av klientövergripande funktioner eller behörighetsgating

## Målgruppsanpassning på organisations- och miljönivå {#org-level}

### Ökning {#org-level-overview}

Med målinriktning på organisationsnivå kan funktioner lanseras i organisationen, miljön och regionen. Det styr funktionstillgängligheten i hela organisationer eller specifika driftsättningsmiljöer, i stället för för för enskilda användare.

Det här läget är utformat för funktionsgating på företagsnivå och miljöspecifika utrullningar.

### När ska du använda {#org-level-when}

Använd målinriktning på organisationsnivå när du vill:

* Aktivera en funktion för en hel organisation
* Kontrollera tillgängligheten efter miljö (till exempel stadium kontra produktion)
* Utför en regional utrullning
* Gatufunktioner som baseras på tillstånd eller prenumerationsnivå

### Begränsningar {#org-level-limitations}

Målinriktning på organisations- och miljönivå är inte utformat för följande scenarier:

* Har inte stöd för avancerad användarprofilbaserad målinriktning
* Har inte stöd för procentbaserad utrullning på individuell användarnivå
* Inte avsedd för experimenterande eller A/B-tester

## Jämförelse {#comparison}

| Dimension | Målgruppsanpassning på användarnivå | Målgruppsanpassning på organisations- och miljönivå |
|---|---|---|
| Kontrollomfång | Enskild användare | Organisation, miljö, region |
| Målgruppsbas | Användarprofil och attribut | Organisations- och miljösammanhang |
| Procentvärde för utrullning | Ja | Nej |
| A/B-tester | Ja | Nej |
| Företagsgruppering | Nej | Ja |

## Välja rätt läge {#choosing}

* Om din fråga är *&quot;Vilka användare ska se den här funktionen?&quot;* → Använd **målgruppsanpassning på användarnivå**
* Om din fråga är *&quot;Vilka organisationer eller miljöer ska ha den här funktionen?&quot;* → Använd **organisation och miljönivå som mål**
