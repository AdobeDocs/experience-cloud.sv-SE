---
title: Skapa profiler med API:er
description: Lär dig mer om hur du skapar profiler med API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Skapa profiler med API:er {#creating-profiles-api}

Skapa profiler med en **POST** begäran på profilresursen.

>[!CAUTION]
>
>Om du vill associera en <b>orgUnit</b> till den skapade profilen måste du utöka profilresursen med det här fältet och, efter att tillägget har publicerats, utföra en begäran om POST på <b>ProfileAndServicesExt</b> slutpunkt.
>
>Mer information om profilens resurstillägg finns i <a href="https://helpx.adobe.com/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Kampanjdokumentation</a>.

<br/>

***Exempelbegäran***

Exempelbegäran om POST för att skapa en profil med e-postmeddelandet&quot;john.doe@mail.com&quot;.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Den returnerar den nyligen skapade profilen med e-postadressen&quot;john.doe@mail.com&quot;.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
