---
title: Vanliga frågor om versionshantering
description: Hitta svar på vanliga frågor om versionshantering i Adobe Experience Rollouts.
exl-id: 802b99bd-85ee-4f4d-afca-88d1297f8782
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Vanliga frågor om versionshantering {#release-management-faqs}

## Hur begär jag en release? {#request-release}

Kontakta Experience Rollouts support för att begära en release. Ange teamnamn, programinformation, målgrupp och önskad tidslinje för utrullning.

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

Du kan kombinera flera regler med AND/OR-logik, inklusive kapslade villkor.

## Hur lägger jag till ett program i en release? {#onboard-application}

När releasen har skapats öppnar du den i konsolen och lägger till programmet i versionskonfigurationen. Ägaren av produktreleasen för respektive program kan sedan lägga till relevanta funktionsflaggor.

## En funktion returneras inte för en användare som ska kvalificera sig. Hur felsöker jag? {#troubleshoot}

Följ de här stegen för att felsöka:

1. **Kontrollera frisläppningstillståndet.** Versionen måste vara i läget **Publicerad** eller **Fullständig utrullning** för att fungera med funktioner.
2. **Kontrollera program- och funktionsflaggan.** Kontrollera att funktionsflaggan har skapats för rätt program och att programmet är associerat med rätt version.
3. **Kontrollera att funktionsflaggan är aktiverad.** En inaktiverad flagga visas inte även om den är aktiv.
4. **Granska målgruppsvillkoren.** Bekräfta att användaren uppfyller alla villkor som definieras i målgruppsreglerna. Dubbelkontrollera villkoren för den specifika versionen som funktionen är kopplad till.

## Se även {#see-also}

* [Kontakta support](../support/contact-support.md)
