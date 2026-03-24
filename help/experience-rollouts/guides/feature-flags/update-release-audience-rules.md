---
title: Uppdatera publiceringsregler
description: Lär dig hur du konfigurerar och uppdaterar målgruppskriterier för en release i Adobe Experience Rollouts, inklusive vilka regeltyper som stöds och hur du kombinerar dem.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Uppdatera publiceringsregler {#update-release-audience-rules}

## Få åtkomst till publikinställningarna {#access}

Om du vill börja konfigurera vem som ska ta emot din release går du till målgruppsinställningarna i konsolen:

1. Öppna releasen i Experience Rollouts-konsolen.
2. Gå till fliken **Målgrupp**.
3. Aktivera växlingen bredvid **Målgruppsregler**.
4. Välj om **inkluderingsregler** ska läggas till (vem som ska få utgåvan) eller **exkluderingsregler** (vem som inte ska göra det).

## Målgruppskriterier som stöds {#criteria}

### ID-typ {#id-type}

Målanvändare baserat på deras kontotyp (till exempel personliga konton eller företagskonton).

### Land {#country}

Rikta in er mot användare baserat på deras registrerade land.

### Användar-ID {#user-id}

Ange specifika användare som deras unika användaridentifierare (GUID).

### E-postadress {#email}

Rikta användarna efter deras exakta e-postadress. Om du vill lägga till flera e-postadresser samtidigt väljer du **in** i listrutan för operatorn (i stället för **is**) och sedan:

* Ange en kommaavgränsad lista med adresser i textrutan, eller
* Överför en `.txt`-fil med en adress per rad, eller
* Överför en `.csv`-fil med adresslista

Om listan är mycket stor kan du dela upp den i mindre grupper.

### E-postdomän {#email-domain}

Ange alla användare vars e-postadress tillhör en specifik domän (till exempel `yourcompany.com`) som mål.

### Klient-IP {#client-ip}

Målanvändare baserat på deras klient-IP-adress.

### Procent {#percentage}

Rikta in er på en slumpmässig procentandel av alla användare, inklusive oautentiserade användare.

### Procent (endast autentiserad) {#percentage-auth}

Ange som mål en slumpmässig procentandel av autentiserade användare. Oautentiserade användare exkluderas.

## Kombinera flera regler {#combining-rules}

Du kan kombinera flera målgruppskriterier med hjälp av AND/OR-logik.

**Exempel:**

* Om du bara vill ha företagskonton från en viss domän som mål, kombinerar du regeln **ID-typ** med regeln **E-postdomän** med AND.
* Om du vill ange 10 % av användarna från ett visst land som mål, kombinerar du regeln **Land** med regeln **Procent**.

Använd ikonerna **+/-** för att lägga till eller ta bort villkor. Om du vill duplicera ett villkor markerar du ikonen Duplicera bredvid en befintlig regel. Aktivera **Kapslad logik** och ange ett giltigt uttryck i textrutan för komplex kapslad logik.

## Se även {#see-also}

* [Begär en release](request-a-release.md)
* [Arbetsflöde från början till slut](release-workflow-end-to-end.md)
* [Frigör lägen](release-states.md)
