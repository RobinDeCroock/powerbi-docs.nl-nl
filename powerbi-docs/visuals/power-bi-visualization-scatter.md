---
title: Spreidings-, bellen- en eendimensionale puntdiagrammen in Power BI
description: Spreidingsdiagrammen, eendimensionale puntdiagrammen en bellendiagrammen in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 26dd55f1084d62f9506b02c5852f0396adba305a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61070485"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Spreidingsdiagrammen, bellendiagrammen en eendimensionale puntdiagrammen in Power BI
Een spreidingsdiagram heeft altijd twee waardeassen, waarbij een reeks numerieke gegevens op een horizontale as en een andere reeks numerieke waarden op de verticale as wordt weergegeven. In het diagram worden punten weergegeven op het snijpunt van een numerieke x- en y-waarde, waarbij deze waarden in één gegevenspunt worden gecombineerd. Deze gegevenspunten kunnen, afhankelijk van de gegevens, gelijkmatig of ongelijkmatig over de horizontale as zijn verdeeld.

Bij een bellendiagram worden de gegevenspunten vervangen door bellen. De *grootte* van de bellen geeft de gegevens een extra dimensie.

![voorbeeld van bellendiagram](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Een eendimensionaal puntdiagram lijkt erg op een bellendiagram en een spreidingsdiagram, behalve dat u numerieke of categorische gegevens langs de X-as kunt plaatsen. 

![voorbeeld van bellendiagram](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

U kunt het aantal gegevenspunten instellen tot maximaal 10.000.  

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>Wanneer u een spreidingsdiagram of bellendiagram gebruikt
### <a name="scatter-charts-are-a-great-choice"></a>In de volgende gevallen komen spreidingsdiagrammen goed van pas:
* om relaties weer te geven van tussen de 2 (spreiding) of 3 (bellen) **numerieke** waarden.
* om twee groepen getallen als een reeks xy-coördinaten te tekenen.
* in plaats van een lijndiagram als u de schaal van de horizontale as wilt wijzigen    
* om de horizontale as om te zetten in een logaritmische schaal.
* om werkbladgegevens met paren of gegroepeerde sets waarden weer te geven. In een spreidingsdiagram kunt u de onafhankelijke schalen van de assen aanpassen voor meer informatie over de gegroepeerde waarden.
* om patronen weer te geven in grote gegevenssets, bijvoorbeeld door lineaire of niet-lineaire trends, clusters en uitschieters weer te geven.
* om grote aantallen gegevenspunten te vergelijken zonder rekening te houden met tijd.  Hoe meer gegevens u opneemt in een spreidingsdiagram, des te beter zijn de vergelijkingen die u kunt maken.

### <a name="bubble-charts-are-a-great-choice"></a>In de volgende gevallen komen bellendiagrammen goed van pas:
* als uw gegevens 3 gegevensreeksen bevatten met elk een set waarden.
* om financiële gegevens weer te geven.  Verschillende belgrootten zijn handig om specifieke waarden visueel te benadrukken.
* om te gebruiken met kwadranten.

### <a name="dot-plot-charts-are-a-great-choice-in-place-of-a-scatter-or-bubble"></a>Eendimensionale puntdiagrammen zijn een goede keuze als vervanging van een spreidings- of bellendiagram:
* als u categorische gegevens wilt opnemen langs de X-as

## <a name="create-a-scatter-chart"></a>Een spreidingsdiagram maken
Bekijk deze video voor informatie over de optie Een spreidingsdiagram maken en volg daarna de onderstaande stappen om zelf een spreidingsdiagram te maken.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


In deze instructies wordt het voorbeeld van een retailanalyse gebruikt. Om mee te lezen kunt u het [voorbeeld downloaden](../sample-datasets.md) voor de Power BI-service (app.powerbi.com) of voor Power BI Desktop.   

1. Open het rapport in de bewerkingsweergave en selecteer het gele pictogram met het plusteken om een lege rapportpagina te maken.
 
2. Selecteer de volgende velden in het deelvenster Velden:
   - **Verkoop** > **Verkoop per vierkante meter**
   - **Verkoop** > **Afwijkingspercentage totale verkoop**
   - **District** > **District**

     ![](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

     Als u de Power BI-service gebruikt, moet u het rapport openen in de [bewerkweergave](../service-interact-with-a-report-in-editing-view.md).

3. Converteer naar een spreidingsdiagram. Selecteer het pictogram voor spreidingsdiagrammen in het deelvenster Visualisaties.

   ![](media/power-bi-visualization-scatter/power-bi-scatter-new.png).

4. Sleep **District** van **Details** naar **Legenda**. We hebben nu een spreidingsdiagram die **Afwijking van totale verkoop in %** op de y-as afzet tegen de **verkoop per vierkante meter op de x-as**. De kleuren van de gegevenspunten vertegenwoordigen de districten:

    ![](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Nu gaan we een derde dimensie toevoegen.

## <a name="create-a-bubble-chart"></a>Een bellendiagram maken

1. Sleep **Verkoop** > **Omzet van dit jaar** > **Waarde** vanuit het deelvenster **Velden** naar het gebied **Grootte**. De gegevenspunten worden uitgevouwen naar volumes die evenredig zijn met de verkoopwaarde.
   
   ![punten worden bellen](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

2. Beweeg de muisaanwijzer over een bel. De grootte van de bel geeft de waarde van **Omzet van dit jaar** weer.
   
    ![weergave van knopinfo](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

3. Wanneer u het aantal gegevenspunten zo wilt instellen dat deze in uw bellengrafiek worden weergegeven, vouwt u in de sectie **Indeling** van het deelvenster **Visualisaties** de kaart **Algemeen** uit en past u het **gegevensvolume** aan. U kunt het maximale gegevensvolume instellen op een willekeurige waarde tot 10.000. Naarmate u hogere getallen tegenkomt, raden we u aan eerst de prestaties te testen. 

    ![Gegevensvolume](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png) 

   Omdat meer gegevenspunten kan leiden tot een langere laadtijd, kunt u beter uw rapporten op internet en op mobiel uittesten en ervoor zorgen dat de prestaties overeenkomen met de verwachtingen van uw gebruikers als u toch besluit om rapporten te publiceren met beperkingen aan de bovengrens van de schaal. 

4. U kunt [de kleuren, labels, titels, achtergrond en meer van de visual wijzigen](service-getting-started-with-color-formatting-and-axis-properties.md). Voor een [betere toegankelijkheid](../desktop-accessibility.md) kunt u markeringsvormen aan elke regel toevoegen. Als u voor elke lijn een andere markeringsvorm gebruikt, is het makkelijker voor gebruikers om verschillende lijnen (of vlakken) van elkaar te onderscheiden. Als u de markeringsvorm wilt selecteren, vouwt u de kaart **Vormen** uit en selecteert u vervolgens een markeringsvorm.

      ![Vorm van markering](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

   U kunt ook de markeringsvorm wijzigen in een ruit, driehoek of vierkant:

   ![Vierkante markering](media/power-bi-visualization-scatter/pbi_scatter_chart_hover_square.png)

## <a name="create-a-dot-plot"></a>Een eendimensionaal puntdiagram maken
Als u een eendimensionaal puntdiagram wilt maken, vervangt u het veld voor de numerieke X-as door een categorisch veld.

Verwijder vanuit het venster **X-as** **Sales per sq ft** en vervang dit door **District > DM**.
   
![nieuw eendimensionaal puntdiagram](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)


## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

### <a name="your-scatter-chart-has-only-one-data-point"></a>**Uw spreidingsdiagram heeft slechts één gegevenspunt**
Hebt u een spreidingsdiagram gemaakt en wordt daarin slechts één gegevenspunt weergegeven waarin alle waarden op de x- en y-as worden samengevoegd?  Of worden in het diagram alle waarden langs een horizontale of verticale lijn weergegeven?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Voeg een veld toe aan het gebied **Details** om aan te geven hoe de waarden moeten worden gegroepeerd. Het veld moet uniek zijn voor elk punt dat moet worden weergegeven, bijvoorbeeld een eenvoudig rijnummer of id-veld.

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Als uw gegevens dit niet bevatten, maakt u een veld waarin uw x- en y-waarden samen worden gevoegd in iets unieks per punt:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

[Gebruik van de Query Editor van Power BI Desktop om een indexkolom toe te voegen](../desktop-add-custom-column.md) aan uw gegevensset om een nieuw veld te maken.  Voeg deze kolom toe aan het gebied **Details** van uw visualisatie.

## <a name="next-steps"></a>Volgende stappen

[High-density spreidingsdiagrammen](desktop-high-density-scatter-charts.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)

