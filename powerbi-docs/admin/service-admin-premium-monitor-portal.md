---
title: Power BI Premium-capaciteiten bewaken met behulp van de beheerportal
description: Gebruik de Power BI-beheerportal om uw Premium-capaciteiten te bewaken.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b6f6b819b5c31f655d0c0dc43d8852cb34b5a7a2
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512051"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Capaciteiten bewaken in de beheerportal

Op het tabblad **Status** in het gebied **Capaciteitsinstellingen** in de beheerportal vindt u een overzicht van metrische gegevens over uw capaciteit en ingeschakelde workloads.  

![Tabblad Capaciteitsstatus in de portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Als u meer uitgebreide metrische gegevens nodig hebt, gebruikt u de app [Metrische Power BI Premium-capaciteitsgegevens](service-admin-premium-monitor-capacity.md). De app biedt inzoomen en filteren, en de meest gedetailleerde metrische gegevens voor vrijwel elk aspect dat invloed heeft op de capaciteitsprestaties. Zie [Premium-capaciteiten bewaken met de app](service-admin-premium-monitor-capacity.md) voor meer informatie.

> [!IMPORTANT]
> Als er een hoog resourcegebruik is in uw Power BI Premium-capaciteit, wat leidt tot problemen met prestaties of betrouwbaarheid, kunt u e-mailmeldingen ontvangen om het probleem te identificeren en op te lossen. Dit kan een gestroomlijnde manier zijn om problemen met overbelaste capaciteiten op te lossen. Zie [Meldingen over capaciteit en betrouwbaarheid](service-interruption-notifications.md#capacity-and-reliability-notifications) voor meer informatie.

> [!NOTE]
> Power BI Premium heeft onlangs een nieuwe versie van Premium uitgebracht, genaamd **Premium Gen2**, die momenteel beschikbaar is als preview. Premium Gen2 vereenvoudigt het beheer van Premium-capaciteiten en vermindert de overhead voor beheer. Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie.

## <a name="system-metrics"></a>Metrische gegevens van het systeem

Op het tabblad **Status**, op het hoogste niveau, bieden het CPU-gebruik en geheugengebruik een snel overzicht van de belangrijkste metrische gegevens voor de capaciteit. Deze metrische gegevens zijn cumulatief en omvatten alle ingeschakelde workloads voor de capaciteit.

| **Meting** | **Beschrijving** |
| --- | --- |
| CPU-GEBRUIK | Gemiddeld CPU-gebruik, als percentage van de totale beschikbare CPU. |
| GEHEUGENGEBRUIK | Gemiddeld geheugengebruik, in gigabytes (GB).|

## <a name="workload-metrics"></a>Metrische gegevens van workload

Voor elke workload die is ingeschakeld voor de capaciteit. Het CPU-gebruik en geheugengebruik worden weergegeven.

| **Meting** | **Beschrijving** |
| --- | --- |
| CPU-GEBRUIK | Gemiddeld CPU-gebruik, als percentage van de totale beschikbare CPU. |
| GEHEUGENGEBRUIK | Gemiddeld geheugengebruik, in gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Gedetailleerde metrische gegevens van workload

Elke workload heeft aanvullende metrische gegevens. Welk type metrische gegevens wordt weergegeven, is afhankelijk van de workload. Als u gedetailleerde metrische gegevens voor een workload wilt weergeven, klikt u op de pijl voor uitvouwen (pijl omlaag).

![Workloadstatus uitvouwen](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Gegevensstromen

##### <a name="dataflow-operations"></a>Gegevensstroombewerkingen

| **Meting** | **Beschrijving** |
| --- | --- |
| Totale aantal | totaal aantal vernieuwingen voor elke gegevensstroom. |
| Aantal geslaagd | Totaal aantal geslaagde vernieuwingen voor elke gegevensstroom.|
| Gemiddelde duur (min.) | de gemiddelde duur van een vernieuwing voor de gegevensstroom, in minuten |
| Maximale duur (min.) | de duur van de langst lopende vernieuwing voor de gegevensstroom, in minuten. |
| Gemiddelde wachttijd (min.) | de gemiddelde vertraging tussen de geplande tijd en het begin van een vernieuwing voor de gegevensstroom, in minuten. |
| Maximale wachttijd (min.) | de maximale wachttijd voor de gegevensstroom, in minuten.  |

#### <a name="datasets"></a>Gegevenssets

##### <a name="refresh"></a>Vernieuwen

| **Meting** | **Beschrijving** |
| --- | --- |
| Totale aantal | het totale aantal vernieuwingen voor elke gegevensset. |
| Aantal geslaagd | Totaal aantal geslaagde vernieuwingen voor elke gegevensset. |
| Aantal mislukt | Totaal aantal mislukte vernieuwingen voor elke gegevensset. |
| Slagingspercentage  | Aantal geslaagde vernieuwingen gedeeld door het totale aantal te meten vernieuwingen. betrouwbaarheid. |
| Gemiddelde duur (min.) | de gemiddelde duur van een vernieuwing voor de gegevensset, in minuten.  |
| Maximale duur (min.) | de duur van de langst lopende vernieuwing voor de gegevensset, in minuten. |
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
| Aantal modellen | Het totale aantal verwijderingen van gegevenssets voor deze capaciteit. Wanneer een capaciteit geheugendruk ervaart, worden via het knooppunt een of meer gegevenssets uit het geheugen verwijderd. Gegevenssets die niet actief zijn (waarvoor op dat moment geen query- of vernieuwingsbewerkingen worden uitgevoerd) worden het eerst verwijderd. Vervolgens wordt de volgorde van verwijderen gebaseerd op een meting van 'minst recentelijk gebruikt' (least recently used, LRU). |

#### <a name="paginated-reports"></a>Gepagineerde rapporten

##### <a name="report-execution"></a>Rapportuitvoering

| **Meting** | **Beschrijving** |
| --- | --- |
| Aantal uitvoeringen  | Het aantal keer dat het rapport is uitgevoerd en bekeken door gebruikers.|

##### <a name="report-usage"></a>Rapportgebruik

| **Meting** | **Beschrijving** |
| --- | --- |
| Aantal geslaagd | Het aantal keer dat het rapport is bekeken door een gebruiker. |
| Aantal mislukt |Het aantal keer dat het rapport is bekeken door een gebruiker.|
| Aantal rijen |het aantal rijen met gegevens in het rapport. |
| Duur van het ophalen van gegevens (ms) |de gemiddelde tijd die het kost om gegevens voor het rapport op te halen, in milliseconden. Als dit lang duurt, kan dit duiden op langzame query's of andere problemen met gegevensbronnen.  |
| Verwerkingsduur (ms) |de gemiddelde tijd die het kost om gegevens voor een rapport te verwerken, in milliseconden. |
| Weergaveduur (ms) |de gemiddelde tijd die het kost om een rapport weer te geven in de browser, in milliseconden. |

> [!NOTE]
> Gedetailleerde metrische gegevens voor de **AI**-workload zijn nog niet beschikbaar.

## <a name="next-steps"></a>Volgende stappen

U hebt geleerd hoe u Power BI Premium-capaciteiten kunt bewaken. U kunt nu meer leren over het optimaliseren van capaciteiten.

> [!div class="nextstepaction"]
> [Power BI Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)


Power BI heeft Power BI Premium Gen2 geïntroduceerd als preview-aanbieding, waardoor de Power BI Premium-ervaring als volgt wordt aangepast met verbeteringen:
* Prestaties
* Licenties per gebruiker
* Grotere schaal
* Verbeterde metrische gegevens
* Automatisch schalen
* Minder beheeroverhead

Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie over Power BI Premium Gen2.