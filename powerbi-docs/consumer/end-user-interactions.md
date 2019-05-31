---
title: De interactie tussen visuals in een rapport begrijpen
description: Documentatie voor Power BI-eindgebruikers waarin wordt uitgelegd hoe visuals op een rapportpagina werken.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413166"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hoe visuele elementen elkaar kruislings filteren in een Power BI-rapport
Een van de geweldige functies van Power BI is de manier waarop alle visuals op een rapportpagina onderling zijn verbonden. Als u een gegevenspunt in een van deze visuals selecteert, worden alle andere visuals op de pagina die deze gegevens bevatten, gewijzigd op basis van deze selectie. 

![video van hoe visuals onderling werken](media/end-user-interactions/interactions.gif)

Door standaard, selecteert een gegevenspunt in één visualisatie op een rapportpagina wordt kruislings filteren, kruislings markeren en de andere visualisaties op de pagina omlaag. 

Dit kan nuttig zijn om te bepalen hoe een waarde in uw gegevens draagt bij aan een andere. Bijvoorbeeld, het segment beheer selecteren in het ringdiagram markeert de bijdrage van dat segment aan elke kolom in het totaal aantal eenheden per maand grafiek en deze het lijndiagram aan de rechterkant is gefilterd.

![afbeelding van visuele elementen interactie](media/end-user-interactions/power-bi-interactions.png)

Zie [Over filteren en markeren](../power-bi-reports-filters-and-highlighting.md). 

Hoe de visuals op een pagina precies samenwerken, wordt ingesteld door de *rapportontwerper*. Ontwerpers kunnen visuele interacties in- en uitschakelen, en de standaardinstellingen voor kruislings filteren, kruislings markeren en zoomen wijzigen. 
  
> [!NOTE]
> De termen *kruislings filteren* en *kruislings markeren* worden gebruikt om de hier beschreven werking te onderscheiden van wat er gebeurt wanneer u het venster **Filters** gebruikt en visualisaties markeert.  

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
- Als uw rapport heeft een visualisatie die ondersteuning biedt voor [boren](../power-bi-visualization-drill-down.md), standaard analyseren van één visualisatie heeft geen invloed op de andere visualisaties op de rapportpagina.     
- Als u visualA gebruiken om te communiceren met visualB, wordt de filters op niveau van visualA worden toegepast op visualB.

## <a name="next-steps"></a>Volgende stappen
[How to use report filters](../power-bi-how-to-report-filter.md) (Rapportfilters gebruiken)
