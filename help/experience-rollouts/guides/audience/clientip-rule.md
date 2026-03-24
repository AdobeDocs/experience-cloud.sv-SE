---
title: Målgruppsregel med klientens IP-kontextvariabel
description: Lär dig hur du använder klientens IP-kontextvariabel i målgruppsregler i Adobe Experience Rollouts, inklusive stöd för IP-adresser, CIDR-block och nätverksintervall.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Målgruppsregel med klientens IP-kontextvariabel {#clientip-rule}

Med kontextvariabeln `clientip` kan du ange användare som mål baserat på deras klient-IP-adress. Detta är användbart för att begränsa eller aktivera funktioner som är baserade på det nätverk som användarna använder ditt program från, till exempel för att begränsa tidig åtkomst till användare i ett företagsnätverk.

## Indatatyper som stöds {#input-types}

Kontextvariabeln `clientip` har stöd för tre typer av indatavärden:

| Indatatyp | Beskrivning | Operatorer som stöds |
|---|---|---|
| **IP-adress** | En enda IPv4- eller IPv6-adress | Är, är inte lika med, i |
| **CIDR-block** | Ett intervall med IP-adresser i CIDR-notation (till exempel `192.168.1.0/24`) | Är, i, inte lika med |
| **Nätverksintervall** | Ett fördefinierat namngivet nätverksintervall som underhålls av plattformen | Är en del av |

## Lägga till en klient-IP-regel {#adding-rule}

1. Öppna funktionsflaggan, funktionsgruppen eller teamets funktionsgrupp i konsolen.
2. Gå till fliken **Målgrupp**.
3. Under **Kontext** lägger du till ett villkor med variabeln **clientip** .
4. Markera operatorn och ange värdet (IP-adress, CIDR-block eller välj ett fördefinierat nätverksintervall).

## Se även {#see-also}

* [Använd sammanhang i målgruppsregler](using-context-in-audience-rules.md)
* [Målgrupp i funktionsflaggor och funktionsgrupper](audience-in-feature-flags-and-feature-groups.md)
* [Komplexa målgruppsregler](complex-rules.md)
