---
title: Lijndiagrammen in Power BI
description: Lijndiagrammen in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535785"
---
# <a name="line-charts-in-power-bi"></a>Lijndiagrammen in Power BI
Een lijndiagram is een reeks gegevenspunten die worden vertegenwoordigd door punten en verbonden via rechte lijnen. Een lijndiagram kan bestaan uit een of meer regels. Lijndiagrammen hebben een X en Y-as. 

![een eenvoudig lijndiagram](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Maak een lijndiagram
Deze instructies gebruiken de verkoop en Marketing voorbeeld-app te maken van een lijndiagram waarin de verkoop van dit jaar per categorie wordt weergegeven. Als u wilt volgen, download u de voorbeeldapp in appsource.com.

1. Begin op een nieuwe, lege rapportpagina. Als u de Power BI-service gebruikt, moet u het rapport openen in de [bewerkweergave](../service-interact-with-a-report-in-editing-view.md).

2. Selecteer in het deelvenster velden **SalesFact** \> **totaal aantal eenheden**, en selecteer **datum** > **maand**.  Power BI maakt een kolomdiagram op uw rapportcanvas.

    ![Selecteer in het deelvenster velden](media/power-bi-line-charts/power-bi-step1.png)

4. Converteren naar een lijndiagram door het selecteren van de regelsjabloon grafiek in het deelvenster visualisaties. 

    ![converteren naar lijndiagram weer te geven](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Uw lijndiagram om weer te geven van gegevens voor het jaar 2012 2014 filteren. Als het deelvenster Filters is samengevouwen, vouwt u het nu. Selecteer in het deelvenster velden **datum** \> **jaar** en sleep deze naar het deelvenster Filters. Zet het neer onder de kop **Filters op dit visuele element**. 
     
    ![regel naast het deelvenster velden](media/power-bi-line-charts/power-bi-year-filter.png)

    Wijziging **geavanceerde filters** naar **basisfilters** en selecteer **2012**, **2013** en **2014**.

    ![Filter voor jaar](media/power-bi-line-charts/power-bi-filter-year.png)

6. U kunt desgewenst [de grootte en de kleur van de tekst van de grafiek aanpassen](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Tekengrootte vergroten en Y-axisfont wijzigen](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Extra regels toevoegen aan de grafiek
Lijndiagrammen kunnen veel verschillende regels hebben. En in sommige gevallen kan de waarden op de regels kunnen worden dus uiteenlopende dat ze goed bij elkaar passen niet weergeven. We bekijken aanvullende regels op onze huidige grafiek en ontdek hoe u onze diagram opmaken als de waarden die wordt vertegenwoordigd door de regels zeer verschillende zijn toe te voegen. 

### <a name="add-additional-lines"></a>Extra regels toevoegen
In plaats van het totaal aantal eenheden voor alle regio's als één regel in het diagram bekijkt, kunt u totaal aantal eenheden per regio we opgesplitst. Extra regels toevoegen door te slepen **Geo** > **regio** naar de bron van de legenda.

   ![Een regel voor elke regio](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Gebruik twee Y-assen
Wat gebeurt er als u wilt zoeken op de totale verkoop en totaal aantal eenheden in dezelfde grafiek? Verkoopcijfers zijn dus veel hoger dan eenhedengetallen, waardoor het lijndiagram onbruikbaar. De rode lijn voor totaal aantal eenheden lijkt in feite gelijk zijn aan nul.

   ![zeer uiteenlopende waarden](media/power-bi-line-charts/power-bi-diverging.png)

Zeer uiteenlopende waarden weergegeven op een grafiek, gebruikt u een combinatiegrafiek. U kunt meer informatie over combinatiegrafieken door te lezen [combinatiegrafieken in Power BI](power-bi-visualization-combo-chart.md). In het onderstaande voorbeeld kunt we verkoop- en totaal aantal eenheden samen in één grafiek weergeven door het toevoegen van een tweede Y-as. 

   ![zeer uiteenlopende waarden](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
* Een lijndiagram weer te geven geen dubbele Y-assen.  U moet in plaats daarvan een combinatiegrafiek gebruiken.
* In de bovenstaande voorbeelden zijn de grafieken zodanig ingedeeld dat de tekengrootte vergroten, tekstkleur wijzigen, astitels toevoegen, center de grafiektitel en legenda, start beide assen op nul en nog veel meer. Het deelvenster opmaak (verfrollerpictogram) heeft een eindeloze set met opties voor het maken van het uiterlijk van uw grafieken de manier waarop die u laten wilt. De beste manier om te leren is open het opmaakvenster en verkennen.

## <a name="next-steps"></a>Volgende stappen

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)


