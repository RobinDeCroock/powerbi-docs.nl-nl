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
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/16/2019
ms.locfileid: "66413166"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hoe visuele elementen elkaar kruislings filteren in een Power BI-rapport
Een van de geweldige functies van Power BI is de manier waarop alle visuals op een rapportpagina onderling zijn verbonden. Als u een gegevenspunt in een van deze visuals selecteert, worden alle andere visuals op de pagina die deze gegevens bevatten, gewijzigd op basis van deze selectie. 

![video van hoe visuals onderling werken](media/end-user-interactions/interactions.gif)

Wanneer een gegevenspunt in één visualisatie op een rapportpagina wordt gebruikt, worden de andere visualisaties op de pagina kruislings gefilterd, kruislings gemarkeerd en ingezoomd. 

Dit kan handig zijn om aan te geven hoe een van de waarden in uw gegevens bijdraagt aan een andere. Als u bijvoorbeeld het segment Beheer in het ringdiagram selecteert, wordt de bijdrage van dat segment aan elke kolom in het diagram Totaal aantal eenheden per maand gemarkeerd en is het lijndiagram aan de rechterkant gefilterd.

![afbeelding van hoe visuals onderling werken](media/end-user-interactions/power-bi-interactions.png)

Zie [Over filteren en markeren](../power-bi-reports-filters-and-highlighting.md). 

Hoe de visuals op een pagina precies samenwerken, wordt ingesteld door de *rapportontwerper*. Ontwerpers kunnen visuele interacties in- en uitschakelen, en de standaardinstellingen voor kruislings filteren, kruislings markeren en zoomen wijzigen. 
  
> [!NOTE]
> De termen *kruislings filteren* en *kruislings markeren* worden gebruikt om de hier beschreven werking te onderscheiden van wat er gebeurt wanneer u het venster **Filters** gebruikt en visualisaties markeert.  

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
- Als uw rapport een visualisatie bevat die ondersteuning biedt voor [analyseren](../power-bi-visualization-drill-down.md), heeft het analyseren van één visualisatie standaard geen invloed op de andere visualisaties op de rapportpagina.     
- Als u visualisatieA gebruikt om te communiceren met visualisatieB, worden filters op het visuele niveau van visualisatieA toegepast op visualisatieB.

## <a name="next-steps"></a>Volgende stappen
[How to use report filters](../power-bi-how-to-report-filter.md) (Rapportfilters gebruiken)
