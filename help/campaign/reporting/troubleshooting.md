---
title: Felsökning av dynamisk rapportering
description: Här finns vanliga frågor om dynamisk rapportering.
audience: end-user
level: Intermediate
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: a58fc8fd-e510-45ef-8fe9-c75ff4498113
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 1%

---

# Felsökning{#troubleshooting}

I det här avsnittet finns vanliga frågor om dynamisk rapportering.

## För Unika öppningar och Unika klick matchar inte antalet i den sammanställda raden dem i enskilda rader {#unique-open-clicks-no-match}

Detta är ett förväntat beteende.
Vi kan ta följande exempel för att förklara det här beteendet.

Ett e-postmeddelande skickas till profilerna P1 och P2.

P1 öppnar e-postmeddelandet två gånger den första dagen och sedan tre gånger den andra dagen.

P2 öppnar e-postmeddelandet en gång den första dagen och öppnar det inte igen de följande dagarna.
Här visas en visuell representation av profilernas interaktion med det skickade e-postmeddelandet:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Dag</strong> <br/> </th> 
   <th align="center"> <strong>Öppnar</strong> <br/> </th> 
   <th align="center"> <strong>Unika öppningar</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> Dag 1<br/> </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> Dag 2<br/> </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

För att förstå det totala antalet unika öppningar måste vi summera antalet rader på **[!UICONTROL Unique Opens]** som ger oss värdet 3. Men eftersom e-postmeddelandet endast var avsett för två profiler bör den öppna frekvensen vara 150 %.

Om du inte vill få ett procentvärde som är högre än 100 behålls definitionen för **[!UICONTROL Unique Opens]** som antalet unika utskicksloggar som öppnats. Även om P1 öppnade e-postmeddelandet dag 1 och dag 2 är deras unika öppningar fortfarande 1.

Detta resulterar i följande tabell:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>Öppnar</strong> <br/> </th> 
   <th align="center"> <strong>Unika öppningar</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong> dag </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Dag 1<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Dag 2<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Unika antal baseras på en HLL-baserad skiss, vilket kan orsaka små defekter vid stora antal.

## Antalet öppna stämmer inte med antalet databaser {#open-counts-no-match-database}

Detta kan bero på att heuristik används i dynamisk rapportering för att spåra öppningar även när vi inte kan spåra åtgärden **[!UICONTROL Open]**.

Om en användare till exempel har inaktiverat bilder på sin klient och klickar på en länk i e-postmeddelandet, kanske inte **[!UICONTROL Open]** spåras av databasen, men **[!UICONTROL Click]** kommer att spåras.

Därför har **[!UICONTROL Open]**-spårningsloggarnas antal kanske inte samma antal i databasen.

Sådana förekomster läggs till som **&quot;ett e-postklick innebär att ett e-postmeddelande öppnas&quot;**.

>[!NOTE]
>
>Eftersom antalet är unikt och bygger på en HLL-baserad skiss, kan mindre avvikelser mellan antalet uppstå.

## Hur beräknas antalet återkommande/transaktionsbaserade leveranser? {#counts-recurring-deliveries}

Vid arbete med återkommande och transaktionsrelaterade leveranser tillskrivs antalet både överordnade och underordnade leveranser.
Vi kan ta ett exempel på en återkommande leverans med namnet **R1** som ska köras varje dag på dag 1 (RC1), dag 2 (RC2) och dag 3 (RC3).
Låt oss anta att bara en person har öppnat alla underordnade leveranser flera gånger. I det här fallet visas antalet **[!UICONTROL Open]** som 1 för varje enskild återkommande underordnad leverans.
Eftersom samma person klickade på alla leveranser kommer den överordnade återkommande leveransen också att ha **[!UICONTROL Unique open]** som 1.

Rapporterna ska se ut så här:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Leverans</strong> <br/> </th> 
   <th align="center"> <strong>Skickat</strong> <br/> </th> 
   <th align="center"> <strong>Levererat</strong> <br/> </th>
   <th align="center"> <strong>Öppnar</strong> <br/> </th> 
   <th align="center"> <strong>Unika öppningar</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Vad betyder färgerna i min rapporttabell? {#reports-color-signification}

Färger som visas i dina rapporter är slumpmässiga och kan inte anpassas. De representerar en förloppsindikator och visas för att hjälpa dig att bättre lyfta fram det högsta värdet som nås i dina rapporter.

I exemplet nedan har cellen samma färg eftersom värdet är 100 %.

![](assets/troubleshooting_1.png)

Om du ändrar **[!UICONTROL Conditional formatting]** till anpassad blir cellen grönare när värdet når den övre gränsen. Om den når den undre gränsen blir den rödare.

Här anger vi till exempel **[!UICONTROL Upper limit]** till 500 och **[!UICONTROL Lower limit]** till 0.

![](assets/troubleshooting_2.png)

## Varför visas värdet N/A i mina rapporter?

![](assets/troubleshooting_3.png)

Värdet **N/A** kan ibland visas i dina dynamiska rapporter. Det här kan visas av tre anledningar:

* Leveransen har tagits bort och visas här som **N/A** för att inte orsaka diskrepans i resultaten.
* När du drar och släpper dimensionen **[!UICONTROL Transactional Delivery]** till dina rapporter kan värdet **N/A** visas som ett resultat. Det beror på att Dynamic Report hämtar alla leveranser även om de inte är transaktionsbaserade. Detta kan också inträffa när du drar och släpper dimensionen **[!UICONTROL Delivery]** i rapporten, men i det här fallet representerar värdet **N/A** transaktionsleveranser.
* När en dimension används med ett mått som inte är relaterat till dimensionen. I exemplet nedan har en uppdelning lagts till med dimensionen **[!UICONTROL Tracking URL]** trots att antalet **[!UICONTROL Click]** har angetts till 0 i den här leveransen.

  ![](assets/troubleshooting_4.png)

## Leveransrapporter visar ofullständiga data när anpassad målmappning används

Om du använder importerade anpassade målmappningar i leveranser och inga data visas i de olika rapporterna, kan det betyda att rapportmappningarna inte skapades för dessa målmappningar.

Så här löser du det:

* När du har importerat målmappningen från en XML-fil måste du också importera rapportanrikningen.

* I stället för att importera målmappningen kan du skapa den direkt i Adobe Campaign webbanvändargränssnitt, som automatiskt skapar rapportanrikningen.

## Skillnad mellan kolumnrubrikens nummer och summan av raderna

Skillnaden mellan kolumnrubriksnumret och summan av alla rader förväntas i följande fall:

* **Unika mått**: Om du använder unika mått kan det totala antalet som visas i rubriken ändras, eftersom det baseras på mottagar-ID:n i stället för på en enkel summa radantal. Följaktligen kan en enda profil utlösa flera händelser i olika dimensioner, vilket leder till flera rader i datauppsättningen. I sidhuvudet räknas dock varje profil bara en gång.

  Exempel:

   * Om en profil A öppnar ett e-postmeddelande på tre olika dagar visas A på tre rader per dag, men A räknas som 1 i rubriken.

   * Om profil A klickar på tre olika länkar i ett e-postmeddelande samma dag visas A på tre rader vid nedbrytning per URL, men i rubriken räknas A som 1. Detsamma gäller för uppdelningar per enhet och webbläsare.

* **Open Metrics**: Antalet Open Metrics (Öppna mått) bestäms genom att totalen för både de faktiska Open-händelserna och de unika klickhändelserna (per mottagar-ID) samlas, exklusive de fall där en open-händelse inte har inträffat sedan en e-postlänk inte kan klickas utan en open-händelse.

  Exempel:

   * När profil A öppnar ett spårat e-postmeddelande (med URL U1) registreras det som en open-händelse med URL:en angiven som null. När du klickar på U1 skapas en klickningshändelse senare. Även om A:s klickning på U1 räknas som en öppen händelse finns det ingen specifik öppen händelse för U1. A räknas därför bara en gång i det unika antalet öppna.

   * En profil R öppnar ett e-postmeddelande dag 1, registrerar en öppen händelse och klickar på en länk. Under de kommande två dagarna öppnar R e-postmeddelandet igen och klickar på länken igen, vilket genererar en klickhändelse varje dag. R:s engagemang spåras dagligen i Open-numret, men R räknas bara en gång i kolumnrubriken, med fokus på unika åtaganden.

* **Negerad händelse**: I rapporter betyder negerad händelse leveransförsök som ursprungligen markerades som lyckade men som misslyckades efter återförsök. Dessa indikeras av antalet -1. För att undvika missförstånd exkluderas dessa negativa tal från de leveranspått som visas. Det innebär att summan av alla rader för leveransmåttet kanske inte matchar kolumnrubriknumret.
