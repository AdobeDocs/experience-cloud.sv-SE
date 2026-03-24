---
title: Lägg till procentregler i målgruppskriterier
description: Lär dig hur du lägger till procentbaserade regler inom målgruppskriterier i Adobe Experience Rollouts för att ange olika procentsatser för utrullning för olika målgruppssegment.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Lägg till procentregler i målgruppskriterier {#adding-percentage-rules}

## När procentregler ska användas på målgruppsfliken {#when-to-use}

Fältet **procentuell utrullning** på fliken Grundläggande information använder en enda procentsats för hela målgruppen. 50 % utrullning innebär till exempel att 50 % av alla användare som matchar dina målgruppskriterier får funktionen.

Vissa utrullningsscenarier kräver dock olika procentandelar för olika grupper, till exempel:

* 100 % av användare i Storbritannien och 50 % av användare i USA
* Alla användare från en importerad e-postlista, plus 50 % av användarna från ett visst land

I dessa fall ska du använda regeln **Procent** i profilavsnittet på fliken **Målgrupp** kombinerat med kapslad logik.

>[!TIP]
>
>Om du vill använda en enda procentsats för hela målgruppen - till exempel 10 % av användarna i (USA och Storbritannien) - använder du den **procentuella utrullningen** på fliken Grundläggande information i stället.

## Lägga till en procentregel {#how-to-add}

Alternativet **Procent** är tillgängligt som regel i profilavsnittet på fliken Målgrupp.

1. Gå till fliken **Målgrupp** i funktionsflaggan eller funktionsgruppen.
2. Lägg till en **procentregel** under **Profil** och ange önskat värde.
3. Lägg till andra målgruppsvillkor som du behöver (t.ex. en landskapsregel).

## Kombinera procentregler med kapslad logik {#nested-logic}

Använd **kapslad logik** för att kombinera villkoren om du vill använda olika procentsatser för olika segment:

1. Aktivera **kapslad logik** i målgruppsregelavsnittet.
2. Varje villkor tilldelas ett nummer automatiskt.
3. Ange ett logiskt uttryck som refererar till dessa tal.

Använd ett av följande uttryck för att beskriva förhållandet mellan dina villkor:

* `1 and (2 or 3)` - villkor 1 OCH (villkor 2 ELLER villkor 3)
* `(1 and 2) or 3` — (villkor 1 OCH villkor 2) ELLER villkor 3
* `(1 and 2) or (3 and 4)` - två oberoende grupper

## Exempel {#examples}

**Exempel 1: Alla användare från en importerad lista och 10 % av användarna från ett visst land**

Lägg till två regler: en för den importerade användarlistan och en procentregel (10 %) i kombination med en landskapsregel. Använd kapslad logik: `1 or (2 and 3)`.

**Exempel 2: 10 % av användarna i USA och 20 % av användarna i Storbritannien**

Lägg till fyra regler: Land = USA, Procent = 10 %, Land = Storbritannien, Procent = 20 %. Använd kapslad logik: `(1 and 2) or (3 and 4)`.

## Se även {#see-also}

* [Målgrupp i funktionsflaggor och funktionsgrupper](audience-in-feature-flags-and-feature-groups.md)
* [Komplexa målgruppsregler](complex-rules.md)
* [Ange en funktion som gradvis ska rulla ut](../feature-flags/set-feature-gradual-rollout.md)
