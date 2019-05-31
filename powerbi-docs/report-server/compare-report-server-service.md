---
title: Comparing Power BI Report Server and the Power BI service (Power BI Report Server vergelijken met de Power BI-service)
description: In dit artikel worden de functies van Power BI Report Server en de Power BI-service vergeleken.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.date: 05/22/2019
ms.openlocfilehash: c4254420ae949b1fae6a1407cd045589c23da3c8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187677"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparing Power BI Report Server and the Power BI service (Power BI Report Server vergelijken met de Power BI-service)

Power BI Report Server en de Power BI-service hebben veel overeenkomsten en een paar belangrijke verschillen. In deze tabel worden de overeenkomsten en verschillen uitgelegd.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Functies van Power BI Report Server en de Power BI-service

| Functies | Power BI Report Server | Power BI-service | Opmerkingen |
|---------|---------|---------|---------|
| Implementatie | On-premises of gehoste cloud | Cloud | Power BI Report Server kan worden geïmplementeerd in Azure VM’s (gehoste cloud) indien gelicentieerd via Power BI Premium |
| Brongegevens | Cloud en/of on-premises | Cloud en/of on-premises |  |
| Licentie | Power BI Premium of SQL Server EE met SA | Power BI Pro en/of Power BI Premium | |  
| Levenscyclus | Beleid voor moderne levenscyclus | Volledig beheerde service |  |
| Releasecyclus | Elke 4 maanden | Eén keer per maand | Nieuwste functies en oplossingen worden het eerst uitgebracht in de Power BI-service. De meeste kernfuncties worden in de volgende paar releases doorgevoerd in Power BI Report Server. Sommige functies zijn alleen bedoeld voor de Power BI-service. |
| Power BI-rapporten maken in Power BI Desktop | Ja | Ja |  |
| Power BI-rapporten maken in de browser | Nee | Ja |  |
| Gateway vereist | Nee | Ja voor on-premises gegevensbronnen |  |
| Realtime streaming | Nee | Ja | [Realtimestreaming in Power BI](../service-real-time-streaming.md) |
| Dashboards | Nee | Ja | [Dashboards in de Power BI-service](../consumer/end-user-dashboards.md) |
| Distributiegroep met rapporten die apps gebruiken | Nee | Ja | [Apps maken en publiceren met dashboards en rapporten](../service-create-distribute-apps.md) |
| Inhoudspakketten | Nee | Ja | [Organisatie-inhoudspakketten: Inleiding](../service-organizational-content-pack-introduction.md) |
| Verbinding maken met services zoals Salesforce | Ja | Ja | [Verbinding maken met de services die u gebruikt](../service-connect-to-services.md) met inhoudspakketten in de Power BI-service. In Power BI Report Server gebruikt u gecertificeerde connectors om verbinding te maken met de services. Zie [Power BI-rapportgegevensbronnen in Power BI Report Server](data-sources.md) voor meer informatie. |
| Q&A | Nee | Ja | [Q&A in de Power BI-service en Power BI Desktop](../power-bi-tutorial-q-and-a.md) 
| Snelle inzichten | Nee | Ja | [Automatisch gegevensinzichten genereren met Power BI](../consumer/end-user-insights.md) |
| In Excel analyseren | Nee | Ja | [Analyseren in Excel](../service-analyze-in-excel.md) 
| Gepagineerde rapporten | Ja | Ja | [Gepagineerde rapporten zijn beschikbaar in de Power BI-service](../paginated-reports-report-builder-power-bi.md) in preview in een Premium-capaciteit (Engelstalig) |
| Power BI - Mobiel-apps | Ja | Ja | [Overzicht van mobiele Power BI-apps](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ARC GIS-kaarten | Nee | Ja | [ArcGIS-kaarten in de Power BI-service en Power BI Desktop, door Esri](../visuals/power-bi-visualization-arcgis.md) |
| E-mailabonnementen voor Power BI-rapporten | Nee | Ja | [Uzelf of anderen abonneren](../service-report-subscribe.md) op een rapport of dashboard in de Power BI-service |
| E-mailabonnementen voor gepagineerde rapporten | Ja | Nee | [E-maillevering in Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| Gegevensmeldingen | Nee | Ja | [Gegevensmeldingen in de Power BI-service](../service-set-data-alerts.md)
| Beveiliging op rijniveau (RLS) | Ja | Ja | Beschikbaar in de DirectQuery-modus (gegevensbron) en in de importmodus <br>Beveiliging op rijniveau met de [Power BI-service](../service-admin-rls.md) <br>Beveiliging op rijniveau in [Power BI Report Server](row-level-security-report-server.md) |
| Modus Volledig scherm | Nee | Ja | [De modus Volledig scherm](../consumer/end-user-focus.md) in de Power BI-service |
| Geavanceerde Office 365-samenwerking | Nee | Ja | [Samenwerken in een app-werkruimte met Office 365](../service-collaborate-power-bi-workspace.md) |
| R-visuals | Nee | Ja | [R-visuals maken](../desktop-r-visuals.md) in Power BI Desktop en deze publiceren naar de Power BI-service. U kunt Power BI-rapporten met R-visuals niet opslaan naar Power BI Report Server.  |
| Preview-functies | Nee | Ja | [Aanmelden voor preview-functies van de Power BI-service](../consumer/end-user-preview-features.md) |
| Aangepaste visuals | Ja | Ja | [Aangepaste visualisaties in Power BI](../power-bi-custom-visuals.md) |
| Power BI Desktop | Versie geoptimaliseerd voor Report Server, beschikbaar voor downloaden met Report Server | Versie geoptimaliseerd voor de Power BI-service, beschikbaar in de Windows Store | [Power BI Desktop voor de rapportserver](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop voor de Power BI-service](http://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Volgende stappen

[Power BI Report Server installeren](install-report-server.md)  