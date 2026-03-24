---
title: Felsökning
description: Använd workbench Experience Rollouts för att diagnostisera problem med utvärdering av funktionsflaggor för specifika användare, inklusive att kontrollera vilka funktioner som är aktiverade, inaktiverade eller omatchade för en viss användaridentitet.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# Felsökning {#troubleshooting}

Upplevelseutrullningar innehåller ett inbyggt diagnostikverktyg som kallas **Funktioner Workbench** som hjälper dig att förstå exakt vilka funktionsflaggor en viss användare får och varför. Använd den för att ta reda på rapporter om oväntade funktioner utan att behöva återge kodproblem.

## Öppna Funktioner i Workbench {#access-workbench}

Så här öppnar du Funktioner i Workbench:

1. Logga in på Experience Rollouts-konsolen.
2. Navigera till **Workbench > Slutanvändare** på den övre menyn.
3. Välj fliken **Funktioner**.

## Ange en användaridentitet {#input-identity}

Om du vill söka efter funktionsflaggor för en viss användare anger du följande information i workbench-formuläret:

* **ID-typ** - Välj den typ av identifierare som du använder. De typer som stöds är e-post, GUID och besökar-ID. Du kan också ange en **versionsflagga** direkt för att se vilka releaser som aktiverats för en användare baserat på deras flaggvärde.
* **ID-värde** - Ange användarens identifierare. Om du väljer e-post som ID-typ bör du tänka på att flera GUID kan kopplas till samma e-postadress. En GUID-listruta tillhandahålls så att du kan växla mellan associerade GUID:n.
* **Autentiseringskälltyp** - Välj om det är tillämpligt för din integrering.
* **Kontextvariabler** - Ange valfritt nyckelvärdepar som påverkar utvärderingen av målgruppsregler (till exempel land, enhetstyp).
* **Team och program** - Välj det team och program som du vill hämta funktionsflaggor för. Ditt nuvarande team och ett av dess program är förvalda som standard.

När du har fyllt i formuläret väljer du **Hämta funktioner**.

## Tolka resultaten {#interpret-results}

Resultatet beror på vilken ID-typ du angav.

### E-post- eller GUID-sökning {#email-guid-lookup}

När du söker efter en användare via e-post eller GUID visas två avsnitt i resultatet:

**Versionsflaggor**

I det här avsnittet visas tre listor för det valda teamet och programmet:

* **Aktiverad** - Versioner som för närvarande är aktiva för den här användaren.
* **Inaktiverad** - Versioner som finns men som inte har aktiverats för den här användaren.
* **Oanvänd** - Frigör bitar som inte är kopplade till sig.

Releaser som är associerade med det valda teamet och programmet visas högst upp i varje lista.

**Funktionsflaggor och grupper**

I det här avsnittet visas alla funktionsflaggor för det valda teamet och det valda programmet som är aktiverade för användaren. Varje tävlingsbidrag innehåller:

* Nyckel och namn för funktionsflagga
* Funktionsgrupp (om flaggan tillhör en)
* Variant (om A/B-testning är konfigurerad)
* Om flaggan är publiklänkad

Du kan också välja **Visa begäran/svar** för att undersöka exakt vilken API-begäran och vilket svar som gav resultatet.

### Icke-självmejl eller icke-GUID {#non-self-lookup}

När den e-postadress som du har angett inte är din egen, eller när en annan typ av ID än GUID används, visas endast avsnittet **Funktionsflaggor och grupper**.

### Sökning efter versionsflagga {#release-flag-lookup}

När du anger en **versionsflagga** som ID-typ visas endast avsnittet **Releasflaggor** med en lista över vilka versioner som aktiverats och inaktiverats för användaren som är associerad med den flaggan.

## Vanliga problem {#common-issues}

I följande tabell beskrivs vanliga problem och hur du undersöker dem med hjälp av workbench.

| Symptom | Vad du ska kontrollera |
|---|---|
| Användaren får ingen funktionsflagga som han/hon bör | Verifiera teamet och programurvalet. Kontrollera att användarens ID matchar målgruppsregeltypen (e-post, GUID osv.). Bekräfta att funktionen är i läget **Publicera** eller **Hel utrullning**. |
| Funktionen är oväntat aktiverad för alla användare | Bekräfta att funktionen inte har några målgruppsregler eller att procentandelen är inställd på 100 %. Kontrollera om funktionen är i läget **Fullständig utrullning**. |
| Målgruppsregeln matchar inte | Använd workbench med kontextvariabler för att bekräfta att värdena som skickas vid körningen matchar det som är konfigurerat i målgruppsregeln. |
| Funktionsflaggans tillstånd är korrekt, men användaren ser fortfarande gammalt beteende | Kontrollera den TTL som har konfigurerats för programmet. SDK cachelagrar funktionsdata och uppdateras endast vid det konfigurerade avsökningsintervallet. |

## Se även {#see-also}

* [Få support](get-support.md)
* [Kontakta support](contact-support.md)
* [Uppdatera publiceringsregler](../feature-flags/update-release-audience-rules.md)
* [Frigör lägen](../feature-flags/release-states.md)
