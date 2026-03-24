---
title: Integrera upplevelseutrullningar i appen
description: Lär dig hur du integrerar Adobe Experience Rollouts i ditt program, oavsett om det är en webbtjänst, en webbegenskap, en mobilapp eller ett datorprogram.
source-git-commit: 5dfb2fad7d04fc7f681337195de9c26e8aa26a09
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Integrera upplevelseutrullningar i appen {#integrate}

Det här avsnittet innehåller riktlinjer för integrering för alla Experience Rollouts-klienter, ordnade efter programtyp.

## Välj integreringsväg {#choose}

Välj den guide som matchar din programtyp:

1. [Starthandbok](startup-guide.md) - Börja här om du vill få en översikt över alla integrationssteg
2. [Datorprogram](desktop-applications.md) - API-integrering med Direct REST för datorprogram
3. [Mobilprogram](mobile-applications.md) - REST API-integrering för mobilappar
4. [Webbprogram](web-applications.md) - REST API-integrering för webbegenskaper
5. [Webbtjänster](web-services.md) - SDK-integration på serversidan för backend-tjänster
6. [SDK:er](sdks.md) - SDK-arkitektur, krav och tillgängliga SDK:er
7. [Integreringssteg](integration-steps.md) - Detaljerade steg-för-steg-integreringsinstruktioner

## Programtyper i korthet {#overview}

| Programtyp | Rekommenderad integrering |
|---|---|
| **Webbtjänst/serverdel** | Java SDK eller Node.js SDK |
| **Webbprogram** | REST API - funktions-API V3 |
| **Mobilprogram** | REST API - funktions-API V3 |
| **Datorprogram** | REST API - funktions-API V2 |
