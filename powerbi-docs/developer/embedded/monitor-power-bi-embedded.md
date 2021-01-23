---
title: Power BI Embedded bewaken
description: Begin hier om te leren hoe u Power BI Embedded kunt bewaken.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 1b8ebbd7913bc5763f9f4dd8576fbc4783e8d531
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690744"
---
# <a name="monitor-power-bi-embedded"></a>Power BI Embedded bewaken

Wanneer u belang rijke toepassingen en bedrijfs processen hebt die afhankelijk zijn van Azure-resources, wilt u deze resources controleren op hun Beschik baarheid, prestaties en werking. In dit artikel worden de bewakings gegevens beschreven die worden gegenereerd door Power BI Embedded en hoe u de functies van Azure Monitor kunt gebruiken om deze gegevens te analyseren en te waarschuwen.

## <a name="monitor-overview"></a>Overzicht van monitor

De pagina **overzicht** in de Azure portal voor elk exemplaar van *Power bi embedded* bevat de volgende informatie:

* **Resource groep** : de [resource groep](/azure/azure-resource-manager/management/overview#resource-groups) waarvan het exemplaar deel uitmaakt
* **Status** : de status van uw Power bi embedded-exemplaar
* **Locatie** : de locatie van uw Power bi embedded-exemplaar
* **Resource naam** : de naam van uw Power bi embedded-exemplaar
* **SKU** : de SKU die uw Power bi embedded-exemplaar gebruikt
* **Abonnements naam** : de naam van uw Power bi embedded-exemplaar abonnement
* **Abonnements-id** : de abonnements-id van uw Power bi embedded-abonnement

## <a name="what-is-azure-monitor"></a>Wat is Azure Monitor?

*Power bi embedded* maakt bewakings gegevens met behulp van [Azure monitor](/azure/azure-monitor/overview). Dit is een volledige stack bewakings service in azure met een volledige set functies voor het bewaken van uw Azure-resources naast bronnen in andere Clouds en on-premises.

Begin met het artikel [bewaking van Azure-resources met Azure monitor](/azure/azure-monitor/insights/monitor-azure-resource), waarin de volgende concepten worden beschreven:

- Wat is Azure Monitor?
- Kosten die zijn gekoppeld aan bewaking
- Bewaken van gegevens die zijn verzameld in azure
- Gegevens verzameling configureren
- Standaard Programma's in azure voor het analyseren en waarschuwen van bewakings gegevens

In de volgende secties vindt u een beschrijving van de specifieke gegevens die zijn verzameld voor Power BI Embedded en vindt u voor beelden voor het configureren van gegevens verzameling en het analyseren van deze gegevens met Azure-hulpprogram ma's.

## <a name="monitoring-data"></a>Bewakingsgegevens

Power BI Embedded worden dezelfde soorten bewakings gegevens verzameld als andere Azure-resources die worden beschreven in [gegevens van Azure-resources bewaken](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources).

Zie [bewaking *Power bi embedded* gegevens referentie](monitor-power-bi-embedded-reference.md) voor gedetailleerde informatie over de metrische gegevens en logboek gegevens die zijn gemaakt door Power bi Embedded.

## <a name="collection-and-routing"></a>Verzameling en route ring

De metrische gegevens van het platform en het activiteiten logboek worden automatisch verzameld en opgeslagen, maar kunnen worden doorgestuurd naar andere locaties met behulp van een diagnostische instelling.  

Bron logboeken worden pas verzameld en opgeslagen als u een diagnostische instelling hebt gemaakt en deze naar een of meer locaties wilt door sturen.

Zie [Diagnostische instelling maken voor het verzamelen van platform logboeken en metrische gegevens in azure](/azure/azure-monitor/platform/diagnostic-settings) voor het gedetailleerde proces voor het maken van een diagnostische instelling met behulp van de Azure Portal, CLI of Power shell. Wanneer u een diagnostische instelling maakt, geeft u op welke categorieën logboeken u wilt verzamelen. De categorieën voor *Power bi embedded* worden vermeld in [Power bi embedded bewakings gegevens referentie](monitor-power-bi-embedded-reference.md#resource-logs).

### <a name="using-powershell-to-enable-diagnostics"></a>PowerShell gebruiken om diagnostische gegevens in te schakelen

Als u metrische gegevens en diagnostische logboek registratie wilt inschakelen met behulp van Power shell, gebruikt u de onderstaande opdrachten. Zie [een log Analytics-werk ruimte maken en configureren in azure monitor met behulp van Power shell](/azure/azure-monitor/platform/powershell-workspace-configuration)voor meer informatie over het gebruik van Power shell om diagnostische gegevens in te scha kelen.

* Gebruik deze opdracht om de opslag van diagnostische logboeken in een opslagaccount in te schakelen:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    De opslagaccount-id is de resource-id voor het opslagaccount waarnaar u de logboeken wilt verzenden.

* Gebruik deze opdracht om het streamen van diagnostische logboeken naar een Event Hub in te schakelen:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* De id voor de Azure Service Bus-regel is een tekenreeks met deze indeling:

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Gebruik deze opdracht om het verzenden van diagnostische logboeken naar een Log Analytics-werkruimte in te schakelen:

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* U kunt de resource-id van de Log Analytics-werkruimte achterhalen door de volgende opdracht te gebruiken:

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

U kunt deze parameters combineren om meerdere uitvoeropties in te schakelen.

De metrische gegevens en logboeken die u kunt verzamelen, worden besproken in de volgende secties.

## <a name="analyzing-metrics"></a>Metrische gegevens analyseren

U kunt metrische gegevens voor *Power bi embedded* met metrische gegevens uit andere Azure-Services analyseren door **metrische gegevens** te openen in het menu **Azure monitor** . Zie [aan de slag met Azure Metrics Explorer](/azure/azure-monitor/platform/metrics-getting-started) voor meer informatie over het gebruik van dit hulp programma.

Voor een lijst met de platform gegevens die voor Power BI Embedded worden verzameld, [zie *Power bi embedded* gegevens referentie bewaking controleren](monitor-power-bi-embedded-reference.md#metrics)  

Ter referentie ziet u een lijst met [alle metrische resource gegevens die worden ondersteund in azure monitor](/azure/azure-monitor/platform/metrics-supported).

## <a name="analyzing-logs"></a>Logboeken analyseren

Gegevens in Azure Monitor logboeken worden opgeslagen in tabellen waarin elke tabel een eigen set unieke eigenschappen heeft.  

Alle resource Logboeken in Azure Monitor hebben dezelfde velden die worden gevolgd door servicespecifieke velden. Het algemene schema wordt beschreven in [Azure monitor resource-logboek schema](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema) het schema voor Power bi Embedded Resource Logboeken vindt u in de [Power bi embedded gegevens verwijzing](monitor-power-bi-embedded-reference.md#schemas).

Het [activiteiten logboek](/azure/azure-monitor/platform/activity-log) is een Azure-aanmelding voor een platform dat inzicht biedt in gebeurtenissen op abonnements niveau. U kunt deze onafhankelijk bekijken of door sturen naar Azure Monitor-logboeken, waar u veel complexere query's kunt uitvoeren met behulp van Log Analytics.  

Voor een lijst met de typen bron logboeken die zijn verzameld voor Power BI Embedded raadpleegt u [Power bi embedded gegevens referentie controleren](monitor-power-bi-embedded-reference.md#resource-logs)  

Zie [Power bi embedded gegevens referentie bewaken](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables) voor een lijst met de tabellen die worden gebruikt door Azure monitor logboeken en query's die kunnen worden doorzocht door log Analytics.  

### <a name="sample-kusto-queries"></a>Voor beeld van Kusto-query's

> [!IMPORTANT]
> Wanneer u **Logboeken** in het menu Power bi embedded selecteert, wordt log Analytics geopend met het query bereik dat is ingesteld op de huidige Power bi Embedded Resource. Dit betekent dat logboek query's alleen gegevens van die bron bevatten. Als u een query wilt uitvoeren die gegevens uit andere Power BI Embedded resource of gegevens uit andere Azure-Services bevat, selecteert u **Logboeken** in het menu **Azure monitor** . Zie de [logboek query bereik en het tijds bereik in Azure Monitor Log Analytics](/azure/azure-monitor/log-query/scope/) voor meer informatie.

Hieronder vindt u query voorbeelden voor het bewaken van Power BI Embedded.

* Dit is een query die in minder dan vijf minuten (300.000 milliseconden) is voltooid.

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* Capaciteitsnamen identificeren.

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>Waarschuwingen

Azure Monitor waarschuwingen geven u proactief op de hoogte wanneer er belang rijke voor waarden worden gevonden in uw bewakings gegevens. Hiermee kunt u problemen in uw systeem identificeren en oplossen voordat uw klanten ze opmerken. U kunt waarschuwingen instellen voor [metrische gegevens](/azure/azure-monitor/platform/alerts-metric-overview), [Logboeken](/azure/azure-monitor/platform/alerts-unified-log)en het [activiteiten logboek](/azure/azure-monitor/platform/activity-log-alerts).

## <a name="next-steps"></a>Volgende stappen

Lees meer informatie over logboekregistratie van diagnostische gegevens in Azure-resources.

>[!div class="nextstepaction"]
>[Power BI Embedded gegevens referentie bewaken](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[Azure-resources bewaken met Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource)