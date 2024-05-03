---
title: Konfigurera API-åtkomst
description: Lär dig hur du ställer in åtkomst till Campaign Standards-API:er.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: efbbd0cd-9c56-4ad0-8bcb-efba4b63c28b
source-git-commit: 3e7af8a9ba41ab54738fff2f69388595041a8574
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 30%

---

# Konfigurera API-åtkomst {#setting-up-api-access}

Adobe Campaign Standard API-åtkomst konfigureras enligt stegen nedan. Varje steg beskrivs i [Adobe Developer-dokumentation](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Hantera certifikat i [Adobe Developer](https://developer.adobe.com/), kontrollera att du har **Systemadministratör** rättigheter till organisationen eller [utvecklarkonto](https://helpx.adobe.com/se/enterprise/using/manage-developers.html) i Admin Console.

1. **Kontrollera att du har ett digitalt certifikat** eller skapa ett vid behov. De offentliga och privata nycklarna som tillhandahålls med certifikatet behövs i följande steg.
1. **Skapa en ny integrering av Adobe Campaign Service** in [Adobe Developer](https://developer.adobe.com/) och konfigurera det. Dina autentiseringsuppgifter genereras sedan (API-nyckel, klienthemlighet ...).
1. **Skapa en JSON-webbtoken (JWT)** från de inloggningsuppgifter som tidigare genererats och signera den med din privata nyckel. JWT kodar all identitets- och säkerhetsinformation som Adobe behöver för att verifiera din identitet och ge dig åtkomst till API:t.

   >[!IMPORTANT]
   >
   >JWT (JSON Web Tokens) håller på att tas ur bruk och ersätts med OAuth. Övergången genomförs stegvis inom ramen för Campaigns kommande releaser. JWT-autentiseringsuppgifterna (Service Account) har markerats som inaktuella och fortsätter att fungera till och med 27 januari 2025. Därför måste du migrera programmet eller integreringen för att använda de nya autentiseringsuppgifterna för OAuth Server-till-Server före 27 januari 2025. OAuth-autentisering rekommenderas. Du hittar alla element som ska migreras från JWT-autentisering till OAuth-autentisering på dessa sidor:
   >* [Migrering](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementering](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Vanliga frågor om JWT-borttagning](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

1. **Byt ut din JWT mot en åtkomsttoken** genom en begäran om POST. Denna åtkomsttoken måste användas i varje rubrik för dina API-begäranden.

För att upprätta en säker tjänst-till-tjänst Adobe I/O API-session måste varje begäran till en Adobe-tjänst innehålla informationen nedan i auktoriseringshuvudet.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;organization>**: Detta är ditt personliga organisations-ID, och Adobe tillhandahåller ett organisations-ID för var och en av dina instanser:

   * &lt;organization> : din produktionsinstans,
   * &lt;organization-mkt-stage>: din sceninstans.

  Kontakta din administratör eller din teknikkunniga Adobe-kontakt för att få ditt organisations-ID-värde. Du kan även hämta den till Adobe I/O när du skapar en ny integrering i licenslistan (se <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Adobe Developer-dokumentation</a>).

* **&lt;access_token>**: Din personliga åtkomsttoken, som hämtades när din JSON-webbtoken byttes ut via en POST.

* **&lt;API_KEY>**: Din egen API-nyckel. Det tillhandahålls i Adobe I/O efter att en ny integrering med Adobe Campaign Service har skapats.

  ![alt-text](assets/tenant.png)

## Felsökning

Om följande fel uppstår under AdobeIO-integreringen:

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Kontakta administratören eller den tekniska kontaktpersonen på Adobe för att kontrollera om CNAME-parametern har skapats på rätt sätt.
