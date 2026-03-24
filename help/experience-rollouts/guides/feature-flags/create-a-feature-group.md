---
title: Skapa en funktionsgrupp
description: Lär dig hur du skapar en funktionsgrupp i Adobe Experience Rollouts för att hantera flera funktionsflaggor mellan program i teamet som en enda enhet.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Skapa en funktionsgrupp {#create-feature-group}

## Förutsättningar {#prerequisites}

Innan du skapar en funktionsgrupp gör du följande:

* Du har åtkomst till konsolen Experience Rollouts - se [Logga in på konsolen](../console/log-in-to-the-console.md)
* Du tillhör ett team - se [Hantera team](../teams/manage-teams.md)
* Ditt program är introducerat - se [Ansluta ditt program](../applications/onboard-your-application.md)
* Du har rollen **Utvecklare** eller **Ägare av produktreleaser** - se [Användarroller](../teams/user-roles.md)
* Du har skapat de funktionsflaggor som du vill lägga till i gruppen - se [Skapa din första funktionsflagga](create-your-first-feature-flag.md)

En introduktion till funktionsgrupper finns i [Funktionsgrupper för att styra flera funktioner](../../concepts/feature-groups-to-control-multiple-features.md).

## Steg 1: Skapa funktionsgruppen {#create}

Öppna konsolen och starta en ny funktionsgrupp:

1. Logga in på konsolen Experience Rollouts och gå till **Funktionstestning > Funktionsgrupper**.
2. Välj **Ny funktionsgrupp**.

## Steg 2: Grundläggande information {#basic-details}

Konfigurera de allmänna inställningarna för funktionsgruppen:

1. Ange en titel, nyckel, beskrivning och eventuellt en tagg.
2. Ange en **procentuell utrullning** för funktionsgruppen.
3. Om du vill köra ett A/B-test väljer du mer än en variant. Annars låter du den vara på en variant. Mer information finns i [A/B-testning med funktionsflaggor](a-b-testing.md).

## Steg 3: Målgrupp {#audience}

Definiera vem som ska få funktionerna i den här gruppen:

1. Lägg till målgruppskriterier på fliken **Målgrupp** för att definiera vilka användare som ska få funktionen.
2. Lägg till ett eller flera program från ditt team under **Program**. Funktionsgrupper kan omfatta flera program så länge de tillhör samma team.

>[!NOTE]
>
>Rollen **Utvecklare** är i begränsat läge. Lägg till ditt eget användar-ID under **Målgrupp > Profil > Användar-ID** för att testa privat. Om du vill ha externa användare som mål behöver du rollen **produktversionsägare**.

## Steg 4: Funktioner {#features}

Tilldela de funktionsflaggor som ska styras av den här gruppen:

1. Under fliken **Funktioner** visas en ruta för varje program som du har valt.
2. Lägg till funktionsflaggor för varje program.
3. Om du valde flera varianter (för A/B-testning) visas flikar för varje variant. Lägg till lämpliga funktionsflaggor i varje.

>[!IMPORTANT]
>
>En funktionsflagga kan bara användas med en metod, antingen direkt som en funktionsflagga, via en funktionsgrupp eller via en release. När du lägger till en funktionsflagga i en funktionsgrupp tas alla målgrupps- eller procentuella utrullningar som angetts för flaggan bort. Funktionsflaggor som redan har tilldelats en annan release eller funktionsgrupp visas inte i listan.

## Steg 5: Schema (valfritt) {#schedule}

Du kan schemalägga att funktionsgruppen ska aktiveras vid ett senare datum och en senare tidpunkt. Mer information finns i [Schema](schedule.md).

## Se även {#see-also}

* [Ange att en funktionsgrupp ska rullas ut gradvis](set-feature-group-gradual-rollout.md)
* [A/B-testning med funktionsflaggor](a-b-testing.md)
* [Funktionsgrupper som styr flera funktioner](../../concepts/feature-groups-to-control-multiple-features.md)
