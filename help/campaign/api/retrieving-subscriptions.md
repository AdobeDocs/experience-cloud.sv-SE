---
title: Hämta prenumerationer
description: Lär dig hur du hämtar prenumerationer med API:er
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 6d935074-3196-45c5-97cd-ccb7c80bbba8
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Hämta prenumerationer med API:er {#retrieving-subscriptions-api}

## Hämta profiler som prenumererar på en tjänst

Detta är en tvåstegsprocedur.

1. Hämta prenumerations-URL:en för den önskade tjänsten.
1. Utför en GET-förfrågan på prenumerations-URL:en. Den returnerar en lista över prenumerationer för tjänsten, med varje associerad profil.

>[!CAUTION]
>
>REST API returnerar egenskapen &quot;href&quot; som innehåller den URL som ska användas. <b>Använd alltid den URL som finns i svaret för att göra efterföljande API-begäran</b>.

<br/>

***Exempelbegäran***

Utför en GET-förfrågan för att hämta tjänsten.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar prenumerations-URL:en för tjänsten.

```
  {
    ...
    "messageType": "email",
    "name": "SVC1",
    "subscriptions": {
                "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
    },
    ...
  },
```

Utför en GET-förfrågan på prenumerations-URL:en.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Listan över prenumerationer för tjänsten visas, med varje associerad profil.

```
  {
    ...
    "service": ...,
    "serviceName": "SVC3",
    "subscriber": {
        "PKey": "<PKEY>",
        "email": "",
        "firstName": "John",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
        "lastName": "Doe",
    },
  }
```

## Hämtar de tjänster som en profil prenumererar på

Detta är en tvåstegsprocedur.

1. Hämta prenumerations-URL:en för en viss profil.
1. Utför en GET-begäran på URL:en. Den returnerar en lista över prenumerationer för profilen, med alla tillhörande tjänster.

<br/>

***Exempelbegäran***

Utför en GET-förfrågan för att hämta profilen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar prenumerations-URL:en för profilen.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
    ...
  }
```

Utför en GET-förfrågan på prenumerations-URL:en.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar listan över tjänster som profilen prenumererade på.

```
  {
    ...
    "PKey": "<PKEY>",
    "created": "2017-03-03 10:54:00.363Z",
    "service": {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
      "label": "Sport Newsletter",
      "name": "SVC1",
      "title": "Sport Newsletter (SVC1)"
    },
    ...
  }
```
