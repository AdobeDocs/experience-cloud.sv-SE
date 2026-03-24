---
title: Användarroller
description: Lär dig mer om de fem användarrollerna i Adobe Experience Rollouts och hur du väljer rätt roll för varje teammedlem.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Användarroller {#user-roles}

Experience Rollouts har fem roller. Varje roll är utformad för en särskild uppsättning ansvarsområden. Roller utesluter varandra som standard - en medlem med rollen Admin har inte automatiskt behörigheten Produktfrigivningsägare. Tilldela flera roller till en medlem när mer omfattande åtkomst behövs.

## Tillgängliga roller {#roles}

| Roll | Ansvarsområden |
|---|---|
| **Admin** | Lägger in program i konsolen, hanterar teammedlemmar och godkänner eller avvisar åtkomstbegäranden. Krävs innan teamet kan börja använda funktionsflaggor. |
| **Ägare till produktreleaser** | Skapar och uppdaterar funktionsflaggor och funktionsgrupper för respektive program. Kan länka målgrupper till funktionsflaggor för att göra funktioner tillgängliga för externa användare. |
| **Utvecklare** | Fungerar i sandlådesammanhang för att testa funktioner bakom funktionsflaggor utan att påverka andra användare. Kan visa en funktionsflagga för en privat målgrupp (till exempel ett visst användar-ID eller en viss e-postadress) i Stage eller Production. |
| **Funktionsadministratör** | Skapar och hanterar funktionsgrupper mellan team. Använd den här rollen när du koordinerar flaggor mellan program som ägs av olika team. |
| **Versionshanteraren** | Hanterar versioner för flera team och program och uppdaterar målgruppsreglerna som definierar vem som får en release. |

## Välja rätt roll {#choosing}

Använd följande vägledning för att tilldela roller:

* **Lägga till eller uppdatera funktionsflaggor för ditt program** → **Ägare till produktreleaser**
* **Testar funktioner privat utan att påverka andra** → **Utvecklare**
* **Hantera funktionsgrupper mellan team** → **Funktionsadministratör**
* **Hantera releaser för flera team och program** → **Versionshanteraren**
* **Inledande program och hantering av teammedlemskap** → **Admin**

>[!NOTE]
>
>En medlem kan ha mer än en roll. En tekniker som både testar funktioner och hanterar teamets program bör till exempel ha både rollerna **Utvecklare** och **Administratör**.

## Behörighetsfel {#permissions-error}

Om en medlem stöter på ett fel av typen &quot;inte tillräcklig behörighet&quot; när han/hon försöker uppdatera en funktion eller grupp, måste han/hon ha rollen **produktversionsägare**. Kontakta teamadministratören om du vill lägga till den här rollen.

## Se även {#see-also}

* [Lägg till medlemmar i ditt team](add-team-members.md)
* [Hantera team](manage-teams.md)
