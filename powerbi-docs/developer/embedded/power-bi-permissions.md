---
title: Power BI-machtigingen
description: Power BI-machtigingen
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 51c43a19613381d39e0397864e55baed2022663c
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79491359"
---
# <a name="power-bi-permissions"></a>Power BI-machtigingen

## <a name="permission-scopes"></a>Machtigingsbereiken

Power BI-machtigingen geven een toepassing de mogelijkheid om bepaalde acties namens een gebruiker uit te voeren. Machtigingen zijn pas geldig als deze door een gebruiker zijn goedgekeurd.

| Weergavenaam | Beschrijving | Bereikwaarde |
| --- | --- | --- |
| Alle gegevenssets weergeven |De app kan alle gegevenssets voor de aangemelde gebruiker en gegevenssets waartoe de gebruiker toegang heeft, weergeven. |Dataset.Read.All |
| Alle gegevenssets lezen en schrijven |De app kan alle gegevenssets voor de aangemelde gebruiker en gegevenssets waartoe de gebruiker toegang heeft, weergeven en er naar schrijven. |Dataset.ReadWrite.All |
| Gegevens toevoegen aan de gegevensset van een gebruiker |Geeft een app toegang tot het toevoegen of verwijderen van gegevenssetrijen van een gebruiker. Deze machtiging verleent de app geen toegang tot de gegevens van de gebruiker. |Data.Alter_Any |
| Inhoud maken |De app kan automatisch inhoud en gegevenssets maken voor een gebruiker. |Content.Create |
| Groepen van de gebruiker weergeven |De app kan alle groepen weergeven waartoe de aangemelde gebruiker behoort. |Group.Read |
| Alle groepen weergeven |De app kan alle groepen weergeven waartoe de aangemelde gebruiker behoort. |Group.Read.All |
| Alle groepen lezen en schrijven |De app kan alle groepen voor de aangemelde gebruiker en groepen waartoe de gebruiker toegang heeft, weergeven en ernaar schrijven. |Group.ReadWrite.All |
| Alle dashboards weergeven |De app kan alle dashboards voor de aangemelde gebruiker en dashboards waartoe de gebruiker toegang heeft, weergeven. |Dashboard.Read.All |
| Alle rapporten weergeven |De app kan alle rapporten voor de aangemelde gebruiker en rapporten waartoe de gebruiker toegang heeft, weergeven. De app kan ook de gegevens binnen de rapporten bekijken, evenals de structuur. |Report.Read.All |
| Alle rapporten lezen en schrijven |De app kan alle rapporten voor de aangemelde gebruiker en rapporten waartoe de gebruiker toegang heeft, weergeven en er naar schrijven. Hiermee wordt niet het recht verleend om een nieuw rapport te maken. |Report.ReadWrite.All |
| Alle capaciteiten lezen en schrijven |De app kan alle capaciteiten voor de aangemelde gebruiker en capaciteiten waartoe de gebruiker toegang heeft, weergeven en ernaar schrijven. Hiermee wordt niet het recht verleend om een nieuwe capaciteiten te maken. |Capacities.ReadWrite.All |
| Alle capaciteiten lezen |De app kan alle capaciteiten voor de aangemelde gebruiker en capaciteiten waartoe de gebruiker toegang heeft, weergeven en ernaar schrijven. Hiermee wordt niet het recht verleend om een nieuwe capaciteiten te maken. |Capacities.Read.All |
| Alle inhoud in de tenant lezen en schrijven |De app kan alle artefacten, zoals groepen, rapporten, dashboards en gegevenssets, in Power BI weergeven en ernaar schrijven. Hiervoor dient de aangemelde gebruiker een Power BI-servicebeheerder te zijn. |Tenant.ReadWrite.All |
| Alle inhoud weergeven in de tenant |De app kan alle artefacten, zoals groepen, rapporten, dashboards en gegevenssets, in Power BI weergeven. Hiervoor dient de aangemelde gebruiker een Power BI-servicebeheerder te zijn. |Tenant.Read.All |

Een toepassing kan machtigingen aanvragen wanneer deze voor de eerste keer probeert om aan te melden bij een gebruikerspagina door de aangevraagde machtigingen door te geven in de bereikparameter van de aanroep. Als de machtigingen worden verleend, wordt een toegangstoken geretourneerd naar de app, die in toekomstige API-aanroepen kan worden gebruikt. De toegang kan alleen worden gebruikt door een specifieke toepassing.

> [!NOTE]
> In de API's van Power BI worden werkruimten nog steeds groepen genoemd. Als er wordt verwezen naar groepen, werkt u in feite met werkruimten.

## <a name="requesting-permissions"></a>Machtigingen aanvragen

U kunt de API aanroepen voor verificatie met een gebruikersnaam en wachtwoord, maar om acties te ondernemen namens een andere gebruiker, moeten machtigingen worden aangevraagd die de gebruiker vervolgens goedkeurt. Daarna wordt het resulterende toegangstoken verzonden in alle toekomstige aanroepen. Voor dit proces wordt het [OAuth 2.0](https://oauth.net/2/)-standaardprotocol gebruikt. De daadwerkelijke implementatie verschilt mogelijk, maar de OAuth-stroom voor Power BI bevat de volgende elementen:

* **Aanmeldings-UI**: dit is de UI die de ontwikkelaar kan aanroepen om machtigingen aan te vragen. De gebruiker moet hiervoor aangemeld zijn als dit nog niet het geval is. De gebruiker moet ook de machtigingen goedkeuren die de toepassing aanvraagt. In het aanmeldingsvenster wordt een toegangscode of een foutbericht naar een omleidings-URL die wordt opgegeven.
  * Een standaardomleidings-URL moet worden verstrekt door Power BI voor gebruik door systeemeigen toepassingen.
* **Autorisatiecode**: autorisatiecodes worden na aanmelding geretourneerd aan webtoepassingen via URL-parameters in de omleidings-URL. Omdat deze zich in parameters bevinden, is er een beveiligingsrisico. Webtoepassingen moeten de autorisatiecode uitwisselen voor een autorisatietoken
* **Autorisatietoken**: worden gebruikt om API-aanroepen te verifiëren namens een andere gebruiker. Het bereik ervan wordt beperkt tot een specifieke toepassing. Tokens hebben een ingestelde levensduur en als ze verlopen, moeten ze worden vernieuwd.
* **Vernieuwingstoken**: wanneer tokens verlopen, wordt een proces in gang gezet om deze te vernieuwen.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)