---
title: Indikatorberäkning
description: Förstå resultaten av dina rapporter med en lista över varje metrisk formel.
level: Intermediate
audience: end-user
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: 06fb21a5-ae98-4c14-97f0-7f851d60ae7d
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---

# Indikatorberäkning{#indicator-calculation}

>[!NOTE]
>
>För att kunna bearbeta och hantera stora volymer och realtidsanalyser på ett bättre sätt använder dynamisk rapportering ungefärliga aggregeringar för distinkta räkningsberäkningar. Ungefärlig aggregering erbjuder begränsad minnesanvändning och är ofta snabbare än exakta beräkningar.

Tabellerna nedan visar en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp.

## E-postleverans {#email-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etikett</strong> <br/> </th> 
   <th> <strong>Fältnamn</strong> <br/> </th> 
   <th> <strong>Beräkningsformel för indikator</strong> <br/> </th> 
   <th> <strong>Kommentarer</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Konto inaktiverat <br/> </td> 
   <td> @disabled<br/> </td> 
   <td> count(@errorReason=4)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> På blockeringslista <br/> </td> 
   <td> @svartlistad<br/> </td> 
   <td> count(@errorReason=8, @errorType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Blocklist frekvens <br/> </td> 
   <td> @rateBlacklisted<br/> </td> 
   <td> @svartlistad/@skickad<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr> 
  <tr> 
   <td> studsar + fel <br/> </td> 
   <td> @bounces<br/> </td> 
   <td> count(@status=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Studsa + felfrekvens <br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> @bounces/@sent<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Klicka på<br/> </td> 
   <td> @klickningar<br/> </td> 
   <td> count(@trackingUrlType=1, 10 eller 11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Klicka igenom frekvensen <br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> @uniqueclicks/@deliver<br/> </td> 
   <td> Nämnaren för tariffberäkning är endast baserad på Levererad.<br/> </td> 
  </tr> 
  <tr> 
   <td> Levererad<br/> </td> 
   <td> @levererad<br/> </td> 
   <td> count(@status=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Levererad frekvens <br/> </td> 
   <td> @rateDelived<br/> </td> 
   <td> @levererad/@skickad<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr> 
  <tr> 
   <td> Hårda studsar <br/> </td> 
   <td> @hardBounces<br/> </td> 
   <td> count(@errorType=2 OCH @errorReason=8)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Hård studentfrekvens <br/> </td> 
   <td> @rateHardBounces<br/> </td> 
   <td> @hardBounces/@sent<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr> 
  <tr> 
   <td> Ogiltig domän <br/> </td> 
   <td> @invalidDomain<br/> </td> 
   <td> count(@errorReason=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Postlådan är full<br/> </td> 
   <td> @mailBoxFull<br/> </td> 
   <td> count(@errorReason=5)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Spegelsida <br/> </td> 
   <td> @mirrorPage<br/> </td> 
   <td> count(@trackingUrlType=6)<br/> </td> 
   <td> Nämnaren för tariffberäkning är endast baserad på Levererad.<br/> </td> 
  </tr> 
  <tr> 
   <td> Spegelsidhastighet <br/> </td> 
   <td> @rateMirrorPage<br/> </td> 
   <td> @mirrorPage/@deliver<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Inte ansluten<br/> </td> 
   <td> @notConnected<br/> </td> 
   <td> count(@errorReason=6)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Öppna<br/> </td> 
   <td> @uniqueOpen<br/> </td> 
   <td> count(@trackingUrlType=2 + unique(@trackingUrlType=1,2,3,6,10,11) - unique(@trackingUrlType=2))<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Öppen frekvens <br/> </td> 
   <td> @rateÖppnas<br/> </td> 
   <td> @opens/@deliver<br/> </td> 
   <td> Nämnaren för tariffberäkning är endast baserad på Levererad.<br/> </td> 
  </tr> 
  <tr> 
   <td> Karantän<br/> </td> 
   <td> @karantän<br/> </td> 
   <td> isQuarantine=true<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Karantänsats <br/> </td> 
   <td> @rateQuarantine<br/> </td> 
   <td> @karantän/@skickad<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr>
  <tr> 
   <td> Avvisad<br/> </td> 
   <td> @avvisad<br/> </td> 
   <td> count(@errorReason=20, @errorType=2)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Avvisad frekvens <br/> </td> 
   <td> @rateRejected<br/> </td> 
   <td> @avvisad/@skickad<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr> 
  <tr> 
   <td> Behandlad/skickad<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @levererad + @studsar<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mjuk studs <br/> </td> 
   <td> @softBounces<br/> </td> 
   <td> count(@errorType=1)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mjuk studsfrekvens <br/> </td> 
   <td> @rateSoftBounces<br/> </td> 
   <td> @softBounces/@sent<br/> </td> 
   <td> Nämnaren för tariffberäkning baseras på antalet skickade (levererade + studsar).<br/> </td> 
  </tr> 
  <tr> 
   <td> Unika klick<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> Unika klick beräknas med ThetaSketch-koncept. </a>.<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unika öppningar<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> unique(@trackingUrlType=1,2,3,6,10,11)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Onåbar <br/> </td> 
   <td> @ej nåbar<br/> </td> 
   <td> count(@errorReason=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Avbeställ <br/> </td> 
   <td> @unsubscribes<br/> </td> 
   <td> count(@trackingUrlType=3)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Avbeställningsfrekvens <br/> </td> 
   <td> @rateUnsubscribes<br/> </td> 
   <td> @unsubscribes/@deliver<br/> </td> 
   <td> Nämnaren för tariffberäkning är endast baserad på Levererad.<br/> </td> 
  </tr> 
  <tr> 
   <td> Okänd användare: <br/> </td> 
   <td> @unknownUser<br/> </td> 
   <td> count(@errorReason=1)<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

<!--
## Push notification delivery {#push-notification-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> @opens<br/> </td> 
   <td> @count(status=open)<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> (@opens/@delivered)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique opens<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> Unique opens is calculated using ThetaSketch concepts of unique RecipientIds.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> @count(status=interact)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> Unique clicks is calculated using ThetaSketch concepts.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> (@interact/@delivered)*100<br/> </td> 
  </tr> 
 </tbody> 
</table>

## In-App delivery {#in-app-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
   <th> <strong>Comments</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
   <td> sent=delivered<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
   <td> delivered=sent<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=view) or @count(status=button 1 click + button 2 click + dismissals)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> @inappclicks<br/> </td> 
   <td> @count (status=click)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> @uniqueinapp<br/> </td> 
   <td> @unique(@count (status=clicks))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> @inappclickthrough<br/> </td> 
   <td> Total clicks on Button 1 or Button 2/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> @dismissal<br/> </td> 
   <td> @count (status=close)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> @uniquedismissal<br/> </td> 
   <td> @unique(@count (status=close))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> @dismissalrate<br/> </td> 
   <td> Total close/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>
-->
