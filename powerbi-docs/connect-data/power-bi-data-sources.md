---
title: Power BI-gegevensbronnen
description: In dit artikel staan de gegevensbronnen die door Power BI worden ondersteund, inclusief informatie over DirectQuery en de on-premises gegevensgateway.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/07/2020
ms.author: davidi
ms.openlocfilehash: 918b9a98d66a1c739421433d35f593dc74d19773
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91981476"
---
# <a name="power-bi-data-sources"></a>Power BI-gegevensbronnen

In de volgende tabel staan de gegevensbronnen die door Power BI worden ondersteund voor gegevenssets, inclusief informatie over DirectQuery en de on-premises gegevensgateway. Zie [Verbinding maken met gegevensbronnen voor Power BI-gegevensstromen](../transform-model/service-dataflows-data-sources.md) voor meer informatie over gegevensstromen.

| Gegevensbron | Verbinding maken via Power BI Desktop | Verbinding maken en vernieuwen via de service | DirectQuery/liveverbinding | Gateway (ondersteund) | Gateway (vereist) | Power BI-gegevensstromen |
|---|---|---|---|---|---|---|---|
| Access-database | Ja | Ja | Nee | Ja <sup>1</sup> | Ja | Ja |
| Active Directory | Ja | Ja | Nee | Ja | Ja | Ja |
| Adobe Analytics | Ja | Ja | Nee | Nee | Nee | Nee |
| Amazon Redshift | Ja | Ja | Ja | Ja | Nee | Ja |
| appFigures | Ja | Ja | Nee | Nee | Nee | Nee |
| AtScale-kubussen | Ja | Ja | Ja | Ja | Nee | Nee |
| Azure Analysis Services | Ja | Ja | Ja | Nee | Nee | Nee |
| Azure Blob Storage | Ja | Ja | Nee | Ja | Nee | Ja |
| Azure Cosmos DB | Ja | Ja | Nee | Nee | Nee | Nee |
| Azure Cost Management | Ja | Ja | Nee | Nee | Nee | Nee |
| Azure Data Explorer (kusto) | Ja | Ja | Ja | Ja | Nee | Ja |
| Azure Data Lake Storage Gen1 | Ja | Ja | Nee | Nee | Nee | Nee |
| Azure Data Lake Storage Gen2 | Ja | Ja | Nee | Ja | Nee | Ja |
| Azure DevOps | Ja | Ja | Nee | Nee | Nee | Nee |
| Azure DevOps Server | Ja | Ja | Nee | Ja | Ja | Nee |
| Azure HDInsight (HDFS) | Ja | Ja | Nee | Nee | Nee | Nee |
| Azure HDInsight Spark | Ja | Ja | Ja | Nee | Nee | Ja |
| Azure SQL Database | Ja | Ja | Ja | Ja | Nee | Ja |
| Azure SQL Data Warehouse | Ja | Ja | Ja | Ja | Nee | Ja |
| Azure Table Storage | Ja | Ja | Nee | Ja | Nee | Ja |
| BI-connector | Ja | Ja | Ja | Ja | Ja | Nee |
| BI360 - Budgettering en financiële rapportage | Ja | Ja | Nee | Nee | Nee | Nee |
| Common Data Service | Ja | Ja | Nee | Nee | Nee | Ja |
| Data.World - Get Dataset | Ja | Ja | Nee | Nee | Nee | Nee |
| Denodo | Ja | Ja | Ja | Ja | Ja | Nee |
| Dremio | Ja | Ja | Ja | Ja | Ja | Nee |
| Dynamics 365 (online) | Ja | Ja | Nee | Nee | Nee | Nee |
| Dynamics 365 Business Central | Ja | Ja | Nee | Nee | Nee | Nee |
| Dynamics 365 Business Central (on-premises) | Ja | Ja | Nee | Nee | Nee | Nee |
| Dynamics 365 Customer Insights | Ja | Ja | Nee | Nee | Nee | Nee |
| Dynamics NAV | Ja | Ja | Nee | Nee | Nee | Nee |
| Emigo Data Source | Ja | Ja | Nee | Nee | Nee | Nee |
| Entersoft Business Suite | Ja | Ja | Nee | Nee | Nee | Nee |
| Essbase | Ja | Ja | Ja | Ja | Ja | Nee |
| Exasol | Ja | Ja | Ja | Ja | Ja | Nee |
| Excel | Ja <sup>3</sup> | Ja <sup>3</sup> | Nee | Ja <sup>3</sup> | Nee <sup>4</sup> | Ja |
| Facebook | Ja | Ja | Nee | Nee | Nee | Nee |
| Bestand | Ja | Ja | Nee | Ja | Ja | Ja |
| Map | Ja | Ja | Nee | Ja | Ja | Ja |
| GitHub | Ja | Ja | Nee | Nee | Nee | Nee |
| Google Analytics | Ja | Ja | Nee | Nee | Nee | Nee |
| Google BigQuery | Ja | Ja | Ja | Nee | Nee | Ja |
| Hadoop-bestand (HDFS) | Ja | Nee | Nee | Nee | Nee | Nee |
| HDInsight Interactive Query | Ja | Ja | Ja | Nee | Nee | Nee |
| IBM DB2 | Ja | Ja | Ja | Ja | Nee | Ja |
| IBM Informix-database | Ja | Ja | Nee | Ja | Nee | Nee |
| IBM Netezza | Ja | Ja | Ja | Ja | Ja | Nee |
| Impala | Ja | Ja | Ja | Ja | Ja | Ja |
| Indexima | Ja | Ja | Ja | Ja | Ja | Nee |
| Industrial App Store | Ja | Ja | Nee | Nee | Nee | Nee |
| Information Grid | Ja | Ja | Nee | Nee | Nee | Nee |
| InterSystems IRIS | Ja | Ja | Ja | Ja | Ja | Nee |
| Intune-datawarehouse | Ja | Ja | Nee | Nee | Nee | Nee |
| Jethro ODBC | Ja | Ja | Ja | Ja | Ja | Nee |
| JSON | Ja | Ja | Nee | Ja** | Nee <sup>4</sup> | Ja |
| Kyligence Enterprise | Ja | Ja | Ja | Ja | Ja | Nee |
| MailChimp | Ja | Ja | Nee | Nee | Nee | Nee |
| Marketo | Ja | Ja | Nee | Nee | Nee | Nee |
| MarkLogic ODBC | Ja | Ja | Ja | Ja | Ja | Nee |
| Inzichten in Microsoft Azure-verbruik | Ja | Ja | Nee | Nee | Nee | Nee |
| Microsoft Exchange | Ja | Ja | Nee | Ja | Nee | Nee |
| Microsoft Exchange Online | Ja | Ja | Nee | Nee | Nee | Ja |
| Microsoft Graph Security | Ja | Ja | Nee | Ja | Nee | Nee |
| Mixpanel | Ja | Ja | Nee | Nee | Nee | Nee |
| MySQL | Ja | Ja | Nee | Ja | Ja | Ja |
| OData | Ja | Ja <sup>7</sup> | Nee | Ja | Nee | Ja |
| ODBC | Ja | Ja | Nee | Ja | Ja | Ja |
| OLEDB | Ja | Ja | Nee | Ja | Ja | Nee |
| Oracle | Ja | Ja | Ja | Ja | Ja | Ja |
| Paxata <sup>8</sup> | Ja | Ja | Nee | Ja | Nee | Nee |
| PDF | Ja | Ja | Nee | Ja | Nee <sup>4</sup> | Ja |
| Planview Enterprise One - CTM | Ja | Ja | Nee | Nee | Nee | Nee |
| Planview Enterprise One - PRM | Ja | Ja | Nee | Nee | Nee | Nee |
| Planview Projectplace | Ja | Ja | Nee | Nee | Nee | Nee |
| PostgreSQL | Ja | Ja | Ja | Ja | Nee | Ja |
| Power BI-gegevensstromen | Ja | Ja | Nee | Nee | Nee | Ja |
| Power BI-gegevenssets | Ja | Ja | Ja | Nee | Nee | Nee |
| Power Platform-gegevensstromen | Ja | Ja | Nee | Nee | Nee | Ja |
| Python-script | Ja | Ja <sup>5</sup> | Nee | Ja <sup>5</sup> | Ja | Nee |
| QubolePresto | Ja | Ja | Ja | Ja | Ja | Nee |
| Quick Base | Ja | Ja | Nee | Ja | Ja | Nee |
| QuickBooks Online | Ja | Ja | Nee | Nee | Nee | Nee |
| R-script | Ja | Ja <sup>5</sup> | Nee | Ja <sup>5</sup> | Nee | Nee |
| Roamler | Ja | Ja | Nee | Ja | Nee | Nee |
| Salesforce-objecten | Ja | Ja | Nee | Nee | Nee | Ja |
| Salesforce-rapporten | Ja | Ja | Nee | Nee | Nee | Ja |
| SAP Business Warehouse-berichtenserver | Ja | Ja | Ja | Ja | Ja | Ja |
| SAP Business Warehouse-server | Ja | Ja | Ja | Ja | Ja | Ja |
| SAP HANA | Ja | Ja | Ja | Ja | Ja | Ja |
| SharePoint-map | Ja | Ja | Nee | Ja | Nee <sup>4</sup> | Ja |
| SharePoint-lijst | Ja | Ja | Nee | Ja | Nee <sup>4</sup> | Ja |
| SharePoint Online-lijst | Ja | Ja | Nee | Ja | Nee | Ja |
| Smartsheet | Ja | Ja | Nee | Nee | Nee | Ja |
| Snowflake | Ja | Ja | Ja | Ja | Nee | Ja |
| Spark | Ja | Ja | Ja | Ja | Nee | Ja |
| SparkPost | Ja | Ja | Nee | Nee | Nee | Nee |
| SQL Server | Ja | Ja | Ja | Ja | Ja | Ja |
| SQL Server Analysis Services | Ja | Ja | Ja | Ja | Ja | Nee |
| Stripe | Ja | Ja | Nee | Nee | Nee | Nee |
| SurveyMonkey | Ja | Ja | Nee | Ja | Nee | Nee |
| SweetIQ | Ja | Ja | Nee | Nee | Nee | Nee |
| Sybase | Ja | Ja | Nee | Ja | Ja | Ja |
| TeamDesk | Ja | Ja | Nee | Ja | Nee | Nee |
| Tenforce | Ja | Ja | Nee | Nee | Nee | Nee |
| Teradata | Ja | Ja | Ja | Ja | Ja | Ja |
| Tekst/CSV | Ja | Ja | Nee | Ja | Nee <sup>4</sup> | Ja |
| Twilio | Ja | Ja | Nee | Nee | Nee | Nee |
| tyGraph | Ja | Ja | Nee | Nee | Nee | Nee |
| Vertica | Ja | Ja | Ja | Ja | Ja | Ja |
| Web | Ja | Ja | Nee | Ja | Ja <sup>6</sup> | Ja |
| Webtrends | Ja | Ja | Nee | Nee | Nee | Nee |
| Workforce Dimensions | Ja | Ja | Nee | Ja | Nee | Nee |
| XML | Ja | Ja | Nee | Ja | Nee <sup>4</sup> | Ja |
| Zendesk | Ja | Ja | Nee | Nee | Nee | Nee |
| | | | | | | | |

<sup>1</sup> Ondersteund met de [ACE OLEDB-provider](https://www.microsoft.com/download/details.aspx?id=54920), die is geïnstalleerd op hetzelfde apparaat als de gateway.

<sup>3</sup> Voor Excel 1997-2003-bestanden (.xls) is de [ACE OLEDB-provider](https://www.microsoft.com/download/details.aspx?id=54920) vereist.

<sup>4</sup> Vereist voor de on-premises versie van de technologie.

<sup>5</sup> Alleen ondersteund met de [persoonlijke gateway](service-gateway-personal-mode.md).

<sup>6</sup> Vereist voor .html-, .xls- en Access-databases

<sup>7</sup> Power BI-service biedt geen ondersteuning voor OData-feeds waarvoor verificatie is vereist.

<sup>8</sup> Paxata wordt ondersteund in de versie van Power BI Desktop die is geoptimaliseerd voor Power BI Report Server. Het wordt niet ondersteund in Power BI-rapporten die zijn gepubliceerd in Power BI Report Server. Zie [Power BI-rapportgegevensbronnen in Power BI Report Server](../report-server/data-sources.md) voor de lijst met ondersteunde gegevensbronnen.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

- Voor veel gegevensconnectors in Power BI Desktop is Internet Explorer 10 (of nieuwer) vereist voor verificatie. 
- Sommige gegevensbronnen zijn beschikbaar in Power BI Desktop en geoptimaliseerd voor Power BI Report Server, maar worden niet ondersteund wanneer ze worden gepubliceerd in Power BI Report Server. Zie [Power BI-rapportgegevensbronnen in Power BI Report Server](../report-server/data-sources.md) voor de lijst met ondersteunde gegevensbronnen.

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
[Power BI-rapportgegevensbronnen in Power BI Report Server](../report-server/data-sources.md)
