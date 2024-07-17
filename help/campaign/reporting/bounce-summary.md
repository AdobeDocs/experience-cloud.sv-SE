---
title: Studssammanfattning
description: Med en färdig rapport om studssammanfattning får du reda på status för skickade kampanjer och vilka fel de har råkat ut för.
audience: end-user
level: Intermediate
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 1%

---

# Studssammanfattning{#bounce-summary}

Den här rapporten innehåller information om de övergripande hårdfel och mjuka fel som uppstått under leveranser samt den automatiska bearbetningen av studenterna.

![](assets/campaign_reports_bounces.png)

Varje tabell representeras av sammanfattande nummer och diagram. Du kan ändra hur detaljerna visas i deras respektive visualiseringsinställningar.

**Flöde 5-ompartitionen** visar fem leveranser med det högsta antalet karantän:

Tabellen **Studsorsaker** innehåller tillgängliga data för de typer av fel som orsakade studsar för varje leverans:

* **[!UICONTROL User unknown]**: Den typ av fel som genereras när en leverans skickas till en ogiltig e-postadress.
* **[!UICONTROL Invalid domain]**: Den typ av fel som genereras när en leverans skickas till en e-postadress vars domän är fel eller inte längre finns.
* **[!UICONTROL Unreachable]**: Den typ av fel som påträffades i meddelandeleveranssträngen, t.ex. domänen som inte går att nå för tillfället.
* **[!UICONTROL Account disabled]**: Den typ av fel som genereras när en leverans skickas till en e-postadress som inte längre finns.
* **[!UICONTROL Mailbox full]**: Den typ av fel som genereras när mottagarens inkorg är full. Det görs fem försök att leverera meddelandet innan det här felet genereras.
* **[!UICONTROL Not connected]**: Den typ av fel som genereras när mottagarens mobiltelefon är avstängd eller inte är ansluten till ett nätverk när meddelandet skickas.

  >[!NOTE]
  >
  >Den här typen av fel gäller endast leveranser i mobilkanaler.

* **[!UICONTROL Refused]**: Den typ av fel som genereras när en adress nekas av Internet-leverantören. Exempel: när en säkerhetsregel har tillämpats av antispam-program.

Tabellen **Domänompartition** visar de övergripande problem som uppstått under leveranser enligt mottagardomänen.
