---
title: Best practices voor gegevensstromen
description: Een verzameling koppelingen naar best practices en richtlijnen voor gegevensstromen
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: fb688b20fd8b5ee1288f670fba9f7f45fc058680
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565353"
---
# <a name="dataflows-best-practices"></a>Best practices voor gegevensstromen

Power BI-**gegevensstromen** zijn een bedrijfsgerichte oplossing voor gegevensvoorbereiding, die een ecosysteem van gegevens mogelijk maakt dat klaar is voor verbruik, hergebruik en integratie. Dit artikel bevat een lijst best practices, met koppelingen naar artikelen en andere informatie die u meer inzicht geven in gegevensstromen en hoe u deze optimaal kunt gebruiken.

## <a name="dataflows-across-the-power-platform"></a>Gegevensstromen over Power Platform

Gegevensstromen kunnen worden gebruikt op verschillende Power Platform-technologieën, zoals Power Query, Microsoft Dynamics 365 en andere Microsoft-producten. Zie [Gegevensstromen in Microsoft-producten gebruiken](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) voor meer informatie over hoe gegevensstromen werken op het Power Platform.


## <a name="dataflows-best-practices-table-and-links"></a>Tabel met en koppelingen naar best practices voor gegevensstromen

De volgende tabel bevat een verzameling koppelingen naar artikelen over best practices voor het maken van of werken met gegevensstromen. De koppelingen bevatten informatie over het ontwikkelen van bedrijfslogica en complexe gegevensstromen, hergebruik van gegevensstromen en hoe u uw gegevensstromen kunt schalen tot bedrijfsformaat.


|**Onderwerp**  |**Hulpgedeelte**  |**Koppeling naar artikel of inhoud**  |
|---------|---------|---------|
|Power Query     | Tips en trucs om optimaal te profiteren van uw ervaring met data-wrangling        |[Best practices voor Power Query](/power-query/best-practices)        |
|Berekende entiteiten gebruiken     |Er zijn prestatievoordelen voor het gebruik van berekende entiteiten in een gegevensstroom         |[Scenario's voor berekende entiteiten](/power-query/dataflows/computed-entities-scenarios)         |
|Complexe gegevensstromen ontwikkelen     |Patronen voor het ontwikkelen van grootschalige, presterende gegevensstromen         |[Complexe gegevensstromen](/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Gegevensstromen opnieuw gebruiken     |Patronen, richtlijnen en gebruiksvoorbeelden         |[Gegevensstromen opnieuw gebruiken](/power-query/dataflows/best-practices-reusing-dataflows)         |
|Grootschalige implementaties     |Grootschalig gebruik en richtlijnen als aanvulling op de bedrijfsarchitectuur         |[Datawarehousing met behulp van gegevensstromen](/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Verbeterde berekeningsengine gebruiken     |De gegevensstroomprestaties potentieel tot 25x verbeteren         |[Verbeterde berekeningsengine](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Uw workloadinstellingen optimaliseren     |Haal het maximale uit onze infrastructuur voor gegevensstromen door de hulpmiddelen te begrijpen die u kunt gebruiken om de prestaties te maximaliseren         |[Configuratie van workload van gegevensstromen](dataflows-premium-workload-configuration.md)         |
|Tabellen samenvoegen en uitbreiden     |Goed presterende samenvoegingen maken         |[Uitbreiding van tabellen optimaliseren](/power-query/optimize-expanding-table-columns)         |
|Richtlijnen voor query's vouwen     |Transformaties met behulp van het bronsysteem versnellen         |[Query's vouwen](/power-query/power-query-folding)         |
|Gegevensprofilering gebruiken     |Meer informatie over kwaliteit, distributie en profiel van kolommen         |[Hulpprogramma's voor gegevensprofilering](/power-query/data-profiling-tools)         |
|Foutafhandeling implementeren     |Robuuste gegevensstromen ontwikkelen die bestand zijn tegen fouten bij vernieuwing, met suggesties         |[Patronen voor veelvoorkomende fouten](/power-query/dealing-with-errors)  </br> [Afhandeling van complexe fouten](/power-query/error-handling)      |
|Schemaweergave gebruiken      |De creatie-ervaring verbeteren bij het werken met een brede tabel en het uitvoeren van schemabewerkingen         |[Schemaweergave](/power-query/schema-view)         |
|Gekoppelde entiteiten      |Transformaties opnieuw gebruiken en hiernaar verwijzen         |[Gekoppelde entiteiten](/power-query/dataflows/linked-entities)         |
|Incrementeel vernieuwen      |De meest recente of gewijzigde gegevens laden versus volledig opnieuw laden         |[Incrementeel vernieuwen](/power-query/dataflows/incremental-refresh)         |
|||


        
## <a name="next-steps"></a>Volgende stappen

De volgende artikelen bieden meer informatie over gegevensstromen en Power BI:

* [Inleiding tot gegevensstromen en selfservice voor gegevensvoorbereiding](dataflows-introduction-self-service.md)
* [Een gegevensstroom maken](dataflows-create.md)
* [Een gegevensstroom configureren en gebruiken](dataflows-configure-consume.md)
* [Premium-functies van gegevensstromen](dataflows-premium-features.md)
* [Gegevensstroomopslag configureren voor gebruik van Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [AI met gegevensstromen](dataflows-machine-learning-integration.md)
* [Beperkingen en overwegingen van gegevensstromen](dataflows-features-limitations.md)