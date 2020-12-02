---
title: Verbeterde metagegevens van gegevenssets gebruiken in Power BI Desktop
description: In dit artikel wordt beschreven hoe u verbeterde metagegevens van gegevenssets in Power BI kunt gebruiken.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 09/22/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 2c5e465026f1ba7564bda18ad3b005b024a663a7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404980"
---
# <a name="using-enhanced-dataset-metadata"></a>Verbeterde metagegevens van gegevensset gebruiken

Als Power BI Desktop rapporten maakt, worden er ook metagegevens van de gegevensset in de bijbehorende PBIX- en PBIT-bestanden gemaakt. Voorheen werden de metagegevens opgeslagen in een indeling die specifiek was voor Power BI Desktop. Er werd daarbij gebruik gemaakt van M-expressies gecodeerd in base-64 en gegevensbronnen, en er werden veronderstellingen gedaan over hoe die metagegevens werden opgeslagen.

Met de release van de functie **verbeterde metagegevens van gegevenssets** zijn veel van deze beperkingen verwijderd. PBIX-bestanden worden automatisch geüpgraded naar verbeterde metagegevens bij het openen van het bestand. Met **verbeterde metagegevens van gegevenssets** worden metagegevens die zijn gemaakt door Power BI Desktop weergegeven in een indeling die vergelijkbaar is met wat wordt gebruikt voor Analysis Services-modellen in tabelvorm, op basis van het [objectmodel in tabelvorm](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


De functie **verbeterde metagegevens van gegevenssets** is strategisch en fundamenteel, omdat toekomstige Power BI-functionaliteit op deze metagegevens wordt gebouwd. Enkele andere mogelijkheden die baat kunnen hebben bij uitgebreide metagegevens van gegevenssets, zijn onder andere [lezen/schrijven van XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) voor het beheer van Power BI-gegevenssets en de migratie van Analysis Services-workloads naar Power BI om te profiteren van de functies van de volgende generatie.


## <a name="next-steps"></a>Volgende stappen

U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Wat is er nieuw in Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Query-overzicht met Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Algemene querytaken in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)