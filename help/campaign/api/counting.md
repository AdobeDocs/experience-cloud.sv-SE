---
title: Räkning
description: Lär dig hur du utför räkningsåtgärder.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: d6354249-3b0d-4532-951f-b0fae953f7e1
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 2%

---

# Räkning

Adobe Campaign REST API kan räkna antalet poster i en begäran. Om du vill göra det använder du den URL som returneras i noden **count**.

<br/>

***Exempelbegäran***

Om du vill räkna alla tjänster som har ett **messageType**-värde som är lika med &quot;sms&quot;, utför du en GET-begäran med filtret **byChannel**.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=sms \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar de tjänster som motsvarar filtret.

```
{
    "content": [
        {
            ...
            "messageType": "sms",
            "mode": "newsletter",
            "name": "SVC6",
            ...
        },
        ...
    ],
    "count": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy"
    },
    "serverSidePagination": true
}
```

Utför en GET-förfrågan på **count**-nodens URL för att hämta antalet resultat.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Det returnerar antalet poster.

```
{
    "count": 26
}
```
