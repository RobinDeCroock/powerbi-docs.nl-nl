---
title: Power BI Premium-capaciteiten bewaken met behulp van de beheerportal
description: Gebruik de Power BI-beheerportal om uw Premium-capaciteiten te bewaken.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564902"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Capaciteiten bewaken in de beheerportal

De **Health** tabblad de **capaciteitsinstellingen** gebied in het beheerportal biedt een overzicht over uw workloads capaciteit en ingeschakelde metrische gegevens.  

![Capaciteit Health tabblad in de portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Als u uitgebreidere metrische gegevens nodig hebt, gebruikt u de [metrische gegevens over Power BI Premium capaciteit](service-admin-premium-monitor-capacity.md) app. De app biedt zoomen en filteren, en de meest gedetailleerde metrische gegevens voor bijna elk aspect die betrekking hebben op prestaties van de capaciteit. Zie voor meer informatie, [Monitor Premium-capaciteiten met de app](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Metrische Systeemmeetgegevens

Op de **Health** tabblad op het hoogste niveau, CPU-gebruik en geheugengebruik bieden een snelle weergave van de belangrijkste metrische gegevens voor de capaciteit. Deze metrische gegevens zijn cumulatief, met inbegrip van alle werkbelastingen voor de capaciteit ingeschakeld.

| **Meting** | **Beschrijving** |
| --- | --- |
| CPU-GEBRUIK | Gemiddeld CPU-gebruik, als een percentage van totaal beschikbare CPU-capaciteit. |
| GEHEUGENGEBRUIK | Gemiddelde geheugengebruik, in gigabytes (GB).|

## <a name="workload-metrics"></a>Metrische gegevens over workloads

Voor elke werkbelasting ingeschakeld voor de capaciteit. CPU-gebruik en het geheugen worden weergegeven.

| **Meting** | **Beschrijving** |
| --- | --- |
| CPU-GEBRUIK | Gemiddeld CPU-gebruik, als een percentage van totaal beschikbare CPU-capaciteit. |
| GEHEUGENGEBRUIK | Gemiddelde geheugengebruik, in gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Metrische gegevens over gedetailleerde workloads

Elke werkbelasting kent aanvullende metrische gegevens. Het type van metrische gegevens die worden weergegeven, is afhankelijk van de werkbelasting. Voor gedetailleerde metrische gegevens voor een werkbelasting, klikt u op de uit te breiden (pijl-omlaag).

![Status van de werkbelasting uitvouwen](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Gegevensstromen

##### <a name="dataflow-operations"></a>Bewerkingen van de gegevensstroom

| **Meting** | **Beschrijving** |
| --- | --- |
| Totale aantal | totaal aantal vernieuwingen voor elke gegevensstroom. |
| Aantal geslaagd | Totaal aantal geslaagde vernieuwingen voor elke gegevensstroom.|
| Gemiddelde duur (min) | de gemiddelde duur van een vernieuwing voor de gegevensstroom, in minuten |
| Max. duur (min.) | de duur van de langst lopende vernieuwing voor de gegevensstroom, in minuten. |
| Gemiddelde wachttijd (min.) | de gemiddelde vertraging tussen de geplande tijd en het begin van een vernieuwing voor de gegevensstroom, in minuten. |
| Maximale wachttijd (min.) | de maximale wachttijd voor de gegevensstroom, in minuten.  |

#### <a name="datasets"></a>Gegevenssets

##### <a name="refresh"></a>Vernieuwen

| **Meting** | **Beschrijving** |
| --- | --- |
| Totale aantal | het totale aantal vernieuwingen voor elke gegevensset. |
| Aantal geslaagd | Totaal aantal geslaagde vernieuwingen voor elke gegevensset. |
| Aantal mislukt | Totaal aantal mislukte vernieuwingen voor elke gegevensset. |
| Slagingspercentage  | Het aantal geslaagde wordt vernieuwd die worden gedeeld door het totaal aantal vernieuwingen om te meten. Betrouwbaarheid. |
| Gemiddelde duur (min) | de gemiddelde duur van een vernieuwing voor de gegevensset, in minuten.  |
| Max. duur (min.) | de duur van de langst lopende vernieuwing voor de gegevensset, in minuten. |
| Gemiddelde wachttijd (min.) | de gemiddelde vertraging tussen de geplande tijd en het begin van een vernieuwing voor de gegevensset, in minuten. |
| Maximale wachttijd (min.) | de maximale wachttijd voor de gegevensset, in minuten. |

##### <a name="query"></a>Query

| **Meting** | **Beschrijving** |
| --- | --- |
| Totale aantal | het totale aantal query's dat wordt uitgevoerd voor de gegevensset. |
| Gemiddelde duur (ms) |de gemiddelde queryduur voor de gegevensset, in milliseconden|
| Maximale duur (ms) |de duur van de langst lopende query in de gegevensset, in milliseconden. |
| Gemiddelde wachttijd (ms) |de gemiddelde querywachtduur voor de gegevensset, in milliseconden. |
| Maximale wachttijd (ms) |de duur van de langst wachtende query in de gegevensset, in milliseconden. |

##### <a name="eviction"></a>Verwijdering

| **Meting** | **Beschrijving** |
| --- | --- |
| Model-aantal | Het totale aantal gegevensset databasebestandspagina's voor deze capaciteit. Wanneer een capaciteit geheugendruk ervaart, worden via het knooppunt een of meer gegevenssets uit het geheugen verwijderd. Gegevenssets die niet actief zijn (waarvoor op dat moment geen query- of vernieuwingsbewerkingen worden uitgevoerd) worden het eerst verwijderd. Vervolgens wordt de volgorde van verwijderen gebaseerd op een meting van 'minst recentelijk gebruikt' (least recently used, LRU). |

#### <a name="paginated-reports"></a>Gepagineerde rapporten

##### <a name="report-execution"></a>Uitvoering van statusrapporten

| **Meting** | **Beschrijving** |
| --- | --- |
| Aantal uitvoeringen  | Het aantal keren dat het rapport is uitgevoerd en bekeken door gebruikers.|

##### <a name="report-usage"></a>Rapport gebruik

| **Meting** | **Beschrijving** |
| --- | --- |
| Aantal geslaagd | Het aantal keren dat die het rapport heeft bekeken door een gebruiker. |
| Aantal mislukt |Het aantal keren dat die het rapport heeft bekeken door een gebruiker.|
| Aantal rijen |het aantal rijen met gegevens in het rapport. |
| Data Retrieval Duration (ms) |de gemiddelde tijd die het kost om gegevens voor het rapport op te halen, in milliseconden. Als dit lang duurt, kan dit duiden op langzame query's of andere problemen met gegevensbronnen.  |
| Verwerking van de duur (ms) |de gemiddelde tijd die het kost om gegevens voor een rapport te verwerken, in milliseconden. |
| Rendering duur (ms) |de gemiddelde tijd die het kost om een rapport weer te geven in de browser, in milliseconden. |

> [!NOTE]
> Gedetailleerde metrische gegevens voor de **AI** werkbelasting nog niet beschikbaar.

## <a name="next-steps"></a>Volgende stappen

U hebt geleerd hoe u Power BI Premium-capaciteiten kunt bewaken. U kunt nu meer leren over het optimaliseren van capaciteiten.

> [!div class="nextstepaction"]
> [Power BI Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)
