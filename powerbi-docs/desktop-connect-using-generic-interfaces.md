---
title: Verbinding met gegevens maken via algemene interfaces in Power BI Desktop
description: Lees hoe u verbinding maakt met verschillende gegevensbronnen via algemene interfaces in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eaf2e7fed056653f2ee44e25b493e6b5e170a8dd
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761451"
---
# <a name="connect-to-data-by-using-power-bi-desktop-generic-interfaces"></a>Verbinding met gegevens maken via algemene interfaces in Power BI Desktop 

U kunt verbinding maken met een groot aantal verschillende gegevensbronnen in **Power BI Desktop**, waarbij u ingebouwde gegevensconnectors gebruikt, variërend van **Access-databases** tot **Zendesk**-bronnen, zoals weergegeven in het venster **Gegevens ophalen**. U kunt ook verbinding maken met allerlei *andere* gegevensbronnen, om zo uw verbindingsopties verder uit te breiden, met behulp van de algemene interfaces (zoals **ODBC** of **REST API's**) die zijn ingebouwd in **Power BI Desktop**.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_1.png)

## <a name="power-bi-desktop-data-interfaces"></a>Gegevensinterfaces in Power BI Desktop
**Power BI Desktop** omvat een groeiende verzameling gegevensconnectors die zijn ontworpen om verbinding te maken met een specifieke gegevensbron. De gegevensconnector **SharePoint-lijst** biedt bijvoorbeeld specifieke velden en ondersteunende informatie tijdens de verbinding die zijn ontworpen voor **SharePoint-lijsten**. Dat geldt ook voor andere gegevensbronnen in het venster dat wordt weergegeven wanneer u **Gegevens ophalen > Meer...**  selecteert (zoals in de vorige afbeelding).

Daarnaast kunt u in **Power BI Desktop** verbinding maken met gegevensbronnen die niet worden aangegeven in de lijsten bij **Gegevens ophalen** door een van de volgende algemene gegevensinterfaces te gebruiken:

* **ODBC**
* **OLE DB**
* **OData**
* **REST-API's**
* **R-scripts**

Als u in het verbindingsvensters die deze algemene interfaces bieden, de juiste parameters opgeeft, neemt het aantal gegevensbronnen waartoe u toegang hebt en dat u kunt gebruiken in **Power BI Desktop** aanzienlijk toe.

In de volgende secties vindt u lijsten met gegevensbronnen die toegankelijk via deze algemene interfaces.

Kunt u de gegevensbron die u wilt gebruiken met **Power BI Desktop** niet vinden? Verzend uw idee naar de lijst van het Power BI-team [met ideeën en aanvragen](https://ideas.powerbi.com/).

## <a name="data-sources-accessible-through-odbc"></a>Gegevensbronnen die toegankelijk zijn via ODBC
Met de **ODBC**-connector in **Power BI Desktop** kunt u gegevens importeren uit elk ODBC-stuurprogramma van derden door eenvoudig de **naam van de gegevensbron (DSN)** of een  *verbindingsreeks* op te geven. Desgewenst kunt u ook een SQL-instructie opgeven die wordt uitgevoerd door het ODBC-stuurprogramma.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_2.png)

De volgende lijst bevat enkele voorbeelden van gegevensbronnen waarmee **Power BI Desktop** verbinding kan maken met behulp van de algemene **ODBC**-interface.

| Algemene Power BI Desktop-connector | Externe gegevensbron | Koppeling naar meer informatie |
| --- | --- | --- |
| ODBC |Cassandra |[ODBC-stuurprogramma voor Cassandra](https://www.simba.com/drivers/cassandra-odbc-jdbc/) |
| ODBC |Couchbase DB |[Couchbase en Power BI](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |
| ODBC |DynamoDB |[ODBC-stuurprogramma voor DynamoDB](https://www.simba.com/drivers/dynamodb-odbc-jdbc/) |
| ODBC |Google BigQuery |[ODBC-stuurprogramma voor BigQuery](https://www.simba.com/drivers/bigquery-odbc-jdbc/) |
| ODBC |HBase |[ODBC-stuurprogramma voor HBase](https://www.simba.com/drivers/hbase-odbc-jdbc/) |
| ODBC |Hive |[ODBC-stuurprogramma voor Hive](https://www.simba.com/drivers/hive-odbc-jdbc/) |
| ODBC |IBM Netezza |[Informatie over IBM Netezza](https://www.ibm.com/support/knowledgecenter/SSULQD_7.2.1/com.ibm.nz.datacon.doc/c_datacon_plg_overview.html) |
| ODBC |Presto |[ODBC-stuurprogramma voor Presto](https://www.simba.com/drivers/presto-odbc-jdbc/) |
| ODBC |Project Online |[Artikel over Project Online](desktop-project-online-connect-to-data.md) |
| ODBC |Progress OpenEdge |[Blogbericht over het ODBC-stuurprogramma voor Progress OpenEdge](https://www.progress.com/blogs/connect-microsoft-power-bi-to-openedge-via-odbc-driver) |

## <a name="data-sources-accessible-through-ole-db"></a>Gegevensbronnen die toegankelijk zijn via OLE DB
Met de **OLE DB**-connector in **Power BI Desktop** kunt u gegevens importeren uit elk OLE DB-stuurprogramma van derden door eenvoudig een *verbindingsreeks* op te geven. Desgewenst kunt u ook een SQL-instructie opgeven die wordt uitgevoerd door het OLE DB-stuurprogramma.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_3.png)

De volgende lijst bevat enkele voorbeelden van gegevensbronnen waarmee **Power BI Desktop** verbinding kan maken met behulp van de algemene **OLE DB**-interface.

| Algemene Power BI Desktop-connector | Externe gegevensbron | Koppeling naar meer informatie |
| --- | --- | --- |
| OLE DB |SAS OLE DB |[SAS-provider voor OLE DB](https://support.sas.com/downloads/package.htm?pid=648) |
| OLE DB |Sybase OLE DB |[Sybase-provider voor OLE DB](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.infocenter.dc35888.1550/doc/html/jon1256941734395.html) |

## <a name="data-sources-accessible-through-odata"></a>Gegevensbronnen die toegankelijk zijn via OData
Met de **OData**-connector in **Power BI Desktop** kunt u gegevens importeren van elke **OData**-URL door de **OData**-URL eenvoudig te typen of te plakken. U kunt meerdere URL-onderdelen toevoegen door die koppelingen te typen of te plakken in de tekstvakken in het venster **OData-feed**.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_4.png)

De volgende lijst bevat enkele voorbeelden van gegevensbronnen waarmee **Power BI Desktop** verbinding kan maken met behulp van de algemene **OData**-interface.

| Algemene Power BI Desktop-connector | Externe gegevensbron | Koppeling naar meer informatie |
| --- | --- | --- |
| OData |Binnenkort beschikbaar |Kom binnenkort terug voor OData-gegevensbronnen. |

## <a name="data-sources-accessible-through-rest-apis"></a>Gegevensbronnen die toegankelijk zijn via REST-API's
U kunt verbinding maken met gegevensbronnen met behulp van de **REST-API's** en daarmee gegevens gebruiken uit allerlei soorten gegevensbronnen die **REST** ondersteunen.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_5.png)

De volgende lijst bevat enkele voorbeelden van gegevensbronnen waarmee **Power BI Desktop** verbinding kan maken met behulp van de algemene interface voor **REST-API's**.

| Algemene Power BI Desktop-connector | Externe gegevensbron | Koppeling naar meer informatie |
| --- | --- | --- |
| REST-API's |Couchbase DB |[Informatie over Couchbase REST API](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |

## <a name="data-sources-accessible-through-r-script"></a>Gegevensbronnen die toegankelijk zijn via R-scripts
U kunt **R-scripts** gebruiken om toegang te krijgen tot gegevensbronnen en die gegevens gebruiken in **Power BI Desktop**.

![](media/desktop-connect-using-generic-interfaces/r-scripts-2.png)

De volgende lijst bevat enkele voorbeelden van gegevensbronnen waarmee **Power BI Desktop** verbinding kan maken met behulp van de algemene interface van **R-scripts**.

| Algemene Power BI Desktop-connector | Externe gegevensbron | Koppeling naar meer informatie |
| --- | --- | --- |
| R-script |SAS-bestanden |[Richtlijnen voor R-scripts van CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R-script |SPSS-bestanden |[Richtlijnen voor R-scripts van CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R-script |Statistische R-bestanden |[Richtlijnen voor R-scripts van CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |

## <a name="next-steps"></a>Volgende stappen
Met **Power BI Desktop** kunt u verbinding maken met allerlei gegevensbronnen. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   

