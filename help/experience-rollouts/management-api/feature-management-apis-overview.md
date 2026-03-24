---
title: Översikt över API:er för funktionshantering
description: Översikt över API:er för Experience Rollouts som gör att du kan skapa, läsa, uppdatera och ta bort funktionsflaggor, funktionsgrupper och releaser programmatiskt.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Översikt över API:er för funktionshantering {#feature-management-apis-overview}

Med API:erna för Experience Rollouts kan ni hantera funktionsflaggor, funktionsgrupper och releaser programmatiskt. Team som behöver automatisera arbetsflöden eller integrera Experience Rollouts i befintliga distributionssystem kan använda dessa API:er i stället för konsolen.

>[!NOTE]
>
>Åtkomst till hanterings-API:erna med en tjänsttoken beviljas på begäran. Kontakta supporten för upplevelseutrullningar och ange en affärsjustering för att begära åtkomst.

## Tillgängliga hanterings-API:er {#available-apis}

Följande hanterings-API:er är tillgängliga:

* [Hanterings-API:t för funktionsflaggor](feature-flags-management-api.md) - Skapa, läsa, uppdatera och ta bort funktionsflaggor för ett program.
* [API för hantering av funktionsgrupper](feature-group-management-api.md) - Skapa, läsa, uppdatera, ta bort och kontrollera automatiserade utrullningsplaner för funktionsgrupper.
* [API:er för versionshantering](release-management-apis.md) - Skapa och redigera funktionsgrupper och releaser för olika team.

## Gemensamma krav {#common-requirements}

Alla hanterings-API-anrop kräver följande:

* En **API-nyckel** från Adobe Developer Console - se [Prenumerera på API-programmet](../guides/integrate/subscribe-to-api-application.md).
* En **IMS-användaråtkomsttoken** eller **tjänsttoken**, skickas som `Bearer <token>` i huvudet `Authorization`.
* Ett `Content-Type: application/json`-huvud.

API-nycklar och tokens måste etableras separat för scen- och produktionsmiljöer.

## Hjälpguider {#helper-guides}

Följande guider hjälper dig att skapa korrekta API-nyttolaster:

* [Hämta klient-ID för ett program](get-client-id.md) - Leta upp det numeriska klient-ID som krävs av funktionsflaggorna och API:erna för funktionsgrupphantering.
* [Hämta önskade målgruppskriterier](get-audience-criteria.md) - Använd konsolen och GET API för att generera rätt JSON-struktur för målgruppskriterier.
* [API för hanteringskorrigering](management-patch-api.md) - Uppdatera enskilda fält för en funktionsflagga, funktionsgrupp eller funktionsgrupp mellan team utan att skicka hela objektet.

## Se även {#see-also}

* [GET Feature API V3](../feature-api/get-feature-api-v3.md)
* [GET Feature API V2](../feature-api/get-feature-api-v2.md)
* [Prenumerera på API-programmet](../guides/integrate/subscribe-to-api-application.md)
