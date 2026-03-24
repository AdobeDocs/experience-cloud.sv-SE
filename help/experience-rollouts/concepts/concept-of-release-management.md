---
title: Frisläppningshantering
description: Läs om hur versionshantering i Experience Rollouts hjälper till att koordinera stora, teamövergripande funktionslanseringar genom funktionsflaggning.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Frisläppningshantering {#concept-of-release-management}

Stora releaser delar några vanliga utmaningar: flera team är inblandade, schemakonflikter och beroenden är svåra att samordna. Versionshantering löser dessa problem genom ett strukturerat sätt att smidigt införa ändringar.

## Vad versionshantering innebär {#what-it-means}

Versionshanteringen omfattar samordningen av en release från början till slut - från det att team börjar utveckla funktioner bakom tills funktionen är helt tillgänglig för alla användare.

Med den kan teamen

* Driftsätt oberoende i sin egen takt i produktionen utan att slutanvändarna får tillgång till funktioner
* Publicera bara när alla deltagande team är klara
* Rulla ut releasen gradvis till en delmängd av användarna innan den är helt tillgänglig

## Så här fungerar det i upplevelseutrullningar {#how-it-works}

Versionshantering i Experience Rollouts bygger på konceptet [funktionsflaggning](what-is-a-feature-flag.md). Varje team distribuerar sin kod till produktion bakom en funktionsflagga. En release är sedan en **samling funktionsflaggor som definierats i flera program och team**.

När alla team är klara kan releasen aktiveras i en enda åtgärd - eller successivt lanseras - utan att någon enskild grupp behöver omdistribuera eller samordna tidsåtgången för driftsättningen.

Detta tillvägagångssätt ger:

* **Oberoende distribution** - Team distribueras enligt eget schema utan att påverka andra team eller slutanvändare.
* **Samordnad aktivering** - Alla flaggor i en release aktiveras tillsammans när releasen aktiveras.
* **Grund utrullning** - Versionen kan öppnas progressivt till ökande procentandelar av användare.

Mer information om hur du konfigurerar releaser i Experience Rollouts finns i [Versionshantering](release-management.md).
