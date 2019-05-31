---
title: Overzicht van de rapporteditor
description: De rapporteditor in de Power BI-service en de rapporteditor in Power BI Desktop zijn vergelijkbaar.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 66e40462081ee2f1156840d137d4c67ad0eb7b45
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61404724"
---
# <a name="tour-the-report-editor-in-power-bi"></a>Rondleiding door de rapporteditor in Power BI

De *rapporteditor* in de Power BI-service en de rapporteditor in Power BI Desktop zijn vergelijkbaar. Doorgaans begint u met het maken van rapporten in Power BI Desktop. Vervolgens publiceert u deze in de Power BI-service, waar u ze verder kunt aanpassen. De Power BI-service is ook de plek waar u de dashboards op basis van uw rapporten maakt.

Nadat u uw dashboards en rapporten hebt gemaakt, deelt u ze met de gebruikers van uw rapporten. Afhankelijk van de manier waarop u de rapporten deelt, kunnen uw eindgebruikers deze raadplegen (maar niet bewerken) in de leesweergave van de Power BI-service. Lees meer over [wat gebruikers van rapporten kunnen doen in de Power BI-service](consumer/end-user-reading-view.md). 

Deze video toont de rapporteditor in Power BI Desktop. Dit artikel beschrijft de rapporteditor in de Power BI-service. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

In de Power BI-service is de rapporteditor alleen beschikbaar in de bewerkingsweergave. Als u een rapport in de bewerkingsweergave wilt openen, moet u de eigenaar of maker van een rapport zijn of bijdrager zijn aan de app-werkruimte waarin het rapport zich bevindt.

De Power BI-rapporteditor bestaat uit drie delen:  

1. de deelvensters **Velden**, **Visualisaties** en **Filters**
2. bovenste navigatiebalken    
3. rapportcanvas     

![De delen van de rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-report-canvas.png)

## <a name="1-the-report-editor-panes"></a>1. De deelvensters van de rapporteditor
![Power BI-rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-report-panes.png)

Er zijn drie deelvensters zichtbaar wanneer u een rapport voor de eerste keer opent: Visualisaties, filters en velden. De deelvensters aan de linkerkant, Visualisaties en Filters, bepalen hoe uw visualisaties eruitzien (type, kleuren, filters, opmaak).  En het deelvenster aan de rechterkant, Velden, beheert de onderliggende gegevens die worden gebruikt in de visualisaties. 

De inhoud die wordt weergegeven in de rapporteditor, hangt af van de selecties die u in het rapportcanvas maakt.  Wanneer u bijvoorbeeld een afzonderlijke visual selecteert:

|  |  |
| --- | --- |
| ![Deelvensters van de rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-panes.png) |<ul><li>De bovenkant van het deelvenster Visualisatie identificeert het type visuele element dat wordt gebruikt; in dit voorbeeld een gegroepeerd kolomdiagram.<br><br></li> <li>Onder in het deelvenster Visualisatie (mogelijk moet u omlaag schuiven) worden de velden weergegeven die in het visuele element worden gebruikt. In deze grafiek worden FiscalMonth, DistrictManager en Total Sales Variance gebruikt. <br><br></li><li>Het deelvenster Filters (mogelijk moet u omlaag schuiven) geeft de filters weer die zijn toegepast. <br><br></li><li>In het deelvenster Velden vindt u de beschikbare tabellen en, als u de naam van een tabel uitvouwt, de velden waaruit deze tabel bestaat. Het gele lettertype laat u weten dat ten minste één veld uit deze tabel wordt gebruikt in de visualisatie.<br><br></li><li>![Pictogram met verfroller](media/service-the-report-editor-take-a-tour/power-bi-paint-roller-icon.png) Selecteer het pictogram met de verfroller om het opmaakvenster weer te geven voor de geselecteerde visualisatie.<br><br></li><li>![Pictogram met vergrootglas](media/service-the-report-editor-take-a-tour/power-bi-magnifying-icon.png) Selecteer het vergrootglaspictogram om het deelvenster Analyse weer te geven.</ul> |

## <a name="the-visualizations-pane"></a>Het deelvenster Visualisaties
![Bovenkant van deelvenster Visualisatie](media/service-the-report-editor-take-a-tour/selectviz.png)

Hier selecteert u een type visualisatie. De kleine afbeeldingen worden *sjablonen* genoemd. In de afbeelding hiervoor is het gegroepeerde staafdiagram geselecteerd. Als u niet eerst een type visualisatie selecteert, maar een visualisatie gaat samenstellen door velden te selecteren, kiest Power BI het type visualisatie voor u. U kunt de selectie van Power BI behouden, maar u kunt het type ook wijzigen door een andere sjabloon te selecteren. Verander zo vaak als u wilt om het type visualisatie te vinden dat het beste bij uw gegevens past.

### <a name="manage-the-fields-in-your-visual"></a>De velden in uw visual beheren
![Middelste gedeelte van deelvenster Visualisatie](media/service-the-report-editor-take-a-tour/power-bi-field-list.png)

De buckets (soms ook wel *wells* genoemd) die in dit deelvenster worden weergegeven, zijn afhankelijk van het type visualisatie dat u hebt geselecteerd.  Als u bijvoorbeeld een staafdiagram hebt geselecteerd, ziet u buckets voor: Waarden, As en Legenda. Wanneer u een veld selecteert, of naar het canvas sleept, voegt Power BI dat veld toe aan een van de buckets.  U kunt ook velden uit de lijst Velden rechtstreeks in de buckets slepen.  Sommige buckets zijn beperkt tot bepaalde typen gegevens.  **Waarden** accepteert bijvoorbeeld geen niet-numerieke velden. Dus als u een veld **naamwerknemer** naar de bucket **Waarden** sleept, verandert Power BI dit in **aantal naamwerknemer**.

### <a name="remove-a-field"></a>Een veld verwijderen
Als u een veld wilt verwijderen uit de visualisatie, selecteert u de **X** rechts van de veldnaam.

![Winkeltype verwijderen uit de legenda](media/service-the-report-editor-take-a-tour/deletefield.png)

Zie [Add visualizations to a Power BI report](visuals/power-bi-report-add-visualizations-i.md) (Visualisaties toevoegen aan een Power BI-rapport) voor meer informatie

### <a name="format-your-visuals"></a>Uw visuele elementen opmaken
Selecteer het pictogram met de verfroller om het venster Opmaken weer te geven. Welke opties er beschikbaar zijn, is afhankelijk van het type visualisatie dat is geselecteerd.

![Het deelvenster Opmaak in de rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-formatting.png)

De opmaakmogelijkheden zijn praktisch eindeloos.  Als u meer wilt weten of zelf op verkenning wilt uitgaan, leest u deze artikelen:

* [De titel, achtergrond en legenda van een visualisatie aanpassen](visuals/power-bi-visualization-customize-title-background-and-legend.md)
* [Kleuropmaak](visuals/service-getting-started-with-color-formatting-and-axis-properties.md)
* [De eigenschappen van de X-as en Y-as aanpassen](visuals/power-bi-visualization-customize-x-axis-and-y-axis.md)

### <a name="add-analytics-to-your-visualizations"></a>Analytische gegevens toevoegen aan uw visualisaties
Selecteer het vergrootglaspictogram om het deelvenster Analyse weer te geven. Welke opties er beschikbaar zijn, is afhankelijk van het type visualisatie dat is geselecteerd.

![Het deelvenster Analyse in de rapporteditor](media/service-the-report-editor-take-a-tour/power-bi-analytics.png)    
Met het deelvenster Analyse in de Power BI-service kunt u dynamische referentielijnen aan visualisaties toevoegen en de aandacht vestigen op belangrijke trends en inzichten. Raadpleeg [Het deelvenster Analyse in de Power BI-service](service-analytics-pane.md) of [Het deelvenster Analyse in Power BI Desktop](desktop-analytics-pane.md) voor meer informatie.

- - -
## <a name="the-filters-pane"></a>Het deelvenster Filters
Via het deelvenster Filters kunt u permanente filters bekijken, instellen en aanpassen voor uw rapporten op niveau van pagina, rapport, drillthrough en visuele elementen. Ja, u kunt filters toepassen voor specifieke rapportpagina's en visuele elementen door bepaalde elementen te selecteren of met behulp van tools als slicers. Door het deelvenster Filters te gebruiken, wordt de status van de filters opgeslagen met het rapport. 

Het deelvenster Filters heeft nog een andere krachtige functie: de mogelijkheid om te filteren op een veld ***dat nog niet wordt gebruikt in een van de visuals in uw rapport***. Dit werkt als volgt. Wanneer u een rapportpagina maakt, voegt Power BI automatisch alle velden die u gebruikt in uw visualisaties toe aan het filtergebied op niveau van visuele elementen van het deelvenster Filters.  Als u echter een filter wilt instellen voor een visueel element, pagina, drillthrough of rapport met behulp van een veld dat momenteel niet wordt gebruikt in een visualisatie, sleept u het naar een van de filterbuckets.   

![Deelvenster Filters](media/service-the-report-editor-take-a-tour/power-bi-formatting-pane.png)

Zie [Add a filter to a report](power-bi-report-add-filter.md) (Een filter toevoegen aan een rapport) voor meer informatie.

Een nieuwe filterervaring is momenteel in preview. De nieuwe filters kunt u zo indelen dat ze eruitzien als het rapport zelf. U kunt ook filters vergrendelen of verbergen voor de gebruikers van uw rapport. 

![Nieuwe filterfunctionaliteit](media/service-the-report-editor-take-a-tour/power-bi-filter-reading.png)

Lees meer over de [nieuwe filterervaring](power-bi-report-filter-preview.md).

- - -
## <a name="the-fields-pane"></a>Het deelvenster Velden
In het deelvenster Velden worden de tabellen en velden weergegeven die zijn opgenomen in uw gegevens en die u kunt gebruiken om visualisaties te maken.

|  |  |
| --- | --- |
| ![Het deelvenster Velden](media/service-the-report-editor-take-a-tour/reportfields.png) |<ul><li>Sleep een veld naar de pagina om een nieuwe visualisatie te starten.  U kunt ook een veld naar een bestaande visualisatie slepen om het veld toe te voegen aan die visualisatie.<br><br></li> <li>Wanneer u een selectievakje naast een veld inschakelt, voegt Power BI dat veld toe aan de actieve (of nieuwe) visualisatie. En het programma beslist ook in welke bucket dat veld moet worden geplaatst.  Moet het veld bijvoorbeeld worden gebruikt als een legenda, as of waarde? Power BI maakt een inschatting en u kunt het indien nodig verplaatsen van die bucket naar een andere. <br><br></li><li>In beide gevallen wordt elk geselecteerde veld toegevoegd aan het deelvenster Visualisaties in de rapporteditor.</li></ul> |

**OPMERKING**: als u Power BI Desktop gebruikt, hebt u ook hebt opties om velden weer te geven/te verbergen, berekeningen toe te voegen enzovoort.

### <a name="what-do-the-field-icons-mean"></a>Wat betekenen de veldpictogrammen?
**∑ Aggregaties** Een aggregatie is een numerieke waarde die wordt opgeteld of waarvan een gemiddelde wordt genomen. Aggregaties worden geïmporteerd samen met de gegevens (die zijn gedefinieerd in het gegevensmodel waarop uw rapport is gebaseerd).
Zie [Aggregates in Power BI reports](service-aggregates.md) (Aggregaties in Power BI-rapporten) voor meer informatie.

![Pictogram met rekenmachine](media/service-the-report-editor-take-a-tour/pbi_calculated_icon.png) **Berekende metingen (ook wel berekende velden genoemd)**  
Elk berekend veld heeft zijn eigen in code vastgelegde formule. U kunt de berekening niet wijzigen; als de berekening bijvoorbeeld een som is, kan deze alleen een som zijn. Lees [Over metingen](desktop-measures.md) voor meer informatie

![Pictogram Uniek veld](media/service-the-report-editor-take-a-tour/icon.png) **Unieke velden**  
Velden met dit pictogram zijn geïmporteerd vanuit Excel en zijn ingesteld om alle waarden weer te geven, ook als ze duplicaten bevatten. Stel dat uw gegevens twee records bevatten voor mensen met de naam 'John Smith' en elk record wordt beschouwd als uniek; ze worden niet bij elkaar opgeteld.  

**![Pictogram Geografie](media/service-the-report-editor-take-a-tour/pbi_geo_icon.png) Geografievelden**  
Locatievelden kunnen worden gebruikt om kaartvisualisaties te maken. 

**![Pictogram Hiërarchie](media/service-the-report-editor-take-a-tour/power-bi-hierarchy-icon.png) Hiërarchie**  
Selecteer de pijl om de velden weer te geven die de hiërarchie vormen. 

## <a name="2-the-top-navigation-bar"></a>2. De bovenste navigatiebalk
Er zijn talrijke acties beschikbaar in de bovenste navigatiebalk; er worden ook voortdurend nieuwe acties toegevoegd. Gebruik de inhoudsopgave bij de Power BI-documentatie of het vak Zoeken voor informatie over een bepaalde actie.

## <a name="3-the-report-canvas"></a>3. Het rapportcanvas
In het rapportcanvas wordt uw werk weergegeven. Wanneer u de deelvensters Velden, Filters en Visualisaties gebruikt om visuele elementen te maken, worden deze samengesteld en weergegeven op uw rapportcanvas. Elk tabblad aan de onderkant van het canvas vertegenwoordigt een pagina in het rapport. Selecteer een tabblad om die pagina te openen. 

## <a name="next-steps"></a>Volgende stappen
[Een rapport maken](service-report-create-new.md)

Meer informatie over rapporten in de [Power BI-service](service-report-create-new.md), [Power BI Desktop](desktop-report-view.md) en [mobiele Power BI-apps](consumer/mobile/mobile-apps-view-phone-report.md).

[Basisconcepten voor Power BI-ontwerpers](service-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

