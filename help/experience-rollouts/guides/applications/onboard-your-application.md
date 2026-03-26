---
title: Anpassa applikationen
description: Lär dig hur du kan integrera ett nytt program i Adobe Experience Rollouts så att teamet kan börja skapa och hantera funktionsflaggor.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Anpassa applikationen {#onboard-your-application}

Du måste ha rollen **Admin** för att lägga till ett nytt program. Kontakta teamadministratören om du behöver verifiera eller uppdatera din roll.

## Lägg till ett nytt program {#add-application}

1. Logga in på konsolen Experience Rollouts och gå till **Admin > Program**.

   >[!NOTE]
   >
   >Om knappen **Nytt program** inte visas kontrollerar du att du är i rätt team och att du har rollen **Admin**.

2. Välj **Nytt program**.

3. Välj den **kanal** som matchar din programtyp (webb, mobil, dator eller tjänst).

4. Ange följande information:

   | Fält | Beskrivning |
   |---|---|
   | **Program-ID** | En unik identifierare som används för att anropa Experience Rollouts från din kod. Använd programmets klient-ID. |
   | **TTL** | Avsökningsintervallet (i sekunder) för uppdatering av cache per program. Gäller endast SDK:er på serversidan. |
   | **Team** | Teamet som ska äga och hantera det här programmet. Endast medlemmar i det här teamet kan skapa och redigera funktionsflaggor för det. |

5. Välj **Lägg till**. Ditt program är nu registrerat och klart för konfiguration av funktionsflagga.

## Vad kommer härnäst {#next-steps}

När ditt program väl har anslutit kan ditt team börja skapa funktionsflaggor:

* [Skapa din första funktionsflagga](../feature-flags/create-your-first-feature-flag.md)
* [Integrera upplevelseutrullningar i appen](../integrate/integrating-in-your-app.md)

## Se även {#see-also}

* [Hantera program](manage-applications.md)
* [Logga in på konsolen](../console/log-in-to-the-console.md)
