---
title: Typen filters in Power BI-rapporten
description: Een paginafilter, visualisatiefilter of rapportfilter aan rapport in Power BI toevoegen
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874408"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Typen filters in Power BI-rapporten

Filters gedragen zich niet allemaal op dezelfde manier omdat ze niet op dezelfde manier zijn gemaakt. Hoe u ze maakt beïnvloedt hun gedrag in het nieuwe filterdeelventer in de bewerkingsmodus. In dit artikel beschrijven we de verschillende soorten filters: de verschillende manieren waarop u ze maakt en hun verschillende functies. Meer informatie over [filters toevoegen aan rapporten](power-bi-report-add-filter.md). 

![Filterdeelvenster](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Laten we beginnen met de twee meest voorkomende filtertypen: handmatige en automatische filters.

## <a name="manual-filters"></a>Handmatige filters 

Handmatige filters zijn de filters die makers van rapporten ergens in het nieuwe filterdeelvenster slepen en neerzetten. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen dit filter in het nieuwe deelvenster bewerken, verwijderen, wissen, verbergen, vergrendelen, een nieuwe naam geven of sorteren.

## <a name="automatic-filters"></a>Automatische filters 

Automatische filters zijn de filters die automatisch worden toegevoegd aan de visuele elementen van het filterdeelvenster wanneer u een visueel element bouwt. Deze filters zijn gebaseerd op de velden waaruit uw visuele element bestaat. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen dit filter in het nieuwe deelvenster bewerken, wissen, verbergen, vergrendelen, een nieuwe naam geven of sorteren. Ze kunnen de automatische filters niet verwijderen, omdat het visuele element naar die velden verwijst.

## <a name="more-advanced-filters"></a>Meer geavanceerde filters

De volgende filtertypen komen minder vaak voor, maar het is nog steeds belangrijk om ze te begrijpen als ze worden weergegeven in uw rapport. Bovendien zijn ze mogelijk nuttig voor u bij het maken van de juiste filter voor uw rapport.

## <a name="include-and-exclude-filters"></a>Opname- en uitsluitingsfilters

Opname- en uitsluitingsfilters worden automatisch toegevoegd aan het filterdeelvenster wanneer u de opname- en uitsluitingsfunctie voor een visueel element gebruikt. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen dit filter in het nieuwe deelvenster verwijderen, vergrendelen of sorteren. Ze kunnen een opname- of uitsluitingsfilter niet bewerken, wissen of een nieuwe naam geven, omdat het gekoppeld is aan de opname- en uitsluitingsfunctie van visuele elementen.

![Uitsluitingsfilter](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Inzoomfilters

Inzoomfilters worden automatisch toegevoegd aan het filterdeelvenster wanneer u de inzoomfunctie voor een visueel element in uw rapport gebruikt. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen dit filter in het nieuwe deelvenster bewerken of verwijderen. Ze kunnen dit filter niet verwijderen, verbergen, vergrendelen, een nieuwe naam geven of sorteren omdat het gekoppeld is aan de inzoomfunctie van visuele elementen. Om het inzoomfilter te verwijderen, klikt u op de uitzoomknop voor het visuele element.

![Inzoomfilter](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Kruisfilters

Kruisfilters worden automatisch toegevoegd aan het nieuwe deelvenster wanneer een inzoomfilter wordt doorgegeven aan een ander visueel element op de rapportpagina via de functie voor kruislings filteren of markeren. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen dit filter niet verwijderen, wissen, verbergen, verbergen, vergrendelen, een nieuwe naam geven of sorteren omdat het gekoppeld is aan de inzoomfunctie van visuele elementen. Ze kunnen dit filter ook niet bewerken omdat het voortkomt uit inzoomen in een ander visueel element. Om het inzoomfilter te verwijderen, klikt u op de uitzoomknop voor het visuele element dat het filter doorgeeft.

## <a name="drillthrough-filters"></a>Drillthrough-filters

Drillthrough-filters worden tussen pagina’s verstuurd via de drillthrough-functie. Ze worden weergegeven in het drillthrough-deelvenster. Er zijn twee typen drillthrough-filters. Het eerste type is het type dat de drillthrough aanroept. Rapportredacteurs kunnen dit type filter bewerken, verwijderen, wissen, verbergen of vergrendelen. Het tweede type is het drillthrough-filter dat aan het doel wordt doorgegeven op basis van de filters op paginaniveau van de bronpagina. Rapportredacteurs kunnen dit tijdelijke type drillthrough-filter bewerken, verwijderen of wissen. Ze kunnen dit filter niet vergrendelen of verbergen voor eindgebruikers.

## <a name="url-filters"></a>URL-filters

URL-filters worden toegevoegd aan het nieuwe deelvenster door een URL-query-parameter toe te voegen. Gebruikers met een bewerkingsmachtiging voor het rapport kunnen het filter in het nieuwe deelvenster bewerken, verwijderen of wissen. Ze kunnen dit filter niet verbergen, vergrendelen, een nieuwe naam geven of sorteren omdat het gekoppeld is aan de URL-parameter. Om het filter te verwijderen, verwijdert u de parameter uit de URL. Hier is een voorbeeld-URL met een parameter:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![URL-filter](media/power-bi-report-filter-types/power-bi-filter-url.png)

Meer informatie over [URL filters](service-url-filters.md).

## <a name="pass-through-filters"></a>Pass-through-filters

Pass-through-filters zijn filters op het niveau van visuele elementen, die door middel van Q&A worden gemaakt. Auteurs kunnen deze filters in het nieuwe deelvenster verwijderen, verbergen of sorteren. Ze kunnen deze filters echter niet een nieuwe naam geven, bewerken, wissen of vergrendelen.

![Pass-through-filter met Q&A](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Vergelijking tussen filtertypes

Deze tabel vergelijkt wat auteurs kunnen doen met de verschillende typen filters.

| Filtertype | Bewerken | Clear | Verwijderen | Verbergen | Vergrendelen | Sorteren | Naam wijzigen |
|----|----|----|----|----|----|----|----|
| Handmatige filters | J | J | J | J | J | J | J |
| Automatische filters | J | J | N | J | J | J | J |
| Opname-/uitsluitingsfilters | N | N | J | J | J | J | N |
| Inzoomfilters | J | J | N | N | N | N | N |
| Kruisfilters | N | N | N | N | N | N | N |
| Drillthrough-filters (roepen drillthrough aan) | J | J | J | J | J | N | N |
| Drillthrough-filters (tijdelijk) | J | J | J | N | N | N | N |
| URL-filters - tijdelijk | J | J | J | N | N | N | N |
| Pass-through-filters | N | N | J | J | N | J | N |



## <a name="next-steps"></a>Volgende stappen

[Filters aan rapporten toevoegen](power-bi-report-add-filter.md)

[Rondleiding door het deelvenster Filters van het rapport](consumer/end-user-report-filter.md)

[Filters en markeren in rapporten](power-bi-reports-filters-and-highlighting.md)

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

