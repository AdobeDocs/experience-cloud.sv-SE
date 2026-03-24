---
title: Vanliga frågor om versionshantering
description: Hitta svar på vanliga frågor om versionshantering i Adobe Experience Rollouts.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Vanliga frågor om versionshantering {#release-management-faqs}

## Hur begär jag en release? {#request-release}

Se [Begär en release](request-a-release.md) för den fullständiga processen och den information du behöver ange.

## Vilka målgruppskriterier stöds för releaser? {#audience-criteria}

Releaser har stöd för följande målgruppsregler:

* ID-typ (kontotyp)
* Land
* Användar-ID (GUID)
* E-postadress (individuell lista eller grupplista)
* E-postdomän
* Klient-IP
* Procent (alla användare)
* Procent (endast autentiserade användare)

Du kan kombinera flera regler med AND/OR-logik, inklusive kapslade villkor. Mer information finns i [Uppdatera målgruppsregler för releaser](update-release-audience-rules.md) för steg-för-steg-konfigurationsinstruktioner.

## Hur lägger jag till ett program i en release? {#onboard-application}

När releasen har skapats öppnar du den i konsolen och lägger till programmet i versionskonfigurationen. Ägaren av produktreleasen för respektive program kan sedan lägga till relevanta funktionsflaggor. Se [Frigör arbetsflöde från början till slut](release-workflow-end-to-end.md) för hela sekvensen.

## En funktion returneras inte för en användare som ska kvalificera sig. Hur felsöker jag? {#troubleshoot}

Följ de här stegen för att felsöka:

1. **Kontrollera frisläppningstillståndet.** Versionen måste vara i läget **Publicerad** eller **Fullständig utrullning** för att fungera med funktioner. Se [Frigör lägen](release-states.md).
2. **Kontrollera program- och funktionsflaggan.** Kontrollera att funktionsflaggan har skapats för rätt program och att programmet är associerat med rätt version.
3. **Kontrollera att funktionsflaggan är aktiverad.** En inaktiverad flagga visas inte även om den är aktiv.
4. **Granska målgruppsvillkoren.** Bekräfta att användaren uppfyller alla villkor som definieras i målgruppsreglerna. Dubbelkontrollera villkoren för den specifika versionen som funktionen är kopplad till.

## Se även {#see-also}

* [Begär en release](request-a-release.md)
* [Uppdatera publiceringsregler](update-release-audience-rules.md)
* [Frigör lägen](release-states.md)
* [Arbetsflöde från början till slut](release-workflow-end-to-end.md)
