---
title: Begär en release
description: Lär dig hur du begär en ny samordnad release i Adobe Experience Rollouts och vilken information som ska tillhandahållas.
exl-id: 8eee84b2-fbd5-4713-90ac-92fd7b74c163
source-git-commit: f4c365e1a0e61ba3dec298dfa8ab0d9e74e1259a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Begär en release {#request-a-release}

## Förutsättningar {#prerequisites}

* Du har rollen **Versionshanteraren** - se <!-- broken link[User roles](../teams/user-roles.md) -->
* Ditt program är introducerat - se [Ansluta ditt program](../applications/onboard-your-application.md)

>[!TIP]
>
>Granska <!--[Releases and cross-team feature groups](releases-and-cross-team-feature-groups.md)--> innan du begär en release. En funktionsgrupp för flera team kan tillgodose dina behov med mindre omkostnader - den är självbetjäning och stöder en mer omfattande målgruppsanpassning.

## Skicka en supportförfrågan {#submit}

Att skapa releaser är inte självbetjäning. Kontakta Experience Rollouts support för att begära en ny release. Ange följande information:

| Fält | Beskrivning |
|---|---|
| **Namn** | Ett unikt namn för releasen. Ta inte med blanksteg i releasenamnet. |
| **Team** | Teamet som äger releasen. |
| **Miljö** | Den miljö där releasen ska skapas (scen eller produktion). |
| **Mål** | En kort beskrivning av vad den här versionen kommer att lansera och varför. |
| **Program** | Det eller de program som ska ingå i releasen. |
| **Varaktighet** | Hur länge du vill att releasen ska vara aktiv. Utgåvorna förväntas vara stängda eller baselerade inom tre månader. Ange en affärsjustering om du behöver längre. |

>[!NOTE]
>
>Antalet aktiva releaser vid en given tidpunkt är begränsat. Planera att basera eller stänga releasen inom tre månader för att frigöra kapacitet för andra team.

## När releasen har skapats {#after}

När du har fått en bekräftelse på att releasen har skapats loggar du in på konsolen och slutför versionskonfigurationen. Se [Frigör arbetsflöde från början till slut](release-workflow-end-to-end.md) för hela stegsekvensen.

## Se även {#see-also}

* [Arbetsflöde från början till slut](release-workflow-end-to-end.md)
* [Uppdatera publiceringsregler](update-release-audience-rules.md)
* [Frigör lägen](release-states.md)
