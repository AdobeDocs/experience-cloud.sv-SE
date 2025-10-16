---
title: Uppdatera profiler
description: Läs mer om hur du uppdaterar profiler med API:er
role: Developer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till migrerade Campaign Standard-användare"
exl-id: fa3796ee-a00c-4d70-bf3d-e8d2099f1116
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---

# Uppdatera profiler med API:er{#updating-profiles-api}

Uppdatering av profiler utförs med en **PATCH**-begäran.

`https://mc.adobe.io/<ORGANIZATION>/campaign/<apiName>/<resourceName>/<PKEY>`

1. Det första steget är att **hämta profilen**.

1. Utför en **PATCH-begäran** på profilen i en andra begäran med den slutförda informationen i nyttolasten.

1. För att kontrollera om PATCH-begäran har uppdaterat profilen kan vi utföra en slutgiltig GET-förfrågan.

<br/>

***Exempelbegäran***

Exempelbegäran från GET om att hämta en profil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Svar på begäran.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "Amy",
            "lastName":"Dakota",
            "birthDate": "1980-10-24",
            ...
        }
    ]
}
```

PATCH begär att få uppdatera &quot;phone&quot;-attributet.

```
-X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-d '{"phone":"3301020304"}'
```

Den returnerar PKEY och URL för att hämta den uppdaterade profilen.

```
{
    "PKey": "<PKEY>",
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/@2v1dr3ZKJveMDhAdh0MPnh9hNQQ93qb7AW6BNVVKknjwXvTZRBAgUqz1SNcB4ZndgjqOofx3BwBZYBftlmObISoM3rs"
}
```
