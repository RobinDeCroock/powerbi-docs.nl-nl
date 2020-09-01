---
title: Natuurlijke taal gebruiken door middel van importeren, live-verbinding en DirectQuery
description: In dit artikel wordt besproken hoe de Q&A-functie werkt met de verschillende soorten gegevensbronnen die beschikbaar zijn in Power BI. We kijken ook naar de concepten van indexeren en opslaan in cache.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706195"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Natuurlijke taal gebruiken door middel van importeren, live-verbinding en DirectQuery

Met de Q&A-functie in Power BI kunt u snel antwoorden krijgen over uw gegevens door gebruik te maken van natuurlijke taal om vragen over die gegevens te stellen. In dit artikel wordt beschreven hoe indexering en caching worden gebruikt om de prestaties voor elke ondersteunde configuratie te verbeteren.

## <a name="what-data-sources-are-supported-in-qa"></a>Welke gegevensbronnen worden ondersteund in Q&A?

Voor Q&A worden de volgende configuraties ondersteund:

- Modus Importeren
- Modus Live-verbinding: met behulp van on-premises SQL Server Analysis Services, Azure Analysis Services of Power BI-gegevenssets
- Directe query: Azure Synapse, Azure SQL en SQL Server 2019. Hoewel andere bronnen in de modus directe query kunnen werken, ondersteunen we deze bronnen niet officieel.

Standaard wordt Q&A ingeschakeld in een rapport als u de Q&A-visual gebruikt. Er wordt een prompt weergegeven als u een DirectQuery- of live-verbinding gebruikt. U kunt de mogelijkheden voor natuurlijke taal voor een rapport expliciet in- of uitschakelen in de opties.

![Q&A-bureaubladopties](media/qna-desktop-options.png)

Zie [Beperkingen van Power BI Q&A](q-and-a-limitations.md) voor meer informatie.

## <a name="how-does-indexing-work-with-qa"></a>Hoe werkt indexeren met Q&A?

Wanneer u Q&A inschakelt, wordt er een index gemaakt om snel realtime-feedback te geven aan de gebruiker en om de vragen van de gebruiker te interpreteren. Het kan enige tijd duren voordat de index is gemaakt en deze heeft de volgende elementen en beperkingen.

- Alle kolomnamen en tabellen worden aan de index toegevoegd, tenzij deze expliciet zijn uitgeschakeld in het Q&A-hulpprogramma.
- Alle tekstwaarden die kleiner zijn dan 100 tekens worden geïndexeerd. Tekstwaarden die groter zijn dan 100 tekens worden niet geïndexeerd. 
- Er worden maximaal vijf miljoen unieke waarden in de Q&A-index opgeslagen. Als u deze drempelwaarde overschrijdt, bevat de index niet alle mogelijke waarden, wat de nauwkeurigheid van de resultaten van Q&A kan verminderen.
- Als er een fout optreedt tijdens het indexeren, blijft de index onvolledig en wordt deze opnieuw gemaakt bij de volgende vernieuwing, zoals wordt beschreven in de volgende sectie.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Hoe vaak wordt de index vernieuwd en in de cache opgeslagen?

In Power BI Desktop wordt de index gemaakt op het moment dat u Q&A gebruikt. Er wordt een klein pictogram weergegeven zodat u weet dat de index wordt samengesteld. Gedurende deze periode kan het enige tijd duren om de Q&A-visual en eventuele suggesties te laden.

In Power BI Service wordt de index opnieuw gemaakt bij het publiceren/herpubliceren en vernieuwen. De Q&A-index wordt niet altijd automatisch gemaakt en wordt soms on-demand gemaakt om vernieuwing van de gegevensset te optimaliseren. Voor DirectQuery indexeren we de gegevens meestal eenmaal per dag om de impact op de DirectQuery-bron te verminderen.

## <a name="next-steps"></a>Volgende stappen

U kunt op verschillende manieren natuurlijke taal in uw rapporten integreren. Raadpleeg deze artikelen voor meer informatie:

* [Q&A-visual](../visuals/power-bi-visualization-q-and-a.md)
* [Best practices voor Q&A](q-and-a-best-practices.md)
