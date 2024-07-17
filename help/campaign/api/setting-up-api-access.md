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
source-git-commit: 18979fea28f4f3adce1139293203a59876831313
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 27%

---

# Konfigurera API-åtkomst {#setting-up-api-access}

Adobe Campaign Standard API-åtkomst konfigureras enligt stegen nedan. Var och en av dessa steg beskrivs i [Adobe Developer-dokumentationen](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Om du vill hantera certifikat i [Adobe Developer](https://developer.adobe.com/) måste du ha **systemadministratörsbehörighet** i organisationen eller ett [utvecklarkonto](https://helpx.adobe.com/se/enterprise/using/manage-developers.html) i Admin Console.

1. **Kontrollera att du har ett digitalt certifikat** eller skapa ett vid behov. De offentliga och privata nycklarna som tillhandahålls med certifikatet behövs i följande steg.
1. **Skapa en ny integrering av Adobe Campaign-tjänsten** i [Adobe Developer](https://developer.adobe.com/) och konfigurera den. Dina autentiseringsuppgifter genereras sedan (API-nyckel, klienthemlighet ...).
1. **Skapa en OAuth Server-till-Server**-autentiseringsuppgift genom att följa dessa [implementeringssteg](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

   >[!IMPORTANT]
   >
   >JWT (JSON Web Tokens) håller på att tas ur bruk och ersätts med OAuth. Övergången genomförs stegvis inom ramen för Campaigns kommande releaser. JWT-autentiseringsuppgifterna (Service Account) har markerats som inaktuella och fortsätter att fungera till och med 27 januari 2025. Därför måste du migrera programmet eller integreringen för att använda de nya autentiseringsuppgifterna för OAuth Server-till-Server före 27 januari 2025. OAuth-autentisering rekommenderas. Du hittar alla element som ska migreras från JWT-autentisering till OAuth-autentisering på dessa sidor:
   >* [Migrering](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementering](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Vanliga frågor om JWT-borttagning](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

För att upprätta en säker tjänst-till-tjänst Adobe I/O API-session måste varje begäran till en Adobe-tjänst innehålla informationen nedan i auktoriseringshuvudet.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;ORGANISATION>**: Detta är ditt personliga organisations-ID, och Adobe tillhandahåller ett ORGANISATIONS-ID för var och en av dina instanser:

   * &lt;ORGANIZATION> : din produktionsinstans,
   * &lt;ORGANIZATION-mkt-stage>: din sceninstans.

  Kontakta din administratör eller din teknikkunniga Adobe-kontakt för att få ditt organisations-ID-värde. Du kan även hämta den till Adobe I/O när du skapar en ny integrering i licenslistan (se <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Adobe Developer-dokumentationen</a>).

* **&lt;ACCESS_TOKEN>**: Din personliga åtkomsttoken, som hämtades när du bytte din JSON-webbtoken via en POST.

* **&lt;API_KEY>**: Din egen API-nyckel. Det tillhandahålls i Adobe I/O efter att en ny integrering med Adobe Campaign Service har skapats.

  ![Alt-text](assets/tenant.png)

## Felsökning

Om följande fel uppstår under AdobeIO-integreringen:

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Kontakta administratören eller den tekniska kontaktpersonen på Adobe för att kontrollera om CNAME-parametern har skapats på rätt sätt.
