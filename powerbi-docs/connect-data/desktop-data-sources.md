---
title: Gegevensbronnen in Power BI Desktop
description: Gegevensbronnen in Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 038d0fc4b136f89db290010289d24ee41454c9ea
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353330"
---
# <a name="data-sources-in-power-bi-desktop"></a>Gegevensbronnen in Power BI Desktop

Met Power BI Desktop kunt u verbinding maken met gegevens uit veel verschillende bronnen. Zie [Power BI-gegevensbronnen](power-bi-data-sources.md) voor een volledige lijst met beschikbare gegevensbronnen.

U maakt verbinding met gegevens met behulp van het lint **Start**. Als u het menu **Meest voorkomend** met gegevenstypen wilt weergeven, selecteert u het knoplabel of de pijl omlaag van **Gegevens ophalen**.

![Menu Meest voorkomend met gegevenstypen, Gegevens ophalen in Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Als u naar het dialoogvenster **Gegevens ophalen** wilt gaan, geeft u het menu **Meest voorkomend** met gegevenstypen weer en selecteert u **Meer**. U kunt het dialoogvenster **Gegevens ophalen** ook weergeven (en het menu **Meest voorkomend** omzeilen) door het pictogram **Gegevens ophalen** rechtstreeks te selecteren.

![Knop Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Het Power BI-team breidt de beschikbare gegevensbronnen voor Power BI Desktop en de Power BI-service voortdurend uit. Daarom ziet u vaak vroege versies van gegevensbronnen waaraan wordt gewerkt en die worden aangeduid als **bèta** of **preview**. Een gegevensbron die is gemarkeerd als **bèta** of **preview**, heeft beperkte ondersteuning en functionaliteit en dient niet te worden gebruikt in een productieomgeving. Daarnaast is het mogelijk dat gegevensbronnen die als **bèta** of **preview** voor Power BI Desktop zijn gemarkeerd, pas beschikbaar zijn voor gebruik in de Power BI-service of in andere Microsoft-services als de gegevensbron algemeen beschikbaar is.

> [!NOTE]
> Voor veel gegevensconnectors in Power BI Desktop is Internet Explorer 10 (of nieuwer) vereist voor verificatie. 


## <a name="data-sources"></a>Gegevensbronnen

In het dialoogvenster **Gegevens ophalen** zijn gegevenstypen ingedeeld in de volgende categorieën:

* Alles
* Bestand
* Database
* Power Platform
* Azure
* Onlineservices
* Overige

De categorie **Alle** omvat alle gegevenstypen uit alle categorieën.

### <a name="file-data-sources"></a>Bestandsgegevensbronnen

De categorie **Bestand** biedt de volgende gegevensverbindingen:

* Excel
* Tekst/CSV
* XML
* JSON
* Map
* PDF
* SharePoint-map

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Bestand**.

![Bestandsgegevensbronnen, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Databasegegevensbronnen

De categorie **Database** biedt de volgende gegevensverbindingen:

* SQL Server-database
* Access-database
* SQL Server Analysis Services-database
* Oracle-database
* IBM Db2-database
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
* AtScale-kubussen
* Data Virtuality LDW (bèta)
* Denodo
* Dremio
* Exasol
* Indexima
* InterSystems IRIS (bèta)
* Jethro (bèta)
* Kyligence
* Linkar PICK Style/MultiValue Databases (Beta)
* MariaDB (bèta)
* MarkLogic
* BI-connector
* Actian (bèta)

> [!NOTE]
> Sommige databaseconnectors moet u eerst inschakelen door **Bestand > Opties en instellingen > Opties** te selecteren en vervolgens **Voorbeeldfuncties** en de connector in te schakelen. Als u geen van de hierboven genoemde connectors ziet en ze wel wilt gebruiken, controleert u de instellingen voor **Voorbeeldfuncties**. Houd er ook rekening mee dat een gegevensbron die wordt gemarkeerd als *bèta* of *preview*, beperkte ondersteuning en functionaliteit heeft en niet dient te worden gebruikt in een productieomgeving.

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Database**.

![Databasegegevensbronnen, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Power Platform-gegevensbronnen

De categorie **Power Platform** biedt de volgende gegevensverbindingen:

* Power BI-gegevenssets
* Power BI-gegevensstromen
* Microsoft Dataverse
* Power Platform-gegevensstromen (bèta)

In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Power Platform**.

![Power Platform-gegevensbronnen, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Azure-gegevensbronnen

De categorie **Azure** biedt de volgende gegevensverbindingen:

* Azure SQL-database
* Azure Synapse Analytics (SQL DW)
* Microsoft Azure Analysis Services-database
* Azure Database for PostgreSQL
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Explorer (Kusto)
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Cost Management
* Azure Databricks
* Azure Time Series Insights (Bèta)


In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Azure**.

![Azure-gegevensbronnen, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Gegevensbronnen voor onlineservices

De categorie **Onlineservices** biedt de volgende gegevensverbindingen:

* SharePoint Online-lijst
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (on-premises)
* Microsoft Azure Consumption Insights (bèta)
* Azure DevOps (alleen Boards)
* Azure DevOps Server (alleen Boards)
* Salesforce-objecten
* Salesforce-rapporten
* Google Analytics
* Adobe Analytics
* appFigures (bèta)
* Data.World - Gegevensset ophalen (bèta)
* GitHub (bèta)
* LinkedIn Sales Navigator (bèta)
* Marketo (bèta)
* Mixpanel (bèta)
* Planview Enterprise One - PRM (bèta)
* QuickBooks Online (bèta)
* Smartsheet
* SparkPost (bèta)
* SweetIQ (bèta)
* Planview Enterprise One - CMT (bèta)
* Twilio (bèta)
* Zendesk (bèta)
* Asana (bèta)
* Dynamics 365 Customer Insights (Bèta)
* Emigo Data Source
* Entersoft Business Suite (bèta)
* FactSet Analytics
* Palantir Foundry
* Industrial App Store
* Intune Data Warehouse (bèta)
* Microsoft Graph Security (bèta)
* Projectplace voor Power BI
* Product Insights (bèta)
* Quick Base
* Spigit (bèta)
* TeamDesk (bèta)
* Webtrends Analytics (bèta)
* Witivio (bèta)
* Workplace Analytics (bèta)
* Zoho Creator (bèta)
* eWay-CRM (bèta)
* Hexagon PPM Smart API


In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Onlineservices**.

![Gegevensbronnen voor onlineservices, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Andere gegevensbronnen

De categorie **Overige** biedt de volgende gegevensverbindingen:

* Web
* SharePoint-lijst
* OData-feed
* Active Directory
* Microsoft Exchange
* Hadoop-bestand (HDFS)
* Spark
* Hive LLAP
* R-script
* Python-script
* ODBC
* OLE DB
* Acterys: Automatisering en planning van modellen (bèta)
* Automation Anywhere (bèta)
* Solver
* Cherwell (bèta)
* Cognite Data Fusion (bèta)
* FHIR
* Information Grid (bèta)
* Jamf Pro (bèta)
* MicroStrategie voor Power BI
* Paxata
* QubolePresto (bèta)
* Roamler (bèta)
* Short Cuts Business Insights (bèta)
* Siteimprove
* SurveyMonkey (bèta)
* Tenforce (Smart)List
* TIBCO (R) Data Virtualization (bèta)
* Vena (bèta)
* Vessel Insight (bèta)
* Zucchetti HR Infinity (bèta)
* Anaplan-connector v1.0 (bèta)
* Starburst Enterprise Presto (bèta)
* Lege query



In de volgende afbeelding ziet u het venster **Gegevens ophalen** voor **Overige**.

![Andere gegevensbronnen in Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Op dit moment is het niet mogelijk om verbinding te maken met aangepaste gegevensbronnen die zijn beveiligd met Azure Active Directory.

### <a name="template-apps"></a>Sjabloon-apps

U kunt sjabloon-apps voor uw organisatie vinden door de koppeling **Sjabloon-apps** onderaan het venster **Gegevens ophalen** te selecteren. 

![Het dialoogvenster Gegevens ophalen voor overige gegevensbronnen in Power BI Desktop](media/desktop-data-sources/data-sources-12.png)

Beschikbare sjabloon-apps kunnen variëren op basis van uw organisatie.

## <a name="connecting-to-a-data-source"></a>Verbinding maken met een gegevensbron

Als u verbinding wilt maken met een gegevensbron, selecteert u de gegevensbron in het venster **Gegevens ophalen** en selecteert u **Verbinding maken**. In de volgende afbeelding is **Web** geselecteerd in de categorie **Overige**.

![Verbinding maken met web, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Er wordt een verbindingsvenster weergegeven dat specifiek is voor het type gegevensverbinding. Als referenties zijn vereist, wordt u gevraagd ze op te geven. In de volgende afbeelding ziet u hoe een URL wordt ingevoerd om verbinding te maken met een webgegevensbron.

![Invoer-URL, dialoogvenster Van web, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Voer de URL of de gegevens voor de bronverbinding in en selecteer **OK**. Power BI Desktop maakt de verbinding met de gegevensbron en toont de beschikbare gegevensbronnen in de **Navigator**.

![Dialoogvenster Navigator, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Kies de knop **Laden** onder in het deelvenster van de **Navigator** om de gegevens te laden. Als u de query wilt transformeren of bewerken in Power Query-editor voordat u de gegevens laadt, selecteert u de knop **Gegevens transformeren**.

Dat is alles wat u hoeft te weten om verbinding te maken met gegevensbronnen in Power BI Desktop! Probeer verbinding te maken met onze groeiende lijst gegevensbronnen en kom regelmatig terug. We blijven deze lijst voortdurend uitbreiden.

## <a name="using-pbids-files-to-get-data"></a>Gegevens ophalen met behulp van PBIDS-bestanden

PBIDS-bestanden zijn Power BI Desktop-bestanden die een specifieke structuur hebben, samen met een PBIDS-extensie om aan te geven dat het een Power BI-gegevensbronbestand betreft.

U kunt een PBIDS-bestand maken om de ervaring met **Gegevens ophalen** te stroomlijnen voor nieuwe of onervaren rapportontwerpers in uw organisatie. Als u het PBIDS-bestand maakt op basis van bestaande rapporten, is het eenvoudiger voor beginnende ontwerpers van rapporten om nieuwe rapporten te bouwen op basis van dezelfde gegevens.

Wanneer een auteur een PBIDS-bestand opent, wordt Power BI Desktop geopend en wordt de gebruiker gevraagd om referenties te verifiëren en verbinding te maken met de gegevensbron die in het bestand is opgegeven. Het dialoogvenster **Navigatie** wordt weergegeven en de gebruiker moet de tabellen van die gegevensbron selecteren om in het model te laden. Gebruikers moeten mogelijk ook de database(s) en verbindingsmodus selecteren als die niet zijn opgegeven in het PBIDS-bestand.

Vanaf dat moment kan de gebruiker beginnen met het samenstellen van visualisaties of **Recente bronnen** selecteren om een nieuwe groep tabellen in het model te laden.

Momenteel ondersteunen PBIDS-bestanden slechts één gegevensbron in één bestand. Als u meer dan één gegevensbron opgeeft, resulteert dat in een fout.


### <a name="how-to-create-a-pbids-connection-file"></a>Een PBIDS-verbindingsbestand maken

Als u een bestaand Power BI Desktop-bestand (PBIX-bestand) hebt dat al is verbonden met de gegevens waarin u geïnteresseerd bent, kunt u dit verbindingsbestand gewoon exporteren vanuit Power BI Desktop. Dit is de aanbevolen methode, aangezien het PBIDS-bestand automatisch kan worden gegenereerd vanaf het bureaublad. Daarnaast kunt u het bestand nog steeds bewerken of handmatig maken in een teksteditor. 

Als u het PBIDS-bestand wilt maken, selecteert u **Bestand > Opties en instellingen > Instellingen voor gegevensbron**:

![De menuoptie Instellingen voor gegevensbron](media/desktop-data-sources/data-sources-09.png)

In het dialoogvenster dat wordt weergegeven, selecteert u de gegevensbron die u wilt exporteren als een PBIDS en selecteert u vervolgens **PBIDS exporteren**.

![Het dialoogvenster Instellingen voor gegevensbron](media/desktop-data-sources/data-sources-10.png)

Wanneer u de knop **PBIDS exporteren** selecteert, genereert Power BI Desktop het PBIDS-bestand. U kunt het bestand onder een andere naam opslaan en delen met anderen. U kunt het bestand ook openen in een teksteditor en het bestand verder aanpassen. Zo kunt u de verbindingsmodus in het bestand zelf opgeven, zoals wordt weergegeven in de volgende afbeelding. 

![Een teksteditor gebruiken om het PBIDS-bestand te wijzigen](media/desktop-data-sources/data-sources-11.png)

Als u PBIDS-bestanden liever handmatig in een teksteditor maakt, moet u de vereiste invoer voor één verbinding opgeven en het bestand opslaan met de extensie PBIDS. Desgewenst kunt u de verbindingsmodus ook opgeven als DirectQuery of Importeren. Als **mode** ontbreekt/null is in het bestand, wordt de gebruiker die het bestand opent in Power BI Desktop gevraagd om **DirectQuery** of **Importeren** te selecteren.


### <a name="pbids-file-examples"></a>Voorbeelden van PBIDS-bestanden

Deze sectie bevat enkele voorbeelden van veelgebruikte gegevensbronnen. Het bestandstype PBIDS ondersteunt alleen gegevensverbindingen die ook worden ondersteund in Power BI Desktop, met de volgende uitzonderingen: Wiki URLS, Live Connect en Lege query.

Dit PBIDS-bestand bevat *geen* verificatie-informatie en tabel- en schema-informatie.  

De volgende codefragmenten tonen enkele algemene voorbeelden voor PBIDS-bestanden. Ze zijn echter niet volledig of allesomvattend. Voor andere gegevensbronnen kunt u verwijzen naar de [DSR-indeling (Data Source Reference) voor protocol- en adresgegevens ](/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Als u de verbindingsbestanden bewerkt of handmatig maakt, zijn deze voorbeelden alleen bedoeld voor het gemak. Ze zijn niet volledig en bevatten niet alle ondersteunde connectors in DSR-indeling.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Map

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>SharePoint-lijst

De URL moet verwijzen naar de SharePoint-site zelf, niet naar een lijst binnen de site. Gebruikers krijgen een navigator waarmee ze een of meer lijsten op die site kunnen selecteren, waarbij elk van die lijsten een tabel in het model wordt.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Tekstbestand

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Gegevensstroom

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Volgende stappen

U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Query-overzicht met Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Algemene querytaken in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)