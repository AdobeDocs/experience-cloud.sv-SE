---
title: Frigör lägen
description: Lär dig mer om livscykelstadierna för en release i Adobe Experience Rollouts, inklusive vad varje steg betyder och vilka övergångar som tillåts.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---


# Frigör lägen {#release-states}

En versionshanterare kan uppdatera en releases tillstånd direkt från konsolens navigeringsfält. Läget styr om releasen är live, begränsad till testning, helt utrullad eller stängd.

## Tillgängliga lägen {#states}

| # | Läge | Beskrivning | Tillåtna ändringar |
|---|---|---|---|
| 1 | **Utkast** | Versionen sparas i systemet men är ännu inte aktiv. Inga målgruppsregler tillämpas. | Alla ändringar är tillåtna (release, funktioner, målgrupp). |
| 2 | **Sparad** | Versionen är registrerad och en plats tilldelas den. Versionen är ännu inte synlig för användarna. | Alla ändringar tillåts. |
| 3 | **Publicerad** | Versionen är live för den angivna publiken. Användare som uppfyller målgruppens kriterier får tillgång till funktionerna. | Alla ändringar tillåts. |
| 4 | **Fullständig utrullning** | Versionen är tillgänglig för alla användare oavsett målgruppsregler. Alla målgruppsregler tas bort. | Tillåtna funktionsändringar. Målgruppen kan inte ändras. |
| 5 | **Baslinje** | Alla användare har nu funktionerna från den här versionen som standardbeteende. Villkorskoden kan tas bort. Versionsplatsen är frigjord. | Inga ändringar tillåts. |
| 6 | **Avbruten** | Versionen har stoppats. Inga användare får funktioner från den här versionen. Versionsplatsen är frigjord. | Inga ändringar tillåts. |

## Tillåt övergångar {#transitions}

Alla övergångar är inte tillåtna. Genom att förstå de tillåtna sökvägarna kan du planera utrullningen och undvika fel när du hanterar lägesändringar:

* En release kan gå framåt genom följande lägen: Utkast → Sparad → Publicerad → Fullständig utrullning → Baslinje
* En release kan avbrytas från utkast, sparad, publicerad eller fullständig utrullning
* När baslinjen har stängts eller avbrutits tillåts inga fler ändringar

## Frisläpp kapacitet {#capacity}

Antalet aktiva (sparade eller publicerade) versioner är begränsat. Så här frigör du kapacitet:

* Flytta slutförda releaser till **Baslinje** när alla deltagande program har tagit bort villkorskoden.
* **Avbryt** versioner som misslyckades och som inte kommer att fortsätta.

Planera att börja eller avbryta era releaser inom tre månader.

## Se även {#see-also}

* [Begär en release](request-a-release.md)
* [Arbetsflöde från början till slut](release-workflow-end-to-end.md)
* [Uppdatera publiceringsregler](update-release-audience-rules.md)
