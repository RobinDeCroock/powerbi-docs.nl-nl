---
title: Comparing Power BI Report Server and the Power BI service (Power BI Report Server vergelijken met de Power BI-service)
description: In dit artikel worden de functies van Power BI Report Server en de Power BI-service vergeleken.
author: maggiesMSFT
ms.author: maggies
keywords: ''
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 01/25/2021
ms.openlocfilehash: ba0fada8ed167b9ba788f4f0d2f9ab9e900dcde4
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044282"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparing Power BI Report Server and the Power BI service (Power BI Report Server vergelijken met de Power BI-service)

Power BI Report Server en de Power BI-service hebben veel overeenkomsten en een paar belangrijke verschillen. In deze tabel worden de overeenkomsten en verschillen uitgelegd.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Functies van Power BI Report Server en de Power BI-service

| Functies | Power BI Report Server | Power BI-service | Opmerkingen |
|---------|---------|---------|---------|
| Implementatie | On-premises of gehoste cloud | Cloud | Power BI Report Server kan worden geïmplementeerd in Azure VM’s (gehoste cloud) indien gelicentieerd via Power BI Premium of SQL Server Enterprise met Software Assurance|
| Brongegevens | Cloud en/of on-premises | Cloud en/of on-premises |  |
| Licentie | Power BI Premium of SQL Server EE met SA (Software Assurance) | Power BI Pro en/of Power BI Premium | |  
| Levenscyclus | Beleid voor moderne levenscyclus | Volledig beheerde service |  |
| Releasecyclus | Drie keer per jaar (januari, mei, september) | Eén keer per maand | Nieuwste functies en oplossingen worden het eerst uitgebracht in de Power BI-service. Een aantal functies van Power BI Desktop-releases voor de service worden in elke release gepubliceerd in Power BI Report Server. De meeste andere functies zijn alleen bedoeld voor de Power BI-service. |
| Power BI-rapporten maken in Power BI Desktop | Ja | Ja |  |
| Power BI-rapporten maken in de browser | Nee | Ja |  |
| Gedeelde Power BI-gegevenssets hosten en er verbinding mee maken | Nee | Ja | [Introductie van gegevenssets in verschillende werkruimten](../connect-data/service-datasets-across-workspaces.md) |
| Gateway vereist | Nee | Ja voor on-premises gegevensbronnen |  |
| Realtime streaming | Nee | Ja | [Realtimestreaming in Power BI](../connect-data/service-real-time-streaming.md) |
| Dashboards | Nee | Ja | [Dashboards in de Power BI-service](../consumer/end-user-dashboards.md) |
| Distributiegroep met rapporten die apps gebruiken | Nee | Ja | [Apps maken en publiceren met dashboards en rapporten](../collaborate-share/service-create-distribute-apps.md) |
| Inhoudspakketten | Nee | Ja | [Organisatie-inhoudspakketten: Inleiding](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Verbinding maken met services zoals Salesforce | Ja | Ja | [Verbinding maken met de services die u gebruikt](../connect-data/service-connect-to-services.md) met inhoudspakketten in de Power BI-service. In Power BI Report Server gebruikt u gecertificeerde connectors om verbinding te maken met de services. Zie [Power BI-rapportgegevensbronnen in Power BI Report Server](data-sources.md) voor meer informatie. |
| Q&A | Nee | Ja | [Q&A in de Power BI-service en Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Snelle inzichten | Nee | Ja | [Automatisch gegevensinzichten genereren met Power BI](../consumer/end-user-insights.md) |
| In Excel analyseren | Nee | Ja | [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md) 
| Gepagineerde rapporten | Ja | Ja | [Gepagineerde rapporten zijn beschikbaar in de Power BI-service](../paginated-reports/paginated-reports-report-builder-power-bi.md) in preview in een Premium-capaciteit (Engelstalig) |
| Power BI - Mobiel-apps | Ja | Ja | [Overzicht van mobiele Power BI-apps](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS voor Power BI | Ja | Ja | [ArcGIS voor Power BI](../visuals/power-bi-visualizations-arcgis.md) |
| E-mailabonnementen voor Power BI-rapporten | Nee | Ja | [Uzelf of anderen abonneren](../collaborate-share/service-report-subscribe.md) op een rapport of dashboard in de Power BI-service |
| E-mailabonnementen voor gepagineerde rapporten | Ja | Ja | [Uzelf en anderen abonneren op gepagineerde rapporten in de Power BI-service](../consumer/paginated-reports-subscriptions.md)<br><br>[E-maillevering in Reporting Services](/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Gegevensmeldingen | Nee | Ja | [Gegevensmeldingen in de Power BI-service](../create-reports/service-set-data-alerts.md)
| Beveiliging op rijniveau (RLS) | Ja | Ja | Beschikbaar in de DirectQuery-modus (gegevensbron) en in de importmodus <br><br>Beveiliging op rijniveau met de [Power BI-service](../admin/service-admin-rls.md) <br><br>Beveiliging op rijniveau in [Power BI Report Server](row-level-security-report-server.md) |
| Veel-op-veel-relaties | Nee | Ja | [Veel-op-veel-relaties toepassen](../transform-model/desktop-many-to-many-relationships.md) in Power BI Desktop |
| Drillthrough voor verschillende rapporten | Nee | Ja | [Drillthrough voor verschillende rapporten gebruiken](../create-reports/desktop-cross-report-drill-through.md) |
| Modus Volledig scherm | Nee | Ja | [De modus Volledig scherm](../consumer/end-user-focus.md) in de Power BI-service |
| Geavanceerde Microsoft 365-samenwerking | Nee | Ja | [Samenwerken in een werkruimte](../collaborate-share/service-collaborate-power-bi-workspace.md) met Microsoft 365 |
| R-scripts en visuals | Nee | Ja | [R-visuals maken](../create-reports/desktop-r-visuals.md) en R-scripts in Power BI Desktop uitvoeren en publiceren naar de Power BI-service. U kunt Power BI-rapporten met R-scripts of -visuals niet opslaan naar Power BI Report Server.  |
| Python-scripts en -visuals | Nee | Ja | [Python-scripts en -visuals maken](../connect-data/desktop-python-scripts.md) in Power BI Desktop en deze publiceren naar de Power BI-service. U kunt Power BI-rapporten met Python-scripts of -visuals niet opslaan naar Power BI Report Server. |
| Preview-functies | Nee | Ja | [Aanmelden voor preview-functies van de Power BI-service](../consumer/end-user-preview-features.md) |
| Power BI-visuals | Ja | Ja | [Power BI-visuals](../developer/visuals/power-bi-custom-visuals.md) |
| Samengestelde modellen | Nee | Ja |
| Power BI Desktop | Versie geoptimaliseerd voor Report Server, beschikbaar voor downloaden met Report Server | Versie geoptimaliseerd voor de Power BI-service, beschikbaar in de Windows Store | [Power BI Desktop voor de rapportserver](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop voor de Power BI-service](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Volgende stappen

[Power BI Report Server installeren](install-report-server.md)