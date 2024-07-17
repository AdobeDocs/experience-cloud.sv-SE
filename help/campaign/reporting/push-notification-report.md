---
title: Rapport om push-meddelanden
description: Med den färdiga push-meddelanderapporten får du veta hur dina push-meddelanden fungerar.
level: Intermediate
audience: end-user
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---

# Rapport om push-meddelanden{#push-notification-report}

>[!CAUTION]
>
>Observera att du måste dra och släppa **[!UICONTROL Message type]**-måtten i dina tabeller för att dela upp dina data beroende på leveranstyper, i det här fallet push-meddelanden.

Rapporten **Push-meddelanden** innehåller information om hur push-meddelanden i Adobe Campaign har fungerat. Den här användningsklara rapporten hjälper dig att förstå hur användare interagerar med push-meddelanden, mobilprogram och leveranser.

![](assets/dynamic_report_push.png)

Varje tabell representeras av sammanfattande nummer och diagram. Du kan ändra hur detaljerna visas i deras respektive visualiseringsinställningar.

Den första tabellen **Översikt över push-meddelandeåtaganden** är uppdelad i tre kategorier: per dag, per mobilapp och efter leverans. Den innehåller tillgängliga data för mottagarens reaktivitet för leveransen:

* **[!UICONTROL Processed/sent]**: Totalt antal skickade push-meddelanden.
* **[!UICONTROL Delivered]**: Antal push-meddelanden som har skickats, i relation till det totala antalet skickade push-meddelanden.
* **[!UICONTROL Impressions]**: Antal gånger ett push-meddelande har levererats till enheten och lämnats orört i meddelandecentret. I de flesta fall bör imponeringsnumret motsvara det levererade numret. Detta garanterar att enheten fick meddelandet och vidarebefordrade informationen till servern.
* **[!UICONTROL Unique impressions]**: Antal visningar per mottagare.
* **[!UICONTROL Click through rate]**: Procentandel användare som interagerade med push-meddelandet.
* **[!UICONTROL Open rate]**: Procentandel öppna push-meddelanden.

![](assets/dynamic_report_push_2.png)

Den andra tabellen **Push Notification Click &amp; opens** är uppdelad i tre kategorier: per dag, per mobilapp och per leverans. Den innehåller tillgängliga data för mottagarnas beteende per leverans:

* **[!UICONTROL Impressions]**: Totalt antal push-meddelanden som visas av mottagarna.
* **[!UICONTROL Unique impressions]**: Antal visningar per mottagare.
* **[!UICONTROL Click]**: Antal gånger ett push-meddelande har levererats till enheten och användaren klickat på det. Användaren ville antingen visa meddelandet, som sedan flyttas till Push Open tracking, eller stänga det.
* **[!UICONTROL Unique clicks]**: Antal gånger en unik användare interagerar med push-meddelandet, t.ex. klickar på meddelandet eller knappen.
* **[!UICONTROL Open]**: Totalt antal push-meddelanden som levererats till enheten och användaren klickat på för att öppna appen. Det här liknar kommandot Push Click (Push-klicka), förutom att Push Open (Push Open) inte aktiveras om meddelandet stängs.
* **[!UICONTROL Unique Opens]**: Antal mottagare som öppnade leveransen.
