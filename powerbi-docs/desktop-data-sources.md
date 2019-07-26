---
title: Gegevensbronnen in Power BI Desktop
description: Gegevensbronnen in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/15/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8d8e77d8fe4ebea5b457ba282014bb8dc738191a
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324846"
---
# <a name="data-sources-in-power-bi-desktop"></a>Gegevensbronnen in Power BI Desktop
Met Power BI Desktop kunt u verbinding maken met gegevens uit veel verschillende bronnen. Onderaan op deze pagina vindt u een volledige lijst met beschikbare gegevensbronnen.

Als u verbinding wilt maken met gegevens, selecteert u **Gegevens ophalen** op het lint **Start**. Als u de pijl-omlaag selecteert of de tekst **Gegevens ophalen** op de knop, wordt het menu met **meest voorkomende** gegevenstypen weergegeven, zoals in de volgende afbeelding:

![Gegevens ophalen in Power BI](media/desktop-data-sources/data-sources_01.png)

Als u **Meer...** selecteert in het menu **Meest voorkomend**, wordt het venster **Gegevens ophalen** weergegeven. U kunt het venster **Gegevens ophalen** ook weergeven (en het menu **Meest voorkomend** omzeilen) door de **pictogramknop** **Gegevens ophalen** rechtstreeks te selecteren.

![Knop Gegevens ophalen](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> Het Power BI-team breidt de beschikbare gegevensbronnen voor **Power BI Desktop** en de **Power BI-service** voortdurend uit. Daarom ziet u vaak vroege versies van gegevensbronnen waaraan wordt gewerkt en die worden aangeduid als *bèta* of *preview*. Een gegevensbron die wordt gemarkeerd als *bèta* of *preview*, heeft beperkte ondersteuning en functionaliteit en dient niet te worden gebruikt in een productieomgeving.

## <a name="data-sources"></a>Gegevensbronnen
Gegevenstypen zijn ingedeeld in de volgende categorieën:

* Alle
* Bestand
* Database
* Power BI
* Azure
* Onlineservices
* Overige

De categorie **Alle** omvat alle gegevenstypen uit alle categorieën.

De categorie **Bestand** biedt de volgende gegevensverbindingen:

* Excel
* Tekst/CSV
* XML
* JSON
* Map
* PDF
* SharePoint-map

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Bestand**.

![Gegevens ophalen > Bestand](media/desktop-data-sources/data-sources_03.png)

De categorie **Database** biedt de volgende gegevensverbindingen:

* SQL Server-database
* Access-database
* SQL Server Analysis Services-database
* Oracle-database
* IBM DB2-database
* IBM Informix-database (bèta)
* IBM Netezza
* MySQL-database
* PostgreSQL-database
* Sybase-database
* Teradata-database
* SAP HANA-database
* SAP Business Warehouse-toepassingsserver
* SAP Business Warehouse-berichtenserver
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* AtScale-kubussen (bèta)
* BI-connector
* Dremio
* Exasol
* Indexima (bèta)
* InterSystems IRIS (bèta)
* Jethro (bèta)
* Kyligence Enterprise (bèta)
* MarkLogic (bèta)

> [!NOTE]
> Sommige databaseconnectors moet u eerst inschakelen door **Bestand > Opties en instellingen > Opties** te selecteren en vervolgens **Voorbeeldfuncties** en de connector in te schakelen. Als u geen van de hierboven genoemde connectors ziet en ze wel wilt gebruiken, controleert u de instellingen voor **Voorbeeldfuncties**. Houd er ook rekening mee dat een gegevensbron die wordt gemarkeerd als *bèta* of *preview*, beperkte ondersteuning en functionaliteit heeft en niet dient te worden gebruikt in een productieomgeving.

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Database**.

![Gegevens ophalen > Databases](media/desktop-data-sources/data-sources_04.png)

De categorie **Power BI** biedt de volgende gegevensverbindingen:

* Power BI-gegevenssets
* Power BI-gegevensstromen

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Power BI**.

![Gegevens ophalen > Power BI](media/desktop-data-sources/data-sources_05.png)

De categorie **Azure** biedt de volgende gegevensverbindingen:

* Azure SQL-database
* Azure SQL Data Warehouse
* Microsoft Azure Analysis Services-database
* Azure Blob Storage
* Azure-tabelopslag
* Azure Cosmos DB (bèta)
* Azure Data Lake Storage Gen2 (Bèta)
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Data Explorer (Kusto)
* Azure Cost Management (bèta)

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Azure**.

![Gegevens ophalen > Azure](media/desktop-data-sources/data-sources_06.png)

De categorie **Onlineservices** biedt de volgende gegevensverbindingen:

* SharePoint Online-lijst
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (on-premises)
* Common Data Service
* Microsoft Azure Consumption Insights (bèta)
* Azure DevOps (bèta)
* Azure DevOps Server (bèta)
* Salesforce-objecten
* Salesforce-rapporten
* Google Analytics
* Adobe Analytics
* appFigures (bèta)
* Data.World - Gegevensset ophalen (bèta)
* Facebook
* GitHub (bèta)
* MailChimp (bèta)
* Marketo (bèta)
* Mixpanel (bèta)
* Planview Enterprise One - PRM (bèta)
* Planview Projectplace (bèta)
* QuickBooks Online (bèta)
* Smartsheet
* SparkPost (bèta)
* Stripe (bèta)
* SweetIQ (bèta)
* Planview Enterprise One - CMT (bèta)
* Twilio (bèta)
* tyGraph (bèta)
* Webtrends (bèta)
* Zendesk (bèta)
* Emigo Data Source (bèta)
* Entersoft Business Suite (bèta)
* Industrial App Store
* Intune Data Warehouse (bèta)
* Microsoft Graph Security (bèta)
* Quick Base
* TeamDesk (bèta)
* Dynamics 365 Customer Insights (Bèta)

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Onlineservices**.

![Gegevens ophalen > Onlineservices](media/desktop-data-sources/data-sources_07.png)

De categorie **Overige** biedt de volgende gegevensverbindingen:

* Web
* SharePoint-lijst
* OData-feed
* Active Directory
* Microsoft Exchange
* Hadoop-bestand (HDFS)
* Spark
* R-script
* Python-script
* ODBC
* OLE DB
* BI360 - Budgeting & Financial Reporting (bèta)
* Denado
* Information Grid (bèta)
* Paxata 
* QubolePresto (bèta)
* Roamler (bèta)
* SurveyMonkey (bèta)
* Tenforce (Smart)List (bèta)
* Workforce Dimensions (bèta)
* Lege query

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Overige**.

![Gegevens ophalen > Overige](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> Op dit moment is het niet mogelijk om verbinding te maken met aangepaste gegevensbronnen die zijn beveiligd met Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Verbinding maken met een gegevensbron
Als u verbinding wilt maken met een gegevensbron, selecteert u de gegevensbron in het venster **Gegevens ophalen** en selecteert u **Verbinding maken**. In de volgende afbeelding is **Web** geselecteerd in de categorie **Overige**.

![Verbinding maken met web](media/desktop-data-sources/data-sources_08.png)

Er wordt een verbindingsvenster weergegeven dat specifiek is voor het type gegevensverbinding. Als referenties zijn vereist, wordt u gevraagd ze op te geven. In de volgende afbeelding ziet u hoe een URL wordt ingevoerd om verbinding te maken met een webgegevensbron.

![Web-URL invoeren](media/desktop-data-sources/datasources_fromwebbox.png)

Nadat u de URL of de gegevens voor de bronverbinding hebt ingevoerd, selecteert u **OK**. Power BI Desktop maakt de verbinding met de gegevensbron en toont de beschikbare gegevensbronnen in de **Navigator**.

![Navigator-scherm](media/desktop-data-sources/datasources_fromnavigatordialog.png)

U kunt de gegevens laden door de knop **Laden** onderaan in het deelvenster **Navigator** te selecteren of de query bewerken voordat gegevens worden geladen door de knop **Bewerken** te selecteren.

Dat is alles wat u hoeft te weten om verbinding te maken met gegevensbronnen in Power BI Desktop! Probeer verbinding te maken met onze groeiende lijst gegevensbronnen en kom regelmatig terug. We blijven deze lijst voortdurend uitbreiden.

## <a name="next-steps"></a>Volgende stappen
U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Query Overview with Power BI Desktop](desktop-query-overview.md) (Queryoverzicht met Power BI Desktop)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Common Query Tasks in Power BI Desktop](desktop-common-query-tasks.md) (Algemene querytaken in Power BI Desktop)    
