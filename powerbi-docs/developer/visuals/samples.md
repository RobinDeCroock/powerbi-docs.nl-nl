---
title: Samples van Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel vindt u voorbeelden van Power BI-visuals, waaronder slicers, meer dan 20 typen grafieken, WebGL en R-visuals en -scripts. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 3da805a10a8b43dc7b1f1750583a79494557d519
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888484"
---
# <a name="samples-of-power-bi-visuals"></a>Voorbeelden voor Power BI-visuals

U kunt deze Power BI-visuals downloaden, gebruiken en wijzigen vanuit GitHub. Deze voorbeelden laten zien hoe u veelvoorkomende situaties kunt afhandelen bij het ontwikkelen met Power BI.

## <a name="slicers"></a>Slicers

Een slicer beperkt het deel van de gegevens dat wordt weergegeven in andere visualisaties in een rapport. Slicers zijn een van de manieren waarop u gegevens kunt filteren in Power BI.

| <img src="media/samples/chiclet-slicer.png" alt="Screenshot shows Chiclet Slicer." width="200">  | <img src="media/samples/timeline-slicer.png" alt="Screenshot shows Timeline slicer." width="200"> | <img src="media/samples/sample-slicer.png" alt="Screenshot shows Slicer sample." width="200">|
| ------------- | ------------- | -------------|
| [Chiclet-slicer](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Een afbeelding of tekstknoppen weergeven die als een filter in het canvas fungeren voor andere visuals | [Tijdlijnslicer](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Grafische datumbereikselector die filtert op datum | [Voorbeeld van slicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Toont het gebruik van de geavanceerde filter-API

## <a name="charts"></a>Grafieken

Doe inspiratie op in onze galerie met staafdiagrammen, cirkeldiagrammen, woordwolken en nog veel meer.

| <img src="media/samples/aster-plot.png" alt="Screenshot shows Aster Plot." width="200">  | <img src="media/samples/bullet-chart.png" alt="Screenshot shows Bullet chart." width="200"> | <img src="media/samples/Chord.png" alt="Screenshot shows Chord." width="200">|
| ------------- | ------------- | -------------|
| [Asterdiagram](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Een variatie op een standaardringdiagram, waarin een tweede waarde wordt gebruikt om een zwaaihoek te bewerkstelligen | [Uitgebreid staafdiagram ](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Een staafdiagram met extra visuals waarmee context wordt gegeven, die kan worden gebruikt voor het bijhouden van doelstellingen | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Een methode voor grafische weergave van de relatie tussen gegevens in een matrix
| <img src="media/samples/dot-plot.png" alt="Screenshot shows Dot plot." width="200"> | <img src="media/samples/dual-kpi.png" alt="Screenshot shows Dual K P I." width="200">| <img src="media/samples/enhanced-scatter.png" alt="Screenshot shows Enhanced Scatter." width="200"> 
| [Puntdiagram](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Geeft de frequentieverdeling op een prachtige manier weer | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Geeft een efficiënt beeld van twee metingen over een bepaalde periode, waarbij de trend voor de metingen op een gemeenschappelijke tijdlijn wordt weergegeven | [Verbeterde spreidingsgrafiek](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Verbeteringen in het bestaande spreidingsdiagram
| <img src="media/samples/forcegraph.png" alt="Screenshot shows Force Graph." width="200">| <img src="media/samples/gantt.png" alt="Screenshot shows Gantt." width="200">| <img src="media/samples/table-heatmap.png" alt="Screenshot shows Table Heatmap." width="200">
| [Krachtgrafiek](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagram met kromme paden waarvan de lay-out wordt bepaald door aantrekkende en afstotende krachten. Dit diagram kan worden gebruikt om verbindingen tussen entiteiten weer te geven | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Een staafdiagram waarin een projecttijdlijn of -schema met resources wordt weergegeven | [Tabelheatmap](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Gemakkelijk en intuïtief gegevens vergelijken met behulp van kleuren in een tabel
| <img src="media/samples/histogram-chart.png" alt="Screenshot shows Histogram chart." width="200"> | <img src="media/samples/linedot-chart.png" alt="Screenshot shows LineDot chart." width="200"> | <img src="media/samples/mekko-chart.png" alt="Screenshot shows Mekko chart." width="200"> 
| [Histogram](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Hiermee wordt de verdeling van gegevens over een ononderbroken interval of een bepaalde periode weergegeven | [LineDot-grafiek](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Een lijndiagram waarin de punten worden weergegeven in een animatie. Hiermee kunt u gegevens goed onder de aandacht brengen bij een publiek | [Mekkodiagram](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Een combinatie van een 100% gestapeld kolomdiagram en een 100% gestapeld staafdiagram die tot één weergave zijn samengevoegd
| <img src="media/samples/multikpi.png"alt="Schermopname van Multi-KPI." width="200"> | <img src="media/samples/powerkpi.png"alt="Schermopname van Power KPI." width="200"> | <img src="media/samples/powerkpi-matrix.png"alt="Schermopname van Power KPI-matrix." width="200"> 
| [Multi-KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Een krachtige multi-KPI-visualisatie met een sleutel-KPI en meerdere sparklines aan ondersteunende gegevens | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Een krachtige KPI-indicator met een grafiek met meerdere lijnen en labels voor de huidige datum, waarde en afwijkingen | [Power KPI Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Balanced scorecards en een onbeperkt aantal metrische gegevens en KPI's in een compacte, eenvoudig te lezen lijst
| <img src="media/samples/pulse-chart.png" alt="Screenshot shows Pulse chart." width="200">| <img src="media/samples/radar-chart.png" alt="Screenshot shows Radar chart." width="200"> | <img src="media/samples/sankey-chart.png" alt="Screenshot shows Sankey chart." width="200"> 
| [Pulse-grafiek](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Dit lijndiagram met opmerkingen over belangrijke gebeurtenissen is ideaal wanneer u gegevens van achtergrondinformatie wilt voorzien| [Radardiagram](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Meerdere metingen worden weergegeven langs een categorische as, wat nuttig is om kenmerken te vergelijken | [Sankeydiagram](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Stroomdiagram waarbij de breedte van de reeks zich verhoudt tot de hoeveelheid van de stroom
| <img src="media/samples/stream-graph.png" alt="Screenshot shows Stream graph." width="200"> | <img src="media/samples/sunburst.png" alt="Screenshot shows Sunburst chart." width="200">| <img src="media/samples/tornado.png" alt="Screenshot shows Tornado chart." width="200">
| [Stroomgrafiek](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Een gestapeld vlakdiagram met een vloeiende interpolatie, dat wordt vaak gebruikt om waarden over een bepaalde periode weer te geven | [Zonnestraalgrafiek](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Ringdiagram met meerdere niveaus om hiërarchische gegevens weer te geven| [Tornadodiagram](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Het relatieve belang van variabelen voor twee groepen vergelijken
 | <img src="media/samples/word-cloud.png" alt="Screenshot shows Word Cloud." width="200">
 | [Woordwolk](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Een leuke visual maken van veelvoorkomende tekst in uw gegevens

## <a name="webgl"></a>WebGL

Met WebGL kan in webinhoud een API op basis van OpenGL ES 2.0 worden gebruikt voor 2D- en 3D-rendering in een HTML-canvas.

| <img src="media/samples/globe-map.png" alt="Screenshot shows Globe Map." width="250">|
| ------------- |
| [Wereldkaart](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Weergavelocaties op een interactieve 3D-kaart

## <a name="r-visuals"></a>R-visuals

Deze voorbeelden laten zien hoe u de analytische en visuele kracht van R-visuals en R-scripts kunt bundelen.

| <img src="media/samples/association-rules.png" alt="Screenshot shows Association rules." width="200">| <img src="media/samples/clustering.png" alt="Screenshot shows Clustering." width="200">| <img src="media/samples/clustering-with-outliers.png" alt="Screenshot shows Clustering with outliers." width="200">|
|------------- |------------- |------------- |------------- |
| [Association Rules](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Relaties tussen schijnbaar niet-gerelateerde gegevens opsporen met behulp van if-then-instructies | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Vergelijkbare groepen in uw gegevens zoeken met behulp van het k-means algoritme | [Clustering met uitschieters](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Vergelijkbare groepen en uitschieters in uw gegevens zoeken
| <img src="media/samples/correlation-plot.png" alt="Screenshot shows Correlation plot." width="200"> | <img src="media/samples/decision-tree-chart.png" alt="Screenshot shows Decision tree chart." width="200"> | <img src="media/samples/forecasting-tbats.png" alt="Screenshot shows Forecasting T B A T S." width="200"> 
| [Correlatie-grafiek](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>De variabelen met de hoogste correlatie in een gegevenstabel markeren | [Beslissingsboomstructuur](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Schematisch boomstructuurdiagram voor het bepalen van statistische waarschijnlijkheid met recursieve partitionering | [Prognose maken van TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Tijdreeksprognose voor reeksen met meerdere seizoensgebondenheden met behulp van het TBATS-model
| <img src="media/samples/forecasting-with-ARIMA.png" alt="Screenshot shows Forecasting with ARIMA." width="200"> | <img src="media/samples/funnel-plot.png" alt="Screenshot shows Funnel plot." width="200"> | <img src="media/samples/outliers-detection.png" alt="Screenshot shows Outliers detection." width="200"> 
| [Prognose maken met ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Toekomstige waarden voorspellen op basis van historische gegevens met behulp van Autoregressive Integrated Moving Avg (ARIMA) | [Trechterdiagram](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Uitschieters in uw gegevens vinden met behulp van een trechterdiagram | [Detectie van uitschieters](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Uitschieters in uw gegevens vinden met de meest geschikte methode en weergave
| <img src="media/samples/spline-chart.png" alt="Screenshot shows Spline chart." width="200"> | <img src="media/samples/time-series-decomposition-chart.png" alt="Screenshot shows Time Series decomposition chart." width="200"> | <img src="media/samples/time-series-forecasting-chart.png" alt="Screenshot shows Time series forecasting chart." width="200">
| [Spline-grafiek](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Ruis in gegevens visualiseren en begrijpen | [Tijdreeksontledingsgrafiek](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>De tijdreeksonderdelen begrijpen met behulp van seizoen- en trendontleding met Loess | [Tijdreeks- en prognosediagram](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Een exponentieel vereffeningsmodel gebruiken om toekomstige waarden te voorspellen op basis van eerder geobserveerde waarden

## <a name="next-steps"></a>Volgende stappen

Als u zelf Power BI-visuals wilt gaan maken, raadpleegt u [Een aangepaste visual met cirkelkaart voor Power BI ontwikkelen](develop-circle-card.md).
