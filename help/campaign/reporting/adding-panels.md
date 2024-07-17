---
title: Lägga till paneler
description: Med en dynamisk rapport kan du lägga till en panel för att bättre filtrera data beroende på den valda tidsperioden.
audience: end-user
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
level: Intermediate
exl-id: c87f6155-821d-422d-86e5-4f5533d62fda
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---

# Lägga till paneler{#adding-panels}

## Lägga till en tom panel {#adding-a-blank-panel}

Du kan påbörja rapporten genom att lägga till en uppsättning paneler i en separat eller anpassad rapport. Varje panel innehåller olika datauppsättningar och består av frihandstabeller och visualiseringar.

Med den här panelen kan du skapa rapporter efter behov. Du kan lägga till så många paneler du vill i dina rapporter för att filtrera data med olika tidsperioder.

1. Klicka på ikonen **Paneler** . Du kan också lägga till en panel genom att klicka på fliken **Infoga** och välja **Ny tom panel**.

   ![](assets/dynamic_report_panel_1.png)

1. Dra och släpp den **tomma panelen** på instrumentpanelen.

   ![](assets/dynamic_report_panel.png)

Nu kan du lägga till en friformstabell på panelen för att börja målinrikta data.

## Lägga till en frihandstabell {#adding-a-freeform-table}

Med frihandstabeller kan du skapa en tabell för att analysera data med hjälp av de olika mätvärden och dimensioner som finns i tabellen **Komponent** .

Det går att ändra storlek på alla tabeller och visualiseringar och de kan flyttas för att bättre anpassa rapporten.

1. Klicka på ikonen **[!UICONTROL Panels]**.

   ![](assets/dynamic_report_panel_1.png)

1. Dra och släpp **[!UICONTROL Freeform]**-objektet på instrumentpanelen.

   Du kan också lägga till en tabell genom att klicka på fliken **[!UICONTROL Insert]** och välja **[!UICONTROL New Freeform]** eller genom att klicka på **[!UICONTROL Add a freeform table]** i en tom panel.

   ![](assets/dynamic_report_panel_2.png)

1. Lägg till en **[!UICONTROL Segment]** från fliken **[!UICONTROL Components]** i det övre fältet i fältet **[!UICONTROL Drop a segment here]**.

   ![](assets/dynamic_report_panel_3.png)

1. Dra och släpp objekt från fliken **[!UICONTROL Components]** till kolumnerna och raderna för att skapa tabellen.

   ![](assets/dynamic_report_freeform_3.png)

1. Klicka på ikonen **[!UICONTROL Settings]** om du vill ändra hur data visas i kolumnerna.

   ![](assets/dynamic_report_freeform_4.png)

   **[!UICONTROL Column settings]** består av:

   * **[!UICONTROL Number]**: gör att du kan visa eller dölja sammanfattningsnummer i kolumnen.
   * **[!UICONTROL Percent]**: gör att du kan visa eller dölja procent i kolumnen.
   * **[!UICONTROL Interpret zero as no value]**: gör att du kan visa eller dölja när värdet är lika med noll.
   * **[!UICONTROL Background]**: gör att du kan visa eller dölja den vågräta förloppsindikatorn i celler.
   * **[!UICONTROL Include retries]**: gör att du kan inkludera återförsök i resultatet. Detta är bara tillgängligt för **[!UICONTROL Sent]** och **[!UICONTROL Bounces + Errors]**.

1. Markera en eller flera rader och klicka på ikonen **[!UICONTROL Visualize]**. En visualisering läggs till för att återspegla de rader du har valt.

   ![](assets/dynamic_report_freeform_5.png)

Nu kan du lägga till så många komponenter du behöver och även lägga till visualiseringar för att ge grafiska representationer av dina data.
