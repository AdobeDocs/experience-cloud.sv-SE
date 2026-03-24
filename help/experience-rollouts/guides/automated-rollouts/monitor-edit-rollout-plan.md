---
title: Övervaka och redigera en utrullningsplan
description: Lär dig hur du spårar förloppet för en automatiserad utrullningsplan i Adobe Experience Rollouts och hur du pausar, återupptar eller avbryter en pågående plan.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Övervaka och redigera en utrullningsplan {#monitor-edit-rollout-plan}

När en automatiserad utrullning är klar kan ni följa dess utveckling och ingripa om det behövs. Den här sidan beskriver hur du läser förloppsindikatorn, pausar och återupptar en plan och avbryter den om det behövs.

Den här sidan förutsätter att du redan har skapat och publicerat en utrullningsplan. Se [Skapa en automatiserad utrullning](create-automated-rollout.md) om du inte har konfigurerat en ännu.

## Visa utrullningsförlopp {#view-progress}

När utrullningsplanen har börjat köras öppnar du fliken **Målgrupp** för funktionen för att se planens aktuella tillstånd. I planen visas en förloppsindikator som anger vilket fasblock som är aktivt.

Använd förloppsindikatorn för att förstå följande:

* **Slutförda block** - Alla fas- och vänteblock ovanför indikatorn har körts. Dessa block är låsta och kan inte redigeras.
* **Aktuellt block** - Det markerade blocket är den aktiva fasen eller vänteperioden.
* **Kommande block** - Alla fas- och vänteblock under indikatorn har inte körts ännu. Dessa kan fortfarande redigeras.

## Pausa en utrullningsplan {#pause}

Om du vill pausa utrullningen när som helst medan den pågår väljer du **Pausa utrullning** i konsolen.

När planen har pausats:

* Publiken från det sista slutförda fasblocket förblir aktiv. Användare i den målgruppen fortsätter att få tillgång till funktionen.
* Funktionsflaggan, funktionsgruppen eller teamets funktionsgrupp är fortfarande i det aktuella läget eller publicerade läget. Funktionen fortsätter att användas av den aktiva målgruppen.
* Kommande fas- och vänteblock går fortfarande att redigera.

Om du vill återuppta en pausad plan väljer du **Återuppta utrullning**. Planen fortsätter där den slutade.

## Avbryta en utrullningsplan {#abort}

Om du vill stoppa utrullningsplanen permanent väljer du **Avbryt utrullning** i konsolen.

När planen avbryts:

* Publiken från det sista slutförda fasblocket är aktiv och funktionen fortsätter att vara tillgänglig för den målgruppen.
* Själva funktionen är inte inaktiverad - om du vill sluta använda funktionen helt måste du avbryta releasen separat eller inaktivera funktionsflaggan eller gruppen.
* Kommande fas- och vänteblock kan inte längre redigeras.
* En avbruten plan kan inte återupptas.

>[!IMPORTANT]
>
>Funktionen inaktiveras inte automatiskt när du avbryter en utrullningsplan. Gör en separat åtgärd för funktionstillståndet om du inte längre vill att det ska visas för användarna.

## Redigera kommande fasblock {#edit-upcoming}

Medan planen pågår (eller pausas) kan du fortfarande redigera alla faser eller vänteblock som ännu inte har körts:

* Justera målgruppsreglerna eller procentandelen för ett kommande fasblock.
* Ändra varaktighet eller fast datum för ett kommande vänteblock.

Slutförda block är låsta och kan inte ändras.

## Se även {#see-also}

* [Skapa en automatiserad utrullning](create-automated-rollout.md)
* [Automatiserat utrullningskoncept](automated-rollout-concept.md)
* [Frigör lägen](../feature-flags/release-states.md)
