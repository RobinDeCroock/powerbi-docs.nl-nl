---
title: De functie Slicers synchroniseren inschakelen in Power BI-visuals
description: In dit artikel wordt beschreven hoe u de functie Slicers synchroniseren kunt toevoegen aan Power BI-visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 055878988a197b80a8e4842a6567966f75af2ce5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880142"
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
