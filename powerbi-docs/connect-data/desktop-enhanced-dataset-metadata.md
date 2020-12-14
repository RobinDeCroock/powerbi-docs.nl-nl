---
title: Verbeterde metagegevens van gegevenssets gebruiken in Power BI Desktop
description: In dit artikel wordt beschreven hoe u verbeterde metagegevens van gegevenssets in Power BI kunt gebruiken.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906958"
---
# <a name="using-enhanced-dataset-metadata"></a>Verbeterde metagegevens van gegevensset gebruiken

Als Power BI Desktop rapporten maakt, worden er ook metagegevens van de gegevensset in de bijbehorende PBIX- en PBIT-bestanden gemaakt. Voorheen werden de metagegevens opgeslagen in een indeling die specifiek was voor Power BI Desktop. De metagegevens die worden gebruikt met base 64 gecodeerde M-expressies en gegevensbronnen. Power BI doet veronderstellingen over hoe de metagegevens zijn opgeslagen.

Met de release van de functie **verbeterde metagegevens van gegevenssets** zijn veel van deze beperkingen verwijderd. PBIX-bestanden worden automatisch geüpgraded naar verbeterde metagegevens bij het openen van het bestand. Met **verbeterde metagegevens van gegevenssets** worden metagegevens die zijn gemaakt door Power BI Desktop weergegeven in een indeling die vergelijkbaar is met wat wordt gebruikt voor Analysis Services-modellen in tabelvorm, op basis van het [objectmodel in tabelvorm](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


De functie **Verbeterde metagegevens van gegevenssets** is strategisch en elementair. Er wordt toekomstige Power BI-functionaliteit gebaseerd op de metagegevens. Die andere functies zullen profiteren van de verbeterde metagegevens van de gegevensset:

- [XMLA lezen/schrijven](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) voor het beheer van Power BI gegevenssets
- Migratie van Analysis Services-workloads naar Power BI om te profiteren van de functies van de volgende generatie.

## <a name="limitations"></a>Beperkingen
Vóór de ondersteuning met verbeterde metagegevens werd in Power BI Desktop voor SQL Server-, Oracle-, Teradata- en verouderde HANA-verbindingen een systeemeigen query toegevoegd aan het gegevensmodel. Deze query wordt gebruikt door gegevensmodellen van de Power BI-service. Met ondersteuning met verbeterde metagegevens wordt de systeemeigen query tijdens runtime door het gegevensmodel van de Power BI-service opnieuw gegenereerd. De door Power BI Desktop gemaakte query wordt niet gebruikt. In de meeste gevallen wordt deze ophaalbewerking op de juiste manier opgelost, maar sommige transformaties werken niet zonder dat de onderliggende gegevens worden gelezen. Mogelijk worden er fouten weergegeven in rapporten die eerder wel hebben gewerkt. De fout ziet er bijvoorbeeld als volgt uit: 

'Kan een M-query in tabel Dimension City niet naar een systeemeigen bronquery converteren. Probeer het later opnieuw of neem contact op met ondersteuning. Geef de volgende gegevens op wanneer u contact opneemt met de ondersteuning.' 

U kunt uw query's op drie verschillende plaatsen in Power BI Desktop verhelpen:

- Wanneer u wijzigingen toepast of een vernieuwingsbewerking uitvoert.
- In een waarschuwingsbalk in de Power Query-editor, waarin wordt gemeld dat de expressie niet naar de gegevensbron kan worden gepusht.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="Schermopname van het bericht Querywijzigingen toepassen: Kan de expressie niet pushen naar de gegevensbron.":::
- Wanneer u evaluaties uitvoert bij het openen van een rapport om te controleren of u query's hebt die niet worden ondersteund. Het uitvoeren van deze evaluaties kan gevolgen hebben voor de prestaties.


## <a name="next-steps"></a>Volgende stappen

U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Wat is er nieuw in Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Query-overzicht met Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Algemene querytaken in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
