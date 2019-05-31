---
title: Lintgrafieken gebruiken in Power BI
description: Lintgrafieken maken en gebruiken in de Power BI-service en Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 08a2de32b092ba24b66ddd9f173be1eaea8819ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394408"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Lintgrafieken gebruiken in Power BI
U kunt lintgrafieken gebruiken om gegevens te visualiseren en snel te ontdekken welke gegevenscategorie de hoogste rang heeft (hoogste waarde). In lintgrafieken kunnen wijzigingen in de rang goed worden weergegeven, waarbij voor elke periode de hoogste rang (waarde) altijd bovenaan wordt weergegeven. 

![lintgrafiek](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Een lintgrafiek maken
Als u wilt volgen, opent u [Voorbeeldrapport van een retailanalyse](../sample-retail-analysis.md). 

1. Selecteer **Lintgrafiek** in het deelvenster **Visualisaties** als u een lintgrafiek wilt maken.

    ![visualisatiesjablonen](media/desktop-ribbon-charts/ribbon-charts_02.png)

    Lintgrafieken verbinden met behulp van linten een gegevenscategorie met het gevisualiseerde tijdcontinuüm, zodat u kunt zien hoe de rang van een bepaalde categorie langs de X-as (meestal de tijd) verandert.

2. Selecteer velden voor **As**, **Legenda** en **Waarde**.  In dit voorbeeld zijn de volgende velden geselecteerd: **Datum**, **Categorie** en **Verkopen van dit jaar**.  

    ![geselecteerde velden](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Omdat de gegevensset gegevens voor slechts één jaar bevat, hebben we het veld **Jaar** uit de well **As** verwijderd. 

3. Het lintdiagram toont de positie van elke andere maand. U ziet hoe de positie in de tijd verandert.  De categorie Startpagina is bijvoorbeeld van de derde naar de vierde positie gegaan en weer terug naar de derde. De categorie Juniors zijn in juli van de derde naar de vijfde positie gegaan. 

    ![lintgrafiek](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Een lintgrafiek opmaken
Als u een lintgrafiek maakt, hebt u de beschikking over opmaakopties in de sectie **Opmaken** van het deelvenster **Visualisaties**. De opmaakopties voor lintgrafieken zijn soortgelijk als die voor een gestapelde kolomdiagram. Voor linten zijn er daarnaast aanvullende opmaakopties beschikbaar.

![lintsjabloon in het deelvenster Visualisatie](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Met deze opmaakopties voor lintgrafieken kunt u de volgende aanpassingen maken.

* **Afstand**: hiermee kunt u aanpassen hoeveel afstand u tussen de linten wilt hebben. Het getal is een percentage van de maximale kolomhoogte.
* **Afstemmen op de kleur van de reeks**: hiermee kunt u de kleur van de linten afstemmen op de kleur van de reeks. Indien dit is ingesteld op **uit**, zijn alle linten grijs.
* **Doorzichtigheid**: hiermee kunt u aangeven hoe doorzichtig de linten moeten zijn. De standaardwaarde is 30.
* **Rand**: hiermee kunt u een donkere rand boven en onder aan de linten plaatsen. Standaard zijn de randen afwezig.

Omdat het lintdiagram geen Y-as-labels bevat, kunt u eventueel gegevenslabels toevoegen. Selecteer in het deelvenster Opmaak de optie **Gegevenslabels**. 

![opmaakopties voor gegevenslabels](media/desktop-ribbon-charts/power-bi-labels.png)

opmaakopties instellen voor uw gegevenslabels.  In dit voorbeeld hebben we de tekstkleur op wit, het aantal decimalen op nul en de weergave-eenheden op duizenden ingesteld. 

![lintsjabloon in het deelvenster Visualisatie](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Volgende stappen

[Spreidingsdiagrammen en bellendiagrammen in Power BI](power-bi-visualization-scatter.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)