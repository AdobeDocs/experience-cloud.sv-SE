---
title: Varumärke
description: Upptäck alla verktyg som finns för att hantera era varumärkesidentiteter
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: f6438303-5ae8-47c6-8c34-8e586f4b6fe7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 16%

---

# Kom igång med varumärken {#branding-gs}

>[!IMPORTANT]
>
>Varumärken kan inte skapas eller ändras av slutanvändare: dessa åtgärder måste utföras av den tekniska administratören för Adobe Campaign. Kontakta Adobes kundtjänst om du har frågor.

Alla företag har varumärkesriktlinjer som definierar både visuella element och tekniska detaljer. Adobe Campaign hjälper er att hantera dessa riktlinjer centralt, så att ni kan presentera en enhetlig varumärkesbild för era kunder i allt ni gör, från logotyper i e-postmeddelanden till URL:er och domäner som används i era kampanjer.

Tekniska administratörer kan skapa och hantera flera varumärken inom Adobe Campaign. På så sätt kan ni definiera alla element som utgör er varumärkesidentitet, inklusive logotyper och till och med inställningar för e-postspårning. När de har skapats kan dessa varumärken enkelt kopplas till era leveranser.

Du kan lägga till nya entiteter i organisationen i Campaign eller skapa en ny typ av e-post som du måste skicka under en annan underdomän. Gör så här:

1. **Konfigurera en ny underdomän** - För alla nya underdomäner som ska användas av Adobe är det första steget att konfigurera den. Du kan göra detta via [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=sv) eller kontakta din Adobe tekniska kontakt. Läs mer om underdomänskonfigurationen [på den här sidan](https://experienceleague.adobe.com/sv/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Kontrollpanelen är tillgänglig för alla administratörsanvändare. Stegen för att bevilja administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv#discover-control-panel).

1. **Skapa en leveransmall** - När det nya varumärket är tillgängligt är det bästa sättet att skapa minst en ny tom leveransmall som refererar till det nya varumärket. [Läs mer](branding-assign.md).

1. **Kontrollera leveransriktlinjer** - Innan du börjar använda den nya domänen bör du diskutera strategin med Adobe Deliverability-teamet. De hjälper dig att definiera de bästa metoderna om en ny tillhörighet ska skapas för att till exempel dela IP-adresser mellan domäner och/eller om en rampplan ska definieras.
