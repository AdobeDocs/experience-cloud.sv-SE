---
audience: user
user-guide-title: Adobe Experience Rollouts
user-guide-description: Lär dig hur du använder Adobe Experience Rollouts för att hantera funktionsflaggor, kontrollerade lanseringar och riktade releaser i alla program.
source-git-commit: cd1d882942705f51440ae99f4ce6daf467d3283c
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Adobe Experience Rollouts {#experience-rollouts}

+ [Ökning](home.md)
+ Komma igång {#get-started}
   + [Introduktion till upplevelselanseringar](getting-started/introduction.md)
   + [Varför använda upplevelseutrullningar](getting-started/why-use-experience-rollouts.md)
   + [Lägen för upplevelseutrullningar](getting-started/experience-rollouts-modes.md)
+ Concepts {#concepts}
   + [Vad är en funktionsflagga?](concepts/what-is-a-feature-flag.md)
   + [Funktionsflaggor för att aktivera och inaktivera funktioner](concepts/feature-flags-to-enable-disable-features.md)
   + [Funktionsgrupper som styr flera funktioner](concepts/feature-groups-to-control-multiple-features.md)
   + [Frisläppningshantering](concepts/concept-of-release-management.md)
   + [Versionshantering i upplevelseutrullningar](concepts/release-management.md)
   + [gradvis utrullning](concepts/gradual-rollout.md)
+ Användarhandböcker {#guides}
   + Komma igång med konsolen {#console}
      + [Logga in på Experience Rollouts-konsolen](guides/console/log-in-to-the-console.md)
      + [Miljööversikt](guides/console/environments-overview.md)
      + [Begär åtkomst](guides/console/request-access.md)
      + [Team och deras administratörer](guides/console/teams-and-admins.md)
      + [Skapa ett nytt team](guides/console/create-a-new-team.md)
   + Team {#teams}
      + [Hantera team](guides/teams/manage-teams.md)
      + [Användarroller](guides/teams/user-roles.md)
      + [Lägg till medlemmar i ditt team](guides/teams/add-team-members.md)
      + [Vanliga frågor om teamhantering](guides/teams/team-management-faq.md)
   + Program {#applications}
      + [Hantera program](guides/applications/manage-applications.md)
      + [Anpassa applikationen](guides/applications/onboard-your-application.md)
   + Integrera upplevelseutrullningar {#integrate}
      + [Integrera upplevelseutrullningar i appen](guides/integrate/integrating-in-your-app.md)
      + [Starthandbok](guides/integrate/startup-guide.md)
      + [Datorprogram](guides/integrate/desktop-applications.md)
      + [Mobilappar](guides/integrate/mobile-applications.md)
      + [Webbprogram](guides/integrate/web-applications.md)
      + [Webbtjänster](guides/integrate/web-services.md)
      + [SDK](guides/integrate/sdks.md)
      + [Integreringssteg](guides/integrate/integration-steps.md)
      + [Prenumerera på API-programmet i Adobe Developer Console](guides/integrate/subscribe-to-api-application.md)
   + Funktionsflaggor och releaser {#feature-flags-releases}
      + [Funktioner, funktionsgrupper och releaser](guides/feature-flags/features-feature-groups-releases.md)
      + [Skapa din första funktionsflagga](guides/feature-flags/create-your-first-feature-flag.md)
      + [Ange en funktion som gradvis ska rulla ut](guides/feature-flags/set-feature-gradual-rollout.md)
      + [Skapa en funktionsgrupp](guides/feature-flags/create-a-feature-group.md)
      + [Ange att en funktionsgrupp ska rullas ut gradvis](guides/feature-flags/set-feature-group-gradual-rollout.md)
      + [A/B-testning med funktionsflaggor](guides/feature-flags/a-b-testing.md)
      + [Releaser och teamöverskridande funktionsgrupper](guides/feature-flags/releases-and-cross-team-feature-groups.md)
      + [Arbetsflöde från början till slut](guides/feature-flags/release-workflow-end-to-end.md)
      + [Begär en release](guides/feature-flags/request-a-release.md)
      + [Uppdatera publiceringsregler](guides/feature-flags/update-release-audience-rules.md)
      + [Frigör lägen](guides/feature-flags/release-states.md)
      + [Skapa en funktionsgrupp för flera team](guides/feature-flags/create-cross-team-feature-group.md)
      + [Vanliga frågor om versionshantering](guides/feature-flags/release-management-faqs.md)
      + [Analyser](guides/feature-flags/analytics.md)
      + [Schema](guides/feature-flags/schedule.md)
   + Målgruppskriterier {#audience}
      + [Målgrupp i funktionsflaggor och funktionsgrupper](guides/audience/audience-in-feature-flags-and-feature-groups.md)
      + [Använd sammanhang i målgruppsregler](guides/audience/using-context-in-audience-rules.md)
      + [Komplexa målgruppsregler](guides/audience/complex-rules.md)
      + [Använd företagsorganisationsdata i målgruppsregler](guides/audience/using-enterprise-org-data.md)
      + [Lägg till procentregler i målgruppskriterier](guides/audience/adding-percentage-rules.md)
      + [Målgruppsregel med klientens IP-kontextvariabel](guides/audience/clientip-rule.md)
   + Arbetsflöden för olika miljöer {#cross-environment}
      + [Koncept för flera miljöer](guides/cross-environment/cross-environment-concept.md)
      + [Koppla miljöer till ett program](guides/cross-environment/associate-environments.md)
      + [Visa funktionsflaggor i olika miljöer](guides/cross-environment/view-feature-flags-across-environments.md)
      + [Importera funktionsflaggor](guides/cross-environment/import-feature-flags.md)
   + Automatiserade utrullningar {#automated-rollouts}
      + [Skapa en automatiserad utrullning](guides/automated-rollouts/create-automated-rollout.md)
      + [Automatiserat utrullningskoncept](guides/automated-rollouts/automated-rollout-concept.md)
      + [Övervaka och redigera en utrullningsplan](guides/automated-rollouts/monitor-edit-rollout-plan.md)
   + Support {#support}
      + [Felsökning](guides/support/troubleshooting.md)
      + [Få support](guides/support/get-support.md)
      + [Kontakta support](guides/support/contact-support.md)
   + SDK-versioner {#sdk-releases}
      + Java SDK {#java-sdk}
         + [Integreringsguide för Java SDK](guides/sdk-releases/java/java-sdk-integration-guide.md)
         + [Versionsinformation för Java SDK](guides/sdk-releases/java/java-sdk-release-notes.md)
      + Node.js SDK {#nodejs-sdk}
         + [Integreringsguide för Node.js SDK](guides/sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
         + [Node.js Versionsinformation för SDK](guides/sdk-releases/nodejs/nodejs-sdk-release-notes.md)
      + [SDK prestandatester](guides/sdk-releases/java-sdk-benchmarking.md)
<!--+ Feature API {#feature-api}
  + [GET Feature API V3](feature-api/get-feature-api-v3.md)
  + [GET Feature API V2](feature-api/get-feature-api-v2.md)
+ Management API {#management-api}
  + [Feature management APIs overview](management-api/feature-management-apis-overview.md)
  + [Feature flags management API](management-api/feature-flags-management-api.md)
  + [Feature group management API](management-api/feature-group-management-api.md)
  + [Release management APIs](management-api/release-management-apis.md)
  + [Get client ID for an application](management-api/get-client-id.md)
  + [Get desired audience criteria](management-api/get-audience-criteria.md)
  + [Management patch API](management-api/management-patch-api.md)-->
