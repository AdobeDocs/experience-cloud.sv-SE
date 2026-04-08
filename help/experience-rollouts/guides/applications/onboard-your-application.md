---
title: Anpassa applikationen
description: Lär dig hur du lägger in ett nytt program i Adobe Experience Rollouts så att du kan börja skapa och hantera funktionsflaggor.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Anpassa applikationen {#onboard-your-application}

Du måste ha rollen **Admin** för att lägga till ett nytt program. Kontakta administratören om du behöver verifiera eller uppdatera din roll.

## Lägg till ett nytt program {#add-application}

1. Logga in på konsolen Experience Rollouts och navigera till **Experience Rollout > Applications**.

   >[!NOTE]
   >
   >Om knappen **Nytt program** inte visas kontrollerar du att du har rollen **Flyttal-admin**.

2. Välj **Nytt program**.

3. Välj den **plattform** som matchar din programtyp (webb eller mobil).

4. Ange följande information:

   | Fält | Beskrivning |
   |---|---|
   | **Program-ID** | En unik identifierare som används för att anropa Experience Rollouts från din kod. Använd programmets klient-ID. |
   | **TTL** | Avsökningsintervallet (i sekunder) för uppdatering av cache per program. Gäller endast SDK:er på serversidan. |

5. Välj **Lägg till**. Ditt program är nu registrerat och klart för konfiguration av funktionsflagga.

## Vad kommer härnäst {#next-steps}

När programmet väl har anslutit kan du börja skapa funktionsflaggor:

* [Skapa din första funktionsflagga](../feature-flags/create-your-first-feature-flag.md)
* [Integrera upplevelseutrullningar i appen](../integrate/integrating-in-your-app.md)

## Se även {#see-also}

* [Hantera program](manage-applications.md)
* [Logga in på konsolen](../console/log-in-to-the-console.md)
