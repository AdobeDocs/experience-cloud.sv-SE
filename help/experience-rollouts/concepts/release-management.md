---
title: Versionshantering i upplevelseutrullningar
description: Läs om hur versionshantering i Experience Rollouts koordinerar multiteam-leverans genom mörk driftsättning, produktionstestning och gradvisa driftsättningar.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---


# Versionshantering i upplevelseutrullningar {#release-management}

En typisk större release omfattar flera team och flera program, var och en med sina egna tidslinjer och beroenden. Experience Rollouts är en modell för versionshantering som låter team arbeta oberoende samtidigt som de levererar en samordnad, kontrollerad release till slutanvändarna.

## Viktiga funktioner {#capabilities}

### Mörka distributioner {#dark-deployments}

Teamen behöver inte längre tidlägga sin koddistribution med ett visst publiceringsdatum. Kod kan när som helst distribueras till produktion bakom funktionsflaggor. Slutanvändarna ser ingen ändring förrän releasen aktiveras. Team kan driftsätta i sin egen takt och vara säkra på att inget exponeras i förtid.

### Testning i produktion {#testing-in-production}

När koden har distribuerats till produktionen - mörk driftsättning - kan upplevelseutrullningar öppna funktionerna för interna testare och QA-team. Detta möjliggör fullständig testning mot produktionsmiljön och verkliga produktionsdata, utan risk för att slutanvändarna exponeras för förändringar.

### gradvis utrullning {#gradual-rollout}

När en release är klar att publiceras behöver den inte vara helt eller ingenting. Med Experience Rollouts kan du styra utrullningen stegvis - från en liten andel av användarna, övervaka feedback och prestanda samt utöka publiken över tid. Detta minskar belastningen på backend-system och ger team tid att svara på eventuella problem innan de får full exponering.

### Samordnad aktivering {#coordinated-activation}

Flera team utvecklar funktioner oberoende av varandra, var och en bakom sina egna funktionsflaggor. När alla team är klara tillhandahåller Experience Rollouts en enda kontrollpunkt för att aktivera alla flaggor mellan team och program samtidigt - eller gradvis - så att releasen blir en sammanhängande upplevelse.

## Se även {#see-also}

* [Frisläppningshantering](concept-of-release-management.md)
* [Funktionsgrupper som styr flera funktioner](feature-groups-to-control-multiple-features.md)
* [gradvis utrullning](gradual-rollout.md)
