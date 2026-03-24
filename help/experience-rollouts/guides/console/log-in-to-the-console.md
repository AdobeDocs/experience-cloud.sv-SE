---
title: Logga in på Experience Rollouts-konsolen
description: Lär dig hur du kommer igång med Adobe Experience Rollouts genom att hitta ditt team, begära åtkomst och logga in på konsolen.
source-git-commit: a7ff5bf33bd8e8c5ff89848955bf6af33b0d6c21
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# Logga in på Experience Rollouts-konsolen {#log-in}

Att komma igång med Experience Rollouts innebär tre steg: att hitta eller skapa ditt team, begära åtkomst och logga in på konsolen.

## Innan du börjar {#before-you-begin}

Upplevelseutrullningar är organiserade kring **team**. Varje team äger ett eller flera program och hanterar funktionsflaggor för dessa program. Innan du kan logga in måste du tillhöra ett team.

Fråga din produkt eller tekniker om det redan finns ett team för ditt projekt. Om det gör det ber du teamadministratören att lägga till dig med rätt [användarroll](../teams/user-roles.md). Om inget team finns ännu följer du stegen i [Skapa ett nytt team](create-a-new-team.md).

## Begär åtkomst {#request-access}

När du vet vilket team du ska gå med i begär du åtkomst via din organisations åtkomsthanteringssystem. Se [Begär åtkomst](request-access.md) för steg-för-steg-instruktioner.

När din begäran har godkänts får du de behörigheter som är kopplade till rollen som beviljas av din teamadministratör.

## Logga in på konsolen {#log-in-steps}

När åtkomst har beviljats:

1. Gå till [https://experience.adobe.com/](https://experience.adobe.com/) och logga in med din organisations autentiseringsuppgifter.
2. Välj **Upplevelserullningar** i programväljaren.
3. Välj lämplig miljö - **Stage** för testning, **Production** för live-rollouts. Mer information finns i [Miljööversikt](environments-overview.md).

## Första steget efter inloggning {#first-steps}

När du har loggat in kontrollerar du att programmet visas i konsolen. Applikationerna hanteras av teamadministratörer. Om ditt program inte finns med i listan kontaktar du teamadministratören för att få det tillagt. Mer information finns i [Hantera program](../applications/manage-applications.md).

## Nyckelterminologi {#terminology}

| Villkor | Definition |
|---|---|
| **Team** | En självhanterad grupp som äger program och hanterar funktionsflaggor. Team har en platt struktur med olika användarroller och behörighetsnivåer. |
| **Program** | Programmet som du vill styra med funktionsflaggor. Varje program ägs av ett team. |
| **Funktionsflagga/Funktionsgrupp/release** | Artefakter som skapats i Experience Rollouts för funktionstestning och versionshantering. |
