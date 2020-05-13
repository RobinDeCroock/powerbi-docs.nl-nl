---
title: Richtlijnen voor samengestelde modellen in Power BI Desktop
description: Hier vindt u richtlijnen voor het ontwikkelen van samengestelde modellen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 528fc40427a1cb242d9154028d1a7c6617c8a14e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279680"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Richtlijnen voor samengestelde modellen in Power BI Desktop

Dit artikel is bedoeld voor gegevensmodelleerders die samengestelde modellen willen ontwikkelen in Power BI. Er worden gebruikscases beschreven en u krijgt richtlijnen voor het ontwerpproces. De richtlijnen zijn met name bedoeld om u te helpen bepalen of een samengesteld model wel geschikt is voor uw oplossing. Als dat het geval is, helpt dit artikel u ook bij het ontwerpen van een optimaal model.

> [!NOTE]
> In dit artikel wordt niet ingegaan op samengestelde modellen in het algemeen. Als u niet volledig bekend bent met samengestelde modellen, raden we u aan eerst het artikel [Samengestelde modellen in Power BI Desktop gebruiken](../transform-model/desktop-composite-models.md) te lezen.
>
> Omdat samengestelde modellen uit ten minste één DirectQuery-bron bestaan, is het ook belangrijk dat u een grondige kennis hebt van [modelrelaties](../transform-model/desktop-relationships-understand.md), [DirectQuery-modellen](../connect-data/desktop-directquery-about.md)en [richtlijnen voor het ontwerpen van DirectQuery-modellen](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Gebruikscases voor samengestelde modellen

Als dat mogelijk is, kunt u modellen het beste ontwikkelen in de importmodus. Deze modus biedt namelijk niet alleen de grootste flexibiliteit, maar ook de beste prestaties.

Importmodellen zijn echter niet geschikt voor het oplossen van uitdagingen met betrekking tot grote gegevensvolumes of bij rapportage over bijna realtime gegevens. In deze gevallen kunt u een DirectQuery-model overwegen, op voorwaarde dat uw gegevens zijn opgeslagen in één gegevensbron die [wordt ondersteund door de DirectQuery-modus](../connect-data/power-bi-data-sources.md).

In de volgende situaties is het zinvol om een samengesteld model te ontwikkelen.

- Het model kan een DirectQuery-model zijn, maar u wilt de prestaties verbeteren. In een samengesteld model kunnen de prestaties worden verbeterd door voor elke tabel de juiste opslag te configureren. U kunt ook [aggregaties toevoegen](../transform-model/desktop-aggregations.md). Beide optimalisaties worden verderop in dit artikel besproken.
- U wilt een DirectQuery-model combineren met aanvullende gegevens, die in het model moeten worden geïmporteerd. Geïmporteerde gegevens kunnen worden geladen vanuit een andere gegevensbron of uit berekende tabellen.
- U wilt twee of meer DirectQuery-gegevensbronnen combineren tot één model.

> [!NOTE]
> Samengestelde modellen kunnen geen bronnen van live-verbindingen of analytische databases van DirectQuery combineren. Voorbeelden van bronnen van live-verbindingen zijn [extern gehoste modellen](../connect-data/service-datasets-understand.md#external-hosted-models) en Power BI-gegevenssets. SAP Business Warehouse en SAP HANA zijn voorbeelden van bronnen van analytische DirectQuery-databases.

## <a name="optimize-model-design"></a>Modelontwerp optimaliseren

Een samengesteld model kan worden geoptimaliseerd door het configureren van [opslagmodi](../transform-model/desktop-storage-mode.md) voor tabellen en door [aggregaties](../transform-model/desktop-aggregations.md) toe te voegen.

### <a name="table-storage-mode"></a>Table-opslagmodus

In een samengesteld model kunt u de opslagmodus voor elke tabel configureren (met uitzondering van berekende tabellen):

- **DirectQuery**: We raden u aan deze modus in te stellen voor tabellen die grote gegevensvolumes vertegenwoordigen of die bijna realtime resultaten moeten leveren. Gegevens worden nooit in deze tabellen geïmporteerd. Deze tabellen zijn meestal feitentabellen: tabellen die worden gebruikt voor overzichten.
- **Importeren**: Het wordt aangeraden deze modus in te stellen voor dimensietypetabellen, ofwel tabellen die worden gebruikt voor filteren en groeperen. Dit is in feite de enige optie voor tabellen op basis van bronnen die niet worden ondersteund door de DirectQuery-modus. Berekende tabellen zijn altijd importtabellen.
- **Dual**: U wordt aangeraden deze modus in te stellen voor dimensietypetabellen, wanneer de mogelijkheid bestaat dat deze tegelijk met DirectQuery-feitentabellen uit dezelfde bron worden bevraagd.

Er zijn verschillende scenario's mogelijk waarin Power BI een query uitvoert op een samengesteld model:

- **Alleen query's op een of meer import- of dual-tabellen**: Alle gegevens worden opgehaald uit de modelcache. Dit biedt de snelst mogelijke prestaties. Dit scenario is gebruikelijk voor dimensietypetabellen die worden bevraagd met behulp van filters of slicervisualisaties.
- **Query's op een of meer dual- of DirectQuery-tabellen uit dezelfde bron**: Alle gegevens worden opgehaald door een of meer native query's te verzenden naar de DirectQuery-bron. Dit biedt de snelst mogelijke prestaties, met name wanneer de juiste indexen bestaan voor de brontabellen. Dit scenario is gebruikelijk voor query's waarbij dual-dimensietypetabellen en DirectQuery-feitentabellen worden gekoppeld. Deze query's zijn _intra-eiland_ en dus worden alle een-op-een- of een-op-veel-relaties geëvalueerd als [sterke relaties](../transform-model/desktop-relationships-understand.md#strong-relationships).
- **Alle overige query's**: Deze query's omvatten relaties tussen eilanden. De reden hiervoor is dat een importtabel is gekoppeld aan een DirectQuery-tabel of een dual-tabel aan een DirectQuery-tabel vanuit een andere bron. In het laatste geval gedraagt de tabel zich als een importtabel. Alle relaties worden geëvalueerd als [zwakke relaties](../transform-model/desktop-relationships-understand.md#weak-relationships). Het betekent ook dat groeperingen die worden toegepast op niet-DirectQuery-tabellen, als een virtuele tabel moeten worden verzonden naar de DirectQuery-bron. In dit geval kan de native query inefficiënt zijn, met name voor grote groepeersets. Bovendien bestaat de kans dat er gevoelige gegevens worden blootgesteld in de native query.

Kort samengevat, adviseren wij het volgende:

- Denk goed na of een samengesteld model wel de juiste oplossing is. Hoewel een dergelijk model integratie op modelniveau mogelijk maakt van verschillende gegevensbronnen, krijgt u ook te maken met complexe ontwerpaspecten en de mogelijke gevolgen hiervan.
- Stel de opslagmodus in op **DirectQuery** wanneer een tabel een feitentabel is waarin grote hoeveelheden gegevens worden opgeslagen, of wanneer bijna realtime resultaten vereist zijn.
- Stel de opslagmodus in op **Dual** wanneer een tabel een dimensietypetabel is en deze tegelijk wordt bevraagd met **DirectQuery**-feitentabellen op basis van dezelfde bron.
- Configureer de juiste vernieuwingsfrequenties om de modelcache voor dual-tabellen (en eventuele afhankelijke berekende tabellen) synchroon te houden met de brondatabase(s).
- Streef ernaar om de integriteit van gegevens te garanderen tussen gegevensbronnen (inclusief de modelcache): zwakke relaties elimineren rijen wanneer gerelateerde kolomwaarden niet overeenkomen.
- Optimaliseer DirectQuery-gegevensbronnen met de juiste indexen voor efficiënte samenvoegingen, filters en groeperingen.
- Laad geen gevoelige gegevens in import- of dual-tabellen als er het risico bestaat dat een native query wordt onderschept. Zie Gevolgen voor de beveiliging in het artikel [Samengestelde modellen in Power BI Desktop gebruiken](../transform-model/desktop-composite-models.md#security-implications) voor meer informatie.

### <a name="aggregations"></a>Aggregaties

U kunt aggregaties toevoegen aan DirectQuery-tabellen in uw samengestelde model. Aggregaties worden opgeslagen in de cache in het model en werken dus als importtabellen (hoewel ze niet kunnen worden gebruikt als een modeltabel). Ze hebben als doel om de prestaties te verbeteren voor query's met een algemener aggregatieniveau. Zie [Aggregaties in Power BI Desktop](../transform-model/desktop-aggregations.md) voor meer informatie.

Wij adviseren om altijd een basisregel te hanteren voor een aggregatietabel: Het aantal rijen moet minstens een factor tien kleiner zijn dan van de onderliggende tabel. Als de onderliggende tabel bijvoorbeeld één miljard rijen bevat, mag de aggregatietabel niet groter zijn dan 100 miljoen rijen. Deze regel zorgt ervoor dat de prestatieverbetering voldoende groot is ten opzichte van de kosten voor het maken en onderhouden van de aggregatietabel.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Samengestelde modellen in Power BI Desktop gebruiken](../transform-model/desktop-composite-models.md)
- [Modelrelaties in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [DirectQuery-modellen in Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [DirectQuery in Power BI Desktop gebruiken](../connect-data/desktop-use-directquery.md)
- [Problemen met het DirectQuery-model in Power BI Desktop oplossen](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI-gegevensbronnen](../connect-data/power-bi-data-sources.md)
- [Opslagmodus in Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Aggregaties in Power BI Desktop](../transform-model/desktop-aggregations.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)
