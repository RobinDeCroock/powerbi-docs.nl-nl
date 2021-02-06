---
title: Power BI Embedded gegevens referentie bewaken
description: Belang rijk referentie materiaal dat nodig is wanneer u Power BI Embedded bewaakt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: subject-monitoring
ms.date: 01/14/2021
ms.openlocfilehash: 9c07e75736b3ccdb33bf76f79656a8982cddb6d8
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617014"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>Power BI Embedded gegevens referentie bewaken

Zie [Power bi embedded bewaken](monitor-power-bi-embedded.md) voor meer informatie over het verzamelen en analyseren van bewakings gegevens voor Power bi Embedded.

## <a name="metrics"></a>Metrische gegevens

In deze sectie vindt u alle automatisch verzamelde platform gegevens die zijn verzameld voor Power BI Embedded.  

|Metrisch type | Resource provider/type naam ruimte<br/> en koppelen aan afzonderlijke gegevens |
|-------|-----|
| Capaciteiten | [Micro soft. PowerBIDedicated/capaciteiten](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Capaciteiten

Resource provider en-type: [micro soft. PowerBIDedicated/capaciteiten](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| Name | Metrisch | Eenheid | Description |
|:---|:-------|:-----|:------------|
|Geheugen (gen1) |memory_metric               |Bytes        |Geheugen. Bereik 0-3 GB voor a1, 0-5 GB voor a2, 0-10 GB voor a3, 0-25 GB voor A4, 0-50 GB voor A5 en 0-100 GB voor A6. Wordt alleen ondersteund voor Power BI Embedded resources van de eerste generatie. |
|Geheugen overbelasting (gegevens sets) (gen1) |memory_thrashing_metric     |Percentage      |Gemiddeld geheugen overbelasting. Wordt alleen ondersteund voor Power BI Embedded resources van de eerste generatie. |
|QPU High-gebruik (gen1) |qpu_high_utilization_metric |Count        |QPU hoog gebruik in de laatste minuut, 1 voor hoog QPU gebruik, anders 0. Wordt alleen ondersteund voor Power BI Embedded resources van de eerste generatie. |
|Query duur (gegevens sets) (gen1) |QueryDuration               |Milliseconden |DAX-query duur in laatste interval. Wordt alleen ondersteund voor Power BI Embedded resources van de eerste generatie. |
|Wachtrij lengte van de taak pool voor query's (gegevens sets) (gen1) |QueryPoolJobQueueLength     |Count        |Aantal taken in de wachtrij van de query thread pool. Wordt alleen ondersteund voor Power BI Embedded resources van de eerste generatie. |

## <a name="metric-dimensions"></a>Metrische dimensies

Zie [multidimensionale metrische](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics)gegevens voor meer informatie over de metrieke dimensies.

Power BI Embedded heeft geen metrische gegevens die dimensies bevatten.

## <a name="resource-logs"></a>Resourcelogboeken

In deze sectie vindt u de typen bron logboeken die u kunt verzamelen voor Power BI Embedded.

Zie voor naslag informatie een overzicht van [alle categorie typen van bron logboeken die in azure monitor worden ondersteund](/azure/azure-monitor/platform/resource-logs-schema).

In deze sectie vindt u alle bron logboek categorie typen die zijn verzameld voor Power BI Embedded.  

|Type bron logboek | Resource provider/type naam ruimte<br/> en koppelen aan afzonderlijke gegevens |
|-------|-----|
| Capaciteiten | [Micro soft. PowerBIDedicated/capaciteiten](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Tabellen Azure Monitor logboeken

In deze sectie wordt verwezen naar alle Azure Monitor-Kusto-tabellen die relevant zijn voor Power BI Embedded en die beschikbaar zijn voor query's door Log Analytics.

|Resourcetype | Notities |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |Een lijst met tabellen hieronder weer geven |

### <a name="power-bi-embedded"></a>Power BI Embedded

| Tabel |  Beschrijving |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Vermeldingen uit het Azure-activiteiten logboek die inzicht bieden in gebeurtenissen op abonnements niveau of beheer groeps niveau die in azure zijn opgetreden.    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | Hiermee worden bron logboeken voor Azure-Services opgeslagen die gebruikmaken van Azure Diagnostics modus. In resource Logboeken wordt de interne werking van Azure-resources beschreven. |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Metrische gegevens die worden verzonden door Azure-Services die hun status en prestaties meten. |

Zie de [Naslag informatie over Azure monitor logboek tabel](/azure/azure-monitor/reference/tables/tables-resourcetype)voor een verwijzing naar Azure monitor logboeken/log Analytics tabellen.

## <a name="activity-log"></a>Activiteitenlogboek

U kunt de categorie **Engine** en/of de categorie **AllMetrics** selecteren.

### <a name="engine"></a>Engine

De categorie Engine geeft de bron de gebeurtenissen die hieronder worden weer gegeven. Voor elke gebeurtenis zijn er eigenschappen.

|     Naam van de gebeurtenis     |     Beschrijving van de gebeurtenis     |
|----------------------------|----------------------------------------------------------------------------------|
|    Controle van aanmeldingen    |    Registreert alle nieuwe verbindingen met Engine sinds het begin van de tracering.    |
|    Initialisatie van sessies    |    Registreert alle gestarte sessies sinds het begin van de tracering.    |
|    Start van Vertipaq-query    |    Registreert alle keren dat VertiPaq SE-query is gestart sinds het begin van de tracering.    |
|    Start van query    |    Registreert alle keren dat de query is gestart sinds het begin van de tracering.    |
|    Einde van query    |    Registreert alle keren dat de query is geëindigd sinds het begin van de tracering.    |
|    Einde van Vertipaq-query    |    Registreert alle keren dat VertiPaq SE-query is geëindigd sinds het begin van de tracering.    |
|    Controle van afmeldingen    |    Registreert alle verbroken Engine-verbindingen sinds het begin van de tracering.    |
|    Error    |    Registreert alle Engine-fouten sinds het begin van de tracering.    |

#### <a name="event-example"></a>Gebeurtenis voorbeeld

In de onderstaande tabel ziet u een voor beeld van een gebeurtenis.

| Eigenschapsnaam | Voorbeeld van Einde van Vertipaq-query | Beschrijving van de eigenschap |
|---|---|---|
| EventClass | XM_SEQUERY_END | Gebeurtenisklasse wordt gebruikt om gebeurtenissen te categoriseren. |
| EventSubclass | 0 | Gebeurtenissubklasse biedt extra informatie over elke gebeurtenisklasse. (bijvoorbeeld, 0: VertiPaq Scan) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | Id van hoofdactiviteit. |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | Tijd waarop de gebeurtenis is gestart, indien beschikbaar. |
| StartTime | 2018-04-06T18:30:11.9137358Z | Tijd waarop de gebeurtenis is gestart, indien beschikbaar. |
| JobID | 0 | Taak-id voor voortgang. |
| ObjectID | 464 | Object-id |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | Tijd waarop de gebeurtenis is beëindigd. |
| Duur | 0 | De tijdsduur (in milliseconden) van de gebeurtenis. |
| SessionType | Gebruiker | Sessietype (de entiteit die de bewerking heeft veroorzaakt). |
| ProgressTotal | 0 | Totaal van voortgang. |
| IntegerData | 0 | Gegevens in gehele getallen. |
| Ernst | 0 | Ernstniveau van een uitzondering. |
| Geslaagd | 1 | 1 = geslaagd. 0 = mislukt (een 1 betekent bijvoorbeeld dat een machtigingscontrole is voltooid en een 0 dat deze controle is mislukt). |
| Error | 0 | Foutnummer van een specifieke gebeurtenis. |
| ConnectionID | 3 | Unieke verbindings-id. |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | Id van de gegevensset waarin de instructie van de gebruiker wordt uitgevoerd. |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | Sessie-GUID. |
| SPID | 180 | Serverproces-id. Hiermee wordt een specifieke gebruikerssessie geïdentificeerd. Deze id komt exact overeen met de sessie-GUID die wordt gebruikt voor XML/A. |
| ClientProcessID | null | De proces-id van de clienttoepassing. |
| ApplicationName | null | De naam van de clienttoepassing waarin de verbinding met de server tot stand is gebracht. |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | De naam van de resource Power BI Embedded-capaciteit. |

### <a name="allmetrics"></a>AllMetrics

Als u de optie **AllMetrics** inschakelt, worden alle metrische gegevens geregistreerd die u met een Power BI Embedded-resource kunt gebruiken.

De volgende tabel geeft een lijst van de bewerkingen met betrekking tot Power BI Embedded die in het activiteiten logboek kunnen worden gemaakt.

## <a name="schemas"></a>Schema 's

Power BI Embedded gebruikt het **Power bi toegewezen** schema.

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Azure Power BI Embedded bewaken](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Logboekregistratie van diagnostische gegevens in Azure-resources](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)
