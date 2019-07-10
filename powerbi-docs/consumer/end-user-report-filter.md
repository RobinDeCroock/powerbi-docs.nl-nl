---
title: Rondleiding maken door het deelvenster Rapportfilters
description: Een rapportfilter toevoegen aan een rapport in de Power BI-service voor gebruikers
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532957"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Rondleiding door het deelvenster Filters van het rapport

In dit artikel wordt het rapportvenster **Filters** in Power BI-service besproken. Gebruik de filters om nieuwe inzichten in uw gegevens te ontdekken.

Er zijn veel verschillende manieren om gegevens te filteren in Power BI. Zie [Over filters en markeren in Power BI-rapporten](../power-bi-reports-filters-and-highlighting.md) voor meer informatie over filters.

![Schermopname van een rapport in de browser, met een pijl die wijst naar de optie Filters.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Het deelvenster Filters van het rapport gebruiken

Als een collega een rapport met u deelt, bekijk dan het deelvenster **Filters**. Het wordt soms samengevouwen aan de rechterzijde van het rapport. Selecteer het om het uit te breiden.

![Schermopname van het rapport met een uitgevouwen deelvenster Filters.](media/end-user-report-filter/power-bi-filter-pane.png)

Het deelvenster **Filters** bevat filters die de rapport*ontwerper* aan het rapport heeft toegevoegd. *Gebruikers* als uzelf kunnen de bestaande filters gebruiken en wijzigingen opslaan, maar geen nieuwe filters aan het rapport toevoegen. In de bovenstaande schermopname heeft de ontwerper bijvoorbeeld twee filters op paginaniveau toegevoegd: **Segment** en **Jaar**. U kunt deze filters gebruiken en wijzigen, maar u kunt geen derde filter op paginaniveau toevoegen.

Rapporten in de Power BI-service houden alle wijzigingen bij die u in het deelvenster **Filters** maakt. De service past deze wijzigingen toe op de mobiele versie van het rapport.

Selecteer ![Schermopname van de optie Standaardinstelling herstellen](media/end-user-report-filter/power-bi-reset.png) als u de standaardinstellingen van de ontwerper voor het deelvenster **Filters** wilt herstellen. in de bovenste menubalk.

## <a name="view-all-the-filters-for-a-report-page"></a>Alle filters weergeven voor een rapportpagina

Het deelvenster **Filters** toont alle filters die door de ontwerper aan het rapport zijn toegevoegd. In het deelvenster **Filters** kunt u ook informatie over de filters weergeven en deze gebruiken. U kunt uw wijzigingen opslaan of **Standaardinstelling herstellen** gebruiken om de oorspronkelijke filterinstellingen terug te draaien.

Als er wijzigingen zijn die u wilt opslaan, kunt u ook een persoonlijke bladwijzer maken.  Raadpleeg [Wat zijn bladwijzers?](end-user-bookmarks.md) voor meer informatie.

Het deelvenster **Filters** toont en beheert verschillende soorten rapportfilters. Deze kunnen worden toegepast op een visual, rapportpagina of geheel rapport.

In dit voorbeeld hebben we een visual met twee filters geselecteerd. De rapportagepagina heeft ook filters; deze staan onder de kop **Filters op deze pagina**. Het gehele rapport heeft bovendien een filter voor **Datum**.

![Schermopname van een rapport met een visualisatie en markering van de bijbehorende filters.](media/end-user-report-filter/power-bi-all-filters2.png)

Naast sommige filters staat **(Alle)** . **(Alle)**  betekent dat alle waarden in het filter worden opgenomen. In de bovenstaande schermopname informeert **Segment (Alle)** dat deze rapportpagina gegevens bevat over alle productsegmenten. Als u het paginaniveaufilter **Regio is West** selecteert, bevat de rapportpagina alleen gegevens voor de regio West.

Iedereen die dit rapport bekijkt, kan met deze filters werken.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Alleen filters weergeven die zijn toegepast op een visual

Ga met de muisaanwijzer over de visual om het filterpictogram ![Schermopname van het filterpictogram](media/end-user-report-filter/power-bi-filter-icon.png) weer te geven en beter zicht te krijgen op de filters die op een specifieke visual zijn toegepast. Selecteer dat filterpictogram om een pop-upvenster weer te geven met alle filters, slicers, enz. die invloed hebben op die visual. De filters in het pop-upvenster zijn dezelfde filters die in het deelvenster **Filters** worden toegepast.

![Schermopname van een lijst filters met pijlen die wijzen naar de posities van deze filters in het deelvenster Filters.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

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

In het volgende voorbeeld:

1. Kunnen we zien dat er een kruisfilter op het kolomdiagram is toegepast.

1. **Opgenomen** geeft aan dat het kruislingse filter is bedoeld voor **Segment** en dat er drie zijn opgenomen.

1. Is een slicer toegepast voor **Kwartaal**.

1. Is **Regio** een filter dat op deze rapportpagina is toegepast.

1. Zijn **isVanArsdel** en **Year** filters die op deze visual zijn toegepast.

![Schermopname van een rapport en bijbehorende filters, waarbij de lijst met filters is genummerd zodat deze samenvalt met de bovenstaande genummerde lijst.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Zoeken in een filter

Soms kan een filter een lange lijst waarden hebben. Gebruik het zoekvak om de gewenste waarde te zoeken en selecteren.

![Schermopname van hoe u kunt zoeken in een filter.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Filtergegevens weergeven

Bekijk de beschikbare waarden en tellingen om een filter te begrijpen.  Bekijk de details van het filter door de pijl naast de naam van het filter aan te wijzen en te selecteren.
  
![Schermopname van een filter dat aangeeft dat de regio West is geselecteerd.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Filterselecties wijzigen

Een manier om te zoeken naar inzichten in gegevens, is door de filters te gebruiken. U kunt filterselecties wijzigen via de vervolgkeuzelijst naast de veldnaam.  Afhankelijk van het filter en type gegevens dat Power BI filtert, variëren uw opties van eenvoudige selecties in een lijst tot het identificeren van datum- of cijferbereiken. In het geavanceerde filter hieronder hebben we het filter **Total Units YTD** in de treemap gewijzigd naar 2000 tot 3000. U ziet dat door deze wijziging Prirum uit de treemap wordt verwijderd.
  
![Schermopname van een rapport en de bijbehorende filters, waarin Fashions Direct is geselecteerd.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Houd de CTRL-toets ingedrukt om meer dan één filterwaarde per keer te selecteren. De meeste filters ondersteunen meervoudige selectie.

### <a name="reset-filter-to-default"></a>De standaardwaarden van het filter opnieuw instellen

Selecteer **Standaardinstelling herstellen** in de bovenste menubalk als u alle wijzigingen die u in de filters hebt aangebracht wilt terugzetten.  Deze selectie herstelt de oorspronkelijke staat van de filters die door de rapportontwerper werden ingesteld.

![Schermopname van de optie Standaardinstelling herstellen.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Een filter wissen

Als er slechts één filter is dat u op **(Alle)** wilt instellen, kunt u dit wissen door het gumpictogram ![Schermopname van het gumpictogram.](media/end-user-report-filter/power-bi-eraser-icon.png) te selecteren naast de naam van het filter.
  
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