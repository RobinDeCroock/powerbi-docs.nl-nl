---
title: Inzichten over dashboardtegels uitvoeren en bekijken
description: Als eindgebruiker van Power BI, kunt u meer informatie krijgen over inzicht in uw dashboardtegels.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: fcfb16de53b4e6c67b7c46fec87ab614d07cb9b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61049103"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Gegevensinzichten over dashboardtegels bekijken met Power BI
Elke visualisatietegel op het dashboard is een poort naar het verkennen van gegevens. Als u een tegel selecteert, wordt er een rapport geopend waarin u kunt filteren en sorteren, en dieper kunt ingaan op de gegevensset achter het rapport. En wanneer u inzichten uitvoert, wordt de gegevensverkenning voor u uitgevoerd met Power BI.

Voer Snelle inzichten uit om interessante interactieve visualisaties op basis van uw gegevens te genereren. Snelle inzichten kunnen worden uitgevoerd voor een specifieke dashboardtegel en u kunt zelfs inzichten uitvoeren voor een inzicht!

De functie voor inzichten is gebouwd op een groeiende [set geavanceerde analytische algoritmen](end-user-insight-types.md) die zijn ontwikkeld samen met Microsoft Research. We blijven Microsoft Research gebruiken om ervoor te zorgen dat meer mensen op nieuwe en intuïtieve manieren inzichten in hun gegevens kunnen vinden.

## <a name="run-insights-on-a-dashboard-tile"></a>Inzichten uitvoeren op een dashboardtegel
Als u inzichten uitvoert voor een dashboardtegel, wordt in Power BI alleen gezocht in de gegevens die zijn gebruikt om deze specifieke dashboardtegel te maken. 

1. [Open een dashboard.](end-user-dashboards.md)
2. Beweeg de muisaanwijzer over een tegel. selecteer het beletselteken (...) en kies **Inzichten weergeven**. 

    ![modus voor beletseltekenmenu](./media/end-user-insights/power-bi-hover.png)


3. De tegel wordt geopend in de [focusmodus](end-user-focus.md) met de kaarten voor inzichten weergegeven aan de rechterkant.    
   
    ![Focusmodus](./media/end-user-insights/pbi-insights-tile.png)    
4. Wekt een bepaald inzicht uw interesse? Selecteer deze kaart om dieper te graven. Het geselecteerde inzicht wordt aan de linkerkant weergegeven en de nieuwe kaarten met inzichten, die uitsluitend zijn gebaseerd op dit ene inzicht, worden aan de rechterkant weergegeven.    

 ## <a name="interact-with-the-insight-cards"></a>Interactie met de kaarten met inzichten
Als er een inzicht is geopend, kunt u doorgaan met verkennen.

   * Filter de visual op het canvas.  Als u de filters wilt weergeven, selecteert u de pijl in de rechterbovenhoek om het deelvenster Filters uit te vouwen.

     ![inzicht in een uitgevouwen menu Filters](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Inzichten uitvoeren op de inzichtkaart zelf. Dit wordt vaak aangeduid als **verwante inzichten**. Selecteer in de rechterbovenhoek het gloeilamppictogram ![Inzichten verkrijgen](./media/end-user-insights/power-bi-bulb-icon.png) of selecteer **Inzichten verkrijgen**.
     
     ![Menubalk met pictogram Inzichten verkrijgen](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     Het inzicht wordt aan de linkerkant weergegeven en de nieuwe kaarten, die uitsluitend zijn gebaseerd op dit ene inzicht, worden aan de rechterkant weergegeven.
     
     ![Inzichten in inzichten](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Selecteer in de linkerbovenhoek **Focusmodus sluiten** om terug te keren naar het oorspronkelijk inzichtencanvas.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
- **Inzichten weergeven** werkt niet met DirectQuery, maar alleen met gegevens die zijn geüpload naar Power BI.
- **Inzichten weergeven** werkt niet met alle typen dashboardtegel. Het is bijvoorbeeld niet beschikbaar voor aangepaste visuele elementen.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Volgende stappen
Meer informatie over de [typen Snelle inzichten die beschikbaar zijn](end-user-insight-types.md)

