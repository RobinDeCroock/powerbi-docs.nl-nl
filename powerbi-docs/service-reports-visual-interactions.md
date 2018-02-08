---
title: De interactie tussen visuals in een rapport wijzigen
description: Documentatie voor het instellen van Visuele interacties in een Microsoft Power BI-rapport en een Power BI Desktop-rapport.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/10/2018
ms.author: mihart
ms.openlocfilehash: a7c4db0044772c28a3cb7a62649de3001945246c
ms.sourcegitcommit: afd6e9e6f8b192b26486cd04d2cbc9de046911b3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/11/2018
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Visualisatie-interacties in een Power BI-rapport
Als u machtigingen hebt om een rapport te bewerken, kunt u **Visuele interacties** gebruiken om te wijzigen hoe visualisaties op een rapportpagina invloed op elkaar hebben. 

Visualisaties op een rapportpagina kunnen standaard worden gebruikt voor het kruislings filteren en markeren van de andere visualisaties op de pagina.
Als u bijvoorbeeld een staat op een kaartvisualisatie selecteert, wordt de kolomdiagram gemarkeerd en wordt het lijndiagram zo gefilterd dat alleen de gegevens worden weergegeven die van toepassing zijn voor die staat.
Zie [Over filteren en markeren](power-bi-reports-filters-and-highlighting.md). En als u een visualisatie hebt die ondersteuning biedt voor [analyseren](power-bi-visualization-drill-down.md), heeft het analyseren van één visualisatie standaard geen invloed op de andere visualisaties op de rapportpagina. Maar deze standaardgedragsuitingen kunnen beide worden genegeerd en er kunnen interacties worden ingesteld per visualisatie.

In dit artikel ziet u hoe u **Visuele interacties** gebruikt in de [bewerkingsweergave](service-interact-with-a-report-in-editing-view.md) van de Power BI-service en in Power BI Desktop. Als een rapport met u is gedeeld, kunt u de instellingen voor Visuele interacties niet wijzigen.

> [!NOTE]
> De termen *kruislings filteren* en *kruislings markeren* worden gebruikt om de hier beschreven werking te onderscheiden van wat er gebeurt wanneer u het venster **Filters** gebruikt en visualisaties markeert.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecteer een visualisatie om deze actief te maken.  
2. Toon de opties voor **Visuele interacties**.
    - Selecteer de vervolgkeuzelijst op de menubalk van rapporten in de Power BI-service.

       ![](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - Selecteer in Desktop **Indeling > Interacties**.

        ![](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. Als u de besturingselementen voor interactie tussen visualisaties wilt inschakelen, selecteert u **Interacties bewerken**. Power BI voegt pictogrammen voor kruislings filteren en kruislings markeren toe aan alle andere visualisaties op de rapportpagina.
   
    ![](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. Bepaal welke impact de geselecteerde visualisatie op de andere moet hebben.  Herhaal dit eventueel voor alle andere visualisaties op de rapportpagina.
   
   * Als de visualisatie kruislings moet worden gefilterd, selecteert u het **filterpictogram** ![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Als de visualisatie kruislings moet worden gemarkeerd, selecteert u het **markeerpictogram** ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Als er niets hoeft te gebeuren, selecteert u het pictogram voor **geen impact** ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).

4. Als u besturingselementen voor analyseren wilt inschakelen, selecteert u **Analysefilters voor andere visuals**.  Wanneer u nu omlaag (of omhoog) gaat in een visualisatie, worden de andere visualisaties op de rapportpagina gewijzigd om uw huidige analyseselectie weer te geven. 

   ![](media/service-reports-visual-interactions/drill2.gif)

### <a name="next-steps"></a>Volgende stappen
[How to use report filters](power-bi-how-to-report-filter.md) (Rapportfilters gebruiken)

[Filters en markeren in rapporten](power-bi-reports-filters-and-highlighting.md)

[Power BI - basisconcepten](service-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
