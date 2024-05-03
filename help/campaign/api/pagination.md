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
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# Sidnumrering

Som standard läses 25 resurser in i en lista.

The **_lineCount** kan du begränsa antalet resurser som anges i svaret.  Du kan sedan använda **nästa** för att visa nästa resultat.

>[!NOTE]
>
>Använd alltid URL-värdet som returneras i **nästa** nod för att utföra en sidnumreringsbegäran.
>
>The **_lineStart** begäran beräknas och måste alltid användas inom den URL som returneras i **nästa** nod.

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

Svar på begäran, med **nästa** nod som ska utföra sidnumrering.

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

Som standard är **nästa** noden är inte tillgänglig vid interaktion med tabeller med stora mängder data. Om du vill kunna utföra sidnumreringen måste du lägga till **_forcePagination=true** parameter till din call URL.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>Antalet poster över vilka en tabell anses vara stor definieras i Campaign Standard **XtkBigTableThreshold** alternativ. Standardvärdet är 100 000 poster.
