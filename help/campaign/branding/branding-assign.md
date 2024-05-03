---
title: Varumärke
description: Upptäck hur ni tilldelar ert varumärke
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 19%

---

# Tilldela ert varumärke {#branding-assign}

>[!IMPORTANT]
>
>Varumärkesalternativen är för närvarande begränsade till e-post och push-leveranser.

## Länka ett varumärke till en mall {#linking-a-brand-to-a-template}

Om du vill använda de parametrar som definierats för ett varumärke måste det vara länkat till en leveransmall. Om du vill göra det måste du skapa eller redigera en mall.

Din mall kommer att länkas till varumärket. I e-postredigeraren kommer element som **e-postadressen till standardavsändaren**, **standardavsändarens namn** eller **logotypen** att använda konfigurerade varumärkesdata.

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Om du vill skapa en leveransmall kan du duplicera en inbyggd mall, konvertera en befintlig leverans till en mall eller skapa en leveransmall från början. [Läs mer](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates)

När mallen har skapats kan du koppla den till ett varumärke. Så här gör du:

1. Bläddra till **[!UICONTROL Resources]** `>` **[!UICONTROL Templates]** `>` **[!UICONTROL Delivery templates]** i Adobe Campaign Explorer.

1. Välj en leveransmall eller duplicera en befintlig.

   ![](assets/branding_assign_V8_1.png)

1. Öppna **[!UICONTROL Properties]** av den leveransmall du valt.

   ![](assets/branding_assign_V8_2.png)

1. Från **[!UICONTROL General]** väljer du ditt varumärke på **[!UICONTROL Branding]** nedrullningsbar meny.

   ![](assets/branding_assign_V8_3.png)

1. När konfigurationen är klar väljer du **OK**.

Nu kan du använda den här mallen för att skicka leveranser.

>[!TAB Adobe Campaign Web]

Om du vill skapa en leveransmall kan du duplicera en inbyggd mall, konvertera en befintlig leverans till en mall eller skapa en leveransmall från början. [Läs mer](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/delivery-template)

När mallen har skapats kan du koppla den till ett varumärke. Så här gör du:

1. Gå till **[!UICONTROL Templates]** -fliken, från **[!UICONTROL Deliveries]** vänster meny och välj en leveransmall.

   ![](assets/branding_assign_web_1.png)

1. Klicka på **[!UICONTROL Settings]**.

   ![](assets/branding_assign_web_2.png)

1. Från **[!UICONTROL Delivery]** -fliken, gå till **[!UICONTROL Branding]** och välj det varumärke som du vill länka till mallen.

   ![](assets/branding_assign_web_3.png)

1. Bekräfta valet och spara mallen.

Nu kan du använda den här mallen för att skicka leveranser.

>[!ENDTABS]

## Tilldela ett varumärke till din leverans {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Följ stegen nedan för att skapa en ny fristående leverans.

1. Om du vill skapa en ny leverans går du till **[!UICONTROL Campaigns]** -fliken.

1. Klicka **[!UICONTROL Deliveries]** och klicka på **[!UICONTROL Create]** ovanför listan över befintliga leveranser.

   ![](assets/branding_assign_V8_4.png)

1. Välj en leveransmall.

1. Öppna **[!UICONTROL Properties]** av den leveransmall du valt.

   ![](assets/branding_assign_V8_5.png)

1. Från **[!UICONTROL General]** väljer du ditt varumärke på **[!UICONTROL Branding]** nedrullningsbar meny.

   ![](assets/branding_assign_V8_6.png)

1. När konfigurationen är klar väljer du **OK**.

1. Anpassa leveranserna ytterligare. Mer information om hur du skapar e-postmeddelanden finns i [Designa och skicka e-post](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) -avsnitt.

>[!TAB Adobe Campaign Web]

Följ stegen nedan för att skapa en ny fristående leverans.

1. Gå till **[!UICONTROL Deliveries]** till vänster och klicka på **[!UICONTROL Create delivery]** -knappen.

   ![](assets/branding_assign_web_4.png)

1. Välj E-post eller Push-meddelande som kanal och välj en leveransmall i listan.

1. Bekräfta genom att klicka på knappen **[!UICONTROL Create delivery]**.

1. Från **[!UICONTROL Properties]** sida, klicka **[!UICONTROL Settings]**.

   ![](assets/branding_assign_web_5.png)

1. Från **[!UICONTROL Delivery]** -fliken, gå till **[!UICONTROL Branding]** fält.

   ![](assets/branding_assign_web_6.png)

1. Markera det varumärke som du vill länka till mallen.

   ![](assets/branding_assign_web_7.png)

1. Anpassa leveranserna ytterligare. Mer information om hur du skapar e-postmeddelanden finns i [Skapa din första e-postadress](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email) -avsnitt.

>[!ENDTABS]
