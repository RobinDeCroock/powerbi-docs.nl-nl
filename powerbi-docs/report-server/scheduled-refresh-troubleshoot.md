---
title: Problemen met geplande vernieuwing oplossen in Power BI Report Server
description: In dit artikel worden de hulpmiddelen beschreven die beschikbaar zijn voor het oplossen van problemen met geplande vernieuwing in Power BI Report Server.
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.author: mblythe
ms.openlocfilehash: 6f35ab1dfb14fe5a48fce0b56823ce7bab32d05d
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543930"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Problemen met geplande vernieuwing oplossen in Power BI Report Server
In dit artikel worden de hulpmiddelen beschreven die beschikbaar zijn voor het oplossen van problemen met geplande vernieuwing in Power BI Report Server.

Als er nieuwe problemen worden gemeld, wordt dit artikel bijgewerkt met informatie om u te helpen.

## <a name="common-issues"></a>Veelvoorkomende problemen
Hieronder vindt u de meest voorkomende problemen die u kunt tegenkomen wanneer u vernieuwen wilt plannen voor een rapport. 

### <a name="driver-related-problems"></a>Problemen met stuurprogramma
Om verbinding te maken met verschillende gegevensbronnen, kunnen er stuurprogramma's van derden nodig zijn die op de juiste manier moeten zijn geïnstalleerd om verbinding te kunnen maken. Deze stuurprogramma's moeten niet alleen worden geïnstalleerd op de computer waarop u Power BI Desktop gebruikt, maar ook op de rapportserver.

Een stuurprogramma kan zowel 32 bits als 64 bits zijn. Zorg ervoor dat u het 64 bits stuurprogramma installeert, aangezien Power BI Report Server 64 bits is.

Raadpleeg de fabrikant voor meer informatie over het installeren en configureren van stuurprogramma's van derden.

### <a name="memory-pressure"></a>Geheugendruk
Geheugendruk kan optreden wanneer rapporten meer geheugen vereisen voor verwerking en weergave. Geplande vernieuwing van rapporten kan een aanzienlijke hoeveelheid geheugen vragen op de computer, met name voor grotere rapporten. Geheugendruk kan resulteren in rapportfouten, evenals een potentiële crash van de rapportserver zelf.

Als u regelmatig geheugendruk vaststelt, kan het zinvol zijn om te kijken naar een uitgeschaalde implementatie van de rapportserver om de belasting van resources te verdelen. U kunt ook opgeven dat een bepaalde rapportserver moet worden gebruikt om gegevens te vernieuwen, via de instelling `IsDataModelRefreshService` in het bestand rsreportserver.config. Met deze instelling kunt u een of meer servers definiëren als de front-endserver voor het afhandelen van rapporten op aanvraag, en een andere set servers voor alleen geplande vernieuwing.

Zie [Monitor an Analysis Services Instance](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance) (Een Analysis Services-exemplaar bewaken) voor informatie over het bewaken van een Analysis Services-exemplaar.

Zie [Geheugeneigenschappen](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties) voor informatie over geheugeninstellingen in Analysis Services.

### <a name="kerberos-configuration"></a>Kerberos-configuratie
Om verbinding te maken met een gegevensbron via Windows-referenties, kan het nodig zijn om beperkte Kerberos-overdracht te configureren. Zie [Configure Kerberos to use Power BI reports](configure-kerberos-powerbi-reports.md) (Kerberos configureren om Power BI-rapporten te gebruiken) voor meer informatie over het configureren van beperkte Kerberos-overdracht.

## <a name="known-issues"></a>Bekende problemen
Informatie over bekende problemen wordt hier vermeld wanneer deze beschikbaar komt.

## <a name="configuration-settings"></a>Configuratie-instellingen
De volgende instellingen kunnen worden gebruikt om invloed te hebben op geplande vernieuwing. Instellingen in SQL Server Management Studio (SSMS) gelden voor alle rapportservers binnen een uitgeschaalde implementatie. Instellingen in het bestand rsreportserver.config gelden voor de specifieke server waarop ze zijn geconfigureerd.

**Instellingen in SSMS:**

| Instelling | Beschrijving |
| --- | --- |
| MaxFileSizeMb |De maximale bestandsgrootte voor geüploade rapporten. De standaardwaarde is 1000 MB (1 GB). De maximumwaarde is 2000 MB (2 GB). |
| ModelCleanupCycleMinutes |Bepaalt hoe vaak het model wordt gecontroleerd om het te verwijderen uit het geheugen. De standaardwaarde is 15 minuten. |
| ModelExpirationMinutes |Bepaalt na hoeveel minuten van inactiviteit het model verloopt en wordt verwijderd. De standaardwaarde is 60 minuten. |
| ScheduleRefreshTimeoutMinutes |Bepaalt hoe lang het vernieuwen van gegevens kan duren voor een modus. De standaardwaarde is 120 minuten. Er is geen bovengrens. |

**Instellingen in het bestand rsreportserver.config:**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Hulpmiddelen voor probleemoplossing
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Logboeken die relevant zijn voor geplande vernieuwing van Power BI-rapporten
De logboekbestanden met informatie over geplande vernieuwing zijn de logboeken RSPowerBI_. Deze bevinden zich in de map LogFiles in de map waarin de rapportserver is geïnstalleerd. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Fout opgetreden**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Gegevens vernieuwd***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Onjuiste referenties**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Uitgebreide logboekregistratie inschakelen
Het inschakelen van uitgebreide logboekregistratie is in Power BI Report Server hetzelfde als voor SQL Server Reporting Services.

1. Open `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Wijzig onder `<system.diagnostics>` de waarde voor **DefaultTraceSwitch** in **4**.
3. Wijzig onder `<RStrace>` de waarde voor **Components** in **all:4**. 

### <a name="executionlog"></a>ExecutionLog
Wanneer er een Power BI-rapport wordt gegenereerd, of een schema voor geplande vernieuwing wordt uitgevoerd, worden nieuwe vermeldingen toegevoegd aan het uitvoeringslogboek in de database. Deze vermelding zijn beschikbaar in de weergave **ExecutionLog3** in de catalogusdatabase van de rapportserver.

Vermeldingen in het uitvoeringslogboek voor Power BI-rapporten verschillen van vermeldingen voor andere rapporttypen.

* De kolom TimeRendering is altijd 0. Weergave (rendering) van Power BI-rapporten gebeurt in de browser, niet op de server.
* Er zijn 2 aanvraagtypen en daaropvolgende itemacties:
  * **Interactive**: wanneer een rapport wordt weergegeven.
    * **ASModelStream**: wanneer het gegevensmodel vanuit de catalogus naar Analysis Services wordt gestreamd.
    * **ConceptualSchema**: wanneer de gebruiker klikt terwijl het rapport wordt weergegeven.
    * **QueryData**: wanneer gegevens worden opgevraagd bij de client.
  * **Refresh Cache**: wanneer een schema voor gepland vernieuwen wordt uitgevoerd.
    * **ASModelStream**: wanneer het gegevensmodel vanuit de catalogus naar Analysis Services wordt gestreamd.
    * **DataRefresh**: wanneer gegevens worden vernieuwd uit een of meer gegevensbronnen.
    * **SaveToCatalog**: wanneer het gegevensmodel weer wordt opgeslagen in de catalogus.

## <a name="analysis-services"></a>Analysis Services
Het kan soms handig zijn om de instellingen van Analysis Services aan te passen voor probleemoplossing of om geheugenlimieten te wijzigen.

> [!IMPORTANT]
> Deze instellingen worden opnieuw ingesteld wanneer u de rapportserver bijwerkt. Bewaar daarom een kopie van de wijzigingen zodat u deze indien nodig opnieuw kunt toepassen.
> 
> 

### <a name="install-location"></a>Installatielocatie
Dit is de locatie waar Power BI Report Server en Analysis Services standaard worden geïnstalleerd:

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Instellingen van Analysis Services configureren (msmdsrv.ini)
In de map `<install directory>\PBIRS\ASEngine` vindt u het bestand *msmdsrv.ini*, dat u kunt gebruiken om verschillende instellingen van Analysis Services te beheren. Als u dit bestand opent, zult u direct zien dat dit bestand niet alle instellingen bevat die u in het bestand msmdsrv.ini zou verwachten. 

Dit komt omdat het werkelijke Analysis Services-proces dat wordt uitgevoerd door Power BI Report Server , wordt gestart in `<install directory>\PBIRS\ASEngine\workspaces`. In die map vindt u dan ook het volledige *msmdsrv.ini*-bestand dat u gewend bent. Het is belangrijk om het bestand in de map workspaces niet te wijzigen, aangezien deze map opnieuw wordt gemaakt wanneer het Analysis Services-proces wordt gestart. Als u een instelling wilt beheren, doe dit dan door het bestand msmdsrv.ini te wijzigen in de map `<install directory>\PBIRS\ASEngine`.

De volgende instellingen worden opnieuw ingesteld wanneer het Analysis Services-proces wordt gestart. Wijzigingen van deze instellingen worden dus genegeerd.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Lokaal Analysis Services-proces profileren
U kunt voor diagnostische doeleinden een trace van SQL Profiler uitvoeren op het lokale Analysis Services-proces. Ga als volgt te werk om verbinding te maken met het lokale exemplaar van Analysis Services.

SQL Server Profiler Trace is opgenomen in de [download van SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Start **SQL Server Profiler** als beheerder.
2. Selecteer de knop **New Trace**.
3. Selecteer in het dialoogvenster **Connect to server** de optie **Analysis Services** en voer **localhost:5132** in voor de servernaam.
4. Selecteer in het dialoogvenster **Trace properties** de gebeurtenissen die u wilt vastleggen en selecteer **Run**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Pagina's in het geheugen vergrendelen
Als u een Power BI-rapport niet kunt weergeven, kan het helpen om de bevoegdheid **Pagina's in het geheugen vergrendelen** toe te wijzen aan het servicesaccount waaronder Power BI Report Server wordt uitgevoerd. Zie [Windows privileges assigned to the Analysis Services service account](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv) (Windows-bevoegdheden die zijn toegewezen aan het serviceaccount van Analysis Services) voor meer informatie over het configureren van **Pagina's in het geheugen vergrendelen**.

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

