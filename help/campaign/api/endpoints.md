---
title: Slutpunkter
description: Läs mer om API:ernas slutpunkter.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 9f6d3da6-374d-47f5-bc8f-b31b19cbb5ca
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# Slutpunkter {#endpoints}

Tillgängliga slutpunkter för Adobe Campaign REST API:

* **/profileAndServices**: interagerar med utanför rutorna. Utökade fält är inte tillgängliga med den här slutpunkten.
* **/profileAndServicesExt**: interagerar med anpassade fält som läggs till under det anpassade resurstillägget för profiler eller tjänster. Mer information om anpassade resurser finns i [det här avsnittet](custom-resources.md).
* **/&lt;transactionalapi>**: interagera med API:t för transaktionsmeddelanden (namnet på API-slutpunkten för transaktionsmeddelanden beror på din instanskonfiguration). Mer information om detta finns i [det här avsnittet](managing-transactional-messages.md).
* **/workflow/execution**: interagerar med arbetsflöden. Mer information om detta finns i [det här avsnittet](controlling-a-workflow.md).

Som standard är de viktigaste tillgängliga resurserna för **profileAndServices** och **profileAndServicesExt** API:er är:

* **/profile**: interagerar med profiler från Campaign-databasen. Använd kommandot **/service** slutpunkt. Mer information om profiler i Campaign finns i [Kampanjdokumentation](https://helpx.adobe.com/campaign/standard/audiences/using/about-profiles.html).
* **/service**: hantera prenumerationstjänster. Mer information om tjänster i Campaign finns i [Kampanjdokumentation](https://helpx.adobe.com/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Alla andra resurser som har utökats eller skapats är tillgängliga via **ProfileAndServicesExt** Endast API. De måste vara kopplade till **Profil** resurs för att vara tillgänglig.
