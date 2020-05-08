---
title: Rondleiding maken door het deelvenster Rapportfilters
description: Een rapportfilter toevoegen aan een rapport in de Power BI-service voor gebruikers
author: mihart
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: cb3947ec7aaf6d67a22eb1d7543a57e66e87f5f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "79114455"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Rondleiding door het deelvenster Filters van het rapport

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

In dit artikel wordt het rapportvenster **Filters** in Power BI-service besproken. Gebruik de filters om nieuwe inzichten in uw gegevens te ontdekken.

Er zijn veel verschillende manieren om gegevens te filteren in Power BI. Zie [Over filters en markeren in Power BI-rapporten](../power-bi-reports-filters-and-highlighting.md) voor meer informatie over filters.

![Schermopname van een rapport in de browser, met een pijl die wijst naar de optie Filters.](media/end-user-report-filter/power-bi-report.png)

## <a name="working-with-the-report-filters-pane"></a>Het deelvenster Filters van het rapport gebruiken

Als een collega een rapport met u deelt, bekijk dan het deelvenster **Filters**. Het wordt soms samengevouwen aan de rechterzijde van het rapport. Selecteer het om het uit te breiden.

![Schermopname van het rapport met een uitgevouwen deelvenster Filters.](media/end-user-report-filter/power-bi-expand-filter-pane.png)

Het deelvenster **Filters** bevat filters die de rapport*ontwerper* aan het rapport heeft toegevoegd. *Gebruikers* als uzelf kunnen de bestaande filters gebruiken en wijzigingen opslaan, maar geen nieuwe filters aan het rapport toevoegen. In de bovenstaande schermopname heeft de ontwerper bijvoorbeeld drie filters op paginaniveau toegevoegd: **Segment is Alle**, **Jaar is 2014** en **Regio is Centraal**. U kunt deze filters gebruiken en wijzigen, maar u kunt geen vierde filter op paginaniveau toevoegen.

Rapporten in de Power BI-service houden alle wijzigingen bij die u in het deelvenster **Filters** maakt. De service past deze wijzigingen toe op de mobiele versie van het rapport. 

Als u de standaardinstellingen die de ontwerper heeft geconfigureerd voor het deelvenster **Filters** wilt herstellen, selecteert u **Standaardinstellingen herstellen** in de bovenste menubalk.

![Schermopname van het pictogram Standaardinstelling herstellen.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Als u de optie **Standaardinstellingen opnieuw instellen** niet ziet, is deze mogelijk uitgeschakeld door de rapport*ontwerper*. De *ontwerper* kan tevens specifieke filters vergrendelen, zodat u deze niet kunt wijzigen.

## <a name="view-all-the-filters-for-a-report-page"></a>Alle filters weergeven voor een rapportpagina

Het deelvenster **Filters** toont alle filters die door de ontwerper aan het rapport zijn toegevoegd. In het deelvenster **Filters** kunt u ook informatie over de filters weergeven en deze gebruiken. Sla wijzigingen die u maakt op of gebruik **Standaardinstelling herstellen** om de originele filterinstellingen te herstellen.

Als er wijzigingen zijn die u wilt opslaan, kunt u ook een persoonlijke bladwijzer maken. Raadpleeg [Wat zijn bladwijzers?](end-user-bookmarks.md) voor meer informatie.

Het venster **Filters** toont en beheert verschillende typen rapportfilters: rapport, rapportpagina en visual.

In dit voorbeeld hebben we een visual met drie filters geselecteerd. De rapportagepagina heeft ook filters; deze staan onder de kop **Filters op deze pagina**. Het gehele rapport heeft bovendien een filter voor **Datum**.

![Schermopname van een rapport met een visualisatie en markering van de bijbehorende filters.](media/end-user-report-filter/power-bi-filters-pane.png)

Naast sommige filters staat **(Alle)** . **(Alle)**  betekent dat alle waarden in het filter worden opgenomen. In de bovenstaande schermopname informeert **Segment (Alle)** dat deze rapportpagina gegevens bevat over alle productsegmenten. 

Iedereen die dit rapport bekijkt, kan met deze filters werken.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Alleen filters weergeven die zijn toegepast op een visual

Ga met de muisaanwijzer over de visual om het filterpictogram ![Schermopname van het filterpictogram](media/end-user-report-filter/power-bi-filter-icon.png) weer te geven en beter zicht te krijgen op de filters die op een specifieke visual zijn toegepast. Selecteer dat filterpictogram om een pop-upvenster weer te geven met alle filters, slicers, enz. die invloed hebben op die visual. De filters in de pop-up zijn dezelfde filters die worden weergegeven in het venster **Filters**, plus aanvullende filters die van invloed zijn op de geselecteerde visual.

![Schermopname van een lijst filters met pijlen die wijzen naar de posities van deze filters in het deelvenster Filters.](media/end-user-report-filter/power-bi-hover-filters.png)

Dit zijn de typen filters die in deze weergave kunnen worden weergegeven:

- Standaardfilters
- Slicers
- Kruislings markeren
- Kruislings filteren
- Geavanceerde filters
- Top N-filters
- Relatieve datumfilters
- Synchroonslicers
- Opname-/uitsluitingsfilters
- Filters die via een URL zijn doorgegeven

In dit voorbeeld:
1. Met **Inbegrepen** wordt aangegeven dat het visuele element is gefilterd. Dit betekent dat de staten Utah, Colorado en Texas zijn geselecteerd in een van de andere visuals op deze rapportpagina. In dit geval is het de kaart. Door de selectie van die drie staten worden de gegevens van alle andere staten niet weergegeven in het geselecteerde staafdiagram.  

1. **Datum** is een filter dat wordt toegepast op alle pagina's in dit rapport,

1. **Regio is Centraal** en **Jaar is 2014** zijn filters die zijn toegepast op deze rapport pagina en

4. **Fabrikant is VanArsdel, Natura, Aliqui of Pirum** is een filter dat wordt toegepast op de visual.


### <a name="search-in-a-filter"></a>Zoeken in een filter

Soms kan een filter een lange lijst waarden hebben. Gebruik het zoekvak om de gewenste waarde te zoeken en selecteren.

![Schermopname van hoe u kunt zoeken in een filter.](media/end-user-report-filter/power-bi-search.png)

### <a name="display-filter-details"></a>Filtergegevens weergeven

Bekijk de beschikbare waarden en tellingen om een filter te begrijpen.  Bekijk de details van het filter door de pijl naast de naam van het filter aan te wijzen en te selecteren.
  
![Schermopname van een filter dat aangeeft dat de regio West is geselecteerd.](media/end-user-report-filter/power-bi-filter-expand.png)

### <a name="change-filter-selections"></a>Filterselecties wijzigen

Een manier om te zoeken naar inzichten in gegevens, is door de filters te gebruiken. U kunt filterselecties wijzigen via de vervolgkeuzelijst naast de veldnaam.  Afhankelijk van het filter en type gegevens dat Power BI filtert, variëren uw opties van eenvoudige selecties in een lijst tot het identificeren van datum- of cijferbereiken. In het geavanceerde filter hieronder hebben we het filter **Total Units YTD** in de treemap gewijzigd naar 2000 tot 3000. U ziet dat door deze wijziging Pirum uit de treemap wordt verwijderd.
  
![Schermopname van een rapport en de bijbehorende filters, waarin de visual treemap is geselecteerd.](media/end-user-report-filter/power-bi-treemap-filters.png)

> [!TIP]
> Houd de CTRL-toets ingedrukt om meer dan één filterwaarde per keer te selecteren. De meeste filters ondersteunen meervoudige selectie.

### <a name="reset-filter-to-default"></a>De standaardwaarden van het filter opnieuw instellen

Selecteer **Standaardinstelling herstellen** in de bovenste menubalk als u alle wijzigingen die u in de filters hebt aangebracht wilt terugzetten.  Deze selectie herstelt de oorspronkelijke staat van de filters die door de rapportontwerper werden ingesteld.

![Schermopname van de optie Standaardinstelling herstellen.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Een filter wissen

Als u een filter wilt herstellen naar (Alle), wist u het filter door de gum naast de naam van het filter te selecteren.

![Schermopname van het gumpictogram.](media/end-user-report-filter/power-bi-eraser.png)
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Volgende stappen

Leer hoe en waarom [visuals elkaar in een rapport kruislings filteren en markeren](end-user-interactions.md)