---
title: Skapa en funktionsgrupp för flera team
description: Lär dig hur du skapar en funktionsgrupp för flera team i Adobe Experience Rollouts för att samordna funktionsflaggor för program som ägs av olika team.
source-git-commit: a1ed4582217001ffcf500cd7b634d9959adbe028
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# Skapa en funktionsgrupp för flera team {#create-cross-team-feature-group}

## Förutsättningar {#prerequisites}

Innan du skapar en funktionsgrupp för flera team bör du bekräfta följande:

* Du har åtkomst till konsolen - se [Logga in på konsolen](../console/log-in-to-the-console.md)
* Du ingår i ett team och programmet ingår
* Du har rollen **Funktionsadministratör** - se [Användarroller](../teams/user-roles.md)
* Du har skapat de funktionsflaggor som ska inkluderas - se [Skapa din första funktionsflagga](create-your-first-feature-flag.md)

En funktionsgrupp för flera team gör det möjligt att paketera funktionsflaggor från program i flera team med avancerad målgruppsanpassning. Till skillnad från releaser är den helt självbetjäning och har ingen begränsning av antalet du kan skapa. Se [Releaser och funktionsgrupper mellan team](releases-and-cross-team-feature-groups.md) för en jämförelse.

## Steg 1: Skapa funktionsgruppen för flera team {#create}

Börja skapa från avsnittet Releaser i konsolen:

1. Navigera till **Funktioner och releaser > Releaser** i konsolen.
2. Välj **Ny funktionsgrupp (flera team)**.

## Steg 2: Grundläggande information {#basic-details}

Ange en titel, nyckel, beskrivning och eventuellt en tagg. Konfigurera följande alternativ:

* **Procentandel av utrullningen** - Ange hur mycket av publiken som tar emot funktionen.
* **Utrullningstyp** - Välj Manuell eller Automatiserad. Se [Automatiserade rollouts](../automated-rollouts/automated-rollout-concept.md) för mer information om hur automatiserade rollouts fungerar.

>[!NOTE]
>
>A/B-testning stöds inte för team-funktionsgrupper. Om du vill köra A/B-tester använder du en [standardfunktionsgrupp](create-a-feature-group.md) (programmen måste finnas i samma team).

## Steg 3: Målgrupp {#audience}

Aktivera **Målgruppsregler** på fliken **Målgrupp** och konfigurera:

* **Segment** - Välj ett fördefinierat målgruppssegment.
* **Ytterligare filter** - Lägg till profilbaserade eller kontextbaserade kriterier direkt.
* **Program** - Välj ett eller flera program från ditt team eller andra team.

>[!IMPORTANT]
>
>Om du lägger till ett program från ett annat team får funktionsadministratörerna i det teamet behörighet att lägga till funktionsflaggor för sina program i teamets funktionsgrupp. Du kan inte lägga till deras funktionsflaggor själv.

## Steg 4: Funktioner {#features}

Under fliken **Funktioner** visas en ruta för varje program:

* För program i ditt eget team kan du lägga till funktionsflaggor direkt.
* För program från andra team är rutorna nedtonade - teamets funktionsadministratörer måste lägga till flaggorna.

>[!IMPORTANT]
>
>En funktionsflagga kan bara användas med en metod i taget. Om du lägger till en flagga i en funktionsgrupp för flera team tas alla målgrupper och procentandelar som anges på flaggan bort direkt. Flaggor som redan finns i en annan release eller funktionsgrupp visas inte.

## Steg 5: Schema (valfritt) {#schedule}

Du kan schemalägga att teamets funktionsgrupp ska aktiveras vid ett senare datum och en senare tidpunkt. Mer information finns i [Schema](schedule.md).

## Hantera lägen {#states}

Teamet som skapar teamets funktionsgrupp äger den och kan hantera dess status. Funktionsadministratörens medlemmar i det ägande teamet kan övergå mellan lägen med listrutan Läge:

| Läge | Beskrivning |
|---|---|
| **Spara** | Sparad och inte live. Alla ändringar är tillåtna. |
| **Publicera** | Live för den konfigurerade publiken. Funktionsadministratörer kan fortsätta uppdatera målgruppskriterier och procentuell utrullning. |
| **Fullständig utrullning** | Tillgängligt för alla användare. Det går inte att begränsa målgruppen ytterligare efter den här punkten. |
| **Originalplan** | Funktioner är nu standard. Teamteamets funktionsgrupp är stängd. |
| **Avbryt** | utrullningen har stoppats. Inga användare får funktioner från den här gruppen. |

## Vanliga frågor {#faqs}

**Finns det en gräns för antalet funktionsgrupper mellan team?**
Nej. Till skillnad från releaser finns det ingen gräns. Arkivera eller inaktivera grupper när de inte längre behövs.

**Vad är skillnaden mellan en release och en funktionsgrupp för flera team?**
En detaljerad jämförelse finns i [Releaser och teamöverskridande funktionsgrupper](releases-and-cross-team-feature-groups.md).

## Se även {#see-also}

* [Releaser och teamöverskridande funktionsgrupper](releases-and-cross-team-feature-groups.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [Skapa en automatiserad utrullning](../automated-rollouts/create-automated-rollout.md)
