---
title: Adobe Campaign webbgränssnitt
description: 64-bitars tabeller
badge: label="BEGRÄNSAD TILLGÄNGLIGHET" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Begränsat till användare som migrerats till Campaign Standarden"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# 64-bitars scheman {#64-bit-tables}

För att underlätta övergången från Campaign Standard till Campaign v8 har flera tabeller ändrats från 32 till 64 bitar. Campaign Standarden stöder 64-bitars PK i flera färdiga scheman, medan Campaign v8 stöder 32-bitars PK i de flesta scheman.

## Begränsningar

* Den här tekniska ändringen gäller endast kunder som migrerar från Campaign Standard.
* Schema- och utsändningstillägg stöds inte i 64 bitar. Den stannar kvar om 32 bitar.
* Loggar för leveranser som skickas till tekniska användare är inte tillgängliga i Campaign v8.
* Endast PostgreSQL stöds.

## Ändrade scheman

Här är listan över scheman som har ändrats till 64 bitar och deras ändrade attribut.

| Schemanamn | Attributnamn |
|--- |--- |
| nms:broadLogRcp | id |
| nms:trackingLogRcp | id |
| nms:excludeLogRcp | id |
| nms:broadLogVisitor | id |
| nms:trackingLogVisitor | id |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrackingLog | id |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPress | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | id |
| nms:trackingLogAppSubRcp | id |
| nms:excludeLogAppSubRcp | id |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
