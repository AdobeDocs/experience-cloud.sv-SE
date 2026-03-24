---
title: Målgrupp i funktionsflaggor och funktionsgrupper
description: Lär dig hur du definierar målgruppskriterier för funktionsflaggor och funktionsgrupper i Adobe Experience Rollouts med hjälp av profilattribut, segment och målgruppsberäknaren.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Målgrupp i funktionsflaggor och funktionsgrupper {#audience-overview}

Experience Rollouts ger en rik målgruppsanpassning för funktionsflaggor och funktionsgrupper. Du kan kombinera profilattribut, kontextvariabler och målgruppssegment för att exakt kontrollera vilka användare som får en funktion.

## Profilregler {#profile-rules}

Med profilregler kan du inrikta dig på användare baserat på attribut som land, e-postdomän, kontotyp, användar-ID och annat. Du kan kombinera flera attribut med AND/OR-operatorer och skapa kapslad logik för komplexa målinriktningsscenarier.

Om du vill lägga till profilregler går du till fliken **Målgrupp** i en funktionsflagga eller funktionsgrupp och lägger till villkor under **Profil**.

Du kan spara en uppsättning målgruppsregler som en återanvändbar **målgrupp** för användning över flera flaggor och grupper.

Kontextbaserad målinriktning (till exempel efter användarens aktiva språk eller klienttyp) finns i [Använd kontext i målgruppsregler](using-context-in-audience-rules.md).

## Segment {#segments}

Funktionsflaggor och funktionsgrupper har stöd för målgruppssegment. Med segment kan du:

* Använd en enda fördefinierad målgruppsdefinition för flera funktionsflaggor och grupper
* Inkludera **händelsebaserade kriterier** i målgruppen - något som inte är möjligt enbart med profilregler

Om du vill använda ett segment går du till fliken **Målgrupp** och väljer ett eller flera segment i listan. Du kan kombinera flera segment med operatorerna AND/OR och lägga till ytterligare profil- eller kontextfilter tillsammans med dem.

>[!NOTE]
>
>Du behöver rollen **Testhanteraren** eller senare för att skapa målgruppssegment.

## Målgruppskalkylator {#audience-calculator}

När du har definierat målgruppsvillkoren väljer du **Beräkna** i det nedre fältet för att få ett beräknat antal användare som uppfyller kraven. Detta hjälper er att validera målgruppens räckvidd innan ni aktiverar funktionen.

>[!NOTE]
>
>Målgruppsberäknaren returnerar inget värde när kontextvariabler ingår i kriterierna, eftersom kontextvärden bestäms vid körning och inte kan förutsägas i förväg.

## Se även {#see-also}

* [Använd sammanhang i målgruppsregler](using-context-in-audience-rules.md)
* [Lägg till procentregler i målgruppskriterier](adding-percentage-rules.md)
* [Komplexa målgruppsregler](complex-rules.md)
* [Skapa din första funktionsflagga](../feature-flags/create-your-first-feature-flag.md)
