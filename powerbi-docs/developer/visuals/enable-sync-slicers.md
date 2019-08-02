---
title: Slicers synchroniseren inschakelen
description: De functie Slicers synchroniseren toevoegen voor Power BI-visuals
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425017"
---
# <a name="sync-slicers"></a>Slicers synchroniseren

Gebruik API 1.13 of hoger in uw aangepaste slicervisual om de functie [Slicers synchroniseren](https://docs.microsoft.com/power-bi/desktop-slicers) te ondersteunen.

Het tweede benodigde aspect is de ingeschakelde optie in `capabilities.json` (zie onderstaande voorbeeld).

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

Nadat u wijzigingen hebt aangebracht in `capabilities.json`, ziet u het deelvensters met opties voor Slicers synchroniseren door op uw aangepaste slicervisual te klikken.

> [!NOTE]
> Als uw slicer uit meer dan één veld bestaat (categorie of meting) wordt de functie uitgeschakeld, omdat Slicers synchroniseren geen ondersteuning biedt voor meerdere velden worden.

![Het deelvenster Slicers synchroniseren](./media/sync-slicers-panel.png)

In het deelvenster ziet u dat u de zichtbaarheid en filtratie van uw slicer op meerdere rapportpagina's kan worden toegepast.
