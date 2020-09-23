---
title: Wat is Power BI Report Server?
description: U kunt een overzicht krijgen van Power BI Report Server zodat u begrijpt hoe het is aangepast voor SQL Server Reporting Services (SSRS) en de rest van Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/28/2020
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 4b2b29effb1d9b4b2d8e743990dd3dd0d27470f8
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859837"
---
# <a name="what-is-power-bi-report-server"></a>Wat is Power BI Report Server?

Power BI Report Server is een on-premises rapportserver met een webportal waarin u rapporten en KPI's kunt weergeven en beheren. De server bevat de hulpprogramma's om Power BI-rapporten, gepagineerde rapporten, mobiele rapporten en KPI's te maken. Uw gebruikers hebben op verschillende manieren toegang tot deze rapporten: ze kunnen ze in een webbrowser of op een mobiel apparaat bekijken of als een e-mailbericht in hun Postvak IN.

![De webportal van Power BI Report Server](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Power BI Report Server vergelijken 
Power BI Report Server lijkt op zowel SQL Server Reporting Services als de online Power BI-service, maar er zijn verschillen. Net als de Power BI-service host Power BI Report Server Power BI-rapporten (PBIX), Excel-bestanden en gepagineerde rapporten (RDL). Power BI Report Server wordt net als Reporting Services on-premises uitgevoerd. De functies van Power BI Report Server zijn een uitbreiding op de functies van Reporting Services: alles wat u kunt doen in Reporting Services, kunt u doen met Power BI Report Server. Daarnaast biedt het ondersteuning voor Power BI-rapporten. Zie [Comparing Power BI Report Server and the Power BI service](compare-report-server-service.md) (Power BI Report Server vergelijken met de Power BI-service) voor meer informatie.

## <a name="licensing-power-bi-report-server"></a>Licenties voor Power BI Report Server
Power BI Report Server is beschikbaar via twee verschillende licenties: [Power BI Premium](../admin/service-premium-what-is.md) en SQL Server Enterprise Edition met Software Assurance. Zie [Microsoft Volume Licensing](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=1&ShowArchived=True) voor meer informatie. Met een licentie voor Power BI Premium kunt u een hybride implementatie maken waarin de cloud en uw on-premises omgeving gemengd zijn.

Als u Power BI-rapporten publiceert naar Power BI Report Server, hebt u ook een Power BI Pro-licentie nodig. U hebt geen Power BI Pro-licentie nodig om Power BI-rapporten op Power BI Report Server weer te geven en ermee te werken.

> [!NOTE]
> Bij Power BI Premium is de Power BI Report Server alleen opgenomen in P-SKU's. Deze is niet opgenomen in EM-SKU's.

## <a name="web-portal"></a>Webportal
Het toegangspunt voor Power BI Report Server is een veilige webportal die u in een moderne browser kunt bekijken. Hier hebt u toegang tot al uw rapporten en KPI's. De inhoud op de webportal is in een traditionele mappenhiërarchie gerangschikt. In uw mappen wordt inhoud per type gegroepeerd: Power BI-rapporten, mobiele rapporten, gepagineerde rapporten, KPI's en Excel-werkmappen. Gedeelde gegevenssets en gedeelde gegevensbronnen staan in hun eigen mappen en kunnen worden gebruikt als bouwstenen voor uw rapporten. U kunt uw favorieten taggen, zodat u ze in één map kunt bekijken. En u kunt KPI's rechtstreeks in de webportal maken. 

![De webportal van Power BI Report Server](media/get-started/web-portal.png)

Afhankelijk van uw machtigingen kunt de inhoud van de webportal beheren. U kunt rapportverwerking inplannen, rapporten op aanvraag openen en u abonneren op gepubliceerde rapporten. U kunt ook uw eigen aangepaste [huisstijl](/sql/reporting-services/branding-the-web-portal) toepassen op uw webportal. 

Meer informatie over de [webportal van Power BI Report Server](/sql/reporting-services/web-portal-ssrs-native-mode) (Engelstalig).

## <a name="power-bi-reports"></a>Power BI-rapporten
U maakt Power BI-rapporten (PBIX) met de versie van Power BI Desktop die voor de rapportserver is geoptimaliseerd. Vervolgens publiceert u ze en bekijkt u ze in de webportal in uw eigen omgeving.

![Power BI-rapporten in Power BI Report Server](media/get-started/powerbi-reports.png)

Een Power BI-rapport biedt een meervoudige weergave in een gegevensmodel, met visualisaties die andere bevindingen en inzichten uit dat gegevensmodel voorstellen.  Een rapport kan één visualisatie of pagina's vol visualisaties bevatten. Afhankelijk van uw functie kunt u rapporten lezen en verkennen of ze voor andere personen maken.

Lees hier meer over het [installeren van Microsoft Power BI Desktop](install-powerbi-desktop.md).

## <a name="paginated-reports"></a>Gepagineerde rapporten
Gepagineerde rapporten (RDL) zijn rapporten in documentstijl met visualisaties, waarin tabellen horizontaal en verticaal kunnen worden uitgebreid om alle gegevens weer te geven, eventueel doorlopend op volgende pagina's. Ze zijn ideaal voor het genereren van documenten met een perfecte vaste indeling die zijn geoptimaliseerd voor afdrukken, zoals PDF- en Word-bestanden. 

![Gepagineerde rapporten in Power BI Report Server](media/get-started/paginated-reports.png)

U kunt gepagineerde rapporten maken met [Report Builder](/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) of Report Designer in [SQL Server Data Tools (SSDT)](/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Mobiele rapporten van Reporting Services
Mobiele rapporten maken verbinding met on-premises gegevens en hebben een responsieve indeling die wordt aangepast aan verschillende apparaten en de wijze waarop deze worden vastgehouden. U maakt ze met SQL Server Mobile Report Publisher.

Meer informatie over [Mobiele rapporten van Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Programmeerfuncties van Report Server
Maak gebruik van de programmeerfuncties van Power BI Report Server zodat u uw rapporten kunt uitbreiden en aanpassen met API's voor het integreren of uitbreiden van gegevens en het verwerken van rapporten in aangepaste toepassingen.

Meer [ontwikkelaarsdocumentatie voor Report Server](/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Volgende stappen
[Power BI Report Server installeren](install-report-server.md)  
[Report Builder downloaden](https://www.microsoft.com/download/details.aspx?id=53613)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)