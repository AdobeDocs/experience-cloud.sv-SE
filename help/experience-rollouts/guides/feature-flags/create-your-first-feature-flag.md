---
title: Skapa din första funktionsflagga
description: Lär dig hur du skapar en funktionsflagga i Adobe Experience Rollouts, anger en målgrupp och testar den innan du distribuerar den till användarna.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Skapa din första funktionsflagga {#create-feature-flag}

## Förutsättningar {#prerequisites}

Fyll i följande innan du skapar en funktionsflagga:

* Du har åtkomst till konsolen Experience Rollouts - se [Logga in på konsolen](../console/log-in-to-the-console.md)
* Du tillhör ett team - se [Hantera team](../teams/manage-teams.md)
* Ditt program är introducerat - se [Ansluta ditt program](../applications/onboard-your-application.md)
* Du har rollen **Utvecklare** eller **Ägare av produktreleaser** - se [Användarroller](../teams/user-roles.md)

## Steg 1: Skapa funktionsflaggan {#create}

Så här skapar du en ny funktionsflagga:

1. Logga in på konsolen Experience Rollouts och gå till **Funktioner och releaser > Funktionsflaggor**.
2. Välj ditt program i listrutan **Program**.
3. Välj **Ny funktion**.
4. Ange en titel, nyckel, beskrivning och eventuellt en tagg.
5. Du kan också lägga till ett målgruppsvillkor (se steg 2).
6. Spara inställningarna för funktionsflaggan.

## Steg 2: Lägg till ett målgruppsvillkor {#audience}

Målgruppskriterier styr vilka användare som ser funktionen. Du kan lägga till villkor baserat på:

* Profilattribut (t.ex. land, e-postdomän, användar-ID)
* Kontextvariabler
* Fördefinierade målgruppssegment

Om du vill lägga till målgruppsvillkor går du till fliken **Målgrupp** när du skapar eller redigerar en funktionsflagga.

>[!NOTE]
>
>Rollen **Utvecklare** är i begränsat läge. Utvecklare kan bara visa en funktion för sig själva genom att lägga till ett eget användar-ID under **Målgrupp > Profil > Användar-ID**. Om du vill visa en funktion för externa användare behöver du rollen **produktversionsägare**.

## Steg 3: Beräkna målgruppens storlek {#audience-size}

När du har lagt till målgruppsvillkor väljer du **Beräkna** i det nedre fältet för att få ett beräknat antal användare som är kvalificerade för funktionen. Detta hjälper er att validera er målinriktning innan ni publicerar.

## Steg 4: Schema (valfritt) {#schedule}

Du kan schemalägga en funktionsflagga att aktivera vid ett framtida datum och en framtida tidpunkt. Mer information finns i [Schema](schedule.md).

## Vanliga frågor: Jag kan inte lägga till en funktionsflagga som utvecklare {#faq}

Rollen **Utvecklare** är i begränsat läge. Utvecklare kan testa funktioner privat genom att lägga till sitt användar-ID till målgruppen. De kan inte visa funktioner för externa användare. Använd rollen **Product Release Owner** om du vill frisläppa funktioner till externa användare. Kontakta teamadministratören för att uppdatera din roll.

## Se även {#see-also}

* [Ange en funktion som gradvis ska rulla ut](set-feature-gradual-rollout.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
* [Användarroller](../teams/user-roles.md)
