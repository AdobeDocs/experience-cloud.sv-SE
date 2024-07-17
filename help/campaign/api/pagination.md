---
title: Sidnumrering
description: Lär dig hur du utför sidnumreringsåtgärder.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# Sidnumrering

Som standard läses 25 resurser in i en lista.

Med parametern **_lineCount** kan du begränsa antalet resurser som anges i svaret.  Du kan sedan använda noden **next** för att visa nästa resultat.

>[!NOTE]
>
>Använd alltid URL-värdet som returneras i noden **next** för att utföra en sidnumreringsbegäran.
>
>**_lineStart**-begäran beräknas och måste alltid användas inom den URL som returneras i noden **next**.

<br/>

***Exempelbegäran***

Exempelbegäran om GET för att visa 1 post för profilresursen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Svar på begäran, med noden **next** som utför sidnumrering.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "John",
            "lastName":"Doe",
            "birthDate": "1980-10-24",
            ...
        }
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

Som standard är noden **next** inte tillgänglig när den interagerar med tabeller med stora mängder data. För att kunna utföra paginering måste du lägga till parametern **_forcePagination=true** i din anrops-URL.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>Antalet poster över vilka en tabell anses vara stor definieras i Campaign Standarden **XtkBigTableThreshold** . Standardvärdet är 100 000 poster.
