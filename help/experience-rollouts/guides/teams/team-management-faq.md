---
title: Vanliga frågor om teamhantering
description: Hitta svar på vanliga frågor om att hantera team, medlemmar och roller i Adobe Experience Rollouts.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Vanliga frågor om teamhantering {#team-management-faq}

## Jag försöker lägga till en användare, men sökningen returnerar inga resultat {#user-not-found}

Detta kan inträffa i scenmiljön om användaren aldrig har loggat in på scenen tidigare. Lös detta genom att be användaren att logga in på scenkonsolen minst en gång för att skapa sitt konto i Stage-identitetssystemet. När de har loggat in kan du försöka söka efter dem igen.

## Jag är administratör men jag kan inte skapa eller redigera funktionsflaggor {#admin-cannot-edit-flags}

Roller i upplevelseutrullningar utesluter varandra. Rollen **Admin** ger teamhanteringsbehörigheter men inkluderar inte behörigheterna för en **produktversionsägare**. För att kunna skapa och redigera funktionsflaggor måste en medlem ha rollen **Product Release Owner** förutom rollen **Admin**.

Kontakta teamadministratören om du vill ha ytterligare roller tilldelade. I [Användarroller](user-roles.md) finns en fullständig beskrivning av vad varje roll kan göra.

## Har administratörer en hierarki? Kan en administratör åsidosätta en annan? {#admin-hierarchy}

Nej. Team i Experience Rollouts har en platt struktur. Alla medlemmar med rollen **Admin** har samma behörigheter och kan hantera varandras konfigurationer. Det finns inget hierarkiskt godkännandearbetsflöde mellan administratörer.

## Hur tar jag bort en medlem från mitt team? {#remove-member}

Medlemmar tas bort via åtkomsthanteringssystemet. Som administratör kan du söka efter medlemmens åtkomstpost för ditt team och återkalla deras roll. Om du är osäker på hur du ska göra detta kontaktar du din organisations åtkomsthanteringsteam.

## Kan en medlem ha mer än en roll? {#multiple-roles}

Ja. Tilldela flera roller till en medlem när deras ansvarsområden omfattar mer än en funktion. En teammedlem som både hanterar teamet och skapar funktionsflaggor bör till exempel ha rollerna **Admin** och **Product Release Owner**.

## Se även {#see-also}

* [Användarroller](user-roles.md)
* [Lägg till medlemmar i ditt team](add-team-members.md)
* [Hantera team](manage-teams.md)
