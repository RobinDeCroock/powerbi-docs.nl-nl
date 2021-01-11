---
title: De functie Slicers synchroniseren inschakelen in Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u de functie Slicers synchroniseren kunt toevoegen aan Power BI-visuals. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885281"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Slicers synchroniseren in Power BI-visuals

Gebruik API-versie 1.13.0 of hoger in uw aangepaste slicervisual om de functie [Slicers synchroniseren](../../visuals/power-bi-visualization-slicers.md) te ondersteunen.

Daarnaast moet u de optie inschakelen in het bestand *capabilities.json*, zoals weergegeven in de volgende code:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Nadat u het bestand *capabilities.json* hebt bijgewerkt, kunt u het deelvenster met opties voor **Slicers synchroniseren** weergeven als u de aangepaste slicervisual selecteert.

> [!NOTE]
> De functie Slicers synchroniseren ondersteunt niet meer dan één veld. Als uw slicer meer dan één veld (**Categorie** of **Meting**) heeft, wordt de functie uitgeschakeld.

![Het deelvenster Slicers synchroniseren](media/enable-sync-slicers/sync-slicers-panel.png)

In het deelvenster **Slicers synchroniseren** ziet u dat de zichtbaarheid en filtratie van uw slicer op meerdere rapportpagina's kan worden toegepast.