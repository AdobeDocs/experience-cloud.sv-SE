---
title: Hantera transaktionsmeddelanden
description: Lär dig hur du hanterar transaktionsmeddelanden med API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
hidefromtoc: true
hide: true
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Hantera transaktionsmeddelanden {#managing-transactional-messages}

När du har skapat och publicerat en transaktionshändelse måste du integrera den som utlöser den här händelsen på webbplatsen.

Du vill t.ex. att en händelse om att kunden överger en varukorg ska utlösas så fort någon av dina kunder lämnar webbplatsen innan de köper produkterna i kundvagnen. För att kunna göra detta måste du som webbutvecklare använda API:t REST Transactional Messages.

1. Skicka en begäran enligt metoden POST, som utlöser [sändning av transaktionshändelsen](#sending-a-transactional-event).
1. Svaret på begäran om POST innehåller en primärnyckel, som gör att du kan skicka en eller flera begäranden via en GET-begäran. Du kan sedan hämta [händelsestatusen](#transactional-event-status).

## Skicka en transaktionshändelse {#sending-a-transactional-event}

Transactional-händelsen skickas via en POST-begäran med följande URL-struktur:

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;ORGANISATION>**: ditt personliga organisations-ID. Se [det här avsnittet](must-read.md).

* **&lt;transactionalAPI>**: API:t endPoints för transaktionsmeddelanden.

  Namnet på API-slutpunkten för transaktionsmeddelanden beror på instanskonfigurationen. Det motsvarar värdet &quot;mc&quot; följt av ditt personliga organisations-ID. Låt oss ta Geometrixx exempel med&quot;geometrixx&quot; som företags-ID. I så fall skulle begäran om POST vara följande:

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

  Observera att API-slutpunkten för transaktionsmeddelanden också visas under API-förhandsgranskningen.

* **&lt;eventID>**: den typ av händelse som du vill skicka. Detta ID genereras när händelsekonfigurationen skapas

### Rubrik för begäran om POST

Begäran måste innehålla rubriken&quot;Content-Type: application/json&quot;.

Du måste lägga till en teckenuppsättning, till exempel **utf-8**. Observera att det här värdet beror på vilket REST-program du använder.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### Brödtext för begäran om POST

Händelsedata finns inuti JSON-POSTEN. Händelsestrukturen beror på dess definition. Knappen för förhandsgranskning av API på resursdefinitionsskärmen innehåller ett exempel på en begäran.

Följande valfria parametrar kan läggas till i händelseinnehållet för att hantera sändning av transaktionsmeddelanden som är länkade till händelsen:

* **förfallodatum** (valfritt): efter det här datumet avbryts sändningen av transaktionshändelsen.
* **schemalagd** (valfritt): från detta datum bearbetas transaktionshändelsen och transaktionsmeddelandet skickas.

>[!NOTE]
>
>Värdena för parametrarna &quot;expiration&quot; och &quot;schedule&quot; följer ISO 8601-formatet. ISO 8601 specificerar användningen av versalen &quot;T&quot; för att separera datum och tid. Den kan dock tas bort från indata eller utdata för bättre läsbarhet.

### Svar på begäran om POST

POSTEN returnerar transaktionshändelsens status när den skapades. Om du vill hämta den aktuella statusen (händelsedata, händelsestatus..) använder du den primärnyckel som returneras av POSTENS svar i en GET-begäran:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***Exempelbegäran***

POST begär att få skicka händelsen.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "email":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

Svar på begäran om POST.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### Status för transaktionshändelse {#transactional-event-status}

I svaret kan du i statusfältet se om händelsen har bearbetats eller inte:

* **väntande**: händelsen väntar - händelsen får den här statusen när den precis har utlösts.
* **bearbetar**: händelsen väntar på att levereras - den håller på att omvandlas till ett meddelande och meddelandet skickas.
* **pausad**: Händelseprocessen pausas. Den bearbetas inte längre, utan ligger i en kö i Adobe Campaign-databasen.
* **bearbetad**: händelsen bearbetades och meddelandet skickades.
* **ignorerades**: händelsen ignorerades av leveransen, vanligtvis när en adress är i karantän.
* **deliveryFailed**: Ett leveransfel uppstod när händelsen bearbetades.
* **routingFailed**: routningsfasen misslyckades - detta kan till exempel inträffa när den angivna händelsetypen inte kan hittas.
* **tooOld**: Händelsen gick ut innan den kunde bearbetas. Detta kan inträffa av olika orsaker, till exempel om en sändning misslyckas flera gånger (detta leder till att händelsen inte längre är uppdaterad) eller när servern inte längre kan bearbeta händelser efter att den har överlagrats.
* **targetingFailed**: Campaign Standarden kunde inte utöka en länk som används för meddelandemål.
