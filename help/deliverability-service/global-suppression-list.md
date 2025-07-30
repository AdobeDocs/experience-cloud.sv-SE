---
title: Global undertryckningslista
description: Upptäck den globala listan över inaktiveringar
hide: true
exl-id: 40aef987-52a3-470b-88ca-c716a116bdfc
source-git-commit: 9d12eece2ca9f8f36951f8575bb0ac42bc10a728
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Global undertryckningslista {#global-suppression-list}

En inaktiveringslista består av e-postadresser som kunderna vill utesluta från leveranser, eftersom det kan skada deras sändningsrykte och leveransfrekvenser om de skickar till dessa kontakter. För närvarande håller Adobe en uppdaterad lista över kända dåliga e-postadresser som har visat sig vara skadliga för engagemanget och utskickets anseende och ser till att e-post inte skickas till dem. Listan hanteras i en global undertryckningslista som är gemensam för alla Adobe-kunder. Adresserna och domännamnen som finns i den globala undertryckningslistan är dolda. Endast antalet uteslutna mottagare anges i leveransrapporterna.

Nu går det att hantera den globala undertryckningslistan från ett gränssnitt som är tillgängligt internt. Denna lista kommer endast att underhållas av leveranskonsulter. Den globala undertryckningslistan kan innehålla e-postadresser eller domänadresser.

## Åtkomst till den globala listan över inaktiveringar

Gå till **[!UICONTROL Gloabl suppression list]** om du vill få tillgång till den detaljerade listan över undantagna e-postadresser och domäner.

>[!CAUTION]
>
>Behörigheter att visa, exportera och hantera den globala undertryckningslistan beror på den distributionslista som du har tilldelats. Läs mer

Två flikar visas: **[!UICONTROL Email]** och **[!UICONTROL Domain]**.

Det finns filter som du kan använda för att bläddra igenom listan.

## Lägga till adresser och domäner

Det finns för närvarande två sätt som adresser läggs till i den globala listan över undertryckningar:

* Lista strukturerad av leveransgruppen.
* Lista från tredjeparts tjänsteleverantör Blackbox.

Du kan lägga till e-postadresser eller domäner [en i taget](#add-one-address-or-domain), eller [i gruppläge](#upload-csv-file) via en CSV-filöverföring.

Det gör du genom att markera knappen **[!UICONTROL Add email or domain]** och sedan följa en av metoderna nedan.

### Lägg till en adress eller domän {#add-one-address-or-domain}

1. Välj alternativet **[!UICONTROL One by one]**.

1. Välj adresstypen: **[!UICONTROL Email address]** eller **[!UICONTROL Domain address]**.

1. Ange den e-postadress eller domän som du vill utesluta från sändningen.

   >[!NOTE]
   >
   >Se till att du anger en giltig e-postadress (till exempel abc@company.com) eller domän (till exempel abc.company.com).

1. Ange en orsak om det behövs.

   >[!NOTE]
   >
   >Alla ASCII-utskrivbara tecken mellan 32 och 126 är tillåtna i det här fältet. Den fullständiga listan finns till exempel på [den här sidan](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}.

1. Klicka på **[!UICONTROL Submit]** för att bekräfta.

### Överföra en CSV-fil {#upload-csv-file}

1. Välj alternativet **[!UICONTROL Upload CSV]**.

1. Ladda ned CSV-mallen som ska användas, som innehåller kolumnerna och formatet nedan:

   ```
   TYPE,VALUE,COMMENT
   EMAIL,abc@somedomain.com,Comment
   DOMAIN,somedomain.com,Comment
   ```

   >[!CAUTION]
   >
   >Ändra inte namnen på kolumnerna i CSV-mallen.
   >
   >Filstorleken får inte överstiga 1 MB.

1. Fyll i CSV-mallen med de e-postadresser och/eller domäner som du vill lägga till i listan över inaktiveringar.

   >[!NOTE]
   >
   >Alla ASCII-tecken mellan 32 och 126 tillåts i kolumnen **Kommentar**. Den fullständiga listan finns till exempel på [den här sidan](https://en.wikipedia.org/wiki/Wikipedia:ASCII#ASCII_printable_characters){target="_blank"}.

1. När du är klar drar och släpper du CSV-filen och klickar sedan på **[!UICONTROL Submit]** för att bekräfta.

>[!NOTE]
>
>När överföringen är klar kontrollerar du att den lyckades genom att kontrollera dess status från gränssnittet. [Lär dig hur](#recent-uploads)

### Kontrollera status för senaste överföringar {#recent-uploads}

Klicka på knappen **[!UICONTROL Recent uploads]** om du vill kontrollera statusen för de senaste CSV-filerna som du har överfört.

Möjliga statusar är:

* **[!UICONTROL Pending]**: Filöverföringen bearbetas.
* **[!UICONTROL Error]**: Filöverföringen misslyckades på grund av ett tekniskt fel eller ett filformatsfel.
* **[!UICONTROL Complete]**: Filöverföringen har slutförts.

Om vissa adresser inte har rätt format läggs de inte till i den globala listan över undertryckningar under överföringen.

När överföringen är klar kopplas den då till en rapport. Du kan hämta den för att kontrollera de fel som påträffats.

## Ta bort adresser

Använd knappen **[!UICONTROL Delete]** om du vill ta bort en adress från den globala listan.

>[!CAUTION]
>
>Adresser eller domäner som läggs till automatiskt av tredjeparts tjänsteleverantör Blackbox kan inte tas bort av konsulter via gränssnittet. Detta kan endast göras via en backend-biljett.
