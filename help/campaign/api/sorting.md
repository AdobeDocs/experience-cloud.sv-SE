---
title: Sortering
description: Läs mer om hur du utför sorteringsåtgärder
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 7db25b8d-a6f1-4151-bf37-c47e9991ae48
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 10%

---

# Sortering

Sortering är tillgängligt som standard i stigande ordning. Om du vill sortera i fallande ordning lägger du till **%20desc** i värdet för parametern **_order**.

Om du vill veta om ett fält kan sorteras kontrollerar du parametern &quot;sorterable&quot; i metadata för resursen. Mer information om detta finns i [det här avsnittet](metadata-mechanism.md).

<br/>

***Exempelbegäranden***

* Exempelbegäran om GET för att hämta e-post i databasen i alfabetisk ordning.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran.

  ```
  {
  "content": [
      "adam@email.com",
      "allison.durance@example.com",
      "amy.dakota@mail.com",
      "andrea.johnson@mail.com",
      ...
  ]
  ...
  }
  ```

* Exempelbegäran om GET för att hämta e-postmeddelandet i databasen i fallande alfaordning.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email%20desc \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Svar på begäran.

  ```
  {
  "content": [
      "tombinder@example.com",
      "tombinder@example.com",
      "timross@example.com",
      "john.smith@example.com",
      ...
  ]
  }
  ```
