---
title: Skapa en anpassad profildimension
description: Lär dig hur du skapar en anpassad profildimension baserad på anpassade profildata.
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 3%

---

# Skapa en anpassad profildimension{#creating-a-custom-profile-dimension}

Rapporter kan också skapas och hanteras baserat på anpassade profildata som har skapats under mottagarschematillägget.

* [Steg 1: Utöka mottagarschemat](##extend-schema)
* [Steg 2: Länka ditt nya anpassade fält](#link-custom)
* [Steg 3: Skapa en dynamisk rapport för att filtrera mottagare med den anpassade profildimensionen](#create-report)

## Steg 1: Utöka mottagarschemat {#extend-schema}

Om du vill lägga till ett nytt profilfält måste du utöka ditt schema enligt följande:

1. Navigera till **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** i Utforskaren.

   ![](assets/custom_field_1.png)

1. Identifiera ditt anpassade mottagarschema och markera det. Om du ännu inte har utökat det inbyggda nms:mottagarschemat, se [detta förfarande](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Lägg till ditt anpassade fält i schemaredigeraren.

   Så här lägger du till ett anpassat fält för lojalitet i mottagarschemat:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Klicka på **[!UICONTROL Save]**.

1. Identifiera sedan ditt anpassade brunLogRcp-schema och markera det. Om du ännu inte har utökat det inbyggda leveransloggschemat finns mer information i [detta förfarande](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Lägg till samma anpassade fält som mottagarschemat i schemaredigeraren.

   ![](assets/custom_field_3.png)

1. Klicka på **[!UICONTROL Save]**.

1. Om du vill använda ändringarna i scheman startar du guiden Databasuppdatering via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure]** och kör Uppdatera databasstrukturen. [Läs mer](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Det nya profilfältet är nu klart att användas och markeras av dina mottagare.

## Steg 2: Länka ditt nya anpassade fält {#link-custom}

>[!NOTE]
>
> Du kan bara lägga till upp till 20 anpassade fält i den dynamiska rapporten.

Nu när ditt profilfält har skapats måste vi länka det till motsvarande dynamiska rapporteringsdimension.

1. Navigera till **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** > **[!UICONTROL Additional reporting field]** i Utforskaren.

   ![](assets/custom_field_5.png)

1. Klicka **[!UICONTROL New]** för att skapa en motsvarande dynamisk rapporteringsdimension.

1. Välj **[!UICONTROL Edit expression]** och bläddra igenom mottagarschemat för att hitta det anpassade profilfältet som du skapade tidigare.

   ![](assets/custom_field_6.png)

1. Klicka på **[!UICONTROL Finish]**.

1. Skriv in din dimension **[!UICONTROL Label]**, visas i Dynamic Reporting och klicka på **[!UICONTROL Save]**.

   ![](assets/custom_field_7.png)

Ditt anpassade profilfält är nu tillgängligt som en anpassad profildimension i dina rapporter. Om du vill ta bort din anpassade profildimension kan du markera den och klicka på **[!UICONTROL Delete]** -ikon.

Nu när mottagarschemat har utökats med det här profilfältet och din anpassade dimension har skapats kan du börja målinrikta mottagare i leveranser.

## Steg 3: Skapa en dynamisk rapport för att filtrera mottagare med den anpassade profildimensionen {#create-report}

När leveransen är klar kan du dela upp rapporter med hjälp av din anpassade profildimension.

1. Från **[!UICONTROL Reports]** väljer du en färdig rapport eller klickar på **[!UICONTROL Create]** för att starta en från början.

   ![](assets/custom_field_8.png)

1. I **[!UICONTROL Dimensions]** kategori, klicka på **[!UICONTROL Profile]** dra och släpp sedan den anpassade profildimensionen i frihandstabellen.

   ![](assets/custom_field_9.png)

1. Dra och släpp mätvärden för att börja filtrera data.

1. Dra och släpp en visualisering på arbetsytan om det behövs.
