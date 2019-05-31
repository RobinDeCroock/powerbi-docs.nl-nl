---
title: Automatisch gegevensinzichten genereren met Power BI
description: Meer informatie over het verkrijgen van inzicht in uw gegevenssets en dashboardtegels.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 9e1c4a3942c75f41dc105e424685d32badbf3866
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61238219"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>Automatisch gegevensinzichten genereren met Power BI
Hebt u een nieuwe gegevensset en weet niet precies waar u moet beginnen?  Moet u snel een dashboard bouwen?  Wilt u snel inzichten zoeken die u hebt gemist?

Voer Snelle inzichten uit om interessante interactieve visualisaties op basis van uw gegevens te genereren. Snelle inzichten kan worden uitgevoerd op een volledige gegevensset (Snelle inzichten) of op een specifieke dashboardtegel (Scoped inzichten). U kunt inzichten zelfs uitvoeren op een inzicht.

> [!NOTE]
> Inzichten werken niet met DirectQuery, maar alleen met gegevens die zijn geüpload naar Power BI.
> 

De functie voor inzichten is gebouwd op een groeiende [set geavanceerde analytische algoritmen](service-insight-types.md) die zijn ontwikkeld samen met Microsoft Research. We blijven Microsoft Research gebruiken om ervoor te zorgen dat meer mensen op nieuwe en intuïtieve manieren inzichten in hun gegevens kunnen vinden.

## <a name="run-quick-insights-on-a-dataset"></a>Snelle inzichten uitvoeren op een gegevensset
Kijk hoe Amanda snelle inzichten uitvoert op een gegevensset, een inzicht opent in de focusmodus, een van de inzichten vastmaakt aan haar dashboard en vervolgens inzichten verkrijgt voor haar dashboardtegel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Nu is het uw beurt. Verken inzichten door gebruik te maken van het de [voorbeeld van kwaliteitsanalyse van leveranciers](sample-supplier-quality.md).

1. Selecteer op het tabblad **Gegevenssets** het beletselteken (...) en kies **Inzichten verkrijgen**.
   
    ![Tabblad Gegevenssets](media/service-insights/power-bi-ellipses.png)
   
    ![Menu met weglatingstekens](media/service-insights/power-bi-tab.png)
2. Er worden [verschillende algoritmen](service-insight-types.md) in Power BI gebruikt om trends in uw gegevensset te zoeken.
   
    ![Dialoogvenster Inzichten zoeken](media/service-insights/pbi_autoinsightssearching.png)
3. Uw inzichten zijn binnen enkele seconden klaar.  Selecteer **Inzichten weergeven** om visualisaties weer te geven.
   
    ![Het bericht Geslaagd](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Met sommige gegevenssets kunt u geen inzichten genereren, omdat de gegevens statistisch gezien niet significant zijn.  Zie [Uw gegevens optimaliseren voor inzichten](service-insights-optimize.md) voor meer informatie.
   > 
    
1. De visualisaties worden weergeven op een speciaal canvas voor **Snelle inzichten** met maximaal 32 afzonderlijke kaarten met inzichten. Elke kaart bevat een grafiek of diagram plus een korte beschrijving.
   
    ![Canvas Snelle inzichten](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interactie met de kaarten met inzichten
  ![Speldpictogram](media/service-insights/pbi_hover.png)

1. Beweeg de muisaanwijzer over de kaart en selecteer het speldpictogram om de visualisatie toe te voegen aan een dashboard.
2. Beweeg de muisaanwijzer over een kaart, selecteer het beletselteken (...) en kies **Inzichten weergeven**. Hiermee opent u het inzicht in een volledig scherm.
   
    ![Inzicht in volledig scherm](media/service-insights/power-bi-insight-focus.png)
3. In de focusmodus kunt u het volgende:
   
   * De visualisaties filteren.  Selecteer de pijl in de rechterbovenhoek van het deelvenster Filters om de filters weer te geven.
        ![Inzicht in uitgevouwen menu Filters](media/service-insights/power-bi-insights-filter-new.png)
   * Maak de kaart met inzichten vast aan een dashboard door het speldpictogram ![Speldpictogram](media/service-insights/power-bi-pin-icon.png) of **Visueel element vastmaken** te selecteren.
   * Voer inzichten uit op de kaart zelf. Dit wordt vaak aangeduid als **scoped inzichten**. Selecteer in de rechterbovenhoek het gloeilamppictogram ![Pictogram Inzichten verkrijgen](media/service-insights/power-bi-bulb-icon.png) of selecteer **Inzichten verkrijgen**.
     
       ![Menubalk met pictogram Inzichten verkrijgen](media/service-insights/pbi-autoinsights-tile.png)
     
     Het inzicht wordt aan de linkerkant weergegeven en de nieuwe kaarten, die uitsluitend zijn gebaseerd op dit ene inzicht, worden aan de rechterkant weergegeven.
     
       ![Inzichten in inzichten](media/service-insights/power-bi-insights-on-insights-new.png)
4. Selecteer in de linkerbovenhoek **Focusmodus sluiten** om terug te keren naar het oorspronkelijk canvas inzichten.

## <a name="run-insights-on-a-dashboard-tile"></a>Inzichten uitvoeren op een dashboardtegel
In plaats dat u inzichten zoekt in een complete gegevensset, kunt u uw zoekopdracht afbakenen tot de gegevens die zijn gebruikt om een dashboardtegel te maken. Ook dit wordt vaak aangeduid als **scoped inzichten**.

1. Open een dashboard.
2. Beweeg de muisaanwijzer over een tegel. Selecteer het beletselteken (...) en kies **Inzichten verkrijgen**. De tegel wordt geopend in de [focusmodus](service-focus-mode.md) met de kaarten voor inzichten weergegeven aan de rechterkant.    
   
    ![Focusmodus](media/service-insights/pbi-insights-tile.png)    
4. Wekt een bepaald inzicht uw interesse? Selecteer deze kaart om dieper te graven. Het geselecteerde inzicht wordt aan de linkerkant weergegeven en de nieuwe kaarten met inzichten, die uitsluitend zijn gebaseerd op dit ene inzicht, worden aan de rechterkant weergegeven.    
6. Blijf in uw gegevens spitten, en wanneer u een interessant inzicht hebt gevonden, kunt u dit vastmaken aan uw dashboard door in de rechterbovenhoek **Visueel element vastmaken** te selecteren.

## <a name="next-steps"></a>Volgende stappen
Als u de eigenaar van een gegevensset bent, kunt u deze [optimaliseren voor Snelle inzichten](service-insights-optimize.md)

Meer informatie over de [typen Snelle inzichten die beschikbaar zijn](service-insight-types.md)

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

