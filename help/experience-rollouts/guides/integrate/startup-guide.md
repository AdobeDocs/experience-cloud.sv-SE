---
title: Starthandbok
description: Följ de här stegen för att integrera ditt program med Adobe Experience Rollouts, från att begära åtkomst till att skapa din första funktionsflagga.
exl-id: 7aa09535-45fa-4ddf-9e3f-a23f8a8ee666
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Starthandbok {#startup-guide}

Följ de här stegen för att integrera Experience Rollouts i ditt program.

## Steg 1: Begär åtkomst {#step-1-access}

Begär åtkomst till Experience Rollouts-konsolen och gå med i ditt team. Se [Begär åtkomst](../console/request-access.md) för steg-för-steg-instruktioner.

## Steg 2: Anlita programmet {#step-2-onboard}

När du fått åtkomst loggar du in på Experience Rollouts-konsolen och kontrollerar att ditt program finns med i ditt team. Om så inte är fallet ber du teamadministratören att lägga till det. Se [Anlita ditt program](../applications/onboard-your-application.md).

Före introduktionen ska du förbereda följande:

| Krav | Information |
|---|---|
| **Program-ID** | En unik klientidentifierare som används vid anrop av API:er för upplevelseutrullningar. Använd ditt programs befintliga klient-ID där det är tillgängligt. |
| **Klienter på serversidan** | Om du integrerar med en SDK på serversidan behöver du ett ID för administratörsklient med rätt behörigheter. |
| **Skrivbordsklienter** | En produktkod och en produktversion kan användas i stället för ett klient-ID. |

## Steg 3: Hämta dina autentiseringsuppgifter {#step-3-credentials}

Om du integrerar via en SDK på serversidan behöver du ett klient-ID för tjänsttoken. Kontakta Experience Rollouts-support om du vill få ditt klient-ID tillåtslista innan du kan göra API-anrop från SDK.

## Steg 4: Integrera med en SDK {#step-4-integrate}

Följ [integreringsstegen](integration-steps.md) för din programtyp. Välj den sökväg som passar din hög:

* **Webbtjänster** → Java SDK eller Node.js SDK
* **Webb och mobilappar** → Web SDK eller mobil SDK (kommer snart)
* **Datorprogram** → SDK (kommer snart)

## Steg 5: Skapa och testa flaggan för den första funktionen {#step-5-feature-flag}

När integreringen är klar skapar du din första funktionsflagga i konsolen och testar den:

* [Skapa din första funktionsflagga](../feature-flags/create-your-first-feature-flag.md)

## Se även {#see-also}

* [Integrera upplevelseutrullningar i appen](integrating-in-your-app.md)
* [Integreringssteg](integration-steps.md)
* [SDK](sdks.md)
