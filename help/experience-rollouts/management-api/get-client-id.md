---
title: Hämta klient-ID för ett program
description: Lär dig hur du hittar det numeriska klient-ID:t för ett program i Experience Rollouts-konsolen, som krävs när du anropar hanterings-API:erna.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Hämta klient-ID för ett program {#get-client-id}

Funktionsflaggorna och API:erna för funktionsgrupphantering kräver en numerisk `clientId` för att identifiera vilket program funktionen tillhör. Detta skiljer sig från det strängbaserade IMS-klient-ID som används för API-autentisering.

Följ de här stegen för att hitta det numeriska klient-ID:t för ett program.

## Steg {#steps}

Så här hittar du det numeriska klient-ID:t för ett program:

1. Logga in på Experience Rollouts-konsolen.
2. Navigera till **Funktioner och releaser**.
3. Välj fliken **Funktionsflaggor**.
4. Öppna listrutan **Program** och välj det program vars klient-ID du behöver.
5. Titta på webbadressen i webbläsarens adressfält. Efter `feature-flags/` visas det numeriska klient-ID:t för det programmet.

Om URL:en till exempel slutar med `.../feature-flags/1191/...` är klient-ID:t `1191`.

## Använd klient-ID i API-anrop {#use-in-api}

Skicka det här värdet som `clientId`-parameter i hanterings-API-begäranden. När du till exempel skapar en funktionsflagga:

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## Se även {#see-also}

* [Hanterings-API för funktionsflaggor](feature-flags-management-api.md)
* [API för hantering av funktionsgrupper](feature-group-management-api.md)
* [Hämta önskade målgruppskriterier](get-audience-criteria.md)
