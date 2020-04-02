---
title: Uitgebreide metagegevens van gegevenssets gebruiken in Power BI Desktop (preview-versie)
description: In dit artikel wordt beschreven hoe u verbeterde metagegevens van gegevenssets in Power BI kunt gebruiken.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3812f16489d304912ec9574352897e1effb29d4a
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201396"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Verbeterde metagegevens van gegevensset gebruiken (preview)

Als Power BI Desktop rapporten maakt, worden er ook metagegevens van de gegevensset in de bijbehorende PBIX- en PBIT-bestanden gemaakt. Voorheen werden de metagegevens opgeslagen in een indeling die specifiek was voor Power BI Desktop. Er werd daarbij gebruik gemaakt van M-expressies gecodeerd in base-64 en gegevensbronnen, en er werden veronderstellingen gedaan over hoe die metagegevens werden opgeslagen.

Met de release van de functie **verbeterde metagegevens van gegevenssets** zijn veel van deze beperkingen verwijderd. Wanneer de functie **verbeterde metagegevens van gegevenssets** is ingeschakeld, gebruiken metagegevens die zijn gemaakt door Power BI Desktop een indeling die vergelijkbaar is met wat wordt gebruikt voor Analysis Services-modellen in tabelvorm, op basis van het [Objectmodel in tabelvorm](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


De functie **verbeterde metagegevens van gegevenssets** is strategisch en fundamenteel, omdat toekomstige Power BI-functionaliteit op deze metagegevens wordt gebouwd. Enkele andere mogelijkheden die baat kunnen hebben bij uitgebreide metagegevens van gegevenssets, zijn onder andere [lezen/schrijven van XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) voor het beheer van Power BI-gegevenssets en de migratie van Analysis Services-workloads naar Power BI om te profiteren van de functies van de volgende generatie.

## <a name="enable-enhanced-dataset-metadata"></a>Verbeterde metagegevens van gegevensset inschakelen

De functie **verbeterde metagegevens van gegevenssets** is momenteel beschikbaar als preview-versie. Als u uitgebreide metagegevens van gegevenssets wilt inschakelen, selecteert u in Power BI Desktop **Bestand > Opties en instellingen > Opties > Preview-functies** en selecteert u vervolgens het selectievakje **Gegevenssets opslaan met indeling voor verbeterde metagegevens**, zoals wordt weergegeven in de volgende afbeelding. 

![De preview-functie inschakelen](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

U wordt gevraagd Power BI Desktop opnieuw op te starten.

![Prompt voor opnieuw opstarten](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Wanneer de preview-functie is ingeschakeld, probeert Power BI Desktop de PBIX- en PBIT-bestanden bij te werken die de vorige metagegevensindeling gebruiken. 

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

In de preview-versie gelden de volgende beperkingen wanneer de preview-functie is ingeschakeld.

Bij het openen van een bestaand PBIX- of PBIT-bestand dat niet is bijgewerkt, mislukt de upgrade als de gegevensset een van de volgende functies of connectors bevat. Als deze fout zich voordoet, zou dat niet direct invloed moeten hebben op de gebruikerservaring. Power BI Desktop blijft ook de vorige metagegevensindeling gebruiken.

* Python-scripts
* Aangepaste connectors
* Azure DevOps Server
* BI-connector
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* M-expressies met bepaalde tekencombinaties, zoals '\\n' in kolomnamen
* Wanneer u gegevenssets gebruikt met de functie **verbeterde metagegevens van gegevenssets** ingeschakeld, kunnen eenmalige aanmelding (SSO) niet worden ingesteld in de Power BI-service

Daarnaast kunnen PBIX- en PBIT-bestanden die al zijn bijgewerkt om **verbeterde metagegevens van gegevenssets** te gebruiken *niet* de bovenstaande functies of connectors in de huidige versie gebruiken.


## <a name="next-steps"></a>Volgende stappen

U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Wat is er nieuw in Power BI Desktop?](desktop-latest-update.md)
* [Query-overzicht met Power BI Desktop](desktop-query-overview.md)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Algemene querytaken in Power BI Desktop](desktop-common-query-tasks.md)
