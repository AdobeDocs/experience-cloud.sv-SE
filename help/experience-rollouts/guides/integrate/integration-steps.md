---
title: Integreringssteg
description: Följ integreringsstegen för din programtyp för att ansluta Adobe Experience Rollouts till din webbtjänst, webbapp, mobilapp eller datorprogram.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Integreringssteg {#integration-steps}

Välj den integrationssökväg som matchar programtypen.

## Webbtjänster {#web-services}

Backend-tjänster kan integreras med hjälp av en SDK på serversidan. Välj SDK för din teknikstack.

**Java**

Följ [Java SDK-integreringsguiden](../sdk-releases/java/java-sdk-integration-guide.md) för konfiguration, beroendekonfiguration och initiering.

**Node.js**

Följ integreringsguiden för [Node.js SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) för installation och initiering.

**Andra språk**

Om din hög inte finns med i listan ovan kan du integrera direkt med **funktions-API:t V3** (se avsnittet Funktions-API i den här handboken). Kontakta supporten för upplevelseutrullningar om du behöver hjälp.

## Webb- och mobilapplikationer {#web-mobile}

Webb- och mobilprogram anropar **funktions-API V3** för att hämta funktionsflaggor för den aktuella användaren och tillämpa villkorsstyrd logik i programmet.

Se **GET Feature API V3** i API:t för funktioner i den här handboken för fullständig API-referens.

## Datorprogram {#desktop}

Skrivbordsprogram anropar **funktions-API V2** för att hämta funktionsflaggor.

Se **GET Feature API V2** i API:t för funktioner i den här handboken för fullständig API-referens.

>[!IMPORTANT]
>
>Skrivbordsklienter måste respektera TTL-värdet i API-svaret och implementera en smidig felhantering för att API inte ska vara tillgängligt. Mer information om krav finns i [Datorprogram](desktop-applications.md).

## Se även {#see-also}

* [Starthandbok](startup-guide.md)
* [SDK](sdks.md)
* [Webbtjänster](web-services.md)
* [Datorprogram](desktop-applications.md)
