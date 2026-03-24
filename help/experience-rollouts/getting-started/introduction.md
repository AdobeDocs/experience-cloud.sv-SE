---
title: Introduktion till upplevelselanseringar
description: Läs om hur Adobe Experience Rollouts är ett system med kontrollerad version som gör det möjligt att distribuera funktioner progressivt till målgrupper.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Introduktion till upplevelselanseringar {#introduction}

Adobe Experience Rollouts är ett system med kontrollerad version som låter team driftsätta funktioner hela vägen till produktionen samtidigt som de har exakt kontroll över vem som ser dem och när. En funktion kan vara i produktion och osynlig för slutanvändarna, och sedan aktiveras progressivt för en viss målgrupp - utan någon omdistribution.

## Från utveckling till produktion {#dev-to-prod}

Upplevelseutrullningar har stöd för hela processen från det första utvecklingssteget till den allmänna tillgängligheten:

1. **Utvecklartestning** - En utvecklare skapar en funktionsflagga, distribuerar sin kod till valfri miljö och testar mot endast sin egen session. Inga andra användare påverkas och ingen förgrening krävs.

2. **Målinriktad förhandsgranskning** - En produktägare länkar en publik till funktionsflaggan och gör funktionen tillgänglig för en definierad delmängd av användare (till exempel betatestare eller en viss region) för validering och feedback.

3. **Grund utrullning** - Funktionen öppnas progressivt för en större publik - 1 %, 10 %, 50 %, 100 % - med möjlighet att pausa, justera eller inaktivera funktionen i vilket steg som helst.

4. **Allmän tillgänglighet** - När valideringen är klar blir funktionen tillgänglig för alla användare.

## Kärnfunktioner {#capabilities}

Upplevelseutrullningar är en funktionshanteringsplattform som ger:

* **Funktionsflaggor** - Aktivera eller inaktivera en funktion under körning för en viss målgrupp, utan att behöva omdistribuera kod.

* **Målgruppsanpassning** - Kontrollera vilka som ser en funktion med hjälp av användarprofildata, procentbaserade regler, e-postadress, e-postdomän, IP-adress eller sammanhangsbaserade attribut.

* **Funktionsgrupper** - Paketera flera relaterade funktionsflaggor mellan program och hantera dem som en enda enhet, så att samma målgrupp får en enhetlig upplevelse.

* **Releaser** - Koordinera stora gruppöverskridande rollouter genom att gruppera funktionsflaggor från flera team och program i en enda release-händelse.

* **Delvisa rollouter** - Phase feature delivery incremental to reduce risk, collect feedback, and manage backend load.

* **Avsluta switch** - Stäng av en funktion omedelbart om ett problem upptäcks, utan kodändring eller omdistribution.
