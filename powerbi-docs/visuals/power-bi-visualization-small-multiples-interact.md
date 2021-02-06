---
title: Interactie met kleine veelvouden in Power BI (preview-versie)
description: In dit artikel wordt uitgelegd hoe u met kleine veelvouden of trellising kunt werken.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617339"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Interactie met kleine veelvouden in Power BI (preview-versie)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Met kleine veelvouden of trellising splitst u een visueel element in meerdere versies van zichzelf. In dit artikel wordt uitgelegd hoe u de meeste interactie ermee kunt doen.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Scherm opname van kleine veelvouden voor categorie en regio.":::

Wilt u kleine veelvouden maken? Zie [kleine veelvouden maken in Power bi (preview)](power-bi-visualization-small-multiples.md).

## <a name="scroll-in-a-small-multiple"></a>Schuiven in een kleine veelvoud

Kleine veelvouden kunnen meer afzonderlijke grafieken bevatten die in het raster passen. Als dat het geval is, kunt u omlaag schuiven om de rest van uw categorieën te zien.

Voor een categorische X-as met veel categorieën ziet u ook een schuif balk voor elk exemplaar van die as. Door te schuiven op die as worden ze allemaal tegelijk verplaatst. Als u een schuif wiel gebruikt, houdt u SHIFT ingedrukt om de categorische-assen te schuiven.

## <a name="select-data-to-cross-highlight"></a>Gegevens selecteren om te markeren

U kunt verschillende subsets van gegevens selecteren door verschillende onderdelen van het visuele element te selecteren.

### <a name="select-data-points"></a>Gegevens punten selecteren

Beweeg de muis aanwijzer over het gegevens punt op één veelvoud om de knop info in dat veelvoud weer te geven. U ziet ook een hulplijn lijn op de X-as voor lijn diagrammen. Selecteer dat gegevens punt om andere visuele elementen te markeren door de waarde van de as en de kleine categorie en de andere veelvouden te dimmen.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="Selecteer een gegevens punt in een kleine veelvoud.":::

### <a name="select-a-categorical-axis-value"></a>Een waarde voor een categorische-as selecteren

Selecteer een categorie label om andere visuele elementen met die Aswaarde te markeren.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="Selecteer een categorieas in een kleine veelvoud.":::

### <a name="select-a-title"></a>Een titel selecteren

Selecteer de titel van een veelvoud om andere visuele elementen te kruisen door de categorie in die subkoptekst.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="Selecteer een titel in een kleine veelvoud.":::

### <a name="legend"></a>Legenda

Selecteer een legenda categorie om andere visuele elementen kruislings te markeren en andere veelvouden te markeren.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="Selecteer een item in de legenda in een kleine veelvoud.":::


## <a name="sort"></a>Sorteren

Met de nieuwe sorteer functionaliteit kunt u meerdere aspecten van een visueel element tegelijk sorteren. Sorteer op de categorie en ook door de as in elk veelvoud. 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="De kleine veelvouden sorteren.":::

## <a name="next-steps"></a>Volgende stappen

[Kleine veelvouden in Power BI maken (preview)](power-bi-visualization-small-multiples.md)
