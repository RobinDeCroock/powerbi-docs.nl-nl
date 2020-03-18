---
title: Power BI-gegevensbronnen
description: In dit artikel staan de gegevensbronnen die door Power BI worden ondersteund, inclusief informatie over DirectQuery en de on-premises gegevensgateway.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: 1853e710958b5bed0dad011594d9e04ccc99842d
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041672"
---
# <a name="power-bi-data-sources"></a>Power BI-gegevensbronnen

In de volgende tabel staan de gegevensbronnen die door Power BI worden ondersteund voor gegevenssets, inclusief informatie over DirectQuery en de on-premises gegevensgateway. Zie [Verbinding maken met gegevensbronnen voor Power BI-gegevensstromen](service-dataflows-data-sources.md) voor meer informatie over gegevensstromen.

> [!NOTE]
> Voor veel gegevensconnectors in Power BI Desktop is Internet Explorer 10 (of nieuwer) vereist voor verificatie. 


| Gegevensbron | Verbinding maken via Power BI Desktop | Verbinding maken en vernieuwen via de service | DirectQuery/liveverbinding | Gateway (ondersteund) | Gateway (vereist) |
|---|---|---|---|---|---|---|---|
| Access-database | Ja | Ja | Nee | Ja <sup>1</sup> | Ja |
| Active Directory | Ja | Ja | Nee | Ja | Ja |
| Adobe Analytics | Ja | Ja | Nee | Nee | Nee |
| Amazon Redshift | Ja | Ja | Ja | Ja | Nee |
| appFigures | Ja | Ja | Nee | Nee | Nee |
| AtScale-kubussen | Ja | Ja | Ja | Ja | Nee |
| Azure Analysis Services | Ja | Ja | Ja | Ja <sup>2</sup> | Nee |
| Azure Blob Storage | Ja | Ja | Nee | Ja | Nee |
| Azure Cosmos DB | Ja | Ja | Nee | Nee | Nee |
| Azure Cost Management | Ja | Ja | Nee | Nee | Nee |
| Azure Data Explorer (kusto) | Ja | Ja | Ja | Nee | Nee |
| Azure Data Lake Storage Gen1 | Ja | Ja | Nee | Nee | Nee |
| Azure Data Lake Storage Gen2 | Ja | Ja | Nee | Ja | Nee |
| Azure DevOps | Ja | Ja | Nee | Nee | Nee |
| Azure DevOps Server | Ja | Ja | Nee | Ja | Ja |
| Azure HDInsight (HDFS) | Ja | Ja | Nee | Nee | Nee |
| Azure HDInsight Spark | Ja | Ja | Ja | Nee | Nee |
| Azure SQL Database | Ja | Ja | Ja | Ja <sup>2</sup> | Nee |
| Azure SQL Data Warehouse | Ja | Ja | Ja | Ja <sup>2</sup> | Nee |
| Azure Table Storage | Ja | Ja | Nee | Ja | Nee |
| BI-connector | Ja | Ja | Ja | Ja | Ja |
| BI360 - Budgettering en financiële rapportage | Ja | Ja | Nee | Nee | Nee |
| Common Data Service | Ja | Ja | Nee | Nee | Nee |
| Data.World - Get Dataset | Ja | Ja | Nee | Nee | Nee |
| Denodo | Ja | Ja | Ja | Ja | Ja |
| Dremio | Ja | Ja | Ja | Ja | Ja |
| Dynamics 365 (online) | Ja | Ja | Nee | Nee | Nee |
| Dynamics 365 Business Central | Ja | Ja | Nee | Nee | Nee |
| Dynamics 365 Business Central (on-premises) | Ja | Ja | Nee | Nee | Nee |
| Dynamics 365 Customer Insights | Ja | Ja | Nee | Nee | Nee |
| Dynamics NAV | Ja | Ja | Nee | Nee | Nee |
| Emigo Data Source | Ja | Ja | Nee | Nee | Nee |
| Entersoft Business Suite | Ja | Ja | Nee | Nee | Nee |
| Essbase | Ja | Ja | Ja | Ja | Ja |
| Exasol | Ja | Ja | Ja | Ja | Ja |
| Excel | Ja <sup>3</sup> | Ja <sup>3</sup> | Nee | Ja <sup>3</sup> | Nee <sup>4</sup> |
| Facebook | Ja | Ja | Nee | Nee | Nee |
| Bestand | Ja | Ja | Nee | Ja | Ja |
| Map | Ja | Ja | Nee | Ja | Ja |
| GitHub | Ja | Ja | Nee | Nee | Nee |
| Google Analytics | Ja | Ja | Nee | Nee | Nee |
| Google BigQuery | Ja | Ja | Nee | Nee | Nee |
| Hadoop-bestand (HDFS) | Ja | Nee | Nee | Nee | Nee |
| HDInsight Interactive Query | Ja | Ja | Ja | Nee | Nee |
| IBM DB2 | Ja | Ja | Ja | Ja | Nee |
| IBM Informix-database | Ja | Ja | Nee | Ja | Nee |
| IBM Netezza | Ja | Ja | Ja | Ja | Ja |
| Impala | Ja | Ja | Ja | Ja | Ja |
| Indexima | Ja | Ja | Ja | Ja | Ja |
| Industrial App Store | Ja | Ja | Nee | Nee | Nee |
| Information Grid | Ja | Ja | Nee | Nee | Nee |
| InterSystems IRIS | Ja | Ja | Ja | Ja | Ja |
| Intune-datawarehouse | Ja | Ja | Nee | Nee | Nee |
| Jethro ODBC | Ja | Ja | Ja | Ja | Ja |
| JSON | Ja | Ja | Nee | Ja** | Nee <sup>4</sup> |
| Kyligence Enterprise | Ja | Ja | Ja | Ja | Ja |
| MailChimp | Ja | Ja | Nee | Nee | Nee |
| Marketo | Ja | Ja | Nee | Nee | Nee |
| MarkLogic ODBC | Ja | Ja | Ja | Ja | Ja |
| Inzichten in Microsoft Azure-verbruik | Ja | Ja | Nee | Nee | Nee |
| Microsoft Exchange | Ja | Ja | Nee | Ja | Nee |
| Microsoft Exchange Online | Ja | Ja | Nee | Nee | Nee |
| Microsoft Graph Security | Ja | Ja | Nee | Ja | Nee |
| Mixpanel | Ja | Ja | Nee | Nee | Nee |
| MySQL | Ja | Ja | Nee | Ja | Ja |
| OData | Ja | Ja | Nee | Ja | Nee |
| ODBC | Ja | Ja | Nee | Ja | Ja |
| OLEDB | Ja | Ja | Nee | Ja | Ja |
| Oracle | Ja | Ja | Ja | Ja | Ja |
| Paxata | Ja | Ja | Nee | Ja | Nee |
| PDF | Ja | Ja | Nee | Ja | Nee <sup>4</sup> |
| Planview Enterprise One - CTM | Ja | Ja | Nee | Nee | Nee |
| Planview Enterprise One - PRM | Ja | Ja | Nee | Nee | Nee |
| Planview Projectplace | Ja | Ja | Nee | Nee | Nee |
| PostgreSQL | Ja | Ja | Ja | Ja | Nee |
| Power BI-gegevensstromen | Ja | Ja | Nee | Nee | Nee |
| Power BI-gegevenssets | Ja | Ja | Ja | Nee | Nee |
| Power Platform-gegevensstromen | Ja | Ja | Nee | Nee | Nee |
| Python-script | Ja | Ja <sup>5</sup> | Nee | Ja <sup>5</sup> | Ja |
| QubolePresto | Ja | Ja | Ja | Ja | Ja |
| Quick Base | Ja | Ja | Nee | Ja | Ja |
| QuickBooks Online | Ja | Ja | Nee | Nee | Nee |
| R-script | Ja | Ja <sup>5</sup> | Nee | Ja <sup>5</sup> | Nee |
| Roamler | Ja | Ja | Nee | Ja | Nee |
| Salesforce-objecten | Ja | Ja | Nee | Nee | Nee |
| Salesforce-rapporten | Ja | Ja | Nee | Nee | Nee |
| SAP Business Warehouse-berichtenserver | Ja | Ja | Ja | Ja | Ja |
| SAP Business Warehouse-server | Ja | Ja | Ja | Ja | Ja |
| SAP HANA | Ja | Ja | Ja | Ja | Ja |
| SharePoint-map | Ja | Ja | Nee | Ja | Nee <sup>4</sup> |
| SharePoint-lijst | Ja | Ja | Nee | Ja | Nee <sup>4</sup> |
| SharePoint Online-lijst | Ja | Ja | Nee | Ja <sup>2</sup> | Nee |
| Smartsheet | Ja | Ja | Nee | Nee | Nee |
| Snowflake | Ja | Ja | Ja | Ja | Nee |
| Spark | Ja | Ja | Ja | Ja | Nee |
| SparkPost | Ja | Ja | Nee | Nee | Nee |
| SQL Server | Ja | Ja | Ja | Ja | Ja |
| SQL Server Analysis Services | Ja | Ja | Ja | Ja | Ja |
| Stripe | Ja | Ja | Nee | Nee | Nee |
| SurveyMonkey | Ja | Ja | Nee | Ja | Nee |
| SweetIQ | Ja | Ja | Nee | Nee | Nee |
| Sybase | Ja | Ja | Nee | Ja | Ja |
| TeamDesk | Ja | Ja | Nee | Ja | Nee |
| Tenforce | Ja | Ja | Nee | Nee | Nee |
| Teradata | Ja | Ja | Ja | Ja | Ja |
| Tekst/CSV | Ja | Ja | Nee | Ja | Nee <sup>4</sup> |
| Twilio | Ja | Ja | Nee | Nee | Nee |
| tyGraph | Ja | Ja | Nee | Nee | Nee |
| Vertica | Ja | Ja | Ja | Ja | Ja |
| Web | Ja | Ja | Nee | Ja | Ja <sup>6</sup> |
| Webtrends | Ja | Ja | Nee | Nee | Nee |
| Workforce Dimensions | Ja | Ja | Nee | Ja | Nee |
| XML | Ja | Ja | Nee | Ja | Nee <sup>4</sup> |
| Zendesk | Ja | Ja | Nee | Nee | Nee |
| | | | | | | | |

<sup>1</sup> Ondersteund met de [ACE OLEDB-provider](https://www.microsoft.com/download/details.aspx?id=54920), die is geïnstalleerd op hetzelfde apparaat als de gateway.

<sup>2</sup> Ondersteund met dezelfde M-functie als de on-premises versie, waardoor beperkte verificatieopties ontstaan (de gateway ondersteunt OAuth niet).

<sup>3</sup> Voor Excel 1997-2003-bestanden (.xls) is de [ACE OLEDB-provider](https://www.microsoft.com/download/details.aspx?id=54920) vereist.

<sup>4</sup> Vereist voor de on-premises versie van de technologie.

<sup>5</sup> Alleen ondersteund met de [persoonlijke gateway](service-gateway-personal-mode.md).

<sup>6</sup> Vereist voor .html-, .xls- en Access-databases

## <a name="single-sign-on-sso-for-directquery-sources"></a>Eenmalige aanmelding (SSO) voor DirectQuery-bronnen

Wanneer de optie voor eenmalige aanmelding is ingeschakeld en uw gebruikers toegang hebben tot rapporten die op de gegevensbron zijn gebouwd, verzendt Power BI hun geverifieerde Azure AD-referenties in de query's naar de onderliggende gegevensbron. Hierdoor kan Power BI rekening houden met de beveiligingsinstellingen die op het niveau van de gegevensbronnen zijn geconfigureerd.
De optie voor eenmalige aanmelding heeft effect op alle gegevenssets die gebruikmaken van deze gegevensbron. Het heeft geen invloed op de verificatiemethode die wordt gebruikt om scenario's te importeren. De volgende gegevensbronnen ondersteunen SSO (eenmalige aanmelding) voor verbindingen via DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) wordt niet ondersteund. Gebruikers die gebruik willen maken van SSO met DirectQuery, moeten worden uitgesloten van MFA.

## <a name="next-steps"></a>Volgende stappen

[Verbinding maken met gegevens in Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[DirectQuery gebruiken in Power BI](desktop-directquery-about.md)  
[SQL Server Analysis Services-livegegevens in Power BI](sql-server-analysis-services-tabular-data.md)  
[Wat is een on-premises gegevensgateway?](service-gateway-onprem.md)  
