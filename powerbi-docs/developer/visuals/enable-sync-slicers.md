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
ms.openlocfilehash: 345971384fff0e0b215d2898ee1684f4a5bac486
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114308"
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

![Het deelvenster Slicers synchroniseren](media/enable-sync-slicers/sync-slicers-panel.png)

In het deelvenster **Slicers synchroniseren** ziet u dat de zichtbaarheid en filtratie van uw slicer op meerdere rapportpagina's kan worden toegepast.
