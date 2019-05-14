---
title: Gateway-prestaties controleren (openbare preview)
description: In dit artikel bevat informatie over het controleren van de prestaties van de activiteiten van on-premises data gateway.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535362"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Gateway-prestaties controleren (openbare preview)

Gateway-beheerders hebben voor het bewaken van prestaties, traditioneel afhankelijk van het handmatig controleren via het hulpprogramma Prestatiemeter van Windows-prestatiemeteritems. We bieden nu extra logboekregistratie en een [Gateway prestaties PBI sjabloonbestand](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) voor het visualiseren van de resultaten. Deze functie biedt nieuwe inzichten in het gebruik van de gateway en kunt u om op te lossen traag presterende query's.

> [!NOTE]
> Deze functie is momenteel alleen beschikbaar voor de on-premises data gateway in de standaardmodus en niet voor de persoonlijke modus.

## <a name="enable-performance-logging"></a>Prestaties logboekregistratie inschakelen

Als u wilt deze functie inschakelt, moet u de volgende wijzigingen aan de *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* -bestand in de ' \Program Files\On-premises gegevensgateway ' map:

1. Update **QueryExecutionReportOn** naar _waar_ aanvullende logboekregistratie inschakelen voor query's uitgevoerd met behulp van de gateway. Als u deze optie inschakelt, maakt het rapport van de uitvoering van Query- en de Query-Uitvoeringsrapport aggregatie-bestanden.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Update **SystemCounterReportOn** naar _waar_ aanvullende logboekregistratie inschakelen voor geheugen en CPU-systeem prestatiemeteritems. Als u deze optie inschakelt, wordt het bestand System teller aggregatie-rapport gemaakt.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Er zijn andere waarden in het configuratiebestand die u kunt indien nodig bijwerken.

    - **ReportFilePath**: Bepaalt het pad waar de drie logboekbestanden worden opgeslagen. Standaard is dit pad "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises gegevens gateway\Report" of "Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On-premises gegevens gateway\Report", afhankelijk van de versie van het besturingssysteem. Als u een service-account voor de gateway dan _PBIEgwService_, dit deel van het pad vervangen door de naam van de service-account.
    - **ReportFileCount**: Hiermee bepaalt u het nummer van de logboekbestanden van elk type te behouden. De standaardwaarde is 10.
    - **ReportFileSizeInBytes**: Bepaalt de grootte van het bestand te houden. De standaardwaarde is 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Bepaalt het aantal minuten waarvoor de gegevens van de uitvoering van query's worden samengevoegd. De standaardwaarde is 5.
    - **SystemCounterAggregationTimeInMinutes**: Bepaalt het aantal minuten waarvoor de Systeemitems wordt geaggregeerd. De standaardwaarde is 5.

1. Nadat u de wijzigingen hebt aangebracht in het configuratiebestand, moet u de gateway voor deze configuratiewaarden die moeten worden van kracht opnieuw starten. U gaat nu zien de rapportbestanden die worden gegenereerd in de locatie die u hebt opgegeven voor **ReportFilePath**.

    > [!NOTE]
    > Het kan maximaal 10 minuten duren, plus de hoeveelheid tijd instellen voor **QuerExecutionAggregationTimeInMinutes** in het configuratiebestand totdat bestanden start weergegeven in de map.

## <a name="understand-performance-logs"></a>Inzicht in het logboek prestaties

Wanneer u deze functie inschakelt, maken we drie nieuwe logboekbestanden:

- Het rapport van de uitvoering van Query
- Het rapport aggregatie van Query uitvoeren
- Het rapport aggregatie van teller

Het rapport van de uitvoering van Query bevat informatie over de uitgevoerde van gedetailleerde query. We leggen de volgende kenmerken:

|Kenmerk |Beschrijving |
| ---- | ---- |
|**GatewayObjectId** |De unieke id voor de gateway. |
|**RequestId** |De unieke id voor een aanvraag voor een gateway. Het kan zijn hetzelfde voor meerdere query's. |
|**DataSource** |Het gegevensbrontype en de gegevensbron bevat. |
|**QueryTrackingId** |De unieke id voor een query. |  
|**QueryExecutionEndTimeUTC** |Tijd wanneer uitvoering van de query is voltooid. |
|**QueryExecutionDuration**(ms) |De duur voor de uitvoering van een query. |
|**QueryType** |Bijvoorbeeld het query - type, de query doorgegeven wordt mogelijk een Power BI vernieuwen/DirectQuery of query's van PowerApps en Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Tijd wanneer activiteiten, zoals in de wachtrij, het ophalen van gegevens, compressie, gegevensverwerking en enzovoort voltooid voor gegevensverwerking. |
|**DataProcessingDuration**(ms) |De duur voor gegevensverwerking activiteiten, zoals in de wachtrij, het ophalen van gegevens, compressie, gegevensverwerking, enzovoort. |
|**Geslaagd** |Hiermee wordt aangegeven als de query is geslaagd of mislukt. |
|**ErrorMessage** |Als de query is mislukt, geeft het foutbericht. |
| | |

De Query-Uitvoeringsrapport aggregatie bevat querygegevens verrekend voor een bepaalde periode door **GatewayObjectId**, **DataSource**, **succes**, en **QueryType**. De standaardwaarde is 5 minuten, maar u kunt dit aanpassen zoals hieronder wordt beschreven. We leggen de volgende kenmerken:

|Kenmerk |Beschrijving |
| ---- | ---- |
|**GatewayObjectId** |De unieke id voor de gateway. |
|**AggregationStartTimeUTC** |Begin van de periode waarvoor de Querykenmerken zijn samengevoegd. |
|**AggregationEndTimeUTC** |Einde van het tijdvenster voor welke query kenmerken zijn samengevoegd. |
|**DataSource** |Het gegevensbrontype en de gegevensbron bevat. |
|**Geslaagd** |Hiermee wordt aangegeven als de query is geslaagd of mislukt. |
|**AverageQueryExecutionDuration**(ms) |Gemiddelde uitvoeringstijd van de query voor het tijdvenster voor aggregatie. |
|**MaxQueryExecutionDuration**(ms) |Maximale uitvoeringstijd voor het tijdvenster voor aggregatie. |
|**MinQueryExecutionDuration**(ms) |Minimale query uitvoeringstijd voor het tijdvenster voor aggregatie. |
|**QueryType** |Bijvoorbeeld het query - type, de query doorgegeven wordt mogelijk een Power BI vernieuwen/DirectQuery of query's van PowerApps en Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Gemiddelde tijd voor gegevensverwerking activiteiten, zoals in de wachtrij, het ophalen van gegevens, compressie, gegevensverwerking, enzovoort in voor het tijdvenster voor aggregatie. |
|**MaxDataProcessingDuration**(ms) |Maximale tijd voor gegevensverwerking activiteiten, zoals in de wachtrij, het ophalen van gegevens, compressie, gegevensverwerking, enzovoort voor het tijdvenster voor aggregatie. |
|**MinDataProcessingDuration**(ms) |Minimale tijd voor gegevensverwerking activiteiten, zoals in de wachtrij, het ophalen van gegevens, compressie, gegevensverwerking en enzovoort voor het tijdvenster voor aggregatie. |
|**Aantal** |Aantal query's. |
| | |

Het rapport teller aggregatie bevat system itemwaarden verrekend voor een bepaalde periode. De standaardwaarde is 5 minuten, maar u kunt dit aanpassen zoals hieronder wordt beschreven. We leggen de volgende kenmerken:

|Kenmerk |Beschrijving |
| ---- | ---- |
|**GatewayObjectId** |De unieke id voor de gateway. |
|**AggregationStartTimeUTC** |Begin van de periode waarvoor system prestatiemeteritems zijn geaggregeerd. |
|**AggregationEndTimeUTC** |Einde van het tijdvenster voor welke items hebt zijn geaggregeerd. |
|**CounterName** |Systeem-tellers, met inbegrip van geheugen en CPU-gebruik door de gateway, mashup, en algemene door de computer die als host fungeert de gateway. |
|**Max** |Maximale waarde voor het prestatiemeteritem systeem voor het tijdvenster voor aggregatie. |
|**Min** |Minimale waarde voor de teller systeem voor het tijdvenster voor aggregatie. |
|**Gemiddelde** |Gemiddelde waarde voor het prestatiemeteritem systeem voor het tijdvenster voor aggregatie. |
| | |

## <a name="visualize-gateway-performance"></a>Prestaties van een gateway visualiseren

Nu kunt u de gegevens die zich in de logboekbestanden visualiseren.

1. Download de [Gateway prestaties PBI sjabloon](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) en opent u het gebruik van Power BI desktop.

1. In het dialoogvenster dat wordt geopend, Controleer of het pad naar map overeenkomt met de waarde in **ReportFilePath**.

    ![Pop-upvenster voor het mappad](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Selecteer **Load**, en het sjabloonbestand begint met het laden van de gegevens uit uw logboekbestanden. Alle visuele elementen moeten vervolgens worden ingevuld met de gegevens in de rapporten.

1. (Optioneel) dit bestand opslaan als een PBIX en deze publiceren naar uw service voor automatische vernieuwingen worden.

Bovendien kunt u dit sjabloonbestand aanpassen aan uw behoeften aanpassen. Zie voor meer informatie over Power BI-sjablonen, [Microsoft Power BI-Blog post](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).