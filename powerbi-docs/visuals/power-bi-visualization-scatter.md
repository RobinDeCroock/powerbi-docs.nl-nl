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
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8222194359077cb0d88286a33d1c9b2a05f6bd80
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390838"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Spreidingsdiagrammen, bellendiagrammen en eendimensionale puntdiagrammen in Power BI

Een spreidingsdiagram heeft altijd twee waardeassen, waarbij een reeks numerieke gegevens op een horizontale as en een andere reeks numerieke waarden op de verticale as wordt weergegeven. In het diagram worden punten weergegeven op het snijpunt van een numerieke x- en y-waarde, waarbij deze waarden in één gegevenspunt worden gecombineerd. Power BI kan deze gegevenspunten gelijkmatig of ongelijkmatig over de horizontale as verdelen. Dat hangt ervan af welke gegevens het diagram vertegenwoordigt.

Bekijk deze video voor informatie over de optie Een spreidingsdiagram maken en volg daarna de onderstaande stappen om zelf een spreidingsdiagram te maken.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

U kunt het aantal gegevenspunten instellen tot maximaal 10.000.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>Wanneer een spreidingsdiagram, bellendiagram of eendimensionaal puntdiagram gebruiken

### <a name="scatter-and-bubble-charts"></a>Spreidings- en bellendiagrammen

Een spreidingsdiagram toont de relatie tussen twee numerieke waarden. Bij een bellendiagram worden de gegevenspunten vervangen door bellen. Hierbij vertegenwoordigt de *grootte* van de bellen een derde, extra dimensie voor de gegevens.

![Schermopname van een voorbeeld van een bellendiagram.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

In de volgende gevallen komen spreidingsdiagrammen goed van pas:

* Om relaties tussen twee numerieke waarden weer te geven.

* Om twee groepen getallen als één reeks X- en Y-coördinaten uit te zetten.

* Om te gebruiken in plaats van een lijndiagram wanneer u de schaal van de horizontale as wilt wijzigen.

* Om de horizontale as om te zetten in een logaritmische schaal.

* Om werkbladgegevens weer te geven met die paren of gegroepeerde sets waarden bevatten.

    > [!TIP]
    > In een spreidingsdiagram kunt u de onafhankelijke schalen van de assen aanpassen voor meer informatie over de gegroepeerde waarden.

* Om patronen weer te geven in grote gegevenssets, bijvoorbeeld door lineaire of niet-lineaire trends, clusters en uitbijters weer te geven.

* Om grote aantallen gegevenspunten te vergelijken zonder rekening te houden met tijd.  Hoe meer gegevens u opneemt in een spreidingsdiagram, des te beter zijn de vergelijkingen die u kunt maken.

Naast wat spreidingsdiagrammen voor u kunnen doen, zijn bellendiagrammen in de volgende gevallen een goede keuze:

* Als uw gegevens drie gegevensreeksen bevatten met elk een set waarden.

* Om financiële gegevens weer te geven.  Verschillende belgrootten zijn handig om specifieke waarden visueel te benadrukken.

* Om te gebruiken met kwadranten.

### <a name="dot-plot-charts"></a>Eendimensionale puntdiagrammen

Een eendimensionaal puntdiagram lijkt erg op een bellendiagram en een spreidingsdiagram, behalve dat u ook numerieke of categorische gegevens langs de X-as kunt uitzetten.

![Schermopname van een eendimensionaal puntdiagram.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Dit type diagram is een prima keuze als u categorische gegevens wilt uitzetten langs de X-as.

## <a name="prerequisites"></a>Vereisten

* De Power BI service

* Het rapport Voorbeeld van een retailanalyse

## <a name="create-a-scatter-chart"></a>Een spreidingsdiagram maken

Als u mee wilt doen, meld u zich aan bij de [Power BI-service](https://app.powerbi.com) en opent u het rapport [Voorbeeld van een retailanalyse](../sample-datasets.md) in de weergave [Rapport bewerken](../service-interact-with-a-report-in-editing-view.md).

1. Selecteer ![Schermopname van het gele pluspictogram.](media/power-bi-visualization-scatter/power-bi-yellow-plus-icon.png) om een lege rapportpagina te maken.

1. Selecteer in het deelvenster **Velden** deze velden:

    * **Verkoop** > **Verkoop per vierkante meter**

    * **Verkoop** > **Afwijkingspercentage totale verkoop**

    * **District** > **District**

    ![Schermopname van het gegroepeerde kolomdiagram, het deelvenster Visualisaties en het deelvenster Velden met de velden die u hebt geselecteerd omkaderd.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. Selecteer ![Schermopname van het pictogram voor spreidingsdiagrammen.](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) in het deelvenster **Visualisaties** om het gegroepeerde kolomdiagram om te zetten in een spreidingsdiagram.

   ![Schermopname van een gegroepeerd kolomdiagram dat wordt omgezet in een spreidingsdiagram.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Sleep **District** van **Details** naar **Legenda**.

    Power BI genereert een spreidingsdiagram waarin **Total Sales Variance %** wordt uitgezet langs de Y-as en **Sales Per Square Feet** langs de X-as. De kleuren van de gegevenspunten vertegenwoordigen de districten:

    ![Schermopname van het spreidingsdiagram.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Nu gaan we een derde dimensie toevoegen.

## <a name="create-a-bubble-chart"></a>Een bellendiagram maken

1. Sleep **Sales** > **This Year Sales** > **Value** vanuit het deelvenster **Velden** naar het vak **Grootte**. De gegevenspunten worden uitgevouwen naar volumes die evenredig zijn met de verkoopwaarde.

   ![Schermopname van een spreidingsdiagram dat wordt omgezet in een bellendiagram door Sales Value toe te voegen aan het vak Grootte.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Beweeg de muisaanwijzer over een bel. De grootte van de bel geeft de waarde van **Omzet van dit jaar** weer.

    ![weergave van knopinfo](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

1. Wanneer u het aantal gegevenspunten wilt instellen dat wordt weergegeven in uw bellendiagram, vouwt u in de sectie **Indeling** van het deelvenster **Visualisaties** de kaart **Algemeen** uit en past u de waarde voor **Gegevensvolume** aan.

    ![Schermopname van het deelvenster Visualisaties met het pictogram Indeling, de vervolgkeuzelijst Algemeen en de optie Gegevensvolume omkaderd.](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png)

    U kunt het maximale gegevensvolume instellen op een willekeurige waarde tot 10.000. Naarmate u hogere getallen tegenkomt, raden we u aan eerst de prestaties te testen.

    > [!NOTE]
    > Meer gegevenspunten kunnen leiden tot een langere laadtijd. Als u toch besluit om rapporten te publiceren met beperkingen voor de bovengrens van de schaal, zorg er dan voor dat u de rapporten test op internet en op mobiele apparaten. Het is immers belangrijk dat de prestaties van de grafiek overeenkomen met de verwachtingen van uw gebruikers.

1. U kunt [de kleuren, labels, titels, achtergrond en meer van de visual wijzigen](service-getting-started-with-color-formatting-and-axis-properties.md).

    Voor een [betere toegankelijkheid](../desktop-accessibility.md) kunt u markeringsvormen aan elke regel toevoegen. Als u de markeringsvorm wilt selecteren, vouwt u **Vormen** uit, selecteert u **Vorm van markering** en selecteert u een vorm.

    ![Schermopname van de vervolgkeuzelijst Vormen met de opties voor markeringsvormen omkaderd.](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

    U kunt de markeringsvorm wijzigen in een ruit, driehoek of vierkant. Als u voor elke lijn een andere markeringsvorm gebruikt, is het makkelijker voor rapportgebruikers om verschillende lijnen (of vlakken) van elkaar te onderscheiden.

## <a name="create-a-dot-plot-chart"></a>Een eendimensionaal puntdiagram maken

Als u een eendimensionaal puntdiagram wilt maken, vervangt u het veld voor de numerieke **X-as** door een categorisch veld.

Ga naar het deelvenster **X-as**, verwijder **Sales per sq ft** en vervang dit door **District** > **District Manager**.

![Schermopname van een nieuw eendimensionaal puntdiagram.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

### <a name="your-scatter-chart-has-only-one-data-point"></a>Uw spreidingsdiagram heeft slechts één gegevenspunt

Hebt u een spreidingsdiagram gemaakt en wordt daarin slechts één gegevenspunt weergegeven waarin alle waarden van de X- en Y-as worden samengevoegd?  Of worden in het diagram alle waarden langs een horizontale of verticale lijn weergegeven?

![Schermopname van een spreidingsdiagram met één gegevenspunt.](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Voeg een veld toe aan het vak **Details** om aan Power BI aan te geven hoe de waarden moeten worden gegroepeerd. Het veld moet uniek zijn voor elk punt dat moet worden weergegeven. Denk hierbij aan een rijnummer of id-veld.

![Schermopname van een spreidingsdiagram met RowNum toegevoegd aan het vak Details.](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Als uw gegevens dit niet bevatten, maakt u een veld waarin uw X- en Y-waarden worden samengevoegd in iets unieks per punt:

![Schermopname van een spreidingsdiagram met TempTime toegevoegd aan het vak Details.](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

[Gebruik van de Query Editor van Power BI Desktop om een indexkolom toe te voegen](../desktop-add-custom-column.md) aan uw gegevensset om een nieuw veld te maken. Voeg vervolgens deze kolom toe aan het vak **Details** van uw visualisatie.

## <a name="next-steps"></a>Volgende stappen

* [High-densitysampling in Power BI-spreidingsdiagrammen](desktop-high-density-scatter-charts.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
