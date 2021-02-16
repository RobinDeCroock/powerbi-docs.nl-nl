---
title: Een filter toevoegen aan een rapport in Power BI
description: Een paginafilter, visualisatiefilter of rapportfilter aan rapport in Power BI toevoegen
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 02/12/2021
LocalizationGroup: Reports
ms.openlocfilehash: f7c17b810070a79c9f4a9f4a0756cbcaa8831f18
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531761"
---
# <a name="add-a-filter-to-a-report-in-power-bi"></a>Een filter toevoegen aan een rapport in Power BI

In dit artikel wordt uitgelegd hoe u een visualisatie filter, pagina filter of rapport filter kunt toevoegen aan een rapport in Power BI. U moet een rapport kunnen bewerken om filters toe te voegen. De voor beelden in dit artikel bevinden zich in de Power BI-service en de stappen zijn bijna identiek in Power BI Desktop. Zoekt u een overzicht? Bekijk eerst de [filters en markeer deze in Power bi rapporten](power-bi-reports-filters-and-highlighting.md) .

![Nieuwe filterfunctionaliteit](media/power-bi-report-add-filter/power-bi-filter-reading.png)

Power BI biedt een aantal verschillende soorten filters, van handmatige en automatische filters tot drillthrough en passthrough. Lees hier meer over de [verschillende soorten filters](power-bi-report-filter-types.md).

Nadat u filters hebt toegevoegd, kunt u [de filters in uw Power bi-rapporten zodanig indelen](power-bi-report-filter.md) dat deze eruitzien en op de gewenste manier reageren.

## <a name="filters-in-editing-view-or-reading-view"></a>Filters in de bewerkingsweergave of leesweergave
U communiceert met rapporten in twee verschillende weer gaven: Lees weergave en bewerk weergave. In dit artikel wordt beschreven hoe u filters maakt in de **bewerkingsweergave** voor rapporten.  Zie [deze snelstartgids](../consumer/end-user-report-filter.md) voor meer informatie over filters in de leesweergave.

Omdat filters *behouden blijven* wanneer het rapport niet meer de focus heeft, behoudt Power BI gemaakte wijzigingen in het filter, de slicer en andere gegevensweergaven. U kunt dus verdergaan waar u bent gebleven wanneer u terugkeert naar het rapport. Als u niet wilt dat uw filter wordt gewijzigd, selecteert u **opnieuw instellen op standaard waarden** in de bovenste menu balk.

:::image type="content" source="../consumer/media/end-user-report-filter/power-bi-reset-icon.png" alt-text="Standaard pictogram opnieuw instellen.":::

Als de maker van het rapport, welke filters u met het rapport opslaat, worden de *Standaard filter status* voor al uw rapport lezers. Wanneer u **opnieuw instellen op standaard waarden** selecteert, keert dat terug naar.

## <a name="levels-of-filters-in-the-filters-pane"></a>Niveaus van filters in het deelvenster Filters
Of u nu Power BI Desktop of Power BI-service gebruikt, het deel venster filters wordt weer gegeven aan de rechter kant van het rapport papier. Als het deelvenster niet wordt weergegeven, selecteert u het symbool '>' in de rechterbovenhoek om het deelvenster uit te vouwen.

U kunt filters instellen op drie verschillende niveaus voor het rapport: op het niveau van de visuele niveaus, op pagina niveau en op rapportniveau. In dit artikel wordt uitgelegd hoe u de verschillende niveaus kunt instellen.

## <a name="add-a-filter-to-a-visual"></a>Een filter aan een visualisatie toevoegen
Visuele elementen hebben twee verschillende soorten filters.
U kunt op twee verschillende manieren een filter op het niveau van een visueel element toevoegen aan een visueel element. 

* De velden in een visueel element worden automatisch gefilterd op het visuele element. 
* Als Report Designer kunt u een veld identificeren dat nog niet het visuele element is en dit veld direct toevoegen aan de Bucket **filters op niveau van visuele elementen** .
 
Op de manier maakt dit artikel gebruik van het voor beeld van een retail analyse, als u dit wilt installeren en wilt volgen. Installeer het voor beeld-inhouds pakket voor de [Retail analyse](sample-retail-analysis.md#get-the-content-pack-for-this-sample) .

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filteren met een veld dat niet is opgenomen in de visualisatie

1. Selecteer in de Power BI-service **meer opties (...)**  >  **Bewerk** om uw rapport te openen in de bewerkings weergave.
   
   ![Knop rapport bewerken.](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Open de deel Vensters visualisaties, filters en velden als deze nog niet zijn geopend.
   
   ![De deelvensters Visualisaties, Filters en Velden](media/power-bi-report-add-filter/power-bi-display-panes.png)

3. Selecteer een visueel element om het te activeren. In dit geval is dit het spreidings diagram op de pagina overzicht. Alle velden in het visuele element bevinden zich in het deel venster **Visualisaties** . Ze worden ook weer gegeven in het deel venster **filters** , onder de **filters op deze Visual** -kop.
   
   ![Filters op visualisatieniveau selecteren](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
  
1. Selecteer in het deelvenster Velden het veld dat u wilt toevoegen als een nieuw filter op het niveau van visuele elementen en sleep het veld naar het gebied **Filters op niveau van visuele elementen**.  In dit voor beeld slepen we **categorie** om **gegevens velden hier** onder **filters in deze Visual** toe te voegen.
     
    ![Een veld toevoegen aan het deelvenster Filters](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    De **categorie** kennisgeving is *niet* toegevoegd aan de visualisatie zelf.
     
1. Selecteer **kinderen**. Het spreidings diagram wordt gefilterd, maar de andere visuele elementen blijven hetzelfde.
     
    ![Scherm afbeelding toont een spreidings diagram met de gefilterde waarden op basis van het nieuwe veld.](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Als u het rapport met dit filter opslaat, kunnen rapport lezers communiceren met het **categorie** filter in de Lees weergave, waarden selecteren of wissen.
    
    Als u een *numerieke kolom* naar het filtervenster sleept om een filter op visualniveau te maken, wordt het filter toegepast op de *onderliggende gegevensrijen*. Als u bijvoorbeeld een filter toevoegt voor het veld **UnitCost** en het instelt op **UnitCost** > 20, worden alleen gegevens weergegeven voor de productrijen waar de kosten per eenheid hoger zijn dan 20, ongeacht de totale kosten per eenheid voor de gegevenspunten die in de visual worden weergegeven.

## <a name="add-a-filter-to-an-entire-page"></a>Een filter toevoegen aan een hele pagina

U kunt ook een filter op paginaniveau toevoegen om een hele pagina te filteren.

1. Open in de Power BI-service het rapport Retail Analysis en ga vervolgens naar de pagina **District Monthly Sales**. 

2. Selecteer **...**  > **Rapport bewerken** om het rapport in de bewerkingsweergave te openen.
   
   ![De knop Rapport bewerken](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Open de deel Vensters visualisaties, filters en velden als deze nog niet zijn geopend.

3. Selecteer in het deelvenster Velden het veld dat u wilt toevoegen als een nieuw filter op paginaniveau en sleep het veld naar het gebied **Filters op paginaniveau**.  
4. Selecteer de waarden die u wilt filteren en stel het filtertype in op **Standaardfilters toepassen** of **Geavanceerd filteren**.
   
   Alle visualisaties op de pagina worden opnieuw getekend om de wijziging te weerspiegelen.
   
    Als u het rapport met het filter opslaat, kunnen lezers van het rapport met het filter werken in de leesweergave door waarden te selecteren of te wissen.

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>Een filter op rapportniveau toevoegen om een rapport volledig te filteren

1. Selecteer **Rapport bewerken** om het rapport in de bewerkweergave te openen.
   
   ![De knop Rapport bewerken](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Open het deelvenster Visualisaties en filters en het deelvenster Velden, indien deze nog niet zijn geopend.
3. Selecteer in het deelvenster Velden het veld dat u wilt toevoegen als een nieuw filter op rapportniveau en sleep het veld naar het gebied **Filters op rapportniveau**.  
4. Selecteer de waarden die u wilt filteren.

    De visuele elementen op de actieve pagina (en ook op alle andere pagina's van het rapport) worden gewijzigd overeenkomstig het nieuwe filter. Als u het rapport met het filter opslaat, kunnen lezers van het rapport met het filter werken in de leesweergave door waarden te selecteren of te wissen.

1. Selecteer de pijl Vorige om terug te keren naar de vorige rapportpagina.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

- Als het deel venster velden niet wordt weer gegeven, controleert u of u zich in de [bewerkings weergave](service-interact-with-a-report-in-editing-view.md)van het rapport bevindt.
- Als u een groot aantal wijzigingen hebt aangebracht in de filters en wilt terugkeren naar de standaard instellingen, selecteert u **opnieuw instellen op standaard waarden** in de bovenste menu balk. Houd er rekening mee dat de auteur van het rapport weet welke filters er zijn wanneer u *het rapport opslaat* als standaard instellingen voor het filter.

## <a name="next-steps"></a>Volgende stappen

[De filters in uw Power BI-rapporten opmaken](power-bi-report-filter.md)

[Rondleiding door het deelvenster Filters van het rapport](../consumer/end-user-report-filter.md)

[Filters en markeren in rapporten](power-bi-reports-filters-and-highlighting.md)

[Verschillende soorten filters in Power BI](power-bi-report-filter-types.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
