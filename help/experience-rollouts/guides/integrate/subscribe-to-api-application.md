---
title: Prenumerera på API-programmet i Adobe Developer Console
description: Lär dig hur du prenumererar ditt program på Experience Rollouts API via Adobe Developer Console så att du kan anropa funktionsflaggans slutpunkter.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Prenumerera på API-programmet i Adobe Developer Console {#subscribe-to-api}

Om du vill anropa API:t för Experience Rollouts från ditt program måste du prenumerera på det via [Adobe Developer Console](https://developer.adobe.com/console). Detta ger programmet ett klient-ID som Experience Rollouts använder för att identifiera anroparen.

## Förutsättningar {#prerequisites}

Innan du prenumererar bekräftar du följande:

* Ditt program introduceras i Experience Rollouts-konsolen - se [Bädda in ditt program](../applications/onboard-your-application.md)
* Du har tillgång till Adobe Developer Console för din organisation

## Prenumerera på API:t för upplevelseutrullningar {#subscribe}

Följ de här stegen för att prenumerera ditt program på API:t för Experience Rollouts:

1. Gå till [Adobe Developer Console](https://developer.adobe.com/console) och logga in med din organisations autentiseringsuppgifter.
2. Välj ett projekt eller skapa ett nytt.
3. Välj **Lägg till API**.
4. Sök efter och välj **API för upplevelseutrullningar**.
5. Följ anvisningarna för att konfigurera API:t och generera autentiseringsuppgifter.
6. Observera det **klient-ID** som genererats för ditt projekt. Det här är den identifierare som du använder när du anropar Experience Rollouts API och när du introducerar programmet i Experience Rollouts-konsolen.

## SDK-integreringar på serversidan {#server-sdk}

Om du integrerar med Java SDK eller Node.js SDK behöver du både ett **service token**-klient-ID och en API-nyckel. Tjänsttoken gör att SDK kan anropa API:er för Experience Rollouts i bakgrunden.

>[!NOTE]
>
>Klient-ID:n för SDK på serversidan måste tillåtslista av Experience Rollouts-stöd innan de kan göra API-anrop. Kontakta supporten när du har slutfört Developer Console-installationen.

## Se även {#see-also}

* [Starthandbok](startup-guide.md)
* [SDK](sdks.md)
* [Anpassa applikationen](../applications/onboard-your-application.md)
* [Integreringssteg](integration-steps.md)
