---
title: Power BI-rapportgegevensbronnen in Power BI Report Server
description: Power BI-rapporten kunnen verbinding maken met een aantal gegevensbronnen. Afhankelijk van hoe de gegevens worden gebruikt, zijn er verschillende gegevensbronnen beschikbaar.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: fe8ad0b951fedb17a97007e48808d2bfd7467e88
ms.sourcegitcommit: 6c2c7a090b0826e3cfc3a897566e802857bbacc8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68808214"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI-rapportgegevensbronnen in Power BI Report Server
Power BI-rapporten kunnen verbinding maken met een aantal gegevensbronnen. Afhankelijk van hoe de gegevens worden gebruikt, zijn er verschillende gegevensbronnen beschikbaar. De gegevens kunnen worden geïmporteerd of de gegevens kunnen rechtstreeks worden opgevraagd rechtstreeks met DirectQuery of een liveverbinding met SQL Server Analysis Services.

Deze gegevensbronnen zijn specifiek voor Power BI-rapporten die in Power BI Report Server worden gebruikt. Zie [Data Sources Supported by Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) (Gegevensbronnen die worden ondersteund door Reporting Services) voor meer informatie over gegevensbronnen die worden ondersteund met gepagineerde rapporten (.rdl).

> [!IMPORTANT]
> Alle gegevensbronnen in een Power BI Desktop-rapport moeten het configureren van een geplande vernieuwing ondersteunen.
>  

## <a name="list-of-supported-data-sources"></a>Lijst met ondersteunde gegevensbronnen

Andere gegevensbronnen werken mogelijk ook, ondanks dat ze niet op de ondersteunde lijst staan.

| **Gegevensbron** | **In cache opgeslagen gegevens** | **Geplande vernieuwing** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server-database |Ja |Ja |Ja |
| SQL Server Analysis Services |Ja |Ja |Ja |
| Azure SQL Database |Ja |Ja |Ja |
| Azure SQL Data Warehouse |Ja |Ja |Ja |
| Excel |Ja |Ja |Nee |
| Access-database |Ja |Ja |Nee |
| Active Directory |Ja |Ja |Nee |
| Amazon Redshift |Ja |Nee |Nee |
| Azure Blob Storage |Ja |Ja |Nee |
| Azure Data Lake Store |Ja |Nee |Nee |
| Azure HDInsight (HDFS) |Ja |Nee |Nee |
| Azure HDInsight (Spark) |Ja |Ja |Nee |
| Azure Table Storage |Ja |Ja |Nee |
| Dynamics 365 (online) |Ja |Nee |Nee |
| Facebook |Ja |Nee |Nee |
| Map |Ja |Ja |Nee |
| Google Analytics |Ja |Nee |Nee |
| Hadoop-bestand (HDFS) |Ja |Nee |Nee |
| IBM DB2-database |Ja |Ja |Nee |
| Impala |Ja |Nee |Nee |
| JSON |Ja |Ja |Nee |
| Microsoft Exchange |Ja |Nee |Nee |
| Microsoft Exchange Online |Ja |Nee |Nee |
| MySQL-database |Ja |Ja |Nee |
| OData-feed |Ja |Ja |Nee |
| ODBC |Ja |Ja |Nee |
| OLE DB |Ja |Ja |Nee |
| Oracle Database |Ja |Ja |Ja |
| PostgreSQL-database |Ja |Ja |Nee |
| Power BI-service |Nee |Nee |Nee |
| R-script |Ja |Nee |Nee |
| Salesforce-objecten |Ja |Nee |Nee |
| Salesforce-rapporten |Ja |Nee |Nee |
| SAP Business Warehouse-server |Ja |Ja |Ja |
| SAP HANA-database |Ja |Ja |Ja |
| SharePoint-map (on-premises) |Ja |Ja |Nee |
| SharePoint-lijst (on-premises) |Ja |Ja |Nee |
| SharePoint Online-lijst |Ja |Nee |Nee |
| Snowflake |Ja |Nee |Nee |
| Sybase-database |Ja |Ja |Nee |
| Teradata-database |Ja |Ja |Ja |
| Tekst/CSV |Ja |Ja |Nee |
| Web |Ja |Ja |Nee |
| XML |Ja |Ja |Nee |
| appFigures (bèta) |Ja |Nee |Nee |
| Microsoft Azure Analysis Services-database |Ja |Nee |Ja |
| Azure Cosmos DB (bèta) |Ja |Nee |Nee |
| Azure HDInsight Spark (bèta) |Ja |Nee |Nee |
| Common Data Service (bèta) |Ja |Nee |Nee |
| comScore Digital Analytix (bèta) |Ja |Nee |Nee |
| Dynamics 365 for Customer Insights (bèta) |Ja |Nee |Nee |
| Dynamics 365 for Financials (bèta) |Ja |Nee |Nee |
| GitHub (bèta) |Ja |Nee |Nee |
| Google BigQuery (bèta) |Ja |Nee |Nee |
| IBM Informix-database (bèta) |Ja |Nee |Nee |
| IBM Netezza (bèta) |Ja |Nee |Nee |
| Kusto (bèta) |Ja |Nee |Nee |
| MailChimp (bèta) |Ja |Nee |Nee |
| Inzicht van Microsoft Azure-verbruik (bèta) |Ja |Nee |Nee |
| Mixpanel (bèta) |Ja |Nee |Nee |
| Planview Enterprise (bèta) |Ja |Nee |Nee |
| Projectplace (bèta) |Ja |Nee |Nee |
| QuickBooks Online (bèta) |Ja |Nee |Nee |
| Smartsheet |Ja |Nee |Nee |
| Spark (bèta) |Ja |Nee |Nee |
| SparkPost (bèta) |Ja |Nee |Nee |
| SQL Sentry (bèta) |Ja |Nee |Nee |
| Stripe (bèta) |Ja |Nee |Nee |
| SweetIQ (bèta) |Ja |Nee |Nee |
| Troux (bèta) |Ja |Nee |Nee |
| Twilio (bèta) |Ja |Nee |Nee |
| tyGraph (bèta) |Ja |Nee |Nee |
| Vertica (bèta) |Ja |Nee |Nee |
| Visual Studio Team Services-feed (bèta) |Ja |Nee |Nee |
| Webtrends (bèta) |Ja |Nee |Nee |
| Zendesk (bèta) |Ja |Nee |Nee |

> [!IMPORTANT]
> De beveiliging op rijniveau die is geconfigureerd voor de gegevensbron, moet werken voor DirectQuery (SQL Server, Azure SQL Database, Oracle en Teradata) en liveverbindingen, mits Kerberos goed is geconfigureerd in uw omgeving.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lijst met ondersteunde verificatiemethoden voor modelvernieuwing

Power BI Report Server biedt geen ondersteuning voor verificatie op basis van OAuth voor modelvernieuwing. Sommige gegevensbronnen, zoals Excel of Access-databases, maken gebruik van een afzonderlijke stap zoals Bestand of Web om verbinding te maken met gegevens.

| **Gegevensbron** | **Anonieme verificatie** | **Verificatie met sleutel** | **Gebruikersnaam en wachtwoord** | **Windows-verificatie** |
| --- | --- | --- | --- | --- |
| SQL Server-database |Nee |Nee |Ja |Ja |
| SQL Server Analysis Services |Nee |Nee |Ja |Ja |
| Web |Ja |Nee |Ja |Ja |
| Azure SQL Database |Nee |Nee |Ja |Nee |
| Azure SQL Data Warehouse |Nee |Nee |Ja |Nee |
| Active Directory |Nee |Nee |Ja |Ja |
| Amazon Redshift |Nee |Nee |Nee |Nee |
| Azure Blob Storage |Ja |Ja |Nee |Nee |
| Azure Data Lake Store |Nee |Nee |Nee |Nee |
| Azure HDInsight (HDFS) |Nee |Nee |Nee |Nee |
| Azure HDInsight (Spark) |Ja |Ja |Nee |Nee |
| Azure Table Storage |Nee |Ja |Nee |Nee |
| Dynamics 365 (online) |Nee |Nee |Nee |Nee |
| Facebook |Nee |Nee |Nee |Nee |
| Map |Nee |Nee |Nee |Ja |
| Google Analytics |Nee |Nee |Nee |Nee |
| Hadoop-bestand (HDFS) |Nee |Nee |Nee |Nee |
| IBM DB2-database |Nee |Nee |Ja |Ja |
| Impala |Nee |Nee |Nee |Nee |
| Microsoft Exchange |Nee |Nee |Nee |Nee |
| Microsoft Exchange Online |Nee |Nee |Nee |Nee |
| MySQL-database |Nee |Nee |Ja |Ja |
| OData-feed |Ja |Ja |Ja |Ja |
| ODBC |Ja |Nee |Ja |Ja |
| OLE DB |Ja |Nee |Ja |Ja |
| Oracle-database |Nee |Nee |Ja |Ja |
| PostgreSQL-database |Nee |Nee |Ja |Nee |
| Power BI-service |Nee |Nee |Nee |Nee |
| R-script |Nee |Nee |Nee |Nee |
| Salesforce-objecten |Nee |Nee |Nee |Nee |
| Salesforce-rapporten |Nee |Nee |Nee |Nee |
| SAP Business Warehouse-server |Nee |Nee |Ja |Nee |
| SAP HANA-database |Nee |Nee |Ja |Ja |
| SharePoint-map (on-premises) |Ja |Nee |Nee |Ja |
| SharePoint-lijst (on-premises) |Ja |Nee |Nee |Ja |
| SharePoint Online-lijst |Nee |Nee |Nee |Nee |
| Snowflake |Nee |Nee |Nee |Nee |
| Sybase-database |Nee |Nee |Ja |Ja |
| Teradata-database |Nee |Nee |Ja |Ja |
| appFigures (bèta) |Nee |Nee |Nee |Nee |
| SQL Server Analysis Services-database (bèta) |Nee |Nee |Nee |Nee |
| Azure Cosmos DB (bèta) |Nee |Nee |Nee |Nee |
| Azure HDInsight Spark (bèta) |Nee |Nee |Nee |Nee |
| Common Data Service (bèta) |Nee |Nee |Nee |Nee |
| comScore Digital Analytix (bèta) |Nee |Nee |Nee |Nee |
| Dynamics 365 for Customer Insights (bèta) |Nee |Nee |Nee |Nee |
| Dynamics 365 for Financials (bèta) |Nee |Nee |Nee |Nee |
| GitHub (bèta) |Nee |Nee |Nee |Nee |
| Google BigQuery (bèta) |Nee |Nee |Nee |Nee |
| IBM Informix-database (bèta) |Nee |Nee |Nee |Nee |
| IBM Netezza (bèta) |Nee |Nee |Nee |Nee |
| Kusto (bèta) |Nee |Nee |Nee |Nee |
| MailChimp (bèta) |Nee |Nee |Nee |Nee |
| Microsoft Azure Consumption Insights (bèta) |Nee |Nee |Nee |Nee |
| Mixpanel (bèta) |Nee |Nee |Nee |Nee |
| Planview Enterprise (bèta) |Nee |Nee |Nee |Nee |
| Projectplace (bèta) |Nee |Nee |Nee |Nee |
| QuickBooks Online (bèta) |Nee |Nee |Nee |Nee |
| Smartsheet |Nee |Nee |Nee |Nee |
| Spark (bèta) |Nee |Nee |Nee |Nee |
| SparkPost (bèta) |Nee |Nee |Nee |Nee |
| SQL Sentry (bèta) |Nee |Nee |Nee |Nee |
| Stripe (bèta) |Nee |Nee |Nee |Nee |
| SweetIQ (bèta) |Nee |Nee |Nee |Nee |
| Troux (bèta) |Nee |Nee |Nee |Nee |
| Twilio (bèta) |Nee |Nee |Nee |Nee |
| tyGraph (bèta) |Nee |Nee |Nee |Nee |
| Vertica (bèta) |Nee |Nee |Nee |Nee |
| Visual Studio-teamservices (bèta) |Nee |Nee |Nee |Nee |
| Webtrends (bèta) |Nee |Nee |Nee |Nee |
| Zendesk (bèta) |Nee |Nee |Nee |Nee |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lijst met ondersteunde verificatiemethoden voor DirectQuery

Power BI Report Server biedt geen ondersteuning voor verificatie op basis van OAuth voor DirectQuery.

| **Gegevensbron** | **Anonieme verificatie** | **Verificatie met sleutel** | **Gebruikersnaam en wachtwoord** | **Windows-verificatie** | **Geïntegreerde Windows-verificatie** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-database |Nee |Nee |Ja |Ja |Ja |
| SQL Server Analysis Services |Nee |Nee |Ja |Ja |Ja |
| Azure SQL Database |Nee |Nee |Ja |Nee |Nee |
| Azure SQL Data Warehouse |Nee |Nee |Ja |Nee |Nee |
| Oracle-database |Nee |Nee |Ja |Ja |Ja |
| SAP Business Warehouse-server |Nee |Nee |Ja |Nee |Nee |
| SAP HANA-database |Nee |Nee |Ja |Ja |Nee |
| Teradata-database |Nee |Nee |Ja |Ja |Ja |


## <a name="next-steps"></a>Volgende stappen
Nu u verbinding hebt met de gegevensbron, kunt u [een Power BI-rapport maken](quickstart-create-powerbi-report.md) op basis van de gegeven in die gegevensbron.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

