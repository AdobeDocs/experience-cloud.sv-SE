---
title: Kom igång med dynamiska rapporter
description: WLäs mer på användningsavtalet för dynamisk rapportering
level: Beginner
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
audience: end-user
source-git-commit: c6a6cb7da640c9c29af71487e468f38ebf51d4f6
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Dynamiskt användningsavtal för rapportering {#pii-agreement}

Syftet med användningsavtalet för dynamisk rapportering är att det ska fungera som ett popup-medgivande för databearbetning. Som standard är avtalet bara synligt och kan bara accepteras eller avvisas av användare som tilldelats administrationsrättigheter.

Om du vill få åtkomst till användningsavtalet för dynamisk rapportering väljer du **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**.

![](assets/pii-agreement.png)

Tre alternativ är tillgängliga:

* **[!UICONTROL Ask me later]**: Innan du har godkänt eller avvisat avtalet visas inte profildimensionerna i dina rapporter och dina kunders personliga ID-information samlas inte in eller skickas.
* **[!UICONTROL Accept]**: Genom att acceptera det här avtalet ger du Adobe Campaign tillstånd att registrera dina kunders personuppgifter och överföra dem till rapporteringen eller datacentret.
* **[!UICONTROL Decline]**: Om du avböjer avtalet visas inte profildimensionerna i dina rapporter och dina kunders personliga ID-information samlas inte in eller skickas. Observera att i det här fallet kommer externalID fortfarande att samlas in och användas för att identifiera slutanvändare.

Tabellen nedan visar vad som händer efter att du har godkänt det här avtalet beroende på din region.

|  | Dynamisk rapportering | Microsoft Dynamics 365-anslutning |
|---|---|---|
| Amerika och Asien-Stillahavsregionen | **Funktionen är tillgänglig**. <br>All körklar information (dvs. ort, land/region, stat, kön och segment baserat på ålder) och anpassad profilinformation har överförts till USA:s rapportcenter. | **Funktionen är tillgänglig**. <br>Alla färdiga och anpassade profilfält och händelsefält i Adobe Campaign behandlas i datacentret i USA. |
| EMEA (Europa, Mellanöstern och Afrika) | **Funktionen är tillgänglig**. <br>All körklar information (t.ex. ort, land/region, stat, kön och segment utifrån ålder) och anpassad profilinformation har överförts till EMEA: s rapportcenter. | **Funktionen är tillgänglig.** <br>Alla färdiga och anpassade profilfält och Adobe Campaign händelsefält har bearbetats i EMEA:s datacenter. <br>**[!UICONTROL Control data]**&#x200B;som innehåller registreringsdata för Adobe I/O och ID:n för kundslutanvändarhändelser som skickas och lagras i datacentret i USA. |

Tabellen nedan visar vad som händer efter att avtalet har avböjts beroende på din region. Observera att även om du avböjer det här avtalet är rapportering om leveranser och integrering med Microsoft Dynamics 365 fortfarande tillgänglig.

| Län | Dynamisk rapportering | Microsoft Dynamics 365-anslutning |
|---|---|---|
| Amerika och Asien-Stillahavsregionen | **Funktionen är tillgänglig**. <br> Ingen körklar och anpassad profilinformation överfördes till USA:s rapportcenter med undantag för ExternalID. | **Funktionen är tillgänglig**. <br>Inga färdiga eller anpassade profilfält har skickats till datacentret i USA, med undantag för externt ID och mottagar-ID. <br>Alla Adobe Campaign-händelsefält har bearbetats i det amerikanska datacentret med undantag för spegelsides-ID. |
| EMEA (Europa, Mellanöstern och Afrika) | **Funktionen är tillgänglig**. <br>Ingen körklar och anpassad profilinformation har överförts till EMEA: s rapportcenter med undantag för ExternalID. | **Funktionen är tillgänglig.** <br>Inga färdiga eller anpassade profilfält har skickats till EMEA-datacentret, med undantag för externt ID och mottagar-ID. <br>Alla Adobe Campaign-händelsefält har bearbetats i EMEA-datacentret med undantag för spegelsides-ID. |

Det här alternativet är inte slutgiltigt. Du kan alltid ändra det genom att välja alternativet **[!UICONTROL realtimeReporting_collectPII]** i **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**.

Värdet kan ändras när som helst. Värdet 1 motsvarar **[!UICONTROL Ask me later]**, 2 **[!UICONTROL Decline]** och 3 **[!UICONTROL Accept]**.
