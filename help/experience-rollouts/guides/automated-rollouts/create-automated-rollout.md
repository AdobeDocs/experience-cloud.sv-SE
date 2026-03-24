---
title: Skapa en automatiserad utrullning
description: Lär dig hur du konfigurerar en automatiserad utrullningsplan i Adobe Experience Rollouts med fasblock och vänteblock så att målgruppen utökas automatiskt över tid.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Skapa en automatiserad utrullning {#create-automated-rollout}

Med en automatiserad utrullning kan du definiera alla utrullningsfaser och deras scheman i en session. Upplevelseutrullningar går automatiskt från en fas till nästa, utan att du behöver gå tillbaka till konsolen för varje steg. Mer information finns i [Automatiserat utrullningskoncept](automated-rollout-concept.md).

Automatiserade lanseringar stöds för funktionsflaggor, funktionsgrupper och teamöverskridande funktionsgrupper.

## Steg 1: Aktivera automatiserad utrullning {#enable-automated-rollout}

När du skapar en ny funktionsflagga, funktionsgrupp eller funktionsgrupp för flera team öppnar du fliken **Grundläggande information** och letar upp alternativet **Välj typ av utrullning** . Standardvärdet är **Manuell**. Om du vill aktivera en automatiserad utrullningsplan väljer du **Automatisk utrullning**.

>[!NOTE]
>
>När du väljer Automatisk utrullning ställs procentvärdet i fältet Grundläggande information automatiskt in på 100 % och blir icke-redigerbart. Du styr procentandelen för varje fas individuellt på fliken Målgrupp.

## Steg 2: Skapa utrullningsplanen {#build-rollout-plan}

Öppna fliken **Målgrupp** och aktivera växlingsknappen **Faser**. Detta aktiverar kontrollerna **Lägg till fasblock** och **Lägg till vänteblock**.

Om du vill skapa en utrullningsplan lägger du till fas- och vänteblock i den ordning som du vill att de ska köras:

### Lägga till ett fasblock {#add-phase-block}

Ett fasblock definierar målgruppskriterierna för en fas av utrullningen. Det första fasblocket konfigureras med de målgruppskriterier som redan finns på sidan. För varje efterföljande fasblock fylls den föregående fasens målgrupp i automatiskt som startpunkt.

Konfigurera målgruppen för varje fasblock:

* **Procent** - Ange vilken procentandel av den definierade målgruppen som ska ta emot funktionen i den här fasen.
* **Målgruppsregler** - Lägg till profil-, kontext- eller segmentbaserade regler för specifika användare.

>[!IMPORTANT]
>
>Varje efterföljande fas bör expandera, inte ersätta, den föregående fasens målgrupp. Ta inte bort målgruppsregler från tidigare faser när du konfigurerar senare, eftersom detta kan utesluta användare som redan har fått funktionen av misstag.

### Lägg till ett vänteblock {#add-wait-block}

Ett vänteblock definierar pausen mellan två fasblock. När du har lagt till ett vänteblock väljer du något av följande alternativ:

| Alternativ | Beskrivning |
|---|---|
| **Vänta** | En relativ varaktighet - till exempel, vänta 2 dagar, vänta 4 timmar. Upplevelseutrullningar går vidare till nästa fasblock när den här varaktigheten har gått ut. |
| **Vänta på** | Ett fast datum och en fast tid. Upplevelseutrullningar går vidare till nästa fasblock vid den angivna tidpunkten. |

### Lägg till efterföljande fasblock {#add-subsequent-phases}

Upprepa processen för att lägga till ytterligare fasblock och vänta tills din fullständiga utrullningsplan har konfigurerats.

## Steg 3: Schemalägg eller publicera utrullningen {#schedule-or-publish}

När utrullningsplanen är klar väljer du hur den ska aktiveras:

* **Schema** - Ange ett framtida datum och en framtida tid för utrullningen så att den startar automatiskt. Mer information finns i [Schema](../feature-flags/schedule.md).
* **Publicera manuellt** - Aktivera funktionsflaggan eller flytta funktionsgruppen till läget **Publicera** om du vill starta direkt.

Planen börjar köras från det första fasblocket. Du kan övervaka och redigera den aktiva planen när som helst. Se [Övervaka och redigera en utrullningsplan](monitor-edit-rollout-plan.md).

## Se även {#see-also}

* [Automatiserat utrullningskoncept](automated-rollout-concept.md)
* [Övervaka och redigera en utrullningsplan](monitor-edit-rollout-plan.md)
* [Ange en funktion som gradvis ska rulla ut](../feature-flags/set-feature-gradual-rollout.md)
* [Målgruppskriterier](../audience/audience-in-feature-flags-and-feature-groups.md)
