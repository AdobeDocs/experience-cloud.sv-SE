---
title: Metadatamekanism
description: Läs mer om metadatafunktionen.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 1%

---

# Metadatamekanism {#metadata-mechanism}

Du kan hämta resursmetadata med **resourceType** i en GET-förfrågan:

`GET /profileAndServices/resourceType/<resourceName>`

Svaret returnerar huvudmetadata från resursen (alla andra fält är beskrivande eller interna):

* The **Innehåll** noden returnerar resursens fält. För varje fält i **innehåll** nod hittar vi följande fält:

   * &quot;apiName&quot;: namnet på attributet som används i API:erna.
   * &quot;type&quot;: det här är definitionen på högnivåtyp (sträng, tal, länk, samling, uppräkning...).
   * &quot;dataPolicy&quot;: fältets värde måste följa givna policyregler. Om regeln dataPolicy till exempel har värdet &quot;email&quot; måste värdet vara en giltig e-postadress. Under en PATCH eller POST kan dataPolicy kontrollera värdet eller ändra värdet till transform (till exempel smartCase).
   * &quot;category&quot;: anger fältets kategori i frågeredigeraren.
   * &quot;resType&quot;: Detta är den tekniska typen.

     Om&quot;type&quot; har fyllts i med värdet&quot;link&quot; eller&quot;collection&quot; är värdet resTarget namnet på resursen som länken pekar på.
Om &quot;type&quot; har fyllts i med värdet &quot;enumeration&quot;, läggs ett &quot;values&quot;-fält till och varje uppräkningsvärde beskrivs i **values** nod.

* The **Filter** noden returnerar URL:en för att hämta associerade filter. Mer information om filter finns i [det här avsnittet](filtering.md) -avsnitt.

<!-- créer une section au même niveau sur les liens -->
<!-- dans l'exemple: birthdate, email +  mettre 2 liens : un de type 1-1 , 1-N
si on prend l'exemple de l'org unit, on aura un bon exemple lien -->
<!-- plus reparler du node Data -->

<br/>

***Exempelbegäran***

Utför en GET-förfrågan för resursen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Den returnerar den fullständiga beskrivningen av profilresursen.

```
{
...
"content": {
  "email": {...},
    ...
    },
"data": "/profileAndServices/profile/",
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>"
    },
"help": "Identified profiles",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/metadata",
"label": "Profiles",
"mandatory": false,
"name": "profile",
"pkgStatus": "never",
"readOnly": false,
"schema": "nms:recipient",
"type": "item"
}
```
