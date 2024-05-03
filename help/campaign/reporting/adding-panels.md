---
title: Lägga till paneler
description: Med en dynamisk rapport kan du lägga till en panel för att bättre filtrera data beroende på den valda tidsperioden.
audience: end-user
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
level: Intermediate
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---

# Lägga till paneler{#adding-panels}

## Lägga till en tom panel {#adding-a-blank-panel}

Du kan påbörja rapporten genom att lägga till en uppsättning paneler i en separat eller anpassad rapport. Varje panel innehåller olika datauppsättningar och består av frihandstabeller och visualiseringar.

Med den här panelen kan du skapa rapporter efter behov. Du kan lägga till så många paneler du vill i dina rapporter för att filtrera data med olika tidsperioder.

1. Klicka på **Panel** -ikon. Du kan också lägga till en panel genom att klicka på **Infoga-flik** och markera **Ny tom panel**.

   ![](assets/dynamic_report_panel_1.png)

1. Dra och släpp **Tom panel** till din instrumentpanel.

   ![](assets/dynamic_report_panel.png)

Nu kan du lägga till en friformstabell på panelen för att börja målinrikta data.

## Lägga till en frihandstabell {#adding-a-freeform-table}

Med frihandstabeller kan du skapa en tabell för att analysera data med hjälp av de olika mätvärden och dimensioner som finns i **Komponent** tabell.

Det går att ändra storlek på alla tabeller och visualiseringar och de kan flyttas för att bättre anpassa rapporten.

1. Klicka på **[!UICONTROL Panels]** -ikon.

   ![](assets/dynamic_report_panel_1.png)

1. Dra och släpp **[!UICONTROL Freeform]** objekt på kontrollpanelen.

   Du kan också lägga till en tabell genom att klicka på **[!UICONTROL Insert]** flik och markera **[!UICONTROL New Freeform]** eller genom att klicka **[!UICONTROL Add a freeform table]** i en tom panel.

   ![](assets/dynamic_report_panel_2.png)

1. I **[!UICONTROL Drop a segment here]** fält, lägga till **[!UICONTROL Segment]** från **[!UICONTROL Components]** i det övre fältet.

   ![](assets/dynamic_report_panel_3.png)

1. Dra och släpp objekt från **[!UICONTROL Components]** i kolumnerna och raderna för att skapa tabellen.

   ![](assets/dynamic_report_freeform_3.png)

1. Klicka på **[!UICONTROL Settings]** om du vill ändra hur data visas i kolumnerna.

   ![](assets/dynamic_report_freeform_4.png)

   The **[!UICONTROL Column settings]** består av

   * **[!UICONTROL Number]**: gör att du kan visa eller dölja sammanfattningsnummer i kolumnen.
   * **[!UICONTROL Percent]**: gör att du kan visa eller dölja procent i kolumnen.
   * **[!UICONTROL Interpret zero as no value]**: låter dig visa eller dölja när värdet är lika med noll.
   * **[!UICONTROL Background]**: gör att du kan visa eller dölja den vågräta förloppsindikatorn i celler.
   * **[!UICONTROL Include retries]**: gör att du kan ta med återförsök i resultatet. Detta är endast tillgängligt för **[!UICONTROL Sent]** och **[!UICONTROL Bounces + Errors]**.

1. Markera en eller flera rader och klicka på **[!UICONTROL Visualize]** -ikon. En visualisering läggs till för att återspegla de rader du har valt.

   ![](assets/dynamic_report_freeform_5.png)

Nu kan du lägga till så många komponenter du behöver och även lägga till visualiseringar för att ge grafiska representationer av dina data.
