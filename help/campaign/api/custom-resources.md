---
title: Anpassade resurser
description: Läs mer om anpassad resurshantering med API:er/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 2%

---

# Anpassade resurser {#custom-resources}

Adobe Campaign levereras med en fördefinierad datamodell, där data definieras med olika resurser. Du kan utöka datamodellen som tillhandahålls genom att utöka resurserna för att lägga till egna anpassade fält eller anpassade tabeller, till exempel köp- eller produkttabeller.

Anpassade resurser är tillgängliga via API:er med **/profileAndServicesExt** slutpunkt och det anpassade resursnamnet.

`https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/`

>[!NOTE]
>
>Använd alltid <b>&quot;cus&quot;</b> prefix före resursens namn.

Du kan utföra vilken åtgärd som helst med anpassade resurser, förutsatt att de är länkade till profiltabellen. Låt oss titta på tabellstrukturen nedan:

![alt-text](assets/cusresources.png)

I så fall kommer alla resurser från **Transaktion**, **TransactionDetails** och **Produkt** tabeller är tillgängliga så länge de är länkade till **Profil** tabell.

<br/>

***Exempelbegäran***

Exempelbegäran om GET för att få åtkomst till den utökade profilen AndServicesExt-resursen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
```

Den returnerar listan med alla länkade anpassade resurser. Du kan sedan använda resurs-URL:erna för att utföra alla API-åtgärder som beskrivs i den här dokumentationen.

```
{
"apiName": "resourceType",
"cusProduct": {
        "content": ...,
        "data": "/profileAndServicesExt/cusProduct/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusProduct/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
"cusTransaction": {
        "content": ...,
        "data": "/profileAndServicesExt/cusTransaction/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusTransaction/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
    ...
}
```
