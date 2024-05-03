---
title: Kom igång med Campaign REST API:er
description: Skapa integreringar och skapa ett eget ekosystem genom att interagera Campaign med en panel med tekniker.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 48%

---

# Kom igång med Campaign REST API:er {#get-started-apis}

>[!CAUTION]
>
>Den här dokumentationen är avsedd för Adobe Campaign Standard-kunder som migrerar till Campaign v8.
>
>Innan du genomför API-anrop bör du kontrollera de begränsningar för skalor som motsvaras i licensavtalet. Se denna [sida](https://helpx.adobe.com/se/legal/product-descriptions/campaign-standard.html#ITInfrastructureResourcesbyActiveProfilesTiers) för mer information om detta.

Kampanjens REST-API:er är avsedda att göra att du kan **skapa integreringar** för Adobe Campaign och **bygga ditt eget ekosystem** genom att interagera med Adobe Campaign med den tekniska panel som du använder.

Med Adobe Campaign REST API:er får du tillgång till följande funktioner:

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="villkor" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">Profiler</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="villkor" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">Tjänster och prenumerationer</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="villkor" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">Anpassade resurser</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="villkor" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">Arbetsflöden</a></p></td>
</tr></table>

Om du vill använda Campaign REST API:er måste du ha ett Adobe I/O-konto. Detta är ett obligatoriskt första steg för att fortsätta och upptäcka API-funktionerna.
Mer information om detta finns i [det här avsnittet](setting-up-api-access.md).

De API:er vi tillhandahåller använder **standardkoncept** med ett REST-gränssnitt och JSON-nyttolaster.

Alla slutpunkter beskrivs ingående i den här dokumentationen med de allmänna synpunkterna som du bör känna till när du hanterar API:t, den fullständiga API-referensen, kodexempel och snabbstartguider. Alla exempel fungerar med Postman men du kan använda valfri REST-klient.

Om något saknas eller verkar vara felaktigt kan du fråga vår [community](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community).
