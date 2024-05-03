---
title: Interagera med anpassade resurser
description: Läs mer om anpassad resurshantering med API:er/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Interagera med anpassade resurser {#interacting-with-custom-resources}

The **/customResources** kan du visa anpassade resurser för Campaign i REST. Baserat på detta API finns det en integrering mellan anpassade entiteter och externa slutpunkter.

Slutpunkten /customResources har exakt samma beteende som slutpunkten /profileAndServices.

De anpassade resurser som visas i detta API är:

* alla enheter som inte visas under /profileAndServicesExt
* alla enheter som inte är länkade till profilen och, för dessa enheter, deras underordnade och indirekt underordnade.
* som standard alla enheter som inte är länkade till något, samt deras underordnade och indirekt underordnade.

>[!NOTE]
>De anpassade resurser som är tillgängliga under /profileAndServicesExt visas inte i API:t /customResources.


Här följer ett exempel på hur du hämtar metadata från en anpassad resurs:

```
GET /customResources/resourceType/<customResourceName>
```

GET, POST, PATCH och DELETE används för att skapa, uppdatera eller ta bort objekt.

```
POST /customResources/<customResourceName>
```
