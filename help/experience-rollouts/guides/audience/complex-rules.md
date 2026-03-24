---
title: Komplexa målgruppsregler
description: Lär dig hur du arbetar med stora eller komplexa målgruppsregler i Adobe Experience Rollouts, inklusive massvärdegränser och hur du delar upp regler över flera villkor.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# Komplexa målgruppsregler {#complex-rules}

## Gränser för massvärde {#bulk-value-limits}

När du lägger till ett stort antal värden i en målgruppsregel - till exempel en lång lista med e-postadresser - kan du få ett felmeddelande om att regeln har överskridit den tillåtna maxstorleken.

Varje målgruppsregel har en storleksgräns per attribut. För e-postadresser beror gränsen på posternas totala teckenlängd i stället för på ett fast antal. Som en allmän riktlinje bör du använda ungefär **100-115 e-postadresser per regel**.

Om du behöver ange fler poster som mål än vad som tillåts enligt den här gränsen kan du dela upp listan i mindre segment och använda dem som separata ELLER-anslutna villkor med hjälp av kapslad logik.

## Använda kapslad logik för komplexa regler {#nested-logic}

Med kapslad logik kan du kombinera flera målgruppsvillkor med exakt OCH/ELLER-kontroll. Så här aktiverar du den:

1. Lägg till de målgruppsvillkor ni behöver.
2. Aktivera **kapslad logik** i målgruppsregelavsnittet.
3. Varje villkor tilldelas ett tal. Ange ett logiskt uttryck som refererar till dessa tal, till exempel:
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

Detta är samma mekanism som används för procentregler i kombination med andra kriterier. Se [Lägg till procentregler i målgruppskriterier](adding-percentage-rules.md) för fungerande exempel.

## Se även {#see-also}

* [Målgrupp i funktionsflaggor och funktionsgrupper](audience-in-feature-flags-and-feature-groups.md)
* [Lägg till procentregler i målgruppskriterier](adding-percentage-rules.md)
* [Uppdatera publiceringsregler](../feature-flags/update-release-audience-rules.md)
