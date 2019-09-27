---
title: De functie Slicers synchroniseren inschakelen in Power BI-visuals
description: In dit artikel wordt beschreven hoe u de functie Slicers synchroniseren kunt toevoegen aan Power BI-visuals.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 47f0148528d1ccfd451aa8e8ed87b4bec99d087e
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194398"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Slicers synchroniseren in Power BI-visuals

Gebruik API-versie 1.13 of hoger in uw aangepaste slicervisual om de functie [Slicers synchroniseren](https://docs.microsoft.com/power-bi/desktop-slicers) te ondersteunen.

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

![Het deelvenster Slicers synchroniseren](./media/sync-slicers-panel.png)

In het deelvenster **Slicers synchroniseren** ziet u dat de zichtbaarheid en filtratie van uw slicer op meerdere rapportpagina's kan worden toegepast.
