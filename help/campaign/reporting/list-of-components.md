---
title: Lista över komponenter
description: Här finns en lista med alla komponenter som finns i     Dynamiska rapporter och definitioner.
level: Beginner
audience: end-user
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 5c58db92-7878-4c70-b076-a393f1cda8b7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Lista över komponenter {#list-of-components}

Observera att om två komponenter inte är kompatibla visas värdet **Ingen** i cellen.

## Dimensioner {#dimensions}

Tabellen nedan visar en lista över de dimensioner som används i rapporter och deras definitioner.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> Definition <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Webbläsare <br/> </td> 
   <td> Webbläsare som meddelandet öppnades eller klickades på.<br/> </td> 
  </tr> 
  <tr> 
   <td> Kampanj<br/> </td> 
   <td> Etikett och ID för din kampanj.<br/> </td> 
  </tr> 
  <tr> 
   <td> Leverans<br/> </td> 
   <td> Etikett och ID för leveransen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Enhet <br/> </td> 
   <td> Enhet från vilken e-post/SMS/push-meddelandet öppnades/visades/klickades.<br/> </td> 
  </tr> 
  <tr> 
   <td> Felorsak <br/> </td> 
   <td> Typer av fel som orsakade studsar för varje leverans, t.ex. okänd användare, ogiltig domän eller postlåda full.<br/> </td> 
  </tr> 
  <tr> 
   <td> Namn på mobilapp <br/> </td> 
   <td> Namn på mobilprogrammet <br/> </td> 
  </tr>
  <tr> 
   <td> Plattform <br/> </td> 
   <td> Plattform för enheten som meddelandet öppnades/visades/klickades på från.<br/> </td> 
  </tr> 
  <tr> 
   <td> Profil<br/> </td> 
   <td> Grupperar om färdiga och anpassade profilfält som skapats under profilresurstillägget.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mottagardomän <br/> </td> 
   <td> Domän som används för att öppna e-postmeddelandet.<br/> </td> 
  </tr> 
  <tr> 
   <td> Återkommande leverans <br/> </td> 
   <td> Etikett och ID för den återkommande leveransen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avsändardomän <br/> </td> 
   <td> Domänen som används för att skicka e-postmeddelandet.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avsändarens IP<br/> </td> 
   <td> IP som används för att skicka e-postmeddelandet.<br/> </td> 
  </tr> 
  <tr> 
   <td> Spårnings-URL<br/> </td> 
   <td> URL som användaren klickade på i meddelandet.<br/> </td> 
  </tr> 
  <tr> 
   <td> URL-spårningskategori <br/> </td> 
   <td> Kategori tilldelad spårnings-URL.<br/> </td> 
  </tr> 
  <tr> 
   <td> URL-etikett <br/> för spårning </td> 
   <td> En etikett har angetts för URL:en, till exempel spegelsida, kontakta oss eller öppna.<br/> </td> 
  </tr> 
  <tr> 
   <td> Transaktionsleverans<br/> </td> 
   <td> Etikett och ID för transaktionsleveransen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Variant<br/> </td> 
   <td> Variant av e-postmeddelandet vid A/B-testning.<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Mätvärden {#metrics}

Tabellerna nedan ger dig en lista över de mätvärden som används i rapporter och deras definitioner beroende på leveranstyp.

### E-postmått {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Mått <br/> </th> 
   <th> Definition <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> På blockeringslista <br/> </td> 
   <td> Antal mottagare som har deklarerat ett e-postmeddelande som skräppost eller skräppost.<br/> </td> 
  </tr> 
  <tr> 
   <td> Blocklist frekvens <br/> </td> 
   <td> Procentandel leveranser som är markerade på blockeringslista.<br/> </td> 
  </tr> 
  <tr> 
   <td> studsar + fel <br/> </td> 
   <td> Totalt antal fel som sammanställts under leverans och automatisk returbearbetning i relation till totalt antal skickade meddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Studsa + felfrekvens <br/> </td> 
   <td> Procentandel e-postmeddelanden som studsade jämfört med e-postmeddelanden som skickades.<br/> </td> 
  </tr> 
  <tr> 
   <td> Klicka på<br/> </td> 
   <td> Antal gånger som ett innehåll klickades i en leverans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Klicka igenom frekvensen <br/> </td> 
   <td> Procentandel klick i en leverans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Levererad<br/> </td> 
   <td> Antal meddelanden som har skickats, i relation till totalt antal skickade meddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Levererad frekvens <br/> </td> 
   <td> Procentandel meddelanden som skickades.<br/> </td> 
  </tr> 
  <tr> 
   <td> Hårt studs<br/> </td> 
   <td> Totalt antal permanenta fel, till exempel fel e-postadress.<br/> </td> 
  </tr> 
  <tr> 
   <td> Hård studsfrekvens <br/> </td> 
   <td> Procentandel leveranser som misslyckades på grund av permanenta fel.<br/> </td> 
  </tr> 
  <tr> 
   <td> Spegelsida <br/> </td> 
   <td> Antal mottagare som klickade på länken för spegelsidan.<br/> </td> 
  </tr> 
  <tr> 
   <td> Spegelsidhastighet <br/> </td> 
   <td> Procentandel klick på spegelsidlänken jämfört med totalt antal leveransmeddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Erbjud klickningar<br/> </td> 
   <td> Antal gånger som någon klickade på ett erbjudande i en leverans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Erbjud klickfrekvens <br/> </td> 
   <td> Procentandel klick i ett erbjudande.<br/> </td> 
  </tr> 
  <tr> 
   <td> Öppna<br/> </td> 
   <td> Antal gånger ett meddelande öppnades i en leverans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Öppen frekvens <br/> </td> 
   <td> Procentandel öppnade meddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Behandlad/skickad<br/> </td> 
   <td> Totalt antal försändelser för leveransen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Karantän<br/> </td> 
   <td> Antal meddelanden som studsade och resulterade i karantän för adressen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Karantänsats <br/> </td> 
   <td> Procent av karantän jämfört med skickade meddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avvisad<br/> </td> 
   <td> Antal meddelanden som klassificerats som skräppost av SMTP-servrar.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avvisad frekvens <br/> </td> 
   <td> Procentandel av meddelanden som markerats som avvisade.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mjuk studs <br/> </td> 
   <td> Totalt antal tillfälliga fel, t.ex. en fullständig inkorg.<br/> </td> 
  </tr> 
  <tr> 
   <td> Mjuk studsfrekvens <br/> </td> 
   <td> Procentandel leveranser som misslyckades på grund av temporär orsak.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unika klick<br/> </td> 
   <td> Antal mottagare som klickat på ett innehåll i en leverans.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unika öppningar<br/> </td> 
   <td> Antal mottagare som öppnade leveransen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unik avbeställning<br/> </td> 
   <td> Antal mottagare som klickat på länken för att ta bort prenumerationen.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avbeställningsfrekvens <br/> </td> 
   <td> Antal unika avprenumerationer jämfört med levererade meddelanden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Avbeställ <br/> </td> 
   <td> Antal klick på länken för att avbryta prenumerationen.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## Segment {#segments}

Tabellen nedan ger dig en lista över de segment som används i rapporter och deras definitioner.

<table> 
 <thead> 
  <tr> 
   <th> Segment<br/> </th> 
   <th> Definition <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Ålder: Boomerer 1<br/> </td> 
   <td> Mottagare från 1946 till 1954.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: blommor 2<br/> </td> 
   <td> Mottagare från 1955 till 1965.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Från 18 till 25<br/> </td> 
   <td> Mottagare mellan 18 och 25 år.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Från 26 till 30<br/> </td> 
   <td> Mottagare mellan 26 och 30 år.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Från 31 till 40<br/> </td> 
   <td> Mottagare mellan 31 och 40 år.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Från 41 till 50<br/> </td> 
   <td> Mottagare mellan 41 och 50 år.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Generation X<br/> </td> 
   <td> Mottagare från 1966 till 1976.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Generation Y (tusendels)<br/> </td> 
   <td> Mottagare från 1977 till 1994.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Generation Z<br/> </td> 
   <td> Mottagare från 1995 till idag.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: större än 50<br/> </td> 
   <td> Mottagare vars ålder är större än 50.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: mindre än 25<br/> </td> 
   <td> Mottagare vars ålder är mindre än 25.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Mindre än 30<br/> </td> 
   <td> Mottagare vars ålder är mindre än 30.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: mindre än 40<br/> </td> 
   <td> Mottagare vars ålder är mindre än 40.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: Mindre än 50<br/> </td> 
   <td> Mottagare vars ålder är mindre än 50.<br/> </td> 
  </tr> 
  <tr> 
   <td> Ålder: tyst generering <br/> </td> 
   <td> Mottagare födda 1945 eller tidigare.<br/> </td> 
  </tr> 
  <tr> 
   <td> Alla besök<br/> </td> 
   <td> Alla mottagare<br/> </td> 
  </tr>
 </tbody> 
</table>
