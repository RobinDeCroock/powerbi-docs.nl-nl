---
title: Rondleiding maken door het deelvenster Rapportfilters
description: Een filter toevoegen aan een rapport in de Power BI-service voor zakelijke gebruikers
author: mihart
ms.reviewer: mihart
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/29/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb283858d9e6fe016e382f4c662de6b66bce0258
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91600697"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Rondleiding door het deelvenster Filters van het rapport

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

In dit artikel wordt het rapportvenster **Filters** in Power BI-service besproken. Gebruik de filters om nieuwe inzichten in uw gegevens te ontdekken.

Er zijn veel verschillende manieren om gegevens te filteren in Power BI. In dit artikel wordt uitgelegd hoe u het deelvenster **Filters** gebruikt.  U kunt ook filteren door gegevenspunten in een rapportvisual te selecteren om de andere visuals op de pagina te filteren. Dit wordt **kruislingse filtering** en **kruislingse markering** genoemd. Raadpleeg [Filters en markeringen in Power BI-rapporten](../create-reports/power-bi-reports-filters-and-highlighting.md) voor meer informatie over kruislingse filtering en kruislingse markering.

![Schermopname van een rapport in de browser, met een pijl die wijst naar de optie Filters.](media/end-user-report-filter/power-bi-reports.png)

## <a name="working-with-the-report-filters-pane"></a>Het deelvenster Filters van het rapport gebruiken

Als een collega een rapport met u deelt, bekijk dan het deelvenster **Filters**. Het wordt soms samengevouwen aan de rechterzijde van het rapport. Selecteer het om het uit te breiden.

![Schermopname van het rapport met een uitgevouwen deelvenster Filters.](media/end-user-report-filter/power-bi-expand-filters-pane.png)

Het deelvenster **Filters** bevat filters die de rapport*ontwerper* aan het rapport heeft toegevoegd. *Zakelijke gebruikers* als uzelf kunnen de bestaande filters gebruiken en wijzigingen opslaan, maar geen nieuwe filters aan het rapport toevoegen. In de bovenstaande schermopname heeft de ontwerper bijvoorbeeld drie filters op paginaniveau toegevoegd: **Segment is Alle**, **Jaar is 2014** en **Regio is Centraal**. U kunt deze filters gebruiken en wijzigen, maar u kunt geen vierde filter op paginaniveau toevoegen.

Sommige filters zijn gearceerd, en andere niet. Als een filter is gearceerd, betekent dit dat er een filter is toegepast en dat sommige gegevens worden uitgesloten. De filterkaart **Regio** is bijvoorbeeld gearceerd. Wanneer u de kaart uitvouwt, ziet u dat alleen **Centraal** is geselecteerd in de vervolgkeuzelijst. Omdat Regio zich onder de koptekst **Filters op deze pagina** bevindt, worden in alle visuals op deze pagina de regio’s **West** en **Oost** uitgesloten.

![Schermopname van de filter Regio uitgevouwen, en met de optie Centraal weergegeven met een vinkje.](media/end-user-report-filter/power-bi-filter-region.png)

Rapporten in de Power BI-service houden alle wijzigingen bij die u in het deelvenster **Filters** maakt. De service past deze wijzigingen toe op de mobiele versie van het rapport. 

Als u de standaardinstellingen die de ontwerper heeft geconfigureerd voor het deelvenster **Filters** wilt herstellen, selecteert u **Standaardinstellingen herstellen** in de bovenste menubalk.

![Schermopname van het pictogram Standaardinstelling herstellen.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Als u de optie **Standaardinstellingen opnieuw instellen** niet ziet, is deze mogelijk uitgeschakeld door de rapport*ontwerper*. De *ontwerper* kan tevens specifieke filters vergrendelen, zodat u deze niet kunt wijzigen.

## <a name="view-all-the-filters-for-a-report-page"></a>Alle filters weergeven voor een rapportpagina

Het deelvenster **Filters** toont alle filters die door de ontwerper aan het rapport zijn toegevoegd. In het deelvenster **Filters** kunt u ook informatie over de filters weergeven en deze gebruiken. Sla wijzigingen die u maakt op of gebruik **Standaardinstelling herstellen** om de originele filterinstellingen te herstellen.

Als er wijzigingen zijn die u wilt opslaan, kunt u ook een persoonlijke bladwijzer maken. Raadpleeg [Wat zijn bladwijzers?](end-user-bookmarks.md) voor meer informatie.

Het venster **Filters** toont en beheert verschillende typen rapportfilters: rapport, rapportpagina en visual.

In dit voorbeeld hebben we een visual met drie filters geselecteerd: **Fabrikant**, **Maand** en **Totaal aantal eenheden**. De rapportagepagina heeft ook filters; deze staan onder de kop **Filters op deze pagina**. En het hele rapport heeft een filter voor **Datum**, weergegeven onder **Filters op alle pagina's**.

![Schermopname van een rapport met een visualisatie en markering van de bijbehorende filters.](media/end-user-report-filter/power-bi-filter-pane.png)

Naast sommige filters staat **(Alle)**. **(Alle) ** betekent dat alle waarden in het filter worden opgenomen. In de bovenstaande schermopname informeert **Segment (Alle)** dat deze rapportpagina gegevens bevat over alle productsegmenten. 

Iedereen met machtigingen om dit rapport weer te geven, kan met deze filters werken.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Alleen filters weergeven die zijn toegepast op een visual

Ga met de muisaanwijzer over de visual om het filterpictogram ![Schermopname van het filterpictogram](media/end-user-report-filter/power-bi-filter-icon.png) weer te geven en beter zicht te krijgen op de filters die van invloed zijn op een specifieke visual. Selecteer dat filterpictogram om een pop-upvenster weer te geven met alle filters, slicers, enz. die invloed hebben op die visual. De filters in de pop-up zijn dezelfde filters die worden weergegeven in het deelvenster **Filters**, plus eventuele aanvullende filters die van invloed zijn op de geselecteerde visual.

![Schermopname van een lijst filters met pijlen die wijzen naar de posities van deze filters in het deelvenster Filters.](media/end-user-report-filter/power-bi-filters-hover.png)

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

In dit voorbeeld geldt het volgende:
1. Met **Inbegrepen** wordt aangegeven dat het visuele element is gefilterd. Dit betekent dat de staten Alabama en Texas zijn geselecteerd in een van de andere visuals op deze rapportpagina. In dit geval is het de kaartvisual. Door de selectie van deze twee staten worden de gegevens van alle andere staten niet weergegeven in het geselecteerde staafdiagram.  

1. **Datum** is een filter dat wordt toegepast op alle pagina's in dit rapport.

1. **Regio is Centraal** en **Jaar is 2014** zijn filters die zijn toegepast op deze rapportpagina.

4. **Fabrikant is VanArsdel, Natura, Aliqui of Pirum** is een filter dat wordt toegepast op de visual.


### <a name="search-in-a-filter"></a>Zoeken in een filter

Soms kan een filter een lange lijst waarden hebben. Gebruik het zoekvak om de gewenste waarde te zoeken en selecteren.

![Schermopname van hoe u kunt zoeken in een filter.](media/end-user-report-filter/power-bi-search-filter.png)

### <a name="display-filter-details"></a>Filtergegevens weergeven

Als u een filter wilt begrijpen, vouwt u dit uit en bekijkt u de beschikbare waarden en tellingen.  Als u het filter wilt uitvouwen, selecteert u de pijl naast de filternaam.
  
![Schermopname van een filter dat aangeeft dat de regio West is geselecteerd.](media/end-user-report-filter/power-bi-filters-expand.png)

### <a name="change-filter-selections"></a>Filterselecties wijzigen

Een manier om te zoeken naar inzichten in gegevens, is door de filters te gebruiken. U kunt filterselecties wijzigen via de vervolgkeuzelijst naast de veldnaam.  Afhankelijk van het filter en type gegevens dat Power BI filtert, variëren uw opties van eenvoudige selecties in een lijst tot het identificeren van datum- of cijferbereiken. In het geavanceerde filter hieronder hebben we het filter **Total Units YTD** in de treemap gewijzigd naar 2000 tot 3000. U ziet dat door deze wijziging Pirum uit de treemap wordt verwijderd.
  
![Schermopname van een rapport en de bijbehorende filters, waarin de visual treemap is geselecteerd.](media/end-user-report-filter/power-bi-treemap-filter.png)

> [!TIP]
> Houd de CTRL-toets ingedrukt om meer dan één filterwaarde per keer te selecteren. De meeste filters ondersteunen meervoudige selectie.

### <a name="reset-filter-to-default"></a>De standaardwaarden van het filter opnieuw instellen

Selecteer **Standaardinstelling herstellen** in de bovenste menubalk als u alle wijzigingen die u in de filters hebt aangebracht wilt terugzetten.  Deze selectie herstelt de oorspronkelijke staat van de filters die door de rapportontwerper werden ingesteld.

![Schermopname van de optie Standaardinstelling herstellen.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Een filter wissen

Als u een filter wilt herstellen naar (Alle), wist u het filter door de gum naast de naam van het filter te selecteren.

![Schermopname van het gumpictogram.](media/end-user-report-filter/power-bi-erase.png)
  
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
