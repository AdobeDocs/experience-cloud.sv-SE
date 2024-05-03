---
title: Kontrollera ett arbetsflöde
description: Lär dig hur du styr ett arbetsflöde med API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 9%

---

# Kontrollera ett arbetsflöde {#controlling-a-workflow}

Du kan styra ett arbetsflöde direkt från REST API, via en POST som innehåller arbetsflödes-ID och det körningskommando som krävs:

`POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands`

>[!CAUTION]
>
>Om arbetsflödes-ID ändras i Adobe Campaign fungerar inte längre API-begäran.

Fyra körningskommandon finns för att styra ett arbetsflöde:

* Starta
* Pausa
* Återuppta
* Stoppa

Mer information om körningskommandona finns i [Kampanjdokumentation](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/executing-a-workflow/about-workflow-execution.html).

<br/>

***Exempelbegäranden***

* Starta ett arbetsflöde.

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"start"}'
  ```

  <!-- + réponse -->

* Stoppa ett arbetsflöde.

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"stop"}'
  ```

  <!-- + réponse -->
