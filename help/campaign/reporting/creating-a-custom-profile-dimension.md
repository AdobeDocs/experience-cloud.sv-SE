---
title: Skapa en profildimension
description: Lär dig hur du skapar en profildimension baserat på profildata.
audience: reporting
content-type: reference
level: Intermediate
exl-id: a12dc772-13c7-45ff-9fbf-3dfdd3801eae
source-git-commit: 5da9b29c424f019f3dafc127a41e974017af494c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Skapa en profildimension{#creating-a-custom-profile-dimension}

Rapporter kan också skapas och hanteras baserat på profildata som skapats under mottagarschematillägget.

* [Steg 1: Utöka mottagarschemat](##extend-schema)
* [Steg 2: Länka ditt nya anpassade fält](#link-custom)
* [Steg 3: Skapa en dynamisk rapport för att filtrera mottagare med profildimensionen](#create-report)

## Steg 1: Utöka mottagarschemat {#extend-schema}

Om du vill lägga till ett nytt profilfält måste du utöka ditt schema enligt följande:

1. Navigera till mappen **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** i Utforskaren.

   ![](assets/custom_field_1.png)

1. Identifiera ditt anpassade mottagarschema och markera det. Om du ännu inte har utökat det inbyggda nms:mottagarschemat kan du läsa [den här proceduren](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Lägg till ditt anpassade fält i schemaredigeraren.

   Så här lägger du till ett anpassat fält för lojalitet i mottagarschemat:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Klicka på **[!UICONTROL Save]**.

1. Identifiera sedan ditt anpassade brunLogRcp-schema och markera det. Om du ännu inte har utökat det inbyggda leveransloggschemat kan du läsa [den här proceduren](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Lägg till samma anpassade fält som mottagarschemat i schemaredigeraren.

   ![](assets/custom_field_3.png)

1. Klicka på **[!UICONTROL Save]**.

1. Om du vill använda ändringarna i scheman startar du guiden Databasuppdatering via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure]** och kör uppdateringsdatabasstrukturen. [Läs mer](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Det nya profilfältet är nu klart att användas och markeras av dina mottagare.

## Steg 2: Länka ditt nya anpassade fält {#link-custom}

>[!NOTE]
>
> Du kan bara lägga till upp till 20 anpassade fält i den dynamiska rapporten.

Nu när ditt profilfält har skapats måste vi länka det till motsvarande dynamiska rapporteringsdimension.

Innan du utökar loggen med vårt profilfält måste du kontrollera att PII-fönstret accepterades för att kunna skicka PII-data till en dynamisk rapport. Se denna [sida](pii-agreement.md) för mer information om detta.

1. Navigera till mappen **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** > **[!UICONTROL Additional reporting field]** i Utforskaren.

   ![](assets/custom_field_5.png)

1. Klicka på **[!UICONTROL New]** om du vill skapa en motsvarande dimension för dynamisk rapportering.

1. Välj **[!UICONTROL Edit expression]** och bläddra igenom mottagarschemat för att hitta det profilfält som du skapade tidigare.

   ![](assets/custom_field_6.png)

1. Klicka på **[!UICONTROL Finish]**.

1. Skriv in dimensionen **[!UICONTROL Label]**, synlig i dynamisk rapportering, och klicka på **[!UICONTROL Save]**.

   ![](assets/custom_field_7.png)

Ditt profilfält är nu tillgängligt som profildimension i dina rapporter. Om du vill ta bort din profildimension kan du markera den och klicka på ikonen **[!UICONTROL Delete]**.

Nu när mottagarschemat har utökats med det här profilfältet och din anpassade dimension har skapats kan du börja målinrikta mottagare i leveranser.

## Steg 3: Skapa en dynamisk rapport för att filtrera mottagare med profildimensionen {#create-report}

När leveransen är klar kan du dela upp rapporter med hjälp av din profildimension.

1. På fliken **[!UICONTROL Reports]** väljer du en färdig rapport eller klickar på knappen **[!UICONTROL Create]** för att starta en från början.

   ![](assets/custom_field_8.png)

1. Klicka på **[!UICONTROL Profile]** i kategorin **[!UICONTROL Dimensions]** och dra och släpp profildimensionen i frihandstabellen.

   ![](assets/custom_field_9.png)

1. Dra och släpp mätvärden för att börja filtrera data.

1. Dra och släpp en visualisering på arbetsytan om det behövs.

