---
title: Analyser
description: Lär dig hur du aktiverar och använder den inbyggda kontrollpanelen för analys i Adobe Experience Rollouts för att spåra funktionsflaggans prestanda och mäta effekten av utrullningen.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analyser {#analytics}

Experience Rollouts innehåller inbyggda analysfunktioner för funktionsflaggor, funktionsgrupper, teamöverskridande funktionsgrupper och releaser. Använd kontrollpanelen för analyser för att förstå hur många användare som deltar i utrullningen och hur varianten och kontrollgrupperna jämför.

## Aktivera analys {#enable}

Analyser måste aktiveras på två nivåer:

1. **Programnivå** - Kontakta Experience Rollouts-stöd för att aktivera analyser för ditt program.
2. **Funktionsflaggnivå** - När analyser har aktiverats för programmet markerar du kryssrutan **Aktivera analys** på fliken **Grundläggande information** för varje funktionsflagga som du vill spåra.

>[!NOTE]
>
>Analyser kan aktiveras för upp till 20 funktionsflaggor per program som standard. Kontakta supporten om du behöver höja denna gräns.

## Visa kontrollpanelen för analyser {#dashboard}

När analysen är aktiverad kommer alla funktionsflaggor, funktionsgrupper och releaser för programmet att börja spåra data. Gå till instrumentpanelen genom att välja **Resultat** på den funktionsflagga, funktionsgrupp eller release som du vill analysera.

Kontrollpanelen visar:

* **Deltagare** - Totalt antal användare som är kvalificerade för funktionen (variant + kontrollgrupp kombinerat)
* **Kontrollgrupp** - Antal användare som har tilldelats kontrollgruppen (användare som har fått standardupplevelsen)
* **Diagram på dagnivå** - Dagliga linjediagram som visar registrering i varianten och kontrollgruppen över tiden. Markörer visar när konfigurationen för funktionsflaggan uppdaterades
* **Analys på variantnivå** - ackumulerat antal användare som är registrerade i kontrollgruppen och varje variant

För funktionsgrupper och releaser väljer du listrutan **Resultat** för att välja ett program och visa analyser för det programmet. Analyser är bara tillgängligt för program som har det aktiverat.

## Se även {#see-also}

* [Skapa din första funktionsflagga](create-your-first-feature-flag.md)
* [A/B-testning med funktionsflaggor](a-b-testing.md)
* [Skapa en funktionsgrupp](create-a-feature-group.md)
