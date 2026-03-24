---
title: Automatiserat utrullningskoncept
description: Förstå hur automatiserade lanseringar fungerar i Adobe Experience Rollouts, inklusive fasblock, vänteblock och hur lanseringsplanen utvecklas automatiskt.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---


# Automatiserat utrullningskoncept {#automated-rollout-concept}

Med en automatiserad utrullning kan du definiera hela din infasade lanseringsplan på en gång. Istället för att manuellt gå tillbaka till konsolen för att utöka publiken för varje fas, konfigurerar du alla faser och deras scheman direkt och Experience Rollouts går igenom dem automatiskt.

Automatiserade lanseringar stöds för funktionsflaggor, funktionsgrupper och teamöverskridande funktionsgrupper.

## Så här fungerar det {#how-it-works}

En utrullningsplan består av **fasblock** och **vänteblock** som körs i sekvens:

* **Fasblock** - Definierar målgruppskriterier för en fas av utrullningen. När planen når ett fasblock blir den målgruppen aktiv för funktionen.
* **Vänteblock** - Definierar paus mellan två fasblock. Ett vänteblock kan antingen vara en relativ varaktighet (till exempel &quot;vänta 3 dagar&quot;) eller ett fast datum och en fast tid.

Planen börjar när du publicerar funktionen eller schemalägger den för ett framtida datum. Upplevelseöverrullningar flyttas automatiskt från ett block till nästa enligt det schema du konfigurerade.

## Beteende för fasblock {#phase-block-behavior}

Varje efterföljande fasblock är förifyllt med målgruppen från den föregående fasen. Detta gör det enklare att bygga stegvis växande rollouts där varje ny fas omfattar alla tidigare målgrupper förutom de nya.

>[!IMPORTANT]
>
>Målgruppsreglerna i varje fasblock kan redigeras, så du måste se till att inte ta bort målgruppsvillkor från tidigare faser när du lägger till nya. Om du minskar målgruppsomfånget kan användarna oväntat förlora åtkomsten till en funktion.

## Lägen för utrullningsplan {#rollout-plan-states}

När en utrullningsplan är klar kan den vara i ett av tre lägen:

| Läge | Beskrivning |
|---|---|
| **Pågår** | Planen körs. En förloppsindikator i konsolen visar vilket fasblock som är aktivt. Alla slutförda block är låsta och kan inte redigeras. |
| **Pausad** | Planen är vilse. Publiken från det sista slutförda fasblocket förblir aktiv. Framtida fas- och vänteblock kan fortfarande redigeras medan de pausas. |
| **Avbruten** | Planen har stoppats permanent. Publiken från det sista slutförda fasblocket förblir aktiv. Inga fler ändringar av planen tillåts. Funktionen inaktiveras inte när du avbryter planen - du måste ändra funktionsläget separat om du vill sluta använda den. |

## Se även {#see-also}

* [Skapa en automatiserad utrullning](create-automated-rollout.md)
* [Övervaka och redigera en utrullningsplan](monitor-edit-rollout-plan.md)
* [Ange en funktion som gradvis ska rulla ut](../feature-flags/set-feature-gradual-rollout.md)
