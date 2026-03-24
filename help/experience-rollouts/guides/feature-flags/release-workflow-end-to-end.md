---
title: Arbetsflöde från början till slut
description: Lär dig det kompletta arbetsflödet för hantering av en samordnad release i Adobe Experience Rollouts, från att definiera funktionsflaggor till publicering.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# Arbetsflöde från början till slut {#release-workflow}

Den här sidan beskriver den fullständiga sekvensen av aktiviteter som ingår i en samordnad release som hanteras av en versionshanterare.

## &#x200B;1. Definiera funktionsflaggor per program {#define-flags}

Varje produktteam tilldelar en **produktversionsägare** som loggar in på Experience Rollouts-konsolen och skapar funktionsflaggor för de program de äger. Produktgruppen implementerar sedan den villkorliga logiken i sin kod, vilket placerar funktioner bakom dessa flaggor.

## &#x200B;2. Skapa releasen {#create-release}

För att skapa en ny release krävs en supportförfrågan - den är inte helt självbetjänad. Kontakta Experience Rollouts om du vill skapa releasen. Ange namn, ägande team, målmiljö, mål, deltagande program och förväntad varaktighet.

När releasen har bekräftats öppnar Release Manager konsolen och slutför versionskonfigurationen.

## &#x200B;3. Lägg till funktionsflaggor i versionen {#add-flags}

För varje program som läggs till i releasen loggar programmets produktversionsägare in och lägger till de relevanta funktionsflaggorna i releasen. De här flaggorna representerar de funktioner som kommer att publiceras med releasen.

## &#x200B;4. Konfigurera målgruppen {#configure-audience}

Release Manager väljer målgrupp för releasen - till exempel 1 % av användarna i ett visst land, alla användare med en viss e-postdomän eller en lista med specifika användar-ID:n. När den är konfigurerad sparar och publicerar Release Manager releasen, som gör den offentlig för den angivna publiken.

## &#x200B;5. Utöka och hantera utrullningen {#expand}

När releasen är klar kan Release Manager justera målgruppsreglerna för att gradvis utöka utrullningen, övervaka eventuella problem och använda kontrollerna för att hantera livscykeln. Mer information finns i [Releasedatan](release-states.md).

## Viktiga punkter {#key-points}

* Alla deltagande program driftsätter sin kod för produktion oberoende av funktionsflaggor - ingen samordnad driftsättningstid behövs.
* Versionen är den enda kontrollpunkten som aktiverar alla flaggor mellan team samtidigt.
* Målgruppsanpassning för releaser baseras på autentiseringstokenattribut (land, e-post, användar-ID, procent).

## Se även {#see-also}

* [Begär en release](request-a-release.md)
* [Uppdatera publiceringsregler](update-release-audience-rules.md)
* [Frigör lägen](release-states.md)
